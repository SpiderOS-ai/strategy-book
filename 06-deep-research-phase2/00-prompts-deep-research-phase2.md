# Deep Research Prompts — Phase 2 : Reverse Engineering Complet Palantir

> Generés le 17 fév 2026, session 6
> À lancer dans Perplexity Pro Deep Research
> Objectif : reverse engineer la méthode complète Palantir, de l'avant-vente au support long-terme

---

## Prompt 1 — PRE-SALES & BOOTCAMP : Le playbook commercial complet, jour par jour

```
I want to fully reverse-engineer Palantir's pre-sales and AIP Bootcamp methodology with granular operational detail. Not strategy — I want the EXACT playbook an FDE team follows.

### PRE-SALES (Before the bootcamp)

1. **Prospecting & qualification**: How does Palantir identify and qualify prospects? What criteria make a company "bootcamp-ready"? What's the ICP (ideal customer profile)? Who initiates contact — inbound vs outbound? What role does the Account Executive play vs the Deployment Strategist at this stage?

2. **Pre-bootcamp preparation (2-4 weeks before)**:
   - What specific data does Palantir request from the client? In what format? (CSV dumps? API access? Database credentials? Read-only replicas?)
   - How do FDEs pre-build pipelines and ontology before Day 1? How much is ready before the client walks in?
   - How are the 3-5 use cases selected? Who decides — Palantir or client? What framework do they use to evaluate which use cases will have the most impact?
   - What "art of the possible" demos exist? Are they vertical-specific (healthcare, manufacturing, defense, finance)? Are they live on Foundry or pre-recorded?
   - What legal/security/NDA process happens before data sharing?
   - What's the internal Palantir staffing process? How is the bootcamp team assembled? Who picks the FDEs?

### BOOTCAMP (5 days)

For EACH DAY, I need:
- **Agenda**: Hour-by-hour if possible, or at minimum morning/afternoon blocks
- **Deliverables**: What tangible artifacts are produced by end of day?
- **Client interactions**: Who from the client is in the room? What are they doing (watching? co-building? presenting?)
- **Palantir team activities**: What is each role doing (FDE coding? DS facilitating? AE observing?)
- **Tools used**: Which Foundry tools are opened (Pipeline Builder? Ontology Manager? Workshop? AIP Logic?)
- **Decision points**: What decisions are made during the day that shape the rest of the week?

Specific questions per day:
- **Day 1**: What does "problem framing" look like concretely? Is there a structured workshop format (design thinking, jobs-to-be-done, process mapping on whiteboard)? What's the "art of the possible" demo — is it a live Foundry instance or slides? How do they show the client's OWN data already ingested?
- **Day 2-3**: What does "co-building" mean exactly? Are client engineers writing PySpark code? Or are they pointing at a screen while FDEs type? What's the ontology mapping process — do they use Ontology Manager UI, or code-first? What does the "working prototype end of Day 2" actually look like — a Workshop app? A dashboard? A notebook?
- **Day 4**: What does "stress testing" mean concretely? Who runs the scenarios? What format — live demo with domain experts asking questions? War-gaming? What are "edge cases" in this context?
- **Day 5**: What's in the executive presentation? Is there a standard deck template? How is ROI quantified — what formula? What does the "deployment roadmap" document look like? What commercial terms are discussed — pricing? Contract structure? Pilot scope?

### POST-BOOTCAMP (Weeks 1-6)

- What documents are delivered within 48 hours? Executive summary? Technical assessment? ROI projection? Proposed architecture?
- How long do prototypes stay accessible in the sandbox?
- What's the follow-up cadence? Weekly calls? On-site visits?
- How do they handle the ~78% that DON'T convert? Do they re-engage? When? How?
- What's the commercial proposal format? Is there a standard MSA/SOW template?

### EVIDENCE I'M LOOKING FOR:
- Blog posts from Palantir employees or FDEs describing bootcamp experiences
- Glassdoor reviews mentioning bootcamp processes
- Customer testimonials describing their bootcamp experience
- AIPCon presentations showing bootcamp methodology
- Palantir job descriptions for "Deployment Strategist" or "Forward Deployed Engineer" that describe bootcamp responsibilities
- Any leaked or public playbook documents
- Patent filings related to deployment methodology
- Interviews with Alex Karp, Shyam Sankar, or other executives describing the bootcamp process in operational detail
```

---

## Prompt 2 — PILOT IMPLEMENTATION : La méthode de déploiement 90 jours, artefact par artefact

```
I want to fully reverse-engineer Palantir's 90-day pilot deployment methodology — the "Acquire" phase. Not the business model — I want the EXACT process an FDE team follows to go from "signed pilot contract" to "production system running."

### WEEK-BY-WEEK BREAKDOWN

For each phase, I need:
- **Activities**: What does the FDE team physically DO each day?
- **Meetings**: Who do they meet with? How often? What format (standup, workshop, executive review)?
- **Artifacts produced**: What documents, code, configurations, or applications are created?
- **Client involvement**: Who from the client participates? What's expected of them?
- **Tools used**: Which Foundry components are used at each stage?
- **Decision points**: What choices shape the deployment?

### PHASE 1: DISCOVERY & DATA COLLECTION (Weeks 1-3)

1. **Stakeholder mapping**: Who do FDEs interview? How many interviews? What questions do they ask? Is there a structured interview guide?

2. **Process mapping methodology**:
   - How do FDEs map the client's business processes? Do they use a specific framework (value stream mapping, BPMN, swimlane diagrams)?
   - Do they literally walk the factory floor / hospital ward / trading desk? How much time is spent observing vs interviewing?
   - What artifacts come out of process mapping? Process diagrams? Data flow diagrams? Entity-relationship diagrams?
   - How do they identify which processes are "ontology-worthy" vs noise?

3. **Data discovery & inventory**:
   - How do FDEs catalog the client's data sources? Is there a data inventory template?
   - What questions do they ask data owners? ("What system is this in? How often is it updated? Who has access? What format?")
   - How do they assess data quality? Is there a scoring framework?
   - How do they handle the "data access politics" problem concretely? What's the negotiation playbook for getting access from hostile gatekeepers?

4. **Use case prioritization**:
   - After discovery, how do they narrow down to the first 1-3 use cases?
   - What criteria? (ROI potential, data readiness, champion strength, expansion potential)
   - Is there a scoring matrix? A formal framework?

### PHASE 2: ONTOLOGY DESIGN & DATA INTEGRATION (Weeks 2-6)

5. **Ontology design process**:
   - How does an FDE decide what becomes an Object Type vs a Property vs a Link?
   - Is there a design document template? An ontology schema diagram?
   - How do they name things? Is there a naming convention?
   - Do they show the ontology design to the client for validation? In what format?
   - How many iterations does the ontology go through before stabilizing?

6. **Data pipeline construction**:
   - What's the step-by-step process for building a pipeline in Foundry?
   - Do FDEs use Pipeline Builder (visual) or Code Repositories (PySpark/Python)?
   - What does a typical transform look like? (e.g., "read from SAP BAPI, extract customer records, clean phone numbers, map to Customer Object Type")
   - How is data quality handled? Automated validation? Manual review? Both?
   - What's the testing process for pipelines? Unit tests? Integration tests?

7. **Data source connection**:
   - How does the connector setup work technically? (Install an agent? VPN? Direct DB connection? API key?)
   - How long does it typically take to connect one data source?
   - What are the most common failure modes? (Firewall issues? Schema changes? Rate limiting?)

### PHASE 3: ACTIONS, SECURITY & APPLICATION (Weeks 4-10)

8. **Action Type design**:
   - How do FDEs identify which user actions to model?
   - What's the process: interview users about "what do you DO with this data?" → map to Action Types?
   - How are validation rules designed? Who decides the business rules?
   - How is the writeback configured? (Webhook URL? Source system API? Direct DB write?)

9. **Security configuration**:
   - How is RBAC set up concretely? Is there a questionnaire for the client? ("Who should see what?")
   - How is row-level security implemented? Property-level? Cell-level?
   - What's the testing process for security policies?

10. **Application building**:
    - How does Workshop work step-by-step? What widgets are available?
    - How do you bind a table widget to an Object Type? A button to an Action?
    - Who designs the UI — the FDE? A designer? The client?
    - How many iterations does a Workshop app go through?
    - How do they decide between Workshop (low-code) vs Slate (custom frontend) vs Quiver (analytics)?

### PHASE 4: USER TRAINING & HANDOFF (Weeks 8-12)

11. **Training methodology**:
    - How do they train end users? Classroom? 1-on-1? Video? Documentation?
    - What training materials are produced?
    - How many hours of training per user role?
    - Do they identify "power users" / "citizen developers"?

12. **Go-live process**:
    - Is there a formal go-live checklist?
    - How is the transition from "FDE-operated" to "client-operated" managed?
    - What monitoring is set up? Alerts? Dashboards?
    - What's the support model post go-live? SLA? On-call FDE?

13. **Success measurement**:
    - How do they measure pilot success? What KPIs?
    - Who presents results to the client executive?
    - What's in the "business case for expansion" document?

### EVIDENCE I'M LOOKING FOR:
- Nabeel Qureshi's blog posts about FDE methodology (he wrote extensively about his 8 years at Palantir)
- Job descriptions for FDE, Deployment Strategist, Solutions Architect that detail responsibilities
- Palantir developer documentation (docs.palantir.com) describing Pipeline Builder, Ontology Manager, Workshop
- AIPCon customer presentations showing implementation timelines
- Case studies with specific timelines and artifacts mentioned
- Patent filings related to ontology creation, pipeline building, or deployment methodology
- Engineering blog posts on palantir.com/blog or medium.com
- Foundry documentation or OSDK documentation
```

---

## Prompt 3 — EXPAND & SCALE : Comment ils rendent le client captif puis autonome

```
I want to fully reverse-engineer Palantir's post-pilot methodology — the "Expand" and "Scale" phases. How does a $100K pilot become a $5.6M enterprise platform? What's the EXACT playbook for making a client both captive and autonomous?

### EXPAND PHASE (Year 1-3, $250K → $1-5M ACV)

1. **Expansion trigger identification**:
   - How do FDEs systematically identify expansion opportunities?
   - Is there a formal "use case backlog" process?
   - Do they run "Build with AIP" bootcamps for existing customers? How do these differ from initial bootcamps?
   - When attendees "identify 100 use cases" — how is this facilitated? Is it a brainstorming workshop? Post-it exercise?
   - How do they prioritize which department to expand into next?

2. **Cross-department ontology expansion**:
   - How does the ontology grow from 1 department to 3-5?
   - What are the technical challenges? (conflicting entity definitions, duplicate data, security boundaries between departments)
   - How do they handle "the same customer exists in both Sales CRM and Finance ERP with different IDs"? Entity resolution methodology?
   - Is there an ontology governance process? Who approves new Object Types?

3. **Center of Excellence (CoE) formation**:
   - At what point does the CoE get formed? (Month 6? Month 12? After how many users?)
   - What's the formation process? Who initiates — Palantir or client?
   - What's the training curriculum for each CoE role?
     - Platform Owner: what training? How long?
     - Ontology Steward: what skills needed? How do they learn ontology design?
     - Data Engineers ("South team"): what Foundry skills do they need?
     - App Developers ("North team"): Workshop certification? What's the learning curve?
     - Permissions Manager: RBAC configuration training?
   - Does Palantir offer formal certification programs?
   - How often does the CoE meet? What's the governance cadence?

4. **Champion cultivation playbook**:
   - How does Palantir systematically cultivate internal champions?
   - What events/programs do they invite champions to? (User groups? Annual conference? Executive dinners?)
   - How do they arm champions with ROI data to present internally?
   - What happens when a champion leaves the organization?
   - How do they create "champion redundancy" (multiple advocates)?

5. **Commercial expansion mechanics**:
   - How is expansion pricing structured? Per-user? Per-use-case? Platform tier?
   - Are expansion terms pre-negotiated in the initial contract?
   - Is there a "land" price and a different "expand" price?
   - How do contract renewals work? Auto-renew? Annual negotiation?
   - What's the role of the Account Executive vs Deployment Strategist in expansion?

### SCALE PHASE (Year 3+, $5M-20M+ ACV)

6. **FDE withdrawal process — "The Graduation"**:
   - How does Palantir reduce FDE presence without losing the client?
   - What's the timeline? Gradual reduction over months? Hard cutover?
   - What capabilities must the client demonstrate before FDE withdrawal?
   - What support model replaces FDE on-site presence? (Support tickets? Office hours? Quarterly reviews?)
   - How do they prevent "withdrawal anxiety" — client feeling abandoned?

7. **Self-service enablement**:
   - How does a client go from "FDE builds everything" to "client builds 70-85% of apps"?
   - What training programs enable this transition?
   - What's the self-service tooling? (Workshop + AIP = citizens can build apps?)
   - How long does it take to reach self-service? (Airbus: 2-3 years, Army: longer — why the difference?)
   - What's the failure rate? Do some clients NEVER reach self-service?

8. **Stickiness & lock-in mechanics** (the honest version):
   - What specifically makes Palantir hard to leave? Break it down:
     - Data integration dependencies (how many systems connected?)
     - Ontology complexity (how many Object Types? How interconnected?)
     - Application dependencies (how many apps built on the ontology?)
     - Institutional knowledge captured (decision logs, user edits, audit trails)
     - Security configuration complexity (RBAC policies, markings)
     - Training investment (CoE team, citizen developers)
   - What's the estimated cost to switch away? ($2.5-7.5M is cited — what's the breakdown?)
   - Has any large customer successfully left Palantir? What happened?
   - How does Palantir respond to churn threats? Price concessions? Additional FDE support?

9. **Support model at scale**:
   - What does ongoing Palantir support look like for a Scale-phase customer?
   - Is there a tiered support model? (Bronze/Silver/Gold?)
   - What SLAs exist? Response times? Resolution times?
   - How are platform updates managed? (Apollo pushes updates — does the client control timing?)
   - What's the quarterly/annual business review format?

10. **Palantir's revenue protection playbook**:
    - How do they protect against competitor displacement at renewal?
    - How do they handle Microsoft Fabric / Databricks encroachment?
    - What's the "defensive expansion" strategy — expanding ontology to make switching harder?
    - How do they justify premium pricing vs open-source alternatives?

### EVIDENCE I'M LOOKING FOR:
- Customer case studies with multi-year timelines (Airbus Skywise, BP, NHS, US Army, Lear Corporation)
- Former customer or FDE testimonials about expansion/scale phases
- Palantir investor presentations with cohort economics
- Job descriptions for "Customer Success Manager" or "Platform Support Engineer"
- Documentation about Palantir's support portal or help desk
- Contract terms visible in government procurement databases (USAspending.gov, G-Cloud, GeBIZ)
- Competitor analyses mentioning Palantir switching costs
- Analysis from Gartner, Forrester, or IDC about Palantir's customer lifecycle
```

---

## Prompt 4 — FOUNDRY TOOLS CONCRET : Comment Workshop, Pipeline Builder, Ontology Manager marchent vraiment

```
I want to understand HOW Palantir Foundry's core tools actually work at the UI and implementation level. Not marketing — I want the actual user experience of building with Foundry.

### ONTOLOGY MANAGER

1. **Creating an Object Type step-by-step**:
   - What does the Ontology Manager UI look like? (Screenshots if available)
   - How do you create a new Object Type? (Click "New" → name it → select backing dataset → map columns to properties?)
   - How do you define Properties? (Data types available: string, integer, float, date, timestamp, geohash, struct, array, attachment, marking, etc.)
   - How do you create Link Types between Object Types? (Select source Object Type → define relationship type → select target → set cardinality)
   - How do you define Interfaces (abstract types that multiple Object Types can implement)?
   - How do you define Functions (TypeScript computed properties)?

2. **Decision framework — Object vs Property vs Link**:
   - When does an entity deserve its own Object Type vs being a Property of another object?
   - Example: "Customer Address" — is it a Property of Customer, or a separate Address Object Type linked to Customer?
   - What are the guidelines Palantir teaches FDEs?
   - When do you use a Struct (nested object) vs a linked Object Type?

3. **Schema evolution**:
   - How do you modify an existing Object Type? (Add property? Rename? Change type?)
   - What's the "replacement pipeline" pattern for breaking schema changes?
   - How do you handle migrations? Is there a migration tool or is it manual?

### PIPELINE BUILDER

4. **Visual pipeline creation**:
   - What does the Pipeline Builder UI look like?
   - How do you create a new pipeline? (Select input dataset → add transform nodes → configure output)
   - What transform nodes are available? (Filter, Join, Aggregate, Pivot, Union, Custom Code, etc.)
   - Can you mix visual nodes with code (PySpark)?

5. **Code-based pipeline creation (Code Repositories)**:
   - What's the Palantir-specific Python API? (The @transform decorator, Input/Output objects, IncrementalTransformInput)
   - What does a real transform look like? (Read from Source A, join with Source B, clean, write to ontology-backing dataset)
   - How do you schedule pipelines? (Cron? Event-driven? On data arrival?)
   - How do you handle incremental processing vs full recomputation?
   - What testing frameworks exist for pipeline code?

6. **Data lineage**:
   - How is lineage automatically tracked? (Does Foundry record every transform's input→output?)
   - What does the lineage graph visualization look like?
   - Can you trace a specific value back to its raw source?
   - How does lineage interact with security markings?

### WORKSHOP (Application Builder)

7. **Building an application step-by-step**:
   - What does Workshop look like? (Canvas with drag-and-drop widgets?)
   - What widgets are available? (Table, Chart, Map, Form, Button, Text, Filter, Timeline, KPI Card, etc.)
   - How do you bind a Table widget to an Object Type? (Select Object Type → choose which Properties to show as columns → configure sorting/filtering)
   - How do you add an Action button? (Select Action Type → configure which properties are editable → set validation display)
   - How do you create a filter that narrows down objects? (Property filter? Geo filter? Date range?)
   - How do you link multiple widgets together? (Click a row in Table A → filters Table B to show related objects?)

8. **Workshop vs Quiver vs Contour vs Slate**:
   - Workshop: operational applications (forms, workflows, action buttons). When?
   - Quiver: dashboards and KPIs. How is it different from Workshop charts?
   - Contour: ad-hoc data exploration. What can you do that Workshop/Quiver can't?
   - Slate: custom HTML/JS/CSS applications. When do you need this over Workshop?
   - Is there a decision matrix Palantir teaches?

### AIP (AI Integration Platform)

9. **AIP Logic**:
   - How do you create an AIP Logic function? (Natural language → code generation → test → deploy?)
   - How does AIP access Ontology objects? (Receives typed objects, not raw data — what does this look like in code?)
   - How do you constrain what an AI agent can DO? (Action permissions, guardrails, approval workflows)
   - What's the "AIP Assist" experience in Ontology Manager and Workshop?

10. **OSDK (Ontology SDK)**:
    - What is OSDK exactly? (TypeScript/Python client for external apps to query/modify ontology)
    - How do you generate the SDK? (Auto-generated from ontology schema?)
    - What does a typical OSDK query look like in TypeScript?
    - How do external apps (custom web frontends, mobile apps) consume ontology data via OSDK?

### APOLLO (Deployment)

11. **How Apollo works**:
    - What is Apollo's architecture? (Central management plane + customer-side agents?)
    - How does it push updates to 300+ environments simultaneously?
    - How does a customer control which updates they accept? (Automatic? Manual approval? Staged rollout?)
    - How does it handle air-gapped / classified networks? (Sneakernet? Secure transfer? Physical media?)
    - What's the release cadence? (Daily patches? Weekly features? Quarterly major?)
    - What rollback mechanisms exist?

### EVIDENCE I'M LOOKING FOR:
- Palantir developer documentation at docs.palantir.com
- Foundry training materials or certification program content
- YouTube videos showing Foundry/Workshop/Pipeline Builder in action (AIPCon demos, customer demos)
- OSDK documentation and code examples (GitHub: palantir/osdk-ts, palantir/foundry-platform-typescript)
- Engineering blog posts from palantir.com/blog
- Developer community posts (Stack Overflow, Reddit r/palantir)
- Patent filings describing UI mechanisms
- Job descriptions that mention specific Foundry tools
- Third-party review sites (G2, Gartner Peer Insights) with detailed feature descriptions
```

---

## Instructions pour Nathan

1. Lancer les 4 prompts dans Perplexity Pro (Deep Research)
2. Sauvegarder les résultats dans `04-external-deep-research/` :
   - `deep-research-report-8-presales-bootcamp-playbook.md`
   - `deep-research-report-9-pilot-implementation-methodology.md`
   - `deep-research-report-10-expand-scale-captivity-playbook.md`
   - `deep-research-report-11-foundry-tools-concrete-ux.md`
3. Si Perplexity génère des Compass artifacts, les sauver aussi :
   - `compass-bootcamp-playbook.md`
   - `compass-pilot-methodology.md`
   - `compass-expand-scale.md`
   - `compass-foundry-tools.md`
4. Me redonner la main pour synthétiser et enrichir le blueprint
