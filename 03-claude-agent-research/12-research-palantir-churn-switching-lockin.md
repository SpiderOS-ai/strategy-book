# Palantir Customer Churn, Switching Costs, and Lock-In Mechanics: An Independent Assessment

**Date:** 2026-02-17
**Methodology:** Web research across SEC filings, investigative journalism, analyst reports, government contract databases, Gartner Peer Insights, and independent critics. This report prioritizes non-Palantir sources.

---

## 1. Customers Who Left Palantir

Palantir's marketing suggests near-zero churn. The historical record tells a different story, especially in the pre-AIP era (before 2023).

### Confirmed Departures

**Coca-Cola (2016):** Coca-Cola agreed to a pilot in July 2014 but refused to sign a five-year contract in January 2016. The deal would have climbed to $18 million/year by year five. Coca-Cola cited three reasons: (1) cost was too high, (2) they "wanted deeper industry expertise in a partner," and (3) the "working relationship" with Palantir's young engineers was "difficult." This was a marquee loss -- Palantir had invested significant FDE resources into the engagement ([Fast Company](https://www.fastcompany.com/4006398/palantir-has-lost-major-clients-like-coca-cola-american-express-and-nasdaq)).

**American Express (2016):** AmEx ended its Palantir engagement after the company failed to deliver expected results. Palantir blamed AmEx's own hardware limitations and lack of executive support, rather than accepting responsibility for the failure. This pattern of blaming the customer recurred across multiple accounts ([Fast Company](https://www.fastcompany.com/4006398/palantir-has-lost-major-clients-like-coca-cola-american-express-and-nasdaq)).

**Nasdaq (2015-2016):** A meeting between Palantir CEO Alex Karp and the Nasdaq CEO in late 2014 led to a security-related pilot in early 2015. The relationship was "in tatters" by July, following what was described as a "somewhat wacky brainstorm" about potential projects beyond security. The engagement collapsed without expansion ([BuzzFeed News](https://www.buzzfeednews.com/article/williamalden/inside-palantir-silicon-valleys-most-secretive-company)).

**Home Depot (2017):** Home Depot had been a key cybersecurity client. They terminated the relationship for two reasons: (1) Home Depot determined it could rely on its own employees for the work Palantir engineers were doing, and (2) Home Depot was "rankled" when Palantir staff sought to drum up additional business in other departments while being paid by the cybersecurity team. The upselling within the customer organization backfired ([CNBC](https://www.cnbc.com/2017/02/24/palantir-dumped-by-key-cybersecurity-client-home-depot.html)).

**NYPD (2017):** This is the most instructive case. After five years of using Palantir, the NYPD quietly began building a replacement system called "Cobalt" in summer 2016. In February 2017, they announced internally they would cancel the Palantir contract. The NYPD alleged that Palantir refused to provide data in portable formats -- specifically, the "analytical insights and tags" that NYPD investigators had created within the software could not be exported. The NYPD built Cobalt using a group of IBM products tied together with NYPD-created software. The police department believed Cobalt was cheaper and more intuitive than Palantir, and valued the greater degree of control it offered. Michael Burry later cited this case: "If the NYPD can do it on a government budget," implying that Palantir's technology is not irreplaceable ([BuzzFeed News](https://www.buzzfeednews.com/article/williamalden/theres-a-fight-brewing-between-the-nypd-and-silicon-valley); [Benzinga](https://www.benzinga.com/markets/tech/26/02/50660704/palantirs-moat-is-just-obstruction-of-data-transfer-michael-burry-says)).

**JPMorgan Chase (2017):** JPMorgan was once Palantir's marquee corporate customer, engaging Palantir in 2009 with as many as 120 forward-deployed engineers. The relationship deteriorated when in 2013, JPMorgan executives discovered a security executive was using Palantir software to monitor them -- reading their emails and tracking phone calls. The trust breach was fatal to the engagement ([Bloomberg](https://www.bloomberg.com/features/2018-palantir-peter-thiel/)).

### Key Observation

Most of these departures occurred between 2015-2017, when Palantir was still primarily a government-focused company attempting to break into the commercial market. The common threads: excessive cost, cultural friction between Palantir's Silicon Valley engineers and corporate clients, boundary violations (surveillance misuse at JPMorgan, unauthorized upselling at Home Depot), and a perception that the technology did not deliver enough value to justify the price.

---

## 2. Why Customers Churn

Based on the historical record and analyst commentary, churn drivers fall into distinct categories:

### Cost Shock
Palantir contracts can exceed $1 million per month for large deployments. Clients "balked at Palantir's high prices," and the Coca-Cola case demonstrated that multi-year escalation clauses ($18M by year five) can kill deals even after successful pilots ([Fast Company](https://www.fastcompany.com/4006398/palantir-has-lost-major-clients-like-coca-cola-american-express-and-nasdaq)). G-Cloud pricing in the UK lists Foundry & AIP at GBP 3,000,000 per licence ([UK Digital Marketplace](https://www.applytosupply.digitalmarketplace.service.gov.uk/g-cloud/services/804537709233305)).

### Internal Build Decision
Multiple customers concluded they could replicate Palantir's functionality internally. Home Depot determined its own employees could do the work. The NYPD built Cobalt. JPMorgan reportedly developed in-house capabilities. The pattern suggests that after enough exposure to Palantir's methodology, technically sophisticated organizations can internalize the approach.

### Cultural and Relationship Friction
Coca-Cola specifically cited a "difficult working relationship" with Palantir's young engineers. This is a recurring theme: Palantir's FDE culture -- scrappy, move-fast, Silicon Valley ethos -- can clash with the more structured, hierarchical cultures of Fortune 500 companies and government agencies.

### Trust Violations
The JPMorgan surveillance incident is the most extreme example, but Home Depot's frustration with unauthorized upselling reflects a broader pattern of Palantir employees overstepping boundaries within customer organizations.

### Value Uncertainty
Clients "expressed doubts that its software could produce valuable insights over time." Gartner Peer Insights reviewers note that Foundry "should be mainly used for POCs and MVPs as it lacks proper tools for product industrialisation," suggesting some customers hit a ceiling on value extraction ([Gartner Peer Insights](https://www.gartner.com/reviews/market/data-integration-tools/vendor/palantir-technologies/product/foundry)).

---

## 3. Switching Cost Breakdown: What Specifically Makes Leaving Hard

### Ontology Recreation (The Primary Lock-In)
The ontology is the central abstraction in Palantir's platform. It maps an organization's entities, relationships, workflows, and decision logic into a structured semantic layer. This is not merely a database schema -- it encodes years of institutional knowledge about how the organization operates.

Rebuilding an ontology from scratch in another system means:
- Re-mapping every entity type (customers, products, assets, employees, transactions) and their relationships
- Re-encoding business rules and decision logic embedded in the ontology
- Reconstructing the "digital twin" of the organization's operations
- Losing the iterative refinements accumulated over years of use

Morningstar explicitly identified the ontology as the switching cost driver: "Palantir's Ontology, Switching Costs Warrant Quadrupling of Our Fair Value Estimate" ([Morningstar](https://www.morningstar.com/company-reports/1261306-worth-the-hype-palantirs-ontology-switching-costs-warrant-quadrupling-of-our-fair-value-estimate)).

### Data Pipeline Rebuilding
Every integration from external data sources into Palantir must be rebuilt when migrating away. As HASH.ai noted: "Integrations from external data sources with a data backbone need re-establishing or re-creating in the event of any move away." For a large enterprise with dozens or hundreds of connected data sources, this alone represents months of work ([HASH Blog](https://hash.ai/blog/the-problem-with-palantir)).

### Application Rewriting
Palantir's Workshop (application builder) and operational applications built on top of the ontology are Palantir-proprietary. Every operational dashboard, workflow application, and decision-support tool must be rebuilt from scratch on a new platform.

### Security and Access Control Reconfiguration
Palantir's granular, classification-based access controls are deeply embedded in the platform. Permission structures, role hierarchies, and data governance rules are platform-specific and cannot be exported. For organizations in regulated industries (finance, healthcare, defense), this represents months of security recertification work.

### Training and Institutional Knowledge Loss
FDEs and internal "Palantir champions" accumulate deep platform-specific expertise. When switching, this human capital is stranded. New platform skills must be acquired across the organization.

### The Analytical Layer Problem (Burry's Critique)
Michael Burry identified the core issue: "The friction exists in the area between raw data and the insights derived from that data." Raw data can technically be exported (CSV, JSON, Parquet), but the analytical work product -- the tags, annotations, models, and derived insights built over years -- is trapped in Palantir's proprietary layer. "If a customer cannot leave without losing years of analytical work, the moat is actually just obstruction" ([Benzinga](https://www.benzinga.com/markets/tech/26/02/50660704/palantirs-moat-is-just-obstruction-of-data-transfer-michael-burry-says)).

---

## 4. Estimated Switching Costs

No independent consultant or analyst has published definitive dollar estimates for migrating away from Palantir, in part because no large-scale migration has been publicly documented in detail. However, reasonable inferences can be drawn:

### Palantir's Own Marketing Claims
Palantir advertises that it can migrate customers *to* its platform, compressing "timelines from years to weeks." The asymmetry is telling: if migration *to* Palantir takes years without their help, migration *away* -- without their cooperation -- takes at least as long.

### NYPD Case Estimate
The NYPD began building Cobalt in summer 2016 and planned to switch by July 2017 -- roughly 12 months for a relatively small deployment (one police department). For a Fortune 500 company with enterprise-wide Foundry deployment, 18-36 months is a reasonable estimate.

### Cost Components (Analyst-Inferred)
For an enterprise spending $10M-$50M/year on Palantir:
- **Ontology recreation:** 6-18 months of data engineering effort, $2M-$10M depending on complexity
- **Pipeline rebuilding:** 3-12 months, $1M-$5M for dozens of integrations
- **Application rewriting:** 6-18 months, $2M-$8M for operational applications
- **Security recertification:** 3-6 months, $500K-$2M
- **Training and productivity loss:** 6-12 months of reduced efficiency, $1M-$3M
- **Dual-running costs:** 3-6 months of parallel systems, $3M-$15M
- **Total estimated switching cost:** $10M-$43M, or approximately 1-3x annual Palantir spend

For government customers in classified environments, add 12-36 months for ATO (Authority to Operate) recertification, costing $90,000-$700,000 for the certification alone, plus extensive engineering time ([Second Front](https://www.secondfront.com/resources/blog/dod-ato-explained/)).

---

## 5. Lock-In Mechanisms: Intentional or Emergent?

### The Intentional Case
Several indicators suggest lock-in is by design, not accident:

1. **Peter Thiel's philosophy:** Palantir's founder wrote in *Zero to One* that monopolies "set their own prices" and should pursue market dominance. The HASH.ai analysis explicitly connects this philosophy to Palantir's strategy ([HASH Blog](https://hash.ai/blog/the-problem-with-palantir)).

2. **Proprietary ontology format:** Data exists within Palantir "in a proprietary shape and format" that, while exportable to CSV/JSON, produces files that "are not readily usable by any other equivalent system." This is a deliberate architectural choice.

3. **FDE embedding strategy:** Embedding 50-120 engineers inside a customer organization (as with JPMorgan) creates operational dependency. Critics note the FDE model "can foster client dependency on the vendor's engineers for ongoing operations, potentially masking underlying product flaws" ([Everest Group](https://www.everestgrp.com/palantir-inside-the-category-of-one-forward-deployed-software-engineers-blog/)).

4. **The NYPD data refusal:** The allegation that Palantir refused to provide data in portable formats -- if true -- is the most direct evidence of intentional lock-in.

### Palantir's Counter-Argument
Palantir's UK G-Cloud listing states: "The platform features an open, pluggable architecture with publicly documented APIs at every tier of the software. All data in the platform can be securely exported in non-proprietary formats." Palantir claims its software "has been purposefully designed to prevent vendor lock-in" ([UK Digital Marketplace](https://www.applytosupply.digitalmarketplace.service.gov.uk/g-cloud/services/804537709233305)).

### The Reality
Even if raw data export is technically possible, the ontology, applications, permissions, and derived insights cannot meaningfully transfer. The lock-in is structural rather than contractual -- you can leave, but you leave behind years of organizational intelligence encoded in a proprietary format. This is the distinction Burry identifies: the moat is not the data itself, but the "obstruction of data transfer" -- the gap between raw data and usable insights.

---

## 6. Competitor Displacement Attempts

### Databricks
Databricks has pushed Unity Catalog as a governance layer rivaling Palantir's security controls, historically a key reason government agencies and banks chose Gotham/Foundry. However, Databricks lacks Palantir's ontology layer, operational application builder, and embedded FDE support model. No confirmed cases of Databricks fully displacing Palantir at an existing customer have been documented ([The Brand Hopper](https://thebrandhopper.com/2025/12/22/who-are-palantirs-competitors-in-software-industry/)).

### Snowflake
Snowflake's Unistore workload attempts to handle both transactional and analytical data, attacking Palantir's strength in operational workflows. If Snowflake can handle day-to-day operations, the need for Foundry as an operational layer diminishes. However, Snowflake remains primarily a data warehousing platform and lacks the ontological framework, application layer, and government security certifications that define Palantir's value proposition.

### Microsoft Fabric
The most credible threat by distribution advantage. Fabric sits inside the ecosystem most enterprises already pay for through their Microsoft Enterprise Agreement, making it effectively "already included." However, Fabric lacks the depth of Palantir's ontology, the FDE deployment model, and the classified-environment certifications. Microsoft competes on breadth and convenience; Palantir competes on depth and mission-criticality ([i4C](https://www.i4c.com/palantir-vs-snowflake-vs-databricks-which-one-fits-your-business/)).

### Key Observation
No competitor has publicly displaced Palantir at scale at an existing major customer. The competitive threat is more about preventing new Palantir wins than displacing existing deployments. This is itself evidence of switching cost effectiveness.

---

## 7. Palantir's Churn Defense Playbook

### Bootcamp Strategy for Expansion
Palantir's AIP bootcamps are the primary tool for defending and expanding existing accounts. These intensive 1-5 day sessions challenge customers to compare internal efforts against Palantir's platform. A reported example: a $3M contract expanded to an enterprise-wide agreement in the same quarter after a bootcamp. Since mid-2023, Palantir has completed bootcamps with 915 organizations. U.S. commercial revenue grew 121% YoY, with TCV up 342% YoY in Q3 FY2025 ([GTM Foundry](https://www.gtmfoundry.vc/p/palantirs-bootcamp-gtm-strategy)).

### FDE Surge
When a customer threatens to churn, Palantir can deploy additional FDEs to demonstrate value, build new use cases, and deepen the integration. This increases switching costs while simultaneously addressing the customer's immediate pain points.

### Pricing Flexibility
Palantir's own customer-facing analytics include capabilities to "assess the impact of different fee structures on customer retention" and "reprice existing accounts to prevent churn." This suggests structured price concession mechanisms exist for at-risk accounts.

### Executive Escalation
Alex Karp and senior leadership are known to engage directly with major customers. The Acquire-Expand-Scale model involves executive involvement at critical decision points.

### Product Evolution (AIP)
The 2023 launch of AIP (Artificial Intelligence Platform) gave Palantir a powerful retention tool: existing Foundry/Gotham customers can layer generative AI capabilities on top of their existing ontology, creating new value without additional integration work. This directly addresses the historical churn driver of "doubts that software could produce valuable insights over time."

---

## 8. Contract Structure as Lock-In

### Contract Terms
Palantir generally offers contract terms of one to five years. Many contracts contain "termination for convenience" provisions, meaning customers can theoretically exit with less than twelve months' notice. As of December 31, 2024, remaining deal value was $3.1 billion (commercial) and $2.3 billion (government) ([SEC 10-K 2024](https://investors.palantir.com/files/2024%20FY%20PLTR%2010-K.pdf)).

### Government Mega-Contracts
The U.S. Army Enterprise Agreement has a performance period of up to 10 years with a $10 billion ceiling. The Maven Smart System contract started at $480M (sole-source, no competition, with the Pentagon determining no other company could meet requirements), then increased by $795M. These are not easily reversible commitments ([CNBC](https://www.cnbc.com/2025/08/01/palantir-lands-10-billion-army-software-and-data-contract.html); [DefenseScoop](https://defensescoop.com/2024/05/29/palantir-480-million-army-contract-maven-smart-system-artificial-intelligence/)).

### UK Contracts
The NHS Federated Data Platform: seven years, GBP 330 million. The UK MOD Enterprise Agreement establishes a multi-year framework. These long-duration contracts create contractual lock-in on top of the technical switching costs.

### Paradox of Convenience Termination
While Palantir acknowledges convenience termination clauses, the technical switching costs make this largely theoretical. A customer can terminate the contract, but they cannot easily terminate their dependence on the platform.

---

## 9. Government Contract Stickiness

Government contracts exhibit unique lock-in dynamics beyond normal enterprise switching costs:

### ATO (Authority to Operate)
New software entering government classified environments requires ATO certification, which can take 3 months to 3 years and cost $90,000-$700,000 for the certification alone. Palantir's existing IL6 authorization from DISA represents years of accumulated security certification that any replacement would need to replicate ([Second Front](https://www.secondfront.com/resources/blog/dod-ato-explained/)).

### Security Clearance Infrastructure
Palantir maintains a substantial cleared workforce. Replacing them would require a competitor to sponsor equivalent security clearances -- a process that itself takes 6-18 months per person.

### Sole-Source Precedent
The Maven contract was awarded sole-source because the Pentagon "officially determined no other company was capable of meeting its requirements." Once this determination is made, it creates institutional and legal precedent for renewal without competition.

### Classified Environment Air Gaps
Classified environments are air-gapped, preventing access to external APIs and internet. Any replacement system must be fully self-contained and certified for the specific classification level. Development teams "rigorously test software in a commercial cloud only to find that it fails upon deployment to a classified region" due to missing services and strict security controls.

### Institutional Knowledge and Workflow Embedding
Palantir's platforms become embedded in the daily operational workflows of military and intelligence agencies. TITAN (Tactical Intelligence Targeting Access Node) provides soldiers with "next-generation data fusion and deep-sensing capabilities." Replacing a battlefield targeting system mid-deployment is not a realistic option.

### The $180 Billion Recompete Window
There are approximately $180 billion in federal recompetes coming in FY2025-2026. While this theoretically creates opportunities for competitors, Palantir's entrenched position through embedded engineers, security certifications, and operational dependency creates formidable advantages in recompete situations ([FedSavvy Strategies](https://www.fedsavvystrategies.com/palantir-federal/)).

---

## 10. Net Revenue Retention Trajectory

Palantir's net dollar retention (NDR) tells the story of decreasing churn and increasing expansion:

| Period | NDR | Notes |
|--------|-----|-------|
| 2021-2022 | >120% | Pre-AIP era, strong expansion |
| Q3 2023 | 107% | Trough -- commercial growth slowing pre-AIP |
| Q1 2024 | 111% | AIP bootcamps beginning to drive expansion |
| Q2 2024 | 114% | Continued acceleration |
| Q3 2024 | 118% | +400 bps QoQ |
| Q4 2024 | 120% | +200 bps QoQ |
| Q1 2025 | 120% | Stable |
| Q3 2025 | 134% | +600 bps QoQ, AIP-driven |
| Q4 2025 | 139% | Record high, +500 bps QoQ |

Sources: [Palantir IR Q4 2024](https://investors.palantir.com/news-details/2025/Palantir-Reports-Q4-2024-Revenue-Growth-of-36-YY-U.S.-Revenue-Growth-of-52-YY-Issues-FY-2025-Revenue-Guidance-of-31-YY-Growth-Eviscerating-Consensus-Estimates/); [Palantir Q3 2025 Investor Presentation](https://investors.palantir.com/files/Palantir%20-%20Q3%202025%20Investor%20Presentation.pdf); [Motley Fool Q4 2025 Transcript](https://www.fool.com/earnings/call-transcripts/2026/02/02/palantir-pltr-q4-2025-earnings-call-transcript/)

### What Drove the Improvement?
1. **AIP launch (mid-2023):** Gave existing customers a reason to expand spend without new integration work
2. **Bootcamp flywheel:** 915 organizations bootcamped since mid-2023, driving rapid expansion within existing accounts
3. **Revenue per top customer growth:** Average revenue for top 20 customers grew from $54.6M (2023) to $64.6M (2024)
4. **Customer count acceleration:** 45% YoY customer count growth in Q3 2025, with commercial customers growing 49%
5. **Reduced early-stage churn:** The bootcamp model reduces pilot-to-expansion failure rates

### Is Churn Actually Decreasing?
Palantir does not disclose gross retention (GRR) separately from net retention (NDR). NDR of 139% could mask underlying churn if expansion is sufficiently large. However, the trajectory from 107% to 139% almost certainly reflects both lower churn AND higher expansion. A company losing significant customers would struggle to achieve 139% NDR even with aggressive upselling.

### Implied Churn Math
If gross retention is approximately 90-95% (a reasonable assumption for enterprise software), then expansion contribution in Q4 2025 was approximately 44-49% -- meaning existing customers nearly doubled their spend on average. This is extraordinary but plausible given AIP adoption.

---

## 11. Customer Satisfaction Data

### Gartner Peer Insights
- **Palantir (overall):** 3.7 stars (Data & Analytics market, 6 reviews)
- **Palantir Foundry:** 4.6 stars (Data Integration Tools, 61 reviews)
- **Palantir AIP:** Reviewed under AI Application Development Platforms

Sources: [Gartner Peer Insights - Palantir](https://www.gartner.com/reviews/market/data-and-analytics/vendor/palantir-technologies); [Gartner Peer Insights - Foundry](https://www.gartner.com/reviews/market/data-integration-tools/vendor/palantir-technologies/product/foundry)

### What Customers Love
- **FDE support quality:** "Great employees providing onsite support, reacting to issues and concerns promptly and professionally"
- **Data integration breadth:** "Can collect data from any existing systems without modifying those systems"
- **Security model:** Classification-based access controls are a differentiator for regulated industries
- **Ontology as organizational intelligence:** Once built, the ontology becomes genuinely valuable

### What Customers Hate
- **Opaque pricing:** "The price model is not clear" -- a recurring complaint
- **Dependency on Palantir engineers:** "Complex initial setup and configuration requires expert help and significant time investment" with "some workflows so advanced they require Palantir engineers"
- **Not production-ready for all use cases:** "Should be mainly used for POCs and MVPs as it lacks proper tools for product industrialisation"
- **High skill requirements:** "Requires certain level of IT skills which is difficult to ensure for all the users"
- **Forced updates:** Monthly mandatory updates with no ability to stay on older versions

### NHS UK Case Study: Low Adoption
Fewer than a quarter of England's 215 hospital trusts were actively using Palantir's Federated Data Platform by the end of 2024. Many trusts reported they "already have similar tools in use that presently exceed the capability and application of what the FDP is currently trying to develop." Green Party MPs demanded an inquiry, and the BMA raised concerns about patient data privacy. 48% of UK adults surveyed said they would opt out if the FDP is run by a private company ([Pulse Today](https://www.pulsetoday.co.uk/news/technology/nhs-england-to-face-legal-action-over-heavily-redacted-palantir-contract/); [pharmaphorum](https://pharmaphorum.com/news/concerns-voiced-palantir-wins-ps330m-nhs-data-contract)).

---

## 12. Synthesis: The Lock-In Verdict

### The Honest Assessment

Palantir's lock-in is real, substantial, and likely at least partially intentional. It operates on multiple reinforcing layers:

1. **Technical lock-in:** Proprietary ontology, non-portable analytical work product, platform-specific applications
2. **Operational lock-in:** Embedded FDEs, workflow dependency, institutional knowledge trapped in the platform
3. **Contractual lock-in:** Multi-year agreements, 10-year government frameworks, sole-source precedent
4. **Regulatory lock-in:** ATO certifications, security clearances, classified environment dependencies
5. **Knowledge lock-in:** Trained users, organizational expertise, sunk learning investment

Palantir's public claims about data portability and open APIs are technically accurate at the raw data level but misleading about the full scope of switching costs. You can export your CSV files. You cannot export your ontology, your applications, your security configurations, or the years of analytical work product your team created. This is the gap Burry identified as "obstruction of data transfer."

### What Has Changed

The 2015-2017 churn wave occurred when Palantir was a different company: pre-IPO, primarily government-focused, with an immature commercial go-to-market. Since then:

- AIP has given customers a compelling reason to stay and expand
- The bootcamp model has improved initial value delivery
- Net dollar retention has climbed from 107% to 139%
- Customer count is growing 45% YoY
- Revenue per top customer continues to expand

Palantir's lock-in is becoming stronger, not weaker. Each new AIP deployment, each ontology extension, each new application built on Workshop deepens the switching cost. The question for prospective customers is not whether they can leave -- they technically can -- but whether the cost of leaving will ever be justified by the alternative.

### Morningstar's Final Word

Morningstar assigns Palantir a "narrow moat" based on switching costs and intangible assets, noting that "the high friction with switching vendors suggests deals will become more lucrative over time" and that "the switching cost moat is trending positively." They raised their fair value estimate to $150/share, driven in part by "the lack of a true competitor to Palantir's ontological framework" ([Morningstar](https://www.morningstar.com/company-reports/1261306-worth-the-hype-palantirs-ontology-switching-costs-warrant-quadrupling-of-our-fair-value-estimate)).

---

## Source Index

### Investigative Journalism
- [Fast Company: Palantir has lost major clients](https://www.fastcompany.com/4006398/palantir-has-lost-major-clients-like-coca-cola-american-express-and-nasdaq)
- [CNBC: Palantir dumped by Home Depot](https://www.cnbc.com/2017/02/24/palantir-dumped-by-key-cybersecurity-client-home-depot.html)
- [BuzzFeed News: Inside Palantir](https://www.buzzfeednews.com/article/williamalden/inside-palantir-silicon-valleys-most-secretive-company)
- [BuzzFeed News: NYPD vs Palantir](https://www.buzzfeednews.com/article/williamalden/theres-a-fight-brewing-between-the-nypd-and-silicon-valley)
- [Bloomberg: JPMorgan and Palantir](https://www.bloomberg.com/features/2018-palantir-peter-thiel/)

### Analyst Reports & Investor Commentary
- [Morningstar: Palantir Moat Analysis](https://www.morningstar.com/company-reports/1261306-worth-the-hype-palantirs-ontology-switching-costs-warrant-quadrupling-of-our-fair-value-estimate)
- [Benzinga: Michael Burry on Palantir](https://www.benzinga.com/markets/tech/26/02/50660704/palantirs-moat-is-just-obstruction-of-data-transfer-michael-burry-says)
- [Seeking Alpha: Palantir Moat and Valuation](https://seekingalpha.com/article/4829854-palantir-understand-the-moat-to-understand-the-valuation-let-the-story-play-out)
- [IO Fund: Palantir Stock Analysis](https://io-fund.com/cloud-software/cybersecurity/palantir-stock-how-high-is-too-high)

### Independent Critiques
- [HASH Blog: The Problem with Palantir](https://hash.ai/blog/the-problem-with-palantir)
- [Medium: Beyond Palantir's Ontology](https://medium.com/towards-data-engineering/beyond-palantirs-ontology-the-paradigm-the-platform-and-the-path-to-open-semantics-f8e8b3b5fe93)
- [Brennan Center: Palantir Contract Dispute and NYPD](https://www.brennancenter.org/our-work/analysis-opinion/palantir-contract-dispute-exposes-nypds-lack-transparency)

### SEC Filings & Investor Materials
- [Palantir 2024 10-K](https://investors.palantir.com/files/2024%20FY%20PLTR%2010-K.pdf)
- [Palantir Q4 2024 Earnings](https://investors.palantir.com/news-details/2025/Palantir-Reports-Q4-2024-Revenue-Growth-of-36-YY-U.S.-Revenue-Growth-of-52-YY-Issues-FY-2025-Revenue-Guidance-of-31-YY-Growth-Eviscerating-Consensus-Estimates/)
- [Palantir Q3 2025 Investor Presentation](https://investors.palantir.com/files/Palantir%20-%20Q3%202025%20Investor%20Presentation.pdf)
- [Motley Fool: Q4 2025 Earnings Transcript](https://www.fool.com/earnings/call-transcripts/2026/02/02/palantir-pltr-q4-2025-earnings-call-transcript/)

### Government Contracts & Policy
- [FedScoop: Government's Embrace of Palantir](https://fedscoop.com/palantir-federal-agencies-government-data/)
- [FedSavvy Strategies: Palantir Federal Dominance](https://www.fedsavvystrategies.com/palantir-federal/)
- [DefenseScoop: Maven Contract](https://defensescoop.com/2024/05/29/palantir-480-million-army-contract-maven-smart-system-artificial-intelligence/)
- [CNBC: $10B Army Contract](https://www.cnbc.com/2025/08/01/palantir-lands-10-billion-army-software-and-data-contract.html)
- [Second Front: DoD ATO Explained](https://www.secondfront.com/resources/blog/dod-ato-explained/)
- [UK Digital Marketplace: Palantir G-Cloud Listing](https://www.applytosupply.digitalmarketplace.service.gov.uk/g-cloud/services/804537709233305)

### NHS UK Controversy
- [Pulse Today: NHS Palantir Legal Action](https://www.pulsetoday.co.uk/news/technology/nhs-england-to-face-legal-action-over-heavily-redacted-palantir-contract/)
- [pharmaphorum: NHS Data Contract Concerns](https://pharmaphorum.com/news/concerns-voiced-palantir-wins-ps330m-nhs-data-contract)
- [Democracy for Sale: NHS Adoption Rates](https://democracyforsale.substack.com/p/palantirs-nhs-data-platform-rejected-hospitals)

### Customer Reviews
- [Gartner Peer Insights: Palantir Foundry](https://www.gartner.com/reviews/market/data-integration-tools/vendor/palantir-technologies/product/foundry)
- [Gartner Peer Insights: Palantir Overall](https://www.gartner.com/reviews/market/data-and-analytics/vendor/palantir-technologies)

### Competitive Analysis
- [i4C: Palantir vs Snowflake vs Databricks](https://www.i4c.com/palantir-vs-snowflake-vs-databricks-which-one-fits-your-business/)
- [The Brand Hopper: Palantir Competitors](https://thebrandhopper.com/2025/12/22/who-are-palantirs-competitors-in-software-industry/)

### FDE Model Analysis
- [Everest Group: Palantir FDE Model](https://www.everestgrp.com/palantir-inside-the-category-of-one-forward-deployed-software-engineers-blog/)
- [GTM Foundry: Palantir Bootcamp Strategy](https://www.gtmfoundry.vc/p/palantirs-bootcamp-gtm-strategy)
- [FourWeekMBA: Palantir Business Model](https://fourweekmba.com/palantir-business-model/)
