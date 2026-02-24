# Deep Research Prompts for Spider Strategy
**Date:** February 17, 2026
**Purpose:** Fill remaining knowledge gaps identified after reading all 13 research documents and running complementary research agents.

---

## Prompt #1 — Palantir Ontology: The Technical Implementation Nobody Documents

**Goal:** Understand the engineering decisions behind Palantir's Ontology layer to inform Spider's PostgreSQL-based implementation.

**What we already know:** 6 primitives (Object Types, Properties, Links, Actions, Interfaces, Value Types); 3 layers (Semantic, Kinetic, Dynamic); Object Storage V2; OMS/OSS microservices.

**What we need:** The HOW — implementation details for building an equivalent.

```
You are conducting deep technical research for a startup building an open-source
alternative to Palantir's Ontology layer, targeting European SMBs on PostgreSQL.

We already know the WHAT (6 primitives: Object Types, Properties, Links, Actions,
Interfaces, Value Types; 3 layers: Semantic, Kinetic, Dynamic; Object Storage V2;
OMS/OSS microservices). We need the HOW — the engineering decisions that make it
work in production.

Research these specific implementation questions:

1. SCHEMA EVOLUTION & VERSIONING
- How does Palantir handle Ontology schema changes when a backing dataset's
  schema evolves (e.g., a column is renamed in SAP)?
- Is there a schema registry? Version numbering? Migration tooling?
- What happens to downstream applications (Workshop apps, Actions) when an
  Object Type's properties change?
- Look for: Palantir developer documentation, Foundry SDK changelogs, community
  forums (palantir.com/docs, community.palantir.com), GitHub issues on
  palantir/osdk-ts, palantir/foundry-platform-typescript, conference talks
  (especially Palantir DevCon, FoundryCon)

2. CONFLICT RESOLUTION & DATA RECONCILIATION
- When a source system (e.g., SAP) says a field has value X but a human analyst
  edited it to Y through a Workshop Action, which wins?
- Is there a "last-write-wins" or "source-of-truth priority" model?
- How does the "writeback dataset" pattern work mechanically — does the Action
  write to a separate dataset that gets merged with source data on next sync?
- Look for: Palantir documentation on "writeback datasets", "edits layer",
  "object edits", Action side effects, data reconciliation patterns

3. REAL-TIME INDEXING & QUERY PERFORMANCE
- Object Storage V2 (OSV2) replaced the legacy Phonograph. What is the actual
  storage/indexing technology? (Elasticsearch? Custom inverted index? Column store?)
- How does Palantir achieve sub-second search across millions of objects with
  complex property filters and relationship traversals?
- What are the known performance limits? (Max objects per type, max properties,
  max link depth for traversal queries)
- Look for: Palantir engineering blog posts, patents (search USPTO for Palantir
  Technologies LLC patents on "object storage", "ontology indexing", "semantic
  search"), job postings mentioning specific technologies

4. ACTION TRANSACTION MODEL
- When an Action modifies multiple objects across types (e.g., "approve purchase
  order" updates the PO, creates a receipt, and triggers a payment), is this
  atomic?
- What isolation level? Optimistic concurrency? Saga pattern?
- How are Action side effects (webhooks, notifications, downstream pipeline
  triggers) guaranteed?
- Look for: Palantir OSDK documentation on Action execution, TypeScript/Python
  SDK source code on GitHub, Foundry API documentation

5. SECURITY MODEL INTERNALS
- "Markings" and PBAC (Purpose-Based Access Control): how granular is it really?
  Per-object? Per-property? Per-cell?
- How do markings propagate through Links? (If I can see Object A but not
  Object B, and there's a Link between them, what do I see?)
- How does AIP enforce Ontology permissions when an LLM agent executes Actions?
  Is there a separate permission layer for AI vs human users?
- Look for: Palantir FedRAMP documentation, security whitepapers, SOC 2 reports,
  government RFP responses (especially UK G-Cloud framework documentation which
  is publicly available)

For each question, provide:
- The most authoritative source found (with URL)
- The specific technical answer if documented
- If not documented, the best inference from available evidence
- What this means for building an equivalent on PostgreSQL

Focus on PRIMARY sources (Palantir's own docs, code, patents, employee talks)
over analyst speculation. Palantir's developer documentation at
https://www.palantir.com/docs/foundry/ and their GitHub repos (especially
osdk-ts, foundry-platform-typescript, conjure) are the best starting points.
```

---

## Prompt #2 — The FDE-to-Platform Transition: Palantir's Margin Metamorphosis

**Goal:** Build a quantitative model of unit economics evolution from FDE-heavy to self-service.

**What we already know:** Bootcamp counts, gross margin trajectory (68%→84%), NDR (107%→139%), FDE comp ranges, some ACV expansion examples.

**What we need:** Time-series data on FDE ratios, bootcamp conversion funnel, margin decomposition, AIFD quantified impact.

```
You are researching the economics of Palantir's transition from services-heavy
to platform-driven revenue, for a startup that wants to START where Palantir is
trying to END (self-service, AI-automated deployment).

We already know:
- 560+ bootcamps across 465+ orgs by end 2023, 1,300+ by June 2024
- ~22% estimated bootcamp conversion rate (analyst estimate, not official)
- Gross margin went from 67.7% (2020) to 84% (2025)
- NDR went from 107% to 139%
- FDE comp: $171K-$415K; target ratio 1 FDE : $2-5M ARR
- Healthcare example: 2 bootcamps → $96M deal
- Utility: $7M → $31M ACV in 1 year
- Revenue per employee: ~$1.01M (FY2025)
- AI FDE (AIFD) initiative: "years of SAP work in two weeks"
- 4,414 total employees, ~1,383 engineering

Research these SPECIFIC gaps:

1. THE FDE HEADCOUNT CURVE
- How has the ratio of FDEs to total employees changed from 2016 to 2025?
- In 2016, FDEs ("Deltas") outnumbered software engineers. When did this flip?
- What is the current estimated FDE count? (Palantir stopped breaking this out)
- How many FDEs does a typical $10M ACV account require in year 1 vs year 3
  vs year 5?
- Look for: Palantir 10-K filings (employee category breakdowns), Glassdoor
  data, LinkedIn workforce analytics, Pragmatic Engineer newsletter, former
  employee blog posts

2. BOOTCAMP CONVERSION FUNNEL — REAL NUMBERS
- What percentage of bootcamp attendees convert to paying customers within
  90 days? 6 months? 12 months?
- What is the typical initial ACV from a bootcamp conversion?
- What is the "dark funnel" — companies that do bootcamps but don't convert?
  Why do they fail?
- Has Palantir disclosed the cost per bootcamp (FDE time, infrastructure,
  travel)?
- Look for: Palantir earnings call transcripts (especially Q&A sections where
  analysts ask about conversion), investor day presentations, GTM Foundry
  analysis, equity research notes from Morgan Stanley / Citi / Deutsche Bank

3. THE MARGIN TRANSFORMATION MECHANICS
- Gross margin went from 68% to 84% in 5 years. How much of this is:
  (a) Revenue mix shift (more software subscription, less services)?
  (b) FDE cost reclassification (moving FDE costs from COGS to R&D/S&M)?
  (c) Actual automation reducing human labor per dollar of revenue?
  (d) Price increases on existing contracts?
- What is the services vs. software revenue split? (Palantir doesn't break
  this out explicitly — but some analysts have estimated it)
- Look for: Palantir 10-K cost breakdowns, analyst models from RBC/Morgan
  Stanley/Deutsche Bank, Michael Burry's Substack analysis of Palantir's
  accounting (he specifically questioned margin accounting), BuzzFeed 2016
  leak data

4. AI FDE (AIFD) INITIATIVE — QUANTIFIED IMPACT
- Palantir claims AI FDEs can do "years of SAP work in two weeks." What are
  the actual before/after metrics?
- How many AI FDEs exist vs traditional FDEs?
- What tasks has AIFD actually automated? (Schema mapping? Pipeline creation?
  Workshop app generation? Client communication?)
- Is there evidence of FDE headcount reduction correlated with AIFD rollout?
- Look for: Palantir AIPCon presentations (especially 2024-2025 demos),
  YouTube recordings of Palantir events, Palantir blog posts on AIFD,
  job posting trends on LinkedIn/Glassdoor

5. CUSTOMER SELF-SERVICE METRICS
- What percentage of Palantir's revenue comes from customers who operate
  the platform without regular FDE support?
- The "1 billion API requests per week" stat — how much of this is from
  customer-built applications vs Palantir-deployed apps?
- What is the typical timeline from initial deployment to customer
  self-sufficiency?
- Look for: Palantir investor presentations, customer case studies
  (especially Airbus Skywise with 50K+ users, US Army Vantage, NHS),
  earnings call commentary on "platform maturity" or "customer independence"

For each finding, assess RELIABILITY:
- [CONFIRMED] = directly from Palantir filings or official documentation
- [ESTIMATED] = analyst calculation or reasonable inference from public data
- [SPECULATIVE] = educated guess based on indirect evidence

The goal: build a quantitative model of "what happens to unit economics as
a Palantir-like company transitions from FDE-heavy to self-service." This
model will inform Spider's financial projections.
```

---

## Status des gaps

| Gap | Couvert par | Reste à faire |
|-----|------------|---------------|
| Ontology internals (versioning, transactions, security) | Docs 01-claude/gpt | **Prompt #1** |
| FDE→Self-Service economics curve | Docs 00a/00b + agents | **Prompt #2** |
| French SMB market (WTP, digitalization, CAC) | Agent a631c57 + France Num 2025 | ✅ Suffisant |
| Counter-thesis data (AI failures, bear cases) | Agent a798430 | ✅ Sauvegardé dans 06-*.md |
| Odoo/ERP France market | Agent a68e8f5 (partial) | ✅ Suffisant pour décisions |
| Competitive landscape | Docs 03-claude/gpt | ✅ Complet |
| Spider blueprint & GTM | Docs 05-claude/gpt | ✅ Complet |
