# PALANTIR — FULL RESEARCH RECAP

**Complete knowledge base for AI context — Product, Delivery, Commercial, Market**

Compiled February 2026 from 50+ research documents, patent filings, earnings calls, AIPCon transcripts, SEC filings (S-1, 10-K), UK G-Cloud pricing, and former employee interviews across 6 research phases.

**Structure:**
- Part 1 (A): Architecture & Technology — Ontology, data integration, pipelines, Workshop, AIP, OSDK, security
- Part 2 (B): Delivery Method — FDE model, pre-sales, bootcamp, pilot, expand, scale
- Part 3 (C): Commercial Engine — Financials, pricing, competitive landscape, lock-in, Palantir Mafia, risks
- Part 4: Market Context — TAM, EU regulations, French AI sovereignty, SMB gap, e-invoicing
- Part 5: GTM Synthesis — Go-to-market strategy, implementation methodology, consulting comparison, replication blueprint
- Part 6: Errata & Corrections — 10 critical data corrections
- Appendix: Visual Atlas — Quick reference with all key diagrams described

**Key FY2025 Metrics:**
| Metric | Value |
|--------|-------|
| Revenue | $4.475B (+56% YoY) |
| Net Dollar Retention | 139% (Q4 2025) |
| Customers | 954 (+34% YoY) |
| Expansion Multiple | 56x ($100K → $5.6M) |
| GAAP Gross Margin | 84% |
| Revenue per Employee | $1.01M |
| Bootcamps Conducted | 1,300+ (mid-2024) |
| FCF Margin | 82% |
| Market Cap | ~$313B |

---


# ═══════════════════════════════════════════════════════════════
# PART 1: THE PRODUCT — ARCHITECTURE & TECHNOLOGY
# ═══════════════════════════════════════════════════════════════

Now I have the complete file. Let me produce the full structured markdown extraction.

---

# MEGA DOCUMENT -- PART 1: THE PRODUCT
## What Palantir Actually Built and How It Works

**Part 1 of 4**

# The Product: What Palantir Built

A complete technical anatomy of Palantir's platform stack -- four platforms, one Ontology, 400+ connectors, 50+ widgets, and the AI layer that ties it all together. Every claim sourced from official documentation, patent filings, or confirmed practitioner accounts.

---

## 1.1 The Four Platforms

Palantir is not a single product. It is a stack of four interconnected platforms, each built in a different era to solve a different problem, all converging on a single abstraction: the Ontology. Understanding how these four layers relate is the key to understanding why the system is so difficult to replicate.

### [Diagram: Palantir's four-platform stack]

- **AIP** -- 2023 -- AI Layer
  - Tool-use architecture | 50+ LLMs | Orchestrator Selector | Agent Studio
  - GPT-4o/5, Claude 3-4.5, Llama 3-4, Gemini 2-3, Mistral, Grok | BYOM

- **FOUNDRY** -- 2016 -- Commercial Data OS
  - 150+ microservices | Spark + Flink | Cloud-agnostic (Iceberg, Parquet)
  - Kubernetes/Rubix | MMDP | Virtual Tables | Pipeline Builder | Workshop | OSDK

- **GOTHAM** -- 2008 -- Intelligence DNA
  - EAV/CR model | AtlasDB + RevDB + Horizon | Raptor federated search
  - 6 apps: Graph, Gaia, Browser, Object Explorer, Dossier, Inbox | REST APIs

- **APOLLO** -- Continuous Delivery -- The Invisible Platform
  - Constraint-based pull model | Hub-spoke mesh | 360K+ deployments/month
  - FedRAMP High | IL5/IL6 | CMMC | 3.5 min avg deploy | 4.9 min rollback

- **ONTOLOGY** -- spans every platform (vertical bar connecting all four layers)

*Palantir's four-platform stack. Apollo deploys all three upper layers. The Ontology is the shared abstraction that spans every platform.*

---

### Gotham (2008)

Palantir's original intelligence platform, built for the IC (Intelligence Community). Gotham introduced the core idea: an **Entity-Attribute-Value / Component-Relationship (EAV/CR)** data model that could represent any real-world entity without schema changes.

#### Storage Layer
- **AtlasDB** -- Distributed KV store with snapshot isolation and MVCC transactions
- **RevDB** -- Revision database tracking full object history
- **Horizon** -- Time-series and event storage engine

#### 6 Core Applications
- **Graph** -- Network visualization and link analysis (the flagship)
- **Gaia** -- Geospatial mapping and temporal analysis
- **Browser** -- Full-text search across all objects
- **Object Explorer** -- Structured entity navigation
- **Dossier** -- Report builder combining multiple views
- **Inbox** -- Alert triage and task management

#### Integration
- **Raptor** -- Federated search across disconnected Gotham instances
- REST APIs for programmatic access
- Plugin system for custom analyzers

---

### Foundry (2016)

The commercial data operating system. Foundry took Gotham's ontology concept and rebuilt it for enterprise-scale data operations with a modern cloud-native architecture.

#### Architecture
- **150+ microservices** running on Kubernetes (via Rubix, Palantir's hardened K8s distribution)
- Compute engines: **Apache Spark** (batch), **Apache Flink** (streaming), custom engines for specialized workloads
- **Cloud-agnostic** storage: Apache Iceberg table format, Parquet columnar files
- **Multimodal Data Plane (MMDP)** -- unified interface for structured, unstructured, and streaming data

#### Key Capabilities
- **Virtual Tables** -- federated query against Snowflake, Databricks, BigQuery without data movement
- **400+ data connectors** for ingestion
- **Pipeline Builder** -- visual DAG-based ETL
- **Workshop** -- low-code operational app builder
- **Code Repositories** -- Git-backed IDE for Python/Java/SQL transforms
- **OSDK** -- type-safe SDKs generated from the Ontology

---

### AIP (2023)

The AI layer built on top of the Ontology. AIP's critical design decision: **LLMs never touch the Ontology directly**. They interact through a tool-use architecture with explicitly scoped permissions.

#### Three-Layer Architecture (from patent EP4443310A1)
- **Orchestrator Selector** -- receives prompts, routes to the correct service orchestrator
- **Service Orchestrators** -- format requests for specific data processing services
- **Data Processing Services** -- execute operations (search, filter, visualize, traverse, write)

#### Model Support
- **50+ models**: GPT-4o through GPT-5, Claude 3 through 4.5, Llama 3-4, Gemini 2-3, Mistral, Grok
- **BYOM (Bring Your Own Model)** support for custom fine-tuned models
- Role-based profiles with four components: Knowledge Bases, Functions, Plugins, Templates

---

### Apollo (CD Platform)

The continuous delivery infrastructure that makes everything else possible. Apollo deploys all Palantir software, including itself, across every environment -- from AWS to air-gapped SCIFs.

#### Architecture (from patent US10263845B2)
- **Constraint-based pull model** -- nodes pull updates matching their constraints, not pushed centrally
- **Hub-spoke mesh** -- spokes can bootstrap from peer spokes, not just the hub
- Desired-state reconciliation (Kubernetes-like convergence loop)
- Pre-caching of deployment artifacts before maintenance windows

#### Performance
- **360,000+ deployments/month** across all environments
- **3.5 minutes** average deployment time
- **4.9 minutes** average rollback time
- Canary deployments via "tracks" -- progressive rollout to user subsets

#### Certifications
- FedRAMP High, IL5/IL6, CMMC
- Spokes operate autonomously when disconnected from hub

---

> **Key Insight:** The four platforms are not independent products. They share the Ontology as a universal data model. An object defined in Foundry is the same object that AIP reasons about, that Workshop displays, that OSDK exposes via API, and that Apollo deploys to the edge. This shared abstraction is the architectural moat.

### Key Metrics

| Metric | Value |
|--------|-------|
| Deployments per month | 360K+ |
| Foundry microservices | 150+ |
| Supported LLM models | 50+ |
| Data connectors | 400+ |

---

## 1.2 The Ontology -- The Core Innovation

The Ontology is Palantir's single most important abstraction. It is not a database, not a schema, not a data catalog. It is a **runtime-editable metadata overlay** that maps real-world entities onto tabular datasets. Patent US20200293561A1 reveals that objects are **materialized views over tabular data** -- the Ontology never stores data itself; it maps to datasets by specifying which exact rows and columns store each property value.

> **Critical Distinction:** The Ontology is a metadata layer, not a database. When you create an "Employee" object type, you are not creating a new table. You are declaring a schema that maps to existing columns in one or more backing datasets. The Ontology is a *view*, not a *store*.

### [Diagram: Ontology Architecture: 6 Primitives, 3 Layers]

#### SEMANTIC LAYER (WHAT)
Entities, properties, relationships

- **Object Types** -- Schema of real-world entities. String PK, properties, backing datasource, writeback dataset
- **Properties** -- 17+ base types: Boolean, Date, Decimal, GeoPoint, Vector, TimeSeries, Structs (1-10 fields, depth 1)
- **Link Types** -- Named business semantics: one-to-one, one-to-many, many-to-many
- **Interfaces** -- Abstract types for polymorphism. Not backed by datasets

#### KINETIC LAYER (HOW)
Actions, Functions, writeback rules

- **Action Types** -- Permissible mutations -- the "verbs" of the Ontology. Typed params | Validation rules | Side effects | Role-based perms. Function-backed for complex logic | Transactional commit
- **Functions** -- Code-based logic native to the Ontology. TypeScript v2 or Python | Operate on objects via interfaces. Sandboxed execution | Polyglot (C, Java, Python, Ruby, JS)

#### DYNAMIC LAYER (GUARDRAILS)
Security, governance, real-time indexing, automation

- **OMS** -- Ontology Management Service. Stores schemas, type definitions
- **Object Storage V2** -- Canonical store + Object Data Funnel. Vector clock conflict resolution
- **Object Set Service** -- Read path for object queries. ElasticSearch indexing
- **Permissions** -- View = perm on object type AND backing datasource. MDOs: column-wise access | Actions: perms on type + resources
- **Schema Evolution** -- Non-breaking: add types/properties. Breaking: change data type/PK (up to 500 migrations/op)

*The Ontology's three-layer architecture with six primitives. The Semantic Layer defines WHAT exists, the Kinetic Layer defines HOW it can be changed, and the Dynamic Layer enforces GUARDRAILS.*

---

### The 6 Ontology Primitives

#### Object Types
The schema definition of a real-world entity or event. Both "JFK" and "LHR" are objects of an "Airport" object type.

- **Primary key** must be a string type, no exceptions
- Backed by one or more datasets -- creating an object type does not create a new table
- Includes a writeback dataset for receiving user mutations
- Object type ID cannot be modified after first deploy
- URIs identify types (RDF/semantic-web heritage from patent US9589014B2)

> **Dataset Analogy:** Object Type = Dataset schema, Object = Row, Property = Column, Link = Join

#### Properties
Characteristics of an object type. 17+ base types with struct and validation support.

**17+ Base Types:**
- Boolean, Byte, Date, Decimal, Double, Float
- GeoPoint, GeoShape, Integer, Long, Short, String
- Timestamp, Vector, TimeSeries, MediaRef

**Composite Types:**
- **Structs** -- 1-10 fields, depth of 1 (no nesting). Uses ElasticSearch object field indexing
- **Value Types** -- regex validation, range constraints, enum enforcement
- Shared properties can be reused across multiple object types

#### Link Types
Relationships between two object types with named business semantics.

- **Cardinalities**: one-to-one, one-to-many, many-to-many
- API name on plural side must be plural: `employee.subordinates.all()`
- Multiple links between same types need distinct names (e.g., "Manager" and "Direct Report")
- Links enable traversal in queries and applications without SQL joins
- Patent US10061828B2: link reversal during cross-ontology replication

#### Action Types
Permissible mutations -- the "verbs" of the Ontology. Actions represent what users can *do* to data.

- **Typed parameters** with required/optional flags and data type constraints
- **Validation rules** (submission criteria) checked before execution
- **Side effects** -- notifications, webhooks, downstream triggers
- **Role-based permissions** -- who can execute and on which objects
- Function-backed actions for complex business logic
- All actions commit **transactionally** to the Ontology

#### Interfaces
Abstract types enabling polymorphism across object types.

- **Not backed by datasets** -- cannot be instantiated directly
- Define shape and capabilities that multiple object types can implement
- Functions can accept any object type implementing a given interface
- Enable building applications that work across object types without hardcoding
- TypeScript v2 struct types are defined using interfaces

#### Functions
Code-based logic integrated natively into the Ontology.

- **Languages**: TypeScript v2 or Python
- Operate on objects via interfaces (input and output interface object sets)
- Sandboxed execution in isolated processing engine instances
- Patent US11842171B2: polyglot support (C, Java, Python, Ruby, JS) with resource limits
- Stored in a separate "function registry" enabling reuse across applications
- Auto-generated APIs regenerated when ontology changes

---

### Backend Architecture

#### How the Ontology Actually Works Under the Hood

Derived from patent US20200293561A1 ("Object Platform for Datasets"), the Ontology's backend comprises five engines:

| Engine | Role | Details |
|--------|------|---------|
| **Datastore** | Backing data storage | Contains actual data instances in potentially heterogeneous formats and locations |
| **Definition Engine (OMS)** | Schema management | Stores object definitions: properties, types, relationships. Editable at runtime. |
| **Association Engine** | Object-to-data mapping | Maps which exact database rows and columns store each property value |
| **Cache Engine** | Materialized views | Loads data as object properties into cache for object-oriented operations without parsing entire datasets |
| **Interface Engine** | APIs | Exposes Object Search API, Object Load API, Object Modify API. Auto-regenerated on schema changes. |

#### Conflict Resolution
Uses **vector clocks** (a distributed systems technique) with commit logs storing timestamps and user/security metadata. Conflicts resolve through configurable rules based on modification timing, origin, and user security levels. This confirms the object platform is designed for multi-writer distributed scenarios.

#### Schema Evolution
- **Non-breaking changes**: Add new object types, add new properties, add new link types. No migration required.
- **Breaking changes**: Change data type, change primary key, remove properties. Requires migration.
- Migration system supports up to **500 migrations per operation**
- Ontology migration across stacks (patent US10754822B2) is fundamentally an **identifier translation exercise** -- rewiring dataset references, not copying data

---

### Permission Model

Access control is dual-gated: you need permission on *both* the Ontology schema and the underlying data.

- **View an object**: requires permission on the object type AND the backing datasource
- **MDOs (Multi-Dataset Objects)**: support column-wise access -- different users can see different properties of the same object based on which backing datasets they can access
- **Execute an action**: requires permission on the action type PLUS all resources the action will edit
- Permission enforcement happens at the API layer, not the data layer (patent US11842171B2)
- **Transitive permission revocation**: revoking access to a source dataset automatically revokes access to all derived datasets through the lineage chain

---

## 1.3 Data Integration

Getting data into Foundry is the first step of every deployment. Palantir's Data Connection module provides 400+ connectors spanning databases, SaaS applications, cloud storage, enterprise systems, and streaming platforms, with three distinct connection architectures.

### [Diagram: Data Integration Architecture]

**SOURCES:**
- Databases (JDBC)
- SAP (SLT CDC)
- SaaS / ERP APIs
- Kafka / Kinesis
- Cloud Storage
- REST / Webhooks
- Media / Files

**CONNECTORS:**
- **Direct (Foundry Worker)** -- Cloud-side processing. No customer-hosted agent
- **Agent Proxy** -- Lightweight tunnel on Linux. Compute stays on Foundry
- **Agent Worker (legacy)** -- Compute on customer host. File-based syncs only

**INGESTION:**
- **Batch (CDC)** -- Debezium-based
- **Streaming** -- Kafka / Kinesis / Pub/Sub
- **Push (REST)** -- Webhook + API endpoints
- **Media** -- Images, docs, video

**FOUNDRY DATASETS:**
- **Immutable Datasets** -- Versioned transactions, 3-phase commit protocol, Delta encoding for history
- **Ontology** -- Object Types + Link Types mapped from datasets

**SECURITY:**
- Credentials: AES-256-GCM encryption at rest
- Dataset transactions: immutable, versioned, 3-phase protocol
- Build catalog: full traceability of inputs + code per output
- Private Link support: AWS, Azure, GCP

*End-to-end data integration flow: sources connect through three architectures, ingest via four modes, land as immutable versioned datasets, and map to the Ontology.*

---

### Connector Categories

#### Databases
- JDBC connectors: PostgreSQL, MySQL, MariaDB, Oracle, SQL Server, Db2, Informix, SQLite, Sybase, Vertica, Athena, Hive
- Custom JDBC connector for any JDBC-compatible source
- Connection optimization guidance for performance tuning

#### Cloud & SaaS
- Cloud warehouses: Snowflake, BigQuery, Databricks (via Virtual Tables)
- Cloud storage: S3, Azure Blob, GCS
- SaaS: Salesforce, ServiceNow, Workday, Jira, Slack
- ERP: SAP (certified add-on), NetSuite, D365

#### Streaming & Events
- Apache Kafka, AWS Kinesis, Google Pub/Sub
- Webhooks for event-driven push
- Listeners for Jira, Slack, Pub/Sub
- Streaming syncs for real-time flows

---

### SAP Certified Add-On (Deep Dive)

Palantir's SAP connector is not a generic JDBC integration. It is an **SAP Certified Add-On** installed directly on the SAP application layer via SAINT (SAP Add-On Installation Tool), developed in partnership with Diskover Limited.

- **Supported systems**: S/4HANA, ECC, Business Warehouse, SLT Replication Server
- **Three components**: `PALANTIR` (shared objects, required), `PALCONN` (connector objects/services), `PALODATA` (optional, SLT OData APIs)
- **Change Data Capture**: integrates with SAP SLT using database triggers for efficient incremental replication
- Uses native SAP security policies and application logic -- not a bypass

---

### Dataset Transaction Model (from patent US9946738B2)

Every dataset in Foundry follows a git-like immutable, versioned model. Data is **never overwritten**.

#### Three-Phase Commit Protocol

| Phase | Operation | Details |
|-------|-----------|---------|
| **1. Initiation** | `start transaction` | Client requests transaction opening, receives unique transaction ID |
| **2. Write** | Multiple `write` commands | Data writes to containers in data lake with acknowledgment |
| **3. Commit** | `commit` | System assigns commit ID, atomically updates transaction metadata |

Transaction entries record: dataset name, transaction ID, start timestamp, committed flag, commit ID, and container references. Delta encoding stores version differences to reduce storage while maintaining full historical access.

---

## 1.4 Pipeline Builder & Code Repos

Foundry provides two complementary approaches to building data pipelines: a visual DAG canvas (Pipeline Builder) for no-code/low-code users, and Git-backed Code Repositories for engineers who need full PySpark/Pandas/Java/SQL power.

### [Diagram: Pipeline Builder: Visual DAG Canvas]

**Input nodes:** Dataset Input, Streaming Input, External Sync

**Transform nodes:** Filter / Sort, Join (7 types), Aggregate, Pivot / Reshape, Geospatial, 500+ Functions

**Output nodes:** Dataset Output, Object Types, Link Types, Virtual Tables

**70+ TRANSFORM NODES:**
- **Data Manipulation:** Filter, Sort, Select, Drop, Rename, Normalize, Top rows, Drop duplicates
- **Joins:** Inner, Left, Right, Outer, Cross, Anti, Semi, Mapping, KNN
- **Geospatial:** Distance, Intersection, KNN geo-join
- **Reshape:** Pivot, Unpivot, Explode, Flatten
- **File Parsing:** CSV, JSON, Excel, XML, Shapefile
- **Advanced:** Pattern mining, Split on condition

*Pipeline Builder's visual DAG canvas with 70+ transform nodes, supporting inputs from datasets, streams, and external syncs, outputting to datasets, Ontology entities, and virtual tables.*

---

### Expression System: 500+ Built-in Functions

| Category | Functions |
|----------|-----------|
| **Arithmetic** | Add, Multiply, Divide, Modulo, Absolute, Rounding, Trigonometric |
| **String** | Concatenation, Upper/Lower, Substring, Regex matching, String length |
| **Array** | Array concat, distinct, sort, filter, union/intersection |
| **Date/Time** | Current timestamp, Date sequence, Epoch conversion, Part extraction, Date arithmetic |
| **Geospatial** | Create GeoPoint, Geometry buffer, Haversine distance, Coordinate conversion |
| **Advanced** | Parse JSON, Cipher encrypt, Text to embeddings (LLM), Case/When, Coalesce |

---

### Branching & Versioning
- **Copy-on-write semantics** (patent US20210149857A1): test branches share input snapshots with master, only logic is copied
- Three views: Edit, Proposals, History
- Merge replaces master's logic + updates output references
- Test branches modify transforms independently without affecting production
- Parameterized pipelines for reusable, configurable workflows

### Code Repositories
- **Git-backed IDE** within Foundry
- Languages: Python (PySpark), Java, SQL, Mesa
- `@transform` decorator: explicit control over inputs/outputs
- `@transform_df`: convenience decorator returning DataFrames directly
- `@incremental`: process only new data with semantic versioning
- Multi-input, multi-output transforms supported

---

### Data Lineage (Monocle)

Every `@transform` execution records input-output relationships as directed edges in a global dependency graph. This extends to Pipeline Builder pipelines, data syncs, and Ontology mappings -- everything that reads or writes a dataset creates a lineage edge.

- **Global DAG**: zoomable, pannable graph of all Foundry resources
- **Expand upstream/downstream**: single or full expansion to raw sources or final outputs
- **Column-level analysis**: find datasets with a given column, frequent columns histogram
- **Build triggering**: trigger builds for out-of-date datasets directly from the lineage view
- **Monocle** extends lineage to cover actions, applications, AIP Logic functions, and Workshop modules

---

### Scheduling & Triggers

#### Time Triggers
- Standard Unix cron expressions (5 fields + timezone)
- GUI for simple schedules
- **LLM-powered** natural language schedule generation

#### Event Triggers
- Dataset-update triggers
- New-data triggers
- Job-succeeded triggers

#### Compound Triggers
- **AND**: "all of these triggers"
- **OR**: "any of these triggers"
- Combine time + event for predictable SLAs

---

> **Patent US20250094439A1 -- Custom IL for LLM-to-Pipeline:** Palantir built a proprietary intermediate language specifically for LLM-to-pipeline translation, **2x to 100x more token-efficient** than JSON. ANTLR parser generators convert LLM outputs back into executable pipeline code. The prompt architecture includes "mistake context instructions" -- examples of errors to avoid -- a concrete few-shot error prevention technique.

---

## 1.5 Workshop -- Low-Code App Builder

Workshop is Palantir's primary application development surface. It is a **type-safe widget composition system** (patent US11500620B2) where the Ontology acts as the type system. Every widget operates on Ontology objects -- there is no concept of binding a widget directly to a raw dataset table.

### [Diagram: Workshop: 50+ Widgets Across 6 Categories]

#### CORE DISPLAY
- Object Table -- the workhorse
- Object List -- scrollable cards
- Object View -- detail page
- Property List -- key-value
- Links -- relationship graph
- Object Set Title -- "47 Flights"
- Data Freshness, Edit History, Action Log

#### VISUALIZATION
- Chart XY -- bar, line, scatter
- Pie Chart -- pie / donut
- Vega Chart -- full Vega-Lite
- Gantt Chart -- scheduling
- Map (MapboxGL) -- geospatial
- Pivot Table, Metric Card, Timeline
- Stepper, Status Tracker, Markdown

#### FILTERING & INPUT
- Filter List -- most feature-rich
- Object Dropdown -- single select
- String Selector -- dropdown/radio
- Date/Time Picker
- Text Input, Numeric Input
- Exploration Filter Pills
- Search Bar, Prominent Term, User Select

#### AIP WIDGETS
- AIP Agent -- chat + 4 tool types
- AIP Analyst -- analytics focus
- AIP Generated Content -- LLM output
- AIP Interactive -- operational AI

#### EVENTS & ACTIONS
- Button Group -- primary trigger
- Inline Action -- auto-gen forms
- Media Uploader
- Audio Recorder, Comments, Tabs

#### EMBEDDING
- Iframe -- bidirectional comms
- Embedded Module -- var mapping
- Custom Widgets -- React/TS
- 50 params, 50 events limit per widget set

#### VARIABLE SYSTEM -- The Central Nervous System
- 12 types: Object Set, Filter, String, Numeric, Boolean, Date, Timestamp, GeoPoint, GeoShape, Array, Struct, TimeSeries
- 6 definition mechanisms: Static, Function, Aggregation, Object Property, Object Set Definition, Variable Transformation

*Workshop's 50+ widgets organized into 6 categories, all connected through the variable system which provides lazy computation and visual dependency graphing.*

---

### Variable System

Variables are the central nervous system of every Workshop module. They control how data moves between widgets, how user interactions propagate, and how application state is maintained.

#### 12 Variable Types

| Type | Description |
|------|-------------|
| Object Set | Most commonly used -- one or more objects |
| Object Set Filter | Property/value pairs for narrowing sets |
| String | Text content |
| Numeric | Integers and floats |
| Boolean | True/false |
| Date / Timestamp | Date and timestamp values |
| GeoPoint / GeoShape | Geographic data |
| Array | Arrays of any base type |
| Struct | Composite key-value maps |
| TimeSeries Set | Time series from single objects |

#### 6 Definition Mechanisms

| Mechanism | How it works |
|-----------|-------------|
| **Static** | Manually set a fixed value |
| **Function** | Computed by TypeScript Function on Objects |
| **Aggregation** | Derived from object set (count, sum, avg) |
| **Object Property** | Single object's property value |
| **Object Set Def** | Object type + filters + link traversals |
| **Transformation** | Pipeline of operations on other variables |

#### Computation Behavior
- **Lazy evaluation in view mode** -- variables only recompute when displayed by a visible widget
- Three recompute modes: **Automatic** (on upstream change), **Event-triggered** (on explicit event), **Load + Event** (on module load + events)
- Visual dependency graph in editor shows how variables connect to widgets and to each other

---

### Layout Hierarchy
Workshop applications follow a strict composition hierarchy:
- **Module** -- top-level container
- **Header** -- persistent navigation bar
- **Pages** -- distinct views within a module
- **Sections** -- content groups within a page
- **Widgets / Layouts** -- UI components within sections
- **Overlays** -- modal dialogs triggered by events

### Event System
Events drive interactivity between widgets:
- **Open / Close overlay** -- modal dialogs
- **Switch page** -- navigation within module
- **Reset / Set variable** -- state mutations
- **Stream LLM response** -- progressive AI output
- Events can be chained: button click triggers action, action success sets variable, variable change refreshes widget

---

> **Workshop Design Constraints:** 200K export limit per object set. Approximately 5 primary actions per screen. 30-40% whitespace recommended. Maximum 10 visible components at a time. **All data MUST be Ontology Object Types** -- you cannot bind to raw datasets in Workshop. This is the fundamental constraint that forces organizations to build and maintain the Ontology.

---

## 1.6 Application Building Spectrum

Palantir offers five distinct application-building surfaces. Choosing the right one is a critical architectural decision. The following comparison covers every dimension that matters in practice.

| Dimension | Workshop | Slate | Contour | Quiver | OSDK |
|-----------|----------|-------|---------|--------|------|
| **Data source** | Ontology Objects only | Ontology + raw datasets | Raw datasets (tabular) | Ontology Objects | Ontology via generated SDK |
| **Code required** | None (TS Functions for advanced) | HTML, CSS, JS (Handlebars) | None | None | Full (React/TS/Python/Java) |
| **Writeback** | Full (Actions, Inline, Cell-level) | Yes, via Ontology | No writeback | No writeback | Full (Actions API) |
| **Scale** | Enterprise operational workflows | Pixel-perfect bespoke apps | Millions+ rows | ~50K rows aggregation limit | Unlimited (external hosting) |
| **Mobile** | Native responsive layouts | Manual CSS responsive | No | No | Full (custom build) |
| **AIP integration** | Full (4 AIP widgets) | Limited (via Functions + Iframe) | Limited | AIP Generate for cards | Full (API-level access) |
| **Maintenance** | Lower (Palantir manages widgets) | Higher (custom code) | Low | Low | Full ownership |
| **Best for** | Inbox/triage, COPs, task management, operational dashboards | Pixel-perfect dashboards, legacy apps with HTML control | Ad-hoc exploration, large dataset analysis | Object analytics, time series, sensor data | External-facing apps, custom frameworks, CI/CD control |

> **Decision Rule:** Start with Workshop unless you have a specific reason not to. It covers ~90% of use cases, requires no code, and Palantir manages widget upgrades. Use Slate only for pixel-perfect custom UIs. Use Contour for ad-hoc data exploration on raw tables. Use Quiver for time-series analytics on Ontology objects. Use OSDK for external-facing apps or when you need full framework control.

---

## 1.7 AIP Deep Dive

AIP (Artificial Intelligence Platform) is Palantir's AI layer. Its defining architectural choice is that **LLMs never touch the Ontology directly**. Instead, they interact through a tool-use architecture where every operation is explicitly scoped, permission-bounded, and auditable. This is not just a chatbot bolted onto a data platform -- it is a multi-agent orchestration system with four levels of guardrails.

### [Diagram: AIP Architecture: Tool-Use with Guardrails]

**User Prompt** --> **ORCHESTRATOR SELECTOR** (LLM determines which service to route to)

**PROFILE (US20240419658A1):** Knowledge Bases + Functions + Plugins + Templates (injected into Orchestrator Selector)

**Service Orchestrators:**
- Search Orchestrator
- Ontology Orchestrator
- Action Orchestrator

**DATA PROCESSING SERVICES:** Query Objects | Apply Actions | Call Function | Calculator

**4 GUARDRAIL LEVELS:**
- **L1: Constrained Actions** -- Action Types define the ONLY mutations possible
- **L2: Tool Scoping** -- Agents see ONLY whitelisted tools
- **L3: Permission-Bounded** -- AI executes with the user's actual permissions
- **L4: Staging (Scenarios)** -- Git branch for data: fork, test, then apply

**ONTOLOGY (never touched directly by LLMs)**

*AIP's three-layer routing architecture with four guardrail levels. The LLM acts as a router, not a direct data accessor. All mutations flow through typed Action Types with the user's actual permissions.*

---

### AIP Logic -- Visual No-Code AI Workflows

AIP Logic provides a visual workflow builder for orchestrating AI-powered operations without writing code.

#### Workflow Node Types

| Node | Purpose | Details |
|------|---------|---------|
| **Use LLM** | Call an LLM with tools | 4 tool types: Query Objects, Apply Actions, Call Function, Calculator |
| **Apply Action** | Execute an Ontology action | Creates, modifies, or deletes objects via typed Action Types |
| **Execute Function** | Run an Ontology Function | TypeScript or Python logic on objects |
| **Conditional** | Branching logic | If/else based on variable values or LLM output |
| **Loop** | Iteration | Iterate over object sets or array variables |
| **Create Variable** | Store intermediate results | Persist values between workflow steps |

---

### Agent Studio -- Explicitly Scoped AI Agents

Agent Studio is where you configure which tools an AI agent can access. The key principle: **only whitelisted tools are accessible**. An agent cannot discover or use tools that were not explicitly granted.

- **Action tools** -- execute Ontology actions (create, modify, delete objects)
- **Object query tools** -- search and retrieve objects with property filters
- **Function tools** -- execute TypeScript/Python functions registered in the Ontology
- Each tool is configured with specific object types and access scopes
- Agents can read and write Workshop variables, enabling interaction with the surrounding application

---

### Scenarios -- Git Branch for Operational Data

Scenarios are the fourth guardrail level: a **fork of live Ontology data** where you can apply actions, run ML models, and see projections without affecting production.

- Create a scenario from any point in time as a branch of the current data state
- Apply actions within the scenario -- changes are isolated from live data
- Run ML models and optimization algorithms on the forked data
- Compare scenario outcomes side-by-side before choosing which to apply
- Merge scenario changes back to production if approved
- Used for what-if analysis: "What if we reroute 50 trucks?" or "What if we hire 20 more nurses?"

---

> **Patent US20240346388A1 -- Security-Aware AI:** Palantir trains **separate LLM models per security classification level**, not just filtering outputs. A base model trains on low-permission data, then continues training on higher-permission data (additive), or separate models per tier are combined via an ensemble at inference. Incoming requests are routed to the appropriate model based on the user's permission level. This prevents data leakage through LLM inference -- a fundamentally more secure approach than RAG-based post-generation filtering.

---

## 1.8 OSDK -- Ontology SDK

The Ontology SDK enables external applications to programmatically query and modify the Ontology. It is a **code-generated, type-safe client library** tailored to your specific ontology entities. When the ontology changes, you regenerate the SDK and the new types flow through to all consuming applications.

### [Diagram: OSDK: Code-Generated Type-Safe Access]

**Ontology** (Object Types, Actions, Links, Functions) --> codegen --> **Developer Console** (Select entities, generate SDK package) --> **Type-Safe SDK** (TypeScript, Python, Java, OpenAPI) --> **Your Application** (React, Node, Django, Spring Boot, scripts)

#### CORE API SURFACE

| Operation | Methods |
|-----------|---------|
| **Query** | fetchPage(), fetchOne(), asyncIter() |
| **Filter** | .where({ prop: { $eq, $gt, $startsWith } }) |
| **Aggregate** | $count, $sum, $avg, $groupBy |
| **Links** | obj.$link.relation.fetchPage() |
| **Actions** | applyAction(), batchApplyAction(), $validateOnly |
| **Functions** | executeFunction({ params }) |

*OSDK flow: Ontology definitions are code-generated into type-safe SDKs (TypeScript, Python, Java, or OpenAPI), enabling external applications to query, filter, aggregate, traverse links, and execute actions.*

---

### TypeScript OSDK

```typescript
// Setup
import { createClient } from "@osdk/client";
import { createPublicOauthClient } from "@osdk/oauth";

const auth = createPublicOauthClient(
  CLIENT_ID, FOUNDRY_URL, "http://localhost:8080/callback"
);
const client = createClient(STACK_URL, ONTOLOGY_RID, auth);

// Query with filters
const tasks = await client(Task)
  .where({
    projectId: { $eq: "proj-abc" },
    status: { $startsWith: "in_" }
  })
  .fetchPage({
    $orderBy: { dueDate: "desc" },
    $pageSize: 50
  });

// Traverse links
const emp = await client(Employee).fetchOne("emp-42");
const depts = await emp.$link.department.fetchPage();

// Execute action
await client(CreateEmployee).applyAction({
  name: "Alice", role: "Engineer"
});
```

### Python OSDK

```python
# Query objects
page = client.ontology.objects.Employee.page(
    page_size=30, page_token=None
)

# Filter with operators
results = client.ontology.objects.Employee.where(
    Employee.object_type.department == "Engineering"
)

# Boolean composition
results = client.ontology.objects.Employee.where(
    ~Employee.object_type.id.is_null() &
    (Employee.object_type.role == "Manager")
)

# Aggregation
grouped = client.ontology.objects.Employee.where(
    ~Employee.object_type.name.is_null()
).group_by(
    Employee.object_type.department.exact()
).count().compute()
```

### Key Metrics

| Metric | Value |
|--------|-------|
| API gateway requests/week | 1B+ |
| Authentication standard | OAuth 2.0 |
| Languages | 3 (TS, Python, Java) |
| Source | Open on GitHub (osdk-ts) |

---

## 1.9 Security & Infrastructure

Security is not a feature bolted onto Palantir's stack -- it is a structural property embedded in every layer. From Rubix (hardened Kubernetes) to tamper-resistant audit logging, from 5-layer progressive redaction to cross-classification sharing with cryptographic verification, the security architecture is what makes Palantir deployable in environments where no other commercial software can operate.

### [Diagram: Security Architecture: Defense in Depth]

**INFRASTRUCTURE: RUBIX (Hardened Kubernetes)**
- 48h node recycling
- Cilium network segmentation
- FedRAMP High / IL5 / IL6 / CMMC
- Air-gapped mesh operations

**DATA SHARING: Namespace-Based Permissions**
- Metadata permission changes (not copies)
- Transitive revocation through lineage chain
- Column-level + row-level automatic filtering

**5-LAYER PROGRESSIVE REDACTION (Patent US9857960B1)**
1. Access Control
2. Provenance
3. Object Type
4. Property Type
5. Media Type

**CROSS-CLASSIFICATION SHARING (Patent US9081975B2)**
- Cryptographic digest verification | Asymmetric translation rules | Shortest-path translation | Origin classification stack | CBAC + RBAC + no-classification hybrid

**TAMPER-RESISTANT AUDIT LOGGING (Patent US11593317B2)**
- Dual-datastore (immutable + accessible) | 50KB chunked blocks | Content-addressable storage (SHA-1/SHA-512) | Keystroke logging | External hash comparison

*Five defense layers: hardened infrastructure, namespace-based data sharing, 5-level progressive redaction, cross-classification sharing, and tamper-resistant audit logging.*

---

### Rubix: Hardened Kubernetes

Palantir does not run stock Kubernetes. Rubix is a hardened distribution with security measures that go far beyond default K8s.

- **48-hour node recycling** -- every node is terminated and replaced every 48 hours, preventing persistent compromises
- **Cilium network segmentation** -- eBPF-based network policies for microsecond-level traffic control between pods
- Certifications: **FedRAMP High, IL5, IL6, CMMC**
- Supports air-gapped operations with autonomous spoke nodes
- All inter-service communication encrypted in transit

### 5-Layer Progressive Redaction

Patent US9857960B1 describes five criteria applied *in order* before any data leaves a system:

1. **Access control classifications** -- security clearance-based filtering
2. **Provenance** -- information source tracking (who contributed this data?)
3. **Data object type** -- category-based filtering (e.g., SIGINT vs HUMINT)
4. **Data object property type** -- specific attribute filtering (e.g., redact "phone number" but keep "country")
5. **Media type** -- file format/data type filtering (e.g., strip images but keep text)

Graph exports include serialized graph state + ontology mappings + GUIDs for cross-system entity resolution.

### Cross-Classification Sharing

Patent US9081975B2 enables data sharing between organizations with *different* security classification schemes (e.g., CIA and NSA).

- **Three mapping approaches**: one-to-one, one-to-many (parent-child type preservation), and drop lists (types blocked until mapped)
- **Round-trip stability check**: data is transformed to importing schema, then back. If stable across multiple round-trips, export proceeds
- **Cryptographic digest**: update packets include a hash verifying both sites use compatible mappings
- **Origin classification stack**: every boundary crossing is logged as a provenance chain
- Supports CBAC, RBAC, and classification-free databases in the same topology

### Tamper-Resistant Audit Logging

Patent US11593317B2 describes an audit system using **content-addressable storage** (similar to git's object store).

- **Dual-datastore architecture**: immutable append-only repository + customer-accessible system log
- **50KB chunked blocks**: activity encrypted, compressed, then hashed (SHA-1 or SHA-512)
- **Hash as address**: hash codes function as block addresses for retrieval
- **Multi-layer detection**: intrusion detection, kernel security logging, keystroke capture, system call auditing
- **External hash comparison**: logs pushed externally for cross-system tamper detection
- Neither Palantir nor the customer can modify logs without detection

---

### Data Sharing Model (Patent US20230306000A1)

Foundry's sharing operates by **updating namespace markings** associated with datasets, not by moving data. This is fundamentally a metadata permission change, not a data copy.

| Mechanism | How It Works | Impact |
|-----------|-------------|--------|
| **Namespace markings** | Modify which workspaces can access a dataset by updating its namespace metadata | Zero data movement, instant access change |
| **Workflow enforcement** | Users must provide legal justification; owners must explicitly approve | No bypassing structured approval processes |
| **Transitive revocation** | Denying upstream access automatically revokes all downstream derived datasets | Access cascades through entire lineage chain |
| **Data minimization** | Column-level and row-level filtering applied automatically based on scope rules | Users only see what their role permits |

---

> **Why This Matters for Replication:** The security architecture is not an add-on -- it is woven into the data model (namespace markings), the lineage system (transitive revocation), the API layer (permission enforcement), and the infrastructure (Rubix, Apollo mesh). You cannot extract the "product features" without also extracting the security model. Any replication attempt must treat security as a first-class architectural concern from day zero, not as a compliance checkbox to address later.

---

## SUMMARY -- Part 1 Key Takeaways

### The Ontology Is Everything
It is not a database. It is a **runtime-editable metadata overlay** with 6 primitives, 3 layers, 5 backend engines, vector clock conflict resolution, and a dual-gated permission model. Every other feature -- Workshop, AIP, OSDK -- depends on it.

### AI Through Guardrails
AIP's architecture ensures LLMs **never touch the Ontology directly**. Four guardrail levels (constrained actions, tool scoping, permission-bounded execution, scenarios) make AI safe for operational use. The LLM is a router, not a data accessor.

### Security Is Structural
From 5-layer progressive redaction to cross-classification sharing with cryptographic digests, from 48h node recycling to content-addressable audit logs -- security is not a feature, it is the **architecture itself**.

### Summary Metrics

| Metric | Value |
|--------|-------|
| Platforms | 4 (Gotham, Foundry, AIP, Apollo) |
| Ontology primitives | 6 |
| Workshop widgets | 50+ |
| Data connectors | 400+ |
| Pipeline functions | 500+ |
| Property base types | 17+ |

# ═══════════════════════════════════════════════════════════════
# PART 2: THE DELIVERY METHOD
# ═══════════════════════════════════════════════════════════════

# Part 2: The Delivery Method

The FDE model, pre-sales qualification, AIP Bootcamp, 90-day pilot, expand, scale, and the delivery economics.

---

## Section 2.1 -- The FDE Model

### FDE Pod Structure -- Deployment Team per Client

- 3-5 people per pod
- Auftragstaktik doctrine: field teams own all execution decisions

**Central Pod: CLIENT POD** -- 3-5 people

**DELTA (FDE / FDSE) -- Technical Deployment:**

- **Forward Deployed Engineer** -- Median age ~25 | Top CS + philosophy/math
- **FDE (Ontology Builder)** -- Data modeling, pipeline construction
- **FDSE (Software Engineer)** -- Platform extensions, custom tooling
- **FDIE (Infrastructure)** -- Cloud, networking, security

**ECHO (DS / AE) -- Strategy & Relationship:**

- **Deployment Strategist (DS)** -- Ex-McKinsey/BCG/Bain | C-level mgmt
- **Account Executive (AE)** -- Deal structure, commercial terms

**AUFTRAGSTAKTIK DOCTRINE:** Senior leaders set objectives. Field teams own execution.

- Acquire phase: 4-5 FDEs/client
- Scale phase: 0-1 FDEs/client

*Fig 2.1 -- FDE Pod Structure showing Delta (technical) and Echo (strategic) roles per client deployment*

---

### FDE = "Forward Deployed Engineer" -- Not a Consultant

The FDE is the atomic unit of Palantir's delivery model. Every other process -- Bootcamp, Pilot, Expand, Scale -- revolves around deploying and eventually withdrawing FDEs. The distinction is critical: an FDE is not a consultant, not a solutions engineer, not a professional services body.

> **Barry McCardel** (former FDE, now CEO of Hex): *"A startup CTO embedded in someone else's organization."*

FDEs operate under **Auftragstaktik** -- the Prussian military doctrine of mission command. Senior leadership at Palantir HQ sets high-level strategic objectives (e.g., "win this account," "prove value in supply chain"). All execution decisions are delegated entirely to the field team. There is no project management office, no Gantt chart from HQ, no weekly status call to a VP. The pod decides what to build, when to build it, and how to present it.

This creates **Darwinistic competition** among solutions: different pods at different clients may develop competing approaches to similar problems. The approaches that work get folded back into the platform as product primitives. The ones that fail disappear.

**What FDEs Do NOT Produce:**
No PowerPoint decks. No requirements documents. No formal roadmaps. No business cases. No SOWs. The deliverable is always **working software on real data**. If it cannot be demonstrated live, it does not exist in the FDE worldview.

---

### Delta (FDE / FDSE) -- The Technical Core

**Median age: ~25.** Recruited from top CS programs, but disproportionately from philosophy, math, and physics backgrounds. Palantir values decomposition thinking and first-principles reasoning over framework knowledge.

#### Compensation Bands (2024-2025)

| Level | Base Salary | Total Comp (incl. equity) | Notes |
|---|---|---|---|
| Entry FDE | $135K - $200K | $171K - $415K | Fresh grad, 0-2 years |
| Senior FDE | $160K - $220K | $300K - $550K | 2-5 years, pod lead capability |
| Staff FDE | $200K - $260K | $630K+ | Technical director, multi-pod |

**CONFIRMED** Glassdoor / Levels.fyi aggregation

#### Hiring

- **Acceptance rate: 1-2%** -- comparable to elite special forces selection rates
- **Decomposition interview**: candidates are given an ambiguous real-world problem (e.g., "How would you model the supply chain of a hospital during a pandemic?") and must break it into data objects, relationships, and actions in real time
- No LeetCode-style algorithm questions -- the interview tests *how you think about messy problems*, not whether you can invert a binary tree
- Cultural filter: high agency, comfort with ambiguity, willingness to travel 4-5 days/week in Acquire phase

#### Glassdoor Reality Check

- **3.9/5** -- Overall Rating
- **2.7/5** -- Work-Life Balance
- **4.2/5** -- Compensation

> **Anonymous FDE on Glassdoor**: *"You will not be doing real engineering work. You're configuring a platform and writing glue code. But you will learn more about how enterprises actually work in 6 months than most engineers learn in a career."*

**Travel:** Heavy during Acquire phase -- 4-5 days/week on-site at client. Decreases to 2-3 days in Expand, near-zero in Scale as the platform matures and client self-serves.

---

### Echo (Deployment Strategist) -- The Strategic Layer

Deployment Strategists are typically recruited from **McKinsey, BCG, Bain, and Goldman Sachs**. Their job is not to sell -- it is to **shape the deal**, manage the C-level relationship, map the political landscape, and ensure the FDE pod is solving the right problem for the right stakeholder at the right time.

- **Political cartography**: DS maps every stakeholder (sponsor, champion, blocker, neutral) before a single line of code is written
- **Narrative control**: DS frames every demo, every executive readout, every expansion pitch in the language the client's leadership uses
- **Deal architecture**: DS structures contracts to maximize expansion potential -- short initial terms, clear success metrics, expansion triggers built into the SOW
- **Triage authority**: When a pod has 10 possible use cases, the DS decides which 2-3 will create the most political capital

**Delta + Echo Symbiosis:**
The Delta builds. The Echo strategizes. Neither can succeed without the other. A brilliant technical demo to the wrong audience is wasted. A perfectly positioned narrative with a broken prototype is worse than nothing. The pod structure forces tight coupling between technical execution and strategic positioning.

---

### FDE Work as R&D, Not Services

> **Barry McCardel**: *"Every bespoke solution is a potential product primitive."*

This is one of Palantir's most important accounting and strategic choices: **FDE work is classified as R&D in financials, not as professional services revenue**. This is not merely an accounting preference -- it reflects the actual workflow:

1. FDE builds a bespoke solution for Client A's supply chain problem
2. The approach works. The pod documents the pattern
3. Palantir's platform team generalizes it into a reusable module
4. The module ships to 50 other clients as a platform feature

Examples of FDE-originated features that became platform primitives: **Object Explorer**, **Contour** (the analytics tool), several **Workshop widget types**, and the initial **AIP Logic** patterns for supply chain optimization.

#### Onboarding Reading List

New FDEs receive a curated reading list that signals the intellectual culture Palantir cultivates:

| Book | Author | Why It Matters |
|---|---|---|
| *Impro* | Keith Johnstone | Improvisation, status dynamics, reading a room -- core DS/FDE skill for stakeholder discovery |
| *The Looming Tower* | Lawrence Wright | Intelligence failures, institutional silos -- the exact problems Palantir was founded to solve |
| *Interviewing Users* | Steve Portigal | Ethnographic research methods for understanding actual workflows vs. documented processes |
| *Getting Things Done* | David Allen | Personal productivity system -- FDEs juggle 10-20 parallel workstreams at a client |
| *Principles* | Ray Dalio | Radical transparency, meritocratic decision-making -- Palantir's internal operating system |

---

## Section 2.2 -- Pre-Sales & Qualification

### Qualification Funnel -- From First Touch to Bootcamp

**Layer 1: ACQUISITION CHANNELS**
- Inbound: AIPCon, content, media
- Outbound: targeted enterprise
- Partners: Accenture (2,000+)
- ~60% filtered

**Layer 2: ICP FILTER -- 8 "Bootcamp-Ready" Criteria**
- Budget authority | Data maturity | Exec sponsor | Clear pain | Tech readiness | Timeline | Strategic fit | Scale potential
- ~40% filtered

**Layer 3: SCOPING CALLS (3-5 calls, 60-90 min each)**
- Use case alignment | Data landscape | Stakeholder mapping | "Goldilocks zone" targeting
- ~25% filtered

**Layer 4: PRE-BOOTCAMP PREPARATION (2-4 weeks)**
- 5 workstreams: Data | Pre-construction | Use cases | Legal | "Art of the Possible" demo

**Layer 5: AIP BOOTCAMP (5 days)**
- ~5/day globally | FREE for client
- 22% convert in 90 days
- 1,400+ bootcamps by Q3 2024
- Cost: $12K-$36K each

*Fig 2.2 -- Pre-sales qualification funnel showing progressive filtering from initial contact to bootcamp entry*

---

### Acquisition Channels

**Inbound:**
- **AIPCon events** -- 3 conferences in 2024, thousands of attendees. Tampa General signed a **$50M, 7-year deal** at AIPCon 3
- **Content & media** -- Demo Day videos, YouTube channel, Shyam Sankar's blog posts
- **Word of mouth** -- FDE alumni network (Hex, Anduril, Scale AI founders are all ex-Palantir)

**Outbound:**
- **Targeted enterprise prospecting** -- AE identifies companies matching the ICP
- **Executive referrals** -- Palantir board members and advisors facilitate introductions
- **Government channels** -- IDIQ vehicles, GSA Schedule, UK G-Cloud (GBP 150K/person/quarter)

**Partners:**
- **Accenture**: 2,000+ trained professionals, largest SI partner
- **Deloitte**: Government and commercial consulting overlay
- **AWS, Azure, GCP**: Marketplace listings and co-sell motions

---

### Ideal Customer Profile -- 8 "Bootcamp-Ready" Criteria

Palantir qualifies prospects against a strict ICP before committing to a bootcamp. The criteria define the **"Goldilocks zone"** -- organizations that are sophisticated enough to benefit but not so mature that they have already built their own data platform.

| # | Criterion | What It Means | Disqualification Signal |
|---|---|---|---|
| 1 | **Budget Authority** | Sponsor can authorize $100K-$500K without board approval | Multi-year budget committee required for any purchase |
| 2 | **Data Maturity** | Has structured data in databases, not just spreadsheets | All data in Excel files emailed between departments |
| 3 | **Executive Sponsor** | C-suite or VP-level champion who will attend bootcamp | No executive willing to commit time |
| 4 | **Clear Pain Point** | "Hair on fire" problem with quantifiable cost | Vague interest in "AI strategy" with no specific problem |
| 5 | **Technical Readiness** | Has APIs, databases, or at minimum a data warehouse | No IT team, no cloud infrastructure, no data engineering |
| 6 | **Timeline Pressure** | External deadline or competitive threat creating urgency | "We're exploring options for next year's budget cycle" |
| 7 | **Strategic Alignment** | Problem maps to Palantir's core strengths (supply chain, operations, defense) | Pure marketing analytics or consumer app use case |
| 8 | **Scalable Potential** | Initial use case can expand to 5-10+ use cases across departments | One-off project with no expansion path |

**ESTIMATED** Synthesized from multiple source descriptions of bootcamp qualification criteria

**The "Goldilocks Zone":**
Palantir avoids two extremes: (1) companies too small or immature to benefit (under ~$500M revenue, no data infrastructure), and (2) companies so large and sophisticated they have already built competing internal platforms (FAANG, top-tier banks with 1,000+ data engineers). The sweet spot is **$1B-$50B revenue companies with real data but poor data integration** -- they have the pain, the data, and the budget, but not the internal capability to solve it.

---

### Scoping Call Process

**3-5 calls, 60-90 minutes each**, conducted over 2-4 weeks. The scoping process is deliberately rigorous -- Palantir invests significant pre-sales effort because a failed bootcamp is worse than no bootcamp (it poisons the relationship and wastes FDE capacity).

#### Scoping Call Sequence

| Call | Focus | Palantir Attendees | Client Attendees |
|---|---|---|---|
| 1 | Problem definition, initial data landscape | DS + AE | Exec sponsor + 1-2 business leads |
| 2 | Technical deep-dive: data sources, infrastructure | FDE + FDIE | IT/data engineering leads |
| 3 | Use case prioritization, success metrics | DS + FDE | Business leads + analytics team |
| 4-5 | Legal, security, logistics, bootcamp scheduling | Full pod + legal | Procurement, security, IT ops |

---

## Section 2.3 -- AIP Bootcamp -- 5 Days

### Top-Line Metrics

- **1,400+** -- Bootcamps by Q3 2024
- **~5/day** -- Running Globally
- **FREE** -- Cost to Client
- **$12-36K** -- Cost to Palantir Each

### AIP Bootcamp -- 5-Day Timeline with Deliverables

**DAY 1:**
- Executive Framing
- AI intuition building
- Use case alignment
- "Art of the Possible" demo on client's OWN data
- Deliverable: Vision doc
- 5-20 stakeholders present

**DAY 2:**
- First Vertical Slice
- Build first working prototype
- Connect real data sources
- Create ontology objects
- Build basic Workshop app
- Deliverable: Live prototype -- End-to-end on real data

**DAY 3:**
- AIP Logic Integration
- "Strongest emotional reaction" moment
- AI agents on the ontology with guardrails + HITL
- Deliverable: AI-powered app -- The "magic" moment

**DAY 4:**
- Stress Testing
- Edge cases & exceptions
- Scale testing
- User acceptance testing
- Polish & refinement
- Deliverable: Hardened app -- Production-ready quality

**DAY 5:**
- Executive Readout
- ROI presentation
- Conversion pitch
- Next steps proposal
- Proof of Value scope
- Deliverable: ROI deck

**PRE-BOOTCAMP PREPARATION (2-4 Weeks Before):**

1. **Data Workstream** -- Source inventory, access credentials, sample extracts
2. **Pre-construction** -- 5-10 object types ready, thin ingestion pipeline
3. **Use Case Selection** -- Prioritized by impact + feasibility in 5 days
4. **Legal & Logistics** -- NDA, data agreement, room booking, invites
5. **"Art of the Possible"** -- Demo environment built, starter ontology ready

**Post-bootcamp:**
- 48h package delivery
- Sandbox access for client team
- Proof of Value scoping (8-12 weeks)
- ~22% conversion rate within 90 days

*Fig 2.3 -- AIP Bootcamp 5-day timeline showing day-by-day progression, pre-bootcamp preparation workstreams, and post-bootcamp follow-up cadence*

---

### Bootcamp Team Composition

**Palantir Side:**

| Role | Count | Function |
|---|---|---|
| Deployment Strategist (DS) | 1 | Leads the engagement, manages executives |
| FDE / FDSE | 2-3 | Builds the prototype, configures ontology |
| Account Executive (AE) | 1 | Commercial relationship, deal structure |
| FDIE (Infrastructure) | 0-1 | Environment setup, data connectivity |
| Specialist | 0-1 | Domain expert if needed (e.g., healthcare, defense) |

**Client Side:**
- **5-20 stakeholders** (8-12 typical)
- Executive sponsor (must attend Day 1 and Day 5)
- Business process owners (2-4)
- Data/IT representatives (2-3)
- End users who will use the tool (2-5)
- Optional: procurement, legal, security

**Client Participation is Non-Negotiable:**
A bootcamp where client stakeholders disengage after Day 1 is a failed bootcamp. The DS manages attendance ruthlessly -- the executive sponsor must see Day 3's "magic moment" and Day 5's readout to convert.

---

### Bootcamp Volume Growth

| Period | Cumulative Bootcamps | Run Rate | Key Milestone |
|---|---|---|---|
| Mid-2023 | ~50 | ~2-3/week | Initial launch of AIP bootcamp format |
| Q4 2023 | ~230 | ~15/week | Ryan Taylor: "reoriented our go-to-market" |
| Q1 2024 | ~560 | ~25/week | Karp: "overfilled... like a rock concert" |
| Q2 2024 | ~915 | ~25-30/week | International expansion of bootcamp format |
| Q3 2024 | 1,400+ | ~25-30/week (~5/day) | Conversion engine at full velocity |

**CONFIRMED** Earnings calls, investor presentations

**Economics of the Free Bootcamp:**
Each bootcamp costs Palantir **$12,000-$36,000** in direct costs (FDE/DS time, travel, infrastructure). At ~1,400 bootcamps by Q3 2024, that is **$16.8M-$50.4M in total bootcamp investment**. With a ~22% conversion rate and median pilot ACV of $250K-$350K, the math works: ~308 conversions x ~$300K = ~$92M in first-year pilot revenue generated. The bootcamp is a loss-leader with a clear payback.

---

### Day-by-Day Operational Detail

#### D1 -- Executive Framing + AI Intuition

- **Morning**: Executive-level presentation on "what AI can actually do today" -- not theoretical, grounded in concrete examples from similar industries
- **Midday**: Use case alignment session. DS facilitates. 3-5 candidate use cases narrowed to 1-2 for the bootcamp build
- **Afternoon**: **"Art of the Possible" demo** -- pre-built on the client's own data (from pre-bootcamp prep). This is the first "wow" moment. Stakeholders see their own data, their own terminology, their own workflows reflected in Palantir's platform
- **Outcome**: Shared understanding of what will be built in Days 2-4. Executive buy-in to the chosen use case

#### D2 -- First Vertical Slice

- **Morning**: FDE team connects real data sources live. This is not a demo on synthetic data -- it is production data flowing through Foundry pipelines
- **Midday**: Create ontology objects (5-10 types), define relationships, build the first transforms
- **Afternoon**: Build a basic Workshop application -- the first screen a user will interact with. By end of Day 2, there is a **working end-to-end prototype**
- **Outcome**: Something clickable, something demonstrable, something that uses real data. Not a mockup. Not a wireframe. *Working software.*

#### D3 -- AIP Logic Integration -- The "Magic Moment"

- **Morning**: Integrate AIP Logic -- AI agents that operate on the ontology. Show LLM-powered recommendations, anomaly detection, or automated decision support
- **Midday**: Demonstrate guardrails and human-in-the-loop (HITL) controls. This addresses the #1 executive fear: "will the AI do something dangerous?"
- **Afternoon**: This is the **"strongest emotional reaction" moment**. When a VP of Supply Chain sees an AI agent correctly identify a disruption pattern that took their team 3 weeks to find manually -- and it did it in seconds -- the deal is effectively made
- **Outcome**: Emotional conviction. The prototype is no longer hypothetical. It is real. It works. The executive sponsor becomes an internal champion

#### D4 -- Stress Testing + Polish

- **Morning**: Edge cases and exception handling. What happens when data is missing? When volumes spike? When users input unexpected values?
- **Midday**: Scale testing with larger data volumes. Performance tuning
- **Afternoon**: UI polish, workflow refinement, user acceptance testing with end users. The prototype must look and feel like a production tool, not a hack
- **Outcome**: A hardened prototype that can withstand executive scrutiny and skeptical questioning on Day 5

#### D5 -- Executive Readout + Conversion Pitch

- **Morning**: DS and FDE prepare the executive readout. ROI quantification based on what was built and demonstrated
- **Midday**: **Executive readout** -- live demo of the working prototype to the full C-suite/senior leadership. Not slides. Live software on live data
- **Afternoon**: Next steps proposal. Proof of Value scope (8-12 weeks), team requirements, budget estimate. The DS presents a clear path from bootcamp to production
- **Outcome**: Decision to proceed (or not). If yes: 48-hour package delivery, sandbox access, follow-up cadence begins within the week

---

## Section 2.4 -- Pilot -- 90 Days (Acquire Phase)

### Pilot Economics -- Deliberately Unprofitable

- **$600K** -- Avg Acquire Revenue (S-1)
- **-$65.4M** -- Total Acquire Cohort Loss
- **-43%** -- Contribution Margin (Acquire)

The 90-day pilot is an **investment, not a revenue event**. Palantir deliberately prices pilots at $100K-$500K -- below cost -- because the objective is not to profit on the pilot but to demonstrate value so compelling that the client expands to $1M-$5M+ within 12-24 months.

> **Colin Anderson** (President): Palantir's model is *"only financially sustainable for seven-figure contracts and above."* The pilot exists to prove the path to seven figures.

| Phase | ACV Range | Term | Contribution Margin |
|---|---|---|---|
| Pilot (Acquire) | **$100K - $500K** | 3-6 months | **-43%** |
| Platform (Expand) | $500K - $2M | 12 months | -43% to +35% |
| Enterprise (Scale) | $2M - $10M+ | Multi-year | **+55%+** |

---

### 90-Day Pilot -- 4 Overlapping Phases (Gantt)

- **Phase 1 -- Discovery** (W1-3): 10-30 interviews | Stakeholder mapping
- **Phase 2 -- Ontology** (W2-6): 15-40 sources identified | 3-10 connected | Pipeline build
- **Phase 3 -- Build** (W4-10): 3-10 apps | 5-15 dashboards | 10-30 automated pipelines
- **Phase 4 -- Handoff** (W8-12): 3-tier training | Go-live | FDE withdrawal plan

*Fig 2.4 -- 90-day pilot Gantt chart showing four overlapping phases: Discovery, Ontology & Integration, Actions/Security/Apps, and Training & Handoff*

---

### Phase 1 -- Discovery (Weeks 1-3)

The first 3 weeks are ethnographic fieldwork, not requirements gathering. FDEs and DSs embed themselves in the client's operation to understand **how work actually happens** -- not how the org chart says it should happen.

#### Stakeholder Mapping

- **10-30 interviews in the first 2 weeks.** Order of meeting matters -- the DS choreographs introductions to build trust sequentially
- Map every stakeholder: sponsor, champion, blocker, neutral, influencer
- Identify the **real decision-makers** (often not the people with the fanciest titles)

> **Sarah Constantin** (former FDE): *"Win the hearts of front-line workers... squeeze out opponents in the middle."* The strategy is bottom-up + top-down simultaneously, bypassing middle management skeptics.

#### The Impro Framework

Drawn from Keith Johnstone's *Impro* (on the onboarding reading list), FDEs are taught to **"arrive empowered to discover, not just deliver."** This means:

- Ask open-ended questions, not leading ones
- Observe status dynamics in meetings -- who defers to whom?
- Match the communication style of each stakeholder (technical depth for engineers, business outcomes for executives)
- Never assume the documented process is the real process

**SOPs Are Corporate Fiction:**
A core FDE principle: **Standard Operating Procedures describe how work should happen, not how it does happen.** The gap between documented process and actual practice is where the highest-value use cases live. An FDE who builds to the SOP will build the wrong thing.

#### Ethnographic Approach

> **Zoe Scaman**: *"Become wallpaper -- present enough to observe, invisible enough not to trigger the immune system."*

FDEs shadow front-line workers: warehouse operators, nurses, supply chain planners, intelligence analysts. They watch screen-by-screen what the workers actually do, noting every workaround, every manual step, every "we do this because the system doesn't let us do that" moment.

#### 5 Fundamental Discovery Questions

| # | Question | What It Reveals |
|---|---|---|
| 1 | "Walk me through what you did yesterday, step by step." | Actual workflow, not idealized process |
| 2 | "What information do you wish you had but don't?" | Data gaps, integration opportunities |
| 3 | "When something goes wrong, how do you find out?" | Alerting gaps, latency in decision-making |
| 4 | "What takes the most time that feels like it shouldn't?" | Automation candidates, high-value use cases |
| 5 | "If you could change one thing about your tools, what would it be?" | UI/UX pain points, integration priorities |

---

### Phase 2 -- Ontology & Integration (Weeks 2-6)

This phase overlaps with Discovery -- it begins as soon as the first data sources are identified. The objective is to build the **digital twin** of the client's operational reality.

#### Data Landscape Mapping

- **15-40 data sources identified** during discovery
- **3-10 sources connected** during the pilot (the rest come in Expand)
- Pipeline architecture: **Raw -> Clean -> Semantic** (three-layer pipeline pattern)

**Data Access Is Political Warfare:**

> **Nabeel Qureshi** (8 years as FDE): *"8-12 weeks just getting data access."*

Data access is not a technical problem. It is a political problem. Every data source has an owner, and that owner has incentives to protect their territory. The DBA who controls the ERP database is not obstructing because they are incompetent -- they are obstructing because giving access means giving up power.

#### 5 Navigation Strategies for Data Access Politics

| # | Strategy | When to Use |
|---|---|---|
| 1 | **Executive mandate**: Get the CIO/CTO to send an email directing teams to cooperate | When blockers are in middle management and there is strong executive sponsorship |
| 2 | **Read-only first**: Request read-only access to reduce perceived risk | When the data owner is risk-averse but not hostile |
| 3 | **Show value first**: Build a prototype with available data, then demonstrate what is possible with the blocked data | When the blocker needs to see ROI before cooperating |
| 4 | **API bypass**: If the database is locked down, find an API or export mechanism that does not require the DBA's involvement | When the blocker is genuinely uncooperative and the sponsor supports the workaround |
| 5 | **Reciprocity**: Offer the data owner something valuable in return -- a dashboard, an insight, access to combined data they could not see before | When the blocker is protecting their turf but would benefit from integration |

---

### Phase 3 -- Actions, Security & Applications (Weeks 4-10)

#### Action Types Implementation

Actions are the bridge between insight and execution. They turn the ontology from a read-only dashboard into an **operational decision system**. Types implemented during the pilot:

- **Manual actions**: User-triggered operations (approve, reject, reassign, escalate)
- **Automated actions**: Rule-based triggers (if inventory below threshold, create PO)
- **AI-assisted actions**: AIP Logic recommendations with human-in-the-loop approval
- **Webhook actions**: Write-back to source systems (update SAP, send email, trigger workflow in ServiceNow)

#### Security Architecture -- 4 Levels

| Level | Mechanism | What It Controls |
|---|---|---|
| 1 -- Project | Project-level isolation | Which teams can see which ontology objects |
| 2 -- Object | Row-level security on ontology objects | Which records a user can see (e.g., only their region's data) |
| 3 -- Property | Column-level masking | Which fields are visible (e.g., salary hidden from non-HR) |
| 4 -- Action | Action-level permissions + RBAC | Who can trigger which actions (e.g., only managers can approve POs) |

Additional: **Markings** (classification labels like CONFIDENTIAL, RESTRICTED) and **RBAC** (Role-Based Access Control with inheritance from organizational hierarchy).

#### Workshop Applications Built During Pilot

- **3-10** -- Workshop Apps Built
- **5-15** -- Dashboards Created
- **10-30** -- Automated Pipelines

---

### Phase 4 -- Training & Handoff (Weeks 8-12)

#### 3-Tier Training Program

| Tier | Audience | Format | Duration | Outcome |
|---|---|---|---|---|
| Executive | C-suite, VP-level sponsors | 1:1 or small group | 2-4 hours | Can articulate ROI, navigate dashboards, approve expansion |
| Power Users | Business analysts, team leads | Hands-on workshop | 2-3 days | Can build basic Workshop apps, create queries, configure alerts |
| End Users | Front-line operators | On-the-job + guides | 4-8 hours | Can use applications daily, follow workflows, report issues |

#### Go-Live Process

- **Week 10**: Soft launch with power users (monitored closely, FDE on standby)
- **Week 11**: Expanded rollout to full user base
- **Week 12**: Go-live readout. Success metrics presented. Expansion proposal delivered

#### Daily FDE Schedule Template (by Phase)

| Time | Phase 1 (Discovery) | Phase 2-3 (Build) | Phase 4 (Handoff) |
|---|---|---|---|
| 8:00-9:00 | Pod standup + plan | Pod standup + sprint review | User support office hours |
| 9:00-12:00 | Stakeholder interviews | Ontology/pipeline/app build | Training sessions |
| 12:00-13:00 | Working lunch with users | Working lunch with users | Debrief with client team |
| 13:00-17:00 | Process observation + shadowing | Build + demo iterations | Documentation + knowledge transfer |
| 17:00-18:00 | DS-FDE debrief | DS-FDE debrief + demo prep | Expansion planning session |
| 18:00-20:00+ | Notes, analysis, planning | Night build (if needed) | Transition documentation |

---

## Section 2.5 -- Expand Phase (Year 1-3, $250K -> $1-5M ACV)

### Expand Phase -- Triggers, Mechanisms & Growth Path

**Starting point: PILOT COMPLETE** -- $100K-$500K ACV

**Expansion Triggers:**

1. **Proximity Discovery** -- Adjacent teams see the pilot app and ask "can we have something like that?"
2. **Stakeholder Cartography** -- DS maps new champions in other departments. Proactive outreach
3. **Platform Usage Analytics** -- Telemetry shows which users, features, and data are underserved

**Expansion Mechanisms:**

1. **"Build with AIP" Bootcamps** -- 20-50 participants (vs 5-20), for existing clients only, ontology-based not greenfield
2. **"100 Use Cases" Exercise** -- Brainstorm by department, canvas template + triage, live prototyping top picks
3. **Cross-Dept Ontology Growth** -- 5-20 objects (pilot) -> 100-500+ objects (expand) -> 500-1,000+ (Army/bp scale)
4. **Centre of Excellence (CoE)** -- Established 6-18 months post, client's own Palantir team, certifications (Dec 2025)

**Champion System -- 4 Levels of Client Enablement:**
User -> Power User -> Builder -> Architect

**Outcome: $250K -> $1-5M ACV** -- 4-20x expansion in 12-36 months

*Fig 2.5 -- Expansion phase flowchart: triggers, mechanisms, champion system, and ACV growth trajectory*

---

### Expansion Triggers

Expansion is not accidental. Palantir designs the pilot to **create expansion demand** through three deliberate mechanisms:

- **Proximity discovery**: The pilot team's adjacent departments see the working application and ask for their own. A supply chain pilot generates demand from procurement, logistics, and finance teams who share adjacent data
- **Stakeholder cartography**: The DS continuously maps new potential champions. Every executive meeting includes a soft pitch for adjacent use cases. The political map expands with each interaction
- **Platform usage analytics**: Palantir tracks which features are used, which data sources are queried most, and which users log in daily. This telemetry identifies underserved teams and untapped use cases

---

### "Build with AIP" Bootcamps (for Existing Clients)

Distinct from the initial 5-day bootcamp, "Build with AIP" bootcamps are for **existing clients** who want to expand their usage. Key differences:

| Dimension | Initial Bootcamp | "Build with AIP" Bootcamp |
|---|---|---|
| Participants | 5-20 (8-12 typical) | **20-50 participants** |
| Starting point | Greenfield (no ontology) | Existing ontology + live data |
| Objective | Prove value, convert to pilot | Expand use cases, grow adoption |
| Cost | Free | Often included in contract |
| Client knowledge | Learning Palantir for the first time | Power users leading, new users joining |

---

### The "100 Use Cases" Exercise

A structured brainstorming workshop designed to surface **every possible application** of the ontology across the organization. Process:

1. **Department-by-department brainstorm**: Each department generates 15-30 potential use cases on a canvas template (structured as: problem, data required, expected outcome, estimated impact)
2. **Triage**: DS and FDE score each use case on a 2x2 matrix (impact vs. feasibility). Top-right quadrant gets prioritized
3. **Live prototyping**: The top 3-5 use cases are prototyped during the workshop -- in hours, not days -- leveraging the existing ontology
4. **Expansion roadmap**: The scored list becomes the 12-18 month expansion roadmap, with each use case mapped to a potential ACV increment

**Why 100?**
The number 100 is deliberate. It forces participants past the obvious 5-10 use cases and into creative territory. Use cases 50-100 are often the most valuable because they represent cross-departmental workflows that no single team would have identified alone.

---

### Cross-Department Ontology Growth

| Stage | Object Types | Typical Scope | Example |
|---|---|---|---|
| Pilot | **5-20** | Single team, 1-2 use cases | Order, Product, Supplier, Warehouse |
| Expand | **100-500+** | 3-5 departments, 10-30 use cases | + Employee, Machine, Route, Customer, Invoice, Contract... |
| Scale (Army/bp) | **500-1,000+** | Enterprise-wide, 50-200+ use cases | Full operational digital twin of the organization |

#### Entity Resolution

As the ontology grows across departments, the same real-world entity appears in multiple source systems with different identifiers, spellings, and formats. **Entity Resolution** is the ML pipeline that merges them:

1. **Blocking**: Reduce the comparison space (e.g., only compare entities in the same country)
2. **Comparison**: Score similarity across multiple attributes (name, address, ID, phone)
3. **Clustering**: Group records that likely represent the same entity
4. **User feedback loop**: Analysts confirm or reject proposed merges, improving the model over time

---

### Centre of Excellence (CoE)

Established **6-18 months post-deployment**, the CoE is the client's own internal Palantir team. It represents the transition from "Palantir builds for us" to "we build on Palantir."

#### Curriculum by Role

| Role | Training Hours | Key Skills |
|---|---|---|
| Data Engineers | **80-100h** | Pipeline construction, transforms, data quality, scheduling |
| App Developers | **40-60h** | Workshop app building, widget configuration, action design |
| Ontology Architects | 60-80h | Object type design, relationship modeling, security architecture |
| Business Analysts | 20-40h | Contour queries, dashboard building, report automation |
| AIP Specialists | 30-50h | AIP Logic configuration, prompt engineering, agent design |
| Platform Admins | 40-60h | User management, security, monitoring, infrastructure |

**Palantir Certifications**: Launched December 2025. Formal certification tracks for each role, enabling clients to validate their internal Palantir expertise and reducing dependency on FDEs. **CONFIRMED**

#### Champion System -- 4 Levels

- **Level 1 -- User**: Uses apps daily. Follows workflows. Reports issues.
- **Level 2 -- Power User**: Builds queries. Creates dashboards. Trains others.
- **Level 3 -- Builder**: Builds Workshop apps. Configures actions. Designs ontology extensions.
- **Level 4 -- Architect**: Designs ontology. Owns security model. Plans platform evolution.

---

### Third-Party Ecosystem

Palantir is building a partner ecosystem of firms that can implement and extend Foundry/AIP without Palantir FDEs:

| Partner | Type | Scale | Focus |
|---|---|---|---|
| **Accenture** | System Integrator | 2,000+ trained professionals | Large-scale enterprise deployments |
| **Ontologize** | Boutique (ex-Palantir) | ~50-100 people | Ontology design, data integration |
| **Multiverse** | Training/Apprenticeships | Varies | Building client-side Palantir capability |
| **CodeStrap** | Development Partner | ~20-50 people | Custom Workshop app development |
| **Deloitte** | System Integrator | Growing practice | Government and regulated industries |

---

## Section 2.6 -- Scale Phase (Year 3+, $5-20M+ ACV)

### FDE Graduation Curves -- Withdrawal Timeline & Revenue Impact

The diagram shows Commercial (0-36 months) vs Government (0-48+ months) FDE withdrawal curves, with an inverse ACV Growth line ($100K -> $5.6M). The breakeven point occurs around Month 12. Phase labels at bottom:

- **ACQUIRE (loss)** -- early months
- **EXPAND (-43% to +35%)** -- mid-period
- **SCALE (+55%+ margin)** -- maturity

*Fig 2.6 -- FDE graduation curves showing Commercial (0-36 months) vs Government (0-48+ months) withdrawal timelines, overlaid with ACV growth trajectory. The inverse relationship between FDE count and revenue is the core of Palantir's economic model.*

---

### FDE Graduation / Withdrawal

The Scale phase is defined by the **deliberate withdrawal** of FDEs -- not abandonment, but graduation. The client's internal team (CoE) takes over day-to-day operations, and the FDE pod shrinks from 4-5 to 0-1 people.

| Sector | Full FDE Pod (4-5) | Reduced (2-3) | Minimal (0-1) | Total Timeline |
|---|---|---|---|---|
| Commercial | Months 0-6 | Months 6-18 | Months 18-36+ | **0-36 months** |
| Government | Months 0-12 | Months 12-30 | Months 30-48+ | **0-48+ months** |

**ESTIMATED** Based on multiple FDE accounts and deployment timelines

**Government Accounts Are Stickier:**
Government deployments retain FDEs longer for three reasons: (1) higher security clearance requirements make internal hires harder, (2) procurement cycles are slower for expanding internal teams, and (3) the operational stakes (military, intelligence) make clients reluctant to remove experienced operators.

---

### Self-Service Enablement & The Lock-In Reality

#### The "Captive-Autonomous" Paradox

As clients graduate to self-service, a paradox emerges: they become simultaneously **more autonomous in usage** and **more captive in infrastructure**. The more they build on the ontology, the more data, workflows, applications, and institutional knowledge are embedded in Palantir's platform -- and the harder it becomes to leave.

#### 5 Layers of Lock-In (Honest Assessment)

| # | Layer | Switching Difficulty | Estimated Switching Cost |
|---|---|---|---|
| 1 | **Data integration**: 15-40 connectors, custom pipelines | High | $2-5M to rebuild |
| 2 | **Ontology**: 100-1,000+ object types, relationships, business logic | Very High | $3-10M to redesign |
| 3 | **Applications**: 10-100+ Workshop apps used daily by hundreds of users | Extreme | $2-8M to replace |
| 4 | **Institutional knowledge**: The ontology IS the organization's operational knowledge | Near-impossible | $1-10M + years |
| 5 | **Human capital**: CoE team trained exclusively on Palantir tools | High | $2-10M retraining |

**Total estimated switching cost: $10M-$43M** for a mature Scale-phase client. **ESTIMATED**

**The Lock-In Knife Cuts Both Ways:**
While lock-in protects Palantir's revenue, it also constrains their pricing power. If clients feel "trapped" and resentful, they become vocal critics and reduce referral value. Palantir mitigates this by ensuring the platform delivers genuine, measurable value -- the lock-in is tolerated because the alternative (rebuilding from scratch) is worse than paying the renewal.

---

### Revenue Protection -- NDR & Expansion Economics

#### Net Dollar Retention (NDR) Trajectory

| Quarter | NDR | Interpretation |
|---|---|---|
| Q3 2023 | 107% | Modest expansion, pre-AIP era |
| Q1 2024 | 114% | AIP bootcamp ramp beginning to show in expansion |
| Q3 2024 | 120% | Existing clients adopting AIP on top of Foundry |
| Q3 2025 | 134% | Full AIP expansion cycle accelerating |
| Q4 2025 | **139%** | Best-in-class for enterprise software |

**CONFIRMED** Earnings calls

#### Expansion Multiple

- **56x** -- $100K initial -> $5.6M mature ACV
- **$94M+** -- Avg revenue per top 20 client (+45% YoY)

**CONFIRMED** Investor presentations, Q4 2025 earnings

---

## Section 2.7 -- Key Metrics -- The Delivery Model by Numbers

**Row 1:**
- **22%** -- Bootcamp -> Conversion in 90 Days
- **56x** -- $100K initial -> $5.6M mature ACV
- **139%** -- Net Dollar Retention (Q4 2025)

**Row 2:**
- **$1.01M** -- Revenue per Employee
- **-43%** -- Acquire Contribution Margin
- **+55%** -- Scale Contribution Margin

**Row 3:**
- **$94M+** -- Avg Revenue per Top 20 Client
- **GBP 150K** -- UK G-Cloud per Person/Quarter
- **~$80-150K** -- FDE Cost per $1M ARR (2025E)

### Margin Progression Across Lifecycle

| Phase | Timeline | ACV Range | Contribution Margin | FDE Intensity | FDE Cost / $1M ARR |
|---|---|---|---|---|---|
| **Acquire** | Month 0-3 | $100K-$500K | **-43%** | 4-5 FDEs / client | ~$700K (2016) -> ~$80-150K (2025E) |
| **Expand** | Month 3-36 | $500K-$5M | **-43% to +35%** | 2-3 FDEs / client | Declining as platform takes over |
| **Scale** | Year 3+ | $5M-$20M+ | **+55%+** | 0-1 FDE / client | Near-zero (client self-serves) |

---

## Section 2.8 -- Case Studies -- The Delivery Method in Practice

### Case Study Landscape -- Sector Distribution & Scale

**INDUSTRIAL:**
- Airbus Skywise -- 140+ airlines, 11,900 aircraft
- Lear Corporation -- 100 -> 16,000 users
- Trinity Rail -- $30M impact / 3 months

**CONSUMER / CPG:**
- General Mills -- $14M/yr ($40K/day)
- Fujitsu -- $9M savings / 3 months

**HEALTHCARE:**
- Tampa General -- $50M / 7-year deal
- Nebraska Medicine -- 2,100% discharge increase

**DEFENSE / GOVERNMENT:**
- US Army Vantage/Maven/TITAN -- 20 people replacing 2,000 for targeting operations

*Fig 2.7 -- Case study landscape across Industrial, Consumer, Healthcare, and Defense sectors*

---

### Airbus Skywise

**SCALE PHASE | INDUSTRY PLATFORM**

**The gold standard for Palantir's "platform becomes industry infrastructure" thesis.** What started as a data integration project for Airbus's manufacturing operations evolved into **Skywise** -- an industry-wide analytics platform serving the global aviation ecosystem.

- **140+ airlines** using Skywise for fleet management
- **11,900+ aircraft** monitored on the platform
- **50% of the global in-service fleet** connected
- Palantir's Foundry is the backend; Airbus sells the service to airlines

Key Metrics:
- **140+** -- Airlines Connected
- **11,900+** -- Aircraft Monitored
- **50%** -- Global In-Service Fleet

**Strategic Significance:**
Skywise demonstrates that Palantir's ontology can become the **data backbone for an entire industry**, not just a single company. This is the ultimate expansion play: one client becomes the distribution channel for the platform to hundreds of downstream users.

---

### General Mills -- $14M/Year ($40K/Day)

**SCALE PHASE | SUPPLY CHAIN**

General Mills is one of Palantir's most cited commercial case studies. The company uses Foundry for **end-to-end supply chain optimization** -- from demand forecasting through production scheduling to distribution logistics.

- **$14M annual contract value** (~$40K per day)
- Supply chain ontology covering raw materials, production lines, warehouses, retail distribution
- AIP Logic for demand sensing and automated procurement decisions
- Credited with significant reduction in waste and out-of-stock incidents

#### Expansion Path

| Phase | Scope |
|---|---|
| Pilot | Single supply chain node |
| Expand | Full supply chain network |
| Scale | Enterprise-wide + AI optimization |

- **$14M/yr** -- Annual Contract Value

---

### Fujitsu -- $9M Cost Reduction in 3 Months

**EXPAND PHASE | IT OPERATIONS**

Fujitsu deployed Foundry for IT service management optimization. Within **3 months**, they identified and eliminated $9M in operational inefficiencies by integrating data across siloed IT systems that had never been connected before.

- **Speed of impact**: 3 months from deployment to $9M in identified savings
- **Method**: Connected 15+ IT management tools into a unified ontology, revealing redundant processes, underutilized licenses, and overlapping service contracts
- This case study is frequently cited in bootcamp "Art of the Possible" demos for IT operations use cases

---

### Tampa General Hospital -- $50M, 7-Year Deal

**SCALE PHASE | HEALTHCARE**

Tampa General signed a **$50M, 7-year contract** at AIPCon 3 -- one of the largest and longest healthcare deals in Palantir's history. The deal covers hospital operations, clinical workflow optimization, and patient flow management.

- **$50M over 7 years** (~$7.1M ACV)
- Signed publicly at AIPCon 3 -- deliberate marketing for the healthcare vertical
- Covers: patient flow optimization, OR scheduling, supply chain, staffing
- Uses AIP for predictive patient demand and automated resource allocation

**AIPCon as a Deal-Closing Venue:**
Tampa General's public signing at AIPCon demonstrates how Palantir uses its conferences not just for lead generation but for **deal acceleration**. The social proof of signing on stage, surrounded by other enterprise leaders, reduces the perceived risk of a large commitment.

---

### Nebraska Medicine -- 2,100% Increase in Discharge Lounge Utilization

**EXPAND PHASE | HEALTHCARE**

Nebraska Medicine deployed Foundry for patient flow optimization, focusing on the discharge process -- one of the biggest bottlenecks in hospital operations. Results:

- **2,100%** -- Increase in Discharge Lounge Utilization

- **Problem**: Patients ready for discharge were occupying beds needed for incoming patients, creating cascading delays throughout the hospital
- **Solution**: Ontology connecting patient status, bed availability, transport, and discharge documentation into a single operational view
- **Impact**: Discharge lounge utilization increased from near-zero to active use, freeing beds hours earlier and reducing ER boarding times

---

### Lear Corporation -- 100 Users/4 Use Cases -> 16,000 Users/280 Use Cases

**SCALE PHASE | MANUFACTURING**

Lear Corporation is one of the most dramatic examples of the Expand -> Scale trajectory. The deployment grew **160x in users and 70x in use cases**:

| Metric | Pilot | Scale | Multiple |
|---|---|---|---|
| Users | 100 | **16,000** | 160x |
| Use Cases | 4 | **280** | 70x |
| Departments | 1 | 15+ | 15x+ |

**CONFIRMED** Palantir investor presentations

> This case study validates the entire Acquire -> Expand -> Scale economic model. A small pilot with 100 users grew to an enterprise-wide platform with 16,000 users. The ontology expanded from 4 initial use cases to 280 -- demonstrating that once the data foundation is in place, the marginal cost of each new use case approaches zero.

---

### Trinity Rail -- $30M Bottom-Line Impact in 3 Months

**EXPAND PHASE | MANUFACTURING**

Trinity Industries (rail car manufacturing) deployed Foundry for supply chain and production optimization. The speed of impact is what makes this case notable:

- **$30M bottom-line impact in the first 3 months**
- Optimization areas: production scheduling, raw material procurement, maintenance forecasting, logistics routing
- The $30M figure represents cost avoidance + revenue acceleration from faster delivery times
- ROI timeline: positive ROI within the first quarter of deployment -- a powerful proof point for bootcamp conversion pitches

**Why 3-Month Impact Matters:**
If Palantir can demonstrate $30M impact in 3 months on a pilot that costs $100K-$500K, the ROI math becomes irresistible. A 60x-300x return in one quarter removes every budget objection. This is why case studies like Trinity Rail are prominently featured in bootcamp executive readouts.

---

### US Army -- Vantage / Maven / TITAN

**SCALE PHASE | DEFENSE**

The US Army is Palantir's largest and most complex government deployment, spanning multiple programs:

| Program | Function | Scale |
|---|---|---|
| **Vantage** | Army-wide data analytics platform | Enterprise (250,000+ potential users) |
| **Maven Smart System** | AI-powered intelligence analysis | Multi-domain intelligence fusion |
| **TITAN** | Tactical Intelligence Targeting Access Node | Field-deployable targeting system |

**20 People Replacing 2,000:**
The most striking metric from the Army deployment: **a team of 20 operators using Palantir can perform targeting analysis that previously required 2,000 analysts.** This 100x efficiency gain is the most extreme example of Palantir's force-multiplier effect. It reflects both the power of the integrated ontology (connecting intelligence sources that were previously siloed) and the automation capabilities of AIP Logic (processing data volumes no human team could handle).

- **Ontology scale**: 500-1,000+ object types covering personnel, equipment, terrain, intelligence, logistics, operations
- **Security model**: Multi-level classification (UNCLASSIFIED through TS/SCI) with compartmented access controls -- the most complex security architecture in any Palantir deployment
- **FDE retention**: Government deployments retain FDEs for 48+ months due to security clearance requirements and operational criticality
- **Contract value**: Multiple contracts totaling hundreds of millions. The Army is in the "top 20 clients" generating $94M+ annually

---

## Summary -- The Delivery Method -- Key Takeaways

### The Machine in One Paragraph

Palantir's delivery method is a **deliberate loss-leading engine** that converts free bootcamps ($12-36K cost) into $100K-$500K pilots, then expands them to $1-5M in years 1-3, and ultimately to $5-20M+ at maturity. The FDE pod -- 3-5 people mixing technical builders (Delta) with strategic advisors (Echo) -- operates under Auftragstaktik doctrine, making all execution decisions in the field. As the client matures, FDEs graduate out and the Centre of Excellence takes over, creating the "captive-autonomous paradox": clients become simultaneously more self-sufficient in usage and more locked in to the platform ($10-43M switching costs). The result is a 139% net dollar retention rate, a 56x expansion multiple, and $1.01M revenue per employee -- making Palantir's delivery model one of the most efficient in enterprise software.

### The Funnel (Volume)

| Metric | Value |
|---|---|
| AIPCon attendees | **Thousands** |
| Bootcamps conducted | **1,400+ (Q3 2024)** |
| Conversions (est. 22%) | **~308** |
| Scale-phase clients (top 20) | **$94M+ avg/client** |

### The Economics (Margin)

| Metric | Value |
|---|---|
| Bootcamp cost to Palantir | **$12-36K each** |
| Acquire margin | **-43%** |
| Expand margin (month 12) | **~+35%** |
| Scale margin (year 3+) | **+55%+** |

# ═══════════════════════════════════════════════════════════════
# PART 3: THE COMMERCIAL ENGINE
# ═══════════════════════════════════════════════════════════════

# Part 3: The Commercial Engine

Financials, pricing, flywheel, government strategy, competitive landscape, lock-in mechanics, and risks.

---

## 03.1 Financial Profile

### Key Metrics

| Metric | Value | Change |
|--------|-------|--------|
| FY2025 Revenue | $4.475B | +56% YoY |
| Q4 2025 Revenue | $1.407B | +70% YoY |
| US Commercial Rev | $1.465B | +109% YoY |
| Q4 US Commercial | $507M | +137% YoY |
| GAAP Gross Margin | 84% | |
| Net Dollar Retention | 139% | |
| Total Customers | 954 | +34% YoY |
| Revenue / Employee | $1.01M | |
| Adj Free Cash Flow | $2.27B | +82% YoY |
| FY2026 Revenue Guide | $7.19B | +61% Guide |
| Q4 Total Contract Value | $4.3B | +138% YoY |
| FY2025 Net Income | $1.625B | +250% YoY |
| Market Cap | ~$313B | |
| Top 20 Avg / Client | $94M+ | |
| Expansion Multiple | 56x | |

### Revenue Trajectory: FY2020 -- FY2026E

Chart data points:

| Fiscal Year | Revenue | YoY Growth |
|-------------|---------|------------|
| FY2020 | $1.09B | |
| FY2021 | $1.54B | +41% |
| FY2022 | $1.91B | +24% |
| FY2023 | $2.23B | +17% |
| FY2024 | $2.87B | +29% |
| FY2025 | $4.48B | +56% |
| FY2026E | $7.19B | +61% |

AIP Launch annotation: April 2023

Palantir revenue trajectory showing the AIP inflection point. FY2026E represents company guidance of $7.19B.

### Profitability Milestones

| Metric | FY2023 | FY2024 | FY2025 | Trend |
|--------|--------|--------|--------|-------|
| Revenue | $2.23B | $2.87B (+29%) | $4.475B (+56%) | Accelerating |
| GAAP Gross Margin | 81% | 82% | 84% | Expanding |
| S&M % of Revenue | ~24% | ~22% | ~21% | Improving |
| Net Income (GAAP) | $210M | $464M | $1.625B (+250%) | Breakout |
| Adj. Free Cash Flow | $730M | $1.25B | $2.27B (+82%) | Compounding |
| Customer Count | 497 | 711 | 954 (+34%) | Broadening |
| Revenue / Employee | ~$630K | ~$780K | $1.01M | Elite |
| Net Dollar Retention | 115% | 120% | 139% | Best-in-class |

**Key Insight:** Palantir's $1.01M revenue per employee makes it among the most efficient enterprise software companies at scale. For comparison: ServiceNow ~$550K, Salesforce ~$400K. Only a handful of companies (Nvidia, Broadcom) exceed this figure.

### Revenue Composition Shift

US Commercial has become the primary growth vector, surpassing Government growth for the first time in company history:

| Segment | FY2023 | FY2024 | FY2025 |
|---------|--------|--------|--------|
| US Government | $1.22B | $1.34B | $1.57B |
| US Commercial | $0.70B | $0.70B | $1.47B |
| International | $0.31B | $0.83B | $1.44B |
| **Total** | **$2.23B** | **$2.87B** | **$4.475B** |

US Commercial: +109% YoY

Revenue composition FY2023--FY2025 showing the explosive growth of US Commercial driven by AIP adoption.

---

## 03.2 Pricing Architecture

> **"There is no pricing strategy for AIP."** -- Alex Karp, CEO. A deliberate land-grab strategy: price discovery through value, not catalogs.

### Three-Layer Pricing Model

**LAYER 1: CORE PLATFORM LICENSE**
Per-core licensing model based on compute capacity

- **Foundry:** 66K GBP/core/year
- **Gotham:** 141K GBP/core/year
- **Apollo:** $100/install/month

**LAYER 2: USAGE-BASED AI CONSUMPTION**
AIP compute consumption metered per model invocation + data processed

- LLM Inference: Token-based billing
- Pipeline Runs: Execution metering
- Ontology Queries: Volume-based
- Data Storage: TB-based

**LAYER 3: FDE & PROFESSIONAL SERVICES**
Forward Deployed Engineers + Training & Enablement

- FDE Embedding: 150K GBP/person/quarter (~$760K/yr)
- Bootcamp: 1,100 GBP/person
- Workshop: 1,750 GBP/person
- Integrator: 2,100 GBP/person

Palantir's three-layer pricing architecture: core license + AI consumption + services. G-Cloud UK pricing data.

### G-Cloud UK License Tiers

The UK G-Cloud framework provides the most transparent window into Palantir pricing. The tier structure reveals a logarithmic scale designed for massive enterprise expansion:

| Tier | Annual License (GBP) | Typical Customer Profile |
|------|---------------------|--------------------------|
| Level 0 | 250,000 GBP | Pilot / single department proof-of-concept |
| Level 1--3 | 500K -- 2M GBP | Multi-team deployment, initial Ontology build |
| Level 4--7 | 2M -- 25M GBP | Enterprise-wide platform, Centre of Excellence |
| Level 8--11 | 25M -- 200M GBP | Ministry / large-enterprise multi-year |
| Level 12--15 | 200M -- 1B GBP | National-scale programs (e.g., NHS FDP) |

### Training & Enablement Pricing

**Per-Person Training Rates (G-Cloud UK)**

| Program | Price (GBP) |
|---------|-------------|
| Bootcamp (5-day intensive) | **1,100** |
| Developer Training | **1,000** |
| Workshop (use-case focused) | **1,750** |
| Integrator Certification | **2,100** |

**FDE Embedding Economics**

- **Rate:** 150K GBP/person/quarter (~$760K/year)
- **Typical engagement:** 2--4 FDEs for 6--18 months
- **Internal cost:** ~$200K--$350K salary + overhead
- **Margin on FDE:** ~50--65% (but negative contribution in Acquire phase due to unbilled hours)
- **Graduation target:** 36 months (commercial), 48 months (government)

**Deliberate Price Opacity:** Karp's "no pricing strategy for AIP" is not carelessness -- it is a calculated land-grab tactic. By avoiding published pricing, Palantir can: (1) price to value rather than cost, (2) offer aggressive initial deals to win strategic accounts, (3) expand pricing as usage grows organically. The G-Cloud data reveals that once a customer is locked in at Level 0, they predictably graduate upward -- often jumping 2--3 tiers per renewal cycle.

---

## 03.3 The Acquire > Expand > Scale Flywheel

### Unit Economics by Phase

Central flywheel: 56x expansion

**ACQUIRE**
- $0 (bootcamp) > $100K--$500K pilot
- Margin: -43%
- 2--4 FDEs embedded, single use case

**EXPAND**
- $250K > $1M--$5M ACV
- Margin: -43% to +35%
- Multi-dept, CoE build, Build with AIP

**SCALE**
- $5M--$20M+ ACV
- Margin: +55%
- Self-service, minimal FDE, revenue protection

**FEEDBACK LOOP**
- FDE insights > platform improvements
- Better product > faster expansion
- Every deployment improves the core

**$100K initial > $5.6M mature ACV = 56x expansion multiple**
S&M as % of revenue: 47% (2020) > 21% (2025) -- the flywheel compounds

The Palantir flywheel: each phase has distinct unit economics. The feedback loop from FDE field insights back into the platform is the hidden competitive advantage.

### Phase 1: Acquire

- **ACV:** $0 (bootcamp) to $100K--$500K
- **Margin:** -43% (investment phase)
- **FDE intensity:** 2--4 embedded engineers
- **Duration:** 0--6 months
- **Goal:** Solve a "hair on fire" problem; demonstrate undeniable value in weeks
- **Entry point:** Free AIP bootcamp (5-day) converts to paid pilot

### Phase 2: Expand

- **ACV:** $250K > $1M--$5M
- **Margin:** -43% to +35% (breakeven ~month 9)
- **FDE intensity:** Decreasing, CoE forming
- **Duration:** 6--24 months
- **Goal:** Multi-department spread; "Build with AIP" bootcamps drive viral adoption
- **Champions:** Internal advocates trained as certified builders

### Phase 3: Scale

- **ACV:** $5M--$20M+ (top 20 at $94M+)
- **Margin:** +55% (platform leverage)
- **FDE intensity:** Minimal / graduated
- **Duration:** 24+ months (indefinite)
- **Goal:** Self-service capability; CoE runs independently; revenue protection through lock-in
- **Protection:** Multi-year contracts, deep Ontology dependency

### Sales & Marketing Efficiency Over Time

| Year | S&M as % of Revenue | Revenue | Interpretation |
|------|---------------------|---------|----------------|
| 2020 | **47%** | $1.09B | Pre-commercial pivot -- government sales intensive |
| 2021 | ~34% | $1.54B | IBM/commercial partnerships ramp |
| 2022 | ~28% | $1.91B | Bootcamp motion proving out |
| 2023 | ~24% | $2.23B | AIP bootcamp as self-funding acquisition channel |
| 2024 | ~22% | $2.87B | Product-led growth amplifying |
| 2025 | **~21%** | $4.475B | Flywheel compounding -- NDR 139% drives organic growth |

**S&M Leverage:** Palantir has cut S&M spend from 47% of revenue to ~21% over five years while *accelerating* growth from +17% to +56%. This is the flywheel in action: existing customers expand organically (139% NDR), reducing the marginal cost of each incremental dollar of revenue.

---

## 03.4 Government Strategy

### Government Contract Vehicle Architecture

**PALANTIR GOVERNMENT CONTRACT LANDSCAPE**

**PROCUREMENT VEHICLES**

- **OTA** -- Other Transaction Authority
- **IDIQ** -- Indefinite Delivery / Qty
- **Sole Source** -- JEDI-like exclusives
- **G-Cloud UK** -- UK framework agreement

**Certifications:**
FedRAMP Moderate/High | DoD IL5/IL6 | CMMC | Air-gapped via Apollo (sneakernet) | SecNumCloud (pending)

**LANDMARK CONTRACTS**

| Contract | Value | Description |
|----------|-------|-------------|
| US Army ESA | $10.0B | Enterprise Software Acquisition -- 10-year ceiling. Vantage (Army Foundry), data fabric for all Army commands |
| Project Maven (DoD) | $1.3B | AI/ML for intelligence analysis & targeting. Originally Google (dropped 2018) > Palantir prime |
| TITAN (Army) | $823M | Tactical Intelligence Targeting Access Node. Ground-station hardware/software for battlefield intelligence |
| NHS FDP (UK) | 330M GBP | Federated Data Platform for NHS England. Largest UK health data contract; controversial privacy debates |
| Warp Speed Manufacturing OS | -- | Industrial base modernization program -- extending from defense supply chain to broader manufacturing infrastructure. NGA, State Dept appearances at AIPCon 4 signal expanding agency footprint beyond traditional IC/DoD |

Palantir's government contract architecture spanning US DoD, IC, and international (UK NHS). OTA and IDIQ vehicles enable faster procurement cycles.

### Government vs. Commercial Dynamics

**Government Advantages**

- **Longer contracts:** 5--10 year ceilings vs. 1--3 year commercial
- **Higher switching costs:** Security certifications + institutional knowledge
- **Competitive moat:** FedRAMP High + IL5/IL6 + air-gap capability eliminates most competitors
- **Budget stability:** Appropriated funding more predictable than commercial cycles
- **Network effects:** Each agency adoption creates cross-agency demand

**Government Challenges**

- **Longer graduation:** 48 months to Scale vs. 36 months commercial
- **Procurement friction:** Protest risk (lost original Army DCGS-A bid to protest)
- **Budget concentration:** Top-heavy revenue from few mega-contracts
- **Political risk:** Administration changes affect priorities
- **Growth ceiling:** TAM limited by defense/intel budgets (~$800B US, but addressable fraction smaller)

---

## 03.5 Competitive Landscape

### Competitive Positioning: Operational Complexity vs. Platform Completeness

Axes: X = PLATFORM COMPLETENESS (data > model > action), Y = OPERATIONAL COMPLEXITY HANDLED

Quadrants:
- Top-left: NICHE TOOLS
- Top-right: OPERATIONAL PLATFORMS
- Bottom-left: POINT SOLUTIONS
- Bottom-right: DATA PLATFORMS

Positioning:

| Company | Position | Revenue/Valuation |
|---------|----------|-------------------|
| Palantir | Top-right (dominant) | $4.5B |
| Microsoft (Fabric+Copilot) | Mid-right | -- |
| Databricks | Mid-right, lower | $5.4B run-rate |
| Snowflake | Center-right, lower | $3.3B |
| Google Cloud | Mid-center | -- |
| Anduril | Top-left | $30.5B valuation |
| Scale AI | Top-center-left | $14B valuation |
| Helsing | Top-left | $4.5B |
| C3.ai | Center-left | $389M |
| Dataiku | Center | ~$200M |
| Tempus | Bottom-left | -- |
| Harvey | Bottom-left | -- |
| Altana | Bottom-left | -- |
| McKinsey (QB) | Mid-left | ~$17B |
| Accenture | Mid-left | $64.9B |

Legend:
- Platform / Palantir
- Data infrastructure
- Defense tech
- Threat / consulting

Competitive positioning map. Palantir occupies a unique position at the intersection of maximum platform completeness and highest operational complexity. Circle size approximately proportional to revenue.

### Direct Competitors: Detailed Comparison

| Company | Revenue | Valuation | Customers | Ontology? | Gov/Air-gap? | Threat Level |
|---------|---------|-----------|-----------|-----------|--------------|--------------|
| **Databricks** | $5.4B run-rate | $134B | 10,000+ | Unity Catalog (data, not operational) | No | Medium |
| **Snowflake** | $3.3B FY2025 | ~$70B | 10,000+ | No (Cortex AI = analytics layer) | No on-prem | Low |
| **C3.ai** | $389M FY2025 | ~$4B | ~90 | No | Limited | Minimal |
| **Dataiku** | $150--200M+ ARR | $3.7B | 500+ | No | No | Medium |

### Databricks: The Most Nuanced Relationship

**Competitive Tension**

- **$5.4B run-rate** vs. Palantir's $4.475B -- larger by revenue
- **10,000+ customers** vs. 954 -- bottom-up adoption at massive scale
- **Unity Catalog:** Data governance layer that competes with Ontology's data lineage capabilities
- **GTM contrast:** Self-service, developer-first vs. Palantir's top-down FDE model
- **Price advantage:** $50K entry point vs. Palantir's $250K+ minimum

**Strategic Partnership (Sep 2024)**

- Foundry can now run natively on Databricks Lakehouse
- Ontology sits on top of Unity Catalog
- Palantir handles operational layer; Databricks handles data engineering
- **Interpretation:** Palantir acknowledges Databricks won the data layer -- focuses on the operational layer above
- Similar pattern to AWS/Azure partnerships: infrastructure commoditizes, Ontology differentiates

### Defense Tech Competitors

**Anduril ($30.5B valuation)**

- **Model:** Hardware-first (drones, autonomous vehicles, sensors) + Lattice OS for tactical COP
- **Convergence:** Lattice OS increasingly competes with Gotham for battlefield common operating picture
- **Divergence:** Anduril builds hardware Palantir never will; Palantir has enterprise data platform Anduril lacks
- **Reality:** Joint deployments exist -- more complementary than competitive today
- **Palantir Mafia connection:** Founded by Palmer Luckey and ex-Palantir engineers; Trae Stephens (Palantir board) sits on Anduril board

**Scale AI ($14B valuation)**

- **Donovan:** Most direct competitor to AIP in military AI applications
- **Origin:** Data labeling empire pivoting aggressively into defense platforms
- **Alexander Wang:** Youngest billionaire founder, aggressive government positioning
- **Advantage:** Deep relationships with AI model companies from labeling business
- **Weakness:** No equivalent to Ontology; less deployment experience in classified environments

### Hyperscaler Threat Analysis

**Existential Risk #1: Microsoft**

**Microsoft Fabric + Copilot + Power Platform + Dynamics 365 + Purview** represents the single greatest long-term threat. The bull thesis: "80% of Palantir use cases at 20% of the cost." Microsoft has 400M+ Office 365 users, enterprise trust, and is aggressively bundling AI into every product.

**Microsoft: Five Critical Gaps That Protect Palantir (for now)**

| # | Gap | Why It Matters | Durability |
|---|-----|----------------|------------|
| 1 | **No Ontology equivalent** | Fabric is a data platform, not an operational decision platform. No semantic business object layer connecting data to real-world actions. | 5+ years |
| 2 | **Integration tax** | Microsoft products require stitching together 6+ services (Fabric + Copilot + Power Automate + Dynamics + Purview + Azure ML). Palantir ships one platform. | 3--5 years |
| 3 | **No classified capability** | Azure Government exists, but not at IL5/IL6 for core AI workloads. No air-gapped Copilot deployment. | 5+ years |
| 4 | **Productivity vs. operational DNA** | Microsoft optimizes for knowledge worker productivity (email, documents, spreadsheets). Palantir optimizes for operational decisions under uncertainty (supply chains, battlefield, fraud detection). | 3--5 years |
| 5 | **No FDE expertise model** | Microsoft partners with system integrators. Palantir's FDEs have domain expertise + engineering skills that create stickier, faster deployments. | 2--4 years |

**Google Cloud**

- **Position:** Strong AI components (Gemini, BigQuery, Vertex AI) but weaker enterprise assembly
- **Cloud share:** ~12% (distant third behind AWS and Azure)
- **Maven history:** Dropped Project Maven in 2018 under employee pressure -- Palantir picked it up
- **Assessment:** Technically capable but culturally misaligned with defense/government -- the "Maven scar" persists

**Hyperscaler Summary**

The hyperscalers can replicate individual Palantir capabilities (data pipelines, ML inference, dashboards) but struggle to replicate the **integrated operational layer** -- the Ontology + Actions + Apollo deployment stack. Palantir's moat is not any single feature but the system-of-systems integration that takes years to build and tune per customer.

### Consulting Firms: The Structural Misalignment

| Firm | Revenue | AI Revenue | Model | Palantir Relationship |
|------|---------|------------|-------|----------------------|
| **McKinsey (QuantumBlack)** | ~$16--18.8B | ~40% AI-related | Advisory + custom builds | Competitive in analytics; no product |
| **BCG (X)** | $13.5B | $2.7B (20%) | Design + implementation | Competitive in transformation projects |
| **Accenture** | $64.9B | $2.7B GenAI (tripled YoY) | SI + outsourcing | Preferred Partner |
| **Deloitte** | $67.2B | Significant (undisclosed) | Audit + consulting + SI | Partner on government implementations |

**Why Consulting Firms Cannot Become Palantir**

**Economic misalignment:** A consulting firm earns $5M on a 12-month project with 30 consultants. Palantir earns $500K on that same use case with 2 FDEs and a platform license that renews and expands. The consulting firm is *incentivized* to keep building; Palantir is incentivized to make the customer self-sufficient. This structural divergence means consulting firms will always partner with (or compete against) Palantir -- they cannot replicate the product-platform model because doing so would cannibalize their core business.

Deloitte is already scrapping traditional consulting titles in favor of AI-native roles -- an acknowledgment that the old model is under pressure. But the revenue model remains labor-hour-driven.

### European Sovereignty Competitors

European data sovereignty regulations and political pressure are creating a parallel competitive ecosystem designed specifically to replace American platforms:

| Company | Valuation / Revenue | Focus | Direct Displacement of Palantir? |
|---------|---------------------|-------|----------------------------------|
| **Helsing** | $4.5B+ valuation | European defense AI | Most credible "European Palantir" for military. Operates in France, Germany, UK. |
| **ChapsVision ArgonOS** | Private (French) | Intelligence & law enforcement | Confirmed -- Replaced Palantir at DGSI (French domestic intel) |
| **Thales Cortex/ARTEMIS** | ~EUR 20B (parent) | Defense & intelligence platforms | Designed to -- Built explicitly to replace Gotham in French intelligence |
| **DataWalk (Poland)** | Public (WSE) | Law enforcement analytics | Markets itself as "Palantir alternative" for European police/intel |
| **Mistral AI** | EUR 11.7B | LLM / foundation models | French military AI partner 2026--2030. SecNumCloud 3.2 certified. Not a platform competitor but could power European alternatives. |

**International Growth Stall:** Palantir's international commercial revenue grew only +2% YoY at one point -- a stark contrast to the +109% US commercial growth. European sovereignty regulations (GDPR, SecNumCloud, German constitutional rulings on foreign intelligence platforms) are creating structural headwinds that may permanently cap Palantir's European government TAM. The DGSI replacement and Thales ARTEMIS program are not exceptions -- they are the beginning of a trend.

### Vertical AI: Death by a Thousand Cuts?

The most underappreciated competitive threat is not a single company but the collective emergence of vertical-specific AI platforms that solve narrow problems better than a horizontal platform can:

**Tempus AI**
- ~$700M+ revenue
- Precision medicine. Genomic data + clinical AI. Healthcare-specific Ontology equivalent.

**Harvey AI**
- $195M ARR, $8B valuation
- Legal AI. Contract analysis, due diligence, litigation support. Domain expertise no horizontal platform can match.

**Altana AI**
- Supply chain intelligence
- Global supply chain graph. Directly competes with Foundry's supply chain use cases.

**Hebbia**
- AI-native knowledge work. Document analysis for finance, legal, consulting. Threatens Foundry's analytics layer in knowledge-worker use cases.

**EvenUp**
- Legal AI for personal injury. Hyper-specific vertical that demonstrates how narrow AI can deliver faster ROI than configuring a horizontal platform.

**The thesis:** No single vertical AI company threatens Palantir. But collectively, they nibble at the edges of every industry Palantir targets. A hospital might choose Tempus over configuring Foundry for genomics. A law firm might choose Harvey over an AIP bootcamp. The risk is not replacement -- it is TAM compression.

---

## 03.6 Lock-In Mechanics

### The Seven Layers of Switching Cost

**SWITCHING COST PYRAMID**
Estimated total switching cost for mature deployment: $10M -- $43M

| Layer (top to bottom) | Name | Detail | Estimated Cost |
|-----------------------|------|--------|---------------|
| 7 (top, smallest) | ONTOLOGY | ~30% replicable | $5--15M to rebuild |
| 6 | DATA GRAVITY | Years of integrated, cleaned, enriched data | $2--8M in data eng |
| 5 | WORKFLOW DEPENDENCY | Hundreds of automated pipelines + actions | $1--5M to recreate |
| 4 | INTEGRATION COMPLEXITY | 400+ connectors configured per mature deployment | $1--4M to re-integrate |
| 3 | TRAINING INVESTMENT | CoE staff, certified builders, institutional knowledge | $0.5--3M sunk cost |
| 2 | ORGANIZATIONAL INERTIA | Executive sponsorship, procurement cycles, change management | $0.5--4M opportunity cost |
| 1 (bottom, widest) | CONTRACTUAL LOCK-IN | Multi-year terms, volume commitments, early termination fees | $0--4M penalty |

**TOTAL: $10M -- $43M estimated switching cost**
For a mature deployment ($5M+ ACV, 3+ years embedded)

**THE CAPTIVE-AUTONOMOUS PARADOX**
Palantir makes customers operationally autonomous (self-service CoE, citizen builders) while making them technically captive (Ontology, data gravity, workflow dependency). All confirmed Palantir departures predate 2018. No known large-scale deplatforming since AIP launch.

The seven-layer switching cost pyramid. Each layer compounds with the others, creating a cumulative barrier of $10M--$43M for mature deployments.

### Ontology as Moat: The 30% Replicability Problem

Industry analysis estimates that only ~30% of a Palantir Ontology deployment can be replicated by competitors. The remaining 70% consists of:

**What Cannot Be Easily Replicated**

- **Semantic business logic:** Years of encoding domain-specific rules, hierarchies, and relationships into Object Types and Link Types
- **Data lineage graphs:** Full provenance tracking from raw source to derived metric, across hundreds of data sources
- **Action configurations:** Automated workflows that trigger real-world actions (purchase orders, alerts, deployments) based on Ontology state changes
- **Institutional knowledge:** FDE-captured domain expertise embedded in the Ontology structure itself

**What Can Be Replicated (The 30%)**

- **Data pipelines:** ETL/ELT from source systems (Databricks, Snowflake can replicate)
- **Dashboards & visualizations:** Tableau, Power BI, Looker can cover 80% of analytical use cases
- **ML model hosting:** SageMaker, Vertex AI, Databricks MLflow replicate model ops
- **Basic data governance:** Unity Catalog, Purview, Collibra handle metadata and access control

**The Lock-In Paradox:** Palantir's genius is that lock-in feels like empowerment. Customers build their own applications on the platform (AIP App Builder, Workshop), train their own builders (CoE), and eventually run operations independently. But every application they build deepens their dependency on the Ontology substrate. The more autonomous they become as operators, the more captive they become as platform users. All confirmed large-scale departures from Palantir occurred before 2018, in the era before the modern Ontology architecture was fully established.

### Data Gravity: The Invisible Lock

After 2--3 years of Palantir deployment, a typical enterprise has:

| Metric | Value |
|--------|-------|
| Configured Connectors | 400+ |
| Automated Pipelines | 100s |
| Of Enriched Historical Data | Years |

Moving off Palantir does not mean just replacing software. It means:

- **Re-integrating every data source** -- each connector required custom configuration, authentication, schema mapping
- **Recreating data transformation logic** -- cleaning rules, deduplication logic, enrichment steps built over years
- **Rebuilding derived datasets** -- computed features, aggregations, and time-series that feed downstream applications
- **Retraining users** -- hundreds of certified builders and analysts fluent in Palantir's tooling
- **Accepting operational downtime** -- no "hot swap" migration path exists; parallel operation is cost-prohibitive

---

## 03.7 The Palantir Mafia

### Alumni Network: 170+ Startups, $24B+ Total Raised

Central node: PALANTIR -- 170+ startups, $24B+ raised

**Unicorns ($1B+ valuation):**

| Company | Category |
|---------|----------|
| Anduril | $30.5B |
| ElevenLabs | AI Voice |
| Ironclad | Contract AI |
| Chapter | Medicare |
| +5 more unicorns | -- |

**Notable alumni / companies:**

| Company/Person | Note |
|----------------|------|
| Affirm | Max Levchin |
| OpenAI | Bob McGrew |
| Hex | McCardel |
| Fox Corp | Hildebrandt |

**Co-founders / key figures:**
- Trae Stephens
- Joe Lonsdale
- Stephen Cohen

Stats: 9+ unicorns | 170+ startups | $24B+ raised

The Palantir Mafia network. More ex-Palantir founders per capita than ex-Googlers in each YC batch despite 50x fewer employees.

### Why the FDE Role Is a "Founder Factory"

The Forward Deployed Engineer role at Palantir is uniquely suited to producing startup founders because it combines:

**What FDEs Learn**

- **Customer empathy at speed:** FDEs sit with customers weekly, understanding their pain points intimately -- the same skill startup founders need
- **Full-stack execution:** FDEs write code, design systems, manage stakeholders, and ship product -- all at once
- **Operating under constraints:** Air-gapped networks, classified environments, production pressure -- builds resilience
- **Business model intuition:** Seeing how $100K pilots become $5M+ contracts teaches pricing and GTM instinctively

**The Network Effect**

- **Shared vocabulary:** Ex-Palantir founders can recruit, advise, and invest in each other using a common operational language
- **Pattern recognition:** Every FDE has seen 10+ enterprise deployments -- they know what works and what fails across industries
- **Institutional credibility:** "Ex-Palantir" on a resume signals technical depth + business acumen to VCs
- **Anduril proof point:** The most valuable Palantir spin-out ($30.5B) was founded by ex-Palantir people solving a problem they identified during Palantir deployments

**By The Numbers:** **170+ startups** founded by ex-Palantir employees. **$24B+ total raised** across the portfolio. **9+ unicorns** including Anduril ($30.5B), ElevenLabs, Ironclad, Chapter, and more. The disproportionate stat: *"More ex-Palantir founders than ex-Googlers in each YC batch despite 50x fewer employees."* Palantir has ~4,400 employees vs. Google's ~180,000+.

---

## 03.8 Risks & Counter-Thesis

### Risk 1: Valuation -- Priced Beyond Perfection

| Metric | Value |
|--------|-------|
| Trailing P/E | 206--223x |
| Price / Sales | 48--102x |
| Market Cap | ~$313B |

At ~$313B market cap on $4.475B revenue, Palantir trades at one of the highest multiples in enterprise software history. For context:

- **Rishi Jaluria (RBC Capital):** $50 price target -- one of the most bearish analysts on Wall Street, implying ~60% downside
- **Michael Burry ("Big Short"):** Purchased 50,000 put options against Palantir -- a high-conviction bet on overvaluation
- **Historical context:** Even at Palantir's guided $7.19B FY2026 revenue, the forward P/S remains ~43x -- still among the richest on the market

**Bull Response:** Bulls argue that Palantir's total addressable market in "enterprise AI operating system" is $500B+ and that current growth rates (56% YoY accelerating) justify premium multiples. The counter: no software company in history has sustained 50%+ growth to $10B+ revenue. The question is not whether Palantir is a great company -- it is whether the current price already reflects 5+ years of perfect execution.

### Risk 2: Microsoft Bundling

The "80% of use cases at 20% of cost" thesis. Microsoft is aggressively bundling AI capabilities into its existing product suite that 90%+ of enterprises already pay for:

| Palantir Capability | Microsoft Equivalent | Cost Differential |
|---------------------|---------------------|-------------------|
| Data integration & pipelines | Microsoft Fabric | Often included in E5 license |
| AI assistants & copilots | Microsoft Copilot | $30/user/month add-on |
| Workflow automation | Power Automate | $15/user/month |
| Data governance | Microsoft Purview | Included in E5 |
| Operational dashboards | Power BI | $10--$20/user/month |

**The Five Gaps** (Ontology, integration tax, classified, operational DNA, FDE model) protect Palantir today -- but Microsoft closes gaps relentlessly. Each gap has a 2--5 year estimated durability window.

### Risk 3: LLM Obsolescence of the Ontology

The theoretical risk: if LLMs become good enough at "schema-on-read" (understanding arbitrary data at query time without pre-defined structure), the Ontology's "schema-on-write" approach becomes unnecessary overhead.

**Counter-evidence: AI Agents Are Not Ready**

| Benchmark / Study | Finding | Implication |
|-------------------|---------|-------------|
| **APEX-Agents benchmark** | Best agents achieve only 18--29.8% accuracy on complex operational tasks | LLMs cannot reliably replace structured operational logic |
| **MIT Study (2025)** | 95% of GenAI pilots fail to deliver measurable P&L impact | Hallucination risk makes unstructured AI unsafe for high-stakes decisions |
| **S&P Global (2024)** | 42% of AI projects abandoned before production | Raw AI without operational scaffolding fails at enterprise scale |
| **BCG (2025)** | Only 5% of companies create value from AI at scale | The 95% failure rate validates the need for structured platforms |
| **IDC (2024)** | 88% of AI scaling initiatives fail | Moving from prototype to production requires exactly what Ontology provides |

**Palantir's Bet:** Palantir's thesis is that LLMs are powerful but unreliable -- and the Ontology provides the "guardrails" that make AI operationally safe. AIP does not replace the Ontology; it layers AI *on top of* the Ontology, using structured business logic to constrain LLM outputs. If schema-on-read ever becomes reliable enough for mission-critical operations, this thesis collapses -- but current benchmarks suggest that day is 5--10 years away, if ever.

### Risk 4: The "Palantirization" Trap (a16z Warning)

Andreessen Horowitz coined the term "Palantirization" to describe AI companies that inadvertently become consulting firms. The risk manifests in two ways:

**For Palantir Itself**

- **FDE job posting growth:** 800--1,000% increase in FDE-like roles posted in 2025
- **The tension:** Every FDE hired is a human whose work must eventually be replaced by platform leverage, or margins stagnate
- **Revenue per employee is rising ($1.01M)** -- so far, Palantir is winning this race

**For Palantir Imitators**

- Most companies copying the "FDE + platform" model become "Accenture for X with a nicer front-end"
- Without the Ontology and 20 years of deployment learnings, the platform never reaches escape velocity
- The copycat ends up selling services, not software -- 30% margins instead of 84%

### Risk 5: Customer Internalization

The **News Corp pattern:** sophisticated customers build internal capabilities that replicate Palantir's value, then reduce or eliminate their Palantir spend. This is the logical endpoint of Palantir's own "make the customer autonomous" strategy -- taken to its conclusion.

- **Who is at risk:** Large technology-forward enterprises with $5M+ engineering budgets and existing data science teams
- **Why it is limited:** Building Ontology-equivalent capability requires 3--5 years and $20M+ investment. Most companies conclude it is cheaper to keep paying Palantir $5M/year than spend $20M to replicate it internally.
- **Palantir's defense:** Continuous platform innovation (AIP, Agent capabilities) means the target keeps moving. By the time a customer replicates today's Palantir, Palantir has shipped two more generations.

### Risk 6: European Sovereignty Ceiling

**Evidence of Displacement**

- **DGSI (France):** ChapsVision ArgonOS *replaced* Palantir at French domestic intelligence -- confirmed
- **German constitutional ruling:** Court limitations on foreign intelligence platforms processing German citizen data
- **Thales ARTEMIS:** Explicitly designed to replace Gotham in French intelligence community
- **International commercial growth:** +2% YoY at low point -- structural headwind, not cyclical

**Structural Drivers**

- **GDPR enforcement:** Increasing scrutiny of US company data processing in EU
- **SecNumCloud 3.2:** French certification that effectively excludes US cloud providers
- **EU AI Act:** Additional compliance burden for non-EU AI platforms
- **Political will:** Post-Snowden, post-Trump sovereignty is a bipartisan European priority
- **Funding:** EUR 10B+ in EU defense tech funding flowing to Helsing, Mistral, Thales

### Risk 7: Hidden AI Costs -- Industry-Wide Headwind

If the broader AI market corrects due to disappointing ROI, Palantir's premium valuation suffers even if its own product works. The data is sobering:

| Metric | Value |
|--------|-------|
| AI Projects Over Budget | 96% |
| Average AI Infra Cost | $85K/mo |
| RAG Hallucination Rate | 17--33% |

These statistics represent the industry-wide AI deployment reality. Palantir's Ontology-constrained approach is designed to mitigate these exact problems, but if enterprise buyers become broadly skeptical of AI ROI, new customer acquisition slows regardless of Palantir's superior approach.

**The Paradox:** Industry-wide AI failure may actually *benefit* Palantir in the medium term. As companies fail with DIY AI approaches (95% failure rate per MIT), they turn to proven platforms. Palantir's pitch -- "your AI experiments failed because you lacked operational structure, and we provide that structure" -- becomes more compelling after failed alternatives. But in the short term, AI skepticism depresses the entire sector's multiples.

### Risk Summary Matrix

| Risk | Probability | Impact | Time Horizon | Mitigation |
|------|-------------|--------|--------------|------------|
| **Valuation correction** | High | Severe | 0--2 years | Organic growth may outrun multiple compression |
| **Microsoft bundling** | Medium | High | 3--5 years | 5 critical gaps; operational DNA hard to replicate |
| **LLM obsolescence of Ontology** | Low | Existential | 5--10 years | Current agent benchmarks (18--30% accuracy) validate Ontology |
| **Palantirization trap** | Medium | Medium | Ongoing | Revenue/employee rising; platform leverage proven |
| **Customer internalization** | Low | Medium | Ongoing | Continuous innovation + $10--43M switching cost |
| **European sovereignty ceiling** | High | Medium | 1--3 years | US market growth compensates; international commercial refocus |
| **AI cost/ROI backlash** | Medium | Medium | 1--3 years | Palantir benefits from "flight to proven platforms" |

### The Bear Case in One Paragraph

Palantir is a genuinely exceptional company trading at a valuation that requires genuinely exceptional outcomes. At 200x+ trailing P/E and ~50--100x P/S, the stock prices in 5--7 years of 40%+ revenue growth with no multiple compression -- something no enterprise software company has ever achieved. Microsoft is closing the "5 gaps" incrementally. European sovereignty regulations are structurally capping international growth. The Ontology moat, while deep today, faces a theoretical existential threat from improving AI agent capabilities. And the entire AI sector faces a potential reckoning as 95% of enterprise AI projects fail to deliver measurable ROI. Palantir may be the best AI company in the world and still be overvalued.

### The Bull Case in One Paragraph

Palantir has built the only operational AI platform that actually works at enterprise scale -- and the data proves it: 139% NDR, 84% gross margins, $1.01M revenue per employee, 56x expansion multiples, and acceleration from 17% growth to 56%. The AIP inflection is real and durable: US Commercial growing 109% is not a one-quarter anomaly but a fundamental shift in enterprise AI adoption. The Ontology moat is widening, not narrowing: every customer deployment makes the product better, and every AI failure in the market validates the need for structured operational platforms. The $313B market cap values Palantir at a premium because it *is* the premium -- the one company that has cracked the code on making AI operational at scale.

# ═══════════════════════════════════════════════════════════════
# PART 4: THE MARKET CONTEXT
# ═══════════════════════════════════════════════════════════════

# Part 4: The Market Context

TAM expansion, the "Service as a Software" structural shift, EU regulatory moats, sovereign cloud dynamics, and the EUR 150B+ SMB white space that Palantir cannot address.

---

## 04.1 The "Service as a Software" Structural Shift

### Core Thesis: AI Collapses the Cost of Custom Business Outcomes

The global consulting and IT services market is valued at **$5--6 trillion**. Historically, this market was untouchable by software because every engagement required bespoke human labor: strategy consultants, systems integrators, custom code, change management. AI is now collapsing the marginal cost of delivering these custom outcomes toward zero. The result is a structural shift where **services become software-addressable**---what Foundation Capital terms "Service as a Software."

This is not a marginal improvement. It is a category creation event. The entire $5--6T services market becomes the addressable universe for AI-native platforms that can deliver consulting-grade outcomes at software economics.

#### Diagram: Three Forces Converging: Service --> Software

**FORCE 1: LLM Reasoning Quality**
- API pricing dropped ~90% Mar 2023 --> late 2025
- GPT-4 cost: $30/M --> $2.50/M

**FORCE 2: AI Coding Acceleration**
- 3-5x developer productivity
- Copilot, Cursor, Claude Code
- Custom app cost collapses

**FORCE 3: Agent Orchestration**
- Multi-step autonomous workflows
- Tool use, memory, planning
- Replaces human process chains

These three forces converge into --> **"SERVICE AS A SOFTWARE"**
- $5-6 Trillion consulting/services market becomes software-addressable
- FDE model viable at $50-100K contracts (down from $1M+)

#### Key Metrics

| Metric | Value |
|--------|-------|
| LLM API pricing drop (Mar 2023 --> late 2025) | **~90%** |
| Developer productivity acceleration with AI tools | **3--5x** |
| New viable FDE contract floor (down from $1M+) | **$50--100K** |

> **Strategic Implication:** When the Forward Deployed Engineer model becomes viable at $50--100K contracts instead of $1M+, the addressable customer base expands by 10--100x. This is not a pricing change---it is a structural expansion of who can afford Palantir-grade operational AI. The question is whether Palantir will pursue this downmarket shift, or leave it to new entrants.

---

## 04.2 TAM Expansion: From $50B to Trillions

### The TAM Is Expanding Faster Than Any Single Company Can Capture

Palantir's traditional TAM---data analytics software---was approximately **$50 billion**. With the shift to enterprise AI infrastructure, analysts now size the opportunity at **$500B+** (Wedbush). But the real prize is much larger: Foundation Capital estimates that AI will unlock **$4.6 trillion** in services-to-software conversion over the next five years.

#### Diagram: Nested TAM -- From Data Analytics to the Entire Services Economy

- **SERVICE AS A SOFTWARE: $4.6T IN 5 YEARS** (Foundation Capital estimate) -- outermost layer
- **IT SERVICES SPENDING: $1.5T (2024) --> $2.3T (2028)**
- **ENTERPRISE AI INFRA: $500B+** (Wedbush estimate)
- **~$50B Traditional Data Analytics TAM** -- innermost layer

Adjacent markets:
- **AGENTIC AI:** $4.5B (2025) --> $98B (2033), 46.9% CAGR
- **AI CONSULTING:** $11B (2025) --> $91B (2035), 26.2% CAGR

Expansion multipliers:
- **10x** traditional --> AI infra
- **92x** traditional --> full SaaS

#### High-Growth Adjacent Markets

| Market | 2025 | Forecast | CAGR |
|--------|------|----------|------|
| **AI Consulting** | $11B | $91B (2035) | 26.2% |
| **Agentic AI** | $4.5B | $98B (2033) | 46.9% |
| **IT Services** | $1.5T (2024) | $2.3T (2028) | ~11% |

#### TAM Layers

| Layer | Size | Source |
|-------|------|--------|
| Traditional data analytics | **~$50B** | Industry consensus |
| Enterprise AI infrastructure | **$500B+** | Wedbush |
| Service as a Software | **$4.6T** | Foundation Capital |

> **Key Insight:** Palantir's current revenue ($2.87B in 2024) represents less than **0.06%** of the full $4.6T service-as-software opportunity. Even at 10x current scale, the company would occupy a fraction of the addressable market. This is why new entrants have massive room to build.

---

## 04.3 The $150B SMB Gap Palantir Cannot Fill

### Structural Minimum: Why Palantir Leaves 25M+ European SMEs Behind

Palantir's business model has a structural floor. The Forward Deployed Engineer model, AIP Bootcamp logistics, Gotham/Foundry platform complexity, and enterprise sales cycles combine to create a **minimum ACV of $250K--$500K**. Below this threshold, the unit economics of the Palantir model do not work---the cost of a single FDE exceeds the revenue from the contract.

In Europe alone, there are **25 million+ SMEs** that are too small for Palantir but too complex for point-solution SaaS tools. They need operational AI---integrated data, automated workflows, intelligent dashboards---but they need it at EUR 500--5,000/month, not EUR 20,000+/month.

#### Diagram: The SMB Gap -- Too Complex for Point Tools, Too Small for Palantir

**POINT SaaS TOOLS** (lower-left zone)
- Power BI, Tableau, HubSpot
- Single-function, no integration
- EUR 100-1,000/month
- Simple data problems only

**THE GAP** (middle zone, highlighted)
- 25M+ European SMEs
- Need integrated operational AI
- Cannot afford $250K+ contracts
- Too complex for point tools

**"REVERSE PALANTIR"** (target zone within the gap)
- EUR 500-5,000/month
- AI services OS for SME long tail

**PALANTIR / ENTERPRISE AI** (upper-right zone)
- Gotham, Foundry, AIP
- FDE-intensive delivery
- Min ACV: $250K-$500K
- ~600 commercial customers
- Enterprise-only economics

Axis labels: Y = Operational Complexity, X = Annual Contract Value (ACV)
ACV tick marks: EUR 1K, EUR 12K, EUR 60K, EUR 250K, EUR 1M+

### The "Reverse Palantir" Bet

A "Reverse Palantir" strategy targets the long tail: build a Palantir-grade operational AI platform, but deliver it as self-serve SaaS at SMB price points. Instead of starting with governments and going to enterprise, start with SMBs and expand up.

> **At 100,000 SMBs x EUR 12,000/year = EUR 1.2B ARR**
>
> This is roughly half of Palantir's total revenue, achieved through volume instead of contract size.

### Target Unit Economics

| Metric | Target |
|--------|--------|
| Annual ACV | **EUR 3,600--6,000** (EUR 300--500/mo) |
| CAC | **< EUR 3,000** |
| LTV:CAC ratio | **> 5:1** |
| Gross margins | **> 80%** |
| Break-even | **~500 customers at EUR 500/month** |
| Payback period | **< 12 months** |

> **Why This Gap Persists:** Palantir's entire organizational DNA is built around high-touch, FDE-driven delivery. Their sales team, compensation structure, and product architecture all optimize for $250K+ deals. Moving downmarket would require a fundamentally different GTM motion, product experience, and cost structure. This is not a decision they can make incrementally---it requires a separate product line or a separate company entirely.

---

## 04.4 EU Regulatory Landscape: Moats Made of Law

### Regulation as Competitive Advantage

The European Union has built the most comprehensive regulatory framework for data and AI in the world. For US-centric incumbents, these regulations are compliance costs. For EU-native companies, they are **structural moats**. Every new regulation raises the barrier to entry for non-European competitors and increases the premium that European enterprises will pay for sovereign-compliant solutions.

### 4.4.1 EU AI Act [Landmark Regulation]

The EU AI Act is the world's first comprehensive AI regulation. It classifies AI systems by risk level and imposes graduated obligations. For operational AI platforms---business data analytics, ontology building, workflow automation---the classification is **limited or minimal risk**, which means lighter compliance requirements. This is a structural advantage for data platforms compared to high-risk AI applications (hiring, credit scoring, law enforcement).

#### EU AI Act Implementation Timeline

| Date | Phase | Details |
|------|-------|---------|
| **Feb 2, 2025** [ACTIVE] | Prohibited practices banned | AI literacy obligations begin |
| **Aug 2, 2025** | GPAI model obligations | General-purpose AI providers must comply |
| **Aug 2, 2026 (KEY DATE)** | High-risk systems (Annex III) | Transparency & fines enforceable |
| **Aug 2, 2027** | Full scope enforcement | All AI Act provisions in full effect |

Note: Digital Omnibus may delay high-risk deadlines by up to 16 months.

| Metric | Value |
|--------|-------|
| Initial compliance cost for high-risk AI systems | **EUR 500K--2M** |
| Compliance cost for small vendors | **EUR 12K/system** |

> **Risk Classification Advantage:** Business data analysis, ontology building, and operational dashboards fall under **limited or minimal risk** classifications. This means data platforms face lighter obligations than high-risk applications (recruitment AI, credit scoring, biometrics). A "Palantir for SMBs" built around operational analytics would have a simpler compliance path than many other AI applications.

### 4.4.2 GDPR as Structural Moat

GDPR is no longer just a compliance requirement---it is a market-shaping force that creates structural advantages for European-sovereign solutions. After eight years of enforcement, the data tells a clear story.

| Metric | Value |
|--------|-------|
| Total GDPR fines since 2018 | **2,245** |
| Total fine amount since 2018 | **EUR 5.65B** |
| Fines in 2025 alone (+38% YoY) | **EUR 2.3B** |

> **Sovereign Premium:** European enterprises pay **15--25% premiums** for solutions that guarantee data sovereignty. This is not a preference---it is a procurement requirement backed by legal risk calculations.

> **Sales Cycle Advantage:** Sales cycles are **40--60% shorter** for sovereign solutions. When procurement teams can skip the 6-month legal review of US data transfer risk, deals close dramatically faster.

### 4.4.3 NIS2 Directive [Critical Infrastructure]

The Network and Information Systems Directive 2 (NIS2) classifies cloud providers as **critical infrastructure**, imposing cybersecurity obligations that cascade through the entire supply chain.

**Scope:**
- **Germany alone:** ~29,500 companies in scope
- Cloud providers, managed services, and digital infrastructure providers are "essential entities"
- **Flow-down requirement:** in-scope entities must assess the cybersecurity posture of their entire supplier chain

**Penalties:**
- **EUR 10M** or **2% of global turnover** (whichever is higher)
- Personal liability for senior management
- Mandatory incident reporting within 24 hours
- Regular security audits and penetration testing

> **Supply Chain Effect:** NIS2's flow-down provision means that even companies not directly in scope will be asked by their customers to demonstrate cybersecurity compliance. An EU-native platform built on sovereign infrastructure automatically satisfies these supplier assessment requirements, creating a default preference in procurement decisions.

### 4.4.4 DORA -- Digital Operational Resilience Act [Financial Services]

DORA entered enforcement on **January 17, 2025**, covering approximately **22,000 EU financial entities**. It creates the most prescriptive ICT risk management framework for financial services globally.

| Metric | Value |
|--------|-------|
| EU financial entities in scope | **22,000** |
| Annual turnover penalty or EUR 10M | **10%** |
| Compliance pillars required | **5** |

#### The Five DORA Pillars

| # | Pillar | Requirement |
|---|--------|-------------|
| 1 | **ICT Risk Management** | Comprehensive framework for identifying, protecting, detecting, responding to, and recovering from ICT risks |
| 2 | **Incident Management** | Classification, reporting, and management of ICT-related incidents with mandatory notification timelines |
| 3 | **Resilience Testing** | Regular testing of ICT systems including threat-led penetration testing (TLPT) for critical entities |
| 4 | **Third-Party Risk** | Monitoring and managing risks arising from ICT third-party service providers including contractual requirements |
| 5 | **Threat Intelligence Sharing** | Voluntary arrangements for sharing cyber threat information and intelligence among financial entities |

### 4.4.5 The CLOUD Act Problem [Sovereignty Threat]

The US Clarifying Lawful Overseas Use of Data (CLOUD) Act gives US authorities the legal power to **compel US-headquartered technology providers to hand over data stored anywhere in the world**---including data stored on EU soil, in EU data centers, for EU customers.

> **Microsoft CLO admitted under oath before the French Senate** that they cannot guarantee the safety of EU data from US government access requests. This testimony fundamentally changed the EU sovereign cloud procurement calculus.

> **Concrete Impact:** In **November 2025**, the International Criminal Court (ICC) replaced Microsoft Office with **OpenDesk**, a European open-source productivity suite. The stated reason: data sovereignty concerns stemming directly from the CLOUD Act. When the ICC---an institution handling the most sensitive criminal justice data in the world---decides US software is too risky, it signals a structural shift in European procurement.

### 4.4.6 SecNumCloud 3.2 [France-Specific]

SecNumCloud is the French national security certification for cloud service providers, administered by ANSSI (Agence nationale de la securite des systemes d'information). Version 3.2 is the most demanding cloud security certification globally.

**Requirements:**
- **360+ requirements** across 14 thematic areas
- Non-EU entities **cannot hold >39% of capital** in the certified entity
- **18--36 months** to achieve certification
- **EUR 500K--2M+** certification investment
- Data must remain on French soil
- No foreign law can compel data disclosure

**Currently Certified Providers:**

| Provider | Notes |
|----------|-------|
| **3DS Outscale** | Dassault Systemes subsidiary |
| **OVHcloud** | French-born cloud leader |
| **S3NS (Thales-Google)** | Joint venture structure |

**Mistral AI models** are available on SecNumCloud infrastructure via OUTSCALE---enabling sovereign AI model deployment on certified French cloud.

### Regulatory Stack: Cumulative Compliance Advantage

Each regulation compounds the advantage for EU-native, sovereign-compliant platforms.

| Regulation | Scope | Penalty | Advantage for EU-Native |
|------------|-------|---------|------------------------|
| **GDPR** | All data processing in EU | 4% global turnover / EUR 20M | 15-25% sovereign premium, 40-60% shorter sales cycles |
| **EU AI Act** | All AI systems in EU market | 7% global turnover / EUR 35M | Business analytics = minimal risk classification |
| **NIS2** | ~29,500 entities (DE alone) | 2% global turnover / EUR 10M | Sovereign infra satisfies supplier assessments |
| **DORA** | ~22,000 financial entities | 10% annual turnover / EUR 10M | EU-hosted = simpler third-party risk compliance |
| **CLOUD Act** | All US-HQ'd providers | N/A (enables US government data access) | Non-US ownership = immune to extraterritorial reach |
| **SecNumCloud 3.2** | French gov & sensitive sectors | Procurement exclusion | Certified = mandatory for French government contracts |

---

## 04.5 French AI Sovereignty Push: EUR 109B+ in Motion

### France Is Betting Big on AI Sovereignty

The February 2025 AI Action Summit in Paris catalyzed an unprecedented wave of AI investment commitments. France is positioning itself as Europe's AI leader with a multi-pronged strategy: public funding, private capital, sovereign infrastructure, and a national champion (Mistral AI).

#### Diagram: French AI Sovereignty -- Investment Flows

**FRENCH AI ECOSYSTEM** -- EUR 109B+ total commitments

| Entity | Amount | Details |
|--------|--------|---------|
| **Bpifrance** | **EUR 10B** | For AI ecosystem development. Public investment bank. |
| **France 2030** | **EUR 2.22B** | Over 5 years for AI R&D. Government innovation program. |
| **Brookfield / Data4** | **EUR 20B** | Through 2030 for data centers. Physical AI infrastructure. |
| **Fluidstack** | **EUR 10B** | 500K GPUs by 2026. GPU compute infrastructure. |

**MISTRAL AI -- NATIONAL CHAMPION**

| Attribute | Value |
|-----------|-------|
| Valuation | **EUR 11.7B** |
| Military contracts | 2026-2030 |
| GPU capacity | **18K NVIDIA Grace Blackwell** |
| SecNumCloud | Available via OUTSCALE |

**TOTAL ANNOUNCED: EUR 109B+ | Public + Private | Infrastructure + Models + Ecosystem**

France is creating the most complete sovereign AI stack in Europe.

#### Key Metrics

| Metric | Value |
|--------|-------|
| Total AI investment commitments | **EUR 109B+** |
| Mistral AI valuation (National champion) | **EUR 11.7B** |
| Fluidstack GPU target by 2026 | **500K GPUs** |

---

## 04.6 Sovereign Cloud Cost Advantage

### Sovereignty Does Not Mean Expensive

A persistent misconception in the market is that sovereign European cloud infrastructure costs more than US hyperscalers. The data tells the opposite story. Even with the SecNumCloud premium (+30%), sovereign French cloud providers cost roughly **half** of equivalent AWS configurations in the Paris region.

#### Cost Comparison: Equivalent Configuration

Comparable compute instance with similar vCPU, RAM, and storage. Monthly pricing, eu-west-3 (Paris) region.

| Provider | Monthly Cost | SecNumCloud | vs. AWS | CLOUD Act Exposure |
|----------|-------------|-------------|---------|-------------------|
| **AWS eu-west-3** | **~EUR 3,100/month** | No | --- | Yes |
| **OVHcloud** (SecNumCloud) | **~EUR 1,140/month** | Yes | **-63%** | No |
| **Scaleway** | **~EUR 1,230/month** | In progress | **-60%** | No |

> **Cost Math:** Even adding the SecNumCloud premium of +30% to the base sovereign price: **EUR 1,140 x 1.3 = EUR 1,482/month**---still **52% cheaper** than AWS. Sovereignty is not a cost penalty. It is a cost advantage with a compliance bonus.

---

## 04.7 European SMB Data Maturity: The Reality on the Ground

### Most European SMBs Are Still in the Excel Era

Before designing a "Palantir for SMBs," one must understand where European SMBs actually are in their data maturity journey. The picture is sobering: the vast majority of European SMBs are still managing their data in spreadsheets, and the adoption of even basic analytics tools remains extremely low.

#### Diagram: European SMB Data Maturity Ladder

Where 25M+ European SMEs actually stand today:

| Level | Name | Adoption | Details |
|-------|------|----------|---------|
| **Level 5** | Operational AI (Palantir-grade) | **<1%** | Top of the maturity ladder |
| **Level 4** | Big Data Analytics | **10%** | Only 10% of SMEs adopted big data analytics |
| **Level 3** | Data Analytics | **~15-34%** | 14.5% small / 33.8% medium enterprises with high digital maturity. Structured analysis, some automation. |
| **Level 2** | Basic BI Tools | **~27%** | Power BI (13.92% market share), Tableau (13.03%). Dashboards, but siloed and static. |
| **Level 1** | Spreadsheets | **83.3%** | 83.3% of SMEs use Excel/Google Sheets as primary data tool. Manual, error-prone, no automation. |

68% of SMEs cite cybersecurity/privacy barriers as primary obstacle to data adoption.

#### Key Metrics

| Metric | Value |
|--------|-------|
| SMEs using Excel as primary data tool | **83.3%** |
| SMEs that adopted Big Data Analytics | **10%** |

> **Product Design Implication:** Any platform targeting European SMBs must meet them where they are: in Excel. The product must accept CSV/XLSX imports as the primary data onboarding mechanism and deliver immediate value from spreadsheet data before attempting to sell deeper integrations. The jump from Level 1 (spreadsheets) directly to Level 5 (operational AI) must feel like a single step, not five.

---

## 04.8 French SMB Tech Success Stories: Proof the Market Works

### French B2B SaaS Has Produced Multiple Unicorns Serving SMBs

The European SMB tech market is not theoretical. Multiple French companies have built billion-euro businesses selling software to small and mid-size businesses. These companies prove that the GTM motion works, the buyer persona exists, and the unit economics are viable.

### Pennylane [Accounting]

| Metric | Value |
|--------|-------|
| Valuation | **EUR 2.2B** |
| ARR | **~EUR 100M** |

- **550 employees**
- AI-powered accounting for SMBs and accountants
- Fastest-growing French B2B SaaS
- Proof that financial SMB SaaS scales in France

### Qonto [Business Banking]

| Metric | Value |
|--------|-------|
| Valuation | **EUR 5B** |
| Revenue (+44% YoY) | **EUR 448.7M** |

- **600,000+ customers** across Europe
- **Profitable** --- rare for European fintechs at scale
- Business finance management for SMBs
- Proves massive SMB customer acquisition possible in EU

### Agicap [Cash Management]

| Metric | Value |
|--------|-------|
| Total Raised | **EUR 130M+** |
| Customers | **8,000+** |

- **50%+ revenue international** (expanded from France)
- Cash flow management and forecasting for SMBs
- Lyon-based, proving B2B SaaS works outside Paris
- Cash-centric SMB pain point resonates across EU

### Spendesk [Spend Management]

| Metric | Value |
|--------|-------|
| Total Raised | **EUR 260M** |
| ARR (profitable Q1 2025) | **EUR 50M+** |

- **Profitable since Q1 2025**
- Corporate cards, invoices, expense management
- 7,000+ mid-market customers
- Path to profitability validated in European SaaS

> **Pattern Recognition:** All four companies share a common pattern: they took a specific financial pain point (accounting, banking, cash flow, spending), built an elegant SaaS product, priced it for SMBs (EUR 50--500/month), and scaled through product-led growth supplemented by inside sales. An operational AI platform for SMBs would follow a similar GTM playbook but with a broader value proposition---the "operating system" layer that connects all these point solutions.

---

## 04.9 French E-Invoicing Mandate: The Forced Digitization Catalyst

### Every French B2B Transaction Will Generate Structured Data

France's mandatory e-invoicing regime is a once-in-a-generation forced digitization event. Starting in September 2026, every B2B invoice in France must be electronic, using the **Factur-X** format (hybrid PDF with embedded XML). This means that for the first time, **every single B2B transaction will produce machine-readable structured financial data**---regardless of the size or digital maturity of the businesses involved.

### Implementation Timeline

- **September 2026:** **All businesses must receive e-invoices.** Large enterprises (CA > EUR 800M) must also emit e-invoices. This is the big bang moment---the entire B2B economy must be ready to receive structured invoice data.

- **September 2027:** **Mid-size enterprises must emit e-invoices.** Companies with CA between EUR 10M and EUR 800M join the emission requirement. The volume of structured data flowing through the economy expands dramatically.

- **September 2028:** **All SMBs must emit e-invoices.** Full coverage. Every B2B transaction in France now generates structured Factur-X XML data. The entire economy is digitized by force of law.

> **Strategic Opportunity:** The e-invoicing mandate creates a **forced data onboarding event** for every SMB in France. Companies that have never used any software beyond Excel will suddenly have structured financial data flowing through digital systems. A platform that positions itself as the "intelligent layer" on top of this newly digitized data---providing analytics, forecasting, anomaly detection, and automated workflows---would have a natural insertion point into millions of businesses that were previously unreachable. The Factur-X XML standard means data arrives pre-structured, eliminating the biggest obstacle to AI adoption: messy, unstructured input data.

#### Key Dates

| Date | Milestone |
|------|-----------|
| **Sep 2026** | Reception obligation begins for all |
| **Sep 2027** | Mid-size emission obligation |
| **Sep 2028** | Full SMB emission obligation |

---

## 04.10 Vertical AI Benchmarks: What "Good" Looks Like

### The Best Vertical AI Companies Are Growing Faster Than Any Prior SaaS Generation

Vertical AI companies---those building AI-native products for specific domains---are achieving growth rates that were previously unthinkable in enterprise software. These benchmarks set the bar for what a European operational AI platform should aspire to.

### Top Vertical AI Companies (2025)

| Company | ARR / Revenue | Domain | Key Metric |
|---------|--------------|--------|------------|
| **Ramp** | **$1B+ ARR** | Corporate finance | AI-native expense management, massive scale |
| **Rippling** | **$570M ARR** | HR + IT + Finance | Compound platform strategy, multi-product |
| **Vanta** | **$220M ARR** | Compliance automation | ~3 years to $10M ARR, regulatory-driven growth |
| **Harvey** | **$195M ARR** | Legal AI | ~18 months to $10M ARR, fastest vertical ramp |
| **Odoo** | **$300M+ ARR** | SMB ERP (open source) | European-born, open-source, 12M+ users globally |
| **DualEntry** | Early stage | AI-native ERP | Attempting full ERP replacement with AI-first design |

### Bessemer Vertical AI Benchmarks (2025)

Bessemer Venture Partners tracks the key operating metrics of top-performing vertical AI companies.

| Metric | Value |
|--------|-------|
| Year-over-year revenue growth | **~400%** |
| Gross margins (AI-native companies) | **~65%** |
| Use hybrid pricing (seat + usage) | **92%** |

> **Pricing Model Insight:** **92% of top vertical AI companies use hybrid pricing**---combining a base seat/subscription fee with usage-based components (API calls, tokens consumed, automations run). This is a critical design choice for a European SMB AI platform: charge a predictable monthly base for the platform, then add usage fees as customers deploy more AI workflows. This aligns incentives and creates natural expansion revenue.

---

## 04.11 Three Strategic White Spaces

### Where to Build: The Gaps Nobody Has Filled

Analysis of Palantir's model, the regulatory landscape, the SMB data maturity reality, and the vertical AI benchmark data reveals three distinct strategic white spaces. Each represents a multi-billion-euro opportunity with compounding competitive moats.

### White Space 1: Mid-Market Operational AI

- **ACV:** $100K-$500K
- **Scope:** Global
- **Target:** 500-5,000 employee companies globally

No company today delivers Palantir's Ontology-style operational AI for mid-market companies (500--5,000 employees). Palantir starts at $250K+ and requires FDEs. Traditional BI tools (Tableau, Power BI) provide dashboards but not operational decision-making. The gap between "seeing a chart" and "the system recommends and executes the optimal action" remains unfilled for companies below the Palantir threshold.

A "Palantir Lite" that delivers **80% of the value at 20% of the price** could capture a market that neither Palantir (too expensive) nor BI tools (too simple) currently serve. The key is productizing what Palantir's FDEs do manually into self-serve workflows and templated ontologies.

**Moats:**
- Data network effects + switching costs
- Ontology compounds over time
- TAM: Multi-billion globally

### White Space 2: Sovereign Operational AI for EU Government

- **ACV:** $500K-$5M+
- **Scope:** EU Government
- **Target:** EU national & regional governments, defense, health

There is no European equivalent to Palantir's Gotham/Foundry for EU government use cases. European governments need operational AI for defense, healthcare administration, infrastructure management, and public safety---but they cannot use Palantir because of the CLOUD Act, sovereignty concerns, and the political optics of routing national security data through a US-headquartered company founded by a Trump-aligned billionaire.

A platform built **SecNumCloud-native + EU AI Act compliant by design** would have a structural advantage in every EU government procurement. The EUR 109B+ French AI investment commitment signals massive demand. The ICC's departure from Microsoft shows the trend is accelerating.

**Moats:**
- SecNumCloud certification
- EU AI Act compliance by design
- TAM: EUR 50B+ EU gov tech

### White Space 3: European SMB Operations Platform

- **ACV:** EUR 500-5,000/month
- **Scope:** 25M+ European SMEs
- **Target:** 25M+ European SMEs starting with France

No "Palantir for SMBs" exists. No platform integrates the operational data of small European businesses---invoices, bank transactions, inventory, CRM, HR---into a unified data layer with AI-powered insights and automated workflows. Instead, SMBs cobble together 5--15 point solutions, export CSVs into Excel, and make decisions based on gut feel and stale spreadsheets.

The opportunity is compounded by three regulatory catalysts:

- **E-invoicing mandate (Sep 2026):** forces structured data creation across all French B2B transactions
- **GDPR/NIS2:** creates 15--25% sovereign premium and procurement preference for EU-native platforms
- **EU AI Act:** business analytics classified as minimal risk, simplifying compliance

At **100,000 SMBs x EUR 12,000/year = EUR 1.2B ARR**. This is a scalable, high-margin, regulation-protected business with compounding data moats.

**Moats:**
- Regulatory compliance stack
- Data gravity + e-invoice lock-in
- TAM: EUR 150B+ (100K SMBs x EUR 12K)

### Strategic Synthesis

> All three white spaces share a common thesis: **Palantir proved the value of operational AI but designed it for a narrow market**. The structural forces of AI cost deflation, EU regulation, and forced digitization are simultaneously expanding the market and creating barriers that favor new, EU-native entrants. The question is not whether these opportunities exist---the data confirms they do. The question is who builds for them first, and whether they build a single platform that can serve all three segments or three separate companies.

### Final Summary Metrics

| Metric | Value |
|--------|-------|
| Total service-as-software opportunity in 5 years | **$4.6T** |
| European SMEs underserved by current tools | **25M+** |
| French AI investment commitments 2025 | **EUR 109B+** |

# ═══════════════════════════════════════════════════════════════
# PART 5: GTM SYNTHESIS & REPLICATION BLUEPRINT
# ═══════════════════════════════════════════════════════════════

# Comprehensive Research Synthesis: Palantir GTM, Implementation Methodology, and Spider Replication Blueprint

**Synthesized from 18 research files across 4 project phases | February 2026**

---

## Table of Contents

1. [Go-to-Market Strategy: The Bootcamp-to-Lock-In Pipeline](#1-go-to-market-strategy)
2. [Pre-GTM Playbook and Delivery Method](#2-pre-gtm-playbook)
3. [Implementation and Deployment Methodology](#3-implementation-methodology)
4. [The FDE Model, Training, Onboarding, and Alumni Network](#4-fde-model)
5. [Consulting vs. Palantir Methodology Comparison](#5-consulting-vs-palantir)
6. [Churn, Switching Costs, and Lock-In Mechanics](#6-churn-and-lock-in)
7. [Government Contracts Methodology](#7-government-contracts)
8. [Competitor Deployment Comparison](#8-competitor-comparison)
9. [The Palantir Mafia: Ex-FDE Startups](#9-palantir-mafia)
10. [Replication Blueprint: Spider as AI-Native Palantir for European SMBs](#10-replication-blueprint)
11. [Odoo/ERP Market Context in France and SMB Data Maturity](#11-odoo-erp-context)
12. [Errata and Critical Corrections](#12-errata)

---

## 1. Go-to-Market Strategy: The Bootcamp-to-Lock-In Pipeline

### The AIP Bootcamp Revolution

Palantir's go-to-market motion underwent a fundamental transformation beginning in mid-2023 with the introduction of AIP Bootcamps. These are free, immersive 1-to-5-day sessions where prospective customers work directly on the Palantir platform using their own production data. Bloomberg described them as "part hackathon, part conference, and part party." Palantir absorbs all costs as a customer acquisition mechanism.

The format brings 5-20 stakeholders into the room -- a deliberate mix of C-suite sponsors, business unit leaders, technical architects, and end-users. The Palantir team present includes 1-2 Deployment Strategists, 2-4 FDEs building prototypes in real-time, 1 Product Specialist, 1 Account Executive, and optionally a Solution Architect. The 2-4 weeks of pre-work before each bootcamp involves 3-5 calls with client stakeholders to identify promising use cases and prepare data integration.

CEO Alex Karp set "10 hours" as the benchmark: if value cannot be demonstrated in that time, the use case is wrong. The bootcamp volume scaled at remarkable speed:

- Mid-2023: approximately 50 total bootcamps
- End of 2023: 560+ bootcamps across 465 organizations
- June 2024: 1,300+ total bootcamps
- Late 2024: running at approximately 5 bootcamps per day

### Conversion Economics and Sales Cycle Compression

The analyst consensus on conversion rate (Morgan Stanley, Wedbush Securities, RBC Capital Markets) is approximately 22%, not the 30-50% initially estimated in Phase 1 research. This means approximately 78% of bootcamp engagements do not convert. The estimated cost per bootcamp to Palantir is $12K-$36K (loaded personnel cost for 1-5 days with 5-8 people), producing a Customer Acquisition Cost per converted customer of $110K-$165K. Initial ACV from conversions typically runs $200K-$500K (median $250K-$350K).

The non-conversion breakdown (speculative, from analyst modeling): data readiness failures (25-30%), budget/procurement blockers (20-25%), internal politics (15-20%), use case mismatch (10-15%), competitive displacement (5-10%), and timing issues (10-15%).

The sales cycle compression is dramatic. Pre-bootcamp, Palantir's average sales cycle ran 9+ months (per S-1 filing), with the S-1-era median around 264 days and an average deal size of $835K. Post-bootcamp, CRO Ryan Taylor stated the cycle compresses to approximately 6 weeks from bootcamp to signed contract. New U.S. commercial customer acquisition rose sequentially from 4% in Q2 2023 to 12% in Q3 to 22% in Q4 of the same year.

### The Acquire/Expand/Scale Revenue Flywheel

Palantir's entire commercial model runs on a three-phase revenue flywheel that justifies deliberate losses during acquisition.

**Acquire Phase**: Initial ACV of $100K-$500K. FDEs are heavily on-site, sometimes living in the client's city. Contribution margin is negative. The 2019 cohort data from the S-1 filing shows $600K average first-year revenue per customer against $65.4M total contribution loss across the new cohort. Palantir knowingly invests in every new relationship.

**Expand Phase**: ACV grows to $1M-$5M+. The ontology spreads to 2nd and 3rd departments. Margin trajectory improves from -43% to +35% as platform leverage kicks in and FDE intensity decreases. This is where the ontology moat compounds -- each new department connected increases switching costs exponentially.

**Scale Phase**: ACV reaches $5M-$20M+. Enterprise-wide deployment. FDE presence is minimal -- mostly maintenance plus new use case consultation. Contribution margin reaches +55%. The client's own teams build most new applications on the platform.

The average expansion multiple is 59x: an initial $100K contract grows to $5.6M in mature annual contract value. This is the economic engine justifying negative acquisition margins.

### Net Dollar Retention Trajectory

NDR tells the AIP story most clearly. It was declining through 2023, hitting 107% by Q3 2023. Then:

| Quarter | NDR |
|---------|------|
| Q3 2023 | 107% |
| Q1 2024 | 114% |
| Q3 2024 | 120% |
| Q3 2025 | 134% |
| Q4 2025 | 139% |

The 32-percentage-point improvement in roughly two years reflects explosive within-account expansion. Customer retention sits at approximately 98% as of 2024.

### Case Studies Demonstrating the Funnel

**Nebraska Medicine**: First bootcamp in January 2024, production in 6 weeks, 2,000% increase in Discharge Lounge utilization, 1,200+ AI-drafted insurance appeal letters, 10+ AIP applications in Year 1, converted to multi-year multi-million dollar contract.

**Fortune 100 CPG Company**: Integrated 7 ERP systems into a unified digital twin in a 5-day bootcamp, projecting $100M in year-1 operational savings.

**Tampa General Hospital**: Palantir became "the fabric of our health system operating system."

**Land O'Frost**: Reduced production planning from 40 hours to 30 minutes (98.75% reduction).

**Unnamed Utility Company**: ACV grew from $7M to $31M in one year (+343%).

**Unnamed Healthcare System**: 2 bootcamps led to a $96M total contract value.

**Lear Corporation**: Scaled from 100 users and 4 use cases to 16,000 users and 280 use cases.

---

## 2. Pre-GTM Playbook and Delivery Method

### Revenue and Customer Metrics

Palantir's financial trajectory demonstrates the machine's output:

| Metric | Value |
|--------|-------|
| 2025 Revenue | $4.48B |
| Revenue Growth (2025) | 56% YoY |
| U.S. Commercial Revenue Growth (Q4 2025) | 137% YoY |
| Customer Count (Q4 2025) | 954 |
| Average Revenue per Customer | ~$4.7M |
| GAAP Gross Margin (2025) | ~84% |
| Adjusted Operating Margin (Q4 2025) | 57% |
| Rule of 40 Score | 127% |
| Free Cash Flow (2025) | $2.3B adjusted |
| Total Remaining Deal Value | $11.2B |
| Revenue per Employee (2025) | ~$1.01M-$1.1M |

### Sales Force Structure

Palantir's approach is deliberately unusual: sales comprises just 3% of headcount (~195 employees out of 4,414 as of September 2025). Engineering represents approximately 44% of employees. CEO Alex Karp famously said he would only build a sales team "if investors forced him to," and he personally spent approximately 250 days per year on the road closing and maturing deals.

Enterprise Account Executives earn a median OTE of $280K with a 49/51 base-variable split. Approximately 34% hit quota. The pricing structure includes Gotham at $141,000 per server core perpetual license (per GSA pricing) with $28,000/core annual maintenance, and Foundry also priced per core. AIP uses usage-based pricing across compute, storage, and ontology volume. Multi-year agreements of 3-5 years are standard.

### Deal Velocity Post-AIP

Concrete deal progressions show the accelerated funnel: a $3M contract expanded to an enterprise-wide agreement within the same quarter; one of the largest U.S. home construction companies went from startup to pilot to conversion of a $40M+ multiyear deal in a single quarter; a medical device manufacturer signed a multiyear expansion just 5 months after initial contract, increasing ACV more than eightfold; Q4 2025 saw 180 deals above $1M, 84 above $5M, and 61 above $10M.

---

## 3. Implementation and Deployment Methodology

### The Ontology: Core Architecture

The Ontology is the architectural element that transforms Palantir from a data analytics vendor into an operating system. It functions as an operational layer sitting atop all integrated digital assets, connecting datasets and models to their real-world counterparts.

**Semantic Layer**: Defines Object Types (Patient, Vehicle, Transaction), Properties (name, timestamp, status -- supporting up to 2,000 properties per object type), and Link Types (relationships between objects).

**Kinetic Layer**: Defines Action Types specifying how objects can be modified, with built-in validation rules, approval workflows, and audit trails. All writes must go through Action Types, preventing ad hoc data modifications.

**Dynamic Layer**: Governs security controls, role-based access, and enforcement logic.

Building an Ontology follows a systematic process: raw data is ingested from source systems using Palantir's Magritte connector framework (SAP, Oracle ERPs, CRMs, IoT sensors, Snowflake, Databricks, document stores, custom APIs). Data is cleaned and transformed using Pipeline Builder (visual/low-code) or code repositories. Datasets are mapped to Object Types via the Ontology Manager. Applications, dashboards, AI agents, and workflows are built on top.

### FDE-to-Self-Service Graduation Curve

**Commercial Customers**:
- Heavy FDE (0-6 months): FDEs lead all development, build initial ontology, create first production applications
- Co-Development (6-18 months): Client teams begin building alongside FDEs
- Guided Autonomy (18-36 months): Client teams build most applications independently
- Self-Sufficient (36+ months): Client fully autonomous; platform support only

**Government Customers**: Same progression but with extended timelines (0-12, 12-24, 24-48, 48+ months) driven by security clearance requirements and ATO processes.

**Revenue Breakdown by Engagement Maturity** (estimated):
- Fully self-service: 25-35% of revenue (mature customers, 3+ years on platform)
- Hybrid model: 45-55% (some FDE support, mostly client-driven)
- Heavy FDE engagement: 15-20% (new deployments, complex government work)

Case studies: Airbus Skywise reached 50,000+ users across 100+ airlines with 85-90% self-service after approximately 2-3 years of FDE engagement. US Army Vantage reached 50,000+ users with 60-70% self-service. NHS Federated Data Platform (GBP 330M contract) is at 20-30% self-service in early deployment.

### AI-Assisted Forward Deployment

AI automation within Palantir's deployment process now covers (confirmed from AIPCon 2024 demos):
- Schema/ontology mapping from existing data sources: HIGH automation
- Data pipeline creation and configuration: HIGH
- Workshop application generation from natural language: MEDIUM-HIGH
- Code generation for data transforms: HIGH (reducing boilerplate by 80%+)

Tasks still requiring humans: client relationship management and stakeholder alignment, complex business logic requiring deep domain expertise, security architecture design for classified/regulated environments, change management and organizational adoption, and edge cases requiring contextual judgment about data quality.

Before/after economics: time to first prototype compressed from 2-4 months to 5 days; time to first production deployment from 6-18 months to 1-3 months; FDE person-months per deployment from 12-60 to 2-6; engagements each FDE can handle per year from 1-2 to 5-15+.

CTO Shyam Sankar's claims: "SAP ERP migrations that used to take years now take two weeks"; "Planning processes reduced from 160 hours to 10 minutes"; "Root cause analysis accuracy went from <20% to >99%."

FDE labor cost per $1M ARR has dropped from approximately $700K (2016) to $280K (2020) to an estimated $80K-$150K (2025).

---

## 4. The FDE Model, Training, Onboarding, and Alumni Network

### Profile and Hiring

FDEs (internally codenamed "Delta") are Palantir's atomic unit of delivery. The ideal candidate has 1+ year post-college experience, with a median age of approximately 25. Academic backgrounds skew toward top CS programs (Stanford, MIT, CMU), but Palantir actively recruits from philosophy, mathematics, and physics backgrounds. The company's own description emphasizes "unusual sensitivity to social context" -- the ability to read a room, navigate organizational politics, and translate unspoken client needs into technical requirements.

The interview process takes approximately 36 days with a 1-2% acceptance rate. The signature interview is the "Decomposition Interview" testing the candidate's ability to break down complex problems.

### FDE Reading List (confirmed from former FDE interviews)

All new FDEs receive:
- **Impro** (Keith Johnstone) -- on improvisation and status dynamics
- **The Looming Tower** (Lawrence Wright) -- foundational context for intelligence community origins
- **Interviewing Users** (Steve Portigal) -- user research techniques
- **Getting Things Done** (David Allen) -- personal productivity system

This reading list reveals Palantir's philosophy: FDEs are improvisers, intelligence analysts, user researchers, and project managers rolled into one.

### Onboarding and Training

New FDEs undergo a multi-week internal bootcamp covering ontology design, with production access from day 1 and a 3-6 week paired placement with a senior FDE. The training emphasizes learning by doing in production environments rather than classroom theory.

### Compensation

| Level | Base Salary | Total Comp (incl. equity) |
|-------|-------------|---------------------------|
| Entry-Level FDE | $135,000 - $200,000 | $171,000 - $415,000 (median $215,000) |
| Senior FDE | $200,000 - $300,000 | $500,000 - $800,000 |

FDE services are listed on the UK G-Cloud framework at GBP 150,000 per person per quarter (equivalent to approximately $750,000 USD per FDE per year).

### Team Structure

Estimated 1,000-1,500 FDEs out of 4,414 total employees (25-35% of headcount). Typical team size per customer deployment is 4-5 engineers. Total headcount has been growing, not declining, despite AI automation: 3,838 (2023) to 3,950 (2024) to 4,414 (September 2025) -- a 15%+ increase. This is Jevons Paradox in action: AI made each FDE more productive, so Palantir hired more to handle more engagements.

### The R&D vs. COGS Classification

FDE costs are classified as R&D, not Cost of Revenue -- a strategic accounting decision confirmed in the S-1 filing. Palantir argues FDE insights feed back into platform development, justifying R&D classification. The result: FDE labor does not reduce gross margin. Michael Burry publicly argued this classification inflates gross margins. If reclassified to COGS, 2024 gross margin would drop from the reported 82-84% to approximately 79%.

### Deployment Strategists ("Echoes")

Internally codenamed "Echo," Deployment Strategists are recruited from ex-McKinsey, BCG, and Bain backgrounds. They are a hybrid of management consultant, sales engineer, product manager, and account strategist. Typically 1-2 per bootcamp engagement. Their most critical function: determining which use case to build first -- the "Goldilocks zone" that is technically feasible within days, visibly impactful to executives, and extensible enough to seed the ontology for future use cases.

### Industry Adoption

FDE job postings across the technology industry grew 800-1,000% in 2025 (LinkedIn data). Companies adopting the model include OpenAI, Anthropic ("Applied AI Engineers"), Scale AI, Ramp (15 FDEs in pods), and Databricks (now building its own FDE teams).

---

## 5. Consulting vs. Palantir Methodology Comparison

### The Structural Inversion

Traditional MBB (McKinsey, BCG, Bain) consulting and Palantir's delivery model represent fundamentally different approaches to creating enterprise value.

**MBB Engagement**: 8-12 weeks, $500K-$1.25M, leverage pyramid structure (Partner/Engagement Manager/Associate/Business Analyst). Deliverable is slides and recommendations. Knowledge is captured in consultant brains and PowerPoint decks. Revenue model is purely time-based billing. Handoff occurs at engagement end with implementation left to the client.

**Palantir Model**: 1-5 day bootcamp followed by ongoing deployment. Deliverable is running production software. Knowledge is embedded in the platform's ontology. Revenue model is software subscription with services bundled. No handoff -- continuous build with FDE presence that gradually decreases.

Key replacement dynamics: slides replaced by software, handoff replaced by continuous build, pyramid replaced by pod (1 Deployment Strategist + 2-4 FDEs), McKinsey's PDNet knowledge management replaced by product-embedded knowledge.

### The Accenture Partnership as Validation

The December 2025 Accenture-Palantir partnership (2,000+ Accenture professionals trained on Palantir) represents the "Accenture Paradox" -- selling and deploying AI tools that reduce demand for traditional consulting services. Accenture's bet: the AI consulting and implementation market grows faster than traditional consulting shrinks ($11B in 2025 projected to $91B by 2035, 26% CAGR).

Consulting firms are not dying but transforming. Accenture's GenAI revenue in FY2025 reached $2.7B (tripled from prior year). BCG's AI revenue hit $2.7B (20% of total revenue). McKinsey's AI/digital-related revenue is approximately 40% of total. Traditional consulting (strategy decks, process redesign) is declining while AI-powered consulting (deployment, integration, change management) is booming.

---

## 6. Churn, Switching Costs, and Lock-In Mechanics

### Five Layers of Lock-In

Palantir creates switching costs through five reinforcing mechanisms:

1. **Technical Lock-In**: The Ontology represents the organization's entire data universe with typed properties, relationships, actions, and security rules. No standard export format exists. Reimplementation requires reverse-engineering thousands of object types, links, and business rules.

2. **Operational Lock-In**: Downstream applications (dashboards, workflows, AI agents) all read from the Ontology. Removing the Ontology breaks every application simultaneously. Daily operational decisions depend on the platform.

3. **Contractual Lock-In**: Multi-year agreements of 3-5 years are standard. Usage-based pricing means switching requires rebuilding the entire compute and pipeline infrastructure.

4. **Regulatory Lock-In**: In government and regulated industries, Palantir holds FedRAMP High, IL5/IL6, and CMMC Level 2 certifications. Replacing the platform requires a new vendor to achieve the same certifications -- a process that can take 12-24 months.

5. **Knowledge Lock-In**: Decision data accumulates over time, creating a compounding knowledge asset. Trade secrets and institutional knowledge are exposed to and embedded in the platform. Staff become trained and proficient on Palantir's tools. This human capital lock-in is often the most powerful.

### Estimated Switching Costs

Switching costs range from $10M to $43M per enterprise client (estimated as 1-3x annual spend), with an 18-36 month reimplementation timeline. Morningstar published a report titled "Worth the Hype: Palantir's Ontology, Switching Costs Warrant Quadrupling of Our Fair Value Estimate."

### Confirmed Departures (Pre-Ontology Maturity)

Major confirmed departures all occurred during 2015-2017, before the Ontology was fully mature:
- **Coca-Cola** (2016): Ended after pilot; Palantir's approach deemed too heavy for CPG analytics
- **American Express** (2016): Departed after multi-year engagement
- **Nasdaq** (2015-16): Ended relationship
- **Home Depot** (2017): Chose internal capabilities
- **NYPD** (2017): Ended contract; political and budget factors
- **JPMorgan** (2017): Built internal data platform instead

No major enterprise departures have been publicly confirmed since the Ontology matured post-2018 and AIP launched in 2023.

---

## 7. Government Contracts Methodology

### Contract Vehicles and Scale

Palantir's government business uses specialized contract vehicles designed for rapid procurement:

**Other Transaction Authority (OTA)**: Exempts from standard Federal Acquisition Regulation (FAR), enabling faster procurement. Used for Army TITAN ($823M) and other defense contracts.

**Indefinite Delivery/Indefinite Quantity (IDIQ)**: Framework agreements with maximum ceilings against which individual task orders are placed. Army Enterprise Systems Architecture (ESA) is a $10B/10-year IDIQ.

**UK G-Cloud**: Framework listing at GBP 66K/core for Foundry, GBP 150K/person/quarter for implementation services, GBP 3M/year organization license.

### Largest Contracts

| Contract | Value | Agency |
|----------|-------|--------|
| Army ESA | $10B / 10 years | U.S. Army |
| Maven | $1.3B | DoD |
| TITAN | $823M | U.S. Army |
| Vantage | $618.9M | U.S. Army |
| ICE contracts | $248.3M cumulative | DHS |
| NHS FDP | GBP 330M | UK NHS |
| UK MoD | GBP 240.6M cumulative | UK Ministry of Defence |
| Total UK | GBP 670M across 34 contracts | Multiple UK agencies |

### Certifications

FedRAMP High authorization, IL5/IL6 authorization (Department of Defense classified environments), CMMC Level 2 certification. These certifications create a regulatory moat: competitors must achieve the same authorizations before they can even compete for these contracts, a process taking 12-24+ months.

---

## 8. Competitor Deployment Comparison

### No Competitor Has Built an Equivalent to the Ontology

The cross-competitor analysis reveals that while multiple companies compete with individual Palantir capabilities, none has replicated the Ontology as an operational layer.

**Dataiku**: 5-50x cheaper than Palantir, positioned as "significantly cheaper and less intense to deploy." Has a visual data pipeline and ML model management. Lacks an operational layer -- users can analyze data but cannot trigger business processes through the platform. Competes on analytics, not operations.

**Databricks**: Engineering-first platform with the strongest data lakehouse architecture. Now hiring its own "FDEs" to mimic Palantir's deployment model. Has Unity Catalog for governance and is building AI/BI capabilities. Lacks operational write-back and ontology-like semantic layer. Competes on data engineering and ML infrastructure.

**Snowflake**: 850+ partners in its ecosystem, dominant in cloud data warehousing. No ontology, no operational layer. Pure analytical infrastructure. Snowflake Cortex adds AI capabilities but remains query-focused rather than action-focused.

**Microsoft Fabric**: The biggest distribution threat. Power BI at EUR 9.40/user/month offers analytics capabilities overlapping with Palantir's dashboarding. Microsoft's integration across Office 365, Azure, Dynamics, and Copilot gives it unmatched enterprise distribution. However, Microsoft cannot automate specific operational workflows -- it is too horizontal. The threat is not that Microsoft will build an ontology, but that "good enough" analytics bundled with existing Microsoft subscriptions will reduce the perceived need for a specialized platform.

**C3.ai**: 130+ pre-built AI applications but struggling operationally -- revenue declined 19% YoY as of August 2025.

### The Palantir Differentiation

The fundamental advantage: Palantir is the only platform that combines data integration, semantic modeling (Ontology), operational write-back (Actions), security governance (Dynamic Layer), and AI capabilities (AIP) in a single platform. Competitors offer subsets. The CTO's summary: "Our advantage comes down to Ontology. It's really an advantage on the AI demand side. Now that LLMs have showed up, you can leverage them in a way no one else can."

---

## 9. The Palantir Mafia: Ex-FDE Startups

### Scale of the Network

The "Palantir Mafia" encompasses 170+ startups founded by alumni, having collectively raised $24B+, producing 9+ unicorns. 59% of founders have engineering backgrounds; 15% went through Y Combinator; 31% launched since 2020. Nabeel Qureshi's claim: "there are usually more ex-Palantir founders than there are ex-Googlers in each YC batch, despite there being ~50x more Google employees."

### Notable Alumni Startups

| Company | Founder(s) | Raised / Valuation | Sector |
|---------|-----------|-------------------|--------|
| **Anduril** | Palmer Luckey, Trae Stephens | $3.8B raised | Defense technology |
| **ElevenLabs** | Piotr Dabkowski | $11B valuation | AI voice synthesis |
| **Ironclad** | Jason Boehmig | $3.2B valuation | Legal contract management |
| **Chapter** | Cobi Blumenfeld-Gantz | Unicorn | Medicare enrollment |
| **SpaceX** (key hires) | Multiple alumni | N/A | Aerospace |

### Support Infrastructure

- **Palumni**: Dedicated VC fund investing in alumni startups
- **8VC** (Joe Lonsdale, Palantir co-founder): Dedicated vehicles for alumni companies
- **XYZ VC**: Maintains focus on Palantir alumni network
- Average FDE tenure: 3.2 years; 35% leave within first year; 2.7/5 work-life balance rating on Glassdoor

The alumni network functions as a deliberate talent export machine: FDEs learn to be "startup CTOs" at Palantir, then leave to build companies that often become Palantir customers or complement the ecosystem.

---

## 10. Replication Blueprint: Spider as AI-Native Palantir for European SMBs

### The Core Thesis

Spider aims to be an AI-native version of Palantir's Ontology-driven platform targeting European SMBs (specifically French PMEs in the EUR 1-50M revenue range) at EUR 500-5,000/month. The fundamental innovations versus Palantir:

1. **AI agents replace 45-55% of FDE work** (corrected from the initial 65-80% estimate) for standard deployments
2. **Free scan replaces expensive bootcamp**: Connect to Odoo via API, auto-generate ontology, identify 3-5 automation opportunities in 2-4 hours (cost: EUR 10-20 in LLM API calls vs. Palantir's $50K-100K bootcamp)
3. **Self-service onboarding eliminates the deployment bottleneck**: Guided wizard where a non-technical business owner connects Odoo, selects industry template, reviews AI-generated ontology, activates pre-built workflows -- target under 1 day with less than 2 hours of human involvement
4. **ERP bridge turns existing Odoo data into instant ontology seed**: Odoo's PostgreSQL schema (~500+ tables in standard install) with well-known entities enables AI agents with Odoo domain knowledge to convert it into a functional ontology within hours

### Target Market

France's approximately 150,000-200,000 PMEs in the EUR 1-50M revenue range. However, the Phase 4 errata corrects this: the realistic addressable market (companies with both ERP/structured data systems AND EUR 10-100M annual revenue) is 50,000-100,000 European companies. The "25M European SMEs" headline was always a fantasy.

Estimated French TAM: approximately EUR 2.25B for SMB data and analytics tools. At EUR 1,000/month ARPA, EUR 1M ARR requires 84 clients; EUR 5M ARR requires 417 clients.

### Technology Stack

- **Database**: PostgreSQL as single data backbone (already Odoo's database), using JSONB columns for lightweight ontology (entity_types, entities, relationships, actions tables). pgvector for semantic search replacing LanceDB.
- **LLM**: Mistral AI as primary for GDPR-sensitive operations and sovereignty narrative (Mistral Large for complex analysis, Mistral Small for routine tasks, self-hosted Mistral Nemo 12B for complete sovereignty). Claude as premium reasoning backend.
- **Infrastructure**: Scaleway Kapsule (managed Kubernetes) with ArgoCD for GitOps, Kong Gateway for API routing, namespace-per-tenant isolation. Infrastructure serves 50 customers at EUR 1,500-2,500/month total cost.
- **Open-source assembly** (70%): PostgreSQL, Kubernetes, Kong, ArgoCD, React, Nango (SaaS integrations), Metabase (embedded BI), pgvector.
- **Custom-built IP** (30%): Ontology Engine, AI Process Mapper, Agent Orchestration Layer, Custom Odoo Connector, Tenant Configuration system.
- **MVP development cost**: EUR 40-70K for Year 1.

### Unit Economics

At EUR 1,000/month ARPA:
- Onboarding cost: EUR 2,500-5,000 (32-64 hours human work + EUR 180-350 AI API costs)
- Monthly cost to serve: EUR 160-450 per client
- Year 1 gross margins: 55-70%
- Year 2 gross margins: 80-85%
- Payback period: 4-6 months
- LTV/CAC ratio: exceeds 10x

At EUR 500/month, margins thin to 30-40% in Year 1 with 6-10 month payback -- the danger zone.

### Go-to-Market Sequence

**Phase 1 (March-August 2026)**: Prove the Jordan/Com Prive use case (EUR 1.6M advertising agency with triple data entry pain). Target 5-10 paying customers at EUR 500-2,000/month by month 6. Start with operations automation, not analytics.

**Phase 2 (September 2026-February 2027)**: Build repeatable playbook. Integration templates for French SMB tool stack (Pennylane, Odoo, Sellsy/HubSpot, Google Workspace, Microsoft 365). Target 15-30 customers, EUR 15-30K MRR.

**Phase 3 (March 2027-February 2028)**: Service-to-software transition. Self-service onboarding wizard. Target 50-100 customers, EUR 100-200K MRR. Fundraising trigger: seed round of EUR 2-3M.

**Phase 4 (March 2028-2029)**: Platform and ecosystem. Marketplace of integrations and templates. Partner channel through Odoo integrators.

### Competitive Positioning

Spider occupies genuine whitespace: no competitor serves France's 150,000+ PMEs with an integrated data-intelligence-automation platform. Microsoft Fabric is too horizontal. Dataiku is too expensive (EUR 50K-200K+/year). Metabase is free for basic BI but offers no data transformation, AI agents, or process automation. Palantir cannot profitably serve EUR 6K-60K/year deal sizes.

Spider's moat is process knowledge, not technology. The tacit understanding of how a French advertising agency routes data between Google Sheets, Notion, and Pennylane -- and the ability to automate that specific workflow -- is something no horizontal platform can replicate.

The European sovereignty narrative strengthens the positioning: 63% of European IT decision-makers cite data sovereignty as "important" or "critical." Spider's "100% French stack" (Scaleway, Mistral, French-built platform) is a genuine procurement advantage.

### Critical Risks

1. **Nathan's focus diffusion** (Very High probability, Critical impact): Simultaneously running Drakkar, Spider, Spider Content, Influence Lab, and multiple events
2. **Financial fragility** (High, Critical): Drakkar's EUR 70K EBITDA provides essentially no margin for R&D
3. **Market readiness** (Medium-High, High): French SMBs may not pay for AI operations platforms
4. **Competitive platform moves** (High, Medium): Microsoft Copilot + Power BI could make basic analysis free
5. **Single-point-of-failure CTO** (High, Critical): Entire technical infrastructure depends on one person at EUR 4K/month

---

## 11. Odoo/ERP Market Context in France and SMB Data Maturity

### Odoo Market Position

Odoo has reached 15M users globally, EUR 650M ARR, EUR 5B valuation, growing at 42%, targeting EUR 1B revenue by 2027. In France, there are approximately 800-1,368 Odoo customers with 123 official partners. France is the 2nd or 3rd largest Odoo market globally.

The broader French ERP market is valued at $3.49B (2024), projected to reach $6.40B by 2030 at 9.7% CAGR.

### Odoo API Ecosystem

A critical technical detail: Odoo's XML-RPC API is deprecated in Odoo 19 and will be fully removed in Odoo 20 (expected fall 2026), replaced by JSON-2 API. This is a breaking change for any integration built on XML-RPC. Rate limits: SaaS instances throttled at approximately 1 call/sec; self-hosted instances have no rate limiting.

Schema auto-discovery is possible via ir.model and ir.model.fields endpoints. Odoo's standard install contains 500+ tables organized around well-known entities. An AI agent can auto-discover the schema with 90%+ accuracy because Odoo follows conventions (res_partner, sale_order, account_move).

**Nango does NOT support Odoo** -- Spider must build a custom connector. This is actually an advantage: the custom Odoo connector becomes part of Spider's IP.

### French E-Invoicing Mandate

The French government mandates electronic invoicing beginning September 2026 (reception) and September 2027 (emission for PMEs). This is driving ERP adoption across French SMBs and creates a natural entry point for Spider.

### European SMB Data Maturity -- The Sobering Reality

Eurostat 2024 data reveals extremely low data maturity across European SMBs:

| Metric | Value |
|--------|-------|
| EU enterprises (10-49 employees) using Excel as primary analytical tool | 83.3% |
| Using any form of business analytics software | 14.5% |
| Using any AI technology (including basic ML) | 8.9% |
| AI tool adoption among French SMBs specifically | 26% (France Num survey) |
| SMBs reporting zero ERP customization (using defaults) | 44.8% |
| French cloud adoption | 22.9% vs 38.9% EU average |
| French AI adoption | 5.9% vs 8.0% EU average |

Gartner reports 87% of SMBs have low BI maturity; 70-90% rely on Excel as their primary data tool.

The implication: Spider must CREATE data structure, not just consume it. The first 3-6 months of any deployment involves data engineering -- connecting ERP systems, normalizing formats, building the foundational data layer. The value proposition must start with "we will organize your data" before "we will give you insights from your data."

For SMB deployments, change management is critical: the CFO is the likely champion, time-to-first-value must be under 4 weeks, and the product must work within the "Excel + email" reality rather than demanding the customer adopt an entirely new paradigm.

### Odoo Implementation Costs (Context for Spider Pricing)

For a 50-user company: approximately $80K-130K first-year total ($50K-100K upfront implementation + $50K recurring). Only 49.7% of ERP implementations finish on schedule; only 46.4% complete within budget.

---

## 12. Errata and Critical Corrections

Phase 4 research identified 10 corrections that materially change the picture presented in earlier phases. These are not minor adjustments -- they collectively redefine the opportunity.

### Correction #1: FDE Automation Rate
- **Original**: 65-80% of FDE work can be automated by AI
- **Corrected**: 45-55% for standard deployments; 30-40% for complex/custom deployments
- Implication: Plan for a team of 8-15 deployment engineers, not 3-5

### Correction #2: ACV Compression
- **Original**: AI agents can compress ACV down to $5K-$50K for SMBs
- **Corrected**: Minimum viable ACV is $300K-$750K even with maximum automation
- Former Palantir CFO Colin Anderson: "The model is only financially sustainable for seven-figure contracts and above"
- Implication: SMBs under EUR 10M revenue are structurally unreachable with the FDE model. Any "Palantir for SMBs" must either radically redesign delivery to be self-service from day one, or target mid-market (EUR 10-100M revenue) instead.

### Correction #3: TAM
- **Original**: 25M+ European SMEs as addressable market
- **Corrected**: 50,000-100,000 companies with both ERP systems AND EUR 10-100M revenue
- A 250-500x reduction. The "long tail of European SMBs" narrative collapses.

### Correction #4: AI Agent Readiness
- **Original**: AI agents are an imminent structural unlock
- **Corrected**: Best AI agent score on real-world tasks (APEX benchmark, 2025): 29.8%. Gartner predicts 40% of agentic AI projects canceled by 2027. MIT study: 95% of AI pilots fail to reach production. RAND Corporation: 80% of AI projects fail overall.
- Human deployment teams remain essential for at least 2-3 more years.

### Correction #5: Bootcamp Conversion Rate
- **Original**: 30-50% conversion from bootcamps
- **Corrected**: ~22% (analyst consensus from Morgan Stanley, Wedbush, RBC)
- CAC per converted customer rises to $110K-$165K (from the initial $45K-$75K estimate)

### Correction #6: Gross Margin Trajectory
- **Original**: 68% to 84% purely through automation and platform maturity
- **Corrected**: GAAP gross margin improved only 81% to 84% (3pp) in 2 years. Approximately 50% of improvement is genuine operational leverage; 50% is accounting-related. Adjusted for FDE reclassification: ~79%.

### Correction #7: FDE Headcount
- **Original** (implied): FDE headcount is declining
- **Corrected**: Growing. Total headcount: 3,838 to 3,950 to 4,414 (+15%). Jevons Paradox: AI is a scaling tool, not a cost-cutting tool.

### Correction #8: "AI Kills Consulting" Narrative
- **Original**: AI will structurally destroy consulting
- **Corrected**: AI consulting market growing $11B to $91B (26% CAGR). Accenture GenAI revenue: $2.7B. BCG AI revenue: $2.7B. McKinsey AI/digital: ~40% of total. Consulting is transforming, not dying.

### Correction #9: European SMB Data Maturity
- **Original** (implied): European SMBs are "ready" for data platforms
- **Corrected**: 83.3% still on Excel; only 8.9% use any AI; 44.8% zero ERP customization. You cannot build an ontology from data that does not exist in structured form.

### Correction #10: Self-Service Revenue Ratio
- **Original** (implied): Most revenue from self-service customers
- **Corrected**: Only 25-35% fully self-service. 3+ year timeline to self-service maturity. Palantir is NOT yet a pure SaaS company.

### The Meta-Correction

Taken together, the 10 corrections tell a single story: the Palantir model is more defensible than initially thought -- and therefore harder to replicate. The moat is not just software; it is accumulated human expertise, customer relationships, deployment methodology, and institutional knowledge built over 20 years and $3B+ in cumulative R&D spend. A startup can build a narrower, faster version targeting European mid-market, but must be honest about the human capital, time, and ACV constraints involved. The opportunity is real but smaller, slower, and more human-intensive than Phase 1 research suggested. That is not a death sentence -- it is a realistic foundation for building something that actually works.

---

## Source Files

1. `/Users/nathanmenard/code/SpiderOS/researches/spider-strategy/01-initial-research/00a-claude-pre-gtm-machine.md`
2. `/Users/nathanmenard/code/SpiderOS/researches/spider-strategy/01-initial-research/00b-claude-pre-gtm-delivery-playbook.md`
3. `/Users/nathanmenard/code/SpiderOS/researches/spider-strategy/01-initial-research/00c-gpt-pre-gtm-playbook-FR.md`
4. `/Users/nathanmenard/code/SpiderOS/researches/spider-strategy/01-initial-research/02-claude-implementation-gtm.md`
5. `/Users/nathanmenard/code/SpiderOS/researches/spider-strategy/01-initial-research/02-gpt-implementation-gtm.md`
6. `/Users/nathanmenard/code/SpiderOS/researches/spider-strategy/01-initial-research/05-claude-replication-blueprint.md`
7. `/Users/nathanmenard/code/SpiderOS/researches/spider-strategy/01-initial-research/05-gpt-replication-blueprint.md`
8. `/Users/nathanmenard/code/SpiderOS/researches/spider-strategy/03-claude-agent-research/08-research-odoo-france-erp-market.md`
9. `/Users/nathanmenard/code/SpiderOS/researches/spider-strategy/03-claude-agent-research/10-research-odoo-api-ecosystem.md`
10. `/Users/nathanmenard/code/SpiderOS/researches/spider-strategy/03-claude-agent-research/12-research-palantir-churn-switching-lockin.md`
11. `/Users/nathanmenard/code/SpiderOS/researches/spider-strategy/03-claude-agent-research/12-research-palantir-competitors-deployment-comparison.md`
12. `/Users/nathanmenard/code/SpiderOS/researches/spider-strategy/03-claude-agent-research/12-research-palantir-government-contracts.md`
13. `/Users/nathanmenard/code/SpiderOS/researches/spider-strategy/03-claude-agent-research/13-research-palantir-fde-training-onboarding.md`
14. `/Users/nathanmenard/code/SpiderOS/researches/spider-strategy/03-claude-agent-research/13-research-palantir-mafia-ex-fde-startups.md`
15. `/Users/nathanmenard/code/SpiderOS/researches/spider-strategy/06-deep-research-phase2/13-research-consulting-vs-palantir-methodology.md`
16. `/Users/nathanmenard/code/SpiderOS/researches/spider-strategy/06-deep-research-phase2/14-research-smb-data-platform-deployment.md`
17. `/Users/nathanmenard/code/SpiderOS/researches/spider-strategy/05-final-synthesis/part-b-consulting.html`
18. `/Users/nathanmenard/code/SpiderOS/researches/spider-strategy/05-final-synthesis/part-d-errata.html`


# ═══════════════════════════════════════════════════════════════
# APPENDIX: VISUAL ATLAS — QUICK REFERENCE
# ═══════════════════════════════════════════════════════════════

# The Complete Palantir Playbook -- VISUAL ATLAS

**Product - Delivery - Commercial - Market**

Everything you need to understand and replicate Palantir's model, in diagrams.

## Hero Stats

| Metric | Value |
|--------|-------|
| FY2025 Revenue | $4.475B |
| Net Dollar Retention | 139% |
| Customers | 954 |
| Expansion Multiple | 56x |
| Gross Margin | 84% |
| Rev/Employee | $1.01M |

---

## // 01 -- The Big Picture

Three interlocking systems: BUILD the platform, DELIVER to customers, SELL the expansion. Feedback loops connect all three columns.

### BUILD Column

1. **Data Sources** -- ERP, CRM, IoT, APIs, files
2. **Connectors** -- 150+ native - 3 architectures
3. **Pipelines** -- Spark / Flink / DuckDB / Polars
4. **Ontology** -- 6 primitives - 3 layers (Semantic + Kinetic + Dynamic)
5. **AI / AIP** -- 50+ models - tool-use agents
6. **Apps** -- Workshop / Slate / OSDK
7. **Actions** -- Writeback to source systems

- CLOSED LOOP (writeback arrow from Actions back to Data Sources)

### DELIVER Column

1. **Lead Gen** -- AIPCon, inbound, outbound
2. **Qualification** -- Scoping call 60-90 min
3. **Bootcamp** -- 5 days - FREE - 22% conv.
4. **Pilot (Acquire)** -- 90 days - $100-500K - -43% margin
5. **Expand** -- Yr 1-3 - $1-5M - +35% margin
6. **Scale** -- Yr 3+ - $5-20M+ - +55% margin
7. **CoE (Self-Service)** -- Client builds 70-85% of apps

### SELL Column

1. **S&M 21% of Revenue** -- Down from 47% in 2020
2. **Acquire: Negative Margin** -- $100-500K ACV, -43% margin
3. **Expand: +35% Margin** -- $1-5M ACV, NDR 139%
4. **Scale: +55% Margin** -- $5-20M+ - 56x expansion
5. **$1.01M / Employee** -- $4.475B Revenue -- $7.19B FY26 Guide

### Cross-Column Feedback Arrows

- BUILD -> DELIVER: platform (Ontology powers bootcamp)
- DELIVER -> SELL: convert (Conversion feeds revenue)
- SELL -> BUILD: revenue funds R&D -> platform improvement
- DELIVER -> BUILD: FDE field insights

---

## // 02 -- The Four Platforms

Four interlocking platforms that layer on each other. Gotham now runs ON Foundry. Apollo is the cross-cutting deployment backbone.

### GOTHAM
- 2008 - Intelligence & Defense
- Graph, Gaia, Browser, Dossier
- Five Eyes, NATO, US Army $10B
- Runs on Foundry

### FOUNDRY
- 2016 - Commercial OS
- 150+ microservices - Rubix K8s
- Primary revenue driver

### AIP
- 2023 - AI Layer
- 50+ models - AIP Logic - Agent Studio
- LLMs reason over typed Ontology objects

### APOLLO (Cross-cutting CI/CD)
- 360K deploys/month
- 300+ environments
- 3.5 min deploy time
- <20 engineers
- Hub-spoke model
- Constraint-based pull
- FedRAMP High, IL5/IL6

### Key Insight
LLMs receive typed Ontology objects, NOT raw text. AI sees "Order #4521 status=pending, amount=12,500 EUR"

### Platform Timeline
- 2008: Gotham
- 2016: Foundry
- 2020: Apollo
- 2023: AIP

---

## // 03 -- The Ontology Stack

Bottom-to-top architecture from raw data to user-facing applications. The Ontology is the nucleus through which all data is accessed, all actions executed, all AI reasons.

### Stack (bottom to top)

1. **Raw Data Sources** -- Databases - APIs - Files - Streaming - IoT - SaaS
2. **Data Connection -- 150+ Connectors** -- Direct Ingest - Agent-Based Proxy - Air-Gapped Worker
3. **Pipeline Builder & Code Repos** -- 80+ transforms - 300+ functions - 7 join types - raw -> clean -> semantic
4. **THE ONTOLOGY**
   - **SEMANTIC** layer -- Objects, Links, Properties -- "What exists in the world?"
   - **KINETIC** layer -- Actions -- writeback, functions, webhooks, streaming flows
   - **DYNAMIC** layer -- Guardrails -- RBAC, markings, cell-level ACL, audit, provenance
   - 6 Primitives: Object Types, Properties, Link Types, Action Types, Interfaces, Functions
5. **AI / AIP -- 50+ Models - Tool-Use Architecture** -- AIP Logic (no-code) - Agent Studio - 4-level guardrails - model-agnostic
6. **Applications** -- Workshop (50+ widgets) - Slate - Contour - OSDK - Quiver

### OSS Equivalents (right column)

| Layer | OSS Equivalent | Replicability |
|-------|---------------|---------------|
| Applications | Retool / Appsmith | ~65% replicable |
| AI/AIP | LangChain / LlamaIndex | ~60% replicable |
| Ontology | **No OSS Equivalent** | **~30% replicable** |
| Ontology Core IP | typed entities + actions + functions + security + real-time index | -- |
| Pipeline Builder | Dagster / Airflow | ~80% replicable |
| Data Connection | Airbyte (~300 connectors) | ~75% replicable |
| Raw Data | Spark / Flink / DuckDB | ~95% replicable |

---

## // 04 -- Workshop Widget Universe

50+ widgets organized by category. Workshop is Palantir's primary low-code app builder, operating entirely on Ontology objects.

### DISPLAY Widgets
- Object Table
- Object List
- Object View
- Property List
- Links
- Object Set Title
- Markdown
- Media Preview
- PDF Viewer
- Data Freshness
- Edit History
- Action Log Timeline
- Image Annotation
- Audio & Transcription

### VISUALIZATION Widgets
- Chart XY (bar, line, scatter)
- Pie Chart
- Vega Chart (custom)
- Gantt Chart
- Map (MapboxGL)
- Pivot Table
- Metric Card (KPI)
- Timeline
- Stepper
- Status Tracker
- Spreadsheet Display
- Free-form Analysis

### FILTERING Widgets
- Filter List
- Object Dropdown
- String Selector
- Date & Time Picker
- Text Input
- Numeric Input
- Exploration Filter Pills
- Exploration Search Bar
- Prominent Term
- User Select

### AIP / AI Widgets
- AIP Agent (chat)
- AIP Analyst
- AIP Generated Content
- AIP Interactive
- Button Group (actions)
- Inline Action (forms)
- Media Uploader
- Comments
- Tabs

### EMBEDDING Widgets
- Iframe (bidirectional)
- Embedded Module
- Custom Widgets (React)

### VARIABLE SYSTEM
12 types: Object Set, Filter, String, Numeric, Boolean, Date, Timestamp, GeoPoint, GeoShape, Array, Struct, TimeSeries

### LAYOUT
Module > Pages > Sections > Widgets - Lazy evaluation - Visual dependency graph

---

## // 05 -- The Delivery Pipeline

Horizontal timeline with role-based swimlanes, from first contact to client autonomy.

### Swimlane Roles
- **DS / Echo** (Deployment Strategist)
- **FDE / Delta** (Forward Deployed Engineer)
- **AE** (Account Executive)
- **Client**

### Phases

| Phase | Duration | DS/Echo | FDE/Delta | AE | Client |
|-------|----------|---------|-----------|-----|--------|
| PRE-SALES | 2-4 weeks | Scoping calls | -- | Qualify & pitch | -- |
| PRE-BOOT | 2-4 weeks | Use case select | Data prep, starter ontology | -- | Provide data |
| BOOTCAMP | 5 days - FREE | Facilitate & frame | Build prototype (live, real data) | Day 1 + Day 5 | Co-build & stress test |
| POST-BOOT | 48h + 8-12 wk | Weekly calls | -- | Commercial proposal | -- |
| PILOT | 90 days - $100-500K | Stakeholders | Build production (3-10 apps, 10-30 pipes) | -- | Co-dev & train (3-tier training) |
| EXPAND | Yr 1-3 - $1-5M | -- | New depts (50-100+ objects) | -- | Co-build (50-70% client) |
| SCALE | Yr 3+ - $5-20M+ | -- | -- | -- | 70-85% self-service |
| CoE | self-service | -- | -- | -- | Autonomous (3-10+ people) |

### Key Metrics
- **22% Convert** -- avg deal >$1M
- **MARGIN trajectory:** -43% (Pilot) -> +35% (Expand) -> +55% (Scale)

---

## // 06 -- Bootcamp Day-by-Day

5-day intensive. Cost to Palantir: $12-36K. Cost to client: FREE. The most consequential GTM innovation since founding.

### DAY 1 -- Executive Framing
- Problem framing workshop
- "Art of the Possible" demo
- AI intuition session
- Data reality check
- Select 1-2 use cases
- **DELIVERABLES:** Use-case slate, Process flow diagrams, Data inventory, Min viable ontology design
- 70%+ stakeholder time

### DAY 2 -- First Vertical Slice
- Pipeline Builder transforms
- Ontology Manager setup
- First Workshop app
- "Walking skeleton"
- Real data, not mock
- **DELIVERABLES:** Working pipeline, 5-15 object types, 5-20 link types, Workshop skeleton app

### DAY 3 -- AIP Logic
- Ontology Actions setup
- AIP Logic integration
- AIP Assist embedded
- LLM-powered workflows
- **DELIVERABLES:** 2-3 end-to-end workflows, 1+ LLM function/agent, Full Workshop app
- Strongest emotional moment

### DAY 4 -- Stress Test & Polish
- War-gaming by domain experts
- Failure categorization
- AIP Evals & Observability
- Polish & bug-fix
- Demo narrative prep
- **DELIVERABLES:** Eval suite, Failure mode register, Hardened prototype
- Most collaborative day

### DAY 5 -- Executive Readout
- Live demo (not slides)
- ROI projection
- Deployment roadmap
- 5-10 senior stakeholders
- 45-60 min incl. Q&A
- **DELIVERABLES:** Executive summary, Technical assessment, ROI 3 scenarios, Phased roadmap

### Bottom Line
Cost to Palantir: **$12-36K** - Cost to Client: **FREE** - Team: 2-5 Palantir + 5-20 client stakeholders - ~5 bootcamps/day globally - 1,300+ total (mid-2024)

---

## // 07 -- Pilot 90-Day Gantt

4 overlapping phases transforming a signed contract into a production system. Pod: 3-5 people. ACV: $100-500K. Margin: -43%.

### Phase 1: Discovery (W1-W3)
- 10-30 interviews
- Stakeholder mapping, data inventory, use-case select

### Phase 2: Ontology (W2-W7)
- 15-40 sources, 3-10 connected
- Pipeline build, ontology design (3-5 iterations), 10-30 pipelines

### Phase 3: Apps (W4-W11)
- 3-10 apps, 5-15 dashboards
- Action types, security config (7 layers), Workshop apps, AIP integration

### Phase 4: Handoff (W7-W12)
- 3-tier training
- Power users (8-40h), operators (2-8h), executives (30-60min), go-live

### Pod Composition
- **1-2 DS** + **2-3 FDSE** - FDE: 50-70 hr/week, 50-80% travel - ACV: **$100-500K** - Margin: **-43%** - Deliberately unprofitable

---

## // 08 -- The FDE Model

Palantir's atomic unit of delivery. Not consultants -- they build production software, not slide decks.

### Traditional Consulting (MBB) vs Palantir FDE Model

| Dimension | Traditional Consulting (MBB) | Palantir FDE Model |
|-----------|-----------------------------|--------------------|
| Structure | Pyramid: Partners > Managers > Analysts | Flat pod: Echo (DS) + Delta (FDE) + Delta (FDE) + AE |
| Deliverable | Slides | Working software |
| Engagement | Handoff then done | Continuous, embedded, on-site |
| Revenue Model | Billable hours model | Software license model (not billable hours) |
| Code | No code shipped | Ship code |
| Knowledge | Knowledge leaves | Knowledge stays in the Ontology |
| Duration/Cost | 6-9 month engagements, $2-10M | -- |

### Pod Roles
- **Echo (DS):** ex-MBB, strategy
- **Delta (FDE):** ~25 yo, build fast, Stanford/MIT, ship code
- **AE:** kickoff + demo day

### FDE Compensation
$171K-$415K entry - 4-5 per client - Glassdoor: 2.7/5 WLB

### FDE Reading List
Impro (Johnstone) - Looming Tower - Interviewing Users - Getting Things Done

### Alumni Network
170+ startups - $24B raised - 9+ unicorns - Anduril, Affirm, OpenAI - 15% via YC

### Industry Impact
FDE job postings grew 800-1,000% (2025) - 33%+ clients never needed FDEs (2024)

### R&D Classification
FDE costs split across COGS + S&M + R&D - Adjusted gross margin ~79% vs reported 84%

### FDE Graduation Curve
- 0-6 mo: FDE 80-90%
- 6-18 mo: Co-development
- 18-36 mo: Guided autonomy
- 36+ mo: Self-sufficient (70-85%)

---

## // 09 -- Financial Flywheel

Deliberately lose money on acquisition, compound through expansion, achieve 55%+ margins at scale. The entire model in one loop.

### Flywheel Stages

1. **ACQUIRE** -- $100-500K ACV -- NEGATIVE margin
2. **EXPAND** -- $1-5M ACV -- -43% -> +35%
3. **SCALE** -- $5-20M+ ACV -- +55% margin
4. RE-INVEST (loops back to ACQUIRE)

### Center Metrics
- NDR 139%
- 56x expansion
- $1.01M/employee
- 84% gross margin
- Rule of 90

### Revenue Trajectory

| Year | Revenue | Notes |
|------|---------|-------|
| FY19 | $0.74B | |
| FY20 | $1.09B | |
| FY21 | $1.54B | |
| FY22 | $1.91B | |
| FY23 | $2.23B | AIP launch |
| FY24 | $2.87B | |
| FY25 | $4.48B | |
| FY26G | $7.19B | (Guidance) |

### Additional Metrics
- Q4 TCV: $4.3B (+138%)
- FCF margin: 82%
- RDV: $5.4B+
- US Comm: +137% YoY
- S&M: 21% of rev (down from 47% in 2020)

---

## // 10 -- Lock-In Pyramid

Seven reinforcing layers of switching cost. Estimated switch: $10M-$43M. All confirmed departures were pre-2018 and never for a superior alternative.

### Layers (easiest to hardest)

| Layer | Name | Description |
|-------|------|-------------|
| 7. (top, easiest) | Political | Executive sponsors, champions |
| 6. | Contractual | Multi-year, expansion clauses, 3-5% escalators |
| 5. | Integration Complexity | 150+ connectors, 50-150+ sources connected |
| 4. | Training Investment | 5-50+ CoE people, certifications |
| 3. | Workflow Dependency | 50-200+ Workshop apps, no export |
| 2. | Data Gravity | Years of integrated data, audit trails, history |
| 1. (bottom, hardest) | **ONTOLOGY (30% replicable -- no OSS equivalent)** | Core IP |

**Switching Cost: $10M-$43M**

---

## // 11 -- Competitive Map

2-axis positioning: product standardization vs. client size. White space: mid-market operational AI, EU sovereign ops, SMB platform.

### Axes
- X-axis: Product Standardization (Services -> Software)
- Y-axis: Client Size (SMB -> Gov/Ent)

### Competitive Positioning

| Company | Ticker | Revenue | Position |
|---------|--------|---------|----------|
| Palantir | PLTR | $4.5B | Top-right (Gov/Ent, Software) |
| Databricks | DBRICKS | $5.4B | Mid-right |
| Snowflake | SNOW | $3.6B | Mid-right |
| Microsoft | MSFT | -- | Top-right (Existential Risk #1) |
| Dataiku | DTKU | ~$200M | Mid-center |
| C3.ai | C3.ai | -- | Upper-center |
| Accenture | ACN | $69.7B | Top-left (Services) |
| McKinsey | MBB | -- | Upper-left (Services) |
| Retool | RETL | -- | Lower-right (SMB, Software) |
| n8n | n8n | -- | Lower-right (SMB) |
| Anduril | ANDRL | $30.5B | Upper-center |
| Scale AI | SCLE | -- | Upper-center |
| Helsing | HLSNG | -- | Upper-left |
| ChapsVision | CHAPS | -- | Upper-left |

### White Space
- Mid-market operational AI
- EU sovereign operations
- SMB platform play
- Min ACV ~$300K even with max AI

---

## // 12 -- EU Regulatory Timeline

Regulation wave 2024-2028. Every new regulation is a procurement trigger for compliant platforms.

### Timeline

| Regulation | Effective | Description |
|-----------|-----------|-------------|
| GDPR | ongoing | -- |
| NIS2 | Oct 2024 | Cybersecurity for critical infrastructure |
| DORA | Jan 2025 | Digital operational resilience for financial sector |
| EU AI Act | Feb 2025 -> Aug 2027 phased | Prohibited AI -> High-risk AI -> Full compliance |
| E-Invoicing France | Sep 2026/27/28 phased | -- |
| SecNumCloud 3.2 | -- | French sovereign cloud certification |

### Context
EUR 109B French AI investment - Sovereign cloud costs ~50% of AWS - ChapsVision replaced Palantir at DGSI - "European Palantir" = Helsing

---

## // 13 -- TAM Visualization

Nested circles from total addressable market to Palantir's current revenue. The gap between $4.5B and $4.6T is the opportunity.

### Nested TAM

| Market Layer | Size | Source |
|-------------|------|--------|
| Services as Software | $4.6T | Foundation Capital thesis |
| Enterprise AI Infra | $500B | Wedbush Securities |
| Agentic AI by 2033 | $98B | -- |
| Data Analytics | ~$50B | -- |
| **Palantir Today** | **$4.5B** | -- |

### Market Context

- **954 customers** vs. ~2,000 Global 2000 companies = barely scratching the surface
- **AI Consulting Market:** 2025: $11B, 2035 projected: $91B (26% CAGR)
- **SMB Gap:** 50K-100K EU companies with ERP + EUR 10-100M revenue. Min ACV $300K = structurally unreachable for most SMBs
- **Defense TAM:** US Army TITAN: $823M, NATO expansion ongoing

---

## // 14 -- Key Numbers

The most important metrics in one view. All from FY2025 actuals unless noted.

| Metric | Value | Detail |
|--------|-------|--------|
| FY2025 Revenue | $4.475B | +56% YoY |
| Net Dollar Retention | 139% | Q4 2025 |
| Total Customers | 954 | +34% YoY |
| Expansion Multiple | 56x | $100K to $5.6M |
| GAAP Gross Margin | 84% | ~79% adjusted |
| Revenue per Employee | $1.01M | 4,414 staff |
| Bootcamps | 1,300+ | mid-2024, ~5/day |
| Bootcamp Conversion Rate | ~22% | (est.) |
| Apollo Deploys/Month | 360K | <20 engineers |
| Microservices per Foundry Instance | 150+ | -- |
| Native Data Connectors | 150+ | 3 architectures |
| AI Models | 50+ | model-agnostic gateway |
| Alumni Startups | 170+ | $24B raised |
| FY2026 Revenue Guidance | $7.19B | +61% |
| Q4 2025 TCV Bookings | $4.3B | +138% YoY |

---

## // 15 -- 7-Step Closed Loop

"BI tools stop at step 6. Palantir closes the loop." The defining architectural pattern -- writeback to source systems.

### 7 Steps

1. **Sources** -- ERP, CRM, IoT, APIs, files, DBs
2. **Connectors** -- 150+ native, 3 architectures
3. **Pipelines** -- raw -> clean -> semantic, 80+ transforms
4. **Ontology** -- 6 primitives, typed objects, 3 layers
5. **AIP / Agents** -- 50+ models, tool-use pattern
6. **Applications** -- Workshop, Slate, 50+ widgets
7. **Actions** -- WRITEBACK to source systems, closes the loop

### CLOSED-LOOP WRITEBACK
Arrow from step 7 (Actions) back to step 1 (Sources)

### Comparison

| Model | Flow |
|-------|------|
| **Traditional BI (stops at step 6)** | Sources -> Pipelines -> Dashboard -> END (read-only, no writeback) |
| **Palantir (closes the loop)** | Sources -> Ontology -> AI -> App -> Action -> Sources (operational) |

BI stops here: at step 6 (Applications).

---

## // 16 -- AIP Guardrails Architecture

Four levels of AI safety built into the platform. The AI inherits the invoking user's permissions -- no privilege escalation possible.

### 4 Security Levels (outermost to innermost)

**LEVEL 4: Staging Review**
Human approves before execution. Actions staged for review.

**LEVEL 3: Permission-Bounded**
AI inherits invoking user's permissions. No privilege escalation.

**LEVEL 2: Tool Scoping**
Only explicitly configured tools are visible. Cannot discover others.

**LEVEL 1: Constrained Action Types**
AI can ONLY perform explicitly listed Action Types. Cannot discover, invoke, or execute any operation not whitelisted.

**AI AGENT** (at center)

### Agent Tools

| Tool | Description |
|------|-------------|
| Query Objects | Search and retrieve Ontology objects |
| Apply Actions | Execute Ontology Action Types (writeback) |
| Call Function | Invoke typed Ontology Functions (TS/Py) |
| Calculator | Arithmetic without LLM approximation |

- Only whitelisted tools accessible
- LLMs receive typed Ontology objects, NOT raw text

---

## // 17 -- NDR & Expansion Trajectory

Net Dollar Retention recovery from 107% trough (Q3 2023) to 139% (Q4 2025). The AIP bootcamp inflection is clearly visible.

### NDR Data Points

| Quarter | NDR | Color |
|---------|-----|-------|
| Q3'23 | 107% | (trough) |
| Q1'24 | 114% | |
| Q3'24 | 120% | |
| Q3'25 | 134% | |
| Q4'25 | **139%** | (current) |

- 100% baseline marked
- AIP launch annotation: Apr 2023

### Expansion by Cohort

| Year | Expansion Multiple |
|------|-------------------|
| Year 1 | 1.0x |
| Year 2 | 1.3-1.5x |
| Year 3 | 2.0-2.5x |
| Year 5 | 3.5-6.0x |
| Year 7+ | 8-10x+ |
| **Mature** | **56x ($100K -> $5.6M)** |

### Case Studies
- **Nebraska Medicine:** 2,000% lounge util. increase
- **Land O'Frost:** 40h -> 30 min (98.75%)
- **Unnamed utility:** $7M -> $31M ACV (+343%)
- **Fortune 100 CPG:** 7 ERPs unified in 5 days
- **General Mills:** $14M/yr (40K$/day)
- **Healthcare:** 2 bootcamps -> $96M TCV

---

## // 18 -- Partnerships & Ecosystem

Transitioning from vertically integrated delivery to platform with ecosystem. Accenture partnership is the most significant signal.

### Implementation Partners (left)
- **Accenture** -- 2,000+ trained pros, $69.7B rev, Dec 2025 partnership
- **Deloitte** -- Implementation & advisory
- **Booz Allen Hamilton** -- Gov/defense focused

### Platform/Tech Partners (right)
- **AWS** -- Cloud infra & marketplace, Apollo: ~$100/install/month
- **Developer Ecosystem** -- build.palantir.com (free), Certifications (Dec 2025)
- **3rd-Party** -- Ontologize, CodeStrap, PVM

---

## // 19 -- Pricing Architecture

No public standard pricing. Visible via UK G-Cloud framework and AWS Marketplace. Perceived as 2-5x more expensive than alternatives.

### Typical Deal Structure Progression

| Stage | Name | ACV | Term | Scope |
|-------|------|-----|------|-------|
| 1 | Pilot | $100K - $500K | 3-6 months | 1-2 use cases, Single team |
| 2 | Platform | $500K - $2M | 12-month term | 3-5 use cases, multiple teams |
| 3 | Expansion | $2M - $10M | Multi-year | Department-wide, cross-functional |
| 4 | Enterprise | $10M - $50M+ | 3-5 year term | Organization-wide platform |

### Published Pricing (UK G-Cloud & Public)

| Product | Price | Source |
|---------|-------|--------|
| Gotham (per core) | $141K/core + $28K/core/yr maint. | US GSA Schedule |
| Foundry (per core) | GBP 66K/core/yr | UK G-Cloud |
| FDE Services | GBP 150K/person/quarter (~$760K/yr) | UK G-Cloud |
| Org License | GBP 3M/yr (unlimited users) | UK G-Cloud |
| Apollo Standalone | ~$100/install/month | Azure Marketplace |
| AIP | "We have no pricing strategy for AIP" -- Karp | Usage-based, land-grab |

---

## // 20 -- Landmark Contracts

Key deals that define Palantir's market position. From intelligence to healthcare to manufacturing.

### GOVERNMENT
- **$10B** -- US Army Enterprise Service (75 prior contracts)
- **$823M** -- US Army TITAN Program
- **GBP 330M** -- NHS Federated Data Platform
- Five Eyes intelligence alliance
- NATO - US SOCOM - Space Force
- Ukraine battlefield intelligence
- US Gov +45% YoY
- 61 deals >$10M in Q4 alone

### COMMERCIAL
- **Airbus Skywise** -- 50K+ users, 100+ airlines, 85-90% self-service
- **General Mills** -- $14M/yr ($40K/day) impact
- **Lear Corporation** -- $30M+ savings H1 2025
- **Unnamed Utility** -- $7M -> $31M ACV in one year
- US Commercial +137% YoY
- Top-20: $94M/customer TTM

### HEALTHCARE
- **Nebraska Medicine** -- 2,000% lounge utilization - 1,200+ AI letters - 10+ apps in Year 1
- **Tampa General Hospital** -- "Fabric of our health system OS"
- **Unnamed Healthcare System** -- 2 bootcamps -> $96M TCV
- **Land O'Frost** -- Planning: 40h -> 30 min (98.75% cut)
- **Panasonic Energy** -- Gigafactory waste reduction, 100K+ ticket search

---

## // 21 -- Apollo Architecture

Constraint-based pull model. Spokes operate autonomously even when disconnected. The invisible backbone making 300+ environments possible with fewer than 20 engineers.

### APOLLO HUB
- Declarative desired-state Plans
- Constraint propagation - Version coordination
- <20 engineers manage everything

### Spokes

| Spoke | Description | Connectivity |
|-------|-------------|-------------|
| CLOUD | AWS, Azure, GCP -- Commercial regions | PULL |
| GOV CLOUD | AWS GovCloud, Azure Gov -- FedRAMP High, IL5/IL6 | PULL |
| ON-PREM | Customer data centers -- Bare-metal, VMware | PULL |
| AIR-GAPPED | Physically isolated networks -- No internet connectivity | AUTONOMOUS PULL |
| EDGE | Vehicles, submarines, FOBs, drones -- Break-glass emergency override | AUTONOMOUS PULL |

### Key Metrics

| Metric | Value |
|--------|-------|
| Deploys/month | 360K |
| Environments | 300+ |
| Deploy time | 3.5 min |
| Rollback time | <5 min |
| Engineers | <20 |
| Standalone price | $100/install/month |

---

## // 22 -- 7 Architectural Principles

Established during Gotham development, carried forward into every subsequent platform. This IS the Palantir DNA.

### The 7 Principles

**1. Ontology-Centric**
All data modeled as typed entities with properties and relationships. The ontology IS the product.

**2. Security First-Class**
Cell-level ACL, mandatory markings woven INTO the data model. Not bolted on.

**3. Orchestrate, Don't Replace**
Sits ON TOP of ERP/CRM/SCADA. Ingests and unifies their data. Never replaces source systems.

**4. Human-in-the-Loop**
AI augments, never fully replaces. Critical decisions require human review. 4-level guardrails enforce this.

**5. FDE Model**
Engineers embedded on-site to configure and operate platform. Deployment model IS the strategy.

**6. Edge / Air-Gap Ready**
Every component functions in disconnected environments. Submarines to FOBs.

**7. Full Provenance Tracking**
Every data point traceable to source. Every access audited. Unbroken chain of custody.

### Key Quotes

> "Sets a standard very hard for any other company to meet." -- Karp, on competitive moat

> "SAP ERP migrations that used to take years now take two weeks." -- Sankar, on AI deployment speed

> "The bottleneck is no longer technology, it's organizational willingness to change." -- Sankar

> "The ontology is the immune system of the enterprise." -- Sankar, on ontology as self/non-self distinction

---

## // 23 -- Revenue Per Employee & AI Leverage

Jevons Paradox in action: AI makes FDEs more productive, so Palantir hired MORE, not fewer. Revenue per employee crossed $1M.

### Revenue Per Employee Trajectory

| Year | Rev/Employee |
|------|-------------|
| 2020 | $448K |
| 2022 | $578K |
| 2024 | ~$800K |
| 2025 | **$1.01M** |

### Jevons Paradox -- AI did NOT reduce headcount:

| Year | Employees |
|------|-----------|
| 2023 | 3,838 |
| 2024 | 3,936 |
| 2025 | 4,414 (+15%) |

### AI Deployment Economics

| Metric | Before | After |
|--------|--------|-------|
| Time to first prototype | 2-4 mo | 5 days |
| Time to production | 6-18 mo | 1-3 mo |
| FDE person-months | 12-60 | 2-6 |
| Engagements per FDE/yr | 1-2 | 5-15+ |

### FDE Labor Cost per $1M ARR
- ~$700K (2016)
- ~$280K (2020)
- ~$80-150K (2025)

Revenue grew 4.1x while COGS grew only 35%

---

## // 24 -- Compute Architecture

Multi-engine by design. The platform selects the right engine based on data volume and processing mode.

### Engines

| Engine | Mode | Use Cases | Data Scale |
|--------|------|-----------|------------|
| Apache Spark | BATCH | Large-scale ETL, Historical reprocessing, ML feature engineering | GB to TB+ distributed |
| Apache Flink | STREAMING | Real-time event processing, CDC (Change Data Capture), Continuous aggregations | Continuous streams |
| DuckDB / Polars | IN-PROCESS | Fast analytical queries, No cluster overhead, Columnar analytics | MB to low GB |
| Virtual Tables | PUSHDOWN | Query sent to external engine (Snowflake, Databricks, BQ), Data never moves | Any size, federated |
| Mesa | PROPRIETARY | Constraint-solving, Scheduling, routing, Allocation problems | Optimization |

### Engine Selection Logic
Data >10GB batch -> Spark - Continuous stream -> Flink - Data <10GB analytical -> DuckDB - External warehouse -> Virtual Tables - Optimization -> Mesa

### Code Environments
Python/PySpark, Python/Pandas, Python/Polars, SQL, Java, TypeScript (Functions), Mesa

---

## // 25 -- Security Model

The most sophisticated element and the hardest to replicate. Cell-level ACL, mandatory markings, and AI execution-context controls.

### 7-Layer Defense (bottom to top)

| Layer | Name | Description |
|-------|------|-------------|
| Layer 1 | Dataset / Project RBAC | Resource-level permissions - Full audit logging - Provenance tracking |
| Layer 2 | Mandatory Markings (MAC) | Binary markings travel WITH data - Inherited through all pipelines |
| Layer 3 | Row-Level Security (RLS) | Dynamic row predicates - Per-object row-level filtering |
| Layer 4 | Column-Level | Property suppression per user/group - Restricted views with predicates |
| Layer 5 | Cell-Level ACL | Row + column intersection control - AES-256-GCM encryption at rest & transit |
| Layer 6 | Action-Level | Per-action execution permissions - Validation rules - Submission criteria |
| Layer 7 | App-Level | Per-application access controls - Module visibility - Workshop permissions |

Markings auto-propagate: derived data inherits union of markings from all source data -- prevents "downhill" flow

### AI Execution Security

**Identity Context**
AI agent operates under the invoking user's identity. No privilege escalation.

**Purpose Context Scoping**
AI access further restricted to a specific purpose beyond user perms.

**Anti-Exfiltration**
Prevents AI from becoming cross-domain data exfiltration channel.

**Link-Visibility Semantics**
Prevents inference of classified objects via traversal, edge counts, exists queries.

**OSS replicability: ~40% (Apache Ranger + OPA)**

---

## // 26 -- Valuation Context

Market cap ~$313B at $132/share. Rule of 90. Both the bull and bear cases in one view.

### BULL CASE

| Signal | Detail |
|--------|--------|
| Rule of 90 | 56% growth + 34% adj. operating margin |
| $7.19B FY26 guide | +61% YoY growth on $4.5B base |
| US Comm +137% YoY | One of fastest growth re-accelerations ever |
| NDR 139% and rising | Expansion flywheel accelerating |
| FCF margin 82% | $1.15B free cash flow in Q4 alone |
| 954 of ~2,000 G2K | "Barely scratching the surface" -- Karp |
| AIP as wedge product | Compressed 9-mo sales cycle to 6 weeks |
| Defense moat widening | $10B Army, TITAN, NATO, Ukraine |
| $4.6T TAM thesis | Services as Software (Foundation Capital) |
| Cash: $5.2B+ | No debt, zero dilution risk |

### BEAR CASE

| Risk | Detail |
|------|--------|
| P/S ~44-70x | 3-5x comparable software companies |
| P/E ~210x trailing | Extreme valuation premium |
| Margin inflation | Burry: FDE costs inflate margin 84% vs 79% |
| SBC ~$500M/yr | Stock-based comp still significant |
| FDE structural ceiling | Jaluria (RBC): TAM limited by bespoke model |
| MSFT bundling threat | "80% of use cases at 20% of cost" |
| EU sovereignty risk | ChapsVision replaced PLTR at DGSI |
| -36% from ATH | $132 vs $207 peak (Feb 2025) |
| Jaluria PT: $50 | Implies ~62% downside from current |
| Burry: $912M puts | 50K put options, reportedly up ~35% |

---

## Footer

Based on FY2025 actuals, patent filings, earnings calls, SEC filings (S-1, 10-K), UK G-Cloud pricing, AIPCon presentations, former employee interviews, and public documentation. Confidence levels: CONFIRMED = primary sources | ESTIMATED = triangulated | SPECULATIVE = single-source inference. Generated February 2026. 26 sections. 25 SVG diagrams. 1 metrics grid.
