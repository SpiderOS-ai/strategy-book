# SPIDER -- CARTOGRAPHIE CONCURRENTIELLE & ROADMAP DE POSITIONNEMENT 2026-2028

> Document interne. Brut.
> Objectif : savoir exactement qui est sur le terrain, ou ils vont, et comment Spider se positionne face a eux sur 24 mois.
> Croise : SPIDER-FINAL.md, SPIDER-PALANTIR-BLUEPRINT.md, 04-cas-jordan.md, recherches marche fevrier 2026.
> Genere le 19 fevrier 2026.

---

## TABLE DES MATIERES

PART 1 : [Cartographie Concurrentielle 2026](#part-1--cartographie-concurrentielle-2026)
PART 2 : [Roadmap de Positionnement 2026-2028](#part-2--roadmap-de-positionnement-2026-2028)

---

# PART 1 -- CARTOGRAPHIE CONCURRENTIELLE 2026

Le marche n'est pas un diagramme propre. C'est un champ de bataille avec 7 categories d'acteurs qui se chevauchent, se cannibalisent, et laissent un vide beant au centre. Spider vise ce vide.

`[SCHEMA: "Carte de Positionnement Concurrentiel Spider 2026" -- Matrice 2 axes. Axe vertical : "COUVERTURE METIER" (de "1 fonction" en bas a "chaine de valeur complete" en haut). Axe horizontal : "DE LA DONNEE A LA DECISION" (de "visualisation" a gauche a "recommandation actionnable" a droite). Quadrant haut-gauche "ERP / PLATEFORMES" : Odoo (centre-haut-gauche), SAP (haut-gauche), Sage (centre-gauche), Cegid (centre-gauche), Pennylane (bas-gauche). Quadrant bas-gauche "WORKFLOW AUTOMATION" : Zapier (bas-gauche), Make (bas-gauche), n8n (bas-gauche). Quadrant bas-droite "AI EMPLOYEES / AGENTS" : Dust.tt (centre-bas-droite), Lindy AI (bas-droite), 11x.ai (centre-droite), Artisan AI (bas-droite), Sintra AI (bas-centre). Quadrant haut-droite "ORCHESTRATEURS IA" : OpenAI Frontier (haut-droite, mais hors PME), Microsoft Copilot Studio (haut-droite, hors PME), Salesforce AgentForce (haut-droite, hors PME), Google Vertex (haut-droite, hors PME). En bas-centre : CrewAI et LangChain (frameworks, pas des produits finis). SPIDER : point rouge en haut-droite, juste en dessous des orchestrateurs mais DANS le terrain PME. Fleche diagonale de bas-gauche a haut-droite avec label "Le chemin de Spider". Zone vide au centre-droite entouree de pointilles : "LE VIDE -- personne ne fait le travail de terrain pour les PME avec une couverture metier complete ET des recommandations actionnables". Les concurrents non-tech (assistante de direction, cabinet comptable, BPO, ne rien faire) sont hors cadre, listes en note en bas.]`

---

## 1. ORCHESTRATEURS IA (la couche du dessus)

Ce sont les fournisseurs d'infrastructure. Ils construisent les modeles, les plateformes, les SDK. Ils visent les entreprises de 10 000+ employes avec des budgets IT a 6-7 chiffres.

### OpenAI Frontier

- **Lance le :** 5 fevrier 2026
- **Ce que c'est :** plateforme de deploiement et gestion de flottes d'agents IA en entreprise. "Fleet management software for AI agents."
- **Clients annonces :** HP, Intuit, Oracle, State Farm, Thermo Fisher Scientific, Uber
- **Fonctionnement :** connecte les data warehouses, CRM, systemes de ticketing, applications internes pour donner du contexte partage aux agents. Les agents raisonnent sur les donnees, executent des taches complexes (fichiers, code, outils). Processus d'onboarding des agents similaire a la gestion d'employes humains.
- **Pricing :** non communique. Acces limite a un pool de clients selectionnes. Elargissement prevu courant 2026.
- **Funding :** OpenAI = $13B+ leves au total. Pas le meme univers.
- **Cible :** Fortune 500. PME = inexistant dans leur radar.

### Microsoft Copilot Studio / Agent 365

- **Ce que c'est :** plateforme unifiee de creation et gouvernance d'agents IA. Agent 365 = control plane centralise (gouvernance, monitoring, compliance). Copilot Studio = builder low-code pour agents enterprise.
- **Pricing :** Microsoft 365 Copilot a $30/user/mois. Copilot Studio pour agents custom en plus.
- **Nouveautes 2026 :** MCP servers pour que les agents programment des reunions, generent des documents, envoient des emails, mettent a jour le CRM. Upgrade one-click de Agent Builder vers Copilot Studio.
- **Cible :** enterprises Microsoft-first. PME francaises sur Odoo/Sage = pas dans l'ecosysteme.

### Google Vertex Agent Builder

- **Ce que c'est :** plateforme open de creation d'agents enterprise. 100+ connecteurs via Apigee. Multi-agent systems en Python (ADK -- Agent Development Kit).
- **Pricing :** baisse de prix janvier 2026. Pay-per-use Google Cloud.
- **Nouveautes 2026 :** Tool Governance via Cloud API Registry. Agent Registry dans Gemini Enterprise.
- **Cible :** equipes tech avec competences cloud. PME = zero chance.

### Salesforce AgentForce

- **Ce que c'est :** agents IA integres dans l'ecosysteme Salesforce. 3 modeles de pricing.
- **Pricing :** $2/conversation, OU Flex Credits a $0.10/action (100K credits pour $500), OU licences per-user a $125-550/user/mois (AELA).
- **Chiffres :** $540M ARR au Q3 FY2026 (+330% YoY). 18 500 deals fermes, 9 500 payes. Seulement ~8% de la base Salesforce (150K+ clients) a adopte AgentForce.
- **Cible :** la base installée Salesforce. PME francaises sur Odoo = hors scope.

### Pourquoi ils ne descendront pas sur les PME en 2026

3 raisons structurelles :

1. **Economie.** Un deal enterprise OpenAI Frontier ou Salesforce AgentForce = $100K-$1M+ ACV. Un deal PME Spider = 6K EUR/an. Il faudrait 100-150 PME pour egaler 1 enterprise. Les sales enterprise ne savent pas vendre a des patrons de PME qui ne repondent pas aux emails et decident sur un coin de table.

2. **Complexite du terrain.** Ces plateformes presupposent des equipes IT, des data engineers, des process documentes. 83.3% des PME francaises utilisent Excel comme outil analytique principal (Eurostat 2024). 44.8% n'ont aucune customisation ERP. Frontier ne peut pas se brancher la ou il n'y a rien a brancher.

3. **Culture.** Le dirigeant PME ne veut pas un "AI agent platform." Il veut que "quelqu'un s'occupe de la facturation." Le pont entre le SDK et la facturation, c'est exactement la ou Spider se place.

**Menace reelle a 24 mois :** faible. Ces acteurs tirent le marche vers le haut, ce qui eduque les dirigeants et cree de la demande. Spider recupere la demande que ces acteurs ne peuvent pas servir.

---

## 2. PLATEFORMES IA POUR AGENTS / "AI EMPLOYEES"

C'est la couche qui semble la plus proche de Spider. Mais aucun ne fait le travail de terrain.

### Dust.tt

- **Pays :** France (Paris)
- **Fondateurs :** Gabriel Hubert, Stanislas Polu (ex-OpenAI)
- **Ce que c'est :** plateforme d'assistants IA connectes aux donnees internes de l'entreprise. Les utilisateurs creent des "assistants" (agents specialises) qui accedent a Slack, Notion, Google Drive, GitHub, etc.
- **Pricing :** 29 EUR/user/mois
- **Funding :** $21.5M (Seed Sequoia 2023, Series A Sequoia 2024)
- **Revenue :** $7.3M en juillet 2025, 66 employes
- **Cible :** equipes tech-savvy en scale-ups/ETI. Clients types : equipes produit, engineering, ops dans des boites tech de 50-500 personnes.
- **Forces :** equipe technique de haut niveau, integration deep avec Slack/Notion, modele self-service qui scale.
- **Faiblesses pour le marche Spider :** 100% self-service (le dirigeant PME ne construira pas ses assistants lui-meme), pas d'integration ERP (Odoo, Sage, Pennylane), pas de dimension consulting/accompagnement.
- **Signal Novutech :** l'integrateur NetSuite europeen Novutech (Paris, 200+ implementations) utilise DEJA Dust pour deployer des agents IA chez ses clients. Autre ERP, autre segment (scale-ups tech, ETI internationales). Valide le marche "integrateur ERP + agents IA." Spider joue la meme partition sur un clavier different.

### Lindy AI

- **Pays :** USA (San Francisco)
- **Fondateur :** Flo Crivello
- **Ce que c'est :** plateforme de creation d'assistants IA personnels. "Build an AI employee in minutes." Templates pre-construits pour des taches specifiques (inbox, meetings, calendar).
- **Pricing :** $29-199/mois selon le plan
- **Funding :** ~$50M leves
- **Revenue :** $5.1M en 2024, 37 employes
- **Cible :** early adopters tech-savvy, freelances, petites equipes
- **Forces :** UX polished, templates rapides, pricing accessible
- **Faiblesses pour le marche Spider :** DIY pur (l'utilisateur configure tout), pas de profondeur metier (ne comprend pas la difference entre une commission espace publicitaire a 13% et 15%), zero integration ERP, zero accompagnement humain

### 11x.ai

- **Pays :** UK/USA (Londres/San Francisco)
- **Fondateur :** Hasan Sukkar
- **Ce que c'est :** "AI SDR" -- agents IA de prospection commerciale (Alice pour l'outbound, Jordan pour le phone).
- **Pricing :** ~$45K/an
- **Funding :** $76M (Seed + Series A Benchmark + Series B a16z, valorisation ~$350M)
- **Revenue :** ~$10M ARR fin 2024 (declare)
- **Cible :** enterprise sales teams
- **Problemes documentes :** churn catastrophique. Perte de 70-80% des clients des premieres cohortes (source: employes, TechCrunch mars 2025). Retention actuelle declaree a 79%. Accusations de faux clients (TechCrunch mars 2025 : "claiming customers it doesn't have"). Coup par $2 500 par reponse positive. Prix hors de portee des PME.
- **Pourquoi pas une menace :** mono-fonction (prospection uniquement), enterprise-only, prix 7.5x le MRR cible de Spider, et surtout : track record de churn qui disqualifie pour le marche PME ou la confiance est tout.

### Artisan AI

- **Pays :** USA (San Francisco)
- **Fondateur :** Jaspar Carmichael-Jack (YC)
- **Ce que c'est :** "AI Employees" pour l'outbound sales (produit phare : Ava, AI SDR).
- **Pricing :** ~$2K/mois
- **Funding :** $36.5M total ($11.5M seed + $25M Series A Glade Brook Capital, avril 2025). Investors : YC, HubSpot Ventures, Day One Ventures.
- **Cible :** equipes sales mid-market
- **Problemes documentes :** hallucinations graves au lancement ("extremely bad hallucinations when we first launched" -- CEO). Churn eleve. Le CEO admet que le produit ne convient pas a tous les segments et qu'ils refusent desormais certaines industries. Test de pricing "success-based" (pay per response) pour contrer la reputation.
- **Pourquoi pas une menace :** mono-fonction sales, hallucinations residuelles (1/10 000 emails -- mais pour une PME de 3 personnes, 1 email hallucine a un client fidele = catastrophe), pas d'ERP, pas de back-office.

### Sintra AI

- **Pays :** USA
- **Ce que c'est :** 12 "AI helpers" pre-configures (marketing, ventes, support, etc.)
- **Pricing :** non communique clairement, modele freemium
- **Funding :** non communique
- **Cible :** solopreneurs, micro-entreprises
- **Faiblesses pour le marche Spider :** pas d'integration ERP, pas d'ontologie business, pas de comprehension de la chaine de valeur. C'est un ChatGPT avec des personas.

### CrewAI

- **Pays :** USA
- **Fondateur :** Joao Moura
- **Ce que c'est :** framework open-source pour orchestrer des equipes d'agents IA. 10M+ agents executes par mois. Utilise par ~50% du Fortune 500.
- **Pricing :** open-source gratuit + offre enterprise payante
- **Funding :** $18M (Series A, Insight Partners + Boldstart, octobre 2024). Angels : Andrew Ng, Dharmesh Shah (HubSpot CTO).
- **Cible :** developpeurs et equipes engineering
- **Pourquoi pas une menace directe :** c'est un outil de developpement, pas un service fini. Spider pourrait meme l'utiliser en interne. Un patron de PME ne touchera jamais CrewAI.

### LangChain

- **Pays :** USA (San Francisco)
- **Fondateur :** Harrison Chase
- **Ce que c'est :** framework + plateforme pour construire des applications LLM et des agents. LangSmith pour le monitoring, LangGraph pour les workflows agents.
- **Pricing :** open-source + LangSmith payant ($39/mois+)
- **Funding :** $260M total ($10M seed Benchmark 2023, $25M Series A Sequoia 2024, $125M Series B IVP octobre 2025). Valorisation : $1.25B (licorne).
- **Cible :** developpeurs, equipes ML/AI
- **Pourquoi pas une menace directe :** meme logique que CrewAI. Infrastructure, pas service. Spider pourrait l'integrer. Le patron de PME ne saura jamais que LangChain existe.

### Synthese : ou chacun se positionne

| Acteur | Self-service vs Managed | Mono vs Multi-fonction | PME-ready | Profondeur metier |
|--------|------------------------|------------------------|-----------|-------------------|
| Dust.tt | Self-service | Multi | Non (tech-savvy only) | Aucune |
| Lindy AI | Self-service | Multi (templates) | Partiellement | Aucune |
| 11x.ai | Managed (mais enterprise) | Mono (sales) | Non | Sales uniquement |
| Artisan AI | Semi-managed | Mono (sales) | Non | Sales uniquement |
| Sintra AI | Self-service | Multi (superficiel) | Oui mais gadget | Aucune |
| CrewAI | DIY (framework) | Multi (outil) | Non | N/A (outil dev) |
| LangChain | DIY (framework) | Multi (outil) | Non | N/A (outil dev) |
| **Spider** | **Managed** | **Multi (chaine valeur)** | **Oui** | **Deep (ontologie)** |

**Pourquoi Spider est different :** Spider est le seul acteur qui combine service manage (le client ne fait rien) + couverture multi-fonction (pas juste sales ou inbox) + profondeur metier (ontologie qui comprend que chez Jordan, une commission espace a 13% s'applique a Cadres Blancs et 15% a JCDecaux) + ciblage PME reellement non-tech. C'est l'intersection de 4 criteres que personne ne remplit.

---

## 3. WORKFLOW AUTOMATION (la couche du dessous)

Les outils de plomberie. Puissants, mais le client doit SAVOIR ce qu'il veut automatiser et LE CONSTRUIRE lui-meme.

### Zapier

- **Pricing :** a partir de $19.99/mois (Free tier disponible)
- **Integrations :** 8 000+ apps
- **Ce que c'est :** l'outil standard pour connecter des apps entre elles. "When X happens in App A, do Y in App B."
- **Cible :** ops teams, marketers, utilisateurs intermediate
- **Revenue :** ~$400M+ ARR estime (non confirme)
- **Forces :** ubiquite, facilite d'utilisation pour des automatisations simples, enorme catalogue
- **Faiblesses pour le marche Spider :** le dirigeant PME ne definira jamais un Zap. Il ne sait pas ce qu'il veut automatiser. Zapier automatise le connu -- Spider automatise ce que le dirigeant ne sait meme pas qu'il devrait automatiser.

### Make (ex-Integromat)

- **Pricing :** a partir de $9/mois
- **Integrations :** 3 000+ apps
- **Ce que c'est :** automatisation visuelle avec scenarios complexes. Plus puissant que Zapier pour les workflows multi-etapes.
- **Cible :** power users, agencies, developpeurs no-code
- **Forces :** pricing agressif, workflows visuels puissants
- **Faiblesses pour le marche Spider :** courbe d'apprentissage pentue. Le patron de Jordan (3 personnes, Excel + Notion + Pennylane) ne construira pas un scenario Make pour automatiser la triple saisie. Il veut que quelqu'un le fasse.

### n8n

- **Pricing :** a partir de 20 EUR/mois (self-hosted gratuit, open-source)
- **Integrations :** 500+ nodes
- **Ce que c'est :** alternative open-source a Zapier/Make. Self-hostable. Tres technique.
- **Cible :** developpeurs, DevOps, equipes tech
- **Forces :** open-source, self-hosted (souverainete), tres flexible
- **Faiblesses pour le marche Spider :** necesssite un dev pour l'installer et le maintenir. PME de 3-50 personnes = zero chance.

### Pourquoi les PME n'utiliseront pas ces outils

Le probleme n'est pas la technologie. C'est la charge cognitive.

Pour automatiser la triple saisie de Jordan (Sheets -> Notion -> Pennylane), il faudrait :
1. Comprendre le concept d'automatisation
2. Identifier les 3 sources et leur logique de connexion
3. Mapper les 33 champs Notion vers les champs Pennylane
4. Gerer les exceptions (commissions a 13% vs 15% vs 20%, gestion a 85 vs 150 EUR)
5. Tester, debugger, maintenir

Jordan ne fera jamais ca. Eline ne fera jamais ca. Audrey ne fera jamais ca. Ils veulent que ca marche. Point.

C'est le vide que Spider remplit : on fait le Zapier/Make/n8n POUR le client, et en plus on detecte ce qu'il aurait du automatiser mais qu'il ne savait meme pas.

---

## 4. ERP / PLATEFORMES TRANSACTIONNELLES

Le socle sur lequel Spider se branche. Pas des concurrents -- des substrats.

### Odoo (+ Odoo 19 avec agents IA integres)

- **Pays :** Belgique (Namur)
- **Fondateur :** Fabien Pinckaers
- **Ce que c'est :** ERP open-source le plus adopte au monde. 12M+ utilisateurs. Suite complete (CRM, facturation, inventaire, RH, e-commerce...).
- **Pricing :** gratuit (Community) ou $24.90/user/mois (Enterprise)
- **Revenue :** ~$300M+ ARR estime
- **ODOO 19 -- LE SIGNAL :** Odoo 19 integre des agents IA natifs. Topics pre-configures : Natural Language Search, Information Retrieval, Create Leads. Les agents peuvent apprendre des documents (RAG), creer des evenements calendrier, generer des leads via Livechat. Supporte ChatGPT et Gemini. Personnalisation du tone of voice.
- **Menace pour Spider :** REELLE mais limitee. Odoo 19 fait de l'IA horizontale/generique. L'agent Odoo cree un lead -- il ne sait pas que chez Jordan, le client Schmidt Mondeville a 36 campagnes avec une marge de 25.1% et qu'il faudrait lui proposer un upsell services manages pour passer a 35%+. Spider connait le metier. Odoo connait les champs de la base de donnees.
- **Timeline menace :** Odoo 19 sort au printemps 2026. Les agents seront basiques en V1. D'ici 12-18 mois, ils s'amelioreront. Spider a une fenetre de 12-18 mois pour capturer la data et creer le moat avant que l'IA Odoo ne devienne competente.

### SAP (+ SAP Joule)

- **Ce que c'est :** ERP enterprise dominant. Joule = assistant IA integre lance en 2023.
- **Pricing :** licences enterprise, $150K-$1M+/an typiquement
- **Cible :** grandes entreprises, ETI internationales. Zero PME francaise de 5-50 personnes.
- **Menace pour Spider :** nulle. Marche completement different.

### Sage

- **Ce que c'est :** ERP/comptabilite, forte presence en France. Sage 100, Sage X3.
- **Pricing :** variable, $30-300+/user/mois selon le produit
- **Cible :** PME francaises comptables, cabinet-driven
- **Menace pour Spider :** Sage est un backend. Spider se branche dessus. Si Sage ajoute des agents IA, meme logique qu'Odoo : horizontale, generique, pas de profondeur metier.

### Cegid

- **Ce que c'est :** ERP/comptabilite/RH/retail, tres present en France. 750K+ clients.
- **Pricing :** SaaS, non standardise
- **Cible :** PME/ETI francaises, surtout retail et comptabilite
- **Menace pour Spider :** meme logique. Cegid restera un socle transactionnel. Les agents viendront par-dessus.

### Pennylane

- **Pays :** France (Paris)
- **Fondateurs :** Arthur Waller, Felix Music
- **Ce que c'est :** plateforme de gestion financiere (comptabilite, facturation, tresorerie) pour PME. Positionnee "le Stripe de la comptabilite francaise."
- **Funding :** $107M+ leves (dont $52M Series C 2024, General Catalyst + Sequoia)
- **Revenue :** ~$50M+ ARR estime
- **Cible :** TPE/PME francaises, via les cabinets comptables (4 000+ cabinets partenaires)
- **Forces :** UX excellente, integration bancaire automatique, adoption forte des cabinets
- **Menace pour Spider :** Pennylane est LA source de donnees financieres de Spider chez Jordan (c'est la 3eme saisie). Si Pennylane ajoute des agents IA pour la relance, le rapprochement, la prevision de tresorerie -- ca empiete sur l'Agent Relance de Spider. Mais Pennylane reste mono-fonction (finance). Spider couvre la chaine de valeur complete.
- **A surveiller :** expansion potentielle de Pennylane vers des fonctions non-comptables (CRM ? achats ? operations ?). Si oui, menace serieuse sur le segment TPE.

### Synthese ERP

Les ERP deviennent des backends commoditises. L'intelligence se deplace VERS le dessus -- la couche agents/decisions. Spider se positionne comme cette couche superieure. Peu importe que le client soit sur Odoo, Sage, ou Pennylane : Spider se branche, extrait, analyse, agit. L'ERP stocke les transactions. Spider comprend le metier.

---

## 5. INTEGRATEURS ODOO (concurrents directs de Drakkar)

Ce sont les concurrents de Drakkar, pas de Spider. Mais ils pourraient pivoter.

### Acteurs identifies

| Integrateur | Localisation | Taille estimee | Specialite |
|-------------|-------------|----------------|------------|
| **Apik** | Belgique/France | 30-50 pers. | Odoo Gold Partner, PME industrielles |
| **Irokoo** | France (Paris) | 15-30 pers. | Odoo Silver Partner, startups/PME |
| **Scalizer** | France (Lyon) | 20-40 pers. | Odoo Gold Partner, e-commerce/industrie |
| **Dynapps** | Belgique | 50-80 pers. | Odoo Gold Partner, ETI |

### Modele economique

100% vente de jours. Parametrage, formation, maintenance. Facturation en TJM (600-1 200 EUR/jour). Zero produit propre. Zero IA. Zero pivot visible.

Ils vivent dans le monde de la "personnalisation ERP" -- celui que Nathan decrit comme mourant : "les scopes 50-100K se feront a 5-10K dans 2-3 ans" avec la compression IA.

### Signal d'alarme : Novutech

Novutech est un integrateur NetSuite (pas Odoo, mais meme logique). Base a Paris, 200+ implementations, cible les scale-ups tech et ETI internationales. Novutech couple DEJA son expertise ERP avec Dust.tt pour deployer des agents IA chez ses clients.

Ceci valide deux choses :
1. Le marche "integrateur ERP + agents IA" est reel et en train de se former
2. Le premier integrateur Odoo qui fera le meme move deviendra un concurrent direct

**Aucun integrateur Odoo n'a fait ce pivot a date.** C'est la fenetre de Spider/Drakkar.

### Pourquoi ils ne pivoteront pas vite

- Leurs revenus actuels viennent de la vente de jours. Pivoter = cannibaliser.
- Leurs consultants sont des fonctionnels ERP, pas des AI engineers.
- Leurs clients ne demandent pas (encore) des agents IA.
- Le CEO type d'un integrateur Odoo ressemble a Benoit Vasseur : "dans 2 ans."

Mais dans 18-24 mois, quand Odoo 19+ aura des agents IA natifs et que les clients commenceront a demander, le plus rapide d'entre eux pivotera. Spider doit etre installe avant.

---

## 6. ESN / CABINETS DE CONSEIL

Joueurs massifs mais pas sur le meme terrain.

### ESN generalistes

| Acteur | Taille | CA | Cible | TJM moyen |
|--------|--------|-----|-------|-----------|
| **Smile** | 2 000+ | ~$200M+ | ETI/Grands comptes | 800-1 200 EUR |
| **Capgemini** | 350 000+ | ~$23B | Fortune 500 | 1 000-2 000 EUR |
| **Sopra Steria** | 55 000+ | ~$6B | Grands comptes publics/prives | 900-1 500 EUR |

PME de 5-50 personnes = economiquement impossible pour ces acteurs. Le cout d'acquisition d'un client PME depasse le revenu du projet. Ils restent sur les ETI/grands comptes.

### Cabinets de conseil

| Acteur | Type | Cible PME | TJM |
|--------|------|-----------|-----|
| **BDO** | Audit/conseil international | ETI/PME moyennes | 200-400 EUR/h |
| **Grant Thornton** | Audit/conseil | ETI | 250-500 EUR/h |
| **Cabinets regionaux** | Comptabilite/conseil | PME locales | 150-250 EUR/h |

Les cabinets regionaux sont les concurrents les plus proches dans l'esprit du dirigeant PME. C'est vers eux qu'il se tourne quand il a un "probleme d'organisation." Mais leur modele est reactif (le client appelle, ils facturent des heures) et non operationnel (ils produisent des recommandations, pas des resultats).

### The Tribe -- le signal

- **Taille :** 70+ personnes, Nantes
- **CEO :** Benoit Vasseur
- **Fait :** a gagne le deal Twoghether face a Drakkar. Le client a choisi "le feeling" (Maxime : "c'est une histoire de feeling"). Angelique (CEO Twoghether) a choisi parce que "ca sent bon."
- **Ce que ca dit :** dans le monde du conseil, la vente est encore 100% relationnelle. La competence technique n'est pas le differenciateur. C'est exactement T2 (la vente B2B est un mensonge).
- **Perception de Benoit Vasseur sur l'IA :** "dans 2 ans." Attentisme general. "A quoi bon investir si c'est perime dans 2 ans."
- **Ce que Nathan en pense :** "hallucine que Benoit ne se rende pas compte en 2026." Nathan vit dans une "microbulle YC." L'ecart de perception est massif.
- **Implication :** l'inertie du marche francais est a la fois un risque (le marche n'est pas pret, il faut l'eduquer) et une opportunite (pas de concurrence immediate de la part des ESN/cabinets locaux sur le segment IA + PME).

---

## 7. LES VRAIS CONCURRENTS (pas tech)

Le concurrent #1 de Spider n'est pas Dust ou Zapier. C'est l'inertie humaine.

### L'assistante de direction

- **Cout :** 2 500-3 500 EUR/mois (charges comprises)
- **Disponibilite :** 35h/semaine, vacances, arrets maladie
- **Forces :** connait les habitudes du patron, gere les exceptions, parle aux clients, fait le cafe
- **Faiblesses :** savoirs non duplicables (quand elle part, tout part avec elle), scaling impossible (il faut en embaucher une deuxieme), cout total reel = 40-50K EUR/an minimum
- **Contre Spider :** Spider ne remplace pas Marie. Spider fait ce que Marie ne fait pas (analyser 726 lignes de campagnes, detecter les 39.3% d'impayes, optimiser les marges). L'argument : "Spider coute 500 EUR/mois. Marie coute 3 000 EUR. Spider fait le travail que Marie ne peut pas faire, ET le travail administratif que Marie fait en 5h/jour."

### Le cabinet comptable

- **Cout :** 150-250 EUR/heure, ou forfaits mensuels 300-2 000 EUR/mois
- **Ce qu'il fait :** comptabilite, fiscal, social, conseil ponctuel
- **Ce qu'il ne fait pas :** operations, suivi de campagnes, relance clients, optimisation des achats
- **Contre Spider :** complementaire, pas concurrent. Spider gere l'operationnel que le comptable ne touche pas. A terme, Spider pourrait meme alimenter le comptable en donnees mieux structurees (flux Pennylane automatise = moins de saisie comptable).

### Le BPO / office manager externalise

- **Cout :** 35-50 EUR/heure
- **Ce qu'il fait :** administratif, saisie, suivi, relance
- **Faiblesses :** scaling lineaire (plus de travail = plus d'heures = plus de cout), pas d'apprentissage cumulatif, pas de diagnostic
- **Contre Spider :** Spider = BPO avec un cerveau. Meme travail, mais Spider apprend de chaque tache executee. Le BPO fait la saisie 726 fois de la meme maniere. Spider fait la saisie 1 fois et automatise les 725 suivantes.

### Ne rien faire (80% des PME)

Le concurrent #1. Absolu. Imbattable sur le prix (0 EUR/mois).

80% des PME francaises n'ont aucune solution d'automatisation. 90% sont en "phase 1" de l'IA (ChatGPT = Google ameliore). Seulement 8.9% utilisent une forme d'IA (Eurostat 2024).

Pour ces 80%, le probleme n'est pas le prix ou la technologie. C'est :
1. Ils ne savent pas qu'une solution existe
2. Ils ne pensent pas en avoir besoin (T5 : le ratio effort/benefice est catastrophique dans leur tete)
3. Ils ont peur de changer (T4 : ils veulent la couronne, pas le fardeau)

Spider ne vend pas un outil a ces 80%. Spider vend du soulagement. "On s'en occupe. Vous, faites ce que vous aimez."

### Tableau comparatif complet

| Alternative | Cout/mois | 24/7 | Apprentissage | Diagnostic | Multi-process | Scaling |
|-------------|-----------|------|---------------|------------|---------------|---------|
| Assistante de direction | 2 500-3 500 EUR | Non | Non | Non | Limité | Lineaire |
| Cabinet comptable | 300-2 000 EUR | Non | Non | Ponctuel | Finance only | Par heure |
| BPO externalisé | 1 400-8 000 EUR | Non | Non | Non | Multi mais lineaire | Lineaire |
| Ne rien faire | 0 EUR | -- | -- | -- | -- | -- |
| **Spider** | **500 EUR entry** | **Oui** | **Cumulatif** | **Proactif** | **Chaine de valeur** | **Par agent** |

---

## 8. STARTUPS IA FRANCAISES A SURVEILLER

L'ecosysteme francais IA est massif (1 114 startups, 16B EUR leves au total) mais fragmente. Voici les acteurs qui pourraient croiser la route de Spider.

### Mistral AI

- **Fondateurs :** Arthur Mensch, Guillaume Lample, Timothee Lacroix (ex-DeepMind, ex-Meta)
- **Funding :** ~$2B+ leves (dont $640M Series B Andreessen Horowitz, juin 2024). Valorisation : ~$6B.
- **Ce que c'est :** foundation models. Concurrence OpenAI/Anthropic/Google sur l'infra LLM.
- **Relation Spider :** fournisseur potentiel, pas concurrent. Spider pourrait utiliser Mistral comme LLM souverain EU pour ses extractions (alternative a Haiku/Sonnet). Argument souverainete.

### H Company

- **Fondateurs :** Charles Kantor, Karl Tuyls (ex-DeepMind)
- **Funding :** $220M seed (record francais, mai 2024)
- **Ce que c'est :** foundation models pour agents IA. Vision long-terme, produit pas encore visible.
- **Relation Spider :** meme logique que Mistral. Infra, pas concurrent direct.

### Pennylane (deja couvert en section 4)

- **Risque specifique :** si Pennylane decide de monter en gamme vers des fonctions non-comptables (gestion des achats, suivi commercial, operations), avec des agents IA integres, c'est une menace serieuse sur le segment TPE/petite PME. Pennylane a l'adoption (4 000+ cabinets partenaires), le financement ($107M+), et la data financiere.
- **Probabilite a 24 mois :** faible. Pennylane a deja les mains pleines avec la comptabilite automatisee et l'expansion europeenne. Mais a surveiller.

### Axonaut

- **Pays :** France (Toulouse)
- **Ce que c'est :** CRM/ERP simplifie pour TPE/PME. Facturation, CRM, comptabilite basique.
- **Pricing :** a partir de 49.99 EUR/mois
- **Cible :** TPE/artisans/independants (1-20 personnes)
- **Forces :** UX simple, pricing accessible, marche francais
- **Menace pour Spider :** faible directement, mais si Axonaut ajoute des agents IA, ils touchent le meme segment. Limite par leur taille (equipe <50 personnes) et leur focus TPE (trop petit pour Spider qui vise 5-50+ personnes).

### L'ecosysteme en chiffres

| Metrique | Valeur |
|----------|--------|
| Startups IA francaises | 1 114 |
| Total leve | 16B EUR |
| Part de l'IA dans le financement French Tech 2025 | 62% ($8.2B sur $13.2B) |
| PME francaises utilisant l'IA | ~10% |
| PME francaises voulant utiliser l'IA | 89% |
| Gap offre/demande | **79 points** |

Ce gap de 79 points (89% veulent, 10% utilisent) est le marche de Spider.

---

# PART 2 -- ROADMAP DE POSITIONNEMENT 2026-2028

`[SCHEMA: "Roadmap de Positionnement Spider 2026-2028" -- Timeline horizontale sur 24 mois. Ligne du haut "SPIDER" (vert) : 5 blocs. Q1 2026 (bleu fonce) : "INVISIBLE -- 0 client -- Jordan Phase 0". Q2 2026 (bleu) : "3-5 clients -- preuve de these -- pricing valide". Q3-Q4 2026 (vert) : "8-20 clients -- 1er template vertical -- assistant lance". H1 2027 (orange) : "30-50 clients -- marque Spider -- reseau partenaires". H2 2027 - 2028 (rouge) : "80-150 clients -- data moat -- Mycelium". Ligne du milieu "CONCURRENTS" (gris) : fleches et labels synchronises avec la timeline Spider. Q1 : "Frontier lance, AgentForce $540M ARR". Q2 : "Odoo 19 lance agents IA, Dust $7M+ ARR". Q3-Q4 : "Gartner 40% enterprise apps avec agents, 11x.ai implose ou pivote". H1 2027 : "Zapier/Make ajoutent agents ?, Dust SMB tier ?". H2 2027-2028 : "Course lancee -- mais Spider a 18+ mois de data captive". Ligne du bas "METRIQUES SPIDER" : MRR croissant (500 EUR -> 3-5K -> 10-14K -> 30-45K -> 144-270K). Diamants G1-G6 positionnes sur la timeline. En haut : barre de maturite IA (Copilote -> Agent executant -> Agent autonome).]`

---

## Q1 2026 (MAINTENANT -- Janvier-Mars)

### Position Spider

- **Statut :** invisible. Zero client. Zero revenue Spider. Tout est sous la marque Drakkar.
- **Equipe active :** Nathan (CEO/FDE), Thierry (FDC), Remy (CTO). Jean en montee de comprehension rapide.
- **Focus :** Jordan Phase 0. Un client. Un process. Un prix. 500 EUR/mois.
- **Gate G1 (semaine 4) :** Jordan renouvelle-t-il ?

### Ce que font les concurrents

| Acteur | Action Q1 2026 | Impact sur Spider |
|--------|----------------|-------------------|
| OpenAI | Frontier lance le 5 fevrier. Acces limite aux enterprises. | Indirect positif : legitime le marche des agents IA, eduque les dirigeants |
| Salesforce | AgentForce a $540M ARR, 18 500 deals. 92% de la base n'a pas encore adopte. | Zero impact : pas le meme segment |
| Microsoft | Copilot Studio Agent 365 pousse fort. MCP servers, governance. | Zero impact : ecosysteme Microsoft, pas Odoo |
| Dust.tt | Continue de croitre ($7.3M ARR mid-2025). Focus equipes tech/scale-ups. | Zero impact direct. A surveiller si annonce SMB. |
| Odoo | Odoo 19 en beta. Agents IA en preview. | A SURVEILLER. Pas encore live mais le signal est clair. |
| Integrateurs Odoo | Aucun pivot IA visible. Business as usual. | Fenetre ouverte pour Spider. |

### Move de Spider

1. Livrer Jordan. Eliminer la triple saisie. Prouver que le modele Service-as-Software fonctionne.
2. Tracker les metriques internes : temps/campagne (humain vs IA), taux erreur, satisfaction.
3. Preparer le diagnostic eclair pour les 2-3 prochains prospects (reseau Drakkar).
4. Nathan continue la veille concurrentielle (Carlos Diaz / Silicon Carne, YC batch, Product Hunt).

### Risques Q1

- Jordan est un ami. Le test commercial est biaise. On le sait. On avance quand meme.
- Le prototype "2h30 de travail" est a double tranchant : si c'est vrai, n'importe quel dev competent peut le faire. La barriere n'est pas le code -- c'est l'ontologie et la relation.

---

## Q2 2026 (Avril-Juin)

### Position Spider

- **Statut :** 3-5 clients, dont au moins 1 non-ami. MRR : 3-5K EUR.
- **Gate G2 (mois 3) :** 3+ clients payants ? <20% churn ?
- **Hypotheses en test :** H1 (un dirigeant paie 500 EUR/mois), H3 (un non-ami signe)

### Ce que font les concurrents

| Acteur | Action Q2 2026 | Impact sur Spider |
|--------|----------------|-------------------|
| Odoo | **Odoo 19 sort officiellement.** Agents IA disponibles (RAG, Natural Language Search, Create Leads). | MENACE MODERATE. Les integrateurs Odoo vont commencer a en parler. Mais l'agent Odoo est generique. |
| Dust.tt | Potentielle annonce d'un tier SMB ou d'un pricing plus bas ? | A surveiller. Si Dust lance a <20 EUR/user pour PME, ca cree du bruit. |
| 11x.ai | Continuation des problemes de retention. Possible pivots. | Pas d'impact. Segment different. |
| Artisan AI | Deploiement du "success-based pricing." Test marche. | Signal interessant : le marche AI employees cherche encore son modele economique. |
| Zapier/Make | Probablement premiers tests de features "AI-suggested automations." | A surveiller. Si Zapier ajoute "nous detectons que vous devriez automatiser X" = rapprochement du modele Spider. |

### Move de Spider

1. **Valider H1-H3.** Le premier client non-ami qui signe a 500 EUR/mois = signal critique. Si ca marche, la these tient. Si ca echoue, il faut comprendre pourquoi (prix ? confiance ? comprehension de l'offre ?).
2. **Definir le pricing reel.** 500 EUR est un test. Apres 3-5 clients, on saura si c'est trop bas (trop facile, pas assez de valeur percue), trop haut (resistance), ou juste.
3. **Premier upsell chez Jordan.** Agent Relance sur les 39.3% d'impayes. Setup 2K EUR + 190-500 EUR/mois. Si Jordan passe de 500 a 700-1 000 EUR/mois, le flywheel est amorce.
4. **Commencer a documenter l'ontologie "agence pub."** C'est le premier template vertical. Si le client 3 est aussi une agence, le temps d'onboarding devrait baisser de 40%+ (test de H4).

### Risques Q2

- Odoo 19 cree du bruit marketing autour des "agents IA dans votre ERP." Les dirigeants pourraient penser que leur ERP suffit.
- Le prix de 500 EUR/mois est peut-etre trop bas pour etre credible. Un dirigeant pourrait se dire "a 500 EUR/mois, ca ne peut pas etre serieux."

---

## Q3-Q4 2026 (Juillet-Decembre)

### Position Spider

- **Statut :** 8-20 clients. MRR : 10-14K EUR. Au moins 2 verticaux testes (agence pub + 1 autre).
- **Gate G3 (mois 6) :** ratio IA/humain s'ameliore ? 50%+ IA sur au moins 2 processus ?
- **Gate G4 (mois 9) :** faut-il construire l'assistant gratuit ?
- **Hypotheses en test :** H2 (50% IA), H4 (transfert ontologie), H6 (ratio FDE s'ameliore)

### Ce que font les concurrents

| Acteur | Action Q3-Q4 2026 | Impact sur Spider |
|--------|-------------------|-------------------|
| Gartner | Prediction : 40% des apps enterprise auront des agents IA fin 2026. | Contexte macro qui legitime Spider. "Meme Gartner le dit." |
| OpenAI Frontier | Elargissement de l'acces. Premiers retours terrain des clients enterprise. | Indirect positif : histoires de succes enterprise = preuve de concept pour le concept agent IA. |
| Odoo | Agents IA V2 dans Odoo 19.x. Features ameliorees. Premiers cas concrets chez les integrateurs. | MENACE CROISSANTE. Les integrateurs Odoo qui comprennent l'IA commenceront a se positionner. |
| Dust.tt | Possible Series B. Expansion produit. | A surveiller mais pas d'impact direct tant qu'ils restent sur equipes tech. |
| LangChain | Licorne a $1.25B. Devient l'infra standard. | Opportunite : Spider peut s'appuyer sur LangChain pour ses pipelines agents. |

### Move de Spider

1. **Productiser.** Passer du bespoke au reproductible. Templates d'ontologie par vertical. Onboarding standardise. Ce qui prenait 4 semaines pour Jordan doit prendre 2 semaines pour le client 10.
2. **Construire le dashboard de supervision.** Les FDC/FDE ne peuvent pas gerer 15-20 clients sans un outil de monitoring centralise.
3. **Lancer le branding Spider.** Passer de "Drakkar" a "Spider" sur les nouveaux clients. Tester le nom, le positionnement, le pitch.
4. **Developper 3-5 agents catalogue.** Agent Relance, Agent Campagnes, Agent Achats, Agent Reporting, Agent Contenu. Pricing standardise.
5. **Premiere version de l'assistant (si G4 valide).** Chatbot IA connecte a Odoo/Pennylane. Gratuit ou credits. Objectif : cheval de Troie pour l'acquisition.
6. **Premiere version de Mycelium en interne.** Avec 8-20 clients, commencer a detecter des patterns cross-clients. Pas encore commercialise -- juste prouve en interne.

### Risques Q3-Q4

- Le ratio FDE:clients ne s'ameliore pas. Chaque client est unique. L'ontologie ne se transfere pas. Si c'est le cas, Spider est une ESN avec de l'IA.
- Un integrateur Odoo francais (Apik ? Scalizer ?) annonce une offre "Odoo + IA" qui ressemble a Spider. Course de vitesse.
- La compression IA continue : ce que Spider vend 500 EUR, un freelance intelligent pourrait le faire pour 200 EUR avec les outils de fin 2026.

---

## H1 2027 (Janvier-Juin)

### Position Spider

- **Statut :** 30-50 clients. MRR : 30-45K EUR. Annualise : 360-540K EUR.
- **Gate G5 (mois 12) :** Spider = entite separee ? 20+ clients, 30K+ MRR, chemin vers 65%+ marges ?
- **Equipe :** 2-4 FDC + 2-4 FDE + Nathan + Remy. Potentiellement 8-10 personnes.

### Ce que font les concurrents

| Acteur | Action H1 2027 | Impact sur Spider |
|--------|----------------|-------------------|
| Zapier | Probable lancement de "Zapier AI Agents" ou equivalent. Automatisations suggerees par l'IA. 8 000+ integrations comme levier. | MENACE SERIEUSE si Zapier ajoute une couche managed/proactive. Spider doit se differencier par la profondeur metier, pas la plomberie. |
| Make | Meme mouvement que Zapier. "Make AI" avec suggestions automatiques. | Meme analyse. |
| Dust.tt | Possible pivot vers SMB/PME avec un tier gratuit ou low-cost. Capitalise sur sa base tech-savvy pour descendre en gamme. | MENACE MODERATE. Dust ne connait pas le metier PME. Mais l'execution est rapide. |
| Odoo | Agents IA V3, plus matures. Premiers agents verticaux (manufacturing, retail ?). | MENACE CROISSANTE. Mais toujours horizontale. Spider connait le metier. Odoo connait la base de donnees. |
| Integrateurs Odoo | 1-2 integrateurs auront lance une offre "Odoo + IA." Signal du marche. | CONCURRENCE DIRECTE sur le segment. La course est lancee. |

### Move de Spider

1. **Construire le reseau partenaires.** Recruter les premiers integrateurs externes certifies Spider. Pas les integrateurs Odoo concurrents -- des profils nouveaux (freelances tech, consultants PME, comptables innovants).
2. **Decision entite separee.** Si les metriques justifient (30K+ MRR, 20+ clients, marges en amelioration) : creer Spider SAS distincte de Drakkar. Capitalisation du deal : Nathan 51%, Jean 20%, Remy 14%, Thierry 10%, Drakkar 5%.
3. **Marque Spider.** Site, contenu, premiers temoignages clients. La marque devient un actif. "Spider gere mes campagnes" = signal de confiance pour le prochain prospect.
4. **Revenue/employee.** A 30-45K EUR MRR avec 8-10 personnes = 36-54K EUR annualise par personne. Loin du $1.01M de Palantir. Mais si on atteint 50K EUR MRR avec 6 personnes grace a l'amelioration du ratio = 100K EUR/personne. Le modele commence a respirer.

### Risques H1 2027

- Le marche PME reste inerte. Les 80% qui ne font rien continuent de ne rien faire. L'education du marche est plus lente que prevue.
- Jean et/ou Thierry ne font pas la transition psychologique de Drakkar vers Spider. L'attrait de la securite Drakkar ($1.5M/an de revenue) freine l'engagement Spider.
- Un acteur inattendu (une startup francaise, un integrateur agressif, un gros cabinet de conseil qui pivote) lance une offre identique avec plus de moyens.

---

## H2 2027 - 2028 (Juillet 2027-Decembre 2028)

### Position Spider

- **Statut :** 80-150 clients. MRR : 144-270K EUR. Annualise : 1.7-3.2M EUR.
- **Gate G6 (mois 18) :** faut-il lever ? PMF confirme, unit economics valides, demande partenaire ?
- **Data moat :** 18+ mois de donnees captives sur 80-150 entreprises. Patterns cross-clients. Le Mycelium commence a produire de la valeur.

### Ce que font les concurrents

| Acteur | Action H2 2027-2028 | Impact sur Spider |
|--------|---------------------|-------------------|
| Tout le monde | Le marche des agents IA PME est devenu visible. Les conferences en parlent. Les cabinets publient des rapports. | **La course est ON.** Mais Spider a 18+ mois de data captive et d'ontologie accumulee. |
| Odoo | Agents IA matures. Marketplace d'agents tiers. Possibles partenariats avec Dust ou equivalent. | Odoo devient le socle backend. Spider reste la couche d'intelligence au-dessus. Coexistence possible. |
| Zapier/Make | Agents IA integres, suggestions proactives. Mais toujours self-service. | Le DIY vs managed reste le differenciateur. Zapier dit "nous avons detecte X." Spider dit "nous avons deja regle X." |
| Nouveaux entrants | Des startups francaises/europeennes lancent des offres similaires. 2-3 concurrents directs apparaissent. | Normal. La question n'est pas "y aura-t-il de la concurrence" mais "Spider aura-t-il assez de data captive pour etre indelogeable." |
| Gartner/analystes | La categorie "Managed AI Operations for SMBs" apparait dans les rapports. | Spider veut etre le leader de cette categorie au moment ou elle est nommee. |

### Move de Spider

1. **Decision fundraise.** Seed 2-5M EUR (Europe ou US). Si les metriques sont la : 100+ clients, 150K+ MRR, unit economics qui tiennent, 2-3 verticaux maitrises. Ou decision de rester self-funded si Drakkar genere assez.
2. **Mycelium en production.** "Ton fournisseur a un probleme. 3 autres PME l'ont signale cette semaine." "Les entreprises de ta taille dans ton secteur paient en 42 jours. Toi, 67." Intelligence collective inter-entreprises.
3. **Spider Score.** Premiere metrique proprietaire. Score de maturite operationnelle. Si un jour un fonds PE demande "Quel est leur Spider Score ?", c'est le debut de Phase 3 (Le Pouvoir).
4. **Expansion geographique.** France d'abord (Normandie -> Ile-de-France -> national). Puis Belgique/Suisse romande (marches francophones similaires).
5. **Revenue/employee cible.** 150-250K EUR/personne (avec IA). Compare : Palantir $1.01M, ESN francaises 100-150K EUR. Spider doit etre au-dessus des ESN pour prouver que ce n'est pas une ESN.

### Risques H2 2027-2028

- **Le race-to-bottom.** L'IA continue de compresser les couts. Ce que Spider vend 500 EUR aujourd'hui, un freelance le fait pour 100 EUR en 2028. Reponse : l'ontologie accumulee + le Mycelium + la relation de confiance.
- **Un GAFAM descend.** Microsoft lance un "Copilot for Small Business" a 30 EUR/mois. Google lance un "Gemini Business Agent." Reponse : ils ne connaitront jamais le metier d'une agence de pub normande. Le generique ne bat pas le specifique sur le segment PME. Mais c'est un pari.
- **La reglementation AI Act.** L'EU AI Act entre en vigueur progressivement. Des contraintes de transparence, d'explicabilite, de supervision humaine. Reponse : Spider a le human-in-the-loop par design (FDC/FDE). C'est un avantage, pas un obstacle.
- **Le modele ne scale pas.** Le ratio FDE:clients reste a 1:10. Spider vaut 1-3x revenue (ESN). Pas 10-20x (SaaS). L'empire ne se construit pas. Reponse : pivoter vers un modele plateforme pur (vendre l'ontologie aux integrateurs, pas le service aux clients).

---

## SYNTHESE -- OU SPIDER GAGNE

### Le vide que personne ne remplit

| Besoin du dirigeant PME | Orchestrateurs IA | AI Employees | Workflow Auto | ERP | ESN | **Spider** |
|------------------------|-------------------|--------------|---------------|-----|-----|------------|
| "Occupe-toi de mes campagnes" | Non | Non | Non | Non | Oui (cher) | **Oui (500 EUR)** |
| "Dis-moi ce qui ne va pas" | Non | Partiellement | Non | Dashboards basiques | Oui (rapport 3 mois) | **Oui (temps reel)** |
| "Fais-le pour moi" | Non | Partiellement (1 fonction) | Non (DIY) | Non | Oui (TJM) | **Oui (agents)** |
| "Ne me demande rien" | Non | Non | Non | Non | Non | **Oui (Shogunat)** |
| "Je ne sais pas ce que j'ai besoin" | Non | Non | Non | Non | Partiellement | **Oui (diagnostic)** |

### Les 3 differenciateurs reels

1. **Managed, pas self-service.** Spider fait le travail. Le dirigeant valide. "Oui." C'est tout.
2. **Profondeur metier, pas generique.** Spider sait que chez Jordan, la commission Cadres Blancs est a 13% et JCDecaux a 15%. Dust ne le saura jamais.
3. **Data captive cumulative.** Chaque jour de fonctionnement = plus de tacite dans Spider. Chaque client = plus de patterns. Chaque trimestre = moat plus profond.

### Ce qui peut tuer Spider

1. Un concurrent qui fait exactement la meme chose avec plus d'argent (ex: integrateur Odoo avec $5M de VC)
2. L'IA qui progresse tellement vite que le "managed" n'a plus de valeur (le dirigeant peut tout faire seul avec un agent generique)
3. L'equipe qui n'execute pas (Nathan est le goulot d'etranglement : vision + produit + sales + tech)
4. Le marche qui ne bouge pas (les 80% restent a 80% pendant 3 ans de plus)

Honnetement : le risque #3 est le plus probable. Tout repose sur Nathan. C'est a la fois la force et la fragilite.

---

> **Ce document est un instantane au 19 fevrier 2026.** Le paysage bougera. Les concurrents apparaitront. Les predictions seront fausses. Ce qui ne changera pas : le vide au milieu. Personne ne fait le travail de terrain pour les PME avec une couverture metier complete et des recommandations actionnables. Tant que ce vide existe, Spider a sa place.
>
> La question n'est pas "le vide existera-t-il encore dans 24 mois ?" (oui). C'est "Spider sera-t-il installe avant que quelqu'un d'autre ne le remplisse ?"

---

*Document genere le 19 fevrier 2026. Cartographie concurrentielle + roadmap de positionnement. Tout est la. Les concurrents et les menaces. Brut.*
