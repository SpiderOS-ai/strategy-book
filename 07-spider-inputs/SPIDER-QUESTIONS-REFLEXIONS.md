# SPIDER -- Questions et reflexions strategiques (v2)

> Ce document integre les reponses de Nathan (19 fevrier 2026) aux questions de la v1.
> Les questions resolues sont archivees. Les questions ouvertes sont approfondies.
> De nouvelles questions emergent des reponses elles-memes.
> Objectif : confronter les hypotheses restantes avec honnetete.

---

## 1. CE QUE NATHAN A CONFIRME (questions resolues)

### 1.1 Jean n'est pas un probleme -- il rattrape

Nathan corrige le prisme d'analyse : Jean ne "contredit" pas Nathan. Jean est en train d'apprendre. Sa note du 18 fevrier est deja beaucoup plus alignee que celle du 22 janvier. Le gap se reduit naturellement. DRK Data Copilot n'est pas un cheval de Troie -- c'est un mauvais angle, point final. Ce qu'on produit (la strategie, les docs) a vocation a tout expliquer a Jean et aux autres.

**Statut : resolu.** On n'aligne pas Jean -- on construit le document qui explique tout.

### 1.2 BMAD : le business model change, pas les modules

Les docs BMAD sont obsoletes sur le modele economique (SaaS classique vs Service-as-Software), mais les modules fonctionnels (Spider People, score de connaissance, profiling DISC/OCEAN, playbooks) restent pertinents dans leur scope. Les features comme Spider People ou le chatbot LLM sont meme des chevaux de Troie potentiels : des points d'entree faciles dans les PME qui ne savent pas que ces outils existent. Possiblement gratuits ou payables a l'usage.

**Statut : clarifie.** Le scope fonctionnel tient. Le packaging et le pricing sont a redefinir.

### 1.3 "Zero effort" = un message date, pas la realite actuelle

Nathan precise : "zero effort" etait le discours d'il y a quelques semaines. Aujourd'hui, le modele prevoit explicitement des consultants (Drakkar au debut, Forward Deployed Engineers ensuite) pour faire le setup. Le client ne fait rien -- mais quelqu'un fait le travail de configuration pour lui.

**Statut : resolu.** Le paradoxe n'en etait pas un. C'etait une erreur de temporalite dans l'analyse.

### 1.4 La stack technique n'est pas trop ambitieuse

Nathan : "A l'ere de l'AI coding, tout va beaucoup plus vite et la stack est ready." Les choix techniques (SurrealDB, architecture distribuee, etc.) seront abordes plus tard. Le chiffre de 70EUR/an par PME "ne vaut rien, c'est de la merde" -- il faudra recalculer.

**Statut : reporte.** Nathan ne veut pas arbitrer la stack maintenant. On notera que le risque est accepte, pas elimine.

### 1.5 Organisation : les roles sont clairs

- **Remy Menard = CTO.** Nathan n'est pas seul sur la tech. Le syndrome du "fondateur qui fait tout" est partiellement resolu.
- **Nathan = CEO + vente.** Avec ses sales si besoin. Il vend, il construit la vision, il dirige.
- **Thierry = consulting.** Pas un FDE au sens Palantir (il n'est pas ingenieur), mais un ex-head of manufacturing Airbus, conseiller au COMEX. Competences de consulting de haut niveau. Il apprendra la dimension IA.
- **Nicolas Guimier = pas un probleme.** Nathan dit que ca sera ok.

**Statut : clarifie.** Reste la question du role exact de Thierry (voir section 2).

---

## 2. DEFIS STRATEGIQUES OUVERTS (ce que Nathan ne sait pas)

### 2.1 Le race-to-bottom pricing

Nathan le dit lui-meme a Benoit : "Avec la vitesse a laquelle l'IA compresse les couts de delivery, combien de temps les scopes 50-100K tiennent ?"

Question miroir : si l'IA compresse les couts pour les agences, elle compressera aussi les couts pour Spider. Un agent qui automatise la facturation Pennylane, ca se construira en 2h avec les outils de 2027. Qu'est-ce qui empeche un freelance de repliquer le service Spider pour Jordan pour 200EUR/mois ?

Reponse possible : l'ontology accumulee + l'effet reseau. Mais Phase 1 (la toile) n'a pas encore d'effet reseau. C'est une course contre le temps.

**Reponse de Nathan : "Tres bonne question, je sais pas."**

C'est la question la plus dangereuse du dossier. Si la reponse est "le moat c'est la data accumulee", alors la VITESSE de capture est le seul avantage. Et la vitesse depend du nombre de clients, qui depend du prix, qui depend de la marge, qui depend de l'automatisation. Cercle vertueux -- ou vicieux.

### 2.2 Jordan : un vrai test commercial ou une demonstration entre amis ?

Jordan est l'ami de Nathan. Le premier mois est gratuit. 726 campagnes, donnees accessibles, probleme clair (triple saisie). Conditions ideales.

Nathan repond : "On le fera payer, a voir combien et comment."

C'est bien. Mais "a voir combien et comment" n'est pas un prix. Jordan qui paie 200EUR/mois apres un mois gratuit ne prouve pas la meme chose que Jordan qui paie 990EUR/mois des le jour 1. Le test commercial n'existe que si le prix teste correspond a celui qu'on veut appliquer ensuite.

**Ce qu'il faut valider :** Jordan accepte-t-il de payer 990EUR/mois sans negociation "entre potes" ? Si oui, on a un signal. Si non, le test ne valide rien de commercial.

### 2.3 L'actif tacite de Drakkar : reel ou narratif ?

Nathan admet : "On a fail justement parce qu'on n'a pas reussi a capter le tacite. Au final, ils ont un CRM mais mal utilise et pas les bonnes infos dedans."

C'est un aveu important. La these dit : "5 ans de deploiement ERP = ontology operationnelle qu'on ne peut pas acheter." Mais si Drakkar n'a meme pas reussi a capter le tacite de Decotec apres 3 ans, en quoi Spider sera different ?

Nathan repond : "Bah l'IA. On peut se connecter a tout 100x plus vite."

La difference est donc technologique, pas humaine. Spider parie que l'IA capture ce que les consultants n'ont pas su capturer. C'est un pari raisonnable -- mais c'est un pari, pas un actif existant. L'ontology operationnelle reste a construire avec Spider. Ce n'est pas un heritage de Drakkar.

**Challenge ouvert :** Le test des "10 regles de decision" reste valide. Si Drakkar peut ecrire noir sur blanc 10 regles operationnelles directement integrables dans un agent IA, c'est un actif. Sinon, l'avantage de Drakkar est un avantage de comprehension du marche, pas un avantage de data.

### 2.4 Service-as-Software vs ESN : comment le marche valorisera Spider ?

Nathan : "Bah Palantir c'est ca non ? Je m'en fous du moyen, je veux creer un empire."

Reponse honnete. Mais le marche ne s'en fout pas, lui. Si Spider reste a 20% humain dans la boucle, les investisseurs le valorisent comme une ESN (1-3x revenue). S'il descend a 5%, c'est un SaaS (10-20x). La difference entre les deux, pour le meme chiffre d'affaires, c'est un facteur 5 a 10 sur la valorisation.

Palantir a 3,800+ employes et vaut 400 milliards. Mais Palantir a mis 17 ans a atteindre la rentabilite. Nathan a-t-il 17 ans ? Non, il a dit 24 mois.

**Reponse de Nathan sur la valorisation : "Idk."**

### 2.5 La fenetre 24 mois : pour qui ?

Nathan ne sait pas si la fenetre de 24 mois concerne le monde ou la France. C'est un probleme.

- Si c'est le monde : Spider est en retard. Les "AI employees" americains (11x.ai, Artisan, Lindy) sont finances a 50M+ et se deploient maintenant.
- Si c'est la France : Spider a peut-etre 3-5 ans. Benoit Vasseur (The Tribe, 70+ personnes, Nantes) ne voit meme pas la disruption arriver. Les PME francaises sont a 90% en phase 1 de l'IA (chatbot basique).

La these dit "2026-2028." Mais la these parle de l'Europe, pas specifiquement de la France. Et Nathan lui-meme reconnait qu'il vit dans une "microbulle YC."

**Question ouverte :** Le timing exact importe moins que la direction. Mais il faut decider : on attaque la France (plus de temps, moins de competition, marche plus lent) ou on vise plus large (moins de temps, plus de competition, marche plus mature) ?

### 2.6 Capgemini, Accenture : cibles ou menaces ?

Nathan : "Actuellement Capgemini etc n'ont pas de Spider. Apres, est-ce que ca va changer ? Est-ce qu'a l'inverse c'est eux nos cibles ? Idk."

Deux scenarios :
1. **Ils bougent.** Accenture lance "AI Managed Services for SMBs." Ils ont la marque, la force de vente, les milliers de consultants. Spider est ecrase.
2. **Ils ne bougent pas.** Parce que les PME a 990EUR/mois ne les interessent pas. Leur ticket moyen est 100x plus eleve. Spider occupe un no man's land commercial que personne ne veut.

Le scenario 2 est le plus probable a court terme. Mais a long terme, si Spider prouve le modele, les gros viendront. La question n'est pas "est-ce qu'ils viendront" mais "combien de temps avant qu'ils viennent, et combien de data aura-t-on accumule d'ici la."

### 2.7 Le pitch en 30 secondes

Nathan : "A toi de me dire. Ca sera justement une des finalites de notre travail."

Clair. C'est un des livrables. Pistes a tester :
- "On fait tourner votre back-office pour 990EUR/mois. Vous, vous vous occupez de vos clients."
- "Embauchez un agent IA. Il ne dort pas, ne demande pas d'augmentation, et connait votre metier."
- "Arretez de saisir 3 fois les memes donnees. Spider le fait pour vous."
- "Le clone de Marie. Sans ego, sans arret maladie, sans demande d'augmentation."

Le bon pitch dependra du persona. Un dirigeant familial n'entend pas le meme message qu'un repreneur corporate. A tester sur 10 dirigeants PME qui ne sont PAS des amis.

### 2.8 Le role exact de Thierry

Nathan clarifie : Thierry n'est pas un FDE au sens Palantir. Il n'est pas ingenieur. Mais il a ete head of manufacturing chez Airbus et conseiller au COMEX. Skills de consulting de tres haut niveau. "Il apprendra."

La question reste : un FDE Palantir deploie du code en production chez le client. Un consultant Drakkar fait du diagnostic strategique. Ce ne sont pas les memes competences. Nathan le reconnait : "Ah oui, j'avais pas compris, bah du coup non mais a voir comment on fait."

**Proposition :** Dissocier les roles. Les FDE (deploiement technique) sont des profils tech a recruter. Thierry est un "Forward Deployed Consultant" -- le bras diagnostic, pas le bras technique. Les deux sont necessaires. Ce n'est pas un probleme, mais il faut le nommer clairement.

---

## 3. NOUVELLES QUESTIONS (ce qui emerge des reponses de Nathan)

### 3.1 L'aveu Palantir : "je m'en fous du moyen, je veux creer un empire"

C'est la phrase la plus revelatrice de la session. Elle dit : la vision prime sur le modele. L'ambition n'est pas negociable. L'execution, si.

C'est une force (conviction, direction) et un risque (si le moyen est mauvais, l'empire ne se construit pas). Un empire a besoin d'un moat. Si le moat est la data captive (pas le code, pas les features), alors la VITESSE de capture est tout.

**Les questions qui en decoulent :**
- A quelle vitesse Spider peut-il aller de 1 a 100 clients ? De 100 a 1000 ?
- Quel est le CAC (cout d'acquisition client) realiste pour une PME francaise ?
- Quelle est la courbe de croissance realiste sachant que les PME francaises sont des adopteurs lents ?
- Si ca prend 5 ans pour atteindre 1000 clients, est-ce que la data accumulee par les 100 premiers suffit a creer un moat ?

### 3.2 Le paradoxe de la capture du tacite

Nathan admet que Drakkar a echoue a capturer le tacite chez Decotec. Spider promet que l'IA le fera automatiquement. Mais si les FDE/consultants doivent d'abord comprendre le metier du client pour configurer Spider, on retombe dans la meme dependance humaine que Drakkar.

**La vraie question :** Qu'est-ce qui rend la capture de Spider fondamentalement differente de la capture de Drakkar -- au-dela de la couche de persistance ?

Hypothese : Drakkar capturait via des rapports, des reunions, des observations. L'information mourrait dans la tete du consultant. Spider capture via des connecteurs automatiques (emails, ERP, CRM, calendrier). L'information se structure automatiquement.

Si c'est ca, le vrai avantage n'est pas "on comprend le metier" mais "on se branche sur les flux de donnees existants et l'IA extrait le tacite." Ca ne necessite pas de comprendre le metier en amont -- ca le revele.

**Mais alors :** le consultant FDE n'a pas besoin d'etre un expert metier. Il a besoin d'etre un expert en connexion de sources et en validation de claims. C'est un profil technique, pas consulting. Ce qui contredit le role prevu pour Thierry (consulting pur).

### 3.3 Le prototype 2h30 : preuve ou piege ?

Nathan dit avoir construit le prototype Jordan en 2h30. Si c'est vrai, c'est extraordinaire. Mais ca veut aussi dire que n'importe quel developpeur competent peut faire la meme chose.

La question n'est pas "est-ce que Spider peut resoudre le probleme de Jordan ?" -- c'est oui. La question est : "est-ce que Spider peut le resoudre d'une maniere qui cree un avantage cumulatif ?"

Si chaque nouveau client demande 2h30 de travail custom, c'est du consulting rapide, pas un SaaS. Si le travail fait pour Jordan rend le travail pour le client 2 plus rapide (et le client 5 quasi-gratuit), c'est un flywheel.

**Hypothese a valider (H4 de la strategy) :** L'ontology se transfère d'un client a l'autre dans le meme vertical. Le cas Jordan (pub exterieure, 726 campagnes, memes reseaux JCDecaux/Clear Channel/Giraudy) se replique directement. Le temps d'onboarding du client 5 est < 60% du temps du client 1. Si ce n'est pas le cas, on est dans un modele de consulting accelere, pas dans un modele de plateforme.

### 3.4 Le vide de pricing

Nathan admet ne pas savoir le prix. Mais les documents donnent 4 modeles differents :

| Source | Prix |
|--------|------|
| These Nathan | 500-5,000 EUR/mois |
| Strategy Jordan | 990 EUR/mois |
| BMAD PRD | 49 EUR/utilisateur/mois |
| DRK Data Copilot (Jean) | 2,000-5,000 EUR/mois + setup |

Quatre modeles = aucun modele. Avant d'approcher un seul client, Spider a besoin d'UNE hypothese de prix a tester. Pas un range. Un chiffre. Qui sera faux -- et qu'on ajustera ensuite.

**Proposition :** 990 EUR/mois all-inclusive pour Jordan (le chiffre de la strategy doc). C'est le prix a tester. Si Jordan renouvelle a 990, on a un data point. Si Jordan negocie a 500, on a un autre data point. Mais on commence avec UN chiffre.

### 3.5 Le cheval de Troie gratuit : et la preuve de revenus ?

Nathan dit que Spider People et le chatbot pourraient etre gratuits ou a l'usage, comme point d'entree dans les PME. Strategie land-and-expand classique. Intelligente.

Mais : des utilisateurs gratuits ne prouvent pas la capacite a generer du revenu. Et si Spider a besoin de financement (meme petit), les investisseurs regarderont le revenu, pas les utilisateurs gratuits.

**Le risque :** on passe 12 mois a construire un produit gratuit que 500 PME utilisent, mais personne ne convertit en paye. On a de la traction d'usage, zero traction de revenu.

**La garde-fou :** le modele a deux vitesses doit etre teste simultanement. Le chatbot gratuit ET les agents payants des le mois 1. Si l'un sans l'autre ne fonctionne pas, on le saura vite.

### 3.6 La scalabilite du modele consulting

Si chaque client necessite un setup consulting (le modele FDE), le business scale avec le headcount. Palantir a 3,800+ employes pour ~600 clients gouvernementaux et entreprises. C'est un ratio d'environ 6 employes par client.

Drakkar a ~25 personnes. Meme avec un ratio plus leger (Spider est plus automatise que Palantir), combien de FDE faut-il pour servir 100 clients ? 1000 ?

| Clients | FDE necessaires (ratio 1:10) | FDE necessaires (ratio 1:20) | FDE necessaires (ratio 1:5) |
|---------|------------------------------|------------------------------|-----------------------------|
| 10 | 1 | 0.5 | 2 |
| 100 | 10 | 5 | 20 |
| 1000 | 100 | 50 | 200 |

Le ratio s'ameliore-t-il avec le temps (parce que l'ontology se transfere et l'IA prend le relais) ou reste-t-il constant (parce que chaque PME est unique et demande du travail custom) ?

**C'est la question fondamentale du modele economique.** Si le ratio stagne, Spider est une ESN avec de l'IA. Si le ratio s'ameliore exponentiellement, Spider est un SaaS deguise en ESN. Toute la these repose sur l'amelioration du ratio.

### 3.7 Le premier mouvement en France : education vs capture

Nathan vit dans une "microbulle YC." Benoit Vasseur (The Tribe, 70+ personnes) ne voit pas la disruption. Twoghether a choisi la reassurance (The Tribe) plutot que l'innovation (Drakkar) en fevrier 2026.

Ca coupe dans les deux sens :
- Moins de competition maintenant. Spider peut se positionner sans se battre.
- Mais aussi : pas d'education du marche. Les PME francaises ne savent pas qu'elles ont besoin de Spider. Elles ne cherchent pas la solution.

Spider devra peut-etre CREER le marche avant de vendre dedans. Le "diagnostic gratuit" est une forme d'education (on montre le probleme avant de vendre la solution). Mais ca demande du temps et de l'energie commerciale.

**Question :** Quel est le budget et le plan pour eduquer le marche ? Le diagnostic gratuit suffit-il ? Faut-il du contenu (LinkedIn, podcast, cas clients publies) ? Faut-il des partenariats (CCI, BPI, clubs de dirigeants) ?

---

## 4. HYPOTHESES A VALIDER (par ordre de priorite)

### Priorite 1 : Hypotheses de survie (si fausses, Spider s'arrete)

| # | Hypothese | Comment tester | Signal d'arret |
|---|-----------|----------------|----------------|
| H1 | Un dirigeant PME paie 990 EUR/mois pour un service gere par Spider | Jordan accepte de payer 990 EUR apres le mois gratuit, sans negociation de prix "entre amis" | Jordan negocie sous 500 EUR ou refuse de payer |
| H2 | L'IA peut gerer 50%+ des taches avec supervision humaine en 6 mois | Tracker le ratio AI/humain par process, chaque mois, chez Jordan | Le ratio reste < 40% AI apres 6 mois |
| H3 | Un deuxieme client qui n'est PAS un ami paie le prix demande | Vendre a un prospect Drakkar ou nouveau dans les 90 jours | Aucun client non-ami ne signe en 90 jours |

### Priorite 2 : Hypotheses de croissance (si fausses, Spider pivote)

| # | Hypothese | Comment tester | Signal de pivot |
|---|-----------|----------------|----------------|
| H4 | L'ontology se transfère entre clients du meme vertical | Mesurer le temps d'onboarding : client 1 vs client 5 dans la pub exterieure | Client 5 prend > 60% du temps du client 1 |
| H5 | Le chatbot gratuit convertit en agents payants | Deployer le chatbot chez 20 PME, mesurer le taux de conversion | Conversion < 10% en 3 mois |
| H6 | Le ratio FDE:clients s'ameliore dans le temps | Tracker les heures humaines par client par mois sur 12 mois | Les heures ne baissent pas apres 6 mois |

### Priorite 3 : Hypotheses de vision (si fausses, Spider marche mais n'est pas un empire)

| # | Hypothese | Comment tester | Implication si faux |
|---|-----------|----------------|---------------------|
| H7 | La data captive cree un moat que les concurrents ne peuvent pas repliquer | Apres 100 clients, evaluer si un nouvel entrant pourrait reproduire le service en partant de zero | Spider est un bon business, pas un monopole |
| H8 | Le mycelium (Phase 2) cree de la valeur inter-entreprise | Apres 50 clients, identifier si Spider detecte des patterns cross-clients utiles | Spider reste un outil par-client, pas un reseau |
| H9 | Le marche valorise Spider comme un SaaS, pas comme une ESN | Quand on leve (si on leve), le multiple propose par les investisseurs | Si multiple < 5x, le marche voit une ESN |

---

## 5. ANGLES MORTS ET RISQUES

### 5.1 Le risque de confirmation

Nathan est son meilleur avocat. La these est brillante, coherente, convaincante. Le danger : on cherche des donnees qui confirment la these au lieu de donnees qui l'infirment.

**Garde-fou concret :** Definir a l'avance ce qui tuerait la these. Si Jordan ne renouvelle pas, c'est un signal. Si aucun client non-ami ne signe en 90 jours, c'est un signal. Si le ratio AI/humain ne s'ameliore pas, c'est un signal. Ecrire ces kill criteria AVANT le lancement et s'y tenir.

### 5.2 Le risque de dispersion

Nathan est CEO Drakkar + architecte Spider + vendeur + stratege + diagnostiqueur terrain. Remy est CTO. Meme avec l'AI coding, construire Spider + operer Drakkar + servir Jordan + trouver de nouveaux clients + ecrire la strategie + gerer Jean + preparer le cap table = beaucoup pour deux personnes.

Le risque n'est pas l'echec. C'est l'epuisement.

### 5.3 Le risque Drakkar

Spider est finance par Drakkar (1.5M EUR/an de CA). Mais Decotec vient de partir. Twoghether a choisi The Tribe. Si Drakkar perd encore 2-3 clients, la tresorerie qui finance Spider se tarit.

Spider doit generer du revenu propre avant que Drakkar ne puisse plus le porter. C'est une course contre deux horloges : la fenetre de marche ET la tresorerie interne.

### 5.4 Le risque de complexite

La stack cible comprend 6 apps Next.js, 4 backends Litestar, PostgreSQL HA, SurrealDB + TiKV, Redis, Zitadel, Nango, KubeSphere, 3 clusters K8s, un AI gateway, et un design system Storybook. Nathan dit que c'est pret et que l'AI coding accelere tout.

Peut-etre. Mais chaque composant ajoute est un point de defaillance. Et chaque minute passee sur l'infra est une minute pas passee avec un client. La question n'est pas "peut-on le construire ?" mais "faut-il le construire maintenant, ou livrer avec un monolithe PostgreSQL qui marche et iterer ensuite ?"

Nathan a reporte cette question. Elle reviendra.

### 5.5 Le risque de marche : l'inertie francaise

90% des PME francaises n'utilisent pas l'IA au-dela du chatbot basique. Le marche n'est pas "early adopter." Il est "late majority" au mieux. Spider devra convaincre des gens qui ne cherchent pas a etre convaincus, dans un pays ou changer de logiciel est un evenement qui prend 18 mois.

La these dit que la triple convergence (crise, transmission, IA) force l'adoption. Mais Benoit Vasseur, avec 70+ employes dans la tech, ne voit pas cette convergence. Si un patron tech ne la voit pas, un patron PME industrielle la verra encore moins.

---

## 6. PROCHAINES ETAPES RECOMMANDEES

### Immediat (cette semaine)

1. **Fixer le prix Jordan a 990 EUR/mois.** Pas de fourchette. Pas de negociation. Tester ce prix unique. Ajuster ensuite selon la reaction.
2. **Ecrire 3 versions du pitch en 30 secondes.** Les tester sur Jordan d'abord, puis sur 5 dirigeants PME non-amis.
3. **Rediger les kill criteria formels.** Si X arrive, on arrete/pivote. Avant de lancer, pas apres.

### Court terme (1 mois)

4. **Livrer le prototype Jordan.** Valider l'elimination de la triple saisie. Mesurer le temps reel (2h30 annonce vs realite).
5. **Tracker le ratio AI/humain des le jour 1.** Chaque tache = tag "AI" ou "humain." C'est la metrique qui decide si Spider est un SaaS ou une ESN.
6. **Identifier 5 prospects non-amis.** Clients Drakkar existants ou nouveaux. Au moins 2 doivent etre hors du reseau personnel de Nathan.

### Moyen terme (3 mois)

7. **G1 : Jordan renouvelle-t-il a 990 EUR/mois ?** Si oui, premier signal. Si non, pourquoi ?
8. **Tester le chatbot gratuit.** Deployer chez 10-20 PME. Mesurer : combien l'utilisent ? Combien demandent plus ? Combien convertissent ?
9. **Formaliser l'ontology.** Ecrire les 10 premieres "regles operationnelles" que Drakkar connait et qui sont integrables dans un agent IA. Si on n'arrive pas a en ecrire 10, l'actif est narratif, pas structurel.
10. **Definir le profil FDE technique.** Ce n'est pas Thierry (consulting). C'est un profil tech qui sait connecter des sources, valider des claims, et configurer des agents. A recruter ou former.

### Long terme (6-12 mois)

11. **Atteindre 5 clients payants.** Dont au moins 3 non-amis, a au moins 500 EUR/mois chacun.
12. **Prouver l'amelioration du ratio AI/humain.** Si apres 6 mois le ratio n'a pas bouge, repenser le modele economique.
13. **Valider le transfert d'ontology.** Le client 5 doit couter significativement moins a onboarder que le client 1.
14. **Decider de la structure juridique.** Spider reste dans Drakkar ou devient une entite separee. La reponse depend des resultats, pas d'un plan predefini.

---

*Document v2 -- 19 fevrier 2026. Integre les reponses de Nathan du meme jour.*
*Les questions ne sont pas des critiques. Ce sont des instruments de precision.*
