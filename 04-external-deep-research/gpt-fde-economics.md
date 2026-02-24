# Economics of Palantir’s shift from services-heavy to platform-driven revenue

## What this research can and cannot prove

This report focuses on five specific gaps you listed: the forward deployed engineer (FDE) headcount curve, bootcamp conversion funnel, margin transformation mechanics, AI FDE (AIFD) quantified impact, and customer self-service metrics. It uses primary sources where possible (SEC filings, Palantir IR releases, and official investor materials) and then triangulates with external sources (workforce analytics, reputable press, and compensation/data vendors) when Palantir stops disclosing. citeturn14view0turn12view1turn24view1turn19search9

A core constraint is structural: since Palantir went public, it has not consistently disclosed a dedicated FDE headcount line item, nor does it break revenue cleanly into “software” vs “services” in a way that supports a clean decomposition. Its prospectus and filings explicitly describe a model that blends software subscriptions, ongoing O&M services, and professional services; they do not provide a direct revenue split across those categories. citeturn14view2turn11view0

**Reliability labels used throughout:**
- **[CONFIRMED]**: Directly supported by Palantir SEC filings, Palantir IR releases, or Palantir investor materials.
- **[ESTIMATED]**: Derived from third-party datasets, analyst-like calculations from public data, or reasonable inference from disclosed numbers.
- **[SPECULATIVE]**: Educated guess based on indirect signals; included only if it clearly helps modelling and is clearly marked.

## FDE headcount curve and the “flip” from Deltas to Devs

### Anchors from filings: total headcount and technical density

**Palantir’s total headcount anchors are strong and auditable:**
- **[CONFIRMED]** As of **December 31, 2019**, Palantir had **2,391 full‑time employees** (S‑1/A). citeturn12view0turn12view1  
- **[CONFIRMED]** As of **December 31, 2024**, Palantir had **3,936 full‑time employees** (FY2024 10‑K). citeturn14view0  
- **[CONFIRMED]** As of **September 30, 2025**, Palantir states an “employee base of **4,414 full‑time employees**” in its Form 10‑Q. citeturn24view1  

**Technical density (not specifically FDE density) is partially disclosed in the S‑1/A:**
- **[CONFIRMED]** As of December 31, 2019, Palantir disclosed **929 “software engineers and other technical staff”** whose main responsibilities are to build/operate/improve Gotham and Foundry; the filing also states that software engineers rotate between field and development functions. citeturn12view1  
This matters because rotation blurs the boundary between “core Dev” and “forward deployed” at the reporting level, making any exact “FDE count” inherently fuzzy even internally. citeturn12view1  

### The 2016 statement and when it likely flipped

You asked: “In 2016, FDEs outnumbered software engineers. When did this flip?”

- **[ESTIMATED]** Multiple third parties repeat that **until 2016** Palantir had **more FDEs (“Deltas”) than software engineers**, framing ~2016 as the pivot point. This appears in Pave’s 2025 write-up (which presents itself as data-driven but does not publish Palantir internal headcount by year). citeturn26view0  
- **[ESTIMATED]** Salesforce’s explainer blog also states Palantir had more “Deltas” than software engineers “until 2016.” citeturn5search6  

**Interpretation for modelling (explicitly marked):**
- **[ESTIMATED]** The cleanest reading of “until 2016” is that the “flip” occurred **around 2016**, potentially spanning **2016–2017** if the underlying data is noisy (hiring waves, title taxonomy). This is not directly confirmed by Palantir filings; treat it as a breakpoint assumption with sensitivity analysis around it. citeturn26view0turn5search6  

### Current estimated FDE count: what can be triangulated

Palantir does **not** publish an FDE count today. Any “current FDE count” must be inferred.

**What we can do reliably:**
- **[CONFIRMED]** Total full-time employees as of Sep 30, 2025: **4,414**. citeturn24view1  
- **[ESTIMATED]** A third-party workforce analytics page (Unify) claims engineering is **1,383 employees** and roughly **44%** of their observed headcount. citeturn27view0  
  - Caution: the same Unify page also reports a “total employees” figure (~3,131) that conflicts with Palantir’s SEC-reported 4,414, indicating dataset coverage/definition gaps (likely LinkedIn-only sampling, geography filters, or stale snapshots). citeturn27view0turn24view1  

**Practical estimate ranges for “FDE-like” staff (Delta + adjacent forward-deployed roles):**
- **[ESTIMATED]** Because Palantir’s own prospectus describes software engineers rotating between field and development, you can model “forward deployed” as an *allocation of engineering time* rather than a strict headcount. citeturn12view1  
- **[SPECULATIVE]** If you still need a headcount proxy, a reasonable modelling approach is to define **FDE-like workforce = (engineering headcount × field allocation%) + (non-engineering deployment roles)**. With engineering at 1,383 as a starting proxy (imperfect), and field allocation between **25% and 60%** (wide by design), that yields roughly **350–830 FDE-equivalents** from engineering time alone. citeturn27view0turn12view1  
- **[SPECULATIVE]** If you assume additional forward-deployed capacity exists outside “engineering” (deployment strategists, field infrastructure, etc.), you can add **10–30% uplift** to capture those roles, yielding a broad band of roughly **400–1,100 FDE-equivalents**. This is not confirmed; it is a modelling convenience band.

### How many FDEs does a $10M ACV account “need” in year 1 vs year 3 vs year 5

Palantir does not disclose this per-account staffing. The best you can do is model phased intensity and use external descriptions of how FDE teams work.

- **[ESTIMATED]** a16z describes Palantir forward-deployed engineers embedded inside customer organisations “often for months,” stitching systems together and shipping workflows on top of Foundry/Gotham. citeturn8search1  
- **[ESTIMATED]** The Financial Times reports Palantir often sends teams of two (one to understand needs, one to execute), in the context of describing the FDE role. citeturn10news51  

A usable staffing curve for a **$10M ACV** account (explicitly a *model*, not a fact):
- **[SPECULATIVE] Year 1 (land + initial production):** **2–6 FDEs** is a defensible band. The lower bound aligns with “teams of two”; the upper bound reflects parallel workstreams (data integration, ontology, app workflows, security/edge) typical of mission-critical deployments. citeturn10news51turn8search1  
- **[SPECULATIVE] Year 3 (expansion + platform maturity):** **1–3 FDEs**, with greater customer-side build capacity. This assumes internal tooling (Apollo, AIP) reduces deployment labour, and customer developers start shipping on-platform. citeturn15view0turn21view0  
- **[SPECULATIVE] Year 5 (steady state):** **0–1 FDE** dedicated, often fractional (one FDE covers multiple mature accounts). This aligns with Palantir’s repeated messaging that software deployment time and required engineers have decreased over time due to platform/infrastructure investments. citeturn15view0turn21view0  

**Modelling implication:** The account contribution margin expands when you can drive (a) lower “FDE-equivalent cost per deployed use case,” and (b) higher customer-built throughput. That is exactly the “start where Palantir is trying to end” thesis.

## Bootcamp conversion funnel: what is disclosed, what is missing, and how to model it anyway

### What bootcamps are, and what scale is officially disclosed

- **[CONFIRMED]** Palantir positions the AIP Bootcamp as an interactive workshop designed to take customers from “0 to use case in 5 days.” citeturn13search2turn19search1  
- **[CONFIRMED]** Palantir IR stated (June 2024) that **“more than 1300 AIP Bootcamps have been completed”** since launch. citeturn19search9  

**What Palantir does not disclose (and you asked for explicitly):**
- **[CONFIRMED: not disclosed]** Palantir does not publish cohort conversion curves (90 days, 6 months, 12 months) in SEC filings or this IR release. citeturn19search9turn14view2  

### Conversion rates and timing: best available evidence

The closest primary-source-adjacent signal in this research set is *not* a number, but a Q&A prompt that confirms investors are asking about bootcamps as a sales accelerator.

- **[CONFIRMED]** In the Q3 2025 earnings call, an analyst explicitly asks about “accelerated sales cycles” from “companies that have gone to the boot camps,” prompting management to discuss customers moving quickly from initial contact to large deals (without giving a numeric conversion rate). citeturn22view4  

**Practical conclusion:**
- **[CONFIRMED: unknown]** % conversion within 90/180/365 days remains **undisclosed** by Palantir in the sources reviewed here.  
- **[ESTIMATED]** Any numeric “bootcamp conversion rate” you see in market commentary should be treated as an analyst shortcut unless it is tied to a reproducible cohort method and clear denominators (per-bootcamp vs per-organisation vs per-attendee). The existence of shifting denominators is acknowledged (even if imperfectly) by third-party commentary observing “560 bootcamps across 465 organisations” style reporting. citeturn19search10turn19search9  

### Typical initial ACV from a bootcamp conversion

Palantir does not publish “bootcamp → initial ACV” distribution. The best you can do is triangulate from:
- Deal-size disclosures (counts of deals ≥$1M, ≥$5M, ≥$10M per quarter).
- Case anecdotes (often not tied to bootcamp cohorts).
- External summaries (lower reliability).

- **[CONFIRMED]** In Q3 2025 Palantir reported **204 deals ≥$1M**, **91 deals ≥$5M**, and **53 deals ≥$10M** for the quarter (not attributed solely to bootcamps). citeturn21view0  
- **[ESTIMATED]** A third-party earnings summary page (TipRanks) repeats anecdotes like “utility expansion $7M → $31M ACV,” and a “new healthcare deal $96M,” but these are not presented as bootcamp conversions with denominators and should be treated as narrative evidence, not funnel math. citeturn20search1  

**Usable modelling assumption (clearly marked):**
- **[SPECULATIVE]** For a bootcamp-driven motion, set an initial ACV distribution with a heavy tail:
  - “Default” conversions: **£/$0.25–2M** initial ACV.
  - “Enterprise-wide” conversions: **£/$2–10M** initial ACV.
  - Outliers: **£/$10M+** (rare, but drives much of the economics).  
  This aligns with Palantir’s own disclosure that deal counts skew toward ≥$1M and that large deals exist in meaningful volume. citeturn21view0  

### The “dark funnel”: why bootcamps fail to convert

Here you actually have unusually relevant primary language from Palantir’s prospectus, because it describes exactly the dynamic: high-cost sales efforts, pilots, and no guarantee of moving customers forward.

- **[CONFIRMED]** Palantir’s S‑1/A states its sales efforts include significant time/expense educating customers and that it **often provides platforms at no or low cost initially** through **short-term pilot deployments**; it explicitly warns there is “no guarantee” it can move customers from the “Acquire phase” into later phases. citeturn11view0  

That prospectus framing helps categorise dark-funnel failure modes (as model inputs):

- **[ESTIMATED] Low readiness:** Data access and data governance barriers: bootcamp produces prototypes, but the org cannot productionise due to permissioning, security, integration backlog. This aligns with Palantir’s emphasis that platforms are complex and implementations can be lengthy. citeturn11view0turn14view2  
- **[ESTIMATED] Economic mismatch:** Customers reject pricing/ROI, which is consistent with older reporting that some customers balked at high prices and doubted long-term value. citeturn7view0  
- **[ESTIMATED] Relationship/process mismatch:** Cultural friction and “difficult working relationships” were cited in reporting on Palantir’s commercial struggles in the mid-2010s; in a bootcamp model, this can kill momentum even if the prototype works. citeturn7view0  

### Cost per bootcamp: what is disclosed and a defendable estimate

Palantir does not disclose “cost per bootcamp.” You can, however, build a cost model that maps to disclosed expense categories.

- **[CONFIRMED]** FY2024 10‑K states Sales and marketing costs include personnel executing pilots “including bootcamps,” plus third‑party cloud hosting services for pilots and travel costs. citeturn14view2  

A practical cost model:

- **[ESTIMATED] Direct labour cost:** (FDE-equivalents × 5 days) × loaded day rate  
- **[ESTIMATED] Variable infra:** cloud hosting for pilots + sandbox environments  
- **[ESTIMATED] Travel/events:** travel costs (explicitly included in S&M) citeturn14view2  

**Example parameterisation (for Spider’s forecasting model):**
- **[SPECULATIVE]** 3 FDE-equivalents × 5 days × £/$1,200–2,500 fully loaded per day ≈ **£/$18k–37.5k** labour
- **[SPECULATIVE]** Cloud + tooling + travel ≈ **£/$5k–30k** (high variance by sector/security)  
- **[SPECULATIVE]** Total cost per bootcamp ≈ **£/$25k–70k** (commercial) and **£/$50k–150k** (high-security/government-like environments)

This is a *range*, intentionally: bootcamps for regulated environments can carry disproportionate security, travel, and infrastructure overhead. citeturn14view2turn11view0  

## Margin transformation mechanics: what the filings imply about the “real” driver

You asked for decomposition across (a) mix shift, (b) cost reclassification, (c) automation, (d) price increases. Only parts of this can be grounded directly.

### What gross margin actually did: GAAP vs adjusted

- **[CONFIRMED]** FY2020 GAAP gross margin was **68%** (Palantir 2020 10‑K), and Palantir also reports **81%** gross margin when excluding stock‑based compensation. citeturn15view0  
- **[CONFIRMED]** FY2024 GAAP gross margin is shown as roughly **80%** in the FY2024 10‑K results discussion. citeturn14view1  
- **[CONFIRMED]** Palantir’s Q4 2025 investor presentation shows **FY2025 adjusted gross margin of 84%** (excluding stock-based compensation) and **Q4 2025 adjusted gross margin of 86%**. citeturn29view0  

**Key inference for your decomposition:**
- **[ESTIMATED]** A large portion of “GAAP gross margin expansion” from 2020 to 2025 is mechanically explained by the **shrinking impact of stock-based compensation within cost of revenue**, because the gap between GAAP and adjusted gross margin is huge in 2020 (68% vs 81%) but small by 2025 in the materials we have (adjusted 84% suggests only modest further expansion beyond 2020’s 81% ex-SBC baseline). citeturn15view0turn29view0  

This does **not** mean unit economics did not improve: it means that, to model “true operational improvement,” your baseline should likely be **gross margin excluding SBC**, not GAAP.

### What Palantir defines as revenue and “services”: implications for mix shift

- **[CONFIRMED]** FY2024 10‑K describes revenue as coming from (i) subscriptions to access software platforms in hosted environments with ongoing O&M services (“Palantir Cloud”), (ii) software subscriptions in customer environments with ongoing O&M services (“On‑Premises Software”), and (iii) professional services. citeturn14view2  

**What this implies:**
- **[ESTIMATED]** Even “software subscription” includes ongoing O&M services; therefore a naïve “software vs services” split will misattribute a meaningful part of delivery effort as “software.” The real economic question is not “is revenue labelled software,” but “how much human labour is deployed per £/$ of recurring revenue.” citeturn14view2turn12view1  

### Evidence for automation reducing labour per dollar of revenue

Two direct statements support real deployment automation:

- **[CONFIRMED]** Palantir’s 2020 10‑K states that investments in Apollo yielded “a significant decrease in the time and number of engineers required to install and deploy” its software, and that time to begin working with a customer decreased “more than five-fold” from 2019 to 2020; “in some cases” customers can be up in “mere hours.” citeturn15view0  
- **[CONFIRMED]** In Q3 2025 commentary, Palantir discusses internal productivity: AIFDE “understands how to connect to data sources, integrate and transform data, create ontologies and functions, and build applications,” and it claims a case where two human FTEs used “an army of AI FTEs” to migrate off a legacy data warehouse in five days (vs SIs taking up to two years). citeturn21view0  

### Cost reclassification: where FDE-related costs can land in the P&L

You asked specifically whether margins improved by moving FDE costs from COGS to R&D/S&M.

The FY2024 10‑K provides a clear disclosure of what’s in which bucket:

- **[CONFIRMED]** Cost of revenue includes salaries/benefits for personnel performing O&M and professional services, subcontractor expenses, “field‑service representatives,” third‑party cloud hosting, hardware costs, travel costs, allocated overhead, and other direct costs. citeturn14view2  
- **[CONFIRMED]** Sales and marketing includes personnel executing pilots “including bootcamps,” plus cloud hosting services for pilots and travel costs. citeturn14view2  

**Modelling implication:**
- **[ESTIMATED]** Bootcamp labour that looks “services-like” can legitimately live in **Sales and marketing**, not COGS, if it is treated as a sales pilot. That accounting choice increases reported gross margin while leaving operating margin unchanged unless total labour declines. citeturn14view2  
- **[SPECULATIVE]** If Palantir’s definition of “pilot/bootcamp” expanded over time, a higher fraction of forward-deployed labour may have migrated from “delivery” to “sales motion,” mechanically supporting gross margin expansion. You cannot confirm the magnitude without a policy change disclosure, so treat as a scenario lever, not a fact.

### Price increases on existing contracts: evidence level

- **[CONFIRMED]** Palantir’s S‑1/A explicitly states pricing structures may change over time and discusses pricing model evolution and concessions risk, but does not quantify price increases. citeturn11view0  
- **[SPECULATIVE]** There is not enough disclosed information in the consulted filings to quantify “price increases” as a driver of margin expansion separately from mix and labour efficiency.

## AI FDE and AIFD: quantified impact and what it likely automates

### What Palantir has actually quantified in public statements

**Operational claims with concrete before/after:**
- **[CONFIRMED]** Q3 2025 earnings call: AIFDE is described as an “AIP native development agent” that can connect to data sources, integrate/transform data, create ontologies/functions, and build applications. citeturn21view0  
- **[CONFIRMED]** Same call: Palantir claims a customer migration that would take “an army of SIs up to two years” was done in “five days” using two humans plus “an army of AI FTEs,” and it emphasises this is “production,” not a prototype. citeturn21view0  

**Investor presentation reinforcement:**
- **[CONFIRMED]** Q4 2025 investor presentation message: Palantir frames “supercharging data migration with AIP,” including “generate comprehensive migration plans in 60 seconds” and “complete migrations in weeks instead of years, at a fraction of the cost.” citeturn18view1turn18view4  

### What tasks AIFD appears to automate

From the call transcript, the automated scope is unusually explicit:

- **[CONFIRMED]** AIFDE automates or accelerates: data source connection, data integration and transformation, ontology and function creation, and application building. citeturn21view0  

From the investor presentation framing, it also targets “migration plan generation” and lifecycle validation.

- **[CONFIRMED]** The investor deck positions AIP as deploying “specialised AI at every stage” of data migration and mentions multiple artefacts (SQL documents, diagrams, API docs) as inputs/outputs in the migration workflow. citeturn18view1turn18view4  

### Are AI FDEs reducing FDE headcount?

No evidence of absolute reduction is visible in SEC-reported headcount:

- **[CONFIRMED]** Full-time employees increased from 3,936 (Dec 31, 2024) to 4,414 (Sep 30, 2025). citeturn14view0turn24view1  

What you do see is a narrative about *decoupling revenue growth from workforce growth*:

- **[CONFIRMED]** In Q3 2025 call commentary, Palantir leadership claims workforce is not growing proportionally to growth and that sales force is declining while revenue accelerates (qualitative claim, not a headcount series). citeturn21view0turn22view4  

**Conclusion for modelling:**
- **[ESTIMATED]** Treat AIFD as a **labour productivity multiplier** rather than a headcount elimination lever in the near term: it allows more deployments per engineer (or faster deployments), supporting higher revenue per employee while headcount still grows. citeturn21view0turn24view1  

### How many AI FDEs exist vs traditional FDEs?

- **[CONFIRMED: not disclosed]** Palantir does not disclose the number of AI FDEs or the proportion of deployments using AI FDE vs traditional approaches in the sources reviewed.

## Customer self-service: what can be inferred and what remains opaque

### Revenue from “self-sufficient customers”: not disclosed

- **[CONFIRMED: not disclosed]** Palantir does not publish the share of revenue coming from customers operating without regular FDE support in SEC filings or the investor materials surfaced here. citeturn14view2turn24view1  

### The best proxy signals: install time compression and on-platform building tools

Two categories of proxy evidence matter for your unit-economics model:

- **[CONFIRMED]** Deployment friction reduction: Palantir’s 2020 10‑K claims deploy/install time and required engineers dropped materially due to Apollo, with a five‑fold time reduction from 2019 to 2020. citeturn15view0  
- **[CONFIRMED]** Customer build enablement: AIFDE is explicitly positioned as helping “customer developers alike,” not just Palantir staff, which is directionally consistent with a move toward customer self-sufficiency. citeturn21view0  

### “1+ billion API gateway requests per week”: current reliability status

- **[ESTIMATED]** A third-party earnings page (TipRanks) includes “1+ billion API gateway requests/week” as part of an earnings summary, but this report did not locate the precise original Palantir quote in filings or the investor PDFs examined. Treat it as *unverified* until you can tie it to an official transcript, shareholder letter, or slide. citeturn20search1  

### Timeline to self-sufficiency: a defendable model structure

You can build a usable “time to self-sufficiency” model without a disclosed metric by anchoring on disclosed programme lengths and deployment acceleration statements:

- **[CONFIRMED]** AIP Bootcamp is framed as **five days** to initial use case. citeturn13search2turn19search1  
- **[CONFIRMED]** Palantir claims some customers can be “up and running” in hours (install/start work), though that is not the same as organisation-wide adoption. citeturn15view0  
- **[CONFIRMED]** Palantir describes customers moving extremely quickly from initial contracts to multi-year expansions (example given: expansion five months after initial contract; two weeks into initial contract conversation shifts to enterprise-wide deployment). citeturn21view0  

A practical maturity curve for Spider (clearly marked as modelling):
- **[SPECULATIVE] Phase A (0–1 month):** Bootcamp + first prototype: heavy Palantir-led.
- **[SPECULATIVE] Phase B (1–6 months):** Productionisation of 1–3 workflows: mixed Palantir/customer.
- **[SPECULATIVE] Phase C (6–18 months):** Customer dev team ships most incremental apps; Palantir focuses on platform extensions and governance.
- **[SPECULATIVE] Phase D (18+ months):** Palantir support becomes episodic; account becomes “platform renew + expansion” driven by customer usage.

This aligns with Palantir’s disclosures that pilots do not always mature, and that field learning loops into product, suggesting a progression from heavy-touch to platform-led. citeturn11view0turn12view4  

## A quantitative model blueprint for Spider: unit economics as “FDE-heavy → self-service”

This section translates the research above into a concrete modelling framework you can plug into Spider’s financial projections. The goal is not to “copy Palantir,” but to quantify what improves when you start closer to the end-state: self-serve onboarding, AI-automated deployment, and customer-built expansion.

### Core model objects

Define each customer/account as a cash-flow object with three state variables:

**Adoption state**
- `t_bootcamp`: time to first working use case (days).  
  - **[CONFIRMED]** Palantir markets 5 days for bootcamp. citeturn13search2turn19search1  
- `t_to_prod`: time to production. (Spider assumption; Palantir implies it can be very short in strong cases.) citeturn15view0turn21view0  

**Labour intensity**
- `fde_eq(t)`: FDE-equivalent effort required per month at time `t`.  
  - Use the phased curve (Year 1: 2–6; Year 3: 1–3; Year 5: 0–1) as a starting point. **[SPECULATIVE]** citeturn10news51turn8search1  
- `aifd_multiplier`: productivity multiplier from automation (AIFD).  
  - **[CONFIRMED]** Evidence supports at least an order-of-magnitude cycle-time improvement in some migration contexts (years → days/weeks). citeturn21view0turn18view1  

**Economic outcomes**
- `ACV_0`: initial ACV after conversion
- `NDR`: net dollar retention / expansion factor

### Bootcamp as CAC: a simple, explicit equation

Treat each bootcamp as a CAC unit:

`CAC_bootcamp = (Labour_cost + Cloud_pilot_cost + Travel_cost) / P(convert)`

Where:
- Labour and cloud/travel categories are explicitly stated as part of S&M via pilots/bootcamps in the 10‑K. citeturn14view2  
- `P(convert)` is **not disclosed** by Palantir; you must run sensitivity bands. citeturn19search9turn22view4  

**Spider advantage target:** If Spider starts with AI-automated deployment, you aim to reduce CAC by reducing the numerator (labour/time) while increasing the denominator (conversion), because the product is closer to self-serve and “time-to-wow” is shorter.

### Margin bridge: how to separate “accounting lift” from “real unit economics”

Create a two-layer gross margin model:

- `GM_gaap(t)`  
- `GM_exSBC(t)`  

Because:
- **[CONFIRMED]** In 2020, Palantir’s GAAP GM (68%) and GM excluding SBC (81%) diverged widely. citeturn15view0  
- **[CONFIRMED]** In FY2025 investor materials, adjusted GM is 84%. citeturn29view0  

For Spider, you likely care about a Palantir-like **GM_exSBC** analogue: “gross margin excluding non-cash distortions,” because that is closer to true platform economics. Palantir’s own numbers imply that “true” gross margin improvement from 2020 to 2025 is closer to **81% → 84%**, not **68% → 84%**. citeturn15view0turn29view0  

### AIFD as the key scaling lever

Model AIFD as affecting three levers simultaneously:

- **Cycle time compression:** `t_to_prod` falls sharply. citeturn21view0turn18view1  
- **Labour compression:** `fde_eq(t)` falls or more accounts per FDE.  
- **Customer self-build acceleration:** customer developers ship more; Palantir-like vendor effort shifts to platform maintenance and governance.

This is consistent with Palantir’s explicit “two humans + AI FTEs” claim and its framing of AIFDE abilities (connecting data, building ontology/functions/apps). citeturn21view0  

### What Spider should treat as “unknowns” that require deliberate sensitivity ranges

These are the parameters Palantir does not disclose cleanly, and thus where Spider’s model should run scenarios:

- `FDE_count` and `FDE_equivalent allocation%`: Palantir has 4,414 full-time employees (Sep 2025) but no published FDE count. citeturn24view1turn12view1  
- `Bootcamp conversion curves`: 90/180/365-day conversion and ACV distributions are not disclosed. citeturn19search9turn22view4  
- “Self-sufficient revenue share”: no disclosure. citeturn14view2turn24view1  
- Services vs software split: described conceptually but not quantitatively separated as a revenue line. citeturn14view2  

**Strategic punchline for Spider:** Palantir’s public materials show that (a) pilots/bootcamps are treated as a sales motion, (b) the platform is continually engineered to reduce deployment labour/time (Apollo → AIFD), and (c) the headline gross margin story is materially influenced by SBC accounting. Spider’s opportunity is to build a model where the *default* pathway is closer to “AIFD-enabled bootcamp outcomes with minimal human deployment,” so that the same flywheel can exist with materially better CAC and faster margin expansion. citeturn14view2turn15view0turn21view0turn29view0