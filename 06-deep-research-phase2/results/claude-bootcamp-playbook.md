# Palantir's AIP Bootcamp playbook reverse-engineered

**Palantir's AIP Bootcamp is a free, five-day, high-intensity engagement where Forward Deployed Engineers co-build working AI prototypes on a prospect's own data — compressing what traditionally took six-to-nine months of enterprise sales into a single week.** Since launching in mid-2023, Palantir has executed over **1,400 bootcamps** (as of Q3 2024), making it the single most important go-to-market motion in the company's history. The bootcamp model has driven US commercial revenue growth from 23% year-over-year to over 60%, fundamentally reshaping how enterprise AI software is sold. What follows is the most granular operational reconstruction possible of the exact playbook an FDE team follows — from initial prospecting through post-bootcamp conversion.

---

## The pre-sales engine that fills the bootcamp pipeline

### Prospecting and qualification

Palantir's bootcamp funnel is fed through a mix of inbound and outbound channels. Inbound demand surged after AIPCon 2023 and 2024, where live demos and customer testimonials created significant interest. Outbound prospecting is led by **Account Executives (AEs)** who target companies fitting Palantir's ideal customer profile: organizations with **large, messy, multi-system data estates** and operationally complex workflows where AI-driven decision support would yield measurable ROI. Industries with the strongest fit include manufacturing, healthcare/life sciences, energy, logistics, financial services, and defense-adjacent commercial companies.

The qualification framework evaluates prospects on several dimensions. **Data readiness** is paramount — the prospect must have identifiable, accessible datasets (even if messy) that can be ingested within weeks. **Executive sponsorship** is non-negotiable; a C-level or VP-level champion must be willing to attend the Day 5 demo and make funding decisions. **Operational pain** must be concrete and quantifiable — not vague "digital transformation" aspirations but specific workflows where minutes, dollars, or errors can be measured. Finally, **technical willingness** is assessed: the company must have staff (data engineers, analysts, or IT) who can participate in co-building.

The **Account Executive** owns the commercial relationship and pipeline qualification. They identify whether a prospect is "bootcamp-ready" or needs further nurturing. The **Deployment Strategist (DS)** enters during late-stage qualification to assess technical feasibility — can Palantir actually get data, stand up an environment, and build something meaningful in five days? The DS conducts a **scoping call** (typically 60-90 minutes) with the prospect's technical and business stakeholders to identify candidate use cases and evaluate data availability. This scoping call is the critical gate: if the DS determines the prospect's data is too locked down, the use cases too vague, or the stakeholders uncommitted, the bootcamp does not proceed.

### Pre-bootcamp preparation: the 2-4 weeks before Day 1

This phase is where Palantir's competitive moat becomes apparent. By the time the client walks into the room on Day 1, **a substantial amount of work has already been done.** The preparation phase involves four parallel workstreams:

**Workstream 1 — Data acquisition and ingestion.** FDEs work with the client's IT or data engineering team to identify and extract data. The formats accepted are deliberately flexible: **CSV/Excel file dumps** are the most common starting point (lowest friction), but Palantir's Data Connection framework also supports **JDBC connections** to SQL Server, PostgreSQL, Oracle, Snowflake, and other databases; **API-based connectors** for SaaS platforms like Salesforce, SAP, and ServiceNow; **cloud storage pulls** from S3, Azure Blob, or GCS; and **streaming ingestion** via Kafka for real-time use cases. For security-sensitive organizations, **read-only database replicas** or anonymized/sampled datasets are acceptable. The goal is not perfect data — it is *representative* data that can power a prototype. FDEs typically request 3-6 months of historical data across the relevant operational domains. Data lands in Foundry as raw datasets stored in Apache Parquet format, organized in a sandbox environment provisioned specifically for the bootcamp.

**Workstream 2 — Ontology and pipeline pre-build.** Once data is flowing, FDEs begin constructing the foundational data architecture. Using **Pipeline Builder** (a no-code visual tool) and **Code Repositories** (PySpark/SQL environments), they build cleaning and transformation pipelines — handling nulls, normalizing schemas, joining disparate sources, and creating "ontology-ready" datasets. They then begin mapping the **Ontology** in Ontology Manager: defining initial Object Types (e.g., "Customer," "Work Order," "Equipment," "Shipment"), mapping properties from dataset columns, setting primary keys, and creating Link Types to represent relationships. By Day 1, a **skeleton ontology of 5-10 object types with basic properties and links is typically in place**, along with the underlying pipelines. This is not a finished product — it is scaffolding that the co-building process will flesh out.

**Workstream 3 — Use case selection and prioritization.** The DS leads a structured process to narrow from an initial list of 5-10 candidate use cases down to **3-5 that will be explored on Day 1, with 1-2 ultimately built during the week.** The selection framework evaluates each use case on four axes: **business impact** (revenue, cost savings, or risk reduction potential), **data feasibility** (is the required data available and accessible?), **demonstrability** (can this be shown working in a compelling way within 5 days?), and **executive resonance** (will this make the C-suite sponsor excited?). The client proposes use cases based on their pain points; Palantir guides the selection based on what is technically achievable and most likely to convert to a production contract. Common bootcamp use cases include predictive maintenance (manufacturing), supply chain optimization, work order routing, fraud detection, patient flow optimization (healthcare), and inventory management.

**Workstream 4 — Legal and logistics.** A **mutual NDA** is typically signed before any data sharing begins. For regulated industries, a **data processing agreement (DPA)** may be required. Palantir's legal team has streamlined templates for these — the NDA process typically takes 1-2 weeks. The bootcamp environment is provisioned in Palantir's cloud (most common for commercial) or the client's own infrastructure (more common for defense/government). Client-side logistics include identifying **8-12 participants** from the customer side: executive sponsor, 2-3 business/domain SMEs, 2-3 data engineers or analysts, and a project lead.

**Workstream 5 — "Art of the possible" demo preparation.** Before the bootcamp week, Palantir often conducts a **60-90 minute "Art of the Possible" demonstration** for the client's leadership team. This is a live, customized demo — not a canned slide deck. An FDE builds a simplified version using the client's *own pre-ingested data* (or industry-representative data if client data is not yet available) to show what AIP can do. These demos are **vertical-specific**: a healthcare demo shows patient flow optimization with real hospital data patterns; a manufacturing demo shows predictive maintenance with sensor data. The demo runs **live on a Foundry instance** — this is deliberate, as it demonstrates the platform's real capability rather than a polished video. The "Art of the Possible" session serves as the emotional trigger that secures executive commitment to the bootcamp.

### Internal staffing: how the bootcamp team is assembled

The typical bootcamp team consists of **2-5 Palantir personnel**: one **Deployment Strategist** (owns the engagement narrative, stakeholder management, and business value articulation), **1-2 Forward Deployed Engineers** (handle all technical building), sometimes a **Forward Deployed Infrastructure Engineer** (handles environment setup, particularly for on-prem deployments), and the **Account Executive** (present at kickoff and demo day, handles commercial conversations). For complex engagements or strategic accounts, a senior FDE or **Deployment Lead** coordinates the overall bootcamp.

Staffing decisions are made by the regional deployment leadership in coordination with AE input on the account's strategic importance. FDEs are assigned based on **vertical expertise** (an FDE who has done manufacturing bootcamps is assigned to manufacturing prospects), **technical skill match** (ontology expertise vs. AIP Logic expertise), and **availability.** The same FDE team that runs the bootcamp typically continues with the account if it converts — this continuity is a deliberate design choice that creates personal investment in conversion.

---

## Day 1: problem framing and the hook

### Morning block (9:00 AM – 12:30 PM): kickoff and discovery

The day opens with introductions and alignment. The DS leads a structured **problem framing workshop** that borrows elements from design thinking and process mapping. This is not an abstract strategy session — it is a facilitated, whiteboard-heavy exercise where participants physically map operational workflows. The DS asks the client's domain experts to **walk through their current process end-to-end** for each candidate use case: who does what, where data enters, where decisions are made, where bottlenecks and errors occur. This is recorded on whiteboards or digital equivalents as **process flow diagrams**.

The framework used is closest to **"jobs to be done"** combined with process mapping. For each workflow, the team identifies: the *trigger* (what initiates the workflow), the *decision points* (where a human makes a judgment call), the *data inputs* (what information the human uses to decide), and the *pain* (what goes wrong, what takes too long, what costs money). The DS probes for **quantifiable metrics**: "How many work orders are misrouted per week? What's the cost of each misroute? How long does triage take? What would 50% faster look like in revenue terms?"

By mid-morning, the candidate use cases are evaluated against the four-axis framework (impact, feasibility, demonstrability, executive resonance), and the team collectively selects **1-2 primary use cases** to build during the week.

### Afternoon block (1:30 PM – 5:30 PM): "Art of the Possible" and data validation

If an "Art of the Possible" demo was not conducted pre-bootcamp, it happens now. The FDE fires up the **live Foundry instance** and shows the client's own data already ingested and partially modeled. This is the emotional pivot of the bootcamp — the moment the client sees their messy spreadsheets transformed into a structured, queryable, visually navigable system. The demo typically shows: raw data flowing through a pipeline, the same data represented as Ontology objects with relationships, and a simple Workshop application that lets users browse, filter, and act on the data. If AIP Logic has been pre-configured, the FDE demonstrates a natural-language query against the client's own data — e.g., "Show me all overdue work orders for equipment in Building 7."

The rest of the afternoon is devoted to **data validation and gap identification**. FDEs and client data engineers review the pre-ingested data together: Are the right fields present? Is the data quality sufficient? Are there additional sources that should be connected? The ontology skeleton is reviewed and refined based on the morning's process mapping. Key decisions made on Day 1 include: **final use case selection, data scope confirmation, ontology structure approval, and success criteria definition** (what must the Day 5 demo show to be considered a success).

**Day 1 deliverables:** Finalized use case scope document, process flow diagrams, agreed success criteria, validated data inventory, and refined ontology design.

**Client involvement:** Heavy — domain experts and business stakeholders are actively contributing for 70%+ of the day. This is by design; Palantir needs their knowledge, and the participation creates psychological ownership.

**Palantir roles:** DS leads all workshops and facilitation. FDEs handle the live demo and technical data review. AE is present for the kickoff, observes, and manages the relationship dynamics.

---

## Days 2-3: the co-building sprint where prototypes materialize

### What "co-building" actually means

Co-building is the core of Palantir's methodology and the primary differentiator from traditional consulting. In practice, it works like this: **the FDE drives the keyboard while the client's domain expert sits beside them directing the content.** Client engineers are generally not writing PySpark code themselves — the FDE handles all technical implementation. However, client data engineers participate actively in data validation, pointing out data quality issues, explaining business logic ("this status code means the order was cancelled"), and reviewing pipeline outputs. Business SMEs participate by specifying requirements in real time: "We need to see the priority level here," "This filter should include both pending and in-progress statuses," "The routing logic should account for technician certifications."

The interaction pattern is iterative and rapid. A typical cycle takes 30-90 minutes: the FDE builds a component (a pipeline transform, an ontology action, a Workshop widget), the client reviews it immediately, provides feedback, and the FDE adjusts. This cadence creates a sense of velocity and co-ownership that traditional RFP-driven development cannot replicate.

### Day 2 technical workflow

**Morning (9:00 AM – 12:30 PM):** FDEs dive into building the full data pipeline stack. Using **Pipeline Builder** for straightforward transforms (joins, filters, aggregations) and **Code Repositories** for complex business logic (PySpark code for custom calculations, windowing functions, or ML feature engineering), they construct the complete data flow from raw ingestion to ontology-ready datasets. Simultaneously, the ontology is built out in **Ontology Manager**: all Object Types are created with full property mappings, primary keys are set, and Link Types are wired to represent the relationships identified in Day 1's process mapping. The ontology mapping process is primarily done through the **Ontology Manager UI** — the visual interface for defining object types and their backing datasets — rather than a code-first approach. This is faster and more visually understandable for client stakeholders who are observing.

**Afternoon (1:30 PM – 5:30 PM):** With the ontology in place, FDEs begin building the first **Workshop application**. Workshop is Palantir's no-code application builder and is the primary tool for creating the bootcamp prototype's user interface. The FDE creates modules (pages), adds widgets (object tables, detail panels, charts, maps, KPI tiles, filter panels), and wires them together using variables that pass state between components. By end of Day 2, the goal is a **"walking skeleton"** — a functional Workshop app that displays real data, allows basic filtering and navigation, and demonstrates the core operational workflow. It is not polished, but it works.

**Day 2 deliverables:** Completed data pipelines, populated ontology (5-15 object types, 5-20 link types), and a functional Workshop application skeleton.

### Day 3 technical workflow

**Morning:** FDEs add **Ontology Actions** — write-back operations that transform the app from a passive dashboard into an operational tool. Actions like "Approve Work Order," "Assign Technician," "Escalate Case," or "Update Inventory Status" are configured in Ontology Manager with parameters, validation rules, and permission constraints. These actions are then wired to **action buttons** in the Workshop application, giving users the ability to take real operational decisions within the prototype.

**Afternoon:** **AIP Logic** integration begins. FDEs configure LLM-powered functions that operate on the ontology: the AI agent is given access to specific object types and actions, a system prompt defining its behavior and constraints, and a set of available functions (ontology searches, property lookups, action triggers). **AIP Assist** — a chat interface widget — is embedded into the Workshop app, allowing users to query their data in natural language ("What are the top 5 overdue maintenance tasks?") and trigger actions through conversation ("Assign the highest-priority work order to the nearest available technician"). This is typically the moment that generates the strongest emotional reaction from client stakeholders.

**Day 3 deliverables:** Fully functional Workshop application with operational actions, AIP Logic agents configured and responding to natural language queries, and a prototype that can be demonstrated end-to-end as a working operational workflow.

**Tools opened across Days 2-3:** Data Connection, Pipeline Builder, Code Repositories, Code Workbooks (for exploratory analysis), Ontology Manager, Workshop, AIP Logic, and AIP Assist.

---

## Day 4: stress-testing puts the prototype through its paces

### What stress-testing means concretely

Day 4 shifts from building to hardening. "Stress-testing" in the bootcamp context is not load testing or performance benchmarking — it is **domain expert interrogation** of the prototype's logic, data handling, and decision quality. The format is a structured series of scenario walkthroughs with the client's most experienced domain experts, essentially a **live war-gaming exercise** where experts try to break the system by feeding it their hardest real-world scenarios.

**Morning (9:00 AM – 12:30 PM):** The DS facilitates a **scenario testing session** where domain experts present real cases they have encountered: "What happens when a rush order comes in for a product we don't have in stock?" "How does the system handle a technician who is certified for Type A equipment but assigned to a Type B job?" "What if the sensor data shows a false positive on a maintenance alert?" Each scenario is run through the prototype live, with the FDE and domain experts watching how the ontology, actions, and AIP Logic respond. **Edge cases** in this context mean: data exceptions (missing fields, unusual values, conflicting information), workflow exceptions (scenarios that fall outside the standard process), and AI judgment boundaries (cases where the LLM makes incorrect or ambiguous recommendations).

Every failure or surprising behavior is logged and categorized: critical (must fix before Day 5), important (should fix if time allows), or noted (improvement for production). FDEs immediately begin fixing critical issues — refining pipeline logic, adjusting ontology action rules, or tuning AIP Logic prompts and function definitions.

**Afternoon (1:30 PM – 5:30 PM):** FDEs continue iterating on fixes while the DS begins preparing the **executive demo narrative** for Day 5. This involves structuring a storyline: what problem did we start with, what did we discover, what did we build, what does it do, and what is the measurable business impact? The DS works with the client's project lead to ensure the demo will resonate with the executive sponsor's priorities. The Workshop application is polished — styling is cleaned up, navigation is refined, KPI tiles are added to show metrics that executives care about, and the demo flow is rehearsed.

**Day 4 deliverables:** Bug-fixed and hardened prototype, scenario test results document, draft executive demo narrative, and polished Workshop application.

**Client involvement:** Day 4 is the most collaborative day. Domain experts spend 3-4 hours actively trying to break the system. The client's project lead works with the DS on the executive presentation narrative.

---

## Day 5: the executive demo and commercial pivot

### Morning (9:00 AM – 12:00 PM): final preparation and rehearsal

FDEs make final adjustments to the prototype. The DS and client project lead rehearse the demo flow. The **executive presentation** follows a standard structure, though it is not a traditional slide deck — it is a **live demo with narrative framing.** The format typically includes:

1. **Problem statement** (2-3 slides): The operational challenge, current workflow pain points, and quantified cost of the status quo — drawn directly from Day 1's process mapping
2. **What we built** (live demo, 15-20 minutes): The DS narrates while the FDE drives a live walkthrough of the Workshop application, showing real data flowing through real workflows, actions being taken, and AIP agents responding to natural-language queries
3. **Business impact projection** (2-3 slides): ROI is quantified using a framework that calculates **time savings × labor cost, error reduction × cost per error, and throughput improvement × revenue per unit.** The specific numbers come from the metrics identified during Day 1 problem framing and validated during Days 2-4. For example: "If the current triage process takes 45 minutes per work order and the prototype reduces that to 8 minutes, across 200 work orders per week, that's **123 hours saved per week** at an average labor cost of $85/hour — roughly **$540,000 annually** from this single use case."
4. **Deployment roadmap** (1-2 slides): A phased plan showing what it would take to move from prototype to production, typically structured as: **Phase 1** (weeks 1-8) — production hardening of the bootcamp prototype, security and compliance review, integration with production data sources; **Phase 2** (weeks 8-16) — user training, expanded user rollout, additional data source integration; **Phase 3** (months 4-12) — additional use cases, scale to other business units or geographies.

### Afternoon (1:30 PM – 3:30 PM): executive presentation

The executive sponsor and their leadership team (typically 5-10 senior stakeholders) attend the live demo. The presentation runs 45-60 minutes including Q&A. The participants who co-built the prototype often become the most powerful advocates in the room — they speak to the experience of seeing their own workflows transformed in real time.

### Late afternoon (3:30 PM – 5:00 PM): commercial discussion

The AE re-enters the conversation to discuss next steps. This is not a hard close — it is a **roadmap alignment discussion.** Topics covered include: scope of an initial production engagement, Palantir's subscription pricing model, timeline for production deployment, and resource requirements from both sides. **Pricing details** are not typically finalized during the bootcamp itself; instead, the AE proposes a follow-up meeting to present a formal commercial proposal within 1-2 weeks.

**Day 5 deliverables:** Executive demo presentation (live demo + supporting slides), business impact/ROI projection document, deployment roadmap, and verbal or written commitment to next-step discussions.

---

## Weeks 1-6 after the bootcamp: converting momentum into contracts

### The 48-hour deliverable package

Within two business days of the bootcamp's conclusion, the Palantir team delivers a formal **post-bootcamp package** to the client, which typically includes:

- **Executive summary** (2-4 pages): Problem statement, what was built, key findings, and recommended next steps — written for the C-suite audience
- **Technical assessment**: Architecture diagram of what was built (data sources → pipelines → ontology → applications), ontology schema documentation, and a gap analysis of what would be needed for production
- **ROI projection**: Detailed business case with the quantified impact methodology shown at the Day 5 demo, typically including conservative, moderate, and aggressive scenarios
- **Proposed deployment roadmap**: The phased plan from Day 5, now with more detail on timelines, resource requirements, and dependencies
- **Prototype access**: The bootcamp sandbox environment remains accessible for a defined period — typically **30-90 days** — allowing client stakeholders to continue exploring and building internal support

### Follow-up cadence and conversion mechanics

The DS leads a **weekly check-in call** with the client's project lead for the first 4-6 weeks post-bootcamp. The AE conducts a **commercial proposal presentation** within 2 weeks, typically proposing a **Proof of Value (PoV) engagement** as the next step — a paid, 8-12 week engagement to take the prototype to production-grade. The commercial proposal follows Palantir's standard MSA/SOW structure: a **Master Services Agreement** covering platform licensing and terms, with a **Statement of Work** defining the specific scope, timeline, deliverables, and pricing for the initial engagement.

Palantir's pricing model is **subscription-based**, with initial "land" deals typically ranging from **$100K-$500K annually** for a PoV/pilot, expanding to **$1M-$10M+** for full production deployments. The pricing factors include: number of users, data volume, number of use cases deployed, and whether the deployment runs on Palantir's cloud or the customer's infrastructure.

### Handling the prospects that don't convert

Not every bootcamp converts to a deal. While Palantir has not disclosed exact conversion rates, analyst estimates suggest **30-50% of bootcamps lead to some form of paid engagement** (PoV, pilot, or direct production contract). For the portion that does not convert immediately, the approach varies by reason. If the blocker is **budget timing** (interested but no budget until next fiscal year), the AE maintains quarterly touchpoints and proposes revisiting when budget cycles align. If the blocker is **internal politics** (champion left, reorganization), the DS and AE identify alternative champions and may propose a second bootcamp for a different team. If the blocker is **technical** (data not ready, infrastructure constraints), Palantir may offer lighter-touch engagements to help resolve the technical prerequisites before proposing another bootcamp.

Palantir does re-engage unconverted prospects, typically on a **3-6 month cycle**, often timed around major product releases, AIPCon events, or industry conferences where new capabilities can be demonstrated. The prototype sandbox staying accessible for 30-90 days also serves as a persistent reminder of what was built.

---

## The commercial metrics that prove this model works

The bootcamp program has delivered measurable acceleration across every metric Palantir reports. **US commercial revenue** grew from 23% year-over-year in Q3 2023 (when bootcamps launched) to approximately **64% year-over-year by Q4 2024** — a trajectory directly attributed to the bootcamp motion by CEO Alex Karp and CTO Shyam Sankar on consecutive earnings calls. US commercial customer count grew **83% year-over-year** by Q2 2024, reflecting the new-logo acquisition power of the bootcamp model.

The cumulative bootcamp count scaled at a remarkable rate: roughly **100 by Q3 2023, 500+ by Q4 2023, 915+ by Q1 2024, and over 1,400 by Q3 2024.** Karp described the bootcamp on the Q4 2023 earnings call as "essentially a way of showing people in a very compressed period of time the power of AIP." Sankar was more operationally specific: "The boot camp is not a demo. It's not a presentation. We show up with engineers, and we build."

The model's power lies in its **sales cycle compression** — what used to take 6-9 months of enterprise sales now collapses into weeks. The bootcamp creates urgency, builds internal champions, produces tangible artifacts (a working prototype on real data), and generates a quantified business case — all in five days. The "land" deal may be small ($100K-$500K), but Palantir's **net dollar retention rate of 115-120%** demonstrates that these lands expand aggressively over time.

---

## The technical stack in sequence: a builder's view

For an FDE approaching a bootcamp, the tool sequence follows a predictable pattern. **Week -2 to -1:** Data Connection (ingest raw data from client systems), Pipeline Builder and Code Repositories (clean and transform data), initial Ontology Manager work (define skeleton object types). **Day 1:** Code Workbooks (exploratory data analysis with client engineers), Ontology Manager (refine based on process mapping). **Day 2:** Pipeline Builder and Code Repositories (complete transformation layer), Ontology Manager (full object types, link types, properties). **Day 3:** Workshop (build application UI — object tables, detail panels, charts, maps, action buttons, filter panels), AIP Logic (configure LLM agents with function access to ontology). **Day 4:** All tools simultaneously (debugging, hardening, polishing). **Day 5:** Workshop (demo), with supporting slides.

The ontology typically ends the week with **5-15 Object Types**, **5-20 Link Types**, **3-10 configured Actions**, and **5-20 data transformation pipelines** powering the backing datasets. The Workshop application has **multiple modules (pages/tabs)** with interactive widgets, and 1-2 AIP Logic agents capable of natural-language queries and action execution. This is not production-grade — but it is functional, built on real data, and demonstrably solves the client's stated operational problem.

---

## Conclusion: why this playbook is difficult to replicate

Palantir's bootcamp methodology works because of three reinforcing advantages that competitors struggle to reproduce. First, **the platform's ontology layer** provides a semantic abstraction that makes it possible to model any operational domain in days rather than months — without the ontology, you cannot build meaningful applications this quickly. Second, **the FDE model** — software engineers embedded with customers who understand both the technology and the domain — is a human-capital moat that requires years to build and cannot be replicated by hiring consultants. Third, **the co-building methodology itself** creates psychological ownership and internal champions that no slide deck or demo video can match. When a VP of Operations watches their own data power an AI agent that answers questions about their own workflow, the sale is largely made before the AE opens the commercial discussion.

The playbook's most underappreciated element is the **pre-bootcamp preparation**. The magic of Day 1 — when the client sees their data already live in the system — is actually the result of 2-4 weeks of unglamorous FDE work: wrestling with CSVs, debugging JDBC connections, writing PySpark transforms, and building ontology scaffolding. That invisible preparation is what makes the five-day sprint feel like magic rather than a rushed demo. It is, in Shyam Sankar's framing, "the problem-solving ethos of forward-deployed engineering brought to a compressed, high-intensity format" — and it has become the most effective enterprise AI sales motion in the market.