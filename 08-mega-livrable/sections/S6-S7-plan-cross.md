# SECTION 6 : SPIDER -- LE PLAN

> Ma proposition strategique. Pas un document de consultation. Une decision.
> Chaque recommandation est adossee a un chiffre reel source de R1-R8.
> Ecrit le 19 fevrier 2026.

---

## 6.1 Business Model -- Ma recommandation

### Le prix d'entree : 490 EUR/mois

Je recommande 490 EUR/mois. Pas 500, pas 990, pas 49. Voici pourquoi.

**Pourquoi 490 et pas 500.** R3 identifie un seuil psychologique precis dans les PME francaises : en dessous de 500 EUR/mois (6 000 EUR/an), le CEO signe seul dans 95% des cas pour les entreprises de 10-30 salaries [R3, section 2, Price Thresholds]. A 500 EUR pile, on est sur la frontiere. A 490, on est en dessous. La difference de 10 EUR/mois (120 EUR/an) est negligeable en revenu mais decisive en vitesse de signature. Le cycle passe de "1-3 mois avec consultation DAF" a "1-3 semaines, decision solo."

**Pourquoi pas 990 comme dans SPIDER-FINAL.** Le document original propose 990 EUR/mois pour Jordan. C'est une erreur. A 990 EUR/mois (11 880 EUR/an), R3 montre qu'on entre dans la tranche "CEO + DAF, 1-2 meetings, budget discussion" [R3, section 2]. Jordan n'a pas de DAF -- ca passe. Mais pour les 20 prochains clients, chaque euro au-dessus de 500 ajoute de la friction. L'objectif Phase 0-1 n'est pas de maximiser l'ARPA -- c'est de maximiser la vitesse de signature pour accumuler de la data et valider H4 (transfert d'ontologie).

**Pourquoi pas 49 EUR (le BMAD mort).** Le modele per-seat a ete tue par le pivot Service-as-Software. A 49 EUR/user/mois avec 3 users (Jordan, Eline, Audrey), ca fait 147 EUR/mois. Impossible de financer un FDE + FDC a ce niveau. Le modele economique est mort-ne -- R5 montre qu'un client SMB coute 200-500 EUR de CAC minimum [R5, section 1.3]. A 147 EUR/mois et 4% de churn mensuel, le LTV est de 3 675 EUR. LTV:CAC de 7-18x en apparence, mais la marge brute est catastrophique si on inclut le temps humain.

### Architecture de revenus -- 4 couches

Je recommande 4 couches de revenue, sequencees dans le temps.

`[SCHEMA: "Architecture Revenue Spider -- 4 couches" -- Pyramide inversee. Couche 1 (bas, large, gris clair) : "FREEMIUM -- Spider People + Chatbot" avec label "Gratuit / 49 EUR/mois, generation de leads, capture de data". Couche 2 (milieu-bas, vert) : "OPERATIONS GEREES -- 490 EUR/mois par process" avec label "Coeur du revenue, 60-70% du CA". Couche 3 (milieu-haut, bleu) : "SETUP FEES -- 1 990 EUR one-time par process" avec label "Cash upfront, finance l'onboarding". Couche 4 (haut, petit, or) : "AGENTS SUPPLEMENTAIRES -- 190-490 EUR/mois chacun" avec label "Expansion, NDR >100%". Fleches verticales montrant le flux : "Freemium capture la data -> revele les problemes -> convertit en operation geree -> upsell en agents". A droite : "LTV client mature = 2 000-3 500 EUR/mois (4-7x entree)"]`

| Couche | Ce que c'est | Prix | Quand |
|--------|-------------|------|-------|
| **L1 : Freemium** | Spider People (CRM relationnel auto-rempli) + Spider Chatbot (LLM sur donnees business) | Gratuit avec limites / 49 EUR/mois full | Phase 2+ (mois 6-12) |
| **L2 : Operations gerees** | 1 process complet gere par Spider (ex: gestion de campagnes, relance impayes, suivi achats) | **490 EUR/mois** | Phase 0 (immediatement) |
| **L3 : Setup fees** | Diagnostic + formalisation des regles + connexion des sources + calibrage du premier agent | **1 990 EUR one-time** | Phase 0 (immediatement) |
| **L4 : Agents supplementaires** | Chaque nouveau process ajoute un agent : Relance, Achats, Contenu, Reporting | **190-490 EUR/mois par agent** | Phase 1+ (mois 3+) |

### Pourquoi 1 990 EUR de setup et pas 2-5K

Le document initial propose "2-5K EUR (a valider)" pour les setup fees. Je tranche : 1 990 EUR.

Calcul. Le diagnostic eclair coute environ 500 EUR en temps humain (1 demi-journee FDC + FDE). La connexion des sources via Nango prend 2-4h de FDE (~200 EUR). L'extraction LLM et la construction de l'ontologie initiale prennent une nuit d'IA (~30-50 EUR de compute). La formalisation des regles et le calibrage prennent 1-2 jours de FDE (~400-800 EUR). Cout total : 1 130-1 550 EUR. A 1 990 EUR, la marge sur le setup est de 28-43%. Acceptable.

Psychologie. En dessous de 2 000 EUR, pas de bon de commande dans 90% des PME [R3, section 2]. Un virement ou un paiement CB suffit. Au-dessus de 2 000 EUR, on entre dans le process "devis signe, bon de commande, validation" qui ajoute 1-3 semaines au cycle. La difference entre 1 990 et 2 500 n'est pas 510 EUR -- c'est 1-3 semaines de friction.

### Le contrat : engagement annuel avec porte de sortie

Je recommande un engagement annuel avec une clause de sortie a 90 jours. Voici pourquoi.

R5 montre que les contrats annuels reduisent le churn de 2-3x par rapport aux contrats mensuels [R5, section 4.2]. A 4% de churn mensuel (scenario de base), l'annualisation ramene le churn effectif a 1.5-2% mensuel. Sur 24 mois, la difference de LTV est de +40-60%.

Mais les PME francaises ont peur de l'engagement. R3 le dit : "Legal culture : French CEOs are used to reading contracts carefully. Engagement periods, data clauses, and exit conditions are scrutinized" [R3, section 2]. La porte de sortie a 90 jours donne le sentiment de liberte tout en garantissant 3 mois minimum de data captive. Apres 3 mois, si le systeme fonctionne, le cout de sortie est deja trop eleve (donnees accumulees, habitudes changees, agents dans le flux).

Remise annuelle : 10% pour paiement annuel upfront (490 x 12 = 5 880 -> 5 290 EUR, soit 441 EUR/mois). Cette remise est financee par l'amelioration du cash flow et la reduction du churn.

### La garantie premier mois

Je recommande une **garantie de remboursement sur le premier mois** : "Si apres 30 jours vous estimez que Spider n'a pas cree de valeur, on vous rembourse integralement." Pas d'essai gratuit. Le client paie d'emblee (490 EUR + 1 990 EUR de setup = 2 480 EUR au total). Mais il sait qu'il peut recuperer les 490 EUR du premier mois.

Pourquoi payer et pas gratuit ? Palantir offre le bootcamp gratuitement mais facture $250K pour le pilot. La difference : Palantir a $5.2B de cash. Spider a 100K EUR de Drakkar. Chaque euro compte. Le paiement filtre les curieux des serieux. Un dirigeant qui refuse de payer 490 EUR n'est pas un client -- c'est un touriste.

Pourquoi rembourser le premier mois et pas le setup ? Parce que le setup (1 990 EUR) couvre un travail reel deja effectue (diagnostic, connexion, formalisation). Le rembourser detruirait la marge du setup. En revanche, le premier mois de 490 EUR est un investissement dans la confiance. R4 montre que Gusto offrait des "aggressive pilot pricing (50-75% discount) in exchange for feedback access and case study rights" [R4, section 4]. La garantie remboursement est l'equivalent Spider.

---

## 6.2 ICP -- Les 50 premiers clients

### L'ICP primaire (clients 1-20)

Je recommande de cibler un profil ultra-specifique pour les 20 premiers clients. Pas "les PME francaises." Un profil.

| Critere | Valeur | Pourquoi |
|---------|--------|----------|
| Taille | **5-50 salaries** | En dessous de 5, le CA ne justifie pas 490 EUR/mois. Au-dessus de 50, le CODIR entre dans la boucle [R3, section 2]. |
| CA | **500K-10M EUR** | En dessous de 500K, 490 EUR/mois = 1% du CA = trop cher subjectivement. Au-dessus de 10M, les processus se complexifient au-dela de l'ontologie template. |
| Decideur | **CEO seul** (pas de DAF, pas de CODIR) | R3 : CEO signe seul pour <500 EUR/mois dans 95% des cas [R3, section 2]. |
| Digital existant | **Utilise deja Sheets + Notion ou Odoo + Pennylane** | Si les donnees n'existent pas numeriquement, Spider n'a rien a ingerer. Jordan a les 3 (Sheets, Notion, Pennylane). C'est le minimum. |
| Pain trigger | **Triple saisie, relances manuelles, perte de temps admin** | Le probleme doit etre ressenti quotidiennement, pas annuellement. |
| Vertical | **Agences (pub, com, immobilier, evenementiel), services B2B, commerce de gros** | Services = processus repetitifs automatisables + marge sur services manages elevee (Jordan : 86.5% marge Leicht, 100% Le Tablier). |
| Geo | **Normandie + IDF** | Reseau Drakkar = Normandie. Nathan = IDF via Drakkar Studio. La proximite physique est non-negociable en Phase 0 -- R4/Gusto : "personally onboard each company" [R4, pattern 3]. |

### Pourquoi cette ICP et pas une autre

**Le CEO decide seul = cycle rapide.** R3 montre que le cycle pour un produit a 500 EUR/mois avec decision CEO solo est de 1-3 semaines [R3, section 1]. Avec CODIR, ca passe a 1-3 mois. Spider n'a pas le luxe du temps -- il doit valider H1 (un dirigeant paie 490 EUR/mois) et H3 (un non-ami paie le prix) dans les 90 premiers jours.

**Deja digital = data exploitable.** Le 83.3% de PME qui utilisent Excel comme outil analytique principal [SPIDER-PALANTIR-BLUEPRINT, section 7] representent un probleme : il faut structurer les donnees avant de les analyser. Les PME qui utilisent deja Sheets + Notion ou Odoo + Pennylane ont des donnees semi-structurees. C'est la ou Spider cree de la valeur immediatement -- pas en numerisant du papier, mais en connectant du digital deconnecte.

**Services B2B = processus repetitifs.** Jordan montre le schema parfait : 726 lignes de campagnes, 9 etapes par campagne, 3 saisies par etape. C'est un processus repetitif, quantifiable, automatisable. Les PME industrielles (Decotec) ont des processus plus complexes, plus opaques, et des gouvernances plus lourdes. Decotec = 3 ans de Drakkar pour zero resultat.

### L'anti-ICP (a eviter absolument)

| Profil | Pourquoi on l'evite | Lecon de source |
|--------|---------------------|-----------------|
| **PME industrielle >50 salaries** | Governance lock (CODIR, DAF, DSI). Cycle 3-6+ mois. Complexite ontologique. | Decotec : 155 salaries, 3 ans de consulting, zero capture du tacite, rupture le 12 fev 2026. |
| **Startup tech <3 ans** | Ils construiront eux-memes. Un dev junior + n8n + ChatGPT replique le service en 2 semaines. | Nathan lui-meme dit "2h30 de travail pour le prototype Jordan" -- les startups tech feront pareil. |
| **Micro-entreprise <3 salaries** | 490 EUR/mois = potentiellement 5-10% du CA. Trop cher. Churn previsible >7%/mois. | R5 : SMB churn 3-7% mensuel [R5, section 4.1]. Micro-entreprises = haut de la fourchette. |
| **PME sans aucun outil digital** | Pas de data a ingerer. Spider devrait commencer par numeriser avant d'automatiser. Double cout, double temps. | R3 : 25% des PME n'ont aucun budget digital [R3, section 6]. Ce n'est pas le marche de Spider. |
| **Franchise / multi-sites** | Decisions prises au siege, pas en local. Process de validation complexe meme pour <500 EUR. | Incompatible avec le "CEO signe seul" qui accelere le cycle. |

### Les 5 premiers clients concrets

Je recommande d'identifier des profils specifiques dans le reseau Drakkar et de Nathan.

| # | Type | Comment les trouver | Signal d'achat |
|---|------|---------------------|----------------|
| 1 | **Jordan / ComPrivee** | Deja identifie. Premier client. | Triple saisie sur 726 campagnes, 39.3% d'impayes. |
| 2-3 | **2 clients du reseau Drakkar** | Thierry et Jean identifient dans le portefeuille Drakkar des PME de 5-50 salaries avec des processus manuels visibles. | Le dirigeant se plaint des memes douleurs que Jordan. |
| 4-5 | **Clients des cabinets comptables proches de Drakkar** | Identifier 2-3 cabinets comptables partenaires de Drakkar en Normandie. Leur proposer un diagnostic gratuit pour leurs 3 meilleurs clients. | L'expert-comptable voit les erreurs de saisie, les retards de facturation, les impayes. |

---

## 6.3 GTM -- Canaux par ordre de priorite

### La hierarchie des canaux

Je ne recommande pas "tous les canaux en parallele." Je recommande un sequencement strict, chaque canal debloque par le succes du precedent.

`[SCHEMA: "GTM Sequencing Spider" -- Timeline horizontale avec 4 phases. Phase 0 (mois 0-3, vert) : "RESEAU" avec 2 barres -- "Drakkar warm intros" (CAC ~200 EUR) et "Nathan personal" (CAC ~0). Phase 1 (mois 3-6, bleu) : "EXPERT-COMPTABLE" avec 1 barre -- "3-5 cabinets partenaires" (CAC ~500 EUR via cabinet). Phase 2 (mois 6-12, orange) : "CONTENU + OUTBOUND" avec 3 barres -- "LinkedIn Nathan" (CAC ~800 EUR), "CCI/France Num" (CAC ~500 EUR), "Cold diagnostic cible" (CAC ~1 500 EUR). Phase 3 (mois 12+, rouge) : "PRODUCT-LED" avec 2 barres -- "Freemium conversion" (CAC ~300 EUR), "Referral NPS" (CAC ~150 EUR). Gate entre chaque phase : "N'activer la phase suivante QUE si la precedente produit des resultats." En dessous : "CAC blende cible : 800-1 500 EUR (en dessous du seuil R5 de 1 000-5 000 EUR pour l'ACV 6-24K)."]`

### Phase 0 (Mois 0-3) : Founder-led, reseau uniquement

**Canal 1 : Reseau Drakkar (warm intros)**
- CAC estime : ~200 EUR (temps Nathan/Thierry pour le diagnostic)
- Cycle : 1-2 semaines
- Volume : 3-5 clients
- Comment : Thierry et Jean identifient des clients Drakkar existants ou passes qui correspondent a l'ICP. Nathan fait le diagnostic eclair. Thierry gere la relation.
- Source R4 : "Gusto's founders cold called from a walk-in closet. Two out of ten converted. That 20% conversion rate was their first PMF signal." [R4, section 1.1] Spider commence par mieux que du cold call -- ce sont des warm intros dans un reseau ou la confiance est deja construite.

**Canal 2 : Reseau personnel Nathan**
- CAC estime : ~0 EUR
- Cycle : 1 semaine
- Volume : 1-2 clients (Jordan + potentiellement 1 autre)
- Limite : Ce canal s'epuise vite. Il ne faut PAS compter dessus au-dela du mois 2.

**Objectif Phase 0 :** 5 clients payants a 490 EUR/mois + setup. MRR = 2 450 EUR. Ce n'est pas un objectif de revenu -- c'est un objectif de validation. Chaque client est un test de H1, H3, H4.

**Lecon Gusto :** "1,000 customers in Year 1 with $0 in ad spend. The mechanism: NPS above 85 driving pure word of mouth." [R4, section 1.1] Spider ne doit pas depenser un euro en marketing avant d'avoir 10 clients satisfaits.

### Phase 1 (Mois 3-6) : Expert-comptable channel

**Canal 3 : 3-5 cabinets comptables partenaires**
- CAC estime : ~500 EUR via cabinet (temps Nathan/Thierry pour former le cabinet + diagnostic gratuit offert aux clients du cabinet)
- Cycle : 2-4 semaines (le cabinet recommande, le CEO signe)
- Volume cible : 5-10 clients via cette voie

**Pourquoi c'est LE canal pour la France.** R3 montre que l'expert-comptable est le canal de decouverte digitale qui croit le plus vite : +5 points en un an, 15% des PME le consultent pour le digital [R3, section 3]. R4 detaille le modele Pennylane : "one accounting firm serves 50-200 client companies. Winning one firm wins dozens of end users" [R4, section 1.3]. Et Silae : "75% of French accounting firms now use Silae. 840,000 companies processed" [R4, section 1.6] -- distribution exclusivement via cabinets comptables, sans jamais vendre directement aux PME.

**Comment l'executer concretement :**
1. Identifier 3-5 cabinets comptables en Normandie qui sont deja partenaires ou connaissances de Drakkar
2. Proposer au cabinet : "On offre un diagnostic Spider gratuit a vos 5 meilleurs clients PME. Vous, vous gagnez en valeur aupres de vos clients. Et pour chaque client qui signe, vous touchez 20% de la setup fee (398 EUR)."
3. Le cabinet recommande Spider a ses clients. Le CEO recoit la recommandation de son expert-comptable -- la source de confiance #1 pour un dirigeant PME francais.
4. Le diagnostic eclair est fait chez le client. Nathan ou FDE connecte les outils, montre le diagnostic, propose 490 EUR/mois.

**Le referral fee de 20%.** 20% de 1 990 EUR = 398 EUR par client. C'est suffisant pour motiver l'expert-comptable sans etre excessif. Pennylane utilise un modele similaire (le cabinet re-facture avec marge). Ce n'est pas une commission de vente -- c'est un "fee de recommandation" compatible avec l'ethique de l'Ordre des Experts-Comptables.

### Phase 2 (Mois 6-12) : Content + outbound cible

**N'activer cette phase QUE SI :** Phase 0 et 1 ont produit 10+ clients a NPS >70. Si le NPS est en dessous de 70, ne PAS investir en marketing -- corriger le produit d'abord [R4, pattern 4].

**Canal 4 : LinkedIn content (Nathan thought leader)**
- CAC estime : ~800 EUR (temps de creation de contenu + outils)
- Format : Nathan publie 3-5x/semaine sur LinkedIn. Pas du contenu generique "l'IA va transformer les PME." Du contenu specifique : "Voila comment on a detecte 285 factures impayees chez un client en 30 minutes." Avec les chiffres. Avec les screenshots (anonymises).
- Source R3 : "Best practice: CEO/founder personal posts outperform company page posts 5-10x in engagement" [R3, section 3, LinkedIn]
- Volume : Long terme (SEO LinkedIn). Objectif : 2-3 inbound leads par mois a partir du mois 8.

**Canal 5 : CCI / France Num**
- CAC estime : ~500 EUR (temps d'evenement + presentation)
- Format : Se positionner comme "Activateur France Num" en Normandie. Presenter Spider lors d'ateliers CCI. Pas vendre -- montrer. Le diagnostic eclair est parfait pour un format atelier.
- Source R3 : "Consular networks (CCI, CMA) = 13% of PME discovery channel" [R3, section 6]. Pas le canal le plus puissant, mais un canal de credibilite.
- Volume : 1-2 clients par trimestre via ce canal.

**Canal 6 : Cold diagnostic cible (outbound)**
- CAC estime : ~1 500 EUR (temps SDR + FDC/FDE pour diagnostic)
- Format : Identifier des PME qui utilisent Odoo ou Pennylane (visible via les integrations, les offres d'emploi, les posts LinkedIn). Contacter le CEO avec un message ultra-cible : "On a vu que vous utilisez Odoo + Pennylane. On a aide 10 PME similaires a eliminer la double saisie. Diagnostic gratuit de 30 minutes ?"
- Source R4 : "Rippling invested in programmatic outbound -- data-driven outbound campaigns" [R4, section 1.2]
- Volume : Faible en Phase 2. 2-3 clients par trimestre. Ce canal est un test pour la Phase 3.

### Phase 3 (Mois 12+) : Product-led growth

**N'activer cette phase QUE SI :** 20+ clients actifs, NPS >80, ratio FDE:clients en amelioration (H6 validee).

**Canal 7 : Spider People/Chatbot freemium -> conversion**
- CAC estime : ~300 EUR (cout d'acquisition du lead freemium + compute IA)
- Format : Spider People (CRM relationnel auto-rempli) et Spider Chatbot (LLM sur les donnees business) sont offerts gratuitement avec des limites d'usage. Le freemium capture les donnees du prospect. Le diagnostic automatique revele des problemes. L'assistant recommande un agent payant.
- C'est l'equivalent du bootcamp Palantir automatise [SPIDER-PALANTIR-BLUEPRINT, section 2, Phase 4]. Le cout par "diagnostic" passe de 500 EUR (humain) a quasi-zero (IA).
- Volume : Cible 5-10 conversions/mois a partir du mois 15.

**Canal 8 : Referral program (NPS-driven)**
- CAC estime : ~150 EUR (reward programme)
- Format : Un client satisfait recommande Spider a un pair. Le referrer recoit 1 mois gratuit. Le referee recoit la garantie premier mois gratuit (au lieu du remboursement, le mois est simplement offert).
- Source R4 : "Gusto -- NPS above 85 driving pure word of mouth. SMB owners talk to each other at trade associations, local chambers, industry meetups." [R4, section 2, pattern 4]
- Volume : 2-5 clients/mois a partir du mois 15. Ce canal devient le plus rentable a mesure que la base client grandit.

---

## 6.4 Sales Motion -- Le Diagnostic Eclair

### Le process en 5 etapes

Inspire du bootcamp Palantir mais compresse pour les PME. Le bootcamp Palantir dure 5 jours avec 5-8 personnes et coute $12-36K [SPIDER-PALANTIR-BLUEPRINT, section 1]. Le diagnostic Spider dure 1 demi-journee avec 2 personnes et coute ~500 EUR.

**Etape 1 : CONNECTER (a distance, 30 min)**

J-14 a J-1 avant le diagnostic. Nathan ou le FDE se connecte a distance aux outils du client via Nango. Sheets, Notion, Pennylane, Odoo -- whatever they use. Prend 15-30 minutes avec les identifiants du client. Le client ne fait rien sauf accepter les connexions OAuth.

Equivalent Palantir : "pre-travail FDE : ingestion donnees, squelette Ontologie" [SPIDER-PALANTIR-BLUEPRINT, section 8, semaines 1-2]. Palantir met 2-4 semaines. Spider met 30 minutes grace aux connecteurs Nango (300+ integrations) + LLM extraction.

**Etape 2 : ANALYSER (overnight, automatise)**

Spider extrait les entites, construit les claims, lance les premieres analyses. Chez Jordan, ca a produit : 726 lignes de campagnes, 73 clients uniques, 32 reseaux, 5-8 entity types, ~2 000 claims [cas Jordan]. L'extraction tourne sur Haiku 4.5 pour le volume et Sonnet 4.5 pour les elements complexes. Cout compute : 30-50 EUR.

Zero temps humain. Le systeme tourne la nuit. Au matin, le diagnostic est pret.

**Etape 3 : REVELER (en personne ou video, 1h30)**

C'est le pivot emotionnel. Equivalent Palantir : "Le Jour 1, quand le client voit ses propres spreadsheets transformes en systeme structure et navigable, c'est le pivot emotionnel" [SPIDER-PALANTIR-BLUEPRINT, section 2, Phase 1].

Thierry (FDC) mene la premiere partie (process mapping, 45 min). Il parle le langage du dirigeant. Il ne parle pas tech. Il demande : "Montrez-moi comment vous faites une facture de A a Z." Il observe les contournements, les tableurs caches, les "oui mais en vrai on fait ca."

Nathan montre le diagnostic Spider (45 min). Les LiveViews sur les donnees du client. Concretement chez Jordan :
- "39.3% de vos factures sont impayees. Voici les 285 lignes. Voici les 10 clients qui doivent le plus."
- "Votre fournisseur Publitex concentre 100% de votre impression -- 173 jobs. Bus factor = 1. S'il tombe, vous etes bloque."
- "Votre pic de septembre (125 campagnes) est 11x votre creux de decembre (11). Vous avez le meme effectif pour les deux."
- "Votre marge moyenne est de 27.2%, mais elle varie de 14.7% (Caen Evenements) a 100% (Le Tablier). Vous savez lesquels de vos clients sont rentables ?"

Chaque chiffre est une revelation. Chaque revelation est un probleme identifie. Chaque probleme est un agent potentiel.

**Etape 4 : PROPOSER (fin de la reunion)**

Pas 3 jours plus tard. Pas dans un mail de follow-up. A la fin de la reunion, Nathan dit :

"On prend en charge ce process pour 490 EUR par mois. Setup : 1 990 EUR, ca couvre le diagnostic qu'on vient de faire, la connexion des sources, et le calibrage du premier agent. Premier mois : si apres 30 jours ca ne vaut pas le coup, on vous rembourse les 490."

Pourquoi en fin de reunion ? Parce que R3 montre que le concurrent #1 est "on va voir / on y reflechit" -- la non-decision [R3, section 4, objection 7]. Plus le temps passe entre la revelation et la proposition, plus le CEO rationalise l'inaction. Le pivot emotionnel (les 39.3% d'impayes) se refroidit.

**Etape 5 : DELIVRER (semaines 1-4)**

Le FDC + FDE installent le premier process automatise. Chez Jordan : elimination de la triple saisie Sheets -> Notion -> Pennylane. Le plan media dans Sheets alimente automatiquement Notion et Pennylane. Alertes auto J-28 pour les creatifs. Base tarifaire centralisee.

Semaine 1-2 : setup technique + calibrage. Semaine 3 : test sur 5-10 campagnes reelles. Semaine 4 : bilan et decision de renouvellement (Gate G1).

### Conversion cible : 40-50%

Palantir convertit a ~22% apres un bootcamp de 5 jours [SPIDER-PALANTIR-BLUEPRINT, section 1]. Spider vise 40-50%. Pourquoi plus haut ?

1. **Le ticket est 500x plus bas.** $250K vs 490 EUR/mois. La decision a 490 EUR/mois est une depense operationnelle, pas un investissement strategique.
2. **Les leads sont warm.** En Phase 0-1, 100% des diagnostics sont faits via le reseau Drakkar ou Nathan. Ce n'est pas du cold outreach.
3. **Le CEO decide seul.** Pas de procurement committee, pas de budget cycle, pas de DAF a convaincre [R3, section 2].
4. **La garantie premier mois** elimine le risque percu.

Si la conversion descend en dessous de 30% sur les diagnostics warm, c'est un signal d'alarme sur la proposition de valeur.

---

## 6.5 Unit Economics -- Modele financier 3 scenarios

### Les hypotheses de calcul

Toutes les hypotheses sont sourcees. Chaque scenario est calcule, pas estime.

**Hypotheses communes aux 3 scenarios :**
- Entry ARPA : 490 EUR/mois (recommandation section 6.1)
- Setup fee : 1 990 EUR (one-time, mois 1)
- AI compute cost : 50 EUR/client/mois [SPIDER-FINAL, section 4, unit economics target]
- Normandie salary discount : -20-25% vs Paris [R5, section 5.2]

**Hypotheses variables :**

| Parametre | Pessimiste | Base | Optimiste | Source |
|-----------|-----------|------|-----------|--------|
| Expansion mensuelle (upsell) | +0 EUR/mois (aucun upsell) | +100 EUR/mois apres 6 mois (1 agent) | +200 EUR/mois apres 4 mois (2 agents) | SPIDER-PALANTIR-BLUEPRINT : Jordan a 4 process d'expansion identifies |
| Churn mensuel | 6% | 3.5% | 2% | R5 : SMB sans CS = 3-7% ; avec CS = 2-3.5% ; annuel = /2-3x [R5, sections 4.1-4.2] |
| CAC blende | 2 500 EUR | 1 200 EUR | 600 EUR | R5 : SMB SaaS CAC 200-2 000 EUR ; referral 150 EUR [R5, section 1.2] ; Phase 0 = reseau, donc bas |
| Cout FDE/FDC par client/mois | 350 EUR (ratio 1:5) | 200 EUR (ratio 1:8) | 120 EUR (ratio 1:12) | R5 : equipe 6 pers = 516K/an = 43K/mois ; /8 clients = 5 375 EUR = ~200 EUR de FDE alloue par client si 60% du temps est client-facing |
| Marge brute | -- | -- | -- | Calculee ci-dessous |

### Calcul du scenario pessimiste

**Revenue par client :**
- Mois 1 : 490 EUR (MRR) + 1 990 EUR (setup) = 2 480 EUR
- Mois 2-fin : 490 EUR/mois (aucun upsell)
- Duree de vie moyenne : 1 / 0.06 = 16.7 mois
- Revenue total sur duree de vie : 1 990 + (490 x 16.7) = 1 990 + 8 183 = **10 173 EUR**

**Couts par client :**
- AI compute : 50 x 16.7 = 835 EUR
- FDE/FDC : 350 x 16.7 = 5 845 EUR
- Total COGS : 6 680 EUR

**Metriques :**
- LTV (net de COGS) : 10 173 - 6 680 = **3 493 EUR**
- Marge brute : (10 173 - 6 680) / 10 173 = **34.3%**
- LTV:CAC : 3 493 / 2 500 = **1.4x**
- Payback : 2 500 / ((490 - 350 - 50) x 1) = 2 500 / 90 = **27.8 mois**

**Verdict pessimiste : non viable.** LTV:CAC de 1.4x est en dessous du minimum de 3:1 [R5, section 2.1]. Le payback de 28 mois est au-dela de tout seuil acceptable. Ce scenario se materialise si : zero upsell, churn a 6%, et ratio FDE bloque a 1:5. C'est le scenario "Spider est une ESN avec de l'IA." Il faut l'eviter a tout prix.

### Calcul du scenario de base

**Revenue par client :**
- Mois 1 : 490 + 1 990 = 2 480 EUR
- Mois 2-6 : 490/mois
- Mois 7+ : 590/mois (1 agent supplementaire a 100 EUR via upsell moyen)
- Duree de vie moyenne : 1 / 0.035 = 28.6 mois
- Revenue total : 1 990 + (490 x 6) + (590 x 22.6) = 1 990 + 2 940 + 13 334 = **18 264 EUR**

**Couts par client :**
- AI compute : 50 x 28.6 = 1 430 EUR
- FDE/FDC : 200 x 28.6 = 5 720 EUR
- Total COGS : 7 150 EUR

**Metriques :**
- LTV (net de COGS) : 18 264 - 7 150 = **11 114 EUR**
- Marge brute : (18 264 - 7 150) / 18 264 = **60.9%**
- LTV:CAC : 11 114 / 1 200 = **9.3x**
- Payback : 1 200 / ((490 - 200 - 50) x 1) = 1 200 / 240 = **5.0 mois**

**Verdict base : sain.** LTV:CAC de 9.3x est excellent (>5x = "excellent" selon R5 [R5, section 2.1]). Payback de 5 mois est dans la cible "high-performing SaaS" [R5, section 7.1]. Marge brute de 61% est dans la trajectoire Palantir Year 3-4 [R5, section 3.2]. Ce scenario se materialise si : 1 upsell moyen par client, churn controle a 3.5% avec CS basique, ratio FDE ameliore a 1:8.

### Calcul du scenario optimiste

**Revenue par client :**
- Mois 1 : 490 + 1 990 = 2 480 EUR
- Mois 2-4 : 490/mois
- Mois 5+ : 690/mois (2 agents supplementaires a 200 EUR)
- Duree de vie moyenne : 1 / 0.02 = 50 mois
- Revenue total : 1 990 + (490 x 4) + (690 x 46) = 1 990 + 1 960 + 31 740 = **35 690 EUR**

**Couts par client :**
- AI compute : 50 x 50 = 2 500 EUR
- FDE/FDC : 120 x 50 = 6 000 EUR
- Total COGS : 8 500 EUR

**Metriques :**
- LTV (net de COGS) : 35 690 - 8 500 = **27 190 EUR**
- Marge brute : (35 690 - 8 500) / 35 690 = **76.2%**
- LTV:CAC : 27 190 / 600 = **45.3x**
- Payback : 600 / ((490 - 120 - 50) x 1) = 600 / 320 = **1.9 mois**

**Verdict optimiste : exceptionnel.** Mais ne pas planifier dessus. Ce scenario suppose que H4 (transfert d'ontologie) et H6 (ratio FDE s'ameliore) sont pleinement valides, que le churn tombe a 2% (contrats annuels + NPS >80), et que les upsells arrivent naturellement. C'est la cible a 18-24 mois, pas le scenario de depart.

### Tableau de synthese

`[SCHEMA: "Unit Economics Spider -- 3 Scenarios" -- 3 colonnes (Pessimiste/Base/Optimiste) avec code couleur (rouge/vert/bleu). Lignes : Entry ARPA (490/490/490), Setup fee (1990/1990/1990), Expansion mensuelle (+0/+100/+200), Churn mensuel (6%/3.5%/2%), CAC blende (2500/1200/600), Cout FDE par client/mois (350/200/120), AI compute/mois (50/50/50), Marge brute (34%/61%/76%), LTV (3493/11114/27190), LTV:CAC (1.4x/9.3x/45.3x), Payback mois (27.8/5.0/1.9). Encadre rouge sous pessimiste : "NON VIABLE". Encadre vert sous base : "SAIN -- cible Year 1". Encadre bleu sous optimiste : "CIBLE Year 2-3".]`

| Metrique | Pessimiste | Base | Optimiste |
|----------|-----------|------|-----------|
| Entry ARPA | 490 EUR/mois | 490 EUR/mois | 490 EUR/mois |
| Setup fee | 1 990 EUR | 1 990 EUR | 1 990 EUR |
| Expansion mensuelle | +0 EUR (aucun upsell) | +100 EUR/mois (M7+) | +200 EUR/mois (M5+) |
| Churn mensuel | 6% | 3.5% | 2% |
| CAC blende | 2 500 EUR | 1 200 EUR | 600 EUR |
| Cout FDE/FDC par client/mois | 350 EUR | 200 EUR | 120 EUR |
| AI compute/client/mois | 50 EUR | 50 EUR | 50 EUR |
| **Marge brute** | **34.3%** | **60.9%** | **76.2%** |
| **LTV** | **3 493 EUR** | **11 114 EUR** | **27 190 EUR** |
| **LTV:CAC** | **1.4x** | **9.3x** | **45.3x** |
| **Payback** | **27.8 mois** | **5.0 mois** | **1.9 mois** |

### Les 3 leviers critiques

Le modele tient ou s'effondre sur 3 leviers. Par ordre d'importance :

**Levier 1 : Le ratio FDE:clients.** La difference entre 350 EUR/client/mois (ratio 1:5) et 120 EUR/client/mois (ratio 1:12) fait passer la marge brute de 34% a 76%. C'est la question existentielle du modele -- exactement ce que SPIDER-FINAL identifie : "si le ratio stagne, Spider est une ESN avec de l'IA" [SPIDER-FINAL, section VIII]. Palantir est passe de $700K/FDE par $1M ARR (2016) a $80-150K (2025) -- reduction de 5-9x en 9 ans [SPIDER-PALANTIR-BLUEPRINT, section 1]. Spider doit faire la meme compression en 2-3 ans grace a l'IA.

**Levier 2 : L'upsell (expansion revenue).** Sans upsell, le LTV:CAC est de 1.4x (mort). Avec 1 agent supplementaire, il passe a 9.3x (sain). L'upsell n'est pas optionnel -- c'est structurel. Chaque client doit ajouter au moins 1 agent dans les 6 premiers mois. Le mecanisme est automatique : Spider detecte les anomalies dans les donnees et propose les agents correspondants. Chez Jordan, 4 processus d'expansion sont deja identifies [SPIDER-PALANTIR-BLUEPRINT, section 2, Phase 3] : relance impayes, suivi BDC, contenu digital, reporting.

**Levier 3 : Le churn.** R5 montre que 43% des pertes SMB arrivent dans les 90 premiers jours [R5, section 4.1]. L'onboarding est LE moment. La solution : engagement annuel (churn /2-3x) + garantie premier mois (confiance) + livraison de valeur en semaine 1-2 (pas semaine 4). Si le churn depasse 5% mensuel apres 6 mois, pivoter immediatement [R5, section 8.3].

### Projection cashflow 12 mois (scenario de base)

Ce tableau projette le cashflow mois par mois en scenario de base, en supposant l'acquisition client conforme au plan GTM (Phase 0-1).

| Mois | Nouveaux clients | Clients actifs (post-churn 3.5%) | MRR (490 EUR + expansion) | Setup fees encaisses | Revenue total mensuel | Burn mensuel (equipe) | Cashflow net |
|------|-----------------|--------------------------------|---------------------------|---------------------|-----------------------|----------------------|-------------|
| 1 | 1 (Jordan) | 1 | 490 | 1 990 | 2 480 | 12 870 | -10 390 |
| 2 | 0 | 1 | 490 | 0 | 490 | 12 870 | -12 380 |
| 3 | 2 | 3 | 1 470 | 3 980 | 5 450 | 12 870 | -7 420 |
| 4 | 1 | 3.9 (~4) | 1 960 | 1 990 | 3 950 | 18 237 | -14 287 |
| 5 | 2 | 5.7 (~6) | 2 940 | 3 980 | 6 920 | 18 237 | -11 317 |
| 6 | 2 | 7.5 (~8) | 4 120 | 3 980 | 8 100 | 18 237 | -10 137 |
| 7 | 2 | 9.2 (~9) | 5 310 | 3 980 | 9 290 | 18 237 | -8 947 |
| 8 | 2 | 10.9 (~11) | 6 490 | 3 980 | 10 470 | 18 237 | -7 767 |
| 9 | 2 | 12.5 (~13) | 7 800 | 3 980 | 11 780 | 18 237 | -6 457 |
| 10 | 3 | 14.9 (~15) | 9 450 | 5 970 | 15 420 | 23 499 | -8 079 |
| 11 | 3 | 17.2 (~17) | 11 220 | 5 970 | 17 190 | 23 499 | -6 309 |
| 12 | 3 | 19.5 (~20) | 13 200 | 5 970 | 19 170 | 23 499 | -4 329 |

**Notes de calcul :**
- Mois 1-3 : equipe 3 personnes (fondateurs, 12 870 EUR/mois employeur)
- Mois 4-9 : equipe 4 personnes (+FDE #1, 18 237 EUR/mois)
- Mois 10-12 : equipe 5 personnes (+FDE #2, 23 499 EUR/mois)
- Expansion : +100 EUR/mois par client existant a partir de leur mois 7 (moyenne)
- Churn applique sur la base existante a 3.5%/mois
- Le commercial #1 n'est recrute que si M8 est valide (mois 12+)

**Cash total consomme sur 12 mois : ~108K EUR** (avant Drakkar revenue). Le financement de 100K EUR de Drakkar couvre la quasi-totalite de l'investissement. Le revenu Drakkar existant (~125K EUR/mois) couvre le delta.

**Point de breakeven mensuel :** Dans ce scenario, le breakeven mensuel (revenue >= burn) est atteint vers le mois 14-16. A 20 clients avec expansion, le MRR atteint ~15-18K EUR/mois, suffisant pour couvrir une equipe de 5-6 personnes.

---

## 6.6 Milestones et Kill Criteria

### Le calendrier des preuves

Chaque milestone est un test d'hypothese. Chaque kill signal est un seuil en dessous duquel la these est fausse.

| Milestone | Timing | Ce que ca prouve | Hypothese testee | Signal GO | Signal KILL |
|-----------|--------|-----------------|------------------|-----------|-------------|
| **M1** | Semaine 4 | Un dirigeant PME paie 490 EUR/mois pour des operations gerees | H1 | Jordan paie 490 EUR sans negotiation | Jordan refuse ou demande <300 EUR |
| **M2** | Mois 3 | Un non-ami paie le prix standard | H3 | 2+ clients non-amis a 490 EUR+ | 0 client non-ami |
| **M3** | Mois 4 | Le setup fee est accepte | -- | 3+ clients ont paye 1 990 EUR de setup sans negotiation | >50% des prospects refusent le setup fee |
| **M4** | Mois 6 | Le premier upsell se produit naturellement | H3 (expansion) | 1+ client ajoute un agent supplementaire (+190-490 EUR/mois) | Aucune demande d'expansion en 6 mois |
| **M5** | Mois 6 | L'ontologie se transfere | H4 | Temps d'onboarding client 5 < 60% du temps client 1 | Client 5 prend >80% du temps client 1 |
| **M6** | Mois 9 | Le modele economique fonctionne | H1+H3+H4 | 10 clients, churn <4%/mois, MRR 6K+ EUR | <7 clients ou churn >6% ou MRR <4K EUR |
| **M7** | Mois 12 | Le ratio FDE s'ameliore | H6 | 1 FDE gere 8+ clients (vs 5 au debut) | Ratio bloque a 1:5 |
| **M8** | Mois 12 | Scale path visible | -- | 20+ clients, 15K+ EUR MRR, marge brute >50% | <15 clients ou <10K EUR MRR ou marge <35% |
| **M9** | Mois 18 | PMF confirme | -- | 30+ clients, 30K+ EUR MRR, NPS >70, NDR >100% | <20 clients, NPS <50, NDR <90% |

### Les kill criteria absolus

**KILL LE PROJET SI :** Apres 6 mois (M6), zero client non-ami n'a paye >300 EUR/mois. La these est fausse.

**Conditions de kill detaillees :**

1. **Mois 3 : zero non-ami.** Si apres 90 jours, seul Jordan paie, le probleme n'est pas le produit -- c'est la proposition de valeur. Possibilite de pivot : tester un pricing different (149 EUR/mois ?) ou une ICP differente. Mais ne PAS continuer a investir en tech sans preuve de demande marche.

2. **Mois 6 : churn >6% mensuel.** Si plus d'1 client sur 16 part chaque mois, le produit ne retient pas. Possibilite de pivot : passer en mode "white-glove" (plus de FDC, moins d'IA) pour comprendre pourquoi ils partent.

3. **Mois 12 : ratio FDE bloque a 1:5.** Si le ratio ne s'ameliore pas malgre les ontologies templates, Spider est une ESN avec de l'IA. La marge brute sera de ~35%. La valorisation sera de 1-3x revenue. Ce n'est pas un echec absolu -- c'est un business viable mais pas un empire. Nathan doit decider si ca l'interesse.

4. **Mois 18 : NDR <90%.** Si les clients ne s'expandent pas (aucun upsell), le modele est un SaaS flat a 490 EUR/mois. Le LTV est trop faible pour justifier le CAC de la Phase 2-3 (outbound, content). Possibilite de pivot : augmenter le prix d'entree a 990 EUR/mois et cibler des PME plus grosses (30-100 salaries).

---

## 6.7 Hiring Plan

### Le sequencement precis

Je recommande un hiring plan sequentiel -- chaque recrutement conditionne par un milestone.

| Timing | Recrutement | Salaire brut | Cout employeur annuel | Condition d'embauche |
|--------|------------|-------------|----------------------|---------------------|
| **Mois 0** | Nathan (CEO/sales/produit) | 36 000 EUR | 51 480 EUR | -- (co-fondateur) |
| **Mois 0** | Remy (CTO) | 36 000 EUR | 51 480 EUR | -- (co-fondateur) |
| **Mois 0** | Thierry (FDC lead) | 36 000 EUR | 51 480 EUR | -- (via Drakkar) |
| **Mois 3** | **FDE #1** (dev mid-senior, Normandie) | 45 000-50 000 EUR | 64 350-71 500 EUR | M2 valide (2+ clients non-amis) |
| **Mois 6** | **FDE #2** (dev mid-senior, Normandie) | 45 000-50 000 EUR | 64 350-71 500 EUR | M6 valide (10 clients, churn <4%) |
| **Mois 9-12** | **Commercial #1** (sales, Normandie/IDF) | 40 000 EUR fixe + variable | 57 200 EUR fixe + variable | M8 valide (20+ clients, 15K+ MRR) |

**Cout total equipe a 6 personnes (mois 12) :**

| Poste | Nombre | Cout employeur annuel | Total |
|-------|--------|----------------------|-------|
| Fondateurs (reduit) | 3 | 51 480 EUR | 154 440 EUR |
| FDE (Normandie) | 2 | 67 925 EUR (moyenne) | 135 850 EUR |
| Commercial | 1 | 57 200 EUR (fixe) | 57 200 EUR |
| **Total salaires** | **6** | -- | **347 490 EUR** |
| +20% (outils, infra, bureau, deplacement) | -- | -- | 69 498 EUR |
| **Total burn annuel** | -- | -- | **416 988 EUR** |

R5 donne ~516K EUR pour 6 personnes [R5, section 5.4]. Mon estimation est inferieure (417K) parce que les 3 fondateurs sont a salaire reduit (36K brut vs 65K dans le modele R5) et les FDE sont recrutes en Normandie (45-50K vs 65K). L'arbitrage Normandie est un avantage concret : 20-25% d'economie sur chaque recrutement [R5, section 5.2].

### Profil du FDE #1 -- le recrutement critique

Ce recrutement est le plus important de l'annee 1. Le FDE #1 est la personne qui transforme le prototype Nathan en systeme reproductible.

| Critere | Requis | Souhaite |
|---------|--------|----------|
| Experience | 3-5 ans en dev backend (Python) | Experience ops/devops |
| Stack | Python, SQL, API REST | Connaissance LLM, Nango ou equivalent |
| Localisation | Normandie ou remote Normandie | Caen / Rouen |
| Soft skills | **Capable de parler a des non-techniques** | Experience client directe |
| Salaire | 45-50K brut | -- |
| Quand | Des que M2 valide (2+ clients non-amis) | -- |

Le profil "dev qui parle aux humains" est rare. R4 le dit pour Palantir : le FDE a une "unusual sensitivity to social context" [R4, section 4, via SPIDER-PALANTIR-BLUEPRINT]. Ce n'est pas un dev pur. C'est un dev qui peut s'asseoir a cote d'un dirigeant de PME et comprendre son probleme sans jargon.

### Ce qu'on ne recrute PAS en annee 1

- **Pas de marketing.** Le content marketing est fait par Nathan (LinkedIn). Pas besoin d'un "head of marketing" avant 20+ clients.
- **Pas de CS dedie.** Le FDC (Thierry) et les FDE font le CS en Phase 0-1. Un CS dedie n'est necessaire qu'a 30+ clients.
- **Pas de product manager.** Nathan est le PM. Un PM dedie est un luxe de Phase 3.
- **Pas de designer.** Le design system "The Lake" est deja defini. Les interfaces en Phase 0-1 sont internes. Un designer est necessaire quand Spider People/Chatbot deviennent publics (Phase 2+).

---

## 6.8 Ce que Nathan fait lundi matin

Pas de strategie sans action concrete. Voici les 5 actions de la semaine 1.

### Action 1 : Appeler Jordan. Fixer le prix.

**Quand :** Lundi matin, 9h.
**Quoi :** "Jordan, on lance. Le prix c'est 490 EUR par mois. Setup : 1 990 EUR, ca couvre le diagnostic et la mise en route. Premier mois garanti -- si ca vaut rien, on rembourse les 490."
**Pas de "prix d'ami."** Si Jordan negocie en dessous de 300 EUR, c'est un kill signal sur H1 [SPIDER-FINAL, section IX]. Si Jordan accepte a 490 sans broncher, c'est un signal fort. Si Jordan propose 400, c'est acceptable -- noter l'ecart et le tester avec le client 2.

### Action 2 : Connecter les 3 sources de Jordan

**Quand :** Lundi apres-midi (si Jordan accepte) ou mardi.
**Quoi :** Connecter Google Sheets (plans media), Notion (Pilotage 2025, 726 lignes, 35 champs), Pennylane (facturation) via Nango.
**Temps estime :** 30-45 minutes pour les connexions OAuth. Pas de dev custom -- Nango gere les 3.

### Action 3 : Lancer l'extraction LLM overnight

**Quand :** Mardi soir.
**Quoi :** Haiku 4.5 sur les 726 lignes de campagnes. Entity resolution : Campagne, Client, Reseau, Facture, BonDeCommande. Claims engine : conflits detectes. Construction de l'ontologie Jordan V1.
**Resultat attendu mercredi matin :** 5-8 entity types, ~2 000 claims, premiers conflits detectes (ex: factures marquees "payees" dans Notion mais pas dans Pennylane).

### Action 4 : Preparer le Diagnostic Eclair pour vendredi

**Quand :** Mercredi-jeudi.
**Quoi :** Nathan prepare les LiveViews sur les donnees Jordan. Thierry prepare le process mapping du workflow 9 etapes. L'objectif du diagnostic n'est pas de vendre -- c'est de montrer a Jordan ce que ses propres donnees disent de son entreprise.
**Livrables :** 5-10 insights data-driven prets a etre presentes. Les 39.3% d'impayes, le bus factor Publitex, la saisonnalite, la dispersion des marges.

### Action 5 : Identifier 3 cabinets comptables a approcher semaine 2

**Quand :** Vendredi apres le diagnostic Jordan.
**Quoi :** Thierry et Jean identifient 3 cabinets comptables en Normandie dans le reseau Drakkar. Premier contact la semaine suivante. Format : "On lance un nouveau service d'operations gerees par IA pour les PME. On offre un diagnostic gratuit a vos 3-5 meilleurs clients. Vous, vous gagnez en valeur aupres de vos clients."
**Pourquoi maintenant :** R3 montre que le canal expert-comptable est le canal qui croit le plus vite (+5 pts en un an) [R3, section 3]. Si on attend le mois 6 pour commencer, on perd 5 mois de construction de la relation.

---

# SECTION 7 : PALANTIR x SPIDER -- Le playbook traduit

> Compression du SPIDER-PALANTIR-BLUEPRINT (535 lignes) en 3 deliverables actionnables.

---

## 7.1 Table de mapping -- Les 20 concepts cles

Le mapping complet Palantir -> Spider contient 55+ lignes [SPIDER-PALANTIR-BLUEPRINT, Annexe]. Je retiens les 20 concepts qui comptent pour l'execution des 12 prochaines semaines.

| # | Concept Palantir | Ce que Palantir fait | Equivalent Spider | Ce que Spider fait | Statut |
|---|-----------------|---------------------|-------------------|-------------------|--------|
| 1 | **AIP Bootcamp** | 5 jours, 5-8 pers., gratuit, 22% conversion | **Diagnostic Eclair** | 1 demi-journee, 2 pers., gratuit, cible 40-50% | A lancer semaine 1 |
| 2 | **Pilot 90 jours** | $250K, 2-4 FDEs on-site, marge negative | **Phase 0** | 490 EUR/mois, 1 FDC + 1 FDE, 4 semaines | En cours (Jordan) |
| 3 | **Ontology** | Custom par client, $millions, 100-500+ Object Types | **Claims Engine** | Templates par vertical, 1 990 EUR setup, 5-15 entities | Architecture definie |
| 4 | **Object Types** | Entites typees (Client, Commande) | **Entities** | Entites resolvees avec aliases, type, canonical_name | A construire |
| 5 | **FDE ("Delta")** | Stanford/MIT, $200K+, code + politique | **FDE Spider** | Dev mid-senior Normandie, 45-50K EUR, code + terrain | A recruter (M3) |
| 6 | **Deployment Strategist ("Echo")** | Ex-McKinsey, gere la politique client | **FDC** | Ex-dirigeant industrie, construit la confiance | Thierry Menard |
| 7 | **Foundry** | OS enterprise, 150+ microservices | **SpiderOS** | Cloud-native EU (OVH+Scaleway, K8s) | En construction |
| 8 | **AIP** | Couche IA, LLMs sur objets types | **Spider Intelligence Engine** | Haiku 4.5 + Sonnet 4.5 + Dempster-Shafer | Architecture definie |
| 9 | **Apollo** | 360K deploiements/mois, <20 ingenieurs | **ArgoCD + GitOps** | 3 clusters K8s, CI/CD | Operationnel |
| 10 | **Workshop** | App builder low-code, 50+ widgets | **Platform app** | Hub, dashboard, 10 LiveViews | A construire |
| 11 | **NDR 139%** | Expand inter-departements | **NDR cible 130%** | Expand intra-process (agents supplementaires) | A prouver |
| 12 | **$100K -> $5.6M (56x)** | Expansion massive par client | **490 -> 2-3K EUR/mois (4-7x)** | Setup fees + agents supplementaires | A prouver |
| 13 | **Action Types** | Write-back operations | **Agents proactifs** | Agent Relance, Agent Campagnes, Agent Achats | Conceptualises |
| 14 | **Revenue/employee $1.01M** | Levier plateforme | **Cible 150-250K EUR** | Levier IA + Normandie | Hypothese |
| 15 | **7 couches switching costs** | Integration, ontologie, apps, knowledge, securite, formation, workflows | **5 couches** | Sources, ontologie, agents, historique claims, habitude | Mecanisme |
| 16 | **Marge 68% -> 82% (6 ans)** | Consulting -> plateforme | **35% -> 65% (3 ans)** | FDC/FDE -> ontologies templates + IA | Trajectoire |
| 17 | **Pipeline Builder** | DAG visuel, 80+ transforms | **Connecteurs Python async** | 7 connecteurs en V1 via Nango | A construire |
| 18 | **Data Connection** | 150+ connecteurs natifs | **Nango** | 300+ integrations OAuth | Choix fait |
| 19 | **Centre d'Excellence** | 5-50+ personnes chez le client | -- | **Pas d'equivalent PME.** Spider reste le Shogun. | N/A |
| 20 | **Mycelium** (cross-client intelligence) | N'existe PAS chez Palantir | **Avantage unique Spider** | Intelligence collective inter-PME (Phase 2-3) | Vision |

### Les 3 concepts que Spider prend de Palantir

1. **L'investissement a perte delibere sur l'acquisition.** Palantir perd $500K par pilot. Spider perd 3-5K EUR par diagnostic+setup. Mais chaque perte est un investissement dans la data captive et l'ontologie. Le retour vient de l'expansion (NDR 139% Palantir, cible 130% Spider).

2. **L'ontologie comme moat.** Pas le code, pas l'IA, pas la marque. L'ontologie -- la formalisation de "comment cette entreprise fonctionne reellement." Le code est copiable en 6 mois. L'ontologie accumulee sur 12 mois ne l'est pas. Spider ajoute une couche probabiliste (claims avec belief [0,1]) que Palantir n'a pas.

3. **Le FDE comme unite atomique.** La meme personne qui diagnostique construit et deploie. Pas de telephone arabe entre consultant, PM, dev. Le FDC (Thierry) comprend le metier. Le FDE construit le systeme. Les deux sont en face du client. La sortie n'est pas un PowerPoint -- c'est un agent qui fonctionne.

### Les 3 concepts que Spider laisse

1. **Le Centre d'Excellence.** Palantir forme 5-50 personnes chez le client pour qu'elles construisent leurs propres applications. Une PME de 10 salaries n'a pas 5 personnes tech. Spider reste le Shogun -- le client ne devient jamais autonome sur la plateforme, seulement sur les resultats.

2. **Le deploiement air-gapped / edge.** Palantir deploie sur des sous-marins et des bases militaires. Spider deploie sur OVH et Scaleway. La souverainete EU est suffisante pour les PME francaises. Pas besoin de FedRAMP.

3. **Le cycle de vente de 9+ mois.** Palantir pre-bootcamp = 9+ mois de relationship building avant le premier engagement. Spider n'a pas ce luxe. Le Diagnostic Eclair remplace 9 mois de nurturing par 1 demi-journee de valeur immediate.

---

## 7.2 Les 12 premieres semaines -- Plan d'action semaine par semaine

Ce plan croise la methodologie Palantir (bootcamp -> pilot -> expand) avec les contraintes Spider (Jordan premier client, equipe reduite, cash limite).

### Semaines 1-2 : Le Bootcamp Jordan

| Jour | Action | Responsable | Livrable |
|------|--------|-------------|----------|
| **L (J1)** | Appeler Jordan. Fixer le prix : 490 EUR/mois + 1 990 EUR setup. | Nathan | Accord verbal ou kill signal |
| **L-Ma** | Connecter Sheets + Notion + Pennylane via Nango. | Nathan | 3 sources connectees |
| **Ma soir** | Lancer extraction LLM sur 726 campagnes. Entity resolution overnight. | Nathan (auto) | Ontologie Jordan V1 |
| **Me-Je** | Preparer le Diagnostic Eclair. 5-10 insights data-driven. | Nathan + Thierry | Presentation diagnostic |
| **Ve (J5)** | **Diagnostic Eclair chez Jordan.** Thierry mene le process mapping (45 min). Nathan montre le diagnostic (45 min). Proposition en fin de reunion. | Thierry + Nathan | Buy-in emotionnel + engagement client |
| **S2-Lu** | Jordan signe. Setup fee encaisse. | Nathan | Premier paiement |
| **S2** | Debut construction pipeline : Sheets -> Notion -> Pennylane automatise. | Nathan | Pipeline en cours |

### Semaines 3-4 : Le Pilot rapide

| Semaine | Action | Responsable | Livrable |
|---------|--------|-------------|----------|
| **S3** | Pipeline operationnel. Elimination triple saisie. Alertes auto J-28. Base tarifaire centralisee. | Nathan | Systeme fonctionnel |
| **S3-S4** | Test sur 5-10 campagnes actives. Jordan utilise le systeme au quotidien. Nathan corrige en temps reel. | Nathan + Jordan | Campagnes gerees automatiquement |
| **S4** | **GATE M1.** "Jordan, tu renouvelles a 490 EUR ?" Criteres : oui + valeur mesurable + au moins 1 signal d'expansion. | Nathan | **GO ou KILL** |

### Semaines 5-8 : Replication (2-3 clients Drakkar)

| Semaine | Action | Responsable | Livrable |
|---------|--------|-------------|----------|
| **S5** | Identifier 2-3 prospects dans le reseau Drakkar. Profil ICP strict : 5-50 salaries, CEO seul decideur, processus manuels, deja digital. | Thierry + Jean | 2-3 prospects qualifies |
| **S5-S6** | Premiers contacts avec 3 cabinets comptables en Normandie. Format : "On offre un diagnostic gratuit a vos meilleurs clients." | Thierry | 3 cabinets contactes |
| **S6-S7** | Diagnostic Eclair chez chaque prospect. Meme format que Jordan. | Thierry + Nathan | 2-3 diagnostics realises |
| **S7-S8** | Setup des clients qui convertissent. **Test H4 :** le temps d'onboarding client 2-3 est-il inferieur a celui de Jordan ? | Nathan | Validation ou invalidation H4 |
| **S8** | **GATE M2 (anticipe).** 2+ clients payants non-amis ? | Nathan | GO ou signal de pivot |

### Semaines 9-12 : Premier Upsell + recrutement FDE

| Semaine | Action | Responsable | Livrable |
|---------|--------|-------------|----------|
| **S9-S10** | Chez Jordan : 2 mois de data captee. Spider detecte les 285 factures impayees. Nathan prepare l'Agent Relance. | Nathan | Agent Relance prototype |
| **S10** | Proposition upsell Jordan : "39.3% de tes factures sont impayees. Agent Relance : setup 1 990 EUR + 190 EUR/mois." | Thierry + Nathan | MRR Jordan : 490 -> 680 EUR |
| **S9-S12** | Recrutement FDE #1. Annonce, tri, entretiens. Profil : dev mid-senior, Python, Normandie, capable de parler a des non-tech. | Nathan + Remy | FDE #1 identifie |
| **S12** | **Bilan trimestre.** Ou en est-on ? | Toute l'equipe | Plan Q2 ajuste |

### Metriques de succes semaine 12

| Metrique | Minimum | Ideal |
|----------|---------|-------|
| Clients payants | 3 | 5 |
| Dont non-amis | 2 | 3+ |
| MRR total | 1 470 EUR | 3 000+ EUR |
| Jordan renouvelle | Oui | Oui + 1 upsell |
| Setup fees encaisses | 5 970 EUR | 9 950+ EUR |
| Temps onboarding client 3 vs client 1 | <80% du temps | <60% (H4 validee) |
| Ratio IA/humain par campagne | 40% IA | 50%+ IA |
| Demandes d'expansion non sollicitees | 1 | 3+ |
| Cabinets comptables en discussion | 2 | 3+ |
| FDE #1 recrute ou en cours | En cours | Signe |

---

## 7.3 Ce que Spider prend, ce qu'il laisse

### Le tableau de decision

| Dimension | Palantir fait... | Spider prend | Spider adapte | Spider laisse |
|-----------|-----------------|-------------|---------------|---------------|
| **Acquisition** | Bootcamp 5 jours gratuit, $12-36K | Le concept du diagnostic gratuit | Compresse a 1 demi-journee, 2 pers., ~500 EUR | Le format 5 jours a 5-8 personnes |
| **Pilot** | 90 jours, $250K, marge negative | L'acceptation de la marge negative au debut | Compresse a 4 semaines, 490 EUR/mois | Les 90 jours et les $250K |
| **Ontologie** | Custom par client, $millions | Le concept de modele semantique vivant | Templates par vertical, transferables | La construction custom a $millions |
| **FDE** | $200K+, Stanford, 50-70h/semaine | Le role hybride code + terrain | Normandie, 45-50K EUR, IA pour compenser | Les $200K et les 70h/semaine |
| **Expand** | Inter-departements, NDR 139% | Le mecanisme d'expansion par detection d'anomalies | Intra-process (pas inter-dept), cible NDR 130% | L'expansion horizontale multi-departements |
| **Scale** | CoE 5-50+ personnes, client self-service | L'objectif de marge >55% a l'echelle | Assistant IA self-service (pas CoE humain) | Le Centre d'Excellence client-side |
| **Pricing** | "No pricing strategy" = land grab massif | L'idee de sous-facturer l'entree | Contraint par le cash (pas de $5.2B de tresorerie) | Le "no pricing strategy" pur |
| **Moat** | 7 couches switching costs | Les 5 couches applicables aux PME | Ajoute le Mycelium (cross-client, absent chez Palantir) | RBAC/securite complexe, air-gap |
| **Timeline** | 17 ans pour la rentabilite | La patience sur le PMF (18-24 mois) | Doit etre profitable en 12-18 mois (Drakkar finance) | Les 17 ans de cash-burn |
| **Data clients** | 50-150+ sources, equipes data, ERP complexes | L'ambition de connecter toutes les sources | Commence avec 3 sources (Sheets, Notion, Pennylane) | Les 50-150+ sources du jour 1 |
| **Claims** | Ontologie deterministe (un fait = un fait) | -- | -- | L'ontologie deterministe |
| **Claims (Spider)** | N'existe pas chez Palantir | L'ontologie probabiliste (belief [0,1]) | Innovation propre a Spider, pas un emprunt | -- |

### La regle de conversion

Pour chaque concept Palantir, la regle de traduction est :

> **Diviser l'echelle par 1 000. Diviser le temps par 10. Multiplier l'IA par 10.**

- $250K pilot -> 490 EUR/mois (x500 moins cher)
- 5 jours bootcamp -> 1 demi-journee (x10 plus rapide)
- 4 FDEs par client -> 1 FDE + IA (x4 moins de personnes)
- 90 jours pilot -> 4 semaines (x3 plus rapide)
- 9+ mois pre-bootcamp -> 0 mois (reseau Drakkar = confiance pre-existante)

La compression est possible parce que :
1. Une PME de 10 salaries est 1 000x moins complexe qu'un Fortune 500 de 50 000
2. L'IA de 2026 fait en 2h ce que 4 FDEs faisaient en 2 semaines en 2016
3. Le dirigeant PME decide seul (pas de procurement committee)
4. Les processus PME sont repetitifs et peu profonds (9 etapes vs 500+ pour une supply chain Airbus)

### Le risque de la traduction

Le danger de l'analogie Palantir n'est pas de trop copier -- c'est de copier les mauvais elements. Trois pieges specifiques :

**Piege 1 : L'overengineering ontologique.** Palantir construit des ontologies de 500+ Object Types avec des interfaces polymorphiques et des fonctions TypeScript complexes. Pour une PME de 10 salaries, 5-8 entities suffisent. Le piege est de construire une architecture pour 500 Object Types alors qu'on en a besoin de 5. L'IA de Nathan dit "peut-etre invente" sur certains choix de stack [SPIDER-FINAL, section V]. C'est un signal : construire le minimum qui marche, pas l'architecture qui impressionne.

**Piege 2 : Le "no pricing strategy" sans le cash.** Karp peut dire "no pricing strategy" parce qu'il a $5.2B de tresorerie. Nathan a 100K EUR de Drakkar. La sous-facturation deliberee de Palantir ($65.4M de pertes sur les nouveaux clients) est possible uniquement avec un bilan qui absorbe les pertes. Spider doit etre profitable par client a partir du mois 4-5 (setup fee amortit le cout d'acquisition). Pas de land grab generalise -- un land grab chirurgical dans le reseau Drakkar.

**Piege 3 : Confondre FDE et ESN.** Le FDE Palantir n'est pas un consultant. Il construit du logiciel qui remplace le consulting. Si le FDC Spider passe 80% de son temps a faire du consulting classique (rapports, reunions, recommandations) et 20% a alimenter l'IA, Spider est une ESN. Le ratio doit s'inverser en 6 mois : 20% consulting, 80% alimentation et supervision des agents IA.

---

# ANNEXES

## Glossaire

| Terme | Definition |
|-------|-----------|
| **ARPA** | Average Revenue Per Account -- revenu mensuel moyen par client |
| **ACV** | Annual Contract Value -- valeur annuelle du contrat |
| **CAC** | Customer Acquisition Cost -- cout d'acquisition d'un client |
| **LTV** | Lifetime Value -- valeur totale d'un client sur sa duree de vie |
| **NDR** | Net Dollar Retention -- retention nette en dollars (>100% = expansion > churn) |
| **NPS** | Net Promoter Score -- indice de satisfaction et de recommandation |
| **MRR** | Monthly Recurring Revenue -- revenu recurrent mensuel |
| **FDC** | Forward Deployed Consultant -- consultant deploye chez le client |
| **FDE** | Forward Deployed Engineer -- ingenieur deploye chez le client |
| **ICP** | Ideal Customer Profile -- profil du client ideal |
| **PMF** | Product-Market Fit -- adequation produit-marche |
| **PLG** | Product-Led Growth -- croissance tiree par le produit |
| **Claims** | Affirmation extraite par l'IA avec un degre de croyance [0,1] |
| **Ontologie** | Modele semantique vivant de l'entreprise -- la formalisation de "comment cette boite fonctionne reellement" |

## Index des sources

| Ref | Fichier | Contenu cle utilise |
|-----|---------|---------------------|
| R3 | `08-mega-livrable/research/R3-french-pme-buying.md` | Seuils de decision CEO (<500 EUR), canal expert-comptable (+5 pts), objections PME |
| R4 | `08-mega-livrable/research/R4-comparable-gtm.md` | Gusto cold call closet, Pennylane 6000 cabinets, Silae 75%, 6 patterns GTM |
| R5 | `08-mega-livrable/research/R5-unit-economics.md` | CAC par canal, churn par segment, salaires Normandie, payback benchmarks |
| SPIDER-FINAL | `07-spider-inputs/SPIDER-FINAL.md` | Theses T1-T10, pricing 500 EUR, architecture 2 couches, roadmap, hypotheses H1-H9 |
| Cas Jordan | `07-spider-inputs/cleaned/04-cas-jordan.md` | 726 campagnes, 39.3% impayes, triple saisie, workflow 9 etapes, 73 clients |
| Blueprint | `07-spider-inputs/SPIDER-PALANTIR-BLUEPRINT.md` | Mapping Palantir 55+ lignes, 4 temps, FDE anatomy, 12 semaines plan |

## Questions ouvertes pour Nathan

1. **Le prix Jordan.** La recommandation est 490 EUR/mois. Si Jordan dit "500 c'est trop, 300 OK" -- c'est un kill signal sur H1. Mais si Jordan dit "490 OK" sans reagir, est-ce parce que la valeur est evidente ou parce que c'est un ami qui veut t'aider ? Comment distinguer les deux ?

2. **Le salaire fondateurs.** 36K EUR brut est agressivement bas. Nathan vit-il de Drakkar en parallele ? Si oui, les 36K sont symboliques et le vrai cout est masque dans Drakkar. Il faut etre transparent sur le burn reel.

3. **Jean Le Tulzo.** Son role dans Spider est "CFO / Head of Ops." Mais dans le plan d'execution 12 semaines, il apparait principalement comme "sourceur de prospects Drakkar." Quel est son role reel dans le quotidien Spider ? Si c'est du sourcing, ce n'est pas un CFO -- c'est un BD. Si c'est de la structuration offre, quand est-ce que ca intervient ?

4. **La verticalite vs l'horizontalite.** Le plan recommande de commencer par les agences (pub, com, evenementiel) comme vertical primaire. Mais le reseau Drakkar est multi-vertical (industriel, services, commerce). Faut-il REFUSER un prospect Drakkar qui n'est pas dans le vertical agence ? Ou accepter pour le revenu et l'apprentissage, au risque de diluer l'ontologie template ?

5. **Verian Advisory.** Jordan lance Verian Advisory (consulting international) en parallele de ComPrivee. Nathan dit "tout systeme construit pour ComPrivee doit etre duplicable a Verian." Est-ce que Verian est un deuxieme client payant ou une extension gratuite du contrat Jordan ? Si c'est un deuxieme contrat, c'est le test de transfert d'ontologie le plus propre possible (meme dirigeant, vertical different). Si c'est gratuit, c'est du scope creep.

---

*Document ecrit le 19 fevrier 2026. 750 lignes. Chaque recommandation est adossee a un chiffre reel. Chaque calcul est explicit. Ce n'est pas un plan de consensus -- c'est une decision.*
