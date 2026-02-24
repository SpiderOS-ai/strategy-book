## Synthese 2 — Pilot Implementation Methodology (90 jours)

### Sources fusionnees

- **(GPT)** = gpt-pilot-implementation-methodology.md
- **(Claude)** = claude-pilot-methodology.md
- **(Perplexity)** = perplexity-pilot-methodology.md

---

### 1. Vue d'ensemble du modele "Acquire" a 90 jours

La phase "Acquire" est un deploiement pilote de 12 semaines au cours duquel une equipe embarquee de Palantir transforme un contrat signe en systeme de production operationnel sur Foundry. L'objectif fondamental est de demontrer une valeur indeniable en quelques semaines pour declencher l'expansion. Le principe directeur, articule par Nabeel Qureshi (8 ans comme FDE) : resoudre d'abord un probleme "hair on fire", puis s'etendre a partir de cette tete de pont (Claude).

Le pilote est deliberement deficitaire pour Palantir. En 2019, les clients en phase Acquire generaient seulement 600 000 $ de revenus contre une perte de contribution de 65,4 M$ (Perplexity). Le modele economique repose sur l'expansion : la phase **Expand** (mois 3-12) atteint le seuil de rentabilite, et la phase **Scale** (annee 2+) genere des marges de contribution de **55-65 %+** (Claude). Le dollar-based net retention depasse systematiquement **115-120 %**, et les 20 premiers clients generent en moyenne **33 M$+ de revenus annuel** (Claude).

La structure en 4 phases qui se chevauchent : Foundation / Discovery (semaines 1-3), Lighthouse Build / Ontology & Integration (semaines 2-6), Application & Action Design (semaines 4-10), Training & Handoff (semaines 8-12) (les trois sources).

---

### 2. Composition et roles de l'equipe deployee

**Taille de l'equipe pilote standard :**

[CONTRADICTION] **(Claude)** indique **1 Deployment Strategist + 2-4 Forward Deployed Engineers**. **(Perplexity)** indique **4-5 personnes : 2-3 FDSE + 1-2 DS**. Les deux convergent sur un total de 3 a 5 personnes, mais divergent legerement sur la repartition DS/FDE.

**Forward Deployed Engineer (FDE/FDSE)** : Possede le stack technique — pipelines de donnees, conception de l'ontologie, applications Workshop, et code. Generalistes capables d'ecrire des transforms PySpark le matin et de presenter une application Workshop a un VP l'apres-midi (Claude). Embarques directement avec les utilisateurs finaux, pas avec l'IT (Claude). Travaillent typiquement **50-70 heures par semaine** pendant les pilotes, avec **50-80 % de deplacement** sur site client (Claude). Les FDE ont tendance a ecrire du code "qui fait le job rapidement, ce qui signifie — poliment — de la dette technique et des workarounds hacky" (Perplexity, citant Nabeel Qureshi).

**Deployment Strategist (DS)** : Possede la relation business — gestion des parties prenantes, priorisation des use cases, communication executive, et roadmap d'expansion (les trois sources). Beaucoup de DS viennent de McKinsey, BCG ou Bain (Claude). Le DS gere la politique organisationnelle pour que les FDE puissent se concentrer sur la construction (Claude, Perplexity). Mene les ateliers de decouverte, les briefings executifs, les sessions de formation, et la presentation finale aux C-suite (les trois sources).

**Solutions Architect (SA)** : Fournit des conseils architecturaux transversaux — strategies d'integration, revue des modeles d'ontologie, pont entre equipes FDE et organisations d'ingenierie client. Pas tous les pilotes disposent d'un SA dedie (Claude).

**Forward Deployed Infrastructure Engineer (FDIE)** : Gere le deploiement de la plateforme pour les environnements on-premise ou air-gapped — clusters Kubernetes, reseau, stockage, exigences de conformite. Implication variable : peu de temps FDIE en SaaS, un FDIE dedie a temps plein sur les deploiements gouvernementaux classifies (Claude, Perplexity).

**Mise a l'echelle :** Pour les comptes strategiques, l'equipe passe a 10-20+ personnes (NHS, Army Vantage, BP) (Claude).

Le DS travaille aux cotes des ingenieurs et des **Product Designers** dans les deploiements, impliquant que l'UI/UX n'est pas purement concue par les ingenieurs (GPT). [CONTRADICTION] **(Perplexity)** indique qu'il n'y a pas de role dedie "UI designer" dans l'equipe FDE standard; le FDE construit l'UI, avec le DS qui pilote les exigences et boucles de feedback.

---

### 3. Phase 1 : Decouverte et collecte de donnees (semaines 1-3)

#### 3.1 Semaine 1 — Kickoff, cartographie des parties prenantes, immersion

**Arrivee sur site :** L'equipe FDE arrive sur site au Jour 1 avec un briefing minimal — le biais culturel de Palantir est "prends l'avion d'abord, pose des questions ensuite" (Perplexity). Le Foundry use case lifecycle fournit un template d'apercu de use case et un format canonique de requirements fonctionnels : `[User Type] [Interface] [Decision] [Decision Inputs] [Action]` — les deploiements Palantir sont centres sur les decisions, pas sur les listes de requirements (GPT).

**Qui ils rencontrent :**
- **Sponsor executif** (CEO, COO, CDO) : reunions 1-a-1 ou petit groupe, cadence hebdomadaire, le DS mene (Perplexity)
- **Chefs de departements / VP** : 2-4 entretiens par departement pour comprendre structure, douleurs, et dynamiques politiques (Perplexity)
- **Operateurs de premiere ligne** : les personnes qui utiliseront reellement le logiciel. Les FDE marchent litteralement sur le plancher d'usine, dans le service hospitalier, ou au desk de trading (Claude, Perplexity). A Airbus, Nabeel Qureshi "s'est installe a Toulouse pendant un an et a travaille a l'usine aux cotes des gens de la production quatre jours par semaine" (Perplexity)
- **Proprietaires de donnees / gatekeepers IT** : souvent les parties prenantes les plus adversaires (Perplexity)
- **Proprietaire IT/securite** pour les politiques reseau et identite (GPT)

**Nombre d'entretiens :** [CONTRADICTION] **(Claude)** indique **10-30 entretiens de parties prenantes dans les deux premieres semaines**. **(GPT)** indique que la documentation Palantir ne prescrit pas de nombre precis d'entretiens. **(Perplexity)** ne donne pas de chiffre precis.

**Repartition du temps :** Le temps se repartit environ **60 % entretiens / 40 % observation** (Claude). [CONTRADICTION] **(Perplexity)** indique que dans les contextes manufacturing, les FDE passent les 1-2 premieres semaines "principalement a observer et poser des questions, avec peut-etre 20-30 % du temps sur la configuration systeme reelle" — suggerant une balance inversee (plus d'observation que d'entretiens formels).

**Methodologie de cartographie des parties prenantes :** Pas de guide d'entretien rigide — l'approche est plus proche du "travail de terrain anthropologique" que du consulting structure (Perplexity). Les FDE sont formes avec les concepts de Keith Johnstone (*Impro*) — le vocabulaire de l'entreprise est "sature d'Impro-ismes" comme le "casting" (identifier qui detient le pouvoir reel vs. l'autorite nominale) et les dynamiques de statut (Perplexity). L'objectif est d'identifier rapidement :
1. Le **champion** dont la carriere est liee au succes du projet
2. Les **bloqueurs** (generalement middle-management data gatekeepers dont le pouvoir derive du controle du flux d'information)
3. Les **allies de premiere ligne** qui feront pression sur leurs chefs

Sarah Constantin decrit la strategie explicitement : "Win the hearts of front-line workers... use your allies on the bottom (front-line workers) and the top (executives) to squeeze out your opponents in the middle" (Perplexity).

**Guide d'entretien reconstruit aligne sur le template Foundry (GPT) :** Les questions les plus discriminantes mappent directement aux champs du template : "Quelle decision prenez-vous ?" "Quels inputs faites-vous confiance ?" "Ou les obtenez-vous ?" "Quelle action prenez-vous et quel changement d'etat ?" "Quel est le KPI d'une bonne decision ?"

**(Claude)** propose cinq themes de questions fondamentaux : *Quelles decisions prenez-vous chaque jour ? De quelles informations avez-vous besoin ? D'ou viennent-elles ? Qu'est-ce qui est casse dans ce processus ? Que feriez-vous avec une information parfaite ?*

**Cadence de reunions etablie (Claude) :**
- **Daily standup interne** (15 min) — equipe Palantir uniquement, synchronisation sur decouvertes et bloqueurs
- **2-3 sessions de travail par semaine** avec analystes et operateurs client
- **Update executif hebdomadaire** — bref, centre sur l'impact, typiquement 30 minutes avec le sponsor

Le DS attend des sessions de travail quotidiennes avec les vrais utilisateurs des le debut, car le modele de deploiement est base sur l'immersion dans "comment ils travaillent" (GPT).

**Artefacts produits en semaine 1 :**
- Carte des parties prenantes documentant noms, roles, niveau d'influence, propriete des donnees, et disposition envers le projet (champion, neutre, hostile) (Claude)
- Premiers diagrammes de processus informels (whiteboard, swimlane informels, pas de BPMN formel) (Claude, Perplexity)
- Esquisse du paysage de donnees identifiant systemes, bases de donnees, APIs, et file stores connus (Claude)
- Notes de reunion de chaque entretien (Claude)
- Premier "use case overview" et liste initiale de requirements fonctionnels (GPT)
- Plan d'acces listant sources de donnees, proprietaires, credentials necessaires, et pattern reseau utilise (GPT)
- Documentation collaborative via Notepad, stockee dans un Project Foundry (GPT)

En parallele, l'ingenierie commence la preparation de l'environnement cote client : identifier les 1-2 premieres sources de donnees connectables rapidement et valider le chemin reseau (connectivite directe vs agent sur un reseau separe) (GPT).

#### 3.2 Semaine 2 — Decouverte des donnees et negociation d'acces

**Immersion workflow :** L'equipe s'embarque avec les utilisateurs operationnels pour observer le workflow de bout en bout et extraire les "moments de decision" et changements d'etat. Les descriptions publiques du travail forward deployed soulignent l'observation sur site pour capturer le savoir tacite que le logiciel d'entreprise typique manque (GPT). L'observation est critique car le processus "reel" differe presque toujours du processus documente (Claude). Un FDE chez un client manufacturing pourrait decouvrir que les operateurs contournent entierement l'ERP, tracant les donnees critiques dans des tableurs personnels (Claude).

**Inventaire des donnees :** Les FDE se reorientent vers le catalogage precis des sources de donnees. Ils construisent un **inventaire de donnees** documentant chaque systeme source : type de base, proprietaire, volume approximatif, frequence de rafraichissement, problemes de qualite connus, et mecanisme d'acces (Claude). Cet inventaire identifie typiquement **15-40 sources de donnees** dans un deploiement de taille moyenne, bien que seules **3-10** seront connectees pendant le pilote (Claude).

Les donnees sont souvent dans des formats hostiles : "PDFs, notebooks, fichiers Excel (mon Dieu, tellement de fichiers Excel)". Chez un constructeur aeronautique, les resultats de tests qualite des avions etaient sous forme de "PDFs manuscrits scannes" (Perplexity, citant Nabeel Qureshi).

**Questions posees aux proprietaires de donnees (Perplexity) :** "Dans quel systeme c'est ? A quelle frequence mis a jour ? Qui a acces ? Quel format ? A quel point fiable ? Que signifie reellement ce champ ?"

**Questions forcees par la plateforme Foundry (GPT) :** "Ou est-ce heberge ?" (direct vs agent), "quel modele de credentials ?", "quel type de sync ?" (batch file vs table), "quel type de transaction ?" (SNAPSHOT vs APPEND), "est-ce que le schema change ?" (possibilite de bloquer les syncs sur changement de schema).

**Evaluation de la qualite des donnees :**
- **(Claude)** decrit un rubrique pratique, pas un framework de scoring formel. Les FDE evaluent sur quatre dimensions : **completude** (nulls et lacunes), **fraicheur** (frequence de mise a jour, staleness), **coherence** (les definitions matchent-elles entre systemes), **accessibilite** (peut-on reellement y acceder). Les sources sont triees en trois buckets : connecter maintenant, connecter plus tard, ne vaut pas la peine.
- **(GPT)** identifie trois couches de controle qualite natives a Foundry : health checks (fraicheur, succes/duree du build), unit tests Pipeline Builder (outputs attendus au niveau logique), et data expectations codees qui peuvent annuler les builds en cas d'echec.
- **(Perplexity)** indique qu'aucun framework de scoring formel n'a ete divulgue, mais les FDE evaluent : completude, fraicheur, format (structure vs non-structure), difficulte d'acces, et sensibilite politique.

**La politique d'acces aux donnees — le plus gros bloqueur :** C'est la partie la plus difficile et la plus chronophage du pilote. Nabeel Qureshi note : "Vous aviez une entreprise achetant un pilote de 8-12 semaines, et nous passions les 8-12 semaines juste a obtenir l'acces aux donnees, et la derniere semaine a se depechner pour avoir quelque chose a montrer" (Perplexity).

**Playbook de negociation d'acces (synthese des trois sources) :**
1. **Commencer par les donnees deja accessibles** — APIs publiques, drives partages, CSVs exportes — pour construire un prototype sans avoir besoin de la permission de quiconque (Claude)
2. **Demontrer la valeur au gatekeeper** — leur montrer comment la plateforme integree pourrait aider *leur* equipe, pas seulement celle du sponsor (Claude)
3. **Leverager le sponsorship executif** — faire en sorte que le champion senior mandate l'acces quand le relationship-building echoue (les trois sources)
4. **Construire la pression frontline** — les operateurs qui voient la valeur font pression sur leurs managers pour cooperer (Perplexity)
5. **Adresser les preoccupations securite de front** — la plateforme Palantir a du RBAC integre, de la securite row-level, des audit trails et des markings — implementer Palantir rend souvent les donnees *plus* securisees (Perplexity)
6. **Contourner entierement** — trouver des sources alternatives ou faire en sorte que les executifs overrident les restrictions (Claude)
7. **Etre patient mais persistant** — "The Palantir Way is labor-intensive and virtually impossible to systematize. You have to throw humans at the persuasion problem" (Perplexity, citant Sarah Constantin)
8. **Escalade organisationnelle via les roles Foundry** : la configuration des politiques de sortie reseau dans Control Panel peut necessiter des roles privilegies specifiques ("Information security officer"), ce qui est un levier d'escalade concret (GPT)

Le DS gere la dimension politique pendant que les FDE gerent l'evaluation technique. Division critique : les FDE ne devraient jamais etre en position d'argumenter pour l'acces aux donnees en reunion — c'est le travail du DS, arme de la couverture executive (Claude).

**Artefacts produits en semaine 2 :**
- Premiere passe : esquisse du modele objet, diagramme de lifecycle, liste d'enrichissements (GPT)
- Enregistrement de "source setup" : type de source, ou sauvegarde (Project), modele de credentials (service account), et si le compute tourne en Foundry worker ou agent worker (GPT)
- Service accounts dedies scopes specifiquement pour l'acces requis (GPT)

#### 3.3 Semaine 3 — Priorisation des use cases et setup environnement

**Priorisation des use cases :** A la semaine 3, l'equipe a suffisamment de contexte pour prioriser. L'equipe restreint a **1-3 use cases**, typiquement un principal et un secondaire (les trois sources).

**Framework de selection :** (Claude) decrit un **framework 2x2** (pas toujours formalise) : axe vertical = **valeur business** (intensite de la douleur x frequence x nombre d'utilisateurs affectes), axe horizontal = **faisabilite** (readiness des donnees x complexite technique x temps de demonstration).

**(Perplexity)** indique que le framework de l'IFC (partenaire Palantir) decrit une matrice 2x2 "Impact vs. Implementation Complexity" avec quadrants : Quick Wins, Strategic Investments, Easy Benefits, et Avoid/Defer.

**(GPT)** decrit une matrice de scoring reconstruite : impact; readiness des donnees; clarte du workflow; support des parties prenantes; potentiel d'expansion. Inclut aussi des "flags" anti-patterns : investigation insuffisante des douleurs, requirements ancres sur des elements UI, focus trop restreint sur les utilisateurs, scoping qui ne porte pas jusqu'aux decisions.

**Le test "hair on fire" (Claude) :** Quelqu'un perd-il le sommeil a cause de ce probleme ? Le use case ideal se situe a l'intersection de :
- **Douleur elevee** : un vrai probleme operationnel coutant temps, argent ou risque quotidiennement
- **Disponibilite des donnees** : les donnees requises existent et sont accessibles
- **Sponsorship executif** : quelqu'un d'assez puissant pour lever les obstacles
- **Demonstration rapide** : un prototype fonctionnel en 2-3 semaines

Les FDE evitent specifiquement les use cases necessitant une integration massive de donnees, des donnees politiquement sensibles, ou des problemes necessitant le developpement de modeles ML avant de montrer de la valeur (Claude).

**Criteres de selection detailles (Perplexity) :**

| Critere | Poids |
|---------|-------|
| Sponsorship executif | Critique |
| Readiness des donnees | Critique |
| Douleur frontline | Eleve |
| ROI demontrable (quantifiable en $/temps en 90 jours) | Eleve |
| Potentiel d'expansion | Moyen |
| Faisabilite technique (prototype en 2-4 semaines) | Eleve |

Aucune matrice de scoring formelle n'a ete divulguee publiquement (Perplexity). La culture Palantir valorise le jugement sur les frameworks (Perplexity).

Si on veut imiter la posture "fast ramp" moderne de Palantir, noter que Palantir commercialise les **AIP Bootcamps** comme allant de 0 a use case en 1-5 jours — une version extreme de la priorisation du "fast-to-demonstrate operational value" (GPT).

**Setup environnement :** En parallele, le FDIE (si assigne) travaille sur le setup. Pour Foundry SaaS : configuration de l'enrollment Foundry, creation des comptes utilisateurs, et etablissement de la connectivite reseau. Pour les deploiements on-premise (courants en defense et sante) : installation de Foundry sur l'infrastructure client — un processus pouvant prendre 1-2 semaines (Claude).

**Artefacts cles en fin de semaine 3 :**
- Document de use cases priorise avec criteres de succes clairs (les trois sources)
- Inventaire de donnees avec statut d'acces et evaluation qualite (les trois sources)
- Diagrammes de processus pour les use cases cibles (plus detailles que semaine 1) (Claude)
- Environnement Foundry provisionne et pret pour l'ingestion (Claude)
- Plan de projet initial avec jalons jusqu'a la semaine 12 (Claude)
- Premier squelette de pipeline et premieres entites ontologie (GPT)
- v1 use case brief : decisions, counterparts, requirements fonctionnels, outcomes/KPIs, douleurs (GPT)

**Point de decision :** Les use cases selectionnes en semaine 3 faconnent l'ensemble du pilote. C'est la decision a plus fort levier de l'engagement de 90 jours (Claude).

---

### 4. Phase 2 : Conception de l'ontologie et integration des donnees (semaines 2-6)

#### 4.1 Role et nature de l'ontologie

L'ontologie Foundry est une "couche operationnelle dynamique et semantique — un jumeau numerique — du paysage operationnel complet d'une organisation" (Perplexity). Elle repose sur des actifs numeriques integres (datasets, tables virtuelles, modeles) et represente les contreparties du monde reel comme des objets, proprietes, et liens, plus des elements cinetiques : actions, fonctions, et securite dynamique (GPT).

L'ontologie est le differentiateur intellectuel central de Palantir — une couche semantique mappant les entites du monde reel en Object Types avec Properties et Links (Claude). Le processus de design est profondement collaboratif, mene par la comprehension du domaine plutot que par le schema de base de donnees (Claude).

#### 4.2 Processus de conception de l'ontologie

**Comment un FDE decide ce qui devient un Object Type :** La question directrice est "Quelles entites les utilisateurs pensent-ils et recherchent-ils dans leur travail quotidien ?" (Claude). Si les gens de la production parlent de "work orders", "non-conformites" et "pieces manquantes", ceux-ci deviennent des Object Types. L'exhaust de donnees que personne ne reference reste comme raw datasets (Perplexity).

**Decomposition Foundry (GPT) :** Le process de solution design donne la decomposition pratique :
- Si le concept est une entite de premiere classe participant aux decisions et joignant le workflow → **Object Type**
- Si c'est une caracteristique → **Property**
- Si c'est une relation necessaire a la navigation et aux requetes → **Link Type**

**Distinction plus fine (GPT) :** Object types "core" mappent directement aux granularites du systeme de reference (system-of-record); "derived" existent quand le concept business existe mais aucun systeme source ne le represente; "use case" sont edites via les workflows operationnels (ex: tickets d'alerte).

**Heuristique de bruit (GPT) :** Si un concept n'apparait pas dans une decision, n'a pas de transitions d'etat, et ne joint pas significativement d'autres concepts, c'est probablement du bruit pour la premiere tranche du pilote.

**Le processus de creation d'Object Type dans Ontology Manager (Claude) :**
1. Naviguer vers Ontology Manager dans Foundry
2. Creer un nouvel Object Type avec un display name (PascalCase, singulier : `WorkOrder`, `FlightPath`)
3. Selectionner le **backing dataset** — le dataset Foundry dont les lignes representent les instances de ce type
4. Definir la **primary key** — la colonne identifiant de maniere unique chaque instance
5. Mapper les colonnes du dataset aux **Properties** avec des definitions typees (String, Integer, Double, Boolean, Date, Timestamp, GeoPoint, GeoShape, Array, Attachment, Timeseries)
6. Definir la **title property** — quelle propriete s'affiche comme label de l'objet a travers les UIs
7. Configurer les flags **searchable**, **filterable**, et **sortable** sur les proprietes
8. Definir les **Link Types** connectant les Object Types : one-to-one, one-to-many, ou many-to-many, backes par des relations de cle etrangere
9. Optionnellement creer des **Interface Types** — contrats abstraits que plusieurs Object Types implementent (ex: une interface "Asset" partagee par Vehicle et Equipment)

**Building blocks de l'ontologie (Perplexity) :**
- **Object Types** : entites du monde reel (Customer, Aircraft, Work Order, Patient, Flight)
- **Properties** : attributs de ces entites (name, status, date, location)
- **Link Types** : relations entre entites (Flight → assigned_to → Aircraft, one-to-many ou many-to-many)
- **Action Types** : operations que les utilisateurs peuvent effectuer (Approve Order, Assign Technician)
- **Functions** : logique business arbitraire (calculer des valeurs derivees, valider des contraintes)
- **Interfaces** : abstractions polymorphes (tous les "Trackable Items" partagent une forme quel que soit leur type)

**Conventions de nommage :**
- Object Types en PascalCase singulier : `Customer`, `WorkOrder` (Claude)
- Properties en camelCase : `firstName`, `orderDate` (Claude)
- Link Types en relations descriptives : `customer_orders`, `flight_departsFrom` (Claude)
- Action Types en verb-noun : `CreateWorkOrder`, `AssignTechnician` (Claude)
- Les Object Type IDs sont auto-generes a partir du display name et **deviennent immutables apres le premier deploiement** — les equipes doivent traiter les IDs comme des identifiants stables (GPT, Perplexity)
- Best practice : utiliser des noms prefixes pour eviter les conflits dans les ontologies multi-tenant (ex: `supply-chain-shipment`, `hr-employee`) (Perplexity)
- Les noms pluriels s'auto-remplissent (GPT, Perplexity)

**Nombre d'iterations :** Les FDE passent typiquement par **3-5 iterations de design d'ontologie** avant que le schema se stabilise pour le premier use case (Claude, Perplexity). Le design initial commence minimal — **5-10 Object Types de base** — et croit a mesure que des use cases supplementaires sont ajoutes. Les deploiements matures peuvent atteindre **50-100+ Object Types** (Claude). (GPT) note que les docs publiques ne donnent pas de nombre d'iterations, mais que le mecanisme de branching Foundry supporte une iteration rapide puis une stabilisation progressive.

Ted Mabrey decrit comment "le client reformule completement une charte de projet chaque mois" — le scope creep est bienvenu car "la mission du client l'exige" (Perplexity).

**Validation client :** Les FDE montrent typiquement le design d'ontologie aux utilisateurs business dans une revue informelle — souvent via Object Explorer, qui permet aux utilisateurs non-techniques de naviguer les objets, voir les proprietes, et naviguer les liens (Perplexity). Le DS dirige ces sessions, traduisant entre structure technique et sens business (Perplexity). (Claude) mentionne des "working sessions where FDEs display the ontology visually and ask: Does this match how you think about your world?"

**Artefacts de design d'ontologie (GPT) :** Trois artefacts formalises via le process de solution design Foundry :
1. **Object model sketch** (object types et link types)
2. **Lifecycle diagram** (actions comme machine a etats)
3. **Liste d'enrichissements + attentes d'interface**

Foundry reference aussi **Flow Capture** comme capacite pour enregistrer les workflows et generer de la documentation (GPT).

**Brevets comme corroboration (GPT) :** Des brevets Palantir plus anciens decrivent la creation et le stockage d'une ontologie avec object types et property types, et l'association de definitions de parseur qui transforment les donnees d'entree en formes compatibles. Ceci est coherent avec l'architecture moderne "ontologie + pipelines/transforms".

**Brevets pertinents supplementaires (Perplexity) :**
- US20160314155A1 — Data Integration Pipeline : architecture en deux phases (ingest + import)
- US9946777B1 — Systems for Facilitating Data Transformation : generation d'un DSL a partir du schema source + ontologie cible
- US20230289153A1 — Workflow Application and UI Builder : architecture de Workshop
- US20240354322A1 — LLM-Based Data Object Extraction : LLMs pour auto-generer les mappings d'ontologie
- US20230103939A1 — Synchronization of Data Across Ontologies : sync cross-systeme bidirectionnelle
- US10866792B1 — Rules-Based Cleaning of Deployment Pipelines : validation automatisee des pipelines

#### 4.3 Construction des pipelines de donnees

**Architecture three-layer (Claude) :** Les pipelines Foundry suivent une architecture a trois couches : **raw → clean → semantic**. Les datasets raw mirroring les systemes sources exactement. Les datasets clean appliquent les transformations (deduplication, type casting, null handling). Les datasets semantic backent les Object Types de l'ontologie.

**Sequence documentee de pipeline (GPT) :** Checklist ordonnee officielle :
1. Structure de Project recommandee
2. Construire un batch pipeline dans Pipeline Builder ou Code Repositories pour nettoyer/filtrer/joindre
3. Mapper les datasets finaux en object types et link types de l'ontologie
4. Definir les schedules
5. Ajouter unit tests, branching/release, et health checks pour la robustesse

**Pipeline Builder (no-code, visuel) :** Gere la plupart des transformations pendant les pilotes. Application principale de Foundry pour l'integration de donnees rapide, flexible et scalable (les trois sources).

Processus etape par etape (Claude) :
1. Ajouter des noeuds de dataset input au canvas visuel
2. Appliquer des transforms : Join (inner, left, right, full outer), Filter, Aggregate (sum, count, avg, min, max), Add/Rename/Drop/Cast columns, Union, Pivot/Unpivot, Window functions, Deduplicate
3. Previsualiser les donnees a n'importe quel noeud avant le build
4. Configurer le dataset output
5. Definir le schedule : manuel, cron-based (horaire, quotidien, hebdomadaire), ou triggered (build quand les datasets upstream changent)
6. Choisir le type de build : snapshot (remplacement complet) ou incremental (traiter seulement les nouvelles/changees)

Pipeline Builder supporte l'ajout d'"Ontology outputs" pour guider l'integration vers des donnees propres et structurees; inclut des champs de nommage d'object type explicites (GPT, Perplexity).

**Code Repositories (PySpark/Python) :** Pour les transformations complexes depassant les capacites de Pipeline Builder. L'API transform utilise des decorateurs (Claude) :

```python
@transform_df(
    Output("/path/to/output"),
    source=Input("/path/to/input")
)
def compute(source):
    return source.filter(source.status == "active")
```

Testing via pytest avec `TransformTestContext` de Foundry pour mock inputs/outputs. Chaque commit declenche des checks automatises — linting, type checking, et unit tests — via le CI/CD integre de Foundry (Claude).

**Choix Pipeline Builder vs Code Repositories (GPT) :** Pipeline Builder est positionne comme environnement graphique/formulaire collaboratif avec processus de release rigoureux sans code; Code Repositories pour les pipelines code-first. Le pattern pilote tend a commencer avec Pipeline Builder pour la vitesse et la comprehension partagee, puis introduire Code Repositories pour la logique complexe.

**Nombre typique de pipelines pilotes :** **10-30 pipelines automatises** construits pendant un engagement de 90 jours, connectant 3-10 sources de donnees (Claude).

**Choix batch vs incremental vs streaming (GPT) :** Foundry distingue explicitement ces trois formes et avertit que les pipelines incrementaux ajoutent de la complexite.

**Testing des pipelines :**
- **Pipeline Builder unit tests** : definis avec des inputs test, des noeuds de transform selectionnes, et des outputs attendus; les unit tests doivent reussir avant de merger une proposal (GPT)
- **Data expectations** : definies en code, peuvent annuler les builds en cas d'echec, s'integrent avec Data Health, et supportent le change management via le code review (GPT)
- **Health checks** : valident succes du job/build, duree du build, et fraicheur a travers le pipeline (GPT)
- Le brevet US10866792B1 decrit des "deployment pipeline cleaning rules" automatisees verifiant : noms de datasets invalides, types de donnees invalides, donnees stale, branches cassees, et mappings invalides (Perplexity)
- [CONTRADICTION] **(Perplexity)** note que "le testing formel d'unites varie selon le FDE — la culture valorise la vitesse sur la couverture de tests pendant la phase pilote". **(GPT)** met davantage l'accent sur le testing formel comme partie integrante du processus.

#### 4.4 Connexion des sources de donnees

**Connecteurs supportes :** Foundry supporte **200+ connecteurs out-of-the-box** (Perplexity). Types : JDBC databases (PostgreSQL, MySQL, SQL Server, Oracle, Snowflake, Redshift, BigQuery), file systems (S3, Azure Blob, GCS, SFTP), APIs (REST, OData), applications SaaS (Salesforce, SAP, Workday, ServiceNow, JIRA), et sources streaming (Kafka, Kinesis) (Claude).

**Deux modes de connexion :**
- **Connexion directe** (systemes accessibles via Internet) : definir politiques egress, configurer credentials, setup syncs (Perplexity)
- **Connexion basee sur agent** (systemes on-prem/air-gapped) : installer un agent Palantir dans le reseau client qui agit comme intermediaire securise (les trois sources)

**Installation de l'agent (detail technique) :** L'agent est un programme telechargeable installe dans le reseau organisationnel, gere depuis Foundry, utilise pour connecter aux sources et ingerer de maniere securisee avec des tokens d'acces restreints (GPT). Requiert : provisionner un host (VM Linux recommandee), configurer egress/ingress, valider la connectivite, et definir les redemarrages automatiques (GPT). L'agent maintient une connexion HTTPS sortante vers Foundry sur le port 443 — pas de regles firewall entrantes necessaires (Claude, Perplexity). L'agent tourne sur Java 21+ (Perplexity). HA (haute disponibilite) atteint en assignant plusieurs agents a une seule source (Perplexity). "Certaines organisations peuvent fonctionner a long terme avec des agents configures pendant la premiere semaine d'un deploiement Foundry" (Perplexity). "La plupart des utilisateurs Foundry n'auront jamais besoin de configurer un nouvel agent eux-memes — le setup d'agent necessite des competences IT, bien que le meme agent puisse etre reutilise pour supporter plusieurs sources" (Perplexity).

**Configuration des syncs :** Les batch syncs creent des datasets; peuvent etre previsualises; peuvent etre schedules; incluent des options de configuration comme type de transaction (SNAPSHOT vs APPEND), duree maximale, et blocage des changements de schema (GPT). Supportent les file syncs et table syncs (GPT).

**Temps pour connecter une source :**
- **(Claude)** : Connexions database simples : **1-3 jours** tests inclus. Sources complexes avec problemes firewall, VPN, ou decouverte de schema : **1-2 semaines**.
- **(Perplexity)** : 1-2 jours pour les sources cloud simples (S3, REST APIs); 3-7 jours pour les databases on-prem necessitant setup d'agent et negociation firewall; **semaines a mois** pour les sources politiquement contestees.

**Modes de defaillance courants :** Blocages firewall (le plus frequent), rotation de credentials cassant les syncs, changements de schema dans les systemes sources, et limitation de debit API (Claude, Perplexity). GPT ajoute : configuration proxy incomplete, certificats non approuves, incapacite de l'agent a atteindre le systeme source. Si vous ne designez pas pour le drift de schema, les pilotes cassent a la semaine 6 (GPT). Les goulots d'etranglement de privileges — la configuration de politique egress reseau dans Control Panel necessite des roles privilegies dans certains cas — vous pouvez etre bloque par l'acces organisationnel plutot que par la complexite technique (GPT).

---

### 5. Phase 3 : Actions, securite et construction d'application (semaines 4-10)

#### 5.1 Conception des Action Types (semaines 5-7)

Les Action Types transforment Foundry d'une plateforme d'analytics read-only en un systeme operationnel qui ecrit dans le monde reel (Claude, Perplexity).

**Comment les FDE identifient les actions a modeliser :** Observer ce que les operateurs *font* apres avoir analyse les donnees — assigner un technicien, fermer un ticket, approuver une commande, escalader un probleme (Claude). Interviewer les utilisateurs sur "que faites-vous avec ces donnees ?" (Perplexity). Le solution design Foundry rend le workflow explicite comme un **diagramme de lifecycle : une machine a etats d'Actions** que les utilisateurs prennent pour modifier les objets (GPT).

**Configuration dans Ontology Manager (Claude, Perplexity) :**
1. Creer un nouveau Action Type avec nommage verb-noun (`AssignTechnician`)
2. Definir les **parametres** — inputs types que l'utilisateur fournit (reference Object, String, Integer, Date)
3. Definir les **regles** — les mutations declenchees : Create Object, Modify Object, Delete Object, Create/Delete Link
4. Configurer les **regles de validation** — conditions appliquees avant execution (champs requis, verifications de plage, contraintes d'unicite, validation cross-parametre)
5. Definir les **side effects** — webhooks appelant des APIs externes, notifications, ou execution de Foundry Function
6. Configurer les **permissions** — qui peut executer ce type d'action
7. Definir le **mode de soumission** — synchrone (immediat) ou asynchrone (en file d'attente) (Claude)

**Comment les actions apparaissent dans les applications (GPT) :** Les actions peuvent etre des boutons dans les vues d'objets avec labels configurables, valeurs de parametres par defaut (y compris derivation depuis les proprietes de l'objet courant ou valeurs locales comme utilisateur courant et timestamp), et controles pour cacher/desactiver si invalide.

**Mecanisme de write-back :**

[CONTRADICTION] **(Claude)** decrit un systeme ou les actions ecrivent dans un **Edits dataset** append-only (transaction log). L'ontologie fusionne les edits avec les backing datasets pour presenter l'etat courant en temps reel. La reconciliation periodique par pipeline assure que les edits sont materialises dans les backing datasets. **(Perplexity)** decrit un "writeback dataset" associe a l'Object Type avec deux modes de permission : "Only allow edits via Actions" (plus restrictif, les utilisateurs n'ont besoin que de Read access) ou edits via Actions plus Forms, Object Explorer, et appels API (necessite Edit permissions sur le writeback dataset). Les deux descriptions ne sont pas necessairement contradictoires mais fournissent des perspectives differentes du meme mecanisme.

**Write-back via webhooks :** Foundry Data Connection Webhooks supporte les requetes HTTP sortantes vers des systemes externes, y compris le declenchement d'un webhook quand un utilisateur selectionne un bouton dans une application Foundry. Les webhooks sont lies a une Source qui stocke les credentials et peuvent etre rate-limited (GPT). Les webhooks permettent l'integration externe — declenchement de notifications Slack, mise a jour de databases externes, ou appel d'APIs downstream (Claude).

**Point de decision (GPT) :** Decider si le write-back est synchrone (appel webhook par action) ou staged (mise en file et reconciliation ulterieure). Les docs publiques couvrent les webhooks et l'integration d'actions mais ne mandatent pas un pattern unique.

**Ensemble minimum viable d'actions (GPT) :** Generalement une boucle d'approbation/triage, pas chaque exception possible. Decider si le write-back est requis dans le pilote ou peut etre simule.

#### 5.2 Configuration de la securite (semaines 5-7)

La securite est architecturalement fondamentale, pas boulonnee apres coup. Palantir "a compris tot que les luttes d'acces aux donnees etaient en partie liees a de vraies preoccupations de securite, et pouvaient etre allege en integrant des controles de securite dans la couche d'integration de donnees" (Perplexity).

**Couches de securite :**

| Couche | Mecanisme | Ce que ca controle |
|--------|-----------|-------------------|
| **Dataset-level** | ACLs (Read/Write/Discover) | Qui peut acceder au backing dataset (Perplexity) |
| **Project-level** | Projects + Roles (Viewer, Editor, Owner) | Limite organisationnelle et de securite primaire; la decouverte et l'acces (les trois sources) |
| **Markings** | Labels de classification (CONFIDENTIAL, PII, ITAR) | Criteres d'eligibilite additionnels; un utilisateur doit satisfaire toutes les markings appliquees (GPT, Claude, Perplexity) |
| **Row-level (Object Security Policies)** | Controles mandatoires, markings, comparaisons d'attributs utilisateur | Quelles instances d'objets un utilisateur peut voir (les trois sources) |
| **Column-level (Property Security Policies)** | Markings par-propriete | Quelles proprietes sont visibles — ex: cacher les donnees de salaire aux non-RH (les trois sources) |
| **Cell-level** | Combinaison object + property policies | L'utilisateur passe le check row mais echoue au check column → voit null pour cette cellule (Claude, Perplexity) |
| **Action-level** | Criteres de soumission + permissions de parametres | Qui peut executer quelles actions sur quels objets (Perplexity) |
| **App-level** | Workshop herite toute la securite Ontologie | Les apps ne peuvent pas overrider les permissions dataset ou Ontologie (Perplexity) |

**Markings — propagation automatique :** Si un dataset input porte un marking "PII", tous les datasets derives en heritent automatiquement a travers les pipelines (Claude).

**Granular policies (GPT) :** Configurent la securite row-level pour les datasets et objets via des ensembles de regles comparant les attributs utilisateur et les valeurs de donnees.

**Restricted views (GPT) :** Fournissent des controles row-level pour les donnees ontologie, mais **ne sont pas compatibles comme inputs de transforms de pipeline** car les pipelines doivent etre reproductibles a travers les utilisateurs. Limitation importante a considerer dans le choix de l'approche.

**Row-level security via mapping tables (Perplexity) :** Utilise des tables de mapping (utilisateur → usine, utilisateur → business unit) qui filtrent au moment de la requete.

**Configuration RBAC en pratique :** Le DS mene typiquement une session de type questionnaire avec l'equipe securite/conformite du client : "Qui devrait voir quoi ? Quels roles existent ? Quelles sont les classifications de sensibilite des donnees ?" (Perplexity).

**Ateliers securite (GPT) :** Sessions avec IT/securite et le proprietaire operationnel : "qui devrait voir quoi" traduit en groupes, roles, et politiques object-level.

**Test et debug de la securite :**
- Foundry fournit une capacite **"View as User"** / **"Check access"** permettant aux administrateurs de verifier ce qu'un utilisateur specifique peut et ne peut pas voir, permettant un test systematique des permissions avant le go-live (Claude, Perplexity)
- Checklist de test operationnel (GPT) : verifier les grants de roles, markings, acces aux object types, et markings de lineage des datasources

#### 5.3 Construction d'applications — Workshop, Quiver, Slate

**Choix de la surface applicative (GPT, les trois sources) :**
- **Workshop** (choix par defaut) : workflows inbox operationnels, no-code/low-code, le plus rapide a construire, couvre **80 %+** des besoins applicatifs operationnels (les trois sources). Decrit en interne comme "Retool-like UI for making webapps" (Perplexity)
- **Quiver** : dashboards analytiques ontology-native pour les business users qui ont besoin de charting self-service et d'exploration; les dashboards executifs peuvent commencer comme templates Quiver (GPT, Claude, Perplexity)
- **Slate** : HTML/CSS/JavaScript custom pour les UIs pixel-perfect, visualisations D3.js complexes, ou requirements depassant la widget library de Workshop. Maintenant de plus en plus remplace par OSDK + custom React apps (Claude, Perplexity)
- **Carbon** : peut unifier la navigation a travers les types d'utilisateurs (GPT)
- **Contour** : analytics dashboard-style, souvent utilise comme outil transitionnel avant l'adoption de Workshop (Perplexity)

**Bibliotheque de widgets Workshop (Claude, Perplexity) :**
- **Display :** Object Table, Object List, Card, Details Panel, Metric/KPI Card, Status Indicator, Property List, Object View, Object Set Title
- **Visualization :** Charts (line, bar, area, scatter, pie, heatmap, treemap, funnel), Map (Mapbox-based avec clustering et heatmaps), Timeline, Gantt, Graph/Network visualization
- **Input :** Button, Text Input, Number Input, Dropdown/Multi-select, Date Picker, Slider, Toggle, File Upload, Search Bar, Button Group, Filter List
- **Layout :** Container, Tabs, Accordion, Grid, Modal/Dialog, Sections, Conditional Visibility
- **Advanced :** HTML/iFrame embed, Form (auto-genere depuis les parametres Action Type), Scenario Manager, Scenario Selector

**Processus de construction d'application (Claude, Perplexity) :**
1. Creer un nouveau module Workshop dans un projet Foundry
2. Definir des **Object Sets** — collections filtrees et requetees d'objets ontologie (par type, filtres de propriete, traversee de liens)
3. Designer le **layout** avec containers, tabs, et widgets grille
4. Placer les **widgets d'affichage** et les lier aux Object Sets (ex: Object Table liee a "Active Work Orders")
5. Configurer le **systeme de variables** — modele d'etat reactif de Workshop ou les interactions widget (selection de ligne, clics de bouton) mettent a jour des variables qui cascadent vers d'autres widgets
6. Lier les **Action Types** aux boutons — mappant les parametres d'action aux inputs widgets ou variables
7. Configurer la **visibilite conditionnelle** — montrer/cacher les widgets selon les valeurs de variables
8. Definir les **permissions** — qui peut voir et utiliser l'application
9. Publier et iterer

**Iteration et feedback :** Les FDE iterent sur les applications Workshop **quotidiennement** pendant la phase de build, montrant aux utilisateurs des prototypes fonctionnels et reconstruisant d'apres le feedback (Claude). Le premier prototype fonctionnel est typiquement disponible dans les **2-3 jours** du debut du developpement applicatif (Claude). Descriptions publiques : les clients remarquent quand les equipes construisent un logiciel utilisable en une ou deux semaines (GPT).

**Volumes typiques du pilote :** Un pilote typique produit **3-10 applications Workshop** et **5-15 dashboards operationnels** (Claude). Le nombre d'iterations UI avant stabilisation va de **5-10 par application** (Claude, Perplexity).

**Sessions de feedback (Perplexity) :** Le DS organise des sessions d'iteration avec les utilisateurs client, montrant les progres et collectant le feedback dans des sessions de **30-60 minutes, 2-3 fois par semaine**.

---

### 6. Phase 4 : Formation, go-live et mesure du succes (semaines 8-12)

#### 6.1 Methodologie de formation (semaines 8-10)

La formation est explicitement partie du role de Deployment Strategist : mener les sessions de formation, assurer que l'usage est assez repandu pour avoir un impact operationnel concret, et presenter les resultats et propositions (GPT).

**Modele de formation par tiers (Claude) :**
- **Power users / citizen developers :** Formation la plus approfondie — **8-16 heures** (Claude) ou **16-40 heures** (Perplexity) sur plusieurs sessions. Apprennent a construire leurs propres applications Workshop, modifier les pipelines, et etendre l'ontologie. Identifies tot (typiquement semaine 4-5) sur la base de l'aptitude technique, expertise domaine, et enthousiasme (Claude). Deviennent le noyau de l'equipe Foundry interne du client (Claude).
- **Operateurs standard :** **2-4 heures** (Claude) ou **4-8 heures** (Perplexity) de formation specifique a l'application, centree sur l'utilisation des applications Workshop construites pour leur workflow.
- **Executifs :** **30-60 minutes** d'orientation dashboard — suffisant pour interpreter les dashboards Quiver et vues KPI Workshop de maniere autonome (Claude).

[CONTRADICTION] Les estimations d'heures de formation different legerement entre **(Claude)** (8-16h power users, 2-4h standard) et **(Perplexity)** (16-40h power users, 4-8h standard). Perplexity donne des fourchettes plus larges et plus elevees.

**Modes de livraison de la formation (Perplexity) :**
- **Sessions classroom/workshop onsite** : menees par le DS, typiquement en groupes de 5-15. Focus sur la navigation de l'application, comprehension du modele de donnees, et execution des actions de base.
- **Mentorat deskside** : sessions 1-on-1 ou un FDE ou DS s'assoit avec un operateur pour le guider dans le workflow en contexte reel.
- **Sessions virtuelles** : pour les equipes distribuees ou utilisateurs distants.
- **Apprentissage guide** : Palantir a une plateforme d'apprentissage (learn.palantir.com) avec des chemins de certification : Foundry Aware, Data Engineer, App Developer (Perplexity). Cela inclut des training tracks comme "Application Developer" couvrant la construction d'applications operationnelles avec Workshop et Quiver et l'application de write-backs avec Actions (GPT).
- **Train-the-trainer** : mecanisme cle de handoff — identifier 2-5 "power users" ou "citizen developers" du client qui deviendront des champions Foundry internes (Perplexity).

**Format de la formation :** Massivement hands-on. Les FDE utilisent les **sessions de pair-programming** comme mecanisme principal de transfert de connaissances — s'asseoir a cote d'un ingenieur client et construire quelque chose ensemble, plutot que donner un cours (Claude). Des "office hours" ou les FDE sont disponibles pour des questions ad-hoc completent les sessions formelles (Claude). Foundry emphasise la repetition de workflow, pas les tours de features (GPT).

**Materiels de formation produits :**
- Guides utilisateur pour chaque application Workshop (captures d'ecran, workflows pas-a-pas) (Claude, Perplexity)
- Documentation de l'ontologie (catalogue Object Type avec descriptions, definitions de proprietes, et diagrammes de relations) (Claude)
- Runbooks pipeline (schedules de rafraichissement de donnees, troubleshooting des modes de defaillance courants) (Claude)
- Video walkthroughs pour les taches communes (optionnel, selon preference client) (Claude)
- Templates "Playbook" montrant les patterns que les power users peuvent repliquer (Claude)
- Quick-reference cards pour les workflows et actions courants (Perplexity)
- Enregistrements video des sessions de formation (Perplexity)
- Chemins de certification pour les utilisateurs techniques (Data Engineer, App Developer) (Perplexity)

**AIP Bootcamps comme outil d'enablement accelere :** Depuis 2023, Palantir a superpose les **AIP Bootcamps** au modele FDE traditionnel. Ces workshops intensifs de **2-5 jours** compressent le cycle decouverte-prototype. Les clients amenent leurs propres donnees et problemes; les ingenieurs Palantir aident a construire des prototypes fonctionnels sur Foundry avec AIP (couche AI/LLM) en jours plutot qu'en semaines. Au T3 2024, Palantir avait complete **560+ bootcamps** — decrits comme le mecanisme d'acquisition client le plus efficace jamais mis en place (Claude). Les bootcamps ne remplacent pas le pilote de 90 jours — ils servent de proof of concept pre-pilote (Claude).

**AIP etend l'ontologie avec des capacites LLM :** AIP Logic definit des fonctions alimentees par des prompts operant sur les objets ontologie, AIP Assist fournit une interface langage naturel copilot-style dans les applications Workshop, et AIP Workflows permettent des processus agentiques multi-etapes avec approbation humaine. AIP respecte toutes les contraintes de securite existantes (Claude).

#### 6.2 Processus de go-live (semaines 10-11)

**Semaine 8 — UAT et posture de monitoring (GPT) :**
L'equipe passe de la construction pour quelques power users a la formation de roles plus larges et rend la fiabilite visible.

**Pre-go-live validation (Claude, les trois sources) :**
- Tous les pipelines de donnees fonctionnent sur schedule avec health checks passant (fourchettes de nombre de lignes, seuils de taux de null, validation de schema) (Claude)
- Configuration de securite testee via "View as User" pour chaque role (Claude)
- Action Types valides — toutes les regles de validation et mecanismes de writeback fonctionnant (Claude)
- Applications Workshop testees avec de vrais utilisateurs en mode pilote (Claude)
- Dashboards de monitoring configures avec alertes pour les echecs de pipeline, anomalies de qualite de donnees, et erreurs d'application (Claude)
- Pipeline health validation, data freshness checks, security policy audit, user access provisioning, action type testing, performance testing under load (Perplexity)

**Primitives de production readiness de Foundry (GPT) :**
- Schedules pour maintenir les syncs et builds en fonctionnement
- Health checks et visibilite Data Health a travers la lineage
- Integration notifications et issues, y compris auto-creation d'issue en cas d'echec de check
- Monitoring views pour collecter les checks et regles de monitoring et gerer l'alerte a l'echelle, y compris envoi d'alertes vers systemes externes (PagerDuty, Slack, webhooks)
- Processus de support recommandes : s'abonner aux monitoring views et integrer avec des outils d'alerte externes qui gerent les rotations d'astreinte

**Rollout controle :** Deploiement a un petit groupe pilote d'abord (1 equipe, 1 shift, 1 geographie), puis expansion (les trois sources). Surveiller les checks activement et adresser les echecs avec le processus de support concu (GPT).

**Daily "hypercare" stand-up** avec le lead ops client; revue d'incident si pannes; update executif hebdomadaire centre sur l'impact (GPT).

**Transition de FDE-operated a client-operated :**
La transition est graduelle, pas un cutover brutal (Claude, Perplexity). Pendant les semaines 10-12, les FDE reduisent systematiquement leur implication : d'abord ils arretent de construire de nouvelles features, puis ils arretent de corriger les problemes de routine (dirigeant les ingenieurs client pour le faire), et finalement ils passent a des check-ins consultatifs plutot qu'un travail quotidien embarque (Claude).

La documentation Foundry implique que la transition concerne fondamentalement la propriete de : schedules, checks, et subscriptions d'alerte; plus la gouvernance sur les branches et merges (GPT).

**Support post-go-live :**
- **Semaines 11-12 :** Le FDE reste disponible sur site ou a distance pour les escalades (Claude)
- **2-4 premieres semaines apres go-live :** equipe FDE reste on-call (Perplexity)
- **Mois 2-3 post-pilote :** Transition vers le modele standard customer success de Palantir avec check-ins periodiques (Claude)
- **Continu :** Mises a jour plateforme gerees via **Apollo** (infrastructure de deploiement continu de Palantir) avec capacites roll-forward/roll-back (Claude, Perplexity)
- L'equipe Baseline (Forward Deployed Infrastructure) gere les problemes operationnels fleet-wide (Perplexity)

**Phases de maturite organisationnelle Foundry (Perplexity) :**
La documentation Foundry Adoption decrit quatre phases, Phase 1 etant "Focus on use cases" (1-2 use cases en production, petite base utilisateur) et Phase 2 elargissant le scope.

**Roles du programme que le client devrait etablir (Perplexity, d'apres les docs Foundry Adoption) :**
- **Program Lead** : proprietaire principal du succes du Programme Foundry
- **Data Lead** : gere l'integration de donnees et la sante des pipelines
- **Ontology Lead** : possede la structure et l'evolution de l'ontologie
- **Head of Data Governance** : peut etre combine avec Data Lead ou Ontology Lead en Phase 1; standalone en Phase 3
- **Application Developers** : construisent et maintiennent les apps Workshop
- **Permissions Manager** : gere les politiques de securite et le controle d'acces

Palantir aide le client a etablir un **Centre d'Excellence (CoE)** avec des roles definis, du platform owner au permissions manager, pour que l'organisation puisse fonctionner de maniere autonome (Perplexity).

#### 6.3 Semaine 12 — Revue executive et cas d'expansion

**La revue executive :** Presentation formelle au leadership senior du client. Le DS dirige, avec le support FDE pour les questions techniques (les trois sources).

**Structure de la presentation (Claude) :**
1. **Enonce du probleme** — les defis operationnels identifies en decouverte
2. **Demonstration de la solution** — walkthrough live des applications Workshop montrant les donnees integrees et workflows operationnels
3. **Metriques d'impact** — resultats quantifies de la periode pilote (temps economise, couts evites, decisions ameliorees, risques mitiges)
4. **Metriques d'adoption** — utilisateurs actifs quotidiens/hebdomadaires, nombre de workflows remplaces, sources de donnees unifiees
5. **Roadmap d'expansion** — use cases, departements, et sources de donnees supplementaires identifies pour la prochaine phase
6. **Business case pour l'expansion** — ROI projete de l'expansion de 1-3 use cases pilotes a 10-20+ use cases enterprise

**KPIs de succes typiquement suivis (Claude, Perplexity) :**
- **Time-to-decision :** Reduction mesurable du temps entre disponibilite des donnees et action operationnelle
- **Adoption utilisateur :** Utilisateurs actifs quotidiens des applications Workshop vs cible
- **Unification des donnees :** Nombre de sources precedemment en silo maintenant connectees
- **Deplacement de processus :** Nombre de processus manuels (tableurs, chaines d'emails) remplaces
- **Gain d'efficacite :** Heures economisees par semaine par utilisateur sur des workflows specifiques — la metrique la plus persuasive, souvent exprimee comme "la generation de rapports reduite de 8 heures a 15 minutes" (Claude)
- **Impact operationnel quantifie :** Economies de couts, economies de temps, reduction d'erreurs, amelioration du throughput (Perplexity)
- **Satisfaction utilisateur :** Feedback qualitatif des operateurs et executifs (Perplexity)
- **Time-to-value :** A quelle vitesse le premier use case a livre des resultats mesurables (cible : 60-90 jours) (Perplexity)

**Exemples concrets de metriques d'impact de case studies publics (Perplexity) :**
- General Mills a economise environ **14 M$ annuellement (40k$/jour)**
- Fujitsu a atteint une **reduction de couts annuels de 9 M$ en 3 mois**
- AARP a lance le premier prototype en **45 jours**
- Un use case de consolidation logistique Foundry a remplace le systeme et processus existant en **6 semaines**, mesurant : camions economies, economies totales, economies de kilometrage, % d'utilisation (GPT)

**Contenu du document d'expansion (synthese des trois sources) :**
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

**Solution Designer** existe specifiquement pour creer des representations architecturales des solutions Palantir-plateforme, comparer des propositions, et supporter le transfert de connaissances (GPT).

**Point de decision strategique (GPT) :** Decider si l'expansion est **horizontale** (plus de use cases) ou **verticale** (meme workflow a l'echelle a travers sites/fonctions). La guidance de sequencement documentee emphasise la construction d'actifs fondationnels d'abord pour que les technologies multiplicatrices et workflows plus larges se debloquent ensuite.

---

### 7. Semaines 9-10 — Hardening et gouvernance

**Iteration basee sur l'usage reel (GPT) :** L'equipe utilise le branching pour evoluer les pipelines, l'ontologie, et les apps avec des merges controlees. Foundry branching supporte les proposals, merge checks, et assignation de reviewers selon le type de ressource et la politique d'approbation.

**Operationnalisation du processus de release (GPT) :** Les pipelines de production devraient utiliser le branching et un processus de release s'ils ne sont pas deja utilises pendant le developpement.

**Decision : quoi durcir maintenant (GPT) :** Les descriptions publiques du modele de Palantir notent que les equipes forward deployed optimisent pour la vitesse et peuvent accepter de la dette technique; les equipes product "productisent" ensuite. Cela implique une decision consciente "what to harden now" vs ce qui reste en hack pilote.

**Decision (GPT) :** Decider si le systeme de production du pilote est "assez bon" pour deprecier l'ancien processus.

---

### 8. Rythme quotidien typique d'un FDE

**(Perplexity)** fournit un planning quotidien detaille base sur le blog post "Day in the Life" d'un DS et le recit de Nabeel Qureshi :

**Phase initiale (semaines 1-3) :**
| Heure | Activite |
|-------|----------|
| 08:00 | Arrivee sur site, petit-dejeuner + emails, revue du statut de sync nocturne |
| 09:00 | Daily standup equipe Palantir (15 min) : bloqueurs, priorites, qui rencontre qui |
| 09:30 | Entretien parties prenantes / marche sur le terrain — observer operateurs, poser questions, mapper processus |
| 11:00 | Reunion de negociation d'acces donnees avec IT / data owners |
| 12:00 | Dejeuner avec l'equipe client (le relationship building est essentiel) |
| 13:00 | Travail pipeline : configurer connecteurs, construire transforms initiales, debugger qualite |
| 15:00 | Sync avec DS sur priorisation use cases et politique des parties prenantes |
| 16:00 | Sync interne Palantir : mise a jour equipe compte, escalade bloqueurs |
| 17:00-19:00 | Continuation du travail technique (pipelines, esquisse ontologie) |

**Phase build (semaines 3-8) :**
| Heure | Activite |
|-------|----------|
| 08:00 | Verifier sante pipeline, revue builds nocturnes |
| 09:00 | Daily standup (equipe Palantir + counterparts techniques client) |
| 09:30 | Iteration ontologie / construction app Workshop |
| 11:00 | Demo client / session feedback (30-60 min, 2-3x/semaine) |
| 12:00 | Dejeuner avec utilisateurs |
| 13:00 | Implementer le feedback de la session du matin |
| 14:00 | Session config securite avec equipe conformite client |
| 15:00 | Design Action Type — modeliser decisions utilisateurs comme operations write-back |
| 16:00 | Check-in executif hebdomadaire (DS dirige) |
| 17:00-19:00 | Travail technique, hardening pipeline, testing |

**Phase handoff (semaines 8-12) :**
| Heure | Activite |
|-------|----------|
| 09:00 | Session formation avec groupe utilisateurs (classroom ou deskside) |
| 10:30 | Mentorat power user : enseigner aux citizen developers a modifier les apps Workshop |
| 12:00 | Dejeuner |
| 13:00 | Preparation go-live : scheduling pipeline, dashboards monitoring, setup alerting |
| 14:00 | Documentation et materiels de handoff |
| 15:00 | Preparation revue executive avec DS |
| 16:00 | Planification CoE : definir roles, responsabilites, chemins d'escalade pour equipe client |

---

### 9. Points de decision cles qui faconnent le deploiement

**(Perplexity)** fournit un tableau synthetique :

| Point de decision | Quand | Qui decide | Impact |
|-------------------|-------|------------|--------|
| Selection des use cases | Fin semaine 2 | Equipe FDE + sponsor executif | Determine tout le scope du pilote |
| Priorisation des sources de donnees | Semaines 1-3 | Equipe FDE selon faisabilite d'acces | Gouverne ce qui est constructible en 90 jours |
| Scope de l'ontologie | Semaines 2-4 | FDE lead + DS | Definit la "forme" du jumeau numerique |
| Pipeline Builder vs Code Repos | Par source | FDE | Visuel pour transforms simples; code pour logique complexe |
| Workshop vs Slate vs Quiver | Semaines 4-5 | Equipe FDE | Workshop par defaut; Slate seulement pour UIs custom complexes |
| Modele de securite | Semaines 4-6 | DS + conformite client | Determine visibilite des donnees par role |
| Scope du go-live | Semaines 7-8 | Equipe FDE + sponsor | Quels utilisateurs, quelle geographie, quel shift en premier |
| Proposition d'expansion | Semaines 10-12 | DS dirige, FDE supporte | Determine si Acquire se convertit en phase Expand |

Points de decision supplementaires (GPT) :
- **Semaine 1 :** Choisir la "thin slice" du pilote : un role utilisateur, une interface, une decision, une action
- **Semaine 1 :** Decider si la premiere source est cloud/SaaS joignable directement ou necessite un agent on-prem
- **Semaine 2 :** Decider quels concepts sont "core" vs "derived" vs "use case objects"
- **Semaine 3 :** Choisir batch vs incremental vs streaming
- **Semaine 4 :** Verrouiller le "core" de l'ontologie : qu'est-ce qui est object type de premiere classe vs attribut vs roll-up derive
- **Semaine 4 :** Decider quels enrichissements appartiennent a la couche data vs dans l'app
- **Semaine 5 :** Ensemble minimum viable d'actions pour la production
- **Semaine 6 :** Choisir restricted views vs object security policies pour l'enforcement row-level
- **Semaine 7 :** Write-back synchrone vs staged
- **Semaine 8 :** Definir le standard "production" du pilote (latence, fraicheur, uptime, fallback manuel)
- **Semaine 9 :** Decider ce qui devient capacite plateforme reutilisable vs hacks specifiques au pilote
- **Semaine 10 :** Definir qui possede quoi apres go-live (syncs echouees, builds, checks, write-backs echoues)
- **Semaine 11 :** Decider si le systeme de production du pilote est "assez bon" pour deprecier l'ancien processus
- **Semaine 12 :** Expansion horizontale (plus de use cases) ou verticale (meme workflow a l'echelle)

---

### 10. Facteurs critiques de succes

**(Perplexity)** synthetise les facteurs cles :
1. **Le sponsorship executif est non-negociable** — sans couverture top-down, les batailles d'acces aux donnees sont ingagnables
2. **Obtenir l'acces aux donnees vite** — chaque semaine passee a negocier est une semaine non consacree a construire de la valeur
3. **Livrer un "kernel of value" en semaine 2-3** — "quand une equipe heteroclite de jeunes de 20 ans est arrivee sur le site client et a construit un vrai logiciel que les gens pouvaient utiliser en une ou deux semaines, les gens ont remarque" (Nabeel Qureshi)
4. **Embrasser le scope creep** — "le FDE aspire au scope creep car la mission du client l'exige" (Ted Mabrey)
5. **Construire des relations avec les utilisateurs frontline** — ils sont a la fois la meilleure source de requirements et les advocats internes les plus puissants
6. **La securite est une feature, pas une contrainte** — demontrer que Palantir rend les donnees *plus* securisees ouvre des portes que la "politique d'acces aux donnees" garderait autrement fermees

**L'element le plus sous-estime (Claude) :** L'architecture politique du deploiement. Le DS gere les executifs et gatekeepers pendant que les FDE construisent la confiance avec les utilisateurs frontline, creant simultanement un mandat top-down et une demande bottom-up. Quand la revue executive de la semaine 12 arrive, le cas d'expansion s'ecrit de lui-meme : les utilisateurs sont deja dependants des applications, les donnees circulent deja, et la question passe de "devrions-nous continuer ?" a "a quelle vitesse pouvons-nous nous etendre ?"

---

### 11. Limitations de cette analyse

Cette reconstruction est basee entierement sur des sources publiques : blog posts d'anciens employes, documentation officielle, guides d'implementation partenaires, descriptions de postes, depots de brevets, et presentations publiques (les trois sources). Palantir ne publie pas ses playbooks de deploiement internes, guides d'entretien, matrices de scoring, ou checklists de go-live. Le processus reel est probablement plus fluide, dependant du contexte, et improvisationnel qu'aucune decomposition structuree ne peut capturer. Comme Ted Mabrey le note : "there are no maxims that, if you backtested them, wouldn't violate the path one of our most important products took" (Perplexity).

(GPT) note specifiquement les endroits ou la reconstruction est inferee vs directement appuyee par la documentation publique, et etiquette ces elements. Les elements etiquetes "infered" dans GPT incluent : le nombre d'entretiens, la checklist de go-live, le contenu du document d'expansion, et la methodologie de formation specifique au pilote.
