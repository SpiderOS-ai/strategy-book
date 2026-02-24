# CHALLENGES V2 — Apres lecture des CODIRs et réponses Nathan

> Date : 20 fevrier 2026
> Ce document integre les 3 transcripts CODIR (19-20 fev) + les reponses aux questions.
> Il remplace QUESTIONS-NATHAN.md comme document de travail actif.

---

## CE QUI A CHANGE — Les revelations des CODIRs

### 1. La situation financiere est CRITIQUE [PROVEN]
Drakkar brule 20-50K€/mois selon les hypotheses. Le studio ne s'autofinance plus. Le staffing est a 55-60% (cible 80%). Le revenu hebdo est 16-17K (cible 20K+). Jean pousse pour modéliser precisement mais personne n'a le chiffre exact.

**Implication Spider :** Le "self-funded R&D via Drakkar" du mega livrable est un mythe. Drakkar ne finance pas Spider — Drakkar SAIGNE et Spider ajoute au saignement. L'investissement Spider (400-500K€ equivalent annee 1) n'est pas du R&D confortable — c'est un pari existentiel.

### 2. Odoo est mort dans la tete de Nathan [PROVEN — VERBATIM]
"J'aime pas Odoo, je trouve que c'est pas un tres bon outil. C'est un tres bon outil comptable. Mais a part ca j'y trouve tres franchement pas grand chose."
"Faut pas miser sur Odoo tout court ! En gros c'est pas notre champ de bataille !"

**Implication Spider :** Le mega livrable dit "Spider se branche au-dessus d'Odoo." En realite, Nathan veut REMPLACER Odoo terme. "On dit on ne va pas remplacer les ERP, on va tout automatiser sur Spider, on va tout plugger dessus, une fois qu'on aura fini, Odoo ca saute." C'est plus agressif que ce qu'on avait. Spider n'est pas un complement d'ERP — c'est un REMPLACEMENT d'ERP a terme.

### 3. Nathan est en burnout reel [PROVEN — VERBATIM]
"Je peux litteralement plus physiquement bosser plus que ca."
Thierry : "T'as prevu de dormir quand ?"
Jean : "C'est juste comment tu prends soin de toi avant qu'on te force a le faire."

**Implication Spider :** Le mega livrable dit "Nathan est le bottleneck." C'est pire que ca. Nathan est a sa limite physique. Le plan "Nathan fait tout en Phase 0" est un plan de burnout. Si Nathan tombe, TOUT s'arrete — Spider, Drakkar, la vente, la strategie.

### 4. Le modele de vente actuel est mort [PROVEN — VERBATIM]
"J'ai la confirmation que ca marche pas."
"Ce qu'on vend c'est degueulasse. On est juste des implementeurs comme les autres."
"On vend du conseil, on vend des pourquoi, et en fait on ne vend pas des reponses."

**Implication Spider :** Le pivot vers "vendre des prototypes/outcomes" n'est pas un choix strategique — c'est une necessite de survie. Le modele audit/consulting ne genere plus assez de cash. Spider doit generer du revenu RAPIDEMENT, pas dans 6-12 mois.

### 5. L'equipe est jugee tres severement [PROVEN — VERBATIM]
"On a vraiment des chevres. Leur ratio est 3 a 10x."
"J'abstrais grandement l'equipe de mon raisonnement. Je pense vraiment qu'on peut tous les remplacer par l'IA."

**Implication Spider :** L'equipe Drakkar n'est PAS l'equipe Spider. Les FDC/FDE ne viendront pas de l'equipe actuelle (sauf peut-etre Charlotte, Julie, Farah pour le relationnel client). Le recrutement de profils nouveaux est critique.

### 6. La vision M&A est confirmee et amplifiee [PROVEN — VERBATIM]
"Dans 5 ans, Spider c'est le plus gros outil de M&A europeen."
"C'est soit rien, soit ca s'approche du milliard."
"Avant je disais on va racheter des boites, maintenant je dis non. En fait, moi je vais permettre aux gens de racheter des boites."

**Implication Spider :** La vision Phase 3 (M&A platform) n'est pas un reve lointain pour Nathan — c'est le COEUR de la strategie. Le mega livrable la traite comme speculative. Nathan la vit comme la raison d'etre.

### 7. Le "speech-to-process" est une capacite nouvelle [PROVEN]
Nathan fait tourner un assistant IA pendant l'appel Jordan qui mappe les process en Figma en temps reel. C'est un differenciateur potentiel majeur non documente.

### 8. Thierry a une vue insider de Palantir chez Airbus [PROVEN — VERBATIM]
"La force de Palantir c'est de connecter toutes les datas entre elles. Mais ils te proposent rien Palantir ! C'est toi qui configures tout !"
"Avec Palantir on est en train de donner ce savoir. Et c'est tout de la magie de Spider."

**Implication Spider :** Palantir chez Airbus est un outil de dashboarding, pas d'operations. Spider doit aller PLUS LOIN que Palantir — pas juste visualiser, mais AGIR (les agents). C'est le differenciateur reel.

### 9. Pas de pricing fixe [REPONSE NATHAN]
"En fait pas de pricing fixe je pense, on fait en fonction du ROI."

**Implication Spider :** La recommandation 490€/mois du mega livrable est potentiellement fausse. Nathan veut du pricing adaptatif au ROI. C'est plus intelligent strategiquement (capture plus de valeur) mais beaucoup plus dur a scaler (chaque deal est custom).

### 10. Le plus gros doute de Nathan = le MOAT [REPONSE NATHAN]
"Beaucoup plus peur qu'un autre acteur fasse mieux que nous et que pas un vrai moat."
"Pour moi on doit trouver du ROI evident. Mais ce qui me fait surtout peur, c'est que TOUS les outils vont proposer ca non?"
"Le moat c'est vraiment notre capacite a recreer les process a partir de data brut."

**Implication Spider :** Nathan sait que l'automatisation pure n'est PAS un moat. Tout le monde pourra automatiser la triple saisie avec Claude + Zapier. Le vrai moat doit etre ailleurs — dans la capacite a comprendre et recreer les process metier a partir de donnees brutes. C'est le Claims Engine / l'ontologie. Mais ca n'existe pas encore.

---

## MES CHALLENGES APRES RELECTURE

### Challenge 1 : La survie de Drakkar conditionne TOUT
Le mega livrable pose Spider comme un projet finance par Drakkar. En realite, Drakkar est en danger. Si Drakkar perd encore 2-3 clients, le burn monte a 50K+/mois et il n'y a plus de filet. Spider ne peut pas se construire sur des fondations qui tremblent.

**Ma proposition :** Separer mentalement les deux. Drakkar doit survivre INDEPENDAMMENT de Spider. Ca veut dire :
1. Thierry + Jean stabilisent l'Accelerateur (objectif : staffing a 80%, revenu a 20K+/semaine)
2. Nathan ne passe PAS plus de 20% de son temps sur Drakkar ops (actuellement c'est 50%+)
3. Si Drakkar ne peut pas s'auto-stabiliser en 3 mois, c'est un signal que l'equipe ne peut pas fonctionner sans Nathan — et ca veut dire que Spider est impossible tant que Nathan est le bottleneck de Drakkar.

### Challenge 2 : Nathan ne peut PAS tout faire
"Je peux litteralement plus physiquement bosser plus que ca." Et pourtant le plan Phase 0 dit "Nathan fait tout." C'est contradictoire.

**Ma proposition :** Le premier recrutement n'est pas un FDE. C'est un "Chief of Staff" / bras droit operationnel pour Nathan. Quelqu'un qui prend 50% des taches Nathan (Drakkar ops, suivi client, coordination equipe) pour que Nathan puisse se concentrer a 80% sur Spider + vente. C'est le recrutement le plus urgent de tous. Peut-etre que Mathis pourrait evoluer vers ce role s'il monte en competence rapidement. Ou que Jean prenne plus de charge operationnelle Drakkar.

### Challenge 3 : Le pricing adaptatif vs la scalabilite
Nathan veut du pricing au ROI. C'est intelligent (capture plus de valeur) mais ca tue la scalabilite. Chaque deal devient du sur-mesure. On ne peut pas construire une machine de vente reproductible sur du pricing custom.

**Ma proposition :** Pricing en 2 couches :
- **Couche 1 (fixe, scalable) :** Abonnement standard a 490-990€/mois selon la taille. C'est le "on s'occupe de vos operations." Prix fixe, decision rapide, CEO signe seul.
- **Couche 2 (variable, ROI-based) :** Setup fees + agents supplementaires prices au ROI. "On a detecte 100K€ d'impayes. Notre agent en recupere 30%. Setup 2K€ + 15% des recuperations." C'est la ou le pricing au ROI fait sens — sur l'upsell, pas sur l'entree.

### Challenge 4 : Le moat n'existe pas et Nathan le sait
Nathan dit que son plus gros doute c'est le moat. Il a raison. Aujourd'hui, Claude + Zapier + un freelance competent = 80% de ce que Spider fait pour Jordan. Le "speech-to-process" est cool mais reproductible.

**Ma proposition :** Le moat ne sera JAMAIS technologique. Il sera dans 3 choses :
1. **La vitesse d'execution.** Etre le premier a avoir 20-50 clients avec des templates d'ontologie operationnels. Un concurrent qui arrive 12 mois plus tard doit tout reconstruire.
2. **La data captive.** Apres 6 mois d'operations, Spider a 6 mois de contexte irreproductible. C'est le moat Google (25 ans de donnees de recherche). Un concurrent peut construire un meilleur outil. Il ne peut pas remonter 6 mois.
3. **Le reseau de distribution.** Si Spider arrive a penetrer le canal expert-comptable (comme Pennylane avec 6000 cabinets), c'est un moat de distribution quasi-impossible a repliquer.

Le moat se CONSTRUIT par l'execution, il ne se DECLARE pas. Et il n'existera pas avant mois 12-18.

### Challenge 5 : Spider remplace l'ERP ou se branche dessus ?
Le mega livrable dit "Spider se branche au-dessus d'Odoo." Nathan dit "une fois qu'on aura fini, Odoo ca saute." C'est deux strategies radicalement differentes.

**Ma proposition :** Phase 0-1, Spider se branche au-dessus (c'est plus facile a vendre : "on ne change rien chez vous"). Phase 2+, Spider remplace progressivement. Mais NE JAMAIS dire au client "on va remplacer votre ERP." Le Shogunat : on remplace sans que le client s'en rende compte. Un jour il se reveille et realise que tout passe par Spider. L'ERP est devenu un backend fantome.

### Challenge 6 : Le Diagnostic Eclair comme produit standalone
Nathan a dit : "Peut-etre, idee tres interessante. Peut-etre l'equivalent de notre bootcamp a nous ?"

**Ma proposition (forte conviction) :** Le Diagnostic Eclair devrait etre le PREMIER produit Spider. Pas l'abonnement. Le diagnostic.
- **Prix :** 1 990€ (one-shot, decision rapide)
- **Livrable :** En 48h, Spider se connecte a vos outils, analyse vos donnees, et vous livre un rapport de 15-20 pages avec des chiffres que vous n'avez JAMAIS vus sur votre propre entreprise.
- **Pourquoi :** Ca genere du revenu IMMEDIAT (pas 490€/mois sur 12 mois, mais 1 990€ maintenant). Ca valide le marche sans engagement long. Ca cree la douleur consciente qui convertit en abonnement. Et ca donne a Nathan 20 datasets clients pour construire l'ontologie.
- **Volume :** 20 diagnostics en 3 mois = 40K€ de revenu + 20 cas pour valider la these. Certains convertissent en abonnement. Les autres sont du cash + de la data.
- **C'est le bootcamp Palantir.** Exactement. Palantir fait 5 jours gratuits. Spider fait 48h pour 1 990€. Le client paie un premium parce que le livrable a de la valeur en soi (le diagnostic revele des choses qu'il ne sait pas).

### Challenge 7 : Thierry comme insider Palantir
Thierry a vu Palantir de l'interieur chez Airbus. Il dit "ils te proposent rien, c'est toi qui configures tout." C'est exactement le gap que Spider doit combler : pas juste connecter les donnees, mais AGIR dessus.

**Ma proposition :** Thierry devrait etre le lead du Diagnostic Eclair. C'est son terrain : comprendre le metier du client, percevoir ses limites, elever le debat. Le Diagnostic Eclair est du consulting augmente par l'IA — exactement la combinaison FDC que le mega livrable decrit. Thierry ne codera pas. Mais il arrivera chez le client avec des donnees que Spider a deja processees, et il les interpretera avec sa credibilite Airbus.

---

## QUESTIONS RESTANTES POUR NATHAN

### Q1 : Est-ce que Jean peut prendre 80% des ops Drakkar ?
Pour que Nathan se concentre sur Spider, il faut que quelqu'un d'autre gere Drakkar au quotidien. Jean est le candidat naturel (finance + structuration). Mais Jean est deja a 38% Drakkar + 20% Spider. Est-ce qu'il est pret a porter Drakkar a 80% pendant que Nathan passe a 80% Spider ?

**Reponse Nathan :**
> [A COMPLETER]

### Q2 : Le Diagnostic Eclair a 1990€ — tu le vendrais a qui demain ?
Pas Jordan (c'est un ami). Un INCONNU. Qui ? Comment tu le trouves ? Quel est le pitch en 30 secondes ?

**Reponse Nathan :**
> [A COMPLETER]

### Q3 : Combien de temps avant que le burn rate devienne fatal ?
Jean dit 20K/mois. Nathan dit peut-etre 50K. A quel rythme les fonds propres diminuent ? Combien de mois de tresorerie reste-t-il ? C'est la question qui determine TOUTE la strategie.

**Reponse Nathan :**
> [A COMPLETER]

### Q4 : Le "speech-to-process" — c'est quoi exactement ?
Tu as fait tourner un assistant IA qui mappe les process en Figma pendant un appel. C'est fait avec quoi ? Claude Code + MCP Figma ? Un outil custom ? C'est reproductible ou c'etait un one-shot ?

**Reponse Nathan :**
> [A COMPLETER]

### Q5 : La relation Spider / Drakkar — fusion ou separation ?
Tu as dit "Phase 2, decision a prendre, Drakkar sort et potentielle levee." Mais Phase 2 c'est mois 5-8 dans le plan. C'est dans 3-6 mois. La decision de fusion/separation doit etre pensee MAINTENANT meme si elle est executee plus tard. Qu'est-ce que tu vois ?

**Reponse Nathan :**
> [A COMPLETER]

### Q6 : Christian (arrivee mai) — Drakkar ou Spider ?
Le CODIR debat de mettre Christian (comptable + ERP + code) sur Drakkar ou Spider. Thierry pousse pour Spider. Nathan est indecis. Si Christian va sur Spider, c'est le premier vrai membre de l'equipe Spider hors fondateurs. C'est un signal fort.

**Reponse Nathan :**
> [A COMPLETER]

---

## MA PROPOSITION DE STRATEGIE REVISEE (post-CODIRs)

### Le plan en 5 etapes

**Etape 0 (MAINTENANT — Semaine 1-2) : Stabiliser Drakkar**
- Jean prend 80% des ops Drakkar
- Thierry stabilise l'Accelerateur (cible 80% staffing)
- Nathan passe a 80% Spider + vente

**Etape 1 (Semaines 3-6) : Diagnostic Eclair comme produit**
- Nathan + Thierry font 10 Diagnostics Eclair a 1 990€
- 5 via reseau Drakkar, 5 via cold (cabinets comptables, LinkedIn)
- Ca genere 20K€ de cash + 10 datasets pour construire l'ontologie
- Certains convertissent en abonnement Spider

**Etape 2 (Mois 2-4) : Jordan + 2-3 clients en abonnement**
- Jordan signe a 500€/mois (prototype construit par Nathan + Remy)
- 2-3 Diagnostics Eclair convertissent en abonnement
- MRR : 2-3K€
- Le Diagnostic Eclair continue en parallele (machine a leads)

**Etape 3 (Mois 4-6) : Premier FDE recrute, premiere productisation**
- Christian (si Spider) ou recrutement externe comme FDE #1
- FDE fait le Diagnostic Eclair + onboarding SEUL (test de scalabilite)
- Templates d'ontologie commencent a emerger
- Si ca marche : startup. Si ca echoue : consulting.

**Etape 4 (Mois 6-12) : Decision Drakkar/Spider**
- Si 10+ clients, 10K+ MRR, ratio FDE s'ameliore : Spider devient l'entite principale
- Levee de fonds ou self-sustaining
- Drakkar est absorbe, vendu, ou mis en maintenance

### Le kill criteria
**KILL Spider si :** Apres 10 Diagnostics Eclair et 3 mois, ZERO client non-ami ne convertit en abonnement >300€/mois. La these est fausse.

---

*Document cree le 20 fevrier 2026. Integre les 3 transcripts CODIR + reponses Nathan.*
