# Claude Agent Research — Index

> Recherches produites par des agents Claude sur des sujets stratégiques clés : financials Palantir, marché ERP France, régulation EU, benchmarks AI, comparables verticaux, et anatomie de la "Palantir Mafia".

---

## `06-research-counter-thesis-data.md`
**Rôle :** Compilation de données chiffrées pour répondre aux thèses baissières — financials Palantir Q4 2025, benchmark APEX-Agents, prédictions Gartner, étude MIT sur l'échec des pilotes AI, et cas Burry/Jaluria.
**Findings clés :**
- Palantir Q4 2025 : $1.407B de revenus (+70% YoY), marge ajustée 57%, NDR 139% — chiffres record sur tous les indicateurs
- APEX-Agents benchmark : le meilleur modèle (Opus 4.6) résout seulement 29.8% des tâches professionnelles en one-shot ; même à 8 essais, le plafond est ~40%
- Gartner prédit que >40% des projets d'IA agentique seront annulés avant fin 2027 ; MIT NANDA : 95% des pilotes GenAI ne génèrent pas de retour P&L mesurable (chiffre controversé, méthodologie étroite)
- Burry a dépensé ~$9.2M (pas $912M) en puts PLTR, avec une thèse bearish centrée sur la valorisation et les "20 ans de pertes" pré-IPO

---

## `07-research-smb-ai-failures-french-market.md`
**Rôle :** Données sur les taux d'échec de l'IA en entreprise, les coûts cachés du déploiement d'agents, la réponse des cabinets de conseil à l'IA, et les économies FDE/consulting.
**Findings clés :**
- BCG "Widening AI Value Gap" : 60% des entreprises ne génèrent aucune valeur matérielle de l'IA ; S&P Global : 42% des entreprises ont abandonné la plupart de leurs initiatives AI en 2025
- McKinsey : 25,000 agents AI pour 40,000 humains, productivité +30% sur la recherche interne, prévoit de couper 10% des effectifs non-client-facing
- Accenture : $2.7B de revenus GenAI/Agentic (tripling YoY) ; le marché du consulting AI croît à 31.6% CAGR vers $72.8B en 2030
- Compensation MBB : $190-285K tout compris pour un MBA hire ; billing client $700-900/h ; marge brute ~48.5% sur un engagement $1M

---

## `08-research-odoo-france-erp-market.md`
**Rôle :** Radiographie du marché ERP français et de la position d'Odoo — utilisateurs, parts de marché, concurrents (Sage, Cegid, SAP), patterns de customisation, et e-invoicing 2026.
**Findings clés :**
- Odoo : 15M d'utilisateurs mondiaux, $650M ARR, 42% de croissance annuelle, valorisation €5B — France est le 2e marché mondial (6,713 stores, ~800 entreprises trackées)
- Marché ERP France : $3.49B en 2024, projeté $6.40B en 2030 (CAGR 9.7%) ; Sage 100 domine avec 43,000 clients en France, Cegid+EBP ~750,000 clients combinés
- Coûts d'implémentation Odoo : $5K-$15K (small) à $50K-$100K+ (large) ; 56% des projets dépassent le budget ; seulement 44.8% sans customisation
- Deprecation XML-RPC en Odoo 19 (octobre 2025) vers JSON-2 API — migration obligatoire avant Odoo 20 (fin 2026), impacte 86% des 7,500 partenaires

---

## `09-research-eu-regulatory-landscape.md`
**Rôle :** Analyse complète du paysage réglementaire EU applicable à Spider : EU AI Act (timeline, classification des risques, coûts de conformité), CLOUD Act, et souveraineté numérique française.
**Findings clés :**
- EU AI Act : les use cases core de Spider (analyse de données business, ontologies, automatisation de workflows) sont classés "risque limité/minimal" — pas de conformité high-risk si Spider opère sur des données d'entités, pas d'individus
- Coûts de conformité high-risk pour une PME éditeur : €500K-2M initial + €200K-800K/an en audits ; les PME ont accès aux sandboxes réglementaires gratuitement et à des templates simplifiés
- France : €109B d'investissements AI annoncés en février 2025 ; Mistral AI valorisée $14B, déployée pour 30,000 agents publics via DINUM ; SecNumCloud = standard gold pour les données sensibles
- Le CLOUD Act américain oblige les hyperscalers US à fournir des données hébergées en Europe à la justice américaine — avantage structurel pour un acteur souverain européen

---

## `10-research-odoo-api-ecosystem.md`
**Rôle :** Deep dive technique sur l'API Odoo — rate limits, pagination, webhooks, migration XML-RPC→JSON-2, structure du schéma, et auto-discovery pour la couche ontologie de Spider.
**Findings clés :**
- API externe disponible uniquement sur le plan Custom ($37.40+/user/mois) ; SaaS limité à ~1 call/sec ; self-hosted sans limite plateforme
- Migration critique : XML-RPC/JSON-RPC deprecated en Odoo 19 (oct. 2025), supprimés sur SaaS en 2026, sur self-hosted avec Odoo 20 (fin 2026) — opportunité pour Spider comme couche d'abstraction "migration-proof"
- Schema auto-discovery via `ir.model` + `ir.model.fields` : les ~20 modèles core (res.partner, sale.order, account.move…) sont stables depuis Odoo 10 ; custom fields préfixés `x_` et state="manual"
- Recommandation architecture Spider : snapshot du schéma à la connexion initiale, webhooks sur les modèles clés pour le temps réel, bulk `search_read` paginé pour la sync initiale

---

## `11-research-vertical-ai-comparables.md`
**Rôle :** Carte du paysage des vertical AI SaaS ayant atteint $10M+ ARR en ciblant les PME — benchmarks de pricing, vitesse de scaling, thesis Bessemer, et comparables français/européens.
**Findings clés :**
- Vanta ($220M ARR, $10-80K/an) est le comparable de pricing le plus proche de Spider ; Harvey ($195M ARR, 3.9x en 1 an) prouve les timelines de croissance possibles ; DualEntry et Campfire valident l'"AI-native ERP" comme catégorie avec $100M+ levés en <18 mois
- Bessemer : le vertical AI croît à ~400% YoY, marges brutes ~65%, ACV = 80% des SaaS verticaux incumbents ; le modèle hybrid (base + usage) génère 21% de croissance plus rapide
- Pennylane (€2.2B, €100M ARR cible) et Qonto (€5B, €448M revenus 2024) prouvent que les PME françaises adoptent les SaaS modernes — mais aucun acteur ne fait "Palantir pour PME"
- La Palantir Mafia (170+ startups, $24B levés) réplique la méthodologie FDE dans des verticaux spécialisés (défense, santé, legal) mais n'attaque pas les PME généralistes

---

## `12-research-palantir-churn-switching-lockin.md`
**Rôle :** Évaluation indépendante du churn historique de Palantir, des mécanismes de lock-in, des coûts de switching estimés, et de la trajectoire NDR de 107% à 139%.
**Findings clés :**
- Churn historique 2015-2017 : Coca-Cola, AmEx, Nasdaq, Home Depot, NYPD, JPMorgan ont tous quitté Palantir — raisons : coût excessif, friction culturelle, violations de confiance, valeur incertaine
- Le lock-in est multi-couches : technique (ontologie propriétaire, applications non-portables), opérationnel (dépendance aux FDEs), contractuel (10 ans Army ESA), réglementaire (ATO certifications)
- Coût de switching estimé pour une entreprise dépensant $10-50M/an : $10-43M, soit 1-3x le spend annuel Palantir ; délai : 18-36 mois minimum
- Burry identifie le vrai problème : pas les données brutes (exportables en CSV) mais "l'obstruction du transfert de données" — les insights analytiques, tags et annotations restent prisonniers

---

## `12-research-palantir-competitors-deployment-comparison.md`
**Rôle :** Analyse comparative de la méthodologie de déploiement des 4 concurrents principaux de Palantir — Dataiku, Databricks, Snowflake, Microsoft Fabric — avec forces/faiblesses vs Foundry.
**Findings clés :**
- Databricks copie littéralement le titre "Forward Deployed Engineer" (FDE) et structure un modèle 3 tiers similaire ; mais sans la couche opérationnelle (pas d'équivalent Ontology+Workshop)
- Dataiku est 5-50x moins cher en licensing mais délègue l'implémentation à des SIs partenaires (Accenture, Deloitte) — pas de bootcamp, cycles de vente plus longs, pas de couche applicative
- Snowflake opère un modèle 100% partner-led (850+ partenaires, 25,000 certifiés) — excellent en breadth mais sans la profondeur ou la vitesse de valeur de Palantir
- L'avantage core de Palantir reste intact : l'Ontologie comme couche sémantique business + Workshop pour les apps opérationnelles — aucun concurrent n'a d'équivalent fonctionnel

---

## `12-research-palantir-government-contracts.md`
**Rôle :** Détails concrets des contrats gouvernementaux Palantir — SOW, pricing G-Cloud, contrats US Army/Space Force/NHS, patterns de recompete, et mécanismes de lock-in contractuel.
**Findings clés :**
- US Army Enterprise Service Agreement : plafond $10B sur 10 ans (juillet 2025) consolidant 75 contrats existants — probabilité de recompete structurellement quasi-nulle
- G-Cloud UK : Foundry & AIP listé à £3M/licence, professional services facturés par personne/trimestre et par sprint de 2 semaines — délibérément abstrait du time-and-materials
- NHS FDP : £330M sur 7 ans, contrat de 586 pages dont 417 pages entièrement caviardées — moins d'un quart des 215 hôpitaux NHS actifs fin 2024
- Le modèle Acquire→Expand→Scale : pilot gratuit/subsidié → contrat initial $1-5M → expansion $10-50M → enterprise agreement $100M+ en sole-source justifiée par proprietary rights

---

## `13-research-european-data-sovereignty.md`
**Rôle :** Guide d'implémentation pratique de la souveraineté des données pour le go-to-market français/EU de Spider — SecNumCloud 3.2, RGPD opérationnel, AI Act, intégration Mistral.
**Findings clés :**
- SecNumCloud 3.2 : 360+ critères, 18-36 mois de processus, €500K-2M+ en préparation — Spider n'a pas besoin de la qualification, il doit tourner SUR une infrastructure qualifiée (3DS Outscale, OVHcloud Bare Metal, S3NS)
- RGPD : Spider agit comme sous-traitant (data processor) — DPA obligatoire avec chaque client, DPIA quasi-certaine requise, droit à l'effacement nécessite une architecture de "cascading erasure" avec lineage graph
- Mistral Large 3 : $0.50/$1.50 per 1M tokens (5-6x moins cher que GPT-4o), déjà disponible sur infrastructure SecNumCloud 3.2 via OUTSCALE — avantage pricing + souveraineté combinés
- L'avantage concurrentiel européen est structurel : CLOUD Act US + FISA §702 empêchent les hyperscalers US de garantir la souveraineté des données EU, même avec des data centers en Europe

---

## `13-research-palantir-fde-training-onboarding.md`
**Rôle :** Rapport exhaustif sur le programme de formation et d'onboarding des FDEs Palantir — bootcamp, structure d'équipe Delta/Echo, compétences techniques, progression de carrière, et attrition.
**Findings clés :**
- Bootcamp de 3-6 semaines centré sur l'ontology design et le customer engagement ; accès production dès le premier jour ; déploiement sur un compte client en quelques semaines
- Structure NATO alphabet : Delta (FDSE = builder technique) + Echo (Deployment Strategist = traducteur business) — équipes de 2-5 par compte, lead = "Commanding Officer"
- Compensation FDE : $185-230K pour un new grad, $215-300K FDSE, $300-415K Senior FDSE, $415-630K+ Staff — médiane $215K, soit 7-10% de prime vs SWE standard
- Critique récurrente : "FDE = tech support + data engineering + low-code app building" — risque de spécialisation sur tooling propriétaire, difficulté à transférer vers FAANG ; durée médiane 3.2 ans, 35% partent dans la première année

---

## `13-research-palantir-mafia-ex-fde-startups.md`
**Rôle :** Répertoire documenté de la "Palantir Mafia" — 170+ startups, $24B levés, profil des fondateurs ex-FDE, patterns répliqués et non-répliqués, et implications pour le positionnement de Spider.
**Findings clés :**
- Chiffres : 170+ startups (111 comptés strictement comme "fondées par"), $24B levés collectivement ; Anduril ($3.8B), ElevenLabs ($11B), Ironclad ($3.2B), Distyl AI ($1.8B) sont les licornes les plus remarquables
- Pattern dominant répliqué : embedding pré-product (Peregrine : 18 mois avec une police avant de coder), couche ontologie-like pour structurer les données chaotiques, hiring bar extrême
- Pattern non-répliqué : le bootcamp sales model à l'échelle de Palantir (5 bootcamps/jour) — personne ne l'a reproduit ; Distyl AI est le plus proche mais à échelle bien inférieure
- Gap stratégique confirmé : aucune entreprise dans l'écosystème Palantir Mafia ne cible explicitement les PME européennes — la majorité va vers défense, santé, legal et Fortune 500
