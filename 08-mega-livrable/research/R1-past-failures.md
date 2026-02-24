# R1 - Past Failures in "AI for SMB Operations"

> **Research question:** Who tried before Spider and failed?
> **Date:** 2026-02-19
> **Sources:** Web research across TechCrunch, Seeking Alpha, Forbes, Sifted, Failory, Glassdoor, Sacra, and industry analyses.

---

## Table of Contents

1. ["Palantir for SMBs" Attempts — Data/BI Platforms Going Downmarket](#1-palantir-for-smbs-attempts)
2. [Knowledge Management Wave (2000s-2010s) — The Tacit Knowledge Problem](#2-knowledge-management-wave)
3. [IBM Watson for Small Business (2016-2019)](#3-ibm-watson-for-small-business)
4. [French AI-for-PME Startups (2022-2025)](#4-french-ai-for-pme-startups)
5. [BPO-for-SMB Historical Failures](#5-bpo-for-smb-historical-failures)
6. ["Service-as-Software" Predecessors](#6-service-as-software-predecessors)
7. [Cross-Cutting Lessons for Spider](#7-cross-cutting-lessons-for-spider)

---

## 1. "Palantir for SMBs" Attempts

### The Core Thesis

Multiple companies tried to bring enterprise-grade data analytics and BI platforms to small and medium businesses. All hit the same wall: **enterprise tools are too complex, too expensive, and require too much data maturity for SMBs.**

### Domo

**What they tried:** Domo, founded by Josh James (also founder of Omniture), raised massive funding and IPO'd with the vision of being a "business management platform" that could serve companies of all sizes, including SMBs. Domo marketed itself as a cloud-based BI tool accessible to non-technical users.

**What happened:**
- IPO in 2018 was a disaster: valuation dropped 77% from its private peak of $2.3B to ~$512M at IPO midpoint pricing.
- The company had a net loss of $176.6M in 2017 and was running out of cash, forcing a desperate IPO just to keep the lights on.
- Revenue stagnated: $317M in 2024, actually declining -0.61% year-over-year.
- Stock fell below its IPO price, valuation slipped under $500M.

**Root cause of failure for SMBs:**
- Pricing of $20,000-$100,000/year is prohibitive for small businesses.
- Platform is complex and designed for enterprises with dedicated IT and BI teams.
- Crushed between free/cheap tools (Google Data Studio, Power BI) and entrenched players (Tableau/Salesforce).
- SMBs don't have the data infrastructure, data literacy, or dedicated analyst teams to extract value from such platforms.

**Spider lesson:** SMBs don't need a "platform." They need someone to do the analysis FOR them and tell them what to do. The tool-first approach fails because it still requires the SMB to have human capital to operate it.

### Looker (pre-Google acquisition)

**What they tried:** Looker built a powerful BI platform with its proprietary LookML modeling language. Acquired by Google for $2.6B in 2019.

**What happened:**
- Starting price was ~$35K/year, later rising to ~$60K/year post-Google acquisition.
- Required strong understanding of LookML, presenting a steep learning curve.
- Microsoft and Amazon both looked at acquiring Looker before Google did.

**Root cause of failure for SMBs:**
- Pricing entirely out of reach ($35K-$60K/year minimum).
- Required technical expertise (LookML) that SMBs simply don't have.
- Never seriously attempted to go downmarket -- it was always an enterprise/mid-market play.

**Spider lesson:** Proprietary technical languages and "empowering" tools are the wrong abstraction for SMBs. The SMB owner wants answers, not the ability to write queries.

### Sisense

**What they tried:** Israeli BI unicorn that raised $300M+ and reached $150M ARR. Focused on embedded analytics and attempted to serve mid-market and smaller companies.

**What happened:**
- Laid off 50% of workforce in 2022.
- Another 15% (100 employees) laid off in July 2023.
- Another 13% (60 employees) laid off in January 2024.
- IPO plans shelved indefinitely. No new funding since 2019.
- Revenue growth stalled despite $150M ARR.

**Root cause of failure for SMBs:**
- Expensive and complex to deploy, requiring significant IT support.
- Advanced features required technical backgrounds.
- Shifted strategy to "embedded analytics" (selling to other software companies) rather than directly to SMBs -- essentially gave up on the direct SMB market.

**Spider lesson:** Even a well-funded unicorn couldn't crack the SMB analytics market. Sisense's pivot to embedded analytics is telling -- they concluded it was better to sell analytics *through* software SMBs already use than to sell directly to SMBs.

### ThoughtSpot

**What they tried:** "Search-driven analytics" -- the idea that business users could type questions in natural language to get data insights, like "Google for your data."

**What happened:**
- Massive layoffs: 12% of company at one point, with some teams losing 75% of members over 2 years.
- Culture deteriorated with "panic, anxiety, stress, and toxicity."
- Multiple leadership changes.

**Root cause of failure for SMBs:**
- Natural language search sounds great in demos but requires "superb data analysis beforehand" to work.
- Advanced features require high skill levels.
- Self-service interface is "more complex and less intuitive than competitors."
- The premise ("ask your data questions") assumes the SMB owner knows which questions to ask -- they often don't.

**Spider lesson:** "Ask your data a question" is the wrong UX paradigm for SMBs. SMBs need a system that PROACTIVELY tells them what's wrong and what to do about it. They don't know what they don't know.

### Palantir's Own SMB Attempt

**What they tried:** Launched "Palantir for Builders" / "Palantir for SMBs" to bring its Foundry platform to smaller companies, targeting "hyper-growth startups and innovative builders."

**What happened:**
- Still very early. Typical Palantir customers average $500M in annual revenue.
- No evidence of meaningful SMB traction yet.
- The initiative reads more like a lead-gen funnel for future enterprise deals.

**Spider lesson:** Even Palantir, with its unmatched data platform, recognizes the SMB opportunity but hasn't cracked it. The approach of "same platform, lower price" is insufficient -- the entire product paradigm must change.

---

## 2. Knowledge Management Wave (2000s-2010s)

### The Core Thesis

Multiple waves of companies tried to capture and organize institutional/tacit knowledge inside organizations. All succeeded at storing EXPLICIT knowledge (documents, wikis, SOPs) but fundamentally failed at capturing TACIT knowledge (the know-how in people's heads).

### Jive Software

**What they tried:** Enterprise 2.0 social collaboration platform combining communities, microblogging, forums, blogs, wikis, and IM under one UI. Designed to surface tacit knowledge through social interactions.

**What happened:**
- Peak market cap: $1.7B in April 2012.
- Declined to ~$400M by 2015. Stock went from $27.16 to ~$5.
- Acquired by ESW Capital (via Aurea) for $462M in 2017 -- a "fire sale" at half its peak value.
- CEO Elisa Steele acknowledged investors "didn't have patience" for the company to achieve growth AND profitability simultaneously.

**Root cause of failure:**
- Market flooded with competitors: Slack, Workplace by Facebook, Microsoft Teams/Yammer, IBM Connections, Salesforce Chatter, Box, Dropbox.
- Social features were "nice to have" but not mission-critical -- easy to cut from budgets.
- Tacit knowledge requires shared activities and context to transfer; a forum post doesn't capture the judgment, intuition, and experiential knowledge that makes experts valuable.
- Employees resist sharing knowledge for fear of losing their unique value.

**Spider lesson:** You cannot extract tacit knowledge by asking people to write it down. It must be captured passively through observation of their actual work processes, decisions, and communication patterns. Spider's approach of embedding itself in operations and learning from actual workflows is structurally superior to "please document what you know."

### Confluence (Atlassian)

**What they tried:** Wiki-based knowledge management, initially for engineering teams, expanded to all departments.

**What happened:**
- Confluence is financially successful as a product, but it fails at its stated mission of "capturing institutional knowledge."
- Lacks content review workflows, version control for knowledge accuracy, and lifecycle management.
- Search is basic and insufficient for large knowledge bases.
- Scales poorly: becomes a graveyard of outdated pages that nobody trusts.

**Root cause of failure at tacit knowledge:**
- Manual documentation requires someone to predict what will be valuable later -- an impossible task.
- Real knowledge lives in conversations, decisions, and iterations that happen too fast for documentation.
- 80% of employees' knowledge is tacit and cannot be captured by writing wiki pages.
- Knowledge becomes stale the moment it's written, because context changes continuously.

**Spider lesson:** Wikis are tombstones of knowledge, not living systems. Spider must be a system that OBSERVES and LEARNS from ongoing operations rather than asking people to stop working and document.

### Guru / Tettra / Notion for Teams

**What they tried:** Modern takes on knowledge management -- Guru (verified knowledge cards delivered in context), Tettra (lightweight wiki for small teams integrated with Slack), Notion (flexible workspace for documentation).

**What happened:**
- Guru and Tettra serve niches but remain small.
- Notion is popular but acknowledged as insufficient for knowledge management at scale: "Notion is NOT the king of Knowledge Management Tools."
- Notion lacks built-in content review, verification workflows, and advanced search.
- All still rely on MANUAL input of EXPLICIT knowledge.

**Root cause of failure at tacit knowledge:**
- Same fundamental problem: requiring humans to voluntarily externalize what they know.
- Experts can't articulate every detail and context of what they know, even when willing.
- Solutions fail to capture the crucial context and discussions surrounding information.
- Questions and collaboration remain siloed in chats, emails, and informal interactions.

**Spider lesson:** The knowledge management problem is not a tooling problem -- it's an incentive and capture-method problem. The only way to capture tacit knowledge at scale is through AI that observes work in real-time, not through tools that ask humans to document.

### Meta-Analysis: Why Tacit Knowledge Capture Always Fails

| Approach | Explicit Knowledge | Tacit Knowledge | Why Tacit Fails |
|---|---|---|---|
| Wikis (Confluence) | Good | Terrible | Requires prediction of future value |
| Social (Jive) | Moderate | Poor | Employees resist sharing; posts lack context |
| Cards (Guru) | Good | Poor | Still manual; verification adds friction |
| Docs (Notion) | Good | Poor | Scales badly; knowledge goes stale |
| **AI observation (Spider)** | **Good** | **Potentially Good** | **Passive capture; no extra work required** |

---

## 3. IBM Watson for Small Business (2016-2019)

### What They Tried

IBM attempted to bring AI to businesses of all sizes through the Watson brand, including:
- **Watson for Oncology** (healthcare, the biggest failure)
- **Watson Marketing** (marketing automation suite)
- **Watson Commerce** (e-commerce tools)
- **Watson Analytics** (self-service analytics)

The broader vision was "AI for everyone" -- democratizing IBM's AI capabilities.

### What Happened

**Watson for Oncology (the headline failure):**
- Trained on synthetic/hypothetical patient cases from a small group of oncologists at Memorial Sloan Kettering, not on real-world data.
- Internal QA memos flagged "multiple examples of unsafe and incorrect treatment recommendations" while the sales team was closing deals.
- MD Anderson ended its $62M project in 2017 citing delays, cost overruns, and procurement problems.
- The entire Watson Health division cost $4B to develop and was sold for just $1B in 2022.

**Watson Marketing & Commerce:**
- IBM sold Watson Marketing to Centerbridge Partners in 2019 (rebranded as Acoustic).
- IBM sold Watson Commerce to HCL Technologies for $1.8B in 2019.
- IBM couldn't compete with Google, Facebook, Amazon, Salesforce in marketing/commerce.

**Watson Analytics (the "AI for everyone" play):**
- Self-service analytics tool launched in 2014, eventually merged into IBM Cognos.
- Never gained significant SMB traction.
- Too complex, too tied to IBM's enterprise ecosystem.

### Root Cause of Failure

1. **Overpromising, underdelivering:** Watson was marketed as general-purpose AI that could solve any problem. In reality, it was a collection of APIs that required massive customization, domain expertise, and data preparation.

2. **Enterprise DNA couldn't go downmarket:** IBM's entire sales motion, pricing, implementation process, and support model was built for enterprises spending millions. They couldn't adapt to an SMB customer paying hundreds or low thousands per month.

3. **No product-market fit for SMBs:** Watson tools required data scientists, developers, and IT infrastructure that SMBs don't have. The "self-service" label was aspirational, not real.

4. **Technology didn't work as promised:** Pre-LLM AI was brittle, narrow, and required extensive training on domain-specific data. It wasn't generalizable enough to serve diverse SMB needs.

**Spider lesson:** Three critical takeaways:
- Don't brand as "AI" -- brand as "results." SMBs don't care about the technology; they care about outcomes.
- Enterprise go-to-market cannot be adapted for SMBs -- it must be rebuilt from scratch with radically different unit economics.
- Pre-LLM AI was structurally incapable of serving SMBs because it required too much customization per client. LLMs change this equation fundamentally, enabling one model to handle diverse business contexts.

---

## 4. French AI-for-PME Startups (2022-2025)

### Market Context

- French startups raised EUR 7.1B in 2024, with AI representing 27% of total funding.
- Only 10% of French companies used AI at all in 2024 -- 4 points up from 2023, well behind Northern Europe (20-28%).
- 2024 was a year of major French startup bankruptcies, though primarily in non-AI sectors.

### Notable French Startup Failures (2023-2024)

While no specific "AI-for-PME" startup was found to have failed spectacularly, the broader French startup graveyard provides relevant lessons:

**Luko (insurtech, targeting PME/individuals):**
- Reached EUR 50M in annual premiums but needed to double to reach profitability.
- Failed to raise Series C in late 2023.
- Entered redressement judiciaire in January 2024.
- Acquired by Allianz for EUR 4.3M (after raising ~EUR 70M+).
- **Root cause:** Couldn't reach critical mass fast enough; unit economics never worked at the scale achieved.

**Cubyn (logistics for e-commerce SMBs):**
- Raised EUR 15M Series D in 2023 at EUR 175M valuation.
- Filed for insolvency July 2024, went out of business September 2024.
- **Root cause:** Logistics for SMBs has brutally thin margins; couldn't scale fast enough before running out of capital.

**Masteos (proptech for SMB investors):**
- Raised ~EUR 70M total, including EUR 40M Series A in 2022.
- Filed for insolvency January 2024; acquired for EUR 1M by Novaxia.
- **Root cause:** Relied on a bull real estate market; when rates rose and deals slowed, the high-touch service model collapsed.

### What's Alive: Pennylane and Qonto

**Pennylane** (AI accounting for PMEs):
- Unicorn status in 2024. Serves 120,000 French SMEs.
- User base grew 40x in two years.
- Raised EUR 175M in January 2026, nearing profitability.
- Directly competing with Qonto (450,000 clients) for the "financial OS for PMEs" position.
- **Key insight:** Pennylane succeeds because it targets accountants (intermediaries) first, not SMEs directly. This gives it distribution leverage and domain expertise.

### Structural Observation: Absence of "AI Operations for PME" Startups

The most notable finding is the near-total ABSENCE of French startups attempting what Spider is attempting: using AI to run day-to-day operations for SMBs. French AI funding flows almost entirely to:
- Foundation models (Mistral AI: EUR 2.8B)
- Biotech/drug discovery (Aqemia, Owkin)
- Vertical SaaS (Pennylane, Qonto)
- Photo/content tools (PhotoRoom)

No one is building an "AI COO for PMEs" in France. This is either a massive opportunity or a signal that the market doesn't believe it's possible.

**Spider lesson:** The French market is wide open for this positioning. But learn from Cubyn, Luko, and Masteos: unit economics must work at small scale before scaling. Don't raise at EUR 175M valuation before proving the model works on 100 clients. Pennylane's strategy of going through intermediaries (accountants) rather than direct-to-SME is worth studying closely.

---

## 5. BPO-for-SMB Historical Failures

### The Structural Barrier

**Why Accenture/Capgemini/McKinsey never served SMBs at scale:**

The economics are fundamentally broken:

| Factor | Enterprise Client | SMB Client |
|---|---|---|
| Typical engagement size | $500K - $5M+ | $2K - $20K/month |
| Sales cycle cost | $50K-$100K (amortized) | Same $50K-$100K (impossible to amortize) |
| Consultant day rate | $2,000-$5,000 | Same rate, but client can't afford it |
| Customization needed | High, but covered by fees | Equally high, but fees don't cover it |
| Account management | Dedicated partner | Same overhead, 1/100th the revenue |
| % of client revenue | 0.05% for $10B company | 1.7% for $300M company (unsustainable) |

**Root cause:** Consulting firms have a structural cost floor set by their talent costs. A McKinsey engagement costs $500K-$1.25M minimum. Even Accenture, the most "industrialized" of the big firms, cannot compress costs below the point where a dedicated team of consultants is economically viable. The overhead of partner relationships, quality control, methodology, and recruiting simply cannot be divided into $5K/month packages.

**The "Big 4" AI failure for mid-market:**
As noted by DAS Advanced Systems: "The economics of Big 4 artificial intelligence consulting services simply don't work for mid-market companies." A $5M investment is 0.05% of revenue for a Fortune 500 company but 1.7% for a $300M company. For a $5M SMB, it would be 100% of revenue.

### BPO for SMBs: The Margin Problem

- BPO providers operating staff leasing models make only ~20% margin on service fees.
- Customer acquisition costs are 5-7x retention costs.
- BPO wage inflation runs 8-12% annually, outpacing price increases.
- Small engagements require the same account management overhead as large ones.
- Result: serving SMBs is structurally unprofitable for traditional BPO.

**Spider lesson:** This is Spider's entire thesis. AI breaks the cost floor that made consulting/BPO impossible for SMBs. Where a human consultant costs $2,000-$5,000/day, an AI agent costs pennies per interaction. The marginal cost of serving one more SMB approaches zero once the system is built. Spider's model works precisely because it replaces the human cost structure with an AI cost structure while delivering comparable (and eventually superior) operational guidance. But Spider must avoid the trap of requiring human-in-the-loop for every client -- that recreates the BPO cost structure.

---

## 6. "Service-as-Software" Predecessors

### Bench Accounting (2012-2024) -- The Cautionary Tale

**What they tried:** "Bookkeeping service powered by software." Humans did the actual bookkeeping, supported by proprietary software. Targeted small businesses. Raised $135M from Shopify, Bain Capital Ventures, and others. Had 35,000+ customers at shutdown.

**What happened:**
- Burned through $135M from 2012 to September 2024.
- Monthly cash burn of $1.5M.
- Forced shutdown December 27, 2024 due to "liquidity crisis."
- Acquired by Employer.com post-mortem.
- Unit economics got WORSE over time, not better (contrary to VC thesis).

**Root cause of failure:**
1. **Dual identity crisis:** Couldn't decide if it was a tech company or a service company. Tried to be both, excelled at neither.
2. **Anti-growth churn:** Most successful customers would hire a finance team and leave. Bench was a stepping stone, not a destination.
3. **Limited service scope:** Cash-basis accounting only, no accrual, no AP/AR tracking. Couldn't grow with clients.
4. **Founder departure:** CEO Ian Crosby was pushed out by the board, replaced by a "professional CEO" who couldn't fix the fundamentals.
5. **Venture debt trap:** A bank called in venture debt, triggering the liquidity crisis.

**Spider lesson:** CRITICAL. Bench is the closest analog to Spider's model and it failed. The key differences Spider must ensure:
- **AI must actually reduce marginal cost per client.** Bench's humans couldn't. If Spider requires humans-in-the-loop for each client, it becomes Bench.
- **Avoid anti-growth churn:** Spider must grow WITH its clients, not be something they graduate from.
- **Don't be a stepping stone:** Provide enough value at every stage that clients never feel they've outgrown the platform.

### ScaleFactor (2014-2020) -- The Fraud

**What they tried:** "AI-automated bookkeeping for SMBs." Promised to automate SMB bookkeeping and payroll with AI. Raised $104M.

**What happened:**
- Shut down June 2020.
- Forbes investigation revealed the "AI" was actually human accountants in the Philippines doing manual bookkeeping.
- Customers reported erroneous financial statements, billing errors, and miscategorized transactions.
- One customer had $17,000 credited incorrectly.
- CEO Kurt Rathmann blamed COVID-19, but the real causes were fraud and dysfunction.

**Root cause of failure:**
1. **Fake AI:** The technology didn't exist. They sold a vision and delivered humans pretending to be AI.
2. **Quality catastrophe:** Manual work done by outsourced labor produced frequent errors.
3. **CEO admission:** "We really thought we could automate the entire back office of a small business" -- but they couldn't, and instead of acknowledging this, they faked it.
4. **Customers wanted humans, not AI:** Rathmann noted "customers were craving a person rather than a computer."

**Spider lesson:** EXISTENTIAL WARNING. Never overpromise AI capabilities. If the AI can't do something, use humans transparently, not secretly. Also: the fact that customers "craved a person" suggests that the right model isn't pure AI -- it's AI that communicates like a trusted advisor, with human escalation paths when needed.

### Pilot (2017-present) -- The Survivor

**What they tried:** "Bookkeeping powered by experts + technology." 50/50 people and software model. Hit 60% gross margins. Backed by Sequoia and Bezos Expeditions.

**What happened:**
- Still operating, ~$43M/year revenue.
- Achieved positive unit economics (unlike Bench).
- But faces structural challenges:
  - Scaling services side brings operational overhead and quality degradation.
  - Low client engagement frequency (don't need Pilot daily).
  - Squeezed between QuickBooks (system of record) and workflow tools (Ramp, Gusto, Stripe).
  - Internal tension between automating more (better margins) and maintaining human service quality.

**Root cause of challenges:**
- **Middleware trap:** Pilot doesn't own the system of record or the daily workflow. It sits in between, vulnerable to being squeezed from both sides.
- **Automation vs. service tension:** Every dollar invested in automation potentially undermines the human service team's jobs and quality.

**Spider lesson:** Don't be middleware. Spider must become the system of record for operational decisions, not a layer on top of other tools. Also: the "automation vs. service" tension is real -- Spider must navigate it by having AI be the PRIMARY delivery mechanism from day one, with humans as exception handlers, not the other way around.

### Olive AI (2012-2023) -- The Overextension

**What they tried:** Healthcare automation. "AI-powered workforce" to automate hospital administrative tasks. Raised $850M, peaked at $4B valuation.

**What happened:**
- Meteoric rise during COVID: $225M round in Dec 2020, $400M round in July 2021.
- 450 workers laid off July 2022 due to "fast-paced growth and lack of focus."
- Shut down October 2023.
- Assets sold to Waystar and Humata Health.

**Root cause of failure:**
1. **Overpromising:** Claimed it would lower administrative spending by 5x. Never delivered.
2. **Lack of focus:** Tried to automate everything at once instead of dominating one workflow.
3. **Scaling before product-market fit:** Grew headcount and client base before the product actually worked reliably.

**Spider lesson:** Focus. Pick a small number of operational areas and dominate them before expanding. Olive tried to be "the AI workforce for everything" and ended up being "the AI workforce for nothing."

---

## 7. Cross-Cutting Lessons for Spider

### Pattern 1: The "Tool vs. Service" Trap

Every failure falls on a spectrum between "pure tool" (Domo, Looker, Sisense) and "pure service" (Bench, traditional BPO). Both extremes fail for SMBs:
- **Pure tools** fail because SMBs lack the human capital to operate them.
- **Pure services** fail because the unit economics of humans serving low-revenue clients don't work.

**Spider's positioning must be:** Service-level outcomes delivered at tool-level economics. AI is the only way to achieve this.

### Pattern 2: The Tacit Knowledge Gap

Every knowledge management tool captured explicit knowledge (documents, procedures) but failed at tacit knowledge (judgment, intuition, contextual expertise). This matters because tacit knowledge is 80% of what makes businesses work.

**Spider's advantage:** If Spider can passively capture and codify tacit knowledge through observation of operations, it solves a problem that a decade of startups (Jive, Guru, Tettra, Notion) could not.

### Pattern 3: Enterprise-to-SMB Migration Never Works

IBM Watson, Domo, Looker, Sisense, Accenture -- every attempt to bring an enterprise product/service downmarket to SMBs has failed. The pricing, complexity, sales motion, and support model are structurally incompatible.

**Spider must be:** Built for SMBs from day one, not an enterprise product with a cheaper tier.

### Pattern 4: Unit Economics Must Work at Small Scale

Bench ($135M burned), ScaleFactor ($104M raised), Olive ($850M raised) -- all burned massive capital assuming unit economics would improve with scale. They didn't.

**Spider must prove:** Positive unit economics with its FIRST 50-100 clients, before scaling.

### Pattern 5: Don't Be a Stepping Stone

Bench's most successful clients left because they outgrew the platform. Any SMB service must grow with the client or face structural churn.

**Spider must ensure:** The platform becomes MORE valuable as the client grows, not less.

### Pattern 6: AI Must Be Real

ScaleFactor faked its AI and collapsed. IBM Watson overpromised and underdelivered. In the LLM era, the technology is finally capable of delivering on the promise -- but only if expectations are managed honestly.

**Spider must:** Underpromise and overdeliver. Start with narrow, reliable capabilities and expand. Never claim the AI can do something it can't.

### Pattern 7: Go Through Intermediaries (Pennylane Model)

Pennylane succeeded where others failed by targeting accountants first, then reaching SMEs through them. This solves the distribution problem (accountants have existing SME relationships) and the credibility problem (accountants validate the tool).

**Spider should consider:** Are there equivalent intermediaries (consultants, accountants, industry associations) who could serve as distribution channels?

---

## Summary Table

| Company | Years | $ Raised/Value | What They Tried | Why They Failed | Spider Lesson |
|---|---|---|---|---|---|
| **Domo** | 2010-now | $2.3B peak -> $500M | BI platform for all sizes | Too expensive, too complex for SMBs | SMBs need answers, not dashboards |
| **Looker** | 2012-2019 | Acq. $2.6B by Google | BI with LookML | $35K+ minimum, requires developers | Don't require technical skill |
| **Sisense** | 2004-now | $150M ARR, 50% layoffs | Embedded analytics | Gave up on direct SMB; pivoted to embedded | Going direct to SMBs is brutally hard |
| **ThoughtSpot** | 2012-now | Layoffs, decline | "Search your data" | Requires data prep + domain expertise | Proactive insights > reactive queries |
| **Jive Software** | 2001-2017 | $1.7B peak -> $462M sale | Enterprise social/KM | Commoditized; couldn't capture tacit knowledge | Passive knowledge capture, not wiki |
| **Confluence** | 2004-now | Part of Atlassian | Wiki knowledge base | Only captures explicit knowledge; goes stale | Living system, not documentation |
| **IBM Watson** | 2011-2022 | $4B invested | AI for everyone | Overpromised; enterprise DNA can't go SMB | Brand as results, not AI |
| **Bench** | 2012-2024 | $135M burned | Bookkeeping service + software | Unit economics worsened; anti-growth churn | AI must reduce marginal cost; grow with client |
| **ScaleFactor** | 2014-2020 | $104M raised | "AI bookkeeping" (fake) | AI was fake; humans doing work secretly | AI must be real; honest about capabilities |
| **Pilot** | 2017-now | ~$43M/yr revenue | Bookkeeping experts + tech | Middleware trap; automation vs. service tension | Own the system of record, not middleware |
| **Olive AI** | 2012-2023 | $850M raised, $4B peak | Healthcare automation | Overpromised; unfocused; scaled too fast | Focus on few workflows before expanding |
| **Luko** | 2018-2024 | ~EUR 70M raised | Insurtech for individuals/PME | Couldn't reach critical mass in time | Unit economics before growth |
| **Cubyn** | 2014-2024 | EUR 15M Series D | Logistics for e-commerce SMBs | Thin margins; couldn't scale fast enough | Avoid thin-margin operational services |
| **Accenture/McKinsey** | Ongoing | N/A | Consulting/BPO for SMBs | $500K+ minimum engagement; structural cost floor | AI breaks the cost floor -- this is Spider's thesis |

---

## The One-Sentence Synthesis

> **Every predecessor failed because they either gave SMBs tools they couldn't use (Domo, Watson, ThoughtSpot) or services they couldn't afford (Accenture, Bench, BPO) -- Spider succeeds only if AI allows it to deliver service-level outcomes at tool-level economics, while passively capturing the tacit knowledge that wiki-based approaches never could.**
