> **Document :** PARTIE 4 — PALANTIR
> **Date :** 21 fevrier 2026
> **Contexte :** Section 4 du document strategique Spider. Ce que Palantir fait, comment, et ce que Spider en tire.
> **Sources :** A2-REFERENCE-PALANTIR.md (SEC filings, earnings calls Q1 2023 - Q4 2025, AIPCon 1-8, DevCon 1-4, Glassdoor 156 reviews FDSE, Gartner Peer Insights, investigations journalistiques, brevets USPTO)

---

**PARTIE 4 — PALANTIR : LE MANUEL**

---

**4.1 Palantir en 60 secondes**

---

Palantir Technologies n'est pas une entreprise de logiciel comme les autres. C'est une entreprise qui a passe 20 ans a construire des outils de guerre de l'information pour la CIA, la NSA et l'armee americaine, puis a applique ces memes architectures au monde commercial. En 2026, cette traduction est complete. Les chiffres sont incontestables.

**Metriques cles FY2025 (annee fiscale close decembre 2025)**

| Metrique | Valeur | Variation YoY |
|----------|--------|---------------|
| Chiffre d'affaires total | $4.475B | +56% |
| Revenue Q4 2025 seul | $1.407B | +70% |
| US Commercial Revenue | $1.465B | +109% |
| Net Dollar Retention (NDR) | 139% | Record absolu |
| Clients totaux | 954 | +34% |
| GAAP Gross Margin | 84% | En expansion |
| Free Cash Flow (ajuste) | $2.27B | +82% |
| Net Income GAAP | $1.625B | +250% |
| Revenue per Employee | $1.01M | ServiceNow : $550K |
| Market Cap (fevrier 2026) | ~$313B | |
| Revenue guidance FY2026 | $7.19B | +61% |
| TCV Q4 2025 | $4.3B | +138% YoY |
| Expansion multiple moyen | 56x ($100K → $5.6M ACV) | |
| Revenue top 20 clients | $94M+ par client en moyenne | |
| Bootcamps conduits | 1,300+ | ~5 par jour en 2024 |
| FDEs estimes | 2,000 - 3,000 | |

**Trajectoire revenus FY2020 - FY2026E**

| Annee | Revenue | Croissance |
|-------|---------|------------|
| FY2020 | $1.09B | — |
| FY2021 | $1.54B | +41% |
| FY2022 | $1.91B | +24% |
| FY2023 | $2.23B | +17% |
| FY2024 | $2.87B | +29% |
| FY2025 | $4.475B | +56% |
| FY2026E | $7.19B | +61% guide |

Le point d'inflexion est identifiable au mois pres : le lancement d'AIP en avril 2023. La croissance est passee de +17% a +56% en deux ans. Ce n'est pas une acceleration lineaire — c'est un changement de regime.

**Trajectoire NDR**

| Periode | NDR | Note |
|---------|-----|------|
| Q3 2023 | 107% | Creux pre-AIP |
| Q4 2024 | 120% | |
| Q3 2025 | 134% | +600 bps QoQ |
| Q4 2025 | 139% | Record historique |

Un NDR de 139% signifie que les clients existants depensent en moyenne 39% de plus chaque annee — sans qu'un seul nouveau client soit acquis. C'est ce que Palantir appelle le flywheel : la plateforme devient plus utile a mesure que l'ontologie client grossit, ce qui justifie des budgets croissants, ce qui finance plus de FDEs, ce qui etend l'ontologie davantage.

---

**4.2 Le modele commercial — les 4 phases**

---

Palantir ne "vend" pas un logiciel. Palantir investit dans des clients qui deviennent des machines a expansion. La progression suit 4 phases avec des economics radicalement differents a chaque etape.

**Vue d'ensemble du flywheel**

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

L'expansion multiple documente est de 56x : de $100K initial a $5.6M d'ACV mature.

**Phase 1 — BOOTCAMP (Acquisition, Semaine 0)**

Cout pour le client : gratuit. Cout pour Palantir : $12,000 a $36,000 par bootcamp (estimation : 1-5 jours, 5-8 personnes). Taux de conversion vers un pilot paye : ~22%.

Palantir organise environ 5 bootcamps par jour au niveau global. Ce n'est pas un canal parmi d'autres — c'est LE canal principal. Ted Mabrey, Head of Global Commercial : *"Our primary means of going to market with AIP will be through these bootcamps."*

**Phase 2 — PILOT / ACQUIRE (Mois 0-6)**

| Parametre | Valeur |
|-----------|--------|
| ACV | $100K - $500K |
| Marge contribution | -43% |
| FDEs embarques | 4-5 par client |
| Duree | 3-6 mois |
| Objectif | Prouver la valeur sur un cas d'usage reel |
| Use cases construits | 1-3 |
| Sources de donnees connectees | 3-10 |

Colin Anderson (ex-CFO, Palantir) : *"The model is only financially sustainable for seven-figure contracts and above, with eight or nine figures being the sweet spot."* Le pilot est un investissement en R&D, pas une source de revenus.

Exemples de conversions rapides cites en earnings calls :
- Utility company : deal 7 chiffres signe 5 jours apres le bootcamp
- Wholesale insurance : $1M+ ACV ferme 16 jours apres le bootcamp
- Convenience store chain : prototype → pilot paye → production en 25 jours

**Phase 3 — EXPAND (Mois 6-24, $500K → $5M ACV)**

| Parametre | Valeur |
|-----------|--------|
| ACV | $500K - $5M |
| Marge | -43% → +35% (breakeven vers mois 9) |
| FDEs | Decroissant, Centre of Excellence en construction |
| Objectif | Multi-departements, 10-30 use cases, adoption virale interne |
| Champions internes | Formes comme builders certifies |
| Ontologie | Passage de 5-15 a 100-500 object types |

Les mecanismes d'expansion sont au nombre de quatre : nouveau use case capte par un champion interne qui l'etend a un autre departement ; "Build with AIP" bootcamps internes ou les employes du client deviennent participants ; ROI demontre en Phase 1 qui debloque le budget Phase 2 ; ontologie etendue qui fait tendre le cout marginal de chaque nouveau use case vers zero.

**Phase 4 — SCALE (Annee 3+, $5M-$20M+ ACV)**

| Parametre | Valeur |
|-----------|--------|
| ACV | $5M - $20M+ (top 20 : $94M+ en moyenne) |
| Marge | +55%+ |
| FDEs | 0-1 (graduation deliberee) |
| Ontologie | 500-1,000+ object types, digital twin de l'organisation |
| Contrats | Multi-annees (5-10 ans pour le gouvernement) |

Le cas Lear Corporation est le plus demonstratif : au stade Pilot, 100 utilisateurs, 4 use cases. Au stade Scale, 16,000 utilisateurs (+160x), 280 use cases (+70x). L'organisation est devenue dependante de la plateforme non pas par contrat mais par utilisation.

Prix par phase, reference publique G-Cloud UK :

| Niveau | Licence annuelle | Profil client |
|--------|-----------------|---------------|
| Level 0 | £250,000 | Pilot / POC |
| Level 1-3 | £500K - £2M | Multi-equipes |
| Level 4-7 | £2M - £25M | Enterprise-wide |
| Level 8-11 | £25M - £200M | Ministere / grand compte |
| Level 12-15 | £200M - £1B | Programmes nationaux (NHS) |

---

**4.3 Le Bootcamp AIP — detail operationnel**

---

Le Bootcamp AIP est une semaine d'immersion intensive, typiquement 5 jours, ou Palantir envoie une equipe d'ingenieurs chez le client pour construire un prototype fonctionnel sur les donnees reelles du client, gratuitement. Ce n'est pas une demonstration. Ce n'est pas une presentation.

Shyam Sankar (CTO) : *"The boot camp is not a demo. It's not a presentation. We show up with engineers, and we build."*

Ryan Taylor (CRO, Q3 2023) : *"We reoriented our go-to-market approach around AIP boot camps, which has allowed us to deliver real workflows on actual customer data in five days or less versus our traditional pilots, which generally take one to three months."*

**Volume de bootcamps**

| Periode | Cumule |
|---------|--------|
| Mi-2023 | ~50 |
| Fin Q3 2023 | ~100 |
| Fin Q4 2023 | 560+, 465+ organisations |
| Fin Q1 2024 | 915+ |
| Juin 2024 | 1,300+ |
| Cadence 2024 | ~5 bootcamps par jour (Bloomberg) |

Alex Karp : *"We're already overfilled for our AIP bootcamp... It's like a rock concert."*

**Prerequis client pour etre "Bootcamp-Ready"**

| # | Critere | Detail |
|---|---------|--------|
| 1 | Participants confirmes | 5-20 stakeholders : C-suite sponsor, business owners, data engineers, operateurs |
| 2 | Static cuts de donnees | Livrees 1-2 semaines avant, formats : CSV, Parquet, JSON, JDBC, API, S3 |
| 3 | Use cases cadres | Discussion de cadrage en amont pour pre-builder |
| 4 | Call de 30 min avec data owners | Apres partage des donnees, pour comprendre la semantique |
| 5 | Signature Terms of Service | Pour provisionner un environnement Foundry prive |
| 6 | Readiness legale et securite | NDA, DPA pour industries reglementees |

**Composition equipe Palantir par bootcamp**

| Role | Nombre | Fonction |
|------|--------|----------|
| Deployment Strategist (DS / Echo) | 1 | Lead narratif, facilitation, stakeholder management |
| FDE / FDSE (Delta) | 1-4 | Construction technique, prototypage, demos live |
| Account Executive (AE) | 1 | Present au kickoff et Jour 5, conversations commerciales |
| Product Specialist | 0-1 | Expert AIP / Foundry avance |
| Solution Architect | 0-1 | Integration enterprise |
| FDIE (Infrastructure) | Optionnel | Deploiements on-prem complexes |

**Le pre-travail invisible — 2 a 4 semaines avant le Jour 1**

La "magie" du Jour 1 est le resultat de 2-4 semaines de travail FDE sans glamour. Cinq workstreams paralleles :

**Workstream 1 — Ingestion donnees.** FDEs luttent avec les CSV, debuggent les connexions JDBC, ecrivent des transformes PySpark. Objectif : les donnees du client sont deja en live dans Foundry au Jour 1. Le client n'arrive pas a un systeme vide.

**Workstream 2 — Ontologie squelette.** 5-10 object types avec proprietes et liens de base deja en place au Jour 1. Environnement sandbox provisionne, permissions configurees.

**Workstream 3 — Selection use cases.** Le DS passe de 5-10 candidats a 1-2 use cases primaires. Framework de selection a 4 axes : Business impact / Data feasibility / Demonstrability / Executive resonance.

**Workstream 4 — Legal, securite, logistique.** NDA, DPA, Terms of Service. Modele de securite a 3 niveaux : Resource-Level, Ontology-Level ACL, Execution-Context AI.

**Workstream 5 — Demo "Art of the Possible".** Demo live de 60-90 minutes pour le leadership client avant la semaine. Un FDE construit une version simplifiee avec les donnees pre-ingerees du client. Objectif : declencheur emotionnel, securiser le buy-in executif avant que le bootcamp commence.

**Jour par jour**

**JOUR 1 — Cadrage, validation donnees, accord sur le plan de construction**

Matin (9:00-12:30) : Welcome et introductions, le DS pose les attentes, presentation des equipes. Problem Framing Workshop — atelier whiteboard-heavy. Le DS fait parcourir les experts domaine a travers leurs workflows actuels bout en bout : trigger, decision points, data inputs, pain. Le questionnement est quantifie : "How many work orders are misrouted per week? What's the cost of each misroute?" Suivi d'une session hands-on "Developing Your AI Intuition" — ce que les LLMs peuvent et ne peuvent pas faire, AIP Logic, prompt engineering, strong typing, tool chaining.

Apres-midi (13:30-17:30) : Demo "Art of the Possible" — le FDE lance l'instance Foundry live. Le client voit ses propres donnees deja ingerees. C'est le pivot emotionnel du bootcamp : les spreadsheets desordonnees transformees en systeme structure navigable. Suivi d'un "data reality check" ou FDEs et data engineers client examinent les donnees ensemble, identifient les gaps, verrouillent la "minimum viable ontology". Selection finale des use cases, puis conversation commerciale ou l'AE confirme le pathway procurement.

Livrables Jour 1 : use-case slate signee, process flow diagrams, data inventory, design de l'ontologie MVO, buy-in emotionnel, AI intuition acquise.

**JOUR 2 — Premier "walking skeleton" fonctionnel**

Matin : Construction de la fondation data avec Pipeline Builder et Code Repositories. Ontologie dans Ontology Manager : tous les Object Types avec property mappings, primary keys, Link Types cables.

Apres-midi : Premiere application Workshop. Modules, widgets (object tables, detail panels, charts, KPI tiles, filter panels), cables via variables, connecte a au moins une action operationnelle.

La cadence iterative est de cycles de 30-90 minutes : FDE construit → client revoit → feedback → ajustement. Pas de "sprints de 2 semaines". Le feedback est immediat.

John Kottlowski (Palantir) : *"sitting shoulder-to-shoulder with our data/tech counterparts, creating immediate, accretive value... within 2 days."*

Livrable Jour 2 : pipeline fonctionnel, ontologie peuplee (5-15 object types, 5-20 link types), app Workshop "walking skeleton" — pas polie, mais fonctionnelle.

**JOUR 3 — Extension use cases + introduction AIP Logic**

Matin : Extension de l'ontologie aux use cases 2 et 3. Ajout des Ontology Actions — operations write-back qui transforment le dashboard passif en outil operationnel : "Approve Work Order", "Assign Technician", "Escalate Case".

Apres-midi : Integration AIP Logic. Fonctions LLM-powered operant sur l'ontologie. L'agent AI recoit acces a des object types specifiques, un system prompt, et un ensemble de fonctions disponibles (queries, lookups, action triggers). AIP Assist est embarque dans Workshop : les utilisateurs peuvent requeter leurs donnees en langage naturel.

C'est typiquement le moment qui genere la reaction emotionnelle la plus forte du bootcamp : un VP Operations voit un agent AI repondre en langage naturel sur ses propres workflows, avec ses propres donnees reelles.

Livrable Jour 3 : 2-3 workflows end-to-end demoables, au moins une fonction LLM-backed, agents AIP Logic configures.

**JOUR 4 — Stress testing, evaluation, durcissement**

Ce que "stress testing" signifie vraiment : pas du load testing. Une interrogation par les experts domaine les plus experimentes du client. Format war-gaming live : les experts essaient de casser le systeme avec leurs scenarios reels les plus difficiles. "What happens when a rush order comes in for a product we don't have in stock?" "What if the sensor data shows a false positive on a maintenance alert?"

Chaque defaillance est loguee : Critical (fix avant Jour 5) / Important / Noted. Les FDEs corrigent immediatement les Critical. L'instrumentation utilise AIP Evals pour les test cases et AIP Observability pour l'historique des runs, traces, logs.

Apres-midi : le DS prepare le narratif executif avec le project lead client. L'application Workshop est "polie" — styling, navigation, KPI tiles executives.

Livrable Jour 4 : suite d'evaluation, failure mode register, prototype bug-fixed, draft narratif executif, app polie.

**JOUR 5 — Readout executif, ROI, roadmap de deploiement**

Executive sponsor plus 5-10 senior stakeholders. Presentation de 45-60 minutes.

Structure : (1) Problem statement en 2-3 slides — la douleur quantifiee du workflow actuel. (2) Demo live 15-20 minutes — le DS narre, le FDE conduit le walkthrough. (3) Business impact projection — ROI quantifie. (4) Deployment roadmap — prototype vers production. (5) Architecture technique en option.

Le framework ROI utilise trois composantes : economies de temps × cout main-d'oeuvre + reduction erreurs × cout par erreur + amelioration throughput × revenu par unite. Exemple concret : "If current triage takes 45 minutes per work order and the prototype reduces it to 8 minutes, across 200 work orders/week — that's $540,000 annually from this single use case."

Dynamique cle : les participants qui ont co-construit pendant 4 jours deviennent les defenseurs les plus puissants dans la salle. L'executive sponsor voit ses propres employes defendre la solution. Palantir n'est pas en train de vendre — ses clients vendent a leur place.

**Taux de conversion**

Le taux de conversion du bootcamp vers un pilot paye est estime a ~22%. Ce chiffre est contre-intuitif pour quiconque croit qu'un effort gratuit de 5 jours devrait convertir plus. Mais 22% sur 1,300+ bootcamps = 286+ clients converts via ce canal seul. Et le cout marginal d'un bootcamp qui ne convertit pas n'est pas perdu : c'est du feedback produit, de la donnee sectorielle, et un prospect qui reste dans le pipeline.

---

**4.4 Le FDE Model — anatomie complete**

---

**Delta vs Echo : les deux roles fondamentaux**

Le modele FDE de Palantir repose sur une dualite rigoureuse. Deux roles, deux types d'humains, une unite de deploiement inseparable.

**DELTA = Forward Deployed Software Engineer (FDSE)**

La definition du Delta par opposition au Dev de produit : "One customer, many capabilities" contre "one capability, many customers". Le Delta construit vite, ecrit du "rough and ready code", priorise l'impact immediat sur l'elegance architecturale.

Profil : median ~25 ans, recrutes dans les top CS programs (Stanford, MIT, CMU) mais aussi philosophie, mathematiques, physique. L'excellence technique est necessaire mais pas suffisante.

Mark Scianna (ex-FDE) : *"If I could sum FDE up in one sentence, it's that Palantir really believes you should put an engineer as close to the problem as possible."*

Historiquement : Palantir a eu plus de Deltas que de Devs avant 2016. L'entreprise a ete construite sur ce ratio.

**ECHO = Deployment Strategist (DS)**

Non-ingenieur. Expert domaine. Gestionnaire de relations. Specialiste du changement organisationnel. Profil typique : ex-McKinsey, BCG, Bain (confirme par analyse LinkedIn). Le "Rainbow role" — aucune definition fixe, autonomie maximale.

Mission du DS : trouver la "Goldilocks zone" — techniquement faisable en quelques jours, visiblement impactant pour les executives, extensible pour seeder l'ontologie pour les use cases futurs.

Pascal Unger (LinkedIn) : *"FDEs handle technical building and implementation; Deployment Strategists manage commercial strategy and change management. Two different humans, two different skill sets, working as one team."*

**La philosophie fondamentale : Auftragstaktik**

Barry McCardel (ex-Palantir, CEO de Hex) decrit la doctrine : mission-type tactics militaires. Les seniors fixent uniquement les objectifs de haut niveau. Les equipes terrain ont toute latitude d'execution. Cela cree un "chaos" intentionnel ou des equipes paralleles s'attaquent aux memes problemes — les vainqueurs emergent par adoption naturelle, competition darwinienne entre solutions.

Cela explique pourquoi les FDEs sont difficiles a manager mais produisent des resultats que des equipes classiques n'atteindraient pas. L'autonomie n'est pas un bug — c'est le mecanisme.

**Semaine typique d'un FDE**

Jours on-site (2-4 jours par semaine selon la phase) : matin avec les stakeholders techniques ou business chez le client ; apres-midi pour monitoring, debugging, deploiement, configuration ; en continu, observation des workflows reels — pas des SOPs documentees ; ad hoc, demonstrations de prototypes et construction de relations aux deux extremes de la hierarchie client, operateurs ET executives.

Jours bureau ou remote (1-3 jours par semaine) : code changes et configurations plateforme ; code reviews ; "What I've Learned From Customers" — mises a jour hebdomadaires partagees company-wide, mecanisme crucial de capitalisation du savoir ; engineering reviews.

Heures reelles : 7h00 a 19h00 typique, plus Slack depuis chez soi. Note Glassdoor work-life balance : 2.7 sur 5. Ce n'est pas un emploi — c'est un style de vie.

Nabeel Qureshi a vecu a Toulouse pendant un an pour Airbus. La devise interne est : "Get on a plane first, ask questions later."

**Pipeline de formation d'un nouveau FDE**

Semaines 1-3 : Bootcamp intensif interne sur l'ontologie, l'engagement client, la plateforme. Semaines 3-6 : placement en paire sur un compte client existant avec un lead senior. Mois 2-4 : propriete croissante de workstreams techniques specifiques. Mois 4-6 : autonomie quasi-complete sur des workstreams definis.

Les 5 livres remis au Jour 1 :
1. Impro (Keith Johnstone) — dynamiques de statut, lire la salle
2. The Looming Tower — histoire du 11 septembre, silos d'information, mission morale de Palantir
3. Interviewing Users (Steve Portigal) — techniques d'interview utilisateur
4. Getting Things Done (David Allen) — productivite sous pression extreme
5. Principles (Ray Dalio) — decision-making, transparence radicale

Le message implicite de cette liste : les competences techniques sont acquises. Ce qui differencie, c'est le social, l'observation, l'organisationnel.

**Ce qui fait vraiment marcher le modele**

Observation over documentation : les FDEs shadowent les utilisateurs plutot que de lire les SOPs. Ils reconstruisent les processus reels, pas les processus officiels. Zoe Scaman : les FDEs doivent devenir "wallpaper — present enough to observe, invisible enough not to trigger the immune system."

Le probleme politique des donnees (8-12 semaines de guerre) : Nabeel Qureshi — "Data integration was the core bottleneck. Organizations controlled data sources and justify their existence by being the gatekeepers of that data source." La solution : sponsoring executif au plus haut niveau (le CEO d'Airbus a defini la priorite directement), demontrer la valeur avant de demander plus d'acces, rendre les gardiens des donnees partenaires plutot qu'obstacles.

La continuite deliberee : le meme FDE team qui execute le bootcamp continue avec le compte s'il convertit. Choix delibere qui cree un investissement personnel dans la conversion. Le FDE ne peut pas "dumper" un compte difficile sur quelqu'un d'autre — il a co-construit le pilot.

Le feedback R&D : le travail FDE est classe en R&D dans les financials, pas en services professionnels. Chaque solution client-specifique est potentiellement un futur primitif produit. Ce qui fonctionne chez un client steel maker peut devenir un template pour tous les steel makers.

**Compensation FDE (2025-2026)**

| Niveau | Compensation totale |
|--------|---------------------|
| New Grad FDSE | $185,000 - $230,000 |
| FDSE | $215,000 - $300,000 (median $215K) |
| Senior FDSE | $300,000 - $415,000 |
| Staff-Level FDSE | $415,000 - $630,000+ |
| FDE embedding G-Cloud UK | 150K GBP par personne par trimestre (~$760K/an) |

**Attrition — la realite**

| Metrique | Valeur |
|----------|--------|
| Tenure moyen company-wide | 3.2 ans |
| Employes moins de 1 an | 35% |
| Point d'inflexion burnout | 2-3 ans |
| Work-life balance Glassdoor | 2.7 sur 5 |

Le modele comme "founder factory" : il y a plus d'ex-Palantir que d'ex-Googlers dans chaque batch YC, malgre 50x plus d'employes chez Google. Anduril, Affirm, Hex, Scale AI — tous des ex-Palantir. L'attrition elevee n'est pas seulement un probleme — c'est aussi un mecanisme de distribution de l'ADN Palantir dans l'ecosysteme tech mondial.

---

**4.5 L'Ontologie — le coeur du moat**

---

**Definition**

L'Ontologie Palantir n'est pas une base de donnees. C'est un metadata overlay editable en temps reel qui mappe des entites du monde reel sur des datasets tabulaires. Les objets sont des materialized views sur des donnees tabulaires — l'Ontologie ne stocke jamais de donnees elle-meme. Elle mappe vers des datasets existants.

Alex Karp : *"In the end you have products, your business, chips and ontology. This is how you get things to work."*

**Les 6 Primitives**

| Primitive | Definition | Details techniques |
|-----------|------------|-------------------|
| Object Types | Schema d'une entite du monde reel | String PK obligatoire, backed par un ou plusieurs datasets, writeback dataset inclus. L'ID ne peut pas etre modifie apres premier deploy |
| Properties | Caracteristiques d'un object type | 17+ types de base : Boolean, Date, Decimal, GeoPoint, Vector, TimeSeries, Structs (1-10 champs, profondeur 1) |
| Link Types | Relations nommees entre object types | Cardinalities : 1-to-1, 1-to-many, many-to-many. Traversal sans SQL joins |
| Action Types | Mutations permises — les "verbes" de l'Ontologie | Parametres types, regles de validation, side effects (notifications, webhooks), permissions role-based, commit transactionnel |
| Interfaces | Types abstraits pour le polymorphisme | Non backes par des datasets. Permettent le code generique sur plusieurs object types |
| Functions | Logique code native a l'Ontologie | TypeScript v2 ou Python, execution sandboxee, registre de fonctions reutilisables, APIs auto-generees sur changement de schema |

**Les 3 Couches**

La couche Semantique (WHAT) — Entites, proprietes, relations. Object Types + Properties + Link Types + Interfaces. Cette couche definit CE QUI EXISTE dans l'univers metier du client.

La couche Cinetique (HOW) — Actions, Functions, regles de writeback. Action Types + Functions. Cette couche definit COMMENT CES ENTITES PEUVENT ETRE MODIFIEES. C'est ce qui transforme un dashboard passif en systeme operationnel.

La couche Dynamique (GUARDRAILS) — Securite, gouvernance, indexation temps reel. OMS (Ontology Management Service) + Object Storage V2 + Permissions + Schema Evolution. Cette couche APPLIQUE LES REGLES de maniere coherente a travers toute la plateforme.

**Architecture backend (Brevet US20200293561A1)**

Cinq moteurs :

| Moteur | Role |
|--------|------|
| Datastore | Stockage de donnees sources |
| Definition Engine (OMS) | Gestion des schemas, editable en temps reel |
| Association Engine | Mapping objet → lignes et colonnes exactes |
| Cache Engine | Materialized views pour operations object-oriented |
| Interface Engine | APIs auto-regenerees sur changement de schema |

Resolution des conflits via vector clocks. Schema evolution : les changements non-breaking (ajout de types et de proprietes) ne necessitent aucune migration. Les changements breaking supportent jusqu'a 500 migrations par operation.

**Pourquoi c'est le moat**

Morningstar : *"Palantir's Ontology, Switching Costs Warrant Quadrupling of Our Fair Value Estimate."*

Quatre raisons pour lesquelles l'Ontologie est un moat structurel et non juste un avantage technique :

Premierement, l'Ontologie encode des annees de connaissance institutionnelle — qui est qui, quoi est quoi, comment les entites sont liees dans cet environnement specifique.

Deuxiemement, elle devient le seul endroit ou toute l'organisation s'accorde sur la signification des donnees. Ce n'est pas technique — c'est politique et epistemologique.

Troisiemement, AIP ne fonctionne PAS sans Ontologie. Les LLMs n'ont jamais acces direct aux donnees. Ils interagissent via une architecture tool-use avec permissions explicitement scopees sur des object types et actions specifiques de l'Ontologie.

Quatriemement, Ryan Taylor : *"Our ontology is pure understanding, concretized in software. This is reality, not rhetoric."* Et : *"LLMs simply don't work in the real world without Palantir."*

**Temps de construction de l'Ontologie par client**

| Phase | Object Types | Use Cases | Acteur |
|-------|-------------|-----------|--------|
| Bootcamp (5 jours) | 5-15 | 1-2 | FDE |
| Pilot (90 jours) | 20-50 | 3-5 | FDE + CoE client |
| Expand (mois 6-24) | 100-500 | 10-30 | CoE client |
| Scale (annee 3+) | 500-1,000+ | 50-200+ | CoE client autonome |

Nebraska Medicine : 1 use case en janvier 2024 → 20+ use cases en 6 mois avec une ontologie unifiee couvrant patient flow, nurse allocation, clinical supplies, revenue cycle. L'ontologie est devenue la colonne vertebrale operationnelle de l'hopital.

---

**4.6 Le Lock-in — les 7 couches**

---

Le lock-in de Palantir est reel, substantiel, et au moins partiellement intentionnel. Comprendre ses mecanismes permet a Spider de concevoir un lock-in similaire par la valeur plutot que par l'obstruction — distinction critique.

**Couche 1 — Lock-in technique (Ontologie)**

Reconstruire une ontologie dans un autre systeme signifie : re-mapper chaque type d'entite et ses relations ; re-encoder les regles business et la logique de decision embarquees ; reconstruire le "digital twin" operationnel de l'organisation ; perdre les raffinements iteratifs accumules sur des annees.

Cout estime pour un client Enterprise : 6 a 18 mois de travail data engineering, $2M a $10M.

**Couche 2 — Lock-in pipelines de donnees**

Toutes les integrations depuis les systemes sources doivent etre reconstruites. Pour une entreprise avec des dizaines ou centaines de sources : 3 a 12 mois, $1M a $5M. Les 400+ connecteurs Palantir ne s'exportent pas dans un format exploitable par un autre systeme.

**Couche 3 — Lock-in applicatif (Workshop)**

Chaque dashboard operationnel, chaque application de workflow, chaque outil de decision construit avec Workshop est specifique a la plateforme Palantir. Tout doit etre reconstruit from scratch ailleurs. Il n'existe pas de "Workshop export" vers React ou Tableau.

**Couche 4 — Lock-in securite et gouvernance**

Structures de permissions, hierarchies de roles, regles de gouvernance des donnees — tout est specifique a la plateforme. Pour les industries reglementees (finance, sante, defense) : 3 a 6 mois de recertification securite, $500K a $2M.

**Couche 5 — Lock-in connaissance institutionnelle**

Les FDEs et "Palantir champions" internes accumulent une expertise profonde plateforme. Lors d'un changement, ce capital humain devient inutilisable. Nouvelles competences a acquerir dans toute l'organisation — les personnes les plus productives sur la plateforme sortante deviennent les moins productives pendant la transition.

**Couche 6 — Lock-in analytique (la critique de Michael Burry)**

Michael Burry : *"The friction exists in the area between raw data and the insights derived from that data."* Les donnees brutes peuvent etre exportees en CSV, JSON, Parquet. Mais le travail analytique — les tags, annotations, modeles, insights derives sur des annees — est piege dans la couche proprietaire de Palantir. Burry : *"If a customer cannot leave without losing years of analytical work, the moat is actually just obstruction."*

C'est la critique la plus pertinente : la difference entre un lock-in par la valeur (le client reste parce qu'il serait stupide de partir) et un lock-in par l'obstruction (le client reste parce qu'il ne peut pas techniquement partir sans se blesser). Palantir oscille entre les deux.

**Couche 7 — Lock-in contractuel et reglementaire**

Contrats multi-annees : 1-5 ans pour le commercial, 10 ans pour le gouvernement US. ATO (Authority to Operate) pour les environnements classifies : 3 mois a 3 ans de processus, $90K a $700K rien que pour la certification. Clearances de securite : 6-18 mois par personne pour un nouveau fournisseur. Precedent sole-source : pour Maven, le Pentagone a officiellement determine qu'aucune autre entreprise n'etait capable de repondre aux exigences.

**Cout total de migration estime**

Pour un client Enterprise depensant $10M-$50M/an :

| Composant | Cout estime |
|-----------|-------------|
| Recreation ontologie | $2M - $10M |
| Reconstruction pipelines | $1M - $5M |
| Reecriture applications | $2M - $8M |
| Recertification securite | $500K - $2M |
| Formation et perte de productivite | $1M - $3M |
| Couts de double-run | $3M - $15M |
| TOTAL | $10M - $43M |

Soit 1 a 3 fois le spend annuel Palantir. Pour les clients gouvernement : ajouter 12 a 36 mois de recertification ATO.

Le paradoxe de la clause de terminaison : Palantir inclut des clauses "termination for convenience". En theorie, les clients peuvent partir. En pratique, partir coute entre $10M et $43M en frais de transition — sans compter les 12-36 mois de perte de productivite. La clause existe juridiquement. L'exit n'existe pas economiquement.

---

**4.7 Les echecs — clients qui ont quitte Palantir**

---

La plupart de ces departs ont eu lieu entre 2015 et 2017, quand Palantir etait essentiellement une entreprise gouvernementale tentant de percer sur le marche commercial. Ces echecs ont enseigne a Palantir ses lecons les plus importantes — et chacun contient une lecon directement applicable pour Spider.

**Coca-Cola (2016) — Le cas de tarification**

Ce qui s'est passe : Coca-Cola a accepte un pilot en juillet 2014 mais a refuse de signer un contrat 5 ans en janvier 2016. L'accord aurait atteint $18M/an en annee 5.

Raisons citees par Coca-Cola : (1) cout trop eleve ; (2) volonte d'une expertise industrielle plus profonde dans un partenaire ; (3) "relation de travail" avec les jeunes ingenieurs Palantir "difficile".

Lecon : la friction culturelle Silicon Valley vs Fortune 500 est reelle. Les escalades de contrat doivent etre justifiees par de la valeur demontree avant d'etre signees. Un contrat de $18M/an qui ne convertit pas cree une anecdote negative qui circule dans les cercles Fortune 500.

**American Express (2016) — La faute attribuee**

Ce qui s'est passe : AmEx a termine son engagement apres que Palantir n'ait pas delivre les resultats attendus.

Pattern dangereux : Palantir a blame les "limitations hardware" d'AmEx et le manque de support executif — refusant d'assumer la responsabilite. Ce pattern de blame du client est revenu dans plusieurs comptes documentés.

Lecon : la responsabilisation est une condition de la confiance durable. Quand ca ne fonctionne pas, le premier reflexe de pointer vers le client est le chemin le plus rapide vers la rupture de confiance et la churn.

**Nasdaq (2015-2016) — La relation detruite en 8 mois**

Ce qui s'est passe : reunion CEO-Karp fin 2014, pilot securite debut 2015, relation "en lambeaux" en juillet. La relation s'est effondree apres un "brainstorm quelque peu farfelu" sur des projets potentiels hors du perimetre initial.

Lecon : ne pas sur-promouvoir hors du cas d'usage initial. La confiance prend du temps a construire et se detruit instantanement. La reunite "ideas session" hors-perimetre est percue comme un manque de focus et un signe que le fournisseur cherche a etendre son emprise avant d'avoir prouve sa valeur dans le perimetre engage.

**Home Depot (2017) — L'upsell non autorise**

Ce qui s'est passe : Home Depot etait un client cybersecurite cle. La relation s'est terminee pour deux raisons : premierement, Home Depot a determine qu'il pouvait compter sur ses propres employes pour le travail que faisaient les ingenieurs Palantir ; deuxiemement, Home Depot etait "irrite" quand des employes Palantir ont tente de solliciter des affaires supplementaires dans d'autres departements — en etant encore remuneres par l'equipe cybersecurite.

Lecon critique : l'expansion doit etre autorisee et orchestree par le client, pas poussee unilateralement par le vendeur. Les FDEs qui etaient pris en charge par le budget cybersecurite ont essaye de vendre a d'autres departements sans autorisation. Violer les frontieres detruit la confiance et la relation, meme si l'intent etait de creer de la valeur.

**NYPD (2017) — Le cas de portabilite des donnees**

Ce qui s'est passe : apres 5 ans d'utilisation de Palantir, le NYPD a commence silencieusement a construire un systeme de remplacement appele "Cobalt" en ete 2016. En fevrier 2017, annonce interne d'annulation du contrat Palantir.

Allegation centrale : Palantir a refuse de fournir les donnees dans des formats portables — specifiquement, les "analytical insights and tags" crees par les investigateurs NYPD dans le logiciel ne pouvaient pas etre exportes. Cobalt utilise des produits IBM assembles avec du code maison NYPD.

Michael Burry : *"If the NYPD can do it on a government budget"* — impliquant que la technologie de Palantir n'est pas irreplacable.

Lecon : le lock-in percu comme "obstruction" plutot que valeur reelle cree de la resentance et pousse les clients vers des alternatives internes. La meilleure defense est que les clients choisissent de rester, pas qu'ils soient obliges.

**JPMorgan Chase (2017) — La violation de confiance absolue**

Ce qui s'est passe : JPMorgan etait le client corporate marquee de Palantir depuis 2009, avec jusqu'a 120 forward-deployed engineers embarques. En 2013, des executives de JPMorgan ont decouvert qu'un executive securite utilisait le logiciel Palantir pour les surveiller eux-memes — lire leurs emails et tracker leurs appels telephoniques. La rupture de confiance a ete fatale.

Lecon absolue : les donnees du client ne doivent jamais etre utilisees contre les interets du client. L'acces extraordinaire confere par l'embedding FDE est une responsabilite, pas un avantage competitif. Cet incident a installe une suspicion institutionnelle sur Palantir dans tout le secteur financier.

**Patterns communs a tous les echecs**

Cinq patterns reviennent systematiquement : (1) cout percu comme excessif par rapport a la valeur demontree ; (2) friction culturelle entre le style Silicon Valley de Palantir et les cultures d'entreprise traditionnelles ; (3) violations de frontieres — surveillance, upsell non autorise, blame du client ; (4) incapacite a delivrer des resultats justifiant le prix ; (5) arrogance — les "jeunes ingenieurs de Palantir" percus comme difficiles.

Depuis 2023, AIP donne aux clients une raison convaincante d'etendre leur spend sans nouvelle integration. Le modele bootcamp ameliore la delivraison de valeur initiale. Le NDR est passe de 107% en Q3 2023 a 139% en Q4 2025. Mais les lecons structurelles restent valables pour tout concurrent — y compris Spider.

---

**4.8 Apollo — la plateforme de deploiement invisible**

---

Apollo est la plateforme de Continuous Delivery de Palantir. Elle deploie tout le logiciel Palantir, y compris elle-meme, dans tous les environnements : du cloud public aux environnements air-gapped militaires de niveau IL6. Apollo est la raison pour laquelle Palantir peut etre partout en meme temps, avec des garanties de securite uniformes.

**Architecture Hub-and-Spoke**

Le Hub Apollo est le plan de gestion centralise. Il contient l'Orchestration Engine, recoit la telemetrie de chaque environnement, evalue les contraintes, emet des Plans.

Le Spoke Apollo est deploye par environnement gere, typiquement un cluster Kubernetes. Les agents pull (pas push) les instructions depuis le Hub. Ils rapportent l'etat observe en continu.

L'architecture pull-based est critique : les agents interrogent le Hub — ils ne recoivent pas de mises a jour poussees. Cela permet l'operation dans les reseaux peu fiables ou restreints, y compris les environnements air-gapped ou la connectivite est intermittente par definition.

**Metriques de performance**

| Metrique | Valeur |
|----------|--------|
| Deployments par mois | 360,000+ |
| Temps moyen de deploiement | 3.5 minutes |
| Temps moyen de rollback | 4.9 minutes |
| Taux de succes des changements | 95.5% |
| Environnements manages | ~1,000 (dont ~100 air-gapped) |
| Upgrades par semaine | ~90,000 automatiques |
| Produits geres | 2,500 services independants |
| Amelioration frequence deploiement | 45x (8,000 → 360,000 par mois) |
| Acceleration lead time | 12,500x (1 mois → 3.5 minutes) |

**Mecanismes de securite Apollo**

Blue-Green Upgrades : nouvelle version deployee aux cotes de l'ancienne, trafic transfere, observation. Rollback automatique si probleme detecte.

Suppression Windows : apres echec de Plan, des fenetres de suppression entity-level puis environment-level evitent les pannes en cascade. Les Plans de rollback restent autorises meme pendant les suppressions — le retour en arriere ne peut jamais etre bloque.

Recall Global : rappel d'une release mauvaise dans tous les environnements simultanement. Les Plans de recall sont prioritaires sur toutes les autres operations.

Canary Promotion : promotion basee sur des SLOs. Seuil sain par defaut : 95% du temps. Rollback automatique si non atteint.

**Apollo pour les environnements classifies**

Apollo est l'unique raison pour laquelle Palantir peut operer dans des reseaux air-gapped (IL5, IL6) sans compromettre les capacites SaaS.

Mode Disconnected : les services Hub Apollo sont installes dans le reseau gouvernemental. Le fonctionnement est identique au mode centralise. Les packages sont transferes via un NOC (Network Operations Center), cryptographiquement signes, valides en integrite avant execution.

PFCS Forward (annonce DISA, 12 fevrier 2026) : autorise l'extension des certifications IL5 et IL6 aux deploiements on-premises et edge tactiques. Le principe : "Authorize once, deploy everywhere" — de la data center enterprise aux vehicules tactiques mobiles.

Certifications : FedRAMP High, DoD IL5/IL6, CMMC, 6 familles de controles NIST.

**Apollo comme produit standalone**

| Tier | Prix |
|------|------|
| Apollo SDK | Gratuit |
| Apollo Core | $100 par installation par mois |

Un service deploye sur 3 environnements (AWS, Azure, on-prem) = $300/mois. Le modele beneficie directement de l'adoption multi-cloud : chaque environnement supplementaire est une ligne de revenu supplementaire.

Clients Apollo non-Palantir : Airbus, BP (economie reportee : $1B sur les plateformes Palantir), US Army ($876M contrat battlefield data management), Rio Tinto, Credit Suisse, Fujitsu, Hyundai Heavy Industries.

**Pourquoi Apollo est strategiquement crucial**

Quatre raisons :

Premierement, Apollo elimine les concurrents de facto dans les environnements classifies. Aucun alternatif commercial ne supporte IL6 nativement.

Deuxiemement, Apollo est le Trojan Horse : un client qui adopte Apollo pour son deploiement devient dependant de l'infrastructure Palantir avant meme d'utiliser Foundry ou AIP.

Troisiemement, Apollo finance une capacite de deploiement que personne d'autre n'a. 360,000 deployments par mois cree une expertise operationnelle impossible a repliquer.

Quatriemement, Apollo cree une moat infrastructurelle separee de la moat produit. On peut imaginer un concurrent construisant une meilleure ontologie. On ne peut pas imaginer un concurrent construisant Apollo en 3 ans.

Shyam Sankar : *"At one customer, two human FTEs spawned an army of AI FTEs to migrate a customer off their legacy data warehouse in five days, something that would have taken an army of SIs up to two years. This is not a prototype. This is production."* Et Q4 2025 : *"AIFDE is now capable of powering complex SAP ERP migrations from ECC to S/4. Years of work now done in as little as two weeks."*

---

**4.9 Ce que Spider copie**

---

Neuf mappings directs entre les mecanismes Palantir et les equivalents Spider.

**Mapping 1 — Le Bootcamp comme seul vrai go-to-market**

Palantir : 5 jours gratuits, construction sur donnees reelles du client, equipe d'ingenieurs embarques, pas une demo mais une co-construction.

Ce que Spider fait : un "Spider Sprint" de 3 a 5 jours. Pas un POC vendu 50K euros. Un investissement gratuit, ou pres de gratuit, qui construit quelque chose de fonctionnel sur les vraies donnees du client.

Pourquoi : le bootcamp cree trois choses qu'aucun autre mecanisme ne peut creer aussi vite — la propriete psychologique (le client a co-construit), les preuves de valeur tangibles (pas des slides), et des champions internes (les co-builders deviennent les defenseurs).

Adaptation necessaire : Spider n'a pas les ressources pour 5 FDEs par bootcamp. La version Spider = 1-2 personnes, 3 jours, cas d'usage pre-selectionne sur donnees clients reelles. L'objectif est identique : le client voit sa propre realite dans le systeme.

**Mapping 2 — Le modele Delta/Echo comme unite minimale de deploiement**

Palantir : chaque deploiement = 1 DS (narratif, relations, business) + N FDEs (technique). Les deux roles sont distincts et complementaires.

Ce que Spider fait : toujours envoyer au moins 2 personnes en engagement client. Une personne technique (capable de construire), une personne business (capable de traduire). Ne jamais envoyer uniquement un "commercial" ou uniquement un "technique".

Pourquoi : le DS seul ne peut pas montrer. Le FDE seul ne peut pas convaincre. La paire est la moindre unite viable. L'unite de deploiement minimale est 2, pas 1.

**Mapping 3 — Le pre-travail invisible comme differenciateur**

Palantir : 2-4 semaines de travail FDE avant le bootcamp. Les donnees sont deja dans le systeme au Jour 1. La "magie" n'est pas de la magie — c'est de la preparation.

Ce que Spider fait : investir significativement avant chaque engagement client visible. Obtenir des donnees echantillons 2 semaines avant. Pre-construire le schema de base. Pre-connecter les sources. Quand le client arrive, son monde est deja dans le systeme.

Impact : le moment ou le client voit ses propres donnees dans le systeme — le "pivot emotionnel" — ne peut pas etre simule. Il doit etre reel pour produire l'effet.

**Mapping 4 — L'ontologie comme foundation architecturale**

Palantir : tout repose sur l'ontologie. Les applications, les agents AI, les actions — tous sont des vues sur l'ontologie. L'ontologie est ce qui accumule la valeur au fil du temps.

Ce que Spider fait : definir un equivalent ontologique. Ce n'est pas necessairement une replique technique exacte de l'Ontologie Palantir, mais le principe est identique — construire une couche semantique qui mappe les entites metier du client (commandes, clients, produits, employes, assets) et leurs relations, sur laquelle tout le reste est construit.

Ce que cette couche doit etre : extensible (chaque nouveau use case augmente sa valeur), co-propriete du client (ils l'ont co-construite), et difficile a migrer (encoding de la connaissance institutionnelle specifique au client).

**Mapping 5 — La progression Acquire/Expand/Scale avec des economics conscientes**

Palantir : les pilots sont deliberement non-rentables a -43%. L'investissement est justifie par l'expansion future.

Ce que Spider fait : ne pas chercher a etre profitable des le premier engagement. Definir explicitement des budgets "investissement" pour les bootcamps et pilots. Tracker les economics par phase, pas par engagement individuel.

Attention : Palantir peut absorber -43% pendant des mois parce que les revenus gouvernementaux financent ces investissements. Spider doit dimensionner ses investissements a ce qu'il peut reellement absorber — le loss-leader delibere est une strategie, le loss-leader accidentel est un chemin vers la faillite.

**Mapping 6 — La quantification ROI comme langage commun**

Palantir : a chaque etape, le DS sonde les metriques quantifiables. "How many work orders are misrouted per week? What's the cost of each misroute?" Le Jour 5 presente un ROI calcule depuis les chiffres du Jour 1.

Ce que Spider fait : integrer la quantification dans chaque phase de la methodologie. Ne jamais presenter un use case sans son ROI calcule en chiffres concrets — pas en pourcentages vagues.

Template ROI Spider : economies de temps × cout par heure + reduction d'erreurs × cout par erreur + gain de throughput × valeur par unite = impact annuel. Ce calcul doit etre fait avec les chiffres specifiques du client, jamais avec des benchmarks generiques.

**Mapping 7 — La creation de champions internes**

Palantir : les participants au co-building deviennent les defenseurs les plus puissants dans la salle executive. Palantir n'essaie pas de convaincre le C-suite directement — Palantir convainc les managers operationnels qui convainquent le C-suite.

Ce que Spider fait : identifier les "champions potentiels" des le scoping. Ce sont les personnes qui souffrent le plus du probleme, ont l'autorite de le resoudre, et seront reconnues si la solution reussit. Les impliquer profondement dans le co-building, pas juste en tant que spectateurs.

**Mapping 8 — La transparence radicale sur les limitations**

Palantir : le Jour 4 est explicitement dedie au stress testing — trouver et documenter les cas ou le systeme echoue. Le "failure mode register" est un livrable officiel.

Ce que Spider fait : ne jamais livrer un prototype sans sa documentation des limitations. Un client qui decouvre les limitations en production perd confiance. Un client qui les connait a l'avance les gere. La transparence sur les limitations est une forme de confiance, pas une faiblesse.

**Mapping 9 — La formation du Centre of Excellence client**

Palantir : l'objectif a long terme est que le client soit autonome. Roles definis : Platform Owner, Permissions Manager, Data Engineers, Application Builders, Analystes. Palantir Learn pour la certification.

Ce que Spider fait : definir les roles equivalent Spider-enabled au niveau client. Creer du materiel de formation. Mesurer le succes non par le nombre de personnes Spider embarquees mais par l'autonomie progressive du client.

Le paradoxe productif : plus le client est autonome, plus il etend l'usage (il peut experimenter sans demander l'aide de Spider), et plus le spend croit. L'autonomie n'est pas un risque de desengagement — c'est le mecanisme d'expansion le plus puissant.

---

**4.10 Ce que Spider ne copie PAS**

---

Sept points ou le modele Palantir n'est pas transposable directement, avec les raisons structurelles et les alternatives Spider.

**Point 1 — Le modele de pricing opaque**

Palantir : opacite de prix totale, "no pricing strategy for AIP", negociation cas par cas, minimum viable $250K+ ACV. La reference G-Cloud UK expose des contrats a partir de £250K/an — et ce n'est que la reference publique minimale.

Pourquoi Spider ne peut pas copier : Spider n'a pas la credibilite de marque, la profondeur de produit, ni les references qui justifient cette opacite. L'opacite de prix est une strategie des entreprises qui ont le leverage. Spider, en phase de lancement, a besoin de prix lisibles et previsibles pour reduire la friction d'entree.

Ce que Spider fait a la place : packaging transparent avec une logique de valeur claire. Le prix augmente avec l'usage et la valeur generee, pas avec l'arcanisme de la negociation. Chaque client sait pourquoi il paie ce montant.

**Point 2 — Les timelines de deploiement**

Palantir : pilots de 3-6 mois. Phases Expand de 6-24 mois. Phases Scale de 24+ mois. Graduation des FDEs en 36 mois pour le commercial, 48 mois pour le gouvernement.

Pourquoi Spider ne peut pas copier : ces timelines sont adaptees a des organisations qui ont le budget et la patience pour des investissements de cette longueur. Pour les PME françaises — cible initiale de Spider — les cycles de decision sont plus courts, les budgets plus limites, et la patience executive differente.

Ce que Spider fait a la place : viser des cycles pilot de 30 a 60 jours maximum. La valeur doit etre demontrable en semaines, pas en mois. Les timelines longues de Palantir sont une consequence de la complexite de ses clients, pas un objectif en soi. Spider optimize pour la demonstration rapide de valeur — pas pour la profondeur de l'engagement initial.

**Point 3 — Le talent pool FDE**

Palantir : FDEs recrutes avec un taux d'acceptation de 1-2% parmi les top CS programs mondiaux. Chaque candidat approuve par les fondateurs. Interview incluant un "Decomposition Interview" specifique. Compensation moyenne $215K pour un new grad.

Pourquoi Spider ne peut pas copier a l'identique : ce type de talent est rare, couteux, et ne correspond pas au marche français au stade early-stage. Palantir a pris plus de 10 ans pour developper ce playbook de recrutement.

Ce que Spider fait a la place : privilegier des profiles hybrides (technique + sens business) avec une expertise domaine forte dans 1-2 verticaux cibles. La profondeur sectorielle — par exemple, le manufacturing français — peut compenser la breadth du profil Palantir generique. Commencer avec 3-4 personnes exceptionnelles plutot qu'une equipe de 20 personnes mediocres. Quality over quantity, avec une specialisation sectorielle comme differenciateur.

**Point 4 — La strategie gouvernement US**

Palantir : 35% du chiffre d'affaires gouvernemental. Contrats sole-source. IL6, FedRAMP High. Programmes Maven, TITAN, Army ESA. Ce segment a ete crucial pour financer les pertes du segment commercial pendant des annees.

Pourquoi Spider ne peut pas copier : l'acces aux mega-contrats gouvernementaux US est le resultat de 15 ans de relations, de certifications ATO couteuses, et d'une culture specifique. Palantir est fondamentalement une entreprise de defense qui s'est ensuite attaquee au commercial. Spider opere sur le marche français et europeen avec des dynamiques de procurement radicalement differentes.

Ce que Spider fait a la place : si la voie publique est envisagee, cibler des appels d'offres europeens plus accessibles. La souverainete numerique europeenne est un avantage competitif potentiel — Palantir est americain, Spider est europeen — pas un desavantage. En 2026, la question de la dependance technologique aux US est un sujet politique reel en Europe.

**Point 5 — Le modele de loss-leader en Acquire a grande echelle**

Palantir : investissement de centaines de millions en pertes sur le segment Acquire pour construire le portefeuille commercial. Le S-1 confirme -$65.4M de perte sur la cohorte Acquire totale. Ce n'est viable que parce que le segment gouvernement generait $1.5B+ par an pour financer la machine.

Pourquoi Spider ne peut pas copier : Spider n'a pas de segment gouvernemental generant $1.5B/an pour financer des pertes sur le commercial. Chaque engagement doit contribuer a la sustainability financiere, meme si la contribution est differee.

Ce que Spider fait a la place : budgeter precisement les "investissements" bootcamp et pilot. Definir un seuil de conversion minimum en dessous duquel un compte n'est pas poursuivi. Le loss-leader delibere est une strategie — le loss-leader accidentel est un chemin vers la faillite. L'asymetrie de Palantir (gouvernement finançant le commercial) n'existe pas pour Spider, et il ne faut pas agir comme si elle existait.

**Point 6 — L'echelle des evenements publics type AIPCon**

Palantir : AIPCon 8 = 70+ speakers, des centaines de participants, national spotlight. Ces evenements coutent des millions a organiser et ne sont possibles que parce que Palantir a 954 clients dont beaucoup sont prets a temoigner publiquement.

Pourquoi Spider ne peut pas copier maintenant : Spider n'a pas encore le portefeuille de clients qui justifie cet investissement. AIPCon a commence modestement avec AIPCon 1 en juin 2023 et a grandi avec le portefeuille. La sequence est inverse de ce qu'on pourrait croire — l'evenement n'a pas cree les clients, les clients ont cree l'evenement.

Ce que Spider fait a la place : investir tres tot dans la documentation de cas d'usage. Chaque client satisfait = un temoignage video, un case study ecrit, une reference disponible. L'equivalent de l'AIPCon pour Spider en Annee 1 est une table ronde de 5 a 10 clients. En Annee 3, si le portefeuille le justifie, un evenement sectoriel.

**Point 7 — La taille des equipes FDE par compte**

Palantir : 4-5 FDEs en phase Acquire. Jusqu'a 120 FDEs embarques chez JPMorgan (cas extreme). Pour un compte strategique, 10-20 FDEs deployes sur plusieurs mois.

Pourquoi Spider ne peut pas copier : ces tailles d'equipes ne sont viables qu'avec des ACV correspondants ($5M+ pour justifier 5 FDEs pendant 6 mois). Spider commence avec des ACV beaucoup plus petits et une base de clients PME.

Ce que Spider fait a la place : optimiser le ratio valeur-delivree sur personnel-deploye. L'AIFDE de Palantir est la reponse a ce probleme — 2 FDEs humains plus des agents AI pour migrer un data warehouse en 5 jours (ce qui aurait pris 2 ans a une armee de SIs). Spider doit integrer cet effet de levier AI des le debut, pas comme evolution future. Le levier IA n'est pas une promesse — il est disponible maintenant et change le denominateur du ratio FDE-par-client de maniere structurelle.

---

**Synthese — ce que Palantir prouve pour Spider**

---

Palantir prouve trois choses que personne d'autre ne pouvait prouver avant 2023.

Premierement, que la methodologie de deploiement est aussi importante que le produit lui-meme. Le bootcamp n'est pas du marketing — c'est le mecanisme de creation de valeur. Le produit sans le bootcamp serait un SaaS generique. Le bootcamp sans le produit serait du consulting. Les deux ensemble creent quelque chose de nouveau.

Deuxiemement, que le NDR de 139% est possible dans l'enterprise software — et que ce NDR vient de l'architecture ontologique qui rend chaque nouveau use case moins cher que le precedent pour le client, et plus rentable pour Palantir.

Troisiemement, que les echecs de 2015-2017 (Coca-Cola, AmEx, Nasdaq, Home Depot, NYPD, JPMorgan) ont ete causes non par des problemes techniques mais par des violations de la confiance, des arrogances culturelles, et des violations des frontieres commerciales. La technologie etait suffisante. L'execution commerciale etait defaillante.

Ces trois preuves sont directement exploitables par Spider — avec les adaptations documentees en 4.10 pour les realites du marche PME europeen et du contexte early-stage.

Alex Karp : *"Unlike seemingly in the most obvious way, we are downstream from the value creation. The reason why that's working is because we are making our clients more money or we're making them more dominant on the battlefield, and they're paying us a subset of that."* C'est le principe directeur. Spider est en aval de la valeur creee. La negociation sur le prix est une negociation sur le partage de cette valeur — pas sur le cout de la plateforme.

---

*Section 4 — 21 fevrier 2026 — v1.0*
