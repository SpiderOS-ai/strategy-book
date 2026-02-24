# PLAYBOOK DÉFINITIF — REVERSE ENGINEERING PALANTIR

> Assemblé le 18 février 2026 à partir de 20+ documents sources (Perplexity Deep Research, ChatGPT Deep Research, Claude Deep Research, Claude Agent Research, Playbook HTML 322KB)
> ~5 000 lignes · Couvre l'intégralité de la méthode Palantir de l'avant-vente à l'après-vente

---

# PARTIE 1 — AVANT-VENTE & AIP BOOTCAMP

> **Playbook operationnel — Methode Palantir**
> Redige a partir de la synthese croisee de trois sources de deep research (GPT, Claude, Perplexity) et du playbook exhaustif consolide (322KB, 27 fichiers de recherche, 4 phases).
> Les annotations (GPT), (Claude), (Perplexity) indiquent les faits provenant d'une seule source.
> Les faits non annotes sont confirmes par au moins deux sources.
> [CONTRADICTION] signale les divergences entre sources.
> [CONFIRMED], [ESTIMATED], [SPECULATIVE] suivent le systeme de confiance du corpus de recherche.

---

## 1.1 Sourcing & Pipeline

### Positionnement strategique du Bootcamp dans le Go-To-Market

Le Bootcamp AIP est **la principale motion go-to-market de Palantir pour AIP**. Ce n'est pas un canal parmi d'autres — c'est LE canal. Trois citations d'executives confirment cette centralite :

- **Ted Mabrey** (Head of Global Commercial) : *"Our primary means of going to market with AIP will be through these bootcamps"* (Perplexity)
- **Alex Karp** (CEO) : *"We're already overfilled for our AIP bootcamp... It's like a rock concert"* (Perplexity)
- **Shyam Sankar** (CTO) : *"The boot camp is not a demo. It's not a presentation. We show up with engineers, and we build"* (Claude)

Le bootcamp remplace a la fois le cold outreach et les POC traditionnels. Palantir a historiquement evite une force de vente traditionnelle. Karp a dit un jour : *"the only way he'd hire salespeople was if he were 'hit by a bus'"* — croyant que les resultats du logiciel se vendraient d'eux-memes (Perplexity). Ce modele a evolue avec l'explosion de la demande pour AIP en 2023-2024.

Ryan Taylor (CRO) a declare sur l'earnings call Q3 2023 : *"We reoriented our go-to-market approach around AIP boot camps, which has allowed us to deliver real workflows on actual customer data in five days or less versus our traditional pilots, which generally take one to three months"* (Perplexity).

### Canaux d'acquisition

Le pipeline est **hybride** (Perplexity), avec une dominante inbound :

#### Inbound (dominant)

- **AIPCon** (2023 et 2024) : Evenements majeurs de generation de demande. Les keynotes, demos live, et temoignages clients generent un flux massif de prospects qualifies.
- **Bouche-a-oreille des alumni de bootcamp** : Les participants aux bootcamps precedents organisent leurs propres evenements et deviennent des *"unofficial salespeople"* (Perplexity). Le bootcamp genere des ambassadeurs de marque independamment de la conversion.
- **Reseaux de partenaires** : Accenture (partenariat formel en decembre 2025 avec 2,000+ professionnels formes sur Palantir — [CONFIRMED]), PVM, Carahsoft.
- **Visibilite via les earnings calls** : Les presentations aux investisseurs, avec des chiffres de croissance spectaculaires, generent de la curiosite chez les decision-makers.

#### Outbound

- Les **Account Executives** ciblent des entreprises specifiques. Karp a decrit l'obtention d'un contrat de 3M$ via outbound prospecting, puis le deploiement d'un bootcamp, et l'expansion a un accord enterprise-wide dans le meme trimestre (Perplexity).
- L'outbound est cible et strategique, pas du mass-market cold calling.

#### Partenaires

- **PVM et Carahsoft** organisent leurs propres bootcamps avec le logiciel Palantir, en particulier pour les verticaux gouvernement/defense (Perplexity).
- **Accenture** : Partenariat formalise en decembre 2025. 2,000+ professionnels Accenture formes sur la plateforme Palantir. Accenture peut effectuer des deploiements et des bootcamps de maniere semi-autonome [CONFIRMED].
- **Deloitte, Booz Allen Hamilton, IBM** : Partenaires d'implementation et d'advisory [CONFIRMED].

### Roles dans le sourcing

| Role | Responsabilite dans le sourcing |
|------|--------------------------------|
| **Account Executive (AE)** | Proprietaire de la relation commerciale. Pipeline qualification. Outbound prospecting. Orchestrateur interne des ressources. Navigue les protocoles de procurement complexes. Developpe les profils clients. (GPT, Claude, Perplexity) |
| **Deployment Strategist (DS)** | Role explicitement operationnel et oriente decouverte. Va onsite pour comprendre les questions critiques. Mene le scoping call. Determine les donnees necessaires. Identifie les use cases. Requiert 25-75% de voyage. (GPT, Perplexity) |

L'AE "shepherds" les engagements du premier meeting au procurement jusqu'au closing (GPT). Le DS determine *"the kinds of data that the clients need to provide"* puis communique avec les ingenieurs pour *"integrate the data, analyse the data and think about the workflow"* (Perplexity).

### Volume de bootcamps

| Periode | Volume cumule | Source |
|---------|--------------|--------|
| Mi-2023 | ~50 bootcamps | [CONFIRMED] |
| Fin Q3 2023 | ~100 bootcamps | (Claude) |
| Fin Q4 2023 | 560+ bootcamps a travers 465+ organisations | [CONFIRMED] |
| Fin Q1 2024 | 915+ bootcamps | (Claude) |
| Juin 2024 | 1,300+ bootcamps | [CONFIRMED] |
| Fin Q3 2024 | 1,400+ bootcamps | (Claude) |
| Fin Q4 2024 | 1,300+ (donnee potentiellement anterieure) | (Perplexity) |
| Cadence 2024 | **~5 bootcamps par jour** globalement | [CONFIRMED] — Bloomberg |

[CONTRADICTION mineure sur la chronologie] Claude donne 1,400+ fin Q3 2024 et Perplexity donne 1,300+ fin Q4 2024. L'ecart est probablement du a des sources differentes ou des moments de citation differents dans les earnings calls.

### Cout pour le client

**GRATUIT**. Les bootcamps initiaux AIP sont *"typically offered free-of-charge"* [CONFIRMED] (GPT, Perplexity). D'apres les SEC filings, Palantir fournit souvent ses plateformes aux clients potentiels *"at no or low cost"* via des pilotes court terme, y compris les bootcamps, et la conversion n'est pas garantie (GPT).

**Cout pour Palantir** : $12K-$36K par bootcamp (cout de personnel charge : 1-5 jours x 5-8 personnes) [SPECULATIVE].

---

## 1.2 Qualification — ICP (Ideal Customer Profile)

### Profil Client Ideal

#### Secteurs cibles

Defense/renseignement, aerospatiale, sante/sciences de la vie, energie/petrole & gaz, manufacturing, services financiers, supply chain, logistique (Claude, Perplexity).

#### Caracteristiques de l'entreprise

- **Grandes entreprises** avec des environnements de donnees complexes, multi-systemes, ou les decisions sont prises *autour* de leurs ERP/CRM plutot que *a travers* eux (Claude, Perplexity).
- Organisations ou le *"existing software stack does not solve"* le probleme (Perplexity).
- Le modele economique FDE requiert des deals **>= 1M$ ACV**. Les contrats sous 200K$ ne sont pas rentables pour le modele FDE (Perplexity).
- La taille moyenne des deals issus de bootcamps depasse 1M$ (Perplexity).

> **Colin Anderson** (ancien CFO, Palantir) : *"The model is only financially sustainable for seven-figure contracts and above, with eight or nine figures being the sweet spot."* [CONFIRMED]

#### Signaux de readiness

1. Le client **reconnait un probleme operationnel specifique** (pas une curiosite vague pour l'IA).
2. Dispose de **donnees structurees et/ou non structurees accessibles** pour l'ingestion.
3. Peut **mobiliser business owners, operateurs, et IT stakeholders** pour un engagement d'une semaine (Perplexity).

### Criteres de qualification "Bootcamp-Ready"

Les trois sources convergent sur les prerequis suivants :

| # | Critere | Detail | Sources |
|---|---------|--------|---------|
| 1 | **Participants confirmes** | Business owners, end-users/operateurs, et IT stakeholders prets a participer. | GPT, Claude, Perplexity |
| 2 | **Static cuts de donnees** | Donnees liees aux workflows/use cases, fournies 1-2 semaines avant le bootcamp. | GPT, Claude, Perplexity |
| 3 | **Discussions de cadrage des use cases** | En amont, pour permettre a Palantir de *"pre-build as much as possible"*. | GPT, Claude, Perplexity |
| 4 | **Discussion de 30min avec les data owners** | Une fois les datasets partages. | Perplexity (GPT mentionne la discussion sans preciser la duree) |
| 5 | **Signature des Terms of Service** | Pour permettre a Palantir d'initialiser un environnement Foundry prive. | GPT, Claude, Perplexity |
| 6 | **Donnees tractables** | Static cut avec identifiants stables, historique suffisant et ground truth pour validation. | (GPT) |
| 7 | **Short list de use cases a fort levier** | Avec des decision-makers engages. | (GPT) |
| 8 | **Readiness legale/securite** | Capacite a gerer rapidement les etapes legales et de setup d'environnement. | (GPT) |

[CONTRADICTION sur le nombre de participants cote client] :
- **Claude** : 8-12 participants (executive sponsor, 2-3 business/domain SMEs, 2-3 data engineers ou analystes, un project lead).
- **Perplexity** : 5-20 stakeholders.
- **Playbook consolide** : 5-20 stakeholders: mix of C-suite sponsors, business unit leaders, technical architects, and end-users [CONFIRMED from AIPCon presentations].

La fourchette 5-20 semble etre le range officiel, avec 8-12 comme configuration typique.

### Le scoping call

Le Deployment Strategist mene un **scoping call** (typiquement **60-90 minutes**) avec les stakeholders techniques et business du prospect (Claude).

**Qui participe :**
- Cote Palantir : Le DS (lead), parfois un FDE senior pour les questions techniques.
- Cote client : Stakeholders techniques (data engineers, IT leads) et business (business owners, domain experts).

**Ce qui est evalue :**
- Use cases candidats et leur faisabilite en 5 jours.
- Disponibilite des donnees (format, volume, accessibilite).
- Engagement des stakeholders cles.
- Obstacles legaux/securite potentiels.

**Le gate :** Ce scoping call est la **porte critique**. Si le DS determine que :
- les donnees du prospect sont trop verrouillees,
- les use cases trop vagues,
- ou les stakeholders non engages,

le bootcamp **ne procede pas** (Claude).

Le processus de pre-qualification implique typiquement **3-5 calls** avec les stakeholders client (playbook consolide) [ESTIMATED].

---

## 1.3 Staffing du Bootcamp

### Composition de l'equipe Palantir

| Role | Nombre | Fonction | Sources |
|------|--------|----------|---------|
| **Deployment Strategist (DS)** | 1 (parfois 1-2) | Proprietaire du narratif, facilitation, stakeholder management, articulation de la valeur business, priorisation des use cases | GPT, Claude, Perplexity |
| **FDE / FDSE** | [CONTRADICTION] | Construction technique, prototypage rapide, demos live, validation donnees | GPT, Claude, Perplexity |
| **Account Executive (AE)** | 1 | Present au kickoff et demo day, conversations commerciales, identification des opportunites d'expansion | GPT, Claude, Perplexity |
| **Product Specialist** | 1 | Expert AIP/Foundry, configuration plateforme, demonstration des capacites avancees | Playbook consolide [ESTIMATED] |
| **Solution Architect** | 0-1 | Integration enterprise, architecture de securite, topologie de deploiement | Playbook consolide [ESTIMATED] |
| **FDIE (Forward Deployed Infrastructure Engineer)** | Optionnel | Setup d'environnement, notamment pour les deploiements on-prem | (Claude) |
| **Specialiste securite ou plateforme** | Optionnel | Sollicite si l'environnement, la gouvernance, ou le pattern d'integration de modele est non-standard | (GPT) |
| **SMEs verticaux** | Optionnel | Ingenieurs avec expertise domaine pour les bootcamps verticaux specifiques | (Perplexity) |

[CONTRADICTION sur le nombre de FDEs] :
- **GPT** : 1-3 FDEs ou AI Engineers
- **Claude** : 1-2 FDEs, equipe totale de 2-5 personnes Palantir
- **Perplexity** : 1-2 FDEs/FDSEs
- **Playbook consolide** : 2-4 FDEs [ESTIMATED]

Pour les engagements complexes ou les comptes strategiques, un **FDE senior** ou **Deployment Lead** coordonne le bootcamp global (Claude).

### Modele Delta/Echo

Palantir utilise un modele interne d'equipes **Echo** et **Delta** [CONFIRMED] (ex-employes) :

#### Echo Team (DS / analystes embarques)

- **Profil** : Experts domaine qui comprennent le terrain du client. Souvent d'anciens officiers militaires, praticiens de sante, ou *"heretiques"* de l'industrie qui comprennent les defauts du statu quo.
- **Background typique** : Ex-McKinsey, BCG, Bain [CONFIRMED from LinkedIn analysis].
- **Fonction** : Identifient les problemes a fort levier, gerent les relations, determinent QUEL use case construire en premier.
- **Citation cle** : Le DS doit trouver le *"Goldilocks zone: technically feasible within days, visibly impactful to executives, and extensible enough to seed the ontology for future use cases"* [CONFIRMED from former DS interviews].

#### Delta Team (FDEs / ingenieurs de prototypage rapide)

- **Profil** : Ingenieurs hautement qualifies, median d'age ~25 ans [CONFIRMED], recrutes dans les top CS programs (Stanford, MIT, CMU) mais aussi en philosophie, mathematiques et physique [CONFIRMED].
- **Fonction** : Construisent vite, ecrivent du *"rough and ready code"* pour delivrer une valeur immediate.
- **Philosophie** : *"Doers, not artisans obsessed with perfect code"* — accoutumes a *"eating a lot of pain"* (Perplexity).
- **Citation cle** : Mark Scianna (ex-FDE, maintenant Forward Deployed VC) : *"If I could sum FDE up in one sentence, it's that Palantir really believes you should put an engineer as close to the problem as possible"* (Perplexity).

#### Comment les deux equipes collaborent

Pascal Unger (LinkedIn) : *"FDEs handle technical building and implementation; Deployment Strategists manage commercial strategy and change management. Two different humans, two different skill sets, working as one team"* (Perplexity).

### Comment l'equipe est assemblee en interne

Les decisions de staffing sont prises par le **leadership regional de deploiement** en coordination avec l'AE, basees sur (Claude, Perplexity) :

1. **Expertise verticale** : Un FDE ayant fait des bootcamps manufacturing est assigne aux prospects manufacturing.
2. **Correspondance des competences techniques** : Expertise ontologie vs. expertise AIP Logic.
3. **Disponibilite**.

**Continuite deliberee** : Le meme FDE team qui execute le bootcamp continue generalement avec le compte s'il convertit — cette continuite est un **choix delibere** qui cree un investissement personnel dans la conversion (Claude).

---

## 1.4 Preparation Pre-Bootcamp (2-4 semaines avant)

La preparation pre-bootcamp est l'element le plus sous-apprecie du playbook. La *"magie"* du Jour 1 — quand le client voit ses donnees deja live dans le systeme — est en realite le resultat de **2-4 semaines de travail FDE sans glamour** : lutter avec des CSVs, debugger des connexions JDBC, ecrire des transformes PySpark, et construire l'echafaudage d'ontologie (Claude).

### Workstream 1 — Acquisition et ingestion des donnees

#### Ce que Palantir demande au client

- **Static cuts de donnees** basees sur le workflow/use case, livrees **1-2 semaines** avant le bootcamp (GPT, Claude, Perplexity).
- Pas de format specifique impose. Les formats acceptes sont (Claude, Perplexity) :
  - **CSV/Excel** : Point de depart le plus courant, moindre friction.
  - **Fichiers Parquet**.
  - **Dumps JSON**.
  - Connexions **JDBC** : SQL Server, PostgreSQL, Oracle, Snowflake (via le framework Data Connection de Foundry).
  - Connecteurs **API** pour les plateformes SaaS : Salesforce, SAP, ServiceNow.
  - Pulls **cloud storage** : S3, Azure Blob, GCS.
  - Ingestion **streaming via Kafka** pour les cas temps reel.
- Pour les organisations sensibles en securite : **replicas read-only** ou datasets anonymises/echantillonnes sont acceptables (Claude).
- Possibilite de choisir entre donnees notionnelles ou donnees reelles : *"You choose! Either notional data or the team can work with you in advance to provide directions on how to integrate their own data"* — PVM (Perplexity).

#### Volume et profondeur des donnees

- Le but n'est pas des donnees parfaites — mais des donnees **representatives** capables d'alimenter un prototype (Claude).
- Les FDEs demandent typiquement **3-6 mois de donnees historiques** sur les domaines operationnels pertinents (Claude).
- Les donnees doivent permettre de produire un static cut avec des **identifiants stables**, plus suffisamment d'historique et de **ground truth** pour valider les outputs (GPT).

#### Ou les donnees atterrissent

Les donnees atterrissent dans Foundry en tant que **raw datasets** stockes en format **Apache Parquet**, organises dans un **environnement sandbox** provisionne specifiquement pour le bootcamp (Claude). Pipeline Builder peut ingerer des donnees de *"any source system"*, y compris des sources structurees et non structurees (GPT). Le framework Data Connection supporte **150+ native connectors** [CONFIRMED].

#### Discussion avec les data owners

Une fois les datasets partages, une **discussion de 30 minutes avec les data owners** est organisee pour comprendre la semantique des donnees (Perplexity ; GPT mentionne cette discussion sans preciser la duree).

### Workstream 2 — Pre-construction ontologie et pipelines

Les FDEs pre-construisent autant que possible avant le bootcamp (GPT, Claude, Perplexity). Le pre-build inclut typiquement **trois couches** (GPT) :

#### Couche 1 : Pipeline d'ingestion et nettoyage

- Utilisation de **Pipeline Builder** (outil visuel no-code, 80+ types de transforms, 7 types de joins, 300+ fonctions built-in — [CONFIRMED]) et **Code Repositories** (environnements PySpark/SQL) pour construire des pipelines de nettoyage et transformation (Claude, Perplexity).
- Gestion des nulls, normalisation des schemas, jointures de sources disparates, creation de datasets *"ontology-ready"* (Claude).
- Le pipeline est construit dans une **branche Foundry** (version-controlled avec branching Git-like — [CONFIRMED]).

#### Couche 2 : Ontologie squelette ("starter ontology")

- Construction d'un **"starter ontology"** / ontologie squelette avec un petit ensemble d'object types et link types requis pour le premier use case demo (GPT, Claude).
- Par le Jour 1, **un squelette de 5-10 object types avec proprietes et liens de base est typiquement en place** (Claude).
- L'ontologie est construite a partir des **6 primitives** Palantir [CONFIRMED] : Object Types, Properties, Link Types, Action Types, Interfaces, Functions.

#### Couche 3 : Environnement demo prepare

- L'environnement est provisionne et l'acces est pret pour **minimiser la friction au Jour 1** (GPT, Claude, Perplexity).
- Posture de permissions configuree.
- AIP tourne sur des **reseaux prives** avec des rails de gouvernance des donnees, pas des environnements partages (Perplexity).
- Infrastructure de securite construite sur AWS, Azure, Google Cloud avec securite et gouvernance integrees (GPT).

### Workstream 3 — Selection et priorisation des use cases

Le DS mene un processus structure pour passer d'une liste initiale de **5-10 use cases candidats** a **3-5 qui seront explores au Jour 1**, avec **1-2 finalement construits** pendant la semaine (Claude).

#### Framework de selection a 4 axes (Claude)

| Axe | Question cle |
|-----|-------------|
| **Business impact** | Revenu, economies, reduction de risque — quel est le gain mesurable ? |
| **Data feasibility** | Les donnees sont-elles disponibles et accessibles ? |
| **Demonstrability** | Peut-on le montrer fonctionnel en 5 jours ? |
| **Executive resonance** | Le C-suite sponsor sera-t-il enthousiaste ? |

#### Framework "top-five business outcome" (Perplexity)

Bob McGrew (ex-OpenAI CRO, ex-Palantir) : *"Pick a top-five business outcome for your customer and build backwards from it. You're shipping results, not 'an install'."*

#### Framework operationnel a 3 scores (GPT)

| Score | Critere |
|-------|---------|
| **Operational leverage** | Le workflow touche-t-il une decision executee dans un systeme d'action — ERP, dispatch, maintenance, operations cliniques ? |
| **Data tractability** | Les donnees sont-elles exploitables en 1-2 semaines ? |
| **Demoability** | Le resultat est-il demontrable dans Workshop et l'Ontology ? |

#### Use cases verticaux typiques

| Vertical | Use cases communs |
|----------|------------------|
| **Manufacturing** | Maintenance predictive, scheduling de production, gestion qualite/reclamations |
| **Supply chain** | Optimisation supply chain, reallocation de centres de distribution, gestion des stocks |
| **Sante** | Optimisation flux patients, placement patients, staffing infirmier |
| **Services financiers** | Detection de fraude, transformation underwriting |
| **Energie** | Scheduling dynamique, economies de procurement |
| **Logistique** | Routage de work orders, optimisation de la planification |
| **Service client** | Triage service client |
| **Infrastructure** | Gestion projets d'infrastructure |

### Workstream 4 — Legal, securite, et logistique

| Element | Detail | Duree typique |
|---------|--------|---------------|
| **Mutual NDA** | Signe avant tout partage de donnees | 1-2 semaines (Claude, Perplexity) |
| **Data Processing Agreement (DPA)** | Requis pour les industries reglementees. Templates standardises chez Palantir | Variable |
| **Terms of Service / License agreement** | Template standard "License and Services Agreement" (documente via GSA Schedule de Carahsoft) | Inclus dans le NDA timeline |
| **Security review** | Modele de securite incluant organisations, spaces, audit logs | Pre-configure |

L'infrastructure de securite comprend :
- Securite et gouvernance integrees (GPT).
- Constructs de gouvernance : organisations et spaces.
- Primitives d'audit : audit logs.
- Validation and oversight avec controles de securite full-spectrum, checkpoints de revue humaine integres, et guardrails comme concepts first-class (documentation UK — GPT).
- Modele de securite a 3 niveaux : Resource-Level Mandatory Markings, Ontology-Level ACL (per-object RLS, per-property column suppression), Execution-Context Controls for AI [CONFIRMED].

### Workstream 5 — Demos "Art of the Possible"

Avant la semaine du bootcamp, Palantir conduit souvent une **demonstration "Art of the Possible" de 60-90 minutes** pour le leadership du client (Claude).

#### Format

- C'est une **demo live et personnalisee** — pas un slide deck (Claude, Perplexity).
- Un FDE construit une version simplifiee utilisant les **propres donnees pre-ingerees du client** (ou des donnees representatives de l'industrie si les donnees client ne sont pas encore disponibles) (Claude, Perplexity).
- La demo tourne **live sur une instance Foundry** — c'est delibere, montrant la capacite reelle de la plateforme (Claude, Perplexity).

#### Contenu — deux types de demos combines (GPT)

1. **Platform primitives demo** : Pipeline Builder, Ontology Manager, Workshop, outils AIP builder — montrant les capacites brutes de la plateforme.
2. **Vertical storyboard demo** : Utilisant un narratif domaine specifique au secteur du client.

#### Demos verticales disponibles

Palantir maintient des **environnements de demo permanents** pour (Perplexity) :
- **Sante** : Placement patients, staffing infirmier.
- **Manufacturing** : Scheduling de production, maintenance predictive (avec donnees capteurs).
- **Supply chain** : Reallocation de centres de distribution.
- **Defense** : Scenarios operationnels.
- **Services financiers** : Workflows specifiques.

#### Objectif strategique

La session "Art of the Possible" sert de **declencheur emotionnel** qui securise l'engagement executif pour le bootcamp (Claude). C'est le moment ou le leadership voit ce qui est *possible* et s'engage a mobiliser les ressources pour la semaine de bootcamp.

---

## 1.5 Execution du Bootcamp — Jour par Jour

### Structure globale en 3 phases

| Phase | Focus | Timing |
|-------|-------|--------|
| Phase 1 | Introductions + Demos produit — *"art of the possible"* + Build AI Intuition | Jour 1 (matin/debut d'apres-midi) |
| Phase 2 | Hands on Keyboards — co-building sur donnees reelles | Jours 2-4 |
| Phase 3 | Showcase + Assessment — presentation executive, prochaines etapes | Jour 5 |

Trois resultats attendus documentes :
1. **Build your AI intuition** : Apercu interactif des LLMs et capacites GenAI en contexte entreprise.
2. **Hands on keyboard** : Demos, sessions hands-on intensives, discussions de groupe.
3. **Develop use cases & tactical implementation plan** : Configurer et deployer les use cases initiaux, preparer l'onboarding/formation des utilisateurs pour l'implementation MVP.

---

### JOUR 1 — Cadrage, confirmation de la realite des donnees, et accord sur le plan de construction

---

#### Matin (9:00 - 12:30)

##### Welcome et introductions (9:00 - 9:30)

Le DS dirige les introductions et pose les attentes pour la semaine (Perplexity). Cadrage des objectifs, presentation de l'equipe Palantir, tour de table cote client.

##### Atelier de cadrage de probleme — Problem Framing Workshop (9:30 - 11:30)

Le DS mene un **atelier structure** qui emprunte au design thinking et au process mapping. C'est un exercice facilite, **whiteboard-heavy**, ou les participants cartographient physiquement les workflows operationnels (Claude).

**Ce qui se passe concretement :**
- Le DS demande aux experts domaine du client de **parcourir leur processus actuel de bout en bout** pour chaque use case candidat : qui fait quoi, ou les donnees entrent, ou les decisions sont prises, ou les goulots d'etranglement et erreurs surviennent (Claude).
- Pour chaque workflow, l'equipe identifie :
  - Le **trigger** : Ce qui initie le workflow.
  - Les **decision points** : Ou un humain exerce un jugement.
  - Les **data inputs** : Quelles informations l'humain utilise pour decider.
  - La **pain** : Ce qui va mal, ce qui prend trop de temps, ce qui coute de l'argent (Claude).

**Probing pour les metriques quantifiables :**
Le DS sonde activement : *"How many work orders are misrouted per week? What's the cost of each misroute? How long does triage take? What would 50% faster look like in revenue terms?"* (Claude).

[CONTRADICTION sur le framework utilise] :
- **Claude** : Le plus proche de *"jobs to be done"* combine avec le process mapping.
- **Perplexity** : Ce n'est pas formellement du "design thinking" ou "JTBD" — c'est plus proche du **propre framework de Palantir** de cartographie des decisions, besoins d'information, et sources de donnees.

En pratique, c'est probablement un framework proprietaire qui emprunte a plusieurs methodologies sans etre formellement rattache a l'une d'entre elles.

##### Session "Developing Your AI Intuition" (11:30 - 12:30)

Session structuree hands-on menee par un ingenieur Palantir (Ankit Shankar en a mene beaucoup a AIPCon — Perplexity). L'objectif est de *"get customers hands-on with the product to understand the strengths and limitations of large language models and how AIP addresses those limitations"* (Perplexity).

**Sujets couverts :**
- Ce que les LLMs **peuvent** et **ne peuvent pas** faire (hallucinations, contraintes de context window).
- Comment **AIP Logic** fonctionne comme outil de builder pour amener un LLM du developpement a la production.
- **Prompt engineering**, testing/evaluation, monitoring, automation.
- Demonstrations de **strong typing**, **tool chaining**, et **raisonnement ontology-grounded**.

**Livrables intermediaires du matin :**
- Process flow diagrams des workflows actuels.
- Liste des pain points quantifies.
- Premiere comprehension des capacites/limitations AI par le client.

---

#### Apres-midi (13:30 - 17:30)

##### Demo "Art of the Possible" (13:30 - 14:30) — si pas faite en pre-bootcamp

Le FDE lance l'**instance Foundry live** et montre les donnees du client deja ingerees et partiellement modelisees (Claude).

C'est le **pivot emotionnel** du bootcamp — le moment ou le client voit ses spreadsheets desordonnees transformees en un systeme structure, interrogeable, navigable visuellement (Claude).

**Ce que la demo montre typiquement :**
1. Les **donnees brutes circulant** dans un pipeline.
2. Les memes donnees representees comme des **Ontology objects** avec des relations.
3. Une **application Workshop simple** permettant de parcourir, filtrer et agir sur les donnees (Claude, Perplexity).
4. Si AIP Logic a ete pre-configure : une **requete en langage naturel** contre les propres donnees du client — ex. *"Show me all overdue work orders for equipment in Building 7"* (Claude).

##### Data reality check et validation (14:30 - 16:00)

- **Valider** ce qui est reellement disponible dans les static cuts fournies (GPT).
- **Confirmer** les identifiants et cles de jointure necessaires pour l'Ontology (GPT).
- **Verrouiller** le "minimum viable ontology" pour le lead use case (GPT).
- FDEs et data engineers client examinent les donnees pre-ingerees **ensemble** (Claude).
- Identification des **gaps de donnees** : quels datasets existent, lesquels manquent, quelles transformations sont requises (GPT).

##### Selection finale des use cases (16:00 - 17:00)

Les use cases candidats sont evalues contre le framework a 4 axes, et l'equipe selectionne collectivement les use cases primaires a construire.

[CONTRADICTION sur le nombre de use cases selectionnes] :
- **GPT** : 3-5 target workflows selectionnes au Jour 1.
- **Claude** : 1-2 primary use cases selectionnes.
- **Perplexity** : Raffinement de 5 candidats a 2-3 primary builds.

En pratique, **1-2 use cases primaires** sont construits end-to-end, avec 1-3 additionnels explores a des niveaux de profondeur moindres.

##### Discussion commerciale et gouvernance (17:00 - 17:30)

L'AE confirme les limites d'evaluation et le pathway de procurement ; s'assure que le bon executive sponsor est programme pour le Jour 5 (GPT, Claude).

---

#### Livrables de fin de Jour 1

| Livrable | Detail | Sources |
|----------|--------|---------|
| **Use-case slate signee** | Avec proprietaires, criteres de succes, et script de demo pour le dernier jour | (GPT) |
| **Process flow diagrams** | Cartographie des workflows actuels | (Claude) |
| **Scope de use case finalise** | Criteres de succes agrees | Claude, Perplexity |
| **Data inventory et build backlog** | Quels datasets existent, lesquels manquent, quelles transformations requises | (GPT) |
| **Design "minimum viable ontology"** | Object types, link types, et proprietes cles candidats pour le lead use case | (GPT) |
| **Inventaire de donnees valide** | Design d'ontologie affine | (Claude) |
| **AI intuition acquise** | Le client comprend les capacites vs. limitations des LLMs | (Perplexity) |
| **Buy-in emotionnel** | Le client a vu ses propres donnees dans Foundry | (Perplexity) |

#### Interactions client — Jour 1

| Acteur | Role pendant le Jour 1 |
|--------|----------------------|
| **Business owners et operateurs client** | Valident les etapes de workflow et ce qui constitue une bonne decision. Contribuent activement pour **70%+ de la journee** (Claude). C'est by design : Palantir a besoin de leurs connaissances, et la participation cree un sentiment de **propriete psychologique**. |
| **IT et data owners client** | Confirment la signification des donnees et la logique de jointure (GPT, Perplexity). |

#### Activites par role — Jour 1

| Role Palantir | Activites |
|---------------|-----------|
| **DS** | Facilite l'atelier, force la priorisation, documente les criteres de succes, aligne les stakeholders, commence a construire le narratif executif (GPT, Claude, Perplexity). |
| **FDE team** | Valide l'approche d'atterrissage et transformation des donnees, draft les types d'ontologie, etablit le plan d'ingenierie pour la semaine. Gere la demo live et la revue technique des donnees (GPT, Claude). |
| **AE** | Confirme les limites d'evaluation et le pathway de procurement. S'assure que le bon executive sponsor est programme pour le Jour 5. Present pour le kickoff, observe, gere la dynamique relationnelle (GPT, Claude). |

#### Outils Foundry utilises — Jour 1

| Outil | Usage |
|-------|-------|
| **Pipeline Builder** | Inspecter les pipelines d'integration et les etapes de transformation. |
| **Ontology Manager** | Commencer a definir les object et link types et connecter les backing datasources. |
| **Workshop** | Esquisser la forme de l'app operationnelle cible. |
| **Code Workbooks** | Analyse exploratoire des donnees avec les ingenieurs client (Claude). |

#### Points de decision — Jour 1

1. Decision sur le **"lead use case"** qui doit etre demo-ready d'ici mi-semaine (GPT).
2. Decision sur le **perimetre de l'ontologie** : Quels objets et liens sont "must-have" vs. "nice-to-have" (GPT).
3. Quels stakeholders client seront les **"co-builders"** pour les Jours 2-3 (Perplexity).
4. Gaps de donnees identifies (datasets additionnels a demander) (Perplexity).

---

### JOUR 2 — Premiere tranche verticale fonctionnelle (le "walking skeleton")

---

#### Ce que signifie concretement le "co-building"

Le co-building est le **coeur de la methodologie Palantir** et le principal differenciateur par rapport au consulting traditionnel (Claude).

**En pratique :** Le FDE tient le clavier tandis que l'expert domaine du client est a cote, **dirigeant le contenu** (Claude, Perplexity). Les ingenieurs client ne sont generalement pas en train d'ecrire du code PySpark eux-memes — le FDE gere toute l'implementation technique (Claude, Perplexity).

**Mais :** Les data engineers client participent activement a la validation des donnees, pointant les problemes de qualite, expliquant la business logic (*"this status code means the order was cancelled"*), et revisant les outputs du pipeline (Claude). Les SMEs business participent en specifiant les exigences en temps reel : *"We need to see the priority level here," "This filter should include both pending and in-progress statuses," "The routing logic should account for technician certifications"* (Claude).

**Temoignage direct :** John Kottlowski (Palantir, bootcamp de Dallas) a decrit l'experience comme *"sitting shoulder-to-shoulder with our data/tech counterparts"* et creant *"immediate, accretive value... within 2 days"* (Perplexity).

**Cadence iterative :** Un cycle typique prend **30-90 minutes** : le FDE construit un composant, le client le revoit immediatement, fournit un feedback, et le FDE ajuste. Cette cadence cree un sentiment de **velocite et co-propriete** que le developpement traditionnel RFP-driven ne peut pas reproduire (Claude).

---

#### Matin (9:00 - 12:30)

##### Construction de la fondation data (9:00 - 10:30)

- Construction de la fondation pour le lead workflow : **clean datasets, identifiants stables, et mappings d'ontologie initiaux** (GPT).
- Les FDEs plongent dans la construction du **full data pipeline stack** :
  - **Pipeline Builder** pour les transformes simples (joins, filtres, aggregations).
  - **Code Repositories** pour la business logic complexe (code PySpark pour calculs custom, windowing functions, ou feature engineering ML) (Claude).

**Livrable intermediaire :** Pipeline branch fonctionnel produisant des clean datasets pour le lead use case.

##### Construction de l'ontologie (10:30 - 12:30)

- Simultanement, l'ontologie est construite dans **Ontology Manager** (Claude) :
  - Tous les **Object Types** sont crees avec des property mappings complets.
  - Les **primary keys** sont definies.
  - Les **Link Types** sont cables pour representer les relations identifiees lors du process mapping du Jour 1.
- Le processus de mapping est principalement fait via le **Ontology Manager UI** — l'interface visuelle — plutot qu'une approche code-first. C'est plus rapide et plus visuellement comprehensible pour les stakeholders client qui observent (Claude, Perplexity).

**Livrable intermediaire :** Ontologie peuplee avec 5-15 object types, backing datasources connectees.

---

#### Apres-midi (13:30 - 17:30)

##### Construction de la premiere application Workshop (13:30 - 16:30)

Avec l'ontologie en place, les FDEs commencent a construire la premiere **application Workshop** (Claude).

**Workshop** est le no-code application builder de Palantir et l'outil principal pour creer l'interface utilisateur du prototype (Claude, Perplexity).

**Ce que le FDE construit concretement :**
1. Cree des **modules** (pages).
2. Ajoute des **widgets** : object tables, detail panels, charts, maps, KPI tiles, filter panels.
3. Les cable ensemble via des **variables** qui passent l'etat entre composants (Claude).
4. Connecte au moins une **action ou fonction** qui rend l'app operationnelle, pas seulement analytique (GPT).

##### Revue et iteration (16:30 - 17:30)

- Les operateurs client s'assoient avec l'app et confirment si elle correspond a leur facon de penser le workflow (GPT, Claude).
- Premiers ajustements basees sur le feedback immediat.

---

#### Livrables de fin de Jour 2

| Livrable | Detail | Sources |
|----------|--------|---------|
| **Pipeline branch fonctionnel** | Clean datasets pour le lead use case | GPT, Claude |
| **Ontology objects visibles dans une application** | Object types avec backing datasources, au moins un link type | (GPT) |
| **Ontologie peuplee** | 5-15 object types, 5-20 link types | (Claude) |
| **App Workshop "walking skeleton"** | UI minimale qui charge des donnees reelles et supporte un parcours utilisateur core | GPT, Claude |

Le **"walking skeleton"** est une app Workshop fonctionnelle qui affiche des donnees reelles, permet le filtrage et la navigation basiques, et demontre le core operational workflow. **Ce n'est pas poli, mais ca fonctionne** (Claude, GPT).

#### Interactions client — Jour 2

| Acteur | Role |
|--------|------|
| **Operateurs client** | S'assoient avec l'app et confirment si elle correspond a leur facon de penser le workflow (GPT, Claude). |
| **Ingenieurs client** | Participent en pair avec les ingenieurs Palantir, mais le framing est *"build live alongside Palantir engineers"*, pas *"client writes all the code"* (GPT, Claude). |

#### Activites par role — Jour 2

| Role Palantir | Activites |
|---------------|-----------|
| **FDE team** | Implemente les transformations et le cablage ontologie ; construit le premier module d'app ; assure la lineage des donnees et la reproductibilite (GPT, Claude). |
| **DS** | Gere les boucles de feedback operateur ; documente les gaps ; ajuste le perimetre pour proteger l'histoire du Jour 5 (GPT, Claude). |
| **AE** | Commence a former le cadrage commercial autour d'un chemin clair *"prototype-to-production"* (GPT, Claude). |

#### Outils Foundry utilises — Jour 2

| Outil | Usage |
|-------|-------|
| **Pipeline Builder et/ou Code Repositories** | Transformes et iteration rapide. |
| **Ontology Manager** | Mapping des datasets en object types, creation de link types. |
| **Workshop** | Construction du prototype UI. |
| **Data Connection** | Ingestion des donnees (Claude). |
| **Code Workbooks** | Analyse exploratoire (Claude). |

#### Points de decision — Jour 2

1. Decision sur si le prototype doit etre **Workshop-first ou agent-first**. La plateforme supporte les deux : Workshop pour les apps operationnelles et AIP Agent Studio pour les assistants ancres dans l'ontologie et les outils (GPT).
2. Decision sur les **objets "source of truth"** qui ancreront tout le grounding AI (GPT).

---

### JOUR 3 — Extension aux use cases additionnels et introduction de la logique AIP workflow

---

#### Matin (9:00 - 12:30)

##### Extension de l'ontologie et des workflows (9:00 - 10:30)

- Etendre la couverture de l'ontologie et de l'app aux **1-2 prochains use cases** (GPT).
- Standardiser les definitions d'objets et patterns de liens pour que les ajouts ulterieurs soient **composables** (GPT).

##### Ajout des Ontology Actions (10:30 - 12:30)

Les FDEs ajoutent des **Ontology Actions** — operations write-back qui transforment l'app d'un dashboard passif en **outil operationnel** (Claude).

**Exemples d'actions configurees :**
- *"Approve Work Order"*
- *"Assign Technician"*
- *"Escalate Case"*
- *"Update Inventory Status"*

Ces actions sont configurees dans **Ontology Manager** avec parametres, regles de validation, et contraintes de permissions (Claude). Elles sont ensuite cablees a des **action buttons** dans l'application Workshop, donnant aux utilisateurs la capacite de prendre des decisions operationnelles reelles dans le prototype (Claude, Perplexity).

**Livrable intermediaire :** Application Workshop avec actions operationnelles fonctionnelles (pas seulement de la visualisation).

---

#### Apres-midi (13:30 - 17:30)

##### Integration AIP Logic (13:30 - 16:00)

C'est la partie la plus spectaculaire du bootcamp. Les FDEs configurent des **fonctions LLM-powered** qui operent sur l'ontologie (GPT, Claude, Perplexity).

**Ce que l'agent AI recoit :**
- Acces a des **object types et actions specifiques** (pas a toute l'ontologie — guardrail de securite).
- Un **system prompt** definissant son comportement et contraintes.
- Un ensemble de **fonctions disponibles** : ontology searches, property lookups, action triggers (Claude).

**AIP Logic** est explicitement concu pour construire, tester, evaluer, monitorer, et automatiser des fonctions LLM-powered (GPT, Perplexity). C'est un visual, no-code LLM workflow builder avec 5 types de blocks [CONFIRMED] : Use LLM, Apply Action, Execute Function, Conditional, Loop.

##### Mise en place d'AIP Assist (16:00 - 17:00)

**AIP Assist** — un widget d'interface chat — est embarque dans l'app Workshop, permettant aux utilisateurs de requeter leurs donnees en **langage naturel** et de declencher des actions par conversation (Claude).

**Exemples de requetes :**
- *"What are the top 5 overdue maintenance tasks?"*
- *"Assign the highest-priority work order to the nearest available technician"*

**Impact emotionnel :** C'est typiquement le moment qui genere la **reaction emotionnelle la plus forte** des stakeholders client (Claude). Le moment ou un VP Operations voit un agent AI repondre a des questions sur ses propres workflows en langage naturel, avec des donnees reelles, est transformateur.

##### Demonstration aux stakeholders elargis (17:00 - 17:30)

Les operateurs client commencent a interagir directement avec les prototypes (Perplexity). Les stakeholders non-techniques fournissent le contexte : *"this is how we actually make this decision"* vs. *"this is how the process is documented"* (Perplexity).

---

#### Livrables de fin de Jour 3

| Livrable | Detail | Sources |
|----------|--------|---------|
| **2-3 workflows end-to-end demoables** | Chaque workflow a data inputs, representation ontologie, et surface operateur | (GPT) |
| **Au moins une fonction ou agent LLM-backed** | Cable aux objects et actions ontologie reels | GPT, Claude |
| **Application Workshop entierement fonctionnelle** | Avec actions operationnelles | (Claude) |
| **Agents AIP Logic configures** | Repondant aux requetes en langage naturel | (Claude) |
| **Prototype demonstrable end-to-end** | Workflow operationnel fonctionnel | (Claude) |
| **Workflows AIP Logic initiaux** | Decision support LLM-augmente | (Perplexity) |

#### Interactions client — Jour 3

| Acteur | Role |
|--------|------|
| **Experts domaine client** | Fournissent des exemples de *"edge cases"* et modes de defaillance inacceptables, preparant le stress testing du Jour 4 (GPT). |
| **IT et securite client** | Examinent les boundaries de permissions pour tout acces AI (GPT). |
| **Stakeholders non-techniques** | Fournissent le contexte operationnel reel vs. documente (Perplexity). |

#### Activites par role — Jour 3

| Role Palantir | Activites |
|---------------|-----------|
| **FDE team** | Implemente les workflows LLM, outils, et integrations ; commence a ecrire les cas d'evaluation (GPT, Claude). |
| **DS** | Construit le narratif *"operateur + AI"*, s'assurant que le prototype resout une decision operationnelle reelle plutot qu'un chatbot de nouveaute (GPT, Claude). |
| **AE** | Aligne les stakeholders sur ce que *"production-grade"* signifie et quels artefacts de procurement sont necessaires (GPT). |

#### Outils Foundry utilises — Jour 3

| Outil | Usage |
|-------|-------|
| **AIP Logic** | Developpement de fonctions LLM, testing, evaluation, monitoring, setup d'automatisation (GPT, Claude, Perplexity). No-code LLM workflow builder. |
| **AIP Agent Studio** | Agents ancres dans l'ontologie, documents, et outils, deployables a l'interieur et en dehors de la plateforme (GPT). Architecture tool-use/function-calling [CONFIRMED]. |
| **Workshop** | Integration d'un AIP Agent dans une interface operateur via les widgets AIP Agent (GPT, Claude, Perplexity). |
| **AIP Assist** | Widget chat interface (Claude). |
| **AI FDE** | Agent AI-powered qui *"operates Foundry for you through conversational commands"* — traduit le langage naturel en operations Foundry (Perplexity). |

#### Points de decision — Jour 3

1. Decision sur les **guardrails et checkpoints human-in-the-loop** (GPT). Les 4 niveaux de guardrails AIP [CONFIRMED] : Constrained Action Types, Tool Scoping, Permission-Bounded, Staging Review.
2. Decision sur l'**approche d'evaluation** : A quoi ressemblent les *"bons"* outputs et comment les tester etant donne le non-determinisme des LLMs (GPT).

---

### JOUR 4 — Stress testing, harnais d'evaluation, et durcissement operationnel

---

#### Ce que "stress testing" signifie dans le contexte du bootcamp

**Ce n'est PAS** du load testing ou du performance benchmarking — c'est une **interrogation par les experts domaine** de la logique du prototype, de la gestion des donnees, et de la qualite des decisions (Claude, Perplexity).

Le format est une serie structuree de **walkthroughs de scenarios** avec les experts domaine les plus experimentes du client, essentiellement un **exercice de war-gaming live** ou les experts essaient de casser le systeme avec leurs scenarios reels les plus difficiles (Claude).

Pour les bootcamps defense/gouvernement, cela peut prendre la forme d'exercices bases sur des scenarios ou les operateurs traversent des situations realistes (Perplexity).

---

#### Matin (9:00 - 12:30)

##### Session de scenario testing structuree (9:00 - 11:30)

Facilitee par le DS. Les experts domaine presentent des **cas reels** rencontres (Claude) :

- *"What happens when a rush order comes in for a product we don't have in stock?"*
- *"How does the system handle a technician who is certified for Type A equipment but assigned to a Type B job?"*
- *"What if the sensor data shows a false positive on a maintenance alert?"*

Chaque scenario est **execute a travers le prototype en live** (Claude).

**Categories de edge cases :**
- **Exceptions de donnees** : Champs manquants, valeurs inhabituelles, informations contradictoires.
- **Exceptions de workflow** : Scenarios en dehors du processus standard.
- **Frontieres de jugement AI** : Cas ou le LLM fait des recommandations incorrectes ou ambigues (Claude).

**Triage des defaillances :**
Chaque defaillance est loguee et categorisee :
- **Critical** : Must fix avant Jour 5.
- **Important** : Should fix si le temps le permet.
- **Noted** : Amelioration pour la production (Claude).

##### Corrections immediates (11:30 - 12:30)

Les FDEs commencent immediatement a corriger les problemes critiques — affinement de la logique de pipeline, ajustement des regles d'action ontologie, ou tuning des prompts AIP Logic et definitions de fonctions (Claude).

##### Review par domain experts elargis

L'equipe FDE fait la demo des prototypes a des **stakeholders plus larges** — y compris des experts domaine qui n'etaient pas dans les sessions de co-building (Perplexity).

**Livrable intermediaire :** "Failure mode register" initial, problemes critiques identifies.

---

#### Apres-midi (13:30 - 17:30)

##### Continuation des corrections (13:30 - 15:00)

Les FDEs continuent d'iterer sur les corrections (Claude).

##### Instrumentation et evaluation (15:00 - 16:30)

- Utilisation d'**AIP Evals** pour creer des test cases et evaluateurs (GPT).
- Utilisation d'**AIP Observability** pour inspecter l'historique des runs, traces, et logs (GPT).
- AIP Evals est concu pour evaluer les Logic functions et agent functions et pour **gerer le non-determinisme** (GPT).

##### Preparation du narratif executive (16:30 - 17:30)

Le DS commence a preparer le **narratif de demo executive** pour le Jour 5 (Claude) :
- Quel probleme avons-nous commence a traiter ?
- Qu'avons-nous decouvert ?
- Qu'avons-nous construit ?
- Que fait-il ?
- Quel est l'**impact business mesurable** ?

Le DS travaille avec le **project lead du client** pour s'assurer que la demo resonera avec les priorites de l'executive sponsor (Claude).

L'application Workshop est **polie** — styling nettoye, navigation affinee, KPI tiles ajoutees pour montrer les metriques qui importent aux executives, et le flux de demo est repete (Claude).

**Livrable intermediaire :** Draft du narratif de presentation, app Workshop polie.

---

#### Livrables de fin de Jour 4

| Livrable | Detail | Sources |
|----------|--------|---------|
| **Suite d'evaluation** | Test cases et evaluateurs pour les comportements AI cles | (GPT) |
| **"Failure mode register"** | Quels scenarios cassent, quelles mitigations existent, quoi reste hors perimetre | (GPT) |
| **Vue d'observabilite** | Traces et logs accessibles via AIP Observability | (GPT) |
| **Prototype bug-fixed et durci** | Corrections des problemes critiques | (Claude) |
| **Document de resultats de scenario test** | Documentation structuree des tests | (Claude) |
| **Draft du narratif de demo executive** | Pret pour finalisation le Jour 5 | (Claude) |
| **Application Workshop polie** | UI nettoyee, KPI tiles ajoutees | (Claude) |
| **Prototypes valides** | Edge cases traites, limitations documentees, prompts affines, feedback incorpore | (Perplexity) |

#### Interactions client — Jour 4

Le Jour 4 est le **jour le plus collaboratif** (Claude).

| Acteur | Role |
|--------|------|
| **Experts domaine** | Passent **3-4 heures** a activement essayer de casser le systeme (Claude). Agissent comme injecteurs de scenarios et juges (GPT, Claude). |
| **Operateurs et SMEs** | Confirment si les outputs peuvent etre fiables en contexte (GPT). |
| **Stakeholders securite et gouvernance** | Valident l'auditabilite et les limites d'acces aux logs (GPT). |
| **Project lead client** | Travaille avec le DS sur le narratif de presentation executive (Claude). |

#### Activites par role — Jour 4

| Role Palantir | Activites |
|---------------|-----------|
| **FDE team** | Tune l'evaluation et l'observabilite ; corrige les joints fragiles et mismatches d'ontologie ; durcit la performance de l'app (GPT, Claude). |
| **DS** | Transforme les resultats du stress test en une histoire claire : ou l'AI est fiable, ou la revue humaine est requise, et comment cela devient un workflow gouverne (GPT, Claude). |
| **AE** | S'aligne sur le packaging commercial de prochaine phase autour d'un plan de deploiement realiste, pas juste une demo (GPT, Claude). |

#### Outils Foundry utilises — Jour 4

| Outil | Usage |
|-------|-------|
| **AIP Evals** | Test cases, evaluateurs, analyse de runs (GPT). |
| **AIP Observability** | Historique des runs, inspection des traces, logging (GPT). |
| **Workshop** | Scenario testing user-facing, polissage UI (GPT, Claude). |
| **Tous les outils simultanement** | Debugging et durcissement transversaux (Claude). |

#### Points de decision — Jour 4

1. Decision sur ce qui est **safe a automatiser maintenant** vs. ce qui requiert une approbation humaine (GPT).
2. Decision sur le **modele de permissions de production minimum** : Quels utilisateurs, roles, et spaces accederont a quels objets et actions (GPT).

---

### JOUR 5 — Readout executif, narratif ROI, et roadmap de deploiement

---

#### Matin (9:00 - 12:00)

##### Derniere repetition de demo et packaging (9:00 - 11:00)

- Les FDEs font les **ajustements finaux** au prototype (Claude).
- Derniere repetition de la demo, verification du flux narratif (GPT, Claude).
- Le DS finalise le narratif ; le FDE verifie la stabilite technique de la demo.

##### Preparation des materials de support (11:00 - 12:00)

Preparation des slides de support (le minimum — la demo est live, pas un slideshow).

---

#### Presentation executive (typiquement 13:30 - 15:30)

L'executive sponsor et son leadership team (typiquement **5-10 senior stakeholders**) assistent a la demo live (Claude). La presentation dure **45-60 minutes** incluant Q&A (Claude).

##### Structure de la presentation

Ce n'est pas un slide deck traditionnel — c'est une **demo live avec cadrage narratif** (Claude, Perplexity) :

| # | Section | Duree | Contenu |
|---|---------|-------|---------|
| 1 | **Problem statement** | 2-3 slides | Le defi operationnel, points de douleur du workflow actuel, et cout quantifie du statu quo — tire directement du process mapping du Jour 1 (Claude). |
| 2 | **What we built** | 15-20 min (demo live) | Le DS narre pendant que le FDE conduit un walkthrough live de l'application Workshop : donnees reelles circulant dans des workflows reels, actions prises, agents AIP repondant en langage naturel (Claude). |
| 3 | **Business impact projection** | 2-3 slides | ROI quantifie (Claude). |
| 4 | **Deployment roadmap** | 1-2 slides | Plan phase : prototype vers production (Claude). |
| 5 | **Architecture technique** | Variable | Comment l'ontologie, les pipelines, et AIP Logic travaillent ensemble (Perplexity). |

[CONTRADICTION sur qui presente] :
- **Perplexity** : C'est le **client** qui presente, pas Palantir — *"the client presents, not Palantir. This creates internal advocates and ownership."*
- **Claude** : *"the DS narrates while the FDE drives."*
- **GPT** : Le DS mene le narratif et le FDE execute la demo live.

Il est probable que le format varie : dans certains cas, le client co-presente (format optimal pour creer des champions internes), dans d'autres Palantir mene la presentation. Le format cross-client showcase (bootcamps multi-organisations) peut favoriser la presentation par le client.

##### Dynamique dans la salle

Les participants qui ont **co-construit le prototype** deviennent souvent les **defenseurs les plus puissants** dans la salle — ils parlent de l'experience d'avoir vu leurs propres workflows transformes en temps reel (Claude).

Palantir organise parfois des **bootcamps multi-organisations** ou les clients peuvent *"share learnings with your team and other clients"* (Perplexity).

##### Quantification du ROI

**Framework de calcul** (Claude) :
- Economies de temps x cout de main-d'oeuvre.
- Reduction des erreurs x cout par erreur.
- Amelioration du throughput x revenu par unite.

Les chiffres specifiques viennent des metriques identifiees pendant le problem framing du Jour 1 et validees pendant les Jours 2-4.

**Exemple concret** (Claude) : *"If the current triage process takes 45 minutes per work order and the prototype reduces that to 8 minutes, across 200 work orders per week, that's 123 hours saved per week at an average labor cost of $85/hour — roughly $540,000 annually from this single use case."*

**Frameworks ROI utilises** (Perplexity) :
| Framework | Metriques |
|-----------|-----------|
| **Time savings** | Heures/FTEs economisees par l'automatisation |
| **Operational efficiency** | Amelioration du throughput, reduction des erreurs, cycles de decision plus rapides |
| **Revenue impact** | Meilleur scheduling, optimisation des prix, retention client |
| **Cost avoidance** | Couts de stockage reduits, disruptions supply chain evitees |

Le ROI est **co-developpe avec le client** pendant le bootcamp, pas impose par Palantir — cela assure la credibilite et le buy-in interne (Perplexity).

**Exemples quantifies de clients :**
- *"10% increase in external transfer volume"* (Perplexity)
- *"2x increase in Hospital at Home volume from the ED"* (Perplexity)
- *"90% reduction in time to generate staff schedules"* (Perplexity)
- *"achieved more in one day with AIP than a top-three hyperscaler accomplished over four months"* (Perplexity)

##### Roadmap de deploiement

[CONTRADICTION sur les timelines de roadmap] :

**Version Claude :**

| Phase | Timeline | Contenu |
|-------|----------|---------|
| Phase 1 | Semaines 1-8 | Durcissement production du prototype bootcamp, revue securite et conformite, integration avec les sources de donnees de production |
| Phase 2 | Semaines 8-16 | Formation utilisateurs, rollout utilisateurs elargi, integration de sources de donnees additionnelles |
| Phase 3 | Mois 4-12 | Use cases additionnels, scaling a d'autres business units ou geographies |

**Version Perplexity :**

| Etape | Timeline | Contenu |
|-------|----------|---------|
| Result 1 | >1 jour | AIP Demo & Deep Dive — Construire l'intuition AI/LLM |
| Result 2 | 1-5 jours | AIP Bootcamp — MVP sur vos donnees, construit par vos equipes |
| Result 3 | 3 mois | ROI Realization — ROI tangible contre utilisateurs/use cases cibles |
| Result 4 | 3-6 mois | Scaling Phase — ROI non-lineaire avec expansion du perimetre |
| Result 5 | 6-9 mois | AI-Powered Foundation — Resultats business transformationnels |

---

#### Discussion commerciale (15:30 - 17:00)

L'AE re-entre dans la conversation pour discuter des prochaines etapes (Claude, Perplexity).

**Ce n'est PAS un hard close** — c'est un **roadmap alignment discussion** (Claude).

**Sujets couverts :**
- Perimetre d'un engagement de production initial.
- Modele de pricing subscription de Palantir.
- Timeline pour le deploiement production.
- Besoins en ressources des deux cotes (Claude, Perplexity).
- Pilot scope et timeline (typiquement 6-8 semaines vers application de production) (Perplexity).
- Structure contractuelle, path d'expansion et vision de partenariat long-terme (Perplexity).

Les **details de pricing** ne sont typiquement pas finalises pendant le bootcamp ; l'AE propose une reunion de suivi pour presenter une proposition commerciale formelle dans les **1-2 semaines** (Claude).

---

#### Livrables de fin de Jour 5

| Livrable | Detail | Sources |
|----------|--------|---------|
| **Prototype MVP fonctionnel** | MVP et preparation a l'onboarding/formation pour implementation | GPT, Claude, Perplexity |
| **Plan d'implementation tactique** | Roadmap detaillee | GPT, Claude, Perplexity |
| **Narratif de pathway vers la production** | Chemin credible prototype-to-production | (GPT) |
| **Presentation demo executive** | Demo live + slides de support | (Claude) |
| **Document de projection business impact/ROI** | Business case quantifie | Claude, Perplexity |
| **Roadmap de deploiement** | Plan phase | Claude, Perplexity |
| **Engagement verbal ou ecrit** | Pour des discussions de prochaine etape | (Claude) |

#### Activites par role — Jour 5

| Role Palantir | Activites |
|---------------|-----------|
| **DS** | Mene le narratif : Probleme, douleur baseline, transformation du workflow, impact operateur, et prochaine phase. (GPT, Claude) |
| **FDE team** | Gere la demo live ; repond aux questions techniques ; montre les preuves d'observabilite et d'evaluation (GPT, Claude). |
| **AE** | Convertit le plan en termes commerciaux et prochaines etapes ; aligne le timeline a la realite de procurement (GPT, Claude). |

---

### Vue consolidee — Stack technique en sequence

Pour un FDE abordant un bootcamp, la sequence d'outils suit un pattern previsible (Claude) :

| Periode | Outils | Activite |
|---------|--------|----------|
| Semaines -2 a -1 | Data Connection, Pipeline Builder, Code Repositories, Ontology Manager (initial) | Ingerer les donnees brutes, nettoyer/transformer, definir le squelette d'object types |
| Jour 1 | Code Workbooks, Ontology Manager | Analyse exploratoire, affiner l'ontologie d'apres le process mapping |
| Jour 2 | Pipeline Builder, Code Repositories, Ontology Manager, Workshop | Couche de transformation complete, object types complets, link types, proprietes, debut UI |
| Jour 3 | Workshop, AIP Logic, AIP Assist, AIP Agent Studio | Construire l'app UI, configurer les agents LLM avec acces aux fonctions ontologie |
| Jour 4 | Tous les outils + AIP Evals, AIP Observability | Debugging, durcissement, polissage, evaluation |
| Jour 5 | Workshop (demo), slides de support | Demo live et presentation executive |

**Ce que l'ontologie contient a la fin de la semaine** (Claude) :
- **5-15 Object Types**
- **5-20 Link Types**
- **3-10 Actions configurees**
- **5-20 pipelines de transformation de donnees** alimentant les backing datasets
- **Plusieurs modules Workshop** (pages/onglets) avec widgets interactifs
- **1-2 agents AIP Logic** capables de requetes en langage naturel et d'execution d'actions

---

## 1.6 Post-Bootcamp

### Package delivre dans les 48 heures

Les trois sources mentionnent un package post-bootcamp, avec des degres de certitude differents :
- **GPT** : Aucun "48-hour packet" standard publie dans les sources publiques, mais infere les artefacts typiques.
- **Claude et Perplexity** : Package formel delivre dans les 2 jours ouvrables.

#### Contenu du package

| Document | Detail | Sources |
|----------|--------|---------|
| **Executive summary** (2-4 pages) | Enonce du probleme, ce qui a ete construit, constats cles, prochaines etapes recommandees — ecrit pour le public C-suite | Claude, Perplexity |
| **Evaluation technique** | Diagramme d'architecture (sources -> pipelines -> ontologie -> applications), documentation du schema d'ontologie, analyse des gaps pour la production | Claude, Perplexity |
| **Projection ROI** | Business case detaille avec scenarios conservateur, modere, et agressif (Claude). Projection de valeur sur 6-12 mois (Perplexity). | Claude, Perplexity |
| **Roadmap de deploiement propose** | Plan phase du Jour 5 avec plus de detail sur timelines, besoins en ressources, et dependances | Claude, Perplexity |
| **Appendice evaluation et observabilite** | Test cases, modes de defaillance, preuves de traces, decisions de gouvernance requises (pour les workflows AI) | (GPT) |

### Duree de vie du sandbox/prototype

[CONTRADICTION sur la duree d'acces] :
- **Claude** : **30-90 jours** d'acces au prototype.
- **Perplexity** : Pas de duree specifique, mais confirme que les prototypes restent accessibles.
- **GPT** : Les SEC filings decrivent des deploiements pilotes court terme, impliquant qu'ils sont time-bounded.

La longevite du prototype est generalement gouvernee par (GPT) :
1. Les termes de l'environnement bootcamp (incluant les ToS).
2. Si l'organisation entre dans une phase contractuelle.
3. Les exigences de retention de donnees.

Le sandbox qui reste accessible sert de **rappel persistant** de ce qui a ete construit (Claude, Perplexity).

Le timeline median **POC-to-production** de Palantir est de **6-8 semaines**, pendant lequel le sandbox evolue de demo vers une application de production (Perplexity).

### Cadence de suivi

| Quoi | Quand | Qui | Sources |
|------|-------|-----|---------|
| **Appels hebdomadaires** | Semaines 1-6 post-bootcamp | DS avec le project lead client | Claude, Perplexity |
| **Presentation de proposition commerciale** | Dans les 2 semaines | AE | (Claude) |
| **Support onsite FDE** | Selon les besoins | FDEs (voyage 25-75%) | (Perplexity) |
| **Retour des participants** | ~2 semaines apres | Participants au bootcamp | (Perplexity) |

Ted Mabrey a indique que les participants au bootcamp reviennent avec *"4-5 use cases 2 weeks later... and a real live initial implementation of a use case and a plan to take that MVP into production"* (Perplexity).

#### Cadence detaillee inferee (GPT)

| Semaine | Activites |
|---------|-----------|
| **Semaine 1** | Confirmer les *"production candidate"* use cases ; verrouiller l'approche d'acces aux donnees (passer des static cuts vers des connexions repeatables) ; formaliser gouvernance et securite. |
| **Semaines 2-4** | Transformer les pipelines bootcamp en pipelines stables et rafraichissables ; durcir l'ontologie ; etendre la formation utilisateurs ; iterer avec les operateurs en boucles serrees. |
| **Semaines 5-6** | Deployer aux vrais utilisateurs ; etablir les voies de monitoring et d'incident ; etendre les suites d'evaluation ; progresser vers un modele operationnel repeatable. |

### Format de la proposition commerciale (MSA/SOW)

L'AE propose typiquement un **Proof of Value (PoV) engagement** comme prochaine etape — un engagement paye de **8-12 semaines** pour amener le prototype a la qualite production (Claude).

#### Structure contractuelle

| Element | Detail | Sources |
|---------|--------|---------|
| **Master Services Agreement (MSA)** | Licensing de la plateforme et termes | Claude, Perplexity |
| **Statement of Work (SOW)** | Perimetre, timeline, livrables, et pricing specifiques | Claude, Perplexity |
| **Template standard** | *"License and Services Agreement"* documente via GSA Schedule de Carahsoft | (Perplexity) |

**Point critique :** Pas de contrat de services traditionnel. Le deploiement FDE est **inclus dans la licence logicielle** — pas de frais d'implementation/consulting separe. C'est une strategie deliberee pour maintenir un alignement *"skin-in-the-game"* (Perplexity).

#### Modele de pricing

**Subscription-based** (Claude, Perplexity).

[CONTRADICTION sur les tailles de deals initiaux] :
- **Claude** : Deals initiaux "land" typiquement de **100K$-500K$ annuels** pour un PoV/pilote, s'etendant a **1M$-10M$+** pour les deploiements production complets.
- **Perplexity** : Prix de **~1M$+ pour le mid-market commercial a 10M$+ pour les grandes entreprises et le gouvernement**, et contrats sous 200K$ non rentables pour le modele FDE.
- **Playbook consolide** : Initial ACV from conversions **$200K-$500K** (median $250K-$350K) — premier contrat, pas valeur d'expansion [ESTIMATED].

Facteurs de pricing (Claude) :
- Nombre d'utilisateurs.
- Volume de donnees.
- Nombre de use cases deployes.
- Si le deploiement tourne sur le cloud Palantir ou l'infrastructure du client.

Alex Karp (Q3 2024 earnings call) : *"We have no pricing strategy for AIP."* — L'objectif est le land grab et la part de marche, pas l'optimisation des revenus. AIP est le produit d'entree ; les licences plateforme Foundry/Gotham sont le vehicule de monetisation [CONFIRMED].

### Gestion des 78% qui ne convertissent pas

#### Breakdown des raisons de non-conversion [SPECULATIVE]

| Raison | % des non-conversions | Description |
|--------|----------------------|-------------|
| **Data readiness failures** | ~25-30% | Donnees trop desordonnees pour etre integrees dans le timeframe du bootcamp |
| **Budget / procurement blockers** | ~20-25% | Valeur prouvee mais budget non approuve |
| **Internal politics** | ~15-20% | Champion parti, reorganisation, projet interne concurrent |
| **Use case mismatch** | ~10-15% | ROI insuffisant pour justifier le prix Palantir |
| **Competitive displacement** | ~5-10% | Client a choisi Databricks, Microsoft, ou un build interne |
| **Timing** | ~10-15% | *"Not now, maybe next year"* |

#### Approche par raison de blocage (Claude)

| Blocage | Strategie de re-engagement |
|---------|---------------------------|
| **Budget timing** | L'AE maintient des touchpoints trimestriels et propose de revisiter quand les cycles budgetaires s'alignent. |
| **Politique interne** | Le DS et l'AE identifient des champions alternatifs et peuvent proposer un **second bootcamp** pour une equipe differente. |
| **Technique** | Palantir peut offrir des **engagements plus legers** pour aider a resoudre les prerequis techniques avant de proposer un autre bootcamp. |

#### Pattern de re-engagement

- **Preserver les apprentissages** : Data mappings, ontology stubs, et le *"use-case slate"* deviennent des notes internes pour une re-entree future (GPT).
- **Re-engager quand les contraintes sont levees** (GPT).
- **Offrir un bootcamp plus etroit** : La documentation UK note que les bootcamps peuvent etre d'un ou plusieurs jours — Palantir peut reduire le perimetre pour re-tester avec un engagement moindre (GPT).
- **Cycle de re-engagement typique** : **3-6 mois**, souvent time autour de releases produit majeures, evenements AIPCon, ou conferences industrielles (Claude).
- Le **sandbox restant accessible** sert de rappel persistant (Claude).
- Le bootcamp genere des **ambassadeurs de marque** independamment de la conversion — les alumni deviennent des *"unofficial salespeople"* (Perplexity).

---

## 1.7 Metriques de Conversion

### Taux de conversion

[CONTRADICTION MAJEURE] — Les sources divergent significativement :

| Source | Taux de conversion | Detail |
|--------|--------------------|--------|
| **Claude** (Phase 2) | 30-50% | *"des bootcamps menent a une forme d'engagement paye"* (PoV, pilote, ou contrat) |
| **Perplexity** | ~70% | *"convertissent en contrats payes dans un trimestre"*, deal moyen >1M$ |
| **GPT** | Non specifie | Palantir ne publie pas les taux ; SEC filings confirment que la conversion n'est pas garantie |
| **Playbook consolide (Phase 4)** | **~22%** | Estimation d'analystes (Morgan Stanley, Wedbush Securities, RBC Capital Markets) [ESTIMATED] |

Le chiffre de **~22%** est la correction officielle du corpus de recherche (Correction #5 du playbook consolide), base sur le consensus des analystes financiers. Les chiffres de 30-50% et 70% sont vraisemblablement des estimations anterieures ou basees sur des definitions differentes de "conversion".

#### Timeline de conversion [SPECULATIVE]

| Delai apres bootcamp | Taux de conversion cumule |
|---------------------|--------------------------|
| Dans les 90 jours | ~10-15% |
| Dans les 6 mois | ~18-22% |
| Dans les 12 mois | ~25-30% |

### Deal size initial moyen

| Source | Deal size initial |
|--------|------------------|
| **Playbook consolide** | $200K-$500K (median $250K-$350K) — premier contrat | [ESTIMATED] |
| **Claude** | $100K-$500K annuels pour un PoV/pilote |
| **Perplexity** | ~1M$+ pour le mid-market |
| **S-1 filing** | $100K-$500K initial ACV | [CONFIRMED] |

Le multiple d'expansion moyen est spectaculaire : un contrat initial de **$100K grandit a $5.6M** en ACV mature — soit un **expansion de 56x** [CONFIRMED from investor presentations].

### CAC estime par bootcamp

| Metrique | Valeur | Confiance |
|----------|--------|-----------|
| **Cout par bootcamp pour Palantir** | $12K-$36K (cout de personnel charge : 1-5 jours x 5-8 personnes) | SPECULATIVE |
| **CAC par client converti (a 22% de conversion)** | ~$110K-$165K | SPECULATIVE |
| **CAC par client converti (a 40% de conversion)** | ~$45K-$75K | SPECULATIVE (estimation originale) |

> **Impact de la correction :** A 22% de conversion, pres de **4 bootcamps sur 5 ne convertissent pas**, rendant le cout d'acquisition de chaque client gagne significativement plus eleve que les estimations initiales.

### Compression du cycle de vente

| Ere | Cycle de vente moyen | Confiance |
|-----|---------------------|-----------|
| **Pre-Bootcamp (ere S-1)** | **9+ mois** | CONFIRMED |
| **Post-Bootcamp** | **~6 semaines** du bootcamp au contrat signe | CONFIRMED — Ryan Taylor, CRO |

C'est une compression de **~6x** du cycle de vente enterprise.

Ryan Taylor a confirme : la methode delivre des workflows reels sur des donnees clients en 5 jours ou moins vs. les pilotes traditionnels de 1-3 mois (Perplexity).

Karp a defie les clients de comparer leurs efforts AI internes contre 10 heures sur la plateforme Palantir (Perplexity).

### Metriques de croissance commerciale liees aux bootcamps

| Metrique | Valeur | Source |
|----------|--------|--------|
| **US commercial revenue growth** | De 23% YoY (Q3 2023, lancement des bootcamps) a **137% YoY** (FY2025) | [CONFIRMED] |
| **US commercial customer count growth** | 83% YoY en Q2 2024 | (Claude) |
| **Total customers** | De 260 (debut 2023) a **954** (Q4 2025) — **3.7x en <3 ans** | [CONFIRMED] |
| **Net dollar retention** | 107% (Q3 2023) -> **139%** (Q4 2025) | [CONFIRMED] |
| **Deals >1M$** | 204 en Q3 2025, dont 45% de nouveaux clients — beaucoup sourced des bootcamps | (Perplexity) |
| **Deals >10M$** | 61 en Q4 2025 seul | [CONFIRMED] |
| **Q4 2025 TCV** | $4.3B (+138% YoY) | [CONFIRMED] |
| **FY2025 total revenue** | $4.475B (+56% YoY) | [CONFIRMED] |
| **Revenue per employee** | **$1.01M** | [CONFIRMED] |

### Cas clients avec metriques specifiques

| Client | Metrique post-bootcamp | Source |
|--------|----------------------|--------|
| **Nebraska Medicine** | Bootcamp en janvier 2024. Production en 6 semaines. Discharge Lounge utilization +2,000%. 1,200+ AI-drafted insurance appeal letters. 10+ applications operationnelles (Year 1). Contrat multi-annees, multi-millions. | [CONFIRMED] — AIPCon 2024 |
| **Fortune 100 CPG** | 7 ERPs unifies en digital twin pendant un bootcamp de 5 jours. Impact projete : $100M en economies operationnelles Year 1. | [CONFIRMED] |
| **Tampa General Hospital** | *"the fabric of our health system operating system"* — CEO | [CONFIRMED] |
| **Land O'Frost** | Production planning reduit de **40 heures a 30 minutes** (reduction de 98.75%). | [CONFIRMED] — AIPCon |
| **Unnamed Utility** | ACV de $7M a $31M en un an (+343%). | [CONFIRMED] — Q4 2025 earnings |
| **Unnamed Healthcare System** | 2 bootcamps -> $96M TCV. | [CONFIRMED] — Q4 2025 earnings |
| **Panasonic Energy** | Gigafactory waste reduction. Semantic search sur 100,000+ repair tickets. | [CONFIRMED] |
| **Komatsu** | Atticus Clark (Mining Program Manager) : l'AI aide a prioriser les taches par urgence — *"game changer"*. | (Perplexity) |

---

## 1.8 Contradictions sur le Bootcamp

### Inventaire complet des contradictions identifiees

| # | Sujet | Source A | Source B | Severite |
|---|-------|----------|----------|----------|
| 1 | **Taux de conversion** | Claude : 30-50% / Perplexity : ~70% | Playbook consolide : **~22%** (analystes Morgan Stanley, Wedbush, RBC) | **CRITIQUE** — Ecart de 1 a 3x. Le chiffre de 22% est la correction officielle basee sur le consensus d'analystes financiers. |
| 2 | **Nombre de participants cote client** | Claude : 8-12 participants | Perplexity : 5-20 stakeholders | Modere — Probablement 8-12 typique dans un range de 5-20. |
| 3 | **Nombre de FDEs** | GPT : 1-3 / Claude : 1-2, equipe totale 2-5 / Perplexity : 1-2 | Playbook consolide : 2-4 FDEs | Modere — Depend de la taille et complexite du bootcamp. |
| 4 | **Nombre de use cases selectionnes au Jour 1** | GPT : 3-5 target workflows | Claude : 1-2 primary use cases / Perplexity : 2-3 primary builds | Faible — Difference entre "explores" et "construits". 1-2 construits end-to-end, 3-5 explores. |
| 5 | **Framework de problem framing** | Claude : Proche du "JTBD" + design thinking | Perplexity : Propre framework Palantir, PAS du JTBD/design thinking | Faible — Probablement un framework proprietaire empruntant a plusieurs methodologies. |
| 6 | **Qui presente au Jour 5** | Claude : Le DS narre, le FDE conduit / GPT : DS mene | Perplexity : Le **client** presente, pas Palantir | Modere — Format probablement variable. Presentation par le client = format optimal pour creer des champions. |
| 7 | **Duree d'acces au sandbox post-bootcamp** | Claude : 30-90 jours | Perplexity : Non specifie / GPT : Time-bounded (SEC filings) | Modere — Probablement variable selon les termes contractuels. |
| 8 | **Deal size initial** | Claude : $100K-$500K / Playbook : $200K-$500K median | Perplexity : ~1M$+ mid-market | Modere — Difference entre "premier contrat" et "taille economiquement viable". |
| 9 | **Roadmap de deploiement post-bootcamp** | Claude : 3 phases sur 12 mois (semaines 1-8, 8-16, mois 4-12) | Perplexity : 5 etapes sur 9 mois (demo, bootcamp, ROI 3 mois, scaling 3-6 mois, foundation 6-9 mois) | Faible — Formats de presentation differents du meme processus. |
| 10 | **Net dollar retention** | Claude : 115-120% (sans date) | Perplexity : 134% US commercial | Faible — Dates differentes. NDR a progresse de 107% (Q3 2023) a 139% (Q4 2025) [CONFIRMED]. Les deux chiffres sont corrects a des moments differents. |
| 11 | **Volume de bootcamps fin 2024** | Claude : 1,400+ fin Q3 2024 | Perplexity : 1,300+ fin Q4 2024 | Faible — Probablement une confusion de dates entre les sources. |
| 12 | **Taille du package 48h** | GPT : Pas de "48-hour packet" standard publie | Claude/Perplexity : Package formel delivre dans les 2 jours ouvrables | Modere — GPT est plus conservateur car base sur les sources publiques uniquement. |

### Analyse des contradictions

La contradiction **la plus critique** est celle du taux de conversion (Contradiction #1). L'ecart entre 22% (analystes) et 70% (Perplexity) est enorme et a des implications majeures :

| Metrique | A 22% de conversion | A 70% de conversion |
|----------|---------------------|---------------------|
| CAC par client converti | ~$110K-$165K | ~$25K-$50K |
| Bootcamps "perdus" | 78% | 30% |
| Justification economique | Viable uniquement si le multiple d'expansion (56x) compense | Tres attractive |

L'explication la plus probable : Perplexity cite peut-etre un taux de conversion incluant des engagements non-payes (evaluations prolongees, second bootcamps) ou un sous-ensemble de bootcamps particulierement qualifies. Le chiffre de 22% est le consensus des analystes financiers bases sur les donnees publiques (revenue, customer count, bootcamp volume) et represente l'estimation la plus rigoureuse.

---

## Annexe — Brevets pertinents (Perplexity)

Palantir detient des brevets lies a l'infrastructure technique qui alimente les bootcamps :

| Brevet | Description |
|--------|-------------|
| **US12260192B2 / US11086602B2** | *"Workflow application and user interface builder integrating objects, relationships, and actions"* — decrit le builder Workshop. |
| **US11461355B1** | *"Ontological mapping of data"* — le processus central de mapping donnees -> ontologie execute pendant la preparation du bootcamp. |
| **US9946777B1** | *"Systems and methods for facilitating data transformation"* — la fonctionnalite Pipeline Builder. |
| **US10861203B1** | *"Ontology-backed automatic chart creation"* — outils de visualisation utilises pendant les demos. |
| **US20200201855A1** | *"System to generate curated ontologies"* — curation d'ontologie a la volee. |

---

## Annexe — Pourquoi ce playbook est difficile a reproduire

Le playbook fonctionne grace a trois avantages se renforcant mutuellement (Claude) :

1. **La couche ontologie de la plateforme** fournit une abstraction semantique qui rend possible la modelisation de n'importe quel domaine operationnel en jours plutot qu'en mois. Sans l'ontologie, impossible de construire des applications significatives aussi rapidement. L'ontologie est construite sur 6 primitives [CONFIRMED] avec 3 couches (Semantic, Kinetic, Dynamic) et repose sur 5 decisions d'ingenierie critiques.

2. **Le modele FDE** — des ingenieurs logiciels embarques avec les clients qui comprennent a la fois la technologie et le domaine — est un moat de capital humain. ~1,000-1,500 FDEs [ESTIMATED], $135K-$300K de base salary [CONFIRMED], $760K/an en pricing gouvernement [CONFIRMED]. Les job postings FDE dans l'industrie ont cru de 800-1,000% en 2025 [CONFIRMED].

3. **La methodologie de co-building elle-meme** cree un sentiment de propriete psychologique et des champions internes qu'aucun slide deck ou video de demo ne peut egaler. Quand un VP of Operations regarde ses propres donnees alimenter un agent AI qui repond a des questions sur son propre workflow, la vente est largement faite avant que l'AE n'ouvre la discussion commerciale (Claude).

> Shyam Sankar : *"the problem-solving ethos of forward-deployed engineering brought to a compressed, high-intensity format"* (Claude).

> Alex Karp : *"[The bootcamp model] sets a standard very hard for any other company to meet."* [CONFIRMED]

---

*Sources primaires : synthese-1-presales-bootcamp-playbook.md (GPT/Claude/Perplexity croise), extracted-playbook-05.md (playbook consolide 322KB), extracted-parts-abcd.md (Parts B-D avec corrections Phase 4). Donnees financieres courantes au Q4 2025 (February 2026).*

---

# PARTIE 2 -- PILOT "ACQUIRE" : DEPLOIEMENT 90 JOURS

> **Sources fusionnees :**
> - **(GPT)** = gpt-pilot-implementation-methodology.md
> - **(Claude)** = claude-pilot-methodology.md
> - **(Perplexity)** = perplexity-pilot-methodology.md
> - **(Synthese-5)** = synthese-5-claude-agent-research.md (recherche agents Claude, 8 fichiers)
> - **(Playbook-05)** = extracted-playbook-05.md / extracted-parts-abcd.md (playbook consolide 322KB)

---

## 2.1 Modele Economique du Pilot

### 2.1.1 Pourquoi Palantir perd de l'argent volontairement

Le pilot de 90 jours est le premier acte d'une strategie deliberee de perte initiale. Palantir investit massivement dans chaque nouveau client avec l'objectif explicite de demontrer une valeur indeniable en quelques semaines pour declencher l'expansion. Le principe est articule par Nabeel Qureshi (8 ans comme FDE) : resoudre d'abord un probleme "hair on fire", puis s'etendre a partir de cette tete de pont (Claude).

**Chiffres exacts du S-1 (2019) :**

| Metrique | Valeur | Source |
|----------|--------|--------|
| Revenus moyens par client Acquire (1ere annee) | **$600,000** | CONFIRMED (S-1) |
| Perte de contribution totale sur la cohorte new customers | **-$65.4M** | CONFIRMED (S-1) |
| Marge de contribution phase Acquire | **Negative** | CONFIRMED (S-1) |
| Marge de contribution phase Expand (mois 3-12) | **-43% a +35%** | ESTIMATED (Playbook-05) |
| Marge de contribution phase Scale (annee 2+) | **+55%+** | ESTIMATED (Claude) |

La logique economique : chaque dollar perdu pendant l'Acquire genere un multiple d'expansion. Un contrat initial de $100K croit en moyenne a **$5.6M de valeur contractuelle annuelle mature** -- soit un **multiple d'expansion de 56x** (CONFIRMED, presentations investisseurs) (Playbook-05).

### 2.1.2 ACV typique du pilot

| Stage | Fourchette ACV | Terme | Scope |
|-------|---------------|-------|-------|
| Pilot (Acquire) | **$100K-$500K** | 3-6 mois | 1-2 use cases, equipe unique |
| Platform initiale (Expand) | $500K-$2M | 12 mois | 3-5 use cases, equipes multiples |
| Expansion | $2M-$10M | Multi-annees | Departement entier, ontologie cross-fonctionnelle |
| Enterprise | $10M-$50M+ | 3-5 ans | Plateforme organisation-wide |

(CONFIRMED, S-1 / Playbook-05)

L'ACV median du pilot post-bootcamp se situe entre **$200K-$500K** (median $250K-$350K) (ESTIMATED, Playbook-05). Alex Karp a cite un contrat de $3M par prospection sortante, puis un bootcamp menant a un "enterprise-wide agreement likely to be significantly larger" dans le meme trimestre (Synthese-5).

### 2.1.3 Marge de contribution negative (-43%)

Pendant la phase Expand (mois 3-12), la marge demarre a **-43%** puis s'ameliore progressivement vers **+35%** a mesure que le levier plateforme prend le relais et que l'intensite FDE diminue (ESTIMATED, Playbook-05). Le point mort se situe quelque part entre le mois 6 et le mois 12, selon la vitesse d'expansion.

**Cout FDE par $1M d'ARR au fil du temps :**

| Annee | Cout FDE par $1M ARR | Interpretation |
|-------|---------------------|---------------|
| 2016 | ~$700K | Presque $1 de main-d'oeuvre FDE pour $1 d'ARR -- un business de consulting deguise |
| 2020 | ~$280K | Maturation de la plateforme reduisant l'intensite FDE par dollar |
| 2025E | ~$80K-$150K | Automatisation IA + self-service plateforme |

(ESTIMATED, Playbook-05)

**Le Net Dollar Retention (NDR) valide le modele :**

| Trimestre | NDR |
|-----------|-----|
| Q3 2023 | 107% |
| Q1 2024 | 114% |
| Q3 2024 | 120% |
| Q3 2025 | 134% |
| Q4 2025 | **139%** |

(CONFIRMED, earnings calls) (Playbook-05)

Les 20 premiers clients generent en moyenne **$94M+ de revenus annuel** par client (+45% YoY) (CONFIRMED, Q4 2025) (Playbook-05).

---

## 2.2 Composition de l'Equipe Deployee

### 2.2.1 Nombre et roles exacts

**Equipe standard du pilot (3-5 personnes) :**

| Role | Nombre | Nom de code interne | Fonction principale |
|------|--------|-------------------|-------------------|
| **Deployment Strategist (DS)** | 1 | "Echo" | Possede la relation business -- gestion des parties prenantes, priorisation des use cases, communication executive, roadmap d'expansion. Beaucoup viennent de McKinsey, BCG ou Bain (CONFIRMED, LinkedIn). Gere la politique organisationnelle pour que les FDE puissent se concentrer sur la construction |
| **Forward Deployed Engineer (FDE/FDSE)** | 2-4 | "Delta" | Possede le stack technique -- pipelines de donnees, ontologie, applications Workshop, code. Generalistes capables d'ecrire des transforms PySpark le matin et de presenter une application Workshop a un VP l'apres-midi |
| **Solutions Architect (SA)** | 0-1 | -- | Conseils architecturaux transversaux -- strategies d'integration, revue des modeles d'ontologie, pont entre equipes FDE et organisations d'ingenierie client. Pas systematiquement dedie |
| **Forward Deployed Infrastructure Engineer (FDIE)** | 0-1 | -- | Deploiement plateforme pour environnements on-premise ou air-gapped -- clusters Kubernetes, reseau, stockage, conformite. Implication variable : peu en SaaS, a temps plein sur deploiements gouvernementaux classifies |

(Claude, Perplexity, Synthese-5)

[CONTRADICTION] **(Claude)** indique **1 DS + 2-4 FDE**. **(Perplexity)** indique **4-5 personnes : 2-3 FDSE + 1-2 DS**. Les deux convergent sur un total de 3 a 5 personnes, mais divergent sur la repartition DS/FDE.

**Pour les comptes strategiques**, l'equipe passe a **10-20+ personnes** (NHS, Army Vantage, BP) (Claude).

### 2.2.2 Le modele en Pod -- structure radicalement plate

L'appariement Delta/Echo est delibere : les Echos gerent les relations parties prenantes, le cadrage des problemes et la direction strategique ; les Deltas gerent l'execution technique, l'integration de donnees et la construction de solutions. Ensemble ils forment l'equipe de deploiement minimale viable (Synthese-5).

**Differences critiques avec la pyramide du conseil MBB :**

| Dimension | Pyramide MBB | Pod Palantir |
|-----------|-------------|-------------|
| Hierarchie | Partner > EM > Associate > BA | DS et FDEs sont des pairs, pas un manager et ses rapports |
| Nombre de personnes | 6 (1 Partner + 1 EM + 2 Associates + 2 BAs) | 3-5 (1 DS + 2-4 FDEs) |
| Sortie | PowerPoint avec recommandations | Logiciel fonctionnel en production |
| Passation | Recommandations remises au client | La meme personne qui diagnostique construit et deploie |
| Autonomie | Pilotee par le Partner | "Radical deference to teams in the field" |

(Synthese-5)

### 2.2.3 Profil des FDE

- **Experience** : 1+ an post-diplome, **age median ~25** (CONFIRMED, Pragmatic Engineer)
- **Backgrounds academiques** : top CS (Stanford, MIT, CMU), mais aussi philosophie, mathematiques, physique (CONFIRMED)
- **Competence distinctive** : "unusual sensitivity to social context" -- capacite a lire une salle, naviguer la politique organisationnelle, et traduire les besoins non-dits
- **Compensation** : entry-level $135K-$200K base, $171K-$415K total comp (median $215K). Senior : $200K-$300K base, $500K-$800K total (CONFIRMED, levels.fyi + Glassdoor) (Playbook-05)
- **Tarification services** (UK G-Cloud) : **GBP 150,000 par personne par trimestre** (~$760K/an/FDE) (CONFIRMED) (Playbook-05)

### 2.2.4 Ratio FDE par client et presence on-site

| Dimension | Donnee |
|-----------|--------|
| Ratio FDE / client pilot | 2-4 FDE + 1 DS par client |
| Heures de travail hebdo | **50-70 heures** pendant les pilots (Claude) |
| Deplacement on-site | **50-80%** du temps sur site client (Claude) |
| Jours on-site / semaine | 2-4 jours (Synthese-5, Nabeel Qureshi) |
| Equilibre vie/travail (Glassdoor) | **2.7/5** (CONFIRMED, 156 reviews) (Synthese-5) |
| Horaires typiques | 7h-19h la plupart des jours, plus Slack depuis la maison et travail occasionnel le weekend (Synthese-5) |

[CONTRADICTION] **(Claude)** parle de 50-80% de deplacement. **(Synthese-5)** precise "2-4 jours/semaine selon la phase" avec des jours bureau/remote pour le code et la planification.

### 2.2.5 La question du designer UI

[CONTRADICTION] **(GPT)** mentionne que le DS travaille aux cotes des ingenieurs et des "Product Designers" dans les deploiements, impliquant que l'UI/UX n'est pas purement concue par les ingenieurs. **(Perplexity)** indique qu'il n'y a pas de role dedie "UI designer" dans l'equipe FDE standard ; le FDE construit l'UI, avec le DS qui pilote les exigences et boucles de feedback. En pratique, le FDE est celui qui construit l'application Workshop. L'esthetique est secondaire par rapport a la fonctionnalite operationnelle.

---

## 2.3 Phase 1 : Decouverte & Collecte (Semaines 1-3)

### 2.3.1 Stakeholder Mapping

#### QUI ils rencontrent -- dans quel ordre et pourquoi

Le biais culturel de Palantir est "prends l'avion d'abord, pose des questions ensuite" (Perplexity). L'equipe FDE arrive sur site au Jour 1 avec un briefing minimal.

**Semaine 1 -- Ordre de rencontre des parties prenantes :**

| Priorite | Qui | Format | Frequence | Mene par | Pourquoi |
|----------|-----|--------|-----------|----------|---------|
| 1 | **Sponsor executif** (CEO, COO, CDO) | 1-a-1 ou petit groupe | Hebdomadaire | DS | Securiser la couverture top-down, valider les priorites strategiques, debloquer l'acces aux donnees |
| 2 | **Chefs de departements / VP** | Entretiens 1-a-1 | 2-4 par departement | DS + FDE | Comprendre structure, douleurs, dynamiques politiques |
| 3 | **Operateurs de premiere ligne** | Observation + entretiens informels | Quotidien | FDE | Comprendre les workflows reels. Les FDE marchent litteralement sur le plancher d'usine, dans le service hospitalier, ou au desk de trading |
| 4 | **Proprietaires de donnees / gatekeepers IT** | Reunions formelles | 2-3 par semaine | DS (politique) + FDE (technique) | Souvent les parties prenantes les plus adversaires. Negocier l'acces aux systemes sources |
| 5 | **Proprietaire IT/securite** | Reunions techniques | Selon besoin | FDIE + FDE | Politiques reseau, identite, conformite |

(Perplexity, Claude, GPT)

**Exemple concret :** A Airbus, Nabeel Qureshi "s'est installe a Toulouse pendant un an et a travaille a l'usine aux cotes des gens de la production quatre jours par semaine" (Perplexity). Ce n'est pas une visite de courtoisie -- c'est une immersion totale.

#### COMBIEN d'interviews

[CONTRADICTION] **(Claude)** indique **10-30 entretiens de parties prenantes dans les deux premieres semaines**. **(GPT)** indique que la documentation Palantir ne prescrit pas de nombre precis d'entretiens. **(Perplexity)** ne donne pas de chiffre precis. Le chiffre de 10-30 est la meilleure estimation disponible.

#### QUELLES questions ils posent

Les FDE n'utilisent PAS de guides d'entretien formels ou de frameworks de decouverte structures comme ceux courants en conseil de gestion (Synthese-5). L'approche est plus proche du "travail de terrain anthropologique" que du consulting structure (Perplexity).

**Questions fondamentales (Claude) -- 5 themes :**

1. **"Quelles decisions prenez-vous chaque jour ?"** -- identifier les moments de decision
2. **"De quelles informations avez-vous besoin pour ces decisions ?"** -- identifier les inputs decisionnels
3. **"D'ou viennent ces informations ?"** -- mapper les sources de donnees
4. **"Qu'est-ce qui est casse dans ce processus ?"** -- identifier les points de douleur
5. **"Que feriez-vous avec une information parfaite ?"** -- envisager l'etat ideal

**Questions alignees sur le template Foundry (GPT) :** Le Foundry use case lifecycle fournit un format canonique de requirements fonctionnels : `[User Type] [Interface] [Decision] [Decision Inputs] [Action]`. Les questions les plus discriminantes mappent directement aux champs du template :

- "Quelle **decision** prenez-vous ?"
- "Quels **inputs** faites-vous confiance ?"
- "Ou les **obtenez-vous** ?"
- "Quelle **action** prenez-vous et quel changement d'etat ?"
- "Quel est le **KPI** d'une bonne decision ?"

**Techniques d'entretien operationnelles (Synthese-5) :**

1. **Observation immersive** : simplement etre present dans l'environnement du client revele les workflows reels vs. les processus declares. "SOPs are corporate fiction: static, incomplete, and often wildly outdated."
2. **L'approche du probleme XY** : distinguer entre les demandes enoncees (Y) et les problemes sous-jacents (X). La premiere question est toujours "What are you trying to accomplish?"
3. **Questionnement contextuel** : "What does this person's day look like? What did they do before this call? What will they do after?"
4. **Construction incrementale de confiance par les quick wins** : resoudre un point de douleur visible rapidement (en quelques jours) pour gagner la confiance et l'acces necessaires a une decouverte plus profonde

#### Framework d'interview : Keith Johnstone's *Impro* et decouverte ethnographique

*Impro: Improvisation and the Theatre* de Keith Johnstone est LE livre que chaque nouvelle recrue FDE recoit le Jour 1. Le vocabulaire de l'entreprise est "sature d'Impro-ismes" (Perplexity). L'objectif n'est pas de poser des questions prescrites mais de **lire les dynamiques de pouvoir** :

**Concepts cles d'Impro operationnalises par les FDE (Synthese-5) :**

- **Comportement haut-statut vs. bas-statut** : "Keeping your head still while talking is high status, whereas moving your head side to side a lot is low status."
- **Transactions de statut** : chaque interaction implique des negociations implicites sur le statut relatif
- **"Casting"** : identifier qui detient le pouvoir reel vs. l'autorite nominale (Perplexity)
- **Lire la salle** : "unusual sensitivity to social context" -- identifier les decideurs, les influenceurs et les resistants

Zoe Scaman decrit le FDE comme devant devenir **"wallpaper -- present enough to observe, invisible enough not to trigger the immune system."** Les FDE doivent "know when to push and when to disappear" tout en "playing political games while looking like you're not playing political games" (Synthese-5).

**Liste de lecture complete d'onboarding (CONFIRMED) (Synthese-5) :**

| Livre | Auteur | Pourquoi |
|-------|--------|---------|
| *Impro* | Keith Johnstone | Dynamiques de statut, lecture des salles |
| *The Looming Tower* | Lawrence Wright | Comprendre les silos d'information (l'histoire d'origine de Palantir) |
| *Interviewing Users* | Steve Portigal | Techniques d'entretien utilisateur -- extraire les vrais besoins |
| *Getting Things Done* | David Allen | Productivite personnelle pour le multitasking intense |
| *Principles* | Ray Dalio | Frameworks decisionnels, transparence radicale |

Note : pas de livres d'ingenierie logicielle, pas de frameworks de conseil. La selection revele que les FDE sont d'abord des "lecteurs de contexte social" (Synthese-5).

#### Artefacts produits : stakeholder map, influence diagram

L'objectif de la semaine 1 est d'identifier rapidement trois categories de personnes (Perplexity) :

1. **Le champion** dont la carriere est liee au succes du projet
2. **Les bloqueurs** (generalement middle-management data gatekeepers dont le pouvoir derive du controle du flux d'information)
3. **Les allies de premiere ligne** qui feront pression sur leurs chefs

Sarah Constantin decrit la strategie explicitement : "Win the hearts of front-line workers... use your allies on the bottom (front-line workers) and the top (executives) to squeeze out your opponents in the middle" (Perplexity).

**Artefacts produits en semaine 1 :**

- **Carte des parties prenantes** documentant noms, roles, niveau d'influence, propriete des donnees, et disposition envers le projet (champion, neutre, hostile) (Claude)
- **Premiers diagrammes de processus informels** (whiteboard, swimlane informels, PAS de BPMN formel) (Claude, Perplexity)
- **Esquisse du paysage de donnees** identifiant systemes, bases de donnees, APIs, et file stores connus (Claude)
- **Notes de reunion** de chaque entretien (Claude)
- **Premier "use case overview"** et liste initiale de requirements fonctionnels (GPT)
- **Plan d'acces** listant sources de donnees, proprietaires, credentials necessaires, et pattern reseau utilise (GPT)
- **Documentation collaborative** via Notepad, stockee dans un Project Foundry (GPT)

**Cadence de reunions etablie des la semaine 1 (Claude) :**

| Reunion | Frequence | Duree | Participants | Objet |
|---------|-----------|-------|-------------|-------|
| Daily standup interne | Quotidien | 15 min | Equipe Palantir uniquement | Decouvertes, bloqueurs, priorites |
| Sessions de travail | 2-3x/semaine | 30-60 min | Analystes et operateurs client | Immersion dans les workflows |
| Update executif | Hebdomadaire | 30 min | DS + sponsor executif | Impact, bloqueurs strategiques |

### 2.3.2 Process Mapping -- LA METHODE DETAILLEE

#### Comment les FDE cartographient les process du client

Les FDE **n'utilisent PAS** de frameworks formels de cartographie des processus metier comme BPMN, cartographie de flux de valeur ou notation structuree de processus (Synthese-5). Ce n'est pas du consulting classique.

**Methode en 4 etapes (Synthese-5) :**

1. **Observer le workflow reel** -- jours ou semaines a regarder comment les gens travaillent vraiment. Les FDE s'incorporent physiquement dans l'environnement operationnel : plancher d'usine, service hospitalier, desk de trading, centre logistique
2. **Reconstruire le processus reel** base sur l'observation (PAS sur la documentation officielle). Le processus "reel" differe presque toujours du processus documente (Claude)
3. **Mapper a l'Ontologie** : identifier les Object Types, Link Types, Action Types, Properties qui emergeront du processus observe
4. **Construire un prototype fonctionnel** (pas de documentation papier, du logiciel fonctionnel)

**Palantir a remplace les cartes de processus papier par une ontologie digitale vivante.** Le FDE marche les memes ateliers, mene les memes entretiens qu'un consultant, mais le resultat est un schema Ontology Manager plutot qu'un deck PowerPoint (Synthese-5).

#### Ce que les FDE utilisent a la place du BPMN

- **Whiteboard sketches informels** pour capturer les flux initiaux (Claude, Perplexity)
- **Swimlane informels** (pas de notation formelle) pour montrer les responsabilites par role
- **Diagrammes de lifecycle** -- une machine a etats d'Actions que les utilisateurs prennent pour modifier les objets. C'est la contribution unique de Palantir : le processus est modelise comme des **transitions d'etat sur des objets ontologie** (GPT)
- **Diagrammes de flux de donnees informels** (pas BPMN) (Synthese-5)
- **Flow Capture** de Foundry pour enregistrer les workflows et generer de la documentation (GPT)
- **Machinery** (outil plateforme) : process mining a partir de journaux d'evenements externes. Mais c'est un outil plateforme, pas la methodologie primaire du FDE (Synthese-5)

Les cabinets MBB utilisent Value Stream Mapping, Swimlane, SIPOC, et BPMN (Synthese-5). Palantir a deliberement rejete cette approche formelle au profit de l'observation directe et du prototypage rapide.

#### Combien de temps passe a OBSERVER vs INTERVIEWER

[CONTRADICTION] **(Claude)** indique une repartition **60% entretiens / 40% observation**. **(Perplexity)** indique que dans les contextes manufacturing, les FDE passent les 1-2 premieres semaines "principalement a observer et poser des questions, avec peut-etre 20-30% du temps sur la configuration systeme reelle" -- suggerant une balance inversee (plus d'observation que d'entretiens formels).

La realite varie probablement selon le contexte :
- **Manufacturing / operations physiques** : 60-70% observation, 30-40% entretiens
- **Services financiers / workflows digitaux** : 60% entretiens, 40% observation

#### Le factory floor walk / hospital ward walk / trading desk walk

L'observation est critique car les FDE documentent le processus **tel qu'observe, pas tel que prescrit** (Synthese-5). Exemples concrets :

- **Airbus, Toulouse** : l'equipe de Qureshi a construit "Asana, but for building planes -- they took disparate sources of data -- work orders, missing parts, quality issues ('non-conformities') -- and put them in a nice interface" en "a week or two" (Synthese-5)
- **Un client manufacturing** : un FDE a decouvert que les operateurs contournaient entierement l'ERP, tracant les donnees critiques dans des tableurs personnels (Claude)
- Nabeel Qureshi a vecu a Toulouse un an pour travailler a l'usine de fabrication d'Airbus 4 jours/semaine (Perplexity, Synthese-5)

Le FDE observe concretement :
- Comment les operateurs demarrent leur journee
- Quels outils ils ouvrent en premier
- A quels moments ils passent d'un systeme a un autre
- Quand ils appellent un collegue pour une information manquante
- Ou ils notent les choses "en attendant"
- Quels contournements informels existent

#### Comment ils identifient les "hair on fire problems"

La question fondamentale est : **"Quelqu'un perd-il le sommeil a cause de ce probleme ?"** (Claude)

L'identification repose sur :
1. **L'observation de la frustration visible** : operateurs qui jurent devant leur ecran, managers qui escaladent en reunion
2. **Les workarounds heroiques** : quand quelqu'un a construit un spreadsheet de 50 onglets pour palier un manque systeme, c'est un "hair on fire problem"
3. **La frequence** : un probleme quotidien affectant 50 personnes vaut plus qu'un probleme annuel affectant 5
4. **Le cout cache** : temps perdu, erreurs, decisions retardees

#### Artefacts produits

- **Diagrammes de processus informels** (plus detailles que semaine 1) (Claude)
- **Diagrammes de flux de donnees** : d'ou les donnees viennent, ou elles vont, ou elles se perdent
- **Pain points map** : cartographie visuelle des points de douleur par role, frequence, et severite
- **Object model sketch** (premiere passe) : object types et link types ebauches (GPT)
- **Lifecycle diagram** : actions comme machine a etats (GPT)
- **Documentation des processus tels qu'observes** (pas tels que prescrits) (Synthese-5)

### 2.3.3 Data Discovery & Inventaire

#### Template d'inventaire des donnees

Les FDE construisent un **inventaire de donnees** systematique documentant chaque systeme source. Cet inventaire identifie typiquement **15-40 sources de donnees** dans un deploiement de taille moyenne, bien que seules **3-10** seront connectees pendant le pilot (Claude).

**Champs de l'inventaire par source :**

| Champ | Description |
|-------|-------------|
| Systeme source | Nom du systeme (ex: SAP ERP, Salesforce CRM) |
| Type de base | Relationnel, fichier, API, streaming |
| Proprietaire | Nom + equipe du data owner |
| Volume approximatif | Nombre de lignes / taille |
| Frequence de rafraichissement | Temps reel, horaire, quotidien, hebdomadaire, manuelle |
| Problemes de qualite connus | Nulls, doublons, donnees stales |
| Mecanisme d'acces | Direct, agent, VPN, API, export manuel |
| Statut d'acces | Obtenu / En negociation / Bloque |
| Evaluation qualite | Connecter maintenant / Connecter plus tard / Ne vaut pas la peine |

(Claude, GPT)

Les donnees sont souvent dans des formats hostiles : "PDFs, notebooks, fichiers Excel (mon Dieu, tellement de fichiers Excel)". Chez un constructeur aeronautique, les resultats de tests qualite des avions etaient sous forme de "PDFs manuscrits scannes" (Perplexity, citant Nabeel Qureshi).

#### Questions posees aux data owners

**Questions metier (Perplexity) :**
- "Dans quel systeme c'est ?"
- "A quelle frequence mis a jour ?"
- "Qui a acces ?"
- "Quel format ?"
- "A quel point fiable ?"
- "Que signifie reellement ce champ ?"

**Questions forcees par la plateforme Foundry (GPT) :**
- "Ou est-ce heberge ?" (cloud accessible directement vs. reseau prive necessitant un agent)
- "Quel modele de credentials ?" (service account, OAuth, token)
- "Quel type de sync ?" (batch file vs table)
- "Quel type de transaction ?" (SNAPSHOT = remplacement complet vs APPEND = ajout)
- "Est-ce que le schema change ?" (possibilite de bloquer les syncs sur changement de schema)

#### Assessment de qualite des donnees (scoring framework)

Aucun framework de scoring formel n'a ete divulgue publiquement (Perplexity). La culture Palantir valorise le jugement sur les frameworks (Perplexity).

**Rubrique pratique utilisee par les FDE (Claude) -- 4 dimensions :**

| Dimension | Ce qu'ils evaluent | Methode |
|-----------|-------------------|---------|
| **Completude** | Nulls et lacunes dans les champs critiques | Inspection directe des premiers echantillons |
| **Fraicheur** | Frequence de mise a jour, staleness | Verification des timestamps de derniere modification |
| **Coherence** | Les definitions matchent-elles entre systemes ? | Comparaison cross-systeme (meme client = meme ID ?) |
| **Accessibilite** | Peut-on reellement y acceder ? | Test de connexion technique |

**Triage en trois buckets :**
1. **Connecter maintenant** : donnees accessibles, de qualite suffisante, necessaires au use case prioritaire
2. **Connecter plus tard** : donnees utiles mais acces difficile ou qualite insuffisante
3. **Ne vaut pas la peine** : effort disproportionne par rapport a la valeur

**Controles qualite natifs a Foundry (GPT) -- 3 couches :**

1. **Health checks** : valident succes du job/build, duree du build, et fraicheur a travers le pipeline
2. **Unit tests Pipeline Builder** : outputs attendus au niveau logique, doivent reussir avant de merger une proposal
3. **Data expectations** : codees en code, peuvent annuler les builds en cas d'echec, s'integrent avec Data Health

#### Le probleme des "data access politics" -- comment ils negocient concretement

C'est **la realite operationnelle la plus importante** du travail FDE. Nabeel Qureshi la decrit directement :

> "Data integration was the core bottleneck. Organizations controlled data sources and 'justify their existence...by being the gatekeepers of that data source.' Pilots often lasted 8-12 weeks...spent all 8-12 weeks just getting data access, and the final week scrambling to have something to demo." (Perplexity, Synthese-5)

**Pourquoi l'acces aux donnees est politique, pas technique (Synthese-5) :**
- Les equipes se definissent par leurs donnees : une equipe qui controle une source de donnees justifie son existence en etant le gardien
- Les donnees revelent des verites inconfortables : une fois integrees, les inefficacites que les equipes individuelles pouvaient cacher deviennent visibles
- Acces = responsabilite : si tout le monde voit les memes donnees, personne ne peut raconter des histoires differentes

**Playbook de negociation d'acces en 8 etapes (synthese des trois sources + Synthese-5) :**

| Etape | Tactique | Qui la mene |
|-------|---------|-------------|
| 1 | **Commencer par les donnees deja accessibles** -- APIs publiques, drives partages, CSVs exportes -- pour construire un prototype sans permission (Claude) | FDE |
| 2 | **Demontrer la valeur au gatekeeper** -- leur montrer comment la plateforme integree pourrait aider *leur* equipe, pas seulement celle du sponsor (Claude) | DS + FDE |
| 3 | **Faire des gardiens des partenaires** : "Your data is so valuable that the CEO wants it in the central platform" (Synthese-5) | DS |
| 4 | **Leverager le sponsorship executif** -- faire en sorte que le champion senior mandate l'acces quand le relationship-building echoue (les trois sources) | DS |
| 5 | **Construire la pression frontline** -- les operateurs qui voient la valeur font pression sur leurs managers (Perplexity) | FDE (indirect) |
| 6 | **Adresser les preoccupations securite de front** -- la plateforme Palantir a du RBAC integre, de la securite row-level -- implementer Palantir rend souvent les donnees *plus* securisees (Perplexity) | DS + FDIE |
| 7 | **Contourner entierement** -- trouver des sources alternatives ou faire en sorte que les executifs override les restrictions (Claude) | DS |
| 8 | **Escalade organisationnelle via les roles Foundry** : la configuration des politiques de sortie reseau dans Control Panel peut necessiter des roles privilegies specifiques ("Information security officer"), ce qui est un levier d'escalade concret (GPT) | FDIE |

**Division critique des responsabilites :** Le DS gere la dimension politique pendant que les FDE gerent l'evaluation technique. Les FDE ne devraient JAMAIS etre en position d'argumenter pour l'acces aux donnees en reunion -- c'est le travail du DS, arme de la couverture executive (Claude).

Sarah Constantin : "The Palantir Way is labor-intensive and virtually impossible to systematize. You have to throw humans at the persuasion problem" (Perplexity).

#### Qui sont les "hostile gatekeepers" et comment les contourner

Les gatekeepers sont generalement des **middle managers IT/data** dont le pouvoir derive du controle exclusif d'une source de donnees. Leur resistance n'est pas irrationnelle -- ils perdent du pouvoir si leurs donnees sont integrees et accessibles a tous (Synthese-5, Perplexity).

La strategie d'encerclement : allies en haut (executives qui mandatent l'acces) + allies en bas (operateurs terrain qui demandent l'acces) = pression des deux cotes sur le gatekeeper au milieu (Perplexity).

### 2.3.4 Priorisation des Use Cases

#### Criteres de selection

A la semaine 3, l'equipe restreint a **1-3 use cases**, typiquement un principal et un secondaire (les trois sources).

**Framework 2x2 (Claude) -- pas toujours formalise :**

- Axe vertical = **Valeur business** (intensite de la douleur x frequence x nombre d'utilisateurs affectes)
- Axe horizontal = **Faisabilite** (readiness des donnees x complexite technique x temps de demonstration)

**Matrice de scoring reconstruite (GPT) :**

| Critere | Description |
|---------|-------------|
| Impact | Intensite du probleme, economies potentielles |
| Readiness des donnees | Donnees disponibles et accessibles ? |
| Clarte du workflow | Le processus de decision est-il compris ? |
| Support des parties prenantes | Y a-t-il un champion fort ? |
| Potentiel d'expansion | Ce use case ouvre-t-il la porte a d'autres ? |

**Anti-patterns flags (GPT) :** investigation insuffisante des douleurs, requirements ancres sur des elements UI, focus trop restreint sur les utilisateurs, scoping qui ne porte pas jusqu'aux decisions.

**Criteres ponderes (Perplexity) :**

| Critere | Poids |
|---------|-------|
| Sponsorship executif | **Critique** |
| Readiness des donnees | **Critique** |
| Douleur frontline | Eleve |
| ROI demontrable (quantifiable en $/temps en 90 jours) | Eleve |
| Faisabilite technique (prototype en 2-4 semaines) | Eleve |
| Potentiel d'expansion | Moyen |

Aucune matrice de scoring formelle n'a ete divulguee publiquement (Perplexity). La culture Palantir valorise le jugement sur les frameworks.

#### Le concept du "lighthouse use case"

Le "lighthouse use case" est celui qui eclaire tout le reste. C'est le use case qui, une fois resolu, cree un appel irresistible pour etendre la plateforme. Il se situe a l'intersection precise de (Claude) :

1. **Douleur elevee** : un vrai probleme operationnel coutant temps, argent ou risque quotidiennement
2. **Disponibilite des donnees** : les donnees requises existent et sont accessibles
3. **Sponsorship executif** : quelqu'un d'assez puissant pour lever les obstacles
4. **Demonstration rapide** : un prototype fonctionnel en 2-3 semaines

**Les FDE evitent specifiquement** les use cases necessitant (Claude) :
- Une integration massive de donnees avant de montrer de la valeur
- Des donnees politiquement sensibles qui declencheront des batailles d'acces
- Le developpement de modeles ML avant de montrer de la valeur

Le DS est le gardien ultime de cette decision. "The wrong first use case can doom a deployment -- too ambitious and it fails; too trivial and it fails to justify Palantir's price point. The DS must find the Goldilocks zone" (Playbook-05).

**Matrice IFC (partenaire Palantir) :** matrice 2x2 "Impact vs. Implementation Complexity" avec quadrants Quick Wins, Strategic Investments, Easy Benefits, et Avoid/Defer (Perplexity).

**Artefacts cles en fin de semaine 3 :**

- Document de use cases priorise avec criteres de succes clairs (les trois sources)
- Inventaire de donnees avec statut d'acces et evaluation qualite (les trois sources)
- Diagrammes de processus pour les use cases cibles (Claude)
- Environnement Foundry provisionne et pret pour l'ingestion (Claude)
- Plan de projet initial avec jalons jusqu'a la semaine 12 (Claude)
- Premier squelette de pipeline et premieres entites ontologie (GPT)
- v1 use case brief : decisions, counterparts, requirements fonctionnels, outcomes/KPIs, douleurs (GPT)

**Point de decision :** Les use cases selectionnes en semaine 3 faconnent l'ensemble du pilot. C'est la decision a plus fort levier de l'engagement de 90 jours (Claude).

---

## 2.4 Phase 2 : Ontologie & Integration (Semaines 2-6)

### 2.4.1 Design de l'Ontologie

#### Comment un FDE decide : Object Type vs Property vs Link

La question directrice est "Quelles entites les utilisateurs pensent-ils et recherchent-ils dans leur travail quotidien ?" (Claude). Si les gens de la production parlent de "work orders", "non-conformites" et "pieces manquantes", ceux-ci deviennent des Object Types. L'exhaust de donnees que personne ne reference reste comme raw datasets (Perplexity).

**Framework de decision detaille (GPT, Synthese-5) :**

| Modeliser comme... | Quand... |
|--------------------|---------|
| **Object Type** | L'entite a son propre cycle de vie ; plusieurs autres entites la referencent ; elle necessite sa propre frontiere de securite/permissions ; les utilisateurs la rechercheront ou prendront des actions dessus ; elle a assez de proprietes pour justifier un backing dataset |
| **Property** | Valeur scalaire simple ; pas de raison pour d'autres objets de referencer cette valeur independamment ; la valeur change uniquement quand l'objet parent change |
| **Struct** | Groupement de 2-10 champs lies (Address, Full Name, GPS Coordinate avec metadata) ; pas de cycle de vie independant ; pas besoin de lier d'autres objets a cette sous-structure |
| **Link Type** | Deux Object Types independants necessitent une relation definie ; la relation elle-meme a un sens (cardinalite, directionnalite) |

**Distinction plus fine des Object Types (GPT) :**

| Type | Description | Exemple |
|------|-------------|---------|
| **Core** | Mappent directement aux granularites du systeme de reference (system-of-record) | `Customer`, `WorkOrder` |
| **Derived** | Existent quand le concept business existe mais aucun systeme source ne le represente | `RiskScore` (calcule cross-systeme) |
| **Use case** | Edites via les workflows operationnels | `Alert`, `TriageTicket` |

**Heuristique de bruit (GPT) :** Si un concept n'apparait pas dans une decision, n'a pas de transitions d'etat, et ne joint pas significativement d'autres concepts, c'est probablement du bruit pour la premiere tranche du pilot.

**Regle pratique de la communaute (Synthese-5) :** "If the client would naturally say 'show me all the Xs,' it is probably an Object Type. If they say 'what is the X of this Y,' it is probably a Property."

#### Le processus de design document / schema diagram

Le processus de creation d'Object Type dans Ontology Manager (Claude) :

1. Naviguer vers **Ontology Manager** dans Foundry
2. Creer un nouvel Object Type avec un display name (PascalCase, singulier : `WorkOrder`, `FlightPath`)
3. Selectionner le **backing dataset** -- le dataset Foundry dont les lignes representent les instances de ce type
4. Definir la **primary key** -- la colonne identifiant de maniere unique chaque instance. Convention : colonne `id` de type string, sans exception. L'ID doit etre inherement unique, construit uniquement a partir des proprietes propres de l'objet (Synthese-5)
5. Mapper les colonnes du dataset aux **Properties** avec des definitions typees (String, Integer, Double, Boolean, Date, Timestamp, GeoPoint, GeoShape, Array, Attachment, Timeseries)
6. Definir la **title property** -- quelle propriete s'affiche comme label de l'objet a travers les UIs
7. Configurer les flags **searchable**, **filterable**, et **sortable** sur les proprietes
8. Definir les **Link Types** connectant les Object Types : one-to-one, one-to-many, ou many-to-many, backes par des relations de cle etrangere
9. Optionnellement creer des **Interface Types** -- contrats abstraits que plusieurs Object Types implementent (ex: une interface "Asset" partagee par Vehicle et Equipment)

**Trois artefacts formalises de design (GPT) :**

1. **Object model sketch** (object types et link types)
2. **Lifecycle diagram** (actions comme machine a etats)
3. **Liste d'enrichissements + attentes d'interface**

**Point critique : Palantir ne valide PAS l'ontologie avec des diagrammes ER ou des documents de schema abstraits.** Ils la valident en montrant aux utilisateurs metier des applications fonctionnelles construites dessus. L'ontologie est validee par l'usage, pas par la revue (Synthese-5).

#### Naming conventions

| Element | Convention | Exemples |
|---------|-----------|---------|
| Object Types | PascalCase singulier | `Customer`, `WorkOrder`, `FlightPath` |
| Properties | camelCase | `firstName`, `orderDate`, `shippingStatus` |
| Link Types | Relations descriptives, pluriel cote pluriel | `customer_orders`, `flight_departsFrom` |
| Action Types | verb-noun | `CreateWorkOrder`, `AssignTechnician` |
| Cles primaires | `id` (string) | `id` |
| Cles etrangeres | `{foreign_object_type}_id` | `customer_id` |
| Proprietes timestamp | `{verbed}_at_timestamp` | `created_at_timestamp` |
| Proprietes utilisateur | `{verbed}_by_user` | `created_by_user` |

(Claude, Synthese-5)

**Regles critiques :**
- Les Object Type IDs sont auto-generes a partir du display name et **deviennent immutables apres le premier deploiement** (GPT, Perplexity)
- Pas d'abbreviations, pas de prefixes tag, jamais de noms versions (`Message_v2`) (Synthese-5)
- Utiliser des noms prefixes pour eviter les conflits dans les ontologies multi-tenant (ex: `supply-chain-shipment`, `hr-employee`) (Perplexity)

#### Validation avec le client : sous quelle forme

Les FDE montrent typiquement le design d'ontologie aux utilisateurs business dans une **revue informelle** -- souvent via **Object Explorer**, qui permet aux utilisateurs non-techniques de naviguer les objets, voir les proprietes, et naviguer les liens (Perplexity). Le DS dirige ces sessions, traduisant entre structure technique et sens business (Perplexity).

(Claude) mentionne des "working sessions where FDEs display the ontology visually and ask: Does this match how you think about your world?"

**Format des sessions de validation :**
- **30-60 minutes, 2-3 fois par semaine** (Perplexity)
- Le FDE montre un prototype fonctionnel (pas un diagramme abstrait)
- Le DS traduit entre langage technique et langage business
- Le feedback est implemente le jour meme ou le lendemain

#### Nombre d'iterations avant stabilisation

Les FDE passent typiquement par **3-5 iterations de design d'ontologie** avant que le schema se stabilise pour le premier use case (Claude, Perplexity). Le design initial commence minimal -- **5-10 Object Types de base** -- et croit a mesure que des use cases supplementaires sont ajoutes. Les deploiements matures peuvent atteindre **50-100+ Object Types** (Claude).

(GPT) note que les docs publiques ne donnent pas de nombre d'iterations, mais que le mecanisme de branching Foundry supporte une iteration rapide puis une stabilisation progressive.

Ted Mabrey decrit comment "le client reformule completement une charte de projet chaque mois" -- le scope creep est bienvenu car "la mission du client l'exige" (Perplexity).

**Echelle de deploiement typique (Synthese-5) :**

| Phase | Object Types |
|-------|-------------|
| Pilot starter (1 use case) | 5-15 |
| Departemental (3-5 use cases) | 20-60 |
| Enterprise (jumeau numerique) | 100-500+ |

#### DDD mapping

| Concept DDD | Equivalent Ontologie Palantir |
|-------------|------------------------------|
| Entity | Object Type |
| Value Object | Property ou Struct |
| Aggregate Root | Object Type primaire |
| Aggregate | Object Type + ses types dependants lies |
| Bounded Context | Projet Ontologie / Groupe |
| Ubiquitous Language | Noms d'Object Type et de Property |
| Domain Event | Action Type (ou Object Type derive) |
| Repository | Backing Dataset + Pipeline |

(Synthese-5)

**Insight critique :** le concept DDD d'Ubiquitous Language est exactement ce que Palantir veut dire par "Object Types and Actions must map to natural-language business concepts that the primary audience (business users) understands." L'Ontologie EST l'Ubiquitous Language (Synthese-5).

### 2.4.2 Construction des Pipelines

#### Architecture three-layer

Les pipelines Foundry suivent une architecture a trois couches (Claude) :

| Couche | Role | Contenu |
|--------|------|---------|
| **Raw** | Miroir exact | Donnees brutes mirroring les systemes sources exactement |
| **Clean** | Nettoyage | Deduplication, type casting, null handling, normalisation |
| **Semantic** | Ontologie | Datasets qui backent les Object Types de l'ontologie |

#### Step-by-step : Pipeline Builder (visuel) vs Code Repositories (PySpark)

**Pipeline Builder (no-code, choix par defaut pour le pilot) :**

Processus etape par etape (Claude) :

1. **Ajouter des noeuds de dataset input** au canvas visuel
2. **Appliquer des transforms** : 70+ types disponibles en drag-and-drop
   - Join (7 types : inner, left, right, full outer, cross, semi, anti)
   - Filter, Aggregate (sum, count, avg, min, max)
   - Add/Rename/Drop/Cast columns
   - Union, Pivot/Unpivot
   - Window functions, Deduplicate
   - Geospatial (distance join, intersection, KNN)
   - Parsing de fichiers (CSV, JSON, Excel, XML)
3. **Previsualiser les donnees** a n'importe quel noeud avant le build (panneau de preview integre)
4. **Configurer le dataset output**
5. **Definir le schedule** : manuel, cron-based (horaire, quotidien, hebdomadaire), ou triggered (build quand les datasets upstream changent)
6. **Choisir le type de build** : snapshot (remplacement complet) ou incremental (traiter seulement les nouvelles/changees)

Pipeline Builder supporte aussi l'ajout d'"Ontology outputs" pour guider l'integration vers des donnees propres et structurees (GPT).

**Systeme d'expressions :** plus de **500 fonctions built-in** -- arithmetique, string, array, date/time, geospatial, type casting, avancees (Parse JSON, cipher encrypt, text to embeddings LLM-powered, Case/When, Coalesce) (Synthese-5).

**Code Repositories (PySpark/Python) -- pour logique complexe :**

```python
from transforms.api import transform, Input, Output

@transform(
    output_dataset_1=Output("/project/output_clean"),
    raw_data=Input("/project/raw_data"),
)
def my_transform(raw_data, output_dataset_1):
    raw_df = raw_data.dataframe()  # TransformInput -> PySpark DataFrame
    # Nettoyage, filtrage, enrichissement...
    clean_df = raw_df.filter(raw_df.status == "active")
    output_dataset_1.write_dataframe(clean_df)
```

(Claude, Synthese-5)

**Choix Pipeline Builder vs Code Repositories (GPT) :** Le pattern pilot tend a **commencer avec Pipeline Builder** pour la vitesse et la comprehension partagee, puis introduire Code Repositories pour la logique complexe.

#### Exemple concret : SAP BAPI vers Customer Object Type

Sequence reconstruite :

1. **Source** : connecteur SAP certifie (Palantir Foundry Connector 2.0 for SAP Applications) -- supporte S/4HANA, ECC, Business Warehouse, SLT Replication Server. Integration SAP SLT pour change data capture (CDC) via triggers base de donnees (Synthese-5)
2. **Raw layer** : sync batch ou CDC creant un dataset mirror des tables SAP (BAPI_CUSTOMER_GETLIST, BAPI_CUSTOMER_GETDETAIL)
3. **Clean layer** : Pipeline Builder -- filtre clients actifs, normalise noms et adresses, deduplique par customer_id, cast des types (string -> integer pour codes postaux mal types)
4. **Semantic layer** : mapping vers Object Type `Customer` avec properties `id`, `name`, `address`, `industry`, `accountManager`, `creditLimit`, `createdAtTimestamp`
5. **Ontologie** : configuration dans Ontology Manager -- backing dataset = clean customer dataset, primary key = `id`, title property = `name`

#### Gestion de la qualite des donnees

Trois couches de controle qualite dans Foundry (GPT) :

1. **Health checks** : succes/echec du job, duree du build, fraicheur des donnees
2. **Unit tests Pipeline Builder** : inputs test definis, outputs attendus au niveau logique, doivent reussir avant merge
3. **Data expectations** : codees en code, peuvent annuler les builds en cas d'echec, s'integrent avec Data Health

Brevet US10866792B1 decrit des "deployment pipeline cleaning rules" automatisees verifiant : noms de datasets invalides, types de donnees invalides, donnees stale, branches cassees, et mappings invalides (Perplexity).

[CONTRADICTION] **(Perplexity)** note que "le testing formel d'unites varie selon le FDE -- la culture valorise la vitesse sur la couverture de tests pendant la phase pilote". **(GPT)** met davantage l'accent sur le testing formel comme partie integrante du processus. Nabeel Qureshi confirme la realite : les FDE "ecrivent du code qui fait le job rapidement, ce qui signifie -- poliment -- de la dette technique et des workarounds hacky" (Perplexity).

#### Process de test

- **Pipeline Builder** : unit tests avec inputs test, noeuds de transform selectionnes, et outputs attendus. Les unit tests doivent reussir avant de merger une proposal (GPT)
- **Code Repositories** : testing via pytest avec `TransformTestContext` de Foundry pour mock inputs/outputs. Chaque commit declenche des checks automatises -- linting, type checking, et unit tests -- via le CI/CD integre de Foundry (Claude)
- **Data expectations** : regles codees qui valident les donnees en sortie et annulent le build si elles echouent (GPT)

**Nombre typique de pipelines pilot :** **10-30 pipelines automatises** construits pendant un engagement de 90 jours, connectant 3-10 sources de donnees (Claude).

### 2.4.3 Connexion des Sources

#### Comment le setup fonctionne techniquement

**Trois modes de connexion (Synthese-5, GPT) :**

| Mode | Description | Quand l'utiliser |
|------|-------------|-----------------|
| **Foundry Worker (Cloud-Side)** | Foundry se connecte directement au systeme source et tire les donnees. Traitement sur infrastructure compute geree de Foundry | Systemes cloud accessibles (S3, APIs SaaS, databases cloud) |
| **Foundry Worker avec Agent Proxy** | Agent leger installe sur host Linux client (RHEL 8+, Ubuntu 22.04+) agit comme tunnel reseau uniquement ; tout le compute reste sur les workers Foundry | Databases on-prem derriere firewalls, systemes VPN |
| **Agent Worker (legacy)** | L'agent execute le compute sur le host client | Syncs fichiers specifiques, micro-batching, filtrage lourd avant sortie du reseau |

**Installation de l'agent (detail technique) :**
- Telecharger depuis Foundry, installer sur host Linux 64-bit, enregistrement automatique (GPT, Synthese-5)
- L'agent maintient une connexion HTTPS sortante vers Foundry sur le port 443 -- **pas de regles firewall entrantes necessaires** (Claude, Perplexity)
- L'agent tourne sur **Java 21+** (Perplexity)
- HA (haute disponibilite) atteint en assignant plusieurs agents a une seule source (Perplexity)
- Configuration dans `<agent-manager-install-directory>/var/conf/runtime.yml` (Synthese-5)
- Configuration certificat si proxy (Synthese-5)

**Configuration des syncs :** Les batch syncs creent des datasets ; peuvent etre previsualises ; peuvent etre schedulees ; options de configuration : type de transaction (SNAPSHOT vs APPEND), duree maximale, blocage des changements de schema (GPT).

**Connecteurs supportes :** **400+ connecteurs** (Synthese-5) couvrant :
- Databases : PostgreSQL, Oracle, SQL Server, MySQL, MongoDB, Snowflake, Redshift, BigQuery, etc.
- File systems : S3, Azure Blob, GCS, SFTP
- APIs : REST, OData
- SaaS : Salesforce, SAP, Workday, ServiceNow, JIRA
- Streaming : Kafka, Kinesis
- Avance : Webhooks, Listeners (Google Pub/Sub, Jira, Slack), Virtual Tables, Private Link

#### Temps typique par data source

| Type de source | Temps de connexion | Source |
|---------------|-------------------|--------|
| Sources cloud simples (S3, REST APIs) | **1-2 jours** | Perplexity |
| Connexions database simples | **1-3 jours** tests inclus | Claude |
| Databases on-prem necessitant setup d'agent et negociation firewall | **3-7 jours** | Perplexity |
| Sources complexes avec problemes firewall, VPN, ou decouverte de schema | **1-2 semaines** | Claude |
| Sources politiquement contestees | **Semaines a mois** | Perplexity |

#### Failure modes les plus frequents

| Mode de defaillance | Frequence | Description |
|--------------------|-----------|-------------|
| **Blocages firewall** | Le plus frequent | Regles firewall bloquant les connexions sortantes de l'agent (Claude, Perplexity) |
| **Rotation de credentials** | Frequent | Credentials expirant et cassant les syncs silencieusement |
| **Changements de schema** | Frequent | Colonnes renommees, ajoutees ou supprimees dans le systeme source. "Si vous ne designez pas pour le drift de schema, les pilots cassent a la semaine 6" (GPT) |
| **Limitation de debit API** | Frequent | Rate limiting sur les APIs tierces (Claude, Perplexity) |
| **Configuration proxy incomplete** | Moderee | (GPT) |
| **Certificats non approuves** | Moderee | (GPT) |
| **Goulots d'etranglement de privileges** | Moderee | Configuration de politique egress reseau necessitant des roles privilegies -- bloque par l'acces organisationnel plutot que par la complexite technique (GPT) |

---

## 2.5 Phase 3 : Actions, Securite, Applications (Semaines 4-10)

### 2.5.1 Design des Action Types

#### Comment les FDE identifient les actions utilisateur

Observer ce que les operateurs *font* apres avoir analyse les donnees -- assigner un technicien, fermer un ticket, approuver une commande, escalader un probleme (Claude).

Le processus suit trois etapes :

1. **Interview** : "Que faites-vous avec cette donnee ?" (Perplexity)
2. **Observation** : regarder concretement les actions physiques/systeme que l'operateur effectue
3. **Modelisation** : le solution design Foundry rend le workflow explicite comme un **diagramme de lifecycle : une machine a etats d'Actions** (GPT)

#### Configuration dans Ontology Manager (Claude, Perplexity)

1. Creer un nouveau Action Type avec nommage verb-noun (`AssignTechnician`)
2. Definir les **parametres** -- inputs types que l'utilisateur fournit (reference Object, String, Integer, Date)
3. Definir les **regles** -- mutations declenchees : Create Object, Modify Object, Delete Object, Create/Delete Link
4. Configurer les **regles de validation** -- conditions appliquees avant execution (champs requis, verifications de plage, contraintes d'unicite, validation cross-parametre)
5. Definir les **side effects** -- webhooks appelant des APIs externes, notifications, ou execution de Foundry Function
6. Configurer les **permissions** -- qui peut executer ce type d'action
7. Definir le **mode de soumission** -- synchrone (immediat) ou asynchrone (en file d'attente) (Claude)

#### Regles de validation : qui decide les business rules

Le DS mene la collecte des regles metier avec les utilisateurs et les process owners. Le FDE les implemente comme regles de validation sur les Action Types. Exemples concrets :

- "Un technicien ne peut pas etre assigne si son statut est 'en conge'"
- "Le montant de commande ne peut pas depasser le credit limite du client"
- "L'approbation necessite un manager de niveau N+2 au-dessus de $50K"

Ces regles sont validees en session de travail avec le client avant mise en production.

#### Configuration du writeback

[CONTRADICTION] **(Claude)** decrit un systeme ou les actions ecrivent dans un **Edits dataset** append-only (transaction log). L'ontologie fusionne les edits avec les backing datasets pour presenter l'etat courant en temps reel. **(Perplexity)** decrit un "writeback dataset" associe a l'Object Type avec deux modes de permission : "Only allow edits via Actions" (plus restrictif) ou edits via Actions plus Forms, Object Explorer, et appels API. Les deux descriptions fournissent des perspectives differentes du meme mecanisme.

**Write-back via webhooks (GPT, Claude) :** Foundry Data Connection Webhooks supporte les requetes HTTP sortantes vers des systemes externes. Les webhooks sont lies a une Source qui stocke les credentials et peuvent etre rate-limited. Cas d'usage : declenchement de notifications Slack, mise a jour de databases externes, appel d'APIs downstream.

**Ensemble minimum viable d'actions pour le pilot (GPT) :** Generalement une boucle d'approbation/triage, pas chaque exception possible. Decider si le write-back est requis dans le pilot ou peut etre simule.

### 2.5.2 Configuration Securite

#### RBAC setup concret

La securite est architecturalement fondamentale chez Palantir, pas boulonnee apres coup. Palantir "a compris tot que les luttes d'acces aux donnees etaient en partie liees a de vraies preoccupations de securite" (Perplexity).

**Processus de setup :** Le DS mene typiquement une session de type questionnaire avec l'equipe securite/conformite du client (Perplexity) :

- "Qui devrait voir quoi ?"
- "Quels roles existent ?"
- "Quelles sont les classifications de sensibilite des donnees ?"
- "Y a-t-il des donnees PII ? ITAR ? Confidentielles ?"

Traduit en : groupes, roles, et politiques object-level (GPT).

#### Les 7 couches de securite

| Couche | Mecanisme | Ce que ca controle |
|--------|-----------|-------------------|
| **Dataset-level** | ACLs (Read/Write/Discover) | Qui peut acceder au backing dataset |
| **Project-level** | Projects + Roles (Viewer, Editor, Owner) | Limite organisationnelle et de securite primaire |
| **Markings** | Labels de classification (CONFIDENTIAL, PII, ITAR) | Criteres d'eligibilite additionnels ; un utilisateur doit satisfaire TOUTES les markings appliquees |
| **Row-level (Object Security Policies)** | Controles mandatoires, markings, comparaisons d'attributs utilisateur | Quelles instances d'objets un utilisateur peut voir |
| **Column-level (Property Security Policies)** | Markings par-propriete | Quelles proprietes sont visibles -- ex: cacher les donnees de salaire aux non-RH |
| **Cell-level** | Combinaison object + property policies | L'utilisateur passe le check row mais echoue au check column -> voit null pour cette cellule |
| **Action-level** | Criteres de soumission + permissions de parametres | Qui peut executer quelles actions sur quels objets |

(Claude, Perplexity, GPT)

**Markings -- propagation automatique :** Si un dataset input porte un marking "PII", tous les datasets derives en heritent automatiquement a travers les pipelines (Claude).

**Row-level security via mapping tables (Perplexity) :** Utilise des tables de mapping (utilisateur -> usine, utilisateur -> business unit) qui filtrent au moment de la requete.

**PBAC (Purpose-Based Access Control) + Markings-Based MAC :** C'est le modele de securite le plus sophistique de Palantir et le plus difficile a repliquer (Playbook-05). Combine le RBAC standard avec des markings mandatoires (MAC -- Mandatory Access Control). Chaque element de donnees peut porter des markings binaires et conjonctifs. La securite est PBAC + MAC + RBAC en couches.

#### Process de test des policies

- Foundry fournit une capacite **"View as User"** / **"Check access"** permettant aux administrateurs de verifier ce qu'un utilisateur specifique peut et ne peut pas voir (Claude, Perplexity)
- Checklist de test operationnel (GPT) : verifier les grants de roles, markings, acces aux object types, et markings de lineage des datasources
- Le test est systematique : pour chaque role, verifier qu'il voit exactement ce qu'il devrait voir et rien de plus

#### Restricted views -- limitation importante

(GPT) : les restricted views fournissent des controles row-level pour les donnees ontologie, mais **ne sont pas compatibles comme inputs de transforms de pipeline** car les pipelines doivent etre reproductibles a travers les utilisateurs. Cela implique une decision architecturale entre restricted views et object security policies pour l'enforcement row-level (GPT semaine 6).

### 2.5.3 Construction des Applications Workshop

#### Step-by-step : comment builder une app Workshop

Processus de construction (Claude, Perplexity) :

1. **Creer un nouveau module Workshop** dans un projet Foundry
2. **Definir des Object Sets** -- collections filtrees et requetees d'objets ontologie (par type, filtres de propriete, traversee de liens)
3. **Designer le layout** avec containers, tabs, et widgets grille. Hierarchie : Module -> Header -> Pages -> Sections -> Widgets/Layouts (Columns/Rows/Tabs) + Overlays (Drawers/Modals) (Synthese-5)
4. **Placer les widgets d'affichage** et les lier aux Object Sets (ex: Object Table liee a "Active Work Orders"). 50+ widgets disponibles repartis en 5 categories (Synthese-5) :
   - **Display** : Object Table, Object List, Card, Details Panel, Metric/KPI Card, Status Indicator
   - **Visualization** : Charts (line, bar, area, scatter, pie, heatmap), Map (Mapbox), Timeline, Gantt, Graph
   - **Input** : Button, Text Input, Number Input, Dropdown/Multi-select, Date Picker, Slider, Toggle, File Upload, Search Bar
   - **Layout** : Container, Tabs, Accordion, Grid, Modal/Dialog, Sections, Conditional Visibility
   - **AIP** : AIP Agent, AIP Analyst, AIP Generated Content, AIP Interactive
5. **Configurer le systeme de variables** -- modele d'etat reactif ou les interactions widget (selection de ligne, clics de bouton) mettent a jour des variables qui cascadent vers d'autres widgets. **12 types de variables** : Object set, String, Numeric, Boolean, Date, Timestamp, GeoPoint, GeoShape, Array, Struct, Time series set, Object set filter (Synthese-5)
6. **Lier les Action Types aux boutons** -- mapper les parametres d'action aux inputs widgets ou variables
7. **Configurer la visibilite conditionnelle** -- montrer/cacher les widgets selon les valeurs de variables
8. **Definir les permissions** -- qui peut voir et utiliser l'application
9. **Publier et iterer**

**Pattern d'application canonique -- Inbox / Task Triage (Synthese-5) :**
- Panneau gauche : Filter List
- Centre : Object Table avec alertes filtrees
- Panneau droit : Object View (detail objet selectionne)
- Bas : Button Group avec actions (Approve, Reject, Escalate)
- Cas d'usage : triage de reclamations, investigation d'alertes, gestion de commandes, admission patient

#### Qui design l'UI

Le **FDE** construit l'application Workshop. Le **DS** pilote les exigences et les boucles de feedback. Il n'y a pas de role dedie "UI designer" dans l'equipe standard (Perplexity). Workshop est decrit en interne comme "Retool-like UI for making webapps" (Perplexity) -- l'accent est sur la fonctionnalite operationnelle, pas l'esthetique.

#### Nombre d'iterations typique

- Le premier prototype fonctionnel est typiquement disponible dans les **2-3 jours** du debut du developpement applicatif (Claude)
- Les FDE iterent **quotidiennement** pendant la phase de build (Claude)
- Le nombre d'iterations UI avant stabilisation : **5-10 par application** (Claude, Perplexity)
- Le DS organise des sessions d'iteration de **30-60 minutes, 2-3 fois par semaine** avec les utilisateurs client (Perplexity)

**Volumes typiques du pilot :**
- **3-10 applications Workshop** (Claude)
- **5-15 dashboards operationnels** (Claude)

#### Decision : Workshop vs Slate vs Quiver vs Contour

| Surface | Quand l'utiliser | Couverture pilot |
|---------|-----------------|-----------------|
| **Workshop** (defaut) | Workflows inbox operationnels, no-code/low-code, le plus rapide a construire | **80%+** des besoins applicatifs (les trois sources) |
| **Quiver** | Dashboards analytiques pour business users, exploration self-service, time series | Dashboards executifs, monitoring KPI |
| **Contour** | Analytics tabulaires, exploration ad-hoc | Outil transitionnel avant adoption Workshop |
| **Slate** | HTML/CSS/JS custom pour UIs pixel-perfect, visualisations D3.js complexes | Rare pendant le pilot, maintenant remplace par OSDK + custom React (Claude, Perplexity) |

---

## 2.6 Phase 4 : Formation & Go-Live (Semaines 8-12)

### 2.6.1 Formation des Utilisateurs

#### Format

La formation est massivement **hands-on** (Claude). Les FDE utilisent les sessions de **pair-programming** comme mecanisme principal de transfert de connaissances -- s'asseoir a cote d'un ingenieur client et construire quelque chose ensemble, plutot que donner un cours (Claude).

**Modes de livraison (Perplexity) :**

| Mode | Description |
|------|-------------|
| **Sessions classroom/workshop onsite** | Groupes de 5-15, menees par le DS |
| **Mentorat deskside** | Sessions 1-on-1, un FDE ou DS guide l'operateur dans le workflow en contexte reel |
| **Sessions virtuelles** | Pour equipes distribuees |
| **Apprentissage guide** | Plateforme learn.palantir.com avec certifications : Foundry Aware, Data Engineer, App Developer |
| **Train-the-trainer** | Identifier 2-5 "power users" qui deviendront champions Foundry internes |
| **Office hours** | FDE disponible pour questions ad-hoc (Claude) |

#### Heures de formation par role

| Tier | Qui | Heures (Claude) | Heures (Perplexity) | Contenu |
|------|-----|-----------------|--------------------| --------|
| **Power users / citizen developers** | Techniques enthousiastes, identifies semaine 4-5 | **8-16h** | **16-40h** | Construire apps Workshop, modifier pipelines, etendre ontologie |
| **Operateurs standard** | Utilisateurs quotidiens | **2-4h** | **4-8h** | Utilisation des apps Workshop pour leur workflow |
| **Executifs** | Decideurs | **30-60 min** | -- | Orientation dashboard, interpretation des KPIs |

[CONTRADICTION] Les estimations d'heures different entre (Claude) (8-16h power users, 2-4h standard) et (Perplexity) (16-40h power users, 4-8h standard). Perplexity donne des fourchettes plus larges et plus elevees.

#### Identification des "power users" / "citizen developers"

Identifies tot (typiquement **semaine 4-5**) sur la base de (Claude) :
- **Aptitude technique** : a l'aise avec les outils digitaux
- **Expertise domaine** : comprend profondement le business
- **Enthousiasme** : demande des fonctionnalites supplementaires, pose des questions avancees

Ils deviennent le noyau de l'equipe Foundry interne du client (Claude) et les futurs membres du Centre d'Excellence (Perplexity).

#### Materiels produits

- Guides utilisateur pour chaque application Workshop (captures d'ecran, workflows pas-a-pas) (Claude, Perplexity)
- Documentation de l'ontologie (catalogue Object Type avec descriptions, definitions de proprietes, diagrammes de relations) (Claude)
- Runbooks pipeline (schedules de rafraichissement, troubleshooting des modes de defaillance courants) (Claude)
- Video walkthroughs pour les taches communes (optionnel, selon preference client) (Claude)
- Templates "Playbook" montrant les patterns que les power users peuvent repliquer (Claude)
- Quick-reference cards pour les workflows et actions courants (Perplexity)
- Enregistrements video des sessions de formation (Perplexity)
- Chemins de certification pour les utilisateurs techniques (Data Engineer, App Developer) (Perplexity)

### 2.6.2 Go-Live

#### Checklist de go-live

**Pre-go-live validation (Claude, GPT) :**

- [ ] Tous les pipelines de donnees fonctionnent sur schedule avec health checks passant (fourchettes de nombre de lignes, seuils de taux de null, validation de schema)
- [ ] Configuration de securite testee via "View as User" pour chaque role
- [ ] Action Types valides -- toutes les regles de validation et mecanismes de writeback fonctionnant
- [ ] Applications Workshop testees avec de vrais utilisateurs en mode pilote
- [ ] Dashboards de monitoring configures avec alertes pour les echecs de pipeline, anomalies de qualite de donnees, et erreurs d'application
- [ ] Pipeline health validation, data freshness checks (GPT)
- [ ] Security policy audit (Perplexity)
- [ ] User access provisioning (Perplexity)
- [ ] Action type testing sous conditions reelles (Perplexity)
- [ ] Performance testing under load (Perplexity)

**Primitives de production readiness de Foundry (GPT) :**
- Schedules pour maintenir les syncs et builds en fonctionnement
- Health checks et visibilite Data Health a travers la lineage
- Integration notifications et issues, y compris auto-creation d'issue en cas d'echec de check
- Monitoring views pour collecter les checks et gerer l'alerte a l'echelle (envoi d'alertes vers PagerDuty, Slack, webhooks)
- Processus de support : s'abonner aux monitoring views et integrer avec des outils d'alerte externes

**Rollout controle :** Deploiement a un petit groupe pilote d'abord (1 equipe, 1 shift, 1 geographie), puis expansion (les trois sources). Daily "hypercare" stand-up avec le lead ops client ; revue d'incident si pannes ; update executif hebdomadaire centre sur l'impact (GPT).

#### Transition "FDE-operated" vers "client-operated"

La transition est **graduelle, pas un cutover brutal** (Claude, Perplexity).

**Semaines 10-12 -- retrait progressif :**
1. D'abord les FDE **arretent de construire de nouvelles features**
2. Puis ils **arretent de corriger les problemes de routine** (dirigeant les ingenieurs client pour le faire)
3. Finalement ils passent a des **check-ins consultatifs** plutot qu'un travail quotidien embarque (Claude)

La documentation Foundry implique que la transition concerne fondamentalement la propriete de : schedules, checks, et subscriptions d'alerte ; plus la gouvernance sur les branches et merges (GPT).

**Roles que le client devrait etablir (Perplexity, docs Foundry Adoption) :**

| Role | Responsabilite |
|------|---------------|
| **Program Lead** | Proprietaire principal du succes du Programme Foundry |
| **Data Lead** | Gere l'integration de donnees et la sante des pipelines |
| **Ontology Lead** | Possede la structure et l'evolution de l'ontologie |
| **Application Developers** | Construisent et maintiennent les apps Workshop |
| **Permissions Manager** | Gere les politiques de securite et le controle d'acces |

Palantir aide le client a etablir un **Centre d'Excellence (CoE)** pour que l'organisation puisse fonctionner de maniere autonome (Perplexity, Synthese-5).

#### Monitoring mis en place

| Monitoring | Outil | Seuil |
|-----------|-------|-------|
| Echecs de pipeline | Health checks + alertes automatiques | Alerte immediate sur tout echec de build |
| Fraicheur des donnees | Data Health | Alerte si donnees plus vieilles que le SLA (ex: >24h pour daily sync) |
| Qualite des donnees | Data expectations | Alerte si taux de null depasse seuil ou si nombre de lignes hors fourchette |
| Erreurs d'application | Monitoring views | Alerte sur erreurs d'action, timeouts |
| Adoption utilisateur | Metriques d'usage Workshop | Suivi DAU/WAU |

#### Support model post go-live

| Periode | Modele | Details |
|---------|--------|---------|
| Semaines 11-12 | FDE reste disponible on-site ou a distance pour escalades | (Claude) |
| 2-4 premieres semaines post go-live | Equipe FDE reste on-call | (Perplexity) |
| Mois 2-3 post-pilot | Transition vers customer success standard | Check-ins periodiques (Claude) |
| Continu | Apollo | Mises a jour plateforme avec roll-forward/roll-back (Claude, Perplexity) |
| Continu | Equipe Baseline | Gere les problemes operationnels fleet-wide (Perplexity) |

### 2.6.3 Mesure du Succes

#### KPIs utilises

| KPI | Description | Exemple de mesure |
|-----|-------------|------------------|
| **Time-to-decision** | Reduction du temps entre disponibilite des donnees et action operationnelle | "Generation de rapports reduite de 8h a 15 min" |
| **Adoption utilisateur** | DAU/WAU des applications Workshop vs cible | X utilisateurs actifs/jour |
| **Unification des donnees** | Nombre de sources precedemment en silo connectees | 5 sources unifiees |
| **Deplacement de processus** | Processus manuels (tableurs, emails) remplaces | 3 workflows Excel remplaces |
| **Gain d'efficacite** | Heures economisees par semaine par utilisateur | La metrique la plus persuasive |
| **Impact operationnel quantifie** | Economies de couts, reduction d'erreurs, amelioration du throughput | En $/temps |
| **Satisfaction utilisateur** | Feedback qualitatif des operateurs et executifs | NPS ou verbatims |
| **Time-to-value** | Rapidite du premier use case a livrer des resultats mesurables | Cible : 60-90 jours |

(Claude, Perplexity)

**Exemples concrets de case studies publics :**
- General Mills : **~$14M/an** (40k$/jour) (Perplexity)
- Fujitsu : **reduction de couts annuels de $9M en 3 mois** (Perplexity)
- AARP : premier prototype en **45 jours** (Perplexity)
- Trinity Rail : **$30M d'impact** en 3 mois (Synthese-5)
- Nebraska Medicine : **2,100% d'augmentation** de l'utilisation du salon de sortie (Synthese-5)
- Land O'Frost : planification production de **40h a 30 min** (Playbook-05)

#### Qui presente les resultats au client executive

Le **DS dirige** la presentation, avec le support FDE pour les questions techniques (les trois sources).

**Structure de la revue executive (Claude) :**

1. **Enonce du probleme** -- les defis operationnels identifies en decouverte
2. **Demonstration de la solution** -- walkthrough live des applications Workshop montrant les donnees integrees et workflows operationnels
3. **Metriques d'impact** -- resultats quantifies de la periode pilote
4. **Metriques d'adoption** -- utilisateurs actifs, workflows remplaces, sources unifiees
5. **Roadmap d'expansion** -- use cases, departements, sources supplementaires pour la prochaine phase
6. **Business case pour l'expansion** -- ROI projete de l'expansion de 1-3 use cases pilotes a 10-20+ use cases enterprise

#### Document "business case for expansion"

**Contenu (synthese des trois sources) :**

- Reaffirmation des requirements fonctionnels livres (GPT)
- Modele objet et diagramme de lifecycle (GPT)
- Couverture d'integration de donnees et lacunes restantes (GPT)
- Modele de securite (GPT)
- ROI quantifie des use cases pilotes (Perplexity)
- Narratif de l'adoption utilisateur et du changement de comportement (Perplexity)
- Roadmap de 3-5 use cases supplementaires identifies pendant la decouverte (Perplexity)
- Plan d'expansion de l'integration de donnees (sources, departements supplementaires) (Perplexity)
- Structure d'equipe proposee pour la phase Expand (Perplexity)
- Estimations cout/timeline pour la phase suivante (Perplexity)
- Metriques d'adoption et KPIs mesures (GPT)
- Roadmap reutilisant l'ontologie et les pipelines fondationnels pour debloquer des workflows supplementaires (GPT)

**Point de decision strategique (GPT) :** Decider si l'expansion est **horizontale** (plus de use cases dans le meme departement) ou **verticale** (meme workflow a l'echelle a travers sites/fonctions).

L'element le plus sous-estime (Claude) : quand la revue executive arrive, le cas d'expansion s'ecrit de lui-meme. Les utilisateurs sont deja dependants des applications, les donnees circulent deja, et la question passe de "devrions-nous continuer ?" a "a quelle vitesse pouvons-nous nous etendre ?"

---

## 2.7 Rythme Quotidien Type d'un FDE

### Phase Discovery (Semaines 1-3)

| Heure | Activite |
|-------|----------|
| 08:00 | Arrivee sur site, petit-dejeuner + emails, revue du statut de sync nocturne |
| 09:00 | **Daily standup equipe Palantir** (15 min) : bloqueurs, priorites, qui rencontre qui |
| 09:30 | **Entretien parties prenantes / marche sur le terrain** -- observer operateurs, poser questions, mapper processus |
| 11:00 | **Reunion de negociation d'acces donnees** avec IT / data owners |
| 12:00 | Dejeuner avec l'equipe client (le relationship building est essentiel) |
| 13:00 | **Travail pipeline** : configurer connecteurs, construire transforms initiales, debugger qualite |
| 15:00 | **Sync avec DS** sur priorisation use cases et politique des parties prenantes |
| 16:00 | **Sync interne Palantir** : mise a jour equipe compte, escalade bloqueurs |
| 17:00-19:00 | Continuation du travail technique (pipelines, esquisse ontologie) |

**Repartition du temps Discovery :** ~30% entretiens, ~30% observation, ~20% setup technique, ~20% coordination/planification

(Perplexity, base sur blog "Day in the Life" d'un DS et recit de Nabeel Qureshi)

### Phase Build (Semaines 3-8)

| Heure | Activite |
|-------|----------|
| 08:00 | **Verifier sante pipeline**, revue builds nocturnes |
| 09:00 | **Daily standup** (equipe Palantir + counterparts techniques client) |
| 09:30 | **Iteration ontologie / construction app Workshop** |
| 11:00 | **Demo client / session feedback** (30-60 min, 2-3x/semaine) |
| 12:00 | Dejeuner avec utilisateurs |
| 13:00 | **Implementer le feedback** de la session du matin |
| 14:00 | **Session config securite** avec equipe conformite client |
| 15:00 | **Design Action Type** -- modeliser decisions utilisateurs comme operations write-back |
| 16:00 | **Check-in executif hebdomadaire** (DS dirige) |
| 17:00-19:00 | Travail technique, hardening pipeline, testing |

**Repartition du temps Build :** ~50% coding/construction, ~25% meetings/demos/feedback, ~15% debugging, ~10% documentation

(Perplexity)

### Phase Handoff (Semaines 8-12)

| Heure | Activite |
|-------|----------|
| 09:00 | **Session formation** avec groupe utilisateurs (classroom ou deskside) |
| 10:30 | **Mentorat power user** : enseigner aux citizen developers a modifier les apps Workshop |
| 12:00 | Dejeuner |
| 13:00 | **Preparation go-live** : scheduling pipeline, dashboards monitoring, setup alerting |
| 14:00 | **Documentation et materiels de handoff** |
| 15:00 | **Preparation revue executive** avec DS |
| 16:00 | **Planification CoE** : definir roles, responsabilites, chemins d'escalade pour equipe client |

**Repartition du temps Handoff :** ~30% formation, ~25% documentation/handoff, ~20% hardening/monitoring, ~15% preparation revue executive, ~10% planification CoE

(Perplexity)

### Jours bureau/remote (Synthese-5)

- Ecriture de modifications mineures de code et configurations plateforme
- Revue de pull requests d'autres membres de l'equipe
- Recherche et planification de solutions client
- Communication par email ou visioconference avec les equipes internes
- Sessions de transfert de connaissances -- partage de mises a jour hebdomadaires "What I've Learned From Customers"
- Revues d'ingenierie et revues de code

---

## 2.8 Contradictions sur le Pilot

### [CONTRADICTION 1] Taille de l'equipe pilote

**(Claude)** : 1 Deployment Strategist + 2-4 Forward Deployed Engineers (total 3-5).
**(Perplexity)** : 4-5 personnes dont 2-3 FDSE + 1-2 DS.
**Resolution** : Les deux convergent sur 3-5 personnes, mais divergent sur le ratio DS/FDE. La composition varie probablement selon la complexite politique (plus de DS) ou technique (plus de FDE) du deploiement.

### [CONTRADICTION 2] Nombre d'entretiens semaines 1-2

**(Claude)** : 10-30 entretiens dans les deux premieres semaines.
**(GPT)** : La documentation Palantir ne prescrit pas de nombre precis.
**(Perplexity)** : Pas de chiffre precis.
**Resolution** : 10-30 est une estimation raisonnable basee sur la pratique, pas un chiffre officiel. Le nombre reel varie enormement selon la taille de l'organisation.

### [CONTRADICTION 3] Repartition observation / entretiens

**(Claude)** : 60% entretiens / 40% observation.
**(Perplexity)** : En manufacturing, les FDE passent les 1-2 premieres semaines "principalement a observer" avec 20-30% de configuration systeme.
**Resolution** : La repartition varie selon le contexte. Les environnements physiques (usine, hopital) favorisent l'observation ; les environnements digitaux (finance, services) favorisent les entretiens.

### [CONTRADICTION 4] Role de designer UI

**(GPT)** : Mentionne des "Product Designers" dans les deploiements.
**(Perplexity)** : Pas de role dedie "UI designer" -- le FDE construit l'UI.
**Resolution** : Possible evolution du modele. Les deploiements historiques etaient purement FDE. Les deploiements plus recents ou plus importants peuvent inclure un designer, mais ce n'est pas standard.

### [CONTRADICTION 5] Heures de formation

**(Claude)** : Power users 8-16h, standard 2-4h.
**(Perplexity)** : Power users 16-40h, standard 4-8h.
**Resolution** : Perplexity donne des fourchettes plus larges et plus elevees. La duree reelle depend de la complexite de l'ontologie et du niveau technique de base des utilisateurs.

### [CONTRADICTION 6] Testing pendant le pilot

**(Perplexity)** : "Le testing formel d'unites varie selon le FDE -- la culture valorise la vitesse sur la couverture de tests."
**(GPT)** : Met l'accent sur le testing formel comme partie integrante du processus.
**Resolution** : La documentation officielle prescrit des tests ; la realite terrain les sacrifie souvent au profit de la vitesse. Nabeel Qureshi confirme : "dette technique et workarounds hacky" pendant le pilot. Le hardening intervient en semaines 9-10.

### [CONTRADICTION 7] Mecanisme de writeback

**(Claude)** : Edits dataset append-only avec reconciliation par pipeline.
**(Perplexity)** : Writeback dataset avec deux modes de permission.
**Resolution** : Descriptions complementaires du meme mecanisme vu sous deux angles differents (architecture interne vs. configuration utilisateur).

### [CONTRADICTION 8] Taux de conversion bootcamp

**(Synthese-5, section A.12)** : "70% convertissent en contrats payes dans un trimestre, avec une taille de deal moyenne depassant $1M."
**(Playbook-05, correction #5)** : "~22% de taux de conversion" (estimation analystes Morgan Stanley, Wedbush, RBC).
**Resolution** : Le chiffre de 70% est une citation ancienne (pre-2024) probablement basee sur des bootcamps tres cibles. Le chiffre de 22% est l'estimation analystes plus recente et plus conservative, tenant compte de l'industrialisation massive (1,300+ bootcamps). Le vrai chiffre est probablement entre les deux selon la qualite du ciblage.

### [CONTRADICTION 9] Nombre de connecteurs

**(Perplexity/Claude dans synthese-2)** : 200+ connecteurs out-of-the-box.
**(Synthese-5, section C.7)** : 400+ connecteurs.
**Resolution** : Le nombre a probablement augmente avec le temps. Le chiffre de 400+ est plus recent et inclut probablement des connecteurs additionnels via marketplace et partenaires.

---

> **Nota :** Cette reconstruction est basee entierement sur des sources publiques : blog posts d'anciens employes (Nabeel Qureshi, Barry McCardel, Ted Mabrey, Sarah Constantin), documentation officielle Foundry, guides d'implementation partenaires, descriptions de postes, depots de brevets, presentations AIPCon, et earnings calls. Palantir ne publie pas ses playbooks de deploiement internes. Le processus reel est probablement plus fluide et improvisationnel qu'aucune decomposition structuree ne peut capturer. Comme Ted Mabrey le note : "there are no maxims that, if you backtested them, wouldn't violate the path one of our most important products took" (Perplexity).

---

# PARTIE 3 -- EXPAND & SCALE : RENDRE LE CLIENT CAPTIF PUIS AUTONOME

> **Contexte** : cette partie couvre les annees 1 a 10+ du cycle de vie client Palantir. Elle detaille comment un pilote a $100-250K ACV se transforme en contrat enterprise a $5-20M+, comment les FDEs se retirent progressivement, et comment le client devient simultanement plus autonome dans l'usage et plus captif dans l'infrastructure. Chaque mecanisme est documente avec les sources disponibles et les contradictions identifiees.

---

## 3.1 Expand Phase (Annee 1-3, $250K -> $1-5M ACV)

### 3.1.1 Identification des Declencheurs d'Expansion

La phase Expand ne se declenche pas par hasard. Palantir a formalise trois mecanismes concrets par lesquels les FDEs identifient systematiquement les opportunites d'expansion au sein d'un compte existant.

**Mecanisme 1 : Decouverte de problemes par proximite**

Les FDEs, physiquement presents dans les bureaux du client 2 a 4 jours par semaine, observent les processus reels -- pas les SOPs officiels, mais le travail tel qu'il se fait reellement. Cette immersion revele les workarounds Excel, les processus manuels, et les points de douleur partages par les departements adjacents. Citation d'un ancien FDE sur Reddit :

> "You solve one problem, and then the person in the next cubicle says 'can you do that for my team too?'"
> -- Ancien FDE Palantir (source : Reddit, via Claude)

**Mecanisme 2 : Cartographie des parties prenantes**

Les FDEs suivent systematiquement qui assiste aux demos, qui transfere les resultats a des collegues, qui pose des questions lors des sessions. Ils construisent un organigramme informel de champions potentiels et de vecteurs d'expansion. Cette cartographie utilise les principes du livre *Impro* de Keith Johnstone (donne a chaque nouvelle recrue le Jour 1) : lecture des dynamiques de statut, identification des decideurs reels vs. titulaires, reperage des resistants.

**Mecanisme 3 : Analytique d'usage plateforme**

La plateforme elle-meme genere des signaux d'expansion. Une forte adoption dans un departement signale la maturite pour l'expansion. Des dashboards partages entre departements revelent une traction organique -- quand un departement non encore deploye consulte regulierement les outputs du departement deploye, c'est un signal d'expansion.

**Prioritisation du prochain departement** (Perplexity) :

La selection du departement suivant repose sur trois criteres :
1. **Adjacence des donnees** -- quels departements partagent des entites avec le deploiement actuel ? Si le deploiement initial est en Supply Chain avec des Object Types `Supplier`, `Part`, `Purchase Order`, le departement Finance partage naturellement l'entite `Supplier` et `Purchase Order`
2. **Impact metier** -- quel workflow ameliore delivre le ROI mesurable le plus rapidement ?
3. **Disponibilite d'un sponsor executif** -- sans sponsor, pas d'expansion

Palantir confirme dans ses filings SEC que les decisions d'expansion dependent en partie de "la capacite de nos forward-deployed engineers a aider nos clients a identifier de nouveaux cas d'usage [et] a moderniser leurs architectures de donnees" (GPT, source : S-1 filing).

**Le "Use Case Backlog" : process formel**

Palantir maintient ce que les inities appellent un **"problem backlog"** ou **"opportunity pipeline"** pour chaque compte -- une liste priorisee de cas d'usage potentiels maintenue collaborativement par le FDE et son Deployment Strategist (Claude). La priorisation suit quatre criteres :
1. Valeur metier estimee
2. Faisabilite technique (les donnees sont-elles disponibles ?)
3. Force du sponsorship executif
4. Rapidite a des resultats demonstrables

La cadence typique est d'identifier **5 a 15 cas d'usage potentiels**, puis de reduire a **2 a 3 quick wins** qui prouvent la valeur inter-departementale en quelques semaines (Claude).

**Gouvernance formelle du backlog (GPT, source : documentation Foundry Phase 2)** :

| Cadence | Contenu |
|---|---|
| **Mensuelle** -- Revue developpement et roadmap | Alignement des livrables, discussion des ameliorations aux cas d'usage existants, identification et priorisation des opportunites pour de nouveaux cas d'usage, evaluation des business cases |
| **Trimestrielle** -- SteerCo | Evaluation de la direction strategique, du perimetre de la plateforme, des couts. Revue des cas d'usage actifs, en developpement et prospectifs avec couts et valeur associes |
| **Mensuelle** -- Revue de creation de projet | Les utilisateurs soumettent de nouvelles demandes via un portail de requetes construit dans Foundry ; les demandes sont approuvees ou refusees via un workflow inbox |

C'est ce mecanisme d'**"intake scalable"** qui transforme des idees dispersees en un pipeline d'expansion controle (GPT).

---

### 3.1.2 "Build with AIP" Bootcamps pour Clients Existants

Les AIP Bootcamps ne servent pas uniquement a l'acquisition de nouveaux clients. Pour les clients existants, Palantir organise des bootcamps specifiques dits "Build with AIP" dont l'objectif et le format different du bootcamp initial.

**Difference avec le bootcamp initial** (Perplexity) :

| Dimension | Bootcamp initial (Acquire) | Bootcamp existant (Expand) |
|---|---|---|
| **Objectif** | Prouver la valeur de zero | Etendre a de nouveaux departements et cas d'usage |
| **Participants** | 5-20 stakeholders, souvent sceptiques | 20-50 participants, incluant des utilisateurs existants convaincus |
| **Connaissance prealable** | Aucune | Les participants comprennent deja les bases Foundry/AIP |
| **Focus** | Premiers prototypes sur donnees client | Construction d'intuition AIP au-dela des interactions chatbot, identification de nouveaux cas d'usage operationnels |
| **Donnees** | Coupes statiques pre-preparees | Ontologie existante + nouvelles sources departementales |
| **Sortie** | 1-3 prototypes fonctionnels | 5-10+ cas d'usage priorises, dont 1-3 prototypes sur nouveaux departements |

**Preparation pre-bootcamp** (Perplexity) : 1 a 2 semaines avant, le client confirme les roles des participants (business owners, utilisateurs, parties prenantes IT), fournit des coupes de donnees statiques pertinentes a leurs workflows, et l'equipe Palantir pre-construit autant que possible sur la base des discussions de haut niveau.

**Participants recommandes** (Claude) : 20 a 50 participants cote client -- sponsors executifs (VP/C-level pour ouverture et cloture), chefs de departement de 3 a 8 fonctions, analystes metier connaissant les points de douleur operationnels, et leads IT/data pour evaluer la faisabilite.

**Structure en 3 phases** (Perplexity) :
- Phase 1 : introductions et demos produit ("experience the art of the possible")
- Phase 2 : hands-on-keyboard ou les participants travaillent directement avec les ingenieurs Palantir
- Phase 3 : showcase et evaluation ou les apprentissages sont partages et les prochaines etapes alignees

---

### 3.1.3 L'Exercice des "100 Cas d'Usage" : Methode de Facilitation

Le chiffre souvent cite de "100 cas d'usage identifies" est atteint via un brainstorming structure a haute velocite.

**Methode detaillee** (Claude, Perplexity) :

**Etape 1 -- Brainstorming par departement (60-90 min)**

Les participants sont groupes par departement (operations, supply chain, finance, RH, conformite, service client). Chaque personne contribue individuellement **3 a 5 points de douleur** sur des post-its ou un outil collaboratif. Avec 30 a 50 participants contribuant chacun plusieurs idees, atteindre 100+ est arithmetiquement direct (6 departements x 8 personnes x 4 idees = 192 idees brutes).

**Etape 2 -- Structuration par canevas**

Les facilitateurs Palantir fournissent un **template de canevas de cas d'usage** pour chaque idee retenue :
- Le probleme
- Les donnees impliquees
- Le processus actuel (comment est-ce fait aujourd'hui ?)
- Le resultat souhaite
- L'impact metier estime ($, heures, risque)

**Etape 3 -- Triage et priorisation (2-3h)**

Les 100+ idees brutes sont filtrees a **5 a 10 cas d'usage hautement prioritaires et techniquement faisables**.

**Etape 4 -- Prototypage en temps reel**

Les ingenieurs Palantir construisent des **prototypes fonctionnels de 1 a 3 cas d'usage** en temps reel pendant le bootcamp, creant le "aha moment" qui convertit en expansion payante (Claude).

[CONTRADICTION] GPT indique que "les materiaux publics de Palantir ne decrivent pas une seule methode canonique de facilitation (par exemple des formats specifiques de post-it) pour generer 100 cas d'usage dans une session" et que le chiffre de 100 provient d'un entonnoir d'ideation structure dont l'output est ensuite trie via la revue de roadmap mensuelle et le SteerCo trimestriel. Claude affirme avec assurance que les participants font un "exercice sticky-note/whiteboard" avec un canevas template, et que Palantir construit des prototypes de 1 a 3 cas d'usage en temps reel. La documentation officielle de Palantir mentionne le processus mais pas les formats specifiques de facilitation ; les descriptions detaillees de Claude semblent provenir de sources secondaires (temoignages, analyses d'analystes).

---

### 3.1.4 Expansion Cross-Departement : Croissance de l'Ontologie

#### Comment l'ontologie grandit de 1 a 3-5 departements

Un deploiement initial commence avec **5 a 20 Object Types** pertinents a un domaine metier unique. Exemple pour une supply chain :

```
Object Types initiaux : Part, Supplier, Purchase Order, Shipment, Warehouse
Link Types : Supplier --fournit--> Part, Purchase Order --contient--> Part, Shipment --expedie_depuis--> Warehouse
```

La premiere expansion identifie des **entites partagees** entre departements (Claude) :
- L'objet `Customer` dans Sales se connecte a `Account` dans Finance
- `Employee` dans HR se lie a `Operator` dans Manufacturing
- `Supplier` dans Procurement se lie a `Vendor` dans Finance

Ces **Link Types inter-departements** creent le tissu connectif qui rend l'ontologie exponentiellement plus precieuse.

**Echelle typique par stade** :

| Stade | Object Types | Link Types (approx.) | Departements |
|---|---|---|---|
| Pilote | 5-20 | 10-40 | 1 |
| Expand precoce | 20-60 | 40-120 | 2-3 |
| Expand mature | 60-150 | 120-400 | 3-5 |
| Enterprise-wide | 100-500+ | 200-1500+ | 5-10+ |
| Tres grands deploiements (US Army, bp) | 500-1000+ | 1000-3000+ | Organisation entiere |

(Claude, Perplexity)

#### Defis techniques de l'expansion cross-departement

**Defi 1 : Definitions d'entites conflictuelles**

Le departement A definit "Client" comme toute personne ayant fait un achat ; le departement B le definit comme toute personne ayant un contrat actif. C'est exactement le probleme de "bounded context" du Domain-Driven Design (DDD).

L'approche Palantir permet de multiples Object Types representant des concepts qui se chevauchent, lies par des relations, plutot que de forcer une unification prematuree (Claude). On peut avoir `Sales_Customer` et `Contract_Customer` lies par un Link Type `represents_same_entity`, avec resolution progressive.

**Defi 2 : Duplication de donnees entre systemes -- Entity Resolution**

Quand "le meme client existe dans le CRM Sales et l'ERP Finance avec des IDs differents", Palantir deploie ses capacites d'**Entity Resolution** :

**Approche Palantir (Perplexity, brevet US)** -- pipeline multi-etapes :
1. **Blocage** : classification des enregistrements en groupes par features (localisation, nom, industrie) pour reduire l'espace de comparaison
2. **Comparaison** : matching au niveau du champ avec ML, incluant des encodages semantiques bases sur des transformers
3. **Clustering** : selection des correspondances finales et resolution des enregistrements vers des entites

Le systeme incorpore des **boucles de feedback utilisateur** ou les analystes peuvent confirmer ou rejeter les correspondances, et ce feedback entraine les modeles ML pour une meilleure precision (Perplexity).

Au niveau praticien, Palantir publie des exemples de code de fuzzy-matching (metriques de similarite Levenshtein, Jaro-Winkler) dans Pipeline Builder (GPT). L'approche inclut des pipelines d'entity resolution configurables ou chaque etape utilise des methodes interchangeables -- le tout gouverne par des regles d'ontologie incluant controle de revision, controle d'acces, versioning et tracking de provenance (Perplexity).

**Approche "Golden Record"** : un Object Type maitre qui agrege a partir de multiples sources, utilisant le linking d'objets plutot que la fusion physique (Claude). Par exemple :

```
Master_Customer (golden record)
  |-- linked to --> CRM_Customer_Record (source : Salesforce)
  |-- linked to --> ERP_Account (source : SAP)
  |-- linked to --> Support_Contact (source : Zendesk)
```

**Implication technique critique** (GPT) : la croissance de l'ontologie est contrainte par la qualite de l'identite. Etendre a de nouveaux departements sans resoudre l'identite cree une ontologie fragile qui ne peut pas supporter de maniere sure les workflows inter-domaines. L'existence d'une ligne de produits Entity Resolution dediee chez Palantir suggere que cette resolution doit etre traitee comme une capacite programmatique, pas un correctif unique.

**Defi 3 : Frontieres de securite entre departements**

Les controles d'acces s'appliquent a quatre niveaux (GPT, Claude) :
1. **Niveau projet** -- isolation des workspaces
2. **Niveau dataset** -- qui peut voir quelles donnees sources
3. **Niveau Object Type** -- qui peut voir quels types d'entites
4. **Niveau objet individuel** -- RLS (Row-Level Security), par exemple "un manager ne voit que les employes de son departement"

Plus des **markings** (controle d'acces obligatoire) et du **RBAC** (controle base sur les roles). Le role de Permissions Manager inclut les structures de groupes, les integrations SAML/identite, et a grande echelle, les vues restreintes et les structures de permissions en collaboration avec la conformite (GPT).

#### Gouvernance de l'Ontologie : qui approuve les nouveaux Object Types

**Modele a deux couches** (Perplexity) :

| Couche | Gouvernance | Vitesse |
|---|---|---|
| **Objets specifiques a un projet** | Crees rapidement par l'equipe projet, utilises exclusivement pour leur scope | Rapide -- jours |
| **Objets "core" de l'ontologie** | Processus de gouvernance rigoureux, evaluation par l'Ontology Manager | Lent -- semaines, revue formelle |

Ce modele federe permet aux departements d'iterer vite tandis qu'un steward central d'ontologie maintient la source de verite canonique.

**Ontology Managers** (GPT) : explicitement responsables de :
- Gerer le backlog de l'ontologie
- Prioriser les demandes de changement
- Evaluer toutes les demandes de nouveaux objets et changements en vue de l'impact plus large et de l'evolution a long terme

**Application Approvals** (GPT) : l'application Approvals de Palantir gere "la demande, l'approbation et l'invocation" de changements. Elle liste explicitement "Review ontology proposals" comme workflow exemple. Les approbations persistent comme un journal d'audit des decisions passees.

**Cadence de gouvernance pour l'ontologie mature** :
- Revues de gouvernance de l'ontologie **bimensuelles ou mensuelles** (Claude, Perplexity)
- Revues strategiques **trimestrielles** (Claude)

---

### 3.1.5 Centre d'Excellence (CoE)

#### Timing exact de formation

Le CoE se forme typiquement **6 a 18 mois** apres le debut du deploiement (Claude), ou **6 a 12 mois** selon Perplexity. GPT est moins specifique sur le timing, liant la formation au franchissement du seuil "multi-use-case, multi-domain, hundreds-of-users" (Phase 3 de Foundry) plutot qu'a un nombre de mois specifique.

[CONTRADICTION] Claude indique 6-18 mois ; Perplexity indique 6-12 mois. En pratique, le seuil de declenchement est approximativement **50 a 200+ utilisateurs actifs** et une valeur prouvee a travers 2-3 cas d'usage (Claude).

**Qui initie la formation du CoE** : l'initiative est collaborative -- le Deployment Strategist de Palantir la recommande dans le cadre du playbook d'expansion, tandis que le sponsor executif du client la porte en interne (Claude). L'equipe programme Foundry de Palantir est decrite comme "a startup within your organization" (GPT).

**Point critique** (GPT, Phase 3 Foundry) : le CoE devrait etre une **rotation plutot qu'une equipe dediee**, utilisee pour combler les lacunes de competences et booster les initiatives sans posseder la responsabilite du domaine a long terme.

#### Curriculum de formation par role

| Role | Description | Formation | Duree estimee |
|---|---|---|---|
| **Platform Owner / Head of Platform** | Strategie globale, roadmaps, budget, securite, administration des permissions, gouvernance, conformite, performance, allocation des couts. Construit documentation et formations sur les best practices. | 1-2 jours fondamentaux Foundry + engagement strategique continu (Claude) ; ~20-40 heures de preparation (Perplexity) | 20-40h |
| **Ontology Steward / Ontology Manager** | Design ontologie, gouvernance, qualite des donnees, gestion du backlog ontologie, evaluation des requetes de nouveaux Object Types. | 2-3 jours design ontologie (Claude) | 16-24h |
| **Data Engineers (equipe "South")** | Developpement de pipelines, integration de donnees, agents de connexion, competences SQL/Python/Spark. Possedent l'ingestion, la sante des pipelines, les SOPs d'escalade et les librairies partagees. | 3-5 jours Pipeline Builder, Code Workbook, code repos (Claude) ; ~80-100 heures incluant Python + SQL + Spark (Perplexity) | 80-100h |
| **Application Developers (equipe "North")** | Construction d'applications Workshop, configuration AIP, Ontology Functions (TypeScript/Python). | 2-4 jours track Workshop (Claude) ; ~40-60 heures preparation (Perplexity) | 40-60h |
| **Permissions Manager** | Configuration RBAC, markings de securite, structures de groupes, integration identite (SAML), vues restreintes a grande echelle. | 1-2 jours formation admin (Claude) | 8-16h |
| **Training Lead / Education Expert** | Onboarding utilisateurs, documentation, alignement de la formation sur la priorisation des cas d'usage, mecanismes "train-the-trainer". | Variable | Variable |

Le CoE peut aussi embarquer des data scientists, des experts pipeline, des developpeurs front-end et des chefs de projet la ou c'est necessaire pour accelerer des initiatives specifiques (GPT).

#### Certifications formelles Palantir

**Programme de certification lance en decembre 2025** (Perplexity) -- premiere fois que l'entreprise ouvre des parcours d'apprentissage standardises pour le marche plus large en dehors des FDEs.

Certifications disponibles :
- **Foundry Aware Certification** (entry-level)
- **Application Developer Certification**
- **Data Engineer Certification**
- **Foundry Developer, Foundry Analyst, AIP Developer** (Claude)

Pas de certification separee encore pour Ontology Steward ou Permissions Manager (Perplexity).

**Portail d'apprentissage** : learn.palantir.com -- cours gratuits ; examens de certification payants, accessibles via un point de contact Palantir ou un administrateur Foundry (GPT). Des guides d'etude pour les examens sont publies sur le meme portail. Dans Foundry, une application Training fait surface le contenu d'apprentissage curate et renvoie vers Palantir Learn (GPT).

**Prix de formation (UK G-Cloud)** (Perplexity) :

| Formation | Prix (GBP) |
|---|---|
| Bootcamp Training | 1 100 GBP/personne |
| Workshop Training | 1 750 GBP/personne |
| Integrator Training | 2 100 GBP/personne |
| Developer Training | 1 000 GBP/personne |
| Developer & Integrator combine | 2 700 GBP/personne |

#### Cadence de gouvernance du CoE

| Frequence | Contenu |
|---|---|
| **Quotidienne** | Standups use-case pour l'execution de livraison (GPT) |
| **Hebdomadaire** | Standups tactiques sur le statut de livraison et les blockers (Claude) |
| **Bimensuelle** | Sprint planning pour l'execution de livraison (GPT) |
| **Bimensuelle/Mensuelle** | Revues de gouvernance ontologie (Claude, Perplexity) |
| **Mensuelle** | Comites directeurs parties prenantes sur les priorites et le ROI (Claude) / Revue developpement et roadmap (GPT) |
| **Trimestrielle** | Revue executive -- roadmap strategique et planification d'expansion (Claude) / SteerCo (GPT) |

#### Ecosysteme tiers de formation et support

| Partenaire | Role | Details |
|---|---|---|
| **Accenture Palantir Business Group** | Deploiement et support | Lance decembre 2025, supporte par **2 000+ professionnels Accenture competents Palantir** et des FDEs Palantir dedies (Perplexity) |
| **Ontologize** | Formation CoE | Fondee par d'anciens employes Palantir, existe specifiquement pour "construire des equipes d'experts Foundry chez les clients et partenaires Palantir" (Perplexity) |
| **Multiverse (NHS)** | Formation specifique NHS | Programme d'apprentissage formant le personnel NHS specifiquement sur les competences Foundry/FDP (Perplexity) |
| **CodeStrap** | Apprentissage open-source | Curriculum open-source Foundry Foundations sur GitHub pour l'apprentissage auto-dirige (Perplexity) |
| **Deloitte** | Implementation et advisory | Partenaire d'implementation (CONFIRMED) |
| **Booz Allen Hamilton** | Defense/gouvernement | Partenaire specifique defense (CONFIRMED) |
| **IBM** | Integration enterprise | Partenaire technologique (CONFIRMED) |

**Palantir for Builders** : free developer stack disponible sur build.palantir.com (Perplexity) -- environnement self-service pour developpeurs individuels.

**Communaute developpeur** : community.palantir.com -- forum public pour utilisateurs et early adopters annonce a AIPCon comme la **Palantir Developer Community** (GPT, Claude, Perplexity).

---

### 3.1.6 Cultivation des Champions

#### Systeme de champions multi-niveaux

Palantir cultive des champions a **quatre niveaux simultanement** (Claude) :

| Niveau | Role | Profil type | Valeur pour Palantir |
|---|---|---|---|
| **1. Champion utilisateur final** | Utilise la plateforme quotidiennement | Travailleur de premiere ligne, analyste | Resiste a toute tentative de suppression de la plateforme |
| **2. Champion operationnel** | Manage des equipes qui utilisent la plateforme | Manager intermediaire | Porte la valeur operationnelle dans les reunions |
| **3. Champion technique** | Construit sur la plateforme | Data engineer, developer | Approfondit l'ancrage technique |
| **4. Champion executif** | Sponsorise le budget | C-level, VP | Securise le financement de l'expansion |

Les champions peuvent etre "assignes top-down ou naitre organiquement bottoms-up". Leur role est de "piloter le succes initial, car les victoires orientees metier sont essentielles pour obtenir un soutien continu et repousser les detracteurs" (Perplexity).

#### Playbook systematique de cultivation

**Mecanisme 1 : Bootcamps AIP comme fabriques de champions**

Les participants construisent de vraies solutions sur leurs propres donnees et sortent avec un MVP qu'ils peuvent demonstrer au leadership. Cela cree des champions naturels qui ont un **sentiment de propriete personnelle** sur un cas d'usage AI fonctionnel (Perplexity). Le participant ne se contente pas d'observer -- il co-construit. La psychologie est celle de l'IKEA effect : les gens valorisent davantage ce qu'ils ont contribue a creer.

**Mecanisme 2 : Ammunition ROI**

- Des **dashboards integres** montrant les heures economisees, les couts evites et les temps de cycle reduits sont construits directement dans les deploiements (Claude)
- Les FDEs et DS preparent des **materiaux de briefing executif** que les champions peuvent utiliser dans les reunions budgetaires (Claude)
- Les revues de roadmap incluent explicitement l'evaluation de business cases pour la valeur des cas d'usage (GPT) -- l'"ammunition ROI" est produite en continu dans le cadre de la gouvernance, pas retroactivement au moment du renouvellement
- **Exemple concret** : Lear Corporation pouvait pointer vers "30 M$+ d'economies pendant le S1 2025" directement attribuables au programme IDEA propulse par Palantir (Perplexity)
- **Quarterly Business Reviews** formelles presentant le ROI aux cotes des roadmaps d'expansion (Claude)

**Mecanisme 3 : Evenements et communaute**

| Evenement | Format | Objectif |
|---|---|---|
| **AIPCon** (conference annuelle, rebrandee depuis DevCon en 2023) | Presentations clients sur scene | Visibilite pour les champions, validation publique (Claude, GPT, Perplexity) |
| **FoundryCon** | Conference flagship client | Deep-dives techniques et retours d'experience (GPT) |
| **Diners executifs et advisory boards** | Cercle restreint, C-level | Donner aux clients seniors une influence sur la direction produit (Claude) |
| **User groups regionaux** | Ex. Boston Palantir User Group | Communaute locale, partage de best practices (GPT) |
| **Sessions "Double Click"** | Deep-dive technique | Approfondissement de sujets specifiques (Claude) |
| **Canaux Slack internes, lunch-and-learns, "show and tell"** | Informel, recurrent | Creer une communaute plutot qu'une dependance single-threaded (Claude) |
| **DevCon** (depuis 2024) | Conference developpeurs, hands-on | 150 builders, 2 jours de lancements produit et competition |

#### "Champion Redundancy" -- Prevenir la dependance a un individu

La redondance des champions est atteinte structurellement (Claude) :

1. **Le CoE distribue les connaissances** a travers **5 a 50+ personnes** -- aucun individu ne detient la totalite du savoir plateforme
2. **Expansion a 3-5 departements** avec des centaines d'utilisateurs actifs signifie que la plateforme devient "trop critique pour etre retiree" independamment du depart de tout individu
3. **L'ontologie elle-meme devient le champion** -- c'est un actif institutionnel, pas personnel (Perplexity)
4. Le **partenariat Accenture** embarque des professionnels qualifies Palantir au sein des organisations clientes, ajoutant une couche de redondance externe (Perplexity)

**Que se passe-t-il quand un champion part** :

Les filings SEC de Palantir reconnaissent que le risque lie aux relations cles est materiel. Toute la strategie d'expansion est concue pour depasser cette vulnerabilite aussi vite que possible (Claude). Si le champion executif part avant que la plateforme ne soit ancree dans 3+ departements, le risque de churn augmente significativement. La reponse de Palantir :
- Engagement immediat au niveau C-level par le DS et l'AE
- Demonstration du ROI accumule au successeur
- Acceleration de l'expansion pour augmenter les couts de switching

---

### 3.1.7 Mecanique Commerciale de l'Expansion

#### Structure de pricing pour l'expansion

Le modele de prix Palantir n'est pas un simple "par utilisateur". Il combine plusieurs dimensions (Claude, Perplexity) :

**Modele par cas d'usage/solution (UK G-Cloud)** (Perplexity) :

Le "level" est determine par un composite de : complexite des sources de donnees, exigences d'output analytique, echelle de la base d'utilisateurs, et exigences d'operationnalisation.

| Niveau | Prix (GBP/an) | Stade typique |
|---|---|---|
| Level 0 | 250 000 GBP | Pilote / cas d'usage unique |
| Level 1 | 500 000 GBP | Expand precoce, 1-2 departements |
| Level 2 | 1 000 000 GBP | Multi-departements, complexite moderee |
| Level 3 | 2 000 000 GBP | Cross-fonctionnel, analytiques multiples |
| Level 4 | 5 000 000 GBP | Operationnel enterprise-wide |
| Level 5 | 10 000 000 GBP | Digital twin a grande echelle |
| Level 6-15 | 20 M GBP - 1 Md GBP | Plateforme enterprise complete / echelle nationale |

**Modele de licence plateforme** (Claude) :

Le prix evolue avec :
- Le volume de donnees traitees
- Le nombre de cas d'usage/applications
- Le nombre d'utilisateurs aux tiers superieurs
- Le modele de deploiement (cloud vs. on-premise vs. air-gapped)

**Licence par core** : 66 000 GBP/core serveur/an avec support annuel a 21 500 GBP/core (Perplexity).

**Organisation License** (enterprise-wide) : 3 000 000 GBP/an pour utilisateurs illimites dans l'organisation (G-Cloud, CONFIRMED).

#### Prix "land" vs prix "expand"

Les deals initiaux "land" sont souvent **subventionnes ou rabaises** pour prouver la valeur, tandis que les contrats d'expansion capturent les tarifs pleins -- c'est la que l'expansion de marge se produit (Claude).

Le modele par cas d'usage est **additif** -- chaque nouveau cas d'usage est une licence separee au niveau approprie. Un client commencant au Level 0 (250K GBP) qui ajoute trois cas d'usage ne passe pas simplement au Level 3 ; il peut acheter Level 0 + Level 1 + Level 1 (1,25M GBP total) ou consolider en un accord enterprise Level 2/3 (Perplexity).

#### Termes pre-negocies et structure contractuelle

| Dimension | Detail |
|---|---|
| **Duree de contrat** | 3-5 ans gouvernement, 1-3 ans commercial (Claude). Duree moyenne : 3-4 ans (Perplexity) |
| **Structure IDIQ (gouvernement)** | Plafonds 5-10x le montant initial (Claude). Ex. : US Army 10 Md$ sur 10 ans |
| **Escalators annuels** | Typiquement 3-5% integres (Claude) |
| **Engagements minimaux de consommation** | Inclus dans les contrats (Claude) |
| **Clauses de resiliation** | Contrats aussi courts qu'un an ; beaucoup permettent la resiliation avec preavis de 3 a 6 mois (GPT) |
| **Provisions d'expansion** | Le contrat initial inclut souvent des ramps liees a des jalons verifies et des declencheurs d'expansion (Perplexity) |
| **Auto-renew vs negociation** | Variable selon le contrat |
| **Consommation AWS Marketplace** | Palantir a evolue vers un prix base sur la consommation pour certaines offres (Perplexity) |

#### Role AE vs DS dans l'expansion

| Role | Responsabilite dans l'expansion |
|---|---|
| **Account Executive (AE)** | Negocie les termes commerciaux, developpe les profils clients, met en oeuvre les strategies de croissance, securise les contrats (Perplexity) |
| **Deployment Strategist (DS)** | Pilote la strategie de compte, gere les relations parties prenantes, identifie les opportunites d'expansion, "possede le plan de compte et la strategie d'expansion" (Claude, fiches de poste Palantir) |
| **FDE** | Execute techniquement, construit les preuves de valeur pour les nouveaux departements |

Le DS est le pivot : il detecte l'opportunite sur le terrain, construit le business case avec le champion client, et le transmet a l'AE pour la negociation commerciale.

---

## 3.2 Scale Phase (Annee 3+, $5M-20M+ ACV)

### 3.2.1 Graduation des FDEs -- "The Withdrawal"

#### Process exact de retrait

Le retrait est **progressif, pas un basculement dur** (Claude, Perplexity). Palantir appelle la phase finale "Hypergrowth" (Phase 4 de Foundry) ou le programme devrait etre "largely self-sufficient" (GPT).

**Timeline detaillee du retrait** :

| Phase | Periode | Role FDE | Part client du dev | Presence |
|---|---|---|---|---|
| **Phase 1 -- Immersion** | Mois 0-12 | FDEs fortement embarques, construction ontologie initiale, pipelines, premieres applications | FDE fait 80-90% de la construction (Claude) | 2-5 FDEs on-site, 2-4 jours/semaine |
| **Phase 2 -- Co-developpement** | Mois 12-24 | Transfert de connaissances commence, FDEs co-construisent avec l'equipe client, CoE se forme, programmes de formation commencent | Client fait 30-50% | 2-3 FDEs, mix on-site/remote |
| **Phase 3 -- Autonomie guidee** | Mois 24-36 | FDEs passent en role conseil/oversight | Client gere 50-70% du developpement (Perplexity) | 1-2 FDEs, principalement remote |
| **Phase 4 -- Self-suffisance** | Mois 36+ | Presence FDE reduite a des check-ins periodiques, revues trimestrielles, ou on-call pour projets complexes | Client construit 70-85% des nouvelles applications (Claude) | 1-2 FDEs couvrant plusieurs comptes, a distance (Claude) |
| **Annee 5+** | -- | Implication FDE principalement strategique : revues d'architecture trimestrielles, introductions de nouveaux produits (rollouts AIP), support pour les initiatives majeures | Client construit 85-90%+ | Engagement ponctuel |

En Phase 4, Palantir declare que les ingenieurs Palantir peuvent etre mobilises pour des "use case boosts and other advisory services", mais les operations quotidiennes et les initiatives de construction sont gerees entierement par les equipes internes (GPT).

#### Courbes de graduation

**Commercial (0-36 mois)** :

| Phase | Timeline | Description |
|---|---|---|
| Heavy FDE | 0-6 mois | FDEs menent tout le developpement, construisent l'ontologie initiale |
| Co-Development | 6-18 mois | Equipes client commencent a construire aux cotes des FDEs |
| Guided Autonomy | 18-36 mois | Equipes client construisent la majorite des applications independamment |
| Self-Sufficient | 36+ mois | Client pleinement autonome |

(ESTIMATED)

**Gouvernement (0-48 mois)** :

| Phase | Timeline | Description |
|---|---|---|
| Heavy FDE | 0-12 mois | Etendu du aux exigences de clearance securite, processus ATO |
| Co-Development | 12-24 mois | Equipes gouvernementales commencent a construire |
| Guided Autonomy | 24-48 mois | Equipes gouvernementales menent la majorite du developpement |
| Self-Sufficient | 48+ mois | Gouvernement pleinement autonome |

(ESTIMATED)

**Pourquoi le gouvernement est plus lent** (Claude) :
- Exigences de clearance securite
- Rotation du personnel tous les 2-3 ans creant des besoins constants de reformation
- Complications de l'ecosysteme de sous-traitants
- Aversion institutionnelle au risque

#### Prerequis que le client doit demontrer avant le retrait

L'equipe client doit demontrer **cinq capacites** (Claude) :

1. Un **CoE fonctionnel** (3 a 10+ personnes) capable de maintenance ontologie et de construction d'applications
2. **Creation d'applications self-service** sans assistance FDE -- le client peut construire une application Workshop end-to-end
3. **Gestion des pipelines de donnees** incluant l'onboarding de nouvelles sources de donnees
4. **Capacite de formation interne** pour les nouveaux utilisateurs -- mecanisme "train-the-trainer" operationnel
5. **Chemins d'escalade etablis** vers le support Palantir -- l'equipe sait comment et quand escalader

Le programme de certification (Application Developer + Data Engineer) fournit des benchmarks formels pour evaluer ces capacites (Perplexity).

#### Comment prevenir le "withdrawal anxiety"

Le retrait genere de l'anxiete chez le client ("et si on n'y arrive pas sans eux ?"). Palantir gere cela par :

1. **Graduation progressive** -- jamais de hard cutover. La presence diminue graduellement
2. **Documentation extensive** -- les FDEs documentent tout pendant la Phase 2
3. **Hotline de support** -- le client sait qu'il peut appeler si besoin
4. **Quick wins autonomes** -- le CoE est guide pour livrer ses premiers cas d'usage independants rapidement, construisant la confiance
5. **Revues d'architecture trimestrielles** -- le lien avec Palantir ne disparait jamais completement

#### Modele de support qui remplace le FDE on-site

La presence FDE sur site est remplacee par (Claude, Perplexity) :

| Service | Description |
|---|---|
| **Portail de support a tickets** | Application Issues dans Foundry pour tracking transparent (GPT, Claude) |
| **Customer Success Manager dedie** | Distant, couvrant plusieurs comptes (Claude) |
| **Quarterly Business Reviews** | Alignement strategique, revue du ROI (Claude) |
| **Architecture office hours** | Sessions periodiques pour les questions complexes (Claude) |
| **Mises a jour plateforme via Apollo** | Automatisation d'une grande partie de la charge operationnelle (Claude) |
| **Engagement FDE on-demand** | Pour les initiatives majeures, a cout additionnel (Claude) |
| **Communaute developpeur** | community.palantir.com (Perplexity) |
| **Ecosysteme partenaire Accenture** | Pour les implementations complexes post-retrait FDE (Perplexity) |

**Support Palantir NHS UK** (GPT) : les termes G-Cloud declarent que Palantir fournira des niveaux de service et un support conformes a un SLA et une politique de support pendant la duree de la commande. Le document SLA complet n'est pas pleinement visible publiquement.

---

### 3.2.2 Self-Service Enablement

#### De "FDE builds everything" a "client builds 70-85%"

Le passage au self-service repose sur trois leviers convergents :

**Levier 1 : Workshop + AIP = plateforme citizen developer**

Workshop fournit la construction d'applications low/no-code au-dessus de l'ontologie. Combine avec AIP (capacites LLM), les utilisateurs metier peuvent construire des applications operationnelles sans competences techniques profondes (Perplexity). Workshop dispose de **50+ widgets built-in** couvrant affichage, visualisation, filtrage, navigation et IA. Les **Inline Actions** permettent aux utilisateurs metier de declencher des writeback vers les systemes sources directement depuis l'interface.

**Levier 2 : AI FDE (le produit, pas la personne)**

Palantir a construit une capacite **"AI FDE"** (AIFDE) qui automatise certaines taches de decouverte et de construction que les FDEs humains geraient precedemment (GPT, Perplexity). Capacites documentees :
- Integration et transformation de donnees via langage naturel
- Developpement d'ontologie (creer/modifier Object Types, Link Types, Action Types)
- Creation de fonctions (ecrire, preview, publier, debugger)
- Construction d'applications Workshop
- Architecture de securite : branching par defaut, propositions de changements pour revue humaine

**Quote definissante** (Shyam Sankar, Q3 2025) :
> "At one customer, two human FTEs spawned an army of AI FTEs to migrate a customer off their legacy data warehouse in five days, something that would have taken an army of SIs up to two years. This is not a prototype. This is production."

**Levier 3 : Programmes de formation structure**

| Programme | Contenu | Cible |
|---|---|---|
| learn.palantir.com | Cours gratuits, certifications payantes | Toute l'equipe client |
| CodeStrap (open-source) | Curriculum Foundry Foundations sur GitHub | Auto-didactes |
| Multiverse (NHS) | Formation specifique Foundry/FDP | Personnel NHS |
| Partenaires (Accenture, Ontologize) | Formation et support sur site | CoE enterprise |

#### Timelines de self-service par type de client

| Organisation | Timeline vers self-service significatif | Niveau atteint | Facteurs |
|---|---|---|---|
| **Airbus Skywise** | 2-3 ans (declare lors d'evenements investisseurs) (Claude) | 85-90% self-service, 50K+ utilisateurs | 11 ans d'histoire totale (2015-2026). Skywise App Store avec 19+ applications. Tiers X1/X2/X3 |
| **Clients commerciaux (moyenne)** | 2-3 ans (Claude) | 70-85% | Workflows repetables, equipes techniques existantes |
| **Lear Corporation** | ~2 ans (2023-2025) | Expansion rapide, 11 000 employes | Les environnements manufacturiers avec des workflows repetables atteignent le self-service plus vite (Perplexity) |
| **Clients gouvernementaux (moyenne)** | 3-5 ans (Claude) | 60-70% | Clearances, rotation personnel, aversion au risque |
| **US Army Vantage** | 3-5 ans+ | 60-70% self-service | Reevaluation tous les 18-24 mois |
| **NHS** | Resultats mitiges | 20-30% (ESTIMATED) | Seulement 34 trusts (15%) utilisaient activement FDP a mi-2025 |

#### Taux d'echec : clients qui n'atteignent JAMAIS le self-service

Certains clients n'atteignent jamais le self-service. Les departs pre-Foundry (Home Depot, AmEx, Hershey's ~2017) ont ete largement attribues aux couts eleves et au manque de maturite de la plateforme a l'epoque (Perplexity).

Un ancien FDE a note : "If a customer doesn't need an FDE they aren't using the platform, or they hired ex-FDEs for cheaper" -- soulignant que le vrai self-service necessite un investissement significatif du client en capacite interne (Perplexity).

Palantir ne publie pas de metrique universelle de "temps vers l'autonomie". Les pilotes peuvent echouer a convertir : Palantir fournit des plateformes a cout nul ou reduit pour les pilotes, et il n'y a "aucune garantie" de pouvoir deplacer les clients d'Acquire vers les phases ulterieures (GPT).

**Repartition du revenu par maturite d'engagement** (ESTIMATED) :

| Segment | % du revenu total | Description |
|---|---|---|
| **Fully self-service** | 25-35% | Clients matures, 3+ ans. Revenu a plus haute marge |
| **Hybride** | 45-55% | Support FDE partiel + principalement client-driven. Plus grand segment |
| **Heavy FDE** | 15-20% | Nouveaux deploiements + gouvernement complexe. Plus basse marge |

**Point historique** (Perplexity) : en 2007, la plupart des clients necessitaient 2+ FDEs, les grands clients comme le NHS necessitant "une petite armee" de 10+ FDEs. En 2024, **plus de 33% des clients** de Palantir n'ont **jamais eu besoin de FDEs**, representant un changement fondamental dans la capacite self-service de la plateforme.

---

### 3.2.3 Stickiness & Lock-in -- La Version Honnete

#### Les 7 couches de switching costs

Le lock-in Palantir n'est pas contractuel -- les clients peuvent theoriquement partir avec un preavis de 3 a 6 mois (GPT). Il est **structurel**, construit couche par couche pendant les annees d'expansion.

**Couche 1 : Dependances d'integration de donnees**

Un deploiement mature connecte **50 a 150+ sources de donnees** -- bases de donnees, APIs, flux IoT, plateformes SaaS, systemes legacy -- chacune avec des connecteurs personnalises, de la logique de transformation, et des controles de qualite construits sur des mois ou des annees. Recreer ces integrations prendrait **6 a 18 mois** d'effort d'ingenierie (Claude).

Foundry est concu comme un backbone pour les environnements complexes et vise explicitement a reduire le cout d'integration dans le temps via des capacites de force-multiplicateur (GPT). Exemple : bp a 2M+ capteurs integres dans un jumeau numerique unifie via Foundry (Perplexity).

**Couche 2 : Complexite de l'ontologie**

L'ontologie encode non seulement un modele de donnees mais des **connaissances institutionnelles** sur le fonctionnement de l'entreprise -- relations entre entites, regles metier, logique de decision. Il n'y a **aucun equivalent direct** dans les plateformes concurrentes (Claude).

L'ontologie Palantir inclut des elements semantiques (objets, proprietes, liens), des elements cinetiques (types d'actions, fonctions), des interfaces (polymorphisme), et la couche dynamique (modeles AI, simulations) -- fondamentalement different des bases de donnees traditionnelles et sans equivalent 1:1 sur Databricks ou Fabric (Perplexity).

Databricks Unity Catalog gere la gouvernance des donnees mais manque la couche de relations et d'actions (Claude).

**Couche 3 : Dependances d'applications**

Les clients matures ont **50 a 200+ applications Workshop** integrees dans les workflows quotidiens -- dashboards operationnels, outils de decision, systemes d'alerte. Chacune reference des objets et actions ontologie. Il n'y a **aucun mecanisme d'export** pour les applications Workshop ; chaque application doit etre reconstruite from scratch sur toute plateforme alternative (Claude).

Chez un client de services financiers, les effets de reseau ont permis de passer d'un cas d'usage unique a **plus de 70 workstreams** a travers conformite, front office, risque et audit interne (GPT).

**Couche 4 : Capture de connaissances institutionnelles**

Pistes d'audit de decisions, analyses historiques, versioning de l'ontologie montrant comment le modele metier a evolue, et annotations generees par les utilisateurs. Ces connaissances sont integrees dans la structure de l'ontologie, pas exportables comme fichiers de donnees (Claude). Les objets Foundry peuvent etre modifies par des edits utilisateurs plus des mises a jour de sources de donnees, avec des strategies de resolution de conflits pour resoudre les valeurs concurrentes (GPT).

**Couche 5 : Complexite de la configuration de securite**

Des milliers de regles RBAC refletant la structure organisationnelle -- permissions au niveau objet, colonne et ligne avec des controles d'acces bases sur les markings -- tout cela necessite recreation (Claude, GPT). L'architecture de securite comprend trois couches : markings obligatoires au niveau ressource, ACL au niveau ontologie, et controles de contexte d'execution pour l'IA.

**Couche 6 : Investissement en formation**

A travers un CoE de **5 a 50+ personnes** plus des communautes de citizen developers dans l'organisation, representant un cout irrecuperable significatif. La reformation de ces equipes a une nouvelle plateforme cree une resistance organisationnelle au changement (Claude).

**Couche 7 : Integration dans les workflows (la couche la plus profonde)**

Les operations quotidiennes dependent des dashboards et workflows Palantir pour la gestion de supply chain, l'allocation de ressources, la maintenance predictive. Le switching cause une **perturbation operationnelle**, pas seulement de la douleur de migration technique (Claude). C'est la couche la plus difficile a quantifier mais la plus dissuasive : remplacer Palantir signifie interrompre les operations pendant la transition.

#### Estimation des couts de switching

[CONTRADICTION] Claude estime les couts de switching a **2-5x la valeur annuelle du contrat Palantir** pour les deploiements mid-stage, et potentiellement **50 a 200M$+ pour les grands deploiements enterprise-wide**. Perplexity estime **2,5 a 7,5M$ par client enterprise** avec le detaille suivant :

| Composant | Cout estime (Perplexity) |
|---|---|
| Migration de donnees | 500K$ - 1,2M$ |
| Reconstruction de l'ontologie | 500K$ - 2M$ |
| Reconstruction des applications | 500K$ - 1,5M$ |
| Connaissances institutionnelles | Non quantifiable |
| Reconfiguration securite | 200K$ - 500K$ |
| Couts de reformation | 300K$ - 800K$ |
| Temps de re-implementation | 6-9 mois |
| **Total (hors perte de productivite)** | **2,5M$ - 7,5M$** |

GPT note que les estimations varient enormement et que Palantir ne publie pas de chiffre standard. L'ecart entre les deux estimations s'explique par la taille du deploiement considere : 2,5-7,5M$ pour un client mid-market, 50-200M$+ pour un Army ou Airbus.

**Point critique** : les donnees elles-memes sont stockees en formats ouverts (Parquet sur object storage) et sont portables -- le lock-in est aux **couches semantique et applicative**, pas a la couche de donnees (Claude).

#### Les 6 clients confirmes qui ont quitte Palantir

| Client | Periode | Raison | Details |
|---|---|---|---|
| **NYPD** | 2012 ~2020 | Contrat expire, remplace par systeme interne | Utilisait Palantir Gotham (~2M$/an). Remplace par le **Domain Awareness System** construit en partenariat avec Microsoft. Possible uniquement parce que le NYPD avait la sophistication technique et un partenariat Microsoft profond que la plupart des organisations n'ont pas (Claude) |
| **New Orleans PD** | 2018-19 | Scandale politique | Programme de police predictive secret termine apres revelation par The Verge. Motive par un contrecoup politique, pas un echec produit (Claude) |
| **JP Morgan** | ~2015-2017 | Preoccupations de securite | L'un des premiers clients commerciaux (depuis ~2009). Relation terminee apres des preoccupations que les ingenieurs Palantir avaient un acces excessif aux donnees financieres sensibles et des allegations de developpement d'applications non autorisees (Claude) |
| **Home Depot, AmEx, Hershey's, Coca-Cola** | ~2017 | Couts eleves, plateforme immature | Departs pre-Foundry. Un employe Palantir de l'epoque a note "there wasn't too much worry within the company because at the time this was a minor endeavor" (Perplexity) |
| **NHS England (partiel)** | Post-2020 | Pressions budgetaires | Le Financial Times a rapporte la fin d'un deal post-Brexit avec Palantir pour les frontieres du a des "pressions budgetaires". NHS a aussi publie un avis de service de "transition et sortie" de 12 mois depuis Foundry vers un nouveau fournisseur FDP pour certains produits Covid (GPT) |

**Schema des departs** (Claude) : les departs ont ete motives par des preoccupations politiques, ethiques ou de securite -- **jamais par la decouverte d'une alternative technique superieure**. La plupart se sont produits avant 2020, quand Foundry etait moins mature et les deploiements plus bespoke. Aucun grand client commercial n'a publiquement quitte Palantir pour la plateforme d'un concurrent dans l'ere Foundry/AIP.

**Migrations concurrentes** (Perplexity) : des competiteurs rapportent des migrations : "from the few customers that use both [Palantir and Databricks], all of them are migrating from Palantir to Databricks over time as contracts expire."

#### Comment Palantir repond aux menaces de churn

| Strategie | Details |
|---|---|
| **Concessions de prix** | Rabais de **30 a 50%** reportes dans certains cas (Claude) |
| **Offres de perimetre elargi** | Nouveaux produits comme AIP pour demontrer une valeur additionnelle (Claude, Perplexity) |
| **Engagement C-level** | Karp et les dirigeants seniors s'engagent personnellement avec les grands comptes a risque (Claude) |
| **Consolidation commerciale** | Ex. : US Army -- 75 arrangements consolides en un seul vehicule contractuel a 10 Md$, avec rabais de volume et horizon de 10 ans (GPT) |
| **Bootcamps supplementaires** | Pour demontrer les nouvelles capacites AIP aux utilisateurs du compte a risque (Perplexity) |
| **Acceleration du support FDE** | FDEs supplementaires deployes pour les deploiements en difficulte (Perplexity) |
| **"Expansion defensive"** | Etendre l'ontologie a des departements supplementaires pour augmenter les couts de switching **avant** les negociations de renouvellement (Perplexity, Claude) |

#### Le paradoxe captif-autonome

La methode post-pilote de Palantir resout une tension apparemment impossible : les clients deviennent plus autonomes dans l'**usage** tout en devenant plus captifs dans l'**infrastructure** (Claude).

A l'annee 3-5, les propres employes du client construisent **70-85% des nouvelles applications**, forment leurs propres utilisateurs, et gerent leur propre ontologie -- ils n'ont genuinement pas besoin des FDEs de Palantir pour les operations quotidiennes.

Mais la plateforme sur laquelle tout cela tourne, l'ontologie encodant leurs connaissances institutionnelles, les centaines d'applications pilotant les operations quotidiennes, et les configurations RBAC refletant tout leur modele de securite organisationnelle -- tout cela existe exclusivement au sein de la stack proprietaire de Palantir (Claude).

**Trois insights structurels** (Claude) :

1. **L'ontologie est le produit, pas le logiciel** -- le vrai livrable de Palantir est un modele formalise du fonctionnement de l'entreprise du client, et ce modele devient plus precieux (et plus difficile a abandonner) a chaque departement qui s'y connecte

2. **Apollo est la troisieme jambe sous-appreciee** -- en gerant l'ensemble du cycle de vie logiciel incluant les deploiements tiers, il cree une couche de dependance operationnelle en dessous du lock-in ontologie et applicatif plus visible. 360 000+ deploiements/mois, 300+ environnements geres, rollback en <5 minutes

3. **La captivite n'est pas contractuelle** -- les filings Palantir explicitent que les clients peuvent n'avoir aucune obligation de renouvellement ; les contrats peuvent etre aussi courts qu'un an ; beaucoup permettent la resiliation avec preavis de 3-6 mois. La captivite est structurelle, pas juridique

**Vulnerabilite ultime du modele** : pas le deplacement competitif mais la **commoditisation de la couche semantique**. Si Databricks, Microsoft ou des projets open-source repliquent avec succes une abstraction de type ontologie avec des capacites de construction d'applications, le premium de Palantir s'effondre. Cela ne s'est pas encore produit -- et la complexite composee de l'integration de l'ontologie, des applications, des permissions et de la livraison continue dans une seule plateforme coherente suggere que cela ne se produira pas rapidement. Mais c'est le risque structurel qui explique pourquoi Palantir court pour etendre le perimetre de l'ontologie au sein de chaque client aussi vite que possible (Claude).

---

### 3.2.4 Support a Long Terme et Protection du Revenu

#### Apollo : infrastructure de livraison continue

Apollo est le mecanisme de livraison continue de Palantir et probablement son avantage concurrentiel le plus sous-apprecie (GPT, Claude, Perplexity).

| Metrique | Valeur |
|---|---|
| Deploiements par mois | 360 000+ (CONFIRMED) |
| Environnements geres | 300+ (CONFIRMED) |
| Temps de deploiement | 3,5 minutes (CONFIRMED) |
| Temps de rollback | <5 minutes (CONFIRMED) |
| Equipe d'ingenierie | <20 ingenieurs (CONFIRMED, CTO talk) |

Apollo est "nativement conscient du modele d'objets de Foundry" et supporte :
- Versioning object-aware
- Overrides de configuration specifiques a l'environnement
- Livraison multi-domaine securisee (incluant les reseaux air-gapped)
- Upgrades sans temps d'arret (blue-green deployment)
- Mecanisme break-glass pour les situations d'urgence

Les clients peuvent configurer des politiques de mise a jour -- auto-update, rollout par etapes, ou approbation manuelle. Les demandes de changement transitent par Approvals pour maintenir un historique et appliquer des politiques d'approbation (GPT).

Apollo est considere comme "arguably Palantir's most important tool for enabling FDE withdrawal" -- en automatisant les mises a jour, le monitoring et les rollbacks, il elimine le besoin de support operationnel humain (Claude).

**Disponibilite standalone** : Apollo est disponible sur Azure et AWS Marketplaces a ~$100/install/mois (CONFIRMED). Le seul produit Palantir vendable independamment du stack Foundry.

#### Revenue protection face aux concurrents

**Contre Databricks** (le concurrent long-terme le plus dangereux) :

Palantir se positionne comme complementaire plutot que competitif : "Databricks fait le data engineering ; nous faisons la prise de decision operationnelle" (Claude). Palantir a annonce un **partenariat produit strategique avec Databricks** (septembre 2024) combinant AIP et l'Ontology System avec l'ingenierie de donnees Databricks (GPT). En pratique, certains clients utilisent les deux -- Databricks pour le data lakehouse, Palantir pour l'ontologie et la couche applicative.

**Contre Microsoft Fabric** (la menace full-stack la plus forte) :

Palantir differencie sur :
1. La profondeur de l'ontologie (Fabric n'a aucun equivalent)
2. La construction d'applications operationnelles (Power Automate est primitif vs. Palantir Actions)
3. Les certifications gouvernement/classifie (FedRAMP High, IL5/IL6)
4. Le systeme de guardrails a 4 niveaux pour l'IA

Palantir prix est largement percu comme **2 a 5x plus cher** que les alternatives pour des capacites de plateforme de donnees comparables (Claude). La justification : vitesse de deploiement via les FDEs, vitesse vers la valeur, impact operationnel en dollars, gouvernance integree, et arguments de cout total de possession (une plateforme vs. 5-10 outils assembles).

**Partenariat Accenture comme moat** : le Accenture Palantir Business Group (decembre 2025) met 2 000+ consultants qualifies Palantir sur le terrain, faisant de Palantir la recommandation par defaut de l'un des plus grands integrateurs de systemes au monde (Perplexity).

**Beachhead gouvernemental** : l'EA de 10 Md$ de l'US Army et le FDP de 330M GBP du NHS creent des architectures de reference auxquelles les clients commerciaux peuvent faire confiance. La validation gouvernementale reduit le risque de procurement pour les acheteurs enterprise (Perplexity).

---

## 3.3 Case Studies Multi-Annees

### 3.3.1 Airbus Skywise -- Le deploiement reference

| Dimension | Detail |
|---|---|
| **Debut** | 2015 (equipe Palantir embarquee en France) ; lancement officiel Skywise juin 2017 apres 2 ans d'experimentation (GPT) |
| **Expand** | Plateforme etendue des operations internes Airbus (20 000+ employes) aux clients airlines (Perplexity) |
| **Scale** | 140+ airlines, **50 000+ utilisateurs** quotidiens, Skywise App Store avec 19+ applications (GPT, Perplexity) |
| **Self-service** | Atteint en **2-3 ans** (declare lors d'evenements investisseurs) (Claude). Estime a **85-90%** |
| **Tiers d'abonnement** | X1 (naviguer les donnees), X2 (naviguer les operations), X3 (naviguer l'inexplore avec AI/ML) (Perplexity) |
| **Revenu estime** | ~**94M$/an** base sur des estimations de licence par utilisateur (Perplexity) |
| **Renouvellement** | Extension multi-annee signee fevrier 2026, avec support de migration cloud souverain (Perplexity) |
| **Detail FDE** | Nabeel Qureshi (FDE Palantir) a vecu a Toulouse pendant un an pour travailler a l'usine de fabrication d'Airbus |
| **Cas d'usage concret** | Investigation de valves haute pression fuyantes sur A330neo -- identification d'un defaut logiciel et emission proactive d'un Airworthiness Directive |

**Implication pour le playbook** : trajectoire de maturite classique Phase 3 a Phase 4 -- livraison embarquee multi-annee plus adoption massive d'utilisateurs (GPT). Le passage de 20K utilisateurs internes a 50K+ incluant les airlines clientes illustre le potentiel de "platform effect" ou le client Palantir (Airbus) redistribue la plateforme a ses propres clients.

### 3.3.2 bp -- Le jumeau numerique decennal

| Dimension | Detail |
|---|---|
| **Debut** | 2014, deploiement dans les operations de production (GPT, Perplexity) |
| **Cas d'usage initial** | Fiabilite de production sur les plateformes offshore (Perplexity) |
| **Expand** | Plateformes offshore (Mer du Nord, Golfe du Mexique), champs gaziers de Khazzan (Oman), maintenance et fiabilite (Perplexity) |
| **Scale** | Integration de **2M+ capteurs** en une image operationnelle unique, jumeau numerique base sur les modeles (Perplexity) |
| **Renouvellement** | Nouvel accord strategique de 5 ans signe **septembre 2024** avec nouvelles capacites AIP (GPT, Perplexity) |

**Implication** : fondation operationnelle d'une decennie plus couche AIP -- expand-first, puis acceleration AI (GPT).

### 3.3.3 US Army Vantage -- L'ancrage progressif

| Dimension | Detail |
|---|---|
| **Expand** | Multiples programmes -- Vantage (extension de 115M$ en decembre 2023), Maven Smart System ($480M IDIQ mai 2024, augmente a $1Md+), Army Intelligence Data Platform, TITAN ($823M) |
| **Scale** | **75 contrats consolides** en un seul Enterprise Agreement avec un plafond de **10 Md$** (aout 2025), periode de commande de 10 ans (GPT, Perplexity) |
| **Utilisateurs** | 50 000+ (CONFIRMED) |
| **Self-service** | 60-70% (ESTIMATED) |
| **Reassessment** | Tous les 18-24 mois "pour assurer une performance et une innovation optimales" (Perplexity) |
| **Impact operationnel** | "The 18th Airborne can now match the performance of what used to be a 2,000-staff targeting cell...with roughly only 20 people today" (Q3 2024 earnings) |

**Implication** : structure commerciale de phase Scale exemplaire -- consolidation, rabais de volume, horizon long ; se couple avec l'autonomie programmatique en interne (GPT).

### 3.3.4 NHS FDP -- Les difficultes du deploiement a echelle nationale

| Dimension | Detail |
|---|---|
| **Entree** | Services offerts pour **1 GBP** pendant la pandemie de Covid-19, mars 2020 (Perplexity) |
| **Expand** | 1M GBP -> deal de 2 ans a 23M GBP -> contrat FDP de **330M GBP** (novembre 2023) (GPT, Perplexity) |
| **Defis** | Controverse politique continue. Seulement **34 trusts (15%)** utilisaient activement les produits FDP a mi-2025, avec plus de la moitie n'ayant pas adopte du tout (Perplexity) |
| **Self-service** | 20-30% (ESTIMATED) -- heavy FDE involvement |
| **Lock-in** | Programme d'apprentissage avec Multiverse formant le personnel NHS sur FDP, mandat pour tous les fournisseurs d'adopter les produits core FDP d'ici **avril 2026** (Perplexity) |
| **Sortie partielle** | NHS a publie un avis de service de "transition et sortie" de 12 mois depuis Foundry pour certains produits Covid (GPT) |

[CONTRADICTION] GPT mentionne une sortie partielle du NHS (transition pour certains produits Covid) tandis que Perplexity decrit une adoption en cours (certes difficile) sans mentionner de sortie. Le Financial Times rapporte separement la fin d'un deal post-Brexit pour les frontieres. Ces elements refletent des dynamiques temporelles differentes -- sortie partielle de produits Covid d'urgence vs. programme FDP long-terme.

**Lecon** : "captif" est fragile sans confiance et adoption ; la gouvernance et les champions ne sont pas optionnels (GPT).

### 3.3.5 Lear Corporation -- L'expansion rapide en manufacturing

| Dimension | Detail |
|---|---|
| **Debut** | 2023 -- premier partenariat pour numeriser les operations de fabrication (Perplexity) |
| **Expand** | Rapidement etendu a qualite, supply chain, approvisionnement, fabrication, finance et design (GPT, Perplexity) |
| **Scale** | **11 000 employes** utilisant la plateforme, **30M$+ d'economies au S1 2025** (GPT, Perplexity) |
| **Renouvellement** | Expansion de 5 ans signee **septembre 2025** deployant Foundry + Warp Speed + AIP a travers la fabrication mondiale (GPT, Perplexity) |

**Implication** : les environnements manufacturiers avec des workflows repetables atteignent le self-service plus vite (Perplexity). L'expansion cross-fonctionnelle rapide (qualite, supply chain, approvisionnement, fabrication, finance, design) illustre la propagation de l'ontologie a travers les domaines.

---

## 3.4 Metriques Cles du Flywheel

### Net Dollar Retention (NDR) Trajectory

| Trimestre | NDR | Confiance |
|---|---|---|
| Q3 2023 | 107% | CONFIRMED |
| Q1 2024 | 114% | CONFIRMED |
| Q3 2024 | 120% | CONFIRMED |
| Q3 2025 | 134% | CONFIRMED |
| Q4 2025 | **139%** | CONFIRMED |

L'acceleration de 107% a 139% en deux ans reflete l'effet compose des AIP bootcamps alimentant le flywheel d'expansion. Historiquement, le NDR US Commercial a atteint un pic de **150%** (cohorte 2021) (Perplexity).

### Expansion par cohorte

| Age du client | Multiple de revenu vs. Annee 1 |
|---|---|
| Annee 1 | 1,0x |
| Annee 2 | 1,3-1,5x |
| Annee 3 | 2,0-2,5x |
| Annee 5 | 3,5-6,0x |
| Annee 7+ | 8-10x+ |

Les clients acquis en 2016 generaient environ **6x leur revenu initial** en 2020 (Claude). La courbe en hockey -- lente annees 1-2, accelerant annees 3-5 -- reflete directement le cycle Acquire-Expand-Scale.

**Le multiple d'expansion** : un contrat initial de **$100K** se transforme en **$5,6M** de valeur annuelle contractuelle mature -- soit un **multiple de 56x** (CONFIRMED, presentations investisseurs).

### Marge de contribution par phase

| Phase | Marge de contribution | Explication |
|---|---|---|
| **Acquire** | **Negative** (ex. : -43%) | Palantir investit massivement : FDEs on-site, temps gratuit, pilotes subventionnes. Cohorte 2019 : $600K revenu moyen par client vs. $65,4M de pertes de contribution totales (S-1) |
| **Expand** | **-43% a +35%** | Marge s'ameliore a mesure que le platform leverage s'installe et l'intensite FDE diminue (ESTIMATED) |
| **Scale** | **+55%** | Revenus a haute marge -- le client construit ses propres applications. Clients Scale en 2019 : 565,7M$ de revenus avec 55% de marge de contribution ; au S1 2020, les memes clients : 296,3M$ avec 68% de marge (S-1) |

### Revenue per Employee

| Annee | Revenue per Employee | YoY |
|---|---|---|
| 2020 | $448K | -- |
| 2022 | $578K | +29% (2 ans) |
| 2024E | ~$800K | +38% (2 ans) |
| 2025E | **$1,01M** | +26% (1 an) |

L'acceleration 2022-2025 (**+74% en 3 ans**, $578K -> $1,01M) est le resultat direct du deploiement assiste par IA rendant chaque employe dramatiquement plus productif. **Paradoxe de Jevons** : malgre cette productivite accrue, le headcount a grandi (3 838 -> 4 414, +15%) -- Palantir utilise l'IA pour faire plus, pas pour couper.

### Cout FDE par $1M ARR

| Annee | Cout FDE par $1M ARR | Interpretation |
|---|---|---|
| 2016 | ~$700K | Quasi $1 de FDE pour $1 de ARR -- un business de consulting deguise |
| 2020 | ~$280K | Maturation de la plateforme reduisant l'intensite FDE |
| 2025E | ~$80K-$150K | Automation IA + self-service plateforme |

(ESTIMATED)

### Efficacite commerciale

Les depenses S&M en pourcentage du revenu sont passees de **47% en 2020 a environ 21% en 2023**, refletant le fait que le revenu d'expansion (moins couteux a capturer que les nouveaux logos) croit plus vite que les depenses d'acquisition (Claude).

| Metrique | Valeur |
|---|---|
| Revenu total FY2025 | $4,475B (+56% YoY) |
| Revenu Q4 2025 | $1,407B (+70% YoY) |
| Croissance US Commercial | 137% YoY |
| Clients totaux Q4 2025 | 954 (+34% YoY) |
| Top-20 clients ACV moyen (TTM) | $94M |
| Remaining Deal Value | $5,4B+ |
| Deals >$10M en Q4 seul | 61 |
| Rule of 40 | ~90+ (56% growth + 34% adj. operating margin) |

---

## 3.5 Contradictions Identifiees sur Expand/Scale

### [CONTRADICTION 1] Timing de formation du CoE

**Claude** indique 6-18 mois. **Perplexity** indique 6-12 mois. **GPT** lie la formation non pas a un nombre de mois mais au franchissement du seuil "multi-use-case, multi-domain, hundreds-of-users" (Phase 3 de Foundry). En pratique, la formation du CoE est vraisemblablement un continuum : les premiers roles (Platform Owner, Ontology Steward) emergent vers 6-9 mois, l'equipe complete de 5-10+ personnes est operationnelle vers 12-18 mois.

### [CONTRADICTION 2] Methode de facilitation des "100 cas d'usage"

**GPT** indique que les materiaux publics de Palantir ne decrivent pas une methode canonique de facilitation (pas de formats specifiques de post-it) et que le chiffre de 100 provient d'un entonnoir d'ideation structure et filtre dans le temps. **Claude** affirme avec assurance que les participants font un exercice sticky-note/whiteboard avec un canevas template, et que Palantir construit 1-3 prototypes en temps reel. La documentation officielle mentionne le processus mais pas les formats ; les descriptions detaillees de Claude semblent provenir de sources secondaires.

### [CONTRADICTION 3] Taux de conversion des bootcamps

**Synthese initiale** (Phase 2) : 30-50% de conversion. **Synthese agent** (A.12) : "environ 70% convertissent en contrats payes dans un trimestre, taille de deal moyenne >$1M." **Correction Phase 4** : ~22% (consensus analystes Morgan Stanley, Wedbush Securities, RBC Capital Markets). **Management Palantir** : "substantial majority" mene a un engagement de suivi. Le chiffre de 70% pourrait inclure les engagements de suivi non contractuels (etudes additionnelles, bootcamps de continuation), tandis que le 22% ne compterait que les contrats payes signes. Le chiffre le plus conservateur et le plus fiable est probablement le **22%** des analystes.

### [CONTRADICTION 4] Couts de switching

**Claude** estime 2-5x la valeur annuelle du contrat (potentiellement 50-200M$+ pour les mega-deploiements). **Perplexity** estime 2,5-7,5M$ par client enterprise. L'ecart est enorme (facteur 10-30x). L'explication probable : Claude inclut les mega-deploiements (US Army, Airbus) tandis que Perplexity donne une fourchette pour un client enterprise "moyen". Les deux chiffres sont probablement valides pour leurs segments respectifs.

### [CONTRADICTION 5] Self-service NHS

**GPT** mentionne une sortie partielle du NHS (transition de 12 mois pour certains produits Covid). **Perplexity** decrit une adoption en cours sans mentionner de sortie. Le Financial Times rapporte separement la fin d'un deal post-Brexit pour les frontieres. Ces elements refletent des contrats et des dynamiques temporelles differents -- le NHS n'est pas un client unique mais un ensemble de contrats distincts (produits Covid d'urgence, FDP long-terme, frontieres post-Brexit).

### [CONTRADICTION 6] Modele d'equipe -- Triade vs Echo/Delta/Core

**Claude** decrit une triade FDE/DS/AE comme modele principal d'expansion. **Perplexity** decrit un modele Echo/Delta/Core Product plus granulaire. Ces deux descriptions ne sont pas mutuellement exclusives : le modele Echo/Delta/Core est une description de l'organisation de l'ingenierie (Delta = FDE, Echo = DS), tandis que la triade FDE/DS/AE decrit les roles commerciaux-strategiques. L'AE est absent du modele Echo/Delta/Core car il est au niveau de l'organisation de vente, pas de l'ingenierie.

### [CONTRADICTION 7] Pourcentage de clients n'ayant jamais eu besoin de FDEs

**Perplexity** affirme qu'en 2024, "plus de 33% des clients n'ont jamais eu besoin de FDEs". Cela semble contradictoire avec la correction #10 (seulement 25-35% du revenu est fully self-service). L'explication : le 33% mesure le nombre de clients, pas le revenu. De nombreux petits clients (post-bootcamp, Palantir for Builders) n'ont jamais eu de FDE mais generent peu de revenu. Les gros clients (qui generent l'essentiel du revenu) ont presque tous eu des FDEs.

---

# PARTIE 4 — FOUNDRY : L'OUTIL EN DÉTAIL

---

## 4.1 Architecture Globale

### 4.1.1 Rubix — La Couche d'Abstraction Infrastructure

Rubix est la couche d'abstraction Kubernetes propriétaire de Palantir. Elle masque le cluster K8s sous-jacent (EKS, AKS, GKE, OpenShift, bare-metal) et fournit une surface de déploiement standardisée pour les microservices de Foundry. [CONFIRMED]

**Caractéristiques techniques :**

- Environ **150+ microservices** par instance Foundry [CONFIRMED]
- Chaque microservice est déployé, versionné et monitoré indépendamment via Apollo
- Rubix gère : service discovery, load balancing, gestion des secrets, health checks
- **Éphéméralité des noeuds** : chaque noeud est recyclé dans les **48 heures** (exigence architecturale stricte empêchant l'accès persistant d'un attaquant)
- Isolation des workloads : sécurité multi-tenant pour le code auteur (PySpark des clients)
- Chiffrement partout : chaque interaction requiert authentification, autorisation, journalisation immutable
- Conformité : FedRAMP High, DoD DISA IL-5/IL-6, CMMC
- Sécurité réseau via Cilium (segmentation réseau), pod security contexts, patterns d'infrastructure immutable

**k8s-spark-scheduler** (open-source `palantir/k8s-spark-scheduler`) : Kubernetes Scheduler Extender fournissant du **gang scheduling** pour Spark. Garantit qu'un driver n'est schedulé que s'il y a de l'espace pour tous ses executors. Algorithmes de détection de demande pour requêter de nouveaux noeuds proactivement. Modes bin-packing : `distribute-evenly` ou `tightly-pack`.

**Autoscaling intelligent :** algorithmes de détection de demande, distribution de workloads optimisant les coûts (AWS, Azure, GCP, Oracle). Apollo calcule et transmet des plans de déploiement pour des rollouts **zero-downtime blue/green**.

### 4.1.2 Les 4 Plateformes

| Plateforme | Année | Cible | Description |
|------------|-------|-------|-------------|
| **Gotham** | 2008 | Renseignement et défense | Produit originel. Architecture EAV/CR (Entity-Attribute-Value with Classes and Relationships). 6 applications : Graph, Gaia, Browser, Object Explorer, Dossier, Inbox. Subsystèmes : AtlasDB (ACID sur Cassandra), RevDB (temporal queries), Horizon (in-memory analytics), Raptor (federated search). |
| **Foundry** | 2016 | Entreprise commerciale | OS d'entreprise généraliste. Généralise l'architecture Gotham pour la supply chain, le manufacturing, la santé, la finance, l'énergie. Substrat sur lequel AIP s'exécute. Principal moteur de revenus. |
| **AIP** | 2023 | Couche IA | Artificial Intelligence Platform. Les LLMs reçoivent des **objets Ontologie typés**, pas du texte brut. Composants : AIP Logic, Agent Studio, Language Model Service (50+ modèles). |
| **Apollo** | Continu | Déploiement | Plateforme de livraison continue. Modèle pull constraint-based. Hub-spoke. 300+ environnements. Disponible standalone (~$100/install/mois). |

**Interopérabilité :** Gotham tourne désormais sur Foundry comme couche de base. Un système de mapping de types cross-plateforme permet de traiter les entités Gotham et Foundry comme synonymes. [CONFIRMED]

### 4.1.3 Le Data Flow en Boucle Fermée — 7 Étapes

Le pattern architectural définissant de Palantir est la **boucle fermée en 7 étapes**. Contrairement aux outils BI traditionnels qui s'arrêtent à la visualisation (étape 6), Palantir ferme la boucle en écrivant les décisions dans les systèmes source (étape 7). [CONFIRMED]

> "Les outils BI s'arrêtent à l'étape 6. Palantir ferme la boucle."

| Étape | Nom | Ce qui se passe | Technologie clé |
|-------|-----|----------------|-----------------|
| **1** | Sources | Les données brutes proviennent des systèmes opérationnels | ERP (SAP, Oracle), CRM (Salesforce), capteurs IoT, fichiers, bases de données, APIs |
| **2** | Data Connection | 150+ connecteurs natifs ingèrent les données via 3 architectures de connexion | Framework Data Connection (direct, proxy agent, worker air-gapped) |
| **3** | Pipelines | Les données sont transformées, nettoyées, enrichies et façonnées pour l'Ontologie | Pipeline Builder (DAG visuel), Code Repos, Spark/Flink/DuckDB |
| **4** | Ontologie | Les données transformées sont mappées sur des Object Types, Properties et Links typés | OMS, Object Storage V2, pipeline Funnel, Elasticsearch |
| **5** | AIP / Agents | Les agents IA raisonnent sur des objets Ontologie typés via architecture tool-use | AIP Logic, Agent Studio, Language Model Service (50+ modèles) |
| **6** | Applications | Les applications opérationnelles rendent les objets Ontologie dans des interfaces dédiées | Workshop (app builder low-code), Quiver, Contour, Slate |
| **7** | Actions | Les décisions sont exécutées comme des Actions Ontologie, qui écrivent dans les systèmes source | Actions Service, connecteurs writeback, webhooks, appels API |

**Flux traditionnel BI :** Sources -> Pipelines -> Dashboard -> FIN

**Flux Palantir :** Sources -> Pipelines -> Ontologie -> IA -> App -> Action -> Sources (boucle)

---

## 4.2 L'Ontologie — Le Coeur du Système

L'Ontologie est le noyau de tout produit Palantir. Ce n'est pas un simple catalogue de métadonnées ou un registre de schéma — c'est un **modèle de données opérationnel vivant** à travers lequel toutes les données sont accédées, toutes les actions exécutées, toute l'IA raisonne, et toute la sécurité est appliquée. [CONFIRMED]

### 4.2.1 Les 6 Primitives

L'Ontologie est construite à partir d'exactement six types primitifs. Tout dans Palantir — chaque widget UI, chaque outil d'agent IA, chaque endpoint API, chaque règle de sécurité — opère sur ces six primitives :

#### 1. Object Types (Tables / Classes d'Entités)

Les définitions d'entités fondamentales du domaine métier. Chaque Object Type définit une classe d'entités avec un ensemble fixe de propriétés typées.

- **Analogie** : une table dans une base de données relationnelle, ou une classe d'entités
- **Exemples** : `Client`, `Commande`, `Produit`, `Entrepôt`, `Expédition`
- Chaque Object Type est adossé à **exactement un dataset** (backing dataset)
- L'ID du type d'objet ne peut pas être modifié après le premier déploiement
- Identifié par un `ontologyRid` stable et immutable ; les noms sont des alias mutables

#### 2. Properties (Colonnes / Attributs)

Attributs typés appartenant à un Object Type. Chaque propriété a un nom, un type, et des métadonnées (searchable, sortable, display name).

- **Analogie** : une colonne dans une table
- **Exemples** : `name` (String), `amount` (Double), `date` (Date), `status` (String), `geolocation` (GeoPoint)

**Types de base supportés :**

| Catégorie | Types |
|-----------|-------|
| **Texte / Booléens** | `String`, `Boolean` |
| **Numériques** | `Integer`, `Short`, `Byte`, `Long`, `Float`, `Double`, `Decimal` |
| **Temporels** | `Date`, `Timestamp` |
| **Géospatiaux** | `GeoPoint`/`Geohash`, `GeoShape`, `GeotimeSeriesReference` |
| **Complexes** | `Array` (pas de null ; pas de nested arrays en OSv2), `Struct` (pas de nesting ; champs ne peuvent pas être des arrays ; max 10 champs), `Vector` (pour embeddings ML) |
| **Spéciaux** | `Attachment`, `MediaReference`, `Timeseries`, `Marking`, `CipherText`/`Cipher` |

[CONTRADICTION] **Types Set et Map** : une source (Claude) liste `Set` et `Map` comme types supportés. Les autres sources ne les mentionnent pas dans les types de propriétés ontologiques et citent explicitement une liste "load-bearing" qui ne contient ni Set ni Map.

**Contraintes sur les types :**
- `Long` : problèmes de représentation JavaScript ; souvent recommandé d'utiliser String à la place
- `Decimal` : ne peut pas être primary key
- `Timestamp` : comme primary key est déconseillé
- `Array` : pas d'éléments null, pas de nested arrays en OSv2
- `Struct` : pas de nesting (profondeur 1), max 10 champs, types de champs limités, sémantiques de requête non-intuitives pour les arrays de structs (indexation ElasticSearch object field)

#### 3. Link Types (Foreign Keys / Relations)

Relations dirigées et typées entre Object Types. Chaque lien a un nom, une cardinalité, et peut porter ses propres propriétés.

- **Analogie** : une clé étrangère / un join entre tables
- **Exemples** : `"commandé par"`, `"contient"`, `"assigné à"`, `"expédié depuis"`
- **Cardinalités supportées** : 1:1, 1:N, N:1, M:N
- Les liens ne sont PAS stockés comme des edges dans un graph database — ils sont résolus au moment de la requête par jointure sur les colonnes de clé étrangère spécifiées dans les backing datasets
- L'UI auto-crée le lien inverse

[CONTRADICTION] **Résolution des liens** : une source affirme catégoriquement que les liens sont résolus "at query time by joining on foreign key columns." D'autres sources disent que les liens sont créés en ajoutant des backing datasources aux object types. Les sources s'accordent sur le fait que c'est un mécanisme relationnel (join), pas un graphe, mais le moment exact de la résolution fait débat.

#### 4. Action Types (Stored Procedures / Endpoints API)

Opérations typées qui mutent l'Ontologie. Les Actions sont le **SEUL moyen** d'écrire des données via la couche Ontologie. Elles incluent des règles de validation, des effets de bord, et un audit logging.

- **Analogie** : une stored procedure ou un endpoint API d'écriture
- **Exemples** : `"approuver commande"`, `"assigner tâche"`, `"escalader cas"`, `"mettre à jour statut"`
- **Composants** : paramètres (inputs requis), logique (créer/modifier/supprimer objets et liens), critères de soumission (règles métier), permissions, writeback dataset

#### 5. Interfaces (Classes Abstraites / Protocoles)

Types abstraits que les Object Types peuvent implémenter. Les Interfaces définissent un contrat (ensemble de propriétés et liens) que plusieurs Object Types partagent, permettant des requêtes et composants UI polymorphiques.

- **Analogie** : une interface Java ou un protocole Swift
- **Exemples** : `Trackable` (implémenté par Order, Shipment, Asset), `Assignable` (implémenté par Task, Incident), `HasLocation` (avec `latitude: Double`, `longitude: Double`)
- Non adossées à des datasets, non instanciables
- Propriétés d'interface : contraintes abstraites que les Object Types implémentants doivent mapper sur des propriétés concrètes
- Contraintes de link type : liens abstraits avec cardinalité (`ONE` ou `MANY`), pouvant être marqués `required`

#### 6. Functions (Colonnes Calculées / UDFs)

Computations TypeScript ou Python enregistrées dans l'Ontologie. Les Functions reçoivent des objets Ontologie typés en entrée et retournent des résultats typés. Appelables depuis les UIs, workflows, agents et autres fonctions.

- **Analogie** : une colonne calculée ou une User-Defined Function
- **Exemples** : `calculateRiskScore(client)`, `estimateDeliveryTime(shipment)`, `findNearestWarehouse(order)`
- Écrites en **TypeScript** dans un Functions Repository / Code Repository dédié
- L'Ontology Manager expose un "Function type view" mais les modifications se font dans le repository de code

### 4.2.2 Les 3 Couches

Les six primitives sont organisées en trois couches architecturales :

#### Couche 1 : SEMANTIC — WHAT — Le Modèle de Données

Définit les entités métier, leurs propriétés et leurs relations. C'est la colonne vertébrale structurelle. Répond à la question : "Qu'est-ce qui existe dans le monde ?"

- Définitions d'Object Types avec propriétés typées
- Définitions de Link Types avec contraintes de cardinalité
- Contrats d'Interface pour l'accès polymorphique
- Versioning de schéma avec identifiants stables (`ontologyRid`)

#### Couche 2 : KINETIC — HOW — Les Flux Temps Réel

Définit comment les données circulent dans le système et comment le système agit sur le monde. C'est la couche opérationnelle.

- Action Types avec règles de validation et effets de bord
- Functions (computations TypeScript/Python)
- Writeback vers les systèmes source (ERP, CRM, bases de données)
- Webhooks pour l'intégration event-driven
- Flux streaming temps réel (Flink-powered)

#### Couche 3 : DYNAMIC — GUARDRAILS — Sécurité & Gouvernance

Définit les contraintes qui gouvernent tout accès et toute mutation. Cette couche est pervasive — elle s'applique à chaque lecture, chaque écriture, chaque inférence IA, chaque rendu UI.

- RBAC (Role-Based Access Control) par objet, par propriété, par ligne
- Markings obligatoires (labels de classification qui voyagent avec les données)
- Audit logging complet de chaque accès et mutation
- Tracking de provenance de la source à la sortie dérivée
- Indexation temps réel pour la recherche et la découverte

### 4.2.3 Backend Services

| Service | Responsabilité | Détail technique |
|---------|---------------|------------------|
| **OMS** (Ontology Metadata Service) | Stockage de schéma | Stocke toutes les définitions : Object Types, Properties, Link Types, Action Types, Interfaces, Functions. Source unique de vérité pour "ce qui existe dans l'Ontologie." [CONFIRMED] |
| **Object Storage V2** | Persistance et indexation | Deux sous-composants : (1) **Data Funnel** — Pipeline batch : `génération de changelog` -> `merge avec edits` -> `build des artefacts de recherche` -> `cutover atomique vers le nouvel index`. (2) **Object Databases** — Stores indexés optimisés pour les lectures rapides. [CONFIRMED] |
| **OSS** (Object Set Service) | Moteur de requête | Gère toutes les opérations de lecture : requêtes de recherche, filtrage, agrégation, résolution d'Object Set. Un "Object Set" est une collection dynamique, évaluée paresseusement, d'objets matchant un prédicat — l'abstraction de requête fondamentale utilisée par toutes les UIs, APIs et agents IA. [CONFIRMED] |
| **Actions Service** | Écritures transactionnelles | Exécute toutes les mutations via l'Ontologie. Utilise la **concurrence optimiste** : les lectures sont lock-free, les écritures sont validées au moment du commit. Si un conflit est détecté, la transaction est rejetée et le client doit retenter. [CONFIRMED] |

**Pipeline Funnel — 5 étapes batch :**
1. **Source Read** — lire les dernières données du backing dataset
2. **Diff / Changelog Generation** — comparer avec la version précédente pour identifier les objets changés, ajoutés et supprimés
3. **Merge with User Edits** — appliquer le log d'edits pour résoudre les conflits entre données pipeline et modifications utilisateur
4. **Build Search Artifacts** — construire les documents Elasticsearch avec toutes les propriétés indexées, références de liens et champs calculés
5. **Atomic Cutover** — swapper l'ancien index avec le nouveau atomiquement

Pour les sources streaming (Flink), le Funnel opère en mode quasi temps réel avec mises à jour incrémentales.

### 4.2.4 Ontology Manager UI

#### Anatomie de l'Interface (3 zones)

L'Ontology Manager (OMA) est accessible depuis la sidebar de navigation de Foundry. C'est l'application centrale où les développeurs définissent le modèle de données.

| Zone | Contenu |
|------|---------|
| **Top bar** | Recherche globale sur les ressources ontologiques, création de nouvelles ressources ("+ Create" / "New"), switching/création de branches |
| **Sidebar gauche** | Navigateur de ressources avec vue "Discover" configurable (favoris, types récemment consultés, groupes). Arborescence hiérarchique de tous les Object Types, Link Types et Interfaces avec recherche. |
| **Zone centrale** | Panneau affichant la configuration de l'entité sélectionnée, avec onglets : Overview, Properties, Links/Datasources, Actions, Permissions, Interfaces |

[CONTRADICTION] **Localisation du bouton de création** : une source décrit le bouton dans la top bar, une autre dans le toolbar, une troisième en haut à droite de la homepage avec un dropdown "New". Les trois décrivent le même workflow mais situent le bouton différemment dans l'UI.

**Vues d'entités distinctes :**
- **Object type view** : sous-sidebar gauche avec pages (Overview, Properties, Datasources, Interfaces) et panneau droit avec le contenu de la page sélectionnée
- **Property editor view** : interface d'édition dédiée ouverte en sélectionnant une propriété
- **Link type view** : ouverte depuis le graphe de types de liens, avec pages Overview/Datasources
- **Action type view** et **Function type view** : chacune avec ses propres onglets d'observabilité ; les fonctions sont éditées dans un code repository, pas en inline

**Modèle mental** : l'Ontology Manager se comporte comme un **"schema IDE git-branch-aware"** où tout est staged puis commité dans l'ontologie.

#### Création d'un Object Type — Step-by-Step (6 étapes)

Palantir documente deux méthodes : un **assistant guidé** (chemin principal) et une **complétion manuelle** si on sort tôt de l'assistant.

1. **Cliquer** sur "New > Create object type" / "+ Create Object Type" depuis l'Ontology Manager
2. **Entrer un display name** (ex: "Customer") et un **API name** (auto-généré, ex: `customer`, mais éditable). Optionnellement choisir une icône et écrire une description
3. **Sélectionner un backing dataset** — parcourir ou rechercher dans le catalogue de données Foundry et pointer vers un dataset. **Chaque Object Type est adossé à exactement un dataset.** Si on n'a pas encore de dataset, Foundry peut générer un dataset vide à l'emplacement choisi (Object Storage V2 uniquement)
4. **Définir le primary key** — sélectionner la colonne qui identifie uniquement chaque instance d'objet. Le primary key doit être unique, déterministe, pas aléatoire. Le timestamp comme primary key est explicitement déconseillé
5. **Mapper les colonnes vers des propriétés** — l'UI auto-détecte les colonnes et suggère des mappings. Un bouton "Add all unmapped columns as new properties" infère IDs, display names et base types depuis le schema du dataset source. L'éditeur a deux panneaux : colonnes datasource à gauche, propriétés mappées à droite
6. **Configurer le title key** — la propriété qui sert de nom d'affichage dans les UIs (ex: `full_name` pour un Employee)

**Étapes optionnelles :**
- Générer des actions standard — l'assistant peut auto-créer des Action Types edit/create/delete et les assigner à un utilisateur/groupe
- Choisir un projet d'enregistrement et cliquer "Create" (cela stage les changements seulement). Puis cliquer **"Save"** en haut à droite de l'Ontology Manager pour appliquer à l'ontologie

**Si on quitte l'assistant tôt** : l'object type reste "unsaved" jusqu'à ce qu'on complète manuellement la checklist : ajouter metadata, ajouter un backing datasource, ajouter des propriétés, mapper les propriétés, configurer primary et title keys.

#### Définition des Properties (types disponibles)

**Éditeur de métadonnées de propriété :** display name, description, statut (experimental/active/deprecated), API name, désignation de clé (title/primary), formatage de valeur, formatage conditionnel, type classes, render hints (toggles searchable/sortable affectant le comportement d'indexation), et visibilité (prominent/hidden).

L'édition peut être faite individuellement ou en **bulk** (changement de base type, ajout/suppression de type classes, render hints, visibilité, formatage).

**Struct** : créé en choisissant "Struct" comme base type, en sélectionnant une colonne backing, puis en ajoutant des champs dans une section "Struct fields". Permet des champs JSON-like structurés — ex: une struct Address avec `street`, `city`, `zip`. Mais n'est **pas** un type "nested JSON" général : c'est une feature de schema contrainte (profondeur 1, max 10 champs).

**Media references** : "juste un base type", mais nécessite que le dataset de support contienne une colonne de référence media et que l'object type ait une media source configurée dans son onglet Capabilities pointant vers le media set correspondant.

#### Création des Links (cardinalité)

**Création :** Naviguer vers Ontology Manager > `New > Link type`, ou depuis la page Overview d'un object type > "Create new link type" depuis le graphe de types de liens.

**Cardinalités supportées :** 1:1, 1:N, N:1, M:N

**Mécanique des clés étrangères :**
- Pour 1:1 ou M:1 : définir une **foreign key** sur un object type qui réfère au **primary key** de l'autre. Exemple : `Flight.tailNumber` (FK) -> `Aircraft.tailNumber` (PK)
- Pour M:N : un **troisième backing dataset** (table de jonction) est requis. Ce dataset ne nécessite que les colonnes primary key des deux object types. Chaque ligne représente une instance de lien.

**Object-backed link types** : construct de modélisation de première classe. On peut représenter une relation comme son propre object type pour stocker des métadonnées sur la relation elle-même (exemple : un objet Flight Manifest liant Aircraft et Flight, avec des propriétés supplémentaires comme Pilot). Règle : "si vous avez besoin d'attributs sur l'edge, Foundry vous dit de promouvoir l'edge en un object-backed link."

**Dans les bindings TypeScript** : le côté "1" donne un `SingleLink` et on appelle `get()` ou `getAsync()`.

L'UI auto-crée le lien inverse. Après soumission, il faut **sauvegarder dans l'Ontology Manager** pour appliquer.

**Convention de nommage API** : côté pluriel en pluriel (`subordinates`, pas `subordinate`). Noms sémantiques distincts pour liens multiples entre mêmes types.

#### Interfaces (types abstraits)

**Création :**
1. Sélectionner New > Interface (ou via la page Interfaces)
2. Fournir display name et API name, description optionnelle et icône
3. Ajouter des propriétés à l'interface, marquer chacune `required` ou `optional`

**Propriétés d'interface** : contraintes de propriétés abstraites que les object types implémentants doivent mapper sur des propriétés concrètes.

**Contraintes de link type d'interface** : liens abstraits avec une cardinalité (`ONE` ou `MANY`), description, API name, et une entité liée qui peut être une autre interface ou un object type concret. Flag `required` pour indiquer si chaque object type implémentant doit fournir au moins une implémentation d'un lien donné.

**Exemple** : une interface `Facility` déclare un lien optionnel one-to-many vers `Airline`. `Airport` et `Seaport` peuvent tous deux implémenter `Facility`, chacun fournissant son propre lien concret vers `Airline`.

**Implémentation :**
1. Depuis l'onglet Interfaces d'un object type, sélectionner "Implement new interface"
2. Choisir l'interface, puis mapper les propriétés requises de l'interface sur des propriétés existantes de l'objet (les propriétés optionnelles peuvent être omises)
3. Si l'interface déclare des contraintes de link type requis, mapper des link types qui satisfont chaque contrainte

**Cas d'usage concret** : un widget map Workshop peut afficher tous les objets "HasLocation" (interface avec `latitude: Double`, `longitude: Double`) quel que soit le type concret — cela active les requêtes polymorphiques.

**Limitation** : l'implémentation des interfaces dans Pipeline Builder supporte le mapping de propriétés, mais **ne supporte pas le mapping de contraintes de link type** ; cela doit être fait dans Ontology Manager.

#### Functions (TypeScript computed)

**Environnement** : les Functions sont écrites en **TypeScript** dans un Functions Repository / Code Repository dédié.

**API TypeScript v1 :**

```typescript
import { Function } from "@foundry/functions-api";
import { Objects, Customer } from "@foundry/ontology-api";

export class CustomerFunctions {
  @Function()
  public getCustomerOrderCount(customer: Customer): Integer {
    const orders = customer.orders.all();  // traverse un lien
    return orders.length;
  }

  @Function()
  public getHighValueCustomers(): Customer[] {
    return Objects.search()
      .customer()
      .filter(c => c.totalSpend.gt(10000))
      .all();
  }
}
```

Les fonctions utilisent le decorator `@Function()`, l'accès type-safe auto-généré à l'ontologie via `@foundry/ontology-api`, la traversée de liens, et peuvent être exposées comme propriétés computées sur des Object Types ou comme handlers d'Actions via `@Action()`.

**API TypeScript v2** : utilise `@osdk/functions` avec `createEditBatch`, `Edits.Object<T>` et `Edits.Link<T>` types pour les edits batch.

**Edit Functions** : annotées avec `@OntologyEditFunction()` et `@Edits(ObjectType)`. Peuvent créer des objets (`Objects.create().ticket(primaryKey)`), modifier des propriétés (`employee.lastName = newName`), set/remove links, et supprimer des objets.

**Capacités** : lecture de propriétés, traversée de liens, edits ontologiques, résultat utilisable dans Workshop et Actions. L'Object Table de Workshop supporte les "derived columns generated on-the-fly via a Function".

**Gestion des timestamps** : utiliser `Timestamp.fromISOString(...)` depuis l'API functions de Foundry.

Les fonctions alimentent les Action Types (writeback), les valeurs computées Workshop, et les intégrations AIP Logic.

### 4.2.5 Decision Framework — Object Type vs Property vs Link vs Struct

**Analogie fondamentale :** Object Type = Dataset, Object = Row, Property = Column, Link = Join

**Heuristique FDE :** "Can someone walk up to this entity and ask questions about it in isolation?" Si oui, c'est un Object Type. Variante : "Will someone ever search for, filter on, or take an action on this entity independently?" Si oui -> Object Type.

#### Quand créer un Object Type

- L'entité a sa propre identité et cycle de vie (primary key stable, créée/modifiée indépendamment)
- L'entité a besoin d'être liée depuis plusieurs endroits
- La "relation" elle-même a besoin d'attributs -> object-backed link types
- L'entité a ses propres propriétés indépendamment consultées/filtrées
- Les utilisateurs doivent prendre des actions dessus indépendamment
- Elle a **plus de 2-3 attributs**
- Elle a besoin de permissions indépendantes

#### Quand garder comme Property

- Attribut concernant uniquement l'objet parent, pas de cycle de vie propre
- Attribut simple de 1-3 champs, unique à son parent, jamais requêté indépendamment, change toujours avec le parent
- On bénéficie de render hints, formatage et contrôles de searchabilité au niveau propriété

#### Quand utiliser un Link

- La relation est navigationnelle et queryable comme une relation, pas juste un string foreign key
- L'entité est partagée entre plusieurs parents

#### Quand utiliser un Struct

- Groupe borné de champs imbriqués qui se comporte comme "une propriété"
- Groupe logiquement lié de champs appartenant à l'objet parent mais avec structure nestée
- On peut vivre avec les contraintes strictes : profondeur 1 (pas de nesting), max 10 champs, types de champs limités, sémantiques de requête non-intuitives pour les arrays de structs

#### L'exemple Customer Address

**Adresse comme simple attribut (Property) :** quand l'adresse est single-valued, change rarement, n'est pas une entité indépendante. Implémentation : quelques propriétés comme `street`, `postcode`, `city`, `country` mappées directement depuis le backing dataset.

**Adresse comme sous-structure bornée (Struct) :** quand on veut "adresse" comme un seul champ conceptuel mais avec des composants structurés, en restant dans les contraintes de struct. Si les adresses n'ont pas besoin de cycle de vie indépendant, liens ou actions.

**Adresse comme entité de première classe (Object Type lié) :** quand les adresses ont leur propre cycle de vie — adresses multiples par client, historique, workflows de validation, géo-enrichissement, déduplication, ou permissions au niveau adresse. Lien Customer <-> Address ; la relation peut être "one-to-many" ou "many-to-many" si partagée.

**Extra Foundry** : si on a besoin de metadata sur la relation elle-même (ex: "address type", "valid from/to", "verified by", "source system"), les object-backed links sont le pattern canonique.

#### Principes de design FDE

- **Start from user workflows, not data models**
- **Ne pas sur-normaliser** — Foundry favorise la **dénormalisation** pour la performance de requête
- **Choisir des primary keys stables et immutables** ; les composite keys doivent être concaténés en une seule colonne
- **Linker avec parcimonie** — chaque lien ajoute de la complexité de requête
- **Utiliser les interfaces** pour les préoccupations transversales plutôt que dupliquer des propriétés
- Modeler pour les **workflows opérationnels d'abord**, puis pour l'analytique

### 4.2.6 Schema Evolution

#### OSv1 vs OSv2

**OSv1 (Phonograph)** : ne peut PAS migrer les user edits en cas de changements breaking ; les changements de schema sont découragés et peuvent nécessiter un unregister/reregister des datasources, risquant la perte d'historique d'edits.

**OSv2** : introduit un **framework de migration intégré** qui détecte automatiquement les changements breaking, affiche un warning, introduit un onglet Migrations dans le flux "Review changes", et bloque la sauvegarde jusqu'à ce qu'une option de migration soit spécifiée.

[CONTRADICTION] **Existence d'un outil de migration** : une source affirme que "Foundry's ontology has no built-in migration tool comparable to Flyway or Liquibase. Schema changes are manual." D'autres sources décrivent un framework de migration intégré dans OSv2 détaillé. La contradiction s'explique probablement par le fait que la première source décrit l'état général/OSv1 tandis que les autres décrivent la fonctionnalité OSv2 spécifique.

#### Breaking vs Non-Breaking Changes

**Changements non-breaking (pas de migration nécessaire) :**
- Ajouter une nouvelle propriété
- Changer display names, descriptions, title key, render hints, type classes, visibilité
- Réordonner les propriétés
- Supprimer ou changer des champs qui n'ont jamais reçu d'edits

**Changements breaking :**
- Changer les datasources d'entrée
- Changer le primary key
- Changer le type d'une propriété
- Changer le property ID si la propriété a des edits
- Supprimer des propriétés éditées ou des champs de struct
- Changer le type d'un champ de struct

#### Framework de migration OSv2

Quand on fait un changement breaking, l'Ontology Manager le détecte automatiquement et bloque la sauvegarde jusqu'à ce qu'on sélectionne une migration depuis l'onglet **Migrations** :

| Migration | Cas d'usage |
|-----------|-------------|
| **Drop all property edits** | Supprimer une propriété sans remplacement |
| **Drop all struct field edits** | Restructuration de struct |
| **Drop all edits** | Reset complet vers l'état datasource |
| **Move edits** | Renommer une propriété ou déplacer vers un nouveau backing dataset |
| **Cast property to new type** | Changer `String` -> `Integer`, etc. (~30 conversions supportées) |
| **Move struct field edits** | Restructuration au sein d'un struct |
| **Revert migration** | Annuler une migration précédemment appliquée |

**Limite** : max 500 migrations de schema à la fois ; les migrations de propriété primary key ne sont pas supportées par le framework.

#### Replacement Pipeline Pattern

Quand on sauvegarde un changement breaking :
1. Une nouvelle version de schema est créée en backend
2. Un **"replacement Funnel batch pipeline"** est orchestré pour mettre à jour l'index de l'object type
3. La nouvelle version devient queryable une fois le remplacement terminé et la nouvelle version déclarée entièrement hydratée par les object databases

Ce mécanisme est **versionné via un pipeline de rebuild d'index**, pas une mutation in-place.

#### Pattern Side-by-Side (pour changements majeurs)

Pour les cas hors OSv2 ou pour des changements majeurs :
1. Créer une nouvelle version du backing dataset avec le nouveau schema
2. Créer un nouvel Object Type (ex: `CustomerV2`)
3. Migrer tous les consommateurs (Workshop apps, Functions, OSDK clients)
4. Tester dans une branche de développement
5. Basculer et déprécier l'ancien type

#### Branching et Ontology-as-Code

Foundry supporte le **branching de datasets et de code** — on peut faire des changements de schema sur une branche, pointer l'Ontology Manager vers cette branche pour tester, valider, puis merger.

Pour les utilisateurs avancés, les définitions de schema ontologique peuvent être **exportées en JSON**, éditées en externe, et réimportées, permettant des workflows "ontology as code". C'est puissant mais opérationnellement risqué : on bypass les guardrails UI.

---

## 4.3 Pipeline Builder & Code Repositories

### 4.3.1 Pipeline Builder (Visuel)

Pipeline Builder est un constructeur **basé sur un graphe DAG** avec une vue canvas comme élément principal. [CONFIRMED]

#### UI : canvas, noeuds, connexions

| Zone | Contenu |
|------|---------|
| **Panneau/sidebar gauche** | Parcours/recherche de datasets d'entrée |
| **Canvas central** | Noeuds connectés par des edges montrant le flux de données, avec outils de panning/drag-select/layout. Les utilisateurs tirent des cercles de sortie blancs pour dessiner des connexions |
| **Panneau/sidebar droit** | Configuration du noeud sélectionné ; panneau Outputs montrant datasets outputs + outputs orientées ontologie (object types et link types) |
| **Panneau de preview en bas** | Échantillonnage des données du noeud sélectionné ; la preview se met à jour en temps réel |

**Supports additionnels :** Folders, Color Groups, Text Nodes, Checkpoints, Job Groups.

#### 80+ transforms disponibles (par catégorie)

**Types de noeuds Input :**
- Foundry datasets (batch ou streaming)
- Données générées/synthétiques
- Dataset syncs

**Transforms (70+ disponibles) :**

| Catégorie | Noeuds |
|-----------|--------|
| **Structural** | Filter (conditions AND/OR composées), Sort, Limit, Top rows, Drop duplicates, Deduplicate (avec stratégie de ranking) |
| **Jointures** | Inner, Left, Right, Full Outer, Cross, Semi, Anti, Mapping, KNN |
| **Agrégation/Windowing** | Aggregate (SUM, COUNT, AVG, MIN, MAX, COUNT DISTINCT, STDDEV, PERCENTILE, COLLECT_LIST — group-by, batch seulement), Aggregate over window, Project over window, Window Functions (ROW_NUMBER, RANK, LAG, LEAD, running aggregates) |
| **Reshaping** | Pivot (valeurs pivot fournies avant runtime pour schema connu), Unpivot, Flatten/Explode (pour arrays), Array elements to columns, Flatten struct |
| **Combinaison** | Union by name (retient les doublons, combine toutes les lignes), Narrow/Wide union |
| **Colonnes** | Select/Drop columns, Rename, Add Column (expression builder avec manipulation string, math, fonctions date, CASE WHEN), Cast Types, Normalize column names |
| **Nettoyage** | Clean String, Trim Whitespace, Cast to Timestamp, Normalize Column Names |
| **Géospatial** | Geo distance join, Geometry intersection join, Geometry KNN join |
| **Parsing de fichiers** | CSV, JSON, Excel, XML, Parse shapefile |
| **Avancé** | Split on condition, Pattern mining, Time-bounded drop duplicates, noeuds LLM (AI-powered data enrichment), OCR transforms |

**Types de noeuds Output :**
- Foundry dataset
- Media set
- Virtual table
- Ontology entity outputs (object types et link types)
- Geotemporal series sync

#### 7 Types de Joins

1. **Inner** — lignes matchant dans les deux tables
2. **Left** — toutes les lignes de gauche + matches de droite
3. **Right** — toutes les lignes de droite + matches de gauche
4. **Full Outer** — toutes les lignes des deux tables
5. **Cross** — produit cartésien
6. **Semi** — lignes de gauche qui ont un match à droite (pas de colonnes droite)
7. **Anti** — lignes de gauche qui n'ont PAS de match à droite

Les joins incluent des previews et un onglet Errors.

#### 300+ Fonctions d'Expression (500+ selon certaines sources)

**Catégories :**
- Arithmétique (add, subtract, multiply, divide, modulo, abs, ceil, floor, round, power, sqrt, log)
- String (concat, substring, trim, upper, lower, replace, split, regex_extract, regex_replace, length, contains, starts_with, ends_with, pad, reverse)
- Array (array_contains, array_size, array_sort, array_distinct, array_union, array_intersect, array_except, array_element_at, array_flatten, array_zip)
- Date/Time (date_add, date_sub, date_diff, date_format, date_trunc, extract, current_date, current_timestamp, months_between, to_date, to_timestamp)
- Géospatial (geo_distance, geo_within, geo_intersection, geo_buffer)
- Type Casting (cast, to_string, to_integer, to_double, to_boolean, to_date, to_timestamp)
- Avancé (Parse JSON, Cipher encrypt, Text to embeddings LLM-powered, Case/When, Coalesce, If/Else, Levenshtein distance)

**Features additionnelles :**
- Paramètres et fonctions réutilisables
- Auto-naming des noeuds selon leur logique (AI feature)
- Auto-génération d'expressions regex depuis des descriptions en langage naturel (AI feature)
- Contrôle de version intégré (branching comme git). Onglet Changes avec diff vs main, merge quand prêt
- Data expectations (health checks et tests unitaires)
- Stratégies d'échantillonnage

[CONTRADICTION] **Mixing visuel et code dans Pipeline Builder** : une source affirme que "Mixing visual and code nodes is fully supported" via un "Custom Code node" avec éditeur Monaco. D'autres sources disent explicitement le contraire : "Not inside a single Pipeline Builder transform board." Le mixing se fait "at the dataset boundary, not inside a node." Pipeline Builder est l'outil "no-code" ; Code Repositories est pour les stages de code spécialisé. Cette contradiction est significative — le consensus est que le mixing se fait au niveau dataset boundary.

### 4.3.2 Code Repositories

IDE web basé sur Git pour les utilisateurs nécessitant un contrôle programmatique au-delà du Pipeline Builder visuel. [CONFIRMED]

**Langages supportés :**
- **Python** (PySpark, Pandas, Polars, DuckDB)
- **Java**
- **SQL**
- **Mesa** (langage propriétaire de Palantir pour la résolution de contraintes)

#### L'API @transform (avec exemples de code)

L'API Python transforms Foundry (librairie `transforms`, open-sourcée sous `palantir/transforms-python`) est basée sur des decorators.

**`@transform`** — la forme la plus générale. Injecte des objets `TransformInput` et `TransformOutput` :

```python
from transforms.api import transform, Input, Output

@transform(
    source_a=Input("/datasets/source_a"),
    source_b=Input("/datasets/source_b"),
    output=Output("/datasets/joined_output")
)
def my_transform(source_a, source_b, output):
    df_a = source_a.dataframe()
    df_b = source_b.dataframe()
    joined = df_a.join(df_b, on="customer_id", how="left")
    cleaned = joined.filter(joined.status != "CANCELLED")
    output.write_dataframe(cleaned)
```

**`@transform_df`** — convenience wrapper qui injecte/retourne des DataFrames directement :

```python
from transforms.api import transform_df, Input, Output
from pyspark.sql import functions as F

@transform_df(
    Output("/Company/Ontology/Backing Datasets/clean_customer_orders"),
    raw_orders=Input("/Company/Data/Raw/SAP/orders"),
    customer_master=Input("/Company/Data/Clean/customer_master"),
)
def compute_clean_customer_orders(raw_orders, customer_master):
    orders_clean = (
        raw_orders
        .filter(F.col("order_status") != "CANCELLED")
        .withColumn("order_date", F.to_date("order_date_str", "yyyyMMdd"))
        .withColumn("order_amount", F.col("order_amount_raw").cast("double"))
    )
    result = orders_clean.join(
        customer_master.select("customer_id", "customer_name", "segment"),
        on="customer_id", how="left"
    )
    return result.withColumn("is_high_value",
        F.when(F.col("order_amount") > 10000, True).otherwise(False))
```

**`@transform_pandas`** — même chose mais pour des Pandas DataFrames.

**Objets Input/Output :**
- `Input(path, alias, branch, description)` — `.dataframe()`, `.filesystem()` (read-only FileSystem), `.rid`, `.branch`, `.txrange`
- `Output(path, alias, sever_permissions, description)` — `.write_dataframe(df)`, `.set_mode("replace"|"modify")`, `.abort()`, `.filesystem()`

#### Incremental Transforms

Le traitement incrémental est une feature de première classe : il utilise l'historique de build des transforms pour éviter de recalculer un output entier à chaque exécution.

**Decorator `@incremental()`** :

```python
from transforms.api import transform, Input, Output, incremental

@incremental()
@transform(
    output=Output("/path/to/output"),
    source=Input("/path/to/source"),
)
def incremental_pipeline(source, output):
    new_data = source.dataframe()  # Seulement les nouvelles lignes depuis le dernier run
    output.write_dataframe(new_data, mode="append")
```

**Modes de sortie :**
- `append` — ajoute les nouvelles lignes
- `replace` — retombe au full recompute
- `modify` — upsert

**Mécanismes clés :**
- `ctx.is_incremental` : boolean indiquant si incrémental ou snapshot
- `source.dataframe(mode="current")` : lit le snapshot complet
- `source.dataframe(mode="previous")` : lit le dernier état commis
- `require_incremental=True` : empêche un full recompute accidentel
- `semantic_version` : l'incrémenter force un full snapshot recompute (utile après des changements de logique)
- Cascading snapshots : si une quelconque input est snapshotted, le transform incrémental se snapshotte automatiquement

**Contraintes :**
- Foundry interdit explicitement que l'input et l'output soient le même dataset (éviter les dépendances cycliques)
- Le "simple default" ne fonctionne en sécurité que quand les lignes output ajoutées sont purement une fonction des lignes input ajoutées
- Pour une logique complexe (joins, aggregations, distinct), utiliser incrémental avec le decorator `transform()` complet

**Decorator `@configure`** : contrôle les profils de ressources (nombre d'executors, mémoire) et peut différer entre les runs snapshot et incrémental.

#### Testing et CI

**Unit tests** : Foundry supporte les tests **pytest** pour les repositories Python (batch pipelines uniquement) et peut exécuter les tests comme partie des checks.

**Module `transforms.testing`** : fournit `mock_transform()` pour les tests unitaires avec des sessions Spark locales.

**Data quality checks** : l'objet `Check` permet de définir des validations sur les outputs :

```python
@transform_df(
    Output("/path/to/output", checks=[
        Check(lambda df: df.filter(df.amount < 0).count() == 0,
              "No negative amounts", on_error=CheckSeverity.WARN),
        Check(lambda df: df.count() > 0,
              "Output is non-empty", on_error=CheckSeverity.FAIL),
    ]),
    source=Input("/path/to/source"),
)
def my_checked_transform(source):
    return source.filter(source.status == "active")
```

**CI intégré** : pousser sur une branche exécute pytest automatiquement, et les PRs ne peuvent pas merger si les tests échouent. Mécaniques CI : `condaPackRun`, environment caching, et style checks optionnels via Gradle plugins. La santé du pipeline est traitée comme partie du processus de build et release.

### 4.3.3 Data Lineage

#### Traçabilité Automatique

Foundry suit automatiquement le lineage au niveau **dataset-transform-dataset**. Chaque déclaration `Input()`/`Output()` crée un edge de lineage. Il n'y a **pas d'opt-in** — ce tracking est obligatoire. [CONFIRMED]

Au niveau transaction, Foundry enregistre :
- Quelles transactions d'entrée ont été consommées
- Quel code de transform (avec git commit hash) a été exécuté
- Quelles transactions de sortie ont été produites

#### Graph de Lineage

Data Lineage est une application interactive pour visualiser comment les datasets circulent dans Foundry.

**Éléments UI :**
- Graphe de lineage interactif (DAG horizontal) zoomable/pannable
- Chaque noeud = une ressource Foundry (dataset, transform, object type)
- Paramètres de branche
- Panneau latéral : Search & Browse, Properties and Histogram, Manage Builds, Manage Schedules, Related Artifacts
- Panneau de détails de noeud : nom, owner, last build time, health status
- Outils de graphe et "Save graph"

**Navigation :**
- Rechercher un dataset, object type ou ressource et l'ajouter comme noeud
- Cliquer sur les flèches gauche/droite pour expander parents (ancêtres) ou enfants (descendants)
- Outil Expand avec contrôles de niveau — un niveau, plusieurs niveaux, ou jusqu'aux sources brutes
- "Find relation between two nodes" montre tous les noeuds intermédiaires
- Coloration par type de transform, health status, groupements custom, ou couleurs assignées manuellement
- Outils de layout : automatique, hiérarchique, vertical, par niveau, ou par groupe de couleur
- Outil Find pour chercher des noeuds ou noms de colonnes dans les datasets sur le graphe
- Export SVG

On peut **déclencher des builds et définir des schedules** directement depuis le graphe de lineage.

**Monocle** : nom interne de Palantir pour l'outil de lineage/visualisation d'architecture étendu couvrant le stack opérationnel complet (flux data-to-ontology, actions et logique, dépendances applicatives, santé des pipelines).

[CONTRADICTION] **Column-level lineage** : une source affirme que le lineage au niveau colonne est "inféré en parsant le Catalyst logical plan de Spark" et que pour Pipeline Builder "each visual node's column flow is tracked explicitly." D'autres sources disent que la fonctionnalité "find datasets with a given column" existe (recherche column-aware), mais le lineage au niveau cellule ou ligne n'est PAS décrit comme une feature standard.

#### Interaction avec les Markings de Sécurité

Les **markings** sont le mécanisme de contrôle d'accès obligatoire de Foundry.

**Propagation automatique** : si Source A porte "SENSITIVE" et Source B porte "CONFIDENTIAL", leur output de join **hérite automatiquement des deux markings**. C'est enforcé au niveau plateforme — un développeur ne peut pas manuellement baisser la classification d'un dataset dérivé.

Data Lineage peut **simuler l'impact de changements de markings** et indique les noeuds qui "stop propagating markings" via du code.

**Mécanique de retrait** : `stop_propagating` et `stop_requiring` sont des propriétés de transform input et ne peuvent pas être ajoutées sur les outputs.

**Accès restreint** : les utilisateurs sans accès aux datasets upstream voient ces noeuds comme des placeholders "restricted".

**Déclassification** : les transforms de "déclassification" approuvés (ex: pipelines d'anonymisation) peuvent réduire les markings, mais nécessitent une approbation de gouvernance explicite et sont logués dans un audit trail immutable.

**Pipeline rollback** : utilise la provenance de données d'une transaction de dataset upstream pour identifier les datasets et transactions downstream et calculer un état de rollback. UX : sélectionner un dataset dans un graphe de lineage, choisir une branche, sélectionner une transaction dans History, puis "Rollback to transaction".

### 4.3.4 Scheduling

Le scheduling Foundry est **dataset-centric** : les schedules exécutent des builds pour garder les pipelines à jour.

**Types de déclencheurs :**

| Type | Description |
|------|-------------|
| **Time-based (Cron)** | Expressions cron standard (5 champs) + fuseau horaire. Constructeur cron visuel dans l'onglet Builds. Sélecteur hourly/daily/weekly/monthly. GUI + prompt en langage naturel AIP pour générer le cron. |
| **Event-driven** | Se déclenche quand des datasets upstream spécifiques sont mis à jour ("Build on upstream change"). Crée des chaînes de build en cascade. |
| **Logique mise à jour** | Se déclenche quand la logique de transform a été mise à jour. |
| **Compound triggers** | AND ("All of these triggers") ou OR ("Any of these triggers") — combinaison de toute condition. |
| **Hybride** | Event-based avec fallback timer. |
| **Manuel** | Bouton "Build" pour une exécution ad-hoc. |

**Types de build :** Single build, Full build (récursif amont), Connecting build (chemin entre inputs spécifiés et outputs cibles).

**Cibles de schedule** : un seul dataset, dependencies, dependents, datasets connectant deux datasets, ou combinaisons.

**Point d'entrée UI** : depuis un dataset preview > Actions > "Manage Schedules", ou depuis Data Lineage, ou le Build Schedules UI.

**Dependency resolver** : Foundry résout automatiquement les upstream datasets et les build dans le bon ordre. Les transforms indépendants s'exécutent en **parallèle** quand "Allow parallel builds" est activé.

**Retry logic** et alerting sont configurables.

### 4.3.5 Data Connectors

#### 400+ Connecteurs

Couvrant bases de données, applications SaaS, stockage cloud et systèmes enterprise.

#### 3 Modes d'Architecture

| Mode | Description | Cas d'usage |
|------|-------------|-------------|
| **Foundry Worker (Cloud-Side)** | Recommandé pour systèmes accessibles cloud. Traitement sur infrastructure compute gérée de Foundry. | Cloud databases, SaaS APIs, object storage (S3, GCS, ADLS) |
| **Foundry Worker avec Agent Proxy** | Recommandé pour on-prem/réseaux privés. Agent léger sur host Linux client (RHEL 8+, Ubuntu 22.04+) agit comme tunnel réseau uniquement ; tout le compute reste sur les workers Foundry. | On-premise databases behind firewalls, VPN-protected systems |
| **Agent Worker (legacy/air-gapped)** | L'agent exécute le compute sur le host client. Pour syncs fichiers spécifiques, micro-batching, ou filtrage lourd avant sortie du réseau. | Air-gapped government/military environments, SCADA/ICS networks |

**Installation agent :** Download depuis Foundry, installation sur host Linux 64-bit, enregistrement automatique, configuration certificat si proxy. Config dans `<agent-manager-install-directory>/var/conf/runtime.yml`.

#### SAP Certified Add-On

**Palantir Foundry Connector 2.0 for SAP Applications** :
- Installation via SAINT
- Développé avec Diskover Limited
- Supporte S/4HANA, ECC, Business Warehouse, SLT Replication Server
- Trois composants : PALANTIR (objets partagés), PALCONN (connecteur), PALODATA (optionnel, SLT OData APIs)
- Intégration SAP SLT pour **change data capture (CDC)** via triggers base de données

#### Connecteurs par catégorie

**Bases de données SQL (JDBC) :** Amazon Athena, Hive, IBM Db2, Informix, MariaDB, MSSQL, MySQL, Oracle, PostgreSQL, SQLite, Sybase, Vertica + connecteur JDBC custom.

**SaaS :** Salesforce (sync bidirectionnel, objets standard et custom), et 400+ autres.

**Avancé :** Webhooks, Listeners (Google Pub/Sub, Jira, Slack), External Connections from Code (compute pushdown), Virtual Tables, Private Link (AWS/Azure/GCP), Streaming syncs.

**Temps de connexion typique :** non publiquement documenté avec précision, mais les bootcamps de 1-5 jours incluent la connexion aux données, suggérant des heures à quelques jours pour les connecteurs standard.

**Failure modes :** retry logic configurable, alerting, detection de datasets obsolètes via Data Lineage.

---

## 4.4 Workshop — Application Builder

### 4.4.1 UI & Widgets

Workshop est un **constructeur d'applications no-code basé sur un canvas** avec un système de grille/layout. [CONFIRMED]

**Layout :**
- **Sidebar gauche** : listing des widgets par catégorie
- **Canvas central** : drag-and-drop pour placer les widgets dans un module layout avec sections
- **Panneau de configuration droit** : configuration du widget sélectionné
- **Mode preview** pour tester
- **Top toolbar** : contrôles pour ajouter des widgets, gérer les variables et previewer

Les applications supportent **plusieurs pages, modules réutilisables et visibilité basée sur les rôles**.

#### 50+ Widgets en 6 Catégories (liste complète)

**1. Widgets d'Affichage de Base (Core Display)**

| Widget | Description |
|--------|-------------|
| **Object Table** | Affichage tabulaire. Supports : sélection de colonnes (y compris time series), colonnes dérivées de Functions, tri simple/multiple, largeurs configurables, édition inline (writeback au niveau cellule), événements de sélection de ligne, actions clic droit personnalisées |
| **Object List** | Liste déroulante de cartes. Multi-select toggle, réordonnancement drag-and-drop, propriétés configurables par carte |
| **Object View** | Page de détail pour un objet unique. Mode "full" (pleine page) ou "panel" (sidebar). Support d'interface de configuration pour passer des variables |
| **Property List** | Propriétés en format clé-valeur |
| **Links** | Objets liés pour un objet donné |
| **Object Set Title** | Titre résumant le set d'objets courant (ex. "47 Flights") |
| **Details Panel** | Panneau de détails d'un objet |
| **Card Sets** | Ensembles de cartes |

**2. Widgets de Visualisation**

| Widget | Description |
|--------|-------------|
| **Chart XY** | Bar, line, scatter. Configuré par ajout de "layers" ; bar chart supporte "Stacked", "Percentage", "Grouped" |
| **Pie Chart** | Pie ou donut, regroupé par type de propriété |
| **Waterfall Chart** | Graphique en cascade |
| **Vega Chart** | Visualisations entièrement personnalisables via grammaire JSON Vega/Vega-Lite (échappatoire pour tout type de graphique) |
| **Map** | Géospatial via MapboxGL. Deux modes : configuration locale ou import de Map Template. Supporte clustering, heatmaps, sélection interactive |
| **Gantt Chart** | Événements dans une vue Gantt interactive. Utilisations : planification, allocation de ressources |
| **Pivot Table** | Groupement dynamique et agrégation. Supports : groupement par lignes (1+ propriétés), groupement par colonnes (max 1 propriété), groupement date dynamique (jour/semaine/mois/année), agrégations (count, cardinality, average, max, min, sum) |
| **Timeline** | Événements sur axe temporel horizontal |
| **KPI / Metric Card** | KPI configurable, souvent Function-backed |
| **Stepper** | Suivi de progression d'une tâche à travers des étapes |
| **Status Tracker** | Statuts d'un processus sur vue timeline |
| **Markdown** | Rendu de texte Markdown |

**3. Widgets Media**

| Widget | Description |
|--------|-------------|
| **Media Preview** | Images, audio, vidéo, documents (URL, RID Foundry, Base64) |
| **PDF Viewer** | Rendu PDF avec recherche par mots-clés |
| **Video Display** | Lecture vidéo |
| **Audio and Transcription Display** | Lecture audio + affichage de transcriptions |
| **Image Annotation** | Dessin de rectangles pour annoter des zones d'intérêt |
| **Spreadsheet Display** | Fichiers tableur depuis une propriété media reference |

**4. Widgets de Filtrage / Input**

| Widget | Description |
|--------|-------------|
| **Filter List** | Le plus riche. Supports : recherche par mots-clés, histogramme de distribution des propriétés, dropdowns single/multi-select, graphiques de distribution, pickers de date, timeline |
| **Property Filter** | Filtre par propriété |
| **Object Dropdown** | Sélection d'un objet unique dans une liste |
| **String Selector** | Dropdown, radio buttons, ou checkboxes |
| **Date and Time Picker** | Saisie date/heure |
| **Date Range Picker** | Sélection de plage de dates |
| **Slider** | Curseur numérique |
| **Search Bar** | Barre de recherche |
| **Toggle** | Interrupteur booléen |
| **Dropdown** | Menu déroulant |
| **Geo Filter** | Dessin sur carte pour filtrage géographique |
| **Object Selector** | Sélection d'objets |
| **Numeric Input** | Saisie numérique |
| **Text Input** | Texte libre |
| **Exploration Filter Pills** | Pilules de filtre interactives ajoutables/retirables dynamiquement |
| **Exploration Search Bar** | Barre de recherche full-text |
| **Prominent Term** | Termes fréquents/importants dans un object set |
| **User Select** | Sélection d'un utilisateur Foundry |

**5. Widgets d'Actions**

| Widget | Description |
|--------|-------------|
| **Action Button / Button Group** | Déclencheur d'action principal. Peut : exécuter une Action (writeback), déclencher un événement Workshop (changement de page, set de variable, ouverture/fermeture d'overlay), ouvrir une URL, démarrer un export d'object set. Trois layouts. Personnalisation : icônes, styles minimaux, styles tag |
| **Inline Action** | Formulaire surfaçant les paramètres d'Action Type directement inline. Interface formulaire et table. Validation live avec messages d'erreur personnalisés. UI automatiquement générée depuis les définitions de paramètres |
| **Bulk Action Button** | Action sur une sélection multiple d'objets |
| **Form** | Formulaire |
| **Media Uploader** | Upload de media |
| **Audio Recorder** | Enregistrement audio |

**6. Widgets AIP (IA/LLM)**

| Widget | Description |
|--------|-------------|
| **AIP Agent** | Assistant IA interactif (interface chat) avec outils enterprise. Configuré via AIP Agent Studio. Quatre types d'outils : recherche sémantique Ontologie (KNN ou vecteur), Actions, applications Workshop, Functions. Peut lire et écrire des variables Workshop |
| **AIP Analyst** | Analyse plus orientée analytique, configurable pour accès aux données, disponibilité d'outils, personnalisation UI |
| **AIP Generated Content** | Sortie d'appel LLM. Peut rendre une réponse streamée. Trois modes : Direct-to-LLM, LLM-via-prompt-function, AIP Logic function |
| **AIP Interactive** | Widget assistant interactif pour workflows opérationnels |

**7. Widgets Meta / Layout / Embedding**

| Widget | Description |
|--------|-------------|
| **Container** | Conteneur de layout |
| **Tabs** | Onglets de navigation |
| **Column Layout** | Layout en colonnes |
| **Conditional Visibility** | Visibilité conditionnelle |
| **Header** | En-tête |
| **Free-form Analysis** | Analyse ad-hoc dans le module Workshop |
| **Data Freshness** | Dernière mise à jour |
| **Edit History** | Historique des edits sur les objets |
| **Action Log Timeline** | Timeline des actions exécutées |
| **Linked Compass Resources** | Ressources Compass liées |
| **Comments** | Section de commentaires threadés |
| **Resource List** | Ressources Foundry |
| **Iframe** | Intégration d'application web. Communication bidirectionnelle via `@osdk/workshop-iframe-custom-widget` npm |
| **Embedded Module** | Intégration d'un autre module Workshop avec mapping de variables parent/enfant |
| **Custom Widgets** | Composants frontend entièrement custom (React, TypeScript). Packageés en "widget sets". Max 50 paramètres et 50 événements par widget |

#### Système de Variables (12 types, 6 mécanismes)

Les **Workshop Variables** sont le mécanisme central de communication inter-widget.

**12 types de variables :**
1. Object set
2. Object set filter
3. String
4. Numeric
5. Boolean
6. Date
7. Timestamp
8. GeoPoint
9. GeoShape
10. Array
11. Struct
12. Time series set

**6 mécanismes de définition :**
1. **Static** : valeur fixe définie manuellement
2. **Function** : calculée dynamiquement par une Function TypeScript sur Objects (FOO)
3. **Object set aggregation** : dérivée de l'agrégation d'un object set
4. **Object property** : liée à la valeur d'une propriété d'un objet unique
5. **Object set definition** : en spécifiant un type d'objet, des filtres de propriétés, et des traversées de liens
6. **Variable transformation** : série d'opérations référençant d'autres variables (style pipeline)

**Évaluation paresseuse** : les variables calculent **paresseusement en mode vue** — elles ne recalculent que quand affichées par un widget visible.

**Trois comportements de recomputation :**
- Automatic : recalcule quand les dépendances amont changent
- Event-triggered : recalcule uniquement déclenchée explicitement par un événement
- Load & event : recalcule au chargement initial du module ET sur événement

**Graphe de dépendances visuel** dans l'éditeur montrant comment les variables connectent aux widgets.

**Système d'événements :**
Open/Close overlay, Switch to page, Expand/Collapse/Toggle section, Switch to tab, Reset variable value, Recompute variable, Set variable value, Stream LLM response into variable, Send to AIP Assist, Open Workshop module.

**Limitation critique :** les événements n'attendent PAS que les computations aval des événements précédents soient complètes avant d'exécuter l'événement suivant.

### 4.4.2 Construction Step-by-Step

#### Binding d'un Table Widget à un Object Type

1. Glisser un widget **Object Table** depuis la sidebar gauche
2. Dans le panneau de config droit, sélectionner un Object Type (ex: "Flight") ou créer/sélectionner une **variable Object Set**
3. Optionnellement spécifier un filtre Object Set
4. Sélectionner quelles propriétés apparaissent comme colonnes — toggle, puis **drag to reorder**. Ou sous Column Configuration, "Add all properties" puis réorganiser en drag
5. Configurer largeurs de colonnes, tri par défaut, filtrage par colonne
6. Activer la sélection de lignes et configurer le comportement au clic
7. Configurer la pagination (25/50/100)

Workshop ne bind **pas aux datasets directement** dans les widgets opérationnels principaux ; il bind aux **object sets et object types** dans l'ontologie.

#### Ajout d'un Action Button

1. Ajouter un widget **Button Group**
2. Section "On click" dans la configuration
3. Sélectionner un Action Type de l'ontologie (ex: "Modify Flight Destination")
4. Le système affiche automatiquement tous les paramètres d'Action. Pour chaque paramètre : valeur par défaut (liée à une variable Workshop), visibilité (Visible/Hidden/Disabled)
5. Configurer le dialogue de confirmation, messages de succès/erreur, et comportement post-action (refresh data, navigate, clear selection)
6. Le bouton respecte les permissions au niveau ontologie — les utilisateurs sans permission d'exécution voient le bouton désactivé ou caché

Les Button Group widgets peuvent aussi déclencher des Workshop events, URLs et exports.

**Inline Action widget** : formulaire surfaçant les paramètres d'Action Type directement inline. Validation live.

**Flux de soumission :**
1. Validation contre les critères de soumission
2. Si échec : messages d'erreur inline
3. Si succès : exécution de l'action
4. Toast de confirmation vert
5. Mise à jour des données objet
6. Toutes les actions commitées **transactionnellement** à l'Ontologie

**Édits inline :** édition au niveau cellule directement dans l'Object Table widget, style "spreadsheet" avec writeback.

#### Filtres et Inter-Widget Linking

**Pattern canonique de linking :**

1. Table A (Customers) configurée pour qu'au clic de ligne, elle écrive `selectedCustomer` dans une variable
2. Table B (Orders) a son Object Set filtré par `Orders where customer = {{selectedCustomer}}`
3. Un Details Panel lit `selectedCustomer` pour afficher toutes les propriétés
4. Une Map surligne la localisation du client sélectionné
5. Un seul widget filtre peut contrôler plusieurs tables, charts et maps via des variables partagées

Le widget **Filter List** rend des filtres par type de propriété sous forme d'histogrammes, charts de distribution, pickers et sélecteurs type-ahead ; inclut la recherche par mot-clé. Connecter un Filter List à la même variable Object Set que la Table permet un filtrage automatique.

**Workshop Events** sont le tissu connectif : les events peuvent être déclenchés par les widgets incluant Button Group et Object Table sur sélection de ligne. C'est ce qui se rapproche le plus d'un "reactive state management layer" : variables + events.

Les boutons peuvent aussi déclencher un **"Send to AIP Assist"** event qui ouvre la sidebar Assist.

#### Layout, Routing, State Management

**Hiérarchie de layout :** Module -> Header -> Pages -> Sections -> Widgets/Layouts (Columns/Rows/Tabs) + Overlays (Drawers/Modals)

**Système de dimensionnement :** Auto (max), Absolute (pixels fixes), Flex (proportionnel).

**Module Interface :** API pour un module Workshop. N'importe quelle variable peut être ajoutée à l'interface. Quand un module A intègre un module B, A mappe ses variables aux variables d'interface de B. Variables complètement partagées entre parent et enfant. Initialisables depuis des query parameters URL.

**Routing :** l'ID de page courant est écrit dans l'URL ; les variables d'interface configurées sont écrites comme query parameters URL ; permet le bookmark, le partage et le deep-linking.

**Sauvegarde d'état :** sauvegarde persistante de l'état de toutes les variables ; restaurable ou partageable.

### 4.4.3 Patterns d'Application

#### Inbox / Task Triage (pattern canonique)

- **Panneau gauche** : Filter List
- **Centre** : Object Table avec alertes filtrées
- **Panneau droit** : Object View (détails de l'élément sélectionné)
- **Bas** : Button Group avec actions (approuver, rejeter, escalader)
- **Cas d'usage** : triage de réclamations, investigation d'alertes, gestion de commandes, gestion de cas, admission patient

#### COP (Common Operating Picture)

- Widget **Map** central
- **Metric Cards** (KPIs)
- **Chart XY** (tendances)
- **Filter List** / Exploration Filter Pills
- Cours officiel : "APPDEV 06: Building a Common Operating Picture in Workshop"

#### Scenarios / Analyse What-If

Un Scenario est un "fork" des données Ontologie généré en appliquant des actions (optionnellement via modèles ML). Modifications de paramètres, exécution de modèle, résultats projetés sans affecter les données live. Application transactionnelle. Intégré avec Vertex (framework de modélisation de Palantir).

---

## 4.5 Workshop vs Quiver vs Contour vs Slate

| Dimension | Workshop | Quiver | Contour | Slate |
|-----------|----------|--------|---------|-------|
| **Usage** | Apps opérationnelles avec writeback | Dashboards, KPIs, time series | Exploration ad-hoc tabulaire | Apps custom full HTML/CSS/JS |
| **Source de données** | Objets Ontologie uniquement | Objets Ontologie + time series | Datasets bruts (tabulaire) | APIs arbitraires + datasets bruts |
| **Writeback** | Oui (Ontology Actions) | Non (read-only) | Non (peut sauver comme nouveau dataset) | Oui (via API / code) |
| **Code requis** | Non (TypeScript Functions pour logique avancée) | Non | Non (point-and-click) | HTML/JS/CSS (templating Handlebars) |
| **Utilisateur cible** | Business ops, managers | Exécutifs, analystes, capteurs | Data analystes | Développeurs |
| **Vitesse de build** | Rapide | Très rapide | N/A (outil d'exploration) | Lent |
| **Custom UI** | Limité à la bibliothèque de widgets + custom widgets | Limité | N/A | Contrôle total (HTML/CSS/JS) |
| **Multi-page** | Oui | Non (dashboard unique) | Non (analysis boards) | Oui |
| **Formulaires/Input** | Oui | Non | Non | Oui (code) |
| **Ontologie requise** | Oui | Oui | Non | Non |
| **Mobile** | Layouts mobiles natifs et design responsive | Non | Non | Limité (CSS responsive manuel) |
| **Intégration AIP** | Complète (AIP Agent, Analyst, Generated Content) | AIP Generate pour ajout/config de cartes | Limitée | Limitée (via Functions et Iframe) |
| **Maintenance** | Faible — Palantir gère les mises à jour de widgets | Faible | Faible | Élevée (outil plus ancien, plus fragile) |
| **Échelle données** | Workflows opérationnels enterprise | ~50,000 lignes agrégation | Très grands datasets (millions+ lignes) | Variable |
| **Idéal pour** | Inbox/triage, COPs, gestion de tâches, dashboards opérationnels | Analytics centrées objet, time series, données capteurs | Exploration ad-hoc, analyse de très grands datasets | Dashboards pixel-perfect, apps legacy nécessitant contrôle HTML |

**Quand utiliser chaque outil :**
- **Les utilisateurs doivent agir/changer le monde** (actions, edits) -> **Workshop**
- **Dashboard de monitoring sans writeback** / **Comprendre le monde** -> **Quiver**
- **Exploration ad-hoc** / **Découvrir le monde** -> **Contour** (recommandé quand les données ne sont pas encore dans l'ontologie)
- **UI pixel-perfect, custom styling/behaviour, librairies JS tierces** (D3, Leaflet) -> **Slate**
- **Choix par défaut pour les nouvelles apps** -> **Workshop**

**Quiver dans Workshop** : les templates Quiver peuvent être **embarqués dans les applications Workshop** pour du contenu analytique au sein de workflows opérationnels.

---

## 4.6 AIP (Artificial Intelligence Platform)

### 4.6.1 AIP Logic

AIP Logic est un **environnement de développement no-code** pour construire, tester et releaser des fonctions alimentées par des LLMs, gouverné par la sécurité plateforme. [CONFIRMED]

#### Les 5 Types de Blocs

| Type de bloc | Description |
|-------------|-------------|
| **Use LLM** | Envoie un prompt (avec contexte Ontologie injecté) à un modèle de langage et capture la réponse structurée. Templates de prompt, traces de raisonnement intermédiaires. |
| **Apply Action** | Exécute un Action Type Ontologie (ex: "approve order", "update status"), qui peut écrire dans les systèmes source |
| **Execute Function** | Exécute une Function Ontologie typée (computation TypeScript ou Python) et retourne son résultat dans le workflow |
| **Conditional** | Branche le workflow selon une condition évaluée contre le contexte courant |
| **Loop** | Itère sur un ensemble d'objets ou résultats, appliquant les blocs suivants à chaque élément |

**Blocs additionnels** : calculateurs, object lookups, traversées de liens, recherche sémantique ("data tool blocks"), création de variables.

**Layout UI :**
- **Gauche** : Inputs, Blocks, Outputs configuration
- **Milieu** : Debugger (montrant les traces de raisonnement intermédiaires du modèle pour les blocs)
- **Droite** : Run panel (historique des runs, création de tests)

[CONTRADICTION] **Runtime LLM vs code déterministe** : une source affirme que "the LLM is used at development time to generate code; the deployed function runs deterministically without any LLM." D'autres sources décrivent AIP Logic comme des fonctions qui UTILISENT des blocs LLM au runtime, avec des blocs "Use LLM" qui ont des templates de prompt et des traces de raisonnement intermédiaires, et un debugger montrant les "model's intermediate reasoning traces." Cette contradiction est fondamentale sur l'architecture d'AIP Logic. Le consensus des sources multiples penche vers l'exécution LLM au runtime.

#### Runtime : LLM at Dev-Time vs at Runtime

Le consensus basé sur les sources multiples et les démos AIPCon : AIP Logic utilise les LLMs **au runtime**, pas uniquement au dev-time. Les blocs "Use LLM" envoient des prompts au moment de l'exécution, et le debugger montre les traces de raisonnement intermédiaires du modèle. La télémétrie de production montre 5,000+ function runs avec traces complètes.

**Workflow de création :**
1. Accéder AIP Logic via la navigation workspace ou +New > AIP Logic
2. Définir les inputs : strings prompts, objets ontologie, object lists, object sets, plus primitives
3. Composer des blocs : Create variable, Apply action, Execute function, Use LLM, boucles, conditionnels
4. Chaîner les blocs : l'output d'un bloc alimente le suivant
5. Run et debug : le Debugger montre les traces de raisonnement intermédiaires
6. Publier : pour les edits ontologiques, il faut publier et l'appeler via une Action
7. Configurer des **Évaluations** pour tester la logique, comparer des modèles, examiner la variance entre les runs

### 4.6.2 Agent Studio

Agent Studio permet la construction d'agents IA autonomes qui interagissent avec l'Ontologie via un ensemble contrôlé d'outils. L'architecture utilise le paradigme tool-use/function-calling. [CONFIRMED]

#### Les 4 Outils

| Outil | Ce qu'il fait |
|-------|---------------|
| **Query Objects** | Rechercher et récupérer des objets Ontologie matchant des filtres et contraintes spécifiés |
| **Apply Actions** | Exécuter des Action Types Ontologie pour créer, modifier ou supprimer des objets et déclencher le writeback |
| **Call Function** | Invoquer des Functions Ontologie typées (computations) et recevoir des résultats structurés |
| **Calculator** | Effectuer des opérations arithmétiques et mathématiques sans approximation LLM |

**Seuls les outils explicitement configurés sont accessibles** à chaque agent. Un agent ne peut pas découvrir ou invoquer des outils qui n'ont pas été whitelistés dans sa configuration. C'est une contrainte de sécurité fondamentale.

### 4.6.3 Language Model Service

Palantir opère un gateway LLM model-agnostique supportant **50+ modèles** : [CONFIRMED]

| Provider | Modèles |
|----------|---------|
| **OpenAI** | GPT-4o, GPT-4.1 |
| **Anthropic** | Claude 3.5, Claude Opus/Sonnet 4 |
| **Meta** | Llama 3.x, Llama 4 |
| **Mistral AI** | Modèles Mistral |
| **Google** | Gemini 2.5 Pro/Flash |
| **xAI** | Grok |
| **BYOM** | Les clients peuvent intégrer des modèles propriétaires ou fine-tunés |

Pour les clients gouvernementaux, les modèles tournent entièrement on-premises.

### 4.6.4 Guardrails — 4 Niveaux de Contrôle

| Niveau | Guardrail | Description |
|--------|-----------|-------------|
| **1** | Constrained Action Types | Définit QUELLES actions l'IA est autorisée à prendre. L'IA ne peut pas effectuer d'opération non explicitement listée dans ses Action Types permis. |
| **2** | Tool Scoping | Définit QUELS outils l'agent peut accéder. Seuls les outils explicitement configurés sont visibles ; l'agent ne peut pas en découvrir d'autres. |
| **3** | Permission-Bounded | L'IA hérite des permissions de l'utilisateur invocateur. Elle ne peut pas voir ou modifier des données que l'utilisateur ne peut pas voir ou modifier. Pas d'escalade de privilèges. |
| **4** | Staging Review | L'humain approuve avant exécution. Les actions sont stagées pour revue, et un humain doit explicitement confirmer avant que les effets de bord ne soient commités. |

**Comment AIP accède à l'Ontologie :** AIP Logic reçoit des objets Ontologie typés, pas des données brutes. On accorde explicitement à chaque bloc LLM l'accès à des object types et propriétés spécifiques :

> "I explicitly gave it access to this object... you can pick a lot of different objects here or narrow it down. This is an explicit access from an LLM to certain ontology... I can give it access to certain properties -- not just from a security standpoint but also from an LLM [hallucination reduction] standpoint."

Le package `@foundry/ontology-api` auto-génère des interfaces TypeScript depuis le schema Ontologie, ce qui signifie que les actions du LLM sont contraintes aux opérations Ontologie valides.

**Observabilité** : tracing au niveau workflow, avec une "Trace view" montrant une timeline d'opérations incluant si les spans proviennent de Functions, Actions, Automations ou appels LLM.

### 4.6.5 AIP Assist — Expérience In-Product

AIP Assist est un outil de support plateforme avec une **sidebar in-app**. Il est explicitement context-aware (conscient de l'app Foundry dans laquelle on se trouve) et est conçu pour **ne pas accéder aux données utilisateur**.

AIP Assist n'est **PAS** un générateur d'applications Workshop. C'est une sidebar d'aide contextuelle entraînée sur la documentation de la plateforme.

**Intégrations documentées :**
- **Dans Workshop** : les widgets Button peuvent déclencher un event "Send to AIP Assist" qui ouvre la sidebar Assist et soumet un prompt statique ou dérivé de variable ; les builders peuvent définir un Agent Assist par défaut
- **Dans Ontology Manager** : lors de la mise à jour d'une ontologie, l'onglet Errors inclut "Explain with AIP Assist" sur une erreur, produisant des suggestions de corrections et explications

**Generative Frontend (en développement)** : une fonctionnalité "Generative Frontend AIP Assist" cible les applications OSDK React. Statut : expérimental. Utilise l'extension Continue dans VS Code Workspaces.

---

## 4.7 OSDK (Ontology SDK)

L'OSDK est le générateur de code schema-driven de Palantir qui produit des **clients types fortement statiques** spécifiques à votre Ontologie. Ce n'est pas un wrapper REST générique — il génère des types qui mirrorent exactement vos Object Types, Link Types et Actions. [CONFIRMED]

**Langages supportés :** TypeScript (NPM), Python (Pip/Conda), Java (Maven), et **OpenAPI** pour tout autre langage.

**Génération :**
1. Les apps OSDK sont créées et gérées dans **Developer Console**
2. Wizard de création : choisir "client-facing application", configurer les OAuth redirect URLs, sélectionner quels object types et action types inclure dans le package SDK
3. Le code généré inclut des classes typées pour chaque Object Type, accesseurs de propriétés, traversées de liens, et invocations d'Actions
4. Les noms de propriétés et descriptions de l'Ontology Manager apparaissent comme JSDoc/docstrings dans l'IDE

**CLI de génération :**

```bash
npx @osdk/cli generate \
  --foundry-url https://your-stack.palantirfoundry.com \
  --ontology-rid ri.ontology.main.ontology.xxx \
  --output-dir ./src/ontology
```

**Écosystème NPM :** `@osdk/client`, `@osdk/api`, `@osdk/oauth`, `@osdk/cli`, `@osdk/react`. Repo open-source : `palantir/osdk-ts`.

**Authentication :** OAuth 2.0 confidential client (backend), OAuth 2.0 public client (browser SPA), et bearer token (développement).

### Exemples de Code TypeScript

**Query avec filtrage et pagination :**

```typescript
import { createClient } from "@osdk/client";
import { MaintenanceTicket } from "./ontology/objects/MaintenanceTicket";

const client = createClient(foundryUrl, ontologyRid, auth);

const tickets = await client(MaintenanceTicket)
  .where({ priority: "HIGH", status: { $ne: "CLOSED" } })
  .orderBy(t => t.createdDate.desc())
  .take(50);

for (const ticket of tickets.data) {
  console.log(ticket.ticketId);     // string - entièrement typé
  console.log(ticket.priority);      // "HIGH" | "MEDIUM" | "LOW"
}
```

**Traverser les liens :**

```typescript
const asset = await tickets.data[0].$link.asset.get();
const departments = await employee.$link.department.fetchPage({ $pageSize: 100 });
```

**Exécuter des actions :**

```typescript
await client(updateTicketStatus).applyAction({
  ticket: tickets.data[0].$primaryKey,
  newStatus: "IN_PROGRESS",
});

// Batch
await client(CreateEmployee).batchApplyAction([...]);

// Validation only
const validation = await client(CreateEmployee).applyAction({...}, { $validateOnly: true });
```

**Hooks React (avec `@osdk/react`) :**

```typescript
import { Todo } from "@my/osdk";
import { useOsdkObjects } from "@osdk/react/experimental";

function TodoList() {
  const { data, isLoading, error } = useOsdkObjects(Todo, {
    orderBy: { createdAt: "desc" },
  });
  // ...
}
```

**Agrégations :**

```typescript
const grouped = await client(MyObject).aggregate({
  $select: { $count: "unordered" },
  $groupBy: { category: "exact", region: "exact" }
});
```

**Filtrage OR :**

```typescript
import OSDK from "@slate-internal/sdk";
const result = await ObjType
  .where(query => {
    const conditions = names.map(n => query.name.eq(n));
    return OSDK.Op.or(...conditions);
  })
  .fetchPage();
```

**Subscribe (WebSocket real-time updates) :** `streamUpdates` pour des mises à jour temps réel.

### Exemples Python et Java

**Python OSDK :** `.get()`, `.page()`, `.iterate()`, `.where()` avec opérateurs d'égalité, null check, string prefix, full-text search, range, boolean composition (AND/OR/NOT), ordering, `.count()`, `.avg()`, `.approximate_distinct()`, `.group_by()`.

**Java OSDK :**

```java
List<Restaurant> result = client.ontology()
    .objects()
    .Restaurant()
    .where(RestaurantFilter.restaurantName().isNull(false))
    .fetchStream()
    .toList();
```

**Platform API bindings** via `foundry-platform-typescript` (installable comme `@osdk/foundry.{namespace}`).

---

## 4.8 Apollo — Déploiement

### Architecture Hub-and-Spoke

1. **Apollo Hub** (central, hébergé par Palantir comme SaaS) : maintient le statut et les requirements de chaque environnement. Contient le moteur d'orchestration et le catalogue. Stocke les settings d'environnement incluant les entités qui doivent exister, les release channels souscrits, et les fenêtres de maintenance.
2. **Remote Apollo Hubs** : déployés dans les réseaux air-gapped ou isolés. Synchronisés avec le Hub principal via des Apollo bundles.
3. **Spoke Environments / Apollo Deployment Platform** : exécutent un Spoke Control Plane et reportent le statut au Hub. Déployé au-dessus de Kubernetes.
4. **Apollo Agents** : déployés dans le Spoke, exécutent les Plans émis par le Hub, puis reportent le "Reported State". Pollent le control plane pour les changements d'état désiré, téléchargent les artifacts des registries, et orchestrent les déploiements Kubernetes.
5. **Apollo SDK** : framework pour les développeurs pour publier les metadata de release.
6. **Apollo Catalog** : couche metadata bridgeant les artifact stores et les environnements gérés. Source de vérité pour toutes les versions de software disponibles.

Les spokes peuvent eux-mêmes être hubs d'autres spokes, permettant des topologies hiérarchiques.

### Modèle Pull (pas Push)

Apollo utilise un **modèle pull constraint-based**, fondamentalement différent des systèmes CI/CD push-based comme Jenkins ou ArgoCD. Au lieu d'un système central poussant des artifacts vers des cibles, Apollo définit des **Plans** declaratifs d'état désiré. Chaque spoke agent pull indépendamment le plan et converge son environnement local.

Essentiel pour la sécurité — **aucune connexion entrante vers les réseaux clients n'est requise**.

### Constraint-Based (pas Desired-State simple)

Le moteur évalue continuellement les Plans possibles pour chaque Spoke, vérifie les contraintes, et émet les Plans dont les contraintes sont satisfaites. Compare l'état cible vs l'état observé à travers tous les environnements. Quand ils diffèrent, il calcule un **Apollo Plan** spécifiant quoi upgrader, où et comment.

Les Plans pour roll off un release rappelé ou exécuter des commandes "break-glass" sont **priorisés**.

### Échelle Opérationnelle

| Métrique | Valeur | Confiance |
|----------|--------|-----------|
| Déploiements par mois | **360,000+** | CONFIRMED |
| Environnements gérés | **300+** | CONFIRMED |
| Microservices déployés | **500+** indépendamment | CONFIRMED |
| Équipes d'ingénierie | **250+** déploient en continu | CONFIRMED |
| Temps de déploiement | **3.5 minutes** | CONFIRMED |
| Équipe engineering Apollo | **<20 ingénieurs** | CONFIRMED |

### Rollback en 4.9 Minutes

**Rollback declaratif** : le control plane remet la version désirée à l'état précédent connu-bon et les agents reconcilent. Temps : **<5 minutes** (confirmé).

**Déclenchement automatique** : quand les health checks (Kubernetes probes + endpoints de santé applicatifs custom) échouent.

**Stratégies de recall :**
- **Stay on current version** — pause des nouvelles installations pendant l'investigation
- **Stay on current with exceptions** — des environnements spécifiques reçoivent le fix
- **Any version newer than recalled** — attendre un fix
- **Roll back to specific known-good version** — forcer le downgrade sur toute la flotte

Les recalls peuvent être déclenchés par les administrateurs, développeurs, ou **automatiquement par Apollo**.

**Vitesse de patch** : 3.5 minutes en moyenne pour patcher un service, moins de 5 minutes pour remédier les problèmes de production. Apollo peut remédier les vulnérabilités en "quelques heures" (référence : remédiation log4j à travers 200+ environnements).

### Air-Gapped : Sneakernet, Bundles Chiffrés

**Mécanisme 1 : Apollo Bundles (sneakernet)** : générés sur le Hub SaaS, contenant uniquement les nouvelles versions nettes de software, configurations et metadata (diffs intelligemment compressés). Gravés sur media physique, transportés vers le réseau classifié, et chargés dans le Remote Hub. Les metadata AV sont incluses ; les payloads sont scannés et vérifiés en intégrité à plusieurs checkpoints.

**Mécanisme 2 : Binary Transfer Service (BTS)** : automatise le transfert de bundles via des **Cross Domain Solutions (CDS)** accréditées. BTS poll le Apollo Catalog pour les nouvelles releases, vérifie les résultats de scan sécurité et checksums cryptographiques, et transfère les artifacts vers le hub distant automatiquement.

**Opération déconnectée** : les environnements peuvent se déconnecter d'un Hub pendant des périodes (ex: véhicules en mouvement) et se reconnecter pour les upgrades plus tard.

**One-way data flow** : pour les niveaux de classification les plus élevés, le flux de données est unidirectionnel — les mises à jour entrent, mais un minimum ou aucune télémétrie ne sort.

**Classifications supportées** : jusqu'à TS/SCI.

[CONTRADICTION] **Sneakernet** : une source dit que les docs publiques "do not describe sneakernet mechanics in detail." D'autres sources donnent des détails précis sur les Apollo Bundles (diffs compressés, media physique, checkpoints de vérification).

### Break-Glass Mechanism

Mécanisme de dérogation d'urgence permettant aux opérateurs autorisés de bypasser les contraintes normales de déploiement et workflows d'approbation en situation de crise. Essentiel pour les déploiements militaires et d'infrastructure critique. [CONFIRMED]

### $100/installation/mois Standalone

Apollo est disponible comme produit standalone sur les **Azure et AWS Marketplaces** à environ **~$100/install/month**. C'est le seul produit Palantir disponible indépendamment du stack Foundry complet. [CONFIRMED]

### Mécanismes de Contrôle Additionnels

**Release Channels** : les environnements souscrivent à des canaux (ex: `canary` -> `beta` -> `stable` -> `government-stable`). Les features passent de develop -> stable automatiquement après adjudication.

**Canary Analysis** : les nouvelles features sont d'abord déployées dans les environnements canary. Apollo monitore les métriques de performance et états d'erreur, promouvant ou rappelant automatiquement les releases.

**Blue/Green Deployment** : zero-downtime — déploie une seconde instance, déplace lentement le traffic.

**Fenêtres de maintenance** : au niveau produit ou environnement, bloquent les upgrades pendant les périodes sensibles. Auto-créées quand des seuils de failure sont atteints.

**Change requests** : système avec statuts Pending Approvals, Approved, Rejected, Cancelled. Sauf DEV, Apollo requiert au moins un approbateur.

**Certifications sécurité** : FedRAMP High (upgraded from Moderate, Dec 2024), DoD IL5, DoD IL6, ICD 503. Apollo encode les SLAs de vulnérabilité InfoSec, s'intègre aux scanners d'images container, et génère des **SBOMs** complets. [CONFIRMED]

---

## 4.9 Compute Architecture

### 5 Moteurs

| Moteur | Mode | Architecture | Workload optimal | Volume |
|--------|------|-------------|-----------------|--------|
| **Apache Spark** | Batch | Distribué (driver + executors) | ETL large-scale, reprocessing historique, ML feature engineering | GB à TB+ |
| **Apache Flink** | Streaming | Distribué (JobManager + TaskManagers avec checkpointing) | Real-time event processing, CDC, agrégations continues | Flux continus |
| **DuckDB** | In-process | Single-process, embedded | Requêtes analytiques rapides sur datasets petits-moyens | MB à low GB |
| **Polars** | In-process | Single-process, Rust-powered DataFrame library | Opérations DataFrame haute-performance | MB à low GB |
| **Virtual Tables** | Pushdown | Fédéré (requête envoyée au moteur externe) | Requêter des données dans des warehouses externes sans les déplacer | Any (données ne bougent pas) |

**Mesa** (propriétaire) : langage de résolution de contraintes pour les problèmes d'optimisation (scheduling, routing, allocation de ressources).

### Logique de Sélection

| Caractéristique | Moteur sélectionné | Justification |
|----------------|-------------------|---------------|
| Données > 10 GB, batch | Apache Spark | Exécution distribuée pour parallélisme |
| Flux continu d'événements | Apache Flink | Stream processing stateful avec exactly-once semantics |
| Données < 10 GB, requêtes analytiques | DuckDB | Démarrage rapide, pas d'overhead cluster, analytique columnar |
| Opérations DataFrame complexes | Polars | Performance Rust avec évaluation paresseuse |
| Données dans un warehouse externe | Virtual Tables | Éviter le mouvement de données ; leverager l'optimisation du moteur externe |
| Problème d'optimisation par contraintes | Mesa | Solveur propriétaire pour scheduling/routing/allocation |

---

## 4.10 Sécurité

### Cell-Level ACL, AES-256-GCM

- **Cell-level ACL** : contrôle d'accès au niveau de la cellule individuelle (intersection ligne + colonne), pas seulement au niveau table ou ligne [CONFIRMED]
- **AES-256-GCM** : données chiffrées au repos et en transit via AES-256 en Galois/Counter Mode [CONFIRMED]

### Markings et PBAC

Palantir combine **Purpose-Based Access Control (PBAC)** avec des **markings obligatoires (MAC — Mandatory Access Control)**.

**Couche 1 : Markings de Ressource Obligatoires**
- Chaque élément de données peut porter des **markings binaires, conjonctifs**
- Les markings sont binaires (un utilisateur a le marking ou non) et conjonctifs (tous les markings requis doivent être présents)
- Les markings suivent des **règles d'héritage** — les données dérivées héritent de l'union des markings de toutes les données source
- Empêche l'information de couler "vers le bas" vers des contextes moins classifiés

**Couche 2 : ACL au Niveau Ontologie**
- **Per-object RLS (Row-Level Security)** — les objets individuels peuvent avoir des règles d'accès
- **Per-property column suppression** — des propriétés spécifiques peuvent être cachées à des utilisateurs spécifiques (ex: voir qu'un Patient existe mais pas son SSN)
- **Restricted views avec dynamic row predicates** — vues filtrant les objets selon des prédicats évalués au runtime

### Propagation à travers les Links

**Link-Visibility Semantics** (détail d'implémentation critique) : la visibilité des liens doit être explicitement définie et testée. Sans implémentation soigneuse, un attaquant peut inférer l'existence d'objets classifiés à travers :
1. Les résultats de traversée qui incluent des liens vers des objets que l'utilisateur ne peut pas voir
2. Les comptages d'edges qui révèlent le nombre de connexions cachées
3. Les requêtes "exists" qui confirment l'existence d'un objet lié sans révéler son contenu

Palantir adresse explicitement ces vecteurs de fuite.

### Permission pour AI vs Humains

**Couche 3 : Contrôles de Contexte d'Exécution pour l'IA**
- **Contexte d'identité** : l'agent IA opère sous l'identité de l'utilisateur invocateur, héritant de ses permissions exactes
- **Scoping de contexte de purpose** : l'accès de l'IA peut être encore restreint à un purpose spécifique (ex: "cet agent est pour l'optimisation supply chain et ne peut pas accéder aux données RH même si l'utilisateur le peut")
- **Empêche l'IA de devenir un canal d'exfiltration cross-domaine** : même si un utilisateur a accès aux données RH et finance, un agent scopé à finance ne peut pas surfacer les données RH

### Brevets Sécurité

**US9081975B2 / US9836523B2 — Partage entre Nexus à Schemas de Classification Différents (2015) :**
- Structure de classification : markings (Top Secret, Secret, Confidential, Restricted, Unclassified) + classifications d'origine
- Règles de traduction **asymétriques** (aller et retour peuvent différer)
- Traduction par chemin le plus court pour minimiser la dégradation de précision
- Invariant de réplication : données exportées et réimportées doivent conserver leurs markings originaux

**US9857960B1 — Collaboration de Données (2018) :**
- Cinq critères de rédaction progressifs : classification, provenance, type d'objet, type de propriété, type de media
- Résolution d'import par déconfliction basée sur timestamp

**US20230306000A1 — Partage d'Actifs Data (2023) :**
- Partage par mise à jour des markings de namespace — pas de déplacement de données
- **Révocation transitive de permissions** : quand l'accès amont est refusé, les datasets dérivés en aval héritent automatiquement des restrictions via la chaîne de lineage
- Minimisation de données : filtrage au niveau colonne et ligne appliqué automatiquement

**US11593317B2 — Journalisation d'Activité Inviolable (2023) :**
- Architecture double-datastore : logs dans un repository append-only immutable et un journal système accessible client
- Journalisation en chunks de 50 Ko, chiffrés, compressés, hashés (SHA-1 ou SHA-512)
- Hash comme adresse (stockage adressable par contenu, similaire au object store de git)
- Détection multi-couche : détection d'intrusion, sécurité kernel, journalisation des frappes clavier, audit d'appels système

**US20240346388A1 — Entraînement LLM Conscient de la Sécurité (2024, en attente) :**
- Segmentation des datasets d'entraînement par niveau de permission
- Entraînement de modèles séparés par tier de sécurité
- Routage à l'inférence selon le niveau de permission des requêtes
- Fondamentalement plus sécurisé que les systèmes RAG avec filtrage post-génération

---

## 4.11 Brevets Techniques Clés

### Brevets Ontologie

**US7962495B2 / US9589014B2 — Ontologie Dynamique (2006) :**
- L'ontologie est incarnée dans un schema de base de données — pas un concept abstrait
- Object Types identifiés par des URIs (héritage RDF/web sémantique)
- Parser definitions éditables à l'exécution — ontologie genuinement dynamique
- Contraintes de type explicites validant les données entrantes
- Structure modifiable sans reconstruire le datastore sous-jacent

**US20200293561A1 — Object Platform for Datasets (2020) :**
- Cinq moteurs : datastore, definition engine, association engine, cache engine, interface engine
- Les objets sont une **couche de vue** sur des données relationnelles/tabulaires
- Stratégie de caching : architecture de vues matérialisées
- Résolution de conflits via commit logs avec "timestamps and vector clocks"
- Trois APIs : Object Search API, Object Load API, Object Modify API

**US10754822B2 — Migration d'Ontologie (2020) :**
- Migration basée sur des "stacks" (environnements de déploiement)
- Traduction d'identifiants de datasets entre stacks, pas déplacement de données
- Sélection de migration selective d'objets spécifiques

**US10061828B2 — Réplication Multi-Master Cross-Ontology (2016) :**
- Trois approches de mapping : One-to-One, One-to-Many, Drop Lists
- Validation pre-export par simulation de transformations aller-retour
- Digest cryptographique pour prévenir la dérive silencieuse des mappings
- Solution pour le partage inter-agences (CIA/NSA)

**US10248722 — Support Multi-Langue pour Ontologie Dynamique :**
- Système de types à trois piliers (object types, property types, link types)
- Support multi-langue pour déploiements internationaux/coalition

### Brevets Pipeline

**US9946738B2 / US10853338B2 — Universal Data Pipeline (2014/2018) :**
- **Principe d'immutabilité** : les données ne sont JAMAIS écrasées. Nouvelles versions créées à côté des historiques
- Delta encoding : versions stockées comme "differences or deltas between dataset versions"
- Protocole de transaction en trois phases : initiation, opérations d'écriture, engagement
- DAGs de dépendances avec parcours en profondeur post-order
- Rebuild en cascade via file de messages
- Build Catalog pour traçabilité complète

**US20210149857A1 — Branching de Pipeline (2020) :**
- Branche master avec pointeurs vers snapshots + logique
- Création de branche test avec sémantique copy-on-write
- Opération merge remplaçant la logique master

**US20250094439A1 — Optimisation de Réponse LLM pour Génération de Pipeline (2024, en attente) :**
- Langage informatique propriétaire optimisé pour l'efficacité de tokens LLM — "2x to 100x more efficient than conventional languages"
- Parsers ANTLR pour parser les sorties LLM en code de pipeline executable
- Instructions de "mistake context" dans les prompts (prévention d'erreurs few-shot)

### Brevets Workshop

**US11500620B2 — Workshop : Workflow Application and UI Builder (2022) :**
- Architecture widget : composants modulaires dans des containers de layout
- Type safety : le builder valide que les inputs/outputs adhèrent aux data object types spécifiques
- Function registry : logique workflow stockée séparément, référencée par les widgets
- Preview WYSIWYG en temps réel

**US11842171B2 — Function Access System (2023) :**
- Cinq composants : Ontology Data Store, API Generation Engine, Function Data Store, Function Manager Engine, Data Object Data Store
- Régénération automatique d'API sur changements d'ontologie
- Fonctions multi-langages (C, Java, Python, Ruby, JavaScript)
- Exécution sandboxée avec limites de ressources
- Contrôle d'accès appliqué au niveau API, pas au niveau données

### Brevets Apollo

**US10263845B2 — Déploiement de Configuration Continue (2019) :**
- Repository de configuration hiérarchique central
- Pre-caching : les sous-serveurs cachent les objets avant les fenêtres de maintenance
- Génération context-aware : un seul objet de définition génère différents objets par système
- Capacité de réseau maillé : les systèmes peuvent requêter des objets depuis des sous-serveurs pairs
- Exécution automatisée : objets contenant des APIs et handlers

**US11444854 — Métriques d'Utilisation Logiciel (2022) :**
- Télémétrie centralisée depuis tous les environnements de déploiement

**Déploiement canary/feature flagging :** utilisateurs assignés à des "tracks" avec différentes versions des mêmes composants.

### Brevets AI/LLM

**EP4443310A1 — Interfaces Système IA (2024) :**
- Architecture en trois couches : Orchestrator Selector -> Service Orchestrators -> Data Processing Services
- LLMs servent deux rôles : sélection de service et formatage de requête
- In-prompt training : exemples directement dans les prompts
- Architecture plugin : services exposés via APIs
- Injection de contexte : permissions utilisateur, analyses précédentes, schemas de données

**US20240419658A1 — Système IA Basé sur Profils (2024) :**
- Profil à quatre composants : Knowledge Bases, Functions, Plugins, Templates
- Plugins activent avant (pour peupler le prompt) et après (pour traiter les résultats)

**US20240346388A1 — Entraînement LLM Conscient de la Sécurité (2024, en attente) :**
- Segmentation des datasets d'entraînement par niveau de permission
- Modèles séparés par tier de sécurité, combinés via modèle ensemble à l'inférence

---

## 4.12 Analyse de Réplicabilité

### Par Couche : de 95% (Data Processing) à 30% (Operational Ontology)

| Couche | Réplicabilité OSS | Alternatives principales | Analyse du gap |
|--------|-------------------|-------------------------|----------------|
| **Data Processing** | ~95% | Apache Spark, Apache Flink, DuckDB | Quasi-identique. Palantir utilise ces moteurs exacts. Le gap est dans la couche de gestion unifiée. |
| **Storage** | ~95% | Apache Iceberg, Apache Parquet | Quasi-identique. Palantir utilise Parquet en interne. |
| **Orchestration** | ~80% | Apache Airflow, Dagster | Alternatives solides. Gap : l'orchestration de Palantir est ontology-aware. |
| **Data Integration** | ~75% | Airbyte (~300 connecteurs) | Airbyte dépasse Palantir en nombre de connecteurs. Gap : architectures agent-based proxy et air-gapped worker manquantes. |
| **App Building** | ~65% | Retool, Appsmith | Bonnes plateformes low-code. Gap : pas ontology-native. |
| **AI / LLM** | ~60% | LangChain, LlamaIndex | Équivalents framework-level. Gap : pas d'injection de contexte Ontologie typé, pas d'architecture guardrail multi-niveau, pas d'héritage de permissions. |
| **CI/CD** | ~50% | ArgoCD + Terraform | ArgoCD est pull-based (GitOps). Gap : pas de planning constraint-based, pas d'opération autonome hub-spoke, pas de readiness air-gap/edge. |
| **Metadata** | ~45% | DataHub, Apache Atlas | Catalog-oriented, pas opérationnel. Ils décrivent les données ; ils ne gouvernent pas l'accès et la mutation runtime. |
| **Security** | ~40% | Apache Ranger + OPA | Row-level security possible. Gap : pas de cell-level ACL, pas de markings obligatoires, pas de link-visibility semantics, pas de contrôles de contexte d'exécution IA. |
| **Operational Ontology** | ~30% | Aucun équivalent | La couche la plus dure à répliquer. Aucun projet open-source ne combine entités typées + actions + fonctions + interfaces + sécurité + indexation temps réel en un modèle opérationnel unifié. C'est le coeur du IP. |

### Stratégies PostgreSQL pour Chaque Couche

> Principe directeur : "Copy the contracts, not the code."

| # | Stratégie | Guidance d'implémentation |
|---|-----------|--------------------------|
| **1** | Stable Ontology IDs + Name Aliases | Chaque Object Type, Property et Link Type reçoit un UUID stable. Les noms sont des alias mutables. Toutes les références internes utilisent l'UUID. |
| **2** | Funnel-Like Orchestrator | Implémenter comme composant logique : changelog generation -> merge-with-user-edits -> build search artifacts -> atomic cutover. Peut démarrer comme fonction PostgreSQL + background job. |
| **3** | User Edits as Append-Only Log | Table append-only dédiée avec résolution de conflits explicite. Défaut : "user edits win." Support alternative : "most recent value." Le log n'est jamais tronqué. |
| **4** | Actions as Atomic Commits | Transactions PostgreSQL avec concurrence optimiste (check de colonne version au commit). Deux classes d'effets de bord : writeback transactionnel (même transaction DB) et best-effort (async, via job queue, at-least-once). |
| **5** | Expose Constraints as Product Behavior | Rendre les contraintes visibles : property hints indexés, caps de profondeur de traversée, limites de throughput, sémantiques at-least-once. Ce sont des contrats produit, pas des détails d'implémentation. |
| **6** | Multi-Datasource per Object Type | Un seul Object Type peut être adossé à plusieurs sources. La logique de merge et résolution de conflits sont explicites et auditables. |
| **7** | Edit-Only Properties | Propriétés sans source pipeline — valeurs purement user-entered. Stockées exclusivement dans le log d'edits. |

---

## 4.13 Contradictions Techniques

| # | Sujet | Description |
|---|-------|-------------|
| **1** | **Types Set et Map** | Une source (Claude) liste `Set` et `Map` comme types de propriétés supportés. Les autres sources ne les mentionnent pas et citent explicitement une liste "load-bearing" qui ne les contient pas. |
| **2** | **Outil de migration intégré** | Une source dit qu'il n'existe pas d'outil de migration comparable à Flyway. D'autres sources décrivent un framework de migration OSv2 détaillé avec 7 types de migrations, onglet dédié, et blocage automatique. Résolution probable : distinction OSv1 (pas d'outil) vs OSv2 (framework complet). |
| **3** | **Mixing visuel et code dans Pipeline Builder** | Une source affirme le support total via Custom Code nodes avec éditeur Monaco. D'autres disent explicitement que le mixing se fait au niveau dataset boundary, pas inside a node. Pipeline Builder est l'outil no-code ; Code Repositories est pour le code. |
| **4** | **AIP Logic runtime** | Une source dit que le LLM génère du code déterministe au dev-time, pas au runtime. D'autres décrivent des blocs LLM exécutant au runtime avec traces de raisonnement, confirmé par les démos AIPCon. Le consensus penche vers l'exécution LLM au runtime. |
| **5** | **Sneakernet / déploiement air-gap** | Une source dit que les détails ne sont pas publiquement documentés. D'autres donnent des détails précis sur les Apollo Bundles (diffs compressés, media physique, checkpoints de vérification) et le Binary Transfer Service. |
| **6** | **Column-level lineage** | Une source décrit le parsing du Catalyst plan Spark et le tracking explicite par noeud Pipeline Builder. D'autres ne décrivent qu'un lineage dataset/transaction et disent que le lineage cellule/ligne n'est PAS une feature standard. |
| **7** | **GeoPoint vs Geohash** | Les dénominations varient (`Geopoint`, `GeoPoint (lat/lng)`, `Geohash (GeoPoint)`) mais le type sous-jacent semble être le même. |
| **8** | **Localisation du bouton de création dans Ontology Manager** | Trois sources placent le bouton à des endroits différents (top bar, toolbar, haut à droite avec dropdown). Le workflow décrit est le même. |
| **9** | **Nombre de connecteurs** | Certaines sources indiquent "150+ native connectors", d'autres "400+ connectors". La différence peut s'expliquer par le comptage (connecteurs natifs vs total incluant JDBC custom, webhooks, etc.). |
| **10** | **Nombre de fonctions d'expression** | "300+ built-in functions" dans certaines sources vs "500+ fonctions built-in" dans d'autres. L'écart peut refléter des mises à jour de version ou des méthodes de comptage différentes. |
