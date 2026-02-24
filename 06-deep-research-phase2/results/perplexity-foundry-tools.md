# Palantir Foundry: Deep Technical Guide — UI & Implementation Level

***

## 1. ONTOLOGY MANAGER — Creating an Object Type Step-by-Step

### The UI

Ontology Manager is a dedicated application accessible from the Foundry sidebar. Its homepage displays a searchable table of all existing Object Types, grouped by configurable labels. The top-right corner contains a **New** button with dropdown options for creating Object Types, Link Types, Action Types, and more.[^1][^2]

### Step-by-step Object Type creation

The recommended path is a **guided step-by-step helper** wizard:[^1]

1. **Click** `New > Create object type` from the Ontology Manager homepage.
2. **Select backing datasource** — pick an existing Foundry dataset. The wizard auto-populates metadata and maps every column to a property. If you don't have one yet, you can continue without a dataset and Foundry generates an empty dataset at a location you choose (Object Storage V2 only).[^1]
3. **Define properties** — the wizard shows a two-pane property editor. Left pane shows datasource columns; right pane shows mapped properties. You can: hover a column and click "Add as a new property," or use "Add all unmapped columns as new properties" to bulk-map. Each property gets a display name, API name, base type, and optional description.[^1]
4. **Set primary key and title key** — the primary key must be unique per record (deterministic, not random). The title key is the human-readable display name (e.g., `full_name` for an Employee).[^1]
5. **Optionally generate standard actions** — the wizard can auto-create edit/create/delete Action Types for this object type and assign them to a user/group.[^1]
6. **Choose a project** and click **Create** (this stages the change). Then click **Save** in the upper right to commit to the ontology.[^1]

### Property base types

The full list of supported property types in the Ontology:[^3][^4]

| Category | Types |
|---|---|
| **Commonly used** | `String`, `Integer`, `Short` |
| **Time-based** | `Date`, `Timestamp` |
| **Number-like** | `Boolean`, `Byte`, `Long`, `Float`, `Double`, `Decimal` |
| **Geospatial** | `Geohash` (GeoPoint), `Geoshape`, `GeotimeSeriesReference` |
| **Complex** | `Array` (of any inner type), `Struct` (nested object with named fields), `Vector` (for ML embeddings) |
| **Special** | `Attachment`, `MediaReference`, `Timeseries`, `Marking`, `CipherText` |

`Struct` types allow nested JSON-like fields within a single property — e.g., an Address struct with `street`, `city`, `zip` fields. `Array` wraps any base type in a list. `Vector` is specifically for AI/ML embedding use cases.[^4][^5]

### Creating Link Types

Navigate to Ontology Manager and choose `New > Link type`, or go to an object type's Overview page and click "Create new link type" from the link type graph.[^6]

The guided helper walks through:

1. **Select cardinality**: One-to-one, One-to-many, Many-to-one, or Many-to-many.[^6]
2. **For 1:1 or M:1**: Define a **foreign key** property on one object type that refers to the **primary key** of the other. Example: `Flight.tailNumber` (FK) → `Aircraft.tailNumber` (PK).[^6]
3. **For Many-to-Many**: You need a **third backing dataset** (a join table). This dataset's only required columns are the primary key columns from both object types. Each row represents one link instance.[^7]
4. **Set API names** and display names for both directions of the link.

The cardinality system uses `ONE` and `MANY` values. Cardinality is a modeling hint — one-to-one is not enforced at the data layer.[^8][^6]

### Interfaces (Abstract Types)

An **interface** describes the shape of an object type and its capabilities, providing polymorphism across object types that share a common structure.[^9][^10]

An interface defines:
- **Interface properties** — abstract property constraints that implementing object types must map to concrete properties.
- **Interface link type constraints** — abstract links with a cardinality (`ONE` or `MANY`), description, API name, and a linked entity that can be another interface or a concrete object type.[^11][^9]
- **Required flag** — whether each implementing object type must provide at least one implementation of a given link.[^11]

Example: A `Facility` interface declares an optional one-to-many link to `Airline`. Both `Airport` and `Seaport` object types can implement `Facility`, each providing their own concrete link to `Airline` that satisfies the interface constraint.[^9]

### Functions (TypeScript Computed Properties)

Functions are authored in TypeScript in Code Repositories and operate on Ontology objects in real time:[^12][^13]

- **Read functions**: Query object sets, traverse links, compute derived values. Import objects from `@foundry/ontology-api`, use `Objects.search().Employee().filter(...)` patterns.[^14][^12]
- **Edit functions**: Annotated with `@OntologyEditFunction()` and `@Edits(ObjectType)`. Can create objects (`Objects.create().ticket(primaryKey)`), update properties (`employee.lastName = newName`), set/remove links, and delete objects.[^15][^12]
- **TypeScript v2 API**: Uses `@osdk/functions` with `createEditBatch`, typed `Edits.Object<T>` and `Edits.Link<T>` unions for batch edits.[^16]
- **Timestamp handling**: Use `Timestamp.fromISOString(...)` from the Foundry functions API.[^17]

Functions power Action Types (for writeback), Workshop computed values, and AIP Logic integrations.

***

## 2. Decision Framework — Object vs Property vs Link vs Struct

### When does an entity deserve its own Object Type?

The Ontology's core analogy: Object Type = Dataset, Object = Row, Property = Column, Link = Join. The decision framework:[^18]

- **Own Object Type** when: the entity has its own lifecycle, its own properties that get independently queried/filtered, it's shared across multiple relationships, or users need to take actions on it independently. Example: `Customer`, `Order`, `Product`.[^18]
- **Property** when: the value is a simple attribute that only makes sense in the context of its parent object and won't be independently queried. Example: `Customer.email`, `Order.status`.[^18]
- **Struct** when: you have a logically grouped set of fields that belong to the parent object but you want nested structure. Example: an `Address` struct with `{street, city, zip, country}` on a `Customer` — if addresses don't need independent lifecycle, links, or actions.[^5]
- **Linked Object Type** when: addresses are shared across entities (billing vs shipping on Orders, employee home address), need independent versioning, or have their own properties that evolve. In this case, make `Address` its own Object Type linked to `Customer` with a many-to-one or many-to-many link.[^7]

### Practical guideline

Ask: "Will someone ever search for, filter on, or take an action on this entity independently?" If yes → Object Type. If no → Property or Struct.

***

## 3. Schema Evolution

### Non-breaking changes (no migration needed)

Adding a new property, changing display names, changing descriptions, or reordering properties are non-breaking — just edit in Ontology Manager and save.[^19][^20]

### Breaking schema changes

These require migrations in Object Storage V2:[^19]
- Changing the data type of an existing property
- Changing the backing datasource
- Changing the primary key
- Deleting a property that has user edits
- Modifying struct field types

### Migration framework (OSv2)

When you make a breaking change, Ontology Manager automatically detects it and blocks saving until you select a migration from the **Migrations** tab:[^19]

| Migration | Use case |
|---|---|
| **Drop all property edits** | Deleting a property with no replacement |
| **Drop all edits** | Full reset to datasource state |
| **Move edits** | Renaming a property or moving to a new backing dataset |
| **Cast property to new type** | Changing `String` → `Integer`, etc. (supported type casts) |
| **Move struct field edits** | Restructuring within a struct |
| **Revert migration** | Undo a previously applied migration |

Once saved, a **replacement Funnel batch pipeline** is automatically orchestrated. The new object type version becomes queryable after the pipeline completes and the new index is fully hydrated.[^19]

Limit: max 500 schema migrations at once; primary key property migrations are not supported by the framework.[^19]

***

## 4. Pipeline Builder (Visual)

### The UI

Pipeline Builder is a **drag-and-drop canvas** where each node represents a transformation. The screen has three main areas:[^21][^22]
- **Left panel**: List of input datasets and output datasets
- **Center canvas**: The node graph — nodes connected by edges showing data flow
- **Bottom panel**: Data preview at any selected node

### Creating a pipeline

1. Open Pipeline Builder and create a new pipeline
2. Add input datasets as source nodes
3. Chain transformation nodes
4. Configure an output dataset node
5. Save, then Build (or Deploy for production schedules)[^21]

### Available transform nodes

Pipeline Builder offers a rich set of visual transforms:[^22][^23][^21]

- **Cleaning**: Clean String, Trim Whitespace, Cast to Timestamp, Normalize Column Names
- **Filtering**: Row filters with conditional logic (IF, CASE, regex)
- **Joining**: Inner, Outer, Left, Right joins with auto-preview of results
- **Aggregating**: Group-by with sum, count, avg, min, max
- **Restructuring**: Pivot, Unpivot, Union, Split
- **Calculated columns**: Expression builder for derived fields
- **Reusables**: Parameters (variables) and reusable functions[^21]

### AI features

Pipeline Builder includes AI-powered capabilities: auto-naming nodes based on their logic, auto-generating regex expressions from natural language descriptions.[^21]

### Version control

Pipeline Builder has built-in **branching** (like git). You work on a branch, see a diff of changes vs. main in the **Changes** tab, and merge when ready.[^21]

### Mixing visual and code

Pipeline Builder doesn't directly embed PySpark code inside visual nodes. However, the pattern is to **prototype in Pipeline Builder** and shift complex parts into **Code Workbook** or **Code Repositories** for Python/SQL/PySpark logic. The output datasets are the same either way — they feed into the same lineage and Ontology.[^22]

***

## 5. Code-Based Pipelines (Code Repositories)

### The `@transform` decorator family

Code Repositories use a Python API built around decorators:[^24]

**`@transform` decorator** — the most general form. Injects `TransformInput` and `TransformOutput` objects:

```python
from transforms.api import transform, Input, Output

@transform(
    source_a=Input("/datasets/source_a"),
    source_b=Input("/datasets/source_b"),
    output=Output("/datasets/joined_output")
)
def my_transform(source_a, source_b, output):
    df_a = source_a.dataframe()
    df_b = source_b.dataframe()
    joined = df_a.join(df_b, on="customer_id", how="left")
    cleaned = joined.filter(joined.status != "CANCELLED")
    output.write_dataframe(cleaned)
```

**`@transform_df` decorator** — convenience wrapper that injects/returns DataFrames directly:[^24]

```python
from transforms.api import transform_df, Input, Output

@transform_df(
    Output("/datasets/processed"),
    source=Input("/datasets/raw")
)
def my_transform(source):
    return source.filter(source.active == True)
```

**`@transform_pandas` decorator** — same but for Pandas DataFrames.[^24]

### Pipeline and registration

Transforms are registered to a `Pipeline` object, exported via `setup.py` entry points. Automatic registration discovers all `@transform`-decorated functions in the module:[^24]

```python
from transforms.api import Pipeline
my_pipeline = Pipeline()
```

### Scheduling

Foundry supports three scheduling modes:[^25][^26][^27]

- **Time-based (Cron)**: Standard cron expressions, e.g., `"0 2 * * *"` for daily at 2 AM
- **Event-based (on data arrival)**: Trigger when specific upstream datasets update — configured by adding "trigger datasets" to the schedule
- **Hybrid**: Event-based with a fallback timer

Schedules are created from Data Lineage or the Build Schedules UI. You select target datasets, define triggers, and Foundry's dependency resolver automatically builds upstream datasets in correct order. Independent transforms run in parallel when "Allow parallel builds" is enabled. Retry logic (count + interval) and alerting can also be configured.[^26]

### Incremental processing

Foundry supports incremental transforms via the `@incremental` decorator:[^28][^29][^30]

- **Incremental mode**: Only new rows (new transactions) are processed. Each run appends to the output — it cannot replace or remove rows.[^29]
- **Snapshot mode**: Full recomputation of the entire dataset.
- **`semantic_version`**: Bumping this number forces a full snapshot recompute, useful after code logic changes.[^31]
- **Cascading snapshots**: If any input is snapshotted, the incremental transform automatically snapshots itself.[^29]
- The `@configure` decorator controls resource profiles (executor count, memory) and can differ between snapshot and incremental runs.[^32][^28]

### Testing

Palantir provides a unit testing framework for PySpark transforms. You can write tests that create mock DataFrames, run your transform logic, and assert results. The official PySpark Style Guide and unit testing documentation cover best practices.[^33]

***

## 6. Data Lineage

### How lineage is tracked

Every transform in Foundry records its `Input → Output` relationships. Since datasets are created uniquely through transforms, Foundry maintains a complete provenance graph automatically.[^34][^35]

### The lineage visualization

Data Lineage is an interactive graph application:[^36][^37]

- **Search** for any dataset, object type, or resource and add it as a node
- Click **left/right arrows** on nodes to expand parents (ancestors) or children (descendants)
- Use the **Expand** tool with level controls — expand one level, multiple levels, or all the way to raw sources[^37]
- **Color-coding**: Nodes can be colored by transform type, health status, custom groupings, or manually assigned colors[^36]
- **Layout tools**: Automatic layout, hierarchical, vertical, by-level, or by-color-group arrangements[^36]
- **Find** tool searches for nodes or column names within datasets on the graph
- Selecting a node shows a **properties panel** with dataset details, links to open in other apps, and a data preview[^36]

### Tracing values and triggering builds

You can trace a dataset back to its raw source by recursively expanding ancestors. The "Find relation between two nodes" feature shows all intermediate nodes. You can also trigger builds and define schedules directly from the lineage graph — including scheduling all upstream or downstream datasets.[^38][^34][^37]

### Lineage and security

Since lineage is integrated with Foundry's permission model, you only see nodes you have access to. Markings on datasets propagate through transforms, and the lineage graph reflects which data flows through security boundaries.[^35]

***

## 7. Workshop (Application Builder)

### The UI

Workshop is a **canvas-based application builder**. You work in a module layout with sections that contain widgets. The right panel shows configuration options for the selected widget. The top toolbar has controls for adding widgets, managing variables, and previewing.[^39][^40]

### Widget categories

Workshop provides a comprehensive widget library organized into categories:[^41][^39]

| Category | Widgets |
|---|---|
| **Core display** | Object Table, Object List, Object View, Property List, Links, Object Set Title |
| **Visualization** | Chart XY (bar/line/scatter), Pie Chart, Waterfall Chart, Vega Chart, Map, Gantt Chart, Pivot Table, Timeline, Metric Card, Stepper, Status Tracker, Markdown |
| **Media** | Media Preview, PDF Viewer, Video Display, Audio + Transcription Display, Image Annotation, Spreadsheet Display |
| **Filtering** | Filter List, Object Dropdown, String Selector, Date and Time Picker, Text Input, Numeric Input, Exploration Filter Pills, Exploration Search Bar, Prominent Term, User Select |
| **Event/Navigation** | Button Group, Media Uploader, Comments, Tabs, Inline Action, Audio Recorder |
| **AIP** | AIP Analyst, AIP Agent, AIP Generated Content |
| **Meta** | Free-form Analysis, Data Freshness, Edit History, Action Log Timeline, Linked Compass Resources |

### Binding a Table widget to an Object Type

1. Add an **Object Table** widget to a section
2. In the right-side properties panel, select **New object set variable** or pick an existing one
3. Choose the Object Type
4. Select which Properties to show as columns
5. Configure sorting, filtering, and column formatting[^40]

### Adding an Action button

1. Add a **Button Group** widget
2. In the **Buttons** section of the config panel, add a new button
3. Under **On click**, select the Action Type (e.g., "Modify Destination")
4. Map Action parameters to variables (e.g., the selected object, property values from inputs)
5. Actions can create, edit, delete, or link objects — all defined as Action Types in Ontology Manager[^42][^43]

### Filtering and cross-widget linking

Add a **Filter List** widget and connect it to the same Object Set variable as your Table. The Filter List automatically generates property-based filters. Date ranges, string selectors, and geo filters all come from dedicated filter widgets.[^44][^40]

**Cross-widget linking**: Workshop uses **variables and events**. When a user clicks a row in Table A, that sets a "selected object" variable. Table B can be configured to filter on objects linked to that selected object. This is done through variable bindings — no code required.[^39][^40]

***

## 8. Workshop vs Quiver vs Contour vs Slate

| Dimension | Workshop | Quiver | Contour | Slate |
|---|---|---|---|---|
| **Primary data source** | Ontology objects | Ontology objects + time series | Raw datasets (tabular) | Arbitrary APIs + datasets |
| **Primary use** | Operational applications with writeback | Analytical dashboards and KPIs | Ad-hoc data exploration | Fully custom HTML/CSS/JS apps |
| **Builder experience** | Point-and-click widgets, no code | Point-and-click charts and analysis | Point-and-click analysis on datasets | WYSIWYG HTML designer with code |
| **Writeback** | ✅ Full (Actions, create/edit/delete objects) | ❌ Read-only analysis | ❌ Read-only analysis (can save as new dataset) | ✅ Via custom API calls |
| **Complexity** | Low-moderate | Low | Low-moderate | High |
| **Maintenance** | Low | Low | Low | High (older tool, more fragile) |

**Decision rule of thumb**:[^45][^46][^2][^47]

- **Objects or time series analysis** → Quiver
- **Raw dataset analysis** → Contour
- **Operational app with forms, workflows, actions** → Workshop
- **Heavy customization, arbitrary external APIs, legacy needs** → Slate

Workshop is the newer, recommended tool for most operational applications. Slate predates Foundry and is more powerful in arbitrary customization but much harder to maintain. Quiver templates can be **embedded inside Workshop** applications for analytical content within operational workflows. Contour and Quiver both support dashboarding, but Workshop provides full layout flexibility, multi-step workflows, and writeback that dashboards can't.[^48][^47]

***

## 9. AIP Logic

### What it is

AIP Logic is a **no-code development environment** for building functions powered by LLMs. It takes inputs (Ontology objects or text strings), processes them through LLM blocks and data tools, and returns outputs (objects/strings) or makes Ontology edits.[^49][^50]

### Creating an AIP Logic function

The interface uses a **block editor**:[^51][^50]

1. **Define inputs** — string prompts, Ontology objects, or other typed values
2. **Add LLM blocks** — each block has a prompt template, explicit access to specific Object Types and properties, and an expected output format
3. **Add data tool blocks** — calculators, object lookups, link traversals, semantic search
4. **Chain blocks** — output of one feeds into the next
5. **Test** — run with sample inputs directly in the editor
6. **Deploy** — publish as a Function usable in Actions, Workshop, or external APIs

### How AIP accesses the Ontology

AIP Logic functions receive **typed Ontology objects**, not raw data. You explicitly grant each LLM block access to specific object types and properties:[^51]

> "I explicitly gave it access to this object... you can pick a lot of different objects here or narrow it down. This is an explicit access from an LLM to certain ontology... I can give it access to certain properties — not just from a security standpoint but also from an LLM [hallucination reduction] standpoint. If you give it access to everything you're going to have more hallucinations."[^51]

The LLM navigates relationships via the Ontology's link types — it knows how to traverse from one object to related objects.[^51]

### Guardrails and governance

- **Data access restrictions**: Each function explicitly declares which Object Types and properties the LLM can see[^51]
- **Action permissions**: What the AI can DO is controlled by Action Type permissions — the same governance that applies to human users
- **Audit trail**: Every action is logged for a complete audit trail[^52]
- **Regulatory bake-in**: Guardrails can encode laws and regulations — restricting access based on data sensitivity (e.g., blocking access to protected employee data)[^52]
- **Approval workflows**: For high-stakes actions, human approval can be required before execution

AIP Logic inherits Foundry's existing security model — user and function permissions govern what any LLM-backed function can access or modify.[^49]

***

## 10. OSDK (Ontology SDK)

### What it is

The Ontology SDK allows external applications to query and modify the Ontology from standard development environments. It supports **TypeScript (NPM), Python (Pip/Conda), Java (Maven), and OpenAPI** for any other language.[^53]

### Auto-generation

OSDK code is **auto-generated from your Ontology schema** using Developer Console. The generated code includes typed classes for each Object Type, property accessors, link traversals, and Action invocations. Property names and descriptions from Ontology Manager appear as JSDoc/docstrings in your IDE.[^53]

### TypeScript query examples

**Basic query with filter and pagination**:[^54]

```typescript
const result = await ObjType
  .where(query => query.tableName.eq("some_value"))
  .fetchPage();
```

**OR filtering**:[^54]

```typescript
import OSDK from "@slate-internal/sdk";

const result = await ObjType
  .where(query => {
    const conditions = names.map(n => query.name.eq(n));
    return OSDK.Op.or(...conditions);
  })
  .fetchPage();
```

**React hook usage** (with `@osdk/react`):[^55]

```typescript
import { Todo } from "@my/osdk";
import { useOsdkObjects } from "@osdk/react/experimental";

function TodoList() {
  const { data, isLoading, error } = useOsdkObjects(Todo, {
    orderBy: { createdAt: "desc" },
  });

  if (!data && isLoading) return <div>Loading...</div>;
  return (
    <div>
      {data?.map(todo => (
        <div key={todo.$primaryKey}>{todo.title}</div>
      ))}
    </div>
  );
}
```

### Java OSDK

The Java OSDK provides a fluent API:[^56]

```java
List<Restaurant> result = client.ontology()
    .objects()
    .Restaurant()
    .where(RestaurantFilter.restaurantName().isNull(false))
    .fetchStream()
    .toList();
```

### How external apps consume OSDK

1. Create an OSDK application in **Developer Console**
2. Generate the SDK package (auto-generated from your Ontology)
3. Install via npm/pip/maven in your frontend or backend project
4. Initialize the client with authentication
5. Query objects, apply actions, subscribe to changes

The OSDK treats Foundry as a backend — leveraging the Ontology's high-scale queries and governance controls.[^53]

***

## 11. Apollo (Deployment Platform)

### Architecture

Apollo uses a **hub-and-spoke architecture** with four key components:[^57]

1. **Apollo Hub** (central) — the SaaS control plane that maintains the status and requirements of every deployment environment. Contains the Orchestration Engine and Catalog.
2. **Remote Apollo Hubs** — deployed inside air-gapped or isolated networks. Kept in sync with the Main Hub via Apollo bundles.
3. **Apollo Deployment Platform** — runs alongside managed software in each environment, sits on top of Kubernetes. Reports current state to the Hub and executes work plans.
4. **Apollo SDK** — a framework for developers to publish release metadata. No code changes required in the application itself.
5. **Apollo Catalog** — metadata layer bridging artifact stores and managed environments. Source of truth for all available software versions.

### How it pushes updates to 300+ environments

The **Orchestration Engine** in the Hub continuously compares target state vs. observed state across all environments. When they disagree, it computes an **Apollo Plan** specifying what to upgrade, where, and how. Once product constraints (dependencies) and environment constraints (maintenance windows) are met, plans execute autonomously.[^57]

### Update control mechanisms

| Feature | Description |
|---|---|
| **Release Channels** | Environments subscribe to channels (e.g., `develop`, `stable`). Features roll from develop → stable automatically after adjudication[^57] |
| **Canary Analysis** | New features ship to canary environments first from the develop branch[^57] |
| **Adjudication** | Apollo monitors performance metrics and error states after each rollout, automatically promoting or recalling releases[^57] |
| **Blue/Green Deployment** | Zero-downtime: deploys a second instance, slowly shifts traffic. Provides early quality signal[^57] |
| **Maintenance & Suppression Windows** | Product-level or environment-level windows that block upgrades during sensitive periods. Auto-created when failure thresholds are met[^57] |

### Air-gapped / classified networks

Apollo handles air-gapped deployments through two mechanisms:[^58][^57]

1. **Apollo Bundles (sneakernet)**: Generated on the SaaS Hub, containing only net-new software versions, configurations, and metadata (intelligently compressed diffs). Burned to physical media, walked to the classified network, and loaded into the Remote Hub. AV metadata is included; payloads are scanned and integrity-verified at multiple checkpoints.

2. **Binary Transfer Service (BTS)**: Automates the bundle transfer process through accredited **Cross Domain Solutions (CDS)**. BTS polls the Apollo Catalog for new releases, verifies security scan results and cryptographic checksums, and transfers artifacts to the remote hub automatically.[^58]

The Remote Hub then operates autonomously, using its local copy of the catalog to orchestrate upgrades across environments within the classified network.

### Release cadence and rollback

- **Patch speed**: 3.5 minutes average to patch a service, under 5 minutes to remediate production issues[^59]
- **Continuous delivery**: 250+ engineering teams deploy continuously; features flow through release channels based on adjudication[^57]
- **Rollback (Recalling)**: Multiple strategies available:[^57]
  - **Stay on current version** — pause new installations while investigating
  - **Stay on current with exceptions** — specific environments get the fix
  - **Any version newer than recalled** — wait for a fix
  - **Roll back to specific known-good version** — force downgrade fleet-wide
- Recalls can be triggered by administrators, developers, or **automatically by Apollo** when health monitoring detects unhealthy releases[^57]

### Security achievements

Apollo is key to Palantir achieving FedRAMP, DoD IL5, IL6, and ICD 503 accreditations. It encodes InfoSec vulnerability SLAs, integrates with container image scanners to auto-recall products with known CVEs, and generates comprehensive SBOMs (Software Bills of Materials) from its Catalog.[^59][^57]

---

## References

1. [Create an object type - Palantir](https://palantir.com/docs/foundry/object-link-types/create-object-type/) - To create a new object type, select the Create your first object type option from the Ontology Manag...

2. [Application reference - Palantir](https://palantir.com/docs/foundry/getting-started/application-reference/) - This page provides a reference for the range of applications available and describes when you may wa...

3. [Palantir](https://www.palantir.com/docs/foundry/object-link-types/properties-overview/) - A property of an object type is the schema definition of a characteristic of a real-world entity or ...

4. [foundry-platform-python/docs/v2/Ontologies/models/ObjectPropertyType.md at develop · palantir/foundry-platform-python](https://github.com/palantir/foundry-platform-python/blob/develop/docs/v2/Ontologies/models/ObjectPropertyType.md) - The official Python SDK for the Foundry API. Contribute to palantir/foundry-platform-python developm...

5. [foundry-platform-python/docs/v2/Ontologies/models/ValueType.md at develop · palantir/foundry-platform-python](https://github.com/palantir/foundry-platform-python/blob/develop/docs/v2/Ontologies/models/ValueType.md) - The official Python SDK for the Foundry API. Contribute to palantir/foundry-platform-python developm...

6. [Create a link type - Palantir](https://www.palantir.com/docs/foundry/object-link-types/create-link-type) - We recommend creating and configuring a new link type with the guided helper outlined below. However...

7. [Palantir Foundry Many to Many link (backing dataset)](https://stackoverflow.com/questions/77099745/palantir-foundry-many-to-many-link-backing-dataset) - I am in search of documentation or advice on how to link two objects together for a many to many rel...

8. [foundry-platform-python/docs/v2/Ontologies/models/InterfaceLinkTypeCardinality.md at develop · palantir/foundry-platform-python](https://github.com/palantir/foundry-platform-python/blob/develop/docs/v2/Ontologies/models/InterfaceLinkTypeCardinality.md) - The official Python library for the Foundry API. Contribute to palantir/foundry-platform-python deve...

9. [Palantir](https://www.palantir.com/docs/foundry/interfaces/interface-link-types-overview) - An interface link type constraint defines an object-to-object relationship common across all object ...

10. [Palantir](https://www.palantir.com/docs/foundry/ontology) - The Palantir Ontology is an operational layer for the organization. The Ontology sits on top of the ...

11. [foundry-platform-python/docs/v2/Ontologies/models/InterfaceLinkType.md at develop · palantir/foundry-platform-python](https://github.com/palantir/foundry-platform-python/blob/develop/docs/v2/Ontologies/models/InterfaceLinkType.md) - The official Python SDK for the Foundry API. Contribute to palantir/foundry-platform-python developm...

12. [TypeScript v1 • Ontology edits - Functions - Palantir](https://www.palantir.com/docs/foundry/functions/api-ontology-edits) - In addition to writing functions that return derived values based on the Ontology, you can also writ...

13. [Functions | Getting Started](https://www.youtube.com/watch?v=RZ1GF6m5Bpw) - Have you ever wondered how to perform complex interactions with your Ontology in real-time? Function...

14. [Querying Object Service Programmatically](https://community.palantir.com/t/querying-object-service-programmatically/522) - I’m currently writing a typescript function to execute a particular ontology search based on the inp...

15. [TypeScript v2 • Ontology edits - Functions - Palantir](https://www.palantir.com/docs/foundry/functions/typescript-v2-ontology-edits) - In addition to writing functions that read data from the Ontology, you can also write functions that...

16. [TypeScript v2 • Ontology edits - Functions - Palantir](https://palantir.com/docs/foundry/functions/typescript-v2-ontology-edits/) - To perform Ontology edits in a TypeScript v2 function, first construct an Ontology edits batch using...

17. [How to Set an Object's Timestamp Property in Foundry Using Functions](https://www.youtube.com/watch?v=WRwQT66GKqI) - Learn how to properly set a timestamp property for an object in Palantir Foundry using functions, an...

18. [Core concepts](https://www.palantir.com/docs/foundry/ontology/core-concepts) - This page describes major concepts related to the Ontology in Foundry. An Ontology is a categorizati...

19. [Object edits and materializations • Manage schema changes](https://www.palantir.com/docs/foundry/object-edits/schema-migrations) - Workflows and applications built on the Foundry Ontology should evolve as an organization's needs ch...

20. [Palantir](https://www.palantir.com/docs/foundry/object-link-types/edit-object-type/) - Editing an object type and its properties can have application-breaking consequences that can disrup...

21. [Intro to Foundry Pipeline Builder](https://www.youtube.com/watch?v=WIQA7u1tbsY) - Pipeline Builder is the most accessible way to build production-grade data pipelines in Palantir Fou...

22. [Day 3 of 15 — Pipeline Builder: Why visual workflows in Foundry are smarter than you think. | srimai v](https://www.linkedin.com/posts/srimai-v-0708a71a5_palantirfoundry-pipelinebuilder-visualetl-activity-7354158327288799233-J8uo) - Day 3 of 15 — Pipeline Builder: Why visual workflows in Foundry are smarter than you think. When peo...

23. [Palantir Foundry Pipeline Builder: Transformations | Date Operations and Split](https://www.youtube.com/watch?v=YpOAxzfa2JA) - In this video, Chandradeep explains how to use transformations in Palantir Foundry Pipeline Builder,...

24. [Palantir](https://www.palantir.com/docs/foundry/transforms-python/transforms-pipelines) - In Python, transforms.api.Transform is a description of how to compute a dataset. It describes the f...

25. [Palantir](https://www.palantir.com/docs/foundry/building-pipelines/scheduling-overview) - In Foundry's data integration layer, a schedule is a key concept enabling data to stay up to date fo...

26. [Mastering Build Schedules in Palantir Foundry for Data ...](https://www.linkedin.com/posts/deepak-suryawanshi-a79665126_foundryawarenessseries-activity-7386704299709509634-yKxO) - 🧠 #FoundryAwarenessSeries | Day 15: Mastering Build Schedules in Palantir Foundry ⚙️ Yesterday we ex...

27. [Schedules | Management, Metrics, and Triggers in Foundry](https://www.youtube.com/watch?v=h_vHxnD0OZQ) - With Schedules set up in Palantir Foundry, they will need to be monitored and configured to adapt da...

28. [Optimizing Resource Allocation for Incremental Pipelines in Palantir Foundry](https://www.youtube.com/watch?v=qSe8OEJGXLo) - Discover how to manage `resource allocation` for incremental pipelines in Palantir Foundry, using co...

29. [Incremental pipelines • Maintaining high performance - Palantir](https://www.palantir.com/docs/foundry/building-pipelines/maintaining-incremental-performance) - Incremental transforms can help minimize resource use by ensuring that only new rows are processed w...

30. [Palantir Foundry incremental testing is hard to iterate on, how do I find bugs faster?](https://stackoverflow.com/questions/69531556/palantir-foundry-incremental-testing-is-hard-to-iterate-on-how-do-i-find-bugs-f) - I have a pipeline setup in my Foundry instance that is using incremental computation but for some re...

31. [Code Repositories | How to Write Incremental Data Transforms in Palantir Foundry](https://www.youtube.com/watch?v=R8LVvy4v7Es) - For more information on how to write incremental data transforms in Palantir Foundry, take a look at...

32. [Resource Allocation for Incremental Pipelines](https://stackoverflow.com/questions/71313127/resource-allocation-for-incremental-pipelines) - There are times when an incremental pipeline in Palantir Foundry has to be built as a snapshot. If t...

33. [Code Repositories | Development Process and Pipeline Craftsmanship in Palantir Foundry](https://www.youtube.com/watch?v=PsRqQ7MQC1A) - In this video, we look at some best practices to follow in the process of developing pipelines in Pa...

34. [Palantir Foundry 101](https://unit8.com/resources/palantir-foundry-101-2/) - Data lineage is about presenting in a clear and intuitive way the graph of datasets and transforms t...

35. [Data Lineage • Overview](https://palantir.com/docs/foundry/data-lineage/overview/) - Data Lineage is an interactive tool that facilitates a holistic view of how data flows through the F...

36. [Data Lineage • Navigation](https://palantir.com/docs/foundry/data-lineage/navigation/) - To make the best use of the Data Lineage application, you will need to know how to navigate the grap...

37. [Graphs • Explore data lineage](https://palantir.com/docs/foundry/data-lineage/explore-lineage/) - Data lineage helps you understand how your data came to be. There are various ways to explore data p...

38. [Palantir](https://www.palantir.com/docs/foundry/learning-data-dataeng-01/03/) - This content is also available at learn.palantir.com ↗ and is presented here for accessibility purpo...

39. [Workshop • Core concepts • Widgets](https://palantir.com/docs/foundry/workshop/concepts-widgets/) - Widgets display content to Workshop users and are the core building blocks of a module's user interf...

40. [Palantir Foundry | Speedrun Your First E2E Workflow – Workshop App + Ontology Actions (Part 2/2)](https://www.youtube.com/watch?v=ISVRT3fj57s) - Welcome back to Foundry Fastlane — where we build Palantir solutions at full speed.

In Part 2 of th...

41. [Workshop • Visualization widgets • Overview](https://www.palantir.com/docs/foundry/workshop/widgets-visualization) - Chart: Pie: Visualize object data as a pie or donut chart. Chart: XY: Visualize an object set as a c...

42. [Button Group - Event-trigger & navigational widgets](https://palantir.com/docs/foundry/workshop/widgets-button-group/) - The Button Group widget allows application builders to add buttons to a Workshop module that can tri...

43. [Use Actions in Workshop](https://palantir.com/docs/foundry/workshop/actions-use/) - Use Actions in Workshop. Actions in Foundry allow users to edit, create, delete, and link object dat...

44. [Palantir Workshop - Filter settings](https://stackoverflow.com/questions/70607764/palantir-workshop-filter-settings) - I'm trying to implement a new feature in my workshop application and I get trouble with filters. I w...

45. [Palantir Foundry: Contour 101](https://www.youtube.com/watch?v=3yzenPa5jOQ) - How do you use Contour? Contour is one of Palantir Foundry's point-and-click analytical applications...

46. [Types of analysis - Palantir](https://palantir.com/docs/foundry/analytics/types-of-analysis/) - Foundry provides two primary tools for point-and-click analysis: Contour and Quiver. Each tool is de...

47. [How is Workshop different from Slate in Foundry?](https://stackoverflow.com/questions/64358691/how-is-workshop-different-from-slate-in-foundry/64361549) - I see that there are Slate and Workshop in the Foundry platform. May I know real business cases wher...

48. [Palantir](https://www.palantir.com/docs/foundry/analytics/dashboards/) - There are two primary ways to build interactive dashboards from Foundry analyses: Contour dashboards...

49. [AIP Logic • Overview - Palantir](https://www.palantir.com/docs/foundry/logic/overview) - AIP Logic is a no-code development environment for building, testing, and releasing functions powere...

50. [Technical Analysis and Application Guide for the Palantir AIP Logic ...](https://www.oreateai.com/blog/technical-analysis-and-application-guide-for-the-palantir-aip-logic-platform/e455dfd4846e0096ff6690262277d820) - This guide provides insights into the architecture and functionality of Palantir's no-code AI develo...

51. [Building with Palantir AIP: Data Tools for RAG/OAG](https://www.youtube.com/watch?v=CiyLviRs4Ng) - Retrieval Augmented Generation (RAG) enables generative AI to retrieve data from outside sources. Pa...

52. [🎥 Palantir AIP: Governing AI for Operational Decisions | Secure, Scalable, and Smart Automation 🤖](https://www.youtube.com/watch?v=LP5u7p5yEEQ) - 🎥 Palantir AIP: Governing AI for Operational Decisions | Secure, Scalable, and Smart Automation 🤖
🌍 ...

53. [Ontology SDK • Overview - Palantir](https://palantir.com/docs/foundry/ontology-sdk/overview/) - The Ontology Software Development Kit (OSDK) allows you to access the full power of the Ontology dir...

54. [I want to create a OSDK-query from slate with a filter to a set of values](https://community.palantir.com/t/i-want-to-create-a-osdk-query-from-slate-with-a-filter-to-a-set-of-values/3002) - I’m failing to write a query in Slate that filters the result to a set of names. (OSDK) The task see...

55. [Getting Started | OSDK TypeScript - Palantir Open Source](https://palantir.github.io/osdk-ts/react/getting-started/) - This guide covers installation, setup, and your first OSDK React application.

56. [Ontology SDK • Java OSDK - Palantir](https://palantir.com/docs/foundry/ontology-sdk/java-osdk/) - This page provides generic documentation for the Java OSDK based on an example Restaurant object and...

57. [[PDF] Palantir Apollo —Solution Overview - Carahsoft](https://static.carahsoft.com/concrete/files/6616/8615/9340/Whitepaper_-_Palantir_Apollo_-_Solution_Overview.pdf)

58. [Deploying Across Security Domains](https://blog.palantir.com/deploying-across-security-domains-449c786d92c0?gi=f46f98571579) - Palantir Binary Transfer Service & Apollo

59. [How Palantir Meets IL6 Security Requirements with Apollo](https://www.carahsoft.com/blog/palantir-meeting-il6-security-requirements-with-apollo-blog-2023) - The bar to operate with IL6 information is rightfully a high one. We know obtaining IL6 authorizatio...

