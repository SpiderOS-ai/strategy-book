# SPIDER MODE PALANTIR POUR PME/ETI

> Document interne. Blueprint d'execution.
> Question unique : "Concretement, comment on fait Spider en mode Palantir pour les PME/ETI europeennes ?"
> Croise : SPIDER-FINAL.md (707 lignes) + Palantir Complete Playbook (322KB, 27 fichiers, 4 phases de recherche)
> Genere le 19 fevrier 2026.

---

## TABLE DES MATIERES

1. [Le Modele Palantir en 60 Secondes](#1-le-modele-palantir-en-60-secondes)
2. [La Traduction Spider -- Phase par Phase](#2-la-traduction-spider--phase-par-phase)
3. [L'Ontology -- Le Vrai Parallele](#3-lontology--le-vrai-parallele)
4. [Le Modele FDE -- La Traduction Concrete](#4-le-modele-fde--la-traduction-concrete)
5. [Le Commercial -- Acquire/Expand/Scale Traduit pour les PME](#5-le-commercial--acquireexpandscale-traduit-pour-les-pme)
6. [Le Moat -- Data Captive vs Ontology](#6-le-moat--data-captive-vs-ontology)
7. [Ce Qui Est Different Et Pourquoi C'est OK](#7-ce-qui-est-different-et-pourquoi-cest-ok)
8. [Plan d'Action -- Les 12 Premieres Semaines](#8-plan-daction--les-12-premieres-semaines)
9. [Annexe : Mapping Complet Palantir -> Spider](#annexe--mapping-complet-palantir---spider)

---

## 1. LE MODELE PALANTIR EN 60 SECONDES

Palantir est une machine a 4 temps. Chaque temps alimente le suivant. Le cycle complet prend 3 a 5 ans par client et transforme un investissement a perte en rente quasi-perpetuelle.

**Temps 1 -- BOOTCAMP (Acquire).** Palantir offre 5 jours gratuits d'immersion. Le C-suite du client vient avec ses donnees. 5-8 personnes Palantir (FDEs + Deployment Strategist) construisent un prototype fonctionnel en temps reel sur les vrais problemes du client. Pas de slides. Du code. Du logiciel qui marche. En 10 heures, la valeur est demontree ou le use case est mauvais. Volume : 5 bootcamps par jour en 2024, 1 300+ cumules. Cout pour Palantir : $12-36K par bootcamp. Conversion : ~22% (analystes Morgan Stanley, Wedbush, RBC). Ceux qui ne convertissent pas deviennent des ambassadeurs gratuits.

**Temps 2 -- PILOT (90 jours, $250K ACV median).** L'equipe FDE s'installe chez le client. 2-4 ingenieurs, 2-4 jours par semaine on-site, 50-70h/semaine. Ils observent le terrain (factory floor walk, hospital ward walk), cartographient les vrais processus (pas les SOPs), construisent l'Ontologie (le modele semantique de l'entreprise), deploient les premieres applications operationnelles. En 90 jours : 10-30 pipelines automatises, 5-15 Object Types, 3-10 applications Workshop. La marge est negative. Volontairement.

**Temps 3 -- EXPAND ($1-5M ACV, NDR 139%).** Le FDE present sur site voit les problemes du departement voisin. "Can you do that for my team too?" L'Ontologie s'etend de 5 a 60+ Object Types, de 1 a 3-5 departements. Les entites partagees (Client, Fournisseur, Commande) creent un tissu connectif inter-departements. La marge passe de -43% a +35%. Le NDR atteint 139% au Q4 2025 -- chaque dollar de revenu existant genere $1.39 l'annee suivante.

**Temps 4 -- SCALE ($5-20M+ ACV, +55% marge).** Le client construit 70-85% de ses propres applications. Le Centre d'Excellence interne (5-50+ personnes) gere l'Ontologie. Les FDEs se retirent progressivement. Mais l'infrastructure -- l'Ontologie, les 50-200+ applications, les 50-150+ sources de donnees connectees, les milliers de regles RBAC -- tout ca vit exclusivement dans Palantir. Switching cost estime : $2.5-7.5M par client enterprise. Le client est autonome dans l'usage, captif dans l'infrastructure.

**Les chiffres qui comptent :**

| Metrique | Valeur |
|----------|--------|
| Expansion moyenne | $100K initial -> $5.6M ACV mature (**56x**) |
| NDR Q4 2025 | **139%** (+500 bps QoQ) |
| Revenue FY2025 | **$4.475B** (+56% YoY) |
| Revenue/employe | **$1.01M** |
| Top-20 clients ACV moyen | **$94M/an** |
| Marge brute GAAP | **84%** (adj. ~79% si FDEs en COGS) |
| Employees | **4,414** (en croissance, pas en reduction) |
| Clients totaux | **954** (x3.7 en <3 ans) |
| Cout FDE par $1M ARR | $700K (2016) -> $80-150K (2025) |

`[SCHEMA: "La Machine Palantir en 4 Temps" -- Pipeline horizontal. 4 blocs relies par des fleches. Bloc 1 "BOOTCAMP" (vert): "5 jours gratuits, $12-36K/bootcamp, 22% conversion" avec icone de marteau. Bloc 2 "PILOT" (bleu): "90 jours, $250K, marge negative, 2-4 FDEs on-site" avec icone de construction. Bloc 3 "EXPAND" (orange): "$1-5M, NDR 139%, 3-5 departements, marge -43% a +35%" avec icone d'expansion. Bloc 4 "SCALE" (rouge): "$5-20M+, +55% marge, client autonome, 70-85% self-service" avec icone de forteresse. Sous chaque bloc: nombre de FDEs (5-8 / 2-4 / 1-2 / 0-1). Fleche de retour en bas du bloc 4 vers le bloc 3 : "56x expansion". En bas : timeline "Semaine 1 -> Mois 3 -> Annee 1-3 -> Annee 3+"]`

---

## 2. LA TRADUCTION SPIDER -- PHASE PAR PHASE

### Phase 1 : BOOTCAMP

**Ce que Palantir fait.** 5 jours d'immersion gratuits. 5-8 personnes Palantir dans la salle (2-4 FDEs, 1-2 Deployment Strategists, 1 Account Executive, 1 Product Specialist). Le client amene 5-20 stakeholders et ses donnees. En 2-4 semaines de pre-travail, les FDEs ont deja ingere les donnees, construit un squelette d'Ontologie (5-10 Object Types), et prepare un environnement demo. Le Jour 1, quand le client voit ses propres spreadsheets transformes en systeme structure et navigable, c'est le pivot emotionnel. Les Jours 2-4, co-building : le FDE code pendant que l'expert metier dirige le contenu. Le Jour 5, demo live devant le C-suite avec ROI quantifie. Pas de slides -- du logiciel qui marche.

**Ce que Spider fait.** Le "Diagnostic Eclair" -- 1 journee, gratuite. Nathan ou Thierry + 1 FDE (a recruter). Format :

| Timing | Activite Spider | Equivalent Palantir |
|--------|----------------|---------------------|
| **J-14 a J-1** | Connexion aux outils du client (Odoo, Pennylane, Gmail, Calendar, Sheets) via Nango. Extraction LLM des premieres claims. Construction du squelette d'entites. | Pre-travail FDE : ingestion donnees, squelette Ontologie |
| **Matin (9h-12h)** | Thierry mene l'atelier process mapping : "Montrez-moi comment vous faites une campagne / une commande / une facture de A a Z." Nathan observe les contournements, les tableurs cachets, les "oui mais en vrai on fait ca." | Jour 1 Palantir : Problem Framing Workshop. Le DS demande "walk me through your end-to-end process." |
| **Dejeuner** | Relation. Thierry parle le langage du dirigeant. Nathan ne parle pas tech. | FDE + DS mangent avec le client. Relationship building delibere. |
| **Apres-midi (13h30-16h)** | Nathan montre le diagnostic Spider : "Voila ce que vos donnees disent de votre entreprise." Les LiveViews (Organigramme, SNA, Diagnostic) revelent ce que 3 ans de consulting n'ont pas capture. Demonstration : "39.3% de vos factures sont impayees." "Votre fournisseur Publitex concentre 100% de votre impression -- bus factor = 1." | Jour 1 Palantir : Demo "Art of the Possible." Le client voit ses donnees dans Foundry pour la premiere fois. Pivot emotionnel. |
| **16h-17h** | Proposition : "On prend en charge ce process pour 500 EUR/mois. Vous, vous faites ce que vous aimez : vos clients." | Jour 5 Palantir : Discussion commerciale. "Pilot de 90 jours a $250K." |

**Adaptation cle.** Palantir met 5-8 personnes pendant 5 jours avec $12-36K de cout. Spider met 2 personnes pendant 1 jour avec ~500 EUR de cout (temps homme + credits IA). La compression est possible parce que :
1. Le client PME est 100x plus simple qu'un Fortune 500 (3 personnes chez Jordan vs 50 000 chez Airbus)
2. L'IA fait en 2h ce que 4 FDEs font en 2 semaines de pre-travail
3. Le diagnostic n'est pas un prototype d'application -- c'est une radiographie des donnees existantes

**Pitch du Diagnostic.** "En 1 journee, on vous montre ce que 3 ans de consulting n'ont pas revele. Gratuit. Aucun engagement. Vous repartez avec le diagnostic que vous gardiez ou non."

**Conversion cible.** Palantir : ~22% bootcamp -> pilot. Spider cible : 40-50% diagnostic -> client payant. Pourquoi plus haut ? Parce que le ticket est 500x plus bas ($250K vs 500 EUR/mois) et que le diagnostic Spider est plus cible (1 process precis vs plateforme enterprise). L'obstacle n'est pas le prix -- c'est la confiance. Et pour ca, on a le reseau Drakkar.

---

### Phase 2 : PILOT

**Ce que Palantir fait.** 90 jours, $250K ACV median. 2-4 FDEs embedded 2-4 jours/semaine on-site. Semaines 1-3 : decouverte (stakeholder mapping, process mapping reel, data inventory -- typiquement 15-40 sources identifiees, 3-10 connectees). Semaines 2-6 : construction de l'Ontologie (5-15 Object Types, 10-30 pipelines), premieres applications Workshop. Semaines 4-10 : Actions (writeback vers les systemes source), securite (7 couches RBAC), polissage. Semaines 8-12 : formation (power users 8-16h, operateurs 2-4h), go-live, transition vers client-operated. Marge : negative. L'objectif n'est pas la rentabilite mais la demonstration de valeur irrefutable.

**Ce que Spider fait.** Phase 0-1 du plan Spider. Jordan = premier pilot. Timeline : 4 semaines (pas 12 -- le scope est radicalement plus petit).

| Semaine | Activite Spider | Equivalent Palantir |
|---------|----------------|---------------------|
| **Semaine 1** | Connexion aux sources (Sheets, Notion, Pennylane). Extraction des 726 lignes de campagnes. Construction de l'Ontologie Jordan : `Campagne`, `Client`, `Reseau`, `Facture`, `BonDeCommande`. Mapping des 33 champs Notion. | Semaines 1-3 Palantir : Data discovery, stakeholder mapping, premiere Ontologie squelette |
| **Semaine 2** | Automatisation de la triple saisie. Le plan media dans Sheets alimente automatiquement Notion et Pennylane. Alertes auto J-28 pour les creatifs. Base tarifaire centralisee. | Semaines 3-6 Palantir : Pipelines de transformation, applications Workshop |
| **Semaine 3** | Test en conditions reelles sur 5-10 campagnes actives. Jordan utilise le systeme. Nathan corrige en temps reel. | Semaines 8-10 Palantir : Stress testing, pilote controlé |
| **Semaine 4** | Bilan. "Jordan, tu renouvelles a 500 EUR/mois ?" Gate G1. | Semaine 12 Palantir : Revue executive, business case for expansion |

**Economie du pilot comparee :**

| Dimension | Palantir | Spider |
|-----------|----------|--------|
| ACV pilot | $250K (median) | **6 000 EUR/an** (500 EUR/mois) |
| Equipe deployee | 2-4 FDEs + 1 DS (3-5 personnes) | **1 FDC (Thierry) + 1 FDE (a recruter)** |
| Cout Palantir du pilot | ~$500K-$1M (salaires FDEs charges) | ~**3-5K EUR** (temps homme + infra) |
| Marge pilot | Negative (-43%) | **Negative mais controlable** (le temps FDC/FDE coute plus que 500 EUR/mois) |
| Sources connectees | 3-10 | **3** (Sheets, Notion, Pennylane) |
| Object Types construits | 5-15 | **5-8** (Campagne, Client, Reseau, Facture, BDC, Plan Media, Imprimeur, Contact) |
| Applications | 3-10 Workshop apps | **1 dashboard + 1 agent** (scope minimal viable) |

**Adaptation cle.** La difference fondamentale : Palantir peut se permettre de perdre $500K par pilot parce qu'un contrat initial de $100K grandit a $5.6M (56x). Spider perd 3-5K EUR de temps homme par pilot et doit les recuperer sur l'upsell. Le multiple d'expansion Spider doit etre au minimum 5-10x pour que le modele fonctionne : un client a 500 EUR doit atteindre 2 500-5 000 EUR/mois sur 6-12 mois. C'est le pari H4 (l'ontology se transfere) et H6 (le ratio FDE:clients s'ameliore).

**Metriques de succes -- ce que Spider traque vs ce que Palantir traque :**

| Metrique Palantir | Valeur cible Palantir | Metrique Spider equivalente | Valeur cible Spider |
|-------------------|----------------------|----------------------------|---------------------|
| Time-to-decision | Reduit de 80%+ | Temps par campagne (humain vs IA) | Reduit de 50%+ |
| Adoption (DAU/WAU) | X utilisateurs actifs | Jordan utilise-t-il Spider quotidiennement ? | Oui/Non binaire |
| Unification donnees | 5+ sources connectees | Sources connectees | 3 minimum |
| Process displacement | Workflows Excel remplaces | Triple saisie eliminee | Oui/Non |
| ROI quantifie | $/temps economises | Heures economisees par semaine | 5-10h/semaine |

---

### Phase 3 : EXPAND

**Ce que Palantir fait.** Apres le succes du pilot dans 1 departement, l'Ontologie s'etend au departement voisin. L'FDE sur site voit les problemes du bureau d'a cote. Les entites partagees (Client, Fournisseur) creent des ponts naturels. Palantir organise des "Build with AIP" bootcamps pour clients existants (20-50 participants, 5-10+ use cases identifies). L'exercice des "100 cas d'usage" genere un pipeline d'expansion. NDR 139% : chaque dollar existant en genere $1.39 l'annee suivante. Le DS maintient un "problem backlog" priorise -- revue mensuelle, SteerCo trimestriel.

**Ce que Spider fait.** L'upsell vertical. Spider ne s'etend pas horizontalement entre departements (le dirigeant PME EST tous les departements). Spider s'etend verticalement : plus de processus pour le meme patron.

| Mecanisme Palantir | Mecanisme Spider | Concretement chez Jordan |
|--------------------|-----------------|--------------------------|
| Le FDE voit le probleme du departement voisin | Spider detecte les anomalies dans les donnees operationnelles | Spider voit que 39.3% des factures sont impayees (285/726) |
| Le DS propose un bootcamp "Expand" interne | Nathan propose un Agent Relance | "Jordan, on a detecte 285 factures impayees. Notre Agent Relance peut chasser ca automatiquement." |
| L'Ontologie croit de 5 a 60+ Object Types | L'Ontologie Spider s'enrichit : `Facture`, `Echeance`, `Relance`, `Paiement` | Nouveaux Object Types lies aux existants via les claims |
| Entites partagees creent des ponts | Les entites Client et Facture lient campagnes et relances | Le meme `Client` est dans les campagnes ET dans les relances |
| Setup fee + nouveau module | Setup fee 2-5K EUR + Agent Relance 190-500 EUR/mois | MRR Jordan passe de 500 a 700-1 000 EUR/mois |

**Le flywheel de l'upsell Spider :**

`[SCHEMA: "Flywheel Spider vs Palantir" -- Deux cercles cote a cote. Cercle gauche "PALANTIR EXPAND" : Dept A (pilot) -> entites partagees -> Dept B (expand) -> plus de donnees -> Dept C -> NDR 139%. Cercle droit "SPIDER EXPAND" : Process 1 (campagnes, 500 EUR) -> data capturee -> anomalie detectee (39.3% impayes) -> Agent Relance propose -> Process 2 (relances, +190 EUR) -> plus de data -> meilleur diagnostic -> Process 3 (achats, +300 EUR). Centre : "Meme logique, axe different." Palantir = expansion horizontale inter-departements. Spider = expansion verticale intra-entreprise.]`

**Processus concrets identifies pour l'expansion chez Jordan :**

| Process | Douleur detectee | Agent Spider | MRR additionnel |
|---------|-----------------|-------------|-----------------|
| Relance impayes | 39.3% de factures impayees | Agent Relance | 190-500 EUR/mois |
| Suivi BDC | BDC manquants, pas de tracking | Agent Achats | 190-300 EUR/mois |
| Contenu digital | 100% marge sur services manages | Agent Contenu | 300-500 EUR/mois |
| Reporting client | Pas de reporting automatise | Agent Reporting | 190-300 EUR/mois |

**Objectif de MRR par client mature :** 500 EUR d'entree -> 2 000-5 000 EUR/mois sur 6-12 mois. Facteur d'expansion cible : **4-10x**. Palantir fait 56x. Spider fait 4-10x. La difference est que Spider le fait sur des milliers de clients a faible ticket, pas sur des centaines a fort ticket.

---

### Phase 4 : SCALE

**Ce que Palantir fait.** Le client construit 70-85% de ses propres applications. Le Centre d'Excellence (5-50+ personnes) est autonome. Les FDEs se retirent progressivement sur 3-5 ans. Apollo automatise les mises a jour (360 000 deploiements/mois, <20 ingenieurs). Le client est captif structurellement (7 couches de switching costs) mais libre contractuellement (resiliation avec 3-6 mois de preavis). 25-35% du revenu Palantir vient de clients fully self-service. Le revenu le plus rentable (+55% marge).

**Ce que Spider fait.** Phase 3-4 du plan Spider. L'assistant devient le canal de vente.

| Phase Scale Palantir | Phase Scale Spider |
|---------------------|--------------------|
| Client construit ses propres apps | Le dirigeant PME utilise l'assistant Spider de maniere autonome |
| Centre d'Excellence gere l'Ontologie | Pas d'equivalent -- le dirigeant PME n'a pas 5-50 personnes tech. C'est Spider qui gere. |
| FDEs se retirent | Le ratio FDC/FDE s'ameliore : 1 pour 15-20 clients au lieu de 1 pour 5-10 |
| Apollo automatise les deploiements | L'IA automatise le monitoring et la maintenance |
| Partenaires (Accenture, 2 000+ pros) | Partenaires (Drakkar d'abord, puis integrateurs Odoo) |
| Self-service sur la plateforme Palantir | Self-service via l'assistant Spider qui diagnostique et recommande des agents |

**L'assistant comme canal de vente (la vision Phase 3 Spider) :**

1. L'assistant gratuit se connecte a l'Odoo/Pennylane du prospect
2. L'assistant diagnostique automatiquement : "43% de vos factures sont en retard", "Votre marge sur le client X est de 8% alors que votre moyenne est de 27%"
3. L'assistant recommande : "Notre Agent Relance peut regler les impayes. Essai gratuit 14 jours."
4. Le prospect active l'agent. Setup fee + MRR.

C'est l'equivalent du bootcamp Palantir, mais automatise et scalable. Le cout par "bootcamp" Spider passe de 500 EUR (diagnostic humain) a quasi-zero (diagnostic IA).

**Le Mycelium -- ce que Palantir n'a pas.** Palantir sert 954 clients. Chaque client est un silo. Airbus ne beneficie pas des donnees de bp. Spider, a 1 000+ clients PME, voit les patterns cross-entreprises :
- "Ton fournisseur a un probleme. 3 autres PME l'ont signale cette semaine."
- "Les entreprises de ta taille dans ton secteur paient leurs fournisseurs en 42 jours. Toi, 67."
- "Le reseau publicitaire X a augmente ses prix de 15% ce trimestre -- 12 de tes concurrents l'ont subi."

C'est le pouvoir de Phase 3 Spider : l'intelligence collective inter-entreprises. Palantir ne peut pas le faire parce que ses clients sont des concurrents ($94M ACV moyen = le meme secteur ne tolere pas le partage). Les PME Spider sont assez petites pour ne pas etre en concurrence directe.

---

## 3. L'ONTOLOGY -- LE VRAI PARALLELE

L'Ontologie est le moat de Palantir. Pas le code. Pas l'IA. L'Ontologie. C'est le modele semantique vivant de l'entreprise -- la formalisation de "comment cette boite fonctionne reellement." Le code est copiable en 6 mois. L'Ontologie accumulee sur 3 ans ne l'est pas.

Spider a sa propre ontologie. La comparaison structurelle :

`[SCHEMA: "Les Deux Ontologies" -- Deux colonnes. Colonne gauche "PALANTIR ONTOLOGY" (fond violet) : 6 primitives empilees -- Objects Types, Properties, Link Types, Action Types, Interfaces, Functions. Chaque primitive a un exemple. En dessous : "3 couches : Semantic (WHAT) / Kinetic (HOW) / Dynamic (GUARDRAILS)". Colonne droite "SPIDER ONTOLOGY" (fond vert) : 5 primitives empilees -- Entities, Claims, Predicates, Beliefs, LiveViews. Chaque primitive a un exemple. En dessous : "3 couches : Extraction (LLM) / Resolution (Dempster-Shafer) / Materialisation (LiveViews)". Au centre : fleches bidirectionnelles reliant les concepts equivalents : Object Type <-> Entity, Property <-> Claim attribute, Link Type <-> Predicate, Action Type <-> pas d'equivalent direct (a construire), Interface <-> pas d'equivalent, Function <-> LiveView. Encadre rouge en bas : "Difference fondamentale : Palantir construit une ontologie custom par client ($millions, FDEs). Spider construit des ontologies templates par vertical (transferables entre clients)."]`

### Mapping des primitives

| # | Primitive Palantir | Description Palantir | Equivalent Spider | Description Spider |
|---|-------------------|---------------------|-------------------|-------------------|
| 1 | **Object Types** | Entites du domaine (Client, Commande, Produit) | **Entities** | Entites resolvees (type, canonical_name, aliases) |
| 2 | **Properties** | Attributs types (name: String, amount: Double) | **Claim attributes** | Proprietes extraites par LLM, chacune avec un degre de croyance [0,1] |
| 3 | **Link Types** | Relations dirigees (Client "commande" Produit, 1:N) | **Predicates** | 14 predicats (HOLDS_ROLE, REPORTS_TO, HAS_COMPETENCE, WORKS_WITH...) |
| 4 | **Action Types** | Operations write-back (ApprouverCommande, AssignerTechnicien) | **Pas d'equivalent direct** | A construire : les agents Spider qui executent (Agent Relance, Agent Campagnes) |
| 5 | **Interfaces** | Contrats abstraits polymorphiques (Trackable, Assignable) | **Pas d'equivalent** | Pas necessaire en V1 -- la complexite PME ne le justifie pas |
| 6 | **Functions** | TypeScript computations (calculateRiskScore, findNearestWarehouse) | **LiveViews** | 10 vues materialisees (Organigramme, SNA, Porter, VSM, Diagnostic...) |

### La difference fondamentale : custom vs template

**Palantir** construit une ontologie unique pour chaque client. L'Ontologie d'Airbus (140+ airlines, 50 000 utilisateurs, 500+ Object Types) n'a rien a voir avec celle de bp (2M+ capteurs, jumeau numerique petrole). Cout de construction : $millions. Temps : 2-3 ans pour la maturite. C'est ce qui rend le modele viable uniquement pour des ACVs a 7+ chiffres.

**Spider** construit des ontologies templates par vertical. L'Ontologie "agence de publicite" creee pour Jordan (Campagne, Client, Reseau, Facture, BDC, Plan Media) sera reutilisee pour la prochaine agence. Le setup du client 5 devrait couter 60% moins cher que le client 1 -- c'est l'hypothese H4, la plus critique du modele.

| Dimension | Ontologie Palantir | Ontologie Spider |
|-----------|-------------------|-----------------|
| Construction | Custom par client, $millions | **Templates par vertical, EUR 2-5K de setup** |
| Object Types typiques | 100-500+ (enterprise mature) | **5-15** (PME) |
| Sources connectees | 50-150+ | **3-7** |
| Temps de construction | 6-18 mois pour la v1 | **2-4 semaines** |
| Qui la construit | 2-4 FDEs ($200K+ chacun/an) | **1 FDE + LLM** |
| Transferabilite | Zero -- chaque ontologie est unique | **Elevee (hypothese H4)** -- templates verticaux |
| Evolution | Revues de gouvernance bimensuelles, Ontology Manager dedie | **Automatique** -- les claims LLM enrichissent en continu |

### Le systeme de claims -- l'innovation propre a Spider

Palantir a une ontologie deterministe : "Pierre est CEO" est un fait dans l'Object Type Employee, propriete `role = "CEO"`. Pas de nuance.

Spider a une ontologie probabiliste : "Pierre est CEO" est un **claim** avec un degre de croyance (belief: 0.95). "Pierre est aussi directeur de production" est un autre claim (belief: 0.72). Quand deux claims se contredisent (K > 0.9 sur l'echelle Dempster-Shafer), Spider leve une alerte. Chaque conflit detecte = opportunite de consulting. "Vos donnees disent que Pierre est CEO et directeur de production. Lequel est vrai ?"

C'est un avantage unique : Palantir prend les donnees pour acquises (les FDEs les nettoient manuellement). Spider traite les donnees comme des croyances concurrentes et fait remonter les conflits. Pour une PME ou le tacite n'est pas ecrit, c'est exactement le bon modele.

---

## 4. LE MODELE FDE -- LA TRADUCTION CONCRETE

Le Forward Deployed Engineer est l'unite atomique de Palantir. Nom de code interne : "Delta". Le programme FDE a engendre 170+ startups, $24B+ de capital leve, et une croissance de 800-1 000% des postes FDE dans l'industrie en 2025.

### Anatomie du FDE Palantir

| Dimension | Detail |
|-----------|--------|
| Profil | "Startup CTO" embarque chez le client. 1+ an post-diplome, age median ~25 |
| Formation | Top CS (Stanford, MIT, CMU), mais aussi philo, maths, physique |
| Competence distinctive | "Unusual sensitivity to social context" -- lit les dynamiques de pouvoir |
| Compensation | Entry: $135-200K base, $171-415K total. Senior: $200-300K base, $500-800K total |
| Tarification | GBP 150 000/personne/trimestre (~$760K/an) |
| Ratio | 2-4 FDEs par client pilot |
| Presence | 50-80% on-site, 2-4 jours/semaine |
| Workweek | 50-70 heures. Glassdoor work-life balance : 2.7/5 |
| Lecture obligatoire | *Impro* (Keith Johnstone), *The Looming Tower*, *Interviewing Users*, *Getting Things Done* |
| Classification comptable | R&D (pas COGS) -- ce qui gonfle la marge brute de ~5pp |

### Le binome Deployment Strategist ("Echo") + FDE ("Delta")

Palantir utilise un modele en pod, radicalement plat :

| Role | Equivalent MBB | Ce qu'il fait |
|------|---------------|---------------|
| **Deployment Strategist** (Echo) | Partner + EM | Ex-McKinsey/BCG/Bain. Possede la relation business, gere la politique organisationnelle, determine QUEL use case construire. Trouve le "Goldilocks zone." |
| **FDE** (Delta) | Associate + BA + le dev | Construit le logiciel. Ecrit du PySpark le matin, presente une app Workshop a un VP l'apres-midi. |

La sortie n'est pas un PowerPoint. C'est du logiciel fonctionnel en production. La meme personne qui diagnostique construit et deploie.

### La traduction Spider : FDC + FDE

| Role Spider | Equivalent Palantir | Profil | Qui aujourd'hui |
|-------------|---------------------|--------|-----------------|
| **FDC** (Forward Deployed Consultant) | Deployment Strategist ("Echo") | Ex-dirigeant industrie, skills consulting. Comprend le metier, cartographie les processus, formalise les regles, construit la confiance avec le CEO. Pas de code. | **Thierry Menard** (lead, ex-Airbus), Jean Le Tulzo (structuration offre) |
| **FDE** (Forward Deployed Engineer) | FDE ("Delta") | Dev mid-senior, experience ops. Connecte les sources, valide les claims, configure les agents, supervise techniquement. | **A recruter** (1-2 profils Phase 1) |

**La difference critique : l'IA remplace les FDEs supplementaires.**

| Dimension | Palantir | Spider |
|-----------|----------|--------|
| Equipe par client pilot | 2-4 FDEs + 1 DS = 3-5 personnes | **1 FDC + 1 FDE + IA** = 2 personnes |
| Ce que font les FDEs supplementaires chez Palantir | Ingestion de donnees, pipelines de nettoyage, construction d'Ontologie, applications Workshop | **L'IA fait ca** : extraction LLM (Haiku 4.5/Sonnet 4.5), entity resolution (Fellegi-Sunter), claims engine (Dempster-Shafer) |
| Ratio cible | 1 equipe pour 1-2 clients | **1 equipe pour 5-10 clients** (Phase 1), **1 pour 15-20** (Phase 3) |
| Salaire | $135-300K/personne | **60-90K EUR/personne** (marche francais) |

**L'amelioration du ratio FDC/FDE:clients est LA question existentielle.** Si le ratio stagne a 1:5, Spider est une ESN avec de l'IA (valorisation 1-3x revenue). Si le ratio atteint 1:20 grace au transfert d'ontologies templates, Spider est un SaaS deguise (valorisation 10-20x revenue). La difference : facteur 5-10 sur la valorisation. Toute la these repose dessus.

Le precedent Palantir : en 2016, chaque $1M d'ARR coutait $700K en FDEs. En 2025, c'est $80-150K. Reduction de 5-9x en 9 ans. Spider doit faire la meme compression en 2-3 ans, grace a l'IA qui n'existait pas en 2016.

---

## 5. LE COMMERCIAL -- ACQUIRE/EXPAND/SCALE TRADUIT POUR LES PME

`[SCHEMA: "Modele Commercial Palantir vs Spider" -- Deux graphiques en miroir. Graphique gauche "PALANTIR" : axe X = temps (0-5 ans), axe Y = marge (de -50% a +60%). Courbe qui commence a -43% (Acquire), remonte vers 0 (mois 6-12), atteint +35% (Expand, annee 2), puis +55% (Scale, annee 3+). En dessous de la courbe Acquire : "Investissement delibere : $65.4M de pertes sur cohorte 2019 new customers." Au-dessus de la courbe Scale : "$5.6M ACV mature (56x expansion)." Graphique droit "SPIDER" : meme axes. Courbe qui commence a -100% (Acquire, cout FDC/FDE > 500 EUR/mois), remonte vers 0 (mois 2-3), atteint +30% (Expand, mois 4-8 avec upsells), puis +50%+ (Scale, annee 2 avec assistant self-service). En dessous : "Investissement controle : 3-5K EUR/client." Au-dessus : "2 000-5 000 EUR/mois (4-10x expansion)."]`

### Phase Acquire : l'entree a perte

| Dimension | Palantir | Spider |
|-----------|----------|--------|
| Prix d'entree | $100-500K ACV | **500 EUR/mois** (6K EUR/an) |
| Cout reel pour l'entreprise | ~$500K-1M (FDEs charges) | **3-5K EUR** (temps FDC/FDE + infra) |
| Marge | **Negative** (-43% sur la cohorte) | **Negative** (500 EUR/mois ne couvre pas le temps humain) |
| Logique | "Land grab" : chaque dollar perdu genere un 56x d'expansion | Chaque client acquis est un test de H4 (transfert d'ontologie) et un noeud du Mycelium |
| Karp : "No pricing strategy for AIP" | Nathan : "Le prix est une hypothese. Pas un modele valide." |

### Phase Expand : l'upsell comme moteur

| Dimension | Palantir | Spider |
|-----------|----------|--------|
| Mecanisme | Expand inter-departements (Supply Chain -> Finance -> RH) | **Expand intra-process** (Campagnes -> Relances -> Achats -> Reporting) |
| NDR | 139% (Q4 2025) | **Cible : 130-150%** (chaque client ajoute 1-2 agents par semestre) |
| Prix par extension | Niveau de licence additionnel (GBP 250K-5M) | **Setup fee 2-5K EUR + Agent 190-990 EUR/mois** |
| Marge | -43% -> +35% | **Ameliore vite** : les setup fees sont du consulting, les agents sont du software |
| Qui detecte les opportunites | FDE on-site (proximite physique) | **L'IA** (diagnostic automatique des anomalies dans les donnees captees) |

### Phase Scale : le self-service

| Dimension | Palantir | Spider |
|-----------|----------|--------|
| Client-side | CoE de 5-50+ personnes construit ses propres apps | **Pas d'equivalent** : le dirigeant PME n'a pas d'equipe tech. Spider reste le Shogun. |
| Canal | Workshop self-service + certification Palantir | **Assistant Spider** : chatbot IA connecte aux donnees, diagnostique et recommande des agents |
| Marge | +55% (revenu le plus rentable) | **+60-70%** (pur software, pas de temps humain) |
| Volume necessaire | 954 clients a $4.7M ACV moyen = $4.475B | **5 000-10 000 clients a 2 000 EUR/mois moyen = $120-240M EUR/an** |

### Le "no pricing strategy" traduit

Karp : "We have no pricing strategy for AIP." Le but est le land grab -- capturer le maximum de clients avant que les concurrents ne bougent. L'AIP est le "razor" gratuit ; Foundry est la "blade" payante.

Nathan : "500 EUR est un test. Le prix sera connu apres 5-10 ventes reelles a des non-amis."

La logique est identique : sous-facturer l'entree pour maximiser la capture. La difference : Palantir peut se permettre des annees de pertes ($5.2B de cash). Spider doit etre rentable en 12-18 mois (finance par Drakkar, pas par Thiel). Le "no pricing strategy" Spider est donc contraint : chaque pilot doit etre au minimum breakeven en comptant les upsells futurs.

---

## 6. LE MOAT -- DATA CAPTIVE VS ONTOLOGY

Palantir et Spider construisent leur moat de la meme maniere : couche par couche, jour apres jour, de facon quasi-invisible. Le client ne realise pas qu'il est captif avant qu'il ne soit trop tard pour partir.

### Les 7 couches de switching costs Palantir -> les 5 couches Spider

| # | Couche Palantir | Cout estime | Couche Spider equivalente | Mecanisme |
|---|----------------|-------------|--------------------------|-----------|
| 1 | Dependances d'integration (50-150+ sources) | 6-18 mois de recreation | **Connexions sources** (3-7 sources) | Chaque jour de fonctionnement = plus de data historique dans Spider |
| 2 | Complexite de l'Ontologie (100-500+ Object Types) | Non reproductible | **Ontologie verticale** (5-15 entities + claims) | Le tacite capture dans les claims n'est pas exportable |
| 3 | Dependances applicatives (50-200+ apps Workshop) | Pas d'export possible | **Agents configures** (1-5 agents par client) | Les regles metier formalisees dans les agents sont proprietaires |
| 4 | Connaissances institutionnelles (audit trails, historique) | Non quantifiable | **Historique des claims** (3+ mois de patterns) | Les patterns de decision accumules ne sont pas reproductibles |
| 5 | Configuration securite (milliers de regles RBAC) | Recreation totale | Pas d'equivalent PME (trop petit pour des RBAC complexes) | -- |
| 6 | Investissement en formation (CoE 5-50+ personnes) | Cout irrecuperable | **Habitude du dirigeant** | Le CEO qui dit "oui" a Spider chaque jour depuis 6 mois ne changera pas |
| 7 | Integration dans les workflows quotidiens | Perturbation operationnelle | **Les agents sont dans le flux** | Quand l'Agent Relance chasse les impayes tous les jours, l'arreter = arreter d'etre paye |

### Ce que Spider a que Palantir n'a pas

**Le Mycelium (effet reseau inter-entreprises).** Chaque client Palantir est isole. Airbus ne voit pas les donnees de bp. A $94M ACV moyen, les clients sont souvent des concurrents directs.

Spider, a 1 000+ clients PME dans le meme tissu economique, cree un reseau d'intelligence collective :
- Phase 1 (La Toile) : data captive par client, impossible a repliquer
- Phase 2 (Le Mycelium) : patterns cross-clients, valeur du reseau
- Phase 3 (Le Pouvoir) : Spider definit les metriques (Spider Score, Indice de Tacite)

C'est un moat que Palantir ne peut structurellement pas construire. Et les Americains ne le verront pas venir -- le marche PME europeen est hors de leur cadre mental.

### Ce que Palantir a que Spider n'a pas

| Avantage Palantir | Impact | Spider peut-il le construire ? |
|------------------|--------|-------------------------------|
| 20 ans de credibilite | Deals de $10B+ (US Army) | Non. Il faut commencer quelque part. |
| $5.2B de tresorerie | Peut perdre de l'argent pendant des annees | Non. Spider a 12-18 mois pour prouver le modele. |
| 4 414 employes dont ~1 000-1 500 FDEs | Deploiement massif parallele | Non en Phase 1. 2-4 FDC + 2-4 FDE pour 20 clients. |
| 954 clients a $4.7M ACV moyen | Effets d'echelle | Non encore. Mais le volume PME compense le ticket. |
| Apollo (360 000 deploiements/mois, <20 ingenieurs) | Avantage operationnel sous-apprecie | Oui. L'infra cloud-native Spider (K8s, ArgoCD) couvre le meme besoin a plus petite echelle. |
| FedRAMP High, DoD IL5/IL6 | Marche gouvernemental US | Non pertinent. Spider vise les PME europeennes, pas le Pentagone. |

---

## 7. CE QUI EST DIFFERENT ET POURQUOI C'EST OK

Il faut etre honnete. L'analogie Palantir-Spider est structurelle, pas exacte. Voici ou elle casse -- et pourquoi ca ne tue pas la these.

### 1. L'echelle du ticket

Palantir : $5M+ ACV moyen. Spider : 500 EUR/mois = 6K EUR/an. Ecart : **~1 000x**.

Pour le meme revenu de $4.5B, Spider aurait besoin de **750 000 clients**. C'est evidemment absurde comme objectif immediat. Mais :
- Spider ne vise pas $4.5B. Il vise $1.7-3.2M EUR annualise en 24 mois (80-150 clients).
- Le marche adressable est 50 000-100 000 PME/ETI europeennes (correction #3 du playbook), pas 25M de micro-entreprises.
- A 2 000 EUR/mois moyen (avec upsells), 5 000 clients = $120M EUR/an. C'est un objectif viable a 5-7 ans.

### 2. Le cycle de vente

Palantir pre-bootcamp : 9+ mois. Post-bootcamp : ~6 semaines. Spider : **1 jour (diagnostic) -> decision en 1 semaine**.

Le cycle Spider est 6x plus court que le cycle Palantir post-bootcamp. Pourquoi ? Parce que le CEO de PME decide seul (pas de procurement committee, pas de budget cycle, pas d'IT gatekeeper). La confiance se construit autrement : pas par 5 jours d'immersion avec 20 stakeholders, mais par 1 journee avec 1 personne -- le patron.

### 3. La profitabilite

Palantir : 17 ans pour devenir profitable (IPO en 2020, premier free cash flow positif en 2022). Spider : **doit etre profitable en 12-18 mois** (finance par Drakkar a ~$1.5M EUR/an, pas par Thiel ou la CIA).

C'est la contrainte la plus dure. Palantir pouvait se permettre de perdre $65.4M sur une cohorte de nouveaux clients parce que Thiel avait mis $30M au depart et qu'ils avaient leve ~$3B avant l'IPO. Spider a 100K EUR de Drakkar et le revenu Drakkar ($1.5M/an) comme filet de securite. Chaque mois compte.

Implication : Spider ne peut pas offrir des pilots gratuits a 22% de conversion. Le diagnostic est gratuit, mais la conversion doit etre >40% pour que le modele tienne. Et les premiers clients doivent etre sources du reseau Drakkar (warm leads), pas du cold outreach.

### 4. La maturite data des clients

Palantir sert des organisations avec 15-40 sources de donnees, des equipes data, des ERP complexes. Spider sert des PME ou (Eurostat 2024) :
- 83.3% utilisent Excel comme outil analytique principal
- Seulement 14.5% utilisent un logiciel d'analytics
- Seulement 8.9% utilisent une forme d'IA
- 44.8% n'ont aucune customisation ERP

Implication : Spider doit commencer par structurer les donnees avant de les analyser. Le diagnostic est aussi un travail d'ingestion et de nettoyage. C'est un investissement supplementaire que Palantir n'a pas (ses clients ont deja les donnees structurees).

### 5. Le capital humain

Palantir recrute a Stanford, MIT, CMU. $215K de compensation mediane pour un FDE junior. Spider recrute... ou ? En Normandie ? A Paris ? Le marche des "ingenieur mid-senior capable de parler a des non-techniques" est reel mais petit en France.

Implication : Spider doit compenser le manque de talent par l'IA. Si Palantir met 4-5 FDEs par client, Spider met 1 FDE + IA. L'IA doit faire le travail de 3-4 FDEs supplementaires. C'est le pari de la compression IA.

### Pourquoi c'est quand meme OK

Le playbook est le meme. La logique est la meme :

1. **Investir a perte pour prouver la valeur** (bootcamp/diagnostic gratuit)
2. **Capturer les donnees pendant qu'on fait le travail** (Ontologie/Claims)
3. **Upsell a partir des anomalies detectees** (NDR 139%/flywheel Spider)
4. **Rendre le depart impossible** (7 couches de switching costs/5 couches Spider)
5. **Automatiser pour que la marge augmente** (FDEs -> self-service / FDC+FDE -> IA)

La seule question est : **Spider peut-il executer ce playbook 1 000x plus vite et 1 000x moins cher ?** L'IA dit oui. Le marche dira.

---

## 8. PLAN D'ACTION -- LES 12 PREMIERES SEMAINES

Ce plan croise la methodologie Palantir (bootcamp -> pilot -> expand) avec les realites Spider (Jordan comme premier client, reseau Drakkar, equipe reduite).

### Semaines 1-2 : Le Bootcamp Jordan

| Jour | Activite | Responsable | Equivalent Palantir | Livrable |
|------|----------|-------------|---------------------|----------|
| J-14 | Connexion aux sources : Google Sheets (plans media), Notion (33+ champs ops), Pennylane (facturation) | Nathan (FDE) | Pre-travail FDE : ingestion donnees, agent proxy setup | Sources connectees, premieres claims extraites |
| J-7 | Extraction LLM : Haiku 4.5 sur les 726 lignes de campagnes. Entity resolution : Campagne, Client, Reseau, Facture. Claims engine : conflits detectes. | Nathan | Pre-travail FDE : Ontologie squelette, 5-10 Object Types | Ontologie Jordan V1 (5-8 Entity types, ~2 000 claims) |
| **J0 (demi-journee)** | Diagnostic Eclair chez Jordan. Thierry mene le process mapping. Nathan montre le diagnostic live : les 10 LiveViews sur les donnees de ComPrivee. Revelation des 39.3% d'impayes, du bus factor Publitex, de la saisonnalite (pic sept 125 / creux dec 11). | Thierry (FDC) + Nathan | Jour 1 Palantir : Problem Framing Workshop + Art of the Possible demo | Process flow mapping, pain points quantifies, buy-in emotionnel |
| J0 (fin) | Proposition : "On gere tes campagnes pour 500 EUR/mois. Tu fais ce que tu aimes : tes clients." | Nathan | Jour 5 Palantir : Discussion commerciale | Accord verbal Jordan |

### Semaines 3-4 : Le Pilot Rapide

| Semaine | Activite | Responsable | Livrable |
|---------|----------|-------------|----------|
| S3 | Construction du pipeline automatise : plan media Sheets -> Notion -> Pennylane. Elimination de la triple saisie. Alertes auto J-28 pour les creatifs. Base tarifaire centralisee. | Nathan + FDE recrute | Pipeline fonctionnel, 1ere campagne traitee automatiquement |
| S3-S4 | Test sur 5-10 campagnes actives. Jordan utilise le systeme au quotidien. Nathan corrige en temps reel (cycles de 30-90 min comme le co-building Palantir). | Nathan + Jordan | Campagnes gerees sans triple saisie |
| **S4 -- Gate G1** | "Jordan, tu renouvelles a 500 EUR/mois ?" Criteres : oui + valeur mesurable + au moins 1 demande d'expansion non sollicitee. Kill criteria : refuse ou negocie sous 300 EUR. | Nathan | **Decision GO/KILL** |

### Semaines 5-8 : Replication (2-3 clients Drakkar)

| Semaine | Activite | Responsable | Equivalent Palantir |
|---------|----------|-------------|---------------------|
| S5-S6 | Identifier 2-3 clients du reseau Drakkar. Profils : PME, 5-50 salaries, processus manuels visibles, dirigeant qui fait confiance a Drakkar. | Thierry + Jean (sourcing) | AE outbound cible + leveraging du reseau de partenaires |
| S6 | Diagnostic Eclair chez chaque prospect. Meme format que Jordan : 1 demi-journee, gratuit, montrer la valeur des donnees. | Thierry (FDC) + Nathan ou FDE recrute | Bootcamp Palantir (compresse de 5 jours a 1 demi-journee) |
| S7-S8 | Setup des clients qui convertissent. **Test de H4** : le temps d'onboarding du client 2-3 est-il inferieur a celui de Jordan ? L'ontologie template "agence pub" se transfere-t-elle ? | Nathan + FDE | Phase pilot 90 jours Palantir (compresse a 2-3 semaines) |
| S8 | **Gate G2 (anticipe)** : au moins 2 clients payants ? L'ontologie se transfere-t-elle ? | Nathan | Validation ou invalidation de H4 |

### Semaines 9-12 : Premier Upsell

| Semaine | Activite | Responsable | Equivalent Palantir |
|---------|----------|-------------|---------------------|
| S9-S10 | Chez Jordan : les donnees captees pendant 2 mois revelent les patterns. Spider detecte les 285 factures impayees. Nathan prepare l'Agent Relance. | Nathan | Phase Expand Palantir : FDE detecte les problemes du departement voisin |
| S10 | Proposition upsell a Jordan : "39.3% de tes factures sont impayees. Notre Agent Relance chasse les retards automatiquement. Setup 2K EUR + 190 EUR/mois." | Thierry (relation) + Nathan (demo) | DS propose le bootcamp "Expand" avec exercice des "100 use cases" |
| S11-S12 | Implementation Agent Relance (si Jordan accepte). Enrichissement de l'Ontologie : `Facture`, `Echeance`, `Relance`, `Paiement`. | Nathan + FDE | Ontologie Palantir s'etend de 5 a 20-60 Object Types (ici : de 5 a 10) |
| **S12 -- Bilan** | Ou en est-on ? | Toute l'equipe | Revue executive Palantir |

**Metriques de succes semaine 12 :**

| Metrique | Cible minimum | Ideal |
|----------|--------------|-------|
| Clients payants | 3 | 5 |
| MRR total | 1 500 EUR | 3 000+ EUR |
| Jordan renouvelle | Oui | Oui + 1 upsell |
| Temps onboarding client 5 vs client 1 | <80% du temps client 1 | <60% (H4 validee) |
| Ratio IA/humain par campagne | 40% IA | 50%+ IA |
| Demandes d'expansion non sollicitees | 1 | 3+ |

---

## ANNEXE : MAPPING COMPLET PALANTIR -> SPIDER

| Concept Palantir | Implementation Palantir | Equivalent Spider | Implementation Spider | Statut |
|-----------------|------------------------|-------------------|----------------------|--------|
| **Gotham** | Plateforme renseignement/defense (2008) | -- | Pas d'equivalent (marche different) | N/A |
| **Foundry** | OS enterprise commercial (2016) | **SpiderOS** | Plateforme cloud-native EU (OVH+Scaleway, K8s, ArgoCD) | En construction |
| **AIP** | Couche IA (2023), LLMs sur objets types | **Spider Intelligence Engine** | Haiku 4.5 + Sonnet 4.5, Dempster-Shafer, LiveViews | Architecture definie |
| **Apollo** | Deploiement continu (360K/mois, <20 ing.) | **ArgoCD + GitOps** | 3 clusters K8s, CI/CD standard | Operationnel |
| **Ontology** (6 primitives) | Object Types, Properties, Links, Actions, Interfaces, Functions | **Claims Engine** (5 primitives) | Entities, Claims, Predicates, Beliefs, LiveViews | A construire |
| **Object Types** | Tables d'entites typees (Client, Commande) | **Entities** | entity(type, canonical_name, aliases) | A construire |
| **Properties** | Attributs types (String, Double, Date) | **Claim attributes** | Attributs extraits par LLM avec belief [0,1] | A construire |
| **Link Types** | Relations dirigees (1:1, 1:N, M:N) | **14 Predicats** | HOLDS_ROLE, REPORTS_TO, HAS_COMPETENCE, etc. | Definis |
| **Action Types** | Operations write-back (ApprouverCommande) | **Agents** | Agent Relance, Agent Campagnes, Agent Achats | Conceptualises |
| **Interfaces** | Types abstraits polymorphiques | -- | Pas necessaire en V1 | N/A |
| **Functions** | TypeScript computations sur l'ontologie | **LiveViews** | 10 vues materialisees (SurrealQL -> transform -> cache) | A construire |
| **OMS** (Ontology Metadata Service) | Stockage de schema, source de verite | **SurrealDB** | Knowledge graph, claims, vecteurs | Choix fait |
| **Object Storage V2** | Persistance + indexation (Funnel pipeline) | **PostgreSQL 16 HA** | Source de verite relationnelle | Choix fait |
| **OSS** (Object Set Service) | Moteur de requete (Object Sets) | **SurrealQL** | Requetes sur le knowledge graph | A construire |
| **Pipeline Builder** | DAG visuel, 80+ transforms, 300+ fonctions | **Connecteurs Python async** | 7 connecteurs en V1, adapteurs par source | A construire |
| **Data Connection** | 150+ connecteurs natifs | **Nango** | 300+ integrations OAuth, refresh tokens auto | Choix fait |
| **Workshop** | App builder low-code, 50+ widgets | **Platform app** (app.spideros.ai) | Hub, dashboard, 10 livrables Spider Intelligence | A construire |
| **AIP Logic** | No-code LLM workflow builder | **Agent pipeline** | Extraction LLM -> Claims -> Resolution -> Agents | Architecture definie |
| **Agent Studio** | Agents tool-use/function-calling | **Agents Spider** | Agents proactifs (Relance, Campagnes, Achats) | Conceptualises |
| **AIP Assist** | Widget chat dans Workshop | **Spider Chatbot** | Interface LLM unifiee sur donnees SpiderOS | P1 (a construire) |
| **AIP Evals** | Test cases et evaluateurs LLM | -- | A definir | N/A |
| **AIP Observability** | Traces, logs, monitoring | **Pattern Datadog** | rules -> check -> notify | Architecture definie |
| **Rubix** | Abstraction K8s (150+ microservices) | **K8s standard** | 3 clusters, GitOps | Operationnel |
| **FDE** ("Delta") | Ingenieur deploye ($135-300K, 25 ans median) | **FDE Spider** | Dev mid-senior, exp. ops (60-90K EUR, a recruter) | A recruter |
| **Deployment Strategist** ("Echo") | Ex-MBB, gere la politique client | **FDC Spider** | Ex-dirigeant industrie, consulting terrain | Thierry Menard |
| **Account Executive** | Proprietaire relation commerciale | **Nathan / Thibault** | CEO fait le commercial en Phase 0-1 | Operationnel |
| **AIP Bootcamp** | 5 jours gratuits, 5-8 pers., 22% conversion | **Diagnostic Eclair** | 1 demi-journee gratuite, 2 pers., cible 40-50% | A lancer |
| **Pilot 90 jours** | $250K, 2-4 FDEs on-site | **Phase 0** | 500 EUR/mois, 1 FDC + 1 FDE, 4 semaines | En cours (Jordan) |
| **Expand** (NDR 139%) | Multi-departement, Ontologie croit | **Upsell vertical** | Multi-process, Agents supplementaires | A tester |
| **Scale** (self-service) | CoE 5-50+ personnes, client construit 70-85% | **Assistant self-service** | L'assistant diagnostique et recommande des agents | Phase 3 (mois 9-12) |
| **Centre d'Excellence** | 5-50+ personnes, formation 80-100h | -- | Pas d'equivalent PME (dirigeant seul) | N/A |
| **Accenture Partnership** | 2 000+ pros formes Palantir | **Drakkar comme premier partenaire** | Puis integrateurs Odoo certifies Spider | A construire |
| **G-Cloud Pricing** | GBP 250K-10M+ par use case level | **Pricing Spider** | 500 EUR/mois entry + agents 190-990 EUR + setup 2-5K | Hypothese |
| **Security Model** (3 couches, 7 niveaux) | PBAC + Markings MAC + RBAC | **Zitadel** | OIDC, SSO, multi-tenancy (suffisant pour PME) | Choix fait |
| **Cell-level ACL** | Securite au niveau cellule | -- | Surdimensionne pour les PME | N/A |
| **Air-gap / Edge** | Deploiement sous-marins, FOBs | -- | Pas pertinent | N/A |
| **Entity Resolution** | ML pipeline multi-etapes, brevete | **Fellegi-Sunter + Jaro-Winkler** | Auto-merge >= 0.94 | Architecture definie |
| **RevDB** | Temporal queries, audit trail | **ATMS simplifie** | Retractation de claims, recompute global <2s | Architecture definie |
| **Revenue/employee** | $1.01M (2025) | **A prouver** | Cible : 150-250K EUR (avec IA) | Hypothese |
| **NDR** | 139% (Q4 2025) | **A prouver** | Cible : 130-150% | Hypothese |
| **Expansion multiple** | $100K -> $5.6M (56x) | **A prouver** | 500 EUR -> 2-5K EUR/mois (4-10x) | Hypothese |
| **Rule of 40** | ~90+ (56% growth + 34% margin) | -- | Trop tot pour mesurer | N/A |
| **Bootcamp volume** | 5/jour, 1 300+ cumules | -- | 1-2/semaine max en Phase 1 | A construire |
| **Conversion bootcamp** | ~22% (analystes) | **Cible : 40-50%** | Ticket 1 000x plus bas = friction plus basse | Hypothese |
| **Switching cost** | $2.5-7.5M par client | **Cout de sortie croissant quotidiennement** | Data captive + tacite formalise + agents dans le flux | Mecanisme |
| **7 couches lock-in** | Integration, Ontologie, Apps, Connaissance, Securite, Formation, Workflows | **5 couches** | Sources, Ontologie, Agents, Historique claims, Habitude | Conceptualisees |
| **Mycelium** (cross-client intelligence) | N'existe PAS chez Palantir | **Avantage unique Spider** | Intelligence collective inter-PME (Phase 2-3) | Vision |

---

> **Ce document est un point de depart, pas un point d'arrivee.** Chaque hypothese marquee "A prouver" est un test a executer. Chaque "A construire" est du travail a faire. Le playbook est le meme que Palantir. L'echelle est differente. La vitesse doit etre plus rapide.
>
> La question n'est pas "Spider peut-il etre Palantir ?" -- c'est "Spider peut-il executer le playbook Palantir 1 000x plus vite, 1 000x moins cher, pour un marche que Palantir ne peut pas voir ?"
>
> Jordan est le test. Les 12 prochaines semaines sont la reponse.

---

*Document genere le 19 fevrier 2026. Croise SPIDER-FINAL.md + Palantir Complete Playbook (27 fichiers, 322KB, 4 phases de recherche). Tout est la.*
