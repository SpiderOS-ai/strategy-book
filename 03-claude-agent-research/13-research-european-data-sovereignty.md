# European Data Sovereignty: Implementation Guide for Spider's French/EU Go-to-Market

*Research compiled: February 2026*

---

## Table of Contents

1. [SecNumCloud 3.2 in Practice](#1-secnumcloud-32-in-practice)
2. [GDPR Operational Requirements for a Data Platform](#2-gdpr-operational-requirements-for-a-data-platform)
3. [EU AI Act Practical Compliance](#3-eu-ai-act-practical-compliance)
4. [Mistral AI Integration](#4-mistral-ai-integration)
5. [French/EU SaaS Compliance Landscape](#5-frencheu-saas-compliance-landscape)
6. [Sovereign Cloud Pricing](#6-sovereign-cloud-pricing)
7. [Strategic Implications for Spider](#7-strategic-implications-for-spider)

---

## 1. SecNumCloud 3.2 in Practice

### 1.1 What SecNumCloud 3.2 Actually Requires

SecNumCloud is the qualification framework maintained by ANSSI (Agence Nationale de la Securite des Systemes d'Information), France's national cybersecurity agency. Version 3.2 is the most stringent cloud security standard in Europe, encompassing **more than 360 compliance criteria across 14 thematic areas** covering organizational, technical, operational, and legal security.

**Core requirements include:**

- **Data localization**: All data and backups must be hosted within the European Union, with primary infrastructure on French territory.
- **European legal entity**: The cloud service provider must be established in Europe and must not be subject to extraterritorial laws such as the US CLOUD Act, FISA Section 702, or equivalent non-European legislation.
- **Personnel restrictions**: Administration and operation must be carried out by employees located in the EU who are subject to European law.
- **Immunity from extraterritorial laws**: This is the critical differentiator from ISO 27001 -- SecNumCloud 3.2 explicitly requires protection from foreign government data access requests. This is why no US hyperscaler (AWS, Azure, GCP) has obtained the qualification directly.
- **ISO 27001 as baseline**: SecNumCloud builds on ISO 27001 but adds prescriptive obligations including security guides, partitioning, MFA, encryption, PASSI audits (penetration testing by ANSSI-certified auditors), and data localization.
- **Six audit categories**: The 360+ requirements are divided across organizational security, physical security, network security, system security, application security, and legal/governance requirements.

**The qualification process follows four milestones:**

| Milestone | Description |
|-----------|-------------|
| **J0** | Acceptance of the qualification request by ANSSI |
| **J1** | Acceptance of the evaluation strategy |
| **J2** | Evaluation phase (independent audits by PASSI-certified auditors) |
| **J3** | Qualification decision by ANSSI |

Sources: [Scalingo SecNumCloud Guide](https://scalingo.com/blog/secnumcloud-qualification-anssi-guide), [Feel Agile Complete Guide](https://www.feelagile.com/en/guide/guide-secnumcloud), [Cloud Temple SecNumCloud 3.2](https://www.cloud-temple.com/en/secnumcloud-3-2-strengthening-security-and-legal-sovereignty-in-the-cloud/)

### 1.2 Who Has SecNumCloud Qualification Today

As of February 2026, the qualified providers are:

| Provider | Service | Version | Qualification Expiry | Type |
|----------|---------|---------|---------------------|------|
| **3DS Outscale** | Cloud on Demand | **3.2** | 30/11/2026 | IaaS |
| **OVHcloud** | Private Cloud (VMware) | 3.1 | Originally 12/2023, renewed | IaaS |
| **OVHcloud** | Bare Metal Pod | **3.2** | 2028 (qualified 03/2025) | IaaS |
| **S3NS** (Thales/Google) | PREMI3NS | **3.2** | 12/2028 (qualified 12/2025) | IaaS/PaaS/CaaS |
| **Cloud Temple** | Secure Temple | 3.1 | 03/2025 (renewal pending) | IaaS |
| **Oodrive** | Work, Meet, Share | 3.1 | 01/2025 (renewal pending) | SaaS |
| **Worldline** | Cloud Services Secured | 3.1 | 10/2024 (renewal pending) | IaaS |
| **Cegedim.cloud** | CegNumCloud Secured | 3.1 | Active | IaaS |
| **Whaller** | DONJON | 3.1 | Active | SaaS |
| **Orange Business** | Cloud Avenue | 3.1 | Active | IaaS |

**Providers actively pursuing qualification (not yet qualified):**

- **Scaleway**: Passed J0 milestone, targeting qualification by end of 2025/early 2026. Aiming to be the first SecNumCloud-qualified PaaS.
- **NumSpot** (Docaposte/Dassault/Bouygues): SecNumCloud application submitted September 2024. Currently ISO 27001 certified, pursuing SecNumCloud and HDS certifications.
- **Bleu SAS** (Orange + Capgemini): "Cloud de Confiance" targeting qualification first half of 2026.
- **Microsoft** (via Bleu): Targeting SecNumCloud 3.2 for Azure services through the Bleu SAS entity.

Sources: [ANSSI Official List](https://cyber.gouv.fr/produits-services-qualifies), [S3NS Qualification Announcement](https://www.thalesgroup.com/en/news-centre/press-releases/s3ns-announces-secnumcloud-qualification-premi3ns-its-trusted-cloud), [OVHcloud SecNumCloud](https://www.ovhcloud.com/en/compliance/secnumcloud/), [Outscale First 3.2](https://www.3ds.com/newsroom/press-releases/outscale-first-cloud-qualified-secnumcloud-32)

### 1.3 Duration and Cost of Certification

**Duration**: The qualification process typically takes **18 to 36 months** from initial application (J0) to qualification decision (J3). Scaleway, for example, began its process in 2024 and targets completion in late 2025/2026. S3NS passed all three milestones over approximately 24 months.

**Cost**: ANSSI does not publish official costs. Industry estimates place the total investment at:

- **Preparation and documentation**: EUR 500K--2M+ depending on baseline security posture
- **PASSI audit costs**: EUR 200K--500K for independent penetration testing and security audits
- **Ongoing compliance**: Significant annual costs for maintaining qualification (surveillance audits, continuous monitoring)
- **Infrastructure investment**: Physical isolation, dedicated networks, personnel training

The qualification is valid for **3 years**, with mandatory surveillance audits. Renewal requires demonstrating continued compliance. ANSSI rejects any request if an incident or weakness in the security system is discovered.

Sources: [Scalingo Guide](https://scalingo.com/blog/secnumcloud-qualification-anssi-guide), [Oodrive SecNumCloud](https://www.oodrive.com/blog/security/secnumcloud-the-certification-for-cloud-confidence-service-providers/), [Wimi SecNumCloud Overview](https://www.wimi-teamwork.com/en/blog/cybersecurity/all-about-secnumcloud)

### 1.4 Operational Implications for a SaaS Running on SecNumCloud Infrastructure

**What Spider can do:**

- Run on SecNumCloud-qualified IaaS (Outscale, OVHcloud Bare Metal Pod, S3NS PREMI3NS) as a tenant.
- Spider itself does NOT need SecNumCloud qualification -- it needs to run ON SecNumCloud-qualified infrastructure to claim the "Cloud de Confiance" positioning.
- Leverage the infrastructure provider's qualification for marketing and compliance positioning with French public sector and regulated clients.

**What changes operationally:**

- **Reduced service catalog**: SecNumCloud-qualified infrastructure has a narrower service catalog than AWS/Azure. No managed Lambda-like serverless, limited managed database options, fewer PaaS abstractions. You work closer to the metal.
- **Performance**: Generally comparable for compute, but fewer availability zones and less geographic diversity. Outscale and OVHcloud operate primarily from French data centers (Gravelines, Roubaix, Strasbourg for OVHcloud; Paris region for Outscale).
- **Deployment complexity**: More infrastructure-as-code work required. You cannot simply click-deploy from a marketplace. OpenStack APIs are typical.
- **Cost premium**: Expect 20-40% premium over standard public cloud for equivalent compute, though this is offset by the absence of egress fees and simpler pricing.

### 1.5 Can You Use AWS/Azure Services Alongside SecNumCloud?

**Short answer: Yes, with a tiered architecture.** The emerging pattern is:

- **Tier 1 (Sensitive data)**: All client business data, PII, ontology data, and audit logs reside on SecNumCloud-qualified infrastructure. This is Spider's core data layer.
- **Tier 2 (Non-sensitive compute)**: Non-sensitive processing, static assets, CDN, public documentation can run on hyperscalers.
- **Tier 3 (AI inference)**: Mistral models deployed on SecNumCloud infrastructure (OUTSCALE already offers Mistral on SecNumCloud 3.2). Alternatively, self-hosted models on sovereign GPU instances.

The critical rule: **no personal data or client business data may transit through or be stored on non-SecNumCloud infrastructure**. Metadata, aggregated anonymized analytics, or public content can use hyperscaler services.

Sources: [Cloud Temple Hybrid](https://www.cloud-temple.com/en/limiting-the-risks-of-hybrid-cloud-interruption-secnumcloud/), [Qonto SecNumCloud Journey](https://medium.com/qonto-way/beyond-compliance-secnumcloud-without-compromises-fa24bb3336d2)

---

## 2. GDPR Operational Requirements for a Data Platform

### 2.1 Specific Requirements for a Platform Aggregating Client Business Data

Spider aggregates client business data from multiple sources (ERP, CRM, accounting, invoicing). Under GDPR, Spider acts as a **data processor** (sous-traitant) processing data on behalf of its clients (the data controllers). Key obligations:

- **Article 28**: Mandatory Data Processing Agreement (DPA) with each client.
- **Article 30**: Maintain a Register of Processing Activities (ROPA) documenting all data categories, purposes, retention periods, and transfer mechanisms.
- **Article 32**: Implement appropriate technical and organizational measures (encryption at rest and in transit, access controls, pseudonymization where feasible).
- **Article 33/34**: Breach notification -- notify the controller (your client) without undue delay, and no later than 72 hours after becoming aware of a breach.
- **Article 35**: Data Protection Impact Assessment (DPIA) required for high-risk processing.
- **Article 25**: Data protection by design and by default.

### 2.2 Data Processing Agreement (DPA) -- What Must Be Included

A DPA between Spider and its clients must include, at minimum:

| Element | Requirement |
|---------|-------------|
| **Subject matter and duration** | What data is processed, for how long, and for what purpose |
| **Nature and purpose** | Specific processing operations (aggregation, analysis, AI inference) |
| **Type of personal data** | Categories: employee names, client contact info, financial data, etc. |
| **Categories of data subjects** | Employees, clients' customers, suppliers |
| **Controller obligations and rights** | Right to audit, right to instruct, right to object |
| **Processor obligations** | Process only on documented instructions; ensure confidentiality; assist with data subject requests; delete/return data on termination |
| **Sub-processor management** | List of sub-processors (cloud provider, AI provider); prior written consent required for changes |
| **International transfers** | Document any transfers outside EEA (for Spider on sovereign cloud: none) |
| **Technical and organizational measures** | Annex detailing encryption, access controls, backup procedures |
| **Breach notification procedures** | Timeline and format for reporting breaches to the controller |

**Spider's sovereignty advantage**: Unlike competitors using US cloud infrastructure, Spider can state in its DPA that **no data transfers occur outside the EEA** and that **no sub-processor is subject to extraterritorial data access laws**. This eliminates the need for Standard Contractual Clauses (SCCs) and Transfer Impact Assessments (TIAs), which are increasingly burdensome post-Schrems II.

Sources: [European Commission Data Protection](https://commission.europa.eu/law/law-topic/data-protection/information-individuals_en), [Matomo GDPR Guide](https://matomo.org/blog/2025/08/gdpr-compliance/), [Alation GDPR Best Practices](https://www.alation.com/blog/gdpr-data-compliance-best-practices-2025/)

### 2.3 Right to Erasure -- Implementation for a Data Platform

The right to erasure (Article 17) is under **coordinated enforcement in 2025** -- 30 European DPAs are simultaneously investigating how controllers handle erasure requests. This is not theoretical; it is actively enforced.

**Technical implementation for Spider:**

1. **Data catalog with PII tagging**: Every field in the ontology must be tagged as containing PII or not. Column-level tags (e.g., `pii:true`, `pii:email`, `pii:name`) enable automated discovery.

2. **Cascading erasure engine**: When an erasure request arrives, the system must:
   - Query the data catalog for all tables/objects containing the data subject's PII
   - Traverse the lineage graph to find derived data, aggregates, and exports
   - Execute erasure across all locations: primary database, caches, search indexes, backups, DR replicas

3. **Audit logs tension**: GDPR requires deletion of personal data, but compliance and financial regulations require maintaining audit trails. The resolution:
   - **Pseudonymize** rather than delete in audit logs -- replace identifiable data with irreversible hashes
   - Maintain a "tombstone" record proving deletion occurred, without retaining the deleted data
   - Audit logs documenting the deletion itself are lawful under GDPR's legitimate interest basis (compliance evidence)

4. **Backup handling**: Personal data in backups must either be encrypted with disposable keys (crypto-shredding) or deleted within a reasonable retention window. Industry practice is 30-90 days for backup rotation.

5. **Ontology and lineage**: If a data subject's data has been used to train or influence an AI model, the model itself may need to be retrained or the influence isolated. For Spider's recommendation engine, this means ensuring AI outputs are based on aggregate patterns, not individual records.

Sources: [EDPB Coordinated Enforcement on Erasure](https://www.edpb.europa.eu/news/news/2025/cef-2025-launch-coordinated-enforcement-right-erasure_en), [Axiom Right to Be Forgotten vs Audit Trails](https://axiom.co/blog/the-right-to-be-forgotten-vs-audit-trail-mandates), [Databricks GDPR in Delta Lake](https://www.databricks.com/blog/2022/03/23/implementing-the-gdpr-right-to-be-forgotten-in-delta-lake.html), [Galaxy GDPR Right to Erasure in Data Warehouses](https://www.getgalaxy.io/learn/glossary/enforcing-gdpr-right-to-erasure-in-a-data-warehouse)

### 2.4 Data Portability -- Format and Ontology Export

Article 20 requires data to be provided in a **structured, commonly used, and machine-readable format**. Recommended formats include CSV, JSON, and XML. There is no GDPR-mandated specific format for ontology exports.

**Spider's implementation:**

- **Raw data export**: CSV/JSON export of all client data, organized by entity type (customers, invoices, products, employees).
- **Ontology export**: Export the ontology schema as RDF/OWL or JSON-LD (semantic web standards). While not GDPR-required, this differentiates Spider and enables genuine portability -- clients can take their data model, not just their data.
- **Lineage metadata**: Export transformation history and pipeline configurations as machine-readable YAML/JSON.
- **Timeline**: GDPR requires response within 30 days, extendable to 90 days for complex requests.

Sources: [Article 20 GDPR](https://gdpr-info.eu/art-20-gdpr/), [ICO Data Portability Guidance](https://ico.org.uk/for-organisations/uk-gdpr-guidance-and-resources/individual-rights/individual-rights/right-to-data-portability/), [Deloitte GDPR Data Portability](https://www2.deloitte.com/ch/en/pages/risk/articles/gdpr-data-portability.html)

### 2.5 DPIA -- When Required and What It Looks Like

A DPIA is **mandatory** when processing is likely to result in a high risk to individuals' rights and freedoms. For Spider, a DPIA is almost certainly required because:

- The platform involves **systematic processing of business data** that may include employee personal data
- It uses **new technologies** (AI/ML for recommendations and analysis)
- It involves **large-scale processing** of data from multiple sources
- It performs **profiling and automated analysis** that could influence business decisions

**DPIA structure for a data platform like Spider:**

1. **Systematic description of processing**: What data flows in, how it is transformed, what AI models process it, what outputs are generated
2. **Assessment of necessity and proportionality**: Why this processing is necessary for the stated purpose, and whether less invasive alternatives exist
3. **Assessment of risks to individuals**: What could go wrong (data breach, discriminatory AI output, unauthorized access), likelihood, and severity
4. **Measures to mitigate risks**: Encryption, access controls, anonymization, human oversight of AI recommendations, SecNumCloud hosting, regular audits
5. **Consultation with DPO**: Document the Data Protection Officer's opinion
6. **Review schedule**: DPIA is a living document, not a one-off exercise; review annually or when processing changes materially

Sources: [GDPR.eu DPIA Template](https://gdpr.eu/data-protection-impact-assessment-template/), [European Commission DPIA Guidance](https://commission.europa.eu/law/law-topic/data-protection/rules-business-and-organisations/obligations/when-data-protection-impact-assessment-dpia-required_en), [ICO What is a DPIA](https://ico.org.uk/for-organisations/uk-gdpr-guidance-and-resources/accountability-and-governance/data-protection-impact-assessments-dpias/what-is-a-dpia/)

---

## 3. EU AI Act Practical Compliance

### 3.1 Spider as "Limited Risk" -- What This Means Concretely

The EU AI Act (Regulation (EU) 2024/1689) classifies AI systems into four risk tiers: unacceptable, high, limited, and minimal. Spider's AI-powered recommendations, analysis, and automation features fall into the **limited risk** category because:

- Spider does not make decisions with legal or similarly significant effects on individuals (not high-risk)
- Spider's AI generates business recommendations and insights, not autonomous decisions affecting employment, credit, or legal rights
- Spider includes AI-powered interfaces (chatbot-like interactions, generative summaries) that require transparency

**Concrete obligations for limited risk (Article 50):**

| Obligation | What Spider Must Do |
|-----------|-------------------|
| **Human-AI interaction disclosure** | Clearly inform users when they are interacting with an AI system (e.g., "This analysis was generated by AI") |
| **AI-generated content marking** | Mark AI-generated text, summaries, and recommendations as AI-produced, both visibly to users and in machine-readable metadata |
| **No deceptive output** | Ensure AI outputs do not mislead users into believing they are human-produced analysis |
| **Copyright compliance** | Publish summaries of copyrighted data used for training (applies to GPAI providers like Mistral, not directly to Spider as a deployer) |

### 3.2 Documentation Requirements

As a **deployer** (not provider) of AI systems, Spider's documentation burden is lighter than that of model providers like Mistral. Required documentation:

- **Transparency notice**: Clear UI disclosure that AI is used, what it does, and its limitations
- **Usage policy**: Internal policy on how AI is used within the platform, what oversight exists
- **Risk assessment**: Lightweight assessment documenting why Spider's use cases are limited risk, not high risk
- **AI literacy**: Ensure staff have sufficient AI literacy to understand the systems they deploy (Article 4, effective since February 2025)
- **Record-keeping**: Maintain logs of AI system usage, inputs, and outputs for auditability

### 3.3 Timeline of Requirements

| Date | Requirement | Status |
|------|------------|--------|
| **1 August 2024** | AI Act enters into force | Done |
| **2 February 2025** | Prohibited AI practices banned; AI literacy obligations effective | **Active** |
| **2 August 2025** | GPAI model obligations (technical documentation, training data summaries, copyright compliance) -- applies to Mistral as provider | **Active** |
| **2 February 2026** | Member states designate national authorities, penalties framework in place | **Active now** |
| **June 2026** | Final Code of Practice on marking/labeling AI-generated content published | Upcoming |
| **2 August 2026** | **Full applicability**: Article 50 transparency obligations become enforceable; high-risk AI system obligations take effect | **6 months away** |
| **2 August 2027** | High-risk AI systems in Annex I (e.g., regulated products) must comply | Future |

**Key implication for Spider**: The August 2026 deadline is the critical one. By that date, Spider must have implemented all transparency measures: AI interaction disclosure, machine-readable content marking, and user-facing notices on all AI-generated outputs.

Sources: [EU AI Act Official](https://digital-strategy.ec.europa.eu/en/policies/regulatory-framework-ai), [DataGuard Timeline](https://www.dataguard.com/eu-ai-act/timeline), [AI Act Implementation Timeline](https://artificialintelligenceact.eu/implementation-timeline/), [Article 50 Text](https://artificialintelligenceact.eu/article/50/), [DLA Piper August 2025 Obligations](https://www.dlapiper.com/en-us/insights/publications/2025/08/latest-wave-of-obligations-under-the-eu-ai-act-take-effect), [WilmerHale Article 50 Deep Dive](https://www.wilmerhale.com/en/insights/blogs/wilmerhale-privacy-and-cybersecurity-law/20240528-limited-risk-ai-a-deep-dive-into-article-50-of-the-european-unions-ai-act)

---

## 4. Mistral AI Integration

### 4.1 Current Model Lineup (as of February 2026)

| Model | Parameters | Input (per 1M tokens) | Output (per 1M tokens) | Best For |
|-------|-----------|----------------------|------------------------|----------|
| **Mistral Large 3** (Dec 2025) | 123B | $0.50 | $1.50 | Complex reasoning, multilingual, business analysis |
| **Mistral Medium 3.1** (2025) | ~70B | $0.40 | $2.00 | Balanced cost/performance |
| **Mistral Small 3.2** (Jun 2025) | 24B | $0.10 | $0.30 | High-volume, cost-efficient tasks |
| **Codestral 2508** (Aug 2025) | -- | $0.30 | $0.90 | Code generation, pipeline automation |
| **Ministral 3B** | 3B | $0.10 | $0.10 | Edge deployment, simple tasks |
| **Ministral 8B** | 8B | $0.15 | $0.15 | Lightweight inference |
| **Mistral Embed** | -- | $0.10 | -- | Vector embeddings for RAG |
| **Pixtral Large** | -- | $2.00 | $6.00 | Multimodal (vision + text) |

### 4.2 Pricing Comparison: Mistral vs OpenAI vs Anthropic

| Model Class | Mistral | OpenAI | Anthropic |
|------------|---------|--------|-----------|
| **Frontier** | Mistral Large 3: $0.50/$1.50 | GPT-4o: $2.50/$10.00 | Claude 3.7 Sonnet: $3.00/$15.00 |
| **Mid-tier** | Mistral Medium 3.1: $0.40/$2.00 | GPT-4o-mini: $0.15/$0.60 | Claude 3.5 Haiku: $0.80/$4.00 |
| **Small/Fast** | Mistral Small 3.2: $0.10/$0.30 | -- | -- |

**Key insight**: Mistral Large 3 at $0.50/$1.50 is **5x cheaper on input and 6.7x cheaper on output** than GPT-4o. For a data platform processing millions of tokens daily across client analysis tasks, this translates to massive cost savings.

### 4.3 Deployment Options

| Option | Data Residency | Control | Cost | SecNumCloud |
|--------|---------------|---------|------|-------------|
| **La Plateforme (API)** | EU by default (Paris) | Medium | Pay-per-token | No (but EU-hosted) |
| **Mistral on Outscale** | France, SecNumCloud 3.2 | High | Custom contract | **Yes** |
| **Self-hosted (open models)** | Full control | Full | GPU infrastructure cost | Depends on infra |
| **Mistral on Azure/AWS** | Region-dependent | Low | Pay-per-token | No |
| **VPC/On-premise** | Full control | Full | Enterprise contract + infra | Depends on infra |

**Critical finding**: Mistral models are **already available on SecNumCloud 3.2 infrastructure** through OUTSCALE. This is a game-changer for Spider. As of September 2025, Mistral's La Plateforme became operational on OUTSCALE's SecNumCloud-certified infrastructure, and "Le Chat" (Mistral's assistant) is available on SecNumCloud 3.2. OUTSCALE also offers Mistral Embed and Mistral Medium on SecNumCloud 3.2.

### 4.4 Enterprise Offering

Mistral's enterprise tier includes:

- **Data residency guarantees**: All data hosted exclusively in the EU. Option to deactivate features involving transfers outside the EU at organization level.
- **Data governance**: Under the enterprise tier, Mistral does not use customer data for model training. With self-hosted deployment, data stays within your perimeter.
- **Legal positioning**: Mistral AI is a French SAS (simplified joint-stock corporation) headquartered in Paris. It is fully subject to GDPR and is **not subject to the US CLOUD Act** -- unlike OpenAI (US entity), Anthropic (US entity), or Google/Microsoft.
- **Government adoption**: Already deployed for 30,000+ public-sector users through DINUM (Direction interministerielle du numerique) and multiple French ministries.
- **Enterprise pricing**: Entry point around EUR 20K+/month or annual commitments, including private deployment, agent builders, and audit logs.

Sources: [Mistral AI Pricing](https://mistral.ai/pricing), [Mistral Docs Pricing](https://docs.mistral.ai/deployment/ai-studio/pricing), [Mistral Enterprise Deployment](https://llmdeploy.to/solutions/mistral), [Mistral Data Residency FAQ](https://help.mistral.ai/en/articles/347629-where-do-you-store-my-data-or-my-organization-s-data), [OUTSCALE Mistral on SecNumCloud](https://blog.outscale.com/en/outscale-enriches-its-offering-with-mistral-embed-mistral-medium-on-secnumcloud-3-2/), [OVHcloud Mistral Deployment](https://blog.ovhcloud.com/reference-architecture-deploy-mistral-large-model-in-sovereign-environment-ovhcloud/), [Introl France AI Sovereignty](https://introl.com/blog/france-ai-sovereignty-mistral-sovereign-cloud-2025)

### 4.5 Performance Comparison for Business Data Tasks

Based on benchmarks for text-to-SQL and business data analysis tasks:

- **GPT-4o**: Fastest generation times across most categories. Slightly ahead overall on text-to-SQL benchmarks, especially for complex multi-table queries.
- **Claude 3.5 Sonnet**: Strong in complex reasoning tasks. Balances speed and accuracy well. Particularly strong for finance, legal, and nuanced data interpretation.
- **Mistral Large 2/3**: Competitive performance at a fraction of the cost. Excels at multilingual tasks (critical for French SMBs). Strong at structured data extraction and business document processing in French.

**For Spider specifically**: Mistral's combination of competitive performance, French-language optimization, EU data residency, SecNumCloud availability, and dramatically lower cost makes it the default choice. For edge cases requiring frontier reasoning, Claude or GPT-4o can be used via European endpoints as a fallback.

Sources: [Waii Text-to-SQL Comparison](https://blog.waii.ai/text-to-sqls-power-players-comparing-claude-3-5-sonnet-gpt-4o-mistral-large-2-llama-3-1-d4530a3d4407), [Galileo Model Comparison](https://galileo.ai/blog/claude-3-5-sonnet-vs-gpt-4o-enterprise-ai-model-comparison), [Vellum LLM Leaderboard](https://www.vellum.ai/llm-leaderboard)

---

## 5. French/EU SaaS Compliance Landscape

### 5.1 NIS2 Directive

NIS2 (Directive (EU) 2022/2555) repealed NIS1 as of October 18, 2024. Member states had until October 17, 2024 to transpose it into national law, and companies have until **October 2026** for full compliance.

**Relevance for Spider:**

- Cloud service providers are explicitly classified as **critical infrastructure** under NIS2 -- a novelty that directly affects SaaS platforms.
- NIS2 applies to SaaS providers even without physical EU presence, as long as they serve EU customers.
- Spider likely falls within scope if it serves essential or important entities (including SMBs in critical sectors).

**Key requirements:**

| Requirement | What Spider Must Do |
|------------|-------------------|
| **Risk management** | Implement comprehensive risk analysis and continuous monitoring |
| **Incident response** | Establish robust incident response procedures; notify authorities within 24 hours (early warning), 72 hours (full notification) |
| **Supply chain security** | Audit sub-processors (cloud providers, AI providers) |
| **Multi-factor authentication** | Mandatory MFA for all administrative access |
| **Business continuity** | Backup management, disaster recovery, crisis management plans |
| **Reporting** | Regular reporting to national authorities |

**Penalties**: Up to EUR 10 million or 2% of global turnover, whichever is higher.

Sources: [NordLayer NIS2 SaaS Guide](https://nordlayer.com/blog/nis2-implementation-guide-for-saas/), [Opsio NIS2 for SaaS](https://opsiocloud.com/knowledge-base/does-nis2-apply-to-saas/), [Infosecurity NIS2 SaaS Changes](https://www.infosecurity-magazine.com/blogs/nis2-requires-changes-eu-saas/), [EU NIS2 Directive](https://digital-strategy.ec.europa.eu/en/policies/nis2-directive)

### 5.2 E-Invoicing (Facture Electronique) Mandate -- Major Opportunity for Spider

France is implementing mandatory B2B e-invoicing in a phased rollout:

| Date | Obligation | Who |
|------|-----------|-----|
| **1 September 2026** | Receive AND emit e-invoices | Large enterprises (grandes entreprises) |
| **1 September 2027** | Receive AND emit e-invoices | Mid-size enterprises (ETI) |
| **1 September 2028** | Receive AND emit e-invoices | SMEs and micro-enterprises (PME/TPE) |
| **1 September 2026** | Receive e-invoices | **All businesses** |

**Three accepted formats:**

- **Factur-X**: Hybrid PDF + embedded XML. Ideal for SMBs -- human-readable with machine-processable structured data. Based on the EN 16931 European standard.
- **UBL (Universal Business Language)**: Pure XML. Better for automated B2B exchanges between large companies.
- **CII (Cross Industry Invoice)**: UN/CEFACT standard structured XML. For large-volume, complex international exchanges.

**Massive opportunity for Spider:**

1. **All French businesses must be able to receive e-invoices by September 2026** -- this creates immediate demand for systems that can process structured invoicing data.
2. Spider's ontology can ingest Factur-X/UBL/CII data natively, creating rich financial data lineage.
3. SMBs (Spider's target) must emit e-invoices by September 2028 -- Spider can position as the platform that not only handles compliance but turns invoicing data into business intelligence.
4. The mandate requires routing through either the public platform (PPF -- Portail Public de Facturation) or accredited private platforms (PDP -- Plateformes de Dematerialisation Partenaires). Spider could integrate with PDP providers or become one.
5. **e-reporting** (real-time transaction reporting to tax authorities) accompanies e-invoicing -- creating even more structured data flow that Spider can aggregate and analyze.

Sources: [France E-Invoicing Official](https://www.impots.gouv.fr/professionnel/je-decouvre-la-facturation-electronique), [Avalara France Updates](https://www.avalara.com/blog/en/europe/2024/11/france-updates-pdp-on-einvoicing-reform.html), [Sage Facture Electronique](https://www.sage.com/fr-fr/dematerialisation/facture-electronique/), [VAT IT E-Invoicing France](https://vatit.com/blog/e-invoicing-in-france-updates-on-the-b2b-and-b2c-mandate/), [MyFacturation Formats](https://www.myfacturation.com/nos-actualites/formats-factures-electroniques-2026)

### 5.3 DORA (Digital Operational Resilience Act)

DORA (Regulation (EU) 2022/2554) has been enforceable since **January 17, 2025**. It harmonizes digital operational resilience requirements for approximately 22,000 financial entities across the EU.

**Relevance for Spider:**

- If Spider serves financial services clients (banks, insurance, investment firms, payment institutions), those clients are subject to DORA.
- Spider would be classified as an **ICT third-party service provider** and must be contractually bound to DORA requirements.
- Financial clients will demand that Spider's contracts include: SLAs, audit rights, termination rights, exit strategies, and incident notification procedures.

**Five DORA pillars:**

1. **ICT risk management**: Comprehensive risk management framework
2. **Incident management and reporting**: Detect, classify, and report ICT incidents
3. **Digital operational resilience testing**: Regular testing including threat-led penetration testing
4. **Third-party risk management**: Register of all ICT third-party arrangements; audit rights
5. **Cyber threat information sharing**: Voluntary sharing of threat intelligence

**Penalties**: Fines up to 10% of annual turnover or EUR 10 million for financial institutions; up to EUR 1 million for individual senior managers.

**Spider's positioning**: Being on SecNumCloud infrastructure with EU data residency and GDPR-native design makes Spider an attractive option for financial services SMBs who need DORA-compliant vendors.

Sources: [DORA Official](https://www.digital-operational-resilience-act.com/), [InnReg DORA Explained](https://www.innreg.com/blog/dora-regulation-explained), [Yousign DORA Guide](https://yousign.com/blog/dora-regulation), [BMC DORA Explained](https://www.bmc.com/learn/digital-operations-resilience-act-dora-explained.html)

### 5.4 Compliance Certifications Expected by French SMBs

| Certification | Description | Priority for Spider |
|--------------|-------------|-------------------|
| **ISO 27001** | International information security standard. The **absolute minimum** for any serious SaaS in France. De facto passport to public-sector contracts. | **Must have** (Year 1) |
| **HDS** (Hebergeur de Donnees de Sante) | Required for hosting health data. Builds on ISO 27001 with additional requirements. HDS v2.0 mandates EEA data storage. | **If targeting health sector** |
| **SecNumCloud** | ANSSI qualification for cloud providers. Spider does not need this itself but should run on SecNumCloud-qualified infrastructure. | **Infrastructure choice** |
| **SOC 2** | US-origin audit standard. Not legally required in Europe but increasingly expected by international clients and PE/VC investors. | **Nice to have** (Year 2-3) |
| **Cyber Essentials / C5** | Other EU security certifications. Less relevant for French market specifically. | Low priority |
| **GDPR compliance documentation** | Not a "certification" per se, but CNIL expects documented compliance. DPO appointment, ROPA, DPIAs. | **Must have** (Day 1) |

Sources: [Copla ISO 27001 France](https://copla.com/blog/compliance-regulations/iso-27001-regulations-and-implementation-in-france/), [ISMS.online ISO 27001 France](https://www.isms.online/iso-27001/country/france/), [Schellman New HDS Framework](https://www.schellman.com/blog/compliance/new-hds-framework-2024), [EU Cloud Cost Certifications](https://www.eucloudcost.com/blog/cloud-certifications-explained/)

---

## 6. Sovereign Cloud Pricing

### 6.1 OVHcloud Pricing

OVHcloud positions itself as the primary European alternative to US hyperscalers, with **transparent, all-inclusive rates** and no hidden egress fees.

**Key pricing points:**

- **Object Storage**: Approximately **one-third** the cost of equivalent AWS S3 storage
- **Managed Kubernetes**: Compute + storage for **less than half** the cost of AWS EKS
- **Bandwidth**: Unlimited included in most regions (vs. AWS's complex egress pricing that can add EUR 70-90/month per TB)
- **Bare Metal Pod (SecNumCloud)**: Configurations starting from 8 servers (half-rack) to 480 servers (10 racks). Pricing is custom/contact-sales, but expect a **20-40% premium** over standard OVHcloud public cloud pricing for the SecNumCloud qualification layer
- **Revenue scale**: OVHcloud surpassed EUR 1 billion in annual revenue in FY 2025

**Real-world case study**: A mid-size e-commerce company migrated from AWS to OVHcloud, reducing monthly cloud costs from EUR 5,400 to EUR 3,333 -- a **63% saving** -- primarily by eliminating RDS, EKS, and S3 premium pricing plus EUR 800/month in data transfer fees.

Sources: [European Cloud Pricing Comparison](https://european.cloud/2025/06/a-basic-look-at-pricing-of-european-cloud-vendors/), [OVHcloud Pricing](https://www.ovhcloud.com/en/public-cloud/prices/), [DeViLink AWS Alternative](https://www.devilink-consulting.com/en/blog/cloud-alternatives-aws-azure-2026), [OVHcloud Bare Metal Pod](https://www.ovhcloud.com/en/bare-metal/secnumcloud/)

### 6.2 Scaleway Pricing

Scaleway, headquartered in Paris with data centers exclusively in the EU (France and Netherlands), is known for developer-friendly tooling and competitive pricing.

**Key pricing points:**

- **General Purpose instances**: Approximately **half the price** of comparable AWS instances
- **GPU instances (AI inference)**:
  - NVIDIA L4: EUR 0.75/hour per GPU (cost-effective for inference)
  - NVIDIA H100: Starting at EUR 2.73/hour (among the lowest hourly rates for H100 in major cloud providers)
  - NVIDIA L40S: Priced between L4 and H100, ideal for LLM inference
- **GPU regions**: Paris (PAR-1, PAR-2) and Warsaw (WAW-2)
- **SecNumCloud status**: Passed J0 milestone, targeting qualification. Not yet qualified.

**For Spider's AI workloads**: Scaleway's L4 instances at EUR 0.75/hour are excellent for running Mistral Small or inference endpoints, while H100 instances at EUR 2.73/hour can handle Mistral Large for demanding analysis tasks.

Sources: [Scaleway GPU Pricing](https://www.scaleway.com/en/pricing/gpu/), [Scaleway L4 Instance](https://www.scaleway.com/en/l4-gpu-instance/), [Scaleway H100](https://www.scaleway.com/en/h100/), [VPSBenchmarks OVHcloud vs Scaleway](https://www.vpsbenchmarks.com/compare/ovhcloud_vs_scaleway)

### 6.3 NumSpot

NumSpot is the sovereign cloud consortium backed by Docaposte (La Poste group), Dassault Systemes, and Bouygues Telecom.

**Current status (February 2026):**

- **General Availability**: Launched Q1 2025
- **Services**: IaaS and managed PaaS (Red Hat OpenShift, Kubernetes, managed databases) -- the first sovereign cloud to offer managed PaaS services publicly qualifying for trust certification
- **Pricing**: Transparent pricing with no hidden fees; no ingress/egress charges
- **SecNumCloud**: Application submitted September 2024. Currently ISO 27001 certified; SecNumCloud and HDS certifications in progress.
- **Multi-zone**: Multiple cloud regions in France available since H2 2025
- **Roadmap**: Autoscaling for data and container services planned for 2026; enhanced observability services throughout 2025-2026

**Relevance for Spider**: NumSpot is interesting as a future option once SecNumCloud-qualified. Its consortium backing (Docaposte handles postal/digital identity services for millions of French citizens) provides credibility with public sector clients.

Sources: [La Poste NumSpot Launch](https://www.lapostegroupe.com/fr/actualite/numspot-annonce-le-lancement-de-sa-plateforme-de-services-au-premier-trimestre-2025), [CISPE NumSpot Joins](https://www.cispe.cloud/sovereign-cloud-providers-numspot-and-infomaniak-join-cispe/), [NumSpot Marketplace](https://numspot.com/en/produit/cloud-services-marketplace/)

### 6.4 Total Cost Comparison: Sovereign vs Hyperscaler for a Data Platform

**Estimated monthly costs for a Spider-like data platform (mid-scale: 50-100 SMB clients):**

| Component | AWS (eu-west-3) | OVHcloud (SecNumCloud) | Scaleway | Notes |
|-----------|-----------------|----------------------|----------|-------|
| Compute (8 vCPUs, 32GB x 4) | ~EUR 1,200 | ~EUR 600 | ~EUR 550 | OVHcloud/Scaleway ~50% cheaper |
| Managed PostgreSQL | ~EUR 800 | ~EUR 400 | ~EUR 350 | |
| Object Storage (5TB) | ~EUR 120 | ~EUR 40 | ~EUR 50 | OVHcloud 3x cheaper on storage |
| Egress (2TB/month) | ~EUR 180 | EUR 0 | EUR 0 | Free bandwidth on EU providers |
| GPU inference (L4, 8h/day) | ~EUR 600 | N/A | ~EUR 180 | Scaleway L4 at EUR 0.75/h |
| Managed Kubernetes | ~EUR 200 | ~EUR 100 | ~EUR 100 | |
| **Monthly subtotal** | **~EUR 3,100** | **~EUR 1,140** | **~EUR 1,230** | |
| SecNumCloud premium (+30%) | N/A | +EUR 340 | N/A (not yet qualified) | |
| **Total with sovereignty** | **~EUR 3,100** | **~EUR 1,480** | **~EUR 1,230** | |

**Key takeaway**: Running on sovereign European infrastructure is not only a compliance advantage -- it is **genuinely cheaper** than AWS for equivalent workloads. Even with the SecNumCloud premium on OVHcloud, the total cost is roughly half of AWS. The absence of egress fees and simpler pricing models eliminate the surprise bills common with hyperscalers.

Sources: [European Cloud Pricing](https://european.cloud/2025/06/a-basic-look-at-pricing-of-european-cloud-vendors/), [Holori Cloud Comparison](https://calculator.holori.com/compare), [Gart Sovereign Cloud Guide](https://gartsolutions.com/digital-sovereignty-of-europe/)

---

## 7. Strategic Implications for Spider

### 7.1 Sovereignty as Differentiation, Not Just Compliance

The European data sovereignty landscape creates a **structural competitive advantage** for Spider that US-based competitors (Palantir, Databricks, Snowflake) cannot easily replicate:

1. **No CLOUD Act exposure**: Spider, as a French entity running on SecNumCloud infrastructure with Mistral AI, has zero exposure to US government data access requests. This is not a marketing claim -- it is an architectural fact.

2. **Regulatory alignment**: With GDPR, NIS2, DORA, the AI Act, and the e-invoicing mandate all converging in 2025-2026, French SMBs face a compliance tsunami. Spider can position as the single platform that addresses all of these simultaneously.

3. **Cost advantage**: Sovereign European infrastructure is 50-60% cheaper than AWS for equivalent workloads. Spider can pass these savings to clients while maintaining healthy margins.

4. **Mistral as AI backbone**: The availability of Mistral models on SecNumCloud 3.2 infrastructure (via OUTSCALE) means Spider can offer AI-powered analysis with full sovereignty -- no data leaves France, no US entity processes it, and the AI provider itself is a French company.

### 7.2 Recommended Compliance Roadmap for Spider

| Timeline | Action | Priority |
|----------|--------|----------|
| **Immediate** | Appoint DPO; create ROPA; draft standard DPA template | Critical |
| **Q1 2026** | Complete DPIA for the platform; implement PII tagging in ontology | Critical |
| **Q2 2026** | Deploy on OVHcloud Bare Metal Pod (SecNumCloud 3.2) or Outscale; integrate Mistral on SecNumCloud | Critical |
| **H1 2026** | Implement Article 50 transparency measures (AI disclosure, content marking) | Critical (August 2026 deadline) |
| **H2 2026** | Begin ISO 27001 certification process | High |
| **H2 2026** | Build Factur-X/UBL/CII ingestion pipeline for e-invoicing data | High (September 2026 mandate) |
| **2027** | Complete ISO 27001 certification; implement NIS2 compliance measures | High |
| **2027-2028** | Consider SOC 2 for international expansion; HDS if targeting health sector | Medium |

### 7.3 The E-Invoicing Catalyst

The French e-invoicing mandate is perhaps the single most significant near-term market catalyst for Spider:

- **September 2026**: All businesses must receive e-invoices. Large enterprises must emit them.
- **September 2028**: All SMBs must emit e-invoices.
- This creates a **forced digitization event** for every French business. Structured financial data (Factur-X XML) will flow through every B2B transaction.
- Spider can ingest this data natively, building rich financial ontologies automatically.
- Combined with ERP data (Odoo, Sage, Cegid), Spider becomes the intelligence layer sitting on top of the compliance layer.
- **Go-to-market angle**: "Your e-invoicing solution handles compliance. Spider turns that compliance data into competitive intelligence."

### 7.4 Mistral Integration Architecture

**Recommended architecture for Spider:**

```
[Client Data] --> [Spider Ontology Engine on SecNumCloud (Outscale/OVHcloud)]
                        |
                        +--> [Mistral Large 3 on SecNumCloud (Outscale)] -- Complex analysis, reports
                        |
                        +--> [Mistral Small 3.2 (self-hosted on Scaleway GPU)] -- High-volume inference
                        |
                        +--> [Mistral Embed (Outscale SecNumCloud)] -- RAG, semantic search
```

- **All data stays in France** on SecNumCloud-qualified infrastructure
- **AI inference on sovereign infrastructure** -- no US entity involvement
- **Multi-model strategy**: Use Mistral Small for routine tasks (cheap: $0.10/$0.30 per 1M tokens), Mistral Large for complex reasoning ($0.50/$1.50), keeping costs dramatically below OpenAI/Anthropic alternatives
- **Estimated AI cost**: For 50 SMB clients generating ~500M tokens/month, monthly AI cost would be approximately EUR 200-500 with Mistral, vs. EUR 2,000-5,000 with GPT-4o

---

## Summary of Key Findings

| Area | Key Finding | Spider Implication |
|------|------------|-------------------|
| SecNumCloud 3.2 | 360+ requirements, 18-36 month certification, extraterritorial law immunity | Run ON SecNumCloud infra (Outscale, OVHcloud), not GET certified |
| GDPR | 2025 coordinated enforcement on erasure; DPA is mandatory | Build PII tagging, cascading erasure, and crypto-shredding from day one |
| EU AI Act | Article 50 transparency fully enforceable August 2026 | 6 months to implement AI disclosure in all UI surfaces |
| Mistral AI | Available on SecNumCloud 3.2; 5-7x cheaper than GPT-4o; French entity | Default AI provider; multi-model strategy for cost optimization |
| NIS2 | SaaS providers are critical infrastructure; October 2026 compliance | Implement risk management, incident response, MFA, supply chain audit |
| E-invoicing | All French businesses receive e-invoices September 2026 | Build Factur-X/UBL ingestion; position as intelligence layer on compliance data |
| DORA | Enforceable since January 2025 for financial services | Enable Spider to serve finserv SMBs with DORA-compliant contracts |
| Pricing | Sovereign cloud 50-60% cheaper than AWS | Cost is an advantage, not a penalty |
| Certifications | ISO 27001 is table stakes for French market | Prioritize ISO 27001 certification in 2026-2027 |
