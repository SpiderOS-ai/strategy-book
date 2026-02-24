# Palantir's Post-Pilot Playbook: Reverse-Engineering the Expand & Scale Phases
## Customer Expansion Lifecycle Overview
![](https://ppl-ai-code-interpreter-files.s3.amazonaws.com/web/direct-files/f103664eec4b4209ac09f6c7240dca5b/fbc812a6-513b-456c-98c6-05ba4269aab0/953aa99c.png)

![](https://ppl-ai-code-interpreter-files.s3.amazonaws.com/web/direct-files/f103664eec4b4209ac09f6c7240dca5b/fbc812a6-513b-456c-98c6-05ba4269aab0/e4f55a93.png)
Palantir's growth model is built on a deliberate, multi-year progression from a narrow pilot engagement to enterprise-wide platform dependency. The core economic evidence: net dollar retention bottomed at 107% in Q3 2023 and has since climbed to 124% by Q1 2025, with the commercial segment historically reaching 146%+ NDR for mature cohorts. The average contract value across the platform sits at approximately $3.2M, but top accounts like Airbus (est. ~$94M/year) and the US Army ($10B ceiling over 10 years) illustrate what "Scale" phase economics look like.[^1][^2][^3][^4]
---
## EXPAND PHASE (Year 1–3, ~£250K → £2M–5M ACV)
### 1. Expansion Trigger Identification
**How FDEs systematically find expansion opportunities:** The Palantir deployment model uses a three-team topology — Echo (embedded analysts who find real pains and wrangle stakeholders), Delta (FDEs who rapidly build solutions on customer data), and Core Product (which abstracts field patterns into reusable platform features). Echo analysts are specifically designed to be "domain insiders" who identify business problems that FDEs can then solve.[^5]

The expansion trigger identification process works through several mechanisms:

- **AIP Bootcamps for existing customers**: These are 1–5 day immersive, hands-on-keyboard sessions that work for both new and existing customers. The bootcamp structure follows three phases: Phase 1 is introductions and product demos ("experience the art of the possible"), Phase 2 is hands-on keyboards where participants work directly with Palantir engineers, and Phase 3 is showcase and assessment where learnings are shared and next steps aligned. A bootcamp for an existing customer differs from the initial one because participants already understand Foundry/AIP basics — the focus shifts to building AIP intuition beyond chatbot-style interactions and identifying new operational use cases.[^6][^7][^8]

- **Use case identification facilitation**: During bootcamps, participants develop use cases through a combination of interactive overviews, intensive hands-on sessions, and group discussions. The process involves pre-scoping: 1–2 weeks before the bootcamp, the customer confirms participant roles (business owners, users, IT stakeholders), provides static data cuts relevant to their workflows, and Palantir's team pre-builds as much as possible based on high-level use case discussions. The "100 use cases" identification happens through structured workshops where cross-functional business stakeholders brainstorm against real operational data, guided by Palantir SMEs who know how to pattern-match problems to platform capabilities. Palantir explicitly covers use cases across departments: procurement (cost decomposition, negotiation strategies), supply chain (disruption management, signal processing), sales/marketing (lead scoring), and operations.[^9][^7][^10]

- **Deployment Strategist role as expansion scout**: Deployment Strategists go onsite and meet with customer analysts to "understand the critical questions they need to answer and locate their biggest problems," identify relevant datasets, work with FDEs to integrate data, build customized workflows for new user groups, and present proposals for future work to audiences from analysts to C-suite. They are functionally the business-side expansion engine — "taking their feedback to pass to the engineering team, helping them get value from the delivered product, and most importantly — upselling them to sign bigger contracts".[^11][^12][^13]

- **Department prioritization**: The next department is selected based on data adjacency (which departments share entities with the current deployment), business impact (which workflow improvement delivers measurable ROI fastest), and executive sponsorship availability. BP's expansion, for example, started with production reliability across offshore platforms, then extended to maintenance, sensor integration, and eventually an enterprise-wide digital twin spanning 2M+ sensors globally.[^14][^15]
### 2. Cross-Department Ontology Expansion
**How the ontology grows from 1 to 3–5 departments:** The Palantir Ontology is structured in three layers — Semantic (objects, properties, links representing business entities), Kinetic (action types and functions enabling change), and Dynamic (AI-guided decisions and simulations). When expanding across departments, each new domain adds its own Object Types that connect to the existing ontology graph.[^16][^17]

**Technical challenges and solutions:**

- **Conflicting entity definitions**: Palantir has a patented "Generalizable Entity Resolution Based on Ontology Structures" system. It uses a multi-stage approach: blocking (classifying records into groups based on features), comparison (field-level matching with ML, including transformer-based semantic encodings), and clustering (selecting final matches and resolving records to entities). The system incorporates user feedback loops where analysts can confirm or reject matches, and that feedback trains the ML models for improved precision.[^18]

- **Duplicate data across systems**: Palantir's Foundry Entity Resolution product uses AI to "seamlessly link records with AI to establish a reliable, de-duplicated data foundation". When "the same customer exists in both Sales CRM and Finance ERP with different IDs," the ontology resolves this through configurable entity resolution pipelines where each stage uses swappable methods — all governed by ontology rules including revision control, access control, versioning, and provenance tracking.[^19][^18]

- **Ontology governance**: The community has converged on a two-layer governance model — project-specific ontology objects that can be created quickly and used exclusively for their respective projects, and core ontology objects that undergo a more stringent governance process. This mirrors a federated model where departments can iterate fast while a central ontology steward maintains the canonical source of truth. Object types publish through the Ontology Manager with version control, and interfaces provide polymorphism so different departments can model similar concepts consistently.[^17][^20][^21]

**Ontology design follows a systematic process**: 1) Identify business entities, 2) Define attributes, 3) Define relationships (links), 4) Map curated datasets to ontology objects, 5) Publish and version.[^22]
### 3. Center of Excellence (CoE) Formation
**Timing and formation process**: CoE formation typically begins once a customer has moved beyond the initial pilot and is expanding into multiple departments — roughly 6–12 months in, once there are enough active use cases and users to justify a dedicated team. The initiative can come from either side, but the Palantir champion dynamic plays a key role. Companies like Ontologize (founded by ex-Palantir employees) specifically exist to "build teams of Foundry experts at Palantir customers and partners".[^23]

**Certification and training paths (launched December 2025)**: Palantir officially launched its formal certification program, marking the first time the company has opened standardized learning paths for the broader market outside of FDEs:[^24][^25]

| CoE Role | Palantir Certification | Training Focus | Duration |
|---|---|---|---|
| Platform Owner / Foundry Aware | Foundry Aware Certification | Overall platform understanding, governance, use case identification | Entry-level, ~20-40 hours prep |
| App Developer ("North team") | Application Developer Certification | Building front-end operational applications in Workshop, designing business workflows | ~40-60 hours prep[^24] |
| Data Engineer ("South team") | Data Engineer Certification | Python, SQL, Spark, data pipeline construction, ontology mapping, transformations | ~80-100 hours (Python + SQL + Spark)[^26] |
| Ontology Steward | No separate cert yet | Ontology design, entity modeling, governance processes | Covered within Data Engineer + platform training |
| Permissions Manager | No separate cert yet | RBAC configuration, markings, security boundaries | Platform admin training |

The G-Cloud pricing document confirms specific training prices: Bootcamp Training at £1,100/person, Workshop Training at £1,750/person, Integrator Training at £2,100/person, Developer Training at £1,000/person, and combined Developer & Integrator at £2,700/person.[^27]

**Third-party ecosystem**: The Accenture Palantir Business Group (launched December 2025) is supported by 2,000+ Palantir-skilled Accenture professionals and dedicated Palantir FDEs. The NHS FDP apprenticeship program with Multiverse (Euan Blair's firm) trains NHS staff specifically on Foundry/FDP skills. CodeStrap offers an open-source Foundry Foundations Curriculum on GitHub for self-directed learning, and Palantir now offers free developer stacks at build.palantir.com.[^28][^29][^30][^31]
### 4. Champion Cultivation Playbook
**Organic vs. assigned champions**: Palantir champions can be "assigned top-down or grow organically bottoms-up." Regardless of origin, their role is to "drive early success, as business-focused wins are essential to garner continued support and ward off the detractors".[^23]

**Cultivation mechanics:**

- **AIP Bootcamps as champion factories**: Bootcamp participants build real solutions on their own data and exit with an MVP they can demonstrate to leadership. This creates natural champions who have personal ownership of a working AI use case.[^6][^7]
- **ROI ammunition**: Deployment Strategists "present the results of our work and proposals for future work to audiences ranging from analysts to C-suite executives". Champions are armed with quantified outcomes — Lear Corporation, for example, could point to "$30M+ in savings during H1 2025" directly attributable to IDEA program powered by Palantir.[^32][^11]
- **Events and community**: Palantir's annual conferences (AIPCon, DevCon), customer showcases (Phase 3 of bootcamps explicitly includes "share learnings with other clients"), and the growing developer community at community.palantir.com serve as reinforcement mechanisms.[^7]
- **Champion redundancy**: The CoE structure itself creates redundancy — rather than one champion, you have a Platform Owner, multiple app developers, data engineers, and business stakeholders all personally invested in the platform. The Accenture partnership further embeds Palantir-skilled professionals within client organizations.[^30]
- **When a champion leaves**: This is a known risk. The CoE model, certification programs, and emphasis on building institutional ontology knowledge (which persists independent of individuals) are all defensive measures. The ontology itself becomes the "champion" — it's an institutional asset, not a personal one.
### 5. Commercial Expansion Mechanics
![](https://ppl-ai-code-interpreter-files.s3.amazonaws.com/web/direct-files/f103664eec4b4209ac09f6c7240dca5b/fbc812a6-513b-456c-98c6-05ba4269aab0/6890f1a5.png)
**Pricing structure (from G-Cloud procurement document)**:[^27]
Palantir uses a **solution-based/use-case licensing model** where the "level" is determined by a composite of: complexity of data sources, analytical output requirements, user base scale, and operationalization requirements (compute, custom tools, cross-functional needs, Palantir personnel). The tiers from the UK G-Cloud price list:

| Level | Price (GBP) | Typical Stage |
|---|---|---|
| Level 0 | £250,000 | Pilot / single use case |
| Level 1 | £500,000 | Early expand, 1-2 depts |
| Level 2 | £1,000,000 | Multi-dept, moderate complexity |
| Level 3 | £2,000,000 | Cross-functional, multiple analytics |
| Level 4 | £5,000,000 | Enterprise-wide operational |
| Level 5 | £10,000,000 | Large-scale digital twin |
| Level 6–15 | £20M–£1B | Full enterprise platform / national-scale |

Additionally, there's a **core-based licensing** option at £66,000/server core/year with annual support at £21,500/core. Professional services (FDE/implementation) are priced at £125,000/person/quarter for implementation engineers, or £317,000/year for a full-time EU-based Field Service Representative.[^27]

**Expansion pricing mechanics**: The use-case model is additive — each new use case is a separate license at the appropriate level. A customer starting at Level 0 (£250K) who adds three more use cases doesn't just move to Level 3; they may purchase Level 0 + Level 1 + Level 1 (£1.25M total) or consolidate into a Level 2/3 enterprise agreement. The initial contract often includes provisions for expansion — Palantir uses "ramps tied to verified milestones and expansion triggers".[^5]

**Role dynamics**: The Account Executive is responsible for "engaging, evaluating, and delivering new and expansion business opportunities," with core responsibilities including developing customer profiles, implementing growth strategies, and securing enterprise contracts. The Deployment Strategist is the operational expansion scout — scoping "potential engagements in new industries and expanding locations around the world". The AE owns the commercial relationship; the DS owns the operational expansion opportunity identification.[^33][^34][^11]

**Contract structure**: Average contract duration is 3–4 years. Palantir has moved toward consumption-based pricing in AWS Marketplace for some offerings, and the US Army's $10B Enterprise Agreement consolidates 75 contracts into a single vehicle with 10-year ordering period and volume-based discounts.[^1][^35][^36][^37]

***
## SCALE PHASE (Year 3+, £5M–20M+ ACV)
### 6. FDE Withdrawal — "The Graduation"
**Historical context**: In 2007, most customers required 2+ FDEs, with large customers like NHS needing "a small army" of 10+ FDEs. The stated goal was always reaching zero. By 2024, over 33% of Palantir's customers never needed FDEs at all, representing a fundamental shift in the platform's self-service capability.[^38]

**Withdrawal process**: The reduction is gradual, not a hard cutover. As one former FDE noted, "FDEs are great but they should stick to the mega whale customers like Army, NHS, etc." The progression follows the platform maturity curve:[^38]

1. **Phase 1 (Months 0-12)**: FDEs are heavily embedded, building initial ontology, data pipelines, and first applications
2. **Phase 2 (Months 12-24)**: Knowledge transfer begins — FDEs co-build with client team, CoE forms, training programs commence
3. **Phase 3 (Months 24-36)**: FDEs shift to advisory/oversight role, client team handles 50-70% of development
4. **Phase 4 (Month 36+)**: FDE presence reduced to periodic check-ins, quarterly reviews, or on-call for complex projects

**Capability requirements before withdrawal**: The client team must demonstrate competence in ontology extension (adding new Object Types), data pipeline maintenance, Workshop application building, and basic troubleshooting. The certification program (Application Developer + Data Engineer) provides formal benchmarks.[^24]

**Replacement support model**: The FDE on-site presence is replaced by: Palantir Support (ticketing system), the developer community at community.palantir.com, periodic business reviews, and the Accenture/partner ecosystem for complex implementations. "Withdrawal anxiety" is mitigated by ensuring the CoE has sufficient depth and by the platform's increasing self-service tooling.[^30]
### 7. Self-Service Enablement
**The transition from "FDE builds everything" to client builds 70-85% of apps** is enabled by several product evolution steps:

- **Workshop + AIP = citizen developer platform**: Workshop provides low/no-code application building on top of the ontology. Combined with AIP (which brings LLM capabilities), business users can build operational applications without deep technical skills. Palantir's CEO has stated the primary goal is "to see growth within our customers in terms of their business outcomes, their capabilities".[^39]
- **AI FDE (the product, not the person)**: Palantir has built an "AI FDE" capability that gives users "complete authority and visibility over what information the model can access," essentially automating some of the discovery and building tasks that human FDEs previously handled.[^40]
- **Free developer stack**: Available at build.palantir.com, this allows developers to learn and experiment without incurring costs.[^29]

**Timeline variation**:
- **Airbus (2015→present, ~10 years)**: Reached 50,000+ users across 140+ airlines. Self-service is high — the Skywise X1/X2/X3 tiers progressively enable data visibility, operational management, and AI/ML capabilities for airline customers.[^41][^2]
- **Lear Corporation (2023→2025, ~2 years)**: Already has 11,000 employees using the platform with $30M+ in quantified savings. Manufacturing environments with repeatable workflows reach self-service faster.[^32]
- **US Army**: Longer timeline due to security complexity, multiple classification domains, and massive organizational scale. The 10-year $10B EA reflects the ongoing nature of the relationship.[^3]
- **NHS**: Struggling with adoption — only 34 trusts (15%) were actively using FDP products as of mid-2025, with more than half not having adopted at all. This represents a potential "failure to reach self-service" scenario, partly due to organizational resistance and political dynamics rather than technical limitations.[^42]

**Failure rate**: Some customers never reach self-service. Pre-Foundry era departures (Home Depot, AmEx, Hershey's ~2017) were largely attributed to high costs and "how unrefined Palantir was as a company back then". A former FDE noted: "If a customer doesn't need an FDE they aren't using the platform, or they hired ex-FDEs for cheaper" — highlighting that true self-service requires significant client investment in internal capability.[^38][^43]
### 8. Stickiness & Lock-in Mechanics
**Switching cost breakdown** — estimated at $2.5M–$7.5M per enterprise client:[^1]

| Component | Estimated Cost | Lock-in Mechanism |
|---|---|---|
| Data migration | $500K–$1.2M | Data pipeline reconstruction across all integrated systems |
| Ontology reconstruction | $500K–$2M | Rebuilding semantic model (objects, properties, links, interfaces) in new platform |
| Application rebuilding | $500K–$1.5M | All Workshop apps, dashboards, operational workflows |
| Institutional knowledge | Unquantifiable | Decision logs, user edits, audit trails, historical data lineage |
| Security reconfiguration | $200K–$500K | RBAC policies, markings, classification management |
| Retraining costs | $300K–$800K | CoE team, citizen developers certified on new platform |
| Integration time | 6–9 months | Average re-implementation timeline[^1] |

**What specifically makes Palantir hard to leave:**

- **Data integration depth**: A Scale-phase customer like BP has 2M+ sensors integrated into a unified digital twin through Foundry. Rebuilding that integration layer alone takes months.[^15]
- **Ontology complexity**: The ontology is not just a schema — it includes semantic elements (objects, properties, links), kinetic elements (action types, functions), interfaces (polymorphism), and the dynamic layer (AI models, simulations). This is fundamentally different from traditional databases and has no 1:1 equivalent on Databricks or Fabric.[^16][^17]
- **Application dependencies**: Lear has "functions across quality, supply chain, procurement, manufacturing, finance, and design" all connected through Palantir. Each application depends on the ontology, which depends on the data pipelines.[^32]
- **Operational stickiness**: Skywise's integration into "daily operations for airlines and aerospace manufacturers creates high switching costs, making it difficult for competitors to displace Palantir". When 50,000+ users depend on a platform daily, switching has organizational, not just technical, costs.[^44]
- **Platform customization**: 87% of Palantir deployments involve custom solution development, meaning switching requires not just data migration but rebuilding bespoke business logic.[^1]

**Customers who have left**: Home Depot, American Express, Hershey's, Coca-Cola all departed around 2017 — crucially, these were pre-Foundry era customers using older, more rigid software. A Palantir employee from that era noted "there wasn't too much worry within the company because at the time this was a minor endeavor". Post-Foundry departures are rarer, though competitors report some migration: "from the few customers that use both [Palantir and Databricks], all of them are migrating from Palantir to Databricks over time as contracts expire". Palantir's NRR dipped to 107-108% in late 2023, partly attributed to competitive pressure.[^43][^45][^4]

**Churn response**: Palantir responds to churn threats through a combination of: additional bootcamps to demonstrate new AIP capabilities, pricing concessions (particularly at renewal), acceleration of FDE support for struggling deployments, and "defensive expansion" — extending the ontology into additional departments to increase switching costs before renewal negotiations.
### 9. Support Model at Scale
**Apollo continuous delivery**: Apollo is Palantir's deployment infrastructure that manages updates across all customer environments. It is "natively aware of Foundry's object model" and supports object-aware versioning, environment-specific configuration overrides, secure multi-domain delivery (including air-gapped networks), and zero-downtime upgrades. Customers can define release channels and control when their environments take upgrades — they can specify windows for when upgrades should and should not occur.[^46][^47][^48]

**Ongoing support structure**: Palantir provides tiered support through its Support portal. LLM capacity management illustrates the model: all customers start on a "medium tier" sufficient for prototypes and initial use cases, with options to upgrade to Large or XL tiers as usage scales. Customers are instructed to "contact Palantir Support" when hitting rate limits blocking expansion.[^49]

**Business review cadence**: Scale-phase customers typically receive quarterly business reviews where Palantir presents: deployment health metrics, user adoption data, use case pipeline status, and ROI quantification. The Deployment Strategist role explicitly includes presenting "results of our work and proposals for future work to audiences ranging from analysts to C-suite executives".[^11]

**Environment reassessment**: The US Army's Enterprise Agreement includes reassessment every 18–24 months "to ensure optimal performance and innovation", providing a model for how Scale-phase governance works.[^37]
### 10. Revenue Protection Playbook
**Competitive positioning vs. Microsoft Fabric and Databricks:**

| Dimension | Palantir Foundry | Microsoft Fabric | Databricks |
|---|---|---|---|
| Primary strength | Governed operational workflows tied to business objects | Microsoft ecosystem integration, unified analytics | Data science, ML, large-scale processing |
| Target user | Business users + operational teams | BI analysts + data engineers | Data engineers + ML practitioners |
| Ontology/semantic layer | Native, deeply integrated | None (schema-based) | Unity Catalog (emerging) |
| Switching cost | Very high ($2.5–7.5M) | Moderate (MS ecosystem) | Moderate (open-source compatible) |
| Community | Small but growing; certification just launched | Massive Microsoft partner network | Vibrant open-source community |

Source:[^50][^51]

Palantir's competitive response strategy operates on multiple levels:

- **"Defensive expansion" via ontology deepening**: By expanding the ontology across more departments and use cases before renewal, Palantir makes the switching cost calculus even more unfavorable. Each new Object Type, each new application, each new department integrated adds to the switching cost.[^44]
- **AIP as differentiation**: The AIP layer (LLMs + ontology) creates a capability that Databricks and Fabric don't natively replicate — operational AI agents grounded in a governed semantic model. Palantir positions this as "full spectrum AI" rather than just analytics or ML.[^6]
- **Accenture partnership as moat**: The December 2025 Accenture Palantir Business Group puts 2,000+ Palantir-skilled consultants in the field, making Palantir the default recommendation from one of the world's largest SIs.[^30][^31]
- **Platform pricing justification**: Against open-source alternatives, Palantir justifies premium pricing through: time-to-value (bootcamp to production in days, not months), integrated governance and security, the ontology layer that eliminates integration debt, and total cost of ownership arguments (one platform vs. stitching together 5-10 open-source tools). Adjusted gross margins of 84% indicate the market accepts this premium.[^52]
- **Government beachhead**: The US Army $10B EA and NHS £330M FDP create reference architectures that commercial customers can trust. Government validation reduces procurement risk for enterprise buyers.[^53][^3]

***
## Evidence Synthesis: Multi-Year Case Studies
### Airbus Skywise (2015→2026, ~11 years)
- **Pilot**: Palantir embedded a team in France starting 2015[^54]
- **Expand**: Platform grew to serve Airbus internal operations (20,000+ employees), then opened to airline customers
- **Scale**: 140+ airlines, 50,000+ users, Skywise App Store with 19+ applications[^41][^2]
- **Monetization**: Tiered subscriptions (X1 navigate data → X2 navigate operations → X3 navigate uncharted with AI/ML)[^2]
- **Revenue**: Implied ~$94M/year based on user-based licensing estimates[^2]
- **Renewal**: Multi-year extension signed February 2026, with sovereign cloud migration support[^41]
### BP (2014→2024+, ~10+ years)
- **Pilot**: Started 2014 with oil and gas production operations reliability[^14]
- **Expand**: Extended to offshore platforms (North Sea, Gulf of Mexico), Khazzan gas fields (Oman), maintenance and reliability, then enterprise-wide digital twin[^15]
- **Scale**: Integration of 2M+ sensors into single operating picture, model-based digital twin. 5-year strategic relationship renewed September 2024 with new AIP capabilities[^15]
### Lear Corporation (2023→2025+, rapid expansion)
- **Pilot**: First partnered 2023 to digitize manufacturing operations[^32]
- **Expand**: Rapidly grew to quality, supply chain, procurement, manufacturing, finance, and design[^32]
- **Scale**: 11,000 employees using platform, $30M+ savings in H1 2025, 5-year expansion signed September 2025 deploying Foundry + Warp Speed + AIP across global manufacturing[^32]
### NHS FDP (2020→2026+, mixed results)
- **Entry**: Offered services for £1 during COVID-19 pandemic, March 2020[^53]
- **Expand**: £1M contract → £23M two-year deal → £330M FDP contract (November 2023)[^53]
- **Challenges**: Only 34 trusts (15%) actively using products as of June 2025, organizational resistance[^42]
- **Lock-in strategy**: Apprenticeship program with Multiverse training NHS staff on FDP, mandate for all providers to adopt FDP core products by April 2026[^28]
### US Army (2010s→2025+, deepening entrenchment)
- **Expand**: Multiple programs: Vantage ($115M extension December 2023), Maven Smart System, Army Intelligence Data Platform[^55]
- **Scale**: 75 contracts consolidated into single $10B ceiling Enterprise Agreement (August 2025), 10-year ordering period with volume discounts available to all DoD components[^3][^36][^37]

***
## Key Metrics Summary
| Metric | Value | Source |
|---|---|---|
| Net Dollar Retention (Q1 2025) | 124% | Company filings[^4] |
| Historical Peak NDR (US Commercial) | 150% | 2021 cohort[^56] |
| Average Contract Value | $3.2M | Porter's analysis[^1] |
| Switching Costs | $2.5–7.5M | Industry analysis[^1] |
| Platform Customization Rate | 87% | Industry analysis[^1] |
| Client Retention | 93% | Industry analysis[^1] |
| Customers (Q4 2024) | 711 (+43% YoY) | Company filings[^57] |
| Total Revenue Growth (Q4 2025) | 70% YoY | Company filings[^41] |
| US Commercial Revenue Growth (Q4 2025) | 137% YoY | Company filings[^41] |
| Net Income 2025 | $1.625B (+250% YoY) | Company filings[^41] |
| Adjusted Gross Margin | ~84% | Investor analysis[^52] |
| Accenture Palantir-skilled professionals | 2,000+ | Partnership announcement[^30] |

---

## References

1. [Palantir Technologies Inc. (PLTR): 5 Forces Analysis [Jan-2025 Updated]](https://dcfmodeling.com/products/pltr-porters-five-forces-analysis) - Porter's Five Forces Analysis of Palantir Technologies Inc. seeks to shine light on the market dynam...

2. [Palantir's Skywise: the Runway to Monopolize the Sky](https://www.palantirbullets.com/p/how-palantir-seeks-to-monetize-skywise) - How Palantir seeks to monetize Skywise

3. [Palantir lands $10 billion Army software and data contract](https://www.cnbc.com/2025/08/01/palantir-lands-10-billion-army-software-and-data-contract.html) - Palantir has been a key beneficiary of President Donald Trump's clampdown on cost efficiencies using...

4. [Palantir Technologies (PLTR) Dollar Based Net Retention Rate](https://stockanalysis.com/stocks/pltr/metrics/dollar-based-net-retention-rate/)

5. [How Palantir's FDE model revolutionized customer ...](https://www.linkedin.com/posts/mayurhulke_ai-startups-product-activity-7377610646265155584-F7kz) - The Forward Deployed Engineer (FDE) model: doing things that don’t scale at scale. Palantir tested a...

6. [Deploying Full Spectrum AI in Days: How AIP Bootcamps Work](https://blog.palantir.com/deploying-full-spectrum-ai-in-days-how-aip-bootcamps-work-21829ec8d560?gi=5e4fb5d625d4) - Head of Global Commercial Ted Mabrey shares early learnings on why Palantir’s partners find AIP Boot...

7. [[PDF] AIP BOOTCAMP - PVM](https://blog.pvmit.com/hubfs/AIP-bootcamp.pdf)

8. [AIP BOOTCAMP](https://9421792.fs1.hubspotusercontent-na1.net/hubfs/9421792/AIP-bootcamp.pdf)

9. [Deploying Full Spectrum AI in Days: How AIP Bootcamps Work](https://blog.palantir.com/deploying-full-spectrum-ai-in-days-how-aip-bootcamps-work-21829ec8d560) - Palantir Artificial Intelligence Platform (AIP) enables new and existing customers to dramatically a...

10. [Palantir AIP Bootcamp ↘](https://www.hannovermesse.de/apollo/hannover_messe_2024/obs/Binary/A1354173/Palantir%20AIP%20Bootcamp.pdf)

11. [Deployment Strategist - Palantir Technologies](https://www.linkedin.com/jobs/view/deployment-strategist-at-palantir-technologies-4304589565) - Posted 10:13:56 PM. A World-Changing CompanyPalantir builds the world’s leading software for data-dr...

12. [Palantir Technologies hiring Deployment Strategist in New York, NY](https://www.linkedin.com/jobs/view/deployment-strategist-at-palantir-technologies-3658456177) - Posted 9:59:37 PM. A World-Changing CompanyPalantir builds the world’s leading software for data-dri...

13. [Deployment Strategist @ Palantir - Insights](https://www.reddit.com/r/cscareerquestions/comments/evt9ok/deployment_strategist_palantir_insights/)

14. [How Palantir Foundry Powers bp's Digital Transformation in Reliability](https://blog.palantir.com/how-palantir-foundry-powers-bps-digital-transformation-in-reliability-4c644e36b6fc) - An exploration of how Palantir's platform improves bp's production and operations reliability, with ...

15. [Palantir and bp Agree to 5-Year Strategic Relationship With New AI ...](https://www.businesswire.com/news/home/20240909534283/en/Palantir-and-bp-Agree-to-5-Year-Strategic-Relationship-With-New-AI-Capabilities) - The new contract will build on a decade of deep collaboration that has created a firm foundation for...

16. [Ontology Palantir - notes - follow the idea](https://publish.obsidian.md/followtheidea/Content/AI/Ontology+Palantir+-+notes) - 2025-05-09 Palantir Foundry Ontology: Unifying Data, Actions, and Models for Real-Time Business Tran...

17. [Palantir](https://www.palantir.com/docs/foundry/ontology) - The Palantir Ontology is an operational layer for the organization. The Ontology sits on top of the ...

18. [Generalizable entity resolution based on ontology structures](https://patents.google.com/patent/US20250165857A1/en?assignee=palantir&before=priority%3A20241231&after=priority%3A20240101&oq=assignee%3A%28palantir%29+2024) - The system is programmed to determine whether incoming records correspond to known entities within a...

19. [Foundry Entity Resolution - Palantir](https://www.palantir.com/foundry-entity-resolution/) - Seamlessly link records with AI to establish a reliable, de-duplicated data foundation, empowering r...

20. [Overview • Ontology](https://www.palantir.com/docs/foundry/ontology/overview) - The Palantir Ontology is an operational layer for the organization. The Ontology sits on top of the ...

21. [Question on how to balance governing a clean ontology and maximizing speed to value for end user work shop development.](https://www.reddit.com/r/palantir/comments/1ja0j54/question_on_how_to_balance_governing_a_clean/) - Question on how to balance governing a clean ontology and maximizing speed to value for end user wor...

22. [How to Design an Ontology in Palantir Foundry for Data ...](https://www.linkedin.com/posts/vikasteach_palantirfoundry-dataengineering-ontologydesign-activity-7386831965871763456-Rsrp) - 🚀 Ontology Design in Palantir Foundry — The Interview Favorite Question! If you’ve ever interviewed ...

23. [How to become a Palantir Champion: Organic vs. Assigned](https://www.linkedin.com/posts/connordeeks_can-a-palantir-champion-be-assigned-or-activity-7366517853270761473-c5AD) - Can a Palantir "champion" be assigned or does it have to be organic? We see instances where these in...

24. [Palantir Certifications Just Changed Everything (Why You Must Get In Early)](https://www.youtube.com/watch?v=2eCstIz--Pc) - Palantir just announced their official certification program — something the community has been wait...

25. [Palantir Certification Program Launched: Application Developer ...](https://www.linkedin.com/posts/orzen-ai_palantir-certifications-just-changed-everything-activity-7402552329050226689-xaZc) - New video just dropped. Palantir officially released its certification program — and this is a huge ...

26. [codestrap-programs/apprenticeships/foundry-public-certification-training/data-engineer.md at main · doriansmiley/codestrap-programs](https://github.com/doriansmiley/codestrap-programs/blob/main/apprenticeships/foundry-public-certification-training/data-engineer.md) - Curriculum for entering apprenticeships in software engineering. - doriansmiley/codestrap-programs

27. [Microsoft Word - Palantir Pricing (PF Price List).docx](https://notechfortyrants.org/wp-content/uploads/2020/06/Palantir-Pricing-Document.pdf)

28. [Palantir Embedded Further Into NHS By Offering FDP-Focused AI ...](http://unionsafety.eu/docs/HSNewsItems%202025/Nov/PalantirEmbeddedFurtherIntoNHSByOfferingFDRFocusedAIDataApprenticeshipsToNHSStaff.html) - Union Safety is the website of the North West BT Union Health and Safety Coordinators Committee and ...

29. [Become a certified Palantir Foundry engineer. - CodeStrap.me](https://codestrap.me/program/software-apprenticeship-programs-curriculum.html) - Learn Palantir Foundry. Help Reboot Western Economies with Software that Works!

30. [Accenture and Palantir Expand Global Strategic - Varindia](https://www.varindia.com/news/accenture-and-palantir-expand-global-strategic-partnership-to-drive-ai-reinvention) - Accenture and Palantir Technologies have formed the Accenture Palantir Business Group designed to ac...

31. [Palantir and Accenture Launch Global Business Group to Accelerate ...](https://www.beyondspx.com/quote/PLTR/news/palantir-and-accenture-launch-global-business-group-to-accelerate-enterprise-ai-deployment) - Palantir Technologies and Accenture announced the creation of a global Accenture‑Palantir Business G...

32. [Palantir and Lear announce five-year partnership expansion](https://telematicswire.net/palantir-and-lear-announce-five-year-partnership-expansion/) - Palantir Technologies Inc. , a provider of AI software, announced a five-year expansion of its partn...

33. [Palantir Technologies - Account Executive](https://jobs.lever.co/palantir/c98d8819-364e-450d-a96e-84b9061a7170) - The Role Palantir’s US Sales team targets and partners with some of the largest institutions in the ...

34. [Palantir Technologies hiring Account Executive in New York, NY | LinkedIn](https://www.linkedin.com/jobs/view/account-executive-at-palantir-technologies-3924914305) - Posted 4:47:03 PM. A World-Changing CompanyPalantir builds the world’s leading software for data-dri...

35. [Palantir Consumption-Based Pricing in AWS Marketplace 😲](https://www.reddit.com/r/PLTR/comments/wt9ob4/palantir_consumptionbased_pricing_in_aws/)

36. [Palantir Secures $10B Software Army Enterprise Agreement](https://www.govconwire.com/articles/palantir-army-enterprise-agreement-commercial-software-leo-garciga) - Palantir has secured an enterprise agreement, or EA, from the U.S. Army to provide commercial softwa...

37. [Palantir signs $10B enterprise agreement with Army](https://www.washingtontechnology.com/contracts/2025/08/palantir-signs-10b-enterprise-agreement-army/407153/) - The deal consolidates 75 contracts and seeks to drive more data analysis capabilities powered by art...

38. [PLTR employee: "Over 33% of my customers NEVER needed FDEs"](https://www.reddit.com/r/PLTR/comments/1ehgf8u/pltr_employee_over_33_of_my_customers_never/) - PLTR employee: "Over 33% of my customers NEVER needed FDEs"

39. [Inside Palantir: Wildly Different Value Prop for Customers](https://cloudwars.com/cloud-wars-minute/inside-palantir-wildly-different-value-prop-for-customers-growth/) - Our primary goal is to see growth within our customers in terms of their business outcomes, their ca...

40. [AI FDE • Overview - Palantir](https://palantir.com/docs/foundry/ai-fde/overview/) - AI FDE gives users complete authority and visibility over what information the model can access. In ...

41. [Palantir Extends Multi-Year Agreement with Airbus for Skywise Data ...](https://intellectia.ai/news/stock/palantir-extends-multiyear-agreement-with-airbus-for-skywise-data-platform)

42. [No Palantir in the NHS and Corporate Watch Reveal the Real Story ...](https://corporatewatch.org/foi-requests-reveal-palantirs-nhs-fdp-rollout-failures/) - According to NHS England (NHSE), by the end of June 2025, 130 trusts has signed a Memorandum of Unde...

43. [Does anyone have any in depth knowledge of why Home Depot and American Express dumped palantir in 2017?](https://www.reddit.com/r/PLTR/comments/n2osdw/does_anyone_have_any_in_depth_knowledge_of_why/) - Does anyone have any in depth knowledge of why Home Depot and American Express dumped palantir in 20...

44. [Palantir Shares Drop 2.75% Despite Extended Airbus Partnership ...](https://www.ainvest.com/news/palantir-shares-drop-2-75-extended-airbus-partnership-7-09b-volume-ranks-12th-2602/) - This “operational stickiness” is more valuable than short-term contract size, as it ensures long-ter...

45. [Does Databricks compete with Palantir? Or, are they offering solutions that can be implemented within the same organization?](https://www.reddit.com/r/databricks/comments/1bqqlo4/does_databricks_compete_with_palantir_or_are_they/) - Does Databricks compete with Palantir? Or, are they offering solutions that can be implemented withi...

46. [Palantir Apollo: Real-Time Deployment in Foundry](https://sstech.us/real-time-deployment-with-palantir-apollo/) - Learn how Palantir Apollo powers secure, real-time deployment across production environments with co...

47. [Apollo](https://www.palantir.com/assets/xrfr7uokpv1b/3B5KbQ9ujsiDCX4Tnfz3Hy/8d3ee9a6911665f036ce3d28c19cfa0d/PalantirApolloTechnicalWhitePaper.pdf)

48. [[PDF] Palantir Apollo —Solution Overview - Carahsoft](https://static.carahsoft.com/concrete/files/6616/8615/9340/Whitepaper_-_Palantir_Apollo_-_Solution_Overview.pdf)

49. [Administration • LLM capacity management - Palantir](https://palantir.com/docs/foundry/aip/llm-capacity-management/) - Palantir has set a certain maximum capacity for each enrollment, referred to as “enrollment-level ra...

50. [Palantir Foundry Comparison: Data Transformation vs Market Leaders](https://www.trackmind.com/palantir-foundry-data-transformation-market-comparison/) - Explore our Palantir Foundry comparison with Microsoft Fabric and Databricks, showing how Foundry tr...

51. [Databricks and Palantir: Picking the Right Path to Enterprise AI - SPR](https://spr.com/databricks-and-palantir-picking-the-right-path-to-enterprise-ai/) - Compare Databricks vs Palantir for enterprise AI, from governance and ontology to engineering flexib...

52. [Is Palantir's Valuation Sustainably Positioned for 2026? - AInvest](https://www.ainvest.com/news/palantir-valuation-sustainably-positioned-2026-2512/) - Is Palantir's Valuation Sustainably Positioned for 2026?

53. [Palantir's road to the Federated Data Platform contract: a timeline](https://www.digitalhealth.net/2023/11/palantirs-road-to-the-federated-data-platform-contract-a-timeline/) - NHSE's procurement for the Federated Data Platform and award of a £330m contract is story that has s...

54. [Palantir prolonge son accord pluriannuel avec Airbus pour la plateforme Skywise](https://fr.investing.com/news/company-news/palantir-prolonge-son-accord-pluriannuel-avec-airbus-pour-la-plateforme-skywise-93CH-3264794) - Restez informé des actus des entreprises qui ont un impact sur les principaux marchés boursiers. Déc...

55. [Palantir Extends Work to Power U.S. Army Vantage Program](https://www.businesswire.com/news/home/20231215388376/en/Palantir-Extends-Work-to-Power-U.S.-Army-Vantage-Program) - Palantir Technologies Inc. (NYSE: PLTR) today announced the extension of its pivotal partnership wit...

56. [Palantir's US Commercial, US Government, and International Government's Net Dollar Retention is one the highest in the world](https://www.reddit.com/r/PLTR/comments/t448ra/palantirs_us_commercial_us_government_and/)

57. [Is Palantir (PLTR) Expanding Its Client Base or Cashing In on Loyal Spenders?](https://finance.yahoo.com/news/palantir-pltr-expanding-client-cashing-114234380.html) - Palantir Technologies' (PLTR) sales are rising fast. The company's Q4 2024 revenue surged 36% year-o...

