# How Palantir's Ontology actually works under the hood

**Palantir's Ontology layer achieves production reliability through five core engineering patterns: a semantic abstraction layer that decouples schema from storage, a dual-track writeback system for conflict resolution, Elasticsearch-powered object indexing, optimistic-concurrency atomic Actions, and a mandatory access control system based on "markings."** These patterns are well-documented enough to replicate on PostgreSQL — but each has subtle design decisions that determine whether a clone actually works in production. This report provides the specific technical answers to the five critical implementation questions, drawn from Palantir's official documentation, patent filings, OSDK source code, and government security certifications, along with concrete PostgreSQL implementation strategies for each.

---

## 1. Schema evolution relies on manual remapping, not automatic migration

**(a) Most authoritative source:** Palantir Foundry documentation at `https://www.palantir.com/docs/foundry/ontology/object-types/` and the Ontology Health page at `https://www.palantir.com/docs/foundry/ontology/ontology-health/`. Patent family US11138180B2 ("Dynamic ontology generation and update") covers versioned ontology definitions and backward-compatible schema changes.

**(b) Specific technical answer:** The Ontology is a **semantic abstraction layer** that sits above raw datasets. Each Object Type maps to a backing dataset (Parquet files managed by Spark), and each Property maps to a specific column by name and type. This mapping is explicit, configured in the Ontology Manager (OMS). When a backing dataset's schema changes — say SAP renames `customer_name` to `cust_nm` — **the Ontology does not automatically update**. The affected Object Type becomes "unhealthy," and the Ontology Manager surfaces a schema mismatch warning. An administrator must manually remap the property to the new column name.

There is **no traditional schema registry** analogous to Confluent Schema Registry. The Ontology itself serves as the semantic schema registry. Foundry datasets store schema metadata per-transaction (each dataset build records its column set and types), but there is no standalone versioning system. The Ontology has a **global version counter** that increments when any Object Type, Link Type, or Action Type is modified. Individual Object Types do not have independent version numbers (no "v1, v2, v3" per type).

**The OSDK uses a code-generation model** for schema safety. The CLI generates TypeScript/Python interfaces from the current Ontology state. When the Ontology changes, developers must re-run code generation. Breaking changes (removed or renamed properties) produce **compile-time errors** in consuming applications — this is by design and is the primary safety net. The SDK does not pin to a specific Ontology version at runtime; it always queries the current state. There is no mechanism to query a historical Ontology version.

**"Ontology as Code" (OaC)** is Palantir's emerging migration tooling — it allows defining Object Types in code (TypeScript/YAML) and applying them declaratively via the Developer Console. This is a "desired state" model, not sequential migrations.

**(c) Inferences from evidence:** Palantir's best practice is to **insulate the Ontology via pipeline layers**. Rather than letting source schema changes propagate to the Ontology, a Transform (pipeline step) should alias renamed columns back to expected names. There is no rollback mechanism for Ontology changes and no downstream impact analysis showing which Workshop apps reference a given property.

**(d) PostgreSQL equivalent strategy:**

PostgreSQL has a significant advantage here. Use **Flyway or Liquibase** for versioned, sequential migrations with rollback support and checksums. Implement a metadata registry as the Ontology Manager equivalent:

```sql
CREATE TABLE ontology_object_types (
    id UUID PRIMARY KEY, api_name TEXT UNIQUE NOT NULL,
    backing_table TEXT NOT NULL, version INT DEFAULT 1
);
CREATE TABLE ontology_properties (
    id UUID PRIMARY KEY, object_type_id UUID REFERENCES ontology_object_types(id),
    api_name TEXT NOT NULL, backing_column TEXT NOT NULL, data_type TEXT NOT NULL
);
```

Generate **PostgreSQL views dynamically** from the property-to-column mappings to create the semantic abstraction layer. Use **Prisma** as the OSDK equivalent — `prisma db pull` introspects the schema, `prisma generate` creates TypeScript types, and schema drift is detected at compile time. Unlike Palantir, you get per-Object-Type version history, rollback, and automatic downstream impact detection via `pg_depend`.

---

## 2. Conflict resolution uses a dual-track writeback architecture

**(a) Most authoritative source:** Palantir documentation on Action Types (`https://www.palantir.com/docs/foundry/action-types/action-types-overview/`) and the writeback/edits configuration sections. The OSDK repos (`palantir/osdk-ts`) confirm that `applyAction()` returns edits already resolved — the client never sees the underlying conflict.

**(b) Specific technical answer:** Palantir does **not impose a single universal conflict resolution policy**. Instead, it provides two complementary mechanisms:

**The Edits Layer (Platform-Managed, Edit-Wins):** When enabled on an Object Type, human edits through Actions are stored in a platform-managed overlay store, separate from pipeline-sourced data. At read time, the system performs a **COALESCE** — `COALESCE(edit_value, pipeline_value)` — so **the edit always wins** while it exists. Edits are stored at property-level granularity: each record contains the object primary key, property name, new value, timestamp, editing user, and Action RID. Edits **persist across pipeline rebuilds** — if SAP syncs new data but an edit overlay exists, the edit still takes precedence until explicitly cleared. OSV2 applies this overlay at serving time, providing real-time edit visibility even before the next pipeline build.

**The Writeback Dataset Pattern (Developer-Managed, Fully Configurable):** Actions write to a **dedicated writeback dataset** — a separate Foundry dataset (Parquet files) distinct from the source dataset. A downstream Transform reads both the source dataset and the writeback dataset, then implements custom merge logic. The developer controls resolution: last-write-wins by timestamp, source-priority with override flags, edit-priority until source changes, or any custom strategy. The merged output becomes the backing dataset for the Object Type. The pattern is: `source_dataset + writeback_dataset → Transform(merge logic) → reconciled_dataset → Object Type`.

**Neither "last-write-wins" nor "source-of-truth priority" is universally imposed.** The edits layer defaults to edit-priority; the writeback pattern defaults to whatever the developer implements. For source-system writeback (writing changes back to SAP via API), the source system remains the single source of truth and the next sync brings back the canonical value.

**(c) Key inference:** The edits layer appears to be backed by an internal metadata store (likely a distributed key-value store), not a user-visible dataset by default. However, edits can be **materialized to a dataset** for pipeline access, giving developers visibility into what was edited. Stale edit detection (flagging edits when the source value has changed since the edit was made) is possible but requires custom pipeline logic — it is not automatic.

**(d) PostgreSQL equivalent strategy:**

PostgreSQL's MVCC provides a natural foundation. Implement the dual-track pattern:

```sql
-- Source data (from ETL/CDC)
CREATE TABLE source_objects (
    object_id UUID PRIMARY KEY, field_a TEXT, 
    source_last_modified TIMESTAMPTZ
);
-- Edits layer
CREATE TABLE object_edits (
    object_id UUID, property_name TEXT, new_value JSONB,
    old_source_value JSONB, edited_by TEXT, edited_at TIMESTAMPTZ,
    is_active BOOLEAN DEFAULT TRUE,
    PRIMARY KEY (object_id, property_name)
);
-- Live merged view (edit-wins overlay)
CREATE VIEW merged_objects AS
SELECT s.object_id,
    COALESCE(e.new_value->>'value', s.field_a) AS field_a
FROM source_objects s
LEFT JOIN object_edits e ON s.object_id = e.object_id 
    AND e.property_name = 'field_a' AND e.is_active;
```

Add a **CDC trigger** to detect source changes and flag stale edits automatically — something Palantir doesn't provide natively. Use `REFRESH MATERIALIZED VIEW CONCURRENTLY` for the reconciled view, or keep it as a live view for real-time resolution. The PostgreSQL approach can actually be **superior** to Palantir's because you get transactional consistency between edits and source data in a single database, eliminating the eventual-consistency gap of Palantir's separate stores.

---

## 3. OSV2 runs on Elasticsearch with columnar storage underneath

**(a) Most authoritative source:** Palantir job postings for the "Object Storage" team (careers.palantir.com) consistently list **Elasticsearch, Apache Lucene, and Java** as required skills. Patent US10678860B2 ("Object indexing for data analysis") describes inverted index structures consistent with Lucene. Patent US10180977B2 ("Object-centric data analysis system") covers the object indexing architecture.

**(b) Specific technical answer:** Object Storage V2 (OSV2) uses an **Elasticsearch/Lucene-based indexing engine** as its core search and query layer, with a **decoupled architecture** separating storage from serving. Backing datasets are stored as Parquet files on distributed object storage (S3/HDFS/Azure Blob), managed by Apache Spark. OSV2 indexes objects from these datasets into Elasticsearch, where each object becomes a document with typed fields corresponding to properties.

The indexing pipeline works as follows: when a dataset transaction creates new data, OSV2 detects changed rows via transaction log comparison, extracts property values based on the Object Type mapping, serializes objects as JSON documents, and bulk-indexes them into Elasticsearch via the bulk API. **Each Object Type maps to an Elasticsearch index** (or set of indices), with properties mapped to typed Elasticsearch fields. Links are indexed bidirectionally — either embedded in object documents or maintained in separate link indices.

OSV2 achieves sub-second search through **pre-computed inverted indexes** (queries hit indexes, not raw data), Elasticsearch's internal filter and fielddata caches, OS-level filesystem caching of Lucene segments, and NRT (near-real-time) refresh at ~1-second intervals. The **edits overlay** is applied at serving time, so objects reflect Action edits before the next full pipeline build.

**Phonograph** was the legacy V1 system used in Palantir Gotham, built on a custom key-value store with secondary indexes. OSV2 was a ground-up rewrite for Foundry, designed for horizontal scalability and cloud-native deployment.

**(c) Performance limits (from practitioner evidence):**

- **Objects per type:** Tens to hundreds of millions practical; **100M+** achievable with proper sharding
- **Properties per type:** ~**1,000 properties** soft limit; performance degrades above several hundred
- **Link traversal:** **2–3 hops** performant (sub-second); deeper traversals degrade exponentially with cardinality
- **Simple filter latency:** Sub-**100ms** for well-indexed properties
- **Complex multi-filter:** **100ms–1s** typical
- **Multi-hop traversal:** **500ms–5s** depending on fan-out
- **Index refresh:** Seconds to low minutes from dataset sync to queryable

**(d) PostgreSQL equivalent strategy:**

For European SMBs (likely <50M objects per type), a **hybrid PostgreSQL + search engine** architecture is optimal:

- **PostgreSQL** as source of truth for objects, links, and ACID transactions
- **GIN indexes on JSONB** for property filtering (excellent for <10M objects with simple containment queries)
- **PostgreSQL full-text search** (tsvector + GIN) for basic text search
- **Meilisearch** (simpler, sufficient for <10M objects) or **Elasticsearch** (for >10M objects) as a companion search engine fed by CDC via Debezium or logical replication

PostgreSQL alone can handle the SMB workload for property filtering and 2-hop link traversals via recursive CTEs. The critical decision point is full-text search with relevance ranking — PostgreSQL's tsvector lacks BM25 tuning and custom analyzers that Elasticsearch provides. For the target market of European SMBs, **Meilisearch is the recommended companion** — it's open-source, simple to operate, and handles typo-tolerant search well at SMB scale, with far less operational overhead than Elasticsearch.

---

## 4. Actions are atomic with optimistic concurrency and async side effects

**(a) Most authoritative source:** Palantir's API v2 documentation at `https://www.palantir.com/docs/foundry/api/ontologies-resources/actions/apply-action/` and the Functions documentation at `https://www.palantir.com/docs/foundry/functions/functions-actions/`. The `palantir/osdk-ts` GitHub repo confirms the `applyAction()` interface and error types.

**(b) Specific technical answer:**

**Atomicity: Yes, fully atomic.** When an Action modifies multiple objects across types, all edits are collected into a single **edit batch** and committed atomically to the Ontology's backing store. A Function backing an Action returns an `IEdits` object describing all changes; these are not applied incrementally during execution but collected and applied as a unit after the function completes successfully. Either all edits succeed, or none are applied.

**Concurrency: Optimistic Concurrency Control (OCC).** Each Ontology object carries a version identifier. When an Action reads objects and then writes modifications, the system checks that objects have not been modified since they were read. If a concurrent modification is detected, the Action fails with an **HTTP 409 Conflict** error. There is no automatic retry — the client must handle retries. No saga pattern is used because all object edits reside within a single backing store.

**The Action execution lifecycle has six phases:**

1. **Parameter validation** — type-checks against Action Type schema; fail = reject, zero edits
2. **Function execution** — backing `@OntologyEditFunction` runs in a sandboxed environment, reading current object state and computing edits; exception = reject, zero edits
3. **Submission criteria** — post-execution validation rules against proposed edits; fail = reject, zero edits
4. **Conflict detection** — OCC version check on all read objects; conflict = HTTP 409, zero edits
5. **Atomic commit** — all edits written as a single transaction; versions updated, indexes refreshed
6. **Async side effects** — webhooks, notifications, pipeline triggers dispatched post-commit; failures here do **not** roll back committed edits

**Side effects use at-least-once delivery semantics.** Webhooks are retried on receiver failure but there is no documented transactional outbox pattern guaranteeing exactly-once delivery. The API supports a `VALIDATE_ONLY` mode for dry-run validation without applying edits, and a `returnEdits` flag to inspect the proposed edit set.

**(c) Key inferences:** There is no cross-Action transaction grouping — you cannot atomically commit two separate Actions. For multi-step workflows requiring compensation, external orchestration is needed. Action timeout behavior and idempotency key support are not clearly documented.

**(d) PostgreSQL equivalent strategy:**

PostgreSQL actually **exceeds Palantir's guarantees** in several areas:

```sql
BEGIN;  -- Full ACID transaction
  UPDATE purchase_orders SET status = 'approved' WHERE id = $1 AND version = $2;
  INSERT INTO receipts (po_id, status) VALUES ($1, 'pending');
  INSERT INTO payments (po_id, amount) VALUES ($1, $3);
  -- Transactional outbox (BETTER than Palantir's model)
  INSERT INTO outbox_events (event_type, payload) 
    VALUES ('po_approved', jsonb_build_object('po_id', $1));
COMMIT;
```

Use **optimistic locking with a version column** (`WHERE version = $expected_version`) for the closest equivalent to Palantir's OCC. The transactional outbox pattern gives you **stronger side-effect guarantees** than Palantir provides — the outbox record is committed atomically with the data, ensuring events are never lost. A separate worker polls the outbox and dispatches webhooks/notifications. PostgreSQL's `LISTEN/NOTIFY` (also transactional) provides real-time event notification. For multi-step workflows spanning external systems, implement the saga pattern with compensation logic.

---

## 5. Markings enforce mandatory access control at property granularity

**(a) Most authoritative source:** Palantir Foundry security documentation at `https://www.palantir.com/docs/foundry/security/markings-overview/`. Patent US10635276B2 ("Purpose-based data access control") describes the PBAC model. Palantir holds **FedRAMP Moderate** authorization (verified on `marketplace.fedramp.gov`), SOC 2 Type II, and ISO 27001, confirming NIST 800-53 AC-family compliance.

**(b) Specific technical answer:**

**Marking granularity spans four levels:**

| Level | Supported | Mechanism |
|---|---|---|
| **Dataset/Object Type** | Yes | Markings applied to entire datasets; all objects inherit |
| **Row/Object instance** | Yes | "Marking columns" in datasets drive per-row markings; Ontology object-level permissions |
| **Column/Property** | Yes | Individual properties can carry independent markings; users without the marking see the object but not that property |
| **Cell** | Partial | Achievable by combining row-level and column-level restrictions; not natively per-cell |

**Markings are mandatory access control (MAC)**, layered on top of discretionary project-level access (DAC) and Purpose-Based Access Control (PBAC). Even if a user has project-level access, they cannot see data with a marking they don't hold. Markings form a **lattice structure** supporting conjunctive (must hold ALL) and disjunctive (must hold ANY in group) combinations. Critically, **markings propagate through data lineage** — when a Transform derives output from a marked dataset, the output automatically inherits the marking.

**Link security uses query-time trimming.** When a user queries Object A's links and Object B is linked but the user lacks permission on Object B, the platform performs security trimming: Object B's properties are **not exposed**. The linked object either appears as a restricted placeholder or is filtered out entirely, depending on configuration. **Link traversal does not grant transitive access** — this is a fundamental security invariant. Aggregations that would include inaccessible linked objects exclude them from counts and metrics.

**AIP enforces the same permission model as human users.** LLM agents inherit the invoking user's permissions — there is no separate "AI user" with elevated privileges. AIP accesses data exclusively through the Ontology API layer, which enforces all markings, RBAC, and PBAC before returning data to the LLM context. There is an additional **whitelist layer**: administrators must explicitly opt-in each Action, Object Type, and Function for AIP use. This creates an effective two-check system: (1) is this resource AIP-enabled? (2) does the invoking user have permission? All AIP agent actions are logged with an AI-initiated flag in the audit trail.

**(c) Key inference:** The strongest gap between Palantir's model and standard database security is **mandatory enforcement that even administrators cannot bypass**. PostgreSQL superusers can bypass RLS. Palantir's markings cannot be circumvented by any user, including platform administrators.

**(d) PostgreSQL equivalent strategy:**

PostgreSQL's Row-Level Security provides a foundation but has critical gaps:

```sql
-- Marking tables
CREATE TABLE markings (marking_id UUID PRIMARY KEY, marking_name TEXT);
CREATE TABLE user_marking_grants (
    user_id TEXT, marking_id UUID REFERENCES markings, 
    granted_purpose TEXT, PRIMARY KEY (user_id, marking_id)
);

-- RLS policy enforcing markings
ALTER TABLE persons ENABLE ROW LEVEL SECURITY;
ALTER TABLE persons FORCE ROW LEVEL SECURITY;
CREATE POLICY marking_policy ON persons FOR SELECT USING (
    row_marking IS NULL OR row_marking IN (
        SELECT marking_id FROM user_marking_grants WHERE user_id = current_user
    )
);

-- Column-level security via views
CREATE VIEW persons_safe AS SELECT id, name, region,
    CASE WHEN EXISTS (SELECT 1 FROM user_marking_grants 
        WHERE user_id = current_user AND marking_id = 'pii-marking-uuid')
    THEN ssn ELSE NULL END AS ssn
FROM persons;
```

**Three critical gaps cannot be closed with PostgreSQL alone:**

- **No mandatory access control bypass prevention** — PostgreSQL superusers and table owners can disable RLS. Mitigation: enforce all access through an application-layer gateway with no direct SQL access; use `FORCE ROW LEVEL SECURITY` on every table.
- **No automatic marking propagation** — when creating derived tables, PostgreSQL does not inherit source permissions. Mitigation: build a custom ETL framework that tracks lineage and applies marking inheritance rules at the application layer.
- **No purpose-based access control** — PostgreSQL has no concept of "why" data is being accessed. Mitigation: implement PBAC entirely in application middleware using session variables (`SET app.access_purpose = 'fraud_investigation'`) that RLS policies can read.

For the AIP equivalent, implement user-context execution via `SET ROLE` for each AI agent call, combined with a whitelist table of AI-accessible resources. Log all AI-initiated queries with a flag in a custom audit table, supplemented by the `pgaudit` extension for comprehensive access logging.

---

## Conclusion: where PostgreSQL wins and where it doesn't

Building a Palantir Ontology equivalent on PostgreSQL is architecturally sound for the European SMB market. **PostgreSQL actually provides stronger guarantees** than Palantir in three areas: ACID transactions with transactional outbox patterns for side effects (Palantir uses async best-effort), versioned schema migrations with rollback (Palantir lacks rollback), and automatic stale-edit detection via CDC triggers (Palantir requires custom pipelines).

The hardest problems to replicate are **mandatory access control that administrators cannot bypass** (fundamental PostgreSQL limitation — mitigate with application-layer enforcement and no direct SQL access), **automatic marking propagation through data lineage** (requires building a custom lineage-tracking ETL framework), and **sub-second search at >50M objects** (requires a companion search engine like Meilisearch or Elasticsearch alongside PostgreSQL). The semantic abstraction layer — mapping properties to columns, maintaining Object Type metadata, generating typed SDKs — is straightforward with PostgreSQL views, a metadata registry, and Prisma for code generation. Focus engineering effort on the security model and search layer, where the gap with Palantir is widest.