# Palantir Foundry Workshop: Concrete UI-Level Implementation Deep Dive

**Research Date:** 2026-02-17
**Sources:** Official Palantir documentation (docs.palantir.com), Palantir Developer Community (community.palantir.com), Palantir blog posts, Medium articles from practitioners, Palantir GitHub repositories, AIPCon presentations, Palantir Learn training materials.

---

## Table of Contents

1. [Workshop Widget Library -- Complete Inventory](#1-workshop-widget-library----complete-inventory)
2. [How Data Binding Works -- Variables, Object Sets, and the Ontology](#2-how-data-binding-works----variables-object-sets-and-the-ontology)
3. [How Action Buttons Work -- Action Types, Validation, and Confirmation](#3-how-action-buttons-work----action-types-validation-and-confirmation)
4. [Workshop vs Slate vs Quiver vs Contour -- Concrete Differences](#4-workshop-vs-slate-vs-quiver-vs-contour----concrete-differences)
5. [Workshop Application Examples -- Real Patterns and Demos](#5-workshop-application-examples----real-patterns-and-demos)
6. [The Low-Code vs Code Split](#6-the-low-code-vs-code-split)
7. [How AIP Assist Works Inside Workshop](#7-how-aip-assist-works-inside-workshop)
8. [Layout System, Routing, and State Management](#8-layout-system-routing-and-state-management)
9. [Key Limitations and Design Constraints](#9-key-limitations-and-design-constraints)
10. [Source URLs](#10-source-urls)

---

## 1. Workshop Widget Library -- Complete Inventory

Workshop widgets are the fundamental UI components. They are organized into five distinct categories in the official documentation. Every widget operates on the Ontology -- meaning it reads from (and sometimes writes to) Object Types, their properties, and their links. There is no concept of binding a widget directly to a raw dataset table; all data passes through the Object layer.

### 1.1 Core Display Widgets

These present Ontology object data directly to users:

| Widget | What It Does |
|---|---|
| **Object Table** | Tabular display of object data. Supports column selection (including time series columns), derived columns from Functions, sorting by one or multiple columns, configurable column widths and row heights, inline editing (cell-level writeback), row-selection events, and custom right-click row actions. This is the workhorse widget for operational applications. |
| **Object List** | Displays objects as a scrollable list of cards. Supports multi-select toggle, drag-and-drop reordering, configurable property display per card, and selected-object output variable for downstream consumption. |
| **Object View** | Renders a detail page for a single object. Can be configured as "full" (full-page) or "panel" (sidebar) view. Supports interface configuration to pass variables into the Object View's internal Workshop module tabs. Has a legacy mode for older tab configurations. |
| **Property List** | Displays properties of a single object in a key-value list format. |
| **Links** | Displays linked objects for a given object, showing the relationship graph in the Ontology. |
| **Object Set Title** | Displays a title summarizing the current object set (e.g., "47 Flights"). |

### 1.2 Visualization Widgets

These render data graphically or in specialized formats:

| Widget | What It Does |
|---|---|
| **Chart XY** | Bar, line, and scatter charts. Configured by adding "layers" -- each layer corresponds to an object set and a chart type. Bar chart layers support "Stacked," "Percentage," and "Grouped" display modes. |
| **Pie Chart** | Pie or donut chart. Groups objects by a specified property type and displays proportions. |
| **Vega Chart** | Fully customizable visualizations using the Vega and Vega-Lite JSON grammar. This is the escape hatch for any chart type that Chart XY and Pie Chart do not cover. |
| **Gantt Chart** | Displays objects as timed events in an interactive Gantt view. Multiple layers can aggregate temporal data across object types. Used for scheduling and resource allocation workflows. |
| **Map** | Geospatial visualization using MapboxGL rendering. Two configuration modes: (1) Local configuration (build map layers directly in the widget editor), or (2) Import Map Template (select a pre-built map template resource). Supports object set layers, clustering, heatmaps, and interactive selection. |
| **Pivot Table** | Dynamic grouping and aggregation of object data in tabular form. Supports row-level grouping by one or more properties, column-level grouping by up to one property, dynamic date/timestamp grouping (day, week, month, year), sorting, and aggregations (count, cardinality, average, max, min, sum). |
| **Metric Card** | A configurable KPI card highlighting key metrics. Often Function-backed to dynamically compute numerical or categorical values. Can show a single number, percentage, or status. |
| **Timeline** | Visualizes temporal data by rendering objects as events on a horizontal timeline. |
| **Stepper** | Tracks progress of a task through a set of steps, supporting both linear and non-linear progression. |
| **Status Tracker** | Displays statuses of a process on a timeline view -- similar to a workflow progress indicator. |
| **Markdown** | Renders Markdown text. Useful for instructions, descriptions, or context within a module. |
| **Media Preview** | Renders images, audio, video, and documents from a URL, Foundry RID, or Base64-encoded string. |
| **Spreadsheet Display** | Renders spreadsheet files from a media reference property on an object. |
| **Video Display** | Video playback widget (subsumed partially by Media Preview). |
| **Audio and Transcription Display** | Visualizes and allows playback of audio from a media reference property. Can display transcriptions alongside audio waveforms. |
| **PDF Viewer** | Renders PDFs with keyword search capabilities. |
| **Image Annotation** | Allows users to draw rectangles on images to annotate areas of interest. |
| **Resource List** | Displays various types of Foundry resources (e.g., files, datasets). |
| **Data Freshness** | Shows when data was last updated. |
| **Edit History** | Displays the history of edits made to objects. |
| **Action Log Timeline** | Shows a timeline of actions that have been executed. |
| **Linked Compass Resources** | Displays Compass resources linked to the current context. |
| **Free-form Analysis** | Enables ad-hoc analysis within the Workshop module. |

### 1.3 Filtering Widgets

These capture user input to narrow down object sets:

| Widget | What It Does |
|---|---|
| **Filter List** | The most feature-rich filter widget. Visualizes a high-level summary of object data and allows users to filter within that summary. Supports: keyword search across an object set, histogram visualization of property distributions, single- and multi-select dropdowns, distribution charts, single- and multi-date pickers, and timeline displays. Each property can be configured with its own visualization type. |
| **Object Dropdown** | Select a single object from a list. Search is performed on all string properties or specific configured properties. |
| **String Selector** | Displays string options as a dropdown, radio buttons, or checkboxes. |
| **Date and Time Picker** | Date/time input for filtering. |
| **Text Input** | Free-text input field. |
| **Numeric Input** | Numeric input field. |
| **Exploration Filter Pills** | Interactive filter pills that users can add/remove dynamically -- similar to "chip" filters in modern UIs. |
| **Exploration Search Bar** | Full-text search bar for exploring objects. |
| **Prominent Term** | Highlights prominent/frequent terms in an object set for quick filtering. |
| **User Select** | Selects a Foundry user (useful for assigning tasks). |

### 1.4 Event-Trigger and Navigational Widgets

These trigger actions, events, or navigation:

| Widget | What It Does |
|---|---|
| **Button Group** | The primary action trigger. Buttons can: execute an Action (writeback), trigger a Workshop event (page switch, variable set, overlay open/close), open a URL, or start an object set export. Three layout options. Display customization includes left/right icons, minimal styles, and tag styles. |
| **Inline Action** | A form widget that surfaces Action Type parameters directly inline. Supports both form and table interfaces. Live validation with custom error messages. Automatically generates UI based on the Action Type's parameter definitions (required fields, optional fields, validation rules). |
| **Media Uploader** | Allows users to upload media (images, documents) directly within the application. |
| **Audio Recorder** | Records audio directly within Workshop applications. |
| **Comments** | Adds a threaded comments section to a module. |
| **Tabs** | Navigation tabs for switching between content sections within a widget area. |

### 1.5 AIP (AI/LLM) Widgets

These embed AI capabilities directly in Workshop modules:

| Widget | What It Does |
|---|---|
| **AIP Agent** | Embeds an interactive AI assistant (chat interface) with enterprise-specific tools. Configured via AIP Agent Studio. Supports four tool types: Ontology semantic search (KNN or vector), Actions (for ontology edits), Workshop applications (with module interface variables), and Functions (AIP Logic or Ontology Functions). The agent can read and write Workshop variables, enabling it to interact with the rest of the application. |
| **AIP Analyst** | Embeds the AIP Analyst (more analytically focused) as a Workshop widget. Extensive configuration for data access, tool availability, and UI customization. |
| **AIP Generated Content** | Displays the output of an LLM call. Can render a streamed response (similar to a ChatGPT-style streaming display). Configurable with: output variable (string or object set), custom icon, button label, title, loading message, and spinner. Supports Direct-to-LLM mode, LLM-via-prompt-function mode, and AIP Logic function mode. |
| **AIP Interactive** | Interactive assistant widget for operational workflows within Workshop (precursor/variant of AIP Agent). |

### 1.6 Embedding Widgets

| Widget | What It Does |
|---|---|
| **Iframe** | Embeds any web application inside Workshop. Bidirectional communication via the `@osdk/workshop-iframe-custom-widget` npm package. Can read/write Workshop variables and execute Workshop events from the embedded app. |
| **Embedded Module** | Embeds another Workshop module inside the current one, with variable mapping between parent and child modules. |
| **Custom Widgets** | Developers can build entirely custom frontend components (using React, TypeScript, or any web framework) and embed them in Workshop. Custom widgets are packaged as "widget sets" (a Compass resource), each containing multiple widgets with independent entry points. They define parameters and events in a type-safe `main.config.ts` file (limit: 50 parameters, 50 events; IDs must be camelCase). |

---

## 2. How Data Binding Works -- Variables, Object Sets, and the Ontology

### 2.1 The Variable System

Variables are the central nervous system of a Workshop module. They control how data moves between widgets, how user interactions propagate, and how the application state is maintained.

**12 variable types exist:**

| Type | Description |
|---|---|
| **Object set** | One or more objects, filterable by properties or filter variables. This is the most commonly used type. |
| **Object set filter** | Property type/value pairs used to filter object sets. |
| **String** | Text content. |
| **Numeric** | Integers and floats. |
| **Boolean** | True/false. |
| **Date** | Date values. |
| **Timestamp** | Timestamp values. |
| **GeoPoint** | Geographic point data. |
| **GeoShape** | Geographic shape/polygon data. |
| **Array** | Holds arrays of boolean, date, numeric, geopoint, geoshape, string, timestamp, or struct values. |
| **Struct** | Composite types mapping string fields to values. |
| **Time series set** | Time series properties from single objects. |

### 2.2 How Variables Get Their Values

Variables can be defined via six mechanisms:

1. **Static**: Manually set a fixed value.
2. **Function**: Dynamically computed by a TypeScript Function on Objects (FOO).
3. **Object set aggregation**: Derived from aggregating an object set (count, sum, avg, etc.).
4. **Object property**: Tied to a single object's property value (e.g., the "name" of the currently selected object).
5. **Object set definition**: Defined by specifying an object type, property filters, and linked object traversals.
6. **Variable transformation**: A series of operations that reference other variables (pipeline-style).

### 2.3 How a Widget Connects to an Object Type

The concrete binding flow works as follows:

1. **Define an Object Set variable** -- specify the Object Type (e.g., "Flight"), optionally add property filters (e.g., "status = 'Delayed'"), and optionally traverse links (e.g., "Flights linked to Airport where Airport.region = 'US-East'").
2. **Assign the Object Set variable as the Input** to a widget -- e.g., set the Object Table's "Object Set" input to the `flightsObjectSet` variable.
3. **Configure property selectors** -- within the widget configuration panel, select which properties of the Object Type to display as columns (Object Table), card fields (Object List), or axis values (Chart XY).
4. **Configure Output variables** -- the widget emits outputs (e.g., "Selected Object" from Object Table row click, or "Filtered Object Set" from Filter List) that become input variables for downstream widgets.

### 2.4 Filtering Mechanics

Filtering works through **Object Set Filter variables**:

- A Filter List widget takes an Object Set as input and produces an Object Set Filter as output.
- That filter variable is applied to the same (or another) Object Set variable, which automatically narrows the objects displayed in downstream widgets.
- Multiple filter widgets can chain their filter variables onto the same Object Set.
- Property filters within the Filter List support: keyword search, histograms, single/multi-select dropdowns, distribution charts, date pickers, and timeline visualizations.

### 2.5 Lazy Evaluation and Recomputation

Variables compute **lazily in view mode** -- they only recompute when displayed by a visible widget. This prevents unnecessary computation for hidden tabs or collapsed sections.

Three recompute behaviors:
- **Automatic**: Recomputes whenever upstream dependencies change.
- **Event-triggered**: Only recomputes when explicitly triggered by an event (e.g., button click).
- **Load & event**: Recomputes on initial module load AND when triggered by an event.

### 2.6 The Variable Dependency Graph

Workshop provides a **visual dependency graph** in the editor that shows how variables connect to widgets and to each other, including current values and usage patterns. This is the primary debugging tool for data flow issues.

---

## 3. How Action Buttons Work -- Action Types, Validation, and Confirmation

### 3.1 Action Types in the Ontology

Action Types are defined in the Ontology (not in Workshop). They specify:
- **Parameters**: The inputs required (object references, strings, integers, object lists, etc.).
- **Logic**: What happens when executed (create object, modify properties, delete object, create/delete links).
- **Submission criteria**: Business rules that must be satisfied before submission (formerly called "validations").
- **Permissions**: Who can execute the action and on which objects.
- **Writeback dataset**: Where changes are persisted.

### 3.2 Binding an Action to a Button Group

In Workshop, the concrete steps are:

1. Add a **Button Group** widget to the module.
2. Open the button's configuration panel and go to the **"On click"** section.
3. Click **"Select an action..."** dropdown and filter to find the desired Action Type.
4. The system automatically displays all **Action parameters** defined in the Action Type.
5. For each parameter, configure:
   - **Default value** -- bind to a Workshop variable (e.g., bind "Selected Flight" parameter to the variable holding the currently selected object from an Object Table).
   - **Visibility**: `Visible` (user can modify), `Hidden` (completely hidden), or `Disabled` (read-only display).
   - **No default** -- leave empty for user input.

### 3.3 Inline Action Forms

The **Inline Action** widget provides a richer form experience:
- The form is **automatically generated** from the Action Type's parameter definitions. Because Actions are defined in the Ontology with typed parameters (required/optional, data types, validation rules), Workshop knows which fields to show, their types, and their constraints.
- Supports both **form layout** and **table layout** interfaces.
- Configuration can be done in Workshop or in the Ontology Manager.

### 3.4 Validation and Submission Criteria

Submission criteria encode business logic directly:
- Built by combining **conditions** on parameters, user context, and static values into logical statements.
- Example: "Confirm that the user has entered a valid three-character airport code" using a regex pattern condition.
- **Error messages**: Custom messages explain why submission fails (displayed as "1 issue" indicators next to the submit button).
- **Preview testing**: The Form tab in the editor provides a preview to test validation without actual submission.
- **API-level validation**: The Validate Action API endpoint checks whether an action can be run with given parameters, returning VALID or INVALID.

### 3.5 Submission Flow

When a user submits:
1. All inputs are validated against submission criteria.
2. If validation fails, error messages are displayed inline.
3. If validation passes, the action executes.
4. A **green confirmation toast** appears on success.
5. Object data updates to reflect the changes (writeback to the Ontology).
6. All actions are committed **transactionally** to the Ontology -- changes are reflected across all applications consuming the same objects.

### 3.6 Inline Edits

Beyond button-triggered actions, Workshop supports **inline cell-level editing** directly in the Object Table widget. This enables "spreadsheet-like" writeback where users click a cell, modify the value, and the change triggers an Action behind the scenes.

---

## 4. Workshop vs Slate vs Quiver vs Contour -- Concrete Differences

### 4.1 Decision Matrix

| Dimension | Workshop | Slate | Contour | Quiver |
|---|---|---|---|---|
| **Primary purpose** | Operational applications | Highly customized applications/dashboards | Tabular data analysis at scale | Object-centric analytics + time series |
| **Data source** | Ontology Objects only | Ontology Objects + raw datasets | Raw datasets (tabular) | Ontology Objects |
| **Code required** | None (no-code/low-code). TypeScript Functions for advanced logic. | HTML, CSS, JavaScript (Handlebars templating). Full custom code possible. | None (point-and-click). | None (point-and-click). |
| **Customization** | Moderate -- constrained to widget library + custom widgets. | Very high -- full HTML/CSS/JS control via Code Sandbox widget. | Low -- analysis-focused, not app-building. | Low -- analysis-focused, not app-building. |
| **Writeback/Actions** | Full support (Actions, Inline Actions, Inline Edits). | Supported via Ontology integration. | No writeback. | No writeback. |
| **Scale** | Designed for operational workflows at enterprise scale. | Designed for bespoke, pixel-perfect applications. | Optimized for very large datasets (millions+ rows). | Aggregations limited to ~50,000 rows. |
| **Maintenance cost** | Lower -- Palantir manages widget upgrades. | Higher -- custom code must be maintained. | Low. | Low. |
| **Mobile support** | Native mobile layouts and responsive design. | Limited (manual responsive CSS). | No mobile. | No mobile. |
| **Ontology required** | Yes -- all data must be mapped as Object Types. | No -- can work directly with raw datasets. | No -- works on raw tabular data. | Yes -- requires Ontology mapping. |
| **Embedding** | Can embed Slate, Quiver, Contour, custom React apps via Iframe. | Can embed Workshop via Iframe. | Embeddable in dashboards. | Embeddable in Workshop and Slate. |
| **Best for** | Inbox/triage apps, COPs, task management, operational dashboards. | Pixel-perfect dashboards, legacy apps requiring HTML control. | Ad-hoc data exploration, very large dataset analysis. | Object-centric analytics, time series analysis, sensor data. |
| **AIP integration** | Full (AIP Agent, AIP Analyst, AIP Generated Content widgets). | Limited (via Functions and Iframe). | Limited. | AIP Generate for adding/configuring cards. |

### 4.2 Concrete Differences in Practice

**Workshop** is the recommended starting point for new applications. It operates entirely through the Ontology, meaning you never write SQL or reference raw tables. The tradeoff is that all data MUST be mapped as Object Types first. Workshop's widget library covers ~90% of use cases; for the remaining 10%, you build Custom Widgets (React/TypeScript) or embed via Iframe.

**Slate** is the legacy application builder (still actively maintained). Its killer feature is the **Code Sandbox widget** -- a sandboxed environment where you write raw HTML, CSS, and JavaScript. You can use third-party JS libraries, build custom visualizations, and have pixel-level control. The limitation: network requests (fetch) are NOT supported in the Code Sandbox; all data must flow through configured Queries via SlateFunctions. CSS is static (determined at page load) -- you cannot dynamically change styles via Handlebars in CSS classes (only in HTML style attributes). Slate can work directly with raw datasets, bypassing the Ontology entirely.

**Contour** is a point-and-click analytical tool for tabular data at arbitrary scale. It excels when data is NOT in the Ontology, when you need to join multiple large datasets, or when performing exploratory analysis. It is not an application builder -- it is an analyst's tool that can produce dashboards.

**Quiver** is the Ontology-native analytics tool. It works with Objects, Links, and time series data natively (no joins needed -- the Ontology handles relationships). It includes a specialized time series library with sensor/signal processing functions. Aggregations are limited to ~50,000 rows. Quiver is particularly good for embedding analytical cards inside Workshop or Slate applications.

### 4.3 OSDK (Ontology SDK) -- The Fourth Option

Beyond Workshop and Slate, Palantir offers the **OSDK** for building completely custom applications:
- Write React applications using the Ontology SDK (TypeScript NPM package or Python Pip/Conda package).
- Full control over UI, routing, state management, and deployment.
- Can be hosted on Foundry or externally.
- Can be embedded inside Workshop via the Iframe widget with bidirectional variable/event communication.
- Best for: external-facing applications, applications requiring frameworks Workshop does not support, or teams that prefer standard React development.

---

## 5. Workshop Application Examples -- Real Patterns and Demos

### 5.1 Inbox / Task Triage Application

This is the canonical Workshop pattern. The official "Flight Alert Inbox" tutorial demonstrates:
- **Left panel**: Filter List widget with Prominent Terms, property histograms, and keyword search to narrow down Flight Alert objects.
- **Center**: Object Table displaying filtered alerts with columns for flight number, status, severity, airport, and time.
- **Right panel**: Object View showing the detail page for the currently selected alert.
- **Bottom**: Button Group with actions like "Acknowledge Alert," "Escalate," and "Dismiss."
- **Data flow**: Filter List output variable filters the Object Set; Object Table row selection sets a "selected object" variable; Object View and Button Group consume that variable.

Real-world use cases: warranty claims triage, alert investigation, order management, case management, patient intake.

### 5.2 Common Operational Picture (COP)

A multi-organization geospatial dashboard:
- **Map widget** as the central element, displaying objects geographically (e.g., retail store locations overlaid with regional COVID case data).
- **Metric Cards** showing top-line KPIs (total cases, revenue impact, store closures).
- **Chart XY** widgets showing trends over time.
- **Filter List** or **Exploration Filter Pills** for dynamic filtering by region, time period, or category.
- Official Palantir training course: "APPDEV 06: Building a Common Operating Picture in Workshop."

### 5.3 Workshop Design Hub (Marketplace Product)

Palantir offers a Marketplace product called the **Workshop Design Hub** with six high-quality example applications and templates. These serve as starting points for common patterns.

### 5.4 AIPCon 2024 Customer Demos

At AIPCon (June 2024), customers presented applications built with Foundry and AIP:
- **Charter Steel**: Manufacturing optimization.
- **Cleveland Clinic / Cone Health / Trios Health**: Healthcare operations.
- **Kinder Morgan**: Energy infrastructure management.
- **Wendy's QSCC**: Supply chain quality control.
- **Foxtrot + Aniko**: Retail operations.
- These demos showcased Workshop modules with embedded AIP Agents, Scenarios for what-if analysis, and multi-module operational workflows.

### 5.5 Scenario / What-If Analysis

Workshop includes a **Scenarios** feature for modeling:
- A Scenario is a "fork" of Ontology data generated by applying actions (optionally leveraging ML models via Functions).
- Users can modify input parameters, run a model, and see projected outcomes without affecting live data.
- Scenarios are applied **transactionally** -- either all actions apply or none.
- Integrated with Vertex (Palantir's modeling framework) for chaining multiple models together.

---

## 6. The Low-Code vs Code Split

### 6.1 What You Can Do Purely Visually (No Code)

- Add, arrange, and configure all 50+ built-in widgets via drag-and-drop and point-and-click.
- Define Object Set variables with property filters and link traversals.
- Create Filter variables and bind them to filtering widgets.
- Configure data flow between widgets via input/output variables.
- Set up pages, tabs, sections, overlays (drawers and modals).
- Bind Action Types to buttons with parameter defaults and visibility settings.
- Configure Inline Action forms with validation display.
- Set up Chart XY, Pie Chart, Pivot Table, Map, Gantt Chart layers.
- Configure Metric Cards with aggregation-based values.
- Define events (page switches, variable resets, overlay toggles, variable sets).
- Set up routing (URL-based state sharing).
- State saving and sharing.
- Configure Derived Properties (linked property lookups and column math) without code.
- Embed other Workshop modules with variable mapping.
- Set up AIP Agent, AIP Analyst, and AIP Generated Content widgets.

### 6.2 What Requires TypeScript Functions

- **Derived columns in Object Table** that require custom logic beyond simple property lookups or column math (e.g., concatenating values from transitively linked objects, complex calculations).
- **Function-backed Metric Cards** where the metric value requires computation beyond simple aggregation.
- **Complex Object Set definitions** that cannot be expressed through the point-and-click filter/link-traversal interface.
- **Function-backed Actions** that need to perform complex logic (e.g., creating multiple objects, conditional logic, calling external services).
- **Scenarios** that require model integration (wrapping a model in a Function).
- **Custom validation logic** beyond the built-in submission criteria templates.
- **AIP Logic** functions that orchestrate LLM calls with custom prompting and tool integration.

### 6.3 What Requires Full Custom Development (React/OSDK)

- **Custom widgets** that go beyond the built-in widget library (e.g., a specialized 3D visualization, a drag-and-drop Kanban board, a custom graph editor). These are built as React/TypeScript applications packaged as "widget sets."
- **Iframe-embedded applications** that need bidirectional communication with Workshop. Built using the `@osdk/workshop-iframe-custom-widget` npm package with the `useWorkshopContext` React hook.
- **External-facing applications** that need to run outside of Foundry (e.g., a customer portal).

### 6.4 TypeScript Functions Details

Functions are written in TypeScript within Foundry's Code Repositories:
- **TypeScript v2** (current): Uses Node.js runtime with first-class OSDK support.
- **TypeScript v1** (legacy): Functions defined in classes exported from `functions-typescript/src/index.ts`.
- Import object types from `@foundry/ontology-api` and function APIs from `@foundry/functions-api`.
- Functions can read object properties, traverse links, aggregate data, and trigger ontology edits.
- Functions are consumed in Workshop as: variable definitions, derived columns, Metric Card values, Action logic, or AIP Logic orchestration.

---

## 7. How AIP Assist Works Inside Workshop

### 7.1 AIP Assist (Platform-Level Help)

AIP Assist is NOT a Workshop app generator. It is a **contextual help sidebar** available across all Palantir platform applications:
- Trained on Palantir's platform documentation.
- Uses NLP and third-party LLMs (like GPT-4 or Claude) to parse user queries.
- Context-aware -- answers change depending on which application is active (Workshop, Pipeline Builder, etc.).
- In Workshop, you can add a **"Send to AIP Assist" event** to a Button Group that opens the AIP Assist sidebar with a pre-configured prompt. This prompt can use static text or dynamic variable values from the application.

### 7.2 What AIP Assist Does NOT Do (As of 2025)

AIP Assist does **not** generate Workshop modules, layouts, or widgets from natural language. It cannot auto-create an application from a description. It is a documentation-trained assistant, not a generative UI tool.

### 7.3 Generative Frontend -- In Development

A Palantir Developer Community thread (May 2025) reveals that a "Generative Frontend AIP Assist" feature has been proposed and is under early development:
- The goal is to convert natural language descriptions into working frontend interfaces (similar to Vercel's v0 or Replit).
- As of the thread closure, Palantir was building a related capability within **VS Code Workspaces** using the Continue extension, pre-configured with OSDK knowledge, powered by Claude Sonnet 3.5/3.7 for agentic frontend app creation.
- This targets OSDK React applications (not Workshop modules directly).
- Status: experimental / early development. Not generally available.

### 7.4 AIP Widgets IN Workshop (the actual AI integration)

The real AI integration in Workshop is through the AIP widgets described in Section 1.5:
- **AIP Agent widget**: Embeds a chat-based AI assistant directly in the application. The agent can query the Ontology, execute Actions, call Functions, and interact with Workshop variables. This is the flagship AI integration.
- **AIP Generated Content widget**: Displays LLM-generated text (streamed) based on a prompt function or direct LLM call. Used for dynamic summaries, recommendations, or explanations.
- **AIP Analyst widget**: Embeds the analytical AI with configurable data access and tools.
- **"Stream LLM response into variable" event**: A Workshop event that streams an LLM response directly into a string variable, which can then be displayed by any text-capable widget.

---

## 8. Layout System, Routing, and State Management

### 8.1 Layout Hierarchy

Workshop modules have a strict layout hierarchy:

```
Module
  -> Header (global navigation bar)
  -> Pages (multi-screen canvas)
      -> Sections (subdivisions of a page)
          -> Widgets (UI components)
          -> Layouts (nested section containers)
              -> Columns (vertical split)
              -> Rows (horizontal split)
              -> Tabs (tabbed content within a section)
  -> Overlays
      -> Drawers (slide-out panels from left or right, configurable width)
      -> Modals (centered overlays, configurable size)
```

### 8.2 Sizing System

Widget sizing supports three modes:
- **Auto (max)**: Height scales based on content.
- **Absolute**: Fixed pixel dimensions.
- **Flex**: Proportional scaling relative to sibling widgets.

### 8.3 Module Interface (Cross-Module Communication)

The **Module Interface** is the API for a Workshop module:
- Any variable can be added to the module interface by setting an external ID and enabling the module interface toggle.
- When module A embeds module B, module A maps its variables to module B's interface variables.
- Variables passed through the interface are **fully shared** between parent and child.
- Module interface variables can also be initialized from URL query parameters.

### 8.4 Routing

When routing is enabled:
- The current page ID is written to the URL.
- Module interface variables configured with "routing URL update behavior" are written as URL query parameters.
- Users can bookmark, share, and deep-link to specific application states.

### 8.5 State Saving

Workshop supports persistent state saving:
- Users can save the current state of all variables in a module.
- Saved states can be returned to later or shared with other users.
- Enables long-running workflows and collaboration.

### 8.6 Event System Details

Events are triggered by widget interactions and can perform these operations:

| Event Type | What It Does |
|---|---|
| **Open/Close overlay** | Opens or closes a specific drawer or modal. |
| **Switch to page** | Navigates to a different page in the module. |
| **Expand/Collapse/Toggle section** | Controls collapsible sections. |
| **Switch to tab** | Switches the active tab in a tabbed section. |
| **Reset variable value** | Restores a variable to its default value. |
| **Recompute variable** | Forces recomputation of a non-static variable. |
| **Set variable value** | Copies one variable's value to another. |
| **Stream LLM response into variable** | Streams an LLM output into a string variable. |
| **Send to AIP Assist** | Opens AIP Assist with a pre-configured prompt. |
| **Open Workshop module** | Opens another Workshop module in a new tab, passing variable values through the module interface. |

**Critical limitation**: Events do NOT wait for downstream computations of previous events to complete before executing the next event. When a "Set variable value" event fires, the source value copies immediately, but dependent variables may not have updated by the time the next event in the chain executes.

---

## 9. Key Limitations and Design Constraints

### 9.1 Data Limits

- **Export limit**: 200,000 objects for regular properties; 10,000 objects for function-backed derived columns.
- **Pivot Table groupings**: Fixed maximum number of groupings (workaround: "hidden groupings" that users can swap).
- **Quiver aggregation limit**: ~50,000 rows.

### 9.2 Design Best Practices (from official docs)

- Limit total actionable items to ~5 primary actions per screen.
- Maintain 30-40% whitespace.
- Limit visible components to no more than 10 in a single view.
- Avoid more than one iframe widget on-screen (memory/performance impact).

### 9.3 Mobile Constraints

- Collapsible sections are problematic on mobile (hard to tap, insufficient screen space).
- Recommended: Use **Flow layout** instead, showing a scrollable series of widgets.

### 9.4 Variable / Event Constraints

- Custom widgets: limit of 50 parameters and 50 events per widget.
- Parameter and event IDs must be in camelCase format.
- Events do not guarantee sequential execution of downstream computations.

### 9.5 Derived Properties Constraints

- Only supported in a subset of widgets (check documentation per widget).
- Computed at runtime, potentially increasing module load times.
- Object sets referencing derived properties cannot be saved.

### 9.6 Ontology Dependency

- All data in Workshop MUST be mapped as Ontology Object Types. There is no way to display raw dataset tables directly. This is a fundamental architectural decision, not a workaround-able limitation.

---

## 10. Source URLs

### Official Palantir Documentation

- [Workshop Overview](https://www.palantir.com/docs/foundry/workshop/overview)
- [Workshop Core Concepts: Widgets](https://www.palantir.com/docs/foundry/workshop/concepts-widgets)
- [Workshop Core Concepts: Variables](https://www.palantir.com/docs/foundry/workshop/concepts-variables)
- [Workshop Core Concepts: Events](https://www.palantir.com/docs/foundry/workshop/concepts-events)
- [Workshop Core Concepts: Layouts](https://www.palantir.com/docs/foundry/workshop/concepts-layouts)
- [Visualization Widgets Overview](https://www.palantir.com/docs/foundry/workshop/widgets-visualization)
- [Event-Trigger & Navigational Widgets](https://www.palantir.com/docs/foundry/workshop/widgets-event-navigational)
- [Filtering Widgets Overview](https://www.palantir.com/docs/foundry/workshop/widgets-filtering)
- [Object Table Widget](https://www.palantir.com/docs/foundry/workshop/widgets-object-table)
- [Object List Widget](https://www.palantir.com/docs/foundry/workshop/widgets-object-list)
- [Object View Widget](https://www.palantir.com/docs/foundry/workshop/widgets-object-view)
- [Chart XY Widget](https://www.palantir.com/docs/foundry/workshop/widgets-chart)
- [Pie Chart Widget](https://www.palantir.com/docs/foundry/workshop/widgets-pie-chart)
- [Vega Chart Widget](https://www.palantir.com/docs/foundry/workshop/widgets-vega-chart)
- [Gantt Chart Widget](https://www.palantir.com/docs/foundry/workshop/widgets-gantt-chart)
- [Map Widget](https://www.palantir.com/docs/foundry/workshop/widgets-map)
- [Pivot Table Widget](https://www.palantir.com/docs/foundry/workshop/widgets-pivot-table)
- [Metric Card Widget](https://www.palantir.com/docs/foundry/workshop/widgets-metric-card)
- [Filter List Widget](https://www.palantir.com/docs/foundry/workshop/widgets-filter-list)
- [Object Dropdown Widget](https://www.palantir.com/docs/foundry/workshop/widgets-object-dropdown)
- [String Selector Widget](https://www.palantir.com/docs/foundry/workshop/widgets-string-selector)
- [Button Group Widget](https://www.palantir.com/docs/foundry/workshop/widgets-button-group)
- [Inline Action Widget](https://www.palantir.com/docs/foundry/workshop/widgets-inline-action-form)
- [Tabs Widget](https://www.palantir.com/docs/foundry/workshop/widgets-tabs)
- [Media Uploader Widget](https://www.palantir.com/docs/foundry/workshop/widgets-media-uploader)
- [Audio Recorder Widget](https://www.palantir.com/docs/foundry/workshop/widgets-audio-recorder)
- [Spreadsheet Display Widget](https://www.palantir.com/docs/foundry/workshop/widgets-spreadsheet-display)
- [Audio and Transcription Display Widget](https://www.palantir.com/docs/foundry/workshop/widgets-audio-preview)
- [Media Preview Widget](https://www.palantir.com/docs/foundry/workshop/widgets-media-preview)
- [PDF Viewer Widget](https://www.palantir.com/docs/foundry/workshop/widgets-map-legacy)
- [AIP Agent Widget](https://www.palantir.com/docs/foundry/workshop/widgets-aip-agent)
- [AIP Analyst Widget](https://www.palantir.com/docs/foundry/workshop/widgets-aip-analyst)
- [AIP Generated Content Widget](https://www.palantir.com/docs/foundry/workshop/widgets-aip-generated-content)
- [AIP Interactive Widget](https://www.palantir.com/docs/foundry/workshop/widgets-aip-interactive)
- [Iframe Widget](https://www.palantir.com/docs/foundry/workshop/widgets-iframe)
- [Use Actions in Workshop](https://www.palantir.com/docs/foundry/workshop/actions-use)
- [Action Types Overview](https://www.palantir.com/docs/foundry/action-types/overview)
- [Action Types Submission Criteria](https://www.palantir.com/docs/foundry/action-types/submission-criteria)
- [Action Types Parameters](https://www.palantir.com/docs/foundry/action-types/parameter-overview)
- [Derived Properties in Workshop](https://www.palantir.com/docs/foundry/workshop/derived-properties)
- [Functions on Objects Overview](https://www.palantir.com/docs/foundry/workshop/functions-overview)
- [Functions Overview](https://www.palantir.com/docs/foundry/functions/overview)
- [TypeScript v2 Getting Started](https://www.palantir.com/docs/foundry/functions/typescript-v2-getting-started)
- [Custom Widgets Core Concepts](https://www.palantir.com/docs/foundry/custom-widgets/core-concepts)
- [Custom Widgets Development](https://www.palantir.com/docs/foundry/custom-widgets/development)
- [Custom Widgets Parameters and Events](https://www.palantir.com/docs/foundry/custom-widgets/parameters-and-events)
- [Custom Widgets Embedding in Workshop](https://www.palantir.com/docs/foundry/custom-widgets/embedding-in-workshop)
- [Module Interface](https://www.palantir.com/docs/foundry/workshop/module-interface)
- [Embedded Modules](https://www.palantir.com/docs/foundry/workshop/embedded-modules)
- [Workshop Routing](https://www.palantir.com/docs/foundry/workshop/routing)
- [Workshop State Saving](https://www.palantir.com/docs/foundry/workshop/state-saving)
- [Object Set Filter Variables](https://www.palantir.com/docs/foundry/workshop/object-set-filter-variables)
- [Scenarios Overview](https://www.palantir.com/docs/foundry/workshop/scenarios-overview)
- [Scenarios Core Concepts](https://www.palantir.com/docs/foundry/workshop/scenarios-concepts)
- [Workshop Example Applications](https://www.palantir.com/docs/foundry/workshop/example-applications)
- [Application Design Best Practices](https://www.palantir.com/docs/foundry/workshop/application-design-best-practices)
- [Application Design FAQs](https://www.palantir.com/docs/foundry/workshop/application-design-faqs)
- [Workshop Getting Started](https://www.palantir.com/docs/foundry/workshop/getting-started)
- [Workshop Mobile Design](https://www.palantir.com/docs/foundry/workshop/mobile-design)
- [App Building Overview](https://www.palantir.com/docs/foundry/app-building/overview)
- [Application Reference](https://www.palantir.com/docs/foundry/getting-started/application-reference)
- [Ontology Overview](https://www.palantir.com/docs/foundry/ontology/overview)
- [Ontology Applications](https://www.palantir.com/docs/foundry/ontology/applications)
- [Contour Overview](https://www.palantir.com/docs/foundry/contour/overview)
- [Types of Analysis](https://www.palantir.com/docs/foundry/analytics/types-of-analysis)
- [AIP Features](https://www.palantir.com/docs/foundry/aip/aip-features)
- [AIP Assist Overview](https://www.palantir.com/docs/foundry/assist/overview)
- [AIP Assist Application Integrations](https://www.palantir.com/docs/foundry/assist/application-integrations)
- [AIP Agent Studio Overview](https://www.palantir.com/docs/foundry/agent-studio/overview)
- [OSDK React Applications Overview](https://www.palantir.com/docs/foundry/ontology-sdk-react-applications/overview)
- [Ontology SDK Overview](https://www.palantir.com/docs/foundry/ontology-sdk/overview)

### Palantir Community and Blog

- [AIPCon Demo Expo (June 2024)](https://community.palantir.com/t/aipcon-demo-expo/338)
- [Generative Frontend AIP Assist Discussion](https://community.palantir.com/t/generative-frontend-aip-assist/3402)
- [New to Foundry Community Thread](https://community.palantir.com/t/new-to-foundry-what-helped-you-learn-it-quickly/4526)
- [How to Create Custom Widget Discussion](https://community.palantir.com/t/how-to-create-a-custom-widget-for-workshop/2182)
- [Palantir Blog: AIPCon Demos Part 1](https://blog.palantir.com/inside-the-aipcon-8-demos-redefining-the-future-of-enterprise-ai-a0a740fe44ce)
- [Palantir Blog: AIPCon Demos Part 2](https://blog.palantir.com/inside-the-aipcon-8-demos-transforming-manufacturing-insurance-and-construction-2ef01d53ea96)
- [AIPCon 4 Customer Demos](https://www.palantir.com/aipcon4/demos/)

### GitHub and NPM

- [workshop-iframe-custom-widget (GitHub)](https://github.com/palantir/workshop-iframe-custom-widget)
- [@osdk/workshop-iframe-custom-widget (NPM)](https://www.npmjs.com/package/@osdk/workshop-iframe-custom-widget)

### Learning and Training

- [Palantir Learn](https://learn.palantir.com/)
- [APPDEV 06: Building a Common Operating Picture](https://learn.palantir.com/appdev-06)
- [Application Developer Training Track](https://learn.palantir.com/page/training-track-application-developer)
- [Deep Dive: Building Your First Application](https://learn.palantir.com/deep-dive-building-your-first-application)
- [Build with AIP](https://build.palantir.com/)

### Third-Party Articles

- [Mastering Palantir Foundry Workshop (Medium / D-ONE.AI)](https://medium.com/d-one/mastering-palantir-foundry-workshop-building-insightful-dashboards-a5697adeb17d)
- [Palantir: Slate vs Workshop vs OSDK (Medium / Chanon Roy)](https://chanonroy.medium.com/palantir-slate-vs-workshop-vs-osdk-2467028567a8)
- [Palantir Foundry 101: Intro to Contour (Medium / Ontologize)](https://medium.com/ontologize/palantir-foundry-101-intro-to-contour-for-data-analysis-fb486ea1d959)
- [Palantir Foundry AIP (Unit8)](https://unit8.com/resources/palantir-foundry-aip/)
- [Building a Trail Running Demo in Foundry (Medium / Adam Casey)](https://medium.com/@adam-casey/building-a-trail-running-demo-in-palantir-foundry-14c684f0af7c)
