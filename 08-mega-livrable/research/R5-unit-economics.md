# R5 -- Unit Economics Benchmarks for Spider Financial Model

> **Date**: February 2026
> **Purpose**: Provide data-backed benchmarks to build Spider's financial model
> **Scope**: CAC, LTV, gross margins, churn, salaries, revenue/employee, payback periods

---

## 1. Customer Acquisition Cost (CAC)

### 1.1 Overall B2B SaaS CAC Benchmarks

| Metric | Value | Source |
|--------|-------|--------|
| Average B2B SaaS CAC (all channels) | $536 | [First Page Sage 2025](https://firstpagesage.com/reports/b2b-saas-customer-acquisition-cost-2024-report/) |
| SMB-focused SaaS CAC | $200--$300 | First Page Sage 2025 |
| Mid-market SaaS CAC | $1,000--$5,000 | [Phoenix Strategy Group 2025](https://www.phoenixstrategy.group/blog/cac-benchmarks-by-channel-2025) |
| Enterprise SaaS CAC | $5,000--$15,000+ | First Page Sage 2025 |
| New CAC Ratio (median, 2024) | $2.00 S&M spend per $1.00 New ARR | [Benchmarkit 2025](https://www.benchmarkit.ai/2025benchmarks) |
| Top quartile CAC Ratio | $1.00 per $1.00 New ARR | Benchmarkit 2025 |
| Bottom quartile CAC Ratio | $2.82 per $1.00 New ARR | Benchmarkit 2025 |

### 1.2 CAC by Channel (B2B SaaS)

| Channel | Average CAC | Notes |
|---------|-------------|-------|
| Referral programs | $150 | Lowest cost; leverages trust |
| Organic SEO (thought-leadership) | $647 | Lower when optimized; can drop to ~$290 at scale |
| Organic SEO (basic) | $1,786 | Higher initial cost, slow ROI |
| Paid search (Google Ads) | $802 | Faster results, higher ongoing cost |
| Content marketing (established) | ~$290 | 647% ROI long-term ([Understory 2025](https://www.understoryagency.com/blog/b2b-saas-marketing-benchmarks-2025)) |
| LinkedIn Ads | CPM $5--$8 | Pricier but effective for B2B targeting |
| Events / trade shows | $811+ CPL | Single event cost: $10K--$250K all-in |
| Outbound sales (SDR-driven) | $1,980 | Highest CAC; effective for large deals |
| Overall B2B SaaS average | $395 | Blended across channels |

*Sources: [First Page Sage CAC by Channel 2026](https://firstpagesage.com/marketing/cac-by-channel-fc/), [Phoenix Strategy Group](https://www.phoenixstrategy.group/blog/cac-benchmarks-by-channel-2025)*

### 1.3 CAC by ACV / Price Point

| ACV Range | Typical CAC | CAC Payback (median) | Sales Motion |
|-----------|-------------|---------------------|--------------|
| < $5K ACV (~400EUR/mo) | $200--$500 | 9 months | Self-serve / PLG |
| $5K--$15K ACV (~500--1,250EUR/mo) | $500--$2,000 | 12--15 months | Inside sales |
| $10K--$50K ACV (~800--4,000EUR/mo) | $2,000--$5,000 | 15--18 months | Inside sales + demo |
| $50K--$100K ACV | $5,000--$10,000 | 18--24 months | Field sales |
| > $100K ACV | $10,000--$25,000 | 24+ months | Enterprise sales |

**Spider relevance** (targeting 500--2,000EUR/month = 6K--24K EUR ACV):
- Expected CAC range: **1,000--5,000 EUR** depending on channel mix
- Target CAC ratio: **$1.50 or less per $1.00 New ARR** (top half of market)

*Sources: [Benchmarkit 2025](https://www.benchmarkit.ai/2025benchmarks), [SaaS Capital](https://www.saas-capital.com/blog-posts/revenue-per-employee-benchmarks-for-private-saas-companies/)*

### 1.4 French-Specific CAC Data

| Metric | Value | Source |
|--------|-------|--------|
| French SaaS cost to acquire 1 EUR ARR | 1.10--1.40 EUR | [BPI France Le Hub](https://lehub.bpifrance.fr/plan-marketing-plateformes-saas/) |
| French startup ARR burn rate (growth phase) | 15--25% of annual ARR | [France Digitale / EY Barometer](https://francedigitale.org/publications/barometre-france-digitale-ey-2025) |
| Target LTV/CAC for French SaaS | 3:1 | BPI France |
| French startup ecosystem size | 16,200 startups (2025) | France Digitale 2025 |
| French startup revenue growth (median) | +27% YoY | France Digitale 2024 |

---

## 2. LTV (Lifetime Value) Benchmarks

### 2.1 LTV:CAC Ratios

| Segment | LTV:CAC Ratio | Source |
|---------|---------------|--------|
| Median across 612 companies | 3.2:1 | [Optifai 2025](https://optif.ai/learn/questions/b2b-saas-ltv-benchmark/) |
| Median (Benchmarkit 2024) | 3.6:1 | [Benchmarkit 2025](https://www.benchmarkit.ai/2025benchmarks) |
| SMB SaaS (healthy) | 3:1 target | BPI France / industry standard |
| Enterprise SaaS | 5:1 -- 8:1 | Various |
| Minimum viable | 3:1 | SaaStr rule of thumb |
| Warning zone | < 1.5:1 | Industry consensus |

**How to interpret**:
- **< 1:1** -- Unsustainable, losing money on every customer
- **1:1 -- 3:1** -- Marginal; need to improve retention or reduce CAC
- **3:1 -- 5:1** -- Healthy; standard target
- **> 5:1** -- Excellent, or possibly under-investing in growth

### 2.2 Retention Rates (Gross Dollar Retention)

| Segment | Gross Retention | Source |
|---------|----------------|--------|
| SMB SaaS (< $10K ACV) | 80--85% | [Optifai 2025](https://optif.ai/learn/questions/b2b-saas-net-revenue-retention-benchmark/) |
| Mid-market SaaS | 88--92% | KBCM SaaS Survey 2024 |
| Enterprise SaaS | 90--95% | KBCM SaaS Survey 2024 |
| KBCM survey median (all segments) | ~90% gross retention | [KeyBanc 2024](https://investor.key.com/press-releases/news-details/2024/PRIVATE-SAAS-COMPANY-SURVEY-REVEALS-SHIFT-TOWARDS-FUTURE-GROWTH-WITH-A-CONTINUED-FOCUS-ON-OPERATIONAL-EFFICIENCY-AND-PROFITABILITY/default.aspx) |

### 2.3 Net Dollar Retention (NDR / NRR)

| Segment | Median NDR | "Good" NDR | "Excellent" NDR | Source |
|---------|-----------|-----------|----------------|--------|
| SMB (< $5K ACV) | 90--97% | >= 100% | >= 110% | [Optifai 2025](https://optif.ai/learn/questions/b2b-saas-net-revenue-retention-benchmark/) |
| Mid-market | 100--105% | >= 105% | >= 115% | Optifai / ChartMogul |
| Enterprise | 110--120% | >= 115% | >= 130% | Optifai / ChartMogul |
| Median (all venture-backed SaaS) | 106% | -- | -- | ChartMogul 2024 (N=2,100) |
| KBCM survey median | ~101% | -- | -- | KBCM 2024 |
| Top-performing companies | > 120% | -- | -- | [Wudpecker 2025](https://www.wudpecker.io/blog/retention-benchmarks-for-b2b-saas-in-2025) |

**Key insight for Spider**: SMB NDR is structurally lower than enterprise. Achieving 100%+ NDR in SMB requires deliberate **expansion revenue** mechanisms (upsell tiers, usage-based pricing, add-on modules). Without expansion, even 90% NDR means 10% annual revenue erosion from existing cohorts.

### 2.4 LTV Calculation for Spider Scenarios

Assuming Spider's target ACV of 12,000--24,000 EUR (1,000--2,000 EUR/month):

| Scenario | Monthly Churn | Avg Lifetime | ACV | LTV (Gross Margin adj.) |
|----------|--------------|-------------|-----|------------------------|
| Pessimistic (SMB avg) | 5% | 20 months | 18,000 EUR | 18,000 * (20/12) * 0.75 = **22,500 EUR** |
| Realistic (with CS team) | 3% | 33 months | 18,000 EUR | 18,000 * (33/12) * 0.75 = **37,125 EUR** |
| Optimistic (annual contracts) | 1.5% | 67 months | 18,000 EUR | 18,000 * (67/12) * 0.75 = **75,375 EUR** |

*Formula: LTV = ACV x (Avg Lifetime in months / 12) x Gross Margin %*

---

## 3. Gross Margin Benchmarks

### 3.1 By Business Model

| Model | Gross Margin Range | Median | Source |
|-------|-------------------|--------|--------|
| **Pure SaaS** (subscription) | 75--85% | 79% | [CloudZero 2025](https://www.cloudzero.com/blog/saas-gross-margin-benchmarks/), Benchmarkit |
| **Pure SaaS** (top quartile) | 85%+ | 85% | Benchmarkit 2024 |
| **AI-native SaaS** (early stage) | 25--50% | ~25% | [SaaStr](https://www.saastr.com/have-ai-gross-margins-really-turned-the-corner-the-real-math-behind-openais-70-compute-margin-and-why-b2b-startups-are-still-running-on-a-treadmill/) |
| **AI-native SaaS** (at scale) | 50--70% | ~60% | [Monetizely 2026](https://www.getmonetizely.com/blogs/the-economics-of-ai-first-b2b-saas-in-2026) |
| **Managed IT services** | 40--50% | 46.2% | [ConnectWise / Service Leadership Q2 2024](https://www.connectwise.com/company/press/releases/2024-08-06-service-leadership-q2-data-report) |
| **MSP best-in-class** | 50--60% | ~55% | ConnectWise 2024 |
| **Professional services / consulting** | 20--35% | ~25% | [Deltek 2025 Benchmarks](https://www.deltek.com/en/blog/professional-services-benchmarks) |
| **Project-based services** | 15--25% | 19.4% | Service Leadership Q2 2024 |
| **SaaS + services blended** | 65--75% | 71--72% | CloudZero 2025 |

### 3.2 Palantir Gross Margin Evolution (Hybrid Model Case Study)

| Year | Revenue ($B) | Gross Margin | Operating Margin | Employees | Rev/Employee |
|------|-------------|-------------|-----------------|-----------|-------------|
| 2019 | $0.74 | ~68% (est.) | Deep negative | ~2,400 (est.) | ~$310K |
| 2020 | $1.09 | 67.7% | -107.4% | 2,439 | $447K |
| 2021 | $1.54 | 78.0% | -26.7% | 2,439 | $631K |
| 2022 | $1.91 | 78.6% | -8.5% | 2,920 | $654K |
| 2023 | $2.23 | 80.6% | Positive | 3,838 | $581K |
| 2024 | $2.87 | 80.2% | Positive | 3,735 | $728K |
| 2025 | $4.48 | 82.4% | Positive | 3,936 | $1,140K |

*Sources: [MacroTrends PLTR Gross Margin](https://www.macrotrends.net/stocks/charts/PLTR/palantir-technologies/gross-margin), [Bullfincher PLTR Revenue/Employee](https://bullfincher.io/companies/palantir-technologies/revenue-per-employee), [MacroTrends PLTR Employees](https://www.macrotrends.net/stocks/charts/PLTR/palantir-technologies/number-of-employees)*

**Palantir trajectory takeaway**: Palantir improved gross margins from ~68% (services-heavy, pre-IPO) to 82% (software-dominant, 2025) over 6 years. The key driver was converting custom deployments into reusable platform modules (Foundry, AIP). Palantir's contribution margin went from 6.7% in 2019 to 30.6% in H2 2020 -- a dramatic shift as platform leverage kicked in.

### 3.3 Implications for Spider's Hybrid Model

Spider's model will likely evolve through three phases:

| Phase | Mix | Expected Blended Gross Margin |
|-------|-----|------------------------------|
| **Year 1--2** (Services-led) | 70% consulting / 30% software | 35--45% |
| **Year 3--4** (Hybrid) | 40% consulting / 60% software | 55--65% |
| **Year 5+** (Platform-led) | 15% consulting / 85% software | 70--80% |

**Warning**: Below 50% blended gross margin, SaaS multiples do not apply for valuation. Investors look for a clear path to 70%+ gross margin at scale.

---

## 4. Churn Rates by Segment

### 4.1 Monthly Churn Benchmarks

| Segment | Monthly Churn | Annualized | Source |
|---------|--------------|-----------|--------|
| SMB SaaS (< $10K ACV) | 3--7% | 30--58% | [Vena 2025](https://www.venasolutions.com/blog/saas-churn-rate), [Vitally 2025](https://www.vitally.io/post/saas-churn-benchmarks) |
| SMB SaaS (with CS team) | 2--3.5% | 22--35% | Vitally 2025 |
| Mid-market SaaS | 1--2% | 11--22% | [Optifai 2025](https://optif.ai/learn/questions/b2b-saas-churn-rate-benchmark/) |
| Enterprise SaaS | 0.5--1% | 6--12% | Optifai 2025 |
| Average B2B SaaS (2025) | ~0.4%/mo (4.9%/yr) | 4.9% | [UserJot 2026](https://userjot.com/blog/saas-churn-rate-benchmarks) |

**Critical data point**: 43% of all SMB customer losses occur within the first 90 days ([Vitally 2025](https://www.vitally.io/post/saas-churn-benchmarks)). This means onboarding quality is the single most important lever for SMB retention.

### 4.2 Churn by Contract Length

| Contract Type | Churn Multiplier | Typical Churn | Source |
|--------------|-----------------|---------------|--------|
| Monthly contracts | 1x (baseline) | 3--7% monthly | [Paddle](https://www.paddle.com/blog/saas-churn-rate), [HubiFi](https://www.hubifi.com/blog/calculate-saas-churn-rate) |
| Annual contracts | 0.3--0.5x of monthly | 5--15% annual | Paddle, HubiFi |
| Multi-year contracts | 0.1--0.2x of monthly | 3--8% annual | Industry data |

**Key finding**: Annual contracts reduce churn by **2--3x** compared to monthly billing. This is one of the strongest levers Spider can pull to improve unit economics.

### 4.3 Impact of Dedicated CS on SMB Churn

The SMB-to-mid-market churn gap (6.4% vs. 2.8% monthly) narrows to just 1.1% for companies with dedicated SMB customer success teams ([Vitally 2025](https://www.vitally.io/post/saas-churn-benchmarks)). Enterprise-quality retention is achievable for SMB if you invest in CS.

### 4.4 Churn Targets for Spider

| Scenario | Monthly Churn | Annual Churn | Required Strategy |
|----------|--------------|-------------|-------------------|
| **No-go zone** | > 5% | > 46% | Unsustainable; pivot needed |
| **Acceptable (Year 1)** | 3--4% | 30--38% | Normal for early SMB SaaS |
| **Good (Year 2--3)** | 2--3% | 22--30% | Requires CS investment + annual contracts |
| **Excellent (Year 3+)** | 1--2% | 11--22% | Annual contracts + high NPS + sticky workflows |

---

## 5. French Salary Benchmarks for Spider's Team

### 5.1 Employer Cost Multiplier (France)

Employer social charges (charges patronales) in France add **25--45%** to gross salary, with a practical average around **42--45%** for mid-to-high salaries. The total employer cost ("superbrut") is therefore approximately:

> **Employer cost = Gross salary x 1.42 to 1.45**

*Source: [Service Public Entreprendre](https://entreprendre.service-public.gouv.fr/actualites/A17990), [L'Expert Comptable](https://www.l-expert-comptable.com/a/532287-montant-et-calcul-des-charges-patronales.html)*

### 5.2 Developer Salaries (Mid-Senior, 3--7 years experience)

| Role / Location | Gross Annual | Employer Cost (x1.43) | Monthly Employer Cost |
|----------------|-------------|----------------------|---------------------|
| **Developer, Normandy (all levels)** | 39,600 EUR | 56,600 EUR | 4,720 EUR |
| **Developer, Normandy (mid-senior est.)** | 42,000--48,000 EUR | 60,000--68,600 EUR | 5,000--5,720 EUR |
| **Developer Senior, France (median)** | 50,000 EUR | 71,500 EUR | 5,960 EUR |
| **Developer Senior, France (P75)** | 61,500 EUR | 87,900 EUR | 7,330 EUR |
| **Developer Senior, Paris** | 54,000--60,000 EUR | 77,200--85,800 EUR | 6,430--7,150 EUR |
| **Full-stack / Backend Senior, France** | 48,000--60,000 EUR | 68,600--85,800 EUR | 5,720--7,150 EUR |
| **Specialized (Python/AI), Senior** | 55,000--64,000 EUR | 78,600--91,500 EUR | 6,550--7,630 EUR |

*Sources: [Talent.com](https://fr.talent.com/salary?job=d%C3%A9veloppeur), [Indeed Normandie](https://fr.indeed.com/career/d%C3%A9veloppeur/salaries/Normandie), [Glassdoor FR](https://www.glassdoor.fr/Salaires/d%C3%A9veloppeur-senior-salaire-SRCH_KO0,18.htm), [WeLoveDevs](https://welovedevs.com/fr/salaires/senior), [Gefor](https://www.gefor.com/salaire-developpeur-web-en-france/)*

**Normandy discount**: Salaries in Normandy are approximately **20--25% lower** than Paris/Ile-de-France. Paris premium is ~25% over provinces, but cost of living is 8.8% higher overall and 48.9% higher for rent.

**Remote arbitrage**: A developer hired remote from Normandy at province rates (42--48K) who would cost 54--60K in Paris saves the company **12,000--17,000 EUR/year** in gross salary alone (~17,000--24,000 EUR in employer cost).

### 5.3 Consultant Salaries (5--10 years, ex-industry)

| Profile / Location | Gross Annual | Employer Cost (x1.43) | Monthly Employer Cost |
|-------------------|-------------|----------------------|---------------------|
| **Consultant Senior (France avg)** | 55,000--70,000 EUR | 78,600--100,100 EUR | 6,550--8,340 EUR |
| **Consultant Senior (top end)** | 70,000--85,000 EUR | 100,100--121,500 EUR | 8,340--10,130 EUR |
| **Supply Chain Consultant (experienced)** | 50,000--70,000 EUR | 71,500--100,100 EUR | 5,960--8,340 EUR |
| **Supply Chain Consultant (Paris)** | 50,000--70,000 EUR | 71,500--100,100 EUR | 5,960--8,340 EUR |
| **Industry Consultant (freelance TJM)** | 600--1,200 EUR/day | N/A (freelance) | ~10K--20K EUR/mo billed |

*Sources: [Babylone Consulting 2025](https://www.babyloneconsulting.fr/nos-articles/salaire-consultant-senior-grille-de-remuneration-2025/), [Talent.com](https://fr.talent.com/salary?job=consultant+senior), [Glassdoor FR](https://www.glassdoor.fr/Salaires/supply-chain-consultant-salaire-SRCH_KO0,23.htm), [Amalo Recrutement](https://www.amalo-recrutement.fr/blog/quels-sont-les-salaires-dans-la-supply-chain/)*

**Key note**: Senior consultants with 8%+ salary inflation in 2024--2025 due to talent scarcity. An ex-industry consultant (e.g., ex-supply chain director) with 10+ years typically commands 65,000--85,000 EUR gross, or 93,000--121,500 EUR employer cost.

### 5.4 Spider Team Cost Model (Illustrative)

| Role | Headcount | Gross/person | Employer Cost/person | Total Annual |
|------|-----------|-------------|---------------------|-------------|
| Developers (mid-senior, Normandy) | 3 | 45,000 EUR | 64,350 EUR | 193,050 EUR |
| Industry Consultant (senior) | 2 | 65,000 EUR | 92,950 EUR | 185,900 EUR |
| Founder/CEO (reduced salary) | 1 | 36,000 EUR | 51,480 EUR | 51,480 EUR |
| **Total Year 1 team (6 people)** | **6** | -- | -- | **430,430 EUR** |

Add ~20% for tools, infra, office, travel = **~516,000 EUR total burn for 6-person team**.

---

## 6. Revenue Per Employee Benchmarks

### 6.1 Industry Benchmarks

| Company Type | Revenue/Employee | Source |
|-------------|-----------------|--------|
| **Private SaaS (median)** | $129,724 | [SaaS Capital 2025](https://www.saas-capital.com/blog-posts/revenue-per-employee-benchmarks-for-private-saas-companies/) |
| **Private SaaS < $1M ARR** | $50,091 | SaaS Capital 2025 |
| **Private SaaS $1--3M ARR** | $99,858 | SaaS Capital 2025 |
| **Private SaaS $5--10M ARR** | ~$140,000 | SaaS Capital 2025 |
| **Private SaaS $20--50M ARR** | ~$175,000 | SaaS Capital 2025 |
| **Public SaaS (median)** | $283,000 | SaaS Capital 2025 |
| **Public SaaS (IPO target)** | $300,000+ | Industry standard |
| **PLG SaaS companies** | $350,000 | [GrowthUnhinged / OpenView](https://www.growthunhinged.com/p/your-guide-to-arr-per-fte) |
| **Consulting firms** | $199,000 | [Deltek 2025](https://www.deltek.com/en/blog/professional-services-benchmarks) |
| **Professional services in SaaS** | $175,000 | [Statista 2023](https://www.statista.com/statistics/936949/saas-professional-services-worldwide-revenue-per-employee/) |
| **Bootstrapped SaaS** | 15--20% higher than VC-backed | SaaS Capital 2025 |

### 6.2 Palantir Revenue Per Employee (Case Study)

| Year | Revenue | Employees | Rev/Employee |
|------|---------|-----------|-------------|
| 2020 | $1.09B | 2,439 | $447K |
| 2021 | $1.54B | 2,439 | $631K |
| 2022 | $1.91B | 2,920 | $654K |
| 2023 | $2.23B | 3,838 | $581K |
| 2024 | $2.87B | 3,735 | $728K |
| 2025 | $4.48B | 3,936 | $1,140K |

*Source: [Bullfincher](https://bullfincher.io/companies/palantir-technologies/revenue-per-employee), [MacroTrends](https://www.macrotrends.net/stocks/charts/PLTR/palantir-technologies/number-of-employees)*

Palantir CEO Alex Karp stated: "We will grow 10x with fewer employees than we have today" ([SaaStr](https://www.saastr.com/palantirs-ceo-we-will-grow-10x-with-fewer-employees-than-we-have-today/)).

### 6.3 Spider Revenue Per Employee Targets

| Phase | Team Size | Target ARR | Rev/Employee | Comparable |
|-------|-----------|-----------|-------------|-----------|
| Year 1 (pre-revenue) | 6 | 0--150K EUR | 0--25K EUR | Normal pre-PMF |
| Year 2 | 8 | 300--600K EUR | 37--75K EUR | Below $1M ARR median |
| Year 3 | 12 | 800K--1.5M EUR | 67--125K EUR | Approaching SaaS median |
| Year 5 | 20 | 3--5M EUR | 150--250K EUR | Healthy SaaS territory |

**Realistic target for a hybrid model like Spider**: 120,000--180,000 EUR/employee at $3--5M ARR, blending SaaS and consulting revenue. This is between pure consulting ($175K--$199K) and pure SaaS ($130K--$175K at that scale), reflecting the hybrid nature.

---

## 7. Payback Period Benchmarks

### 7.1 Industry Benchmarks

| Segment / ACV | Median Payback | "Good" Target | Source |
|--------------|---------------|--------------|--------|
| SaaS overall (2024) | 18 months | < 15 months | [Benchmarkit 2025](https://www.benchmarkit.ai/2025benchmarks) |
| SaaS overall (2023) | 14 months | < 12 months | Benchmarkit 2024 |
| ACV < $5K (SMB) | 9 months | < 6 months | [ScaleXP 2025](https://www.scalexp.com/blog-saas-benchmarks-cac-payback-2025/) |
| ACV $5K--$25K | 12--15 months | < 12 months | ScaleXP 2025 |
| ACV $25K--$100K | 18--24 months | < 18 months | Benchmarkit |
| ACV > $100K | 24 months | < 24 months | Benchmarkit |
| Early-stage < $1M ARR | 2 months (median) | N/A | [First Page Sage 2025](https://firstpagesage.com/reports/saas-cac-payback-benchmarks/) |
| High-performing SaaS | 5--7 months | -- | First Page Sage 2025 |

**Note on early-stage**: The 2-month median for < $1M ARR companies reflects founder-led sales (near-zero CAC), not sustainable acquisition. As companies scale and invest in marketing/sales, payback naturally extends.

### 7.2 What's Acceptable for Early-Stage / Pre-PMF?

| Stage | Acceptable Payback | Why |
|-------|-------------------|-----|
| Pre-PMF (founder-led sales) | 0--6 months | Low CAC (founder time), high-touch |
| Early post-PMF | 12--18 months | Building repeatable sales motion |
| Growth stage | 12--15 months | Efficiency matters for fundraising |
| Scale | < 12 months | Required for capital efficiency |

**Bessemer Efficiency Score** target: >= 1.0x (every $1 burned produces $1 in new ARR). A 0.5x ratio is "good," 0.5--1.5x is "better," and > 1.5x is "best" ([BVP](https://www.bvp.com/atlas/the-cloud-100-benchmarks-report), [Wall Street Prep](https://www.wallstreetprep.com/knowledge/bessemer-efficiency-score/)).

### 7.3 Spider Payback Scenarios

| Scenario | ACV | CAC | Gross Margin | Payback |
|----------|-----|-----|-------------|---------|
| Low-touch inbound | 12,000 EUR | 2,000 EUR | 70% | **2.9 months** |
| Standard inside sales | 18,000 EUR | 5,000 EUR | 65% | **5.1 months** |
| High-touch consultative | 24,000 EUR | 10,000 EUR | 55% | **9.1 months** |
| Enterprise pilot | 36,000 EUR | 15,000 EUR | 50% | **10.0 months** |

*Formula: Payback = CAC / (ACV x Gross Margin / 12)*

---

## 8. Summary: Spider Unit Economics Model

### 8.1 Target Metrics (Year 3 -- Post-PMF)

| Metric | Target | Benchmark Context |
|--------|--------|------------------|
| ACV | 12,000--24,000 EUR | SMB-to-mid-market French PMEs |
| Blended Gross Margin | 55--65% | Hybrid SaaS + consulting |
| CAC | 3,000--6,000 EUR | Inside sales + content marketing |
| LTV:CAC | >= 3:1 | Industry standard minimum |
| Monthly Churn | 2--3% | Annual contracts + CS team |
| NDR | 95--105% | Expansion via upsell tiers |
| CAC Payback | < 12 months | Healthy SaaS territory |
| Rev/Employee | 100--150K EUR | Hybrid model benchmark |
| Bessemer Efficiency | >= 0.5x | "Good" for early growth stage |

### 8.2 Critical Levers for Spider

1. **Annual contracts over monthly** -- Reduces churn by 2--3x, improves cash flow, lowers CAC payback
2. **Onboarding excellence** -- 43% of SMB churn happens in first 90 days
3. **Expansion revenue** -- Essential to reach 100%+ NDR in SMB segment
4. **Platform leverage** -- Palantir's gross margin improved from 68% to 82% as it productized consulting into software
5. **Normandy cost arbitrage** -- 20--25% salary savings vs. Paris with remote talent
6. **Content-led acquisition** -- Organic SEO CAC ($647) is 3x cheaper than outbound ($1,980)

### 8.3 Red Lines / Warning Signs

| Metric | Red Line | Action |
|--------|----------|--------|
| Monthly churn > 5% | Product-market fit issue | Pause acquisition, fix retention |
| CAC payback > 24 months | Sales motion too expensive | Shift to lower-touch channels |
| LTV:CAC < 1.5:1 | Losing money on customers | Raise prices or cut CAC |
| Gross margin < 40% | Services-heavy, no leverage | Productize faster |
| Burn multiple > 3x | Inefficient spending | Cut burn, focus on efficiency |

---

## Sources Summary

### Benchmarking Reports
- [Benchmarkit 2025 SaaS Performance Metrics](https://www.benchmarkit.ai/2025benchmarks)
- [High Alpha / OpenView 2025 SaaS Benchmarks](https://www.highalpha.com/saas-benchmarks)
- [KeyBanc KBCM 2024 Private SaaS Survey](https://investor.key.com/press-releases/news-details/2024/PRIVATE-SAAS-COMPANY-SURVEY-REVEALS-SHIFT-TOWARDS-FUTURE-GROWTH-WITH-A-CONTINUED-FOCUS-ON-OPERATIONAL-EFFICIENCY-AND-PROFITABILITY/default.aspx)
- [KeyBanc KBCM 2025 Private SaaS Survey](https://investor.key.com/press-releases/news-details/2025/PRIVATE-SAAS-COMPANY-SURVEY-REVEALS-AI-DRIVEN-TRANSFORMATION-AND-SUSTAINED-OPERATIONAL-EXCELLENCE/default.aspx)
- [Bessemer Cloud 100 Benchmarks 2025](https://www.bvp.com/atlas/the-cloud-100-benchmarks-report)
- [SaaS Capital 2025 Revenue Per Employee](https://www.saas-capital.com/blog-posts/revenue-per-employee-benchmarks-for-private-saas-companies/)
- [First Page Sage CAC by Channel 2026](https://firstpagesage.com/marketing/cac-by-channel-fc/)
- [First Page Sage B2B SaaS CAC 2025](https://firstpagesage.com/reports/b2b-saas-customer-acquisition-cost-2024-report/)
- [First Page Sage CAC Payback 2025](https://firstpagesage.com/reports/saas-cac-payback-benchmarks/)
- [Deltek 2025 Professional Services Benchmarks](https://www.deltek.com/en/blog/professional-services-benchmarks)

### Churn & Retention
- [Vena SaaS Churn Rate 2025](https://www.venasolutions.com/blog/saas-churn-rate)
- [Vitally B2B SaaS Churn Benchmarks 2025](https://www.vitally.io/post/saas-churn-benchmarks)
- [Optifai B2B SaaS NRR Benchmarks](https://optif.ai/learn/questions/b2b-saas-net-revenue-retention-benchmark/)
- [Optifai B2B SaaS LTV Benchmarks](https://optif.ai/learn/questions/b2b-saas-ltv-benchmark/)
- [UserJot SaaS Churn 2026](https://userjot.com/blog/saas-churn-rate-benchmarks)

### Gross Margins & AI Economics
- [CloudZero SaaS Gross Margin 2025](https://www.cloudzero.com/blog/saas-gross-margin-benchmarks/)
- [Monetizely AI-First SaaS Economics 2026](https://www.getmonetizely.com/blogs/the-economics-of-ai-first-b2b-saas-in-2026)
- [SaaStr AI Gross Margins](https://www.saastr.com/have-ai-gross-margins-really-turned-the-corner-the-real-math-behind-openais-70-compute-margin-and-why-b2b-startups-are-still-running-on-a-treadmill/)
- [ConnectWise MSP Margins Q2 2024](https://www.connectwise.com/company/press/releases/2024-08-06-service-leadership-q2-data-report)

### Palantir Financial Data
- [MacroTrends PLTR Gross Margin](https://www.macrotrends.net/stocks/charts/PLTR/palantir-technologies/gross-margin)
- [MacroTrends PLTR Revenue](https://www.macrotrends.net/stocks/charts/PLTR/palantir-technologies/revenue)
- [MacroTrends PLTR Employees](https://www.macrotrends.net/stocks/charts/PLTR/palantir-technologies/number-of-employees)
- [Bullfincher PLTR Revenue/Employee](https://bullfincher.io/companies/palantir-technologies/revenue-per-employee)

### French Market Data
- [BPI France Le Hub -- SaaS Marketing](https://lehub.bpifrance.fr/plan-marketing-plateformes-saas/)
- [France Digitale / EY Barometer 2025](https://francedigitale.org/publications/barometre-france-digitale-ey-2025)
- [France Num Barometer 2024](https://www.francenum.gouv.fr/guides-et-conseils/strategie-numerique/comprendre-le-numerique/barometre-france-num-2024-perception)

### French Salary Data
- [Indeed -- Developer Salaries Normandy](https://fr.indeed.com/career/d%C3%A9veloppeur/salaries/Normandie)
- [Glassdoor FR -- Developer Senior](https://www.glassdoor.fr/Salaires/d%C3%A9veloppeur-senior-salaire-SRCH_KO0,18.htm)
- [WeLoveDevs -- Salary Data](https://welovedevs.com/fr/salaires/senior)
- [Talent.com FR](https://fr.talent.com/salary?job=d%C3%A9veloppeur)
- [Babylone Consulting -- Consultant Salaries 2025](https://www.babyloneconsulting.fr/nos-articles/salaire-consultant-senior-grille-de-remuneration-2025/)
- [Amalo Recrutement -- Supply Chain Salaries](https://www.amalo-recrutement.fr/blog/quels-sont-les-salaires-dans-la-supply-chain/)
- [Service Public -- Charges Patronales 2025](https://entreprendre.service-public.gouv.fr/actualites/A17990)
