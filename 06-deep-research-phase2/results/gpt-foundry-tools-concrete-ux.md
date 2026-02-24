# How Palantir Foundry’s core builder tools work in practice

## What this report focuses on
You asked for the builder reality: what an end user actually clicks, what panels exist, what artefacts get created, how schema and pipelines evolve, and where the “magic” is actually just versioning plus orchestration.

Two important constraints shape what can be stated with confidence from public sources. First, Foundry UI is role and environment dependent (permissions, enabled capabilities, Object Storage version, AIP availability), so every “exact” screen can vary even when the workflow is the same. Second, Palantir’s public docs include many annotated screenshots and step guides, but they do not publish every UI microflow or every backend service contract; where something is not explicitly documented, I label it as an inference and keep it conservative.

## Ontology manager: UI anatomy and the step-by-step builder flow

### What the Ontology manager UI looks like
Palantir documents Ontology Manager (OMA) as a multi-pane app with persistent top bar and left sidebar. The top bar is doing three jobs: global search across ontology resources, creation of new ontology resources, and branch switching or creation. citeturn12view2

The left sidebar is the resource navigator. The “Discover” landing view is a configurable homepage that can show favourites, recently viewed object types, and groups, and the docs include screenshots for Discover and the annotated “top bar + sidebar” layout. citeturn12view2turn12view3

Ontology Manager also has distinct entity views that are worth understanding as separate “screens” in the UX:
- Object type view: a left sub-sidebar for pages (Overview, Properties, Datasources, Interfaces, etc.) and a right panel with the selected page content. citeturn12view2turn12view3  
- Property editor view: opened by selecting a property; it’s a dedicated editing interface (with its own screenshot in docs). citeturn12view3  
- Link type view: opened from the object’s link type graph; includes Overview/Datasources pages (with screenshot). citeturn12view3  
- Action type view and Function type view: each has its own “entity page” layout and observability tabs; functions are edited in a code repository, not inline. citeturn12view3turn12view4  

If you want a single “UI mental model”: Ontology Manager behaves like a git-branch-aware schema IDE where everything you do is staged, then committed to the ontology.

### Creating a new Object Type step-by-step
Palantir’s docs describe two ways to create an object type: a guided helper (the primary path) and manual completion if you exit early. citeturn11view1turn14search7

The workflow is explicit in the documentation even when every click is not enumerated:
1. Create object type in the guided helper, then choose a project save location and select “Create”, which only stages changes. You still need to “Save” in the upper right of Ontology Manager to actually apply to the ontology. citeturn11view1turn18view0  
2. Ensure the object type has: metadata, a backing datasource, properties mapped to datasource columns, and a configured primary key and title key. citeturn11view1  
3. If you exit the helper early, the object type remains “unsaved” until you complete the manual checklist Palantir lists: add metadata, add a backing datasource, add properties, map properties, then configure primary and title keys. citeturn11view1  

Two UI details matter because they map to “how does it actually work”:
- There is a datasource pane and a properties pane in the object type configuration experience. The docs call out a specific button: “Add all unmapped columns as new properties”, which infers IDs, display names, and base types from the backing dataset schema. citeturn11view1  
- Primary key and title key are configured in the property editor metadata pane; changing primary key is treated as materially dangerous because edits attach to primary key values. citeturn11view1turn13view2  

A training “speedrun” on Palantir Learn mirrors the same flow at the UI level: navigate to Ontology Manager, click “New”, choose “Object Type”, then proceed with object configuration. citeturn0search8turn15search5

### Defining Properties and the actual type system you get
In Foundry’s ontology, a property is the schema definition of a characteristic of an object type; mapping it to a column is what causes actual values to appear in apps. citeturn13view1turn4search11

The types Palantir publicly documents for properties (and which ones can be keys) are precise and more constrained than most marketing lists. This is the load-bearing table:
- Common numeric/text: String, Integer, Short.  
- Time: Date, Timestamp; timestamp as primary key is explicitly discouraged.  
- Boolean/Byte/Long: supported but with caveats; Long has JavaScript representational issues and is often recommended to be String instead.  
- Float-like: Float, Double, Decimal (not valid as primary key).  
- Vector.  
- Array (no null elements; nested arrays not supported in Object Storage V2).  
- Struct (no nesting; fields cannot be arrays; see struct constraints).  
- Media reference, Time series, Attachment.  
- Geopoint, Geoshape.  
- Marking.  
- Cipher. citeturn13view1turn13view2  

From a builder perspective, property editing is not just “pick a type”. The property metadata editor exposes: display name, description, status (experimental/active/deprecated), API name, key designation (title/primary), value formatting, conditional formatting, type classes, render hints (searchable/sortable toggles affect indexing behaviour), and visibility (prominent/hidden). citeturn17view1turn13view2

Creating more complex types is still done in the same property editor UI: a struct property is created by choosing “Struct” as base type, selecting a backing column, then adding fields in a “Struct fields” section. citeturn14search1turn11view3  
Media references are also “just a base type”, but require that the backing dataset contains a media reference column and that the object type has a media source configured in its Capabilities tab pointing at the relevant media set. citeturn13view0  

### Creating Link Types and what “cardinality” really means in Foundry
A link type is the schema definition of a relationship between two object types; a link instance is analogous to a joined row representing one relationship instance. citeturn11view2turn4search0  

Palantir’s docs also make a backend-relevant point: links are not “virtual edges”. They are created and displayed by adding backing datasources to the object types referenced by the link type; for many-to-many cardinality, the link types themselves have datasources backing them. citeturn11view2  

Cardinality in practice shows up in developer bindings. In the TypeScript API generated for object types, Foundry supports 1-to-1, 1-to-many, and many-to-many. When traversing the “1 side” you get a `SingleLink` and call `get()` or `getAsync()`. citeturn16view3  

For link creation UX: Palantir documents a guided link type creation flow that ends with selecting a project save location, submitting, and then saving in Ontology Manager to apply. citeturn16view2turn11view0  
The docs also describe “object-backed link types” as a first-class modelling construct: you can represent a relationship as its own object type to store metadata on the relationship itself (example: a Flight Manifest object linking Aircraft and Flight, with extra properties like Pilot). citeturn16view2  

Operationally: if you think “I need attributes on the edge”, Foundry is telling you to promote the edge to an object-backed link.

### Interfaces as abstract types and how you implement them
Interfaces in Foundry are explicitly described as an ontology type describing the “shape” and capabilities of object types, enabling polymorphism across multiple implementations. citeturn15search10turn15search3

Creation flow in Ontology Manager:
- Select New > Interface (or use the Interfaces page).  
- Provide display name and API name, optional description and icon.  
- Add properties to the interface (locally recommended) and mark each required or optional. citeturn16view0

Implementation flow is concrete and UI-driven:
- From an object type’s Interfaces tab, select “Implement new interface”, choose the interface, then map required interface properties to existing object properties (optional interface properties can be skipped). citeturn16view1  
- If the interface declares required link type constraints, you must map link types that satisfy each constraint; you can choose an existing link type or create a new one during mapping. citeturn16view1  

The docs also note a product boundary: implementing interfaces in Pipeline Builder is supported for property mapping, but Pipeline Builder does not support link type constraint mapping; that must be done in Ontology Manager. citeturn16view1

### Functions as computed logic and “TypeScript computed properties”
Foundry distinguishes ontology schema (types, properties, links, actions) from executable logic (Functions, Actions, AIP Logic). Ontology Manager exposes “Function type view”, but edits to functions happen in a Functions code repository; the UI provides an “Open in Code Repository” entry point. citeturn12view4  

What functions can do in Foundry is broader than classic FaaS. Palantir documents first-class ontology support: reading properties, traversing links, and performing ontology edits, with the outcome usable in Workshop and actions. citeturn15search2turn15search4turn9search8  

From a “computed properties” standpoint, the most builder-visible manifestation is inside Workshop: the Object Table widget supports “derived columns generated on-the-fly via a Function”. citeturn26search0  
So the implementation reality is: define ontology and APIs, author function code against generated object/link bindings, then consume functions as derived computation in apps.

## Modelling decisions: when to use Object Type vs Property vs Link vs Struct

### The minimum viable decision framework Foundry implies
Palantir’s “core concepts” definition is clean: object type is an entity/event, property is a characteristic, link type is a relationship, action type changes objects. citeturn4search11  
That is definitional, not a heuristic. The heuristics show up indirectly in constraints, key semantics, and in special constructs like object-backed links and structs.

A practical builder framework, aligned to what Foundry actually supports:

Create a separate Object Type when:
- The thing needs its own identity and lifecycle: it has a stable primary key, it is created/modified independently, or it has writeback edits that you want to preserve across other changes. Primary keys are treated as the anchor for edits: edits are “permanently attached” to primary key values, and changing the primary key triggers deletion of edits. citeturn11view1turn17view0  
- The thing needs to be linked to from multiple places; links are first-class and show up as traversable fields in the generated APIs. citeturn16view3  
- The “relationship” itself needs attributes. That is exactly why object-backed link types exist. citeturn16view2  

Keep it as a Property when:
- It is an attribute solely about the parent object and does not need its own lifecycle. Foundry explicitly maps properties to dataset columns and treats them as “fields” in object APIs, which is the fast path for operational apps. citeturn13view1turn16view3  
- You benefit from render hints, formatting, and searchability controls at the property level rather than navigating to another object. citeturn13view2turn17view1  

Use a Link when:
- The relationship is navigational and queryable as a relationship, not just a string foreign key. Link types are modelled and surfaced in user apps by backing datasources, and cardinality determines traversal semantics. citeturn11view2turn16view3  

Use a Struct when:
- You want a bounded, schema’d nested group of fields that behaves as “one property”, and you can live within strict constraints: depth one (no nesting), max 10 fields, limited field types, and non-intuitive query semantics for arrays of structs because of how they are indexed. citeturn11view3turn4search1  

The key is that struct is not a general “nested JSON” type: it is a constrained schema feature with explicit limitations, and that should push you toward linked objects for many real-world cases.

### Worked example: “Customer Address”
There are three distinct “address” realities; each maps to a different Foundry modelling choice.

Address as a simple attribute (Property):
- Use when the address is single-valued, rarely changes, and is not an entity you work with independently.  
- Implementation: a handful of properties like `street`, `postcode`, `city`, `country` (or one string field) mapped straight from the backing dataset. This fits Foundry’s property-to-column model. citeturn13view1turn11view1  

Address as a bounded sub-structure (Struct property):
- Use when you want “address” as a single conceptual field but still need structured components (street, city, etc.) and you stay within struct constraints. Structs are explicitly supported in Ontology Manager and Workshop, but cannot be nested and have tight field and type constraints. citeturn11view3turn4search1  

Address as a first-class entity (Address Object Type linked to Customer):
- Use when addresses have their own lifecycle: multiple addresses per customer, history, validation workflows, geo enrichment, deduplication, or address-level permissions.  
- Use a link type Customer ↔ Address; the relationship can be “one-to-many” (a customer has many addresses) or “many-to-many” if shared, and that impacts datasource backing. citeturn11view2turn16view3  

A Foundry-specific extra: if you need metadata on the relationship itself (example: “address type”, “valid from/to”, “verified by”, “source system”), object-backed links are the canonical pattern: create an intermediate object type to store relationship metadata and link both ends to that object. citeturn16view2  

### What Palantir implicitly teaches FDEs through constraints and tooling
Public docs do not publish an “FDE modelling playbook” as a single artefact, but the platform nudges you hard through:
- Key semantics: title key is “display name”; primary key is unique, and edits attach to it. This pushes you to choose stable identifiers and avoid time-based keys. citeturn11view1turn13view1  
- Type limitations: arrays cannot contain nulls; nested arrays not supported in OSv2; struct fields cannot be arrays; long is awkward for JS clients. These constraints push you away from “throw JSON at it” modelling. citeturn13view1turn11view3  
- First-class support for object-backed links: Palantir explicitly positions them as the way to add metadata to relationships. citeturn16view2  

If you want a compressed rule: model for operational workflows first, then for analytics. Foundry’s app layer (Workshop actions, object navigation, function-backed derived columns) rewards semantic, navigable types far more than “raw table with dozens of columns”.

## Schema evolution: how changes actually propagate and how migrations work

### Editing object types and properties without breaking everything
Editing existing object types is where Foundry’s implementation details matter: your ontology is not “just schema”; it is indexed into object storage and may have user edits/writeback semantics.

Editing object type metadata (icon, display names/description, status, visibility, API name) is supported in-place. Some changes are blocked when status is active (example: API name cannot be changed for active object types). citeturn17view0turn17view1  

Changing backing datasources is a UI flow: go to the Properties page, open “Edit property mapping”, then use “Replace” in the Datasources pane to pick a new datasource. Properties remap automatically only if the new datasource schema matches; otherwise you remap. citeturn17view0  

Property edits can be done individually or in bulk. Bulk editing supports operations like changing base type, adding/removing type classes, render hints, visibility, and formatting. citeturn17view1  

### The Object Storage split: OSv1 vs OSv2 is the real schema-evolution boundary
Palantir is explicit that Object Storage V1 (Phonograph) cannot migrate user edits across breaking schema changes; schema changes are discouraged and can require unregistering/reregistering datasources, risking edit history loss. citeturn17view0turn18view0  

Object Storage V2 introduces a schema migration framework. Ontology Manager detects breaking schema changes, shows a warning, and introduces a Migrations tab in the “Review changes” flow. It blocks you from saving until you specify a migration option. citeturn18view0  

That “migration tool” is therefore not external: it is built into Ontology Manager’s save workflow for OSv2.

### The replacement pipeline pattern: what happens under the hood
When you save a breaking schema change in Ontology Manager:
- A new schema version is created in the backend.  
- A “replacement Funnel batch pipeline” is orchestrated to update the object type’s index.  
- The new version becomes queryable once the replacement completes and the new version is declared fully hydrated by object databases. citeturn18view0turn4search12  

This is the cleanest “implementation-level” statement Palantir publishes: schema changes are mediated by a versioned index rebuild pipeline, not an in-place mutation.

### What counts as breaking and what migrations exist
Breaking changes include: changing input datasources, changing primary key, changing property type, changing property ID if it has edits, deleting edited properties or struct fields, changing struct field type. citeturn18view0  

Non-breaking changes include: display name/title key/render hints/type classes/visibility updates on edited properties, and deleting or changing fields that never received edits. citeturn18view0turn17view0  

Example supported OSv2 migration actions include:
- Drop all property edits (for a property).  
- Drop all struct field edits.  
- Drop all edits (reset object state to input datasources).  
- Move edits (used when replacing or moving where edits are stored). citeturn18view0  

### Advanced option: ontology as JSON
For advanced users, Palantir also documents export-import: ontology schema definitions can be exported to JSON, edited externally, and imported back, enabling “ontology as code” workflows. citeturn27search11  

This is powerful but operationally risky: you bypass the UI guardrails unless you replicate them in process.

## Pipeline builder and code repositories: the real build experience and how lineage is tracked

### Pipeline Builder UI: what you actually manipulate
Pipeline Builder is a graph-based builder where the graph is the primary view. Palantir’s navigation docs enumerate the UI elements and include screenshots:
- Graph canvas with panning/drag-select/layout tools.  
- “Add datasets” and “Transform” controls; selecting a dataset node opens a pop-up to add or edit transforms.  
- Outputs sidebar showing dataset outputs plus ontology-facing outputs (object types and link types), including schema editing and errors.  
- Preview panel for sampling the selected node’s data; right-click a dataset node to open full dataset preview. citeturn19view0turn19view1  

In short: you build a DAG visually, but you also maintain outputs, schemas, and build requirements from the sidebars.

### Visual pipeline creation: joins, unions, filters, aggregates, pivots
Pipeline Builder distinguishes two transformation primitives in the UI:
- Expressions: column in, column out (example: “Split string”).  
- Transforms: table in, table out (example: Pivot, Filter).  
They are configured through a unified interface where transforms like “Drop columns” sit alongside expressions like “Cast” and “Concatenate strings”. citeturn25search4turn6search1  

Concrete transform documentation shows what nodes exist and what configuration feels like:
- Join: select a dataset node, click Join, select the right dataset, then configure join type and match conditions in a form with previews and an Errors tab. citeturn19view2  
- Union: select dataset node, click Union; union retains duplicates; it is positioned as “combine all rows from each dataset”. citeturn25search3  
- Filter: filters rows based on a boolean condition; supported in batch and streaming. citeturn25search0  
- Aggregate: group-by and aggregations; batch. citeturn25search2  
- Pivot: aggregations grouped by columns, pivot values must be provided ahead of runtime so the output schema is known. citeturn25search1  

The transform surface area is huge (geospatial joins, window aggregation for streaming, media transforms, and LLM nodes exist), so the core builder reality is: most “nodes” are wrappers around well-defined transform functions with declared arguments and predictable schema effects. citeturn6search7turn25search8turn5search10  

### Can you mix visual nodes with PySpark code?
Not inside a single Pipeline Builder transform board in the way tools like Databricks notebooks mix code and UI.

Palantir’s official guidance is: Pipeline Builder is the collaborative “no-code” pipeline design tool; Code Repositories is where specialised code stages live (API calls, custom libraries, code-based logical concepts). Since both tools consume and produce Foundry datasets, you can insert code-repo-built datasets before, after, or in the middle of a Pipeline Builder pipeline, and manage schedules/health checks across the full pipeline in Data Lineage. citeturn21view0  

So “mixing” is at the dataset boundary, not inside a node.

### Code Repositories: the transforms API and what real code looks like
The Foundry Python transforms API is decorator-driven:
- Use `@transform.using(...)` to declare Inputs and Outputs; the function parameters match those declarations. citeturn22view0  
- Inputs can be loaded as Polars or pandas dataframes for single-node compute by default; Spark is available for distributed compute. citeturn22view0  
- Spark transforms can take multiple inputs and outputs (documented explicitly). citeturn25search13turn22view0  

Foundry also has the concept of a repository Pipeline object: each Python transforms sub-project exposes a `transforms.api.Pipeline` that registers datasets and locates/executes transform logic during builds. Automatic registration via `discover_transforms()` is the recommended default for most repos. citeturn22view1  

A realistic “join and write” transform therefore has this shape:
- Declare two Inputs (`sourceA`, `sourceB`) and one Output (`cleaned`).  
- Read inputs as Spark dataframes (or Polars if small).  
- Perform joins/cleans.  
- Write the output dataframe to the target dataset.  
This pattern is consistent with how Pipeline Builder and Ontology Manager expect “golden datasets” for ontology backing. The key is that the Ontology mapping step is separate: you write a dataset, then map it as a backing datasource. citeturn22view0turn11view1turn11view2  

### Scheduling pipelines: cron, event-driven, and how schedules appear in the UI
Foundry scheduling is dataset-centric: schedules run builds to keep pipelines up to date. citeturn7search14turn7search6

In Pipeline Builder itself, schedules can be configured to trigger:
- At certain times.  
- When data has updated.  
- When logic has updated.  
- Any combination of conditions. citeturn19view3turn7search14  

Schedules can target:
- A single dataset, dependencies, dependents, datasets connecting two datasets, or combinations. citeturn19view3turn7search14  

The UI entry point Palantir documents is: from a dataset preview, use Actions → “Manage Schedules”, which opens a Data Lineage graph with the schedules panel on the right and a “Create schedule” button. citeturn7search0  

This matters because it reveals the implementation contract: schedules are attached to datasets in the build graph, and Data Lineage is the operational control plane for them.

### Incremental processing vs full recomputation
Incremental computation is a first-class feature: it uses transform build history to avoid recomputing an entire output every run, and Foundry explicitly forbids input and output being the same dataset (to avoid cyclic dependencies). citeturn22view2  

At API level, the `incremental()` decorator converts normal TransformInput/Output/Context into incremental counterparts (IncrementalTransformInput/Output/Context) by reading build history from output datasets. citeturn22view3  

For complex logic (joins, aggregations, distinct), Palantir recommends using incremental with the full `transform()` decorator so you can control read and write modes; the “simple default” only safely works when added output rows are purely a function of added input rows. citeturn23search7turn22view3  

### Testing and CI for pipeline code
Foundry supports pytest-based unit tests for Python repositories (batch pipelines only) and can run tests as part of checks. Palantir also documents CI mechanics like `condaPackRun`, environment caching, and optional style checks via Gradle plugins. citeturn22view4  

The key connective tissue: pipeline health is treated as part of the build and release process, not “best effort”.

### Data Lineage: what it tracks, what the graph looks like, and how markings interact
Foundry Data Lineage is an interactive application for visualising how datasets flow through Foundry. It supports browsing and searching datasets, expanding ancestors/descendants, and visualising pipelines with different colourings. citeturn8search1turn9search0  

The navigation doc enumerates the UI and includes a screenshot with labelled regions: lineage graph, branch settings, side panel (Search & Browse; Properties and Histogram; Manage Builds; Manage Schedules; Related Artifacts), node details panel, graph tools, and “Save graph”. citeturn9search1turn8search18  

Two “implementation-level” capabilities show up here:

Markings and security propagation:
- Markings are Foundry’s mandatory access control mechanism; a marking defines eligibility criteria for access. citeturn8search5turn8search13  
- Data Lineage can simulate the impact of marking changes, and explicitly indicates nodes that “stop propagating markings” via code; the node properties panel surfaces that data access was modified via code. citeturn8search0turn8search9  
- Removing markings has strict mechanics: `stop_propagating` and `stop_requiring` are input transform properties and cannot be added on outputs. citeturn10search2turn10search14  

Rollback and provenance:
- Palantir documents pipeline rollback using data provenance of an upstream dataset transaction to identify downstream datasets and transactions and compute a rollback state, avoiding manual multi-step rollback. citeturn10search1  
- Rollback UX is lineage-driven: select dataset in a lineage graph, pick a branch, select a transaction in History, then “Rollback to transaction”. citeturn10search5  

Can you trace a specific value back to raw source?
- Public documentation describes dataset and transaction provenance (sufficient for “which upstream datasets and which build produced this output”). citeturn10search1turn10search5  
- Palantir also provides “find datasets with a given column” in Data Lineage, which is column-aware search within the lineage graph. citeturn8search15turn9search17  
- Cell or row-level “this exact field value came from that raw record” lineage is not described as a standard Data Lineage feature in public Foundry docs; if it exists in specific deployments, it is not documented in the same way as dataset provenance, so you should assume dataset and transaction-level traceability as the baseline.

## Workshop and the app layer: how you build operational tools and how it differs from Quiver, Contour, and Slate

### What Workshop looks like and what it is for
Workshop is explicitly positioned as a flexible application builder supporting operational patterns like inboxes, alert triage, task management, and investigations. citeturn27search5  

At the UI level, Workshop is widget-driven: modules are built by placing widgets into a layout and configuring inputs/outputs, display options, variables, and actions. The “Widgets” core concept doc describes adding a widget via “+ Add widget” and choosing from the widget selector modal. citeturn1search0turn26search10  

### Binding a Table to Ontology: Object Table widget mechanics
The Object Table widget is the main “grid view” primitive for ontology objects. It supports:
- Displaying one or multiple object types.  
- Choosing displayed columns, including time series columns and derived columns generated via a Function.  
- Sorting and other table behaviours. citeturn26search0  

A Palantir Learn “speedrun” shows the concrete column configuration UX: under Column Configuration, select “Add all properties”, then reorder columns by dragging properties using the handle UI. citeturn26search8turn26search19  

This is the practical binding model: Workshop doesn’t bind to datasets directly in the core operational widgets; it binds to object sets and object types within the ontology.

### Filters: property filters, date pickers, and narrowing object sets
Workshop’s filtering widgets are explicitly designed around object sets:
- Filter List: renders property-type filters as histograms, distribution charts, pickers, and type-ahead selectors; includes keyword search. citeturn26search1turn26search3  
- Separate widgets exist for time input as well, like Date and Time Picker. citeturn26search18  

The docs also clarify a subtle but important behaviour: Filter List configuration becomes richer once the object set is populated because it can infer which property types exist and enable keyword search and filtering by linked object presence. citeturn26search10  

### Actions and buttons: how writeback is wired into Workshop
Foundry Actions are ontology-native building blocks for creating, editing, deleting, and linking objects. Palantir’s Workshop Actions overview gives concrete examples like “Create New Flight” (creates an object and sets properties) and “Delay Flight” (modifies an object). citeturn1search8  

Action definition and governance:
- Actions are administered in Ontology Manager; creating/editing actions can require membership in specific administrative groups (example: `actions-admins`). citeturn1search4turn26search6  

Button wiring:
- Button Group widget can trigger Actions, Workshop events, URLs, and exports; docs give an example of configuring a button to trigger a “Modify Flight Destination” action editing a Destination property. citeturn26search2turn26search16  
- Inline Action widget provides form or table interfaces to create/modify/delete objects or links; it can be configured in Workshop or Ontology Manager. citeturn1search16  

Widget linking and cross-filtering:
- Workshop Events are the connective tissue: events can be triggered by widgets including Button Group and Object Table on row selection, allowing you to wire “click row in table A” into “set variable that filters widget B”. citeturn26search9  
This is the nearest thing Workshop has to a “reactive state management” layer: variables plus events.

### Workshop vs Quiver vs Contour vs Slate: a decision matrix grounded in documented capabilities
Workshop: operational applications
- Best when you need workflow: triage, actions, edits, object navigation, and operator UX patterns. citeturn27search5turn1search8  

Quiver: dashboards and KPI presentation
- Quiver dashboard mode is designed for read-only interactive dashboards to present insights from analysis; you can create dashboards per analysis and drag and drop content into dashboards. citeturn1search1turn1search5  
- Use when the centre of gravity is analysis outputs and presentation, not writeback workflows.

Contour: ad-hoc exploration and analysis paths
- Contour enables visualise/filter/transform without code, organise analyses into analytical paths, parameterise analyses, and save results as new datasets. It is explicitly recommended when some or all data is not mapped in the ontology. citeturn1search2  
- Use when you’re exploring or iterating on transformations rapidly and the ontology is not yet the “API layer” for the problem.

Slate: custom designed applications
- Slate enables drag-and-drop apps with custom design and minimal coding; it supports loading CSS libraries and custom HTML/CSS/JS patterns for advanced widgets. citeturn1search3turn1search7turn1search11  
- Use when Workshop’s widget set cannot deliver the UX you need and you are willing to own front-end design and complexity.

A blunt rule that matches how Foundry is organised in docs:
- Use Workshop when users must change the world (actions, edits). citeturn1search8turn26search16  
- Use Quiver when users must understand the world (dashboards). citeturn1search1  
- Use Contour when builders must discover the world (exploration and “save as dataset”). citeturn1search2  
- Use Slate when the UI itself is the product and custom styling/behaviour is required. citeturn1search3turn1search7  

## AIP: how Logic, Assist, agents, and OSDK connect to ontology objects

### AIP Logic: what building a Logic function actually looks like
AIP Logic is documented as a no-code environment for building, testing, and releasing LLM-powered functions, governed by platform security (user permissions and function permissions). citeturn32view3  

UI layout is explicit and screenshot-backed:
- Left: Inputs, Blocks, Outputs configuration.  
- Middle: Debugger.  
- Right: Run panel. citeturn32view0  

Builder flow in practice:
1. Access AIP Logic via workspace navigation or search shortcut; or create a new Logic from Files using +New → AIP Logic. Logic files must be saved in a project folder. citeturn32view0  
2. Define inputs, including ontology-typed inputs like object, object list, object set, plus primitives (string, boolean, timestamp, struct, media reference, etc.). citeturn32view0  
3. Compose blocks. Palantir documents common blocks: Create variable, Apply action, Execute function, Use LLM, plus loops and conditionals. citeturn32view0turn32view1  
4. Run and debug: running opens the Debugger showing the model’s intermediate reasoning traces for the blocks; the Run panel stores run history and lets you create tests. citeturn32view0turn32view2  
5. Publish: publish the Logic function; for ontology edits, you must publish and call it via an Action, and you must configure an “Apply actions” tool inside a Use LLM block. citeturn32view0turn32view2  

Testing: after publishing, you can configure Evaluations to test logic, compare models, and examine variance across runs. citeturn32view2  

### Constraining what an AI agent can do
The constraint model is a combination of:
- Platform security: AIP Logic inherits Foundry’s permissions model; LLM access is scoped to what permissions allow. citeturn32view3  
- Tooling restrictions: blocks define which tools the model can call (functions, actions, etc.). citeturn32view1turn32view0  
- Action mediation: ontology edits must go through Actions, which are permission checked and auditable. citeturn32view0turn14search10  
- In Workshop embeds like AIP Analyst widget: you can restrict ontology, object type groups, preloaded resources, and available tools directly in widget configuration. citeturn32view4  

Observability: tracing exists at the workflow level, with a “Trace view” showing a timeline of operations, including whether spans came from Functions, Actions, Automations, or LLM calls. citeturn33view4  

### AIP Assist: the in-product experience in Ontology manager and Workshop
AIP Assist is a platform support tool with an in-app sidebar. It is explicitly context-aware (aware of which Foundry app you are in) and is designed not to access your data. citeturn33view3  

Two integrations you asked about are explicitly documented:
- In Workshop: Button widgets can trigger a “Send to AIP Assist” event that opens the Assist sidebar and submits a static or variable-derived prompt; builders can set a default Assist Agent for that workflow. citeturn33view1turn33view2  
- In Ontology Manager: when updating an ontology, the Errors tab includes “Explain with AIP Assist” on an error, producing suggested fixes and explanations. citeturn33view1  

### OSDK: what it is, how it is generated, and how external apps query ontology
OSDK is the Ontology SDK: generated, strongly typed client libraries for interacting with ontology objects, links, and actions from outside Foundry (TypeScript, Python, Java; OpenAPI for others). Palantir positions Foundry as your backend, with governance controls and writeback. citeturn28view0turn30view3  

Generation and scope:
- OSDK apps are created and managed in Developer Console. citeturn28view0turn30view0  
- Creating an application is a wizard: choose client-facing application, configure OAuth redirect URLs, select “Yes, generate an Ontology SDK”, select an ontology, then choose which object types and action types to include in your SDK package. citeturn30view0  
- Tokens are scoped to the entities the app is allowed to access, plus the user’s own permissions. citeturn28view0  
- For other languages, Developer Console can export an OpenAPI spec for the application APIs. citeturn30view4  

Typical TypeScript usage splits into two layers:
- Ontology-specific clients and hooks, documented in the OSDK TypeScript site (React hooks like `useOsdkObjects`, filtering via `where`, ordering via `orderBy`, pivoting to related objects via `pivotTo`, and WebSocket real-time updates via `streamUpdates`). citeturn31view0  
- Platform API bindings via `foundry-platform-typescript`, installable as `@osdk/foundry.{namespace}`, and usable either alongside an ontology client or standalone. citeturn28view3  

Auth and client creation are also concretely documented in the public `osdk-ts` repo: create OAuth client (public or confidential), then `createClient(stackUrl, ontologyRid, auth)` to get a client instance. citeturn28view2turn28view3  

Bootstrap workflow for external frontends:
- Palantir documents `@osdk/create-app` CLI, including required parameters (application RID, foundry URL, client ID, registry URL, etc.) and Node version requirements. citeturn30view1  

If you want the “typed objects not raw data” answer in one sentence: OSDK queries return strongly typed ontology objects whose fields are generated from ontology property API names, and relationships can be traversed in the query layer (example: `pivotTo`) rather than by joining raw tables. citeturn31view0turn16view3  

## Apollo: deployment architecture, approvals, rollbacks, and air-gapped reality

### Apollo’s architecture: hub, spokes, agents, and plan orchestration
Official Apollo docs describe a hub-and-spoke model:
- An Apollo Hub manages multiple Spoke Environments; the hub stores environment settings including entities that should exist, which release channels they subscribe to, and maintenance windows. citeturn34search15turn34search7  
- Spoke Environments run a Spoke Control Plane and report status back to the Hub. citeturn34search3turn34search7  
- Apollo Agents run in the Spoke and execute Plans issued by the Hub, then report “Reported State” back. citeturn3search13  

The orchestration engine is constraint-based: it continuously evaluates possible Plans for each Spoke, checks constraints, and issues Plans whose constraints are satisfied. Plans to roll off a recalled release or execute “break-glass” commands are prioritised. citeturn34search2turn34search6  

This is the implementation backbone for “deploy to 300 environments”: it is not 300 manual pipelines; it is a single control plane issuing plans to many agents.

### How Apollo pushes updates widely and how customers control rollouts
The control mechanics are documented as “release channels” plus “promotion pipelines”:
- Release Channels can auto-add new releases, or be manually curated. citeturn34search12  
- Promotion pipelines define how releases move from one channel to another and the criteria at each stage, enabling stable rollout and environment subscription to channels. citeturn34search14turn34search10  

Customer control is therefore encoded as:
- Which channels an environment subscribes to. citeturn34search15turn34search14  
- What promotion criteria and soak or validation stages exist in the promotion pipeline. citeturn34search10turn34search18  

Change management and approval:
- Apollo has a change request system with statuses like Pending Approvals, Approved, Rejected, Cancelled. citeturn34search1  
- Unless an environment is marked DEV, Apollo requires at least one approver for changes; compliance teams and special reviewer requirements can be configured for regulated domains. citeturn34search5turn34search9  

### Air-gapped and classified networks: what is publicly stated
Apollo’s own white paper claims Apollo can remediate vulnerabilities across “on-premise data centres, edge hardware and classified networks” and describes doing so across 200+ environments and “within hours” during log4j remediation. citeturn36view2turn35view0  

It also claims fleet scale: 300+ deployment environments across on-premise, public, and private clouds. citeturn36view2turn35view0  

On disconnected operation, Apollo docs state environments can become disconnected from a Hub for periods (example: vehicles on the move) and reconnect for upgrades later. citeturn34search15  

For cross-domain delivery tooling, a partner document (Everfox) describes “Palantir Mission Manager” combining Apollo with “Palantir Binary Transfer Solution” and cross domain solutions to enable deployment across multi-sensitivity or classified environments. citeturn3search8  

Public docs do not describe “sneakernet” mechanics in detail; the credible statement is that Apollo’s architecture supports disconnected spokes and classified environments, and Palantir has adjacent transfer solutions for cross-domain delivery, but the operational specifics depend on customer security posture.

### Rollback mechanisms and release cadence
Rollback:
- Apollo documentation explicitly includes “recalling releases” and “define a roll-off strategy” as a first-class getting-started objective. citeturn34search11turn3search0  
- Orchestration prioritises Plans to roll off recalled releases. citeturn34search2  

Cadence:
- Palantir’s Apollo white paper describes development teams releasing “continuously and independently” and rolling out updates asynchronously across services. citeturn36view2turn35view0  
- Apollo docs emphasise release channel promotion and approval gates rather than a single global release cycle, implying cadence is product-specific and policy constrained rather than “weekly for everyone”. citeturn34search12turn34search10turn34search5  

---

If you want to go one level deeper on “implementation”, the next most revealing public artefacts are: the Foundry API reference namespaces exposed via `@osdk/foundry.*` (platform APIs), and the transforms and functions APIs that show exactly which primitives the UI is invoking. The docs and repos already surfaced above give you the concrete contract boundaries where UI ends and runtime orchestration begins.