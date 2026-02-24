# Palantir Technologies Patents: Comprehensive Analysis of Implementation Details

**Research Date:** 2026-02-17
**Sources:** Google Patents, USPTO, Justia Patents, AOIR Academic Research, CB Insights

---

## Executive Summary

Palantir Technologies holds 3,438+ patents globally (2,608 granted, 80%+ active), with 1,701 applications filed at USPTO alone (95.08% grant rate). Their patent portfolio reveals concrete implementation details far beyond marketing materials -- exposing internal architecture decisions around ontology data models, transaction systems, pipeline mechanics, deployment infrastructure, security classification handling, and AI/LLM integration.

This report catalogs 25+ key patents organized by category, extracting the implementation specifics that are not available in public documentation.

---

## 1. ONTOLOGY-RELATED PATENTS

### 1.1 US7962495B2 / US9589014B2 -- Creating Data in a Data Store Using a Dynamic Ontology

- **Patent Numbers:** US7962495B2 (original), US9589014B2 (continuation), US8856153B2 (continuation)
- **Filing Date:** 2006 (original priority)
- **Status:** Granted (multiple continuations)
- **Inventors:** Multiple (foundational Palantir team)

**Key Claims:**
The ontology comprises a plurality of **data object types** and **object property types**. Each object type has a name, URI, and base type. Parser definitions transform input data into modified data compatible with the object property types.

**Concrete Implementation Details Revealed:**
- The ontology is embodied in a **database schema** -- it is not an abstract concept but a literal data model stored in a relational structure
- Object types are identified by **URIs** (Uniform Resource Identifiers), suggesting a RDF/semantic-web heritage in the data model
- Parser definitions are **editable at runtime** -- the ontology is genuinely dynamic, not compiled
- Each property type has explicit type constraints that validate incoming data against the ontology schema
- The ontology structure can be modified (add/remove types, edit property definitions) **without rebuilding the underlying data store**

**What this reveals beyond marketing:** The ontology is not just a "semantic layer" as marketed -- it is a full runtime-editable schema with URI-based type identification, suggesting deep roots in semantic web standards adapted for operational use.

---

### 1.2 US20200293561A1 -- Systems and Methods for Providing an Object Platform for Datasets

- **Patent Number:** US20200293561A1
- **Filing Date:** June 3, 2020
- **Assignee:** Palantir Technologies Inc
- **Inventors:** Rick Ducott, Aakash Goenka, Bianca Rahill-Marier, Tao Wei, Diogo Morant, Jack Grossman, Francis Screene, Subbanarasimhiah Harish, Jim Inoue, Jeremy Kong, Mark Elliot, Myles Scolnick, Quentin Spencer-Harper, Richard Niemi, Ragnar Vorel, Thomas McIntyre, Thomas Powell, Andy Chen

**Key Claims:**
The system comprises five primary engines: **datastore**, **definition engine**, **association engine**, **cache engine**, and **interface engine** that work together to abstract relational data into objects.

**Concrete Implementation Details Revealed:**
- **Object-to-dataset mapping:** Object definitions specify which **exact database rows and columns** store each property value. Objects are not stored natively as objects -- they are a **view layer** over relational/tabular data
- **Caching strategy:** Object data is loaded into cache "as properties of the object" enabling object-oriented operations **without parsing entire datasets**. This reveals a materialized-view architecture
- **Conflict resolution mechanism:** Uses **commit logs** storing "timestamps and vector clocks associated with modifications" plus user/security metadata. Conflicts resolve through configurable rules based on modification timing, origin, and user security levels
- **Three APIs exposed:** Object Search API, Object Load API, Object Modify API -- the fundamental CRUD layer
- The definition engine "describes the object by specifying/identifying one or more properties (characteristics)"

**What this reveals beyond marketing:** The ontology's "objects" are actually **materialized views over tabular datasets** with a caching layer. The conflict resolution uses **vector clocks** (a distributed systems technique), confirming that the object platform is designed for multi-writer distributed scenarios. This is the patent that describes how the "Object Platform for Datasets" actually works under the hood.

---

### 1.3 US10754822B2 -- Systems and Methods for Ontology Migration

- **Patent Number:** US10754822B2
- **Grant Date:** August 25, 2020
- **Inventor:** Mihir Patil

**Key Claims:**
Method for migrating a source ontology from a source stack to a destination stack. The source ontology defines source objects associated with source datasets, and source datasets correspond to destination datasets.

**Concrete Implementation Details Revealed:**
- Ontology migration is **stack-based** -- source and destination are separate "stacks" (deployment environments)
- Migration works by **translating dataset identifiers** between stacks, not by moving actual data
- Users can **selectively migrate** specific objects or exclude objects from migration
- The system maps source data set identifiers to destination data set identifiers, implying that ontologies are tightly coupled to their underlying dataset registry

**What this reveals beyond marketing:** Ontology "migration" between Palantir environments is fundamentally an **identifier translation exercise**, not a data copy. The ontology is a metadata overlay that references datasets by ID, and migration rewires those references.

---

### 1.4 US10061828B2 -- Cross-Ontology Multi-Master Replication

- **Patent Number:** US10061828B2
- **Filing Date:** May 2, 2016
- **Grant Date:** August 28, 2018
- **Inventors:** Richard Allen Ducott, John Kenneth Garrod, John Antonio Carrino, Katherine Brainard

**Key Claims:**
System enabling database sites using **different ontologies** to share data through ontology maps that translate data types between schemas.

**Concrete Implementation Details Revealed:**
- **Three mapping approaches:**
  1. **One-to-One:** Single data type maps directly to single type at peer site (URI1 <-> URI2)
  2. **One-to-Many:** Parent type maps to multiple child types, preserving specialization during round-trip
  3. **Drop Lists:** Types that should NOT be exported until mapping rules exist
- **Pre-export validation:** The exporting peer performs "pre-export peer ontology validation" by **simulating round-trip transformations** -- values are transformed to importing schema, then back. If they stabilize across multiple round-trips, export proceeds
- **Link reversal:** The system handles "opposite asymmetric link types" by reversing link directions during import
- **Update packet structure:** Contains the exporting ontology, database changes, ontology map, and a **cryptographic digest** verifying both sites use compatible mappings
- Related patents: US8515912 ("Sharing And Deconflicting Data Changes In A Multimaster Database System"), US8527461 ("Cross-ACL Multi-Master Replication")

**What this reveals beyond marketing:** This is Palantir's solution for multi-agency/multi-classification data sharing (e.g., between CIA and NSA). The round-trip stability check is a sophisticated safeguard ensuring data fidelity across schema boundaries. The cryptographic digest prevents silent mapping drift between peers.

---

### 1.5 US10248722 -- Multi-Language Support for Dynamic Ontology

- **Patent Number:** US10248722
- **Status:** Granted
- **Inventor:** LeBlanc et al.

**Key Claims:**
The data types in the ontology include **data object types, property types, and link types**, with multi-language support for the dynamic ontology structure.

**What this reveals beyond marketing:** The ontology's type system has three explicit pillars (object types, property types, link types), and the multi-language support indicates the ontology layer is designed for international/coalition deployments.

---

## 2. UI/APPLICATION BUILDING PATENTS

### 2.1 US11500620B2 -- Workflow Application and User Interface Builder Integrating Objects, Relationships, and Actions

- **Patent Number:** US11500620B2 (published as US20210342129A1)
- **Filing Date:** July 6, 2021 (Priority: November 13, 2019)
- **Grant Date:** November 15, 2022
- **Inventors:** Myles Scolnick, Bianca Rahill-Marier, Xinyi Wang, Sarah Beckoff, Quentin Le Pape, Shaun Springer

**Key Claims:**
Object-centric builder software that designs workflow applications leveraging an integrated ontology.

**Concrete Implementation Details Revealed:**
- **Ontology defines four elements for apps:** data object types, relationships among types, properties of types, and **actions associated with types**
- **Widget architecture:** Widgets are modular UI components added to **containers within a layout**. Configuration is ontology-driven: inputs, outputs, and available actions are **constrained by ontology definitions**
- **Type safety:** The builder validates that "inputs and outputs of widgets may be configured to adhere to specific data object types" -- compile-time-like type checking for a no-code builder
- **Widget linking:** Multiple widgets can be linked by **routing one widget's output as another's input** -- this is the reactive binding model
- **Function registry:** Workflow logic is stored separately in a "function registry" and referenced by widgets, enabling **reuse across applications**
- **WYSIWYG preview:** Real-time preview interface showing live updates as designers modify layout, styling, and widget configurations

**What this reveals beyond marketing:** Workshop is fundamentally a **type-safe widget composition system** where the ontology acts as the type system. The "function registry" is a separate service layer enabling shared business logic. The reactive data flow (output-to-input routing) is the core mechanism for building interactive apps without code.

---

### 2.2 US11842171B2 -- Function Access System

- **Patent Number:** US11842171B2 (published as US20210365244A1)
- **Filing Date:** August 9, 2021 (Priority: August 14, 2019)
- **Grant Date:** December 12, 2023
- **Inventors:** Samuel Kedida, Andy Chen, Mihir Rege, Mikita Samsonau, Vipul Shekhawat

**Key Claims:**
Dynamic generation of APIs and function management for data object types. The system detects changes to object definitions and automatically updates APIs.

**Concrete Implementation Details Revealed:**
- **Five architectural components:**
  1. **Ontology Data Store** -- stores object definitions (properties, types, relationships)
  2. **API Generation Engine** -- dynamically creates type-specific REST APIs with permission-based access
  3. **Function Data Store** -- registry of functions in **multiple languages** (C, Java, Python, Ruby, JavaScript)
  4. **Function Manager Engine** -- handles discovery, keyword search, and execution request processing
  5. **Data Object Data Store** -- contains actual instances in potentially heterogeneous formats/locations
- **Automatic API regeneration:** The system monitors ontology changes via **polling or event notifications** and automatically updates APIs when properties are added, removed, renamed, or modified
- **Sandboxed execution:** Functions execute in **isolated processing engine instances** with imposed resource limits
- **Permission-tiered access:** APIs expose all properties but the system prevents unauthorized users from viewing sensitive properties -- access control is enforced **at the API layer, not the data layer**
- **Property multiplicity:** Objects can have more than one property of the same property type

**What this reveals beyond marketing:** This is the patent behind Palantir's "Functions" capability and the OSDK. The key insight is that the API layer is **auto-generated from ontology definitions** and **regenerated on schema changes**. Functions are polyglot (multi-language) and sandboxed. The data objects may live in heterogeneous backing stores -- confirming the ontology is a unification layer, not a single database.

---

## 3. PIPELINE / DATA PROCESSING PATENTS

### 3.1 US9946738B2 / US10853338B2 -- Universal Data Pipeline

- **Patent Numbers:** US9946738B2 (original grant April 17, 2018), US10853338B2 (continuation, December 1, 2020)
- **Filing Date:** October 6, 2016 (Priority: November 5, 2014)
- **Inventors:** Jacob Meacham, Michael Harris, Gustav Brodman, Lynn Cuthriell, Hannah Korus, Brian Toth, Jonathan Hsiao, Mark Elliot, **Brian Schimpf** (former Palantir President), Michael Garland, Evelyn Nguyen

**Key Claims:**
History-preserving data pipeline providing **immutable and versioned datasets**.

**Concrete Implementation Details Revealed:**

**Dataset Management Model:**
- **Immutability principle:** Data is NEVER overwritten. New versions are created alongside historical ones, enabling temporal reconstruction
- **Versioning via transaction commit identifiers:** Each dataset modification generates a version keyed by a transaction commit ID
- **Delta encoding:** Versions are stored as "differences or deltas between dataset versions" to reduce storage consumption while maintaining full historical access

**Transaction Architecture (three-phase protocol):**
1. **Initiation** (`start transaction`): Client requests transaction opening, receives unique transaction ID
2. **Write Operations** (multiple `write` commands): Data writes to containers in data lake with acknowledgment
3. **Commitment** (`commit`): System assigns commit identifier, atomically updates transaction metadata
- Transaction entries record: dataset name, transaction ID, start timestamp, committed flag, commit ID, container references

**Build Dependency System:**
- Maintains **directed acyclic graphs (DAGs)** of build dependencies representing dataset relationships
- **Nodes** = datasets; **Edges** = dependencies; **Leaf nodes** = base datasets; **Root nodes** = final outputs
- **Post-order depth-first traversal** determines build sequencing automatically
- When a base dataset updates, the system identifies dependent "parent datasets" and triggers **cascading rebuilds** through a message queue

**Derivation Programs:**
- Each program entry stores: program name, version ID, dataset dependencies, executable instructions
- Supports **SPARK SQL, HIVEQL, and GROOVY** as transformation languages
- Transformations execute via analytics clusters (Apache Spark, Hive instances) with atomic commits

**Build Catalog:**
- Records each derived dataset version with: dataset name, version, **build dependencies** (exact input versions), **derivation program version**
- Enables complete traceability: determine what inputs and code produced any given output

**What this reveals beyond marketing:** This is the foundational patent for Foundry's pipeline system. The architecture is a **git-like version control system for datasets** with DAG-based build orchestration. The explicit support for Spark SQL, HiveQL, and Groovy confirms the compute layer choices. The message-queue-based cascading rebuild is how "incremental builds" actually work internally.

---

### 3.2 US10754752B2 -- Data Pipeline Monitoring

- **Patent Number:** US10754752B2
- **Grant Date:** August 25, 2020
- **Filing Date:** June 7, 2019
- **Inventors:** Jesse Rickard, Peter Maag, Jared Newman, Giulio Mecocci, Harish Subbanarasimhia, Adrian Marius Dumitran, Andrzej Skrodzki, Jonah Scheinerman, Gregory Slonim, Alexandru Viorel Antihi

**Key Claims:**
Combined event-based and current-status monitoring for pipeline subsystems with validation logic and notification.

**Concrete Implementation Details Revealed:**
- **Collector types:** Filesystem, application, database, and hardware collectors -- each extracting specific fact data objects via APIs, SQL queries, or direct filesystem access
- **Validation framework:** Uses scripting languages and query languages to check thresholds, data volumes, job durations, and resource availability
- **Statistical analysis:** Calculates expected ranges using "standards of deviation around the mean or median value" for anomaly detection
- **Deduplication and auto-resolution:** Reduces alert fatigue by deduplicating repeated validation states and automatically clearing resolved issues
- **Calendar-based visualization:** Dashboard shows critical, warning, and pass statuses over time

**What this reveals beyond marketing:** Palantir's pipeline health monitoring ("Data Health") uses a **multi-collector architecture** with statistical anomaly detection (not just threshold-based). The auto-resolution and deduplication suggest mature operational tooling.

---

### 3.3 US20210149857A1 -- Data Pipeline Branching

- **Filing Date:** December 24, 2020
- **Inventors:** Eliot Ball, Meghan Nayan, Mikhail Proniushkin, Mihir Rege, Vipul Shekhawat

**Key Claims:**
A workbook management system supporting master and test branches of data pipelines with merge operations.

**Concrete Implementation Details Revealed:**
- **Branch data structure:** A master branch comprises pointers to dataset snapshots + transformation logic + pointers to derived output snapshots
- **Test branch creation:** Creates a copy of the master branch's logic with pointers to the **same input snapshots** (copy-on-write semantics)
- **Merge operation:** Replaces the master's logic with the test branch's logic and updates output snapshot references
- **Isolation:** Test branches can modify transformation operations **independently** without affecting production

**What this reveals beyond marketing:** Pipeline branching works like **git branching for data pipelines** -- with copy-on-write semantics for efficiency. The merge is a logic replacement + output reference update, not a data merge. This is the mechanism behind Pipeline Builder's "test runs" feature.

---

### 3.4 US20250094439A1 -- LLM Response Optimization for Data Pipeline Generation

- **Patent Number:** US20250094439A1
- **Filing Date:** September 6, 2024
- **Publication Date:** March 20, 2025
- **Status:** Pending
- **Inventors:** Morten Telling, Alexander Bailey, Richard Burdish, Ankit Shankar, Matthew Hawes, Codrut Lemeni, Nanwei Cai, Tiffany Wang, Joseph Rafidi, Kamran Khan

**Key Claims:**
LLM-based system for generating data pipelines from natural language queries using a custom computer language.

**Concrete Implementation Details Revealed:**
- **Custom language for LLM interaction:** Palantir designed a **proprietary computer language** optimized for LLM token efficiency -- "2x to 100x more efficient than conventional languages" like JSON
- **ANTLR parser generators** used to parse LLM outputs back into executable pipeline code
- **Prompt architecture components:** Expression initializers, transformation initializers, parser initializers, **mistake context instructions** (showing errors to avoid), query example context with sample reasoning
- **Supported transformations:** Join, filter, geo-specific operations (distance joins, geometry filtering), group-by, encode, aggregation, H3 grid manipulations
- **Error handling:** Explicit "mistake context instructions" within prompts guide LLMs away from common errors like invalid type casting -- a form of **few-shot error prevention**
- **UI components:** Pipeline visualization graphs, transformation mode selectors, explanation mode selectors, status indicators

**What this reveals beyond marketing:** Palantir built a **custom intermediate language** specifically for LLM-to-pipeline translation, not using standard JSON/SQL. The use of ANTLR confirms they built a full parser/compiler for this language. The "mistake context" approach is a concrete prompt engineering technique for reducing hallucinations.

---

### 3.5 US8930897B2 -- Data Integration Tool

- **Patent Number:** US8930897B2
- **Grant Date:** January 6, 2015
- **Inventor:** Anthony Albert Nassar

**Key Claims:**
Proactive validation of transformation scripts using ontology parameters.

**Concrete Implementation Details Revealed:**
- Transformation scripts are **linked to ontology configuration files** that define valid entity types and property types
- The system performs **proactive debugging** by checking conditions against ontology parameters BEFORE running the full transformation on large datasets
- Validation determines if entity assignments in the ontology are consistent with builder definitions
- Saves significant time versus traditional approaches of "parsing and transforming large amounts of data" before discovering errors

**What this reveals beyond marketing:** The data integration tool validates transformation scripts **at design time against the ontology schema**, acting like a type checker for data pipelines. This is the precursor to Pipeline Builder's schema validation.

---

## 4. DEPLOYMENT PATENTS (Apollo)

### 4.1 US10263845B2 -- Systems and Methods for Continuous Configuration Deployment

- **Patent Number:** US10263845B2
- **Filing Date:** October 18, 2017
- **Grant Date:** April 16, 2019
- **Inventors:** Nicholas Hall, Hamza Muraj, Jason Free, John Montgomery, James Schweiger, Matthew Levan, Thomas Montague

**Key Claims:**
Configuration definition objects obtained from remote repositories, cached locally, then used to generate tailored deployment packages.

**Concrete Implementation Details Revealed:**
- **Central hierarchical configuration repository** pushes configuration definition objects to sub-servers when committed to version control
- **Pre-caching:** Sub-servers cache configuration objects **before maintenance windows** begin (maintenance windows are ~2 hours for hundreds of MB to GB of patches)
- **Context-aware generation:** A single configuration definition object generates **different configuration objects per system** based on version info and system characteristics
- **Mesh network capability:** Systems can request configuration objects from **peer sub-servers** (not just the central server), enabling operation during network degradation or central server outages
- **Automated execution:** Configuration objects contain APIs and handlers that execute **automatically via service requests** without administrator intervention

**What this reveals beyond marketing:** Apollo's deployment mechanism is a **mesh-networked, pre-cached, context-aware configuration system**. The mesh capability is critical for air-gapped/degraded environments -- systems can bootstrap from peers, not just a central server. The "configuration definition object" pattern is a form of **declarative infrastructure-as-code**.

---

### 4.2 Deployment State Management (Patent number not publicly indexed in search results)

- **Assignee:** Palantir Technologies Inc
- **Inventors:** Mahmoud Abdelsalam, Ryan McNamara, Ashray Jain et al.

**Key Claims:**
Managing states of deployment where configuration changes are detected and propagated.

**Concrete Implementation Details Revealed:**
- The system **detects** configuration changes to be implemented at a deployment
- Configuration changes include one or more **commands** to change deployment configuration
- State management tracks current deployment state against desired state

**What this reveals beyond marketing:** Apollo uses a **desired-state reconciliation model** (similar to Kubernetes) where the system continuously compares actual deployment state against declared desired state and executes commands to converge.

---

### 4.3 Frontend Asset Deployment Tracking (Patent number not publicly indexed in search results)

- **Inventors:** Eliot Ball, Matthew Jenny, Nicholas Gates, Erin Price-Wright, Kamran Khan, Gregory Manis, Emeline Wu

**Key Claims:**
Coordinating deployment of frontend assets to defined user groups via tracks.

**Concrete Implementation Details Revealed:**
- Users are assigned to **tracks** comprising sets of frontend assets
- Each track includes **all individual components required to generate an entire frontend**
- Different tracks can contain **different versions of the same component** -- enabling canary deployments
- New/updated components can be deployed to a **limited subset of users** before widespread rollout

**What this reveals beyond marketing:** This is Palantir's **canary deployment / feature flagging system** for frontend code. The "track" concept is a first-class abstraction for progressive rollouts, not just feature flags.

---

### 4.4 US11444854 -- System to Collect and Visualize Software Usage Metrics

- **Patent Number:** US11444854
- **Filing Date:** December 30, 2019
- **Grant Date:** September 13, 2022

**Key Claims:**
Metrics collection system for software usage at deployments.

**Concrete Implementation Details Revealed:**
- Collects **software usage metrics** from client devices at deployments
- Server identifies **metrics type**, assigns to **metrics category**, calculates and updates a **metrics score**
- Enables tracking of how deployed software is actually being used across all deployment environments

**What this reveals beyond marketing:** Palantir has a centralized telemetry system that feeds back usage data from all deployment environments, enabling data-driven decisions about feature adoption and platform health.

---

## 5. SECURITY PATENTS

### 5.1 US9081975B2 / US9836523B2 -- Sharing Information Between Nexuses with Different Classification Schemes

- **Patent Number:** US9081975B2 (granted July 14, 2015), continuation US9836523B2
- **Filing Date:** October 22, 2012
- **Inventors:** Richard Allen Ducott III, John Kenneth Garrod, Khan Tasinga

**Key Claims:**
Database replication across distributed systems employing divergent security classification frameworks.

**Concrete Implementation Details Revealed:**
- **Classification structure consists of:**
  - **Classification markings:** authorization levels (Top Secret, Secret, Confidential, Restricted, Unclassified)
  - **Origin classifications:** historical records tracking how markings were translated across security domains during replication (a "stack" of translation history)
- **Translation rules:** Map sets of classification markings from one scheme to another. Rules are **asymmetric** -- forward and reverse translations may differ
- **Shortest-path translation:** When multiple translation routes exist, the system selects the **shortest path** to minimize accuracy degradation
- **Replication invariant:** If data with classification C and markings {M} is exported from database D, then reimported after traversing peer databases, it must retain original markings {M}
- **Hybrid domain support:** Accommodates CBAC databases, non-CBAC (RBAC) databases, and databases with no classification framework -- all participating in the same replication topology
- **Classification marking whitelists:** Each nexus maintains a whitelist of permitted export markings

**What this reveals beyond marketing:** This is the patent that makes Palantir deployable across intelligence community boundaries (CIA/NSA/DIA). The "origin classification stack" is a provenance chain for security markings -- every time data crosses a classification boundary, the translation is logged. The asymmetric translation rules and shortest-path algorithm are sophisticated cross-domain solutions that go far beyond simple RBAC.

---

### 5.2 US9857960B1 -- Data Collaboration Between Different Entities

- **Patent Number:** US9857960B1
- **Filing Date:** October 19, 2015
- **Grant Date:** January 2, 2018
- **Inventors:** Graham Dennis, Timothy Taylor, Kimberley Lear, Jesse Rickard, Dyon Balding, Hunter Pitelka, David LeBlanc, Vaughan Shanks, Joel Davies, Steffen Merten, Christopher Cook, Christopher Male, Marc Barker

**Key Claims:**
System for sharing information as a graph while protecting sensitive data through progressive redaction.

**Concrete Implementation Details Revealed:**
- **Five progressive redaction criteria applied in order:**
  1. Access control classifications (security clearance-based)
  2. Provenance (information source tracking)
  3. Data object type (category-based filtering)
  4. Data object property type (specific attribute filtering)
  5. Media type (file format/data type filtering)
- **Graph export format:** Serialized graph state + ontology mappings + globally unique identifiers + audit logs
- **Import resolution:** Receiving entities reconcile duplicates through **timestamp-based deconfliction** and manual conflict resolution

**What this reveals beyond marketing:** Palantir's data sharing model applies **five layers of redaction** before any data leaves a system. The graph-based export with GUIDs enables **cross-system entity resolution** -- the same real-world entity can be recognized across different Palantir deployments.

---

### 5.3 US20230306000A1 -- Data Asset Sharing

- **Patent Number:** US20230306000A1
- **Filing Date:** August 18, 2022
- **Publication Date:** September 28, 2023
- **Inventors:** Alexandra Greehy, Craig Massie, Alexander Bell-Thomas, Helena Kertesz, Mihai Condur, Nicolas Prettejohn, Pieris Christofi, Sam Stoll

**Key Claims:**
Controlled sharing of electronic data assets across organizational boundaries.

**Concrete Implementation Details Revealed:**
- **Four primary object types in sharing framework:**
  1. Data access request objects (tracking justification, approvals, statuses)
  2. Shared data asset objects (containing schema, lineage, ownership metadata)
  3. User objects (categorizing owners and requesters)
  4. Links establishing relationships between entities
- **Namespace-based access control:** Sharing operates by **updating namespace markings** associated with datasets -- rather than moving data, the system modifies which workspaces can access assets
- **Workflow enforcement:** Users cannot bypass structured processes -- must provide **legal justifications** and data owners must explicitly approve
- **Transitive permission revocation:** When upstream data access is denied, **downstream derived datasets automatically inherit restrictions** through the lineage chain
- **Data minimization:** Column-level and row-level filtering applied **automatically** based on scope rules (geographic, role-based)

**What this reveals beyond marketing:** The "namespace marking" approach means Palantir's sharing is implemented as **metadata permission changes, not data copies**. The transitive revocation through lineage is particularly powerful -- if you lose access to a source dataset, all derived datasets automatically become inaccessible. This is the mechanism behind Foundry's "Restricted Views" and "Data Sharing" features.

---

### 5.4 US11593317B2 -- Systems and Methods for Tamper-Resistant Activity Logging

- **Patent Number:** US11593317B2
- **Filing Date:** February 2, 2021
- **Grant Date:** February 28, 2023
- **Inventors:** Nomi Becker, Anne Ryan

**Key Claims:**
Every read, write, or data manipulation action is logged immutably.

**Concrete Implementation Details Revealed:**
- **Dual-datastore architecture:** Logs maintained in both an **immutable append-only repository** and a customer-accessible system log
- **Chunked logging:** Activity broken into **50 KB chunks**, encrypted, compressed, then hashed (SHA-1 or SHA-512)
- **Hash as address:** Hash codes function as "block addresses" for accessing data manipulation activity logs in the append-only datastore
- **Multi-layer detection:**
  - Intrusion detection monitors circumvention attempts
  - Kernel security components log access restriction conflicts
  - **Keystroke logging** captures terminal and browser interactions
  - System call auditing captures user actions
- **Tamper prevention:** Multiple simultaneous hash algorithms make collision attacks impractical
- **External hash comparison:** Log pipeline pushes data externally, enabling cross-system hash comparison to detect modifications
- **Alert triggers:** Suspicious commands, datastore failures, and **logging slowdowns** (indicating disabled logging) all generate alerts

**What this reveals beyond marketing:** The audit system uses **content-addressable storage** (hash-as-address) similar to git's object store. The dual-datastore design means neither Palantir nor the customer can tamper with logs without detection. Keystroke logging at the kernel level is far more invasive than typical application-level audit logging.

---

## 6. AI / LLM INTEGRATION PATENTS

### 6.1 EP4443310A1 -- Artificial Intelligence System User Interfaces

- **Patent Number:** EP4443310A1
- **Filing Date:** April 5, 2024 (Priority: April 6, 2023)
- **Publication Date:** October 9, 2024
- **Inventors:** Martin Copes, Mohamed Zaki Trache, Christopher Jeganathan

**Key Claims:**
Natural language interaction system with orchestration layer coordinating multiple specialized data processing services.

**Concrete Implementation Details Revealed:**
- **Three-layer architecture:**
  1. **Orchestrator Selector** -- receives user prompts, determines which service to use
  2. **Service Orchestrators** -- format requests for specific services
  3. **Data Processing Services** -- execute operations (search, filter, visualize, traverse ontology, write data)
- **LLMs serve two roles:** (1) Service selection (mapping prompts to processors) and (2) Query formatting (translating natural language to service parameters)
- **In-prompt training:** System provides training examples **directly within prompts** rather than retraining models
- **Plugin architecture:** Services exposed via APIs as modular plugins -- search, filtering, visualization, ontology traversal, data writing
- **Context injection:** Services receive context about **user permissions, previous analyses, and data schemas** to generate appropriately scoped responses
- **Transparency UI:** "Plugin monitor panels" reveal which services activated and their inputs/outputs, showing AI decision-making process
- **Available tools include:** Ontology function tool, date/time tool, query objects tool, calculator tool, **apply action tool**

**What this reveals beyond marketing:** AIP's architecture is a **multi-agent orchestration system** where the LLM acts as a router, not a direct data accessor. The "apply action tool" means the AI can trigger ontology actions (write operations) -- confirming that AIP agents can take real-world actions, not just answer questions. The explicit permission context injection is how Palantir maintains security when LLMs interact with data.

---

### 6.2 US20240419658A1 -- Profile-Based Artificial Intelligence System

- **Patent Number:** US20240419658A1
- **Filing Date:** May 28, 2024 (Priority: June 14, 2023)
- **Publication Date:** December 19, 2024
- **Status:** Pending
- **Inventors:** Mohamed Zaki Trache, Martin Copes, Christopher Jeganathan, Frauke Hein, Arttu Voutilainen, Adam Balogh, Joseph Hashim

**Key Claims:**
AI system leveraging "profiles" tied to user roles, cohorts, and organizations for contextualized responses.

**Concrete Implementation Details Revealed:**
- **Profile has four components:**
  1. **Knowledge Bases** -- searchable data repositories (databases, documents) relevant to specific roles
  2. **Functions** -- formulas for calculating properties (e.g., credit risk calculations)
  3. **Plugins** -- data processing tools with API access for searches, visualizations, ontology traversal
  4. **Templates** -- business logic rules with placeholders for dynamic substitution
- **Prompt generation:** System receives simple user input and "automatically generates a detailed prompt for the language model based on a profile" by replacing template placeholders with user context, knowledge base excerpts, and applicable tools
- **Access control integration:** Profiles enable the system to "control access to certain electronic data assets with respect to both the user and the computer-based model"
- **Multi-stage execution:** Plugins activate **both before** (to populate prompt content) **and after** LLM execution (to process results) -- creating a workflow architecture, not simple query-response

**What this reveals beyond marketing:** This is the patent behind AIP's role-based AI configuration. The "profile" is essentially a **pre-built prompt template + tool configuration + knowledge base + security scope** -- meaning each user role gets a fundamentally different AI experience. The multi-stage plugin execution (pre-LLM and post-LLM) reveals that AIP is a **pipeline that wraps the LLM**, not just an LLM with tools.

---

### 6.3 US20240346388A1 -- Security-Aware Large Language Model Training and Model Management

- **Patent Number:** US20240346388A1
- **Filing Date:** March 28, 2024 (Priority: April 12, 2023)
- **Publication Date:** October 17, 2024
- **Status:** Pending
- **Inventor:** Peter Wilczynski

**Key Claims:**
Training machine learning models using segmented training corpora aligned with permission requirements.

**Concrete Implementation Details Revealed:**
- **Training segmentation:** Rather than training one model on all data, the system segments training datasets by **permission level** and trains separate models per security tier
- **Permission framework:** Hierarchical levels encompassing security levels (classified/unclassified) AND access levels (group-based restrictions, e.g., "Division A" narrower than "all company")
- **Multi-model approach:**
  - Option A: Base model trains on low-permission data, then continues training on higher-permission data (additive)
  - Option B: Separate models per permission tier, combined via **ensemble model** at inference
- **Inference-time routing:** System evaluates incoming requests for usage permission level, compares against each model's permission requirement, and routes to appropriate model
- **Metadata association:** Permission requirements attach to models as metadata, enabling **runtime permission checks before query processing**
- **Core problem addressed:** "LLMs create de novo content" that may "contain sensitive information" -- this system prevents models from learning classified information that could leak to unauthorized users

**What this reveals beyond marketing:** Palantir's approach to secure AI is **training separate models per security classification level**, not just filtering outputs. This is a fundamentally different (and more secure) approach than RAG-based systems that rely on post-generation filtering. The ensemble approach allows combining outputs from multiple security-tiered models. This patent directly addresses the "data leakage through LLM inference" problem that is central to military/intelligence AI deployment.

---

## 7. CROSS-CUTTING ANALYSIS

### Key Architectural Patterns Revealed Across Patents

**1. The Ontology Is a Metadata Overlay, Not a Database**
Patents consistently show that ontology objects are **views over tabular datasets** (US20200293561A1), identified by URIs (US9589014B2), with a caching layer for performance. The ontology never stores data itself -- it maps to datasets.

**2. Everything Is Versioned and Immutable**
From datasets (US10853338B2) to configuration (US10263845B2) to audit logs (US11593317B2), Palantir's architecture uses **append-only, immutable, version-controlled data structures**. This is a fundamental design principle.

**3. DAG-Based Dependency Management**
Pipelines use DAGs (US10853338B2), UI widgets use output-to-input chains (US11500620B2), and deployment configurations use dependency graphs. The DAG is the universal computation model.

**4. Conflict Resolution via Vector Clocks**
Object platform conflicts use **vector clocks and timestamps** (US20200293561A1), multi-master replication uses **round-trip stability checks** (US10061828B2), and data sharing uses **timestamp-based deconfliction** (US9857960B1). Distributed consistency is handled through convergent conflict resolution.

**5. Security as First-Class Metadata**
Classification markings are not bolt-on attributes but structural metadata that flows through the entire system -- through replication (US9081975B2), data sharing (US20230306000A1), API generation (US11842171B2), AI inference (US20240346388A1), and audit logging (US11593317B2).

**6. Multi-Environment Mesh Architecture**
Deployment patents reveal a **mesh-networked topology** (US10263845B2) where nodes can bootstrap from peers, not just central servers. This enables air-gapped, degraded, and disconnected operations.

---

## 8. PATENT TIMELINE: EVOLUTION OF PALANTIR'S ARCHITECTURE

| Year | Key Patent | What It Reveals |
|------|-----------|-----------------|
| 2006 | US7962495 -- Dynamic Ontology | Foundational ontology model with URI-based types |
| 2012 | US9081975 -- Cross-Classification Sharing | Multi-domain security replication |
| 2014 | US9946738 -- Universal Data Pipeline | Immutable, versioned dataset architecture (Foundry foundation) |
| 2015 | US8930897 -- Data Integration Tool | Ontology-aware transformation validation |
| 2015 | US9857960 -- Data Collaboration | Five-layer redaction model for inter-agency sharing |
| 2016 | US10061828 -- Cross-Ontology Replication | Multi-master data sharing across different schemas |
| 2017 | US10263845 -- Continuous Configuration | Apollo's mesh deployment architecture |
| 2019 | US11842171 -- Function Access System | Auto-generated APIs from ontology (OSDK foundation) |
| 2019 | US11500620 -- Workflow UI Builder | Workshop's type-safe widget composition |
| 2020 | US20200293561 -- Object Platform | How objects are materialized views over datasets |
| 2020 | US10853338 -- Universal Pipeline (cont.) | Transaction architecture and build catalog |
| 2020 | US10754752 -- Pipeline Monitoring | Multi-collector health monitoring with anomaly detection |
| 2020 | US10754822 -- Ontology Migration | Stack-based identifier translation for migration |
| 2020 | US20210149857 -- Pipeline Branching | Git-like branching for data pipelines |
| 2022 | US11444854 -- Usage Metrics | Telemetry collection across deployments |
| 2022 | US20230306000 -- Data Asset Sharing | Namespace-based permissions with transitive revocation |
| 2022 | US11593317 -- Tamper-Resistant Logging | Content-addressable append-only audit system |
| 2023 | EP4443310 -- AI System Interfaces | AIP's orchestrator-selector-plugin architecture |
| 2023 | US20240419658 -- Profile-Based AI | Role-based AI profiles with multi-stage plugin execution |
| 2023 | US20240346388 -- Security-Aware LLM | Per-classification-tier model training |
| 2024 | US20250094439 -- LLM Pipeline Generation | Custom language for LLM-to-pipeline translation |

---

## 9. IMPLICATIONS FOR COMPETITIVE ANALYSIS

### What Patents Reveal That Marketing Does Not

1. **The ontology is a caching/view layer over datasets** -- it does not replace databases; it sits above them. This means replicating the ontology concept requires building a sophisticated caching and materialization engine, not just a schema definition tool.

2. **Vector clocks for conflict resolution** -- the system is designed for true distributed, multi-writer scenarios (military coalitions), not just single-tenant enterprise use.

3. **Five-layer security redaction** is structurally embedded -- security is not a filter applied after computation but a fundamental constraint on data visibility at every layer.

4. **AIP is a multi-agent orchestrator** -- the LLM does not directly access data. It selects services, which access data within permission boundaries. This is architecturally more complex than typical RAG implementations.

5. **Per-classification model training** for LLMs is a novel approach that no competitor appears to have patented -- potentially giving Palantir unique defensibility in classified AI deployments.

6. **The pipeline system is git-like** -- immutable snapshots, DAG-based builds, branching/merging semantics. This is more sophisticated than most ETL/ELT tools.

7. **Apollo's mesh deployment** enables peer-to-peer configuration distribution -- critical for air-gapped environments where central servers are unreachable.

---

## Sources

- [Google Patents - Dynamic Ontology US9589014B2](https://patents.google.com/patent/US9589014B2/en)
- [Google Patents - Object Platform US20200293561A1](https://patents.google.com/patent/US20200293561A1/en)
- [Google Patents - Workflow UI Builder US20210342129A1](https://patents.google.com/patent/US20210342129A1/en)
- [Google Patents - Function Access System US20210365244A1](https://patents.google.com/patent/US20210365244A1/en)
- [Google Patents - Universal Data Pipeline US20170097950A1](https://patents.google.com/patent/US20170097950A1/en)
- [Google Patents - Pipeline Monitoring US20190286538A1](https://patents.google.com/patent/US20190286538A1/en)
- [Google Patents - Pipeline Branching US20210149857A1](https://uspto.report/patent/app/20210149857)
- [Google Patents - LLM Pipeline Generation US20250094439A1](https://patents.google.com/patent/US20250094439A1/en)
- [Google Patents - Continuous Configuration US10263845B2](https://patents.google.com/patent/US10263845B2/en)
- [Google Patents - Cross-Ontology Replication US10061828B2](https://patents.google.com/patent/US10061828B2/en)
- [Google Patents - Classification Sharing US20150261847A1](https://patents.google.com/patent/US20150261847)
- [Google Patents - Data Collaboration US9857960B1](https://patents.google.com/patent/US9857960B1/en)
- [Google Patents - Data Asset Sharing US20230306000A1](https://patents.google.com/patent/US20230306000A1/en)
- [Google Patents - Tamper-Resistant Logging US11593317B2](https://patents.google.com/patent/US11593317B2/en)
- [Google Patents - AI System Interfaces EP4443310A1](https://patents.google.com/patent/EP4443310A1/en)
- [Google Patents - Profile-Based AI US20240419658A1](https://patents.google.com/patent/US20240419658A1/en)
- [Google Patents - Security-Aware LLM US20240346388A1](https://patents.google.com/patent/US20240346388A1/en)
- [USPTO Report - Palantir Patent Filings](https://uspto.report/company/Palantir-Technologies-Inc/patents)
- [Justia Patents - Palantir Technologies](https://patents.justia.com/assignee/palantir-technologies-inc)
- [GreyB - Palantir Patents Insights](https://insights.greyb.com/palantir-patents/)
- [Daily Upside - Palantir Zero-Trust AI Patent](https://www.thedailyupside.com/technology/artificial-intelligence/palantir-patent-highlights-need-for-zero-trust-security-in-ai/)
- [AOIR - Survey of Palantir Patents](https://spir.aoir.org/ojs/index.php/spir/article/download/12187/10321/75852)
- [PinePat - Palantir Patent Trends 2024](https://www.pinepat.com/en/insights/columns/2024nyeon-palrantieo-tekeunolrojiyi-teugheo-culweon-donghyang)
- [Justia - US11444854 Usage Metrics Patent](https://patents.justia.com/patent/11444854)
- [USPTO Report - Ontology Migration US10754822](https://uspto.report/patent/grant/10,754,822)
- [USPTO Report - Universal Data Pipeline US10853338](https://uspto.report/patent/grant/10,853,338)
- [USPTO Report - Pipeline Monitoring US10754752](https://uspto.report/patent/grant/10,754,752)
