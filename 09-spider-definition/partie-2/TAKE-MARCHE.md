# OU VA LE MARCHE — Mon take

> 21 fevrier 2026. Pas ce que les VC disent. Ce que je pense.

---

## Le take en une phrase

**L'IA ne remplace pas le SaaS. L'IA rend le SaaS invisible. Et ce qui reste visible — la RELATION — devient le seul actif qui compte.**

---

## Le raisonnement

### Ce qui va se passer dans les 18 prochains mois (haute conviction)

**1. Les couches d'execution vont se commoditiser a une vitesse folle.**

Envoyer un email, remplir un formulaire, faire une relance, generer un rapport, analyser un spreadsheet — tout ca sera gratuit ou quasi-gratuit d'ici 18 mois. Pas parce que Spider le fera. Parce que Claude, Gemini, Copilot le feront NATIVEMENT dans les outils que les gens utilisent deja.

La triple saisie de Jordan ? Morte. Pas grace a Spider. Grace a Google qui mettra un bouton "sync" entre Sheets et Pennylane via MCP. C'est une question de mois, pas d'annees.

Tout ce qui peut etre decrit comme "prends cette donnee ici et mets-la la" sera un commodity. C'est la loi d'Altman appliquee : cout de l'intelligence -10x/an. L'execution cognitive simple tend vers zero.

**2. La couche d'orchestration (multi-outils, multi-etapes) va se commoditiser aussi, mais plus lentement.**

Workspace Studio fait deja des workflows cross-app chez Google. Copilot Studio fait pareil chez Microsoft. MCP connecte tout a tout. Zapier/Make/n8n avec des LLM integres font de l'orchestration basique.

Mais l'orchestration FIABLE — celle qui ne plante pas a 2h du matin quand le format de facture de Schmidt a change — c'est plus dur. Dines (UiPath) a raison : il faut du deterministe + de l'agentique. Les workflows purement agentiques echouent sur les cas limites. Les workflows purement deterministes ne s'adaptent pas.

**Prediction :** D'ici fin 2027, l'orchestration basique (si X alors Y, meme cross-outils) sera commoditisee. L'orchestration complexe (gerer les exceptions, s'adapter au contexte, apprendre des erreurs) restera un probleme non-resolu par les outils generiques.

**3. La couche de COMPREHENSION ne va PAS se commoditiser. Et c'est la que tout se joue.**

Voici pourquoi. La comprehension, c'est :
- Savoir que quand Jordan dit "le dossier italien" il parle de la campagne Fratelli pour IKEA Italie et pas de la campagne pasta pour Barilla
- Savoir que Cadres Blancs a augmente ses tarifs en mars et que Jordan a bascule sur Affiouest en reponse
- Savoir que juillet est le mois critique en tresorerie parce que les regies facturent en avance pour septembre
- Savoir qu'Audrey oublie systematiquement les frais de monitoring Oxialive

Ca ne vient PAS des donnees. Ca vient des CONVERSATIONS, des OBSERVATIONS, des INTERACTIONS accumulees dans le temps. Un LLM peut analyser des donnees. Il ne peut pas observer que le ton du dernier email de Schmidt a change et que ca signifie qu'il est en train de chercher un autre fournisseur.

**Le claim :** La comprehension contextuelle — la capacite a comprendre un business SPECIFIQUE dans sa totalite, avec ses non-dits, ses habitudes, ses exceptions — est le seul actif qui resiste a la commoditisation par les LLM. Parce que les LLM operent sur du texte, et la comprehension contextuelle vit dans l'ESPACE ENTRE les textes — dans ce qui n'est pas dit, pas ecrit, pas digitise.

---

### Ce que ca signifie pour le marche (mon take, pas celui des VC)

**Phase 1 (maintenant — fin 2026) : L'illusion de la disruption**

Tout le monde parle de SaaSpocalypse. Les valorisations SaaS chutent. Les agents IA font des demos impressionnantes. Les VCs investissent des milliards dans les "AI agents."

Mais au sol — dans les PME, dans les entreprises reelles — presque RIEN ne change. 95% des projets IA enterprise echouent (MIT). Les PME francaises sont a 17% d'adoption. Le patron de Caen utilise toujours Excel et son telephone.

La Phase 1 est une phase de NARRATIVE, pas de REALITE. Les demos marchent. La production echoue. Les agents sont impressionnants sur les cas simples et catastrophiques sur les cas complexes.

**Qui gagne en Phase 1 :** Les vendeurs de pioches (NVIDIA, cloud providers). Les plateformes de modeles (Anthropic, OpenAI). Les outils pour developpeurs (Cursor, Claude Code). PAS les "AI for business" — parce que le business n'a pas encore compris ce qu'il veut.

**Phase 2 (2027-2028) : La desillusion productive**

Les agents generiques deviennent 10-100x meilleurs. Le patron de PME essaie Claude/Gemini pour la premiere fois. Il est impressionne par les taches simples (resume cet email, analyse ce tableau). Il est decu par les taches complexes (gere mes impayes de bout en bout — l'agent oublie un client, envoie un mauvais montant, ne comprend pas le contexte).

C'est le "Trough of Disillusionment" de Gartner. Le patron dit : "L'IA c'est bien pour les trucs simples, mais pour mon metier, ca marche pas."

**Qui gagne en Phase 2 :** Les entreprises qui ont COMPRIS que le probleme n'est pas l'IA mais le DEPLOIEMENT. Celles qui combinent l'agent IA + un humain qui comprend le metier + un process eprouve. C'est exactement le modele FDE de Palantir. C'est exactement ce que Nathan fait avec Jordan.

**Sauf que :** Ce qui prenait un FDE a $200K/an en 2024 en prendra un a $80K/an en 2027 parce que l'agent fera 70% du travail au lieu de 20%. Le modele FDE se DEMORCRATISE. Plus besoin d'un ingenieur Stanford. Un Charlotte formee pendant 3 mois avec Claude Code peut deployer Spider chez un client. Le goulot d'etranglement n'est plus le talent technique. C'est la COMPREHENSION METIER.

**Phase 3 (2028-2030) : La recomposition**

Les outils generiques gèrent 90% de l'execution et 60% de l'orchestration. Ils ne gerent toujours pas la comprehension. Mais ils ont tellement simplifie le reste que le SEUL differentiel qui reste entre les entreprises est : "qui comprend le mieux le business de son client ?"

Le SaaS est devenu invisible. L'email se gere tout seul. Les factures se traitent toutes seules. Les relances partent toutes seules. La compta se fait toute seule. Tout ca est devenu de l'infrastructure — comme l'electricite, comme internet.

Ce qui reste VISIBLE pour le dirigeant :
- "Est-ce que quelqu'un comprend MON business ?"
- "Est-ce que quelqu'un me dit ce que je ne vois pas ?"
- "Est-ce que quelqu'un me donne confiance sur l'avenir ?"

C'est le retour au CONSEIL. Mais un conseil augmente par une comprehension 100x plus profonde que ce qu'un humain pouvait avoir seul. Le consultant de 2030 arrive chez le client et SAIT deja tout — parce que Spider (ou son equivalent) lui a donne 12 mois de contexte cumule.

**Qui gagne en Phase 3 :** Les entreprises qui possedent la RELATION + la COMPREHENSION. Pas les outils. Pas les donnees. La relation de confiance + la comprehension contextuelle accumulee.

---

### Les implications strategiques que personne ne tire

**Implication 1 : Le produit de Spider n'est pas un logiciel. C'est une RELATION augmentee.**

Dans un monde ou l'execution est gratuite et l'orchestration est commoditisee, le seul actif est la relation de confiance entre Spider et le dirigeant. Le logiciel est le MOYEN de livrer la relation, pas le produit.

Ca change tout :
- Le pricing ne devrait pas etre au logiciel (€/mois pour un outil) mais a la RELATION (€/mois pour "quelqu'un qui comprend mon business")
- Le KPI principal n'est pas le nombre de taches automatisees mais la CONFIANCE du dirigeant (mesurable : NPS, frequence de consultation, temps passe sur la plateforme)
- Le churn n'est pas cause par un concurrent meilleur mais par une rupture de confiance
- Le moat est la PROFONDEUR de la relation, pas la quantite de donnees

**Implication 2 : Le moat de Spider est un moat de RESEAU DE CONFIANCE, pas de data.**

Imagines ceci : Spider a 100 clients PME en Normandie. Chaque client fait confiance a Spider. Spider sait tout sur ces 100 businesses (pas les donnees — la COMPREHENSION).

Un jour, un fonds de PE veut racheter une PME normande. Il demande a Spider : "Comment va cette boite, VRAIMENT ?" Spider peut repondre — pas avec des chiffres publics, mais avec une comprehension contextuelle que personne d'autre n'a.

Un jour, une PME cherche un fournisseur. Spider sait que parmi ses 100 clients, 3 font exactement ce produit. Spider fait l'introduction.

Un jour, un expert-comptable veut savoir si son client va bien. Spider peut lui dire avant que le client lui-meme le sache.

Ce n'est pas un reseau de DONNEES (ca c'est le Mycelium tel que decrit — anonymise, agrege). C'est un reseau de CONFIANCE — Spider est le tiers de confiance qui sait tout et qui fait les connexions.

**C'est le modele du BANQUIER PRIVE, pas le modele de Palantir.** Le banquier prive ne gagne pas parce qu'il a les meilleurs produits financiers. Il gagne parce qu'il CONNAIT ses clients et fait les bonnes introductions au bon moment.

**Implication 3 : Le marche se divise en 3, pas en 2.**

Tout le monde dit "SaaS vs agents." La realite est plus fine :

| Couche | Ce qui se passe | Qui gagne |
|--------|----------------|-----------|
| **Execution** (faire des taches) | Commoditise, gratuit d'ici 2028 | Personne (integre dans les OS) |
| **Orchestration** (coordonner des taches) | Semi-commoditise, les cas simples sont gratuits, les cas complexes restent durs | Quelques plateformes (Zapier evolue, MCP-based tools) |
| **Comprehension** (comprendre le business) | PAS commoditise, RESISTE a la commoditisation | Les entreprises qui VIVENT avec le client (FDE model, service-as-software, relation long terme) |

Spider doit jouer UNIQUEMENT sur la couche comprehension. Si Spider essaie de gagner sur l'execution (triple saisie) ou l'orchestration (workflows automatises), il perd contre Google/Microsoft/Anthropic.

La couche comprehension se monetise differemment :
- Pas au mois (c'est du SaaS)
- Pas a la tache (c'est de l'execution)
- Au RESULTAT ou a la RELATION (c'est du service premium)

**Implication 4 : Les VCs se trompent — mais pas la ou on croit.**

Les VCs (a16z, Sequoia, YC) ont raison sur : l'IA transforme tout, les agents remplacent du travail, le SaaS se repricie.

Les VCs ont TORT sur : la vitesse de l'adoption dans le midmarket/SMB. Ils vivent dans la Bay Area ou une startup de 10 personnes utilise 40 outils SaaS. Le patron de PME a Caen utilise Excel, son telephone, et son comptable. L'adoption IA dans les PME francaises ne sera PAS exponentielle. Elle sera LINEAIRE et LENTE, poussee par :
- Les obligations reglementaires (e-facturation)
- Les intermediaires de confiance (comptables qui recommandent)
- Les crises (un client perdu, une tresorerie en danger, un depart en retraite)

Les VCs ont aussi TORT sur le moat data. Ils projettent le modele Google/Facebook (billions de data points = moat insurmontable) sur les startups. Mais une startup B2B avec 50 clients PME n'a pas un "moat data." Elle a 50 petits ilots de donnees non-connectes. Le moat data ne marche qu'a l'echelle. Et a l'echelle, Google l'a deja.

**Implication 5 : Le vrai timing n'est pas la "fenetre avant Odoo 20." C'est le moment ou les comptables recommandent l'IA.**

L'adoption IA dans les PME ne sera PAS tiree par les PME elles-memes (trop conservatrices, trop occupees, trop peur). Elle sera tiree par les INTERMEDIAIRES — les comptables, les banquiers, les consultants, les CCI.

Le moment ou un expert-comptable dit a son client "vous devriez utiliser Spider pour vos operations" est le moment ou le marche decolle. Pas avant.

Ce moment depend de :
1. Que Spider ait des cas prouves a montrer (prerequis : 10+ clients satisfaits)
2. Que l'expert-comptable y gagne quelque chose (prerequis : Spider ameliore la qualite des donnees que le comptable recoit)
3. Que le risque reputationnel soit faible (prerequis : Spider ne plante pas chez les premiers clients du comptable)

**Prediction concrete :** Le moment ou les comptables recommandent l'IA operationnelle est en 2028, pas en 2026. Parce qu'en 2026, les comptables sont absorbes par la e-facturation. En 2027, ils digerent. En 2028, ils cherchent le prochain levier de valeur pour leurs clients. C'est la que Spider doit etre pret.

Ca veut dire : Spider a 2 ans, pas 12 mois. Mais ces 2 ans doivent etre finances. D'ou l'urgence du cash via le modele consulting/cabinet (Strategie 2 de la STRATEGIE-COMPLETE) pendant que le marche murit.

---

### Le scenario que personne n'envisage

**Et si l'IA ne changeait PAS fondamentalement la facon dont les PME operent ?**

Hypothese : les PME francaises absorbent l'IA comme elles ont absorbe internet, le cloud, et le mobile — LENTEMENT, PARTIELLEMENT, et SANS changer leur mode de fonctionnement fondamental.

- Internet (1995-2010) : les PME ont cree un site web. Elles n'ont pas change leur business model.
- Cloud (2010-2020) : les PME sont passees a Gmail et Dropbox. Elles n'ont pas transforme leurs operations.
- Mobile (2015-2025) : les PME ont WhatsApp. Elles ne font pas de m-commerce.
- IA (2025-2035) : les PME utiliseront ChatGPT pour ecrire des emails. Elles ne remplaceront pas leur assistante.

Dans ce scenario, Spider fait face a un marche qui n'existe pas. Les PME ne veulent pas d'un "OS operationnel IA." Elles veulent un comptable qui repond au telephone et un assistant qui sait ou est le dossier Schmidt.

**Probabilite de ce scenario : 30-40%.** C'est pas negligeable. Et aucun doc du corpus ne le modelise.

**La protection contre ce scenario :** Le modele consulting (Strategie 2). Meme si le marche n'adopte pas l'IA massivement, Nathan + son equipe peuvent delivrer de la valeur en utilisant l'IA POUR le client (sans que le client ait besoin de comprendre l'IA). C'est le modele du plombier : le client ne sait pas comment marche la plomberie. Il paie quelqu'un qui sait.

---

## En resume — le take

1. **L'execution se commoditise (18 mois). L'orchestration se commoditise (3 ans). La comprehension ne se commoditise PAS.**

2. **Le moat durable n'est pas dans les donnees. Il est dans la CONFIANCE + COMPREHENSION accumulees dans une RELATION long terme.** Le modele est celui du banquier prive, pas de Google.

3. **Le marche PME sera LENT (2-3 ans, pas 12 mois).** Tire par les intermediaires de confiance (comptables), pas par les PME elles-memes. Spider doit SURVIVRE pendant la maturation via le consulting.

4. **Les VCs ont raison sur la direction, tort sur la vitesse et le mecanisme.** L'IA transforme tout, mais pas a la vitesse de la Bay Area. Et le moat n'est pas dans les data mais dans la relation.

5. **Le scenario ou le marche PME n'adopte PAS l'IA en profondeur est a 30-40%.** Il faut un plan B (consulting pur) qui marche dans ce scenario.

6. **Spider doit jouer la couche COMPREHENSION, pas execution ni orchestration.** C'est la seule couche qui resiste aux Big Tech. Et c'est la seule ou l'humain reste indispensable.

---

*21 fevrier 2026. Un take, pas un resume.*
