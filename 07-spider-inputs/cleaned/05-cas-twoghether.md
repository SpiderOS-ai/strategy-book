# 05 - Cas Twoghether : deal perdu, double lecon

## Contexte

- **Nature** : Deal perdu face a The Tribe (concurrent). Double lecon : (1) le modele agence est disrupte MAINTENANT, (2) Nathan vit dans une bulle.
- **Fiabilite** : Haute -- deal reel, conversations reelles, perte reelle
- **Personnes cles** :
  - Benoit Vasseur = CEO The Tribe (concurrent/ami de Nathan, 70+ personnes)
  - Angelique = CEO Twoghether (fondatrice, finance le projet, famille aisee)
  - Maxime = commercial Twoghether (contact principal)
  - Yoann = developpeur unique Twoghether (salarie, distant)
  - Thibault Piqueras = commercial Drakkar
  - Matthis Ruel = PO/PM Drakkar, responsable studio
- **Insight cle** : Les acheteurs choisissent l'emotion plutot que la raison. Le modele agence est le marche de la reassurance, pas de la competence.

---

## Timeline du deal

| Date | Evenement | Source |
|------|-----------|--------|
| 17/11/2025 | RDV #1 - Qualification telephonique (Thibault x Maxime) | Aircall |
| 26/11/2025 | RDV #2 - Decouverte des besoins (Nathan, Thibault, Maxime, Angelique, Yohan en visio) | Noota, en personne chez Drakkar |
| 21/01/2026 | RDV #3 - Point suite lancement app (Nathan, Thibault, Maxime, Angelique) | Noota, visio |
| 04/02/2026 | RDV #4 - Rapport audit et echanges collaboration (Nathan, Matthis, Thibault, Maxime) | Noota, visio |
| ~10/02/2026 | Annonce de la perte -- Twoghether part chez The Tribe | Slack interne |
| ~10/02/2026 | Appel Nathan x Maxime (debriefing) | Transcript auto |
| ~10/02/2026 | Echange Benoit (CEO The Tribe) x Nathan | Messages directs |

---

## 1. RDV #1 -- Qualification (17/11/2025)

**Contexte** : Maxime appelle Drakkar suite a une rencontre avec Nathan l'ete precedent. Premier contact telephonique avec Thibault.

**Twoghether en bref** :
- Plateforme de mise en relation de particuliers pour services a la personne
- Differenciateur : connexion directe API URSSAF (toute prestation declaree)
- Equipe : 3 personnes (Angelique fondatrice, Maxime commercial, Yoann developpeur distant)
- Premier dev fait par une agence externe (mal fait), Yoann reprend depuis un an
- Lancement prevu : 5 janvier 2026
- Budget limite (2 ans sans revenus)

**Double besoin exprime** :
1. Application mobile (site pas responsive, Yoann ne maitrise que Android)
2. Backup technique (risque si Yoann malade ou surcharge)

**Signaux importants** :
- Maxime dit avoir "bien matche" avec Nathan
- Ils sondent agences et freelances en parallele
- Maxime previent : "ne pas faire peur a la fondatrice", budget serre, cherchent une agence qui "demarre avec nous"

**RDV suivant cale** : 3 decembre (reporte au 26 novembre finalement)

---

## 2. RDV #2 -- Decouverte des besoins (26/11/2025)

**Contexte** : Premier vrai echange en personne chez Drakkar. Nathan, Thibault, Maxime, Angelique, Yoann (en visio).

**Decouvertes cles** :
- Stack : Laravel (back) + React (front), hebergement OVH
- Yoann fait tout seul, full stack mais pas expert iOS
- L'agence initiale a livre un MVP bancal, Yoann a repris en gardant la base (pas de refonte)
- PWA prevue (pas d'app native)
- Agence de com Hello10/LMWR pour la refonte UX
- Pas de PM/PO, gestion de projet empirique
- Nathan detecte de la dette technique significative

**Nathan presente Drakkar** :
- 7 personnes, trois poles (IA, Dev sur-mesure, ERP)
- 60-70 startups accompagnees historiquement, ~100 clients total
- Cas similaire : Marketface (Blaise Matuidi) -- marketplace de coaching foot
- Framework AARRR, insistance sur la retention comme metrique cle

**Position de Nathan** :
- Ne pas sur-investir maintenant, lancer d'abord et mesurer la traction
- Besoin d'un PM/PO plus que de dev supplementaire
- Proposition d'un point de suivi apres lancement

**Rendez-vous suivant cale pour mi-janvier**

---

## 3. RDV #3 -- Point suite lancement (21/01/2026)

**Contexte** : L'app est lancee depuis 10 jours, com sur reseaux lancee la veille. Premiers inscrits.

**Etat des lieux Twoghether** :
- Site lance, com Meta demarree
- Seuls les prestataires peuvent s'inscrire (clients ouverts le 2 fevrier)
- Bugs en cours de resolution (inscription Stripe Connect)
- Sortie App Store retardee, PWA Android pas optimisee
- Calendrier des disponibilites = UX "degueulasse" (citation Maxime)
- Yoann refuse de refaire le calendrier, dit que c'est trop complexe

**Diagnostic de Nathan (cash, a la demande de Maxime)** :

Nathan est pousse par Maxime a etre direct : "Sois cash parce que je sens que tu cherches tes mots vraiment. Vas-y."

Points souleves :
- **Velocite trop faible** : les fonctionnalites mettent beaucoup trop de temps a sortir
- **Dette technique accumulee** : chaque nouvelle feature risque de casser autre chose, pas de tests
- **Dev seul sans cadre** : Yoann n'utilise pas l'IA, pas les librairies modernes, recode tout from scratch
- **Pas de PM** : Maxime et Angelique ne peuvent pas challenger techniquement
- **Si on recodait tout de zero, ca irait 4-5x plus vite** -- la vraie valeur du MVP c'est la comprehension metier, pas le code

Citation cle de Maxime : "Vous nous posez des questions qui nous emmerdent. C'est des bonnes questions, mais elles nous emmerdent parce qu'on a de la misere a y repondre."

**Conclusion** : Nathan propose un audit + acces au code source. RDV cale le 4 fevrier. Audit chiffre a 2K EUR.

---

## 4. RDV #4 -- Rapport d'audit et echanges collaboration (04/02/2026)

**Contexte** : Drakkar presente son diagnostic complet. Nathan, Matthis (PO/PM), Thibault, Maxime present.

### 4.1 Etat business Twoghether

- Lancement tres light, com ne porte pas assez ses fruits
- Problemes UX dans les 5 premieres minutes post-inscription
- Maxime : "On est sur un debut quand meme un peu tres light"

### 4.2 Diagnostic gestion de projet (Matthis)

**Retour design/Figma** : Positif. Fichier propre, design sympa, bonnes regles de margin/spacing. Manque le parcours fonctionnel complet (reservation, paiement).

**Constats negatifs** :
1. **Melange de granularite** : taches dev, actions commerciales et decisions strategiques dans la meme vue
2. **Cahier des charges qui n'en est pas un** : retours utilisateurs, idees, bugs, questions melanges. Pas de statut, pas de priorite, pas d'assignation
3. **Priorisation absente** : colonne "Importance" vide, "V2" comme fourre-tout

**Citation cle de Matthis** : "Le developpeur travaille a l'aveugle, en piochant dans un flux de demandes non triees. Ce n'est pas un probleme de competences. C'est l'absence d'une couche PM entre la vision et l'execution."

### 4.3 Diagnostic technique (Nathan)

**Rapport d'audit complet (PDF confidentiel Drakkar)** :

Metriques de couverture :
| Critere | Valeur |
|---------|--------|
| Couverture tests | **0%** |
| Ratio inefficience | **6.4x** |
| Presence dev | **44%** |
| Duree projet | **36 mois** |

Stack : React 18 + Laravel 10 + Socket.io. Environ 63K lignes de code (32K TypeScript, 31K PHP).

**Diagnostic technique detaille** :

| Critere | Etat | Criticite |
|---------|------|-----------|
| Architecture backend | Clean Architecture + DDD | SOLIDE |
| Design Patterns | Action pattern + ACL | BON |
| Qualite code | Variable selon zones | MOYEN |
| Securite | 45 vulnerabilites (1 critique) | CRITIQUE |
| Stack frontend | CRA abandonne (EOL) | CRITIQUE |
| Stack backend | Laravel 10 EOL fev. 2025 | CRITIQUE |
| Tests | 0 fichiers sur 906 | CRITIQUE |
| CI/CD | Inexistant | CRITIQUE |

**Dependances critiques** :
- axios ^0.22.0 : Faille de securite critique CVE-2025-27152
- react-scripts (CRA) ^5.0.1 : Projet abandonne par Facebook -- migration requise
- moment.js ^2.29.4 : Obsolete (67KB) -- remplacer par dayjs (2KB)
- laravel/framework ^10.0 : Fin de support fevrier 2025

**Librairies manquantes** : Pas de Redux/Zustand (state management), pas de TanStack Query (data fetching), pas de PHPStan (analyse statique).

**Points forts** : Architecture backend bien pensee, deploiement automatise via Deployer, Sentry configure pour le monitoring.

**Analyse des commits** :

Deux equipes distinctes sur 36 mois :

| | Agence externe | Yoann (interne) |
|--|---------------|----------------|
| Periode | Fev 2023 - Oct 2024 (20 mois) | Nov 2024 - Jan 2026 (15 mois) |
| Commits | 1045 | 249 |
| Bug ratio | 39.5% | 35.3% |
| Developpeurs | 5 | 1 |
| Presence | - | 44% |

Repartition par epic :

| Module | Agence | Yoann | Bug ratio | Description |
|--------|--------|-------|-----------|-------------|
| AUTH | 107 | 17 | 42% | OAuth, sessions, inscription CESU |
| BOOKING | 108 | 10 | 38% | Reservations, disponibilites, calendrier |
| SERVICES | 81 | 19 | 35% | Catalogue, categories, pricing, filtres |
| PAYMENT | 69 | 13 | 55% | Stripe Connect, factures -- zone instable |
| MESSAGING | 73 | 7 | 40% | Socket.io, notifications temps reel |
| ADMIN | 65 | -- | 61% | Backoffice complet -- dette elevee |
| CESU/URSSAF | 10 | 20 | 33% | Integration URSSAF, CESU+, AICI |
| KYC | -- | 4 | 25% | Dataleon v1 + v2 -- from scratch |
| ADS/B2B | -- | 12 | 17% | Publicites, fonctionnalites B2B -- from scratch |

Observation cle : Les modules crees from scratch par Yoann ont un bug ratio 2x meilleur (17-25% vs 40-61%).

Metriques globales : 500 commits bug/fix (41% du total), 14 commits refactoring (1%), 91 jours d'iteration consecutifs, 31% du code reecrit.

**Metriques d'inefficience** :

| Metrique | Valeur | Interpretation |
|----------|--------|---------------|
| Temps reel consomme | ~566 jours | Agence + Yoann cumules |
| Temps optimal estime | ~88 jours | Senior focalise, specs claires, bonne archi |
| Ratio d'inefficience | 6.4x | On a mis 6x plus de temps que necessaire |
| Jours avec activite | 298 jours | Sur 36 mois (~780 jours ouvres) = 38% d'activite |

Sources d'inefficience : context switching, absence de specs, dette technique (sans tests, chaque modification peut casser autre chose), presence fractionnee (44% = perte de contexte entre chaque session).

**Prise de hauteur (Nathan)** :

"Ce projet n'a pas un probleme de developpeur. Il a un probleme de structure."

Profil estime de Yoann :
- Niveau : Mid-level (3-5 ans). Maitrise Laravel/React, applique les patterns existants. Execute bien quand les specs sont claires.
- Forces : Autonome, fiable. Ses creations from scratch (KYC, ADS) sont plus stables que le code herite.
- Limites -- Tests : dans les deux cas, c'est un manque de cadre.
- Limites -- Proactivite tech : n'escalade pas les alertes securite, attend qu'on lui dise.
- Limites -- IA & outils modernes : aucune trace d'utilisation d'outils IA (Copilot, ChatGPT). Pas de CI/CD mis en place. Travaille "a l'ancienne".
- Verdict : Bon executant dans un systeme dysfonctionnel. Avec un PM, un cadre clair et de l'outillage moderne, sa velocite doublerait.

Le vrai probleme :
- **Pas de PM** : aucune priorisation, Yoann pioche dans un flux de demandes non triees
- **Pas de CTO** : personne pour arbitrer tech vs produit (migration Laravel 11 ? tests ? securite ? tout est reporte indefiniment)
- **Presence fractionnee** : 44% = context switching permanent, cout cognitif enorme
- **Dette invisible** : 0 tests = pas de filet de securite, chaque modification peut tout casser

### 4.4 Proposition d'audit

Forfait a 2K EUR, 2 jours :

| Phase | Objectif |
|-------|----------|
| Jour 1 - Matin | Atelier vision : objectifs court/moyen/long terme, documentation des priorites par pilier |
| Jour 1 - Apres-midi | Restructuration backlog, priorisation MoSCoW, definition des workflows de developpement |
| Jour 2 - Matin | Audit technique approfondi : analyse module par module, cartographie de la dette |
| Jour 2 - Apres-midi | Restitution : diagnostic complet + roadmap avec jalons et points de decision |

Livrables : Rapport complet, backlog restructure, plan securite immediat, roadmap 3-6-12 mois.

### 4.5 Scenarios d'accompagnement proposes

| Scenario | Horizon | Description |
|----------|---------|-------------|
| A -- Stabilisation urgente | Court terme | Patch vulnerabilites, CI/CD minimal, tests sur zones sensibles (PAYMENT, AUTH). Accompagnement ponctuel de Yoann. |
| B -- Reprise Front + Mobile | Moyen terme | Le backend Clean Architecture est solide. Le front CRA est le point faible. Migration vers Vite/Next.js, refonte progressive + app mobile. Yoann reste sur le backend, Drakkar prend le front. |
| C -- Modernisation complete | Long terme | Upgrade Laravel 11+, migration TypeScript 5, TanStack Query + Zustand, architecture de tests (80% coverage zones critiques), monitoring. |
| D -- CTO/CPO fractionne | Structurel | Drakkar comme CTO ou CPO externalise. Pilotage du developpeur, structuration backlog, arbitrages techniques, reviews de code. 1-2 jours/semaine. |

Dimensionnement typique : 1 PO mi-temps + 2 devs full time, pendant 1-3 mois pour une refonte. CTO/CPO fractionne : 1 jour/semaine.

---

## 5. La perte -- Echange interne Slack (~10/02/2026)

> **Thibault Piqueras** [3:29 PM]
> Bon mauvaise nouvelle... Twoghether part chez The Tribe...
>
> **Nathan Menard** [3:29 PM]
> Wow
> Ok
> Qu'est-ce qui les a convaincu?
>
> **Thibault Piqueras** [3:30 PM]
> En gros ils ont ete plus rassures sur la suite, du fait qu'ils soient peu staffe, The Tribe a deja propose un plan de route et de reprise. Une roadmap qui les a rassure...
> Ils se sont davantage projetes avec eux
>
> **Nathan Menard** [3:31 PM]
> Je pense qu'il faut essayer de les retourner
> The Tribe ils sont plus chers et moins bons sur ces sujets
>
> **Thibault Piqueras** [3:32 PM]
> Ok tu as une idee en tete ?
>
> **Nathan Menard** [3:33 PM]
> Faut qu'ils nous laissent faire l'audit
> The Tribe ils ont la dalle
> Ils l'ont dit, pas bcp staffe
> Donc evidemment plan de route etc... ils veulent placer LEURS equipes. Ils vont les saigner le plus possible
> Nous on va mettre de l'agilite pour qu'ils aillent aux mieux
> Et ils ont pas les moyens de se payer une agence de 70+ personnes en vrai

---

## 6. La perte -- Appel Nathan x Maxime (debriefing)

Transcript automatique, qualite audio variable. Points cles extraits :

**Ce que Maxime dit sur pourquoi The Tribe a gagne** :

- "On a eu le sentiment qu'ils ont parfaitement compris notre business et ils nous ont rassure sur la suite des evenements."
- "On avait la capacite suite a un point avec The Tribe de se projeter vraiment, alors qu'avec vous, ca restait [...] un peu plus de misere a se projeter."
- "C'est vraiment une histoire de feeling notamment de la part d'Angelique qui va financer ca."
- Ils ont vu Benoit en direct + leads devs + product designers + PM
- "Ils ont ete assez pertinents [...] qui ont tape avec des arguments pile, enfin, qui font mouche"

**Ce que Nathan comprend** :

- "Je pense qu'on n'a pas joue au meme jeu entre les autres et nous."
- "Eux forcément, ils l'ont fait, on va dire un peu plus commercial, a essayer de vous projeter."
- "C'est une grosse machine. Necessairement, ca va etre rassurant au debut, mais vous allez etre dans un axe qui va vous faire beaucoup avancer sur du [dev], mais vous n'allez pas avoir assez d'iterations terrain."
- Nathan reconnait que Drakkar s'est arrete trop tot dans la projection

**Ce que Maxime dit sur Drakkar** :

- "Ca ne remet pas du tout en cause ce que vous avez propose, qu'on a aime."
- "Je t'avais contacte parce que j'avais bien aime la maniere que tu avais de te presenter."
- "Ca veut pas dire qu'on n'aura pas de besoins a moyen long terme."
- "Notre presentation nous a fait prendre conscience qu'il y a des choses qui n'allaient pas, mais ca nous a laisse une espece de boule dans le ventre en disant putain, mais est-ce qu'on y arrivera ?"
- **"Peut-etre que sur les petites equipes, il y a cette notion de rassurant a amener un peu plus."**

---

## 7. La perte -- Echange Benoit (CEO The Tribe) x Nathan

**VERBATIM INTEGRAL -- intelligence strategique critique** :

> **Benoit** : Hello Nathan, il semblerait qu'on etait l'un en face de l'autre sur twoghether
> C'est rare
> On a gagne cette fois ci mais Angelique nous a dit que tu avais ete tres smart dans l'approche
>
> **Nathan** : Hello Benoit,
> Merci pour le message et bravo pour le closing ! J'ai su que c'etait vous seulement a la toute fin, sinon je t'aurais passe un coup de fil directement. Marrant de se recroiser sur des dossiers, surtout sur cette taille
> En vrai, le sujet m'interessait au-dela du deal : je trouve que le modele product studio sur les projets startups/innovation est completement disrupte par l'IA. Ca va encore plus vite que ce que je pensais (et pourtant je suis bullish). Curieux d'avoir ton regard la-dessus a l'occasion !
>
> **B** : L'IA est en train de changer completement le game, c'est a la fois excitant et terrifiant
> On en parle a l'occaz !
> PS : j'ai vendu un premier truc a 16k sur twoghether mais je compte vendre 80k dans un mois et je l'ai verbalise avec Angelique qui n'a pas specialement eu peur du chiffre
>
> **N** : Bien joue ! Je voyais le potentiel vu la famille de madame mais j'avais pas la bande passante pour l'avant-vente ni la phase 1, du coup j'avais pousse un premier truc a 2k pour entrer, gagner du temps et construire derriere. Au final je pense que ca leur a fait peur et que vous avez fait une grosse partie de ce qu'on proposait directement en avant-vente.
> Mais c'est exactement le sujet : au final on serait arrive sur un pricing similaire, mais je me dis que ces scopes a 50-100k, potentiel 200k+ si ca marche bien, pour l'instant ca tient... Mais avec la vitesse a laquelle l'IA compresse les couts de delivery, je me demande combien de temps
> J'ai l'impression qu'il faut soit faire du volume massif et dans le lot avoir une ou plusieurs pepites, soit changer de cible. Y'a peut-etre une troisieme voie mais je vois pas. Nous on prend la deuxieme, focus PME/ETI
> Dis-moi si tu passes vers le Palace / Graslin prochainement qu'on se prenne un cafe, ou je viens te voir quand tu veux !
>
> **B** : Je partage le constat mais dans 2 ans
> Moi la periode me donne envie de lancer des SaaS IA
> Le seul probleme c'est que ma boite a trop besoin de moi
>
> **N** : Je pense c'est un peu plus tot mais peu importe, tout ca arrive vite mine de rien
>
> **B** : oui
>
> **N** : Ouais y'a jamais eu autant d'opportunites et de menaces a la fois. Apres pareil, la value d'un SaaS aujourd'hui et surtout demain c'est complique
>
> **B** : En tout cas, ca cree aussi sa vague d'attentisme niveau biz
>
> **N** : C'est vrai que j'etais surpris du peu de personnes que t'avais niveau sales. Tu dois pas mal enchainer entre tout ca. Apres c'est a toi de voir a quoi t'as envie d'allouer ton temps
> C'est a dire ?
>
> **B** : Les gens sont paumes et n'investissent plus
> A quoi bon investir si c'est perime dans 2 ans
>
> **N** : Ah
> Ouais mais a la fois ils commencent a jouer avec l'IA et ceux rendent comptent que pleins de choses sont possibles
> Du coup ca eduque aussi. Donc l'un dans l'autre je trouve ca va, voir meme que ca repart par rapport a avant

**Reflexion de Nathan (note personnelle)** : "hallucine que Benoit ne se rende pas compte en 2026 mais se rend compte que vis dans une microbulle YC etc et que encore enorme inertie sur les boites Francaises etc."

---

## Analyse de la perte -- Ce que ce cas revele

### Pourquoi Drakkar a perdu

1. **Sous-investissement en avant-vente** : Drakkar a propose un audit a 2K EUR comme porte d'entree. The Tribe a investi des jours entiers d'avant-vente avec des experts (lead devs, product designers, PM) + Benoit en direct.

2. **Pas de projection** : Drakkar a dit "faisons un bilan d'abord, on verra ensuite". The Tribe a dit "voila la roadmap, voila ou on vous emmene". Le client avait besoin de se projeter, pas d'un diagnostic.

3. **Effet "boule dans le ventre"** : Le diagnostic honnete de Drakkar a effraye le client au lieu de le rassurer. Citation Maxime : "Ca nous a laisse une espece de boule dans le ventre en disant putain, mais est-ce qu'on y arrivera ?"

4. **Le marche de la reassurance** : Angelique (la fondatrice qui finance) s'est sentie "plus safe" avec The Tribe. Le choix est emotionnel, pas rationnel. Maxime le dit : "C'est vraiment une histoire de feeling."

5. **Matthis n'a eu qu'une demi-heure** : The Tribe a fait intervenir des experts metier longuement. Nathan n'a fait intervenir Matthis que 30 minutes.

### Ce que Benoit revele (intelligence concurrentielle)

- The Tribe a la dalle : ils placent leurs equipes agressivement
- Premier deal a 16K, objectif 80K dans un mois (verbalise avec Angelique)
- Benoit reconnait que l'IA "change completement le game"
- Mais il situe le vrai impact "dans 2 ans" -- Nathan pense que c'est plus tot
- The Tribe a peu de commerciaux
- Attentisme du marche : "les gens sont paumes et n'investissent plus"

### La bulle de Nathan

Nathan note lui-meme qu'il est "hallucine que Benoit ne se rende pas compte en 2026" mais realise qu'il "vit dans une microbulle YC" et qu'il y a "encore enorme inertie sur les boites francaises". C'est un signal d'autocritique important : la disruption IA que Nathan voit comme imminente n'est pas encore percue par le marche.

### Lecons strategiques pour Spider/Drakkar

1. **Vendre la vision, pas le diagnostic** : Les gens n'achetent pas un bilan de sante, ils achetent la promesse de guerison.
2. **Le modele agence est le marche de la reassurance** : Tant que les clients ne sont pas tech-savvy, ils choisissent le prestataire qui les rassure le plus, pas le plus competent.
3. **Investir en avant-vente** : Ne pas sous-estimer le cout d'acquisition. Un audit a 2K semble "sans risque" mais peut effrayer par sa modestie face a un concurrent qui arrive avec une armada.
4. **L'inertie du marche francais est reelle** : Meme un CEO de 70+ personnes (Benoit) situe l'impact IA "dans 2 ans". Les PME sont encore plus en retard.
5. **La perte confirme la strategie** : Ce type de deal (startup, 50-200K de scope) est exactement le marche qui se fait disrupter. Nathan le sait, et ce deal le confirme. Le pivot vers PME/ETI + agents IA est la bonne direction.
