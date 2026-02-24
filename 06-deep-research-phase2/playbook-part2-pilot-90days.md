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
