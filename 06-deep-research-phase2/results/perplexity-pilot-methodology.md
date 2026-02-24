# Palantir FDE 90-Day Pilot Deployment Methodology: The "Acquire" Phase

## Overview

Palantir's "Acquire" phase is a deliberately loss-making engagement designed to prove the platform's value on 1–3 high-impact use cases within 60–90 days. In 2019, customers in the Acquire phase generated just $600,000 in revenue against a contribution loss of $65.4 million — the intent is to create an irreversible foothold. The deployment is executed by a small, autonomous team of 4–5 people — typically 2–3 Forward Deployed Software Engineers (FDSEs) and 1–2 Deployment Strategists (DSs) — who embed onsite at the client's facilities 3–4 days per week.[^1][^2][^3]

The overarching structure follows four phases that overlap heavily in practice: Foundation (Weeks 1–3), Lighthouse Build (Weeks 2–6), Application & Action Design (Weeks 4–10), and Training & Handoff (Weeks 8–12). What follows is a reconstruction of what happens in each, based on public sources from former FDEs, Palantir's own documentation, partner implementation guides, and patent filings.[^4]

***

## PHASE 1: Discovery & Data Collection (Weeks 1–3)

### Team Deployment & Stakeholder Mapping

The FDE team arrives onsite on Day 1 with minimal pre-briefing — Palantir's cultural bias is "get on a plane first, ask questions later". The first week is almost entirely devoted to understanding the client's world.[^1]

**Who they meet:**
- **C-suite sponsor** (CEO, COO, CDO): The person who signed the contract. Meetings are typically 1-on-1 or small group, weekly cadence. The DS leads these.[^5]
- **Department heads / VP-level**: 2–4 interviews per department to understand organizational structure, pain points, and political dynamics.
- **Frontline operators**: The people who will actually use the software — factory floor supervisors, hospital ward nurses, trading desk analysts. FDEs literally walk the factory floor, hospital ward, or trading desk. At Airbus, Nabeel Qureshi "moved out to Toulouse for a year and worked in the factory alongside the manufacturing people four days a week".[^1]
- **Data owners / IT gatekeepers**: The people who control access to databases, APIs, and source systems. These are often the most adversarial stakeholders.[^1]

**Stakeholder mapping methodology:** There is no evidence of a rigid interview guide. The approach is closer to anthropological fieldwork than structured consulting. FDEs are trained using insights from Keith Johnstone's *Impro* — the company vocabulary is "saturated with Impro-isms" like "casting" (reading who holds actual power vs. nominal authority) and status dynamics. The goal is to quickly identify:[^1]
1. The **champion** who will fight internal battles for you (usually someone whose career is tied to the project succeeding)
2. The **blockers** (usually middle-management data gatekeepers whose power derives from controlling information flow)
3. The **frontline allies** who will pressure their bosses to cooperate

Sarah Constantin's detailed account of the Palantir playbook describes the strategy explicitly: "Win the hearts of front-line workers... use your allies on the bottom (front-line workers) and the top (executives) to squeeze out your opponents in the middle" .

### Process Mapping Methodology

FDEs do not typically use formal BPMN or swimlane diagrams. The approach is deeply contextual and informal — the emphasis is on *understanding the problem*, not producing process documentation artifacts.

**Time allocation:** The balance skews heavily toward observation early on. In manufacturing contexts, FDEs spend the first 1–2 weeks primarily observing and asking questions, with perhaps 20–30% of time spent on actual system configuration. Ted Mabrey describes this as a "Gita-esque experience of incrementally revealed truth" — the FDE discovers what the real problem is through deep immersion, not through a requirements document .

**What "process mapping" looks like in practice:**
- Walking the floor and asking "What do you do when X happens?" repeatedly
- Sitting with operators and watching them use their existing tools (often Excel, SAP, paper forms)
- Identifying where information flow breaks down: "Where do you go when you need to know Y? Who do you call?"
- Mapping data flows informally — what system produces what data, who consumes it, where it gets stuck

**Artifacts produced:** Internal whiteboard diagrams, informal data flow sketches, and crucially, the FDE's own mental model of the business. The real artifact is the FDE's understanding, which gets encoded directly into the ontology design rather than into intermediary documents. The company explicitly values "solving the problem" over documentation — "to hell with generalizability".[^1]

**Decision: What's "ontology-worthy"?** An entity becomes an Object Type when it represents a real-world concept that users need to track, query, and act upon. The test is: "Do operators think in terms of this thing?" If manufacturing people talk about "work orders," "non-conformities," and "missing parts," those become Object Types. Data exhaust that nobody references stays as raw datasets.[^6]

### Data Discovery & Inventory

This is the single hardest and most time-consuming part of the pilot. Nabeel Qureshi notes: "You'd have a company buying an 8–12 week pilot, and we'd spend all 8–12 weeks just getting data access, and the final week scrambling to have something to demo".[^1]

**How FDEs catalog data sources:**
- Interview data owners with questions like: "What system is this in? How often is it updated? Who has access? What format? How reliable is it? What does this field actually mean?" 
- The data is often in hostile formats: "PDFs, notebooks, Excel files (my god, so many Excel files)". In aerospace, a major manufacturer kept "all of the results of airplane quality tests in the form of scanned handwritten PDFs" .[^1]
- No formal scoring framework has been disclosed, but FDEs assess: completeness, freshness, format (structured vs. unstructured), access difficulty, and political sensitivity.

**The "data access politics" playbook:**
Sarah Constantin's account provides the most detailed public description of how Palantir navigates data gatekeepers :

1. **Leverage executive air cover:** The C-suite sponsor can "demand that you be given speedy assistance and data access."
2. **Build frontline pressure:** Operators who see value in the new tools pressure their managers to cooperate.
3. **Address security concerns head-on:** Palantir's platform has built-in RBAC, row-level security, audit trails, and markings — implementing Palantir often makes data *more* secure, not less.[^1]
4. **Be patient but persistent:** "The Palantir Way is labor-intensive and virtually impossible to systematize. You have to throw humans at the persuasion problem — well-paid, cognitively flexible, emotionally intelligent humans" .
5. **Navigate contradictory IT policies:** In large organizations, different departments may have incompatible security requirements. The FDE must find creative workarounds.

**Data connection setup** (technical): Foundry uses the Data Connection application. Two connection modes exist:[^7]
- **Direct connection** (for internet-accessible systems): Define egress policies, configure credentials, set up syncs.
- **Agent-based connection** (for on-prem/airgapped systems): Install a Palantir agent within the client's network that acts as a secure intermediary. The agent runs Java 21+ and maintains an outbound connection to Foundry.

Typical connector setup time per source: 1–5 days depending on complexity. Most common failure modes: firewall/egress policy issues, credential rotation, schema mismatches, and rate limiting. "Most Foundry users will never need to set up a new agent themselves — agent setup requires an IT-focused skill set, though the same agent can be reused to support multiple sources".[^7]

### Use Case Prioritization

After 1–2 weeks of discovery, the team narrows focus to 1–3 use cases. The selection criteria, synthesized from multiple sources:

| Criterion | What It Means | Weight |
|-----------|---------------|--------|
| **Executive sponsorship strength** | Does a C-suite leader personally care about this problem? | Critical [^4] |
| **Data readiness** | Can we actually access the data needed? In what timeframe? | Critical  |
| **Frontline pain** | Do operators viscerally feel this problem daily? | High [^1] |
| **Demonstrable ROI** | Can we quantify value in dollars/time saved within 90 days? | High [^4] |
| **Expansion potential** | Does solving this create demand for adjacent use cases? | Medium [^3] |
| **Technical feasibility** | Can we deliver a working prototype in 2–4 weeks? | High |

No formal scoring matrix has been publicly disclosed. The Palantir culture prizes judgment over frameworks — the FDE team makes the call based on their accumulated understanding. However, IFC's implementation framework (used by Palantir partners) describes a 2×2 matrix of "Impact vs. Implementation Complexity" with quadrants for Quick Wins, Strategic Investments, Easy Benefits, and Avoid/Defer.[^4]

***

## PHASE 2: Ontology Design & Data Integration (Weeks 2–6)

### Ontology Design Process

The Ontology is Palantir's core differentiator — a "dynamic, semantic representation—a digital twin—of an organization's complete operational landscape". It maps siloed data to real-world concepts.[^3]

**The building blocks**:[^6]
- **Object Types**: Real-world entities (Customer, Aircraft, Work Order, Patient, Flight)
- **Properties**: Attributes of those entities (name, status, date, location)
- **Link Types**: Relationships between entities (Flight → assigned_to → Aircraft, one-to-many or many-to-many)
- **Action Types**: Operations users can perform (Approve Order, Assign Technician, Mark for Consolidation)
- **Functions**: Arbitrary business logic (compute derived values, validate constraints)
- **Interfaces**: Polymorphic abstractions (all "Trackable Items" share a shape regardless of whether they're Work Orders or Defect Reports)

**How an FDE decides what becomes an Object Type vs. a Property:**
The heuristic from practitioner accounts:[^8][^9]
1. **Identify business entities** — what do people in the organization *name* and *track* as distinct things? (Employee, Project, Machine, Order)
2. **Define attributes** — what properties does each entity have? (Employee → ID, Name, Department, Hire Date)
3. **Define relationships** — how do entities relate? (Employee works_in Department, Employee assigned_to Project)
4. **Map to cleaned pipeline outputs** — each Object Type is backed by a curated dataset
5. The key design principle from Palantir partners: "Work with the data you have, find the right level of abstraction to describe your real-world needs, and make intentional decisions about where your properties belong"[^9]

**Naming conventions:** Object Type IDs are auto-generated from the display name and cannot be modified after first deployment. Best practice is to use prefixed names to avoid conflicts in multi-tenant ontologies (e.g., `supply-chain-shipment`, `hr-employee`). Plural names auto-populate.[^10][^11]

**Client validation:** FDEs typically show the ontology design to the client's business users in an informal review — often using Object Explorer, which allows non-technical users to browse objects, see properties, and navigate links. The Deployment Strategist leads these sessions, translating between technical structure and business meaning.[^12][^5]

**Iteration count:** The ontology goes through continuous iteration throughout the pilot. Ted Mabrey describes how "the customer completely reframes a project charter every month" — scope creep is welcomed because "the customer's mission demands it" . Expect 3–5 major structural revisions during a 90-day pilot.

### Data Pipeline Construction

Foundry provides two primary tools for building data transformation pipelines:

**Pipeline Builder** (visual, low-code):[^13][^10]
- Drag-and-drop interface for building data integration pipelines
- Supports both batch and streaming datasets
- Can create Object Types and Link Types directly as pipeline outputs
- Typical workflow: Add data source → Apply transforms (filter, join, aggregate, cast types) → Define output as Object Type → Deploy
- Supports adding Ontology outputs (Object Types and Links) directly in the pipeline output panel

**Code Repositories** (PySpark/Python):
- For complex transformations that exceed Pipeline Builder's capabilities
- FDEs "tend to write code that gets the job done fast, which usually means — politely — technical debt and hacky workarounds"[^1]
- Typical transform: read from source (e.g., SAP extract), parse records, clean/normalize fields, apply business logic, output to dataset that backs an Object Type

**A typical transform example** (based on Airbus-type manufacturing scenario):
1. Ingest work order data from SAP via BAPI connector
2. Parse JSON/CSV into structured columns
3. Clean: normalize date formats, trim whitespace, handle nulls
4. Enrich: join with parts inventory data, quality defect records
5. Map to `WorkOrder` Object Type with properties: `order_id`, `status`, `assigned_team`, `aircraft_serial`, `due_date`
6. Create Link Types: WorkOrder → affects → Aircraft, WorkOrder → requires → Part

**Data quality handling:**
- Pipeline Builder includes built-in validation: type checking, null handling, schema enforcement[^14]
- Palantir patent US10866792B1 describes automated "deployment pipeline cleaning rules" that check for: invalid dataset names, invalid data types, stale data, broken branches, and invalid mappings[^14]
- In practice: a combination of automated checks in the pipeline and manual review by the FDE team during iteration sessions with the client

**Testing:** Pipeline Builder supports preview/dry-run of transforms before deployment. Code Repositories support standard testing patterns. Formal unit testing varies by FDE — the culture values speed over test coverage during the pilot phase.

### Data Source Connection (Technical Detail)

The Data Connection application supports 200+ out-of-the-box connectors. The setup requires three components configured in order:[^3][^7]

1. **Network connectivity**: Either direct egress policies (for cloud/internet-accessible sources) or agent installation (for on-prem sources)
2. **Source configuration**: Credentials, connection strings, API keys. The source defines *how* to reach the external system.
3. **Sync configuration**: Defines *what* data to pull and *when*. Supports snapshot (full replace) and incremental (append/delta) syncs.

**Agent installation** (for on-prem): The agent is Palantir software installed on a machine within the client's network. It maintains an outbound HTTPS connection to Foundry on port 443. "Some organizations can operate long-term with agents set up during the first week of a Foundry deployment". HA (high availability) is achieved by assigning multiple agents to a single source.[^7]

**Common connection types:** AWS S3, relational databases (PostgreSQL, SQL Server, Oracle), REST APIs, SFTP, SAP, Snowflake.[^15][^16]

**Typical timeline per data source:** 1–2 days for straightforward cloud sources (S3, REST APIs); 3–7 days for on-prem databases requiring agent setup and firewall negotiation; weeks to months for politically contested data sources .[^1]

***

## PHASE 3: Actions, Security & Application Building (Weeks 4–10)

### Action Type Design

Action Types are the "kinetic" layer of the Ontology — they enable users to write back to data, not just read it.[^17][^6]

**How FDEs identify which actions to model:**
- Interview users about "what do you *do* with this data?" — observe the decisions they make and the workflows they execute[^5]
- Map each user decision to an Action Type: Approve, Reject, Assign, Update Status, Create Record, Link Objects
- Example from Workshop tutorial: A "Mark Shipment for Consolidation" action modifies a property on a Shipment object[^18]

**Action Type configuration**:[^17]
1. **Definition**: Choose change type (Create, Modify, Delete, Link objects)
2. **Parameters**: Define inputs the user must provide (object reference, string, integer, date)
3. **Rules**: Configure what properties change and how (set Status to "Approved", assign to selected User)
4. **Validation/Submission Criteria**: Business rules that must pass before the action executes
5. **Side Effects**: Notifications, webhooks, or triggers that fire after successful submission

**Writeback configuration:** Actions write to a "writeback dataset" associated with the Object Type. Two permission modes exist: "Only allow edits via Actions" (more restrictive, users only need Read access) or allow edits via Actions plus Forms, Object Explorer, and API calls (requires Edit permissions on writeback dataset). Business rules are decided collaboratively between the FDE and the client's subject matter experts.[^19]

### Security Configuration

Security is architecturally foundational, not bolted on after the fact. Palantir "figured out early that data access tussles were partly about genuine data security concerns, and could be alleviated through building security controls into the data integration layer".[^1]

**Security layers**:[^20][^21][^22]

| Layer | Mechanism | What It Controls |
|-------|-----------|-----------------|
| **Dataset-level** | ACLs (Read/Write/Discover) | Who can access the backing dataset at all |
| **Row-level (Object Security Policies)** | Mandatory controls, markings, user-attribute comparisons | Which object instances a user can see — e.g., users only see data for their plant/region |
| **Column-level (Property Security Policies)** | Per-property markings | Which properties are visible — e.g., hide salary data from non-HR users |
| **Cell-level** | Combination of object + property policies | A user passes the row check but fails the column check → sees null for that cell |
| **Action-level** | Submission criteria + parameter permissions | Who can execute which actions on which objects |
| **App-level** | Workshop inherits all Ontology security | Apps cannot override dataset or Ontology permissions |

**How RBAC is configured in practice:** The DS typically leads a questionnaire-style session with the client's security/compliance team: "Who should see what? Which roles exist? What are the data sensitivity classifications?" This maps to Foundry's group-based permissions and marking system. Row-level security uses mapping tables (user → plant, user → business unit) that filter at query time.[^21]

**Testing security policies:** The Workshop "Check access" panel allows administrators to simulate a specific user's view — verifying what objects, properties, and actions they can see.[^19]

### Application Building with Workshop

Workshop is Palantir's primary low-code application builder — described internally as "Retool-like UI for making webapps".[^1]

**Step-by-step process**:[^23][^24][^18]

1. **Create a Workshop module** in a Foundry project
2. **Add widgets** from the widget palette. Core widget types include:
   - **Display**: Object Table, Object List, Property List, Object View, Object Set Title
   - **Visualization**: Chart: XY (bar/line/scatter), Chart: Pie, Map, Gantt, Timeline
   - **Control**: Button Group, Filter List, Dropdown, Toggle, Search Bar
   - **Layout**: Sections, Tabs, Conditional Visibility
   - **Platform**: Scenario Manager, Scenario Selector
3. **Bind widgets to data** via variables:
   - Create an Object Set variable (e.g., "All Shipments" → Object Set of type `ProductShipment`)
   - Connect the Object Set to a Table widget; the table auto-populates columns from Object Type properties
   - Wire a Filter List widget to the same Object Set to enable dynamic filtering
4. **Add Actions**: Place a Button Group widget → configure a button → bind it to an Action Type → map parameters (e.g., "selected object" from table → Action's target object)
5. **Iterate layout**: Split sections, add tabs, configure column widths, apply styles and conditional formatting
6. **Publish**: Save → Publish a version → share the URL with users

**Who designs the UI?** The FDE builds it, with the DS driving requirements and feedback loops. There is no dedicated designer — "UI designer" is not a standard role in the FDE team. The DS runs iteration sessions with client users, typically showing progress and collecting feedback in 30–60 minute sessions 2–3 times per week.[^12]

**Iteration count:** Expect 5–10+ iterations on a Workshop app during a pilot. The feedback loop is extremely tight — "iterate rapidly with users to make sure the solution is what they want and need".[^12]

**Workshop vs. Slate vs. Quiver decision:**
- **Workshop** (default): Low-code, fast to build, suitable for 80%+ of operational applications
- **Slate**: Custom frontend with full HTML/CSS/JS control, for complex UIs that exceed Workshop's widget library. Now increasingly replaced by OSDK + custom React apps[^25]
- **Quiver**: Point-and-click analytics tool, for ad-hoc data exploration rather than operational workflows
- **Contour**: Dashboard-style analytics, often used as a transitional tool before Workshop adoption[^26]

***

## PHASE 4: User Training & Handoff (Weeks 8–12)

### Training Methodology

Training runs concurrently with the late application-building phase, not as a separate step after go-live.

**Training delivery modes**:[^27][^28]
- **Onsite classroom/workshop sessions**: Led by the DS, typically in groups of 5–15. Focus on navigating the application, understanding the data model, and performing core actions.
- **Deskside mentoring**: 1-on-1 sessions where an FDE or DS sits with an operator and walks them through the workflow in their real work context. The DS blog post describes: "01:30 PM — Iteration session with clients to show them the progress I've made since morning — understand their real-world problems, listen to their feedback".[^12]
- **Virtual sessions**: For distributed teams or remote users.
- **Self-guided learning**: Palantir has a learning platform (learn.palantir.com) with certification paths: Foundry Aware, Data Engineer, App Developer.[^18]
- **Train-the-trainer**: A key handoff mechanism — identify 2–5 "power users" or "citizen developers" from the client who will become internal Foundry champions.[^28]

**Training materials produced:**
- Application walkthrough guides (screenshots + step-by-step instructions)
- Video recordings of training sessions
- Quick-reference cards for common workflows and actions
- Certification paths for technical users (Data Engineer, App Developer certifications)

**Hours per role:** No precise public figures, but based on partner accounts: basic users receive 4–8 hours of training; power users / citizen developers receive 16–40 hours over several weeks.[^27][^28]

**Identifying power users:** The DS identifies operators who show natural curiosity, technical aptitude, and influence within their team. These become the internal Center of Excellence (CoE) — "Palantir helps the client stand up a Center of Excellence with defined roles, from platform owner to permissions manager, so the organization can run on its own".[^2]

### Go-Live Process

**Transition from FDE-operated to client-operated**:[^29][^2]

The handoff is gradual, not abrupt. Palantir's stated intent is **autonomy** — "the reality is often a long-term relationship, not because of dependency, but because Palantir's product roadmap keeps offering new capabilities to operationalize".[^2]

**Go-live activities:**
1. **Pre-go-live checklist** (inferred from implementation patterns): Pipeline health validation, data freshness checks, security policy audit, user access provisioning, action type testing, performance testing under load
2. **Phased rollout**: Often deploy to a small pilot group first (1 team, 1 shift, 1 geography), then expand
3. **Monitoring setup**: Foundry provides built-in monitoring for pipeline builds, data freshness, and sync health. Custom dashboards in Contour or Workshop can track application usage metrics.
4. **Apollo continuous delivery**: Apollo manages software updates and deployments across all environments, including roll-forward/roll-back capabilities.[^30]

**Post-go-live support model:**
- During the first 2–4 weeks after go-live, FDE team remains available on-call
- Baseline (Forward Deployed Infrastructure) team handles fleet-wide operational issues[^30]
- The transition to the client's internal team accelerates through Weeks 10–12
- Palantir's Foundry Adoption documentation describes four phases of organizational maturity, with Phase 1 being "Focus on use cases" (1–2 use cases in production, small user base) and Phase 2 expanding scope[^31][^32]

**Program team roles the client should stand up** (from Foundry Adoption docs):[^32]
- **Program Lead**: Primary owner of the Foundry Program's success
- **Data Lead**: Manages data integration and pipeline health
- **Ontology Lead**: Owns the ontology structure and evolution
- **Head of Data Governance**: Can be combined with Data Lead or Ontology Lead in Phase 1; standalone by Phase 3
- **Application Developers**: Build and maintain Workshop apps
- **Permissions Manager**: Manages security policies and access control

### Success Measurement

**How pilot success is measured:**
The Acquire phase is measured against the "business case for expansion" — the goal is to demonstrate enough value that the client funds the Expand phase.

**KPIs typically tracked**:[^4][^3]
- **Time-to-value**: How quickly the first use case delivered measurable results (target: 60–90 days for initial returns)
- **User adoption**: Number of active users, frequency of application usage, breadth of actions taken
- **Quantified operational impact**: Cost savings, time savings, error reduction, throughput improvement. Examples from public case studies: General Mills saved ~$14M annually ($40k/day); Fujitsu achieved $9M annual cost reduction in 3 months; AARP launched first prototype in 45 days.[^3]
- **Data integration breadth**: Number of data sources connected, ontology coverage
- **User satisfaction**: Qualitative feedback from operators and executives

**Who presents results?** The DS typically leads the executive review presentation, with FDE support on technical questions. The presentation targets the C-suite sponsor and builds the case for expanding to additional use cases, departments, and data sources.[^5]

**Business case for expansion document contents** (synthesized):
- Quantified ROI from pilot use cases
- Narrative of user adoption and behavioral change
- Roadmap of 3–5 additional use cases identified during discovery
- Data integration expansion plan (additional sources, departments)
- Proposed team structure for the Expand phase
- Cost/timeline estimates for next phase

***

## Relevant Patent Filings

Several Palantir patents illuminate the technical methodology:

| Patent | Title | Relevance |
|--------|-------|-----------|
| US20160314155A1 | Data Integration Pipeline | Describes the two-phase (ingest + import) pipeline architecture: parse raw data into object fragments, difference against existing objects, merge into object database [^33] |
| US9946777B1 | Systems for Facilitating Data Transformation | Details the transform process: generate a domain-specific programming language from the source schema + target ontology, with error checking, type checking, and autocomplete [^34] |
| US20230289153A1 | Workflow Application and UI Builder | Describes Workshop's architecture: access ontology → display configurable layout → add components → determine valid variables from object type definitions → configure based on user selection [^35] |
| US20240354322A1 | LLM-Based Data Object Extraction | Uses LLMs to auto-generate ontology mappings: extract entity triples from data, classify against existing ontology, auto-create matching Object Types [^36] |
| US20230103939A1 | Synchronization of Data Across Ontologies | Handles cross-system data sync: generate data objects, incorporate into ontology, detect updates, propagate changes bidirectionally [^37] |
| US10866792B1 | Rules-Based Cleaning of Deployment Pipelines | Automated pipeline validation: check for invalid dataset names, invalid data types, stale data, broken branches, invalid source code mappings [^14] |

***

## Daily Rhythm: What a Typical FDE Week Looks Like

Based on the Deployment Strategist "Day in the Life" blog post  and Nabeel Qureshi's account:[^12][^1]

**Early Phase (Weeks 1–3):**
| Time | Activity |
|------|----------|
| 08:00 | Arrive onsite, breakfast over emails, review overnight data sync status |
| 09:00 | Daily standup with Palantir team (15 min): blockers, priorities, who's meeting whom today |
| 09:30 | Stakeholder interview / floor walk — observe operators, ask questions, map processes |
| 11:00 | Data access negotiation meeting with IT / data owners |
| 12:00 | Lunch with client team (relationship building is essential) |
| 13:00 | Pipeline work: configure connectors, build initial transforms, debug data quality issues |
| 15:00 | Sync with DS on use case prioritization and stakeholder politics |
| 16:00 | Internal Palantir sync: update account team on progress, escalate blockers |
| 17:00–19:00 | Continue technical work (pipeline building, ontology sketching) |

**Build Phase (Weeks 3–8):**
| Time | Activity |
|------|----------|
| 08:00 | Check pipeline health, review overnight builds |
| 09:00 | Daily standup (Palantir team + client technical counterparts) |
| 09:30 | Ontology iteration / Workshop app building |
| 11:00 | Client demo / feedback session (30–60 min, 2–3x per week) — show progress, collect feedback, iterate |
| 12:00 | Lunch with users |
| 13:00 | Implement feedback from morning session |
| 14:00 | Security configuration session with client compliance team |
| 15:00 | Action Type design — model user decisions as write-back operations |
| 16:00 | Weekly executive check-in (DS leads): progress update, emerging blockers, scope refinement |
| 17:00–19:00 | Technical work, pipeline hardening, testing |

**Handoff Phase (Weeks 8–12):**
| Time | Activity |
|------|----------|
| 09:00 | Training session with user group (classroom or deskside) |
| 10:30 | Power user mentoring: teach citizen developers to modify Workshop apps |
| 12:00 | Lunch |
| 13:00 | Go-live preparation: pipeline scheduling, monitoring dashboards, alerting setup |
| 14:00 | Documentation and handoff materials |
| 15:00 | Executive review preparation with DS |
| 16:00 | CoE planning: define roles, responsibilities, escalation paths for client team |

***

## Key Decision Points That Shape the Deployment

| Decision Point | When | Who Decides | Impact |
|---------------|------|-------------|--------|
| **Use case selection** | End of Week 2 | FDE team + executive sponsor | Determines entire pilot scope |
| **Data source prioritization** | Weeks 1–3 | FDE team based on access feasibility | Governs what's buildable in 90 days |
| **Ontology scope** | Weeks 2–4 | FDE lead + DS | Defines the "shape" of the digital twin |
| **Pipeline Builder vs. Code Repos** | Per data source | FDE | Visual for simple transforms; code for complex logic |
| **Workshop vs. Slate vs. Quiver** | Weeks 4–5 | FDE team | Workshop is default; Slate only for complex custom UIs |
| **Security model** | Weeks 4–6 | DS + client compliance | Determines data visibility per role |
| **Go-live scope** | Weeks 7–8 | FDE team + sponsor | Which users, which geography, which shift goes first |
| **Expansion proposal** | Weeks 10–12 | DS leads, FDE supports | Determines whether Acquire converts to Expand phase |

***

## Critical Success Factors

From the accumulated evidence, the factors that determine whether a pilot succeeds or fails :[^4]

1. **Executive sponsorship is non-negotiable** — without top-down air cover, data access battles are unwinnable
2. **Get data access fast** — every week spent negotiating access is a week not spent building value
3. **Deliver a "kernel of value" in Week 2–3** — "when a ragtag team of 20-something kids showed up to the customer site and built real software that people could use within a week or two, people noticed"[^1]
4. **Embrace scope creep** — "the FDE yearns for scope creep because the customer's mission demands it" 
5. **Build relationships with frontline users** — they are both your best source of requirements and your most powerful internal advocates
6. **Security is a feature, not a constraint** — demonstrating that Palantir makes data *more* secure opens doors that "data access politics" would otherwise keep closed

***

## Limitations of This Analysis

This reconstruction is based entirely on public sources: blog posts from former employees, official documentation, partner implementation guides, job descriptions, patent filings, and public presentations. Palantir does not publish its internal deployment playbooks, interview guides, scoring matrices, or go-live checklists. The actual process is likely more fluid, context-dependent, and improvisational than any structured breakdown can capture — as Ted Mabrey notes, "there are no maxims that, if you backtested them, wouldn't violate the path one of our most important products took" .

---

## References

1. [Reflections on Palantir - Nabeel S. Qureshi](https://nabeelqu.co/reflections-on-palantir) - Palantir is hot now. The company recently joined the S&P 500. The stock is on a tear, and the compan...

2. [Palantir: Inside the category of one – forward deployed ...](https://www.everestgrp.com/palantir-inside-the-category-of-one-forward-deployed-software-engineers-blog/) - These FDSEs focus exclusively on one customer, building production-ready workflows on Palantir's pla...

3. [Palantir's AI Strategy: Path to AI Dominance From Defense to ...](https://www.klover.ai/palantir-ai-strategy-path-to-ai-dominance-from-defense-to-enterprise/) - This phase is a deliberate loss-leader; for example, in 2019, customers in the acquire phase generat...

4. [[PDF] Enterprise Optimisation with Palantir Platforms - Jimdo](https://storage.e.jimdo.com/file/ecdf96af-e267-4896-9d2c-80deccf7e26f/IFC%20Enterprise%20with%20Palantir.pdf) - Implementation Approach. 60-day manufacturing efficiency lighthouse. 1. 90-day supply chain control ...

5. [Palantir Technologies hiring Deployment Strategist in New York, NY](https://www.linkedin.com/jobs/view/deployment-strategist-at-palantir-technologies-3658456177) - Posted 9:59:37 PM. A World-Changing CompanyPalantir builds the world’s leading software for data-dri...

6. [Overview • Ontology - Palantir](https://palantir.com/docs/foundry/ontology/overview/) - The Palantir Ontology is an operational layer for the organization. The Ontology sits on top of the ...

7. [Data Connection • Initial setup overview](https://www.palantir.com/docs/foundry/data-connection/initial-setup-overview) - This guide will walk you through the process of connecting your organization's data to Foundry. Befo...

8. [How to Design an Ontology in Palantir Foundry for Data ...](https://www.linkedin.com/posts/vikasteach_palantirfoundry-dataengineering-ontologydesign-activity-7386831965871763456-Rsrp) - 🚀 Ontology Design in Palantir Foundry — The Interview Favorite Question! If you’ve ever interviewed ...

9. [How to build an ontology in Palantir Foundry | Fourth Age posted on ...](https://www.linkedin.com/posts/fourth-age_practical-ontologies-how-to-build-them-activity-7305942938935517184-62iR) - Today on our Substack: Pete M. drops Part 2 of our series on practical ontologies, this time on how ...

10. [Palantir](https://www.palantir.com/docs/foundry/pipeline-builder/outputs-add-ontology-output) - You can choose to add an Ontology output to guide your pipeline integration towards clean, structure...

11. [Palantir Deep Dive: Creating Your First Ontology (Beginner-Friendly Walkthrough)](https://www.youtube.com/watch?v=Tj0YAbm41vM) - Ontology is the foundation of how Palantir Foundry models real-world businesses — but it’s also one ...

12. [A Day in the Life of a Palantir Deployment Strategist](https://blog.palantir.com/a-day-in-the-life-of-a-palantir-deployment-strategist-951cb59a5a96) - As a Deployment Strategist at Palantir, you strive to manage difficult situations and find unconvent...

13. [Pipeline Builder • Overview - Palantir](https://palantir.com/docs/foundry/pipeline-builder/overview/) - Pipeline Builder is Foundry's primary application for data integration. You can use Pipeline Builder...

14. [System and methods for rules-based cleaning of deployment pipelines](https://www.perplexity.ai/rest/file-repository/patents/US10866792B1?lens_id=058-706-939-578-796) - publication_number: US10866792B1
assignee: PALANTIR TECHNOLOGIES INC
abstract: Systems and methods a...

15. [Palantir Foundry | Deep Dive: Creating Your First Data Connection](https://www.youtube.com/watch?v=7J0jvKS9BYA) - Welcome to Foundry Fast Lane: Deep Dive — Creating Your First Data Connection.

In this episode, we ...

16. [Data Connection: Getting Data Into Foundry - YEO's IT Journal](https://syeoit.tistory.com/entry/Data-Connection-Getting-Data-Into-Foundry) - Foundry Data Connection offers two methods to connect with data sources: Agents (private networks an...

17. [Use Actions in Workshop - Palantirpalantir.com › docs › foundry › workshop › actions-use](https://www.palantir.com/docs/foundry/workshop/actions-use) - Actions in Foundry allow users to edit, create, delete, and link object data based on defined rule s...

18. [Palantir Deep Dive: Building Your First Application (Beginners Guide)](https://www.youtube.com/watch?v=otjTIMSjPvo) - In this deep dive, we build your first operational application in Palantir Foundry using Workshop — ...

19. [Palantir](https://www.palantir.com/docs/foundry/action-types/permissions/) - Permissions apply to Action types in the following ways: Who can view a given Action type? Who can e...

20. [Object permissioning • Object security policies [Beta] - Palantir](https://www.palantir.com/docs/foundry/object-permissioning/object-security-policies) - Object and property security policies are being rolled out across Foundry enrollments. Contact Palan...

21. [Palantir Foundry Ontology Security: End-to-End Data ...](https://www.linkedin.com/posts/deepak-suryawanshi-a79665126_palantirfoundry-ontologysecurity-rowlevelsecurity-activity-7409034923828797440-44zH) - 🔐 Day 27: Access Control & Security in Palantir Foundry Ontology — How Data Is Actually Protected Se...

22. [Manage granular policies](https://www.palantir.com/docs/foundry/platform-security-management/manage-granular-policies) - Granular policies allow you to configure row-level security for datasets and objects. They are used ...

23. [Developer Deskside | Creating Map Based Workflows with Workshop in Palantir Foundry](https://www.youtube.com/watch?v=bPGnvfyMuxE) - In Palantir Foundry, developers can build operational workflows from data ingestion to interactive a...

24. [Palantir Foundry | Speedrun Your First E2E Workflow – Workshop App + Ontology Actions (Part 2/2)](https://www.youtube.com/watch?v=ISVRT3fj57s) - Welcome back to Foundry Fastlane — where we build Palantir solutions at full speed.

In Part 2 of th...

25. [palantir/workshop-iframe-custom-widget](https://github.com/palantir/workshop-iframe-custom-widget) - Create custom widgets from applications that can read from and write to Workshop variables, as well ...

26. [Modernization success story: Palantir Foundry-powered ...](https://cadmusgroup.com/palantir-foundry-powered-transformation/) - Cadmus played a critical role in migrating legacy data and processes, re-engineering complex ETL fro...

27. [Palantir AIP trainings and enablement](https://10x-partners.com/clients/palantir-aip-trainings-and-enablement) - Designed and delivered a targeted training program for Palantir AIP, successfully enabling 200 IT pr...

28. [Palantir Foundry - Training, Implementation & Data Optimisation](https://www.applytosupply.digitalmarketplace.service.gov.uk/g-cloud/services/689117533248789) - Flexible training delivery for varying user adoption rates; Multiple training delivery modes - onsit...

29. [Implement Palantir Foundry for Government Missions - PVM](https://www.pvmit.com/services/government-palantir-foundry-implementation) - Accelerate your Palantir Foundry implementation with a trusted Palantir implementation Partner for U...

30. [Palantir: Baseline Team - Forward-Deployed Infrastructure ...](https://blog.palantir.com/the-baseline-team-and-forward-deployed-infrastructure-engineering-at-palantir-efd84e72e40b) - The Baseline team aims to reduce the complexity of our fleet as Palantir scales so that our product ...

31. [Foundry adoption • Phase 1: Focus on use cases - Palantir](https://palantir.com/docs/foundry/foundry-adoption/phase-1/) - During Phase 1, team members may take on multiple roles within the team or split their time between ...

32. [Phase 1: Focus on use cases • Roles and responsibilities - Palantir](https://palantir.com/docs/foundry/foundry-adoption/phase-1-roles/) - The following roles and responsibilities are suggestions based on experience working to develop Prog...

33. [DATA INTEGRATION PIPELINE](https://www.perplexity.ai/rest/file-repository/patents/US20160314155A1?lens_id=186-253-843-988-856) - publication_number: US20160314155A1
assignee: PALANTIR TECHNOLOGIES INC
abstract: A data integration...

34. [Systems and methods for facilitating data transformation](https://www.perplexity.ai/rest/file-repository/patents/US9946777B1?lens_id=010-659-523-250-315) - publication_number: US9946777B1
assignee: PALANTIR TECHNOLOGIES INC
abstract: Systems and methods ar...

35. [WORKFLOW APPLICATION AND USER INTERFACE BUILDER INTEGRATING OBJECTS, RELATIONSHIPS, AND ACTIONS](https://www.perplexity.ai/rest/file-repository/patents/US20230289153A1?lens_id=165-740-264-571-200) - publication_number: US20230289153A1
assignee: PALANTIR TECHNOLOGIES INC
abstract: Systems, technique...

36. [LANGUAGE MODEL-BASED DATA OBJECT EXTRACTION AND VISUALIZATION](https://www.perplexity.ai/rest/file-repository/patents/US20240354322A1?lens_id=089-172-479-855-801) - publication_number: US20240354322A1
assignee: PALANTIR TECHNOLOGIES INC
abstract: ...implemented met...

37. [SYNCHRONIZATION OF DATA ACROSS DIFFERENT ONTOLOGIES](https://www.perplexity.ai/rest/file-repository/patents/US20230103939A1?lens_id=064-461-282-320-671) - publication_number: US20230103939A1
assignee: PALANTIR TECHNOLOGIES INC
abstract: ...first ontology ...

