# Research Report: Ontology Design in Practice -- From Palantir to Industry Standards

> Generated 17 Feb 2026, Claude Agent Research
> Purpose: Comprehensive analysis of ontology design discipline for informing Spider's templated vertical ontology strategy

---

## 1. PALANTIR ONTOLOGY DESIGN SPECIFICS

### 1.1 Core Primitives: Object Types, Properties, Links, Actions, Interfaces, Functions

Palantir's Ontology is built on a clear taxonomy of modeling primitives, each mapping directly to a relational-database analogy:

| Dataset Concept | Ontology Concept |
|-----------------|------------------|
| Dataset         | Object Type      |
| Row             | Object           |
| Column          | Property         |
| Join            | Link Type        |

**Object Types** are the schema definition of a real-world entity or event. Both "JFK" and "LHR" are objects of an "Airport" object type. Object types are backed by datasets -- to create objects of type Employee, an organization adds backing datasources to the Employee object type and connects their employee directory and other enterprise data into the Ontology. After the first deploy, the object type ID cannot be modified.

**Properties** are characteristics of an object type. A shared property can be used on multiple object types for consistent modeling and centralized management. Properties support base types: Boolean, Byte, Date, Decimal, Double, Float, Geopoint, Integer, Long, Short, String, Timestamp.

**Structs** are composite property types with multiple fields -- for example, a Full Name struct with First Name and Last Name fields, or an Address struct with Street, City, Postal Code, and Country. Critical constraints: structs have a depth of one (cannot be nested), must have 1-10 fields, and use ElasticSearch object field indexing (which can produce unintuitive results with arrays when querying across struct instances).

**Link Types** define relationships between two object types (1-to-1, 1-to-many, many-to-many). The API name on the plural side should be plural -- `employee.subordinates.all()` not `employee.subordinate.all()`. When multiple links exist between the same two types, they need distinct semantic names (e.g., Employee-to-Employee: "Manager" and "Direct Report", not "Employee" and "Employee2").

**Action Types** define sets of changes to objects, property values, and links that a user can make at once, including side effects. Actions are the "verbs" of the ontology -- they represent what users can DO to data, not just what they can see.

**Interfaces** are abstract types describing the shape and capabilities of object types. They are not backed by datasets and cannot be instantiated directly. Interfaces enable polymorphism -- a function can accept any object type that implements a given interface. Struct types in TypeScript v2 are defined using TypeScript interfaces.

**Functions** are code-based logic (TypeScript v2 or Python) integrated natively into the ontology, operating on objects and property values. Functions support interface object sets as both inputs and outputs.

Sources: [Palantir Ontology Core Concepts](https://www.palantir.com/docs/foundry/ontology/core-concepts), [Object Types Overview](https://www.palantir.com/docs/foundry/object-link-types/object-types-overview), [Structs Overview](https://www.palantir.com/docs/foundry/object-link-types/structs-overview), [Link Types Overview](https://www.palantir.com/docs/foundry/object-link-types/link-types-overview), [Action Types Overview](https://www.palantir.com/docs/foundry/action-types/overview), [Interfaces Overview](https://www.palantir.com/docs/foundry/interfaces/interface-overview)

### 1.2 The Decision Framework: Object Type vs Property vs Link vs Struct

Palantir does not publish a single explicit decision tree, but the community and documentation converge on these heuristics:

**Model as an Object Type when:**
- The entity has its own lifecycle (it is created, updated, deleted independently)
- Multiple other entities reference it
- It needs its own security/permissions boundary
- Users will search for, browse, or take actions on it directly
- It has enough properties to warrant its own backing dataset

**Model as a Property when:**
- The value is a simple scalar or small struct that describes an object
- There is no reason for other objects to reference this value independently
- The value changes only when the parent object changes

**Model as a Struct when:**
- You need to group 2-10 related fields into a single logical property (Address, Full Name, GPS Coordinate with metadata)
- The grouped data does not have its own independent lifecycle
- You do NOT need to link other objects to this sub-structure
- Important: structs cannot be nested and max 10 fields

**Model as a Link when:**
- Two independent object types need a defined relationship
- The relationship itself may have meaning (cardinality, directionality, semantics)
- You need to traverse from one object type to another in queries or applications

The practical rule of thumb from the Palantir community: "If the client would naturally say 'show me all the Xs,' it is probably an Object Type. If they say 'what is the X of this Y,' it is probably a Property."

Sources: [Palantir Community Design Principles](https://community.palantir.com/t/ontology-and-pipeline-design-principles/5481), [Structs Overview](https://www.palantir.com/docs/foundry/object-link-types/structs-overview), [Properties Overview](https://www.palantir.com/docs/foundry/object-link-types/properties-overview)

### 1.3 Naming Conventions in Palantir Deployments

The Palantir community and documentation prescribe specific naming conventions:

- **Object Type names**: Use intuitive full names; avoid abbreviations. Use Groups instead of tag prefixes like `[tag] ObjectName`. Never use versioned names (`Message_v2`) -- instead add new properties or perform a full migration and deprecation.
- **Primary keys**: The `id` column must be a string type, no exceptions. Every Object Type must have a separate, unique primary key column named `id`, even if another unique column exists. The ID must be inherently unique, constructed only from the object's own properties. Composite IDs should not be hashed.
- **Foreign keys**: Follow `{foreign_object_type}_id` or `{link_api_name}_{foreign_object_type}_id`.
- **Timestamp properties**: `{verbed}_at_timestamp` (e.g., `created_at_timestamp`, `updated_at_timestamp`).
- **User reference properties**: `{verbed}_by_user` (e.g., `created_by_user`). Store Foundry user IDs as `multipass_id` for automatic account rendering.
- **Link API names**: Plural on the plural side (`subordinates`, not `subordinate`).
- **Maturity statuses**: Mark object types as Experimental, Active, or Deprecated.

Sources: [Palantir Community Design Principles](https://community.palantir.com/t/ontology-and-pipeline-design-principles/5481)

### 1.4 Deployment Scale: How Many Object Types?

Palantir does not publicly disclose typical object type counts, and no customer case study gives an exact number. However, triangulating from multiple sources:

- **Starter deployment (pilot, 1 use case)**: 5-15 Object Types. The Solution Design phase extracts "core" object types (mapped to source systems) and "derived" types (created through enrichment) from functional requirements. A single use case like route operations might yield: Alert, Flight, Route, Airline, Airport, User, Assignment.
- **Departmental deployment (3-5 use cases)**: 20-60 Object Types. Cross-department expansion introduces conflicting entity definitions and duplicate data challenges.
- **Enterprise-scale digital twin**: Likely 100-500+ Object Types. Palantir describes the Ontology as a "digital twin of the organization" and states it enables "significant economies of scale" by converging effort onto a single reusable data asset. A customer integrating "7+ ERP data sources" to produce a digital twin of the value chain would naturally generate hundreds of types.

The Palantir community emphasizes that isolated Object Types indicate poor design -- objects should be richly linked. The guidance "start with 5-10 entities" from the knowledge graph community (Stardog) aligns with Palantir's pilot approach.

Sources: [Palantir Solution Design](https://www.palantir.com/docs/foundry/use-case-life-cycle/solution-design), [Palantir Ontology Overview](https://www.palantir.com/docs/foundry/ontology/overview), [Stardog Building a Knowledge Graph](https://www.stardog.com/building-a-knowledge-graph/)

### 1.5 Ontology Design Timeline and Iteration

Palantir's documentation does not specify exact timelines, but the methodology is clear:

1. **Functional requirements extraction**: From user interviews and process mapping, identify "what users need to accomplish" -- the decisions they make and the information supporting those decisions.
2. **Draft ontology with placeholder data**: Split effort between a Front End Team (building Objects, Actions, Applications using dummy data) and a Data Engineering Team (integrating and filling out the backing datasets). This parallelization accelerates iteration.
3. **Iterative refinement with domain experts**: "Regularly check in with domain experts and business users" is an explicit design principle. "Be pragmatic. If it works and delivers value then it's good, even if it's not perfect."
4. **Component-to-tool mapping for validation**: Rather than abstract diagrams, Palantir validates ontology design by mapping it to concrete tools -- stand-alone interfaces in Workshop, single-object context in Object Views, dashboards in Quiver.

The knowledge graph community recommends spending "no more than 2 weeks on initial modeling" and looking at "no more than 5-10 different entities" to start. Looking at more suggests the question is too broad.

Sources: [Palantir Community Design Principles](https://community.palantir.com/t/ontology-and-pipeline-design-principles/5481), [Palantir Solution Design](https://www.palantir.com/docs/foundry/use-case-life-cycle/solution-design), [Stardog Building a Knowledge Graph](https://www.stardog.com/building-a-knowledge-graph/)

### 1.6 Validating Ontology with Business Users

Palantir uses multiple validation formats:

- **Solution Designer diagrams**: Creates visual diagrams showing External System -> Data Connector -> Dataset -> Pipeline Builder -> Dataset -> Object -> Workshop -> User Group. This is the "strong foundational point" for alignment.
- **Workshop prototypes**: Workshop is a drag-and-drop application builder where ontology-backed apps are assembled rapidly. Business users interact with real (or dummy) data through tables, forms, maps, and action buttons -- this is the primary validation mechanism.
- **Object Explorer**: Users can search for and browse objects directly, validating that the ontology matches their mental model.
- **Quiver dashboards**: For executive stakeholders who need KPI-level validation.

The key insight: Palantir does NOT validate ontology with ER diagrams or abstract schema documents. They validate it by showing business users working applications built on top of the ontology. The ontology is validated through use, not through review.

Sources: [Palantir Solution Designer Tutorial](https://www.palantir.com/docs/foundry/solution-designer/tutorial-create-your-first-diagram), [Palantir Workshop](https://learn.palantir.com/workshop-course), [Palantir App Building Overview](https://www.palantir.com/docs/foundry/app-building/overview)

---

## 2. ONTOLOGY DESIGN AS A DISCIPLINE

### 2.1 Knowledge Graph Design Best Practices

The knowledge graph community (Stardog, Neo4j, TopQuadrant, Ontotext) converges on several principles:

**Start small, iterate fast**: Specify core classes (entities), properties, and individuals. Use non-technical words for relationships. Reuse terms when possible. Spend no more than 2 weeks on initial modeling with 5-10 entities. More than that suggests the question is too broad.

**Choose the right paradigm for your needs**: For high-performance graph computation and real-time queries, property graph databases (Neo4j) are more suitable. For semantic reasoning and standardized interoperability, RDF triplestores with ontologies (Stardog, GraphDB) should be chosen. Palantir's model is closer to the property graph approach but with a structured schema layer.

**Stakeholder involvement is critical**: Ontology management and knowledge graph development are iterative processes that will evolve over time. Stakeholders should be brought into the process frequently.

Sources: [Stardog Building a Knowledge Graph](https://www.stardog.com/building-a-knowledge-graph/), [Neo4j Ontologies](https://neo4j.com/blog/knowledge-graph/ontologies-in-neo4j-semantics-and-knowledge-graphs/), [Ontotext Knowledge Graphs for Retail](https://www.ontotext.com/blog/knowledge-graphs-for-retail/)

### 2.2 Schema.org as an Ontology Pattern

Schema.org is the world's most widely deployed ontology -- over 45 million web domains use it, with over 450 billion Schema.org objects as of 2024. As of February 2025, there are over 800 schema types. Its design principles are instructive:

**Pragmatic multiple inheritance**: Each type may be a sub-class of multiple types. A Hospital is simultaneously a CivicStructure, MedicalOrganization, and EmergencyService. The decision to allow multiple domains and ranges was "purely pragmatic" -- restricting to single inheritance "forces the creation of a lot of artificial types."

**Example-driven, not axiom-driven**: Schema.org relies heavily on illustrative examples rather than formal axioms. It is "not intended as a universal ontology."

**Flat-enough hierarchy**: Although multiple inheritance exists, the type hierarchy is displayed as a clean tree (picking one primary supertype for display). This pragmatic simplification aids comprehension.

**Extensibility**: Vocabularies can be easily extended through a well-documented extension model, and Schema.org is expected to be used alongside other vocabularies.

**Lesson for Spider**: Schema.org's success comes from being "good enough" for the most common cases, pragmatically handling edge cases through multiple inheritance, and prioritizing adoption over formal completeness. Spider's vertical ontology templates should follow the same philosophy.

Sources: [Schema.org Data Model](https://schema.org/docs/datamodel.html), [Schema.org Wikipedia](https://en.wikipedia.org/wiki/Schema.org), [Schema.org Full Hierarchy](https://schema.org/docs/full.html)

### 2.3 OWL/RDF Ontology Design Patterns

The formal ontology community has developed reusable Ontology Design Patterns (ODPs) that promote modularity, reusability, and systematic construction:

- **Extreme Design (XD)**: An agile, test-driven methodology leveraging ODPs for iterative, requirement-driven knowledge graph development.
- **OTTR (Reasonable Ontology Templates)**: A language for encoding patterns as templates, supporting large-scale automated class/axiom generation.
- **MODL and CS-MODL**: Reusable modular libraries promoting plug-and-play ontology construction with rich documentation and formal axiomatization.

The key benefit is increased modularity -- axioms can be reused independently, avoiding duplication. Semantic Web technologies (RDF and OWL) enable reference models for enterprise architecture where RDF distributes structured information and OWL maintains consistency of extensions.

**Lesson for Spider**: The modular, template-based approach from OWL/RDF design patterns directly maps to Spider's concept of "vertical ontology templates." Each industry template should be a composable module that can be extended without breaking the core.

Sources: [OWL Wikipedia](https://en.wikipedia.org/wiki/Web_Ontology_Language), [Ontology Design Patterns](https://www.researchgate.net/publication/227215903_Ontology_Design_Patterns), [Modular Ontology Modeling Tutorial](https://www.sciencegate.app/document/10.3233/ssw200032)

### 2.4 Domain-Driven Design Mapping to Ontology

Eric Evans' Domain-Driven Design (DDD) provides concepts that map remarkably well to Palantir's model:

| DDD Concept | Palantir Ontology Equivalent | Notes |
|-------------|------------------------------|-------|
| Entity | Object Type | Both have identity and lifecycle |
| Value Object | Property or Struct | Immutable, defined by attributes |
| Aggregate Root | Primary Object Type | The "entry point" object that controls consistency |
| Aggregate | Object Type + its linked dependent types | Cluster of associated objects |
| Bounded Context | Ontology Project / Group | Semantic boundary where terms have precise meaning |
| Ubiquitous Language | Object Type names and Property names | The shared vocabulary between tech and business |
| Domain Event | Action Type (or derived Object Type) | Records that something happened |
| Repository | Backing Dataset + Pipeline | The persistence layer |

**Critical insight**: DDD's concept of Ubiquitous Language is exactly what Palantir means when they say "Object Types and Actions must map to natural-language business concepts that the primary audience (business users) understands." The Ontology IS the Ubiquitous Language.

**Bounded Contexts in Palantir**: Palantir uses project-level separation (Datasource Projects, Integration Projects, Ontology Projects, Application Projects) and Groups to create logical boundaries. When expanding across departments, the challenge of "conflicting entity definitions" is exactly DDD's bounded context problem. BIAN (for banking) explicitly addresses this: "a Service Domain constrained by a bounded context."

**Aggregate Roots in Ontology**: In practice, aggregate roots are the Object Types that business users search for and interact with directly (e.g., Customer, Order, Machine). Subordinate entities (OrderLine, MachineComponent) are accessed through their aggregate root via links.

Sources: [DDD Wikipedia](https://en.wikipedia.org/wiki/Domain-driven_design), [Context Mapper](https://contextmapper.org/docs/bounded-context/), [BIAN Standard](https://www.vanharen.net/standards/bian-banking-architecture/bian-standard-in-3-minutes/)

### 2.5 Entity-Relationship Modeling vs Ontology Design

Traditional ER modeling and ontology design serve different purposes:

| Dimension | ER Modeling | Ontology Design |
|-----------|-------------|-----------------|
| **Scope** | Single database schema | Cross-system semantic layer |
| **Abstraction** | Physical storage layout | Conceptual domain model |
| **Flexibility** | Schema-on-write (rigid) | Schema-on-read (flexible) |
| **Relationships** | Foreign keys with cardinality | Typed, named links with semantics |
| **Evolution** | ALTER TABLE (breaking) | Additive changes, deprecation |
| **Reasoning** | No inference | Can derive new knowledge |
| **Users** | DBAs, developers | Business users, analysts, AI agents |
| **Stability** | Changes require migrations | Naturally extensible |

The fundamental difference: ER models optimize for storage; ontologies optimize for understanding. An ontology is the "API of your organization" (Palantir's phrase), while an ER model is the implementation detail.

Ontologies are model-centric and definition-driven, providing a conceptual framework. Knowledge graphs are data-centric and instance-driven. When you apply an ontology to a set of data points, you create a knowledge graph. The two are complementary, not competing.

Sources: [Knowledge Graph vs Ontology](https://www.puppygraph.com/blog/knowledge-graph-vs-ontology), [Enterprise Knowledge](https://enterprise-knowledge.com/whats-the-difference-between-an-ontology-and-a-knowledge-graph/)

---

## 3. INDUSTRY-SPECIFIC ONTOLOGY TEMPLATES

### 3.1 Manufacturing Ontology (ISA-95)

**Standard**: ISA-95 (ANSI/ISA-95) is the definitive standard for integrating enterprise and control systems in manufacturing. It defines a 5-level hierarchy:

- **Level 4**: Enterprise (ERP) -- business planning and logistics
- **Level 3**: Manufacturing Operations Management (MOM/MES) -- production operations
- **Level 2**: Control systems -- automated equipment control
- **Level 1**: Sensors and actuators
- **Level 0**: Physical process

**Core Entity Types** (derived from ISA-95 object models):

| Object Type | Description | Key Properties |
|-------------|-------------|----------------|
| Equipment | Physical or logical manufacturing resource | type, status, location, capacity |
| PhysicalAsset | Actual machines and components | serial_number, manufacturer, installation_date |
| Material | Raw materials and products | material_class, lot_id, quantity, unit |
| MaterialDefinition | Specification of a material | grade, composition, specs |
| Personnel | Workers and their qualifications | role, certification, shift |
| ProductionOrder | Work order for manufacturing | order_number, status, quantity_target, due_date |
| ProductionSchedule | Planned production timeline | start_time, end_time, priority |
| OperationsDefinition | How products are made | steps, resources_required, time_estimate |

**ISA-95 defines four primary information types**: material properties, equipment operations, physical assets, and personnel/roles.

**Published implementations**: The Digital Twin Consortium published open-source manufacturing ontologies on GitHub. Microsoft has published guidance on transforming manufacturing with ontologies using ISA-95.

Sources: [Rhize ISA-95](https://rhize.com/blog/what-is-isa95/), [IEEE ISA-95 Ontology Paper](https://ieeexplore.ieee.org/document/8471929/), [Digital Twin Manufacturing Ontologies](https://github.com/digitaltwinconsortium/ManufacturingOntologies), [Microsoft Manufacturing Ontologies](https://techcommunity.microsoft.com/blog/iotblog/transforming-manufacturing-with-the-help-of-ontologies/4083555)

### 3.2 Healthcare Ontology (FHIR)

**Standard**: HL7 FHIR (Fast Healthcare Interoperability Resources) is the modern standard for healthcare data exchange. FHIR defines **157 resource types** organized into categories.

**Core Resource Types (Object Types)**:

| Resource | Description | Key Properties |
|----------|-------------|----------------|
| Patient | Demographics and admin info | name, birthDate, gender, address, identifier |
| Practitioner | Healthcare provider | name, qualification, specialty |
| Organization | Hospital, clinic, insurer | name, type, address, contact |
| Encounter | Patient-provider interaction | status, class, period, reason |
| Condition | Diagnosis, health condition | code, clinicalStatus, severity, onset |
| Observation | Measurement or assessment | code, value, effectiveDateTime, status |
| Medication | Drug information | code, form, amount, ingredient |
| MedicationRequest | Prescription | medication, dosageInstruction, status |
| Procedure | Clinical intervention | code, status, performedDateTime |
| DiagnosticReport | Collection of observations | code, status, result, conclusion |
| Claim | Insurance claim | type, provider, total, item |

**FHIR's design pattern**: Resources are modular -- clinical data is split across multiple resources linked by references. A prescription references the receiving Patient, a diagnostic report consists of multiple Observations. Each resource has a standard structure with metadata, narrative, and data elements.

**Lesson for Spider**: FHIR's 157 resources demonstrate that a mature, production healthcare ontology is large. However, a practical SMB deployment might use only 15-25 of these core resources. Spider's healthcare template should start with Patient, Encounter, Practitioner, Organization, Observation, Condition, Medication -- the "inner core."

Sources: [FHIR Resource List](https://www.hl7.org/fhir/resourcelist.html), [FHIR Patient Resource](https://www.hl7.org/fhir/patient.html), [FHIR Encounter Resource](https://www.hl7.org/fhir/encounter.html), [FHIR Data Model Deep Dive](https://kodjin.com/blog/introduction-to-fhir-data-model/)

### 3.3 Financial Services Ontology (FIBO & BIAN)

**FIBO (Financial Industry Business Ontology)**: Developed by the Enterprise Data Management Council (EDMC), published in OWL. As of 2025/Q3 Production: **2,457 classes** across major domains:

- **Business Entities (BE)**: Legal entities, corporate structures, governance
- **Financial Business and Commerce (FBC)**: Markets, exchanges, regulatory
- **Securities (SEC)**: Equities, debt instruments, issuance, classification
- **Derivatives (DER)**: Options, futures, swaps
- **Loans (LOAN)**: Mortgages, credit facilities
- **Foundations (FND)**: Dates, amounts, parties, addresses (shared infrastructure)

**BIAN (Banking Industry Architecture Network)**: A reference architecture for banking based on SOA principles. BIAN defines self-contained "Service Domains" as bounded contexts. Key service domains include: Customer Management, Current Account, Savings Account, Payment Processing, Credit Assessment, Regulatory Compliance, Fraud Detection.

**Core Object Types for a Banking/Financial Services Ontology**:

| Object Type | Description |
|-------------|-------------|
| Customer | Individual or organization with accounts |
| Account | Financial account (checking, savings, investment) |
| Transaction | Financial movement (debit, credit, transfer) |
| Portfolio | Collection of financial instruments |
| Instrument | Security, loan, derivative |
| Risk Assessment | Evaluation of credit/market/operational risk |
| Counterparty | Entity on the other side of a transaction |
| Contract | Legal agreement governing financial relationships |
| Regulatory Filing | Compliance-related submission |

Sources: [FIBO GitHub](https://github.com/edmcouncil/fibo), [FIBO Spec](https://spec.edmcouncil.org/fibo/), [BIAN](https://bian.org/), [BIAN Wikipedia](https://en.wikipedia.org/wiki/Banking_Industry_Architecture_Network), [Ontotext Financial KG](https://www.ontotext.com/blog/the-power-of-ontologies-and-knowledge-graphs-for-the-financial-industry/), [FIB-DM](https://fib-dm.com/finance-ontology-transform-data-model/)

### 3.4 Retail/E-Commerce Ontology (GoodRelations/Schema.org)

**Standard**: GoodRelations is a lightweight e-commerce ontology that has been "almost fully integrated into schema.org" since 2012. It is the official e-commerce data model of schema.org, supported by Google, Yahoo, Bing, and Yandex.

**Core Object Types**:

| Object Type | Description | Key Properties |
|-------------|-------------|----------------|
| Customer | Individual buyer | name, email, loyalty_tier, acquisition_date |
| Product | Item for sale | sku, name, category, price, weight, dimensions |
| ProductCategory | Hierarchical classification | name, parent_category, level |
| Order | Purchase transaction | order_number, status, total, placed_at |
| OrderLine | Individual item in an order | product, quantity, unit_price, discount |
| Inventory | Stock tracking per location | product, location, quantity_on_hand, reorder_point |
| Store/Location | Physical or virtual point of sale | name, address, type, hours |
| Supplier | Entity providing products | name, contact, lead_time, payment_terms |
| Shipment | Delivery of goods | tracking_number, carrier, status, estimated_arrival |
| Return | Product return/exchange | reason, status, refund_amount |
| Promotion | Discount or marketing offer | type, discount_value, valid_from, valid_to, conditions |

**Knowledge graph advantage for retail**: The benefit lies in interconnecting data from disparate systems -- ecommerce websites, inventory, product and customer insights, delivery information, location and preferences data.

Sources: [GoodRelations W3C Wiki](https://www.w3.org/wiki/GoodRelations), [Product Types Ontology](http://www.productontology.org/), [Ontotext KG for Retail](https://www.ontotext.com/blog/knowledge-graphs-for-retail/), [Oracle Retail Data Model](https://docs.oracle.com/cd/B19306_01/bi.102/e10084/logical.htm)

### 3.5 Summary of Published Standards

| Industry | Standard | Maturity | Size | Governance Body |
|----------|----------|----------|------|-----------------|
| Healthcare | HL7 FHIR | Production (v5.0) | 157 resource types | HL7 International |
| Banking | BIAN | Production (v12+) | ~300 service domains | BIAN Association |
| Finance | FIBO | Production (2025Q3) | 2,457 classes | EDMC / OMG |
| Manufacturing | ISA-95 | Production | ~50 object models | ISA / IEC |
| E-Commerce | GoodRelations/Schema.org | Production | ~800 types (schema.org total) | W3C / schema.org |

---

## 4. ENTITY RESOLUTION

### 4.1 The Core Problem

Entity resolution answers: "Is record A from System X the same real-world entity as record B from System Y?" This is the fundamental challenge when building an ontology that spans multiple source systems. The same customer appears in the CRM as "John Smith, ID 12345" and in the ERP as "J. Smith, Account ACC-98765."

Entity resolution encompasses: record linking, record matching, record deduplication, merge-purge, and entity analytics.

### 4.2 Techniques Spectrum

**Rule-Based Matching**:
- Exact match on deterministic keys (email, tax ID, phone number)
- Pattern-based standardization (address normalization, name parsing)
- Pros: Transparent, auditable, fast to implement
- Cons: Brittle, misses fuzzy matches

**Fuzzy/Probabilistic Matching**:
- String similarity metrics: Levenshtein Distance, Jaro-Winkler
- Phonetic algorithms: Soundex, Metaphone
- Probabilistic scoring: Fellegi-Sunter model
- Pros: Handles typos, abbreviations, variations
- Cons: Requires tuning, can produce false positives

**ML-Based Matching**:
- Supervised models trained on labeled match/non-match pairs
- Deep learning approaches (Siamese networks, transformers)
- Recent advances: Multi-agent RAG frameworks with specialized agents
- Pros: Highest accuracy, learns domain-specific patterns
- Cons: Requires labeled training data, less transparent

**LLM-Based Matching (emerging 2024-2025)**:
- Large language models for zero-shot or few-shot entity matching
- Multi-agent RAG frameworks decompose ER into specialized agents
- Pros: Flexible, minimal training data needed
- Cons: Expensive at scale, latency concerns

### 4.3 Palantir's Entity Resolution Approach

Palantir offers **Foundry Entity Resolution** as a dedicated product that "seamlessly links records with AI to establish a reliable, de-duplicated data foundation." In the Palantir system, object resolution is "the act of combining two or more Objects" -- for instance, resolving objects from two different source systems that refer to the same real-world entity.

Within pipelines, Palantir provides:
- **Levenshtein distance expressions** in advanced joins for fuzzy matching
- **Standard deduplication** using specified uniqueness columns
- **Time-bounded deduplication** for streaming data
- **Streaming primary keys** that control how consumers compute a deduplicated current view from a changelog

### 4.4 MDM vs Ontology-Based Resolution

| Dimension | Traditional MDM | Ontology-Based Resolution |
|-----------|----------------|---------------------------|
| Storage | Relational DBMS for master records | Graph/RDF store with equivalence declarations |
| Matching | Rule-based, batch processing | Semantic equivalence, real-time possible |
| Flexibility | Schema changes require migrations | Declare equivalence and be done |
| Cross-system | Requires ETL to golden record | Namespace-based disambiguation (Purchasing:suppliers = A/P:vendors) |
| Cost | High license + integration costs | Potentially lower maintenance for SMBs |
| Maturity | 20+ year track record | Emerging but growing rapidly |

**Key insight for Spider**: For SMBs, a hybrid approach is optimal. Use deterministic matching on strong keys (email, phone, tax ID) for the 80% case, then expose fuzzy-match candidates for human review. The ontology layer can declare equivalence between matched entities without merging the underlying source records -- preserving audit trails and allowing rollback.

In 2025, the emphasis in MDM is shifting to "continuous governance with real-time updates, metadata-aware pipelines, and observability that monitors data health across the master-data lifecycle." New MDM solutions are being built with "machine learning, anomaly detection and smart entity resolution in their core design."

Sources: [Palantir Foundry Entity Resolution](https://www.palantir.com/foundry-entity-resolution/), [Palantir Community Fuzzy Matching](https://community.palantir.com/t/entity-resolution-fuzzy-matching/2160), [Entity Resolution Guide](https://www.peopledatalabs.com/data-lab/datafication/entity-resolution-guide), [AI-Driven MDM 2025](https://apptad.com/blogs/ai-driven-master-data-management-trends-shaping-2025/), [Datavera Ontology MDM](https://datavera.org/en/ekg_ontology.html)

---

## 5. SCHEMA EVOLUTION IN PRACTICE

### 5.1 Breaking vs Non-Breaking Changes

**Non-breaking (additive) changes** -- safe to apply at any time:
- Adding a new Object Type
- Adding a new Property to an existing Object Type
- Adding a new Link Type
- Updating display names, descriptions, icons
- Deleting a Property that has no user edits

**Breaking changes** -- require migration strategy:
- Changing the data type of an existing property
- Changing an object type's backing datasource
- Changing the primary key of an object type
- Renaming or deleting properties that have existing user edits
- Modifying struct field types
- Deleting struct fields with existing edits

### 5.2 Palantir's Schema Migration Framework

When a breaking schema change is saved in Ontology Manager, the system automatically detects it and displays a warning. Users must define a migration before saving. Once saved:

1. A new schema version is created for the object type
2. A **replacement Funnel batch pipeline** is orchestrated to update the index
3. The pipeline creates an entirely new index in the background

**Available migration instructions**:
- **Drop all property edits**: Removes user modifications from specific properties (used when deleting a property with no replacement)
- **Drop all struct field edits**: Targets struct field modifications
- **Drop all edits**: Resets object state to source data
- **Move edits**: Transfers edits to renamed/replacement properties or new datasources (used when renaming a property or replacing a datasource)
- **Move struct field edits**: Handles struct field reassignments
- **Cast property to new type**: Supports ~30 type conversions (String to Integer, Double to Long, Timestamp to String, etc.)
- **Revert**: Undoes previously applied migrations

Limitation: Maximum 500 migrations per operation to prevent performance degradation.

### 5.3 Comparison: Palantir vs Traditional DB Migration Tools

| Dimension | Palantir Replacement Pipeline | Flyway / Alembic / Liquibase |
|-----------|-------------------------------|-------------------------------|
| **Scope** | Ontology schema (semantic model) | Database schema (physical model) |
| **User edits** | Preserves/migrates user edits through intelligent rules | No concept of user edits vs source data |
| **Indexing** | Automatically manages search indexes via replacement pipelines | Manual index management |
| **Approach** | Declarative (choose migration instruction) | Imperative (write migration scripts) |
| **Rollback** | Built-in revert through History section | Requires writing reverse migrations |
| **Versioning** | Automatic schema versions per object type | Version-numbered migration files |
| **Breaking change detection** | Automatic detection with warnings | Developer must identify breaking changes |

### 5.4 General Ontology Versioning Best Practices

From the formal ontology community:

1. **Track version information within the ontology**: Use standardized properties (`owl:versionInfo`, custom annotations) so version metadata is inseparable from the ontology.
2. **Use semantic versioning (X.Y.Z)**: Major = breaking changes, Minor = backward-compatible additions, Patch = bug fixes. This communicates impact level to consumers.
3. **Deprecate before deleting**: Signal that modeling is no longer supported before removing it. Deprecated entities should remain "until the next major change," providing transition periods.
4. **Keep a changelog**: Use version control with sorted serialization to avoid false change detection. Automation preferred over manual tracking.
5. **Deliver the right version**: Provide both a "latest" endpoint and specific version endpoints. Maintain archives of prior versions.

### 5.5 The Expand-Contract Pattern

For breaking changes in production, the widely adopted pattern is:
1. **Expand**: Introduce the new schema alongside the old one
2. **Migrate**: Update consumers to use the new fields/types
3. **Contract**: Remove the old fields/types only after all consumers have migrated

This is equivalent to Palantir's "move edits" migration instruction at the ontology level, and maps to Flyway's approach of additive-then-cleanup migrations at the database level.

Sources: [Palantir Schema Migrations](https://www.palantir.com/docs/foundry/object-edits/schema-migrations), [Enterprise Knowledge Ontology Versioning](https://enterprise-knowledge.com/top-5-tips-for-managing-and-versioning-an-ontology/), [Schema Evolution Best Practices](https://dataengineeracademy.com/module/best-practices-for-managing-schema-evolution-in-data-pipelines/), [Confluent Schema Registry Best Practices](https://www.confluent.io/blog/best-practices-for-confluent-schema-registry/)

---

## 6. IMPLICATIONS FOR SPIDER'S VERTICAL ONTOLOGY TEMPLATES

### 6.1 Template Design Principles

Drawing from all research above, Spider's ontology templates should follow these principles:

1. **Start with 8-15 core Object Types per vertical** -- aligned with Palantir's pilot-size ontology and Stardog's "5-10 entities" recommendation. This is the "inner core" that 80% of SMBs in that vertical will need.

2. **Use DDD's Ubiquitous Language** -- object type names must match exactly how business users talk about their domain. "Bon de commande" not "PurchaseOrder" for French SMBs.

3. **Follow Palantir's naming conventions** -- string primary keys, `{verbed}_at_timestamp` for dates, `{foreign_object_type}_id` for foreign keys. This is battle-tested at scale.

4. **Model structs for embedded data** -- Addresses, contact info, and other multi-field attributes that do not have independent lifecycles should be structs (max 10 fields, no nesting).

5. **Design for additive evolution** -- new properties and object types can be added without breaking existing apps. Breaking changes should be rare and managed through expand-contract patterns.

6. **Validate through working applications, not diagrams** -- following Palantir's approach, validate ontology by building simple apps on top of it and showing them to business users.

### 6.2 Recommended Vertical Template Sizes

Based on industry standards and practical deployment experience:

| Vertical | Core Object Types | Extended (post-expansion) | Reference Standard |
|----------|-------------------|---------------------------|-------------------|
| Manufacturing | 10-12 | 25-40 | ISA-95 |
| Healthcare | 12-15 | 30-50 | HL7 FHIR |
| Financial Services | 8-12 | 25-45 | FIBO / BIAN |
| Retail/E-Commerce | 10-12 | 20-35 | GoodRelations / Schema.org |
| Generic SMB | 6-8 | 15-25 | DDD patterns |

### 6.3 Entity Resolution Strategy for Spider

For SMBs connecting 3-7 systems (typical Odoo + CRM + accounting + vertical tools):

1. **Phase 1 (Pilot)**: Deterministic matching on strong keys (email, phone, SIRET/SIREN for French companies)
2. **Phase 2 (Expand)**: Fuzzy matching on names and addresses using Levenshtein/Jaro-Winkler
3. **Phase 3 (Scale)**: ML-based matching for complex entities (products across catalogs, contacts across CRMs)

The ontology should support entity resolution by design -- every Object Type should have a `source_system` property and a `canonical_id` property, allowing the same real-world entity to exist multiple times with linkage to a resolved canonical record.

### 6.4 Schema Evolution Strategy for Spider

1. **Semantic versioning for templates**: X.Y.Z where major = breaking structural changes, minor = new optional object types/properties, patch = bug fixes to property definitions.
2. **Deprecation-first approach**: Never delete -- deprecate, wait one major version, then remove.
3. **Additive-only between major versions**: New properties always have defaults. New object types are opt-in.
4. **Migration tooling**: Build a lightweight equivalent of Palantir's migration instructions -- at minimum, support "move property" and "cast type" operations.

---

## Sources

### Palantir Documentation
- [Palantir Ontology Overview](https://www.palantir.com/docs/foundry/ontology/overview)
- [Palantir Core Concepts](https://www.palantir.com/docs/foundry/ontology/core-concepts)
- [Palantir Object Types Overview](https://www.palantir.com/docs/foundry/object-link-types/object-types-overview)
- [Palantir Properties Overview](https://www.palantir.com/docs/foundry/object-link-types/properties-overview)
- [Palantir Structs Overview](https://www.palantir.com/docs/foundry/object-link-types/structs-overview)
- [Palantir Link Types Overview](https://www.palantir.com/docs/foundry/object-link-types/link-types-overview)
- [Palantir Action Types Overview](https://www.palantir.com/docs/foundry/action-types/overview)
- [Palantir Interfaces Overview](https://www.palantir.com/docs/foundry/interfaces/interface-overview)
- [Palantir Schema Migrations](https://www.palantir.com/docs/foundry/object-edits/schema-migrations)
- [Palantir Solution Design](https://www.palantir.com/docs/foundry/use-case-life-cycle/solution-design)
- [Palantir Solution Designer Tutorial](https://www.palantir.com/docs/foundry/solution-designer/tutorial-create-your-first-diagram)
- [Palantir Foundry Entity Resolution](https://www.palantir.com/foundry-entity-resolution/)

### Palantir Community & Blog
- [Ontology and Pipeline Design Principles](https://community.palantir.com/t/ontology-and-pipeline-design-principles/5481)
- [Ontology-Oriented Software Development](https://blog.palantir.com/ontology-oriented-software-development-68d7353fdb12)
- [Entity Resolution / Fuzzy Matching](https://community.palantir.com/t/entity-resolution-fuzzy-matching/2160)

### Knowledge Graph & Ontology Design
- [Stardog: Building a Knowledge Graph](https://www.stardog.com/building-a-knowledge-graph/)
- [Neo4j: Ontologies and Semantics](https://neo4j.com/blog/knowledge-graph/ontologies-in-neo4j-semantics-and-knowledge-graphs/)
- [Enterprise Knowledge: Ontology vs Knowledge Graph](https://enterprise-knowledge.com/whats-the-difference-between-an-ontology-and-a-knowledge-graph/)
- [Enterprise Knowledge: Ontology Versioning Tips](https://enterprise-knowledge.com/top-5-tips-for-managing-and-versioning-an-ontology/)
- [Knowledge Graph vs Ontology](https://www.puppygraph.com/blog/knowledge-graph-vs-ontology)
- [Ontology Design Patterns (ResearchGate)](https://www.researchgate.net/publication/227215903_Ontology_Design_Patterns)
- [Modular Ontology Modeling Tutorial](https://www.sciencegate.app/document/10.3233/ssw200032)

### Schema.org
- [Schema.org Data Model](https://schema.org/docs/datamodel.html)
- [Schema.org Full Hierarchy](https://schema.org/docs/full.html)
- [Schema.org Wikipedia](https://en.wikipedia.org/wiki/Schema.org)

### Domain-Driven Design
- [DDD Wikipedia](https://en.wikipedia.org/wiki/Domain-driven_design)
- [Context Mapper: Bounded Context](https://contextmapper.org/docs/bounded-context/)
- [Martin Fowler: Bounded Context](https://martinfowler.com/bliki/BoundedContext.html)

### Industry Standards
- [Rhize: What is ISA-95](https://rhize.com/blog/what-is-isa95/)
- [IEEE: ISA-95 Based Ontology](https://ieeexplore.ieee.org/document/8471929/)
- [Digital Twin Manufacturing Ontologies (GitHub)](https://github.com/digitaltwinconsortium/ManufacturingOntologies)
- [HL7 FHIR Resource List](https://www.hl7.org/fhir/resourcelist.html)
- [HL7 FHIR Patient Resource](https://www.hl7.org/fhir/patient.html)
- [FHIR Data Model Deep Dive](https://kodjin.com/blog/introduction-to-fhir-data-model/)
- [FIBO GitHub](https://github.com/edmcouncil/fibo)
- [FIBO Spec](https://spec.edmcouncil.org/fibo/)
- [BIAN](https://bian.org/)
- [BIAN Wikipedia](https://en.wikipedia.org/wiki/Banking_Industry_Architecture_Network)
- [GoodRelations W3C Wiki](https://www.w3.org/wiki/GoodRelations)
- [Ontotext: KG for Financial Industry](https://www.ontotext.com/blog/the-power-of-ontologies-and-knowledge-graphs-for-the-financial-industry/)
- [Ontotext: KG for Retail](https://www.ontotext.com/blog/knowledge-graphs-for-retail/)

### Entity Resolution & MDM
- [People Data Labs: Entity Resolution Guide](https://www.peopledatalabs.com/data-lab/datafication/entity-resolution-guide)
- [AI-Driven MDM Trends 2025](https://apptad.com/blogs/ai-driven-master-data-management-trends-shaping-2025/)
- [Datavera: Ontology-Based MDM](https://datavera.org/en/ekg_ontology.html)
- [Tamr: Ontologies with Mastered Data](https://www.tamr.com/blog/how-to-leverage-ontologies-with-your-mastered-data)

### Schema Evolution
- [Data Engineer Academy: Schema Evolution](https://dataengineeracademy.com/module/best-practices-for-managing-schema-evolution-in-data-pipelines/)
- [Confluent: Schema Registry Best Practices](https://www.confluent.io/blog/best-practices-for-confluent-schema-registry/)
- [Backward Compatibility in Schema Evolution](https://www.dataexpert.io/blog/backward-compatibility-schema-evolution-guide)
