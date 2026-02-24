# Engineering decisions behind a Palantir-like ontology layer on PostgreSQL

## Scope and framing assumptions

You already have the primitives and layers. The missing piece is the set of production engineering choices that make those primitives safe to evolve, fast to query, and hard to bypass.

Palantir’s public documentation is unusually explicit about two things that matter for “the HOW”: (a) object indexing is a pipeline orchestrated by a dedicated service (“Funnel”) into “object databases”, and (b) user edits are first-class, with explicit conflict-resolution semantics, schema-migration tooling, and transactional considerations around actions and side effects. citeturn13search8turn18view0turn20view2turn16view2turn16view0

What follows is a question-by-question extraction of documented behaviour, plus tightly-scoped inferences where Palantir is silent, and finally a translation into concrete design decisions for a PostgreSQL-first open-source alternative.

## Schema evolution and versioning

Authoritative source: `https://www.palantir.com/docs/foundry/object-edits/schema-migrations`. citeturn21view0

### How Palantir handles ontology schema changes when the backing schema evolves

Palantir treats certain ontology schema edits as “breaking schema changes” that require an explicit migration choice before the change can be saved. In Object Storage V2 (OSv2), Ontology Manager detects breaking changes and blocks saving until a migration is defined. citeturn21view0

When the change is saved, Palantir explicitly states that a new schema version is created for the object type in the backend and a replacement Funnel batch pipeline is orchestrated to rebuild the object type index. The new version becomes queryable (via OSS and other consumers) once the replacement pipeline completes and the new version is declared fully hydrated by the object databases. citeturn21view0turn18view0

This means schema evolution is coupled to: (a) versioned schema state in backend storage, and (b) a two-pipeline model (live pipeline continues serving; replacement pipeline builds in background; then a cutover). citeturn18view0turn21view0

### Mapping changes like “SAP column rename” without breaking apps

At the object-type property-mapping layer, Palantir supports remapping a property to a different backing column (unlink then map to a new column). This is the practical mechanism you would use when a source system column is renamed or replaced. citeturn11search15

Critically, Palantir’s “breaking changes” list includes “changing the ID of a property that has received user edits” and “deleting a property that has received user edits”, but does not treat display-name/rendition changes as breaking. The implication: a stable property identifier is a contract boundary; remap sources behind it when systems drift. citeturn21view0

### Is there a schema registry, version numbering, and migration tooling?

Palantir exposes schema migration tooling directly in Ontology Manager via a Migrations tab during “Review changes”. It offers predefined migration instructions including: drop edits (property/struct/all), move edits (property or whole type, including rename/replace), cast edits to new types, and revert migration through history. citeturn21view0

There is strong evidence of “schema registry semantics” even if it’s not branded as such:

- Backend schema versions exist per object type and are used to control queryability and hydration boundaries. citeturn21view0turn18view0  
- The public Apply Action API supports passing `sdkPackageRid` and `sdkVersion`, signalling that Palantir can interpret action execution against a versioned, generated schema artefact. citeturn16view1  
- Ontology schema definitions can be exported to a JSON file and re-imported, enabling “schema-as-code” workflows outside the UI. citeturn0search18  
- Ontology changes are described as eventually consistent at the API layer: after creating/updating, APIs may lag briefly. That matters for automation that expects immediate schema visibility. citeturn9search26

### What happens to downstream applications when Object Type properties change?

Palantir is blunt: deleting a property will break any views or applications referencing that property. citeturn11search15  
More broadly, it warns that editing object types and properties can have “application-breaking consequences” that disrupt workflows. citeturn11search7

On the developer side, object properties are code-generated into SDK interfaces: the generated field name uses the “API Name” configured in ontology. Any breaking property change becomes either a compile-time break (missing field) or a runtime semantic change (changed type/value constraints) depending on how you regenerate and deploy SDKs. citeturn5search11turn16view1

Best inference where Palantir is not explicit: the “blocking save until a migration is defined” feature is about preserving correctness of *user edits* and indexed data consistency, not about preventing downstream app compilation failures. For apps, the mitigation is versioned SDKs and disciplined rollout, not automatic refactoring. This inference is supported by the fact that Palantir explicitly calls out app-breaking consequences while focusing its migration framework on edit preservation and index rebuilds. citeturn11search15turn21view0

### What this means for building an equivalent on PostgreSQL

A PostgreSQL-first alternative should implement schema evolution as a first-class workflow, not an afterthought:

You need stable, opaque IDs for object types, properties, links, actions, and value types. Treat display names and even “API names” as mutable aliases, but never use them as the primary key of your internal metadata. Palantir’s “changing the ID of a property with user edits is breaking” is the tell: IDs are the contract. citeturn21view0turn5search11

You need “replacement index pipelines” as a product primitive. In Postgres terms: build a new set of physical indexes/materialised views (or a new partition set) beside the old one, validate hydration completeness, then atomically switch read traffic (metadata pointer flip) once ready. This mirrors Palantir’s replacement Funnel pipeline cutover into hydrated search nodes. citeturn18view0turn21view0

You need migration instructions that are edit-aware: drop edits, move edits (rename/replace), and cast edits across types. If you ship without “move edits”, you will force customers into destructive migrations the moment they rename a field that has been edited operationally. citeturn21view0turn10view1

Finally, you need “schema-as-code” export/import and a versioned client artefact (generated SDK or OpenAPI) with a way to pin action executions to a schema version if you want deterministic CI/CD across staging and production. Palantir’s `sdkPackageRid` and `sdkVersion` parameters are a clear pattern to copy. citeturn16view1turn0search18

## Conflict resolution and data reconciliation

Authoritative source: `https://www.palantir.com/docs/foundry/object-edits/how-edits-applied`. citeturn20view2

### Which wins: source value X or human edit Y?

Palantir explicitly models conflicts between input datasource updates and user edits as something that must be resolved transparently at read time, with an explicit conflict-resolution strategy. citeturn20view2

Strategy 1 (“Apply user edits”, default): final object state is determined by user edits for edited properties, regardless of future datasource updates for those properties. Palantir even describes this as “user edits always win” in the illustrative table. citeturn20view2

Strategy 2 (“Apply most recent value”): user edits are conditionally applied only if the edit timestamp is more recent than a timestamp column from the datasource. This is configured per datasource backing an object type, requires a UTC timestamp-typed property, and can lead to different edited properties on the same object being applied or ignored depending on their relative timestamps. citeturn20view0turn20view2

Deletions are treated specially: deletions are not considered an edit; after deletion, the object is not visible regardless of datasource state; if later recreated, it does not inherit previous edits. citeturn20view2

There is also an important caveat: for “edit-only properties”, user edits always apply regardless of the timestamp strategy. citeturn20view2

### How the “writeback dataset” pattern works mechanically

In OSv2, the action path is: Actions service sends a modification instruction to Funnel; Funnel stores it in a queue with offset tracking; offsets are applied to the live indexed data such that reads after the modification is sent are guaranteed to include the user edits. citeturn10view0turn15search21

Persistence is then handled by indexing pipelines: Funnel’s batch pipeline has an explicit “merge changes” job where “recent user edits coming from Actions” are joined with changelog datasets by primary key and stored in a separate Funnel-owned dataset, which is then converted into index files and hydrated into the object database search nodes. citeturn18view0turn18view1

In OSv1/Phonograph writeback (legacy), Palantir describes a manual-editing cache (Phonograph) plus a separate “writeback dataset” that stores the user-modified version while the source dataset remains unmodified. citeturn10view3turn10view2

In OSv2, materialisations play the role of producing a dataset that reflects “the latest state of each object by combining data from both input datasources and user edits”, but edits do not require a materialised dataset to exist. This is a big architectural shift away from “datasets as the primary writeback artefact” toward “indexes as the primary state, datasets as optional exports”. citeturn10view2turn18view0

### Best inference where documentation still leaves gaps

Palantir is explicit about conflict resolution between datasource updates and user edits, including a configurable “most recent value” strategy, so you do not need to guess the top-level semantics. Where Palantir is less explicit is exactly how conflict-resolution interacts with multi-datasource object types when two datasources provide the same logical property. The docs do say each datasource can have a different strategy and that resolution is determined by the datasource backing the property. citeturn20view2

The practical inference: the reconciliation boundary is not “object-level” but “property mapped to datasource-level”. That is consistent with both the per-datasource configuration and the indexing pipeline’s primary-key join approach. citeturn20view2turn18view0

### What this means for building an equivalent on PostgreSQL

You should implement conflict resolution as a configurable policy, not a hidden behaviour.

Default mode should be “user edits win” because operational workflows need durability of decisions even when source systems backfill or correct records. Palantir’s default confirms this. citeturn20view2

You should also implement “most recent value” as an opt-in strategy, but do it per datasource or per property-group, not as a global toggle. Require a trustworthy UTC timestamp from the source (or computed in pipeline) and compare edit application time against source timestamp exactly as Palantir describes, otherwise you will rebuild a subtly different semantic contract. citeturn20view2

Mechanically in Postgres: store edits as an append-only log keyed by (object_type_id, primary_key, property_id) with metadata (edit_applied_at, action_id, user_id, provenance), then build “resolved state” views/materialised views using either (a) last edit wins per property, or (b) conditional apply if edit_applied_at > source_timestamp. The “merge changes” step Palantir documents is conceptually a join between source change log and edit log. citeturn18view0turn20view2

If you want OSv2-like read-your-writes, you need a low-latency path that updates the queryable state immediately (for example, by writing to a hot table or cache in the same transaction) and a background compaction/materialisation job that persists and optimises storage periodically. Palantir does exactly this: immediate index update plus periodic flushing and six-hour persistence cadence when edits exist. citeturn10view0turn18view0

## Real-time indexing and query performance

Authoritative source: `https://www.palantir.com/docs/foundry/object-indexing/funnel-batch-pipelines` (plus OSv2 backend overview). citeturn18view0turn13search8turn5search15

### What OSv2 storage and indexing actually is

Palantir’s public docs describe a service-oriented architecture:

- Funnel is the microservice orchestrating writes into the ontology. It reads from datasets/restricted views/streams and from user edits, then indexes into object databases. citeturn13search8turn18view0  
- Object databases store indexed object data and are responsible for querying, query computation, indexing, and orchestrating user edits. citeturn5search15turn3search7turn10view0  
- Indexing produces “index files” stored as Funnel-owned datasets and then hydrated onto the disks of OSv2 “database search nodes”. citeturn18view0turn4search8  

Palantir does not name the underlying database engine for OSv2 in the OSv2 docs. However, multiple primary Palantir sources strongly indicate Elasticsearch-like semantics in the ontology indexing layer:

- Struct query semantics are described as “indexed similarly to ElasticSearch object field types”, and arrays can have unintuitive behaviour consistent with Elasticsearch nested/object mappings. citeturn9search17  
- Palantir references an `analyzer.not_analyzed` type class as a way to prevent Elasticsearch tokenisation in ontology search contexts. citeturn9search39  
- OSv2 feature gaps include “custom analyzers”, which is terminology tightly associated with Lucene/Elasticsearch analyzers. citeturn3search3  

Best inference: OSv2’s “canonical data store” for search is either Elasticsearch/Lucene-based or a Palantir-managed derivative that intentionally preserves Elasticsearch-like indexing semantics (analyzers, object field behaviour, tokenisation) while wrapping it in Funnel-managed pipelines and object databases. The “search nodes” language and hydration of index files to local disks is also consistent with a distributed search cluster architecture. citeturn18view0turn4search8turn9search17turn9search39

### How Palantir achieves sub-second search on large graphs

The key architectural decisions visible in docs are: pre-indexing plus constrained traversal.

First, not all properties are indexed: filtering, ordering, and aggregations in object searches only work on properties with a “Searchable” render hint, meaning those properties have been indexed for search. This produces a bounded “search schema” rather than indexing everything. citeturn9search13turn4search0

Second, graph traversal depth is capped for performance in the programmable API: the number of Search Around operations in a single search is limited to 3, and deeper traversals fail at runtime. citeturn5search0

Third, Palantir explicitly combines highly-indexed backend filtering with compute backends for heavier tasks: OSv2 is described as an enhanced indexing format optimised for “Search Arounds” and writeback, with smooth hand-offs to multiple compute backends including parallelised Spark as part of a query. citeturn4search12turn5search8

### Known performance limits surfaced publicly

Some hard limits are stated outright:

- Search Around depth in a single object search is limited to 3. citeturn5search0  
- Structs support up to 10 fields. citeturn9search17  
- Streaming indexing throughput is limited to 2 MB/s per object type (with support escalation if higher is needed). citeturn9search6  
- Index size is “mainly limited” by storage space in object databases; for OSv2 this is the disk space of the search nodes. citeturn4search8turn6search2  
- OSv2 supports low-latency streaming indexing “on the order of seconds or minutes”, but also warns streaming treats each stream as a changelog and out-of-order events can produce incorrect ontology data. citeturn3search11turn6search32  

There are also scale claims: the OSv2 backend overview states improved indexing throughput “on the order of tens of billions of objects for a single object type”. Treat this as a marketing-level ceiling, but it is still an explicit public claim about design intent. citeturn4search15

### What this means for building an equivalent on PostgreSQL

If you try to serve Palantir-like search purely with vanilla relational indexes and ad hoc joins, you will lose on latency and operational complexity. The Palantir pattern to copy is: specialised indexed stores and explicit constraints.

On PostgreSQL, you can still approximate this by implementing a dual index strategy:

- A relational “entity store” optimised for point reads and transactional updates (tables keyed by (object_type_id, pk)).  
- A “search store” optimised for text and faceted filters. In Postgres this likely means a combination of GIN indexes over `jsonb`, `tsvector`, and possibly pg_trgm, plus precomputed denormalised columns for “searchable” properties only. Palantir’s Searchable hint concept is essentially “choose what to index”. citeturn9search13turn4search0  

You should also impose traversal constraints in your API from day one: a hard cap on traversal depth (Palantir uses 3 for Search Around in functions) and explicit pagination and size limits. citeturn5search0turn5search4

Operationally, you need the equivalent of Funnel pipelines: a changelog stage, a merge stage (including recent edits), a build stage that emits search-optimised artefacts, and a hydration/cutover stage. In Postgres terms, that’s (a) change capture, (b) merge into “resolved rows”, (c) build materialised views or index tables, (d) atomically switch read pointers. Palantir’s documentation gives you the blueprint. citeturn18view0turn21view0

Finally, expose throughput limits and backpressure explicitly, especially for streaming ingestion. Palantir documents its streaming throughput limit as a product constraint; you will need your own equivalent and a way to scale it. citeturn9search6turn3search11

## Action transaction model

Authoritative sources: action model and execution docs plus Apply Action API. `https://www.palantir.com/docs/foundry/action-types/overview`, `https://www.palantir.com/docs/foundry/action-types/function-actions-batched-execution`, `https://www.palantir.com/docs/foundry/object-edits/how-edits-applied`, and `https://www.palantir.com/docs/foundry/api/ontologies-v2-resources/actions/apply-action`. citeturn4search14turn16view2turn10view0turn16view1

### Atomicity when actions touch multiple objects and types

Palantir defines an action as “a single transaction” that changes properties of one or more objects based on user-defined logic. citeturn4search14turn11search3

For function-backed actions, Palantir states that when actions are triggered in batches, edits are applied atomically at the end of the action call. This is a direct statement of atomic commit semantics for the set of edits produced by a single action invocation. citeturn16view2turn0search17

Palantir also documents “Ontology entity version control” as necessary to guarantee transactionality and avoid data correctness issues during action application, and describes stale-object conflict behaviour in OSv1 and version checks in OSv2. citeturn10view1

### Isolation and concurrency control

Palantir’s action pipeline uses optimistic concurrency signals:

- In OSv1, the Actions server tracks object versions and OSv1 checks if versions changed, throwing `StaleObject` on conflicts. Palantir notes property-level changes are not checked, which can still trigger stale conflicts. citeturn10view1  
- In OSv2, the Actions server performs version checks before posting user edits to Funnel, but on a limited subset compared to OSv1. citeturn10view1  
- In OSv2, edits to objects or links are visible immediately after action completion via the public API, which implies the system provides read-after-write consistency at least at the object database layer for completed actions. citeturn16view1turn10view0  

### Side effects and guarantees

Palantir distinguishes two side-effect ordering models for webhooks:

- Writeback webhooks run before ontology edits; if a writeback webhook fails, “no other changes will be made” in Foundry. This provides some transactionality between Foundry and the external system, but Palantir explicitly warns the reverse failure mode remains possible: the external request may succeed but ontology changes could fail. Only one webhook can be configured as writeback. citeturn16view0turn14view0  
- Side-effect webhooks run after object changes, can execute in no particular order, and may run after the end user sees a success message. They are recommended for “best-effort” notifications or multi-system writeback. citeturn16view0turn15search0  

Notifications have explicit failure handling around permissions: with “require all users to have permissions” (default), if recipients lack access an error is shown and “no data will be edited and no notifications will be sent”; with “require any user”, the action can succeed and only authorised recipients will receive notifications. citeturn14view1turn1search32

For observability, Palantir’s action metrics classifies “side effect failure” explicitly, implying side effects are monitored as a first-class operational concern. citeturn17view0

For automation-triggered executions, Palantir’s Automate effects follow at-least-once execution semantics, and it explicitly recommends designing idempotent operations to handle duplicates. This becomes relevant if your action side effects are invoked via automation pipelines. citeturn14view4turn1search7

### What this means for building an equivalent on PostgreSQL

You should model “action commit” and “side effect execution” as separate concerns with explicit semantics:

Inside your ontology store, support atomic commits across multiple object edits in one action. In Postgres, this can be a single transaction that writes to your edit log and/or resolved state tables, plus emits an action record for auditing. Palantir’s “edits applied atomically at the end of the action call” is a clear contract to match. citeturn16view2turn4search14

Use optimistic concurrency by default: accept an object version token (or ETag) on action submission and fail with a stale-object error when the version is behind. Palantir’s explicit `StaleObject` conflict behaviour tells you users will need a retry/refresh UX. citeturn10view1turn15search21

For side effects, implement the same two-tier model:

- “Writeback side effects” inside the transaction boundary before committing internal writes, with the explicit caveat that distributed transactions are not fully solvable without heavyweight coordination. Palantir is transparent that writeback webhooks only provide one direction of atomicity. citeturn16view0  
- “Best-effort side effects” after commit, asynchronous, retried, and explicitly idempotent. If you also provide an automation engine, it should be at-least-once and you must document this loudly. citeturn14view4turn16view0  

Finally, expose monitoring: action run history, side-effect failure categories, and P95 latencies are not optional once you become an operational system of record. Palantir makes these visible in ontology manager. citeturn17view0

## Security model internals

Authoritative sources: object permissioning and PBAC/AIP security docs. `https://www.palantir.com/docs/foundry/object-permissioning/object-security-policies`, `https://www.palantir.com/purpose-based-access-controls/`, `https://www.palantir.com/docs/foundry/security/markings`, `https://www.palantir.com/docs/foundry/object-permissioning/configuring-rv-access-controls`, `https://www.palantir.com/docs/foundry/administration/configure-scoped-sessions`, and `https://www.palantir.com/docs/foundry/logic/overview`. citeturn1search27turn2search1turn1search4turn2search32turn2search7turn2search33

### Granularity of markings and ontology access control

Palantir uses “Markings” as mandatory access controls at the resource level: access is binary and a user must satisfy all markings applied to access a resource. citeturn1search4turn1search33

Within the ontology, Palantir documents object-level and property-level security:

- Object security policies are built by adding a “mandatory control property” where each row carries a set of markings required to access that object instance. citeturn1search27turn2search22  
- Property security policies can further restrict specific properties (columns) with markings (for example, PII properties). citeturn1search27turn1search23  

Row-level controls are also supported through restricted views: restricted views “enable row-level access controls for ontology data” and can be used to back object types for finer-grained access than dataset-wide permissions. citeturn2search32turn2search18

Classification-based access controls (CBAC) exist as a separate mandatory control model, described as used for sensitive government information and not enabled by default. citeturn2search6turn1search0

Best inference on “per-cell” granularity: Palantir’s ontology permissioning documentation clearly supports per-object (row) and per-property controls, and also supports restricted-view row-level filters. It does not publicly document true per-cell mandatory controls inside an object beyond what you can model as properties themselves. The closest analogue is dataset-level marking propagation and CBAC in the broader platform, but ontology-specific docs focus on object and property policy. citeturn1search27turn2search32turn2search6

### Markings and visibility across links

Palantir’s public docs do not give a crisp, UI-level truth table for: “I can see object A but not object B, but there is a link between them; what is shown?”. What is documented is that ontology authorisation covers both objects and links as data entities, and restricted views are used to control which rows are visible. citeturn1search30turn2search32

A strong, defensible inference based on how Palantir treats partial visibility in multi-datasource objects: when a user cannot view data from some datasources, the unseen values show as `null` during action validation, and permission checks are scoped to the datasources backing the edited properties. This implies the system is designed to avoid leaking unauthorised information by omission/nulling rather than exposing partial identifiers. Applying the same principle to links suggests traversals return only linked objects that pass the caller’s load/view permissions, rather than revealing hidden-object identities. citeturn12view3turn1search30

If you need product certainty, the right approach for an open-source alternative is to specify and test a strict non-leak contract: link existence and link counts should be treated as sensitive metadata and filtered accordingly unless explicitly permitted.

### PBAC and how it affects access enforcement

Palantir’s PBAC (Purpose-Based Access Controls) is described as tightly integrated into Foundry’s access control system to introduce structure to data access decisions and enable governance teams to enforce rules. citeturn2search1

A concrete mechanism exposed in docs is “scoped sessions”: an administrator can configure sessions to be siloed to the purpose a user is currently working on to reduce “cross-pollination”. citeturn2search7

### AIP and ontology permissions when LLM agents execute actions

Palantir states that AIP Logic is built on the same security model as the rest of the platform, including user and function permissions, and that these controls grant an LLM access only to what is necessary for the task. citeturn2search33turn2search12

For actions executed by automation (a useful proxy for “non-human actor execution”), Palantir documents that actions run on behalf of the owner of the automation; i.e., they execute with a specific user’s permissions and will stop if that account is disabled. citeturn15search16turn14view4

Best inference: Palantir’s model is “no special AI permission plane”; AI-driven execution is permissioned via the same primitives as humans (user identity, function permissions, action submission criteria, and session scoping), with additional governance tooling (PBAC/scoped sessions) to constrain context. This inference is consistent with the explicit “same rigorous security model” claim and the “run on behalf of a specific user” automation design. citeturn2search33turn15search16turn2search7

### What this means for building an equivalent on PostgreSQL

Security cannot be bolted on. You need three orthogonal layers:

You need resource-level mandatory access controls (markings) and inheritance rules, because European SMBs still need hard boundaries for HR, finance, M&A, and regulated data. Palantir’s markings are binary and conjunctive; copy that simplicity. citeturn1search4turn1search33

You need ontology-level access controls that operate at least at per-object and per-property granularity. Concretely: implement row-level security (RLS) keyed by mandatory-control tags for object instances, plus column-level suppression for protected properties, plus restricted-view-like policies for dynamic row predicates. Palantir’s mandatory control property and restricted views give you the pattern. citeturn1search27turn2search32

You need execution-context controls for AI and automation: run actions as an identity (human user or service principal) and scope every request to an explicit “purpose” context that gates which object sets and actions are valid, similar to scoped sessions. This is the only credible way to prevent AI tooling from becoming a cross-domain data exfiltration channel. citeturn2search7turn2search33turn15search16

Finally, define link-visibility semantics explicitly and test them. If you do not, you will accidentally leak sensitive relationships through traversal results, edge counts, or “exists” queries.

## Practical synthesis for a PostgreSQL-native open alternative

Palantir’s docs reveal a consistent playbook: separate metadata from physical storage, separate “live queryable state” from “persistent artefacts”, and make evolution workflows explicit.

If you are targeting European SMBs on PostgreSQL, the winning architecture is not “copy Foundry”; it is “copy the contracts”:

Implement stable ontology IDs and treat names as aliases. This is the backbone of safe schema evolution. citeturn21view0turn5search11

Implement a Funnel-like orchestrator as a logical component even if it is not a microservice day one: it should own changelog generation, merge-with-edits, build search artefacts, and cutover. Palantir’s batch pipeline stages map directly. citeturn18view0turn13search8

Implement user edits as an append-only log with explicit conflict resolution strategies, defaulting to “user edits win” and supporting “most recent value” against a source timestamp. Do not improvise this: Palantir’s semantics are now public and customers will expect similar behaviour once you position as an alternative. citeturn20view2turn18view0

Implement actions as atomic commits internally, with optimistic concurrency, and two classes of side effects: transactional “writeback” and best-effort “side effect”. Anything else will produce either data corruption or operational dead-ends when integrating external systems. citeturn16view2turn10view1turn16view0

Expose constraints as product behaviour: searchable property hints, traversal depth caps, throughput limits, and at-least-once execution semantics for automations. Palantir documents these limits because they are necessary to reason about production behaviour. citeturn9search13turn5search0turn9search6turn14view4