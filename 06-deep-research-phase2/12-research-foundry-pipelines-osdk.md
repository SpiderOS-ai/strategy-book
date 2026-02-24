# Palantir Foundry: Data Pipeline Tools and OSDK -- Deep Technical Report

## 1. Pipeline Builder -- The Visual UI for Building Data Pipelines

Pipeline Builder is Foundry's primary no-code/low-code application for building data integration pipelines. It provides a **graph-based, point-and-click interface** where users construct pipelines by connecting visual nodes on a canvas, without needing to write PySpark or SQL code.

### Interface and Layout

The Pipeline Builder interface is organized around a **board** (canvas/graph workspace) where users place and connect nodes. Each node represents an operation -- an input source, a transform, or an output destination. Users **drag white output circles on nodes** to draw connections between them, forming a directed acyclic graph (DAG) of data transformations. The canvas supports:

- **Folders** for organizing groups of nodes hierarchically
- **Color Groups** for visually categorizing related pipeline sections
- **Text Nodes** for inline documentation and comments
- **Checkpoints** for marking intermediate data snapshots that can be inspected
- **Job Groups** for bundling related transforms that execute together

The interface includes a **preview panel** that can run pipeline logic from raw datasets up to any selected node, so users validate transformations before committing to a full build.

### Node Types

**Input Nodes:**
- Foundry datasets (batch or streaming)
- Generated/synthetic data
- Dataset syncs from external connectors

**Transform Nodes (70+ available):**
- **Data Manipulation:** Filter, Sort, Select columns, Drop columns, Rename columns, Normalize column names, Top rows, Drop duplicates
- **Joins:** Inner join, Left join, Right join, Outer join, Cross join, Anti join, Semi join, Mapping join, KNN join
- **Aggregation & Windowing:** Aggregate (grouped), Aggregate over window (time-based or partitioned), Project over window, Window functions
- **Reshape:** Pivot, Unpivot, Explode array, Array elements to columns, Flatten struct
- **Combine:** Union by name, Narrow union, Wide union
- **Geospatial:** Geo distance join, Geometry intersection join, Geometry KNN join
- **File Parsing:** Extract rows from CSV, JSON, Excel, XML; Parse shapefile
- **Advanced:** Split on condition, Pattern mining, Time-bounded drop duplicates

**Output Nodes:**
- Foundry dataset outputs
- Media set outputs
- Virtual table outputs
- Ontology entity outputs (writing directly to the Ontology)
- Geotemporal series sync outputs

### Expression System

Pipeline Builder's **expression system provides over 500 built-in functions** that can be embedded within transforms. Categories include:

- **Arithmetic:** Add, Multiply, Divide, Modulo, Absolute value, Rounding, Trigonometric functions
- **String:** Concatenation, Uppercase/Lowercase, Substring, Regex matching, String length
- **Array:** Array concat, Array distinct, Array sort, Array filter, Array union/intersection
- **Date/Time:** Current timestamp, Date sequence, Epoch seconds to timestamp, Part extraction, Date arithmetic
- **Geospatial:** Create GeoPoint, Geometry buffer, Haversine distance, Coordinate conversion
- **Type Casting:** All standard type conversions
- **Advanced:** Parse JSON string, Cipher encrypt, Text to embeddings (LLM-powered), Case/When conditional logic, Coalesce (first non-null)

Users configure custom expressions through a form-based editor where they can nest expressions within transforms (e.g., inserting a Length expression inside a Filter transform). Users can also **create reusable custom functions** within their pipelines and apply **data expectations** (health checks and unit tests) directly in the visual interface.

Pipeline Builder also supports **parameterized pipelines** for reusable, configurable workflows, and **sampling strategies** for testing on representative data subsets before running on full data.

**Sources:**
- [Pipeline Builder Overview](https://www.palantir.com/docs/foundry/pipeline-builder/overview)
- [Pipeline Builder Transforms Overview](https://www.palantir.com/docs/foundry/pipeline-builder/transforms-overview)
- [Pipeline Builder Functions Index](https://www.palantir.com/docs/foundry/pipeline-builder/functions-index)
- [Pipeline Builder Product Page](https://www.palantir.com/platforms/foundry/data-integration/pipeline-builder/)

---

## 2. Code Repositories -- The Code-Based Pipeline Approach

For users who need the full power of PySpark, Pandas, or Java/Scala, Foundry provides **Code Repositories** -- a Git-backed development environment where data engineers write transforms in code. Code Repositories support Python (PySpark), Java, and SQL transforms.

### The `@transform` Decorator API

The core API lives in the `transforms.api` module. The two primary decorators are:

**`@transform`** -- The general-purpose decorator that provides explicit control over reading inputs and writing outputs:

```python
from transforms.api import transform, Input, Output
from pyspark.sql import functions as F

@transform(
    output_dataset_1=Output("/project/output_clean"),
    output_dataset_2=Output("/project/output_summary"),
    raw_data=Input("/project/raw_data"),
    reference=Input("/project/reference_table")
)
def my_transform(raw_data, reference, output_dataset_1, output_dataset_2):
    raw_df = raw_data.dataframe()            # TransformInput -> PySpark DataFrame
    ref_df = reference.dataframe()

    # Join and clean
    clean = raw_df.join(ref_df, "key_column", "left") \
                  .filter(F.col("status") == "active") \
                  .withColumn("processed_at", F.current_timestamp())

    # Summarize
    summary = clean.groupBy("category").agg(F.count("*").alias("total"))

    output_dataset_1.write_dataframe(clean)    # TransformOutput.write_dataframe()
    output_dataset_2.write_dataframe(summary)
```

**`@transform_df`** -- A convenience decorator that works directly with PySpark DataFrames. It accepts a single `Output` as its positional argument and `Input` objects as keyword arguments. The decorated function receives DataFrames directly (not `TransformInput` wrappers) and returns a DataFrame that is automatically written to the output:

```python
from transforms.api import transform_df, Input, Output

@transform_df(
    Output('/examples/hair_eye_color_processed'),
    hair_eye_color=Input('/examples/students_hair_eye_color')
)
def filter_hair_color(hair_eye_color):
    return hair_eye_color.filter(hair_eye_color.hair == 'Brown')
```

### Input and Output Objects

- **`Input(path, alias=None, branch=None, description=None)`** -- specifies a dataset to read. The `path` is the Foundry resource path.
- **`Output(path, alias=None, sever_permissions=False, description=None)`** -- specifies a dataset to write. `sever_permissions` controls whether downstream permissions propagate.

At runtime, the framework injects:
- **`TransformInput`** -- exposes `.dataframe()` to get a PySpark DataFrame, `.filesystem()` for raw file access (returns a read-only `FileSystem` object), plus metadata: `.rid`, `.branch`, `.txrange`.
- **`TransformOutput`** -- exposes `.write_dataframe(df)`, `.set_mode("replace" | "modify")`, `.abort()` to cancel writing, plus `.filesystem()` for write access. Metadata: `.rid`, `.branch`, `.txrid`.

### Real-World Code Examples

**Abort on empty input:**
```python
@transform(
    out=Output("/output/not_process_empty_files"),
    source_df=Input("/input/sometimes_empty"),
)
def compute(source_df, out):
    source_df = source_df.dataframe()
    if len(source_df.head(1)) == 0:
        out.abort()
    else:
        out.write_dataframe(source_df)
```

**Read an ORC file from the raw filesystem:**
```python
@transform(out=Output("output"), raw=Input("input"))
def compute(ctx, out, raw):
    hadoop_path = raw.filesystem().hadoop_path
    df = ctx.spark_session.read.format('orc').load(f'{hadoop_path}/')
    out.write_dataframe(df)
```

**Multi-input, multi-output:**
```python
@transform(
    output_1=Output("multi_output_1"),
    output_2=Output("multi_output_2"),
    input_1=Input("dataset_a"),
    input_2=Input("dataset_b")
)
def multi_transform(input_1, input_2, output_1, output_2):
    df1 = input_1.dataframe()
    df2 = input_2.dataframe()
    output_1.write_dataframe(df1.withColumn('processed_at', F.current_timestamp()))
    output_2.write_dataframe(df1.unionByName(df2).withColumn('processed_at', F.current_timestamp()))
```

### Incremental Transforms and `@incremental`

For large datasets where re-processing everything is expensive, Foundry supports **incremental transforms** via the `@incremental()` decorator stacked with `@transform` or `@transform_df`:

```python
from transforms.api import transform, Input, Output, incremental

@incremental(semantic_version=1)
@transform(
    daily_aggregate=Output("/output/daily_agg"),
    input_data=Input("/input/events")
)
def compute(ctx, input_data, daily_aggregate):
    input_df = input_data.dataframe()
    latest = input_df.groupBy("group_field").agg(
        F.count_distinct("unique_thing").alias("sum_of_unique")
    )

    if ctx.is_incremental:
        # Read previous output and merge
        previous = daily_aggregate.dataframe(mode='previous', schema=latest.schema)
        merged = previous.unionByName(latest).groupBy("group_field").agg(
            F.sum("sum_of_unique").alias("sum_of_unique")
        )
        daily_aggregate.set_mode('replace')
        daily_aggregate.write_dataframe(merged)
    else:
        daily_aggregate.write_dataframe(latest)
```

Key mechanisms:
- **`ctx.is_incremental`** -- boolean flag indicating whether Foundry is running the build as incremental or snapshot
- **Write modes:** `set_mode("modify")` appends rows; `set_mode("replace")` replaces the entire output
- **Read modes:** `.dataframe(mode="current")` reads the full snapshot; `.dataframe(mode="previous")` reads the last committed output state
- **`semantic_version`** -- incrementing this forces a full snapshot rebuild, useful when logic changes

**Sources:**
- [Transforms Python API Reference](https://www.palantir.com/docs/foundry/transforms-python-spark/transforms-python-api)
- [Python Basic Transforms](https://www.palantir.com/docs/foundry/transforms-python/transforms)
- [Code Examples: Common Operations](https://www.palantir.com/docs/foundry/code-examples/common-operations-transforms)
- [Code Examples: Incremental Transforms](https://www.palantir.com/docs/foundry/code-examples/incremental-transforms-transforms)
- [Incremental Reference](https://www.palantir.com/docs/foundry/transforms-python/incremental-reference)
- [`@transform_df` API Reference](https://www.palantir.com/docs/foundry/api-reference/transforms-python-library/api-transform-df)

---

## 3. Data Lineage -- Automatic Tracking and Visualization

Foundry's **Data Lineage** is an interactive graph-based tool that automatically tracks how data flows through the entire platform -- from raw ingestion through every transformation to final ontology objects and applications.

### How Lineage Is Tracked Automatically

Every time a `@transform` runs, Foundry records the input-output relationship as a directed edge in a global dependency graph. Because transforms explicitly declare their `Input` and `Output` datasets, Foundry knows the full DAG without any manual annotation. This extends to Pipeline Builder pipelines, data syncs, and ontology mappings -- everything that reads or writes a dataset creates a lineage edge.

### The Lineage Graph Interface

The Data Lineage UI presents a **zoomable, pannable graph** where each node represents a Foundry resource (dataset, transform, pipeline, ontology object type). Key interaction features:

- **Search and Add:** Find any Foundry resource via free-text search or tree-based browsing and add it to the graph
- **Expand Upstream/Downstream:** Click chevron arrows on a node to expand one level of ancestors or descendants. Click the **double-chevron** to expand all the way to raw sources (upstream) or final outputs (downstream)
- **Configurable Depth:** Choose how many levels to expose when expanding
- **Automatic Layout:** Apply layout algorithms to organize nodes, or manually drag-and-drop to rearrange
- **Node Coloring:** Automatic or manual color-coding to visually separate distinct pipeline branches or teams
- **Properties Panel:** Select any node to see its details -- metadata, Foundry app links, available actions, permissions impact
- **Save and Share:** Save graph layouts for team collaboration; generate shareable read-only links; export to SVG

### Column-Level Analysis

While Foundry's lineage graph operates primarily at the dataset level, it includes features for column-level discovery:

- **"Find datasets with a given column"** -- search across your entire graph for datasets containing a specific column name
- **"Frequent columns" histogram** -- in any selection of nodes, view the most common column names and highlight which datasets contain them
- **Dataset Preview and Logic** -- select any node and open the Preview tab to see sample data alongside the transformation logic that produced it. This lets you trace how a column was derived

### Operational Features

- **Out-of-date detection:** The graph highlights datasets that are stale relative to their upstream sources
- **Build directly from lineage:** Trigger builds for out-of-date datasets without leaving the lineage view
- **Schedule management:** View, create, and modify schedules directly from within the lineage graph
- **Build timeline:** See the historical build history of any dataset
- **Rollback:** Revert datasets or pipelines to previous states

### Monocle

**Monocle** is Palantir's internal name for the lineage/graph visualization application within Foundry. According to community discussions, Monocle specifically shows "how data and logic interact in sequence and flow into your ontology." It visualizes:

- Actions that operate on ontology objects
- Applications consuming ontology objects
- Published AIP Logic functions consumed by actions
- Workshop modules linked to object types

Monocle is essentially the lineage viewer extended to cover the full operational stack -- not just ETL datasets but also the ontology, actions, and downstream applications. Community members have noted that its coverage is still expanding, with requests for better visibility into AIP Agents, sub-agents, and tool relationships.

**Sources:**
- [Data Lineage Overview](https://www.palantir.com/docs/foundry/data-lineage/overview)
- [Explore Data Lineage](https://www.palantir.com/docs/foundry/data-lineage/explore-lineage)
- [Dataset Preview and Logic](https://www.palantir.com/docs/foundry/data-lineage/dataset-preview-logic)
- [Find Datasets with a Given Column](https://www.palantir.com/docs/foundry/data-lineage/find-column)
- [Graph Visualization Tutorial](https://www.palantir.com/docs/foundry/learning-data-lineage/06)
- [Monocle Community Discussion](https://community.palantir.com/t/monocle-to-visualise-aip-architecture/1769)

---

## 4. Scheduling -- How Pipelines Are Triggered

Foundry provides a comprehensive scheduling system with both time-based (cron) and event-driven triggers, plus compound logic for combining them.

### Trigger Types

**Time Triggers (Cron):**
- Defined using **standard Unix cron expressions** (5 fields: minute, hour, day-of-month, month, day-of-week) plus a time zone
- The schedule editor provides a GUI for defining simple triggers without writing cron syntax
- For complex schedules, users can write custom cron expressions or use an **AIP-powered natural language prompt** that generates the correct cron format (e.g., "every weekday at 8am EST")

**Event Triggers:**
- **Dataset-update triggers** -- fire when a specified dataset receives a new transaction
- **New-data triggers** -- fire when new data rows appear in a dataset
- **Job-succeeded triggers** -- fire when an upstream build job completes successfully
- Event triggers remain satisfied after the event occurs until the schedule runs

**Compound Triggers:**
- Combine multiple triggers using **AND** ("All of these triggers") or **OR** ("Any of these triggers") logic
- Example AND: "Build at midnight BUT ONLY IF the upstream data sync has completed since the last build"
- Example OR: "Build whenever the hourly sync completes OR at 6am regardless"

### Build Types

- **Single build** -- build only the target datasets
- **Full build** -- build all target datasets plus all upstream datasets recursively
- **Connecting build** -- build all datasets on the path between specified inputs and target outputs

### Scheduling Best Practices

Palantir recommends structuring schedules so that event triggers on upstream data are combined with time triggers to create predictable SLAs. The system supports **fallback branch handling** in Pipeline Builder, AI-powered schedule creation, and integration with **Marketplace** for distributing scheduled products.

**Sources:**
- [Scheduling Overview](https://www.palantir.com/docs/foundry/building-pipelines/scheduling-overview)
- [Trigger Types Reference](https://www.palantir.com/docs/foundry/building-pipelines/triggers-reference)
- [Common Scheduling Configurations](https://www.palantir.com/docs/foundry/building-pipelines/common-schedules)
- [Create a Schedule](https://www.palantir.com/docs/foundry/building-pipelines/create-schedule)
- [Scheduling Best Practices](https://www.palantir.com/docs/foundry/building-pipelines/scheduling-best-practices)

---

## 5. Data Connectors -- Connecting to SAP, Salesforce, SQL, and On-Prem Systems

Foundry's **Data Connection** module provides **400+ connectors** spanning databases, SaaS applications, cloud storage, and enterprise systems.

### Architecture: Three Connection Modes

**1. Foundry Worker (Cloud-Side Processing) -- Recommended for cloud-accessible systems:**
- Data processing runs on Foundry's managed compute infrastructure
- The source system must be reachable over the internet (or via Private Link)
- Simplest setup; no customer-hosted components required

**2. Foundry Worker with Agent Proxy (Recommended for on-prem/private networks):**
- A lightweight **agent** is installed on a customer-provided Linux host (RHEL 8+, Ubuntu 22.04+, or equivalent 64-bit Linux)
- The agent acts as a **network tunnel only** -- it does not process data itself
- All compute still runs on Foundry workers; the agent just provides network access to the private system
- The agent manager connects back to Foundry's `magritte-coordinator` service
- Requires proxy/certificate configuration if traffic is intermediated

**3. Agent Worker (Legacy for specific use cases):**
- The agent itself runs the source processing compute on the customer host
- Used only for specific file-based syncs, micro-batching from on-prem systems, or when data must be filtered heavily before leaving the network
- More complex to maintain; Palantir recommends migrating to agent proxy mode

### Agent Installation

- Download the agent software from within Foundry
- Install on a **64-bit Linux host** following the in-platform guide
- The agent registers with Foundry and is managed remotely
- Certificate configuration needed if a transparent/explicit proxy intermediates traffic to Foundry
- Configuration lives in `<agent-manager-install-directory>/var/conf/runtime.yml`

### Connector Examples

**SAP (Certified Add-On):**
- The **Palantir Foundry Connector 2.0 for SAP Applications** is an SAP Certified Add-On, installed via SAINT (SAP Add-On Installation Tool)
- Developed in partnership with Diskover Limited
- Supports **S/4HANA, ECC, Business Warehouse, SLT Replication Server**
- Installed on the SAP application layer itself; uses native SAP security policies and application logic
- Three application components: `PALANTIR` (shared objects, required), `PALCONN` (connector objects/services), `PALODATA` (optional, SLT OData APIs)
- Integrates with **SAP SLT** (Landscape Transformation Replication Server) for **change data capture (CDC)** using database triggers, enabling efficient incremental replication

**Salesforce:**
- Native Salesforce connector syncs data bidirectionally between Salesforce and Foundry datasets
- Can run on a Foundry worker or an agent worker
- Supports standard and custom Salesforce objects

**SQL Databases:**
- Foundry provides **JDBC-based connectors** for: Amazon Athena, Hive, IBM Db2, Informix, MariaDB, Microsoft SQL Server, MySQL, Oracle Database, PostgreSQL, SQLite, Sybase, Vertica
- Custom JDBC connector for any JDBC-compatible source
- JDBC connection optimization guidance available for performance tuning

### Advanced Connectivity Features

- **Webhooks** for event-driven data push
- **Listeners** for Google Pub/Sub, Jira, Slack
- **External Connections from Code** -- Python environments can access sources directly via `compute pushdown`
- **Virtual Tables** for query-based data access without materializing full datasets
- **Private Link support** for AWS, Azure, and GCP
- **Streaming syncs** for real-time data flows

**Sources:**
- [Data Connection Core Concepts](https://www.palantir.com/docs/foundry/data-connection/core-concepts)
- [Data Connection Architecture](https://www.palantir.com/docs/foundry/data-connection/architecture)
- [Set Up an Agent](https://www.palantir.com/docs/foundry/data-connection/set-up-agent)
- [Agent Worker Configuration](https://www.palantir.com/docs/foundry/data-connection/agent-worker)
- [Agent Proxy Configuration](https://www.palantir.com/docs/foundry/data-connection/agent-proxy)
- [SAP Overview](https://www.palantir.com/docs/foundry/sap/overview)
- [SAP SLT Configuration](https://www.palantir.com/docs/foundry/sap/configure-sap-slt)
- [Salesforce Connector](https://www.palantir.com/docs/foundry/available-connectors/salesforce)
- [JDBC Custom Connector](https://www.palantir.com/docs/foundry/available-connectors/custom-jdbc-sources)
- [Foundry Connector 2.0 for SAP v2.31.0 Community Post](https://community.palantir.com/t/foundry-connector-2-0-for-sap-applications-v2-31-0-sp31-is-now-available/510)

---

## 6. OSDK (Ontology SDK) -- External Application Access to the Ontology

The **Ontology SDK (OSDK)** enables external applications -- web frontends, backend services, scripts -- to programmatically query and modify Foundry's ontology. It is a **code-generated, type-safe client library** tailored to your specific ontology entities.

### How It Works

1. **Developer Console:** In Foundry's Developer Console, you create an application and select which ontology entities (object types, action types, link types) it should have access to
2. **Code Generation:** The Console generates a type-safe SDK package for your chosen language, containing classes and methods matching your ontology's property names, action parameters, and link definitions
3. **Install and Use:** Install the generated package (NPM for TypeScript, pip/Conda for Python, Maven for Java) and use it with strong editor autocompletion and type checking
4. **OpenAPI Spec:** For any other language, the Console can export an OpenAPI specification

### Key Benefits
- **Strong type safety** -- generated types match your ontology exactly; editor integration provides autocomplete
- **Scoped tokens** -- each OSDK app uses tokens limited to the specific ontology entities granted, combined with user permissions
- **Centralized maintenance** -- when the ontology changes, regenerate the SDK and the new types flow through

### TypeScript OSDK (`@osdk/client`)

**Installation and Setup:**
```typescript
import { createClient } from "@osdk/client";
import { createConfidentialOauthClient, createPublicOauthClient } from "@osdk/oauth";

// Server-side (confidential client)
const auth = createConfidentialOauthClient(
  "<CLIENT_ID>", "<CLIENT_SECRET>", "<FOUNDRY_URL>"
);

// Browser-side (public client with redirect)
const auth = createPublicOauthClient(
  "<CLIENT_ID>", "<FOUNDRY_URL>", "http://localhost:8080/callback"
);

// Create the client
const client = createClient("https://mystack.palantir.com", "ri.ontology.main.ontology.xxx", auth);
```

**Querying Objects:**
```typescript
// Fetch a page of objects
const result = await client(MyObjectType).fetchPage({ $pageSize: 30 });
console.log(result.data); // array of typed objects

// Fetch a single object by primary key
const obj = await client(MyObjectType).fetchOne("pk-123");

// Async iteration over all objects
for await (const obj of client(MyObjectType).asyncIter()) {
  console.log(obj);
}
```

**Filtering with `.where()`:**
```typescript
// String prefix filter
const filtered = await client(Task).where({
  projectId: { $eq: "proj-abc" },
  status: { $startsWith: "in_" }
}).fetchPage({
  $orderBy: { "dueDate": "desc", "status": "asc" },
  $pageSize: 50
});

// DateTime range filter
const recent = await client(Event).where({
  createdAt: { $gt: "2024-01-01T00:00:00Z" }
}).fetchPage();
```

**Aggregations:**
```typescript
// Simple count
const countResult = await client(MyObject).where({...}).aggregate({
  $select: { $count: "unordered" }
});
console.log(countResult.$count);

// GroupBy with aggregation
const grouped = await client(MyObject).aggregate({
  $select: { $count: "unordered" },
  $groupBy: { category: "exact", region: "exact" }
});
```

**Links (Relationships):**
```typescript
const employee = await client(Employee).fetchOne("emp-42");
const departments = await employee.$link.department.fetchPage({ $pageSize: 100 });
```

**Actions:**
```typescript
// Apply an action
await client(CreateEmployee).applyAction({ name: "Alice", role: "Engineer" });

// Batch action
await client(CreateEmployee).batchApplyAction([
  { name: "Bob", role: "Analyst" },
  { name: "Carol", role: "Manager" }
]);

// Validate before applying
const validation = await client(CreateEmployee).applyAction(
  { name: "Dave", role: "?" },
  { $validateOnly: true }
);

// Execute a query/function
const result = await client(GetEmployeesInCity).executeFunction({ city: "Berlin" });
```

**GitHub Repository:** [palantir/osdk-ts](https://github.com/palantir/osdk-ts) -- Monorepo containing `@osdk/client`, `@osdk/api`, `@osdk/oauth`, and `@osdk/foundry-sdk-generator`. 96.9% TypeScript. Requires Node.js >= 18.19.0. Uses pnpm for package management.

### Python OSDK

**Querying Objects:**
```python
from ontology_sdk.ontology.objects import ExampleRestaurant

# Get a single object
result = client.ontology.objects.ExampleRestaurant.get("primaryKey")

# Paginate
page = client.ontology.objects.ExampleRestaurant.page(page_size=30, page_token=None)

# Iterate all objects
for obj in client.ontology.objects.ExampleRestaurant.iterate():
    print(obj)
```

**Filtering:**
```python
# Equality
results = client.ontology.objects.ExampleRestaurant.where(
    ExampleRestaurant.object_type.restaurant_name == "Pizza Palace"
)

# Null check
results = client.ontology.objects.ExampleRestaurant.where(
    ExampleRestaurant.object_type.restaurant_name.is_null()
)

# String prefix
results = client.ontology.objects.ExampleRestaurant.where(
    ExampleRestaurant.object_type.restaurant_name.starts_with(['foo'])
)

# Full-text search (contains any term)
results = client.ontology.objects.ExampleRestaurant.where(
    ExampleRestaurant.object_type.restaurant_name.contains_any_term(['pizza italian'])
)

# Range comparison
results = client.ontology.objects.ExampleRestaurant.where(
    ExampleRestaurant.object_type.restaurant_name < "Restaurant Name"
)

# Boolean composition (AND, OR, NOT)
results = client.ontology.objects.ExampleRestaurant.where(
    ~ExampleRestaurant.object_type.restaurantId.is_null() &
    (ExampleRestaurant.object_type.restaurantId == '<primaryKey>')
)

# Ordering
results = client.ontology.objects.ExampleRestaurant.where(
    ~ExampleRestaurant.object_type.restaurant_name.is_null()
).order_by(ExampleRestaurant.object_type.restaurant_name.asc()).iterate()
```

**Aggregations:**
```python
# Count
count = client.ontology.objects.ExampleRestaurant.count().compute()

# Average
avg = client.ontology.objects.ExampleRestaurant.avg(
    ExampleRestaurant.object_type.number_of_reviews
).compute()

# Approximate distinct
distinct = client.ontology.objects.ExampleRestaurant.approximate_distinct(
    ExampleRestaurant.object_type.restaurant_name
).compute()

# GroupBy aggregation
grouped = client.ontology.objects.ExampleRestaurant.where(
    ~ExampleRestaurant.object_type.restaurant_name.is_null()
).group_by(
    ExampleRestaurant.object_type.restaurant_name.exact()
).count().compute()
```

### Foundry Platform SDK (Lower-Level API)

For operations outside the ontology (dataset management, admin, raw API access), Palantir provides:

- **Python:** [palantir/foundry-platform-python](https://github.com/palantir/foundry-platform-python) (`pip install foundry-platform-sdk`)
- **TypeScript:** [palantir/foundry-platform-typescript](https://github.com/palantir/foundry-platform-typescript) (NPM packages as `@osdk/foundry.{namespace}`)

```python
import foundry_sdk
from foundry_sdk import FoundryClient

client = FoundryClient(
    auth=foundry_sdk.UserTokenAuth("your_token"),
    hostname="example.palantirfoundry.com"
)

# Dataset operations
for branch in client.datasets.Dataset.Branch.list(dataset_rid):
    print(branch)

# Create a branch
client.datasets.Dataset.Branch.create(dataset_rid, name="feature-branch")
```

**Sources:**
- [OSDK Overview](https://www.palantir.com/docs/foundry/ontology-sdk/overview)
- [Python OSDK](https://www.palantir.com/docs/foundry/ontology-sdk/python-osdk)
- [TypeScript OSDK Migration Guide](https://www.palantir.com/docs/foundry/ontology-sdk/typescript-osdk-migration)
- [Generate OSDK for Other Languages](https://www.palantir.com/docs/foundry/ontology-sdk/generate-osdk-for-other-languages)
- [palantir/osdk-ts on GitHub](https://github.com/palantir/osdk-ts)
- [palantir/foundry-platform-python on GitHub](https://github.com/palantir/foundry-platform-python)
- [palantir/foundry-platform-typescript on GitHub](https://github.com/palantir/foundry-platform-typescript)
- [foundry-platform-sdk on PyPI](https://pypi.org/project/foundry-platform-sdk/0.8.0/)
- [Bootstrap Python OSDK Application](https://www.palantir.com/docs/foundry/ontology-sdk/how-to-bootstrapping-python/)

---

## 7. Rubix -- Palantir's Kubernetes-Based Compute Substrate

**Rubix** is Palantir's hardened, autoscaling implementation of Kubernetes that serves as the compute infrastructure foundation for AIP, Foundry, and Apollo.

### History and Motivation

In January 2017, Palantir kicked off the Rubix project to rebuild their cloud architecture around Kubernetes. The core objective was to create a **secure, scalable, and intelligent scheduling and execution engine** for Spark and other distributed compute frameworks. By 2019, Kubernetes was live across their production fleet, handling hundreds of thousands of Spark jobs across thousands of nodes daily.

### Architecture

Rubix extends open-source Kubernetes with enterprise security and operational hardening:

- **Node Ephemerality:** Every node is recycled within **48 hours**. This is a hard architectural requirement -- every service must be designed for disruption and resilient failover. The aggressive cycling prevents persistent attacker access to compromised infrastructure.
- **Workload Isolation:** Workloads are securely isolated based on operational requirements. This includes multi-tenant security for user-authored code (e.g., PySpark transforms written by customers).
- **Encryption Everywhere:** Every interaction between workloads requires authentication, authorization, and immutable logging.
- **Compliance:** Meets FedRAMP High, DoD DISA IL-5/IL-6, and CMMC standards.
- **Network Security:** Uses Cilium for network segmentation, pod security contexts, immutable infrastructure patterns.

### Spark on Kubernetes: The k8s-spark-scheduler

A critical piece of Rubix is the **`k8s-spark-scheduler`** ([palantir/k8s-spark-scheduler](https://github.com/palantir/k8s-spark-scheduler)), an open-source Kubernetes Scheduler Extender that provides **gang scheduling** for Spark. It solved two production problems:

**Problem 1: Unreliable Executor Scheduling.** With the default `kube-scheduler`, Spark drivers could be scheduled but their executors might not get resources, leading to applications that hang indefinitely consuming cluster resources. The gang scheduler guarantees that **a driver is only scheduled if there is space in the cluster for all of its executors**.

**Problem 2: Slow Autoscaling.** Default Kubernetes autoscaling reacts to resource pressure after the fact. The k8s-spark-scheduler uses **demand-sensing algorithms** to request new nodes proactively based on pending workloads.

The scheduler runs alongside the default kube-scheduler. Users opt in by setting `schedulerName: spark-scheduler` on their pods. It supports:
- FIFO ordering so older driver pods are scheduled before newer ones
- Bin-packing modes: `distribute-evenly` or `tightly-pack`
- Dynamic allocation with min/max executor counts
- Pod annotations for resource declarations: `spark-driver-cpu`, `spark-driver-mem`, `spark-executor-cpu`, `spark-executor-mem`, `spark-executor-count`

> **Note:** The open-source k8s-spark-scheduler was archived in April 2023; Palantir's internal version continues to evolve.

### Intelligent Autoscaling

Rubix includes **demand-sensing algorithms** and workload distribution capabilities that optimize costs across cloud providers (AWS, Azure, Google Cloud, Oracle) and on-premises deployments. The platform operates with Apollo, Palantir's mission control system, which computes and transmits deployment plans for **zero-downtime blue/green rollout** strategies across hundreds of services.

### Spark within Foundry

Apache Spark is the most commonly used execution engine in Foundry's data integration layer. Foundry provides several optimization mechanisms on top of Rubix:

- **Spark profiles** that enable/disable Adaptive Query Execution (AQE), letting Spark automatically determine partition counts at runtime
- **Spark UI** access for debugging job execution plans, stages, and tasks
- Guidance to help Spark's query optimizer: reduce data early, reorder operations so filtering precedes joins, use partitioning strategies

**Sources:**
- [Rubix Architecture Center](https://www.palantir.com/docs/foundry/architecture-center/rubix)
- [Rubix Product Page](https://www.palantir.com/rubix/)
- [Introducing Rubix (Palantir Blog)](https://blog.palantir.com/introducing-rubix-kubernetes-at-palantir-ab0ce16ea42e)
- [Spark Scheduling in Kubernetes (Palantir Blog)](https://medium.com/palantir/spark-scheduling-in-kubernetes-4976333235f3)
- [palantir/k8s-spark-scheduler on GitHub](https://github.com/palantir/k8s-spark-scheduler)
- [Benefits of Ephemeral Compute (Palantir Blog)](https://blog.palantir.com/the-benefits-of-running-kubernetes-on-ephemeral-compute-436e5acf13fb)
- [Spark Concepts in Foundry](https://www.palantir.com/docs/foundry/optimizing-pipelines/spark-concepts)
- [Spark Profiles Reference](https://www.palantir.com/docs/foundry/optimizing-pipelines/spark-profiles-reference)

---

## 8. Monocle and the Foundry Data Catalog (Compass)

### Monocle

**Monocle** is Palantir's graph-based lineage and architecture visualization tool within Foundry. It extends beyond traditional ETL lineage to show the full operational picture:

- **Data-to-ontology flow:** How raw datasets flow through transforms into ontology object types
- **Actions and logic:** Which actions modify ontology objects and what AIP Logic functions they consume
- **Application dependencies:** Which Workshop modules, Quiver analyses, and applications consume which object types
- **Pipeline health:** The state of data pipelines, with proactive monitoring to surface issues before critical errors

According to ex-Palantir engineers (per Hacker News discussions), Monocle is the "graph viewer of the ETL" and is one of Foundry's core differentiating tools alongside the code versioning system, RBAC, and Slate (UI builder). Community discussions on the Palantir Developer Community indicate users are leveraging Monocle to track complex AIP Agent Studio architectures, though visibility into all resource types (e.g., Quiver Analyses, all AIP Agent relationships) is still being expanded.

### Compass and the Data Catalog

Separately, Foundry includes **Compass** as its navigation and organization layer, and within Compass, the **Data Catalog**:

- **Collections and Files:** The Data Catalog is organized into Collections (curated groups of resources for a given topic, audience, or purpose) and Files. Anyone can view collection descriptions, but access to individual files is permission-controlled.
- **Search:** Full-text search across descriptions, column names, file paths, with filters by creator, tags, Projects, and folders
- **Tags:** Structured metadata applied to resources for categorization and discovery. Used to filter collections and search results.
- **Governance:** Platform administrators use the Data Catalog to centrally manage data onboarding and signal governance controls. Organization administrators manage collection membership and permissions.
- **Quicksearch:** A universal search bar for finding Palantir apps, objects, datasets, and other files with advanced filtering

According to a Palantir Blog post on data cataloging, the system is designed to "bring order to chaos" by giving users a curated, searchable interface to discover the data most relevant to them, while administrators maintain governance controls.

**Sources:**
- [Monocle Community Discussion](https://community.palantir.com/t/monocle-to-visualise-aip-architecture/1769)
- [Hacker News: Ex-Palantir Discussion](https://news.ycombinator.com/item?id=33593392)
- [Compass Data Catalog](https://www.palantir.com/docs/foundry/compass/data-catalog)
- [Compass Overview](https://www.palantir.com/docs/foundry/compass/overview)
- [Compass Quicksearch](https://www.palantir.com/docs/foundry/compass/quicksearch)
- [Compass Tags](https://www.palantir.com/docs/foundry/compass/tags)
- [Data Cataloging Blog Post](https://blog.palantir.com/data-cataloging-bringing-order-to-chaos-9fa0db75f3f0)
- [Foundry Governance Processes](https://www.palantir.com/docs/foundry/foundry-adoption/governance-processes)
