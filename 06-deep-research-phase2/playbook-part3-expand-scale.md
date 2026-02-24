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
