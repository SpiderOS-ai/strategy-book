# Reverse-engineering Palantir’s 90-day pilot “Acquire” deployment playbook

## What “Acquire” means in practice and what is knowable publicly

You asked for the exact internal playbook an FDE team follows from signed pilot contract to a production system. Palantir does not publish a single authoritative “Acquire phase” runbook with day-by-day instructions. What can be reverse-engineered with high confidence is the operating system implied by publicly available artefacts: Palantir’s own Foundry documentation (which is unusually explicit about how they expect teams to structure work, pipelines, ontology, security, and release), role descriptions for Forward Deployed Software Engineers and Deployment Strategists (which describe who they meet and what they deliver), and first-hand descriptions of forward deployed work emphasising on-site immersion and rapid iteration. citeturn7view0turn9view0turn6view3turn19view1turn20view0

Two public signals matter because they explain why a 90-day pilot is even plausible:

Palantir’s forward deployed model is explicitly about embedding with customers and rapidly turning messy workflow context into operational software, not just analysis. Public writeups of the model describe capturing “tacit knowledge” by being on-site and watching real work, then shipping “best practice” operational UIs quickly. citeturn6view0turn6view3

Palantir’s Foundry documentation frames use case delivery as building foundations first: a robust pipeline, a practical object model in the ontology, and reusable interfaces for decision capture. That sequencing aligns with delivering a production workflow in weeks rather than quarters. citeturn20view1turn3view4turn3view8turn3view5

This report reconstructs a week-by-week Acquire-style pilot that is consistent with: (a) what Palantir says Deployment Strategists and FDSEs do on-site, (b) Foundry’s documented “use case lifecycle” artefacts and recommended development sequence, and (c) the platform’s concrete mechanics for data connection, pipelines, ontology, actions, application building, governance, and monitoring. Where Palantir is not explicit publicly (for example, “how many interviews” or a proprietary scoring matrix), I provide a best-fit reconstruction and label it as inferred. citeturn9view0turn7view0turn20view0turn19view1turn14view1

## Week-by-week breakdown from signed pilot to production system running

The key to making “week-by-week” real is to describe not just phases, but the repeatable cadence the team runs: daily user contact, frequent demos, and a bias to get a thin operational loop live fast, then harden. Public descriptions highlight that forward deployed teams are expected to embed deeply with customer workflows and win trust by delivering a “kernel of value” quickly. citeturn6view3turn7view0turn9view0

### Week 1: Kickoff, scoping, access path, and the first usable slice

Activities  
The team starts by turning the pilot contract into an execution scope with explicit decisions, users, and outcomes. Foundry’s use case lifecycle documentation literally provides a use case overview template and a canonical functional-requirements format: `[User Type] [Interface] [Decision] [Decision Inputs] [Action]`. That is a strong hint that Palantir-style deployments are decision-centric, not “requirements list” centric. citeturn20view0turn19view1  
In parallel, engineering begins environment readiness on the customer side: identify the first 1–2 data sources that can be connected fast and validate which network path applies (direct connectivity vs agent on a separate network). Foundry’s Data Connection docs show that “set up a source” requires (1) network connection, (2) credentials, (3) agent drivers if using agent worker compute, then creation of the source in the Data Connection UI. citeturn15view3turn14view1turn15view2

Meetings  
A formal kick-off usually includes: executive sponsor, operational owner, IT/security counterpart, and analysts or operators. This mirrors Palantir’s role expectations: FDSEs engage stakeholders from technical teams to executives; Deployment Strategists go on-site to meet customer analysts and locate the biggest pain points. citeturn7view0turn9view0  
You should expect daily working sessions with real users beginning immediately, because the deployment model is based on immersion in “how they work”, not hand-offs. citeturn6view0turn6view3

Artifacts produced  
A first “use case overview” and initial functional-requirements list in the documented format; an initial stakeholders/counterparts map (who cares and why); an access plan listing data sources, owners, credentials needed, and which network pattern will be used. Foundry explicitly encourages capturing collaborative technical writing using Notepad and storing documentation in a Project. citeturn20view0turn15view3

Client involvement  
You need a single accountable sponsor, an operational “process owner”, and at least one analyst/operator who does the work daily. IT/security must assign an owner for network policy and identity, because Foundry’s Data Connection requires specific roles to configure network egress policies in Control Panel in some cases. citeturn15view3turn14view1

Tools used  
Notepad (documentation) is explicitly recommended in the use case lifecycle docs. Data Connection is used to begin source setup (agents if needed). citeturn20view0turn15view3turn14view1

Decision points  
Pick the pilot “thin slice”: one user role, one interface, one decision, one action. This is consistent with Foundry’s approach of mapping functional requirements to components (object model, lifecycle diagram of actions, enrichments, interface expectations). citeturn19view1turn20view0  
Decide whether the first source is cloud/SaaS reachable directly or requires an on-prem agent. citeturn15view3turn14view1

### Week 2: On-site workflow immersion, process capture, first source connected, ontology sketch begins

Activities  
The team embeds with operational users to observe the workflow end-to-end and extract the “decision moments” and state changes. Public descriptions of forward deployed work emphasise going on-site to capture tacit knowledge that typical enterprise software misses. citeturn6view0turn6view3  
Data engineers push hard to get the first source connected: if an agent is required, Foundry documents the agent as a downloadable program installed inside the organisational network, managed from Foundry, used to connect to sources and securely ingest with restricted access tokens. This includes practical infrastructure steps: provisioning a Linux host, configuring egress and ingress, validating connectivity, and setting automatic restarts. citeturn14view1

Meetings  
Daily shadowing or “sit-with” sessions with operators; paired sessions with data owners; and IT/security sessions around network paths and credentials. Deployment Strategist responsibilities explicitly include identifying relevant datasets through deep engagement with workflows and working with FDSEs to integrate data into a stable and extensible pipeline. citeturn9view0turn15view3turn14view3

Artifacts produced  
A first pass at: object model sketch, lifecycle diagram, and enrichments list. Palantir’s “solution design” documentation names these as standard components extracted from functional requirements. citeturn19view1  
A “source setup” record: which source type, where it is saved (Project), credentials model (service account), and whether compute runs as Foundry worker or agent worker. Foundry’s source setup flow includes choosing Foundry worker vs agent worker explicitly. citeturn15view2turn15view1

Client involvement  
Operators must let the team observe exceptions and workarounds, not just happy paths. Data owners must provision service accounts; Foundry recommends dedicated service accounts scoped specifically for required access. citeturn15view2  
Security/IT must implement ingress and egress rules if using agents or restricted network access patterns. citeturn14view1turn15view3

Tools used  
Data Connection: agents, sources. Ontology work starts as sketches but will be implemented in Ontology Manager and the ontology toolchain soon. citeturn14view1turn3view3turn3view8

Decision points  
Decide which concepts are “core” vs “derived” vs “use case objects”. Foundry’s solution design guidance explicitly distinguishes core ontology concepts mapped to systems of record from derived concepts produced in transforms, and operational/use-case object types edited via workflows (for example, alert tickets). citeturn19view1

### Week 3: Data inventory filled out, use cases narrowed, first pipeline and object types land

Activities  
The team expands from “first source connected” to “first dataset reliably syncing” and the start of pipeline development. Foundry documents that setting up a batch sync creates a Foundry dataset, can be run manually or scheduled, and supports file syncs and table syncs with different transaction types like SNAPSHOT vs APPEND, plus options like “allow schema changes”. citeturn14view3turn15view2  
Pipeline work begins with Foundry’s recommended initial steps: establish project structure, create a batch pipeline in Pipeline Builder or Code Repositories to clean/filter/join into high-quality datasets, map final datasets into ontology object types and link types, then set schedules so data flows regularly. citeturn3view4turn17search13

Meetings  
Working sessions converge into a weekly prioritisation checkpoint: pick the first 1–3 use cases to implement as the pilot’s visible outcomes. The Deployment Strategist role explicitly includes presenting results and proposals for future work to audiences up to C-suite, so even at pilot stage the operating model expects an executive-facing narrative and next-step proposal. citeturn9view0

Artifacts produced  
A completed v1 use case brief: decisions, counterparts, functional requirements, outcomes/KPIs, pain points. This is directly aligned to the “use case overview template” in Foundry docs. citeturn20view0  
A first pipeline skeleton and first ontology entities. Pipeline Builder supports adding “Ontology outputs” to guide integration toward clean, structured data; it includes explicit object type naming fields where plural name and object type ID auto-populate from the name, and object type IDs become immutable after the first deploy. citeturn3view7turn16search8

Client involvement  
Client leaders must make the prioritisation choice. Operators validate whether the proposed first workflow is usable. Data owners validate early data semantics and exceptions.

Tools used  
Data Connection for syncs; Pipeline Builder or Code Repositories for transformations; Ontology Manager to start implementing object types and links; scheduling for regular updates. citeturn14view3turn3view4turn3view3turn12view5

Decision points  
Choose Pipeline Builder vs Code Repositories for the first pipelines. Foundry’s “considerations” documentation positions Pipeline Builder as a graph/form environment enabling collaboration and a rigorous release process without code, versus Code Repositories for code-first pipelines. citeturn17search25  
Choose batch vs incremental vs streaming shapes for data based on latency and scale needs; Foundry explicitly distinguishes these and warns incremental pipelines add complexity. citeturn3view4

### Week 4: Ontology scaffolding becomes real, first interface skeleton, branching discipline begins

Activities  
The team converts sketches into a working ontology and a barebones operational application. Foundry’s solution design doc gives a concrete mapping: a stand-alone inbox application is typically a Workshop project; object views should unify context and actions; executive dashboards may start as Quiver templates; Carbon can unify navigation across user types. citeturn19view1turn3view5  
Engineering also puts a release discipline in place. Foundry has a branching model where branches can be created in Code Repositories, Pipeline Builder, Ontology Manager, and Workshop, and changes are merged through proposals with reviewers depending on approval policies. citeturn3view9turn17search15turn17search11

Meetings  
A weekly demo becomes non-negotiable: show operators something that runs, even if rough. This is consistent with public descriptions that customers notice when teams build usable software within a week or two. citeturn6view3  
Parallel reviews: ontology review with SMEs, and data review with data owners.

Artifacts produced  
Ontology v1: object types, properties, link types. Foundry defines link types as schema definitions of relationships between object types; links are instances, analogous to joins between datasets. citeturn21search0turn3view8  
Workshop module v0: layouts, variables, and a first “inbox/table” view pattern. Workshop is explicitly designed for interactive operational apps, including inbox/task management patterns, built on a unified design system and events system. citeturn3view5

Client involvement  
Operators participate in tight feedback loops. IT/security validates that early access patterns comply with policy. Exec sponsor attends demo to keep priority clear.

Tools used  
Ontology Manager; Workshop; Foundry Branching and proposal flow; pipelines and schedules. citeturn3view3turn3view5turn3view9turn12view5

Decision points  
Lock the ontology’s “core”: what is a first-class object type vs an attribute vs a derived roll-up. Foundry encourages identifying primary keys and link cardinality in the object model sketch and tracing core concepts to systems of record. citeturn19view1  
Decide which enrichments belong in the data layer vs inside the app. Foundry offers a heuristic: if an enrichment does not rely on data that can change via user Actions, implement it in the data layer for reuse and performance. citeturn19view1

### Week 5: Pipelines harden, data quality checks start, actions are defined as a state machine

Activities  
Pipeline work expands from “it runs” to “it is stable”: schedules, health checks, and early test coverage. Foundry exposes multiple quality guardrails: Pipeline Builder unit tests (predefined inputs and expected outputs) that must pass before merging proposals, plus health checks for freshness/build success/duration, plus code-defined “data expectations” that can abort builds on failure to prevent bad data propagating. citeturn17search0turn17search10turn17search4  
The team designs Action Types by translating the lifecycle diagram into concrete actions that create/modify/delete objects. Foundry’s solution design explicitly frames lifecycle as a state machine diagram of Actions that transition an object between states. citeturn19view1

Meetings  
Workshops with operators specifically about “what do you do next”: this is where actions, validations, and write-back needs get clarified. Ontology/action review with business owners.

Artifacts produced  
Lifecycle diagram v1 mapped to Action Types; validation rules list; pipeline unit tests and health checks configured; scheduled syncs and builds. citeturn19view1turn14view3turn17search0turn17search1

Client involvement  
Business owners define what actions are allowed and in what states; ops SMEs validate edge cases. Data owners validate that the pipeline produces canonical objects, not duplicates.

Tools used  
Pipeline Builder or Code Repositories; unit tests; Data Health/health checks; Ontology Manager action types; Workshop integration. citeturn17search0turn17search10turn3view3turn3view6turn3view5

Decision points  
Decide the minimum viable action set for production: usually one approval/triage loop, not every possible exception. Decide whether write-back is required in the pilot or can be simulated; this choice changes risk and stakeholder alignment.

### Week 6: Ontology stabilisation, security model chosen, second source improves realism

Activities  
The team extends the ontology and integration coverage enough that the system reflects the real workflow, not a toy. That often requires a second source. Foundry’s “set up a source” process highlights that on-prem or separate-network sources require an agent, and that network policy configuration in Control Panel may require privileged roles. citeturn15view3turn14view1  
Security becomes concrete, because operational pilots usually fail when access is too open or too restrictive. Foundry’s security model is built around Projects as the primary security boundary, with roles granted to users and groups. Markings add eligibility constraints. citeturn16search9turn16search28

Meetings  
Security workshops with IT/security and the operational owner: “who should see what” translated into groups, roles, and object-level policies. Daily operator feedback continues.

Artifacts produced  
RBAC and governance map expressed as: Projects, roles, groups, and markings. Foundry documentation explicitly explains Projects and roles as discretionary access control. citeturn16search9turn16search10turn16search28  
Object-level security configuration approach selection: restricted views and granular policies vs object security policies. Granular policies are described as enabling row-level security for datasets and objects; object security policies provide row-level security for object instances, and property security policies provide column-level security. citeturn16search1turn16search4turn16search7turn16search3

Client involvement  
IT/security must supply group definitions and user attributes if row-level rules depend on them. Operational leadership must accept tradeoffs in early scope.

Tools used  
Security and governance tooling; object permissioning; granular policy management; Projects and roles; markings. citeturn16search2turn16search1turn16search9turn16search28

Decision points  
Choose how you will do row-level enforcement: restricted views vs object security policies. Note that restricted views have important limitations: Foundry documentation warns they cannot be used as inputs to data transformations because pipelines must be reproducible and user-agnostic. citeturn16search6turn16search7  
Decide whether sensitive attributes are protected via column-level policies (property security policies) or via separate object modelling. citeturn16search4turn16search0

### Week 7: Write-back and integrations, operational workflow becomes end-to-end

Activities  
The team implements write-back where value requires it. Foundry supports outbound Webhooks configured in Data Connection to connect Foundry apps to external systems; documentation explicitly describes triggering an HTTP request when a user selects a button in a Foundry application, associating the webhook with a Source that stores credentials, and applying concurrency and rate limits. citeturn14view5  
In parallel, actions are wired into the UI. Foundry’s action documentation explains how actions can be added as buttons in object views, configured with default parameter values, and set to be hidden/disabled if non-visible parameters are invalid. citeturn3view6

Meetings  
Integration review with owners of downstream systems of action: API owners, DB owners, security owners. User testing sessions on “can you complete the workflow start to finish”.

Artifacts produced  
Webhook configurations; action forms; UI events wiring; audit and logging expectations (at least to the extent the platform exposes). citeturn14view5turn3view6turn3view5

Client involvement  
System owners must provide endpoints, credentials, and acceptance criteria. Security must approve outbound connections, rate limiting, and auditability constraints.

Tools used  
Data Connection Webhooks; action types; Workshop. citeturn14view5turn3view6turn3view5

Decision points  
Decide whether write-back is synchronous (webhook call per action) or staged (queue and later reconciliation). Public docs cover webhooks and action integration but do not mandate a single pattern; this is a design choice. citeturn14view5turn3view6

### Week 8: Pilot training wave, UAT, monitoring and on-call posture

Activities  
The team shifts from building for a few power users to training broader roles and making reliability visible. Deployment Strategists are explicitly expected to lead training sessions and ensure the product is used widely enough to have concrete operational impact. citeturn9view0  
Operational readiness work begins: health checks, monitoring views, alert routing. Foundry supports monitoring views as collections of monitoring rules and health checks, and can send alerts to external systems including PagerDuty, Slack, and webhooks. citeturn17search12turn17search7turn17search14

Meetings  
Role-based training sessions; UAT sign-off with process owner; monitoring and support process review.

Artifacts produced  
Training materials, role guides, and runbooks. Foundry’s Learning portal and training tracks exist, but your pilot-specific assets will be bespoke. The platform also provides notifications and can auto-create issues on check failures, supporting a support workflow. citeturn21search22turn17search5turn17search16

Client involvement  
Client designates “power users” and a support counterpart. Client agrees escalation path for data outages and integration failures.

Tools used  
Data Health, monitoring views, notifications and issues; plus Workshop for guided operational use. citeturn17search2turn17search12turn17search5turn3view5

Decision points  
Define the “production” standard for the pilot: acceptable latency, freshness, uptime, and manual fallback. This is where you explicitly choose which checks are critical vs warning. citeturn17search1turn17search10turn17search14

### Week 9: Scale to more users, strengthen governance, performance and usability iteration

Activities  
Iterate based on real usage data and feedback. The team uses branching to evolve pipelines, ontology, and apps with controlled merges. Foundry branching supports proposals, merge checks, and reviewer assignment depending on resource type and approval policy. citeturn3view9turn17search11turn17search6  
Improve app usability: Workshop supports rich widget patterns (tables, object views, buttons, inline actions, filters) and an events system; documentation frames Workshop apps as more interactive than standard dashboards and suitable for operational task management. citeturn3view5turn9view3turn16search11

Meetings  
Weekly exec/steering update; operator retrospectives; governance check-ins.

Artifacts produced  
Versioned releases; updated unit tests; refined enrichments and metrics; expanded training guides.

Client involvement  
Operational owner drives adoption; IT participates in governance hardening.

Tools used  
Branching, approvals, Workshop, pipelines. citeturn17search15turn3view5turn3view4

Decision points  
Decide what becomes reusable platform capability vs pilot-specific hacks. Public descriptions of Palantir’s model note that forward deployed teams optimise for speed and may accept technical debt; product teams later “productise”. Even in your reverse engineering, this implies a conscious “what to harden now” decision. citeturn6view3turn7view0

### Week 10: Production hardening and cutover planning

Activities  
Operationalise release process and rollback posture. Foundry provides explicit best-practice documentation around branching and release process, and highlights that production pipelines should use branching and a release process if not already used during development. citeturn17search3turn17search24  
Strengthen monitoring, alerting, and support processes. Foundry’s recommended support processes include subscribing to monitoring views and integrating with external alerting tools that can manage on-call rotations. citeturn17search16turn17search7

Meetings  
Go-live readiness review with IT/security and ops leadership; runbook walkthrough; cutover rehearsal.

Artifacts produced  
Go-live checklist (inferred, but directly grounded in Foundry capabilities): schedules confirmed; health checks configured; monitoring view subscriptions set; alert routing tested; rollback plan; access/permissions validated; runbooks published. Supporting primitives are explicitly documented (schedules, health checks, monitoring views, notifications). citeturn14view3turn17search10turn17search12turn17search5

Client involvement  
Client nominates “system owner” and “data owner” for post go-live. IT confirms support boundaries.

Tools used  
Schedules, health checks, monitoring views, notifications, issues. citeturn17search10turn17search12turn17search5

Decision points  
Define who owns what post go-live: who responds to failed syncs, failing builds, failing checks, and failed write-backs.

### Week 11: Go-live, hypercare, and transition from FDE-run to client-run

Activities  
Controlled rollout: limited user cohort first, then broader access. Monitor checks actively and address failures with the designed support process. Foundry supports watcher notifications and issue creation on check failures, aiding operational triage. citeturn17search18turn17search5

Meetings  
Daily “hypercare” stand-up with client ops lead; incident review if outages occur; weekly executive update focused on impact.

Artifacts produced  
Incident log; changes merged through branching proposals; updated training and FAQ.

Client involvement  
Client operators use the system in real work. Client IT runs the first-line support motions with coaching.

Tools used  
Data Health; monitoring; branching. citeturn17search2turn17search15turn3view9

Decision points  
Decide whether the pilot’s production system is “good enough” to deprecate the old process. Palantir’s own use case example claims Foundry replaced an existing system and process within 6 weeks for a logistics consolidation workflow, illustrating the ambition to fully replace, not just augment, within pilot-like timescales. citeturn19view0

### Week 12: Prove impact and package the expansion case

Activities  
Measure outcomes against the KPIs defined in the use case overview. Foundry’s use case lifecycle template explicitly demands “outcomes and KPIs” as part of functional scoping. citeturn20view0  
Package the architecture and operating model for expansion. Solution Designer exists specifically to create architectural representations of Palantir-platform solutions, compare proposals, and support knowledge transfer and onboarding. citeturn9view3

Meetings  
Executive readout: impact, what changed operationally, and what to build next. Deployment Strategists are expected to present results and proposals for future work to audiences ranging up to C-suite. citeturn9view0

Artifacts produced  
Impact report and expansion roadmap. If the pilot mirrors Foundry’s own published use case examples, impact metrics tie directly to operational outcomes: savings, throughput, utilisation improvements, decision cycle time reductions. citeturn19view0

Client involvement  
Exec sponsor decides whether to expand. Operational owner commits to governance and adoption model.

Tools used  
Dashboards and reporting can be built in Foundry’s application layer. Foundry’s solution design doc explicitly notes executive dashboards might start as Quiver templates and evolve. citeturn19view1

Decision points  
Decide whether expansion is horizontal (more use cases) or vertical (same workflow scaled across sites/functions). The documented sequencing guidance emphasises building foundational assets first so that multiplier technologies and broader workflows unlock later. citeturn20view1

## Discovery and data collection mechanics for weeks 1 to 3

### Stakeholder mapping

What public evidence says  
Palantir’s documentation does not prescribe a numeric “X interviews in week 1”, but it does prescribe the content you must extract early. The “use case overview template” explicitly asks for counterparts: who the stakeholders are and what they care about, and it forces functional requirements into a structured sentence. citeturn20view0  
Role definitions fill in the “who”: Deployment Strategists go on-site to meet customer analysts, locate biggest problems, identify datasets, and work with FDSEs on extensible pipelines; FDSEs engage customer stakeholders from technical teams to executives. citeturn9view0turn7view0

Reconstructed interview set  
A realistic minimum set for a 90-day pilot is: exec sponsor; operational owner; frontline operators (2–6); analyst(s) who currently build reports; data owners for each system; IT/network; security/identity; and owner(s) of downstream systems-of-action if write-back is required. This matches the stakeholder surface implied by Palantir roles and Foundry’s requirement to reconcile data, actions, and security in one operational layer. citeturn9view0turn7view0turn3view8

Reconstructed interview guide aligned to Foundry’s template  
Instead of free-form “tell me requirements”, the highest-signal questions map to the template fields: “Which decision are you making?” “What inputs do you trust?” “Where do you get them?” “What action do you take and what state changes?” “What is the KPI of a good decision?” This is directly consistent with Foundry’s prescribed functional requirements format. citeturn20view0turn19view1

### Process mapping methodology and “ontology-worthy” selection

What public evidence says  
Public descriptions of forward deployed work stress on-site observation to capture tacit workflow knowledge. citeturn6view0turn6view3  
Foundry’s use case lifecycle documents then formalise process mapping into three concrete artefacts: an object model sketch (object types and link types), a lifecycle diagram (actions as a state machine), and a list of enrichments plus interface expectations. citeturn19view1turn20view0  
Foundry documentation also references Flow Capture as a capability to record workflows and generate documentation, implying a tooling path for turning observed workflows into formal documentation. citeturn19view0

How “ontology-worthy vs noise” is determined in Foundry terms  
Foundry’s solution design doc gives a crisp heuristic: core object types map directly to system-of-record granularities; derived object types exist where the business concept exists but no source system represents it; use case object types are edited through operational workflows. If a concept does not appear in a decision, does not have state transitions, and does not join meaningfully to other concepts, it is likely noise for the first pilot slice. citeturn19view1turn3view8

### Data discovery, inventory, and the “access politics” problem

What public evidence says about the technical inventory  
Foundry’s “set up a source” guide is effectively a data inventory checklist: validate network path; provision credentials (recommended dedicated service account); ensure drivers if using agent worker; then create the source, select Foundry worker vs agent worker, and preview. citeturn15view3turn15view2turn15view1  
Foundry also makes the network reality explicit: if the external system is in a separate network from Foundry, you must use an agent with two network paths (agent to external system; agent to Foundry). citeturn15view3turn14view1

How to answer your “what questions do FDEs ask data owners” prompt using Foundry’s own required fields  
The platform forces the questions: “Where is it hosted?” determines direct vs agent; “what credentials model?” because credentials must be provisioned and stored; “what type of sync?” because batch syncs can be file or table; “what transaction type?” SNAPSHOT vs APPEND; “do schema changes happen?” because you can block syncs on schema changes. citeturn15view3turn14view3

Data quality assessment in Foundry’s native mechanisms  
Foundry gives three concrete quality control layers you can use as a scoring framework: health checks (freshness, build success/duration), Pipeline Builder unit tests (logic-level expected outputs), and code-defined data expectations that can abort builds to stop bad data propagation. citeturn17search10turn17search0turn17search4

The access politics “playbook”, grounded in Foundry’s governance model  
The platform’s security model means access is rarely a single yes/no: it is Projects, roles, groups, and markings; plus potentially row-level policies. That gives you a negotiation structure: “we only need a service account scoped to these tables; access will be limited to this Project; visibility further constrained by markings; and row/column security can be enforced via object security policies or granular policies.” citeturn16search9turn16search28turn16search4turn16search1  
Foundry also documents that configuring network egress policies in Control Panel may require specific privileged roles (“Information security officer”), which is a concrete escalation lever when a gatekeeper blocks progress: you need the right role-holder involved, not just more persuasion. citeturn15view3

### Use case prioritisation into the first 1 to 3 use cases

What public evidence says  
Foundry’s use case lifecycle process forces prioritisation through outcomes and KPIs and by explicitly identifying decisions and users. It also includes “flags” that call out anti-patterns: insufficient investigation of pain points, requirements anchored on UI elements, focus too narrow on users, and scoping that does not carry through to user decisions. citeturn20view0

A reconstructed scoring matrix consistent with Palantir’s delivery model  
Public Palantir role descriptions imply prioritisation around: operational impact, dataset availability, and near-term demonstrability to execs. Deployment Strategists are tasked with locating biggest pain points, identifying datasets, building workflows, leading training, and presenting results and future proposals. That implies a scoring rubric like: impact; data readiness; workflow clarity; stakeholder support; expansion potential. citeturn9view0turn20view0  
If you want to mimic Palantir’s modern “fast ramp” posture, note that Palantir markets AIP Bootcamps as going from 0 to use case in 1 to 5 days, which is effectively an extreme version of prioritising “fast-to-demonstrate operational value.” citeturn18search2

## Ontology and data integration mechanics for weeks 2 to 6

### Ontology design process: object types, properties, links, naming, and iteration

What public evidence says about the ontology’s role  
The Foundry ontology is described as an operational layer sitting on top of integrated digital assets (datasets, virtual tables, models) and representing real-world counterparts as objects, properties, and links, plus kinetic elements like actions, functions, and dynamic security. citeturn3view8turn16search30

How an FDE decides object type vs property vs link in Foundry terms  
Foundry’s own solution design process gives the practical decomposition: object model sketch identifies object types and link types; properties represent characteristics. It also explicitly suggests identifying primary key property for each object type and cardinality for each link type. citeturn19view1turn21search0turn21search12  
In other words: if the concept is a first-class entity that participates in decisions and joins across the workflow, it becomes an object type; if it is a characteristic, it becomes a property; if it is a relationship needed for navigation and querying, it becomes a link type. This is consistent with Foundry’s definitions of properties and link types. citeturn21search12turn21search0

Naming conventions and schema stability signals  
Pipeline Builder auto-populates plural name and object type ID from the object name, and object type IDs become immutable after first deploy. That is a strong signal that teams should treat IDs as stable identifiers and be cautious about churn. citeturn3view7turn16search8  
Ontology creation helpers exist and require specifying metadata, backing datasource, property mappings, and keys, indicating that ontology design is meant to be formal and tool-assisted rather than ad hoc. citeturn21search29turn21search16

How many iterations before stabilising  
Public docs do not give a number. What they do provide is a mechanism for controlled iteration: Foundry Branching lets you change pipelines, ontology, and Workshop apps on a branch and merge via proposals and reviews. In practice, that supports rapid ontology iteration early, then stabilisation as merge overhead increases and IDs become fixed. citeturn17search15turn3view9turn3view7

Patents as weak corroboration of ontology-plus-transforms as a core pattern  
Older Palantir patents describe creating and storing an ontology with object types and property types, and associating parser definitions that transform input data into forms compatible with property types. This is consistent with the modern “ontology + pipelines/transforms” architecture, even if product names have evolved. citeturn21search5turn21search1

### Data pipeline construction: step-by-step, testing, and release

Foundry’s documented baseline pipeline sequence  
The official pipeline development overview gives a concrete ordered checklist: recommended Project structure; build a batch pipeline in Pipeline Builder or Code Repositories to clean/filter/join; map final datasets into ontology object types and link types; set schedules; then add unit tests, branching/release, and health checks for robustness. citeturn3view4turn17search13

Pipeline Builder vs Code Repositories: why the choice matters in a 90-day pilot  
Foundry positions Pipeline Builder as the primary no-code application for fast, flexible, scalable pipelines with real-time feedback. It explicitly states it supports a graph-based environment and collaboration, while still enabling robust release discipline. citeturn17search25  
The pilot pattern tends to start with Pipeline Builder for speed and shared understanding, then introduce Code Repositories for complex logic, reuse, or stricter software engineering practices. This pattern is inferred from the platform positioning, not spelled out as a rule. citeturn17search25turn3view4

Testing process: what Foundry explicitly supports  
Pipeline Builder unit tests: defined with test inputs, selected transform nodes, and expected outputs; unit tests must succeed before merging a proposal. citeturn17search0  
Data expectations: defined in code, can abort builds on failure, integrate with Data Health, and support change management through code review processes. citeturn17search4  
Health checks: validate job/build success, build duration, and freshness throughout the pipeline. citeturn17search10

### Data source connection: agent, source, sync, and common failure modes

What Foundry explicitly documents  
Agents: installed inside an organisational network; connect to sources; enable agent-proxy egress policies and agent worker connections; require provisioning a host (recommended Linux VM), configuring egress/ingress, validating connectivity, and setting automatic restarts. citeturn14view1  
Sources: represent connections to external systems like Postgres, S3, a filesystem, SAP, or a REST API; require network access validation, credentials provisioning, and possibly drivers for agent worker compute; then created in Data Connection with a specific source type and worker selection. citeturn15view0turn15view2turn15view3  
Syncs: batch syncs create datasets; can be previewed; can be scheduled; include configuration options like transaction type, maximum duration, and blocking schema changes. citeturn14view3

Common failure modes, grounded in the above mechanics  
Connectivity failures: incomplete ingress/egress, proxy misconfiguration, certificates not trusted, or inability of agent to reach source system. These are explicitly enumerated as the kinds of configuration required for agent connectivity. citeturn14view1turn15view3  
Schema drift: sync can be configured to prevent running on schema change; if you do not design for drift, pilots break at week 6. citeturn14view3  
Privilege bottlenecks: network egress policy configuration requires privileged Control Panel roles in some cases, meaning you can be blocked by organisational access rather than technical complexity. citeturn15view3

## Actions, security, and application mechanics for weeks 4 to 10

### Action type design and write-back configuration

How Action Types are identified  
Foundry’s solution design makes the workflow explicit as a lifecycle diagram: a state machine of Actions users take to modify objects. That is the cleanest public statement of “how to go from interviews to action modelling”. citeturn19view1

How actions appear in applications and what controls exist  
Foundry documents actions as being integrated across applications, including Object Explorer and Workshop. In object views, actions can be buttons with configurable labels, default parameter values (including deriving defaults from current object properties or local values like current user and timestamp), and controls around hiding/disabling if invalid. citeturn3view6

Write-back via webhooks as a first-class integration mechanism  
Data Connection Webhooks documentation explicitly supports outbound HTTP requests to external systems, including triggering a webhook when a user selects a button in a Foundry application. Webhooks are tied to a Source that stores credentials and can be rate-limited. citeturn14view5  
This is the most direct public answer to “how is write-back configured”: it is typically an HTTP call defined in Foundry, credentialled through a Source, invoked from an app interaction or via Actions. citeturn14view5turn3view6

### Security configuration: RBAC, row-level, column-level, and testing

RBAC in Foundry terms  
Projects are the primary organisational and security boundary; roles on Projects grant permissions to users and groups. citeturn16search9  
Markings add additional eligibility criteria: to access a resource, a user must satisfy all markings applied. citeturn16search28

Row-level and column-level security mechanisms  
Granular policies: used to configure row-level security for datasets and objects through rule sets comparing user attributes and data values. citeturn16search1  
Object security policies: configure view permissions on an object instance (row-level) independently of permissions on backing data; property security policies provide column-level security; together they support cell-level security. citeturn16search4turn16search0  
Restricted views: provide row-level controls for ontology data, but are not compatible as pipeline transform inputs because pipelines must be reproducible across users. citeturn16search3turn16search6turn16search7

Security testing and debugging  
Foundry provides documentation on checking permissions and notes that, for example, a Workshop module displaying a table of objects requires access to the object type and its datasources. This creates an operational test checklist: verify role grants, markings, object type access, and datasource lineage markings. citeturn16search29turn16search28

### Application building: Workshop vs Quiver vs Slate, binding data to UI, and iteration

Choosing the app surface  
Foundry’s solution design doc is unusually explicit: operational inbox workflows map naturally to Workshop; executive dashboards may begin as Quiver templates; Carbon can unify experiences across user types. citeturn19view1turn3view5

What Workshop is optimised for  
Workshop is positioned as a flexible application builder whose apps are more interactive than typical dashboards, using layouts and an events system, and supporting common operational patterns like inbox alert and task management. citeturn3view5  
Workshop’s documentation index shows a large widget surface area: object tables, object lists, object views, buttons, inline actions, filters, maps, Gantt charts, and more, signalling that “build an operational UI quickly” is a core product intent. citeturn9view3

Binding ontology to UI and actions in public terms  
Foundry’s action documentation explicitly references configuring actions in Workshop, and Workshop’s object table documentation references inline editing and cell-level edits, implying that Workshop widgets can be bound to ontology-backed object types and write-backs can be configured at the widget level. citeturn3view6turn16search11

Who designs the UI  
Deployment Strategists work alongside engineers and Product Designers in deployments, implying UI/UX is not purely “engineer-designed”, even if engineers can build it. citeturn9view0turn3view5

Iteration expectations  
Publicly, Palantir’s forward deployed model is biased to ship quickly, then iterate. Descriptions note that forward deployed engineers thrive on producing value quickly and that customers notice when usable software appears within a week or two. citeturn6view3turn7view0  
The platform’s branching model formalises iteration: branches across pipelines, ontology, and Workshop allow controlled changes and merges. citeturn3view9turn17search15

## Training, go-live, monitoring, and success measurement for weeks 8 to 12

### Training methodology and enablement artefacts

What public evidence says  
Training is explicitly part of the Deployment Strategist role: lead training sessions, ensure use is widespread enough to have concrete impact, and present results and proposals. citeturn9view0  
Palantir also markets AIP Bootcamps as an interactive workshop where customers go from 0 to use case in five days and includes onboarding and training users for rollout in operations. That is not the same as your 90-day pilot, but it is consistent with a “teach while building” methodology. citeturn18search2  
Palantir’s learning portal includes training tracks such as “Application Developer”, explicitly calling out building operational applications on top of the ontology using Workshop and Quiver and applying write-backs using Actions. citeturn21search22

What a 90-day pilot training stack typically includes (reconstructed)  
Role-based sessions (operators, analysts, managers), short scenario-driven walkthroughs, and a power-user cohort. Foundry’s own use case patterns emphasise operational decision capture; training tends to be workflow rehearsal, not feature tours. citeturn19view1turn3view5

### Go-live process, monitoring, and post go-live support model

Production readiness primitives Foundry explicitly provides  
Schedules to keep syncs and builds running. citeturn14view3  
Health checks and Data Health visibility across lineage. citeturn17search2turn17search10  
Notifications and issues integration, including auto-creating an issue on check failure. citeturn17search5  
Monitoring views to collect checks and monitoring rules and manage alerting at scale, including sending alerts to external systems like PagerDuty, Slack, and webhooks. citeturn17search12turn17search7  
Recommended support processes explicitly mention subscribing to monitoring views and integrating with external alerting tools that manage on-call rotations. citeturn17search16

Transition from FDE-operated to client-operated (reconstructed)  
Foundry’s documentation implies the transition is fundamentally about ownership of: schedules, checks, and alert subscriptions; plus governance over branches and merges. That is exactly what the “recommended Project and team structure” guidance hints at: teams are responsible not only for transforms but also for schedules, health checks, and integrity tests. citeturn17search17turn3view4

### Success measurement and the expansion case

What public evidence says  
Foundry’s use case overview template demands outcomes and KPIs as part of scoping. citeturn20view0  
A published Foundry use case example for logistics container utilisation defines impact metrics (trucks saved, total savings, mileage savings, utilisation %) and reports that within 6 weeks Foundry replaced the existing system and process. That gives a concrete benchmark for how Palantir frames “pilot success”: measurable operational deltas and willingness to replace core process tooling quickly. citeturn19view0  
Deployment Strategists are expected to present results and proposals for future work to exec audiences, which is effectively the “business case for expansion” deliverable you referenced. citeturn9view0

What the expansion document typically contains (reconstructed, but grounded in Foundry artefacts)  
A restatement of the functional requirements delivered; the object model and lifecycle diagram; data integration coverage and remaining gaps; security model; adoption metrics; measured KPIs; and a roadmap that reuses the foundational ontology and pipelines to unlock additional workflows. This matches Foundry’s focus on building foundational assets first to enable later scaling. citeturn20view1turn19view1turn3view8