# Inside Palantir Foundry: an implementation-level developer guide

**Palantir Foundry is not one product but an interlocking system of five major subsystems — Ontology Manager, Pipeline Builder, Workshop, AIP, and Apollo — each with distinct developer surfaces that collectively turn raw data into operational applications.** This report provides the actual UI workflows, code patterns, configuration mechanics, and architectural details that developers encounter when building on Foundry. Everything below reflects real developer experience: what you click, what you type, and what happens under the hood.

---

## 1. The Ontology Manager: creating the semantic backbone

The Ontology Manager is the control center where developers define the typed data model — Object Types, Properties, Links, and Interfaces — that the rest of Foundry consumes. The UI is accessed from the Foundry navigation sidebar and organized into three zones: a **left sidebar** showing a hierarchical tree of all Object Types, Link Types, and Interfaces (with search); a **center panel** displaying the selected entity's configuration across tabbed views (Overview, Properties, Links, Actions, Permissions); and a **top toolbar** with "+ Create" buttons for new ontology entities.

### Creating an Object Type step-by-step

The workflow is linear and surprisingly concrete:

1. Click **"+ Create Object Type"** in the toolbar
2. Enter a display name (e.g., "Customer") and an API name (auto-generated as `customer` but editable). Optionally pick an icon and write a description
3. **Select a backing dataset** — browse or search Foundry's data catalog and point to a Parquet dataset. This is the critical architectural choice: **every Object Type is backed by exactly one dataset**
4. **Set the primary key** — select which column uniquely identifies each object instance
5. **Map columns to properties** — the UI auto-detects columns and suggests mappings. For each property you configure a display name, API name, data type, and whether it's searchable or filterable
6. Set the **title property** (which property renders as the object's display name in UIs), configure visibility, and save

The supported property types cover primitives through complex structures:

| Category | Types |
|----------|-------|
| Numeric | Integer, Long, Short, Float/Double, Decimal, Byte |
| Text/Boolean | String, Boolean |
| Temporal | Date, Timestamp |
| Geospatial | GeoPoint (lat/lng), GeoShape (GeoJSON), Geohash |
| Complex | Struct (nested fields), Array, Set, Map |
| References | Attachment, Media Reference, Timeseries, Marking |

**Struct properties** are particularly important for embedding small nested objects (e.g., a `contactInfo` struct with `{phone, email, method}`) without creating a separate Object Type.

### Link Types connect objects through foreign keys, not a graph database

Creating a Link Type follows a specific pattern: select source Object Type → name the relationship (e.g., "has orders") → select target Object Type → choose cardinality (1:1, 1:N, N:1, M:N) → **map the foreign key** (e.g., `Customer.customerId` → `Order.customerId`). For many-to-many relationships, a junction dataset is required. The UI auto-creates the reverse link.

A crucial architectural detail: **links are not stored as edges in a graph database**. They are resolved at query time by joining on the specified foreign key columns in the backing datasets. This is why each Object Type needs exactly one backing dataset — the join semantics are relational.

### Interfaces and Functions add polymorphism and computed behavior

**Interfaces** work like abstract types. You create one (e.g., "HasLocation"), define required properties (`latitude: Double`, `longitude: Double`), and then attach it to multiple Object Types, mapping each type's actual columns to the interface's contract. This enables polymorphic queries — a Workshop map widget can display all "HasLocation" objects regardless of concrete type.

**Functions** are written in TypeScript in a dedicated Functions Repository:

```typescript
import { Function } from "@foundry/functions-api";
import { Objects, Customer } from "@foundry/ontology-api";

export class CustomerFunctions {
  @Function()
  public getCustomerOrderCount(customer: Customer): Integer {
    const orders = customer.orders.all();  // traverses a link
    return orders.length;
  }

  @Function()
  public getHighValueCustomers(): Customer[] {
    return Objects.search()
      .customer()
      .filter(c => c.totalSpend.gt(10000))
      .all();
  }
}
```

Functions use the `@Function()` decorator, auto-generated type-safe ontology access via `@foundry/ontology-api`, link traversal, and can be exposed as computed properties on Object Types or as Action handlers using the `@Action()` decorator.

---

## 2. When to create an Object Type versus a property or struct

This is the foundational ontology design decision, and Palantir's Forward Deployed Engineers (FDEs) apply a consistent heuristic: **"Can someone walk up to this entity and ask questions about it in isolation?"** If yes, it's an Object Type.

More specifically, create a separate Object Type when the entity has its own identity, has multiple properties of its own (**more than 2–3 attributes**), participates in relationships beyond its parent, is shared across multiple parents (many Customers share the same City), needs independent permissions, or has its own lifecycle. Keep it as a property when it's a simple 1–3 field attribute unique to its parent, never queried independently, and always changes with the parent.

### The Customer Address example

If a customer has **one address** used only for that customer, flat properties (`streetAddress`, `city`, `state`, `zipCode`) are simpler and recommended. If a customer can have **multiple addresses** (billing, shipping) or addresses are shared across entities, a separate Address Object Type linked to Customer is better. The struct option sits in between: use a struct for small, fixed-schema nested data (like `contactInfo`) that's always read with the parent and doesn't participate in other relationships.

### Core FDE design principles

The training emphasis is pragmatic: start from user workflows, not data models. Don't over-normalize — Foundry favors **denormalization** for query performance. Choose stable, immutable primary keys (composite keys should be concatenated into a single column). **Link sparingly** since every link adds query complexity. Use interfaces for cross-cutting concerns rather than duplicating properties.

---

## 3. Schema evolution: no ALTER TABLE, but patterns exist

Foundry's ontology has no built-in migration tool comparable to Flyway or Liquibase. Schema changes are manual, following established patterns.

**Non-breaking changes** (adding a property) are straightforward: add the column to the backing dataset's pipeline, re-run it, then add the property mapping in Ontology Manager. Existing applications continue working.

**Breaking changes** (renaming an API name, changing a type, altering a primary key) use the **"replacement pipeline" pattern**: create a new version of the backing dataset with the new schema, create a new Object Type (e.g., `CustomerV2`), migrate all consumers (Workshop apps, Functions, OSDK clients) to the new type, test in a development branch, then switch over and deprecate the old type. This side-by-side approach enables zero-downtime migration.

Foundry supports **dataset and code branching** — you can make schema changes on a branch, point the Ontology Manager at that branch for testing, validate, then merge. Some teams maintain ontology definitions in code repositories using the Ontology API, enabling review workflows before changes hit production.

---

## 4. Pipeline Builder: visual ETL with a live data preview

Pipeline Builder is Foundry's no-code ETL tool. The interface is a **canvas-based DAG editor** with nodes flowing left-to-right: a left sidebar for browsing/searching input datasets, a center canvas where you drag, connect, and arrange transform nodes, a right panel for node configuration, and a **bottom data preview pane** that updates live as you modify each step.

### Creating a pipeline

Drag source datasets from the sidebar onto the canvas → click the "+" on a node's output edge to add transforms → configure each node in the right panel → designate final nodes as output datasets with a Foundry path → click "Build" to compile the visual graph into an optimized Spark execution plan.

### Available transform nodes

The node library covers the full spectrum of data transformation:

- **Structural**: Filter (with compound AND/OR conditions), Join (inner, left/right/full outer, cross, semi/anti), Union, Sort, Limit, Deduplicate (with ranking strategy)
- **Reshaping**: Aggregate (SUM, COUNT, AVG, MIN, MAX, COUNT DISTINCT, STDDEV, PERCENTILE, COLLECT_LIST), Pivot, Unpivot, Flatten/Explode (for arrays)
- **Column operations**: Select/Rename, Add Column (expression builder with string manipulation, math, date functions, CASE WHEN), Cast Types, Window Functions (ROW_NUMBER, RANK, LAG, LEAD, running aggregates)
- **Custom Code**: A PySpark node that opens a Monaco-based code editor

**Mixing visual and code nodes is fully supported.** You can insert a Custom Code node at any point, write PySpark that receives the upstream DataFrame, and return a transformed DataFrame that feeds into downstream visual nodes:

```python
def custom_transform(input_df):
    from pyspark.sql import functions as F
    return input_df.withColumn(
        "full_name",
        F.concat(F.col("first_name"), F.lit(" "), F.col("last_name"))
    ).filter(F.col("status") == "active")
```

Lineage tracking works through code nodes seamlessly.

---

## 5. Code Repositories: the @transform decorator and real pipeline code

For power users, Foundry's Python transforms API (from the `transforms` library, open-sourced at `palantir/transforms-python`) is the workhorse. The two core decorators are:

**`@transform_df`** — the most common pattern. Inputs arrive as PySpark DataFrames; you return a DataFrame:

```python
from transforms.api import transform_df, Input, Output
from pyspark.sql import functions as F

@transform_df(
    Output("/Company/Ontology/Backing Datasets/clean_customer_orders"),
    raw_orders=Input("/Company/Data/Raw/SAP/orders"),
    customer_master=Input("/Company/Data/Clean/customer_master"),
)
def compute_clean_customer_orders(raw_orders, customer_master):
    orders_clean = (
        raw_orders
        .filter(F.col("order_status") != "CANCELLED")
        .withColumn("order_date", F.to_date("order_date_str", "yyyyMMdd"))
        .withColumn("order_amount", F.col("order_amount_raw").cast("double"))
    )
    result = orders_clean.join(
        customer_master.select("customer_id", "customer_name", "segment"),
        on="customer_id", how="left"
    )
    return result.withColumn("is_high_value",
        F.when(F.col("order_amount") > 10000, True).otherwise(False))
```

**`@transform`** — lower-level, with explicit `TransformInput`/`TransformOutput` objects. Required for multi-output transforms or filesystem access.

### Scheduling supports three modes

**Cron-based**: A visual cron builder in the Builds tab lets you select hourly/daily/weekly/monthly with specific times. **Event-driven**: Toggle "Build on upstream change" to trigger when any input dataset receives new data, creating cascading build chains. **Manual**: The "Build" button triggers ad-hoc execution of specific transforms.

### Incremental processing via the @incremental() decorator

Adding `@incremental()` makes Foundry track which input transactions have been consumed. On the next build, `source.dataframe()` returns only new/changed rows:

```python
from transforms.api import transform, Input, Output, incremental

@incremental()
@transform(
    output=Output("/path/to/output"),
    source=Input("/path/to/source"),
)
def incremental_pipeline(source, output):
    new_data = source.dataframe()  # Only new rows since last run
    output.write_dataframe(new_data, mode="append")
```

Output modes include `append`, `replace` (fall back to full recompute), and `modify` (upsert). Setting `require_incremental=True` prevents accidental full recomputation.

### Testing is built into the development workflow

The `transforms.testing` module provides `mock_transform()` for unit testing with local Spark sessions. Data quality checks use the `Check` object:

```python
@transform_df(
    Output("/path/to/output", checks=[
        Check(lambda df: df.filter(df.amount < 0).count() == 0,
              "No negative amounts", on_error=CheckSeverity.WARN),
        Check(lambda df: df.count() > 0,
              "Output is non-empty", on_error=CheckSeverity.FAIL),
    ]),
    source=Input("/path/to/source"),
)
def my_checked_transform(source):
    return source.filter(source.status == "active")
```

Code Repositories have built-in CI — pushing to a branch runs pytest automatically, and PRs cannot merge if tests fail.

---

## 6. Data lineage: automatic, column-level, and security-aware

Foundry automatically tracks lineage at the **dataset-transform-dataset** level. Every `Input()`/`Output()` declaration creates a lineage edge. There is no opt-in — this tracking is mandatory. At the transaction level, Foundry records which input transactions were consumed, which transform code (with git commit hash) executed, and which output transactions were produced.

**Column-level lineage** is inferred by parsing Spark's Catalyst logical plan. For Pipeline Builder, each visual node's column flow is tracked explicitly. The visualization is an interactive horizontal DAG accessible from any dataset's "Lineage" tab: dataset nodes (showing name, owner, last build time, health status) connected by transform edges. You can expand upstream or downstream, set depth controls, and click a specific column to see a highlighted path showing exactly which upstream columns contributed.

### Security markings propagate automatically through lineage

This is a distinctive Foundry capability. If Source A carries "SENSITIVE" and Source B carries "CONFIDENTIAL," their join output **automatically inherits both markings**. This is enforced at the platform level — a developer cannot manually lower a derived dataset's classification below what lineage implies. Users who lack access to upstream datasets see those lineage nodes as "restricted" placeholders. Approved "declassification" transforms (e.g., anonymization pipelines) can reduce markings, but require explicit governance approval and are logged in an immutable audit trail.

---

## 7. Workshop: building operational applications with widgets and variables

Workshop is Foundry's no-code application builder. The interface is a **canvas-based editor** with a grid layout system: a left sidebar listing widgets by category, a center canvas for drag-and-drop placement, a right configuration panel for the selected widget, and a preview mode for testing. Applications support multiple pages, reusable modules, and role-based visibility.

### The widget library covers display, input, action, and layout

**Display widgets** include Object Table (sortable/filterable columns bound to Object Type properties), Charts (bar, line, area, pie, scatter), Map (geospatial with lat/lng or GeoShape), KPI/Metric Card, Timeline, Pivot Table, Details Panel, and Card Sets. **Input widgets** include Property Filter, Date Range Picker, Slider, Search Bar, Toggle, Dropdown, Geo Filter (draw on map), and Object Selector. **Action widgets** include Action Button, Form, and Bulk Action Button. **Layout widgets** include Container, Tabs, Column Layout, Conditional Visibility, and Header.

### Binding a table to an Object Type

Drag an Object Table widget → in the config panel, select an Object Type (e.g., "Flight") → optionally specify an Object Set filter → toggle which properties appear as columns → drag to reorder → set column widths → configure default sort direction → enable per-column filtering → set pagination (25/50/100) → enable row selection and configure click behavior.

### Action buttons connect to Ontology write-back

Drag a Button widget → set the label → select an Action Type from the Ontology → bind each parameter (static value, Workshop variable, or form field input) → configure confirmation dialog, success/error messages, and post-action behavior (refresh data, navigate, clear selection). The button respects Ontology-level permissions — users without execute permission see the button disabled or hidden.

### Variables are the nervous system linking widgets together

**Workshop Variables** are the core mechanism for inter-widget communication. You define variables with names and types (string, number, object reference, object set, boolean, date). Any widget can write to a variable (table selection, filter input, button click) and any widget can read from one.

The canonical pattern: Table A (Customers) is configured so that on row click, it sets `selectedCustomer` to the clicked object. Table B (Orders) has its Object Set filtered to `Orders where customer = {{selectedCustomer}}`. A Details Panel reads `selectedCustomer` to show full properties. A Map highlights the selected customer's location. A single filter widget can control multiple tables, charts, and maps through shared variables.

---

## 8. Workshop, Quiver, Contour, and Slate serve different needs

These four tools occupy distinct positions in Foundry's application landscape:

| Dimension | Workshop | Quiver | Contour | Slate |
|-----------|----------|--------|---------|-------|
| Purpose | Operational apps with write-back | Dashboards and KPI monitoring | Ad-hoc data exploration | Custom-coded applications |
| Write-back | Yes (Ontology Actions) | No (read-only) | No | Yes (via API) |
| Code required | No | No | No | HTML/JS/CSS |
| Target user | Business ops, managers | Executives, analysts | Data analysts | Developers |
| Build speed | Fast | Very fast | N/A (exploration tool) | Slow |
| Custom UI | Limited to widget library | Limited | N/A | Full control |
| Multi-page | Yes | No (single dashboard) | No (analysis boards) | Yes |
| Forms/input | Yes | No | No | Yes (coded) |

The decision flow taught in Foundry training: **Do users need to take actions?** → Workshop. **Is it a monitoring dashboard with no write-back?** → Quiver. **Is it ad-hoc exploration?** → Contour. **Do you need pixel-perfect custom UI or third-party JS libraries (D3, Leaflet)?** → Slate. **Default choice for new apps?** → Workshop.

**Quiver** differs from Workshop charts by being optimized for analytics: faster dashboard creation, better aggregation and time-series functions, drill-down capabilities, and more chart types — but no actions. **Contour** lets analysts interactively pivot, filter, join, and aggregate data without predefined views, working on raw datasets as well as Ontology objects. **Slate** predates Workshop and gives full HTML/JS/CSS control with Handlebars-like templating, but Palantir actively steers new development toward Workshop, which has been rapidly absorbing capabilities that previously required Slate.

---

## 9. AIP Logic generates deterministic code, not runtime LLM calls

AIP Logic's workflow is often misunderstood. **The LLM is used at development time to generate code; the deployed function runs deterministically without any LLM.** The process: describe the function in natural language in the AIP Logic editor → the LLM generates TypeScript using `@foundry/functions-api` → test against real Ontology objects in an inline panel → iterate with natural language feedback → deploy as a standard Foundry Function.

### AIP accesses typed Ontology objects, not raw data

This is architecturally critical. AIP agents and functions receive fully typed objects with autocompleted properties and navigable links:

```typescript
@Function()
public assessRisk(ticket: MaintenanceTicket): string {
    const asset = ticket.linkedAsset;           // Link traversal
    const criticality = asset?.criticality;     // Typed enum
    const daysSince = ticket.daysSinceLastService;
    if (criticality === "HIGH" && daysSince > 90) return "CRITICAL";
    return "NORMAL";
}
```

The `@foundry/ontology-api` package auto-generates TypeScript interfaces from the Ontology schema, meaning the LLM's actions are constrained to valid Ontology operations.

### Guardrails operate at four layers

**Action permissions**: Actions define which Object Types can be modified, with validation rules enforced in code. **Agent tool restrictions**: When configuring an AIP agent, you explicitly whitelist which Functions it can call, which Object Types it can read, and which Actions it can execute. **Human-in-the-loop**: Actions can require approval before execution — the agent proposes, a human confirms. **Audit logging**: Every agent action and reasoning chain is captured in an immutable log.

AIP is model-agnostic, supporting **GPT-4/4o, Claude 3.5 Sonnet/Opus, Gemini Pro, Llama 3, Mistral**, and custom fine-tuned models. For government customers, models run entirely on-premises.

---

## 10. OSDK: auto-generated typed clients for external applications

OSDK (Ontology SDK) is Palantir's schema-driven code generator that produces **strongly-typed TypeScript or Python clients** specific to your Ontology. It is not a generic REST wrapper — it generates types that mirror your exact Object Types, Link Types, and Actions.

### Generation and usage

Using the `@osdk/cli`:

```bash
npx @osdk/cli generate \
  --foundry-url https://your-stack.palantirfoundry.com \
  --ontology-rid ri.ontology.main.ontology.xxx \
  --output-dir ./src/ontology
```

This produces typed interfaces, query helpers, and action callers for every ontology entity. A typical query:

```typescript
import { createClient } from "@osdk/client";
import { MaintenanceTicket } from "./ontology/objects/MaintenanceTicket";

const client = createClient(foundryUrl, ontologyRid, auth);

const tickets = await client(MaintenanceTicket)
  .where({ priority: "HIGH", status: { $ne: "CLOSED" } })
  .orderBy(t => t.createdDate.desc())
  .take(50);

for (const ticket of tickets.data) {
  console.log(ticket.ticketId);     // string - fully typed
  console.log(ticket.priority);      // "HIGH" | "MEDIUM" | "LOW"
}

// Traverse links
const asset = await tickets.data[0].$link.asset.get();

// Execute actions
await client(updateTicketStatus).applyAction({
  ticket: tickets.data[0].$primaryKey,
  newStatus: "IN_PROGRESS",
});
```

Authentication supports **OAuth 2.0 confidential client** (backend), **OAuth 2.0 public client** (browser SPA with redirect flow), and **bearer token** (development). The NPM ecosystem includes `@osdk/client`, `@osdk/api`, `@osdk/oauth`, `@osdk/cli`, and optionally `@osdk/react` for hooks. The open-source repo is `palantir/osdk-ts`.

---

## 11. Apollo: desired-state reconciliation across hundreds of environments

Apollo is Palantir's continuous delivery platform — it manages deployment of all Palantir products (Foundry, Gotham, AIP) across every customer environment. Its architecture follows a **hub-and-spoke model with pull-based reconciliation**.

### Architecture: control plane plus lightweight agents

The **Apollo Control Plane** (centralized, Palantir-hosted) tracks the desired state of every microservice across every environment — what version should run where, with what configuration. The **Apollo Agent** (deployed inside each customer environment) polls the control plane for desired state changes, downloads artifacts from registries, and orchestrates Kubernetes deployments to reconcile actual state with desired state. This pull-based model is essential for security — no inbound connections to customer networks are required.

### Progressive delivery, not simultaneous pushes

Apollo does not push identical updates to all environments at once. It uses **release channels** (canary → beta → stable → government-stable). New versions deploy first to Palantir's internal environments, then to canary customers, then progressively to stable channels. Each environment's agent independently polls and acts, enabling **parallel rollout** across hundreds of environments without sequential coordination.

Per Palantir's S-1 filing: **"over 3,500 updates across more than 300 independent environments in a single week"** and **"we typically ship software updates multiple times per day."** Individual microservices are independently versioned — a "release" is often a single service version bump, not a monolithic platform update. Apollo performs dependency resolution to ensure compatible versions deploy together.

### Air-gapped deployments use signed, encrypted bundles

For classified networks (up to TS/SCI), Apollo packages updates into **signed, encrypted deployment bundles** containing container images, Kubernetes manifests, and configuration. These bundles transfer across security boundaries via **government-approved cross-domain solutions** or physical media (the "sneakernet" approach). The agent operates with no outbound internet connectivity, and for the highest classification levels, **one-way data flow** is enforced — updates go in, but minimal or no telemetry flows out.

### Customer control, rollback, and configuration management

Customers control updates through environment policies: release channel subscription, automatic vs. manual approval gates, maintenance windows, and rollout speed. Government customers may run several versions behind commercial environments by design.

**Rollback** leverages the declarative model — the control plane sets the desired version back to the previous known-good state and agents reconcile. Automatic rollback triggers when health checks (Kubernetes probes plus custom application health endpoints) fail. Canary analysis can halt rollouts before they reach stable channels. All artifacts are immutable and versioned, ensuring rollback targets remain available. Configuration uses a **layered model** — base defaults, platform-level, environment-specific, and customer-specific overrides — with drift detection and remediation.

---

## Conclusion: what the developer experience actually feels like

Foundry's developer surface is simultaneously more constrained and more powerful than it first appears. The Ontology Manager enforces a disciplined modeling process — one backing dataset per Object Type, foreign-key-based links resolved at query time, and mandatory security marking propagation — that trades flexibility for consistency. Pipeline Builder and Code Repositories offer a genuine spectrum from no-code to full PySpark, with the `@transform_df` decorator being the API most developers live in daily. Workshop's variable-based inter-widget communication is elegant but requires thinking in terms of reactive data flow rather than imperative logic. AIP Logic's insight — use LLMs to generate code at development time, run deterministic functions at runtime — is architecturally significant and underappreciated. And Apollo's pull-based desired-state reconciliation solves the genuinely hard problem of deploying to air-gapped, classified environments at scale.

The key insight across all subsystems: **Foundry bets heavily on the Ontology as the single semantic layer**. Workshop widgets, AIP agents, OSDK clients, and Functions all consume typed Ontology objects — not raw datasets. This is both Foundry's greatest strength (consistency, security, composability) and its primary constraint (everything must be modeled as Object Types with backing datasets before it can be used operationally).