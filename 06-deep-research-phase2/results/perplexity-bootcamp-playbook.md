# Palantir AIP Bootcamp: The Complete Pre-Sales &amp; Commercial Playbook

***

## Part I: PRE-SALES — Before the Bootcamp

### 1. Prospecting &amp; Qualification

#### Inbound vs. Outbound

Palantir historically relied almost entirely on product-led growth and avoided a traditional salesforce. CEO Alex Karp famously said "the only way he'd hire salespeople was if he were 'hit by a bus'" — believing the software's results would sell themselves. As demand for AIP surged in 2023–2024, this model evolved: the bootcamp itself became the primary GTM motion, replacing both cold outreach and traditional POCs. "Our primary means of going to market with AIP will be through these bootcamps," said Ted Mabrey, Head of Global Commercial.[^1][^2][^3]

The pipeline is now a hybrid:

- **Inbound-heavy**: AIPCon events, customer word-of-mouth (bootcamp alumni hosting their own events), partner networks (Accenture, PVM, Carahsoft), and earnings call visibility generate most demand. Karp noted: "We're already overfilled for our AIP bootcamp... It's like a rock concert".[^3]
- **Outbound**: Account Executives target specific enterprises where Palantir sees fit — Karp described landing a $3M contract via outbound prospecting, then deploying a bootcamp, and expanding to an enterprise-wide deal in the same quarter.[^4]
- **Partner-sourced**: Partners like PVM and Carahsoft run their own bootcamps using Palantir software, particularly for government/defense verticals.[^5]

#### Ideal Customer Profile (ICP)

Palantir's ICP has historically clustered around:

- **Sectors**: Defense/intelligence, aerospace, healthcare, energy/oil &amp; gas, manufacturing, financial services, supply chain-heavy enterprises.[^6][^7]
- **Company characteristics**: Large enterprises with complex, multi-system data environments where "existing software stack does not solve" the problem — organizations where decisions are made *around* their ERP/CRM systems rather than *through* them.[^8]
- **Revenue threshold**: FDE economics require ≥$1M ACV deals. Contracts below $200K don't pencil for the FDE model. Average bootcamp-to-deal size exceeds $1M.[^7][^9][^10]
- **Readiness signals**: Customer acknowledges a specific operational problem; has structured and/or unstructured data available for ingestion; can mobilize business owners, operators, and IT stakeholders for a week-long engagement.[^11]

#### "Bootcamp-Ready" Qualification Criteria

Based on the AIP Bootcamp preparation documentation, a company is considered bootcamp-ready when:

1. They can **confirm participant roles** — business owners, end-users, and IT stakeholders willing to attend.[^12][^11]
2. They can provide **static cuts of data** tied to specific workflows or use cases 1–2 weeks prior.[^11]
3. They can engage in **high-level use case scoping** discussions so Palantir can pre-build.[^11]
4. They can participate in a **30-minute data discussion** once datasets are shared.[^11]
5. They can **sign Terms of Service** to allow Palantir to initialize a private Foundry environment.[^11]

#### Role Division: Account Executive vs. Deployment Strategist

Palantir's commercial organization splits responsibilities between two key roles:

| Role | Primary Function | Activities |
|------|-----------------|------------|
| **Account Executive (AE)** | Commercial ownership, deal strategy, expansion | Outbound prospecting, contract negotiation, quarterly business reviews, identifies expansion opportunities [^4] |
| **Deployment Strategist (DS)** | Client-facing technical strategy, problem framing | Talks to clients about problems needing solving, figures out data requirements, coordinates between client and engineering teams, leads requirements gathering workshops, presents results to C-suite [^13][^14] |

The DS is the connective tissue between the customer's business problem and the FDE team's technical execution. They determine "the kinds of data that the clients need to provide" and then communicate with engineers to "integrate the data, analyse the data and think about the workflow". DS roles require 25–75% travel and experience with programming/scripting (Python, R, SQL).[^13][^14]

***

### 2. Pre-Bootcamp Preparation (2–4 Weeks Before)

#### Step 1: Confirm Participant Roles

Palantir recommends 5–20 stakeholders from across business functions and IT teams. The ideal mix includes:[^5]

- Business owners/decision-makers (who understand the operational pain)
- End-users/operators (who will actually interact with the workflows)
- IT/data stakeholders (who understand source systems and security constraints)

#### Step 2: Access Data

The official requirement is **"static cuts of data based on workflow / use case, provided one to two weeks prior to your Bootcamp"**.[^12][^11]

In practice, this means:

- **Format**: Primarily CSV files, Parquet files, and JSON dumps uploaded directly into Foundry's Pipeline Builder. Foundry supports uploading as structured datasets, media sets, or unstructured datasets. For more mature organizations, API connectors or database read-only replicas can be used, but the bootcamp typically works with static extracts to avoid security and connectivity complexity.[^15][^16]
- **Scope**: Not a full enterprise data lake — targeted datasets relevant to the 3–5 scoped use cases. As PVM's bootcamp documentation notes: "You choose! Either notional data or the team can work with you in advance to provide directions on how to integrate their own data".[^5]
- **Pre-processing**: FDEs pre-build data pipelines using Pipeline Builder before the client arrives. This includes uploading CSVs, generating schemas (Foundry can auto-detect schemas from first rows), cleaning/transforming data, and materializing output datasets ready for ontology mapping.[^17][^15]

#### Step 3: Scope Use Cases (3–5)

Use case selection follows a **"top-five business outcome"** framework. The methodology:[^7]

- **Palantir-guided, client-chosen**: High-level use case discussions determine which problems to tackle. The client identifies their pain points; Palantir's DS and FDE team evaluates feasibility based on data availability, complexity, and potential for visible ROI.
- **Selection criteria**: Bob McGrew's framework (former OpenAI CRO, ex-Palantir): "Pick a top-five business outcome for your customer and build backwards from it. You're shipping results, not 'an install'".[^7]
- **Vertical patterns**: Common use cases by industry include: supply chain optimization, dynamic scheduling, procurement cost savings, customer service triage, quality/claims management, hospital operations, infrastructure project management, underwriting transformation.[^6]
- **Pre-bootcamp pre-building**: Once use cases are scoped, "the Palantir team pre-build as much as possible before the Bootcamp". This means FDEs ingest the data, build initial pipelines, begin ontology scaffolding, and prepare "art of the possible" demos.[^11]

#### Step 4: Prep Ontology

After datasets are shared, there is **"one 30-minute discussion with data owners"** to understand data structure, relationships, and business semantics. The FDE team uses this to:[^11]

- Map raw data fields to Ontology object types, properties, and links
- Define initial Action Types (operations users can take)
- Create the semantic layer that translates raw data into business concepts (e.g., "Aircraft," "Event," "Customer Order")[^18][^19]

#### Step 5: Initialize Stack

The client signs Terms of Service, and Palantir provisions a **private Foundry environment**. This is a sandboxed instance with the client's data loaded, pipelines configured, and initial ontology scaffolded — all before Day 1.[^11]

#### Legal/Security/NDA Process

Before data sharing, standard legal steps include:

- Mutual NDA execution
- Terms of Service / License agreement signing (Palantir has a standard License and Services Agreement template, as documented via government procurement channels)[^20]
- Security review: Palantir emphasizes "operational security, designed for real-time workflows" as a core bootcamp ingredient[^11]
- AIP runs on private networks with data governance rails, not shared environments[^6]

#### Internal Staffing Process

Palantir's bootcamp team typically includes:

- **1–2 FDEs/FDSEs** (Forward Deployed Engineers / Forward Deployed Software Engineers): The technical builders who write code, build pipelines, map ontology, create Workshop apps[^21][^22]
- **1 Deployment Strategist**: Leads problem framing, manages client relationships, facilitates workshops, coordinates between business stakeholders and FDEs[^14][^13]
- **Account Executive**: Present but primarily observing, handling commercial conversations, identifying expansion opportunities[^4]
- **Subject matter experts** (optional): For vertical-specific bootcamps, Palantir may include engineers with domain expertise

Palantir's internal model uses **Echo and Delta teams**:[^23][^24]

- **Echo team** (Deployment Strategists / embedded analysts): Domain experts who understand the client's field, identify high-leverage problems, manage relationships. Often former military officers, healthcare practitioners, or industry "heretics" who understand the status quo's shortcomings.[^24][^23]
- **Delta team** (FDEs / rapid-prototyping engineers): Highly skilled engineers who build fast, write "rough and ready code" to deliver immediate value. "Doers, not artisans obsessed with perfect code" — accustomed to "eating a lot of pain".[^23][^24]

Staffing decisions are typically made by the regional team lead or the DS overseeing the account, selecting FDEs based on vertical expertise, technical skillset (PySpark, data integration experience), and availability.

***

## Part II: THE BOOTCAMP — 5 Days

### Overall Structure: Three Phases

The bootcamp follows a three-phase arc, as documented in Palantir's official AIP Bootcamp materials:[^12][^11]

| Phase | Focus | Timing |
|-------|-------|--------|
| **Phase 1** | Introductions + Product Demos — "art of the possible" | Day 1 (morning/early afternoon) |
| **Phase 2** | Hands on Keyboards — co-building on real data | Days 2–4 |
| **Phase 3** | Showcase + Assessment — executive presentation, next steps | Day 5 |

The official materials describe three expected outcomes:[^11]

1. **Build your AI intuition**: Interactive overview of LLMs and GenAI capabilities in enterprise context
2. **Hands on keyboard**: Demos, intensive hands-on sessions, group discussions
3. **Develop use cases &amp; tactical implementation plan**: Configure and deploy initial use cases, prepare to onboard/train users for MVP implementation

***

### Day 1: Problem Framing &amp; "Art of the Possible"

#### Agenda (Morning)

- **Welcome and introductions**: Palantir team meets client stakeholders. DS leads introductions and sets expectations for the week.
- **"Developing Your AI Intuition" session**: This is a structured, hands-on deep dive led by a Palantir engineer (Ankit Shankar has led many of these at AIPCon). The session's goal is to "get customers hands-on with the product to understand the strengths and limitations of large language models and how AIP addresses those limitations". Topics covered:[^25]
  - What LLMs can and can't do (hallucinations, context window constraints)
  - How AIP Logic works as a builder's tool for taking an LLM from development to production
  - Prompt engineering, testing/evaluation, monitoring, automation
  - Demonstrations of strong typing, tool chaining, and ontology-grounded reasoning[^25]

#### Agenda (Afternoon)

- **"Art of the Possible" demo**: This is a **live Foundry instance** — not slides or pre-recorded video. The demo runs on the client's **own data that was pre-ingested** during the preparation phase. Ted Mabrey's framework: "The value of getting started is so important, and you will move so much more quickly if we can reduce the friction to allow you to get started".[^1][^6][^11]
- The demo showcases what the pre-built pipelines and ontology look like on the client's data, demonstrating Workshop apps, AIP Logic workflows, and ontology-based applications relevant to the scoped use cases.
- **Vertical-specific demos exist**: Palantir maintains demo environments for healthcare (patient bed placement, nurse staffing), manufacturing (production scheduling), supply chain (distribution center reallocation), defense, financial services, etc.[^6][^5]

- **Problem framing workshop**: The DS leads a structured session to refine the 3–5 use cases. This involves:
  - Process mapping: Understanding the current workflow and where it breaks down
  - Decision-point identification: "What decisions are being made? What data feeds those decisions? Where does the existing software stack fail?"[^8]
  - Prioritization: Which use case offers the highest ROI with the fastest path to value?
  - This is not formally "design thinking" or "JTBD" methodology — it's closer to Palantir's own framework of mapping decisions, information requirements, and data sources[^8]

#### Deliverables End of Day 1

- Refined use case prioritization (typically narrowed from 5 candidates to 2–3 primary builds)
- Client team has AI intuition — understands LLM capabilities vs. limitations
- Client has seen their own data in Foundry, creating desire and buy-in

#### Decision Points

- Which use cases to focus the remaining 4 days on
- Which client stakeholders will be the "co-builders" for Days 2–3
- Data gaps identified (additional datasets to request)

***

### Days 2–3: Co-Building

#### What "Co-Building" Means Concretely

"Co-building" at a Palantir bootcamp means the **FDE does the actual building while the client provides domain expertise and real-time feedback**. One attendee from a Dallas bootcamp described it as "sitting shoulder-to-shoulder with our data/tech counterparts" and creating "immediate, accretive value... within 2 days".[^26]

In practice:

- **FDEs are typing**: They write PySpark transforms in Pipeline Builder, configure ontology objects in Ontology Manager, build Workshop applications, and create AIP Logic flows. The client is not expected to write code.
- **Client engineers point and validate**: They confirm data mappings are correct, validate business logic, test outputs against domain knowledge, and flag edge cases.
- **Non-technical stakeholders provide context**: Business owners explain "this is how we actually make this decision" vs. "this is how the process is documented."
- **Reduced coding requirement**: Foundry's Workshop tool operates in a **no-code** manner — once Objects in the Ontology have user-defined Actions, Workshop can automatically generate forms and interfaces. This means even non-technical users can interact with the prototype.[^27][^18]

#### Ontology Mapping Process

The ontology mapping is done primarily through the **Ontology Manager UI** (not code-first). The process:

1. Raw datasets (CSV, JSON, Parquet) are already ingested via Pipeline Builder[^16][^15]
2. FDEs define **Object Types** (e.g., "Aircraft," "Customer Order," "Distribution Center") by mapping dataset columns to object properties[^19][^18]
3. **Links** between objects are defined (e.g., an Order links to a Customer, which links to a Distribution Center)
4. **Action Types** are configured — operations that users can take (approve, assign, update, escalate)[^28][^19]
5. **AIP Logic functions** are added — LLM-backed functions that can reason over ontology objects (e.g., "based on this event data and these regulations, which regulation is most relevant?")[^18][^25]

Palantir holds a family of patents on this ontology-workflow integration, including US12260192B2 ("Workflow application and user interface builder integrating objects, relationships, and actions") which describes how "object-centric builder software can utilize an ontology to design, configure, and build a workflow application".[^29]

#### Tools Used on Days 2–3

| Tool | Purpose |
|------|---------|
| **Pipeline Builder** | Data ingestion, transformation, cleaning. Upload CSVs/JSON, generate schemas, join datasets, materialize outputs [^15][^17] |
| **Ontology Manager** | Define object types, properties, links. Map raw data to business concepts [^19][^30] |
| **AIP Logic** | Build LLM-powered workflows. Prompt engineering, strong typing, tool chaining, evaluation [^25] |
| **Workshop** | No-code application builder. Create operational apps (inboxes, maps, dashboards, metrics views) directly from ontology objects [^28][^31] |
| **AI FDE** | AI-powered agent that "operates Foundry for you through conversational commands" — translates natural language into Foundry operations for data transformations, ontology building, etc. [^32] |

#### "Working Prototype End of Day 2" — What Does It Look Like?

The Day 2 prototype is typically a **Workshop application** — a functional, interactive dashboard/operational app. Examples:

- An orders inbox that displays all orders from an Object Type, with filtering, sorting by urgency, and assign/approve actions[^28]
- A map-based workflow showing distribution centers and customer locations with reallocation tools powered by AIP[^5]
- A supply chain disruption response tool that surfaces impacted orders and recommends alternative fulfillment paths[^33]

As the Reddit aviation safety bootcamp attendee described: Workshop allows building applications "without coding" because "each Object in the Ontology already has user-defined Actions" and Workshop automatically generates interactive forms.[^18]

#### Deliverables End of Day 3

- 2–3 working Workshop prototypes on real client data
- Ontology with object types, links, and actions configured
- Initial AIP Logic workflows demonstrating LLM-augmented decision support
- Client team has participated in building and can articulate the value

***

### Day 4: Stress Testing &amp; Refinement

#### What "Stress Testing" Means

Day 4 shifts from building to validating. The process involves:

- **Domain expert review sessions**: The FDE team demos the prototypes to broader stakeholders — including domain experts who weren't in the co-building sessions. These experts ask probing questions: "What happens when X?" "Does it handle the case where Y?"
- **Edge case scenarios**: The team runs real operational scenarios through the prototype:
  - What happens when data is missing or inconsistent?
  - How does the system handle exceptions to standard workflows?
  - What happens at scale (more objects, more concurrent users)?
  - Does the LLM hallucinate on edge cases? (AIP Logic's evaluation tools are used to test prompt reliability)[^25]
- **War-gaming format**: For defense/government bootcamps especially, this can take the form of scenario-based exercises where operators run through realistic situations
- **Live demo with Q&amp;A**: Domain experts interact with the Workshop app in real-time, testing usability and questioning outputs

#### Who Runs It

- DS facilitates the sessions and manages stakeholder expectations
- FDEs respond to technical questions and make real-time adjustments
- Client domain experts are the primary "testers" — they know the edge cases from lived experience

#### Deliverables End of Day 4

- Validated prototypes with edge cases addressed
- Documented limitations and known issues
- Refined AIP Logic prompts with improved reliability
- Client feedback incorporated into the applications

***

### Day 5: Executive Showcase &amp; Deployment Roadmap

#### The Executive Presentation

Day 5 is **Phase 3: Showcase + Assessment**. This involves:[^11]

- **Internal presentation**: The client team presents what was built to their executive sponsors and leadership. This is a critical dynamic — the **client** presents, not Palantir. This creates internal advocates and ownership.
- **Optional cross-client showcase**: Palantir sometimes organizes multi-organization bootcamps where clients can "share learnings with your team and other clients".[^12][^11]

The presentation typically includes:

1. **Problem statement**: What operational challenges were addressed
2. **Live demo**: Walking through the Workshop apps built during the week
3. **Business impact**: Quantified value — e.g., "10% increase in external transfer volume," "2x increase in Hospital at Home volume from the ED," "90% reduction in time to generate staff schedules"[^34]
4. **Technical architecture**: How the ontology, pipelines, and AIP Logic work together
5. **Deployment roadmap**: Path from MVP to production

#### ROI Quantification

Palantir uses customer-specific metrics rather than a generic formula. Common ROI frameworks include:

- **Time savings**: Hours/FTEs saved through automation (e.g., "achieved more in one day with AIP than a top-three hyperscaler accomplished over four months")[^35]
- **Operational efficiency**: Throughput improvement, error reduction, faster decision cycles
- **Revenue impact**: Better scheduling, pricing optimization, customer retention
- **Cost avoidance**: Reduced inventory carrying costs, prevented supply chain disruptions

The ROI is co-developed with the client during the bootcamp, not imposed by Palantir — this ensures credibility and internal buy-in.[^4]

#### "Deployment Roadmap" Document

The roadmap presented on Day 5 follows Palantir's phased expansion model:[^11]

| Phase | Timeline | Outcome |
|-------|----------|---------|
| Result 1: AIP Demo &amp; Deep Dive | &gt;1 day | Build AI/LLM intuition |
| Result 2: AIP Bootcamp | 1–5 days | MVP on your data, built by your teams |
| Result 3: ROI Realization | 3 months | Tangible ROI against target users/use cases |
| Result 4: Scaling Phase | 3–6 months | Non-linear ROI with scope expansion |
| Result 5: AI-Powered Foundation | 6–9 months | Transformational business results |

#### Commercial Discussion on Day 5

Day 5 includes "align on next steps with Palantir". The AE enters more prominently here. Topics include:[^11]

- Pilot scope and timeline (typically 6–8 weeks to production application)[^8]
- Resource requirements (Palantir FDE support vs. client self-service)
- Contract structure (see Post-Bootcamp section below)
- Expansion path and long-term partnership vision

***

## Part III: POST-BOOTCAMP (Weeks 1–6)

### Documents Delivered Within 48 Hours

Based on the standard commercial workflow:

- **Executive summary**: What was built, key findings, quantified business impact
- **Technical assessment**: Architecture diagram, ontology model, data pipeline documentation, AIP Logic configurations
- **ROI projection**: Based on the use cases demonstrated, projected value over 6–12 months
- **Proposed deployment roadmap**: Phased plan from MVP to production to scale[^11]

### Sandbox Access

The prototypes built during the bootcamp remain accessible in the client's private Foundry environment. Palantir's median POC-to-production timeline is **6–8 weeks**, during which the sandbox evolves from demo into a production application.[^8]

### Follow-Up Cadence

- Bootcamp participants return with "4–5 use cases 2 weeks later... and a real live initial implementation of a use case and a plan to take that MVP into production"[^1]
- Weekly calls with the assigned DS and FDE team during the pilot phase
- On-site support from FDEs as needed (travel 25–75% depending on engagement)[^14]

### Conversion Rate

Palantir does not officially disclose bootcamp conversion rates, but multiple data points suggest strong performance:

- **~70% convert to paid contracts within one quarter**, with average deal size exceeding $1M[^10][^36]
- Q3 2025: Palantir closed 204 deals of at least $1M, with 45% being new customers — many sourced from bootcamps[^36][^37]
- Over 1,300 bootcamps completed as of Q4 2024, with "conversion rates accelerating"[^38]
- 134% net dollar retention in U.S. commercial — meaning existing customers expand significantly post-bootcamp[^36]

### Handling Non-Converters

For organizations that don't convert immediately:

- Sandbox access expires after a defined period
- Palantir maintains the relationship through the AE/DS team
- Re-engagement through AIPCon events, partner-hosted bootcamps, or new use case identification
- The bootcamp itself generates brand advocates regardless of conversion — alumni become "unofficial salespeople"[^39][^2]

### Commercial Proposal Structure

Palantir's commercial model:

- **Contract types**: Annual subscription licenses. Palantir's reported pricing ranges from ~$1M+ for mid-market commercial to $10M+ for large enterprise and government[^36]
- **Land and expand**: The initial deal is often focused on a specific use case, with the expectation of rapid expansion. Karp described a pattern of "$3M initial contract → bootcamp → enterprise-wide agreement in the same quarter"[^4]
- **Palantir License and Services Agreement**: Standard MSA template exists, documented through government procurement channels (e.g., via Carahsoft's GSA Schedule)[^20]
- **No traditional services contract**: FDE deployment is included in the software license — there is no separate implementation/consulting fee. This is a deliberate strategy to maintain skin-in-the-game alignment[^8]

***

## Part IV: EVIDENCE BASE

### Palantir Blog Posts &amp; Official Sources

- **Ted Mabrey**, "Deploying Full Spectrum AI in Days: How AIP Bootcamps Work" (Oct 2023) — the canonical blog post describing bootcamp methodology[^6]
- **Official AIP Bootcamp PDF** — preparation checklist, three-phase agenda, partnership growth model[^11]
- **Chad Wahlquist**, Forward Deployed Architect, "Building with Palantir AIP: The Ontology SDK" — demonstrates how FDEs build ontology-backed applications[^40]
- **Palantir Docs** — Ontology overview, Workshop example applications, AIP Logic, AI FDE agent[^32][^31][^19]

### Executive Interviews

- **Shyam Sankar (CTO) &amp; Ted Mabrey** on Stratechery (2023): Detailed discussion of Foundry operating system, FDE model, data integration challenges, POC timelines (6–8 weeks), and the decision-framework approach to problem solving[^8]
- **Alex Karp** on earnings calls: "We can't do enough of [bootcamps]... It's like a rock concert" (Q4 2023); challenged customers to compare internal AI efforts against 10 hours on Palantir's platform[^41][^3][^4]
- **Ryan Taylor (CRO)** on Q3 2023 earnings: "We reoriented our go-to-market approach around AIP boot camps, which has allowed us to deliver real workflows on actual customer data in five days or less versus our traditional pilots, which generally take one to three months"[^42][^35]

### Customer Testimonials

- **Komatsu**: Atticus Clark (Mining Program Manager) presented at Pontiac, MI bootcamp about AI helping prioritize tasks by urgency — called it a "game changer"[^2][^3]
- **Eaton, HCA Healthcare, Jacobs**: Featured in AIPCon keynotes describing bootcamp-derived use cases[^6]
- **AKOS**: "We are highly impressed with the technology, design, and scalability of Palantir Foundry and AIP... We're so bullish about it that we're adopting it right away"[^43]
- **Dallas bootcamp attendee (John Kottlowski, Palantir)**: "Within 2 days we created immediate, accretive value across their enterprises by sitting shoulder-to-shoulder with our data/tech counterparts"[^26]
- **Aviation safety bootcamp attendee**: Detailed description of ontology construction, AIP Logic usage, Workshop app building with reduced coding requirement[^27][^18]

### Employee Perspectives &amp; Job Descriptions

- **Deployment Strategist JD**: Requires willingness to travel 25–75%, programming experience (Python, R, SQL), responsibilities include leading training sessions, presenting to C-suite, embedding with engineering teams[^14]
- **DS interview process**: 4 rounds including open-ended decomposition ("design an emergency response system"), analytical case studies with data tables, behavioral interviews[^44][^45]
- **Mark Scianna** (former FDE, now Forward Deployed VC): "If I could sum FDE up in one sentence, it's that Palantir really believes you should put an engineer as close to the problem as possible"[^7]
- **Pascal Unger** (LinkedIn): Described the FDE/DS split — "FDEs handle technical building and implementation; Deployment Strategists manage commercial strategy and change management. Two different humans, two different skill sets, working as one team"[^22]

### AIPCon Presentations

- **Ted Mabrey at AIPCon** (Sept 2023): Announced bootcamp strategy — "People who have gone through the bootcamps are coming back with 4–5 use cases 2 weeks later"[^1]
- **Ankit Shankar, "Developing Your AI Intuition"** (AIPCon): The signature Day 1 session teaching LLM strengths/limitations using AIP Logic, with live demonstrations of strong typing, tool chaining, and ontology-grounded reasoning[^46][^25]

### Patent Filings

Palantir holds extensive patents related to the technical infrastructure that powers bootcamps:

- **US12260192B2** / **US11086602B2**: "Workflow application and user interface builder integrating objects, relationships, and actions" — describes the object-centric builder (Workshop) that uses ontology to design and build workflow applications[^47][^29]
- **US11461355B1**: "Ontological mapping of data" — systems for mapping raw data to ontology structures, the core process performed during bootcamp data preparation[^48]
- **US9946777B1**: "Systems and methods for facilitating data transformation" — describes the Pipeline Builder functionality for transforming tabular data to ontology-based object data[^49]
- **US10861203B1**: "Ontology-backed automatic chart creation" — visualization tools used during bootcamp demos[^50]
- **US20200201855A1**: "System to generate curated ontologies" — on-the-fly ontology curation based on user/device characteristics[^51]

### Financial Evidence (Bootcamp ROI on Palantir's Business)

| Metric | Value | Source |
|--------|-------|--------|
| Bootcamps completed (end 2023) | 500+ across 465+ organizations [^4] |  |
| Bootcamps completed (end 2024) | 1,300+ [^38] |  |
| Average bootcamps/day (2024) | ~5 per day globally [^52][^3] |  |
| Conversion rate (estimated) | ~70% within one quarter [^10][^36] |  |
| Average deal size from bootcamp | &gt;$1M [^10] |  |
| Q3 2025 U.S. commercial revenue growth | +121% YoY [^37] |  |
| Q4 2025 total revenue | $1.41B (+70% YoY) [^53] |  |
| Q4 2025 TCV | $4.26B (+138% YoY) [^53] |  |
| Net dollar retention (U.S. commercial) | 134% [^36] |  |

***

## Part V: SYNTHESIS — The Operational Playbook in Sequence

**Weeks -4 to -2**: AE qualifies opportunity → DS conducts discovery calls → Use cases scoped → Data requirements communicated → NDA/ToS signed

**Weeks -2 to -1**: Client provides static data cuts → FDEs ingest data into Pipeline Builder → Ontology scaffolding begins → "Art of the possible" demo prepared on client's own data → 30-min data discussion with client data owners → Private Foundry environment provisioned

**Day 1**: AI Intuition session (morning) → Art of the Possible live demo on client data (early afternoon) → Problem framing workshop with DS facilitation (late afternoon) → Use case prioritization decided

**Day 2**: FDEs begin building first use case → Pipeline Builder transforms, Ontology Manager configuration → Client stakeholders provide real-time domain feedback → Workshop app skeleton emerges → Initial prototype by end of day

**Day 3**: Second and third use cases built → AIP Logic workflows created → Workshop apps refined → Client operators begin interacting with prototypes → Working MVPs by end of day

**Day 4**: Stress testing with domain experts → Edge cases run through prototypes → AIP Logic prompts refined → Usability feedback incorporated → Demo rehearsal for Day 5

**Day 5**: Client presents to their executives → Live demos of working MVPs → ROI discussion → Deployment roadmap presented → Commercial next steps with AE → "Align on next steps with Palantir"

**Week +1**: Executive summary + technical assessment delivered → Sandbox remains accessible → DS schedules weekly follow-up cadence

**Weeks +2–8**: MVP refined to production application → FDE support continues → Commercial proposal formalized → Pilot/subscription contract signed → Expansion use cases identified (clients typically return with 4–5 additional use cases within 2 weeks)[^1]

---

## References

1. [Palantir Technologies on LinkedIn: Announcing AIP Bootcamps | Ted Mabrey at AIPCon](https://www.linkedin.com/posts/palantir-technologies_announcing-aip-bootcamps-ted-mabrey-at-activity-7110311425360699392-4BD6) - "Our primary means of going to market with AIP will be through these bootcamps." "People who have go...

2. [Inside Palantir's AI Sales Secret Weapon: Software Boot Camp](https://finance.yahoo.com/news/inside-palantir-ai-sales-secret-110015454.html) - Lasting from one to five days, they feature demos from engineers, work sessions for attendees and pr...

3. [Palantir CEO says its unconventional boot camps are drawing crowds and driving sales: 'It's like a rock concert'](https://www.businessinsider.com/palantir-unconventional-boot-camps-driving-sales-ceo-says-2024-4?IR=T) - Palantir's unusual sales tactics have included boot camps, which its CEO has likened to "a rock conc...

4. [Palantir's Customer Acquisition Strategy - GTM Foundry](https://www.gtmfoundry.vc/p/palantirs-bootcamp-gtm-strategy) - Going all in on AI Bootcamps.

5. [Palantir Platform Bootcamps - PVMwww.pvmit.com › services › palantir-platform-bootcamps](https://www.pvmit.com/services/palantir-platform-bootcamps) - Book a Palantir Platform Bootcamp or AIP Bootcamp with PVM to unlock the power of your data and and ...

6. [Deploying Full Spectrum AI in Days: How AIP Bootcamps Work](https://blog.palantir.com/deploying-full-spectrum-ai-in-days-how-aip-bootcamps-work-21829ec8d560?gi=5e4fb5d625d4) - Head of Global Commercial Ted Mabrey shares early learnings on why Palantir’s partners find AIP Boot...

7. [How to Build Your 1st Forward Deployed Engineering Team](https://www.peraspera.us/forward-deployed/) - In the years since my deployments, Palantir practiced and perfected the art of putting engineers as ...

8. [An Interview with Palantir CTO Shyam Sankar and Head of Global ...](https://stratechery.com/2023/an-interview-with-palantir-cto-shyam-sankar-and-head-of-global-commercial-ted-mabrey/) - I wanted to take the opportunity to interview Chief Technology Office Shyam Sankar and Head of Globa...

9. [The Forward Deployed Engineer Playbook: A Practitioner's Field ...](https://conikeec.substack.com/p/the-forward-deployed-engineer-playbook) - This Is Not a Deloitte [or] a Sales Engineer Playbook · Phase 1: Insertion · Phase 2: Discovery and ...

10. [Palantir Bootcamps Propel Defense AI Platforms Adoption - AI CERTs](https://www.aicerts.ai/news/palantir-bootcamps-propel-defense-ai-platforms-adoption/) - Discover how Palantir's bootcamps accelerate Defense AI Platforms growth and adoption across governm...

11. [AIP BOOTCAMP](https://9421792.fs1.hubspotusercontent-na1.net/hubfs/9421792/AIP-bootcamp.pdf)

12. [[PDF] AIP BOOTCAMP - PVM](https://blog.pvmit.com/hubfs/AIP-bootcamp.pdf)

13. [Palantir deployment strategist](https://meets.leap.work/t/palantir-deployment-strategist/304) - I’ve recently heard about this role at Palantir called deployment strategist and I’m not quite sure ...

14. [Deployment Strategist - Palantir Technologies](https://www.linkedin.com/jobs/view/deployment-strategist-at-palantir-technologies-4304589565) - Posted 10:13:56 PM. A World-Changing CompanyPalantir builds the world’s leading software for data-dr...

15. [Palantir Foundry Pipeline Builder: Process JSON and CSV Files](https://www.youtube.com/watch?v=Hx64YOwyhiI) - ... analytics and ontology use cases. Perfect for Palantir Foundry beginners and data engineers look...

16. [Palantir Foundry Pipeline Builder: Top Data Ingestion Methods Explained](https://www.youtube.com/watch?v=4g9GjA2Ll9A) - In this video, Chandradeep will explain all the major ways to ingest data into Palantir Foundry usin...

17. [Build with Us | Deep Dive: Building Your First Pipeline](https://www.youtube.com/watch?v=I9iOqre7gqk) - *An updated version of this video is available at https://www.youtube.com/watch?v=MG3KRXCfNaU*

In t...

18. [Palantir AIP Bootcamp : r/PLTR - Reddit](https://www.reddit.com/r/PLTR/comments/18k015u/palantir_aip_bootcamp/) - This is easy to do via Foundry's Workshop tool in a no-code way. Because each Object in the Ontology...

19. [Palantir](https://www.palantir.com/docs/foundry/ontology) - The Palantir Ontology is an operational layer for the organization. The Ontology sits on top of the ...

20. [[PDF] Palantir License and Services Agreement - Carahsoft](https://static.carahsoft.com/concrete/files/5316/6206/2785/Palantir_License_and_Services_Agreement.pdf)

21. [FDE Playbook - Forward Deployed Engineers Guide](https://www.forwarddeployedengineer.site) - Learn what Forward Deployed Engineers (FDE) are, how they work with customers, and why they're cruci...

22. [Pascal Unger's Post](https://www.linkedin.com/posts/pascal-unger_everyone-knows-palantirs-forward-deployed-activity-7392184017263153153-mb2j) - Everyone knows Palantir's Forward Deployed Engineer model. Everyone wants to copy it. Most will fail...

23. [The FDE Revolution: Understanding Forward Deployed Engineers](https://www.forwarddeployedengineer.site/article) - Deep dive into the Forward Deployed Engineer model pioneered by Palantir and now embraced by AI star...

24. [The Forward Deployed Engineer (FDE) Model: A Strategic Playbook ...](https://www.remio.ai/post/the-forward-deployed-engineer-fde-model-a-strategic-playbook-for-ai-startup-success) - Forward Deployed Engineer (FDE) model empowers AI startups to drive deep product discovery, rapid it...

25. [Developing Your AI Intuition | Palantir AIP Bootcamp Session - Lilys AI](https://lilys.ai/en/notes/palantir-aipcon-20251112/developing-ai-intuition-palantir-aip) - Bu Palantir AIP Bootcamp oturumu, izleyicilere yapay zeka sezgilerini geliştirmeleri için pratik bir...

26. [Announcing AIP Bootcamps | Ted Mabrey at AIPCon | John Kottlowski](https://www.linkedin.com/posts/johnkottlowski_announcing-aip-bootcamps-ted-mabrey-at-activity-7113602309368004608-ZVsF) - Strong plug: Palantir Technologies just wrapped up our week-long AIP Bootcamp in Dallas with new and...

27. [BOOTCAMPS, BABY - by Amit Kukreja - Daily Palantir - Substack](https://dailypalantir.substack.com/p/bootcamps-baby) - End of year bootcamp numbers are in for Palantir: 414 bootcamps done. 634 organizations served. 27 i...

28. [Palantir Foundry | Speedrun Your First E2E Workflow – Workshop App + Ontology Actions (Part 2/2)](https://www.youtube.com/watch?v=ISVRT3fj57s) - Welcome back to Foundry Fastlane — where we build Palantir solutions at full speed.

In Part 2 of th...

29. [Workflow application and user interface builder integrating objects, relationships, and actions](https://www.perplexity.ai/rest/file-repository/patents/US12260192B2?lens_id=167-146-118-460-722) - publication_number: US12260192B2
assignee: PALANTIR TECHNOLOGIES INC
abstract: Systems, techniques, ...

30. [Overview • Ontology - Palantir](https://palantir.com/docs/foundry/ontology/overview/) - The Palantir Ontology is an operational layer for the organization. The Ontology sits on top of the ...

31. [Example applications - Workshop - Palantir](https://palantir.com/docs/foundry/workshop/example-applications/) - Create ready-to-use applications using your own data directly from the Workshop home page. Currently...

32. [AI FDE • Overview - Palantirpalantir.com › docs › foundry › ai-fde › overview](https://www.palantir.com/docs/foundry/ai-fde/overview) - AI FDE - the AI-powered forward deployed engineer - is an interactive agent that operates Foundry fo...

33. [Building with Palantir AIP: The Ontology Software Development Kit](https://blog.palantir.com/building-with-palantir-aip-the-ontology-software-development-kit-823fe5ac7aae?gi=ae69aaa45e34) - By Chad Wahlquist, Palantir Forward Deployed Architect

34. [palantir ai bootcamp](https://www.viveevent.com/palantir-ai-bootcamp)

35. [What's in Enterprise IT/VC #406 - by Ed Sim](https://www.whatshotit.vc/p/whats-in-enterprise-itvc-406) - Bootcamps are an exponential leap in time to value as the new AIP platform enables Palantir to show ...

36. [Palantir's Bootcamp-Driven Flywheel and AI Operating System ...](https://www.ainvest.com/news/palantir-bootcamp-driven-flywheel-ai-operating-system-dominance-2026-2601/) - Palantir's Bootcamp-Driven Flywheel and AI Operating System Dominance in 2026

37. [Palantir Q3 2025 Earnings Call](https://www.youtube.com/watch?v=jNOoYoK6u5g) - In Q3 2025, Palantir Technologies reported a remarkable 63% year-over-year revenue growth, driven by...

38. [Palantir Technologies - MLQ.ai](https://mlq.ai/research/palantir-technologies/) - Many bootcamps convert to contracts within weeks. Over 1,300 bootcamps completed as of Q4 2024 5, wi...

39. [PLTR Boot-camps](https://www.borexinvesting.com/2024/04/pltr-boot-camps.html) - Stay updated with Borex Investing for insightful analysis and updates on Nasdaq stocks and ETFs.

40. [Building with Palantir AIP: The Ontology Software Development Kit](https://blog.palantir.com/building-with-palantir-aip-the-ontology-software-development-kit-823fe5ac7aae) - The OSDK enables you to build a custom SDK for your business, harnessing the full power of the Palan...

41. [Palantir's Unconventional Boot Camps Driving Sales, CEO Says](https://www.lambham.com/post/palantir-s-unconventional-boot-camps-driving-sales--ceo-says/) - According to Palantir CEO Alex Karp, the company’s unconventional boot camps are driving sales. Thes...

42. [Palantir's commercial business scales with help of AI boot camps](https://www.constellationr.com/insights/news/palantirs-commercial-business-scales-help-ai-boot-camps) - Palantir has seen traction with "AIP boot camps," which deliver real workflows on customer data in 5...

43. [Attending the Palantir Technologies Bootcamp was an incredible experience.… | AKOS](https://www.linkedin.com/posts/akos-web_attending-the-palantir-technologies-bootcamp-activity-7221608668994121729-TnqW) - Attending the Palantir Technologies Bootcamp was an incredible experience. We are highly impressed w...

44. [Palantir Technologies Deployment Strategist Interview Preparation ...](https://www.cleverprep.com/companies/palantir/deployment-strategist) - Palantir Technologies Deployment Strategist interview preparation guide. Real questions, expert tips...

45. [Palantir Deployment Strategist Interview Guide - Prepfully](https://prepfully.com/interview-guides/palantir-deployment-strategist) - The on-site interview is a significant step in the process and typically consists of three 45-minute...

46. [Developing Your AI Intuition | AIP Bootcamps | Palantir Technologies](https://www.linkedin.com/posts/palantir-technologies_developing-your-ai-intuition-aip-bootcamps-activity-7128418720619614208-CVAx) - The first step to deploying LLMs in your enterprise: building your AI intuition. See how we introduc...

47. [Workflow application and user interface builder integrating objects, relationships, and actions](https://www.perplexity.ai/rest/file-repository/patents/US11086602B2?lens_id=021-149-217-020-262) - publication_number: US11086602B2
assignee: PALANTIR TECHNOLOGIES INC
abstract: Systems, techniques, ...

48. [Ontological mapping of data](https://www.perplexity.ai/rest/file-repository/patents/US11461355B1?lens_id=163-590-314-012-308) - publication_number: US11461355B1
assignee: PALANTIR TECHNOLOGIES INC
abstract: Systems, methods, and...

49. [Systems and methods for facilitating data transformation](https://www.perplexity.ai/rest/file-repository/patents/US9946777B1?lens_id=010-659-523-250-315) - publication_number: US9946777B1
assignee: PALANTIR TECHNOLOGIES INC
abstract: Systems and methods ar...

50. [Ontology-backed automatic chart creation](https://www.perplexity.ai/rest/file-repository/patents/US10861203B1?lens_id=080-806-781-989-872) - publication_number: US10861203B1
assignee: PALANTIR TECHNOLOGIES INC
abstract: Systems and methods f...

51. [SYSTEM TO GENERATE CURATED ONTOLOGIES](https://www.perplexity.ai/rest/file-repository/patents/US20200201855A1?lens_id=193-738-882-509-036) - publication_number: US20200201855A1
assignee: PALANTIR TECHNOLOGIES INC
abstract: Example embodiment...

52. [Inside Palantir's AI Sales Secret Weapon: Software Boot Camp](https://www.bloomberg.com/news/articles/2024-04-23/inside-palantir-s-ai-sales-secret-weapon-software-boot-camp) - The company is averaging five boot camps a day this year to try to take advantage of the AI craze.

53. [[PDF] Palantir - Q4 2025 Investor Presentation](https://investors.palantir.com/files/Palantir%20-%20Q4%202025%20Investor%20Presentation.pdf) - Our Q4 2025 GAAP earnings per share was $0.24. Our Q4 2025 GAAP operating margin was 41%.

