# Palantir Product Demonstrations, Transcripts & Concrete Evidence Report

## Comprehensive Analysis of AIPCon Events (2023-2025), Earnings Calls, DevCon, and Customer Demos

---

## 1. AIPCon 1 (June 1, 2023) -- The AIP Launch Event

### Event Context
Palantir's inaugural AIPCon was publicly livestreamed on June 1, 2023. This was the first major public unveiling of the Artificial Intelligence Platform (AIP), which had been announced just weeks prior. The conference brought together C-suite executives from across Palantir's customer base, with 25+ customers participating.

### Shyam Sankar's 20-Minute AIP Capabilities Demo

CTO Shyam Sankar delivered the defining demonstration of the event -- a 20-minute live walkthrough of AIP's capabilities that revealed, for the first time, the concrete mechanics of how LLMs integrate with Foundry's ontology layer. The demo covered:

**"What You Say Is What You Get" -- Natural Language Data Integration:**
Sankar showed users could type natural language requests such as "give me all the claims from the West Midlands" in English, German, or Ukrainian, and AIP would automatically generate transform boards (data pipelines) for verification. The system could automatically connect ontologies with datasets when prompted -- this was the first public proof that Palantir had built a natural language interface layer over their data pipeline infrastructure.

**AIP Terminal (Command Line Interface):**
AIP's command line interface was demonstrated as a way to interact with enterprise knowledge and applications through LLMs. The primary scenario was a supply chain control tower: a user pasted email content about a distribution center disruption (a fictional "Velenor" distribution center) and asked questions about impacted inventory. The system calculated $13 million in revenue at risk and proposed reallocation actions. Sankar highlighted the time savings: "300 minutes to 3 minutes, with agents potentially solving in 3 seconds."

**Application Building via Natural Language:**
Users could request application scaffolding through natural language descriptions, receiving approximately 80% of the app structure automatically generated. Widgets for metrics like OTIF (On-Time In-Full) and monthly sales could be added. Functions were callable via webhook integrations to SAP and NetSuite, showing for the first time how AIP connected to existing ERP systems.

**AIP Logic IDE (First Public Showing):**
The demonstration revealed AIP Logic's IDE with:
- Chaining of multiple LLM logic blocks
- Tool access for operations like "reallocate product," "shortage KPI calculation," and "reallocable inventory" queries
- Full debugging with chain-of-thought visibility
- Production telemetry showing 5,000+ function runs with complete traces
- Unit test creation directly from production scenarios

**AI Agent Operations:**
Agents were shown automatically processing objects (emails triggering alerts), providing recommendations for human review, and operating within approval workflows. Live monitoring displayed agent performance metrics, historical data, and process views.

**"Leo" AI Copilot Preview:**
Sankar previewed "Leo," an AI copilot concept integrating ontology, agents, and logic directly into the platform interface, supporting proposal branching and production deployment workflows.

### Customer Presentations
Speakers and demo presenters included executives from Molson Coors, Cardinal Health, RBC, Lockheed Martin, PG&E, Tampa General Hospital, DISH Wireless, Siemens Healthineers, and PwC. Each showcased practical implementations of AIP across healthcare, retail, defense, and telecommunications.

**Source:** [Palantir AIP Capabilities Demonstration -- CTO Shyam Sankar at AIPCon (lilys.ai transcript)](https://lilys.ai/notes/157308), [Palantir First AIPCon Announcement](https://www.prnewswire.com/news-releases/palantir-announces-live-stream-of-its-first-aipcon-with-ai-demos--announcements-from-25-customers-301835283.html)

---

## 2. AIPCon 2 (September 14, 2023) -- Scaling AIP to 100+ Organizations

### Event Context
Just three months after launch, AIPCon 2 featured more than 30 organizations showcasing AIP use cases. Palantir reported AIP was already used by more than 100 organizations across energy, finance, hospitality, and healthcare -- achieved in under six months since the platform's introduction.

### Customer Keynotes and Master Classes

**CPKC (Canadian Pacific Kansas City):** Revealed that AIP was their chosen tool for real-time problem-solving and recommendations across their 20,000-mile rail network. This was significant as CPKC represented one of the first major infrastructure/logistics deployments at continental scale.

**HCA Healthcare:** Disclosed dramatic scaling metrics -- from 50 departments and 4 facilities using AIP on June 1st to 150 departments and 9 facilities by September, with a 2024 H1 target of 400 departments and 40 facilities. This demonstrated one of the fastest enterprise rollouts in Palantir's history.

**Eaton, Cintra, Miller's Ale House:** Delivered customer keynotes showing AIP in manufacturing, infrastructure management, and restaurant/hospitality operations respectively.

**Master Classes:** Intuit, the New York Stock Exchange, Cone Health, and Genpact offered hands-on master classes demonstrating AIP usage in financial services, healthcare operations, and professional services automation.

**Source:** [Palantir Customers to Feature AIP in Action at AIPCon](https://www.businesswire.com/news/home/20230907499815/en/Palantir-Customers-to-Feature-Artificial-Intelligence-Platform-in-Action-at-AIPCon-with-30-Presentations-and-Demos), [Palantir AIPCon September 2023 Livestream (LinkedIn)](https://www.linkedin.com/posts/palantir-technologies_aipcon-september-2023-livestream-activity-7107767402536296448-u_Ha)

---

## 3. AIPCon 3 (June 2024) -- The "Woodstock of AI"

### Event Context
The third AIPCon was held in June 2024 and drew approximately 70 customer presenters. CEO Alex Karp emphasized that none of these customers were paid to participate. The audience was roughly 40% existing customers and 60% prospective clients.

### Key Executive Quotes and Product Announcements

**Alex Karp on LLMs and Ontology:**
"In the end you have products, your business, chips and ontology. This is how you get things to work."
"LLMs are like genies of the lamp. AIP is the lamp that controls them."

These quotes crystallize Palantir's competitive thesis: LLMs without structured enterprise data (the ontology) cannot deliver operational value.

### Customer Demos (8 Keynotes)
- **AARP** -- Enterprise AI operations
- **SOMPO Japan** -- Insurance operations in Japan
- **NorthWind** -- Energy sector applications
- **Tampa General Hospital** -- Announced a $50 million, 7-year deal with Palantir during the event itself
- **Jacobs** -- Infrastructure engineering with mixed reality (MR) integration, where front-line engineers assess water plant health through MR glasses with AI-powered visual recommendations displayed in real-time
- **Fujitsu** -- Enterprise IT operations
- **Parexel** -- Pharmaceutical and life sciences
- **United Airlines** -- Airline operations optimization

### Product Feature Highlights

**AIP Evaluator (New Beta Tool):**
Demonstrated for the first time -- allows users to test how different LLMs perform across different tasks and select the optimal model for each use case with single-click deployment. Palantir showed its own internal use: screening candidate applications using AIP to process CVs and identify relevant qualifications.

**SwissRE Forensic Analysis Demo:**
A standout demonstration combining police forensic data with other sources to evaluate insurance claim validity using multi-modal workflows processing unstructured video and image data. A SwissRE representative stated: "I haven't seen another application that can do that. Foundry is the only application that integrates all the processes and closes the loop."

**BYOD (Bring Your Own Data) Live Session:**
Participants in the audience built a book recommendation engine prototype within minutes using AIP during a hands-on session.

**Demo Expo:**
An open-floor format where customers presented short demos of applications they had built with Foundry and AIP, showcasing real production systems.

**Source:** [The Woodstock of AI: Inside Palantir's AIPCon](https://www.palantirbullets.com/p/the-woodstock-of-ai-inside-palantirs), [AIPCon Demo Expo (Palantir Developer Community)](https://community.palantir.com/t/aipcon-demo-expo/338)

---

## 4. AIPCon 4 (September 12, 2024) -- 100+ Organizations, Government Firsts

### Event Context
AIPCon 4 was livestreamed on September 12, 2024, with more than 100 organizations participating. Several customers spoke publicly about their Palantir work for the first time.

### Notable First-Time Public Speakers
- **The National Geospatial-Intelligence Agency (NGA)** -- First public appearance discussing Palantir usage
- **Department of State** -- First public disclosure of AIP deployment
- **Aramark** -- Food services and facilities management
- **bp** -- Energy sector transformation
- **Anduril** -- Defense technology manufacturing
- **Trinity Industries** -- Rail and infrastructure
- **Lear** -- Automotive manufacturing
- **EllisDon** -- Construction management
- **L3Harris** -- Defense technology
- **Owens & Minor** -- Healthcare supply chain
- **Selkirk Sport** -- Consumer products (pickleball equipment)
- **DTN** -- Weather and agricultural intelligence
- **Associated Materials** -- Building products manufacturing

### Tyson Foods -- AIP + Ontology SDK for System Migration

Tyson Foods presented a detailed case study titled "AIP + Ontology SDK for System Migration Problem Solution" demonstrating how AIP and the Ontology SDK were used together to power a complex system migration. The workflow was powered by AIP Logic with GPT-4o, Automate, the Ontology, and the Ontology SDK -- one of the first public confirmations of specific LLM model usage within AIP.

**Source:** [AIPCon 4 Customer Demos (Palantir)](https://www.palantir.com/aipcon4/demos/), [Palantir Reveals New Wave of Customers at AIPCon](https://www.businesswire.com/news/home/20240911139840/en/Palantir-Reveals-New-Wave-of-Customers-in-Action-at-AIPCon), [Tyson Demo PDF](https://www.palantir.com/assets/xrfr7uokpv1b/5GVfxqOkUJ3ZaOGza5G7nM/4257c0eb78ce1a765f5efb25d6f6844a/AIPCon_US_Sep_24_-_Demo_Expo_-_Tyson.pdf)

---

## 5. AIPCon 6 (March 13, 2025) -- Warp Speed and Manufacturing OS

### Event Context
The sixth AIPCon featured 100+ organizations, with over a dozen partners showing real-time outcomes. Several major new customer relationships were revealed for the first time.

### New Customer Announcements
Heineken, Walgreens, R1 RCM, RaceTrac, and Ripcord were publicly revealed as Palantir customers for the first time.

### Warp Speed Manufacturing OS Demonstrations

The defining product story of AIPCon 6 was Warp Speed, Palantir's manufacturing operating system under the Arsenal OS platform. Warp Speed was positioned as a tool for "re-industrializing American manufacturing."

**Anduril Industries** made the case that Warp Speed enhanced their material resource planning by 200x -- a staggering claim for manufacturing efficiency. Anduril was the first company to use the Warp Speed operating system in production.

**Warp Speed Inaugural Cohort Members:**
- Anduril Industries
- L3Harris
- Panasonic Energy of North America (PENA)
- Shield AI
- Red Cat, Saildrone, Saronic, SNC, Ursa Major (second wave)

Warp Speed powers workflows including dynamic material resource planning, phasing in new configurations efficiently, and reducing material and labor variances.

### Other Customer Speakers
AT&T, TWG Global, Lennar, KKR, Owens Corning, Delta Air Lines, L3Harris, Parexel, Wendy's QSCC, JD Power, and Memorial Sloan Kettering Cancer Center.

**Source:** [Palantir's Latest Wave of Customers Take Center Stage at AIPCon](https://www.businesswire.com/news/home/20250311129099/en/Palantirs-Latest-Wave-of-Customers-Take-Center-Stage-at-AIPCon), [Palantir AIPCon 6 on X](https://x.com/PalantirTech/status/1899553733584794106), [Warp Speed Inaugural Cohort](https://www.businesswire.com/news/home/20241211204864/en/Palantirs-Inaugural-Warp-Speed-Cohort-to-Power-Manufacturing-and-Production-Capabilities-Through-Advanced-AI-Technology)

---

## 6. AIPCon 7 (June 2025) & AIPCon 8 (September 4, 2025) -- Enterprise AI at Scale

### AIPCon 7 (June 2025)
AIPCon 7 was held in June 2025 with continued expansion of the customer presentation roster, though detailed public summaries are less available.

### AIPCon 8 (September 4, 2025) -- 70+ Speakers

AIPCon 8 featured 70+ speakers from across Palantir's U.S. commercial customer base. Featured customers included:
- **American Airlines** -- Fleet optimization
- **bp** -- Energy operations
- **Lumen** -- Telecommunications
- **MaineHealth** -- Healthcare delivery
- **Novartis** -- Pharmaceutical R&D
- **The Nuclear Company** -- Nuclear energy
- **TWG Motorsports** -- Motorsport operations
- **Waste Management** -- Environmental services

The customer base showed how they are using Foundry and AIP for: "winning the nuclear power race against China, accelerating pharmaceutical R&D, managing complex responses to natural disasters, optimizing large-scale fleets, invigorating American manufacturing, and delivering the right care to the right patient at the right time."

### AIPCon 8 Demo Details (Blog Series)

Palantir published a two-part blog series documenting standout demos from AIPCon 8:

**Part 1 -- Enterprise AI Redefined (Healthcare, Retail, Defense):**

**Nebraska Medicine (Healthcare):**
Jana Danielson, VP of Revenue Cycle Management, showcased the Guideline Evaluation workflow -- a breakthrough solution built in partnership with Palantir in just 10 hours. The automated solution performs comprehensive analysis of patient medical records and billing information, cross-referencing clinical data points against dynamic insurance company requirements to identify the most accurate diagnostic codes and maximize reimbursement potential. This workflow leverages Nebraska Medicine's unified Ontology infrastructure, which consolidates operations across patient flow management, nurse allocation systems, clinical supplies management, and revenue cycle operations. Their partnership, which began in January 2024, rapidly scaled from a single use case to a comprehensive enterprise deployment encompassing 20+ distinct use cases within six months.

**Part 2 -- Transforming Manufacturing, Insurance, and Construction:**

**Ursa Major Technologies (Manufacturing):**
Nancy Cable, Director of Operations, unveiled their transformation from legacy low-tech processes to an AI-native, Ontology-driven Manufacturing Execution System (MES) called "Warp Speed." The system converts static documentation into dynamic, interactive operational tools that error-proof and automate complex workflows -- a concrete demonstration of manufacturing digitization through Palantir.

**Automated Insurance Underwriting (Insurance):**
A demo showed automated insurance underwriting that accelerates complex aerospace coverage decisions using AI agents to process multiple data streams simultaneously.

**Thomas Cavanagh Construction (Construction):**
Established Foundry as their central operating system, creating scalable construction operations that accommodate business growth without proportional increases in operational complexity. Described as setting "new benchmarks for integrated construction management platforms."

**Source:** [Inside the AIPCon 8 Demos Redefining Enterprise AI (Palantir Blog)](https://blog.palantir.com/inside-the-aipcon-8-demos-redefining-the-future-of-enterprise-ai-a0a740fe44ce), [Inside the AIPCon 8 Demos Transforming Manufacturing, Insurance, and Construction (Palantir Blog)](https://blog.palantir.com/inside-the-aipcon-8-demos-transforming-manufacturing-insurance-and-construction-2ef01d53ea96), [AIPCon 8 Announcement](https://www.businesswire.com/news/home/20250904025905/en/A-New-Set-of-Palantir-Customers-Takes-the-Spotlight-at-AIPCon-8)

---

## 7. Earnings Call Transcripts -- Key Quotes and Context

### Q1 2024 Earnings Call -- Bootcamp Velocity

**Bootcamp Scale:**
Palantir reported sustained high volume of bootcamps with over 915 organizations participating to date.

**Customer Conversion Examples (Ryan Taylor):**
- A leading utility company signed a seven-figure deal just five days after completing the bootcamp
- Another customer immediately signed a paid engagement after just one day of their multi-day bootcamp, then converted to a seven-figure deal three weeks later

### Q2 2024 Earnings Call -- Prototype to Production

**Bootcamp to Deal Timelines (Ryan Taylor):**
- A large wholesale insurance brokerage firm closed a seven-figure ACV deal just 16 days after the bootcamp
- A leading convenience store chain went from prototype out of bootcamp to paid pilot in 25 days, then converted the inventory management and pricing optimization use case into initial production immediately following the pilot
- By June 2024, more than 1,300 AIP Bootcamps had been completed worldwide

**Key Framing:**
"Bootcamps remain a key go-to-market motion, particularly for prototyping what is possible with AI, but the real opportunity and our unique capability lies in moving from prototype to production with these customers."

**Source:** [Palantir Q2 2024 Earnings Call Transcript (Motley Fool)](https://www.fool.com/earnings/call-transcripts/2024/08/05/palantir-technologies-pltr-q2-2024-earnings-call-t/)

### Q3 2024 Earnings Call -- "78 AI Agents" and Military Scaling

**Shyam Sankar on Insurance Automation:**
"We automated the insurance underwriting process for one of America's largest and most well-known insurers with 78 AI agents, taking a process that took two weeks to 3 hours."

This was contextualized as providing "an asymmetrical advantage in the marketplace to buying contracts before the competition has even gotten through 15% of their process."

**Shyam Sankar on Military Targeting (Maven Smart System):**
"The entire targeting and fires process can be done in Maven with 20 people. It used to take 2,000."

**Ryan Taylor on Bootcamp Conversions:**
- "A bottled water manufacturer, a specialty pharmaceutical company and an agricultural software provider all signed seven-figure ACV deals less than two months after their initial bootcamps"
- "A large American equipment rental company expanded its work with us less than eight months after converting to an enterprise agreement, increasing the account ARR 12-fold"

**Alex Karp on Customer Impact:**
"Trinity Rail -- it took just three months to get to a functional workflow with a $30 million impact to its bottom line."

**Shyam Sankar on Ontology's Role:**
"That differentiation starts with the ontology. Using the ontology to drive AIP across these applications."

**Source:** [Palantir Q3 2024 Earnings Call Transcript (Motley Fool)](https://www.fool.com/earnings/call-transcripts/2026/02/03/palantir-pltr-q3-2024-earnings-call-transcript/)

### Q4 2024 Earnings Call -- Operational Speed

**Shyam Sankar on Speed:**
"What used to take five days now takes three minutes" (regarding multinational bank back-office automation).

"Replacing months of arduous manual reviews with AI labor that can flag major risks to engineers in minutes."

"That is a 100-hour process for human engineers, now automated and serving up exceptions for human review."

**Alex Karp on Enterprise Ontology:**
"We're exporting our culture and way of doing things to enterprises... by allowing enterprises to capture their tribal knowledge in a way that they can utilize LLMs."

**Source:** [Palantir Q4 2024 Earnings Call Transcript (Motley Fool)](https://www.fool.com/earnings/call-transcripts/2025/02/04/palantir-technologies-pltr-q4-2024-earnings-call-t/), [Q4 2024 Letter to Shareholders](https://www.palantir.com/q4-2024-letter/en/)

### Q1 2025 Earnings Call -- Ontology as AI Demand Infrastructure

**Shyam Sankar:**
"AIP is proving to be the best harness to build, test, evaluate, and deploy agents to eat the elephant of the enterprise."

"The market has been focused on AI supply -- the models -- while we have been focused on delivering on AI demand."

"Our foundational investments in ontology and infrastructure have positioned us to uniquely deliver on AI demand now and into the world ahead."

### Q2 2025 Earnings Call -- AIFDE First Public Discussion

**Shyam Sankar defining AIFDE:**
"AI FDE is designed to enable autonomous execution across a wide array of tasks, including creating and editing ontology, building data transforms, creating functions, debugging issues and building applications."

"With its own closed-loop error handling, AI FDE can identify and correct issues and notify human users if needed."

**Shyam Sankar on Ontology Necessity:**
"Realizing value from AI in the enterprise requires the seamless integration of LLMs, workflow and software, and that's only possible with ontology."

**Ryan Taylor on Customer Impact Examples:**
- "A healthcare company completed a bootcamp in April, then signed an $88 million TCV deal a month later to coordinate and automate patient care across facilities"
- Citibank: customer onboarding process "once took them 9 days, now takes seconds"
- Fannie Mae: decreased mortgage fraud detection time "from 2 months down to seconds"
- Nebraska Medicine: "2,100% increase in discharge lounge utilization"

**Ryan Taylor:**
"Our ontology is pure understanding, concretized in software. This is reality, not rhetoric."
"LLMs simply don't work in the real world without Palantir."

**Source:** [Palantir Q2 2025 Earnings Call Transcript (Motley Fool)](https://www.fool.com/earnings/call-transcripts/2026/02/03/palantir-pltr-q2-2025-earnings-call-transcript/)

### Q3 2025 Earnings Call -- "Army of AI FTEs" (The Defining Quote)

**Shyam Sankar on AIFDE (Full Context):**
"AIFDE, our AIP-native development agent that understands how to connect to data sources, how to integrate and transform data, how to create ontologies and functions, and build applications, is unleashing incredible speed and productivity for our FTEs and customer developers alike."

**The "Army of AI FTEs" Quote (Full Context):**
"At one customer, two human FTEs spawned an army of AI FTEs to migrate a customer off their legacy data warehouse in five days, something that would have taken an army of SIs [system integrators] up to two years. This is not a prototype. This is production."

**Sankar on Productivity Metrics:**
"Our headcount has grown roughly 10%, but revenue grew 63%. How are we doing that? We've made our FTEs wildly more productive."

**Alex Karp on Tribal Knowledge and AIFDE:**
"We put in AIFDE, we orchestrated an ontology, we take the tribal understanding of their business, the specific nature of their business that makes them particular and valuable and lethal, and we empower that."

**Shyam Sankar on FDE Philosophy:**
"We build software that works, not software that ought to. We build software for the world as it exists, not a world that never was. And this ability to find what's true -- that comes from the FDE."

**Ryan Taylor on Customer Expansion:**
- "A leading medical device manufacturer signed a multi-year expansion just five months after their initial contract, increasing ACV more than eightfold. Two weeks into their initial contract, the conversation evolved from a single use case to pursuing the opportunity of becoming an AI-first enterprise."
- "At a leading insurance company, the CEO has taken personal ownership of their AI transformation, meeting with our team regularly to orchestrate a company-wide transformation around AIP, reimagining every function, from underwriting to claims processing."

**Alex Karp on Value Creation:**
"Unlike seemingly in the most obvious way, we are downstream from the value creation. The reason why that's working is because we are making our clients more money or we're making them more dominant on the battlefield, and they're paying us a subset of that."

**Source:** [Palantir Q3 2025 Earnings Call Transcript (Motley Fool)](https://www.fool.com/earnings/call-transcripts/2025/11/04/palantir-pltr-q3-2025-earnings-call-transcript/)

### Q4 2025 Earnings Call (February 2026) -- SAP Migrations in Two Weeks

**Shyam Sankar (The SAP Quote in Full):**
"AIFDE is now capable of powering complex SAP ERP migrations from ECC to S/4. Years of work now done in as little as two weeks."

"We are generalizing AIFDE to do this for a broader and broader set of problems at our customers."

"AIFDE and OSDK have unleashed pro-code builders in our platforms. We serve over 1 billion API gateway requests a week from applications built by customers on top of AIP."

**Ryan Taylor on Deal Velocity:**
- "A healthcare company completed two bootcamps with us last summer and signed a $96 million deal with us before the end of the year"
- "An engineering services company saw a series of demos in the fall then signed an $80 million deal before year-end"
- "A utility company expanded from $7 million ACV in Q1 2025 to $31 million ACV by year-end"
- "An energy company expanded from $4 million ACV in Q1 2025 to over $20 million ACV by year-end"

**Ryan Taylor:**
"Speed to production and transformational scale is no longer optional; it's existential."

**Alex Karp:**
"AI has just put gasoline on all the tribal knowledge we have in our products."

**Source:** [Palantir Q4 2025 Earnings Call Transcript (Motley Fool)](https://www.fool.com/earnings/call-transcripts/2026/02/02/palantir-pltr-q4-2025-earnings-call-transcript/)

---

## 8. DevCon -- Palantir Developer Conference Series

### DevCon 1 (November 13-14, 2024) -- The Inaugural Developer Conference

Palantir held its first developer conference, bringing together 150 of the most ambitious commercial and government builders and technical leaders for two days of product launches, hands-on development, and competition.

**Major Product Releases:**
- **Ontology SDK 2.0** -- Complete rewrite of the developer toolkit for building applications on top of the Ontology
- **New Platform APIs** -- Expanded programmatic access to Foundry capabilities
- **Workflow Builder** -- A new application for building, debugging, and managing workflows. Users add Ontology resources (objects, LLMs, models, actions, functions, and applications) to a graph and expand to other resources with logical references. Graphs are autogenerated from any Workshop application (CMD+i on macOS / Ctrl+i on Windows)
- **Enhanced language expansiveness** -- Broader programming language support for OSDK

**Beta Products (Early Access):**
- **Agent Studio** -- Environment for building, testing, and deploying AI agents
- **Platform Branching** -- Git-like branching for Foundry platform resources
- **Compute Modules** -- Extensible compute infrastructure
- **Multi-Modal Data Plane** -- Private launch for technical leaders (multi-modal AI capabilities)

**Shyam Sankar Quote:**
"By deprecating backend development, AIP enables customers to focus on delivering value faster." Lennar (homebuilder) shared that they are "building 50x faster on AIP."

**Source:** [Palantir Launches AIP for Developers at DevCon](https://www.businesswire.com/news/home/20241115105189/en/Palantir-Launches-AIP-for-Developers-at-DevCon), [DevCon Event Page](https://www.palantir.com/devcon/)

### DevCon 2 & DevCon 3 (2025)
DevCon 2 followed the inaugural event. DevCon 3 was announced as an exclusive developer event in the Bay Area in late June 2025, where finalists take part in new product launches, hands-on workshops with Palantir product leads, and continue to build upon their projects. DevCon 4 is also listed on Palantir's website.

**Source:** [Palantir DevCon2](https://www.palantir.com/devcon/dc2/), [Palantir DevCon3](https://www.palantir.com/devcon3/), [Palantir DevCon4](https://www.palantir.com/devcon4/)

---

## 9. Key Customer Demo Videos and Case Studies

### Airbus / Skywise -- The Longest-Running Foundry Deployment

Airbus has been using Foundry since 2017 through Skywise, their aviation data platform. Key facts:
- 140+ airlines and 11,900+ aircraft connected
- Covers 50% of Airbus's in-service fleet worldwide
- Generates network effects and provides data feedback loop for future aircraft design

**Concrete Use Case:** Airbus engineers used Skywise to investigate a series of leaking high-pressure valves on the A330neo fleet. By analyzing vast amounts of operational and sensor data from across the connected fleet, they identified a software flaw and proactively issued an emergency Airworthiness Directive -- demonstrating Foundry's ability to surface patterns invisible in isolated datasets.

**Source:** [Palantir-Airbus Partnership Overview](https://www.palantir.com/assets/xrfr7uokpv1b/7uEHPTEM0MkKtBFcx2zh63/9d75da5b76439717ac95135b5012479e/Palantir-Airbus-Partnership_Overview.pdf)

### NHS / UK Healthcare -- COVID-19 and Beyond

Foundry served as the backbone for what has been called the NHS's "biggest ever exercise in operational data integration," providing a single source of truth for the vaccination rollout -- from vaccine supply locations to who had been vaccinated and where uptake was low. Foundry powered aspects of the GOV.UK Coronavirus Dashboard.

**Source:** [Palantir UK Healthcare](https://www.palantir.com/uk/healthcare/), [Written Evidence to UK Parliament (PDF)](https://committees.parliament.uk/writtenevidence/107376/pdf/)

### US Army -- Maven Smart System and TITAN

**Maven Smart System (MSS):**
- Initial $480M five-year IDIQ contract signed May 2024
- Contract ceiling increased by $795M to over $1 billion
- Subsequently expanded to a $10 billion Army contract in August 2025
- 20,000+ active Maven users across 35+ military service and combatant command software tools in three security domains
- User base more than doubled since January 2024
- Covers five combatant commands: CENTCOM, EUCOM, INDOPACOM, NORTHCOM/NORAD, and TRANSCOM
- Supports AI-enabled battlespace awareness, global integration, force management, contested logistics, joint fires and targeting

The comparison quoted by Sankar in earnings calls: "The 18th Airborne can now match the performance of what used to be a 2,000-staff targeting cell during Operation Iraqi Freedom with a targeting cell of roughly only 20 people today."

**TITAN (Tactical Intelligence Targeting Access Node):**
Awarded to Palantir on March 6, 2024. TITAN is the Army's first AI-defined vehicle and next-generation intelligence ground station, consisting of mobile ground stations mounted on trucks that harness AI to collect data from space sensors for warfare strategy and strike targeting. The contract provides for 10 TITAN systems delivered in stages.

**Source:** [Palantir TITAN](https://www.palantir.com/titan/), [Maven $480M Contract (DefenseScoop)](https://defensescoop.com/2024/05/29/palantir-480-million-army-contract-maven-smart-system-artificial-intelligence/), [Maven Contract Increase (DefenseScoop)](https://defensescoop.com/2025/05/23/dod-palantir-maven-smart-system-contract-increase/)

---

## 10. AIFDE -- AI Forward Deployed Engineer (Product Deep Dive)

### Official Capabilities (from Palantir Documentation)

AIFDE translates natural language requests into Foundry operations. Its documented capabilities include:

**Data Integration & Transformation:**
- Connect to data sources
- Integrate and transform data via natural language commands
- Build and maintain data pipelines

**Ontology Development:**
- Create and modify object types
- Define link types between objects
- Configure action types for data editing workflows
- Implement interfaces for consistent object modeling

**Function Creation:**
- Write and preview functions
- Publish new function tags
- Debug issues autonomously

**Application Building:**
- Build Workshop applications
- Configure widgets and layouts

**Safety Architecture:**
- Uses branching by default across all workflows
- Proposes changes in Foundry branch proposals or Code Repository pull requests for human review
- Closed-loop error handling: identifies and corrects issues, notifies humans if needed

**Model Support:**
First-class support for Anthropic, OpenAI, Google, and xAI models along with native tool APIs.

### The Strategic Arc (Earnings Call Evolution)

1. **Q2 2025:** AIFDE introduced as "designed to enable autonomous execution across a wide array of tasks"
2. **Q3 2025:** "At one customer, two human FTEs spawned an army of AI FTEs to migrate a customer off their legacy data warehouse in five days"
3. **Q4 2025:** "AIFDE is now capable of powering complex SAP ERP migrations from ECC to S/4. Years of work now done in as little as two weeks"

This progression shows AIFDE evolving from a general productivity tool to a system capable of replacing entire multi-year enterprise consulting projects.

**Source:** [AI FDE Overview (Palantir Docs)](https://www.palantir.com/docs/foundry/ai-fde/overview), [November 2025 Announcements](https://www.palantir.com/docs/foundry/announcements/2025-11)

---

## 11. AIP Logic -- Concrete Product Capabilities

### What AIP Logic Actually Does (from Documentation)

AIP Logic is a no-code development environment for building, testing, and releasing functions powered by LLMs. Key documented mechanics:

**Block-Based Architecture:**
Functions are composed of blocks -- create variable, apply action, execute function, use LLM. The "Use LLM" block is the core element, where builders engineer prompts, define tools, and specify outputs.

**Three Categories of Ontology-Driven Tools:**
1. **Data tools** -- Query and retrieve Ontology data for LLM context
2. **Logic tools** -- Execute logical operations and functions
3. **Action tools** -- Safely take actions that write back to the Ontology

**Testing & Debugging:**
Running a function opens the Debugger panel showing the LLM chain-of-thought (CoT) for each block. Production telemetry allows monitoring of function runs with complete traces.

**Deployment:**
Functions can be exposed through Workshop applications (via AIP Interactive widget), triggered via Automate (event-driven execution), or called through the Ontology SDK from external applications.

**Source:** [AIP Logic Overview (Palantir Docs)](https://www.palantir.com/docs/foundry/logic/overview), [AIP Logic Getting Started](https://www.palantir.com/docs/foundry/logic/getting-started), [AIP Logic Blocks](https://www.palantir.com/docs/foundry/logic/blocks)

---

## 12. Apollo -- Continuous Delivery Platform

### Concrete Capabilities

Apollo manages the deployment, security, and upgrades for Palantir's software across 300+ unique environments, including 500+ independently-released microservices.

**Key Features Demonstrated:**
- Autonomous safe deployment with staged blue-green upgrades
- Automatic rollback upon detecting emergent issues
- Software Catalog for tracking all production software, versions, and dependencies
- Dashboard and forms for intent-based deployment (no YAML editing required)
- Works across public cloud, private cloud, air-gapped, and edge environments

**Apollo Demo Day (April 2022):**
Palantir held a dedicated Apollo Demo Day in April 2022 showcasing new products and capabilities within the continuous delivery platform.

**Source:** [Palantir Apollo](https://www.palantir.com/platforms/apollo/), [Apollo Blog Post](https://blog.palantir.com/palantir-apollo-powering-saas-where-no-saas-has-gone-before-7be3e565c379), [Apollo Demo Day Announcement](https://www.businesswire.com/news/home/20220427005106/en/Palantir-Showcases-Series-of-New-Products-at-Apollo-Demo-Day)

---

## 13. Palantir 2021 Demo Day -- Historical Foundry/Gotham/Apollo Showcase

The inaugural Demo Day (January 26, 2021) was the first time Palantir publicly demonstrated its platforms in detail. Full English transcript is publicly available.

**Products Demonstrated:**
- Software-Defined Data Integration (SDDI)
- Low-Code/No-Code Environments
- Archetypes (reusable application patterns)
- AI-Enabled Mission Command
- Apollo continuous delivery across all environments

This event predates AIP but established the pattern of public product demonstrations that evolved into the AIPCon format.

**Source:** [English Transcript (PDF)](https://s26.q4cdn.com/381064750/files/doc_downloads/2021/English-Transcript-Q1-2021-Palantir-Demo-Day.pdf), [Demo Day Announcement](https://www.businesswire.com/news/home/20210121005276/en/Palantir-Issues-Additional-Details-Regarding-its-Inaugural-Demo-Day-on-January-26-2021)

---

## Summary: The Evidence Timeline

| Period | Key Milestone | Evidence Type |
|--------|--------------|---------------|
| Jan 2021 | First Demo Day -- Foundry/Gotham/Apollo publicly shown | Full transcript available (PDF) |
| Jun 2023 | AIPCon 1 -- AIP launched with 20-min Sankar demo | Transcript available (lilys.ai) |
| Sep 2023 | AIPCon 2 -- 100+ orgs using AIP; HCA scaling 3x in 3 months | Press releases |
| Jun 2024 | AIPCon 3 -- 70 customers demo; AIP Evaluator launched; Tampa General $50M deal | Blog, community forum |
| Sep 2024 | AIPCon 4 -- NGA, Dept of State first public appearances; Tyson OSDK migration demo | Demo page, PDF |
| Nov 2024 | DevCon 1 -- OSDK 2.0, Workflow Builder, Agent Studio (beta) launched | Press release |
| Mar 2025 | AIPCon 6 -- Warp Speed manufacturing OS; Anduril 200x MRP improvement | Press release |
| Jun 2025 | AIPCon 7 + DevCon 3 | Event pages |
| Sep 2025 | AIPCon 8 -- Nebraska Medicine 10-hour build; Ursa Major MES | Blog series |
| Q3 2024 | "78 AI agents... two weeks to 3 hours" | Earnings transcript |
| Q3 2025 | "Army of AI FTEs... five days... would have taken two years" | Earnings transcript |
| Q4 2025 | "SAP ERP migrations... as little as two weeks" | Earnings transcript |
| Q4 2025 | "$96M healthcare deal from bootcamp"; "1 billion API requests/week" | Earnings transcript |

---

## Key Analytical Takeaways

1. **Progressive Revelation Strategy:** Palantir has methodically increased product transparency from 2021 to 2025. The 2021 Demo Day showed Foundry at a high level; by AIPCon 8 in 2025, specific customers are showing specific applications built in specific timeframes (10 hours for Nebraska Medicine).

2. **Bootcamp-to-Production Pipeline is Quantified:** The earnings calls provide concrete data -- 915+ organizations through bootcamps by Q1 2024, 1,300+ by mid-2024. Conversion timelines range from 5 days (utility company) to 25 days (convenience store) to 2 months (pharma, agriculture, water companies).

3. **AIFDE is the Inflection Point:** The progression from Q2 2025 (introduction) to Q4 2025 (SAP migrations in two weeks) represents a fundamental shift in Palantir's value proposition -- from "we deploy FDEs who build your system" to "we deploy AI FDEs that build your system with minimal human intervention."

4. **Customer Scale is Verifiable:** Specific customers at specific events making specific claims (HCA Healthcare scaling from 50 to 400 departments, Trinity Rail $30M impact in 3 months, Anduril 200x MRP improvement) provide concrete evidence points that can be cross-referenced.

5. **The Ontology Thesis is Consistent:** From Karp's "LLMs are genies, AIP is the lamp" to Sankar's "that differentiation starts with the ontology" to Taylor's "our ontology is pure understanding, concretized in software" -- the messaging has been remarkably consistent and is now backed by AIFDE's ability to autonomously build ontologies from natural language.
