# R7b - Missing Competitors & Adjacent Actors: Supplement to Main Competitor Map

**Date:** 2026-02-19
**Scope:** Actors and tools NOT covered in R2-competitor-trajectories.md
**Method:** Web research, Feb 2026

---

## Table of Contents

1. [Screen/Knowledge Capture Tools](#1-screenknowledge-capture-tools)
   - 1.1 Screenpipe
   - 1.2 Rewind.ai / Limitless
   - 1.3 Microsoft Recall
   - 1.4 Granola.ai
2. [Infrastructure / Middleware (Stack Neighbors)](#2-infrastructure--middleware-stack-neighbors)
   - 2.1 Microsoft Fabric
   - 2.2 Nango
   - 2.3 Airbyte
   - 2.4 LangGraph / LangSmith (LangChain)
   - 2.5 Temporal
3. [French Consulting / Digital Transformation for PME](#3-french-consulting--digital-transformation-for-pme)
   - 3.1 Officeo
   - 3.2 3h18
   - 3.3 Mooncard / Spendesk / Libeo
4. [AI Meeting / Conversation Intelligence](#4-ai-meeting--conversation-intelligence)
   - 4.1 Fireflies.ai
   - 4.2 Fathom
   - 4.3 Noota
5. [Emerging "AI COO" / "AI Chief of Staff" Startups](#5-emerging-ai-coo--ai-chief-of-staff-startups)
   - 5.1 Lindy.ai
   - 5.2 Bardeen.ai
   - 5.3 Composio
   - 5.4 "Palantir for Small Business" scan
6. [Summary Matrix](#6-summary-matrix)

---

## 1. Screen/Knowledge Capture Tools

Spider's thesis T3 posits that 80% of PME operational knowledge is tacit -- in people's heads, in ad-hoc conversations, in what people *see* on screen but never document. These tools attack that problem from different angles.

---

### 1.1 Screenpipe

| Attribute | Detail |
|-----------|--------|
| **URL** | [screenpi.pe](https://screenpi.pe/) |
| **What it does** | Open-source "AI screen memory." Records your screen 24/7, extracts text via OCR, records audio, stores everything locally. You can then search your entire history and automate workflows based on what you've seen/heard. |
| **Founded** | 2024 (San Francisco) |
| **Funding** | Seed stage. Investors: Embedding VC, Founders Inc, Top Harvest Capital. Amount not publicly disclosed. |
| **Pricing** | Free (open-source, self-hosted). Screenpipe Pro: $29/month or $228/year for cloud sync across devices. |
| **Key tech** | MCP server integration (works with Claude Desktop, Cursor). 100% local storage by default. Multi-monitor capture. |
| **Users** | Growing -- Microsoft, Intel, Oracle, GitHub, Alibaba Cloud are testing it. |
| **Recent** | Jan 2026: major upgrade with Claude integration, full timeline, search. |

**How close to Spider's tacit capture thesis?**

Very close in concept, distant in execution. Screenpipe solves the "what did I see/say/hear?" problem for *individuals*. It is a personal memory tool. Spider's tacit capture thesis is about extracting *organizational* knowledge from multiple people and embedding it in business processes. The gap:

- Screenpipe = individual replay / personal productivity
- Spider = organizational knowledge capture -> agent-driven action

**Relevance to Spider: ADJACENT -- Potential integration layer**

Screenpipe could theoretically be a *data source* for Spider agents. If a PME director runs Screenpipe, Spider could (with consent) mine that data to understand workflows that are never documented. But this requires deep privacy/consent work and is not a competitive threat. Screenpipe is not building enterprise features, CRM integrations, or business process automation.

Sources: [Screenpipe](https://screenpi.pe/), [GitHub](https://github.com/mediar-ai/screenpipe), [Screenpipe Blog](https://screenpi.pe/blog/screenpipe-024-developer-program-launch)

---

### 1.2 Rewind.ai / Limitless

| Attribute | Detail |
|-----------|--------|
| **URL** | Defunct (app sunset Dec 2025) |
| **What it did** | Personal AI that recorded everything on your screen, made it searchable. Pivoted in 2024 to a $99 wearable pendant that recorded conversations. |
| **Founded** | By Dan Siroker (ex-Optimizely CEO) and Brett Bejcek |
| **Funding** | $15M at $350M valuation (May 2023, led by a16z) |
| **Current status** | **Acquired by Meta in December 2025.** Hardware sales stopped. Rewind desktop app disabled screen/audio capture as of Dec 19, 2025. Existing pendant customers moved to free Unlimited Plan for 1 year, then wind-down. |
| **Why acquired** | Meta likely acquiring for talent and IP related to always-on AI capture for Meta's AI glasses/wearable strategy. |

**Relevance to Spider: IRRELEVANT (dead product)**

Rewind/Limitless is no longer a market actor. The concept (personal screen memory) is validated but the company is absorbed into Meta. The key takeaway for Spider: the "capture everything" approach generated massive privacy backlash and was commercially unviable as a standalone product. The pendant pivot (trying to make it social/conversational rather than screen-based) also failed commercially. Spider should learn from this: tacit capture must be *consent-first* and *purpose-driven* (capture for a specific business outcome), not "record everything."

Sources: [TechCrunch (Meta acquisition)](https://techcrunch.com/2025/12/05/meta-acquires-ai-device-startup-limitless/), [WinBuzzer](https://winbuzzer.com/2025/12/05/meta-acquires-ai-wearables-startup-limitless-kills-pendant-sales-and-sunsets-rewind-app-xcxwbn/), [9to5Mac](https://9to5mac.com/2025/12/05/rewind-limitless-meta-acquisition/)

---

### 1.3 Microsoft Recall

| Attribute | Detail |
|-----------|--------|
| **What it is** | Windows 11 feature that takes periodic screenshots of everything on-screen, stores locally, makes searchable via AI. |
| **Status (Feb 2026)** | **Still in Windows Insider preview only.** Not generally available. Rolling out gradually to select users after multiple delays and privacy controversies. |
| **Requirements** | Copilot+ PC with 16GB RAM, 256GB storage, NPU chip, Windows Hello biometric enrollment. |
| **Privacy changes** | Now requires Windows Hello enrollment. Filters sensitive info (passwords, credit cards, SSNs) by default. Some apps (Signal) actively block Recall screenshots. |
| **Pricing** | Free (built into Windows 11 on qualifying hardware). |

**Relevance to Spider: LOW (different universe)**

Microsoft Recall targets individual Windows users on expensive new hardware. French PME directors are on mixed Mac/Windows/phone environments. Recall does not aggregate organizational knowledge, does not connect to ERPs or CRMs, and does not trigger business actions. It is a personal search tool, not a business operations layer.

The only indirect threat: if Recall becomes a gateway for Microsoft Copilot to understand business context better, that strengthens the Microsoft 365 + Copilot stack as an alternative to Spider. But this is 2-3 years away from being real for PME.

Sources: [Microsoft Learn](https://learn.microsoft.com/en-us/windows/apps/develop/windows-integration/recall/), [PC Gamer](https://www.pcgamer.com/gaming-industry/microsoft-is-finally-rolling-out-its-controversial-recall-feature-that-screenshots-everything-you-do-again-but-only-for-select-users/), [IT Pro](https://www.itpro.com/technology/artificial-intelligence/microsoft-windows-recall-copilot-pc-rollout)

---

### 1.4 Granola.ai

| Attribute | Detail |
|-----------|--------|
| **URL** | [granola.ai](https://www.granola.ai/) |
| **What it does** | AI meeting notepad. Captures audio directly from your device (no bot joins the call). Generates structured meeting notes, action items, searchable transcripts. New collaboration features let teams share and cross-reference notes. |
| **Founded** | UK-based |
| **Funding** | $67.2M total. Seed $4.25M. Series A $20M+ (Oct 2024). Series B $43M at $250M valuation (May 2025, led by NFDG - Nat Friedman & Daniel Gross). |
| **Pricing** | Free: 25 lifetime meetings. Individual: $18/month. Business: $14/user/month. Enterprise: $35/user/month (opt-out of model training). |
| **Key differentiator** | No bot in the call. Captures via system audio output. Less intrusive than Fireflies/Otter. |

**Relevance to Spider: ADJACENT -- Potential data source**

Granola captures tacit knowledge from conversations, which aligns with Spider's thesis. However, Granola is a *note-taking* tool, not an *operations* tool. It does not trigger actions, update CRMs, or create tasks in ERPs. Granola's collaboration features are team-oriented but still document-centric.

Spider could integrate with Granola (or Noota, which Spider already uses) as a meeting intelligence input: "what was decided in the meeting" feeds Spider's agents to execute follow-ups. But Granola itself is not competing with Spider.

**Threat level: NONE. Integration opportunity: MEDIUM.**

Sources: [TechCrunch](https://techcrunch.com/2025/05/14/ai-note-taking-app-granola-raises-43m-at-250m-valuation-launches-collaborative-features/), [Granola](https://www.granola.ai/), [tl;dv review](https://tldv.io/blog/granola-review/)

---

## 2. Infrastructure / Middleware (Stack Neighbors)

These are tools Spider either uses, could use, or competes with at the infrastructure layer.

---

### 2.1 Microsoft Fabric

| Attribute | Detail |
|-----------|--------|
| **What it is** | End-to-end analytics SaaS platform unifying data integration, transformation, warehousing, real-time processing, data science, and BI. Centered on OneLake (unified data lake). |
| **GA date** | November 2023 |
| **Pricing** | SaaS, capacity-based. Enterprise-oriented pricing. |
| **2026 status** | Maturing into enterprise-grade governance. AI-assisted governance features. Deeper security controls. |

**Relevance to Spider: LOW (different league, different ICP)**

Microsoft Fabric is an enterprise data platform. French PME with 20-500 employees and 2M-50M EUR revenue are not buying Microsoft Fabric. They barely use Power BI. Fabric is for companies with dedicated data teams, data engineers, and analytics budgets.

Spider's data layer is fundamentally different: Spider connects to *operational* data (Odoo, emails, files, conversations) and triggers *actions*. Fabric connects to *analytical* data (warehouses, lakes, pipelines) and produces *dashboards*. These are complementary, not competitive.

**Verdict: IRRELEVANT for Spider's ICP.**

Sources: [Atlan](https://atlan.com/microsoft-fabric/), [Microsoft](https://www.microsoft.com/en-us/microsoft-fabric), [DynaTech](https://dynatechconsultancy.com/blog/microsoft-fabric-unified-data-ai-platform-for-enterprise)

---

### 2.2 Nango

| Attribute | Detail |
|-----------|--------|
| **URL** | [nango.dev](https://nango.dev/) |
| **What it does** | Developer infrastructure for API integrations. Started as open-source OAuth handler for 40 APIs, now supports 400+ APIs with 600+ pre-built integrations. Handles auth (OAuth, API keys), token refresh, webhooks, observability. |
| **Founded** | YC-backed |
| **Funding** | Seed round (amount not disclosed publicly). |
| **Pricing** | Free tier. Growth: $50/month + $1/account/month + $0.01/request. Enterprise: custom. |

**Spider uses Nango.** This is an infrastructure partner, not a competitor.

**Competitors to Nango (relevant if Spider wants to diversify or switch):**

| Platform | Focus | Differentiator | Relevance to Spider |
|----------|-------|-----------------|---------------------|
| **Merge** | Unified API for HRIS/ATS/accounting/CRM | Pre-built unified data models across 200+ integrations. Best for standardized HR/finance integrations. | Low -- Merge's unified models are too rigid for Spider's cross-system agent needs. |
| **Codat** | Accounting & banking integrations for fintech | Deep financial data models for underwriting, loan approval. | Irrelevant -- Spider is not fintech. |
| **Paragon** | Embedded iPaaS + developer SDK | Visual builder + full SDK. Most extensible. | Medium -- could be Nango alternative if Spider needs embedded integration UX for clients. |
| **Finch** | HR/payroll integrations only | 200+ employment systems. | Irrelevant -- too narrow. |
| **Composio** | AI agent integration SDK | 500+ pre-built LLM-optimized toolkits. Agent-native auth. Closed-source tools. | HIGH -- direct competitor to Nango for Spider's agent use case. Composio is purpose-built for AI agents, while Nango is general-purpose. Spider should evaluate Composio as a Nango complement or replacement for agent-specific integrations. |

**Verdict: INFRASTRUCTURE PARTNER. Composio is the one to watch as a potential alternative/complement.**

Sources: [Nango pricing](https://nango.dev/pricing), [Merge alternatives](https://www.merge.dev/blog/nango-alternatives), [Composio](https://composio.dev/blog/nango-alternatives-ai-agents), [Nango blog](https://www.nango.dev/blog/4-most-popular-merge-dev-alternatives)

---

### 2.3 Airbyte

| Attribute | Detail |
|-----------|--------|
| **URL** | [airbyte.com](https://airbyte.com/) |
| **What it does** | Open-source data integration (ELT) platform. Moves data from sources to destinations via pre-built connectors. 300+ connectors. |
| **Founded** | 2020 (San Francisco) |
| **Funding** | $181.35M total. Series B: $150M (Dec 2021). |
| **Pricing** | Open-source: free (self-hosted). Cloud: usage-based. Disrupted pricing in Feb 2025, moving away from volume-based model. Enterprise: custom ($20k+ threshold). |

**Relevance to Spider: LOW -- Different layer**

Airbyte is an ETL/ELT tool that moves data in batch from A to B (e.g., from Salesforce to a data warehouse). Spider needs *real-time operational integration* -- reading and writing back to systems, triggering actions, maintaining state. Airbyte does not do action execution, does not maintain agent state, and is designed for analytics pipelines, not operational automation.

Spider might use Airbyte for bulk data ingestion (e.g., syncing Odoo data to Spider's knowledge base), but it is not a competitor. It is a plumbing tool, not an intelligence layer.

**Verdict: INFRASTRUCTURE -- Possible data ingestion tool, not a competitor.**

Sources: [Airbyte pricing](https://airbyte.com/pricing), [Tracxn](https://tracxn.com/d/companies/airbyte/__msyjFhyA1oYCHhgK3YkbjM6Jfs3I4ehkOtBsvWydrDU)

---

### 2.4 LangGraph / LangSmith (LangChain)

| Attribute | Detail |
|-----------|--------|
| **URL** | [langchain.com](https://www.langchain.com/) |
| **What it does** | LangGraph: open-source agent orchestration framework. Stateful, durable agents with human-in-the-loop. LangSmith: observability/evaluation platform for LLM apps. |
| **Milestones** | LangChain and LangGraph reached v1.0 in 2025. |
| **Users** | Uber, LinkedIn, Klarna. |
| **Pricing** | LangGraph: free (open-source). LangSmith Developer: free (5k traces/month). Plus: $39/seat/month (10k traces). Enterprise: custom. Traces: $2.50-5.00/1k. Deployments: $0.005/run. |

**Relevance to Spider: INFRASTRUCTURE -- Spider likely uses this or should**

LangGraph is the *framework* for building agents. It is not a product that competes with Spider -- it is a tool Spider could use to *build* its agent layer. The distinction is critical:

- **LangGraph** = a framework (like React is to web apps). You build with it.
- **Spider** = a product (like Salesforce is to CRM). Users buy it.

No PME buys "LangGraph." They buy Spider, which might be built on LangGraph internally.

LangSmith is relevant as an observability tool for Spider's engineering team -- monitoring agent performance, debugging failures, tracking costs.

**Direct competitor to Spider's agent layer? NO.** LangGraph does not come with PME connectors, Odoo integrations, business logic, or managed services. It is scaffolding, not a building.

**Verdict: INFRASTRUCTURE TOOL -- Spider should evaluate for internal use. Not a competitor.**

Sources: [LangChain](https://www.langchain.com/langgraph), [LangChain blog](https://blog.langchain.com/langchain-langgraph-1dot0/), [LangSmith pricing](https://www.langchain.com/pricing)

---

### 2.5 Temporal

| Attribute | Detail |
|-----------|--------|
| **URL** | [temporal.io](https://temporal.io/) |
| **What it does** | Durable execution / workflow orchestration platform. Ensures long-running workflows survive crashes, restarts, infrastructure failures. Think "saga pattern as a service." |
| **Founded** | Seattle |
| **Funding** | ~$650M total. Series C: $146M at $1.72B (March 2025). **Series D: $300M at $5B valuation (Feb 2026, led by a16z).** |
| **Users** | OpenAI, Netflix. Billions of workflow executions on platform. |
| **Revenue** | 380% YoY revenue expansion (2025-2026). |
| **Pricing** | Open-source: free. Temporal Cloud: multi-tenant, usage-based. |
| **2026 positioning** | Pivoting hard toward "agentic AI infrastructure." Building microservices to support AI agents. |

**Relevance to Spider: INFRASTRUCTURE -- High-value for Spider's pipeline reliability**

Temporal solves a critical problem for Spider: what happens when an agent workflow is halfway through updating Odoo, sending an email, and syncing a CRM, and the server crashes? Temporal ensures the workflow resumes exactly where it left off.

For Spider's multi-step agent pipelines (connect to Odoo -> read data -> reason -> write back -> send notification -> update CRM), Temporal-style durable execution is essential. Spider does not *compete* with Temporal -- Spider could *build on* Temporal.

The $5B valuation and a16z's bet signal that workflow orchestration for AI agents is considered foundational infrastructure. This validates Spider's architectural need for reliable agent execution.

**Verdict: INFRASTRUCTURE PARTNER -- Spider should seriously evaluate Temporal for agent pipeline reliability. Not a competitor.**

Sources: [TechCrunch](https://techcrunch.com/2025/03/31/temporal-lands-146-million-at-a-flat-valuation-eyes-agentic-ai-expansion/), [GeekWire](https://www.geekwire.com/2026/temporal-raises-300m-hits-5b-valuation-as-seattle-infrastructure-startup-rides-ai-wave/), [SiliconANGLE](https://siliconangle.com/2026/02/17/ai-agent-reliability-startup-temporal-raises-300m-funding/)

---

## 3. French Consulting / Digital Transformation for PME

These are the *human* competitors -- what PME do today instead of buying Spider.

---

### 3.1 Officeo

| Attribute | Detail |
|-----------|--------|
| **URL** | [officeopro.com](https://officeopro.com/) |
| **What it does** | N.1 francais de l'assistance administrative aux entreprises. Network of 6,000+ freelance administrative assistants across France. Deployable within 48 hours. |
| **Pricing** | 38-50 EUR/hour HT, billed on actual hours worked. No setup fees, no commitment. Urgency surcharge +25-50%. |
| **Target** | PME, liberal professions, associations, local authorities, large groups. |
| **Model** | Human-as-a-service. You get a person, not software. |

**Relevance to Spider: DIRECT INCUMBENT (human baseline)**

Officeo is what PME do today instead of using AI agents for back-office. A PME director who needs help with admin, accounting, HR -- they call Officeo and get a human assistant for 40-50 EUR/hour.

**Spider's competitive case vs. Officeo:**

| Dimension | Officeo | Spider |
|-----------|---------|--------|
| Response time | 48h to deploy | Instant (software) |
| Availability | Business hours | 24/7 |
| Cost per hour | 38-50 EUR | Lower (software) |
| Scalability | Linear (more hours = more cost) | Marginal cost near zero |
| Knowledge retention | Person leaves, knowledge leaves | Persists in system |
| Error rate | Human-level | Lower for repetitive tasks |
| Complex judgment | High | Lower (for now) |
| Trust/relationship | High (human) | Low (software, unfamiliar) |

**The real insight:** Spider's first customers might be PME who currently *use* Officeo and want to reduce costs. The sales pitch: "You're paying 50 EUR/hour for someone to do data entry and email follow-ups. Spider does that for 500 EUR/month flat, 24/7, and never forgets."

**But the risk:** PME trust human assistants more than AI. Officeo's model is deeply understood. Spider must first prove reliability before PME will switch.

**Verdict: DIRECT INCUMBENT -- Not a tech competitor but the primary behavioral alternative. Spider must be cheaper, faster, and more reliable than Officeo to win.**

Sources: [Officeo](https://officeopro.com/), [Officeo tarifs](https://officeopro.com/tarifs-prestation-services-administratifs/), [Officeo PME](https://officeopro.com/assistante-pme/)

---

### 3.2 3h18

| Attribute | Detail |
|-----------|--------|
| **URL** | [3h18.fr](https://www.3h18.fr/) |
| **What it does** | Administrative and HR outsourcing for PME. Network of freelance experts for admin, HR, accounting, commercial support. Minimum 2 hours/month. |
| **Pricing** | 50-80 EUR/hour for independent secretaries. Billed monthly for actual work performed. Charged as operating expense (not personnel cost). |
| **Target** | PME, micro-enterprises, startups, liberal professions. |
| **Model** | Same as Officeo: human-as-a-service. Positioned slightly more toward HR/recruitment outsourcing. |

**Relevance to Spider: DIRECT INCUMBENT (same as Officeo)**

Same analysis as Officeo. 3h18 is the *status quo* for PME back-office support. The key difference: 3h18 emphasizes HR and recruitment outsourcing, which overlaps with Spider's potential HR agent (job posting, CV screening, interview scheduling).

At 50-80 EUR/hour, 3h18 is even more expensive than Officeo. The cost arbitrage for Spider is larger.

**Verdict: DIRECT INCUMBENT -- Same behavioral alternative as Officeo, with stronger HR angle.**

Sources: [3h18](https://www.3h18.fr/), [3h18 tarifs](https://www.3h18.fr/tarifs), [3h18 externalisation RH](https://www.3h18.fr/blog/externalisation-rh)

---

### 3.3 Mooncard / Spendesk / Libeo

These three represent **vertical fintech automation for PME** -- each attacking a specific financial workflow.

#### Mooncard

| Attribute | Detail |
|-----------|--------|
| **URL** | [mooncard.co](https://www.mooncard.co/) |
| **What it does** | Corporate payment cards with automated expense management. Card transaction -> automatic categorization -> accounting export. |
| **Funding** | ~$75M total. Series C: $40.6M (April 2023). |
| **Revenue** | $15.1M (2025). 137 employees. |
| **Customers** | 6,000+ |

#### Spendesk

| Attribute | Detail |
|-----------|--------|
| **URL** | [spendesk.com](https://www.spendesk.com/) |
| **What it does** | Complete corporate spend management: cards, invoices, reimbursements, budgets, approvals. |
| **Funding** | $311.1M total. Valuation: $1.5B (unicorn). |
| **Revenue** | $52M ARR (March 2025). 300 employees. |
| **Status** | Reached profitability in June 2025. Spendesk Travel launching 2026. |

#### Libeo

| Attribute | Detail |
|-----------|--------|
| **URL** | [libeo.io](https://libeo.io/) |
| **What it does** | Accounts payable automation: invoice collection, supplier management, bill payments, cash flow management. |
| **Founded** | 2018 (Paris/Vincennes) |
| **Funding** | ~$45M total. Series A: $24.2M (Feb 2021, led by DST Global Partners). |
| **Employees** | 90 |
| **Recent** | Acquired TrackPay (payment tracking). |

**Relevance to Spider: ADJACENT -- Vertical overlap on specific workflows**

These three companies each automate a *single financial workflow* that a Spider agent could theoretically handle (expense tracking, invoice processing, payment management). However:

1. **They are deeply vertical.** Mooncard is a payment card + OCR + accounting sync. Spider is not going to issue payment cards.
2. **They have banking/fintech regulatory moats.** Payment processing requires licenses that Spider does not and should not pursue.
3. **They are Spider's *data sources*, not competitors.** A Spider agent could read expense data from Spendesk and combine it with Odoo data and email data to provide operational insights that Spendesk alone cannot.

The real overlap: if Spider builds an "expense follow-up" agent that reminds employees to submit receipts, categorizes expenses, and syncs to accounting -- that agent is doing 30% of what Mooncard/Spendesk do. But Spider would never match the card-issuance, bank-integration, and compliance depth.

**Key strategic context:** France's mandatory e-invoicing reform (Sept 2026 for large/ETI, Sept 2027 for PME) creates a compliance urgency that these players and Pennylane will capitalize on. Spider should not compete here but should ensure its agents work *with* whatever invoicing tool the PME uses.

**Verdict: ADJACENT -- Not competitors. Potential integration partners. Spider agents should read from these tools, not replace them.**

Sources: [Mooncard](https://www.mooncard.co/), [Spendesk (Sifted)](https://sifted.eu/articles/spendesk-profitability-2025), [Libeo](https://libeo.io/), [Capterra Mooncard](https://www.capterra.com/p/194946/Mooncard/)

---

## 4. AI Meeting / Conversation Intelligence

Spider's tacit knowledge capture could leverage meeting transcription as a primary input source.

---

### 4.1 Fireflies.ai

| Attribute | Detail |
|-----------|--------|
| **URL** | [fireflies.ai](https://fireflies.ai/) |
| **What it does** | AI meeting notetaker. Bot joins calls, records, transcribes, generates summaries and action items. Integrates with CRM (Salesforce, HubSpot). 100+ languages. |
| **Valuation** | $1B (June 2025) |
| **Users** | 20M+ users, 500K+ organizations, 75% of Fortune 500 |
| **Pricing** | Free: limited. Pro: $10/user/month (annual) or $18 (monthly). Business: $19-29/user/month. Enterprise: $39/user/month. Additional AI credit packs: $5-$600. |
| **Key feature** | "Talk to Fireflies" (powered by Perplexity): ask questions and get web search during meetings. |

**Relevance to Spider: ADJACENT -- Data source, not competitor**

Fireflies captures meeting content that Spider's agents could act on. But Fireflies does not execute business actions -- it does not update Odoo, send follow-up emails, or create tasks. It is a recording + transcription + search tool.

Spider could integrate with Fireflies as a meeting intelligence input, but Noota (which Spider already uses) serves the same purpose. No need to switch.

**Verdict: ADJACENT. Not a threat. Noota is the better fit for Spider due to French/GDPR orientation.**

Sources: [Fireflies pricing](https://fireflies.ai/pricing), [Outdoo review](https://www.outdoo.ai/blog/fireflies-ai-pricing)

---

### 4.2 Fathom

| Attribute | Detail |
|-----------|--------|
| **URL** | [fathom.video](https://fathom.video/) |
| **What it does** | Free AI meeting assistant. Auto-joins Zoom/Meet/Teams, records, transcribes (28 languages), generates summaries within 30 seconds. CRM sync (HubSpot, Salesforce). |
| **Funding** | $2M+ crowdfunded. No major VC rounds disclosed. |
| **Pricing** | Free forever (individual): unlimited recording/transcription, 5 AI summaries/month. Premium: ~$15-19/user/month. Team plans available. |
| **Recognition** | #1 on G2 (5.0 rating). Fastest-growing HubSpot Marketplace app. |
| **Recent** | Oct 2025: Asana integration, AI coaching tools, public API, botless recording. |

**Relevance to Spider: LOW -- Same category as Fireflies/Noota**

Fathom is a meeting note tool. Free tier is generous. Good product but no operational automation. Same analysis as Fireflies: data source, not competitor.

**Verdict: LOW RELEVANCE. Noota already serves Spider's needs in this space.**

Sources: [Fathom](https://fathom.video/), [BusinessWire](https://www.businesswire.com/news/home/20251008689349/en/Fathom-Expands-with-New-Features-Designed-to-Extract-Maximum-Value-From-Every-Conversation), [MeetGeek review](https://meetgeek.ai/blog/fathom-ai-pricing)

---

### 4.3 Noota (Spider's current tool)

| Attribute | Detail |
|-----------|--------|
| **URL** | [noota.io](https://www.noota.io/) |
| **What it does** | AI meeting assistant with strong recruitment and sales orientation. Records meetings and phone calls, transcribes in 50+ languages, generates structured reports with key takeaways and action items, drafts follow-up emails. Integrates with CRM and ATS. |
| **Founded** | Toulouse, France |
| **Funding** | EUR 3M (May 2025, led by Blast Club, with Sharpstone and Bpifrance). Total: ~$3.4M. Microsoft France is also an investor. |
| **Pricing** | Free: basic. Pro: $29/user/month. Business: $49/user/month. Enterprise: custom. |
| **Users** | 100K+ users, 50K transcriptions/week. |
| **Compliance** | GDPR, SOC2, ISO 27001. EU data centers. |
| **Key differentiators** | French-founded, GDPR-first, strong recruitment/sales use cases, phone call recording (not just video meetings). |

**Why Spider uses Noota:**

Noota is the best fit for Spider's ICP because:
1. French company -> GDPR compliance, EU hosting, French language support
2. Phone call recording (PME directors talk on the phone more than video calls)
3. Recruitment focus aligns with Spider's HR agent use case
4. Sales intelligence features align with Spider's CRM agent
5. Small company (EUR 3M funding, 29 employees) -> potential for deep partnership or integration

**Noota's competitors (for reference):**

| Tool | Key Difference vs. Noota |
|------|--------------------------|
| Fireflies.ai | Larger (20M users, $1B valuation). More integrations. Less GDPR-focused. |
| Otter.ai | Consumer/prosumer focused. US-centric. |
| Granola.ai | No bot (captures via system audio). More privacy-friendly. No phone recording. |
| Fathom | Free tier generous. Strong HubSpot integration. US-focused. |
| tl;dv | European. Focus on sales/CS calls. |

**Verdict: INFRASTRUCTURE PARTNER -- Spider already uses Noota. The integration should deepen: Noota captures conversations -> Spider agents act on the content.**

Sources: [Noota](https://www.noota.io/), [SiliconCanals](https://siliconcanals.com/frances-noota-secures-3m/), [The AI Insider](https://theaiinsider.tech/2025/05/28/noota-raises-e3m-to-expand-ai-powered-recruitment-and-meeting-intelligence-platform/)

---

## 5. Emerging "AI COO" / "AI Chief of Staff" Startups

This is Spider's direct competitive category: tools that aim to automate business operations end-to-end.

---

### 5.1 Lindy.ai

| Attribute | Detail |
|-----------|--------|
| **URL** | [lindy.ai](https://www.lindy.ai/) |
| **What it does** | AI assistant platform for work. Automates email management, customer support, scheduling, CRM data entry, meeting notes. 1,600+ app integrations (Gmail, Zoom, Twilio, Slack, HubSpot, etc.). |
| **Founded** | 2023 by Flo Crivello (San Francisco) |
| **Funding** | $49.9M total. Series B: $35M (Jan 2023). |
| **Revenue** | $5.1M (Oct 2024). |
| **Team** | 11-50 employees. |
| **Key feature** | "AI assistant that runs your work life." Proactive -- not just reactive to prompts. |
| **Recent** | Sept 2025: integrated Claude Sonnet 4.5 for 30+ hour autonomous operation on complex tasks. |

**Relevance to Spider: MEDIUM-HIGH -- Closest "AI COO" equivalent**

Lindy is the closest publicly-visible startup to Spider's "AI operating layer for business" vision. Key comparison:

| Dimension | Lindy | Spider |
|-----------|-------|--------|
| ICP | US-centric, individual professionals & teams | European PME (2M-50M EUR) |
| Approach | Horizontal (any workflow, any tool) | Vertical (PME operations, ERP-connected) |
| ERP integration | No Odoo/SAP/ERP connectors visible | Odoo-first |
| Managed services | No | Yes (Spider includes human oversight layer) |
| Language/market | English, US | French, EU |
| Data depth | Connects to apps, acts on surface data | Aims to capture tacit knowledge + operational context |
| Pricing | Not publicly disclosed (likely per-seat SaaS) | Outcome-based (Spider's thesis) |

**Why Lindy is not yet a direct threat to Spider:**
1. No ERP integration. Lindy connects to SaaS apps (Gmail, Slack, HubSpot) but not to Odoo, SAP, or structured operational data.
2. No managed services layer. Spider's thesis includes human-in-the-loop oversight for PME who do not trust full automation. Lindy is pure software.
3. No European/French focus. PME need French-language agents, RGPD compliance, EU hosting. Lindy is US-first.
4. Lindy automates individual tasks. Spider aims to orchestrate cross-functional business processes.

**Why Lindy could become a threat in 18 months:**
1. If Lindy adds ERP connectors and enters Europe.
2. If Lindy moves from individual assistant to organizational operations platform.
3. If Lindy's $49.9M in funding allows them to build vertical solutions for SMB operations.

**Verdict: MEDIUM-HIGH THREAT -- Not today, but closest positioning. Watch closely.**

Sources: [Lindy](https://www.lindy.ai/), [Crunchbase](https://www.crunchbase.com/organization/lindy), [Latka](https://getlatka.com/companies/lindyai)

*Note: Lindy was already covered briefly in R2-competitor-trajectories.md. This supplements with deeper analysis.*

---

### 5.2 Bardeen.ai

| Attribute | Detail |
|-----------|--------|
| **URL** | [bardeen.ai](https://www.bardeen.ai/) |
| **What it does** | No-code AI workflow automation via Chrome extension. Drag-and-drop workflow builder with AI agents (copilots) for sales, marketing, project management. 100+ app integrations. |
| **Founded** | 2020 by Artem Harutyunyan and Pascal Weinberger |
| **Funding** | Not publicly disclosed in detail. VC-backed. |
| **Pricing** | Free: basic automations, 100+ templates. Starter: $99/month (annual), 15k credits/year. |
| **Key 2025 move** | May 2025: launched "Work Intelligence Platform" -- AI agents that learn how work happens and execute/improve it autonomously. |

**Relevance to Spider: LOW-MEDIUM**

Bardeen is a *workflow automation* tool (like Zapier with AI), not an *operations management* system. It automates individual tasks (scrape data, fill forms, send messages) but does not orchestrate cross-functional business processes or connect to ERPs.

The "Work Intelligence Platform" (May 2025) is directionally interesting -- agents that "learn how work happens" is close to Spider's tacit capture thesis. But execution is browser-based, US-focused, and individual-oriented.

**Verdict: LOW-MEDIUM THREAT -- More a Zapier/Make competitor than a Spider competitor.**

Sources: [Bardeen](https://www.bardeen.ai/), [PRNewswire](https://www.prnewswire.com/news-releases/bardeen-launches-its-work-intelligence-platform---the-ai-agent-to-automate-automations-302455104.html), [Voiceflow](https://www.voiceflow.com/blog/bardeen-ai)

---

### 5.3 Composio

| Attribute | Detail |
|-----------|--------|
| **URL** | [composio.dev](https://composio.dev/) |
| **What it does** | AI agent integration SDK. 500+ pre-built, LLM-optimized toolkits for connecting AI agents to apps (Salesforce, Jira, Gmail, etc.). Managed auth. Agent-native design. |
| **Positioning** | "The action layer for AI agents." Not an agent platform itself, but the plumbing that lets agents act on the world. |
| **Differentiator vs. Nango** | Composio tools are pre-built and LLM-optimized but closed-source. Nango is open-source and developer-controlled. Composio is faster to ship; Nango offers more customization. |

**Relevance to Spider: INFRASTRUCTURE -- Alternative to Nango for agent integrations**

Composio is not a competitor to Spider. It is a tool Spider could use *instead of* or *alongside* Nango for connecting agents to external APIs. The key advantage: Composio's tools are purpose-built for AI agents, whereas Nango is general-purpose API infrastructure.

**Verdict: INFRASTRUCTURE TOOL -- Spider should evaluate as Nango complement.**

Sources: [Composio](https://composio.dev/blog/nango-alternatives-ai-agents), [Composio platforms](https://composio.dev/blog/ai-agent-integration-platforms), [Nango comparison](https://nango.dev/blog/composio-alternatives)

---

### 5.4 "Palantir for Small Business" / "AI Operations for SMB" Scan

**Search result: No dedicated startup found with this exact positioning.**

The search for "Palantir for small business" returns only Palantir itself (which is aggressively enterprise/government, $1.18B quarterly revenue, $100B+ market cap, not SMB at all). Their AIP Bootcamp model reduces sales cycles from months to days, but their ICP remains Fortune 500 + government.

**What did emerge from the broader scan:**

| Startup | What it does | Relevance |
|---------|-------------|-----------|
| **Balance** (YC) | AI accountancy for SMBs. Agents close monthly books, chase invoices, prepare reports. | ADJACENT -- financial vertical, not operational. |
| **Podium** | AI-powered lead management for local businesses. 100K+ businesses. AI employee responds to leads. | ADJACENT -- sales/lead vertical only. |
| **Zapier Central** | AI bot that monitors spreadsheets, executes actions based on criteria. | Already covered in R2 under Zapier. |

**The gap is real.** No startup is clearly positioning as "Palantir for SMB" or "AI COO for small business" in the way Spider envisions. This is both an opportunity (whitespace) and a warning (maybe the market is not ready, or the problem is too hard to productize).

**The closest equivalents are:**
1. Lindy.ai (individual AI assistant, not SMB operations platform)
2. Dust.tt (enterprise AI agents, not SMB)
3. Spider itself (if it ships)

**Verdict: WHITESPACE CONFIRMED -- Spider's positioning as "AI operations layer for PME" does not have a direct, well-funded competitor. But the absence of competition may signal market timing risk, not just opportunity.**

Sources: [Bloomberg AI startups](https://www.bloomberg.com/features/2025-top-ai-startups/), [Foundation Capital](https://foundationcapital.com/where-ai-is-headed-in-2026/), [Business.com SMB AI](https://www.business.com/articles/ai-usage-smb-workplace-study/)

---

## 6. Summary Matrix

| # | Actor | Category | Direct Threat? | Integration Opp? | Verdict |
|---|-------|----------|---------------|-------------------|---------|
| 1 | **Screenpipe** | Screen capture | No | Medium (data source) | ADJACENT |
| 2 | **Rewind/Limitless** | Screen capture | No | None (dead) | IRRELEVANT |
| 3 | **Microsoft Recall** | Screen capture | No | None | LOW |
| 4 | **Granola.ai** | Meeting notes | No | Medium (data source) | ADJACENT |
| 5 | **Microsoft Fabric** | Analytics platform | No | None | IRRELEVANT |
| 6 | **Nango** | Integration infra | No (Spider uses it) | Already integrated | INFRASTRUCTURE PARTNER |
| 7 | **Composio** | Agent integration SDK | No | High (Nango alt/complement) | INFRASTRUCTURE -- EVALUATE |
| 8 | **Airbyte** | Data integration | No | Low (bulk ingestion) | INFRASTRUCTURE |
| 9 | **LangGraph/LangSmith** | Agent framework | No | High (build tool) | INFRASTRUCTURE -- EVALUATE |
| 10 | **Temporal** | Workflow orchestration | No | High (pipeline reliability) | INFRASTRUCTURE -- EVALUATE |
| 11 | **Officeo** | Human admin assistants | **Yes (incumbent)** | No | DIRECT INCUMBENT |
| 12 | **3h18** | Human admin/HR outsourcing | **Yes (incumbent)** | No | DIRECT INCUMBENT |
| 13 | **Mooncard** | Expense cards | No | Medium (data source) | ADJACENT |
| 14 | **Spendesk** | Spend management | No | Medium (data source) | ADJACENT |
| 15 | **Libeo** | AP automation | No | Medium (data source) | ADJACENT |
| 16 | **Fireflies.ai** | Meeting transcription | No | Low (Noota preferred) | ADJACENT |
| 17 | **Fathom** | Meeting transcription | No | Low | LOW |
| 18 | **Noota** | Meeting transcription | No (Spider uses it) | Already integrated | INFRASTRUCTURE PARTNER |
| 19 | **Lindy.ai** | AI work assistant | **Medium-High** | No | CLOSEST COMPETITOR -- WATCH |
| 20 | **Bardeen.ai** | Workflow automation | Low-Medium | No | ADJACENT (more Zapier competitor) |
| 21 | **"Palantir for SMB"** | -- | None found | -- | WHITESPACE CONFIRMED |

---

## Key Takeaways for Spider Strategy

### 1. The real competitors are humans, not software
Officeo (40-50 EUR/hour) and 3h18 (50-80 EUR/hour) are what PME actually buy today for back-office support. Spider's pricing must beat this on a per-task basis while matching trust. This is the *behavioral* competition.

### 2. The whitespace is real but risky
No well-funded startup is building "AI COO for SMB" or "Palantir for small business." Lindy.ai is the closest but is US-focused, individual-oriented, and has no ERP integration. This validates Spider's positioning but also raises the question: is nobody doing this because the market is not ready?

### 3. Infrastructure choices matter
Spider should evaluate three infrastructure tools seriously:
- **Composio** (agent integration SDK, alternative/complement to Nango)
- **LangGraph** (agent orchestration framework)
- **Temporal** ($5B, a16z-backed -- durable execution for agent pipelines)

### 4. Meeting intelligence is a solved input, not a moat
Noota, Fireflies, Fathom, Granola -- meeting transcription is commoditized. The moat is not in *capturing* conversations but in *acting* on them. Spider's value is the action layer, not the capture layer.

### 5. The Rewind.ai cautionary tale
Rewind (a16z-backed, $350M valuation) tried "capture everything" and failed commercially. Acquired by Meta for talent, product shut down. Lesson: tacit capture must be *purpose-driven* and *consent-first*. Do not try to record everything -- capture what matters for specific business outcomes.

### 6. French fintech vertical is occupied
Pennylane ($4.25B), Spendesk ($1.5B), Mooncard, Libeo -- the financial operations vertical for French PME is well-funded and competitive. Spider should integrate with these tools, not compete with them. Spider's lane is *cross-functional operations*, not financial management.
