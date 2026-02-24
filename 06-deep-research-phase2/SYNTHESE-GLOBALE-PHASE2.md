# Synthèse Complète — Reverse Engineering Palantir (Phase 2)

*Fusion dédupliquée de 5 synthèses (20+ documents sources : GPT, Claude, Perplexity, agents Claude). Tous les faits, chiffres, citations et détails techniques conservés. Écrit en français.*

*Date : 2026-02-18*

---

## Table des matières

1. [Le Modèle Commercial Palantir](#1-le-modèle-commercial-palantir)
2. [Pre-Sales & AIP Bootcamp](#2-pre-sales--aip-bootcamp)
3. [Pilot "Acquire" — Déploiement 90 Jours](#3-pilot-acquire--déploiement-90-jours)
4. [Expand & Scale](#4-expand--scale)
5. [Foundry — Architecture Technique](#5-foundry--architecture-technique)
6. [Ontology Design Patterns](#6-ontology-design-patterns)
7. [FDE — Méthodologie Détaillée](#7-fde--méthodologie-détaillée)
8. [Brevets & Détails d'Implémentation](#8-brevets--détails-dimplémentation)
9. [AIPCon & Preuves Concrètes](#9-aipcon--preuves-concrètes)
10. [Déploiement Data pour PME (contexte Spider)](#10-déploiement-data-pour-pme-contexte-spider)
11. [Contradictions Inter-Sources](#11-contradictions-inter-sources)

---

## 1. Le Modèle Commercial Palantir

### 1.1 Cycle de vie Acquire → Expand → Scale

Les filings S-1 de Palantir décrivent un cycle à trois phases :

- **Acquire** : pilotes à court terme, souvent offerts à **coût nul ou réduit**, opérés à perte pour prouver la valeur. En 2019, les clients Acquire généraient seulement 600 000 $ de revenus contre une perte de contribution de 65,4 M$.
- **Expand** : un compte est classé Expand lorsqu'il génère plus de **100 000 $ de revenu reconnu** sur une année civile **avec une marge de contribution négative**. Ce seuil est un état comptable déterminé en fin d'année, pas un palier calendaire.
- **Scale** : un compte est classé Scale lorsqu'il génère plus de **100 000 $ de revenu reconnu** avec une **marge de contribution positive**.

**Précision** : le seuil de 100 K$ est un seuil de classification (revenu reconnu), pas un prix universel de pilote. Le chiffre de « 5,6 M$ » du S-1 représente le revenu agrégé des clients acquis pendant le S1 2020, pas la conversion d'un pilote unique.

### 1.2 Trajectoire financière par phase

| Phase | Période | ACV approximatif | Marge |
|---|---|---|---|
| Acquire (pilote) | Mois 0-12 | ~100-250 K$ (subsidisé) | Négative |
| Expand | Années 1-3 | ~250 K$ à 2-5 M$ | Positive mais modeste |
| Scale | Année 3+ | 5-20 M$+ | **>55 %** (jusqu'à 68 %) |

Exemple S-1 : en 2019, les clients Scale ont généré **565,7 M$** de revenus avec marge de contribution de **55 %** ; au S1 2020, **296,3 M$** avec marge de **68 %**.

### 1.3 Courbe d'expansion par cohorte

| Âge du client | Multiple de revenu vs. Année 1 |
|---|---|
| Année 1 | 1,0x |
| Année 2 | 1,3-1,5x |
| Année 3 | 2,0-2,5x |
| Année 5 | 3,5-6,0x |
| Année 7+ | 8-10x+ |

Les clients acquis en 2016 généraient environ **6x leur revenu initial** en 2020. La courbe en hockey stick reflète le cycle Acquire-Expand-Scale.

### 1.4 Métriques financières clés

| Métrique | Valeur | Période |
|---|---|---|
| Net Dollar Retention (NDR) | 124 % | Q1 2025 |
| NDR plancher récent | 107 % (Q3 2023) | |
| NDR historique pic US Commercial | 150 % (cohorte 2021) | |
| NDR post-IPO typique | 115-130 %+ | |
| ACV moyen plateforme | ~3,2 M$ | |
| Rétention clients | ~93 % | |
| Rétention brute estimée | 90-95 %+ | |
| Nombre de clients (Q4 2024) | 711 (+43 % YoY) | |
| Top-20 comptes ACV moyen (2023) | 50 M$+ | |
| Remaining Deal Value (Q4 2024) | 4,6 Md$ | |
| Croissance revenu total Q4 2025 | 70 % YoY → 1,41 Md$ | |
| Croissance revenu US Commercial Q4 2025 | 137 % YoY | |
| Résultat net 2025 | 1,625 Md$ (+250 % YoY) | |
| TCV Q4 2025 | 4,26 Md$ (+138 % YoY) | |
| Q3 2025 : deals ≥1M$ | 204 (45 % nouveaux clients) | |
| Taux de personnalisation des déploiements | 87 % | |
| Marge brute ajustée globale | ~84 % | |
| Revenue per employee growth | +63 % revenu avec seulement +10 % headcount (Q3 2025) | |

Les dépenses S&M en % du revenu sont passées de **47 % en 2020 à ~21 % en 2023**, le revenu d'expansion croissant plus vite que les dépenses d'acquisition.

### 1.5 Architecture de pricing

#### Modèle par solution/cas d'usage (G-Cloud UK)

Le « level » est déterminé par : complexité des sources de données, exigences analytiques, échelle utilisateurs, et besoins d'opérationnalisation.

| Niveau | Prix (GBP) | Stade typique |
|---|---|---|
| Level 0 | 250 000 £ | Pilote / cas d'usage unique |
| Level 1 | 500 000 £ | Expand précoce, 1-2 départements |
| Level 2 | 1 000 000 £ | Multi-départements |
| Level 3 | 2 000 000 £ | Cross-fonctionnel |
| Level 4 | 5 000 000 £ | Enterprise-wide opérationnel |
| Level 5 | 10 000 000 £ | Digital twin à grande échelle |
| Level 6-15 | 20 M£-1 Md£ | Enterprise complète / échelle nationale |

**Licence par core** : 66 000 £/core serveur/an + support à 21 500 £/core.

**Services professionnels** : 125 000 £/personne/trimestre ou 317 000 £/an pour un Field Service Representative EU à temps plein.

**Prix de formation (G-Cloud UK)** :

| Formation | Prix (GBP) |
|---|---|
| Bootcamp Training | 1 100 £/personne |
| Workshop Training | 1 750 £/personne |
| Integrator Training | 2 100 £/personne |
| Developer Training | 1 000 £/personne |
| Developer & Integrator combiné | 2 700 £/personne |

#### Modèle de licence plateforme

Le prix évolue avec : volume de données, nombre de cas d'usage/applications, nombre d'utilisateurs, et modèle de déploiement (cloud vs. on-premise). Le modèle par cas d'usage est **additif** — chaque nouveau cas d'usage est une licence séparée. Les contrats incluent souvent des provisions d'expansion avec « ramps liées à des jalons vérifiés ».

#### Structures contractuelles

- Contrats multi-années : **3-5 ans pour le gouvernement**, **1-3 ans pour le commercial**
- Contrats gouvernementaux IDIQ avec plafonds 5-10x le montant initial
- Durée moyenne : **3-4 ans**
- Escalators annuels : **3-5 %**
- Prix basé sur la consommation dans AWS Marketplace pour certaines offres
- Résiliation avec préavis de **3 à 6 mois**

Palantir ne publie pas de tarifs publics standards ; les prix sont visibles via les frameworks de procurement gouvernementaux (G-Cloud UK) ou négociés en privé (AWS Marketplace).

Le prix de Palantir est largement perçu comme **2-5x plus cher** que les alternatives. Pas de frais d'implémentation/consulting séparé — le déploiement FDE est inclus dans la licence logicielle, maintenant un alignement "skin-in-the-game".

---

## 2. Pre-Sales & AIP Bootcamp

### 2.1 Positionnement stratégique

Le Bootcamp AIP est la principale motion go-to-market de Palantir. Ted Mabrey (Head of Global Commercial) : *"Our primary means of going to market with AIP will be through these bootcamps."* Alex Karp : *"We're already overfilled for our AIP bootcamp... It's like a rock concert."* Shyam Sankar : *"The boot camp is not a demo. It's not a presentation. We show up with engineers, and we build."*

Ryan Taylor (CRO, Q3 2023) : *"We reoriented our go-to-market approach around AIP boot camps, which has allowed us to deliver real workflows on actual customer data in five days or less versus our traditional pilots, which generally take one to three months."*

Les bootcamps initiaux AIP sont « typically offered free-of-charge » (documentation UK). Les SEC filings confirment que la conversion n'est pas garantie.

### 2.2 Sourcing et pipeline

Pipeline hybride :
- **Inbound (dominant)** : AIPCon, bouche-à-oreille des alumni, réseaux partenaires (Accenture, PVM, Carahsoft), visibilité earnings calls
- **Outbound** : AEs ciblant des entreprises spécifiques. Karp a décrit un contrat de 3M$ via outbound, puis bootcamp, puis enterprise-wide dans le même trimestre
- **Partenaires** : PVM et Carahsoft organisent leurs propres bootcamps pour les verticaux gouvernement/défense

### 2.3 Profil Client Idéal (ICP) et qualification

**ICP** :
- **Secteurs** : Défense/renseignement, aérospatiale, santé, énergie, manufacturing, services financiers, supply chain, logistique
- **Caractéristiques** : Grandes entreprises avec environnements de données complexes multi-systèmes, où les décisions sont prises *autour* des ERP/CRM plutôt que *à travers* eux
- **Seuil de revenu** : deals ≥ 1M$ ACV (les contrats sous 200K$ ne sont pas rentables pour le modèle FDE)
- **Signaux** : problème opérationnel reconnu, données structurées/non structurées accessibles, capacité à mobiliser stakeholders pour une semaine

**Critères "Bootcamp-Ready"** :
1. **Participants confirmés** : business owners, end-users, IT stakeholders (5-20 stakeholders recommandés)
2. **Static cuts de données** liées aux workflows, fournies 1-2 semaines avant
3. **Discussions de cadrage** en amont
4. **Discussion de 30 minutes avec les data owners** après partage des datasets
5. **Signature des Terms of Service** pour initialiser un environnement Foundry
6. **Données tractables** : identifiants stables, historique suffisant, ground truth
7. **Short list de use cases** avec decision-makers engagés
8. **Readiness légale/sécurité**

**Scoping call** : 60-90 minutes mené par le Deployment Strategist — porte critique avant tout bootcamp.

### 2.4 Rôles

#### Account Executive (AE)
Propriétaire de la relation commerciale, qualification pipeline, orchestration interne. Outbound prospecting, négociation de contrats, QBRs. Présent au kickoff et demo day.

#### Deployment Strategist (DS)
Rôle opérationnel et orienté découverte. Va onsite pour comprendre les questions critiques, identifie les datasets, dirige les formations et démos. Requiert 25-75% de voyage et compétences en programmation (Python, R, SQL). Processus d'entretien : 4 rounds incluant décomposition open-ended, études de cas, entretiens comportementaux.

Pascal Unger (LinkedIn) : *"FDEs handle technical building and implementation; Deployment Strategists manage commercial strategy and change management. Two different humans, two different skill sets, working as one team."*

#### Forward Deployed Engineer (FDE) / FDSE
Ingénierie embarquée avec les clients. Mark Scianna (ex-FDE) : *"Palantir really believes you should put an engineer as close to the problem as possible."*

#### Modèle Echo/Delta (nomenclature alphabet OTAN)

- **Echo = Deployment Strategist** : *"domain insiders with a rebellious streak"*, gèrent les relations, identifient les problèmes à fort levier. Souvent anciens officiers militaires, praticiens de santé. C'est *"a rainbow role"* — pas de parcours définis.
- **Delta = Forward Deployed Software Engineer** : ingénieurs qui construisent vite, *"rough and ready code"*. *"Doers, not artisans obsessed with perfect code"* — accoutumés à *"eating a lot of pain"*. Un Delta se concentre sur *"technology-driven value creation: deploying and customizing Palantir platforms."*

L'appariement Delta/Echo est délibéré : ensemble ils forment l'équipe de déploiement minimale viable.

### 2.5 Staffing du bootcamp

**Équipe Palantir** :
- 1 Deployment Strategist (narratif, facilitation, stakeholder management)
- 1-3 FDEs/AI Engineers (construction technique)
- 1 Account Executive (kickoff + demo day)
- Forward Deployed Infrastructure Engineer (optionnel, pour déploiements on-prem)
- Spécialiste sécurité/plateforme (optionnel)
- Subject matter experts verticaux (optionnel)
- FDE senior / Deployment Lead (pour engagements complexes)

Équipe totale : **2-5 personnes Palantir**. Le même FDE team continue avec le compte s'il convertit.

Décisions de staffing basées sur : expertise verticale, correspondance compétences techniques, disponibilité.

### 2.6 Préparation pré-bootcamp (2-4 semaines)

#### Workstream 1 — Données
- **Static cuts** livrées 1-2 semaines avant. Formats : CSV/Excel (le plus courant), Parquet, JSON. Data Connection supporte JDBC (SQL Server, PostgreSQL, Oracle, Snowflake), connecteurs SaaS (Salesforce, SAP, ServiceNow), cloud storage (S3, Azure Blob, GCS), streaming (Kafka).
- Réplicas read-only ou datasets anonymisés/échantillonnés acceptables. FDEs demandent **3-6 mois de données historiques**.
- Données atterrissent en format Apache Parquet dans un sandbox Foundry.
- Choix possible : données notionnelles ou réelles (PVM : *"You choose!"*).

#### Workstream 2 — Pré-construction
- FDEs pré-construisent : **Pipeline Builder** (no-code) et **Code Repositories** (PySpark/SQL) pour nettoyage/transformation.
- Construction d'un **"starter ontology"** : par le Jour 1, **5-10 object types** avec propriétés et liens de base.
- Environnement démo préparé avec permissions.
- Trois couches pré-build : thin ingestion pipeline, starter ontology, environnement démo.

#### Workstream 3 — Sélection des use cases
- DS passe de **5-10 use cases candidats** à **3-5** explorés au Jour 1, avec **1-2** construits pendant la semaine.
- **Framework de sélection à 4 axes** : business impact, data feasibility, demonstrability, executive resonance.
- **Framework "top-five business outcome"** (Bob McGrew, ex-OpenAI/Palantir) : *"Pick a top-five business outcome for your customer and build backwards from it."*
- **Framework opérationnel à 3 scores** : operational leverage, data tractability, demoability.

#### Workstream 4 — Légal et logistique
- Mutual NDA (1-2 semaines). DPA pour industries réglementées. Signature des Terms of Service.
- AIP tourne sur des réseaux privés avec gouvernance intégrée (AWS, Azure, Google Cloud).
- Constructs de gouvernance : organisations, spaces, audit logs.

#### Workstream 5 — Démo "Art of the Possible"
- Démonstration de **60-90 minutes** live, personnalisée, sur instance Foundry — pas un slide deck.
- Verticales-spécifiques : santé (flux patients), manufacturing (maintenance prédictive), etc.
- Materials : platform primitives demo + vertical storyboard demo.
- Sert de déclencheur émotionnel sécurisant l'engagement exécutif.

### 2.7 Exécution du bootcamp — 5 jours

#### Structure en 3 phases

| Phase | Focus | Timing |
|---|---|---|
| Phase 1 | Introductions + Démos + Build AI Intuition | Jour 1 |
| Phase 2 | Hands-on-keyboards — co-building sur données réelles | Jours 2-4 |
| Phase 3 | Showcase + Assessment — présentation executive | Jour 5 |

#### JOUR 1 — Cadrage et plan de construction

**Matin** :
- Welcome et introductions par le DS.
- **Atelier de cadrage (Problem Framing Workshop)** : exercice whiteboard-heavy. Le DS demande aux experts domaine de parcourir leur processus actuel bout-en-bout. Pour chaque workflow : *trigger*, *decision points*, *data inputs*, *pain*.
- Le DS sonde pour des métriques quantifiables : *"How many work orders are misrouted per week? What's the cost of each misroute?"*
- **Session "Developing Your AI Intuition"** : LLMs (capacités/limites, hallucinations, context window), AIP Logic, prompt engineering, strong typing, tool chaining, raisonnement ontology-grounded.

**Après-midi** :
- **Démo "Art of the Possible"** (si pas faite pré-bootcamp) : données client live dans Foundry. Pivot émotionnel du bootcamp — spreadsheets transformées en système structuré.
- **Data reality check** : validation des données, identification des gaps, verrouillage du "minimum viable ontology".
- Sélection de **1-2 use cases primaires** à construire.

**Livrables J1** : use-case slate signée, process flow diagrams, data inventory, design ontologie minimum viable. Les business stakeholders contribuent **70%+ de la journée**.

**Outils** : Pipeline Builder, Ontology Manager, Workshop, Code Workbooks.

#### JOUR 2 — Première tranche verticale fonctionnelle

**Co-building** : le FDE tient le clavier, l'expert domaine dirige le contenu. Cycle typique : **30-90 minutes** (build → review → feedback → adjust). John Kottlowski (Palantir) : *"sitting shoulder-to-shoulder with our data/tech counterparts"* créant *"immediate, accretive value... within 2 days."*

**Matin** : Pipeline Builder pour transformes simples, Code Repositories pour PySpark complexe. Ontology Manager : Object Types, primary keys, Link Types.

**Après-midi** : première **application Workshop** — widgets (object tables, detail panels, charts, maps, KPI tiles). Objectif : un **"walking skeleton"** fonctionnel.

**Livrables J2** : pipeline branch fonctionnel, ontologie peuplée (5-15 object types, 5-20 link types), app Workshop "walking skeleton".

#### JOUR 3 — Extension et AIP Logic

**Matin** : extension ontologie + **Ontology Actions** (Approve Work Order, Assign Technician, etc.) câblées à des action buttons Workshop.

**Après-midi** : intégration **AIP Logic** — fonctions LLM-powered opérant sur l'ontologie. **AIP Assist** (widget chat) embarqué dans l'app. Moment de **réaction émotionnelle la plus forte**.

**Livrables J3** : 2-3 workflows end-to-end démoables, au moins une fonction/agent LLM, application Workshop entièrement fonctionnelle avec actions, agents AIP Logic configurés.

**AI FDE** (le produit) : agent AI qui *"operates Foundry for you through conversational commands"* — traduit le langage naturel en opérations Foundry.

#### JOUR 4 — Stress testing et durcissement

Le stress testing est une **interrogation par les experts domaine** — pas du load testing. C'est un **exercice de war-gaming live**.

**Matin** : scénarios testing structurés. Chaque défaillance catégorisée : **critical**, **important**, **noted**. FDEs corrigent immédiatement les critiques.

**Après-midi** : instrumentation via **AIP Evals** (test cases, évaluateurs) et **AIP Observability** (traces, logs). DS prépare le narratif de démo executive. Application Workshop **polie**.

**Livrables J4** : suite d'évaluation, failure mode register, prototype bug-fixed et durci, draft narratif de démo.

Jour 4 est le **jour le plus collaboratif** — experts domaine passent **3-4 heures** à casser le système.

#### JOUR 5 — Readout exécutif et roadmap

**Présentation executive** — démo live avec cadrage narratif (pas un slide deck) :
1. Problem statement (2-3 slides)
2. What we built (démo live, 15-20 min)
3. Business impact projection (2-3 slides)
4. Deployment roadmap (1-2 slides)
5. Architecture technique

L'executive sponsor et **5-10 senior stakeholders** assistent. Durée : **45-60 minutes** incluant Q&A.

**Quantification du ROI** : métriques spécifiques au client, co-développées. Framework : économies de temps × coût de main-d'oeuvre, réduction erreurs × coût/erreur, amélioration throughput × revenu/unité. Exemple : *"123 hours saved per week at $85/hour — roughly $540,000 annually from this single use case."*

Exemples clients : *"10% increase in external transfer volume"*, *"90% reduction in time to generate staff schedules."*

**Discussion commerciale** (fin d'après-midi) : roadmap alignment, pas un hard close. Proposition commerciale formelle dans **1-2 semaines**.

### 2.8 Post-bootcamp et conversion

**Package 48h** :
- Executive summary (2-4 pages, C-suite)
- Évaluation technique (architecture, schema ontologie, gaps)
- Projection ROI (scénarios conservateur/modéré/agressif)
- Roadmap de déploiement phasé
- Appendice évaluation/observabilité AI

**Accès sandbox** : reste accessible pendant une période définie. Timeline médian POC-to-production : **6-8 semaines**.

**Cadence de suivi** : DS mène un appel hebdomadaire (4-6 semaines), AE conduit une proposition commerciale (2 semaines). Ted Mabrey : les participants reviennent avec *"4-5 use cases 2 weeks later... and a real live initial implementation."*

**Proposition commerciale — Proof of Value (PoV)** : engagement payé de **8-12 semaines**. Structure MSA/SOW standard.

### 2.9 Métriques de conversion et volume

**Volume de bootcamps** :
- ~92 fin 2022
- ~100 fin Q3 2023
- 500+ fin Q4 2023 (465+ organisations)
- 915+ fin Q1 2024
- 1 300+ fin mi-2024
- ~5/jour globalement en 2024 (Bloomberg)

**Taux de conversion** : estimations divergentes (30-70 %, voir section Contradictions). Deal moyen >1M$.

**Compression du cycle de vente** : de 6-9 mois (enterprise traditionnel) à quelques semaines. Exemples earnings calls : deal 7 chiffres **5 jours** après bootcamp, conversion 7 chiffres **3 semaines** après 1 jour de bootcamp, deal 7 chiffres ACV **16 jours** après bootcamp.

**US commercial revenue growth** : de 23% YoY (Q3 2023, lancement bootcamps) à ~64% YoY (Q4 2024).
**US commercial customer count** : +83% YoY (Q2 2024).

### 2.10 Non-conversions et ré-engagement

Approche par raison de blocage : budget timing (touchpoints trimestriels), politique interne (champions alternatifs), technique (engagements plus légers). Ré-engagement sur **cycle de 3-6 mois**, souvent autour des releases produit ou AIPCon. Les alumni deviennent des *"unofficial salespeople"*.

---

## 3. Pilot "Acquire" — Déploiement 90 Jours

### 3.1 Vue d'ensemble

Déploiement pilote de 12 semaines transformant un contrat signé en système de production opérationnel. Principe directeur (Nabeel Qureshi, 8 ans FDE) : résoudre d'abord un problème *"hair on fire"*, puis s'étendre. Le pilote est délibérément déficitaire.

Structure en 4 phases chevauchantes :
1. Foundation / Discovery (semaines 1-3)
2. Lighthouse Build / Ontology & Integration (semaines 2-6)
3. Application & Action Design (semaines 4-10)
4. Training & Handoff (semaines 8-12)

### 3.2 Composition de l'équipe

**Équipe pilote standard** : 3-5 personnes (1-2 DS + 2-3 FDSE).

- **FDE/FDSE** : possède le stack technique. Travaille **50-70 heures/semaine**, **50-80 % de déplacement**. Tend à écrire du code *"qui fait le job rapidement — poliment — de la dette technique et des workarounds hacky"* (Qureshi).
- **DS** : possède la relation business. Beaucoup viennent de McKinsey/BCG/Bain. Gère la politique organisationnelle pour que les FDE se concentrent sur la construction.
- **Solutions Architect (SA)** : conseils architecturaux transversaux (pas systématique).
- **Forward Deployed Infrastructure Engineer (FDIE)** : déploiement on-premise/air-gapped (variable : peu en SaaS, dédié en gouvernement classifié).
- **Mise à l'échelle** : jusqu'à 10-20+ personnes pour comptes stratégiques (NHS, Army Vantage, BP).

### 3.3 Phase 1 : Découverte (Semaines 1-3)

#### Semaine 1 — Kickoff et immersion

L'équipe FDE arrive sur site au Jour 1 avec briefing minimal — *"get on a plane first, ask questions later."*

**Qui ils rencontrent** :
- Sponsor exécutif (CEO, COO, CDO) : réunions hebdomadaires
- Chefs de départements : 2-4 entretiens par département
- Opérateurs de première ligne (les FDE marchent sur le plancher d'usine). Qureshi *"s'est installé à Toulouse pendant un an et a travaillé à l'usine Airbus aux côtés des gens de la production 4 jours par semaine."*
- Propriétaires de données / gatekeepers IT

**Nombre d'entretiens** : 10-30 dans les deux premières semaines (Claude). Répartition : ~60% entretiens / 40% observation.

**Méthodologie de cartographie des stakeholders** : approche anthropologique, pas consulting structuré. Basée sur les concepts de Keith Johnstone (*Impro*) — *"casting"* (pouvoir réel vs. autorité nominale), dynamiques de statut. Objectif : identifier le **champion**, les **bloqueurs** (middle-management data gatekeepers), les **alliés de première ligne**.

Sarah Constantin : *"Win the hearts of front-line workers... use your allies on the bottom and the top to squeeze out your opponents in the middle."*

**Format des questions** aligné sur le template Foundry `[User Type] [Interface] [Decision] [Decision Inputs] [Action]` — déploiements centrés sur les décisions.

**Cadence établie** : daily standup interne (15 min), 2-3 sessions de travail/semaine avec utilisateurs, update exécutif hebdomadaire (30 min).

**Artefacts semaine 1** : carte des stakeholders, premiers diagrammes de processus (informels, pas BPMN), esquisse du paysage de données, premier use case overview.

#### Semaine 2 — Données et négociation d'accès

**Inventaire des données** : chaque système source documenté (type, propriétaire, volume, fréquence, qualité, mécanisme d'accès). Identifie typiquement **15-40 sources**, dont **3-10** connectées pendant le pilote.

Données souvent hostiles : *"PDFs, notebooks, fichiers Excel (mon Dieu, tellement de fichiers Excel)"*. Chez un constructeur aéronautique : résultats de tests qualité en *"PDFs manuscrits scannés"* (Qureshi).

**Évaluation qualité** (4 dimensions) : complétude, fraîcheur, cohérence, accessibilité. Tri en trois buckets : connecter maintenant, connecter plus tard, pas utile.

**Politique d'accès aux données — le plus gros bloqueur** : Qureshi : *"Nous passions les 8-12 semaines juste à obtenir l'accès aux données, et la dernière semaine à se dépêcher pour avoir quelque chose à montrer."*

**Playbook de négociation** :
1. Commencer par les données accessibles (APIs publiques, CSVs exportés)
2. Démontrer la valeur au gatekeeper
3. Leverager le sponsorship exécutif
4. Construire la pression frontline
5. Adresser les préoccupations sécurité (RBAC intégré, audit trails)
6. Contourner si nécessaire (sources alternatives, overrides exécutifs)
7. Être patient : *"The Palantir Way is labor-intensive and virtually impossible to systematize. You have to throw humans at the persuasion problem"* (Sarah Constantin)

Le DS gère la politique, les FDE gèrent la technique. Division critique : les FDE ne doivent jamais argumenter pour l'accès en réunion.

#### Semaine 3 — Priorisation et setup environnement

Réduction à **1-3 use cases** (un principal, un secondaire).

**Framework de sélection (2x2)** : valeur business (douleur × fréquence × utilisateurs) × faisabilité (readiness données × complexité × temps demo).

**Le test "hair on fire"** : le use case idéal à l'intersection de douleur élevée, disponibilité des données, sponsorship exécutif, démonstration rapide (2-3 semaines).

Les FDE évitent : intégration massive de données, données politiquement sensibles, problèmes nécessitant du ML avant de montrer de la valeur.

**Point de décision** : les use cases sélectionnés en semaine 3 façonnent tout le pilote — c'est la décision à plus fort levier de l'engagement de 90 jours.

### 3.4 Phase 2 : Ontologie & Intégration (Semaines 2-6)

Voir section 5 (Foundry — Architecture Technique) et section 6 (Ontology Design Patterns) pour les détails techniques complets.

**Construction des pipelines** : architecture **raw → clean → semantic**. Pipeline Builder (no-code) pour la plupart des transformations, Code Repositories (PySpark) pour la logique complexe. **10-30 pipelines automatisés** construits pendant les 90 jours, connectant 3-10 sources.

**Design d'ontologie** : 3-5 itérations avant stabilisation. Début minimal (5-10 Object Types), croissance progressive. Déploiements matures : 50-100+ Object Types.

### 3.5 Phase 3 : Actions, Sécurité, Apps (Semaines 4-10)

**Action Types** : transforment Foundry de plateforme read-only en système opérationnel. Configuration dans Ontology Manager : paramètres, règles de mutation, validation, side effects (webhooks), permissions, mode de soumission.

**Sécurité** : architecturalement fondamentale. 7 couches (dataset, project, markings, row-level, column-level, cell-level, action-level, app-level). Propagation automatique des markings à travers les pipelines. "View as User" pour tester les permissions.

**Applications Workshop** : pilote produit **3-10 applications** et **5-15 dashboards**. Premier prototype fonctionnel en **2-3 jours**. Sessions de feedback : 30-60 minutes, 2-3x/semaine.

### 3.6 Phase 4 : Formation & Go-Live (Semaines 8-12)

**Formation par tiers** :
- **Power users / citizen developers** : 8-40 heures (variable selon source). Identifiés semaine 4-5.
- **Opérateurs standard** : 2-8 heures, spécifique à l'application.
- **Exécutifs** : 30-60 minutes, orientation dashboard.

**Modes** : sessions classroom, mentorat deskside, sessions virtuelles, apprentissage guidé (learn.palantir.com avec certifications), train-the-trainer (2-5 power users).

**Go-live** : déploiement contrôlé à un petit groupe pilote d'abord. Daily "hypercare" stand-up. Transition graduelle FDE → client (pas un cutover brutal).

**Revue executive semaine 12** : présentation formelle avec démonstration live, métriques d'impact, métriques d'adoption, roadmap d'expansion, business case.

**KPIs** : time-to-decision, adoption utilisateur, unification des données, déplacement de processus, gain d'efficacité (ex: *"génération de rapports réduite de 8 heures à 15 minutes"*), satisfaction.

**Exemples concrets** : General Mills **14 M$/an** (40K$/jour), Fujitsu **réduction de coûts de 9 M$ en 3 mois**, AARP prototype en **45 jours**.

### 3.7 Rythme quotidien type d'un FDE

**Phase initiale (semaines 1-3)** :
| Heure | Activité |
|---|---|
| 08:00 | Arrivée, revue syncs nocturnes |
| 09:00 | Daily standup Palantir (15 min) |
| 09:30 | Entretiens stakeholders / observation terrain |
| 11:00 | Négociation accès données |
| 12:00 | Déjeuner avec équipe client |
| 13:00 | Travail pipeline |
| 15:00 | Sync DS (priorisation, politique) |
| 16:00 | Sync interne Palantir |
| 17:00-19:00 | Continuation technique |

**Phase build (semaines 3-8)** : iteration ontologie, construction Workshop, sessions feedback client, config sécurité, design Action Types.

**Phase handoff (semaines 8-12)** : formation, mentorat power users, préparation go-live, documentation, préparation revue executive.

### 3.8 Points de décision clés

| Point de décision | Quand | Impact |
|---|---|---|
| Sélection use cases | Fin semaine 2 | Tout le scope du pilote |
| Priorisation sources données | Semaines 1-3 | Ce qui est constructible en 90 jours |
| Scope ontologie | Semaines 2-4 | Forme du jumeau numérique |
| Pipeline Builder vs Code Repos | Par source | Visuel pour simple ; code pour complexe |
| Workshop vs Slate vs Quiver | Semaines 4-5 | Workshop par défaut |
| Modèle de sécurité | Semaines 4-6 | Visibilité par rôle |
| Scope go-live | Semaines 7-8 | Qui/où/quand en premier |
| Proposition d'expansion | Semaines 10-12 | Acquire → Expand |

---

## 4. Expand & Scale

### 4.1 Déclencheurs d'expansion

Trois mécanismes concrets :
1. **Découverte par proximité** : *"You solve one problem, and then the person in the next cubicle says 'can you do that for my team too?'"*
2. **Cartographie des stakeholders** : suivi de qui assiste aux démos, transfère les résultats, pose des questions
3. **Analytique d'usage** : forte adoption signale la maturité pour l'expansion

Sélection du prochain département basée sur : adjacence données, impact métier, disponibilité d'un sponsor exécutif.

**Mécanismes formels** :
- **Revue développement et roadmap** (mensuelle) : alignement, nouvelles opportunités, évaluation business cases
- **SteerCo trimestriel** : direction stratégique, périmètre, coûts
- **Revue de création de projet** (mensuelle) : portail de requêtes → approbation/refus via workflow inbox

### 4.2 Le "problem backlog"

Liste priorisée maintenue par FDE + DS. Priorisation : valeur métier, faisabilité technique, force du sponsorship, rapidité des résultats. Typiquement **5-15 use cases potentiels** réduits à **2-3 quick wins**.

### 4.3 AIP Bootcamps comme accélateur d'expansion

Pour clients existants, le bootcamp diffère : participants comprennent déjà les bases Foundry/AIP — focus sur construction d'intuition AIP et identification de nouveaux use cases.

**La méthode des "100 use cases"** : brainstorming structuré haute vélocité. 20-50 participants groupés par département, exercice post-it/whiteboard, 3-5 points de douleur chacun. Template de canevas : problème, données, processus actuel, résultat souhaité, impact estimé. Les 100+ idées sont filtrées à **5-10 hautement prioritaires**, et **1-3 prototypes** sont construits en temps réel.

Les bootcamps couvrent : approvisionnement (décomposition coûts, négociation), supply chain (perturbations, signaux), ventes/marketing (lead scoring), opérations.

### 4.4 Expansion de l'ontologie cross-département

**Croissance typique** :
- Déploiement initial : **5-20 Object Types** (un domaine)
- Premier expansion : entités partagées entre départements (Customer/Sales ↔ Account/Finance, Employee/HR ↔ Operator/Manufacturing)
- Mature : **100-500+ Object Types** avec 2-3x de Link Types
- Très grands (US Army, énergie) : **500-1 000+**

**Défis techniques** :
- **Définitions conflictuelles** : Palantir permet des Object Types multiples représentant des concepts chevauchants, liés par des relations, plutôt que d'unifier prématurément
- **Entity Resolution** : matching continu de millions d'enregistrements (hashing, AI/ML, fuzzy-matching, approche multi-étapes avec boucles de feedback)
- **Approche "golden record"** : Object Type maître agrégeant de multiples sources via linking

**Gouvernance** :
- Modèle à deux couches : objets projet (rapides) + objets core (processus rigoureux)
- **Ontology Managers** : gèrent le backlog, priorisent les demandes de changement
- **Application Approvals** : workflow auditable pour les changements ontologiques
- Cadence : revues bimensuelles/mensuelles + revues stratégiques trimestrielles

### 4.5 Centre d'Excellence (CoE)

**Timing** : formation commence **6-18 mois** après le début. Seuil : ~50-200+ utilisateurs actifs, valeur prouvée 2-3 use cases. Palantir Phase 3 : le CoE devrait être une **rotation**, pas une équipe dédiée.

**Rôles** :

| Rôle | Formation estimée |
|---|---|
| Platform Owner / Head of Platform | 1-2 jours + engagement stratégique continu |
| Ontology Steward | 2-3 jours design ontologie |
| Data Engineers (équipe "South") | 3-5 jours (80-100h total Python/SQL/Spark) |
| Application Developers (équipe "North") | 2-4 jours Workshop (40-60h total) |
| Permissions Manager | 1-2 jours admin |
| Training Lead | Variable |

**Certifications Palantir** (programme lancé décembre 2025) : Foundry Aware, Application Developer, Data Engineer, Foundry Developer, Foundry Analyst, AIP Developer. Portail gratuit ; examens payants.

**Communauté** : community.palantir.com. Free developer stack sur build.palantir.com.

**Écosystème tiers** :
- **Accenture Palantir Business Group** (décembre 2025) : **2 000+ professionnels** compétents Palantir
- **Ontologize** : fondée par ex-Palantir, construit des équipes Foundry chez les clients
- **NHS FDP / Multiverse** : formation spécifique Foundry pour le NHS
- **CodeStrap** : curriculum open-source Foundry Foundations (GitHub)

### 4.6 Cultivation des champions

**Système multi-niveaux** (quatre simultanément) :
1. Champion exécutif (C-level/VP, sponsorise le budget)
2. Champion opérationnel (manager, utilise quotidiennement)
3. Champion technique (data engineer, construit)
4. Champions utilisateurs finaux (première ligne, résistent à toute suppression)

**Mécanismes** :
- Bootcamps comme fabriques de champions (propriété personnelle du MVP)
- Ammunition ROI : dashboards intégrés (heures économisées, coûts évités). Exemple : Lear Corporation **30 M$+ d'économies S1 2025**
- QBRs formelles présentant ROI + roadmaps
- AIPCon : présentations clients sur scène
- Dîners exécutifs, advisory boards, user groups régionaux
- Sessions "Double Click" de deep-dive technique, canaux Slack, lunch-and-learns

**Redondance** : distribuer connaissances à travers 5-50+ personnes, 3-5 départements, centaines d'utilisateurs actifs. L'ontologie elle-même devient le "champion" — actif institutionnel.

### 4.7 FDE graduation / retrait

Retrait **progressif** :

| Phase | Période | Part client du développement |
|---|---|---|
| Phase 1 | Mois 0-12 | FDE fait 80-90 % |
| Phase 2 | Mois 12-24 | Co-construction, CoE se forme |
| Phase 3 | Mois 24-36 | Client 50-70 %, FDE en conseil |
| Phase 4 | Mois 36+ | Client 70-85 %, FDE en check-ins |
| Année 5+ | - | FDE principalement stratégique |

Présence FDE tombe à **1-2 FDEs couvrant plusieurs comptes**, principalement à distance.

**Prérequis** : CoE fonctionnel (3-10+ personnes), création d'apps self-service, gestion pipelines, formation interne, escalade établie.

**Support de remplacement** : portail tickets, Customer Success Manager dédié, QBRs, architecture office hours, Apollo (mises à jour automatisées), engagement FDE on-demand.

**Historiquement** : en 2007, la plupart des clients nécessitaient 2+ FDEs. En 2024, **+33%** des clients n'ont **jamais eu besoin de FDEs**.

### 4.8 Lock-in et coûts de switching

**Sept couches renforçantes** :
1. **Intégrations** : déploiement mature connecte **50-150+ sources**. Recreation : **6-18 mois** d'ingénierie
2. **Ontologie** : encode connaissances institutionnelles — **aucun équivalent direct** (Databricks Unity Catalog manque relations/actions)
3. **Applications** : 50-200+ apps Workshop sans mécanisme d'export — reconstruction from scratch nécessaire
4. **Connaissances institutionnelles** : pistes d'audit, analyses historiques, versioning ontologie
5. **Configuration sécurité** : milliers de règles RBAC
6. **Investissement formation** : 5-50+ personnes CoE + citizen developers
7. **Intégration workflows** : perturbation opérationnelle, pas seulement technique

**Données portables** : stockées en formats ouverts (Parquet). Le lock-in est aux couches **sémantique et applicative**.

**Coûts de switching** : **2-5x la valeur annuelle du contrat** (mid-stage), ou **2,5-7,5 M$ par client enterprise** (détail : migration données 500K-1,2M$, reconstruction ontologie 500K-2M$, reconstruction apps 500K-1,5M$, sécurité 200-500K$, formation 300-800K$, re-implémentation 6-9 mois).

**Clients partis** : NYPD (système interne avec Microsoft), New Orleans PD (scandale politique), JP Morgan (préoccupations sécurité), Home Depot/AmEx/Hershey's/Coca-Cola (~2017, coûts élevés, plateforme immature). Schéma : départs motivés par politique/éthique/sécurité — **jamais par alternative technique supérieure**. Aucun grand client commercial n'a publiquement quitté dans l'ère Foundry/AIP.

**Réponses anti-churn** : concessions de prix (30-50%), offres de périmètre élargi (AIP), engagement C-level, consolidation commerciale (US Army : 75 contrats → 1 EA de 10 Md$), bootcamps supplémentaires, "expansion défensive" pré-renouvellement.

### 4.9 Le paradoxe captif-autonome

Les clients deviennent plus autonomes dans l'**usage** (70-85% des nouvelles apps construites par eux-mêmes) tout en devenant plus captifs dans l'**infrastructure**. C'est par design.

Trois insights :
1. L'ontologie est le produit — elle devient plus précieuse et plus difficile à abandonner à chaque département connecté
2. Les bootcamps AIP ont fondamentalement modifié l'économie d'acquisition tout en maintenant le même lock-in long-terme
3. Apollo crée une dépendance opérationnelle en-dessous du lock-in ontologie/applicatif

**Vulnérabilité** : pas le déplacement compétitif mais la **commoditisation de la couche sémantique**. Si Databricks/Microsoft/open-source répliquent une abstraction de type ontologie avec construction d'apps, le premium s'effondre.

---

## 5. Foundry — Architecture Technique

### 5.1 Ontology Manager

L'Ontology Manager (OMA) est l'application centrale où les développeurs définissent le modèle de données typé.

**Layout** :
- **Top bar** : recherche globale, création, switching de branches
- **Sidebar gauche** : navigateur de ressources (favoris, récents, groupes)
- **Zone centrale** : configuration (onglets Overview, Properties, Links/Datasources, Actions, Permissions, Interfaces)

**Modèle mental** : un **schema IDE git-branch-aware** où tout est stagé puis commité.

**Création d'Object Type** (pas à pas) :
1. "+ Create Object Type"
2. Display name + API name (auto-généré, éditable)
3. Sélectionner backing dataset (exactement un par Object Type)
4. Définir primary key (unique, déterministe, pas timestamp)
5. Mapper colonnes → propriétés (auto-détection + "Add all unmapped columns")
6. Configurer title key
7. Optionnellement générer actions standard (edit/create/delete)
8. Choisir projet, "Create" (stage), puis "Save" (appliquer)

**Types de propriétés** :

| Catégorie | Types |
|---|---|
| Texte/Booléens | String, Boolean |
| Numériques | Integer, Short, Byte, Long, Float, Double, Decimal |
| Temporels | Date, Timestamp |
| Géospatiaux | GeoPoint/Geohash, GeoShape, GeotimeSeriesReference |
| Complexes | Array (pas de null, pas de nested en OSv2), Struct (pas de nesting, max 10 champs), Vector (embeddings ML) |
| Spéciaux | Attachment, MediaReference, Timeseries, Marking, CipherText |

Contraintes : Long a des problèmes JavaScript ; Decimal ne peut pas être primary key ; Struct max 10 champs, profondeur 1.

**Éditeur de propriétés** : display name, description, status (experimental/active/deprecated), API name, désignation clé, formatage, render hints (searchable/sortable), visibilité (prominent/hidden). Édition bulk supportée.

**Link Types** :
- Cardinalités : 1:1, 1:N, N:1, M:N
- Mécanisme : foreign key pour 1:1/M:1, backing dataset tiers (table de jonction) pour M:N
- **Object-backed link types** : quand la relation elle-même a des attributs → promouvoir l'edge en Object Type
- L'UI auto-crée le lien inverse

**Interfaces** :
- Types abstraits décrivant la "forme" des Object Types → polymorphisme
- Propriétés required/optional que les implémenteurs doivent mapper
- Contraintes de link type d'interface
- Exemple : interface `Facility` implémentée par `Airport` et `Seaport`
- Limitation : Pipeline Builder ne supporte pas le mapping de contraintes de link type

**Functions** :
- Écrites en **TypeScript** dans un Functions Repository dédié
- API v1 : `@Function()` decorator, `@foundry/ontology-api` pour accès typé auto-généré
- API v2 : `@osdk/functions` avec `createEditBatch`, `Edits.Object<T>`
- Edit Functions : `@OntologyEditFunction()` + `@Edits(ObjectType)` pour CRUD
- Alimentent Action Types (writeback), valeurs computées Workshop, intégrations AIP Logic

### 5.2 Pipeline Builder & Code Repositories

#### Pipeline Builder (ETL visuel)

**Interface** : constructeur DAG base sur canvas. Sidebar gauche (datasets), canvas central (noeuds/edges), panneau droit (config/outputs ontologie), panneau preview en bas (temps réel).

**70+ types de noeuds de transformation** :

| Catégorie | Noeuds |
|---|---|
| Structural | Filter (AND/OR), Join (inner/left/right/full/cross/semi/anti), Union, Sort, Limit, Deduplicate |
| Reshaping | Aggregate (SUM, COUNT, AVG, etc.), Pivot, Unpivot, Flatten/Explode |
| Colonnes | Select/Rename, Add Column (expression builder), Cast, Window Functions |
| Nettoyage | Clean String, Trim Whitespace, Cast to Timestamp, Normalize |
| Parsing | CSV, JSON, Excel, XML, Shapefile |
| Avancés | Geospatial joins, KNN, Pattern mining, Time-bounded dedup |

**500+ fonctions built-in** dans le système d'expressions (arithmétique, string, array, date/time, géospatial, JSON parsing, chiffrement, embeddings LLM).

Features : fonctions personnalisées réutilisables, data expectations (health checks), pipelines paramétrés, branching intégré (git-like), features AI (auto-naming, regex generation en langage naturel).

**Ontology outputs** : Pipeline Builder supporte l'ajout direct d'outputs ontologie (object types, link types) avec nommage explicite.

#### Code Repositories (PySpark/Python)

API transforms basée sur décorateurs :

```python
@transform_df(
    Output("/path/to/output"),
    source=Input("/path/to/input")
)
def compute(source):
    return source.filter(source.status == "active")
```

`@transform` (forme générale avec TransformInput/Output), `@transform_df` (convenience wrapper DataFrames), `@transform_pandas` (Pandas). Multi-inputs et multi-outputs supportés.

**Traitement incrémental** : décorateur `@incremental()`. Modes : append, replace, modify (upsert). `require_incremental=True` empêche full recompute accidentel. `semantic_version` pour forcer un rebuild.

**Testing** : pytest via `transforms.testing` avec `mock_transform()`. Data quality checks via objet `Check` (WARN/FAIL). CI intégré : push → pytest automatique, PRs bloquées si échec.

**Choix PB vs Code Repos** : Pipeline Builder pour vitesse et compréhension partagée, Code Repositories pour logique complexe. Mix au niveau dataset boundary.

#### Scheduling

Trois modes :
- **Time-based (Cron)** : constructeur cron visuel + prompt langage naturel AIP
- **Event-driven** : déclenchement sur mise à jour de datasets upstream
- **Hybride** : event-based + fallback timer

Cibles : un dataset, dependencies, dependents, connecting, combinaisons. Dependency resolver automatique, builds parallèles possibles.

### 5.3 Workshop (Application Builder)

**Interface** : constructeur no-code canvas avec grille/layout. Sidebar gauche (widgets par catégorie), canvas central (drag-and-drop), panneau config droit, mode preview.

**Bibliothèque de widgets complète** (~50+) :

| Catégorie | Widgets clés |
|---|---|
| Core display | Object Table, Object List, Object View, Property List, Links, Details Panel, Card Sets |
| Visualisation | Charts (bar/line/area/pie/scatter), Map (Mapbox), Gantt, Pivot Table, Timeline, KPI/Metric Card, Vega Chart, Stepper, Status Tracker, Markdown |
| Media | Media Preview, PDF Viewer, Video, Audio + Transcription, Image Annotation, Spreadsheet |
| Filtrage/Input | Filter List, Object Dropdown, String Selector, Date Picker, Slider, Search Bar, Toggle, Geo Filter, Exploration Filter Pills, User Select |
| Actions | Button Group, Bulk Action Button, Inline Action, Media Uploader, Audio Recorder |
| AIP | AIP Agent, AIP Analyst, AIP Generated Content, AIP Interactive |
| Layout | Container, Tabs, Column Layout, Conditional Visibility, Header |
| Embedding | Iframe (bidirectionnel via @osdk/workshop-iframe-custom-widget), Embedded Module, Custom Widgets (React/TypeScript) |
| Meta | Free-form Analysis, Data Freshness, Edit History, Action Log Timeline, Comments |

**Système de variables** (12 types : object set, filter, string, numeric, boolean, date, timestamp, geopoint, geoshape, array, struct, time series set). 6 mécanismes de définition (static, function, aggregation, object property, object set definition, transformation). Évaluation paresseuse + graphe de dépendances visuel.

**Workshop Events** : Open/Close overlay, Switch page, Expand/Collapse section, Switch tab, Reset/Set/Recompute variable, Stream LLM response, Send to AIP Assist.

**Layout** : Module → Header → Pages → Sections → Widgets/Layouts + Overlays. Routing via URL (deep-linking). Sauvegarde d'état persistante. Module Interface pour composition parent/enfant.

**Limites** : export 200K objets (10K pour colonnes function-backed), Pivot Table groupements max, ~5 actions/écran, 30-40% espace blanc, max 10 composants visibles, custom widgets 50 paramètres/50 events max.

**Workshop bind aux Object Types via l'ontologie** — pas aux datasets directement.

### 5.4 Workshop vs Quiver vs Contour vs Slate

| Dimension | Workshop | Quiver | Contour | Slate |
|---|---|---|---|---|
| Usage | Apps opérationnelles + writeback | Dashboards KPI, time series | Exploration ad-hoc tabulaire | Apps custom HTML/CSS/JS |
| Source données | Ontology objects | Ontology objects + time series | Raw datasets | APIs + datasets |
| Code requis | Non | Non | Non | HTML/JS/CSS |
| Writeback | Oui (Actions) | Non | Non | Oui (via API) |
| Utilisateur | Business ops, managers | Exécutifs, analystes | Data analystes | Développeurs |
| Build speed | Rapide | Très rapide | N/A (exploration) | Lent |
| Mobile | Natif responsive | Non | Non | Limité |
| Ontologie requise | Oui | Oui | Non | Non |
| AIP | Complet | AIP Generate | Limité | Limité |
| Limite | ~50K lignes agrégation (Quiver) | | | Maintenance élevée, legacy |

**Règles** : agir/changer → Workshop ; monitoring sans writeback → Quiver ; exploration ad-hoc → Contour ; pixel-perfect → Slate. Workshop est le choix par défaut.

**Contour** : excelle quand les données ne sont PAS dans l'Ontologie. **Quiver** : templates embarquables dans Workshop. **Slate** : précède Workshop, contrôle HTML/JS/CSS complet avec templating Handlebars-like, Palantir oriente vers Workshop. **Carbon** : navigation unifiée cross-utilisateurs.

### 5.5 AIP (Logic, Assist, Agents)

#### AIP Logic

Environnement de développement **no-code** pour fonctions LLM-powered, gouverné par la sécurité plateforme.

**Layout UI** : Gauche (Inputs/Blocks/Outputs), Milieu (Debugger), Droite (Run panel).

**Workflow** :
1. Définir inputs (strings, ontology objects, object sets, primitives)
2. Composer blocks : Create variable, Apply action, Execute function, Use LLM, boucles, conditionnels + data tools (object lookups, link traversals, semantic search)
3. Chaîner les blocks
4. Run et debug (traces de raisonnement intermédiaires)
5. Publier, puis configurer Evaluations pour testing

**Accès ontologie** : AIP Logic reçoit des **objets typés**, pas des données brutes. Accès explicitement accordé par block LLM à des object types et propriétés spécifiques. Citation : *"If you give it access to everything you're going to have more hallucinations."*

**Guardrails (4 couches)** :
1. Sécurité plateforme (permissions Foundry)
2. Restrictions de tooling (whitelist Functions, Object Types, Actions)
3. Médiation par Actions / human-in-the-loop
4. Audit logging immutable

**Modèles supportés** : GPT-4/4o, Claude 3.5 Sonnet/Opus, Gemini Pro, Llama 3, Mistral, modèles custom. On-premises pour le gouvernement.

**Observabilité** : tracing au niveau workflow avec Trace view (timeline d'opérations).

#### AIP Assist

Sidebar d'aide contextuelle in-app, context-aware. Ne génère **pas** de modules Workshop. Entraîné sur la documentation plateforme. LLMs tiers (GPT-4, Claude).

Intégrations : dans Workshop (event "Send to AIP Assist"), dans Ontology Manager ("Explain with AIP Assist" sur erreurs).

**Generative Frontend** (en développement) : cible les applications OSDK React, pas Workshop directement. Extension Continue dans VS Code, alimentée par Claude Sonnet.

#### AIP Agents

Widget **AIP Agent** dans Workshop : assistant IA interactif (chat) avec 4 types d'outils : recherche sémantique Ontologie (KNN/vecteur), Actions (writeback), applications Workshop (avec variables), Functions (AIP Logic ou Ontology Functions). Peut lire et écrire des variables Workshop.

### 5.6 OSDK

L'Ontology SDK génère des **clients typés statiques** (TypeScript, Python, Java, OpenAPI) spécifiques à l'ontologie — pas un wrapper REST générique.

**Génération** :
- Créer app dans **Developer Console**
- Configurer OAuth, sélectionner ontologie, choisir object/action types
- Code généré avec classes typées, accesseurs, traversées de liens, invocations d'actions

```typescript
const client = createClient(foundryUrl, ontologyRid, auth);
const tickets = await client(MaintenanceTicket)
  .where({ priority: "HIGH", status: { $ne: "CLOSED" } })
  .orderBy(t => t.createdDate.desc())
  .take(50);

// Traverser les liens
const asset = await tickets.data[0].$link.asset.get();

// Exécuter des actions
await client(updateTicketStatus).applyAction({
  ticket: tickets.data[0].$primaryKey,
  newStatus: "IN_PROGRESS",
});
```

**Hooks React** (`@osdk/react`) : `useOsdkObjects` avec filtering, ordering, `pivotTo`, `streamUpdates` (WebSocket real-time).

**Python OSDK** : `.get()`, `.page()`, `.iterate()`, `.where()`, `.count()`, `.avg()`, `.group_by()`.

**Auth** : OAuth 2.0 confidential/public client, bearer token (dev).

**Écosystème NPM** : `@osdk/client`, `@osdk/api`, `@osdk/oauth`, `@osdk/cli`, `@osdk/react`. Repo open-source : `palantir/osdk-ts`.

### 5.7 Apollo (Déploiement)

#### Architecture hub-and-spoke

1. **Apollo Hub** (SaaS central) : moteur d'orchestration, catalogue, settings d'environnement
2. **Remote Apollo Hubs** : dans les réseaux air-gapped, synchronisés via Apollo Bundles
3. **Spoke Environments** : exécutent un Spoke Control Plane
4. **Apollo Agents** : déployés dans les Spokes, pollent le control plane, téléchargent artifacts, orchestrent Kubernetes
5. **Apollo SDK** : framework pour publier metadata de release
6. **Apollo Catalog** : source de vérité pour toutes les versions disponibles

**Modèle pull-based** : aucune connexion entrante requise (critique pour la sécurité).

#### Moteur d'orchestration constraint-based

Évalue continuellement les Plans, compare état cible vs observé, calcule des **Apollo Plans** (quoi upgrader, où, comment). Les Plans de roll-off de releases rappelées sont **prioritisés**.

#### Mécanismes de contrôle

- **Release Channels** : canary → beta → stable → government-stable
- **Promotion pipelines** : critères à chaque étape
- **Canary Analysis** : monitoring post-rollout, promotion/rappel automatique
- **Blue/Green Deployment** : zero-downtime
- **Fenêtres de maintenance** : au niveau produit/environnement, auto-créées sur seuil de failure
- **Change requests** : Pending/Approved/Rejected/Cancelled. Approbateur requis hors DEV.

#### Déploiements air-gapped

- **Apollo Bundles (sneakernet)** : générés sur Hub SaaS, diffs compressés, gravés sur media physique, chargés dans Remote Hub. Metadata AV incluses, checksums vérifiés.
- **Binary Transfer Service (BTS)** : automatise via Cross Domain Solutions (CDS) accréditées.
- Opération déconnectée supportée (véhicules en mouvement, etc.).
- One-way data flow pour les niveaux de classification les plus élevés. Classifications supportées : jusqu'à **TS/SCI**.

#### Échelle et cadence

- **300+ environnements**, 250+ équipes d'ingénierie
- **3 500+ updates/semaine**, multiple fois/jour
- Vitesse de patch : **3,5 minutes** en moyenne, <5 min pour remédier la production
- Remédiation log4j en "quelques heures" à travers 200+ environnements
- 500+ microservices déployés indépendamment

#### Rollback

- Déclaratif (version désirée → état précédent)
- Automatique sur échec health checks
- Stratégies de recall : stay on current, stay with exceptions, any version newer, roll back to specific known-good
- Artifacts immutables et versionnés

#### Certifications

Clé pour FedRAMP, DoD IL5, IL6, ICD 503. Encode les SLAs de vulnérabilité, s'intègre aux scanners d'images container, génère des **SBOMs** complets.

### 5.8 Outils complémentaires

**Data Lineage** : tracking automatique dataset-transform-dataset. Graphe DAG interactif avec search, expand upstream/downstream, coloration, layout. Fonctionnalités opérationnelles : detection datasets obsolètes, build depuis lineage, gestion schedules, rollback. Markings propagés automatiquement.

**Monocle** : outil de lineage/visualisation étendu couvrant le stack complet (data-to-ontology, actions, dépendances applicatives, santé pipelines). *"Graph viewer of the ETL"* — différenciant core de Foundry (ex-ingénieur Palantir, HN).

**Compass** : navigation et organisation. Data Catalog avec Collections, recherche full-text, Tags, Quicksearch universelle.

**Rubix** : implémentation durcie Kubernetes. Noeuds recyclés en **48h** (sécurité). FedRAMP High, DoD IL-5/IL-6, CMMC. `k8s-spark-scheduler` open-source pour gang scheduling Spark.

**Connecteurs** : **400+ connecteurs** (bases de données, SaaS, cloud, enterprise). Trois modes : Foundry Worker (cloud-side), Foundry Worker + Agent Proxy (on-prem), Agent Worker (legacy). SAP Add-On Certifié (Diskover, SLT CDC). Salesforce bidirectionnel. 15+ connecteurs JDBC.

---

## 6. Ontology Design Patterns

### 6.1 Primitives et framework de décision

**Analogie fondamentale** : Object Type = Dataset, Object = Row, Property = Column, Link = Join.

**Heuristique FDE** : *"Can someone walk up to this entity and ask questions about it in isolation?"* Si oui → Object Type. *"Will someone ever search for, filter on, or take an action on this entity independently?"* Si oui → Object Type.

| Créer un Object Type quand | Garder comme Property quand | Utiliser un Struct quand | Utiliser un Link quand |
|---|---|---|---|
| Identité et cycle de vie propres | Attribut simple 1-3 champs | Groupe borné 2-10 champs liés | Relation navigationnelle queryable |
| Primary key stable | Unique à son parent | Pas de cycle de vie indépendant | Entité partagée entre parents |
| Multiple entités la référencent | Jamais query indépendamment | Vit dans les contraintes struct | La relation a un sens |
| Permissions indépendantes | Change toujours avec le parent | Pas de liens nécessaires | |
| Actions indépendantes | | | |

**Exemple "Customer Address"** :
- **Property** : single-valued, change rarement
- **Struct** : composants structurés (street, city, zip), pas de cycle de vie indépendant
- **Object Type lié** : adresses multiples, historique, workflows de validation, geo-enrichissement

### 6.2 Conventions de nommage

- Object Types : **PascalCase singulier** (`Customer`, `WorkOrder`). Noms complets intuitifs, pas d'abréviations, pas de versions (`Message_v2`)
- Properties : **camelCase** (`firstName`, `orderDate`)
- Primary keys : colonne `id` de type string. IDs composites non hashés
- Foreign keys : `{foreign_object_type}_id`
- Link Types : **pluriel** côté pluriel (`subordinates`). Relations descriptives (`customer_orders`)
- Action Types : **verb-noun** (`CreateWorkOrder`, `AssignTechnician`)
- Timestamps : `{verbed}_at_timestamp`
- User references : `{verbed}_by_user` (stocker IDs Foundry comme `multipass_id`)
- Object Type IDs : auto-générés, **immutables après premier déploiement**
- Préfixes pour multi-tenant : `supply-chain-shipment`, `hr-employee`
- Statuts de maturité : Experimental, Active, Deprecated

### 6.3 DDD mapping

| Concept DDD | Équivalent Ontologie |
|---|---|
| Entity | Object Type |
| Value Object | Property ou Struct |
| Aggregate Root | Object Type primaire |
| Aggregate | Object Type + types dépendants liés |
| Bounded Context | Projet Ontologie / Groupe |
| Ubiquitous Language | Noms d'Object Type et Property |
| Domain Event | Action Type (ou Object Type dérivé) |
| Repository | Backing Dataset + Pipeline |

**Insight** : le concept DDD d'Ubiquitous Language est exactement ce que Palantir veut dire par *"Object Types and Actions must map to natural-language business concepts."* L'Ontologie EST l'Ubiquitous Language.

### 6.4 Templates par industrie

| Industrie | Standard | Object Types coeur | Étendu |
|---|---|---|---|
| Manufacturing | ISA-95 | 10-12 | 25-40 |
| Healthcare | HL7 FHIR (157 types) | 12-15 | 30-50 |
| Financial Services | FIBO (2 457 classes) / BIAN (~300 domains) | 8-12 | 25-45 |
| Retail/E-Commerce | GoodRelations / Schema.org (~800 types) | 10-12 | 20-35 |
| PME Générique | DDD patterns | 6-8 | 15-25 |

**ISA-95** : hiérarchie 5 niveaux (Enterprise/ERP → MOM/MES → Control → Sensors → Physical). Types coeur : Equipment, PhysicalAsset, Material, MaterialDefinition, Personnel, ProductionOrder, ProductionSchedule.

**FHIR** : 157 types de ressources. Coeur : Patient, Practitioner, Organization, Encounter, Condition, Observation, Medication, Procedure, DiagnosticReport, Claim.

**Schema.org** : 45M+ domaines web, 450Md+ objets (2024), 800+ types. Héritage multiple pragmatique, example-driven.

### 6.5 Entity Resolution

Spectre de techniques : matching par règles (déterministe), fuzzy/probabiliste (Levenshtein, Jaro-Winkler, Soundex, Fellegi-Sunter), ML (réseaux siamois, transformers), LLM (zero/few-shot, RAG multi-agents).

**Palantir** : Entity Resolution comme produit dédié. Pipeline multi-étapes : blocage (classification features), comparaison (ML + encodages sémantiques transformers), clustering. Boucles de feedback utilisateur entraînant les modèles ML. Dans les pipelines : expressions Levenshtein distance, déduplication standard et bornée dans le temps.

### 6.6 Schema evolution

**Non-breaking** : ajouter propriétés, changer display names/descriptions, supprimer propriétés sans edits.

**Breaking** : changer datasources, primary key, type de propriété, supprimer propriétés éditées.

**Framework de migration OSv2** : détection automatique des changements breaking, onglet Migrations bloquant la sauvegarde. Options : Drop edits, Move edits, Cast to new type, Revert. Max 500 migrations/opération. Pattern "replacement Funnel batch pipeline" pour mettre à jour l'index.

**Pattern side-by-side** : pour changements majeurs — créer nouvelle version du backing dataset, nouvel Object Type (v2), migrer consommateurs, basculer.

**Branching** : datasets et code sur branches, tester dans OMA sur branche, merger. Ontology-as-code : export JSON, édition externe, reimport.

---

## 7. FDE — Méthodologie Détaillée

### 7.1 Nature du rôle

Le FDE n'est ni sales engineer, ni solutions architect, ni consultant. Barry McCardel (ex-Palantir, CEO Hex) : le travail FDE traite les engagements comme de la **R&D plateforme, pas de la prestation de services**. Chaque solution est un primitif produit potentiel.

Marty Cagan (SVPG) : *"empowered engineers directly to spend intense time embedded with customers, with the express purpose of learning the problem and solution space."* Fondamentalement différent du conseil où *"the solution is being dictated to them."*

Le modèle suit l'**Auftragstaktik** (doctrine militaire de tactiques par mission) : dirigeants fixent des objectifs, toutes les décisions d'exécution aux équipes terrain. "Chaos" organisationnel intentionnel, compétition darwiniste entre solutions.

Le rôle FDE est celui d'un **CTO de startup intégré dans l'organisation de quelqu'un d'autre**.

### 7.2 Le pod vs. la pyramide du conseil

**Staffing MBB** : 1 Partner (10-33%) + 1 EM (100%) + 2 Associates (100%) + 2 BAs (100%). Pyramide de levier, marge ~48,5%.

**Pod Palantir** : 1 DS + 2 FDEs (pairs, pas de hiérarchie). Radicalement plus plat.

| Rôle Consulting | Équivalent Palantir | Changement |
|---|---|---|
| Partner | AE + senior DS | Séparation business dev / stratégie technique |
| Engagement Manager | DS | Suppression de "gérer des consultants" |
| Associate | FDE | Analyse-et-slides → construction-et-déploiement |
| Business Analyst | (éliminé) | Absorbé par l'outillage technique |
| Consultant Implémentation | FDE (même personne) | Pas de passation |

### 7.3 Discovery : le framework Impro

Basé sur *Impro: Improvisation and the Theatre* de Keith Johnstone — livre donné à chaque nouvelle recrue le Jour 1. Vocabulaire pour les **dynamiques de statut** (pouvoir non dit).

Concepts opérationnalisés :
- Comportement haut/bas-statut : *"Keeping your head still while talking is high status"*
- Transactions de statut dans chaque interaction
- *"Unusual sensitivity to social context"*

Zoe Scaman : le FDE doit devenir *"wallpaper — present enough to observe, invisible enough not to trigger the immune system."*

### 7.4 Techniques de découverte

Pas de guides d'entretien formels ni de frameworks structurés (RICE, ICE, MoSCoW) :
1. **Observation immersive** : *"SOPs are corporate fiction: static, incomplete, and often wildly outdated."*
2. **Approche du problème XY** : distinguer demandes énoncées vs problèmes sous-jacents
3. **Relations multi-niveaux** simultanées (terrain + dirigeants)
4. **Questionnement contextuel** : *"What does this person's day look like?"*
5. **Quick wins** : résoudre un point de douleur visible rapidement pour gagner confiance et accès

L'efficacité Palantir *"correlates directly to how quickly one can learn to speak the customer's language."*

### 7.5 Process mapping : observation, pas documentation

**Pas** de BPMN, VSM ou notation formelle. Étapes :
1. Observer le workflow réel (jours/semaines)
2. Reconstruire le processus basé sur l'observation
3. Mapper à l'Ontologie (Object/Link/Action Types)
4. Construire un prototype fonctionnel

Chez Airbus : *"Asana, but for building planes"* — work orders, missing parts, non-conformités — livré en *"a week or two."*

**Machinery** : capacité de process mining au niveau plateforme (mining de journaux d'événements). Outil plateforme, pas méthodologie primaire FDE.

### 7.6 Artefacts produits

**Primaires** : schémas d'ontologie, pipelines d'intégration, applications prototypes, configurations personnalisées.

**Secondaires** : diagrammes de flux (informels), documentation des processus (observés), matériaux de formation, notes de terrain hebdomadaires ("What I've Learned From Customers"), analyses de cause racine, catalogues de cas limites.

**Ce que les FDE ne produisent PAS** : decks PowerPoint stratégie, documents d'exigences détaillés, roadmaps long-terme, business cases formels.

### 7.7 Comparaison McKinsey Sprint vs Bootcamp

| Dimension | McKinsey Rapid Diagnostic | Palantir AIP Bootcamp |
|---|---|---|
| Durée | 2-6 semaines | 1-5 jours |
| Sortie | PowerPoint avec recommandations | Prototype logiciel fonctionnel |
| Données | Demandées, échantillonnées | Client live, ingérées dans Foundry |
| Travail | Consultants analysent | FDEs construisent ; clients co-construisent |
| Survit à l'engagement | Slides, modèles Excel | Application en cours d'exécution |
| Conversion | Proposition pour suivi | Démo live d'expansion |
| Coût | $250K-$1M+ | Souvent gratuit |

**Engagement MBB type** : 8-12 semaines, $500K-$1,25M. Day 1 Answer, diagnostic, analyse, synthèse, présentation finale.

**Ce que Palantir a emprunté** : immersion client, décomposition structurée, entretiens stakeholders, diagnostic rapide comme outil de vente, cultivation de champions, cartographie comme fondation.

**Ce que Palantir a changé** : slides → logiciel, élimination de la passation, modèle de revenus récurrents, inversion du levier (plateforme produit au lieu de main-d'oeuvre junior), vitesse ×5-10, client co-construit au lieu de regarder.

### 7.8 Carrière, compensation, turnover

**Usine à fondateurs** : *"more ex-Palantir founders than ex-Googlers in each YC batch, despite 50x more Google employees"* (Qureshi).

**Anciens notables** : Anduril ($14B+, Brian Schimpf/Trae Stephens/Matt Grimm), Affirm (Nathan Gettings), OpenAI (Bob McGrew), Fox/Melody Hildebrandt (CTO), Hex/Barry McCardel (CEO).

**Compensation (2025-2026)** : moyenne $238K, range $205K-$486K, Staff $630K+.

**Glassdoor** : FDSE **3,9/5** (156 reviews), équilibre vie/travail **2,7/5**. Horaires typiques 7h-19h + Slack. Pros : collègues brillants, impact réel, autonomie. Cons : *"a combination between tech support, data engineering, and low-code app building"*, *"flat hierarchy means power is political"*.

**Inflexion à 2-3 ans** : beaucoup quittent pour fonder, rejoindre des startups, ou prendre des rôles leadership.

### 7.9 Liste de lecture d'onboarding

1. *Impro* (Keith Johnstone) — dynamiques de statut
2. *The Looming Tower* (Lawrence Wright) — communauté du renseignement
3. *Interviewing Users* (Steve Portigal) — techniques d'entretien
4. *Getting Things Done* (David Allen) — productivité
5. *Principles* (Ray Dalio) — frameworks décisionnels

Notable pour ce qu'elle **exclut** : pas de livres d'ingénierie logicielle, pas de frameworks de conseil.

---

## 8. Brevets & Détails d'Implémentation

Palantir détient **3 438+ brevets** globalement (2 608 accordés, 80%+ actifs), avec 1 701 demandes à l'USPTO (taux d'octroi 95,08%).

### 8.1 Brevets Ontologie

**US7962495B2 / US9589014B2 — Ontologie Dynamique (2006)** : ontologie incarnée dans un schema de base de données (pas abstrait). Object Types identifiés par URIs (héritage RDF). Parser definitions éditables à l'exécution. Structure modifiable sans reconstruire le datastore.

**US20200293561A1 — Object Platform for Datasets (2020)** : 5 moteurs (datastore, definition, association, cache, interface). Les objets sont une **couche de vue** sur des données tabulaires avec cache (vues matérialisées). Résolution de conflits via **vector clocks** (système distribué). 3 APIs : Object Search, Object Load, Object Modify.

**US10754822B2 — Migration d'Ontologie (2020)** : migration basée sur des "stacks", **traduction d'identifiants** entre environnements (pas copie de données).

**US10061828B2 — Réplication Multi-Master Cross-Ontologie (2016)** : mappings One-to-One/One-to-Many/Drop Lists. Validation par **simulation aller-retour**. Digest cryptographique. Solution pour le partage inter-agences (CIA/NSA).

**US10248722 — Support Multi-Langue** : trois piliers (object/property/link types). Déploiements internationaux/coalition.

**US11461355B1 — Ontological Mapping of Data** : systèmes pour mapper données brutes → structures d'ontologie.

**US9946777B1 — Data Transformation** : génération de DSL depuis schema source + ontologie cible (Pipeline Builder).

**US10861203B1 — Ontology-Backed Chart Creation** : visualisation utilisée dans les démos bootcamp.

**US20200201855A1 — Curated Ontologies** : curation à la volée basée sur caractéristiques utilisateur/device.

**US20240354322A1 — LLM-Based Data Object Extraction** : LLMs pour auto-générer les mappings d'ontologie.

**US20230103939A1 — Synchronization Across Ontologies** : sync cross-système bidirectionnelle.

### 8.2 Brevets Pipeline

**US9946738B2 / US10853338B2 — Universal Data Pipeline (2014/2018)** : **immutabilité** (données jamais écrasées), delta encoding, protocole de transaction en 3 phases, DAG de dépendances, parcours post-order pour séquencement, rebuilds en cascade via file de messages. Langages : SPARK SQL, HIVEQL, GROOVY. Build Catalog pour traçabilité complète.

**Révélation** : le système de pipeline est un **contrôle de version git-like pour datasets** avec orchestration DAG.

**US10754752B2 — Monitoring (2020)** : collecteurs filesystem/application/database/hardware, détection d'anomalies statistiques, déduplication et auto-résolution.

**US20210149857A1 — Branching Pipeline (2020)** : branche master → branche test (copy-on-write) → merge. **Branching git pour pipelines de données**.

**US20250094439A1 — Optimisation Réponse LLM pour Pipeline Generation (2024, pending)** : langage informatique propriétaire **2-100x plus efficient** que JSON en tokens. Parsers ANTLR. Instructions de "mistake context" dans les prompts (prévention d'erreurs few-shot).

**US8930897B2 — Outil d'Intégration (2015)** : debugging proactif vérifiant les conditions avant exécution (précurseur Pipeline Builder).

**US10866792B1 — Rules-Based Cleaning of Deployment Pipelines** : validation automatisée (noms invalides, types invalides, données stale, branches cassées).

**US20160314155A1 — Data Integration Pipeline** : architecture deux phases (ingest + import).

### 8.3 Brevets Workshop/UI

**US11500620B2 / US12260192B2 — Workshop (2022)** : widgets modulaires dans containers, **type safety** (ontologie = système de types pour builder no-code), liaison réactive, function registry séparé, preview WYSIWYG.

**US11842171B2 — Function Access System (2023)** : 5 composants architecturaux. **Régénération automatique d'API** sur changements ontologie. Exécution sandboxée avec limites de ressources. Acces à niveaux de permissions **au niveau API**.

**US20230289153A1 — Workflow Application and UI Builder** : architecture de Workshop.

### 8.4 Brevets Apollo

**US10263845B2 — Déploiement Configuration Continue (2019)** : repository hiérarchique central, **pré-caching** avant fenêtres de maintenance, génération context-aware, **capacité mesh** (pairs bootstrapping), exécution automatisée.

**Réconciliation état désiré** (pattern Kubernetes). Déploiement frontend par **tracks** (canary/feature flagging).

**US11444854 — Métriques d'Utilisation (2022)** : télémétrie centralisée depuis tous les environnements.

### 8.5 Brevets Sécurité

**US9081975B2 / US9836523B2 — Partage Multi-Classification (2015)** : markings de classification (TS/S/C/R/U) + classifications d'origine. Règles de traduction **asymétriques**, traduction par chemin le plus court. Support domaines hybrides (CBAC, RBAC, sans framework). Rend Palantir déployable à travers la communauté du renseignement.

**US9857960B1 — Collaboration de Données (2018)** : 5 critères de rédaction progressifs. Export graphe sérialisé + audit. Déconfliction par timestamp.

**US20230306000A1 — Partage d'Actifs (2023)** : partage par mise à jour de markings (pas de déplacement de données). **Révocation transitive** via chaîne de lineage. Minimisation de données automatique (colonne/ligne).

**US11593317B2 — Journalisation Inviolable (2023)** : double-datastore append-only immutable. Chunks 50 Ko chiffrés/compressés/hashés (SHA-1/SHA-512). Hash comme adresse (stockage adressable par contenu). Détection multi-couche incluant journalisation des frappes clavier.

### 8.6 Brevets AI/LLM

**EP4443310A1 — Interfaces Système IA (2024)** : architecture 3 couches (Orchestrator Selector → Service Orchestrators → Data Processing Services). LLMs pour sélection de service et formatage. In-prompt training. Architecture plugin. Outils : Ontology function, date/time, query objects, calculator, **apply action**.

**Révélation** : AIP est un **système d'orchestration multi-agent** où le LLM agit comme routeur.

**US20240419658A1 — IA Basée sur Profils (2024)** : profil 4 composants (Knowledge Bases, Functions, Plugins, Templates). Plugins activent avant ET après l'exécution LLM — architecture workflow.

**US20240346388A1 — Entraînement LLM Sécurisé (2024, pending)** : datasets segmentés par **niveau de permission**, modèles séparés par tier de sécurité. Routage à l'inférence vers le modèle approprié. Fondamentalement plus sécurisé que RAG + filtrage post-generation.

### 8.7 Patterns architecturaux transversaux (révélés par les brevets)

1. **L'ontologie est une surcouche de métadonnées** sur des datasets tabulaires avec cache
2. **Tout est versionné et immutable** (datasets, configurations, audit logs)
3. **Gestion de dépendances par DAG** (pipelines, widgets, configurations)
4. **Résolution de conflits par vector clocks** (distribué, multi-master)
5. **Sécurité comme métadonnée de première classe** (markings traversent tout)
6. **Architecture mesh multi-environnement** (bootstrapping par pairs, air-gapped)

---

## 9. AIPCon & Preuves Concrètes

### 9.1 Timeline des événements

| Événement | Date | Faits saillants |
|---|---|---|
| Demo Day inaugural | Jan 2021 | Première démo publique Foundry/Gotham/Apollo |
| **AIPCon 1** | 1 juin 2023 | Lancement AIP, démo Sankar 20 min, 25+ clients |
| **AIPCon 2** | 14 sept 2023 | 100+ orgs en <6 mois ; HCA Healthcare scaling rapide |
| **AIPCon 3** | Juin 2024 | ~70 clients, AIP Evaluator, Tampa General $50M/7 ans |
| **AIPCon 4** | 12 sept 2024 | 100+ orgs, NGA/Dept of State première publique, Tyson GPT-4o |
| **DevCon 1** | Nov 2024 | OSDK 2.0, Workflow Builder, Agent Studio beta, 150 participants |
| **AIPCon 6** | Mars 2025 | Warp Speed manufacturing OS, Anduril 200x MRP |
| AIPCon 7 | Juin 2025 | Expansion continue |
| **AIPCon 8** | Sept 2025 | Nebraska Medicine 10h build, Ursa Major MES |
| DevCon 2-4 | 2025 | Séries conférences développeurs |

### 9.2 Démos marquantes

**AIPCon 1** — "What You Say Is What You Get" (requêtes langage naturel en anglais/allemand/ukrainien). AIP Terminal : supply chain, $13M de revenus à risque identifiés, *"300 minutes to 3 minutes, with agents potentially solving in 3 seconds."* Construction d'apps via langage naturel (~80% auto-généré). AIP Logic IDE : 5 000+ function runs avec traces complètes.

**AIPCon 3** — SwissRE : données forensiques policieres + assurance, workflows multi-modaux (vidéo/image). *"I haven't seen another application that can do that."* BYOD : moteur de recommandation de livres en quelques minutes.

**AIPCon 6** — **Warp Speed Manufacturing OS** (Arsenal OS) : *"re-industrializing American manufacturing."* Cohorte inaugurale : Anduril, L3Harris, Panasonic PENA, Shield AI, Red Cat, Saildrone, Saronic, SNC, Ursa Major.

**AIPCon 8** — **Nebraska Medicine** : solution Guideline Evaluation construite en **10 heures**. Croisement données cliniques / exigences assurance. De 1 à 20+ use cases en 6 mois. **Ursa Major** : MES AI-natif Ontology-driven Warp Speed.

### 9.3 Quotes clés des earnings calls

**Vitesse de conversion** :
- Deal 7 chiffres **5 jours** après bootcamp (utility company, Q1 2024)
- Engagement payé **1 jour** après bootcamp, conversion 7 chiffres 3 semaines plus tard
- Deal 7 chiffres ACV **16 jours** après bootcamp (courtier d'assurance, Q2 2024)
- Healthcare company : bootcamp en avril, **$88M TCV** un mois plus tard (Q2 2025)
- Healthcare company : 2 bootcamps l'été, **$96M deal** avant fin d'année (Q4 2025)
- Engineering services : démos automne, **$80M deal** avant fin d'année (Q4 2025)

**Impact opérationnel** :
- Assurance : **78 AI agents**, processus de **2 semaines à 3 heures** (Q3 2024)
- Maven : ciblage avec **20 personnes** au lieu de **2 000** (Q3 2024)
- Trinity Rail : workflow fonctionnel en **3 mois**, **$30M impact** (Q3 2024)
- Banque multinationale : **5 jours à 3 minutes** (Q4 2024)
- **100 heures** de revue ingénieur, automatisées (Q4 2024)
- Citibank : onboarding de **9 jours à secondes** (Q2 2025)
- Fannie Mae : détection fraude de **2 mois à secondes** (Q2 2025)
- Nebraska Medicine : **2 100% increase** discharge lounge utilization (Q2 2025)

**Expansion de comptes** :
- Location d'équipement : ARR **×12** en <8 mois (Q3 2024)
- Medical device manufacturer : ACV **×8** en 5 mois (Q3 2025)
- Utility : $7M → **$31M ACV** en un an (Q4 2025)
- Energy : $4M → **$20M+ ACV** en un an (Q4 2025)

**Citations définissantes** :
- Karp : *"LLMs are like genies of the lamp. AIP is the lamp that controls them."*
- Karp : *"We're exporting our culture... by allowing enterprises to capture their tribal knowledge."*
- Taylor : *"Our ontology is pure understanding, concretized in software."*
- Taylor : *"LLMs simply don't work in the real world without Palantir."*
- Sankar (Q1 2025) : *"AIP is proving to be the best harness to build, test, evaluate, and deploy agents to eat the elephant of the enterprise."*
- Karp (Q4 2025) : *"Speed to production and transformational scale is no longer optional; it's existential."*

### 9.4 AIFDE (AI Forward Deployed Engineer)

**Capacités** : intégration/transformation données, développement ontologie, création fonctions, construction Workshop, architecture sécurité (branching par défaut, propositions pour revue humaine, boucle fermée). Modèles : Anthropic, OpenAI, Google, xAI.

**Arc stratégique** :
- Q2 2025 : introduction comme outil de productivité
- Q3 2025 : migration data warehouse en **5 jours** (2 humains + armée d'AI FTEs vs 2 ans pour SIs)
- Q4 2025 : migrations SAP ECC → S/4 en **2 semaines**
- *"This is not a prototype. This is production."*

Sankar : *"AIFDE understands how to connect to data sources, integrate and transform data, create ontologies and functions, and build applications."*

### 9.5 Case studies majeurs

**Airbus Skywise** (2015-2026, ~11 ans) : 140+ airlines, **50 000+ utilisateurs**, 11 900+ avions connectés (50% flotte Airbus en service). Skywise App Store 19+ apps. Tiers X1/X2/X3. Revenu estimé **~94 M$/an**. Self-service significatif en 2-3 ans. Renouvellement multi-années (février 2026). Cas concret : investigation valves haute pression A330neo → Airworthiness Directive.

**bp** (2014-2024+, ~10 ans) : des plateformes offshore à **2M+ capteurs** en jumeau numérique unifié. Accord stratégique 5 ans (septembre 2024) avec AIP.

**Lear Corporation** (2023-2025) : expansion rapide. **11 000 employés**, **30 M$+ d'économies S1 2025**. Expansion 5 ans (septembre 2025) Foundry + Warp Speed + AIP.

**NHS England** (2020-2026) : entrée pour **1 £** pendant Covid. 1 M£ → 23 M£ → **330 M£** FDP (novembre 2023). Seulement **34 trusts (15%)** utilisaient activement à mi-2025. Mandat FDP pour tous les fournisseurs d'ici avril 2026.

**US Army** (2010s-2025+) : Vantage ($115M extension), Maven Smart System ($480M → $1Md+), **Enterprise Agreement 10 Md$** (75 contrats consolidés, 10 ans). **TITAN** : premier véhicule AI-defined (mars 2024). 20 000+ utilisateurs, 35+ outils, 3 domaines de sécurité, 5 commandements de combat.

**1 milliard+ de requêtes API gateway/semaine** depuis les applications clients (Q4 2025).

---

## 10. Déploiement Data pour PME (contexte Spider)

### 10.1 Méthodologie Odoo

**6 étapes** : Kick-off → Préparation → Configuration & Développement → QA → Déploiement → Go-Live & Support.

**Timelines** :

| Taille | Timeline |
|---|---|
| Petite (setup basique) | 2-4 semaines |
| Moyenne (50-200 employés) | 2-3 mois |
| Multi-module PME | 8-12 semaines (approche phasée) |
| Enterprise complexe | 6+ mois |

27,9% des implémentations ERP utilisent l'approche phasée par module (la plus courante).

**Migration de données** : aspect le plus sous-estimé. Exemple : 6 fichiers Excel différents pour les données client seules. Coûts : quelques milliers à $20K+.

**Coûts pour 50-200 employés** : implémentation initiale $50-100K+, récurrent annuel ~$50K, taux horaire $50-150/h. Total 1ère année ~$130K.

**Modes d'échec** : objectifs flous (38,4% staffing, 34,9% scope creep, 33,7% problèmes techniques/données). **Seulement 49,7% finissent dans les délais, 46,4% dans le budget.**

### 10.2 Data readiness des PME

**Infrastructure typique (10-50M EUR)** :
- Moyenne 58 apps déployées (36 pour <50 employés)
- 66% citent l'intégration comme défi principal
- 64% utilisent un ERP, mais seulement 26% des employés l'utilisent activement
- **Adoption cloud France** : 22,9% en 2023 vs 38,9% UE
- **Adoption IA France** : 5,9% vs 8,0% UE
- Intensité digitale PME françaises : 52% basique vs 57,7% UE
- Analytics : Excel quasi-universel (**70-90%**, le chiffre Gartner 87% le plus défensible)

**Paysage systèmes** : Comptabilité/ERP (Sage, Cegid, Odoo en France ; SAP B1, DATEV en Allemagne). CRM (HubSpot, Salesforce, ou rien/Excel). RH : souvent paie seule. Analytics : **Excel**.

**Modèle de maturité analytics** :

| Stade | Description | Prévalence PME |
|---|---|---|
| 1. Ad Hoc | Analyse manuelle, réactive | ~40-50% |
| 2. Descriptif | Reporting basique | ~25-30% |
| 3. Diagnostique | Identification de patterns | ~10-15% |
| 4. Prédictif | Modèles de prévision | ~3-5% |
| 5. Prescriptif | Optimisation | <1% |

**Timeline Excel → plateforme structurée** : MVP 4-8 semaines, multi-source 2-4 mois, analytics complète 6-12 mois, prédictif/IA 12-24 mois.

### 10.3 Change management

**Ce qui fonctionne** : quick wins d'abord (2-4 semaines), champions cross-fonctionnels (3-5/département), implication = appropriation, "governance-lite".

**Champion dans une PME** :
- **CEO/DG** : sponsor initial, *"reactive rather than proactive"*
- **CFO** : de plus en plus l'évangéliste technologique (*"essential voice in key decision-making"*)
- **Pas d'équipe IT** : 70% des adoptions réussies reposent sur la collaboration cross-fonctionnelle

**Patterns de résistance** : *"Je ne sais pas par où commencer"* (30%), *"Je n'ai pas les compétences"* (26%), *"Ça marche bien comme ça"*, peur du remplacement.

**Formations efficaces** : étape par étape (50%), conseils outils (42%), workshops (38%). Critique : formation spécifique au rôle.

### 10.4 Différences culturelles

**PME françaises** : adoption cloud/IA sous moyenne UE, culture de conformité réglementaire (RGPD, CSRD, facture électronique), sensibilité aux coûts/scepticisme ROI, **relationship-driven**.

**Mittelstand allemand** : owner-managed, décisions rapides, culture planification long-terme, gap compétences digitales (47% moyennes entreprises ont staff ICT, 15% petites), qualité > vitesse.

**PME US** : "move fast", adoption rapide, préférence self-serve, moins de friction réglementaire.

### 10.5 Template de déploiement Spider

**Phase 0 : Découverte (1-2 semaines)** — Entretien CFO/CEO, cartographie sources, identifier 1-2 use cases à impact, définir métriques.

**Phase 1 : Intégration & Quick Win (2-4 semaines)** — Connexion sources primaires (API Odoo/Sage/Cegid, feeds bancaires, Excel), templates industrie pré-construits, premier dashboard fonctionnel, formation 3-5 utilisateurs clés.

**Phase 2 : Expansion (Mois 2-4)** — Sources secondaires, départements additionnels, analytics cross-fonctionnelles, base utilisateur élargie.

**Phase 3 : Intelligence (Mois 4-12)** — Modèles prédictifs, détection d'anomalies, alertes automatisées.

**Benchmark prix** : 15-40K EUR implémentation + 15-50K EUR abonnement annuel (significativement moins qu'ERP, plus que SaaS onboarding).

**Facteurs critiques** :
1. Time to first value < 4 semaines
2. CFO comme champion (langage : ROI, visibilité marges, prévision trésorerie)
3. Template-first, customiser ensuite
4. La qualité des données est le problème de Spider, pas du client
5. Modèle d'onboarding hybride
6. Formation role-based
7. France : confiance par relations personnelles, conformité réglementaire comme valeur

**Benchmarks SaaS** : HubSpot onboarding ~90 jours ($999-$7000), Salesforce mid-market $450K-$2M (12-18 mois). Vanta automatise 90% conformité. Rippling implémentation en 3 semaines. Seuil self-service vs white-glove : $10K-$100K ARR = zone hybride (cible Spider 20-80K EUR).

---

## 11. Contradictions Inter-Sources

### [C1] Taux de conversion des bootcamps
- **Claude** : 30-50% mènent à un engagement payé
- **Perplexity** : ~70% convertissent en contrats payés dans un trimestre, deal moyen >1M$
- **GPT** : Palantir ne publie pas les taux ; SEC filings confirment que la conversion n'est pas garantie
- **Synthèse 3** : estimations d'analystes 50-70%
> La divergence est significative. Les taux réels ne sont pas publiés.

### [C2] Nombre de participants bootcamp côté client
- **Claude** : 8-12 participants (pour un bootcamp initial standard)
- **Perplexity** : 5-20 stakeholders (pour un bootcamp initial)
- **Synthèse 3** : 20-50 participants (pour un bootcamp d'expansion multi-département)
> Le nombre varie selon le type de bootcamp (initial vs expansion) et la taille du client.

### [C3] Nombre de FDEs par bootcamp
- **GPT** : 1-3 FDEs/AI Engineers
- **Claude** : 1-2 FDEs (équipe totale 2-5 Palantir)
- **Perplexity** : 1-2 FDEs/FDSEs
> Convergence sur 1-3 avec variations mineures.

### [C4] Taille équipe pilote DS/FDE
- **Claude** : 1 DS + 2-4 FDEs
- **Perplexity** : 2-3 FDSE + 1-2 DS (4-5 total)
> Convergence sur 3-5 personnes, divergence sur répartition exacte.

### [C5] Framework de cadrage des use cases
- **Claude** : emprunte au design thinking et JTBD, framework à 4 axes
- **Perplexity** : *"pas formellement du design thinking ou JTBD"* — propre framework Palantir
> Le framework est propriétaire mais influence par design thinking/JTBD.

### [C6] Nombre de use cases sélectionnés au Jour 1
- **GPT** : 3-5 target workflows
- **Claude** : 1-2 primary use cases
- **Perplexity** : raffinement de 5 à 2-3 primary builds
> Pas contradictoire si on distingue "explorés" (3-5) vs "construits" (1-2).

### [C7] Qui présente au Jour 5
- **Perplexity** : le **client** présente (*"creates internal advocates and ownership"*)
- **Claude/GPT** : le DS narre, le FDE conduit la démo
> Le format varie probablement selon le bootcamp (client co-présente dans certains cas).

### [C8] Roadmap de déploiement post-bootcamp
- **Claude** : Phase 1 (semaines 1-8, durcissement), Phase 2 (8-16, rollout), Phase 3 (mois 4-12, scale)
- **Perplexity** : 5 résultats séquentiels de 1 jour à 6-9 mois
> Perspectives complémentaires (technique vs business) plutôt que contradictoires.

### [C9] Taille de deal initial
- **Claude** : 100K$-500K$ annuels (PoV/pilote), expansion 1M$-10M$+
- **Perplexity** : ~1M$+ mid-market, 10M$+ grandes entreprises/gouvernement
> Reflète des segments de marché différents (le PoV Claude est plus bas car c'est un pilote initial).

### [C10] Net Dollar Retention
- **Claude** : 115-120%
- **Perplexity** : 134% (US commercial)
- **Synthèse 3** : 124% (Q1 2025), 107% plancher (Q3 2023), 150% pic
> NDR varie par segment et trimestre. Les chiffres ne sont pas contradictoires mais mesurent des choses différentes.

### [C11] Nombre d'entretiens stakeholders en découverte
- **Claude** : 10-30 dans les deux premières semaines
- **GPT** : pas de nombre prescrit dans la documentation
- **Perplexity** : pas de chiffre précis
> Claude est le seul à donner un chiffre — probablement une estimation raisonnable.

### [C12] Répartition temps entretiens/observation
- **Claude** : 60% entretiens / 40% observation
- **Perplexity** : en manufacturing, 20-30% configuration, reste observation/questions
> Varie selon l'industrie et la phase.

### [C13] Heures de formation
- **Claude** : power users 8-16h, standard 2-4h
- **Perplexity** : power users 16-40h, standard 4-8h
> Perplexity donne des fourchettes plus larges et élevées.

### [C14] Timing formation CoE
- **Claude** : 6-18 mois après début
- **Perplexity** : 6-12 mois
- **GPT** : lié au seuil multi-use-case/multi-domain (Phase 3)
> Fourchettes se chevauchent.

### [C15] Accès sandbox post-bootcamp
- **Claude** : 30-90 jours
- **GPT** : time-bounded, non permanent, pas de durée spécifiée
- **Perplexity** : reste accessible (durée non précisée)
> Claude est le seul à donner une fourchette précise.

### [C16] Coûts de switching
- **Claude** : 2-5x valeur annuelle du contrat, potentiellement 50-200M$ pour grands déploiements
- **Perplexity** : 2,5-7,5M$ par client enterprise (détail par composant)
> Ordres de grandeur très différents — Claude inclut les très grands déploiements.

### [C17] Sortie NHS
- **GPT** : transition et exit service de 12 mois (produits Covid)
- **Perplexity** : adoption difficile mais en cours (pas de mention de sortie)
> Pas mutuellement exclusif : sortie partielle produits Covid + difficulté adoption FDP.

### [C18] Triade FDE/DS/AE vs Echo/Delta/Core
- **Claude** : triade FDE/DS/AE
- **Perplexity** : modèle Echo/Delta/Core Product
> Non exclusif : Echo/Delta/Core = ingénierie, FDE/DS/AE = rôles commerciaux-stratégiques.

### [C19] Rôle UI designer dans l'équipe
- **GPT** : le DS travaille avec des Product Designers
- **Perplexity** : pas de rôle dédié UI designer, le FDE construit l'UI
> Dépend probablement de la taille du compte.

### [C20] Testing formel des pipelines pendant le pilote
- **GPT** : testing formel comme partie intégrante du processus
- **Perplexity** : *"la culture valorise la vitesse sur la couverture de tests pendant la phase pilote"*
> Tension réelle entre idéal et pratique.

### [C21] Mécanisme de write-back des Actions
- **Claude** : Edits dataset append-only, fusion avec backing datasets, réconciliation périodique
- **Perplexity** : writeback dataset avec deux modes de permission
> Perspectives différentes du même mécanisme.

### [C22] Types Set et Map dans les propriétés
- **Claude** : liste Set et Map comme supportés
- **GPT/Perplexity** : ne les mentionnent pas
> GPT cite explicitement une liste "load-bearing" sans Set/Map. Claude probablement incorrect.

### [C23] Outil de migration ontologie
- **Claude** : *"no built-in migration tool"* (type Flyway/Liquibase)
- **GPT/Perplexity** : framework de migration intégré dans OSv2
> Claude décrit probablement l'état OSv1 / état général ; GPT et Perplexity décrivent la fonctionnalité OSv2 spécifique.

### [C24] Mixing visuel et code dans Pipeline Builder
- **Claude** : *"fully supported"* via Custom Code node (éditeur Monaco)
- **GPT** : *"Not inside a single Pipeline Builder"* — mixing au dataset boundary
- **Perplexity** : *"doesn't directly embed PySpark code"* — prototyper en PB, shift complexe en Code Repos
> Contradiction significative. GPT et Perplexity convergent sur le mixing au dataset boundary.

### [C25] AIP Logic runtime — LLM au développement vs à l'exécution
- **Claude** : LLM utilisé au **développement** pour générer du code TypeScript déterministe déployé
- **GPT/Perplexity** : fonctions qui **utilisent** des blocs LLM au **runtime** avec traces de raisonnement
> Contradiction fondamentale sur l'architecture. GPT et Perplexity sont plus cohérents avec les démos publiques (traces de raisonnement runtime).

### [C26] Column-level lineage
- **Claude** : inféré en parsant le Catalyst logical plan Spark, tracking explicite par noeud
- **GPT** : "find datasets with a given column" existe, mais lineage cellule/ligne n'est pas standard
- **Perplexity** : ne mentionne pas
> Claude est le seul à décrire un column-level lineage détaillé.

### [C27] Sneakernet / déploiement air-gap
- **GPT** : *"docs publiques ne décrivent pas les mécaniques en détail"*
- **Claude** : *"signed, encrypted deployment bundles"* via cross-domain solutions ou media physique
- **Perplexity** : détails précis sur Apollo Bundles (diffs compressés, checkpoints)
> Claude et Perplexity convergent sur les détails. GPT est plus prudent.

### [C28] Méthode "100 use cases" du bootcamp d'expansion
- **GPT** : *"matériaux publics ne décrivent pas une méthode canonique de facilitation"*
- **Claude** : exercice sticky-note/whiteboard avec canevas template, prototypes 1-3 en temps réel
> GPT est factuel (pas de source officielle), Claude reconstruit à partir de sources secondaires.

### [C29] Jours sur site FDE par semaine
- Qureshi : 3-4 jours/semaine
- Comparaison consulting : *"Palantir embeds FDEs full-time"*
> 3-4 jours est la réalité documentée ; "full-time" est une simplification dans le contexte de comparaison.

### [C30] Frameworks formels de priorisation
- FDE methodology : *"do not use formal frameworks like RICE, ICE, MoSCoW"*
- Consulting comparison : approches structurées MECE utilisées par les DS
> Les DS utilisent des approches structurées ; les FDEs priorisent intuitivement. Les deux coexistent.

### [C31] Durée du problème d'accès aux données
- FDE methodology : pilotes de 8-12 semaines, *"spent all 8-12 weeks just getting data access"*
- Demos/bootcamps : conversions en 1-5 jours avec succès
> Les bootcamps utilisent des static cuts pré-fournies, contournant le problème. Les pilotes affrontent l'accès production.

---

*Sources des 5 synthèses fusionnées :*
- *(GPT)* = rapports GPT (presales, pilot, expand, foundry tools)
- *(Claude)* = rapports Claude (bootcamp, pilot, expand, foundry tools)
- *(Perplexity)* = rapports Perplexity (bootcamp, pilot, expand, foundry tools)
- *(Claude Agents)* = 8 rapports d'agents Claude (FDE methodology, Workshop UI, Pipelines & OSDK, Ontology Design, Brevets, AIPCon, PME)*
- *Les faits non annotés sont confirmés par au moins deux sources.*
