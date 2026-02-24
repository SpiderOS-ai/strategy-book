# Palantir AIP bootcamp pre-sales and delivery playbook with day-by-day operating detail

## Scope, evidence base, and what can be known from public material

This report reconstructs Palantir’s pre-sales and AIP Bootcamp operating playbook using only publicly accessible sources: Palantir investor presentations and filings, official documentation, UK public sector service definition material, partner collateral describing preparation steps, and Palantir role descriptions for Account Executives, Deployment Strategists, and Forward Deployed Engineers. citeturn28view0turn28view1turn28view3turn28view5turn11view3turn17view0turn17view1turn18search4turn24search1turn24search17turn24search0turn25search33turn25search0turn25search1turn25search2

Some elements you asked for are not publicly available at “exact internal playbook” fidelity (for example: internal staffing assignment rules, proprietary templates, conversion rates by cohort, and the exact legal packet used in each deal). Where precision is not possible, this report explicitly labels content as either (a) evidenced directly in sources, or (b) a best-fit operational inference derived from multiple sources that describe the same mechanisms. citeturn11view3turn28view0turn28view8turn17view0turn24search9turn25search28

One critical anchor from Palantir’s own materials is consistent across investor decks and the AIP Bootcamp programme page: the Bootcamp is positioned as Palantir’s go-to-market motion to take an organisation from “zero to use case” in as little as one to five days, with outcomes framed as (a) building AI intuition, (b) developing initial use cases in the software, and (c) onboarding and training users for rollout. citeturn10search21turn28view3turn28view5turn11view1turn11view0

## Pre-sales mechanics and what makes an account “bootcamp-ready”

### How Palantir sources opportunities and why bootcamps sit in the funnel

Palantir explicitly characterises AIP Bootcamps as a new go-to-market approach for AIP, run at high volume, and designed to be immersive “hands-on-keyboard” sessions where customers build live alongside Palantir engineers. citeturn28view3turn28view5turn11view1turn10search21

From SEC risk disclosures, Palantir states that it often provides its platforms to potential customers “at no or low cost” for evaluation via short-term pilots, including at bootcamps, and that conversion is not guaranteed. This implies bootcamps function as an evaluation-to-procurement bridge rather than a classic paid discovery project. citeturn11view3turn28view0

From UK public sector service collateral, Palantir describes initial AIP Bootcamps as “typically offered free-of-charge” and oriented to rapid identification of tools and workflows to enhance time-critical missions, again reinforcing a “prove it fast” pre-sales design. citeturn28view0turn23view0

### ICP signals and “bootcamp-ready” gating criteria

Public sources do not publish a formal ICP scoring rubric, but multiple documents reveal consistent readiness prerequisites that behave like gating criteria:

A bootcamp-ready organisation can supply a bounded slice of real operational data quickly. Partner guidance explicitly calls for “static cuts of data” matched to the target workflow or use case, provided one to two weeks prior. This implies Palantir is not waiting for full enterprise integration before Day One; it prefers a narrow dataset that still represents the operational truth of a priority workflow. citeturn28view8turn24search9turn24search30

A bootcamp-ready organisation can commit the right people for the week. Partner guidance calls for confirmed participant roles spanning business owners, users, and relevant IT stakeholders. This is consistent with Palantir’s own emphasis on operational outcomes and training for rollout, which requires both domain operators and technical stakeholders present, not just innovation teams. citeturn28view8turn28view3turn10search21

A bootcamp-ready organisation has a short list of high-leverage use cases with decision-makers engaged. Partner guidance calls for scoping discussions before the bootcamp so the Palantir team can “pre-build as much as possible”. This only works if the client can decide which workflows matter and provide access to relevant data owners. citeturn28view8turn17view0turn28view1

A bootcamp-ready organisation can clear basic legal and environment setup quickly. Partner guidance references signing Terms of Service so Palantir can set up a private environment. The UK service definition similarly describes secure environments and governance, implying that legal/security readiness is a practical gating step, not a paperwork afterthought. citeturn28view8turn28view0turn26search0turn26search18

### Role split in pre-sales: Account Executive vs Deployment Strategist vs Forward Deployed Engineer

Account Executive ownership: Palantir’s AE role description emphasises leading cross-functional collaboration to “shepherd engagements” from initial meeting through procurement to close, plus developing customer profiles and navigating complex procurement protocols. This positions the AE as the commercial process owner and internal orchestrator of resources, not the primary builder. citeturn18search4turn11view3

Deployment Strategist ownership: The Deployment Strategist role is explicitly operational and discovery-led: going onsite to understand critical questions, identifying relevant datasets, working with Forward Deployed Engineers to integrate data into extensible pipelines, leading training sessions, delivering demos, and presenting results and proposals to audiences up to C-suite. This maps strongly to the “problem framing, enablement, and narrative” spine of a bootcamp. citeturn17view0turn28view3turn10search21

Forward Deployed Engineer ownership: The FDSE role is described as embedded engineering with customers, rapidly understanding issues, architecting and building solutions on business-critical data, developing custom applications, and engaging stakeholders from technical teams to executives. This maps to the “build the thing this week” spine of the bootcamp. citeturn17view1turn28view3turn24search0

## Pre-bootcamp preparation with operational detail and artefacts

### Data request and access patterns that show up in public guidance

Evidenced directly: PVM’s bootcamp preparation guidance calls for “static cuts of data” based on the workflow or use case, delivered one to two weeks before the bootcamp. It does not mandate a specific file format, but the language implies extract-based sharing rather than live production credentials as the default starting point. citeturn28view8turn24search9turn24search30

Evidenced directly: Palantir’s Pipeline Builder product collateral states Foundry can ingest data from “any source system”, including structured and unstructured sources, and Pipeline Builder is Foundry’s primary application for data integration that transforms raw sources into clean outputs for analysis. This supports why bootcamps can begin from extracts and still quickly assemble usable pipelines. citeturn24search1turn24search24turn24search9

Operational inference (best-fit): In practice, the “static cut” most commonly means delimited files (CSV), columnar extracts (Parquet), or database exports that preserve identifiers needed for Ontology mapping. This inference is consistent with Foundry’s dataset abstraction and pipeline tooling, but the exact formats are client-dependent and not specified in Palantir’s bootcamp materials. citeturn24search30turn24search1turn24search10

### How much is built before Day One

Evidenced directly: PVM’s prep guidance says pre-bootcamp scoping discussions help the Palantir team “pre-build as much as possible before the bootcamp” and calls out explicit ontology preparation via a discussion with data owners once datasets are shared. citeturn28view8turn28view0turn24search17

Operational inference (best-fit): The pre-buildable portion typically includes three layers:

A thin ingestion and cleaning pipeline in a Foundry branch. Pipeline Builder is designed for collaborative transformation workflows, and Code Repositories exist for code-authored transforms when needed. This makes it feasible for FDEs to arrive on Day One with data already landing into datasets and some initial transformation steps in place. citeturn24search1turn24search20turn24search3turn24search34

A “starter ontology” that expresses a small set of object types and link types required for the first use case demo. Ontology Manager exists specifically to create object types, connect backing datasources, and maintain ontology structure. PVM’s “prep ontology” step corroborates that at least some ontology work happens before the bootcamp starts. citeturn24search17turn24search13turn28view8

A prepared demo environment and permissions posture. PVM references setting up a private environment after signing Terms of Service, and Palantir’s security documentation emphasises strong governance and access controls. This combination implies the Palantir team aims to minimise Day One friction by having the environment provisioned and access ready. citeturn28view8turn26search2turn26search24

### Use-case selection: Who decides and the filtering logic that is observable

Evidenced directly: PVM’s prep guidance calls for high-level use case discussions prior to the bootcamp, explicitly so Palantir can pre-build. This implies use cases are selected collaboratively before Day One and are not discovered entirely inside the week. citeturn28view8turn28view0

Evidenced directly: Palantir’s “Getting started” partnership guide describes engagements beginning by identifying a key business problem and doing setup work before an execution phase, and it frames early delivery in phases (create foundation, refine workflows, operationalise). While this is a one-month pilot model, it reveals Palantir’s general pattern: pick “a core business problem” first, then build the foundation around it. citeturn28view10turn23view1

Operational inference (best-fit): The use-case filtering framework that best matches Palantir’s own mechanics usually reduces to three practical scores:

Operational leverage: Will this workflow touch a decision that must be executed in a system of action (ERP, dispatch, maintenance, clinical operations), matching Palantir’s “operational outcomes” language. citeturn19view0turn28view0turn23view1

Data tractability in one to two weeks: Can you produce a static cut with stable identifiers, plus enough history and ground truth to validate outputs. This is implied by the one to two week data cut lead time and the goal of reaching a demonstrable use case within days. citeturn28view8turn28view3turn10search21

Demoability in Workshop and the Ontology: Can the workflow be expressed as objects, links, actions, and an operator interface quickly. Palantir’s documentation makes clear that Workshop builds operational applications on the Object layer, while the Ontology maps business concepts to actual data and enables action types and functions. citeturn24search0turn24search10turn24search25turn24search31

### “Art of the possible” demos and vertical patterns

Evidenced directly: Palantir materials frame bootcamps as experiencing generative AI “in the context of your business” and building live alongside Palantir engineers, and partner collateral lists multiple vertical bootcamp themes (for example: supply chain, insurance, healthcare, procurement). citeturn28view9turn28view0turn11view0

Operational inference (best-fit): The “art of the possible” demo typically mixes two demo types:

Platform primitives demo: Showing how Pipeline Builder, Ontology Manager, Workshop, and AIP builder tools (AIP Logic, Agent Studio, Evals) connect into an end-to-end workflow. This is supported by Palantir documentation describing these tools’ purposes. citeturn24search1turn24search17turn24search0turn25search33turn25search0turn25search1

Vertical storyboard demo: Using a domain narrative (maintenance scheduling, supply chain disruptions, clinical operations) to make the same primitives feel “close to home”. This is consistent with Palantir’s public “AIP in action” framing across industries and with customer lists in AIPCon press releases. citeturn28view9turn11view0

### Legal, security, and environment setup before data sharing

Evidenced directly: PVM instructs customers to sign Terms of Service so Palantir can set up a private environment. citeturn28view8

Evidenced directly: Palantir’s AIP security documentation describes AIP as built atop secure infrastructure (AWS, Azure, Google Cloud) and frames security and governance as integral. Palantir’s security model includes governance constructs like organisations and spaces, and auditing primitives like audit logs. citeturn26search0turn26search24turn26search30

Evidenced directly: UK service definition material describes “validation and oversight” with full-spectrum security and audit controls, integrated human review checkpoints, and guardrails as first-class concepts, reinforcing that security controls are part of the delivery design, not an add-on. citeturn28view0turn23view0

### Internal staffing: How the bootcamp team is assembled

Evidenced directly: Palantir describes deploying multi-disciplinary project teams that embed with client teams, and DS and FDSE roles are explicitly designed for onsite engagement, data identification, pipeline integration, workflow building, training, and executive presentations. citeturn28view10turn17view0turn17view1

Operational inference (best-fit): A typical 5-day bootcamp “pod” that matches these role definitions looks like:

One Account Executive: Account owner; procurement pathway; ensuring the right executive stakeholders show up; converting outcomes into a commercial next step. citeturn18search4turn11view3

One Deployment Strategist: Facilitator and operator translator; use-case framing; stakeholder management; driving the daily decision points; owning the narrative for the final day. citeturn17view0turn28view3

One to three Forward Deployed Engineers or AI Engineers: Builders; data and ontology wiring; application workflow and agent configuration; demo hardening. citeturn17view1turn17view2turn24search0turn25search0

Optional security or platform specialist: Pulled in if the environment, governance, or model integration pattern is non-standard. This follows from the emphasis on security, governance, and “tool-driven plugins” in AIP descriptions. citeturn28view0turn26search18turn26search0

## Bootcamp execution: Five days, with agenda blocks, deliverables, tools, roles, and decision points

### The stable spine of a Palantir AIP bootcamp week

Across Palantir and partner materials, the bootcamp week consistently decomposes into three macro stages:

Build AI intuition: An interactive overview of LLMs and generative AI capabilities in the enterprise context. citeturn28view7turn28view0turn10search21

Hands on keyboard build: Intensive co-building sessions with Palantir engineers, oriented to real problems and producing an MVP. citeturn28view7turn28view3turn28view0turn10search21

Develop use cases plus tactical implementation plan: Configuring and deploying initial use cases, and preparing to onboard and train users for MVP implementation. citeturn28view7turn28view0turn28view5turn10search21

What follows is a day-by-day operationalisation of that spine, grounded in Palantir’s toolchain documentation and the preparation requirements above.

### Day one: Framing, confirming data reality, and agreeing the build plan

Agenda blocks (best-fit, evidenced plus inferred):  
Morning: Alignment and problem framing workshop; platform and “art of the possible” orientation; confirm the 3 to 5 target workflows and their operator journeys. This matches Palantir’s emphasis on “tackle real problems most pertinent” and PVM’s instruction to scope use cases before and during the bootcamp. citeturn28view0turn28view8turn17view0  
Afternoon: Data reality check in Foundry; validate what is actually available in the provided static cuts; confirm identifiers and join keys needed for Ontology; lock the “minimum viable ontology” for the lead use case. This is implied by the need to prep ontology with data owners and by Foundry’s ontology mapping mechanics. citeturn28view8turn24search17turn24search13turn24search2

Concrete deliverables by end of day:  
A signed-off “use-case slate” with owners, success criteria, and a demo script for the final day. This is the practical output of “identify the most important problem” work described in DS responsibilities and Palantir’s partnership model. citeturn17view0turn28view10  
A data inventory and a build backlog: Which datasets exist, which are missing, and what transformations are required. This maps to Pipeline Builder’s purpose and DS duties to identify datasets and integrate data into pipelines with FDEs. citeturn24search1turn17view0turn24search9  
A “minimum viable ontology” design: Candidate object types, link types, and key properties for the lead use case, ready to instantiate in Ontology Manager. citeturn24search17turn24search13turn24search6

Client interactions:  
Client business owners and operators: Validate the workflow steps and what constitutes a good decision in the real world, consistent with Palantir’s operational focus. citeturn28view0turn17view0  
Client IT and data owners: Confirm data meaning and join logic, matching PVM’s “discussion with data owners” and the ontology backing datasource requirement. citeturn28view8turn24search13

Palantir team activities by role:  
Deployment Strategist: Facilitates the workshop; forces prioritisation; documents success criteria; aligns stakeholders; begins shaping exec narrative. citeturn17view0  
FDE team: Validates data landing and transformation approach; drafts ontology types; sets up the engineering plan for the week. citeturn17view1turn24search1turn24search17  
Account Executive: Confirms evaluation boundaries and procurement pathway; ensures the right executive sponsor is scheduled for Day Five. citeturn18search4turn11view0

Tools opened most often:  
Pipeline Builder: To inspect data integration pipelines and transformation steps. citeturn24search1  
Ontology Manager: To start defining object and link types and connect backing datasources. citeturn24search17turn24search13turn24search2  
Workshop: To outline the target operational app shape, because Workshop is designed to create operational applications on the object layer. citeturn24search0

Decision points that shape the week:  
Decision on the “lead use case” that must be demo-ready by mid-week. This is critical because Palantir’s own narrative includes achieving results in as little as hours, and the week needs a guaranteed win path. citeturn28view4turn28view3turn11view1  
Decision on ontology scope: Which objects and links are “must-have” for value, versus “nice-to-have”. This matters because ontology edits cascade into app wiring and AIP tool grounding. citeturn24search10turn25search9turn25search28

### Day two: First working vertical slice

Agenda blocks:  
Morning: Build the foundation for the lead workflow: clean datasets, stable identifiers, and initial ontology mappings. This mirrors Palantir’s recurring “create foundation” phase logic and the platform’s emphasis on turning raw data into clean outputs ready for analysis. citeturn28view10turn24search1turn24search30  
Afternoon: Build the first operator-facing prototype in Workshop using ontology-backed objects; then connect at least one action or function that makes the app operational, not just analytical. citeturn24search0turn24search31turn24search10turn24search25

Concrete deliverables by end of day:  
A running pipeline branch that produces clean datasets for the lead use case. Pipeline Builder exists for building these integration pipelines, and Code Repositories can be used where code is needed. citeturn24search1turn24search20turn24search3  
Ontology objects visible in an application: Object types with backing datasources, and at least one link type where relationships matter. citeturn24search13turn24search2turn24search17  
A “walking skeleton” Workshop module: Minimal UI that loads real object data and supports a core user journey. citeturn24search0turn24search8turn24search15

Client interactions:  
Client operators: Sit with the app and confirm whether it matches how they think about the workflow, consistent with the bootcamp focus on “decision-making interfaces” and operational use. citeturn28view0turn24search0  
Client engineers: Pair with Palantir engineers where appropriate, but the observable bootcamp framing is “build live alongside Palantir engineers”, not “client writes all the code”. citeturn28view0turn28view3turn17view1

Palantir team activities by role:  
FDE team: Implements transformations and ontology wiring; builds the first app module; ensures data lineage and reproducibility. citeturn17view1turn24search34turn24search38  
Deployment Strategist: Runs operator feedback loops; documents gaps; adjusts scope to protect the Day Five story. citeturn17view0turn28view1  
Account Executive: Begins shaping commercial framing around a clear “prototype-to-production” path, echoing AIPCon positioning. citeturn11view0turn18search4

Tools opened most often:  
Pipeline Builder and or Code Repositories: For transforms and rapid iteration. citeturn24search1turn24search3turn24search34  
Ontology Manager: For mapping datasets into object types and creating link types. citeturn24search17turn24search29  
Workshop: For the prototype UI. citeturn24search0

Decision points:  
Decision on whether the prototype should be Workshop-first or agent-first. Palantir’s platform supports both: Workshop for operational applications and AIP Agent Studio for assistants grounded in the ontology and tools. citeturn24search0turn25search0turn25search27  
Decision on the “source of truth” objects that will anchor any AI grounding. AIP materials emphasise grounding AI in enterprise data, logic, and operations; the ontology is the binding layer. citeturn19view0turn25search9turn24search10

### Day three: Expansion to additional use cases and introducing AIP workflow logic

Agenda blocks:  
Morning: Extend ontology and app coverage to the next one to two use cases; standardise object definitions and link patterns so later additions are composable. Foundry’s ontology is designed as reusable semantic building blocks that power applications. citeturn24search10turn24search0turn24search13  
Afternoon: Introduce AI workflow components using AIP Logic or AIP Agent Studio so the prototype is not only a dashboard but an operational AI workflow with guardrails. AIP Logic is explicitly designed for building, testing, evaluating, monitoring, and automating LLM-powered functions. citeturn25search33turn25search0turn28view0

Concrete deliverables by end of day:  
Two to three end-to-end workflows that are demoable: Each workflow has data inputs, ontology representation, and an operator surface. citeturn24search0turn24search10turn28view0  
At least one LLM-backed function or agent wired to real ontology objects and actions. AIP Agent Studio builds agents equipped with enterprise context and tools; AIP Logic builds LLM-powered functions leveraging the ontology. citeturn25search0turn25search33turn25search3

Client interactions:  
Client domain experts: Provide “edge case” examples and unacceptable failure modes, preparing for Day Four stress testing. This aligns with Palantir’s emphasis on validation, oversight, and human review checkpoints. citeturn28view0turn26search1  
Client IT and security: Review permissions boundaries for any AI access, consistent with AIP’s security model and governance framing. citeturn26search0turn26search24turn26search30

Palantir team activities:  
FDE team: Implements LLM workflows, tools, and integrations; begins writing evaluation cases. citeturn25search33turn25search1turn25search12  
Deployment Strategist: Constructs the “operator plus AI” narrative, ensuring the prototype solves a real operational decision rather than a novelty chatbot. citeturn28view7turn17view0  
Account Executive: Aligns stakeholders on what “production-grade” means and what procurement artefacts are needed next. citeturn11view0turn18search4

Tools opened most often:  
AIP Logic: For LLM function development, testing, evaluation, monitoring, and potential automation setup. citeturn25search33turn25search31  
AIP Agent Studio: For agents grounded in ontology, documents, and tools, deployable inside and outside the platform. citeturn25search0turn25search18  
Workshop: For integrating an AIP Agent into an operator interface, supported by AIP Agent widgets. citeturn25search35turn24search0

Decision points:  
Decision on guardrails and human-in-the-loop checkpoints. Palantir’s AIP description explicitly includes integrated human review checkpoints and guardrails as first-class concepts. citeturn28view0turn26search1  
Decision on evaluation approach: What “good” outputs look like and how they will be tested given LLM non-determinism. AIP Evals exists specifically to evaluate such workflows. citeturn25search1turn25search25

### Day four: Stress testing, evaluation harnessing, and operational hardening

Agenda blocks:  
Morning: Structured scenario walkthroughs with domain experts; run the prototype against real decision scenarios, including deliberately adversarial inputs. This matches the “operate securely” plus “validation and oversight” emphasis in Palantir materials. citeturn28view9turn28view0turn26search1  
Afternoon: Instrumentation and evaluation: Use AIP Evals to create test cases and evaluators, and use AIP Observability to inspect run history, traces, and logs. This is exactly what these tools are built for. citeturn25search1turn25search2turn25search6turn25search13

Concrete deliverables by end of day:  
An evaluation suite covering the key AI behaviours, with test cases and evaluators suitable for repeated runs. AIP Evals is designed to evaluate Logic functions and agent functions and to manage non-determinism. citeturn25search1turn25search15turn25search31  
A “failure mode register”: Which scenarios break, what mitigations exist (prompting, additional grounding, permission tightening), and what remains out of scope. This is operationally aligned with Palantir’s governance framing and with the need to present a credible production plan. citeturn26search1turn25search25turn28view1  
An observability view for the workflows: Traces and logs accessible through AIP Observability’s run history and trace view concepts. citeturn25search2turn25search29turn25search6

Client interactions:  
Client operators and SMEs: Act as scenario injectors and judges; confirm whether outputs can be trusted in context. citeturn28view0turn17view0  
Client security and governance stakeholders: Validate auditability and log access boundaries, consistent with Foundry audit log capabilities and controlled log permissioning. citeturn26search30turn25search20turn25search34

Palantir team activities:  
FDE team: Tunes evaluation and observability; fixes brittle joins and ontology mismatches; hardens app performance where needed. citeturn24search34turn25search16turn24search36  
Deployment Strategist: Turns stress test outcomes into a clean story: Where the AI is reliable, where human review is required, and how this becomes a governed workflow. citeturn28view0turn26search1  
Account Executive: Aligns on next-phase commercial packaging around a realistic deployment plan, not just a demo. citeturn18search4turn11view0

Tools opened most often:  
AIP Evals: For test cases, evaluators, and run analysis. citeturn25search1turn25search25  
AIP Observability: For run history, trace inspection, and logging. citeturn25search2turn25search6turn25search13  
Workshop: For user-facing scenario testing if the workflow is app-centric. citeturn24search0turn24search27

Decision points:  
Decision on what is safe to automate now versus what requires human approval. Palantir’s AIP description explicitly includes “automate execution” and traceability, but also emphasises oversight and checkpoints. citeturn28view0turn25search33  
Decision on the minimum production permission model: Which users, roles, and spaces will access which objects and actions. This flows from Foundry’s security architecture and organisations/spaces governance model. citeturn26search24turn26search2turn24search35

### Day five: Executive readout, ROI narrative, and deployment roadmap

Agenda blocks:  
Morning: Final demo rehearsal plus packaging. Palantir’s own testimonial emphasises presenting to a CEO “the very next day”, and the bootcamp construct implies a strong executive-facing close. citeturn28view4turn11view0  
Afternoon: Executive presentation plus decision meeting: Confirm whether to proceed to a pilot, rollout, or broader contract; align on scope, governance, and timeline. citeturn11view0turn28view10turn18search4

Concrete deliverables by end of day:  
A working MVP prototype: Palantir partner collateral explicitly frames the bootcamp as exiting with an MVP and preparing to onboard and train users for MVP implementation. citeturn28view9turn28view7turn10search21  
A tactical implementation plan: Partner collateral calls out “develop use cases and tactical implementation plan”, matching the common “what next” deliverable. citeturn28view7turn28view0  
A production pathway narrative: Palantir AIPCon communications describe customers going from prototype to production-grade AI via the bootcamp initiative, indicating that a credible path to production is part of the expected output story. citeturn11view0turn10search1

Client interactions:  
C-suite sponsor and functional leadership: Judge whether the bootcamp outputs justify a broader deployment. This behaviour is directly consistent with DS responsibility to present results and proposals to C-suite executives. citeturn17view0turn28view4  
Procurement and IT leadership: Clarify procurement steps and delivery model, consistent with AE ownership of procurement navigation and engagement shepherding. citeturn18search4turn11view3

Palantir team activities:  
Deployment Strategist: Leads the narrative: Problem, baseline pain, workflow transformation, operator impact, and what the next phase operationally entails. citeturn17view0turn28view10  
FDE team: Runs the live demo; answers technical questions; shows observability and evaluation proof points where AI is involved. citeturn25search2turn25search1turn17view1  
Account Executive: Converts the plan into commercial terms and next steps; aligns timeline to procurement reality. citeturn18search4turn11view0

Tools opened most often:  
Workshop: For the operational MVP interface. citeturn24search0  
AIP Logic or Agent Studio: For AI workflow demonstration, including testing, evaluation, and monitoring hooks as needed. citeturn25search33turn25search0turn25search1turn25search2  
Ontology Manager: For showing the “business language” model that grounds workflows. citeturn24search17turn24search10

Decision points:  
Decision on whether to proceed and at what scope: A narrower paid pilot, a broader rollout, or a pause. SEC filings explicitly note conversion is not guaranteed, so this decision gate is real and expected. citeturn11view3turn28view0  
Decision on whether the MVP remains a bounded use case or becomes the seed of an enterprise ontology and workflow programme. This aligns with Palantir’s “customer enablement” pillar and phased delivery approach in its partnership playbook. citeturn28view10turn23view1

## Post-bootcamp follow-through, conversion mechanics, and what happens when it does not convert

### What is delivered immediately after the bootcamp

Evidenced directly: Public materials do not publish a standard “48-hour packet” list. What is evidenced is that bootcamps aim to exit with an MVP and a tactical implementation plan, and that customers are expected to be onboarded and trained for rollout. citeturn28view7turn28view0turn10search21

Operational inference (best-fit): The typical immediate artefacts required to operationalise what Palantir describes are:

A short executive summary: Problem, prototype, impact, next steps, and constraints.

A technical appendix: Data sources used, pipeline structure, ontology objects and links, and known gaps.

An evaluation and observability appendix for AI workflows: Test cases, failure modes, trace evidence, and required governance decisions. This is strongly suggested by the existence and positioning of AIP Evals and AIP Observability as the core mechanisms for reliable agentic execution. citeturn25search1turn25search2turn25search25

### Sandbox access and prototype longevity

Evidenced directly: Palantir’s public bootcamp materials do not specify how long prototypes remain accessible. Palantir’s SEC filings do, however, describe bootcamps as short-term pilot deployments and evaluation experiences, implying they are time-bounded and not permanent environments by default. citeturn11view3turn28view0

Operational inference (best-fit): Prototype longevity is usually governed by (a) the bootcamp environment terms (including the Terms of Service mentioned by partners), (b) whether the organisation enters a contracted phase, and (c) data retention requirements. The UK service definition document describes off-boarding and data removal and extraction capabilities, implying Palantir has formal processes for retention, export, and purge when a service period ends. citeturn28view8turn28view2turn23view0

### Follow-up cadence in weeks one to six

Evidenced directly: Palantir’s general engagement model describes pre-pilot work followed by a structured delivery phase, with steering committee meetings to ensure alignment and operationalise the solution. Although that document describes a one-month pilot, it is the clearest public description of Palantir’s post-initial-engagement operating cadence. citeturn28view10turn23view1

Operational inference (best-fit): The bootcamp follow-up cadence typically mirrors the pilot structure in compressed form:

Week one: Confirm the “production candidate” use cases from the bootcamp; lock data access approach (moving from static cuts toward repeatable connections); formalise governance and security approach. citeturn28view8turn24search9turn26search24

Weeks two to four: Create foundation and refine workflows: Turn bootcamp pipelines into stable, refreshable pipelines; harden ontology; expand user training; iterate with operators in tight loops. This maps directly to Palantir’s phased delivery model language. citeturn28view10turn17view0turn24search9

Weeks five to six: Operationalise: Deploy to real users; establish monitoring and incident pathways; expand evaluation suites; move toward a repeatable operating model. This matches Palantir’s emphasis on observability, auditability, and training for rollout. citeturn25search2turn26search30turn28view1turn28view0

### Handling non-conversion and re-engagement

Evidenced directly: Palantir discloses that it runs bootcamps and other short-term pilots at no or low cost for evaluation and that there is no guarantee these convert to longer-term revenue-generating contracts. This implies a non-trivial non-conversion rate exists, even if Palantir does not publish the percentage. citeturn11view3turn28view0

Evidenced directly: Palantir’s public metrics focus on bootcamp volume and global scaling rather than conversion rates. Press releases cite hundreds to thousands of bootcamps completed globally, reinforcing that the programme is a high-throughput funnel. citeturn11view0turn11view1turn10search1

Operational inference (best-fit): A reasonable re-engagement pattern for non-converts is:

Preserve the learnings: Data mappings, ontology stubs, and the “use-case slate” become internal notes for future re-entry.

Re-engage when constraints lift: For example, when data access becomes possible or an executive sponsor emerges.

Offer a narrower bootcamp: The UK service definition explicitly notes bootcamps can be single or multi-day, so Palantir can downshift scope to re-test with lower commitment. citeturn28view0turn23view0

### Commercial proposal format and contracting

Evidenced directly: Palantir does not publish a universal MSA or SOW template in public sources. Palantir does publish public-facing contractual addenda for AIP in some contexts, and UK government service definition material references service terms, pricing documents, and a structured approach to onboarding, training, support, and off-boarding. citeturn26search4turn23view0

Evidenced directly: The AE role is responsible for navigating multifaceted procurement and acquisition protocols and shepherding the process to close, supporting the expectation that commercial structure is heavily client-specific rather than a one-size template. citeturn18search4

## Evidence map aligned to your requested source types

Palantir official positioning of bootcamps: Palantir’s bootcamp programme page text describes the bootcamp as an interactive workshop from “0 to use case in 5 days”, with three stated outcomes. citeturn10search21turn16search3

Investor and corporate materials that describe bootcamps operationally: Palantir Q3 2023 and Q4 2023 business updates show the “from 0 to use case in 5 days or less” framing, explicitly call bootcamps “hands-on-keyboard”, and include testimonials about delivering results in less than eight hours and presenting to a CEO the next day. citeturn28view3turn28view4turn28view5turn28view6turn23view2turn12view2

Public-sector service definition content with unusually concrete bootcamp and onboarding detail: The UK “Foundry & AIP service definition” document states bootcamps can be single or multi-day, run one to five days, and are typically offered free-of-charge; it also outlines onboarding phases (scoping and preparation, infrastructure setup, implementation, and support) and discusses security controls. citeturn28view0turn28view1turn23view0

Partner collateral that exposes preparation steps: PVM’s bootcamp document provides a practical readiness checklist: participant roles, static data cuts one to two weeks in advance, scoping discussions, ontology prep with data owners, and Terms of Service to provision a private environment. citeturn28view8turn28view7

Palantir documentation that pins down exactly which tools are used: Foundry docs cover Pipeline Builder, Ontology Manager, Workshop, and Code Repositories; AIP docs cover AIP Logic, AIP Agent Studio, AIP Evals, and AIP Observability, including testing and monitoring mechanics. citeturn24search1turn24search17turn24search0turn24search3turn25search33turn25search0turn25search1turn25search2turn25search6

Job descriptions that define role responsibilities relevant to bootcamps: Deployment Strategist and FDSE postings describe onsite workflow immersion, dataset identification, pipeline integration, training, demos, and executive presentations; AE postings describe shepherding engagements from initial meeting through procurement to close. citeturn17view0turn17view1turn18search4

Items not found with reliable public evidence in this research pass: A leaked internal bootcamp playbook, a standard executive deck template, a published ROI formula, and bootcamp conversion rates by cohort were not available in authoritative public sources. Palantir’s 10-K confirms bootcamps are often low-cost evaluation pilots and warns that conversion is not guaranteed, but it does not provide a conversion percentage. citeturn11view3turn28view0