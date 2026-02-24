# SPIDER — SYNTHESE DEFINITIVE

> 21 fevrier 2026
> Ce document remplace et integre : THESE-SPIDER-FINALE, TAKE-MARCHE, PENSEE-BRUTE, STRATEGIE-COMPLETE, ANALYSE-JORDAN-STRATEGIQUE, et les reponses de Nathan aux 11 questions.
> C'est le document de reference.

---

# CE QU'EST SPIDER

## En une phrase

Spider est un clone IA de Drakkar — un Thierry (expert industrie + management), un Nathan (tech + strategie business), un Jean (finances + operations), et une equipe dev/design — accessible a n'importe quelle PME pour 0.5% de son CA.

## Le probleme

Un dirigeant de PME physique (artisan, industriel, commercant, agence) qui veut transformer ses operations a aujourd'hui 3 options :
- **ERP (Odoo) :** 10K+ d'implementation, pas flexible, grosse montee en competence
- **Dev sur-mesure :** 50-100K€, exactement ce qu'il veut mais hors de prix
- **No-code (Bubble) :** 15-20K€, moins cher mais plafond de verre

**Les 3 options coutent entre 10K et 100K€. Et dans les 3 cas, le dirigeant doit UTILISER l'outil lui-meme.**

## La solution

Spider fusionne les 3 options en une seule. Pour 0.5% du CA (soit ~400€/mois pour une boite a 1M), Spider :
1. Se connecte a tous les outils du client (Pennylane, Gmail, banque, CRM, outils metier)
2. Comprend le business en profondeur (donnees × process × tacite × relationnel)
3. FAIT le travail (relances, planification, reporting, marketing operationnel, alertes)
4. S'ameliore chaque mois (apprentissage continu sur les patterns du client et du vertical)

Le client ne configure rien. Le client ne gere rien. Le client voit son business tel qu'il est reellement — et Spider fait ce qui doit etre fait.

---

# LA THESE MARCHE

## Ce qui se passe dans le monde

**L'IA automatise le travail cognitif. Son cout tend vers zero.**

Le travail de saisie, de relance, de reporting, de planification — tout ce qui est "prendre une information ici et la mettre la" — sera gratuit d'ici 18-24 mois. Gemini, Copilot, Claude le feront dans les outils natifs.

**Consequence : la valeur migre vers l'economie physique.**

Si le cognitif est gratuit, les marges des boites physiques EXPLOSENT. Un plombier qui payait 2 500€/mois d'assistante pour ses devis/factures/relances n'a plus ce cout. Sa marge passe de 10% a 20%. Ces PME physiques deviennent des actifs d'investissement massivement sous-evalues.

**Consequence de la consequence : les fonds vont racheter massivement des PME physiques.**

L'arbitrage est evident : racheter une PME a 3x EBITDA, deployer l'IA, doubler la marge, revendre a 6-8x le nouvel EBITDA. Gil investit deja $500M dans les AI roll-ups de cabinets comptables US. C'est le debut d'une vague qui touchera TOUTE l'economie physique.

## Le marche en 3 couches

| Couche | Ce qui se passe | Qui gagne | Spider ? |
|--------|----------------|-----------|----------|
| **Execution** (faire des taches) | Commoditise, gratuit d'ici 2028 | Personne (integre dans les OS) | NON — pas ici |
| **Orchestration** (coordonner des taches) | Semi-commoditise | Quelques plateformes (Zapier, MCP) | NON — pas ici |
| **Comprehension** (comprendre un business) | PAS commoditise, RESISTE | Ceux qui vivent avec le client | **OUI — Spider est la** |

Spider joue UNIQUEMENT la couche comprehension. C'est la seule couche que les Big Tech ne peuvent pas reproduire — parce qu'elle necessite du contexte accumule, du tacite, de l'intelligence relationnelle, et du temps passe dans les operations reelles.

## Le timing

Perez dit qu'on est en pleine FRENZY (pas au Turning Point). Le crash IA viendra vers 2028-2031. 80% des startups IA mourront. Celles qui survivent seront celles qui ont du cash, des clients reels, et des donnees captives.

Le marche PME sera LENT (2-3 ans, pas 12 mois). Tire par les intermediaires de confiance (comptables, CCI), pas par les PME elles-memes.

Spider doit SURVIVRE la Frenzy (etre profitable, pas bruler du cash) et ETRE EN PLACE pour le Deployment Period (quand la vague de rachats de PME physiques explose).

---

# LE PRODUIT

## L'entree : le diagnostic (2 portes)

Page d'accueil Spider. Deux boutons.

**"Decouvrez ce que vous ne voyez pas dans votre entreprise."**

### Porte gauche : "Je me diagnostique"

- Le dirigeant connecte ses outils (Pennylane, Gmail) via OAuth
- Spider ingere en 24h
- Rapport automatique : 3 indicateurs cles que le dirigeant ne connaissait pas
  - % d'impayes reel
  - Tresorerie previsionnelle a 6 mois
  - Clients a risque (frequence de contact en baisse, ton des emails change)
- Gratuit ou 99€
- Objectif : "wow moment" → conversion vers abonnement ou vers diagnostic humain

### Porte droite : "Un expert le fait pour moi"

- Call de 60 minutes avec un humain Spider (Nathan / Thierry / FDE)
- Speech-to-process : pendant le call, Spider cartographie le business automatiquement (Claude Code + MCP branches a Spider, playbook de questions)
- Rapport complet + plan de transformation + prototype fonctionnel en 2 semaines
- 1 990€
- Objectif : transformation complete → abonnement

### La mecanique cachee

Les deux portes menent au meme endroit : l'abonnement Spider. Mais elles qualifient le client :
- Porte gauche = volume (beaucoup essaient, certains convertissent). Funnel self-service.
- Porte droite = premium (peu essaient, quasi-tous convertissent). Funnel high-touch.

Et la porte gauche est le cheval de Troie : Spider a DEJA ingere toutes les donnees du client avant meme de lui parler. Le diagnostic auto capture Pennylane + Gmail = Spider connait le CA, les impayes, les clients, les relations. Le pricing (0.5% du CA) est calcule en back-office sans que le client ait a donner quoi que ce soit.

## L'abonnement : le clone Drakkar

### Ce que Spider fait chaque mois

**Volet Jean (finances + operations) :**
- Suivi des impayes et relances automatiques (brouillons valides par le dirigeant, puis autonomie progressive)
- Previsionnel de tresorerie actualise en temps reel
- Alertes anomalies (facture inhabituelle, cout qui derive, fournisseur qui augmente)
- Rapprochement bancaire intelligent

**Volet Thierry (industrie + management) :**
- Cartographie des process operationnels (mise a jour continue)
- Detection des goulots d'etranglement
- Suivi de la charge / staffing
- Alertes RH (employe clé qui dessengage, risque de depart)

**Volet Nathan (tech + strategie) :**
- Intelligence relationnelle (quels clients refroidissent, quels prospects sont chauds)
- Benchmarks vs le secteur (quand Spider a assez de clients dans le meme vertical)
- Suggestions strategiques (reallocation de ressources, marges cachees, opportunites)
- Auto-amelioration des agents (chaque mois, les agents sont meilleurs)

### Le modele de qualite

Inspire de Claude / Lovable :
- **Phase brouillon :** Spider prepare les actions (relances, mails, rapports) mais n'envoie rien. Le dirigeant valide.
- **Phase autonomie :** Quand le dirigeant a confiance (apres 1-3 mois), il donne le feu vert sur certaines categories. Les relances < 500€ partent en auto. Les relances > 500€ restent en brouillon.
- **Abonnement par palier d'actions :** Un abo de base couvre N actions/mois. Au-dela, option de monter en plan. Pas de pricing a l'action (usine a gaz). Des paliers simples.

### L'upsell organique

Le dirigeant entre pour UN probleme (les impayes, la saisie, la tresorerie). Spider resout le probleme. Puis Spider DETECTE le probleme suivant :

- Mois 1 : relances (500€/mois)
- Mois 3 : "vos devis prennent 3h chacun, on peut automatiser" → +300€
- Mois 5 : "vos clients n'ont pas ete contactes depuis 4 mois, on peut relancer" → +400€
- Mois 8 : "votre compta est en retard de 2 mois, on peut pre-traiter" → +300€
- Mois 12 : le client paie 1 500-3 000€/mois. Spider fait TOUT le back-office.

L'upsell n'est pas vendu par un commercial. L'upsell est DEMANDE par le client. Parce que le systeme detecte les problemes et les presente au dirigeant : "voici ce qui brule, voici ce que ca coute, voici ce qu'on peut faire."

C'est le NDR 139% de Palantir a l'echelle PME.

---

# LE PRICING

## Le mecanisme

**0.5% du CA mensuel.** Calcule par Spider a partir des donnees Pennylane. Presente au client comme un forfait fixe (pas "0.5% de votre CA" — juste "votre abonnement est de 416€/mois").

| CA annuel client | Abonnement mensuel | Equivalent |
|-----------------|-------------------|------------|
| 200K€ | 83€ | Plancher a definir (minimum 200-300€ ?) |
| 500K€ | 208€ | |
| 1M€ | 416€ | Cas Jordan |
| 2M€ | 833€ | |
| 5M€ | 2 083€ | |
| 10M€ | 4 166€ | Plafond a definir ? |

### Pourquoi ca marche

- **Indolore :** 0.5% du CA est imperceptible. Aucun patron ne sent passer 0.5%.
- **Auto-scale :** Quand le CA monte (GRACE a Spider), le prix monte. Spider capture la valeur qu'il cree.
- **Aligne :** Si le client va mal, Spider gagne moins. Incentives alignees.
- **Pas affiche :** Le client ne voit pas "0.5% du CA." Il voit un forfait. Spider calcule en back-office via Pennylane.

### Le diagnostic auto fixe le prix

C'est la beaute du modele : le diagnostic auto (porte gauche) ingere les donnees Pennylane. Spider CONNAIT le CA du client avant meme de lui parler. Le prix est calcule automatiquement. Le client recoit une proposition personnalisee : "Votre abonnement Spider : 416€/mois."

Pas de negociation. Pas de grille tarifaire. Pas de "combien vous faites de CA ?" Juste : "voici votre prix."

---

# LE MOAT

## La formule

> **Moat = (Data × Process × Tacite × Relationnel) ^ Deploiements**

### Pourquoi chaque terme compte

**Data seule** = commodity (Pennylane l'a, Google l'a)

**Process seul** = copiable (Zapier le fait, Make le fait)

**Tacite seul** = du consulting (McKinsey le fait, cher et lent)

**Relationnel seul** = du CRM (folk, Attio, tout le monde)

**Le croisement des 4** = Spider. Personne d'autre ne croise les donnees financieres reelles (Pennylane) avec les process operationnels (observes par les agents) avec le tacite (capture par le speech-to-process et les corrections du dirigeant) avec l'intelligence relationnelle (ton des emails, frequence des appels, patterns de paiement).

**L'exposant "deploiements"** = le flywheel. Chaque deploiement enrichit les 4 couches pour TOUS les futurs deploiements du meme vertical.

## Les 7 Powers (Helmer) — avec les reponses de Nathan

| Power | Aujourd'hui | A 50 clients | A 500 clients |
|-------|------------|-------------|--------------|
| **Scale Economies** | ABSENT | MOYEN (templates verticaux, cout marginal baisse) | FORT (deploiement 501 coute presque rien) |
| **Network Effects** | ABSENT | NAISSANT (benchmarks cross-clients par vertical) | FORT (oracle predictif, le systeme sait ce qui va arriver) |
| **Counter-Positioning** | **FORT** — ERP a 10-100K ne peut pas descendre a 0.5% du CA sans mourir. Integrateurs a 15-50K ne peuvent pas. Freelances ne font pas du continu. | **FORT** | **FORT** |
| **Switching Costs** | ABSENT | FORT (multi-modules, toutes les operations passent par Spider) | **EXTREME** (arreter Spider = chaos operationnel total) |
| **Branding** | ABSENT | NAISSANT ("tout automatise pour 0.5% du CA") | FORT (Spider = categorie) |
| **Cornered Resource** | MOYEN (Nathan seul) | FORT (equipe de FDE clones de Nathan/Thierry/Jean) | FORT (l'equipe + les templates + le process) |
| **Process Power** | ABSENT | MOYEN (le process 14 jours s'ameliore) | **EXTREME** (500 iterations, impossible a reverse-engineer) |

**Le Counter-Positioning est le seul Power DEJA fort a jour 0.** Les alternatives coutent 10-100K€ de setup. Spider coute 0.5% du CA. Aucun incumbent ne peut s'aligner sans detruire son modele.

## Le Domain Context Lock (8eme Power)

Au-dela des 7 Powers de Helmer, Spider construit un avantage que j'appelle le **Domain Context Lock** :

La comprehension contextuelle accumulee par Spider chez un client (les patterns de paiement, les relations qui refroidissent, les exceptions metier, les habitudes non-ecrites) n'existe NULLE PART ailleurs. Pas dans Pennylane (qui a les chiffres mais pas le contexte). Pas dans Gmail (qui a les emails mais pas les liens avec les factures). Pas dans la tete du dirigeant (qui a oublie la moitie).

Arreter Spider = perdre cette comprehension. C'est comme licencier un employe de 10 ans — on perd tout ce qu'il savait et que personne d'autre ne sait.

Et la comprehension relationnelle (le ton des emails, les signaux faibles de desengagement client, les patterns de negociation) est la DERNIERE chose que l'IA generique ne capturera pas — parce qu'elle necessite des mois d'observation continue dans le contexte specifique de CE business.

---

# LA TRAJECTOIRE

## Acte 1 : Le transformateur (2026-2028)

**Ce que Spider fait :** Transforme des PME physiques une par une. Deploiement 14 jours (porte droite) ou self-service + conversion (porte gauche). Clone de Drakkar accessible pour 0.5% du CA.

**Qui paie :**
- Phase 0 (mois 1-3) : Jordan + Drakkar (dogfooding en parallele) + 2-3 clients reseau Nathan
- Phase 1 (mois 3-6) : 10-15 clients via reseau + porte gauche (auto-diagnostic)
- Phase 2 (mois 6-12) : 20-30 clients, premiers repreneurs/fonds qui decouvrent Spider

**Revenue cible :**
- Mois 3 : 5 clients × 400€ = 2K MRR
- Mois 6 : 15 clients × 600€ (upsell) = 9K MRR
- Mois 12 : 30 clients × 1 000€ (upsell mature) = 30K MRR = 360K ARR

**Le speech-to-process est LE produit :**
- Phase 1 : sur base d'un echange (call ou partage d'ecran), Spider genere automatiquement la cartographie + proposition de transformation. Claude Code + MCP branches a Spider. Playbook de questions.
- Phase 2 : le client le fait SEUL, guide par Spider. Zero humain dans la boucle pour le diagnostic de base.

**Contrainte tresorerie :** 5-6 mois. Spider DOIT generer du cash d'ici mois 3. Le consulting IA en parallele (missions Drakkar repositionnees "transformation IA") finance la transition. Chaque mission consulting est AUSSI un deploiement Spider (dogfooding + data + template).

## Acte 2 : L'oracle (2028-2031)

**Ce que Spider fait :** Avec 200+ clients transformes, Spider voit des patterns invisibles. Spider PREDIT ce qui va se passer dans une PME.

**Nouveaux produits :**
- Spider Score (sante operationnelle, vendu aux fonds/banques)
- Spider Benchmark (comparaison anonymisee intra-vertical)
- Spider Predict (prevision tresorerie, risques clients, opportunites)

**Le network effect emerge :** Plus de clients = meilleurs predictions = plus de clients. Le flywheel tourne.

## Acte 3 : Le createur de jeux (2031+)

Nathan ne vend plus Spider. Nathan UTILISE Spider.

**Option A : Outil pour les fonds.** Spider devient la plateforme de due diligence et de transformation pour les fonds de PE qui rachetent des PME. "Voici les 50 PME les plus transformables de votre secteur. Voici comment les transformer. Voici combien ca va rapporter." Pricing : 50-200K€ par acquisition accompagnee.

**Option B : Le fonds Spider.** Nathan rachete lui-meme les PME les plus transformables. Avantage informationnel insurmontable : Spider CONNAIT les boites de l'interieur. Nathan rachete a 3x EBITDA, transforme en 14 jours, marge ×2, valeur ×2-4.

**Option C : Les deux.** Service-as-Software pour les fonds + acquisitions propres. Nathan joue aux deux jeux a la fois. C'est le "nouveau jeu" qu'il veut creer.

---

# CE QUE NATHAN FAIT MAINTENANT

**Cette semaine (21-27 fevrier) :**

1. **Construire le proto Jordan SUR la plateforme SpiderOS** (pas un script jetable). Remy dans la boucle des ce week-end. Objectif : vendredi 27, 11h, montrer a Jordan un systeme fonctionnel qui fait au minimum la relance d'impayes + visibilite tresorerie.

2. **Documenter le process** de deploiement Jordan etape par etape (le call, le mapping, la configuration, les agents). Ce document devient le playbook FDE que Christian ou un recrute utilisera pour le deploiement #6.

3. **Identifier le client #2** qui n'est PAS un ami. Un repreneur, un contact CCI, un prospect froid. Le test de la these avec un inconnu.

**Mois 1-3 :**

4. **Deployer chez Drakkar en parallele** (plan de charge, staffing, rentabilite projet). Le dogfooding qui resout le probleme Drakkar ET construit le produit Spider.

5. **Construire la porte gauche** (auto-diagnostic). Pipeline : OAuth Pennylane/Gmail via Nango → ingestion overnight Haiku 4.5 → rapport 3 indicateurs. Objectif : en ligne en mois 2.

6. **Faire 5-10 diagnostics** (mix auto + humain). Generer du cash (1 990€ chaque pour la porte droite) + des donnees + des templates verticaux.

**Pas de docs strategie supplementaires. Pas de brainstorm moat. Pas de recherche marche. DEPLOYER.**

---

# LA QUESTION DE THIEL — REPONDUE

**"Quelle verite importante peu de gens partagent avec toi ?"**

Les PME physiques europeennes sont les actifs les plus sous-evalues du monde. Parce que personne ne sait les transformer. Parce que la transformation operationnelle coutait 50-100K€ et 3 ans. L'IA compresse ca a 0.5% du CA et 14 jours. Le premier acteur qui sait faire cette transformation a l'echelle possede la cle de la plus grande reallocation de capital de la decennie — quand les fonds se mettront a racheter massivement ces PME.

Spider n'est pas un SaaS. Spider n'est pas un agent IA. Spider est la MACHINE DE TRANSFORMATION de l'economie physique europeenne. Et Nathan est le seul fondateur en Europe qui combine la comprehension des PME (5 ans de Drakkar), la maitrise technique (Claude Code + stack souveraine), et la vision strategique (M&A + fonds) pour le faire.

C'est le secret. C'est le moat. C'est le jeu.

---

*21 fevrier 2026. Le document definitif. Tout converge. Maintenant on execute.*
