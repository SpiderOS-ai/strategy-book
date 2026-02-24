# Palantir's 90-day pilot deployment, reverse-engineered

Palantir's "Acquire" phase follows a repeatable but adaptive 12-week playbook where a small embedded team — typically **1 Deployment Strategist and 2–4 Forward Deployed Engineers** — transforms a signed pilot contract into a production system running on Foundry. The methodology prioritizes demonstrating undeniable value within weeks, not months, using rapid prototyping grounded in an ontological data model. Palantir invests heavily upfront (often at negative contribution margin) because successful pilots reliably expand: dollar-based net retention consistently exceeds **115–120%**, and top-20 customers average **$33M+ in annual revenue**. The entire process is designed around one principle Nabeel Qureshi articulated from his 8 years as an FDE: solve a "hair on fire" problem first, then expand from that beachhead.

---

## Phase 1: Discovery and data collection (weeks 1–3)

### Week 1 — Stakeholder mapping and immersion

The Deployment Strategist (DS) leads the engagement's first days. The DS and FDE team conduct **10–30 stakeholder interviews** across the organization in the first two weeks, starting with three tiers: executives who sponsor the engagement, middle managers who own operational processes, and frontline operators who touch data daily. The interview protocol follows a semi-structured format, not a rigid questionnaire. Core questions revolve around five themes: *What decisions do you make every day? What information do you need to make them? Where does that information come from? What's broken about that process? What would you do if you had perfect information?*

FDEs physically shadow end users during this week — walking the factory floor, sitting beside analysts at trading desks, observing hospital ward rounds. **Time splits roughly 60% interviewing to 40% observing.** The observation is critical because, as former FDEs consistently report, the "real" process almost always differs from the documented process. An FDE at a manufacturing client might discover that operators bypass the ERP system entirely, tracking critical data in personal spreadsheets. That gap between official workflow and actual workflow is where the highest-value use cases hide.

**Artifacts produced in week 1:**
- Stakeholder map documenting names, roles, influence level, data ownership, and disposition toward the project (champion, neutral, or hostile)
- Initial process flow diagrams (typically informal — whiteboard-style swimlane diagrams, not formal BPMN)
- Data landscape sketch identifying known systems, databases, APIs, and file stores
- Meeting notes from every stakeholder interview

**Meeting cadence established:**
- **Daily internal standup** (15 min) — Palantir team only, to sync on findings and blockers
- **2–3 working sessions per week** with customer analysts and operators
- **Weekly executive update** — brief, impact-focused, typically 30 minutes with the sponsor

### Week 2 — Data discovery and the access negotiation

FDEs shift focus to cataloging data sources with precision. They build a **data inventory** documenting every source system: database type, owner, approximate volume, refresh frequency, known quality issues, and access mechanism. This inventory typically identifies **15–40 data sources** in a mid-size deployment, though only 3–10 will be connected during the pilot.

The data quality assessment follows a practical rubric, not a formal scoring framework. FDEs evaluate each source on four dimensions: **completeness** (how many nulls and gaps), **freshness** (how often updated, how stale), **consistency** (do definitions match across systems), and **accessibility** (can we actually get to it). Sources are triaged into three buckets: connect now, connect later, and not worth connecting.

**Data access politics** represent the single most common blocker in week 2. Data owners — particularly in IT departments — are frequently protective of their databases and hostile to outsiders requesting access. The FDE negotiation playbook uses several tactics in escalating order:

- **Start with data already accessible** — public APIs, shared drives, exported CSVs — to build a working prototype without requiring anyone's permission
- **Demonstrate value to the gatekeeper** — show them how the integrated platform could help *their* team, not just the sponsor's team
- **Leverage executive sponsorship** — have the senior champion mandate access when relationship-building fails
- **Work around entirely** — find alternative data sources or have executives override restrictions

The Deployment Strategist manages the political dimension while FDEs handle the technical assessment. This division is critical: FDEs should never be in the position of arguing for data access in a meeting — that's the DS's job, armed with executive air cover.

### Week 3 — Use case prioritization and environment setup

By week 3, the team has enough context to prioritize. Use case selection follows a **2×2 framework** (though not always formalized into a matrix): the vertical axis measures **business value** (pain intensity × frequency × number of affected users), while the horizontal axis measures **feasibility** (data readiness × technical complexity × time to demonstrate).

The team applies what former FDEs call the **"hair on fire" test**: is someone losing sleep over this problem? The ideal first use case sits at the intersection of four criteria:

- **High pain**: A real operational problem costing time, money, or risk daily
- **Data availability**: The required data exists and is accessible (or can be made accessible quickly)
- **Executive sponsorship**: Someone powerful enough to clear obstacles cares about this specific outcome
- **Quick demonstration**: A working prototype can be shown within 2–3 weeks

FDEs specifically avoid use cases requiring massive upfront data integration, politically sensitive data that would stall the project, or problems that require ML model development before showing any value. The goal is to narrow to **1–3 use cases**, typically one primary and one secondary.

Simultaneously, the Forward Deployed Infrastructure Engineer (FDIE), if assigned, works on environment setup. For cloud-hosted Foundry (SaaS), this involves configuring the Foundry enrollment, setting up user accounts, and establishing network connectivity. For on-premise deployments (common in defense and healthcare), the FDIE installs Foundry on customer infrastructure — a process that can take 1–2 weeks depending on the environment's complexity and security requirements.

**Key artifacts by end of week 3:**
- Prioritized use case document with clear success criteria for each
- Data inventory with access status and quality assessment
- Process flow diagrams for target use cases (more detailed than week 1)
- Foundry environment provisioned and ready for data ingestion
- Initial project plan with milestones through week 12

**Decision point:** The use cases selected in week 3 shape the entire pilot. This is the highest-leverage decision in the 90-day engagement.

---

## Phase 2: Ontology design and data integration (weeks 2–6)

### The ontology design process (weeks 3–4)

The ontology is Palantir's core intellectual differentiator — a semantic layer mapping real-world entities into Object Types with Properties and Links. The design process is deeply collaborative, driven by domain understanding rather than database schema.

**How FDEs decide what becomes an Object Type:** The governing question is *"What entities do users think about and search for in their daily work?"* Each real-world entity that users reference becomes an Object Type. In a hospital deployment, these might be Patient, Ward, Bed, Staff Member, Test Result, and Equipment. In supply chain: Supplier, Part, Purchase Order, Shipment, Factory, and Production Line. In defense: Vehicle, Mission, Personnel, Base, and Supply Request.

**The Object Type creation process in Ontology Manager:**
1. Navigate to Ontology Manager in Foundry
2. Create a new Object Type with a display name (PascalCase, singular: `WorkOrder`, `FlightPath`)
3. Select the **backing dataset** — the Foundry dataset whose rows represent instances of this type
4. Define the **primary key** — the column uniquely identifying each instance
5. Map dataset columns to **Properties** with typed definitions (String, Integer, Double, Boolean, Date, Timestamp, GeoPoint, GeoShape, Array, Attachment, Timeseries)
6. Set the **title property** — which property displays as the object's label across UIs
7. Configure **searchable**, **filterable**, and **sortable** flags on properties
8. Define **Link Types** connecting Object Types: one-to-one, one-to-many, or many-to-many, backed by foreign key relationships
9. Optionally create **Interface Types** — abstract contracts that multiple Object Types implement (e.g., an "Asset" interface shared by Vehicle and Equipment)

**Naming conventions** follow consistent patterns: Object Types in PascalCase singular (`Customer`, `WorkOrder`), Properties in camelCase (`firstName`, `orderDate`), Link Types as descriptive relationships (`customer_orders`, `flight_departsFrom`), Action Types as verb-noun (`CreateWorkOrder`, `AssignTechnician`).

**Iteration count:** FDEs typically go through **3–5 ontology design iterations** before the schema stabilizes for the first use case. The initial design starts minimal — **5–10 core Object Types** — and grows as additional use cases are added. Mature deployments can reach 50–100+ Object Types. Client validation happens through working sessions where FDEs display the ontology visually and ask: "Does this match how you think about your world?"

### Data pipeline construction (weeks 3–5)

Data pipelines in Foundry follow a **three-layer architecture**: raw → clean → semantic. Raw datasets mirror source systems exactly. Clean datasets apply transformations (deduplication, type casting, null handling). Semantic datasets back the Ontology's Object Types.

**Pipeline Builder** (no-code, visual) handles most transformations during pilots. The step-by-step process:
1. Add input dataset nodes to the visual canvas
2. Apply transforms: Join (inner, left, right, full outer), Filter, Aggregate (sum, count, avg, min, max), Add/Rename/Drop/Cast columns, Union, Pivot/Unpivot, Window functions, Deduplicate
3. Preview data at any node before building
4. Configure the output dataset
5. Set the schedule: manual, cron-based (hourly, daily, weekly), or triggered (builds when upstream datasets change)
6. Choose build type: snapshot (full replacement) or incremental (process only new/changed data)

**Code Repositories** (PySpark/Python) handle complex transformations. The transform API uses decorators:

```python
@transform_df(
    Output("/path/to/output"),
    source=Input("/path/to/input")
)
def compute(source):
    return source.filter(source.status == "active")
```

Testing uses pytest with Foundry's `TransformTestContext` for mock inputs/outputs. Every commit triggers automated checks — linting, type checking, and unit tests — through Foundry's built-in CI/CD. Branch-based development enables testing pipeline changes before merging to production.

**Typical pilot pipeline count:** **10–30 automated data pipelines** built during a 90-day engagement, connecting 3–10 data sources.

### Data source connection (weeks 2–4, overlapping)

**Connector setup process:** Foundry's Data Connection application supports JDBC databases (PostgreSQL, MySQL, SQL Server, Oracle, Snowflake, Redshift, BigQuery), file systems (S3, Azure Blob, GCS, SFTP), APIs (REST, OData), SaaS applications (Salesforce, SAP, Workday, ServiceNow, JIRA), and streaming sources (Kafka, Kinesis).

For on-premise sources behind firewalls, the process involves:
1. **Install the Data Connection Agent** (JAR file or Docker container) on a server with network access to the source system
2. **Register the agent** in Foundry — the agent connects *outbound* over HTTPS, requiring no inbound firewall rules
3. **Configure the source** — connection parameters, credentials (encrypted in Foundry)
4. **Define syncs** — map source tables to Foundry datasets with snapshot, incremental, or append modes
5. **Schedule and monitor** — configure sync frequency and health alerts

For cloud-to-cloud connections (Snowflake, BigQuery), direct connectors eliminate the agent requirement.

**Time to connect one source:** Straightforward database connections take **1–3 days** including testing. Complex sources with firewall issues, VPN requirements, or schema discovery challenges can take **1–2 weeks**. Common failure modes include firewall blocks (most frequent), credential rotation breaking syncs, schema changes in source systems, and API rate limiting.

---

## Phase 3: Actions, security, and application building (weeks 4–10)

### Action Type design (weeks 5–7)

Action Types transform Foundry from a read-only analytics platform into an operational system that writes back to the real world. FDEs identify which user actions to model by observing what operators *do* after analyzing data — assign a technician, close a ticket, approve an order, escalate an issue.

**Configuration in Ontology Manager:**
1. Create a new Action Type with verb-noun naming (`AssignTechnician`)
2. Define **parameters** — typed inputs the user provides (Object reference, String, Integer, Date)
3. Define **rules** — the mutations triggered: Create Object, Modify Object, Delete Object, Create/Delete Link
4. Configure **validation rules** — conditions enforced before execution (required fields, range checks, uniqueness constraints, cross-parameter validation)
5. Set **side effects** — webhooks calling external APIs, notifications, or Foundry Function execution
6. Configure **permissions** — who can execute this action type
7. Define **submission mode** — synchronous (immediate) or asynchronous (queued)

**Writeback mechanism:** Actions write to an append-only **Edits dataset** (transaction log). The Ontology merges edits with backing datasets to present current state in real-time. Periodic pipeline reconciliation ensures edits are materialized back to backing datasets. Webhooks enable external system integration — triggering Slack notifications, updating external databases, or calling downstream APIs.

### Security configuration (weeks 5–7)

Security in Foundry operates through four layered mechanisms:

**Projects** serve as the primary organizational unit. Resources (datasets, pipelines, applications) are placed in Projects, and users receive roles: Viewer, Editor, or Owner. Project membership controls discoverability and access.

**Markings** provide classification-based access control. A marking is a label (e.g., "CONFIDENTIAL," "PII," "ITAR") applied at the dataset, column, row, or cell level. Users must hold the corresponding marking grant to see marked data. Markings **propagate automatically through pipelines** — if an input dataset carries a "PII" marking, all derived datasets inherit it.

**Row-level security** restricts which object instances a user can see based on policy rules evaluating user attributes against row properties. Example: "Users in group 'US-Team' can only see rows where region equals 'US'."

**Property-level security** hides specific Object Type properties from users lacking appropriate markings — sensitive fields appear as null or hidden.

**Testing process:** Foundry provides a **"View as User"** capability allowing administrators to verify what a specific user can and cannot see, enabling systematic permission testing before go-live.

### Application building in Workshop (weeks 5–9)

Workshop is where the pilot becomes tangible to end users. It's Foundry's no-code application builder, and it's where FDEs spend the most visible hours during a pilot.

**The Workshop widget library** includes:
- **Display:** Object Table, Object List, Card, Details Panel, Metric/KPI Card, Status Indicator
- **Visualization:** Charts (line, bar, area, scatter, pie, heatmap, treemap, funnel), Map (Mapbox-based with clustering and heatmaps), Timeline, Gantt, Graph/Network visualization
- **Input:** Button, Text Input, Number Input, Dropdown/Multi-select, Date Picker, Slider, Toggle, File Upload, Search Bar
- **Layout:** Container, Tabs, Accordion, Grid, Modal/Dialog
- **Advanced:** HTML/iFrame embed, Form (auto-generated from Action Type parameters)

**The application-building process:**
1. Create a new Workshop module
2. Define **Object Sets** — filtered, queried collections of Ontology objects (by type, property filters, link traversal)
3. Design the **layout** with containers, tabs, and grid widgets
4. Place **display widgets** and bind them to Object Sets (e.g., an Object Table bound to "Active Work Orders")
5. Configure the **variable system** — Workshop's reactive state model where widget interactions (row selection, button clicks) update variables that cascade to other widgets
6. Bind **Action Types** to buttons — mapping action parameters to widget inputs or variables
7. Configure **conditional visibility** — show/hide widgets based on variable values
8. Set **permissions** — who can view and use the application
9. Publish and iterate

**Decision criteria between application tools:**
- **Workshop** (default choice): No-code, ontology-native, fastest to build, covers 80%+ of operational application needs
- **Slate**: Custom HTML/CSS/JavaScript for pixel-perfect UIs, complex D3.js visualizations, or requirements that exceed Workshop's widget library
- **Quiver**: Ontology-native analytics dashboards for business users who need self-service charting and exploration without building full applications

FDEs iterate on Workshop applications **daily** during the build phase, showing users working prototypes and rebuilding based on feedback. A typical pilot produces **3–10 Workshop applications** and **5–15 operational dashboards**. The number of UI iterations before stabilization ranges from **5–10 per application**, with the first working prototype typically available within 2–3 days of beginning application development.

---

## Phase 4: User training and go-live (weeks 8–12)

### Training methodology (weeks 8–10)

FDEs transition from "builder" to "coach" in the final phase. Training follows a tiered model:

**Power users / citizen developers** receive the deepest training — **8–16 hours** over multiple sessions. These individuals learn to build their own Workshop applications, modify pipelines, and extend the Ontology. FDEs identify power users early (typically week 4–5) based on technical aptitude, domain expertise, and enthusiasm. Power users become the nucleus of the customer's internal Foundry team.

**Standard operators** receive **2–4 hours** of application-specific training, focused on using the Workshop applications built for their workflow. Training uses a combination of classroom walkthroughs, one-on-one sessions, and written guides.

**Executives** receive **30–60 minutes** of dashboard orientation — enough to interpret Quiver dashboards and Workshop KPI views independently.

**Training materials produced:**
- User guides for each Workshop application (screenshots, step-by-step workflows)
- Ontology documentation (Object Type catalog with descriptions, property definitions, and relationship diagrams)
- Pipeline runbooks (data refresh schedules, troubleshooting for common failure modes)
- Video walkthroughs for common tasks (optional, depending on customer preference)
- "Playbook" templates showing patterns that power users can replicate

**Training format** is overwhelmingly hands-on. FDEs use **pair-programming sessions** as the primary knowledge transfer mechanism — sitting beside a customer engineer and building something together, rather than lecturing. "Office hours" where FDEs are available for ad-hoc questions supplement formal sessions.

### Go-live process (weeks 10–11)

Go-live follows a structured checklist, though Palantir does not publish a formal public version. Key elements include:

**Pre-go-live validation:**
- All data pipelines running on schedule with health checks passing (row count ranges, null rate thresholds, schema validation)
- Security configuration tested via "View as User" for every role
- Action Types validated — all validation rules and writeback mechanisms functioning
- Workshop applications tested with real users in pilot mode
- Monitoring dashboards configured with alerts for pipeline failures, data quality anomalies, and application errors

**Transition management:** The shift from FDE-operated to client-operated happens gradually, not as a hard cutover. During weeks 10–12, FDEs systematically reduce their involvement: first they stop building new features, then they stop fixing routine issues (directing client engineers to do it), and finally they shift to advisory check-ins rather than daily embedded work.

**Post-go-live support** typically involves:
- **Weeks 11–12:** FDE remains available on-site or remotely for escalations
- **Months 2–3 post-pilot:** Transition to Palantir's standard customer success model with periodic check-ins
- **Ongoing:** Platform updates managed through Apollo (Palantir's continuous deployment infrastructure)

### The executive review and expansion case (week 12)

The final week centers on the **executive review** — a formal presentation to the client's senior leadership. The Deployment Strategist leads this presentation, with FDE support for technical questions.

**Presentation structure:**
1. **Problem statement** — the operational challenges identified in discovery
2. **Solution demonstration** — live walkthrough of Workshop applications showing integrated data and operational workflows
3. **Impact metrics** — quantified results from the pilot period (time saved, cost avoided, decisions improved, risks mitigated)
4. **Adoption metrics** — daily/weekly active users, number of workflows replaced, data sources unified
5. **Expansion roadmap** — identified additional use cases, departments, and data sources for the next phase
6. **Business case for expansion** — projected ROI of expanding from 1–3 pilot use cases to 10–20+ enterprise use cases

**Success KPIs** typically tracked during the pilot:
- **Time-to-decision**: Measurable reduction in time from data availability to operational action
- **User adoption**: Daily active users of Workshop applications versus target
- **Data unification**: Number of previously siloed sources now connected
- **Process displacement**: Number of manual processes (spreadsheets, email chains) replaced
- **Efficiency gain**: Hours saved per week per user on specific workflows — the most persuasive metric, often expressed as something like "report generation reduced from 8 hours to 15 minutes"

The expansion document maps the path from pilot (negative margin for Palantir) to full deployment. Palantir's S-1 filing explicitly described this model: pilot contracts are often loss-making by design, because the **Expand** phase (months 3–12, breakeven margin) and **Scale** phase (year 2+, **55–65%+ contribution margin**) generate the returns.

---

## How AIP Bootcamps have accelerated the Acquire phase

Since 2023, Palantir has layered **AIP Bootcamps** on top of the traditional FDE model. These intensive **2–5 day workshops** compress the discovery-to-prototype cycle dramatically. Customers bring their own data and problems; Palantir engineers help build working prototypes on Foundry with AIP (the AI/LLM layer) in days rather than weeks. By Q3 2024, Palantir had completed **560+ bootcamps**, and the company described them as its most efficient customer acquisition mechanism ever. Bootcamps don't replace the 90-day pilot — they serve as a pre-pilot proof of concept that accelerates the Acquire phase by demonstrating value before the formal engagement begins, effectively compressing stakeholder buy-in from weeks to days.

AIP itself extends the Ontology with LLM capabilities: **AIP Logic** defines prompt-powered functions operating on Ontology objects, **AIP Assist** provides a copilot-style natural language interface within Workshop applications, and **AIP Workflows** enable multi-step agentic processes with human-in-the-loop approval. Critically, AIP respects all existing security constraints — the LLM context is scoped to what the user has permission to see.

---

## Team composition and role boundaries shape every phase

The deployment team's structure explains why the process works. Each role has a distinct function:

**The Forward Deployed Engineer** owns the technical stack: data pipelines, ontology design, Workshop applications, and code. FDEs are generalists who can write PySpark transforms in the morning and demo a Workshop application to a VP in the afternoon. They are embedded directly with end users — not IT — which is critical for understanding real workflows. FDEs typically work **50–70 hour weeks** during pilots, with **50–80% travel** to customer sites.

**The Deployment Strategist** owns the business relationship: stakeholder management, use case prioritization, executive communication, and the expansion roadmap. Many DS hires come from McKinsey, BCG, or Bain. The DS handles organizational politics so FDEs can focus on building. The DS runs discovery workshops and executive briefings; the FDE runs technical working sessions and user demos.

**The Solutions Architect** provides architectural guidance across multiple accounts — designing integration strategies, reviewing ontology models, and bridging FDE teams with client engineering organizations. Not every pilot gets a dedicated SA.

**The Forward Deployed Infrastructure Engineer** manages platform deployment for on-premise or air-gapped environments, handling Kubernetes clusters, networking, storage, and compliance requirements. FDIE involvement varies: SaaS deployments need minimal FDIE time, while classified government deployments may require a dedicated FDIE throughout.

The standard pilot team of **1 DS + 2–4 FDEs** scales up for strategic accounts. Large engagements (NHS, Army Vantage, BP) have fielded teams of 10–20+ people. The team's cost is front-loaded into Palantir's cost of revenue, which is why the Acquire phase runs at negative margin.

---

## Conclusion

The 90-day pilot is not a sales exercise — it is an engineering methodology optimized for speed-to-value in complex data environments. Three design choices make it work. First, FDEs embed with operators, not IT, which means the ontology reflects how the business actually works rather than how databases are structured. Second, the three-layer pipeline architecture (raw → clean → semantic) allows FDEs to show working prototypes from messy data within days, not months. Third, Workshop's no-code binding to the Ontology means the UI evolves as fast as the data model — FDEs iterate on applications daily based on direct user feedback, producing 3–10 working applications in a typical pilot.

The methodology's most underappreciated element is its political architecture. The DS manages executives and gatekeepers while FDEs build trust with frontline users, creating simultaneous top-down mandate and bottom-up demand. When the week-12 executive review arrives, the expansion case writes itself: the users are already dependent on the applications, the data is already flowing, and the question shifts from "should we continue?" to "how fast can we expand?" That conversion dynamic — reflected in Palantir's 115–120% net dollar retention rate — is the business consequence of a deployment methodology that gets the engineering and the politics right in 90 days.