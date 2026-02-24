# ANNEXE A2 — REFERENCE PALANTIR COMPLETE
## Tout ce que Spider doit savoir sur Palantir, distille en un document

> **Date de compilation :** 21 fevrier 2026
> **Sources :** 7 documents de recherche primaires (50+ sources secondaires : SEC filings, earnings calls Q1 2023 - Q4 2025, AIPCon 1-8, DevCon 1-4, Glassdoor 156 reviews FDSE, Gartner Peer Insights, investigations journalistiques, brevets USPTO, comptes-rendus ex-employes)
> **Avertissement de confiance :** Les faits marques [CONFIRMED] ont au moins 2 sources independantes. [ESTIMATED] = inference raisonnee. [SPECULATIVE] = extrapolation.

---

## 1. PALANTIR EN 60 SECONDES

### Metriques cles FY2025 (annee fiscale close decembre 2025)

| Metrique | Valeur | Variation YoY |
|----------|--------|--------------|
| Chiffre d'affaires | **$4.475B** | +56% |
| Revenue Q4 2025 | $1.407B | +70% |
| US Commercial Revenue | $1.465B | **+109%** |
| Net Dollar Retention (NDR) | **139%** | Record absolu |
| Clients totaux | **954** | +34% |
| GAAP Gross Margin | **84%** | En expansion |
| Free Cash Flow (ajuste) | $2.27B | +82% |
| Net Income GAAP | $1.625B | +250% |
| Revenue per Employee | **$1.01M** | Elite (ServiceNow : $550K) |
| Market Cap (fev 2026) | ~**$313B** | |
| Revenue guidance FY2026 | $7.19B | +61% guide |
| TCV Q4 2025 | $4.3B | +138% YoY |
| Expansion multiple moyen | **56x** ($100K -> $5.6M ACV) | |
| Revenue top 20 clients | **$94M+ / client** en moyenne | |
| Bootcamps conduits | 1,300+ | Cadence : ~5/jour en 2024 |
| FDEs chez Palantir | ~2,000-3,000 [ESTIMATED] | |

### Trajectoire revenus FY2020 - FY2026E

| Annee | Revenue | Croissance |
|-------|---------|-----------|
| FY2020 | $1.09B | — |
| FY2021 | $1.54B | +41% |
| FY2022 | $1.91B | +24% |
| FY2023 | $2.23B | +17% |
| FY2024 | $2.87B | +29% |
| **FY2025** | **$4.475B** | **+56%** |
| FY2026E | $7.19B | +61% guide |

**Point d'inflexion :** Le lancement d'AIP en avril 2023 marque le tournant. La croissance est passee de +17% a +56% en deux ans.

### NDR — Trajectoire historique

| Periode | NDR | Note |
|---------|-----|------|
| Q3 2023 | 107% | Creux pre-AIP |
| Q4 2024 | 120% | |
| Q3 2025 | 134% | +600 bps QoQ |
| **Q4 2025** | **139%** | **Record historique** |

Un NDR de 139% signifie que les clients existants depensent en moyenne 39% de plus chaque annee — sans acquerir un seul nouveau client.

---

## 2. LE MODELE COMMERCIAL — LES 4 PHASES

Palantir ne "vend" pas un logiciel. Palantir investit dans des clients qui deviennent des machines a expansion. La progression suit 4 phases avec des economics radicalement differents a chaque etape.

### Vue d'ensemble du flywheel

```
BOOTCAMP (gratuit, 5 jours)
    |
    v  ~22% conversion
PILOT / ACQUIRE ($100K-$500K, 3-6 mois, marge -43%)
    |
    v  expansion organique
EXPAND ($500K-$5M ACV, 6-24 mois, marge -43% → +35%)
    |
    v  auto-service
SCALE ($5M-$20M+ ACV, 24+ mois, marge +55%)
         |
         +---> Feedback FDE → amelioration produit → meilleur bootcamp suivant
```

**Expansion multiple documente : 56x** (de $100K initial a $5.6M ACV mature)

### Phase 1 — BOOTCAMP (Acquisition, Semaine 0)

**Cout pour le client :** Gratuit [CONFIRMED]
**Cout pour Palantir :** $12,000-$36,000 par bootcamp [SPECULATIVE] (1-5 jours x 5-8 personnes)
**Conversion :** ~22% en pilot paye [ESTIMATED]

Palantir organise environ 5 bootcamps par jour globalement. Ce n'est pas un canal parmi d'autres — c'est LE canal principal (Ted Mabrey, Head of Global Commercial : *"Our primary means of going to market with AIP will be through these bootcamps"*).

### Phase 2 — PILOT / ACQUIRE (Mois 0-6)

| Parametre | Valeur |
|-----------|--------|
| ACV | $100K - $500K |
| Marge contribution | **-43%** |
| FDEs embarques | 4-5 / client |
| Duree | 3-6 mois |
| Objectif | Prouver la valeur sur un cas d'usage reel |
| Use cases construits | 1-3 |
| Sources de donnees connectees | 3-10 |

**Colin Anderson (ex-CFO, Palantir) :** *"The model is only financially sustainable for seven-figure contracts and above, with eight or nine figures being the sweet spot."* Le pilot est un investissement en R&D, pas une source de revenus.

Exemples de conversions rapides (earnings calls) :
- Utility company : 7-figure deal signe **5 jours** apres le bootcamp
- Wholesale insurance : closed $1M+ ACV deal **16 jours** apres le bootcamp
- Convenience store chain : prototype → pilot paye → production en **25 jours**

### Phase 3 — EXPAND (Mois 6-24, $250K → $1-5M ACV)

| Parametre | Valeur |
|-----------|--------|
| ACV | $500K - $5M |
| Marge | -43% → +35% (breakeven ~mois 9) |
| FDEs | Decroissant, Centre of Excellence en construction |
| Objectif | Multi-departements, 10-30 use cases, adoption virale interne |
| Champions internes | Formes comme builders certifies |
| Ontologie | Passage de 5-15 a 100-500 object types |

**Mecanismes d'expansion :**
1. Nouveau use case → nouveau departement capte par un champion interne
2. "Build with AIP" bootcamps internes (employes du client comme participants)
3. ROI demontre sur Phase 1 → budget debloque pour Phase 2
4. Ontologie etendue → chaque nouveau use case cout marginal proche de zero

### Phase 4 — SCALE (Annee 3+, $5-20M+ ACV)

| Parametre | Valeur |
|-----------|--------|
| ACV | $5M - $20M+ (top 20 : $94M+ en moyenne) |
| Marge | **+55%+** |
| FDEs | 0-1 (graduation deliberee) |
| Objectif | Auto-service, Centre of Excellence autonome, protection des revenus par le lock-in |
| Ontologie | 500-1,000+ object types, digital twin de l'organisation |
| Contrats | Multi-annees (5-10 ans pour gouvernement) |

**Cas Lear Corporation :** Le cas le plus demonstratif.

| Metrique | Pilot | Scale | Multiple |
|----------|-------|-------|---------|
| Utilisateurs | 100 | 16,000 | 160x |
| Use cases | 4 | 280 | 70x |

**Prix par phase (G-Cloud UK, reference publique) :**

| Niveau | Licence annuelle | Profil client |
|--------|-----------------|--------------|
| Level 0 | £250,000 | Pilot / POC |
| Level 1-3 | £500K - £2M | Multi-equipes |
| Level 4-7 | £2M - £25M | Enterprise-wide |
| Level 8-11 | £25M - £200M | Ministere / grand compte |
| Level 12-15 | £200M - £1B | Programmes nationaux (NHS) |

---

## 3. LE BOOTCAMP AIP — DETAIL OPERATIONNEL

### Vue d'ensemble

Le Bootcamp AIP est une semaine d'immersion intensive (typiquement 5 jours) ou Palantir envoie une equipe d'ingenieurs chez le client pour construire un prototype fonctionnel sur les donnees reelles du client, gratuitement.

**Shyam Sankar (CTO) :** *"The boot camp is not a demo. It's not a presentation. We show up with engineers, and we build."*

Ryan Taylor (CRO, Q3 2023) : *"We reoriented our go-to-market approach around AIP boot camps, which has allowed us to deliver real workflows on actual customer data in five days or less versus our traditional pilots, which generally take one to three months."*

### Volume de bootcamps

| Periode | Cumule |
|---------|--------|
| Mi-2023 | ~50 |
| Fin Q3 2023 | ~100 |
| Fin Q4 2023 | **560+ bootcamps, 465+ organisations** |
| Fin Q1 2024 | 915+ |
| Juin 2024 | **1,300+** |
| Cadence 2024 | **~5 bootcamps par jour** (Bloomberg) |

### Prerequis client pour un bootcamp ("Bootcamp-Ready")

| # | Critere | Detail |
|---|---------|--------|
| 1 | Participants confirmes | 5-20 stakeholders : C-suite sponsor, business owners, data engineers, operateurs |
| 2 | Static cuts de donnees | Livrees **1-2 semaines avant**, formats : CSV, Parquet, JSON, JDBC, API, S3 |
| 3 | Use cases cadrés | Discussion de cadrage en amont pour pre-builder |
| 4 | Call de 30 min avec data owners | Apres partage des donnees, pour comprendre la semantique |
| 5 | Signature Terms of Service | Pour provisionner un environnement Foundry prive |
| 6 | Readiness legale/securite | NDA, DPA pour industries reglementees |

### Composition equipe Palantir (par bootcamp)

| Role | Nombre | Fonction |
|------|--------|----------|
| Deployment Strategist (DS / Echo) | 1 | Lead narratif, facilitation, stakeholder management |
| FDE / FDSE (Delta) | 1-4 | Construction technique, prototypage, demos live |
| Account Executive (AE) | 1 | Present au kickoff et Day 5, conversations commerciales |
| Product Specialist | 0-1 | Expert AIP/Foundry avance |
| Solution Architect | 0-1 | Integration enterprise |
| FDIE (Infrastructure) | Optionnel | Deploiements on-prem complexes |

### Pre-bootcamp — 2 a 4 semaines de travail invisible

La "magie" du Jour 1 est le resultat de 2-4 semaines de travail FDE sans glamour. Quatre workstreams :

**Workstream 1 — Ingestion donnees**
- FDEs luttent avec les CSV, debuggent les connexions JDBC, ecrivent des transformes PySpark
- Objectif : donnees du client deja en live dans Foundry au Jour 1

**Workstream 2 — Ontologie squelette**
- 5-10 object types avec proprietes et liens de base deja en place au Jour 1
- Environnement sandbox provisionne, permissions configurees

**Workstream 3 — Selection use cases**
- DS passe de 5-10 candidats a 1-2 use cases primaires
- Framework de selection a 4 axes : Business impact / Data feasibility / Demonstrability / Executive resonance

**Workstream 4 — Legal, securite, logistique**
- NDA, DPA, Terms of Service
- Modele de securite 3 niveaux : Resource-Level, Ontology-Level ACL, Execution-Context AI

**Workstream 5 — Demo "Art of the Possible"**
- Demo live 60-90 min pour le leadership client avant la semaine
- FDE construit une version simplifiee avec les donnees pre-ingerees du client
- Objectif : declencheur emotionnel, securiser le buy-in executif

### Jour par Jour

---

#### JOUR 1 — Cadrage, validation donnees, accord sur le plan de construction

**Matin (9:00-12:30)**

- *Welcome & introductions* (9:00-9:30) : DS pose les attentes, presentation equipes
- *Problem Framing Workshop* (9:30-11:30) : Atelier whiteboard-heavy. Le DS fait parcourir les experts domaine a travers leurs workflows actuels bout en bout : trigger, decision points, data inputs, pain. Probing quantifie : *"How many work orders are misrouted per week? What's the cost of each misroute?"*
- *"Developing Your AI Intuition"* (11:30-12:30) : Session hands-on LLMs — ce qu'ils peuvent/ne peuvent pas faire, AIP Logic, prompt engineering, strong typing, tool chaining

**Apres-midi (13:30-17:30)**

- *Demo "Art of the Possible"* (13:30-14:30) : FDE lance l'instance Foundry live. Le client voit ses propres donnees deja ingerees. **Pivot emotionnel du bootcamp** — les spreadsheets desordonnees sont transformees en systeme structure navigable
- *Data reality check* (14:30-16:00) : FDEs + data engineers client examinent les donnees ensemble. Identification des gaps. "Minimum viable ontology" verrouille
- *Selection finale use cases* (16:00-17:00) : 1-2 use cases primaires confirmes, 1-3 explorés en surface
- *Discussion commerciale* (17:00-17:30) : AE confirme pathway procurement, executive sponsor confirme pour Jour 5

**Livrables Jour 1 :** Use-case slate signee, process flow diagrams, data inventory, design de l'ontologie MVO, buy-in emotionnel, AI intuition acquise

---

#### JOUR 2 — Premier "walking skeleton" fonctionnel

**Matin :** Construction fondation data (Pipeline Builder + Code Repositories). Ontologie dans Ontology Manager : tous les Object Types avec property mappings, primary keys, Link Types cables.

**Apres-midi :** Premiere application Workshop : modules, widgets (object tables, detail panels, charts, KPI tiles, filter panels), cables via variables, connecte a au moins une action operationnelle.

**Cadence iterative :** Cycles de 30-90 minutes. FDE construit → client revoit → feedback → ajustement.

John Kottlowski (Palantir) : *"sitting shoulder-to-shoulder with our data/tech counterparts, creating immediate, accretive value... within 2 days."*

**Livrable Jour 2 :** Pipeline branch fonctionnel, ontologie peuplee (5-15 object types, 5-20 link types), app Workshop "walking skeleton" — *"not polished, but it works"*

---

#### JOUR 3 — Extension use cases additionnels + introduction AIP Logic

**Matin :** Extension ontologie aux use cases 2 et 3. Ajout des **Ontology Actions** — operations write-back transformant le dashboard passif en outil operationnel ("Approve Work Order", "Assign Technician", "Escalate Case").

**Apres-midi :** **Integration AIP Logic** — fonctions LLM-powered operant sur l'ontologie. L'agent AI recoit acces a des object types specifiques, un system prompt, et un ensemble de fonctions disponibles (queries, lookups, action triggers). **AIP Assist** embarque dans Workshop : les utilisateurs peuvent requeter leurs donnees en langage naturel.

C'est le moment qui genere la reaction emotionnelle la plus forte : un VP Operations voit un agent AI repondre en langage naturel sur ses propres workflows, avec ses donnees reelles.

**Livrable Jour 3 :** 2-3 workflows end-to-end demoables, au moins une fonction LLM-backed, agents AIP Logic configures

---

#### JOUR 4 — Stress testing, evaluation, durcissement

**Ce que "stress testing" signifie vraiment :** Pas du load testing — une interrogation par les experts domaine les plus experimentes du client. Format war-gaming live : experts essaient de casser le systeme avec leurs scenarios reels les plus difficiles.

- *"What happens when a rush order comes in for a product we don't have in stock?"*
- *"What if the sensor data shows a false positive on a maintenance alert?"*

Chaque defaillance loguee : Critical (fix avant Jour 5) / Important / Noted. FDEs corrigent immediatement les Critical.

**Instrumentation :** AIP Evals pour test cases et evaluateurs. AIP Observability pour historique des runs, traces, logs.

**Apres-midi :** DS prepare le narratif executif avec le project lead client. Application Workshop "polie" — styling, navigation, KPI tiles pour executives.

**Livrable Jour 4 :** Suite d'evaluation, failure mode register, prototype bug-fixed, draft narratif executive, app polie

---

#### JOUR 5 — Readout executif, ROI, roadmap de deploiement

**Executive sponsor + 5-10 senior stakeholders. Presentation 45-60 min.**

Structure :
1. Problem statement (2-3 slides) — douleur quantifiee du workflow actuel
2. **Demo live** (15-20 min) — DS narre, FDE conduit le walkthrough
3. Business impact projection — ROI quantifie
4. Deployment roadmap — prototype vers production
5. Architecture technique optionnelle

**Framework ROI :** Economies de temps x cout main-d'oeuvre + Reduction erreurs x cout/erreur + Amelioration throughput x revenu/unite

Exemple concret : *"If current triage takes 45 min per work order and the prototype reduces it to 8 min, across 200 work orders/week — that's $540,000 annually from this single use case."*

**Dynamique cle :** Les participants qui ont co-construit deviennent les defenseurs les plus puissants dans la salle. L'executive sponsor voit ses propres employes defendre la solution.

---

## 4. LE FDE MODEL — ANATOMY COMPLETE

### Delta vs Echo : Les deux roles fondamentaux

**DELTA = Forward Deployed Software Engineer (FDSE)**
- "One customer, many capabilities" (vs. Dev : "one capability, many customers")
- Construit vite, ecrit du *"rough and ready code"*
- Profil : median ~25 ans [CONFIRMED], recrutes dans top CS programs (Stanford, MIT, CMU) mais aussi philosophie, maths, physique
- Citation : Mark Scianna (ex-FDE) : *"If I could sum FDE up in one sentence, it's that Palantir really believes you should put an engineer as close to the problem as possible"*
- Historiquement : Palantir a eu plus de Deltas que de Devs (pre-2016)

**ECHO = Deployment Strategist (DS)**
- Non-ingenieur, expert domaine, gestion des relations, management du changement
- Profil typique : ex-McKinsey, BCG, Bain [CONFIRMED LinkedIn analysis]
- "Rainbow role" — aucune definition fixe, autonomie maximale
- Mission : Trouver la *"Goldilocks zone: technically feasible within days, visibly impactful to executives, and extensible enough to seed the ontology for future use cases"*

Pascal Unger (LinkedIn) : *"FDEs handle technical building and implementation; Deployment Strategists manage commercial strategy and change management. Two different humans, two different skill sets, working as one team."*

### Philosophie fondamentale : Auftragstaktik

Barry McCardel (ex-Palantir, CEO de Hex) : La doctrine de mission-type tactics militaires. Les seniors fixent uniquement les objectifs de haut niveau, les equipes terrain ont toute latitude d'execution. Cree un "chaos" intentionnel ou des equipes paralleles s'attaquent aux memes problemes — les vainqueurs emergent par adoption naturelle (competition darwinienne entre solutions).

### Semaine typique d'un FDE

**Jours on-site (2-4 jours/semaine selon la phase) :**
- Matin : Reunions avec stakeholders techniques ou business chez le client
- Apres-midi : Monitoring, debugging, deploiement, configuration
- En continu : Observation des workflows reels (pas des SOPs documentees)
- Ad hoc : Demonstrations de prototypes, construction de relations avec les operateurs ET les executives

**Jours bureau/remote (1-3 jours/semaine) :**
- Code changes et configurations plateforme
- Code reviews
- "What I've Learned From Customers" — mises a jour hebdomadaires partagees company-wide
- Engineering reviews

**Heures reelles :** 7h00 - 19h00 typique, plus Slack depuis chez soi. Note Glassdoor work-life balance : 2.7/5.

**Voyage :** Nabeel Qureshi a vecu a Toulouse 1 an pour Airbus. Devise : *"Get on a plane first, ask questions later."*

### Onboarding d'un nouveau FDE

**Semaines 1-3 :** Bootcamp intensif interne — ontologie, engagement client, plateforme
**Semaines 3-6 :** Placement paire sur un compte client existant avec un senior lead
**Mois 2-4 :** Propriete croissante de workstreams techniques
**Mois 4-6 :** Autonomie quasi-complete sur des workstreams specifiques

**Les 5 livres remis au Jour 1 :**
1. *Impro* (Keith Johnstone) — Dynamiques de statut, lire la salle
2. *The Looming Tower* — Histoire du 11/9, silos d'information, mission morale de Palantir
3. *Interviewing Users* (Steve Portigal) — Techniques d'interview utilisateur
4. *Getting Things Done* (David Allen) — Productivite sous pression extreme
5. *Principles* (Ray Dalio) — Decision-making, transparence radicale

**Message implicite :** Les competences techniques sont acquises. Ce qui differencie, c'est le social, l'observation, l'organisationnel.

### Ce qui fait vraiment marcher le modele

**1. "Observation over documentation"**
FDEs shadowed les utilisateurs — ils reconstruisent les processus reels, pas les SOPs. Zoe Scaman : FDEs doivent devenir *"wallpaper — present enough to observe, invisible enough not to trigger the immune system."*

**2. Le probleme politique des donnees (8-12 semaines de guerre)**
Nabeel Qureshi : *"Data integration was the core bottleneck. Organizations controlled data sources and 'justify their existence by being the gatekeepers of that data source.'"* La solution : sponsoring executif au plus haut niveau (CEO d'Airbus a defini la priorite directement), demontrer la valeur avant de demander plus d'acces, rendre les gardiens partenaires plutot qu'obstacles.

**3. La continuite deliberee**
Le meme FDE team qui execute le bootcamp continue avec le compte s'il convertit — choix delibere qui cree un investissement personnel dans la conversion.

**4. Feedback R&D**
Le travail FDE est classe en R&D dans les financials, pas en services professionnels. Chaque solution client-specifique est potentiellement un futur primitif produit.

### Compensation FDE (2025-2026)

| Niveau | Compensation totale |
|--------|---------------------|
| New Grad FDSE | $185,000 - $230,000 |
| FDSE | $215,000 - $300,000 (median $215K) |
| Senior FDSE | $300,000 - $415,000 |
| Staff-Level FDSE | $415,000 - **$630,000+** |
| FDE embedding (G-Cloud UK) | 150K GBP/personne/trimestre (~$760K/an) |

### Attrition — La realite

| Metrique | Valeur |
|----------|--------|
| Tenure moyen company-wide | **3.2 ans** |
| Employes < 1 an | **35%** |
| Point d'inflexion burnout | **2-3 ans** |
| Work-life balance Glassdoor | **2.7 / 5** |

**Le modele comme "founder factory" :** Plus d'ex-Palantir que d'ex-Googlers dans chaque batch YC, malgre 50x plus d'employes chez Google. Anduril, Affirm, Hex, Scale AI — tous des ex-Palantir.

---

## 5. L'ONTOLOGIE — LE COEUR DU MOAT

### Definition

L'Ontologie Palantir n'est pas une base de donnees. C'est un **metadata overlay editable en temps reel** qui mappe des entites du monde reel sur des datasets tabulaires. Les objets sont des **materialized views sur des donnees tabulaires** — l'Ontologie ne stocke jamais de donnees elle-meme ; elle mappe vers des datasets existants.

Alex Karp : *"In the end you have products, your business, chips and ontology. This is how you get things to work."*

### Les 6 Primitives

| Primitive | Definition | Details techniques |
|-----------|------------|-------------------|
| **Object Types** | Schema d'une entite du monde reel | String PK obligatoire, backed par un ou plusieurs datasets, writeback dataset inclus. L'ID ne peut pas etre modifie apres premier deploy |
| **Properties** | Caracteristiques d'un object type | 17+ types de base : Boolean, Date, Decimal, GeoPoint, Vector, TimeSeries, Structs (1-10 champs, profondeur 1) |
| **Link Types** | Relations nommees entre object types | Cardinalities : 1-to-1, 1-to-many, many-to-many. Traversal sans SQL joins |
| **Action Types** | Mutations permises — les "verbes" de l'Ontologie | Parametres types, regles de validation, side effects (notifications, webhooks), permissions role-based, commit transactionnel |
| **Interfaces** | Types abstraits pour le polymorphisme | Non backes par des datasets. Permettent le code generique sur plusieurs object types |
| **Functions** | Logique code native a l'Ontologie | TypeScript v2 ou Python, execution sandboxee, registre de fonctions reutilisables, APIs auto-generees sur changement de schema |

### Les 3 Couches

**COUCHE SEMANTIQUE (WHAT) — Entites, proprietes, relations**
Object Types + Properties + Link Types + Interfaces → Definit CE QUI EXISTE

**COUCHE CINETIQUE (HOW) — Actions, Functions, regles de writeback**
Action Types + Functions → Definit COMMENT CES ENTITES PEUVENT ETRE MODIFIEES

**COUCHE DYNAMIQUE (GUARDRAILS) — Securite, gouvernance, indexation temps reel**
OMS (Ontology Management Service) + Object Storage V2 + Permissions + Schema Evolution → APPLIQUE LES REGLES

### Architecture backend (Brevet US20200293561A1)

5 moteurs :

| Moteur | Role |
|--------|------|
| Datastore | Stockage de donnees sources |
| Definition Engine (OMS) | Gestion des schemas, editable en temps reel |
| Association Engine | Mapping objet → lignes/colonnes exactes |
| Cache Engine | Materialized views pour operations OO |
| Interface Engine | APIs auto-regenerees sur changement de schema |

Resolution des conflits via **vector clocks**. Schema evolution : changements non-breaking (ajout de types/proprietes) sans migration. Changements breaking supportent jusqu'a **500 migrations par operation**.

### Pourquoi c'est le moat

**Morningstar :** *"Palantir's Ontology, Switching Costs Warrant Quadrupling of Our Fair Value Estimate"*

1. L'Ontologie encode des annees de connaissances institutionnelles — qui est qui, quoi est quoi, comment les entites sont liees
2. Elle devient le seul endroit ou tout le monde s'accorde sur la signification des donnees
3. AIP ne fonctionne PAS sans Ontologie : les LLMs n'ont jamais acces direct aux donnees. Ils interagissent via une architecture tool-use avec permissions explicitement scopees
4. Ryan Taylor : *"Our ontology is pure understanding, concretized in software. This is reality, not rhetoric."* + *"LLMs simply don't work in the real world without Palantir."*

### Temps de construction de l'Ontologie par client

| Phase | Object Types | Use Cases | Acteur |
|-------|-------------|-----------|--------|
| **Bootcamp** (5 jours) | 5-15 | 1-2 | FDE |
| **Pilot** (90 jours) | 20-50 | 3-5 | FDE + CoE client |
| **Expand** (mois 6-24) | 100-500 | 10-30 | CoE client |
| **Scale** (annee 3+) | 500-1,000+ | 50-200+ | CoE client autonome |

Nebraska Medicine : 1 use case en janvier 2024 → **20+ use cases en 6 mois** avec une ontologie unifiee couvrant patient flow, nurse allocation, clinical supplies, revenue cycle.

---

## 6. LE LOCK-IN — LES 7 COUCHES

Le lock-in de Palantir est reel, substantiel, et au moins partiellement intentionnel.

### Couche 1 — Lock-in technique (Ontologie)

Reconstruire une ontologie dans un autre systeme signifie :
- Re-mapper chaque type d'entite et ses relations
- Re-encoder les regles business et la logique de decision embarquees
- Reconstruire le "digital twin" operationnel de l'organisation
- Perdre les raffinements iteratifs accumules sur des annees

**Cout estime pour un client Enterprise :** 6-18 mois de travail data engineering, $2M-$10M [ESTIMATED]

### Couche 2 — Lock-in pipelines de donnees

Toutes les integrations depuis les systemes sources doivent etre reconstruites. Pour une entreprise avec des dizaines ou centaines de sources : **3-12 mois, $1M-$5M** [ESTIMATED]. Les 400+ connecteurs Palantir ne s'exportent pas dans un autre format exploitable.

### Couche 3 — Lock-in applicatif (Workshop)

Chaque dashboard operationnel, chaque application de workflow, chaque outil de decision construit avec Workshop est specifique a Palantir. Tout doit etre reconstruit from scratch sur une autre plateforme.

### Couche 4 — Lock-in securite et gouvernance

Structures de permissions, hierarchies de roles, regles de gouvernance des donnees — tout est specifique a la plateforme. Pour les industries reglementees (finance, sante, defense) : **3-6 mois de recertification securite, $500K-$2M** [ESTIMATED].

### Couche 5 — Lock-in connaissance institutionnelle

Les FDEs et "Palantir champions" internes accumulent une expertise profonde plateforme. Lors d'un changement, ce capital humain devient inutilisable. Nouvelles competences a acquerir dans toute l'organisation.

### Couche 6 — Lock-in analytique (la critique de Michael Burry)

Michael Burry : *"The friction exists in the area between raw data and the insights derived from that data."* Les donnees brutes peuvent etre exportees (CSV, JSON, Parquet). Mais le travail analytique — les tags, annotations, modeles, insights derives sur des annees — est piege dans la couche proprietaire de Palantir. *"If a customer cannot leave without losing years of analytical work, the moat is actually just obstruction."*

### Couche 7 — Lock-in contractuel et reglementaire

- Contrats multi-annees (1-5 ans commercial, **10 ans** gouvernement US)
- ATO (Authority to Operate) pour les environnements classifies : 3 mois - 3 ans, $90K-$700K rien que pour la certification
- Clearances de securite : 6-18 mois par personne pour un nouveau fournisseur
- Precedent sole-source : Maven initial = "le Pentagone a officiellement determine qu'aucune autre entreprise n'etait capable de repondre aux exigences"

### Cout total de migration estime

Pour un client Enterprise depensant $10M-$50M/an :

| Composant | Cout estime |
|-----------|------------|
| Recreation ontologie | $2M-$10M |
| Reconstruction pipelines | $1M-$5M |
| Reecriture applications | $2M-$8M |
| Recertification securite | $500K-$2M |
| Formation + perte productivite | $1M-$3M |
| Couts de double-run | $3M-$15M |
| **TOTAL** | **$10M-$43M** |

Soit **1-3x le spend annuel Palantir**. Pour les clients gouvernement : ajouter 12-36 mois de recertification ATO.

**Paradoxe de la clause de terminaison :** Palantir inclut des clauses "termination for convenience". En theorie, les clients peuvent partir. En pratique, ils ne peuvent pas partir sans perdre des annees d'intelligence organisationnelle encodee dans un format proprietaire.

---

## 7. LES ECHECS — CLIENTS QUI ONT QUITTE PALANTIR

La plupart de ces departs ont eu lieu entre 2015-2017, quand Palantir etait essentiellement une entreprise gouvernementale tentant de percer sur le marche commercial. Ces echecs ont enseigne a Palantir ses lecons les plus importantes.

### Coca-Cola (2016) — Le cas de tarification

**Ce qui s'est passe :** Coca-Cola a accepte un pilot en juillet 2014 mais a refuse de signer un contrat 5 ans en janvier 2016. L'accord aurait atteint $18M/an en annee 5.

**Raisons citees par Coca-Cola :**
1. Cout trop eleve
2. Ils voulaient une "expertise industrielle plus profonde" dans un partenaire
3. La "relation de travail" avec les jeunes ingenieurs de Palantir etait "difficile"

**Lecon :** La friction culturelle Silicon Valley vs. Fortune 500 est reelle. Les escalades de contrat doivent etre justifiees par de la valeur demontree avant d'etre signees.

### American Express (2016) — La faute attribuee

**Ce qui s'est passe :** AmEx a termine son engagement apres que Palantir n'ait pas delivre les resultats attendus.

**Pattern dangereux :** Palantir a blame les "limitations hardware" d'AmEx et le manque de support executif — refusant d'assumer la responsabilite. Ce pattern de blame du client est revenu dans plusieurs comptes.

**Lecon :** La responsabilisation est une condition de la confiance durable.

### Nasdaq (2015-2016) — La relation detruite en 8 mois

**Ce qui s'est passe :** Reunion CEO-Karp fin 2014 → pilot securite debut 2015 → relation "en lambeaux" en juillet. La relation s'est effondree apres un "brainstorm quelque peu farfelu" sur des projets potentiels hors du perimetre initial.

**Lecon :** Ne pas sur-promouvoir hors du cas d'usage initial. La confiance prend du temps a construire et se detruit instantanement.

### Home Depot (2017) — L'upsell non autorise

**Ce qui s'est passe :** Home Depot etait un client cybersecurite cle. Ils ont termine la relation pour deux raisons :
1. Home Depot a determine qu'il pouvait compter sur ses propres employes pour le travail que faisaient les ingenieurs Palantir
2. Home Depot etait "irrite" quand les employes Palantir ont tente de solliciter des affaires supplementaires dans d'autres departements — **en etant payes par l'equipe cybersecurite**

**Lecon Critique :** L'expansion doit etre autorisee et orchestree par le client, pas poussee unilateralement par le vendeur. Violer les frontieres detruit la confiance et la relation.

### NYPD (2017) — Le cas de portabilite des donnees

**Ce qui s'est passe :** Apres 5 ans d'utilisation de Palantir, le NYPD a commence silencieusement a construire un systeme de remplacement appele "Cobalt" en ete 2016. En fevrier 2017, annonce interne d'annulation du contrat Palantir.

**Allegation centrale :** Palantir a refuse de fournir les donnees dans des formats portables — specifiquement, les "analytical insights and tags" crees par les investigateurs NYPD dans le logiciel ne pouvaient pas etre exportes. Cobalt utilise des produits IBM assembles avec du code maison NYPD.

**Citation cle (Michael Burry) :** *"If the NYPD can do it on a government budget,"* impliquant que la technologie de Palantir n'est pas irreplacable.

**Lecon :** Le lock-in percu comme "obstruction" plutot que valeur reelle cree de la resentance et des alternatives internes. La meilleure defense est que les clients choisissent de rester, pas qu'ils soient forcement obliges.

### JPMorgan Chase (2017) — La violation de confiance

**Ce qui s'est passe :** JPMorgan etait le client corporate marquee de Palantir depuis 2009, avec jusqu'a **120 forward-deployed engineers** embarques. En 2013, des executives de JPMorgan ont decouvert qu'un executive securite utilisait le logiciel Palantir pour **les surveiller eux-memes** — lire leurs emails et tracker leurs appels telephoniques. La rupture de confiance a ete fatale.

**Lecon Absolue :** Les donnees du client ne doivent jamais etre utilisees contre les interet du client. L'acces extraordinaire confere par l'embedding FDE est une responsabilite, pas un avantage competitif.

### Patterns communs a tous les echecs

1. **Cout percu comme excessif** par rapport a la valeur demontree
2. **Friction culturelle** entre le style Silicon Valley de Palantir et les cultures d'entreprise plus traditionelles
3. **Violations de frontieres** — surveillance, upsell non autorise, "blaming" du client
4. **Incapacite a delivrer** des resultats justifiant le prix
5. **Arrogance** — les "jeunes ingenieurs de Palantir" percus comme difficiles

### Pourquoi ces echecs ne se repetent (theoriquement) plus

Depuis 2023, AIP donne aux clients une raison convaincante d'etendre leur spend sans nouvelle integration. Le modele bootcamp ameliore la delivraison de valeur initiale. Le NDR est passe de 107% (Q3 2023) a 139% (Q4 2025). Mais les lecons structurelles restent valables pour tout concurrent.

---

## 8. APOLLO — LA PLATEFORME DE DEPLOIEMENT INVISIBLE

### Qu'est-ce qu'Apollo ?

Apollo est la plateforme de Continuous Delivery de Palantir — elle deploie **tout** le logiciel Palantir, y compris elle-meme, dans tous les environnements : du cloud public aux environnements air-gapped militaires de niveau IL6.

Apollo est la raison pour laquelle Palantir peut etre partout en meme temps, avec des garanties de securite uniformes.

### Architecture Hub-and-Spoke

**Apollo Hub :** Plan de gestion centralise. Contient l'Orchestration Engine. Recoit la telemetrie de chaque environnement, evalue les contraintes, emet des Plans.

**Apollo Spoke :** Deploye par environnement gere (typiquement un cluster Kubernetes). Les agents **pull** (pas push) les instructions depuis le Hub. Rapportent l'etat observe en continu.

**Architecture pull-based critique :** Les agents interrogent le Hub — ils ne recoivent pas de mises a jour poussees. Permet l'operation dans les reseaux peu fiables ou restreints, y compris les environnements air-gapped.

### Metriques de performance

| Metrique | Valeur |
|----------|--------|
| Deployments/mois | **360,000+** |
| Temps moyen de deploiement | **3.5 minutes** |
| Temps moyen de rollback | **4.9 minutes** |
| Taux de succes des changements | **95.5%** |
| Environnements manages | ~1,000 (dont ~100 air-gapped) |
| Upgrades/semaine | ~**90,000** automatiques |
| Produits geres | 2,500 services independants |
| Amelioration frequence deploiement | **45x** (8,000 → 360,000/mois) |
| Acceleration lead time | **12,500x** (1 mois → 3.5 min) |

### Mecanismes de securite Apollo

**Blue-Green Upgrades :** Nouvelle version deployee aux cotes de l'ancienne, trafic transfere, observation. Rollback automatique si probleme detecte.

**Suppression Windows :** Apres echec de Plan, fenetres de suppression entity-level puis environment-level evitent les pannes en cascade. Les Plans de rollback restent autorises meme pendant les suppressions.

**Recall Global :** Rappel d'une release mauvaise dans tous les environnements simultanément. Plans de recall prioritaires sur toutes les autres operations.

**Canary Promotion :** Promotion basee sur des SLOs. Seuil sain par defaut : 95% du temps. Rollback automatique si non atteint.

### Apollo pour les environnements classifies

Apollo est l'unique raison pour laquelle Palantir peut operer dans des reseaux air-gapped (IL5, IL6) sans compromettre les capacites SaaS :

**Mode Disconnected :** Les services Hub Apollo sont installes DANS le reseau gouvernemental. Fonctionnement identique au centralise. Les packages sont transferes via un NOC (Network Operations Center), cryptographiquement signes, valides en integrite.

**PFCS Forward (annonce 12 fevrier 2026 — DISA) :** Authorise l'extension des certifications IL5 et IL6 aux deploiements on-premises et edge tactiques. "Authorize once, deploy everywhere" — de la data center enterprise aux vehicules tactiques mobiles.

**Certifications :** FedRAMP High, DoD IL5/IL6, CMMC, 6 familles de controles NIST

### Apollo comme produit standalone

| Tier | Prix |
|------|------|
| Apollo SDK | Gratuit |
| Apollo Core | **$100 / installation / mois** |

Un service deploye sur 3 environnements (AWS, Azure, on-prem) = $300/mois. Le modele beneficie directement de l'adoption multi-cloud.

**Clients Apollo (non-Palantir) :** Airbus, BP (economie reportee : $1B sur les plateformes Palantir), US Army ($876M contrat battlefield data management), Rio Tinto, Credit Suisse, Fujitsu, Hyundai Heavy Industries.

### Pourquoi Apollo est strategiquement crucial

1. **Il elimine les concurrents** de facto dans les environnements classifies (aucun alternatif commercial ne supporte IL6 nativement)
2. **Il est le Trojan Horse** : un client qui adopte Apollo pour son deploiement devient dependant de l'infrastructure Palantir avant meme d'utiliser Foundry ou AIP
3. **Il finance une capacite de deploiement** que personne d'autre n'a
4. **Il cree une moat infrastructurelle** separee de la moat produit

---

## 9. CE QUE SPIDER DOIT COPIER

### Mapping direct : concept Palantir → equivalent Spider

---

#### 9.1 Le Bootcamp comme seul vrai go-to-market

**Palantir :** 5 jours gratuits, construction sur donnees reelles du client, equipe d'ingenieurs embarques, pas une demo mais une co-construction.

**Spider doit faire :** Creer un "Spider Sprint" de 3-5 jours. Pas un POC vendu $50K. Un investissement gratuit (ou pres de gratuit) qui construit quelque chose de fonctionnel sur les vraies donnees du client.

**Pourquoi :** Le bootcamp cree 3 choses que rien d'autre ne peut creer aussi vite :
1. Propriete psychologique (le client a co-construit)
2. Preuves de valeur tangibles (pas des slides)
3. Des champions internes (les co-builders deviennent les defenseurs)

**Adaptation necessaire :** Spider n'a pas les ressources pour 5 FDEs par bootcamp. La version Spider = 1-2 personnes, 3 jours, cas d'usage pre-selectionne sur donnees clients reelles. L'objectif est identique : le client voit sa propre realite dans le systeme.

---

#### 9.2 Le modele Delta/Echo comme unite minimale de deploiement

**Palantir :** Chaque deploiement = 1 DS (narratif, relations, business) + N FDEs (technique). Les deux roles sont distincts et complementaires.

**Spider doit faire :** Toujours envoyer au moins 2 personnes en engagement client. Une personne technique (capable de construire), une personne business (capable de traduire). Ne jamais envoyer uniquement un "commercial" ou uniquement un "technique".

**Pourquoi :** Le DS seul ne peut pas montrer. Le FDE seul ne peut pas convaincre. La paire est la moindre unite viable.

---

#### 9.3 Le pre-travail invisible comme differenciateur

**Palantir :** 2-4 semaines de travail FDE avant le bootcamp. Les donnees sont deja dans le systeme au Jour 1. La "magie" n'est pas de la magie — c'est de la preparation.

**Spider doit faire :** Investir significativement avant chaque engagement client visible. Obtenir des donnees echantillons 2 semaines avant. Pre-construire le schema de base. Pre-connecter les sources. Quand le client arrive, son monde est deja dans le systeme.

**Impact :** Le moment ou le client voit ses propres donnees dans le systeme (le "pivot emotionnel") ne peut pas etre simule. Il doit etre reel pour produire l'effet.

---

#### 9.4 L'ontologie comme foundation architecturale

**Palantir :** Tout repose sur l'ontologie. Les applications, les agents AI, les actions — tous sont des vues sur l'ontologie. L'ontologie est ce qui accumule la valeur au fil du temps.

**Spider doit faire :** Definir un equivalent ontologique. Ce n'est pas necessairement une replique technique exacte, mais le principe est identique : construire une couche semantique qui mappe les entites metier du client (commandes, clients, produits, employes, assets) et leurs relations, sur laquelle tout le reste est construit.

**Differenciateur key :** Cette couche doit etre **extensible** (chaque nouveau use case augmente sa valeur), **propriete du client** (ils l'ont co-construite), et **difficile a migrer** (encoding de la connaissance institutionnelle).

---

#### 9.5 La progression Acquire → Expand → Scale avec des economics conscientes

**Palantir :** Les pilots sont deliberement non-rentables (-43%). L'investissement est justifie par l'expansion future.

**Spider doit faire :** Ne pas chercher a etre profitable des le premier engagement. Definir explicitement des budgets "investissement" pour les bootcamps et pilots. Tracker les economics par phase, pas par engagement.

**Mais attention :** Palantir peut absorber -43% pendant des mois parce que le capital et les revenus gouvernementaux existants financent ces investissements. Spider doit dimensionner ses investissements a ce qu'il peut reellement absorber.

---

#### 9.6 La quantification ROI comme langage commun

**Palantir :** A chaque etape, le DS sonde les metriques quantifiables. *"How many work orders are misrouted per week? What's the cost of each misroute?"* Le Jour 5 presente un ROI calcule depuis les chiffres du Jour 1.

**Spider doit faire :** Integrer la quantification dans chaque phase de la methodologie. Ne jamais presenter un use case sans son ROI calcule en chiffres concrets — pas en pourcentages vagues.

**Template ROI Spider :** Economies de temps x cout/heure + Reduction d'erreurs x cout/erreur + Gain de throughput x valeur/unite = impact annuel.

---

#### 9.7 La creation de champions internes

**Palantir :** Les participants au co-building deviennent les defenseurs les plus puissants dans la salle executive. Palantir n'essaie pas de convaincre le C-suite — Palantir convainc les managers operationnels qui convainquent le C-suite.

**Spider doit faire :** Identifier les "champions potentiels" des le scoping. Ce sont les personnes qui : (1) souffrent le plus du probleme, (2) ont l'autorite de le resoudre, (3) seront reconnues si la solution reussit. Les impliquer profondement dans le co-building.

---

#### 9.8 La transparence radicale sur les limitations

**Palantir :** Le Jour 4 est explicitement dedie au stress testing — trouver et documenter les cas ou le systeme echoue. Le "failure mode register" est un livrable.

**Spider doit faire :** Ne jamais livrer un prototype sans sa documentation des limitations. Un client qui decouvre les limitations en production perd confiance. Un client qui les connait a l'avance les gere.

---

#### 9.9 La formation du Centre of Excellence client

**Palantir :** L'objectif a long terme est que le client soit autonome. Roles definis : Platform Owner, Permissions Manager, Data Engineers, Application Builders, Analystes. Palantir Learn pour la certification.

**Spider doit faire :** Definir les roles equivalent Spider-enabled au niveau client. Creer du materiel de formation. Mesurer le succes non par le nombre de FDEs embarques mais par l'autonomie progressive du client.

**Paradoxe productif :** Plus le client est autonome, plus il etend l'usage (car il peut experimenter sans demander l'aide de Spider), et plus le spend croit.

---

## 10. CE QUE SPIDER NE DOIT PAS COPIER

### 10.1 Le modele de pricing de Palantir

**Palantir :** Opacite de prix totale ("no pricing strategy for AIP"). Negociation cas par cas. Minimum viable $250K+ ACV. G-Cloud UK expose des contrats a partir de £250K/an.

**Pourquoi Spider ne peut pas copier :** Spider n'a pas la credibilite de marque, la profondeur de produit, ni les references qui justifient cette opacite. L'opacite de prix est une strategie des entreprises qui ont le leverage. Spider, en phase de lancement, a besoin de prix lisibles et previsibles pour reduire la friction d'entree.

**Ce que Spider devrait faire a la place :** Packaging transparent avec une logique de valeur claire. Le pricing augmente avec l'usage, pas avec l'arcanisme.

---

### 10.2 Les timelines de deploiement

**Palantir :** Les pilots durent 3-6 mois. Les phases Expand 6-24 mois. Les phases Scale 24+ mois. Graduation des FDEs en 36 mois (commercial) ou 48 mois (gouvernement).

**Pourquoi Spider ne peut pas copier :** Ces timelines sont adaptees a des organisations qui ont le budget et la patience pour des investissements de cette longueur. Pour les PME françaises (cible initiale de Spider), les cycles de decision sont plus courts, les budgets plus limites, et la patience executive mesurement differente.

**Ce que Spider devrait faire a la place :** Viser des cycles pilote de 30-60 jours maximum. La valeur doit etre demontrable en semaines, pas en mois. Les timelines longues de Palantir sont une consequence de la complexite de ses clients, pas un objectif en soi.

---

### 10.3 Le talent pool FDE

**Palantir :** Les FDEs sont recrutés a 1-2% de taux d'acceptation parmi les top CS programs mondiaux. Chaque candidat doit etre approuve par les fondateurs. L'interview inclut un "Decomposition Interview" specifique. Compensation moyenne $215K.

**Pourquoi Spider ne peut pas copier a l'identique :** Ce type de talent est rare, couteux, et ne correspond pas au marche francais au stade early-stage. Palantir a pris plus de 10 ans pour developper ce playbook de recrutement.

**Ce que Spider devrait faire a la place :** Privilegier des profiles hybrides (technique + sens business) avec une expertise domaine forte dans 1-2 verticaux cibles. La depth dans un secteur (ex : manufacturing français) peut compenser la breadth du profil Palantir generique. Commencer avec 3-4 personnes exceptionelles plutot qu'une equipe de 20 personnes mediocres.

---

### 10.4 La strategie gouvernement US

**Palantir :** 35% du chiffre d'affaires est gouvernemental. Contrats sole-source. IL6, FedRAMP High. Maven, TITAN, Army ESA. Ce segment a ete crucial pour financer les pertes du segment commercial pendant des annees.

**Pourquoi Spider ne peut pas copier :** L'acces aux mega-contrats gouvernementaux US est le resultat de 15 ans de relations, de certifications ATO couteuses, et d'une culture specifique (Palantir est fondamentalement une entreprise de defense qui s'est ensuite attaquee au commercial). Spider operer sur le marche français/europeen avec des dynamiques de procurement radicalement differentes.

**Ce que Spider devrait faire a la place :** Si la voie publique est envisagee, cibler des appels d'offres européens plus accessibles. La souverainete numerique européenne est un avantage competitif potentiel (Palantir = americain), pas un desavantage.

---

### 10.5 Le modele de "loss-leader" en Acquire a grande echelle

**Palantir :** A investi des centaines de millions en pertes Acquire pour construire son portefeuille commercial. S-1 confirme -$65.4M de perte sur la cohorte Acquire totale. Ce n'est viable que parce que le segment gouvernement financait la machine.

**Pourquoi Spider ne peut pas copier :** Spider n'a pas de segment gouvernemental generant $1.5B/an pour financer des pertes sur le segment commercial. Chaque engagement doit contribuer a la sustainability financiere, meme si la contribution est differee.

**Ce que Spider devrait faire a la place :** Budgeter precisement les "investissements" bootcamp et pilot. Definir un seuil de conversion minimum en dessous duquel un compte n'est pas poursuivi. Le loss-leader delibere est une strategie — le loss-leader accidentel est un chemin vers la faillite.

---

### 10.6 L'echelle des AIPCons

**Palantir :** AIPCon 8 = 70+ speakers, des centaines de participants, national spotlight. Ces evenements coutent des millions a organiser et ne sont possibles que parce que Palantir a 954 clients dont beaucoup sont prets a temoigner publiquement.

**Pourquoi Spider ne peut pas copier maintenant :** Spider n'a pas encore le portefeuille de clients qui justifie cet investissement. AIPCon a commence modestement (AIPCon 1 en juin 2023) et a grandi avec le portefeuille.

**Ce que Spider devrait faire a la place :** Investir tres tot dans la documentation de cas d'usage. Chaque client satisfait = un temoignage videographe, un case study ecrit, une reference disponible. L'equivalence de l'AIPCon pour Spider Year 1 est peut-etre une table ronde de 5-10 clients.

---

### 10.7 La taille des equipes FDE par compte

**Palantir :** 4-5 FDEs en phase Acquire. Jusqu'a 120 FDEs embarques chez JPMorgan (extreme). Pour un compte strategique, 10-20 FDEs deployes sur plusieurs mois.

**Pourquoi Spider ne peut pas copier :** Ces tailles d'equipes ne sont viables qu'avec des ACV correspondants ($5M+ pour justifier 5 FDEs pendant 6 mois). Spider commence avec des ACV beaucoup plus petits.

**Ce que Spider devrait faire a la place :** Optimiser le ratio valeur-delivree / personnel-deploye. L'AIFDE (AI Forward Deployed Engineer) de Palantir est la reponse a ce probleme meme chez Palantir — 2 FDEs humains + AI agents pour migrer un data warehouse en 5 jours (ce qui aurait pris 2 ans a une armee de SIs). Spider doit integrer cet effet de levier AI des le debut, pas comme evolution future.

---

## REFERENCE RAPIDE — CITATIONS ET CHIFFRES CLES

**Sur le bootcamp :**
- Alex Karp : *"We're already overfilled for our AIP bootcamp... It's like a rock concert"*
- Shyam Sankar : *"The boot camp is not a demo. It's not a presentation. We show up with engineers, and we build."*
- Ryan Taylor : *"We reoriented our go-to-market approach around AIP boot camps, which has allowed us to deliver real workflows on actual customer data in five days or less"*

**Sur l'ontologie :**
- Alex Karp : *"In the end you have products, your business, chips and ontology. This is how you get things to work."*
- Karp : *"LLMs are like genies of the lamp. AIP is the lamp that controls them."*
- Ryan Taylor : *"Our ontology is pure understanding, concretized in software. This is reality, not rhetoric."*
- Ryan Taylor : *"LLMs simply don't work in the real world without Palantir."*

**Sur les FDEs :**
- Mark Scianna (ex-FDE) : *"If I could sum FDE up in one sentence, it's that Palantir really believes you should put an engineer as close to the problem as possible"*
- Shyam Sankar : *"We build software that works, not software that ought to. We build software for the world as it exists, not a world that never was."*

**Sur AIFDE :**
- Sankar Q3 2025 : *"At one customer, two human FTEs spawned an army of AI FTEs to migrate a customer off their legacy data warehouse in five days, something that would have taken an army of SIs up to two years. This is not a prototype. This is production."*
- Sankar Q4 2025 : *"AIFDE is now capable of powering complex SAP ERP migrations from ECC to S/4. Years of work now done in as little as two weeks."*

**Sur les impacts business :**
- Trinity Rail : *"It took just three months to get to a functional workflow with a $30 million impact to its bottom line."*
- Insurance underwriting : *"78 AI agents, taking a process that took two weeks to 3 hours."*
- Maven targeting : *"The entire targeting and fires process can be done in Maven with 20 people. It used to take 2,000."*
- Nebraska Medicine : *"2,100% increase in discharge lounge utilization"*
- Fannie Mae : *"Mortgage fraud detection time from 2 months down to seconds"*
- Healthcare company Q2 2025 : *"Completed a bootcamp in April, then signed an $88 million TCV deal a month later"*

**Sur le modele economics :**
- Colin Anderson (ex-CFO) : *"The model is only financially sustainable for seven-figure contracts and above, with eight or nine figures being the sweet spot."*
- Alex Karp : *"Unlike seemingly in the most obvious way, we are downstream from the value creation. The reason why that's working is because we are making our clients more money or we're making them more dominant on the battlefield, and they're paying us a subset of that."*

---

*Document compile par Spider Strategy Research — Version 1.0 — 21 fevrier 2026*
*Sources primaires : PLAYBOOK-DEFINITIF-PALANTIR.md, PALANTIR-FULL-RECAP.md, 01-palantir-fde-methodology-deep-dive.md, palantir-demos-transcripts-concrete-evidence.md, palantir-apollo-research.md, 13-research-palantir-fde-training-onboarding.md, 12-research-palantir-churn-switching-lockin.md*
