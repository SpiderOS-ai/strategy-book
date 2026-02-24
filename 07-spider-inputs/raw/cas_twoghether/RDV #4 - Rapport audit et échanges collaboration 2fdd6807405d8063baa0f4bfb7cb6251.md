# RDV #4 - Rapport audit et échanges collaboration

Date: 04/02/2026
Source: Noota Drakkar
Type: RDV prospect / client
Personnes présentes: Angélique Bessé, Matthis, Maxime Bernard resp commercial, Nathan, Thibault
Lien transcript: app.noota.io/share-transcribe/kkNG9lRLVnVV1kN2ADbt9VWBVWYvl2ZtgU1L44SUONTTq1EMVpWT
Status: Terminé

# Rapport d'audit & Roadmap — Compte-rendu de réunion

**Participants :** Matthis Ruel, Thibault Piqueras, Maxime Bernard, Nathan Ménard
**Date :** 2026-02-04

---

## Préambule & mise en place

**Thibault P.** 00:04
— On va mettre que celui-là, les autres on va les faire sauter.

**Thibault P.** 01:37
— Je pense qu'il faudra que je parte dans deux heures.

**Thibault P.** 01:49
— Je fais la première partie et je vous laisse sur la fin.

**Nathan M.** 04:28
— Voilà, l'audio est fusionné, c'est bon. Donc là maintenant tu pourras te démuter.

**Thibault P.** 04:46
— Il faut que ce soit pas moi qui sois en premier. Salut Maxime, ça va ?

**Thibault P.** 05:07
— Juste pour dire, on est connecté. Est-ce que c'est bon pour vous ?

**Maxime B.** 05:34
— Bonjour !

**Thibault P.** 05:35
— Désolé, on n'avait pas vu que vous nous attendiez. On vous attendait comme des cons. Ça va bien ?

**Maxime B.** 05:44
— Oui, vous aussi.

---

## Introduction & contexte business

**Thibault P.** 05:47
— Impeccable. OK, let's go. Du coup, Nathan est bien là, Matthis aussi, notre PO/PM. L'idée, c'est de vous faire un état des lieux de ce qu'on a vu, que ce soit sur la partie code, mais également sur la partie gestion de projet. Vous faire un peu notre analyse et des propositions sur tout ça. C'est pour ça que je parlerai un petit peu moins. D'abord Matthis sur l'aspect plutôt gestion de projet, et puis Nathan sur le côté code.

**Nathan M.** 06:20
— Avant de commencer, la dernière fois qu'on s'était vus, c'était le grand lancement. J'imagine que ça avance un peu de votre côté. Vous en êtes où d'un point de vue business ? C'est toujours compliqué les premières…

**Maxime B.** 06:31
— On a dépassé le million de chiffre d'affaires. C'est incroyable. Non, c'est… On est en train de régler les problèmes des cinq premières minutes post-inscription sur le site, où c'est un peu le bordel, tu ne sais pas quoi faire. Et pour l'instant, la communication mise en place ne porte pas assez ses fruits en termes de nombre d'inscrits. Donc on a rendez-vous avec eux demain pour voir tout ça. On est sur un début quand même un peu très light.

**Nathan M.** 07:06
— OK. Et là, c'est quoi les axes ? Comment vous analysez ça pour l'instant ? C'est-à-dire, en gros, c'est que la com n'est pas bonne ?

**Maxime B.** 07:21
— C'est dur à analyser. On n'a pas tout mis dans la com, dans le sens où on est conscients que le site a un problème d'expérience utilisateur au début. Donc on souhaite régler vraiment ce problème dans un premier temps, et puis après accélérer la com. On a plusieurs leviers là-dessus qu'on n'a pas encore enclenchés parce qu'on se dit que là, pour le coup, c'est encore un peu trop tôt. Donc j'espère d'ici une à deux semaines pouvoir enclencher avec un peu plus de violence.

**Thibault P.** 07:49
— OK.

---

## Diagnostic gestion de projet — Matthis

**Thibault P.** 07:55
— On a fait des pré-diagnostics sur deux choses principales. La partie gestion de projet, et la partie code. Matthis va commencer.

**Nathan M.** 08:26
— Juste pour qu'on arrive rapidement — Matthis a un profil hyper intéressant parce qu'avant il travaillait en incubateur de startups avant d'arriver chez nous. Il a une formation de designer, est arrivé chez nous en tant que designer, avant de monter PO/PM, et là il reprend gentiment la gestion des opérations de tout le studio — donc notre filiale qui fait du développement. Du coup c'est assez chouette parce qu'il a vu des projets en early stage comme chez nous, et des projets qui représentent plusieurs millions de budgets à scale avec plusieurs équipes de développeurs. Je te laisse compléter ta présentation.

**Matthis R.** 09:13
— C'est essentiel, effectivement. Mon rôle chez Drakkar consiste en un mélange de tout ça : encore une partie design — d'ailleurs on en parlera rapidement puisque j'ai regardé tout de suite — et tout le lien entre business et tech avec notre équipe de développeurs. Le sujet que vous avez forcément, cette relation business avec votre développeur intégré, je la connais très bien puisque c'est vraiment ce parallèle que nous, on a entièrement en interne et qui nous permet de bien fonctionner avec nos clients et la livraison des projets.

### Retour design / Figma

**Matthis R.** 09:46
— Voilà. Il y avait un Figma qui m'avait été envoyé. J'en parle pas du tout dans la partie diagnostic. Pourquoi ? Déjà parce que le fichier est propre. Moi j'ai eu que la version prototype, donc j'avais pas forcément le fichier source. Le design est sympa, les écrans sont propres, on a les bonnes règles de margin, spacing, tout ce qui est considéré comme bonnes pratiques. On est contents du résultat, en tout cas franchement c'est très sympa. Donc je n'ai quasiment aucune critique à faire — ça serait du subjectif, "j'aime pas les couleurs", mais c'est personnel donc je rentre pas dans ce sujet-là. Le seul retour que j'ai peut-être, mais peut-être que ça ne m'a pas été fourni, c'est que pour moi il manquait quand même tout un parcours fonctionnel sur la réservation des créneaux, etc. Donc tout le processus intra-app. Là on a toute la partie un peu vitrine qui te fait rentrer dans Twoghether et te fait comprendre. Par contre, je n'ai pas vu tous les process de passage à la caisse, intégration au panier, réservation, les créneaux, etc.

**Maxime B.** 10:46
— Tu veux dire uniquement dans le Figma ?

**Matthis R.** 10:49
— Uniquement dans le Figma.

**Maxime B.** 10:50
— Oui, en fait c'est qu'on avait demandé le travail sur certaines pages, et du coup Yoann, notre dev, s'est débrouillé derrière pour, en fonction de ce qu'il a reçu sur ce Figma-là, ensuite modifier les pages qui n'avaient pas été proposées. C'est une histoire de budget.

**Matthis R.** 11:06
— OK, vous avez arrêté un certain nombre de pages, vous avez défini des layouts avec l'agence.

**Maxime B.** 11:10
— Et par exemple, cette histoire de calendrier, on n'a pas voulu que l'agence bosse dessus parce qu'on est conscients que le calendrier va être amené à bouger très rapidement, donc ça ne servait à rien qu'ils perdent du temps dessus.

**Matthis R.** 11:23
— OK, je comprends mieux. Donc voilà, très peu de retours là-dessus. La plateforme est cool, respecte vraiment de bons standards. Et je trouve les écrans plutôt jolis en plus.

### Constat 1 — Manque de gestion structurelle

**Matthis R.** 11:35
— Je me concentre sur la partie gestion de projet. Là, j'ai un petit peu plus de retours. Clairement, on voit un manque de gestion structurelle sur cette gestion de projet. C'est bien pour ça que nous, on a ces compétences en interne. Il faut très bien comprendre la difficulté que ça peut être côté technique, et même pour vous, d'avoir de la visibilité sur ce qui est livré par le développeur, de lui annoncer des guidelines, des spécifications qui vont lui permettre d'avancer le plus rapidement possible. Nous c'est un accent qu'on met beaucoup : comment optimiser le temps de production de nos équipes techniques. Et là, aujourd'hui, pour lui comme pour vous, je pense que vous manquez cruellement de visibilité, juste au vu de ce que je vois en termes de format.

**Maxime B.** 12:25
— Oui, en fait, on a un souci à ce niveau-là : quand je fais une liste de doléances, de choses qu'il faudrait modifier, c'est difficile pour moi d'estimer un délai, parce que Yoann lui-même a du mal, en fonction du bordel qu'il a l'air d'avoir dans le code, à estimer un délai. Donc je suis parti du principe que nos seuls délais, c'était dans l'espèce de roadmap que j'avais faite, et point barre. Mais conscient que c'est un vrai problème.

**Matthis R.** 12:57
— Ouais, et puis au-delà de ça, l'estimation, effectivement, pour anticiper la vélocité — si vous connaissez le terme, la capacité d'un développeur à livrer dans un temps donné ce qu'il engage — c'est un vrai sujet évidemment, parce que c'est comme ça qu'on vérifie la performance purement opérationnelle d'un développeur. Mais au-delà de ça, il y a ce principe de spécification. J'ai quelques exemples que j'ai récupérés, mais comment est-ce qu'on annonce un besoin fonctionnel ? Aujourd'hui, ils sont souvent très étendus. À moins que vous ayez des séances de discussion plus approfondies, ce qui fait que le Notion documente juste les grandes idées.

**Maxime B.** 13:37
— Effectivement. On a la chance d'être que trois, donc il y a aussi des grandes périodes d'échange. Il y a parfois des moments où quand on bloque sur quelque chose, on écrit les grandes lignes très rapidement sur Notion, et après on en discute et lui se fait sa sauce derrière. Quand on a la chance et la malchance d'être que trois, c'est aussi un peu comme ça qu'on fonctionne.

**Matthis R.** 14:00
— Carrément, je comprends. Et en même temps, c'est extrêmement dangereux à long terme, voire même à moyen terme, parce que même au niveau documentation, pour avoir un historique de ce que vous avez pu faire, reprendre des choses, re-challenger, se rendre compte de comment on avançait précédemment, qu'est-ce qu'on peut réutiliser… Il va vraiment y avoir une douleur à retrouver l'information que vous construisez ensemble, même à trois. C'est justement ça le piège : se dire "je n'écris pas et ce n'est pas grave, c'est dans nos têtes", sauf qu'en fait, six mois après, tout le monde a oublié. Donc il y a un problème dans la temporalité très courte de prévoir les futurs sujets. Et il y a pour moi un manque de précision là-dessus, même si ça doit être compensé par beaucoup d'échanges et du synchrone. Mais il y a une douleur dans l'archivage des données précédentes et de la vision pilotée long terme, qui va vous demander de trop souvent faire ces points de synchronisation qui peuvent impacter la vélocité. Vous avez probablement d'autres choses à faire que réexpliquer quatre fois ce que vous attendez. D'où le but d'aller vraiment beaucoup plus loin. Après, c'est un boulot à part, c'est bien pour ça que c'est mon poste. C'est tout à fait normal quand on n'a pas la ressource de souffrir de ce sujet.

### Constat 2 — Mélange de granularité dans la roadmap

**Matthis R.** (suite)
— Mes trois constats principaux sur la partie projet. D'abord, le mélange de niveaux de granularité, principalement dans la roadmap. Vous avez fait une nouvelle version que j'ai reçue hier, qui compense un des sujets que je voulais remonter : vous avez vraiment fait une roadmap produit, qui ne concerne que le site. Ça, c'est bien. Dans la première version que j'avais vue, on avait "Finalisation UX/UI", "Prospection B2B France" et "Définition des objectifs V2" — donc en fait, il n'y avait pas de séparation produit/tech. Et surtout le plan commercial était mélangé. En fait, Maxime, tu dois avoir des objectifs très business — organisation, déploiement, action commerciale, communication — ça, au même endroit que le produit, ce n'est pas bon, tout simplement parce qu'on ne segmente pas les choses et on se retrouve avec un fourre-tout.

**Maxime B.** 16:20
— Effectivement, quand on a créé ce fichier-là, j'avais en tête qu'il fallait que je parle produit en amont jusqu'à la sortie du site. Une fois que la sortie serait actée, je serais entre guillemets libéré pour aller sur ma partie commerciale. Il s'avère que ça ne s'est pas du tout passé comme ça, et du coup on a eu la nécessité de créer le même fichier, mais pour l'instant sans priorisation — on a juste mis les grands éléments des V1, V2, V3. Mais on a vite pris conscience qu'il fallait qu'on fasse ce document uniquement pour le site. L'idée du tout premier, c'était de comprendre où on allait, parce que ce n'était pas forcément le cas.

**Matthis R.** 17:01
— OK, je comprends. Le piège est logique : c'est toujours le retard ou le changement d'axe ou une nouvelle priorisation. Forcément ta roadmap produit va bouger, ça va décaler d'autres enjeux. D'où le fait de directement les segmenter. Et encore une fois, vous avez pris le bon pli puisque la nouvelle roadmap ne considère que ça, ce qui me semble beaucoup plus logique.

**Maxime B.** 17:22
— Néanmoins, cette roadmap-là, elle vaut ce qu'elle vaut, mais elle nous a permis de comprendre où on voulait aller. C'était déjà ça.

**Matthis R.** 17:28
— Voilà. Vous avez un enjeu qu'on peut moins avoir, nous, par dimension et taille d'équipe : c'est qu'il faut quand même que le développeur puisse imaginer les enjeux business. Donc je comprends l'idée de les lui avoir exposés. Maintenant, c'est juste une question de mettre dans des boîtes pour segmenter et pouvoir mieux piloter au quotidien.

### Constat 3 — Spécifications insuffisantes

**Matthis R.** (suite)
— Deuxième sujet, la partie spécification. C'est un boulot à part entière qui appartient au Product Owner — la gestion d'un backlog et du pilotage d'un développement sur base de spécifications fonctionnelles. C'est-à-dire : comment est-ce que j'exprime un besoin finement pour que le développeur comprenne très rapidement, et quasiment sans aucun doute, ce qu'il doit faire ? J'ai compris que c'était la page "cahier des charges et test". Ce cahier des charges est mélangé et pas précis. On retrouve des retours utilisateurs, des idées de fonctionnalités sans forcément savoir ce qu'on va en faire, des bugs. J'ai vu une ligne rouge "bug critique de paiement". Il y a un problème de mise en valeur des sujets les plus importants. Il y a des questions, des points d'interrogation.

**Maxime B.** 18:39
— Dis-toi que ce fichier-là, il est lu aussi beaucoup en réunion. C'est aussi un endroit où on note "Note-le moi que je m'en souvienne après la réunion". Il y a pas mal de cet aspect-là.

**Matthis R.** 18:53
— C'est là où il faudrait… Je ne viens pas pour dire que c'est le monde idéal, et je comprends vos enjeux. Idéalement, il faudrait reprendre le temps de reprendre chaque spec, les mettre indépendamment, et re-bien préciser le besoin. Par exemple, il y en a une : "Amélioration module paiement". Pour savoir ce qu'il faut faire derrière en termes d'intégration, je suppose que vous l'avez dit oralement, mais sur le fichier, c'est vraiment très léger.

### Constat 4 — Priorisation absente

**Matthis R.** (suite)
— Mon dernier constat, c'est la partie priorisation. Je suppose que vous bougez beaucoup, vous êtes une activité naissante. Tout va bouger un peu tous les jours, on prend des nouvelles décisions, que ce soit au niveau commercial ou produit. C'est hyper logique, mais du coup, ça ne se reporte pas dans le fichier non plus, puisqu'on a un peu tout qui est mis dans V2, quelques trucs avant lancement non définis.

**Maxime B.** 20:03
— Ce fichier-là, je vous l'ai envoyé pour le contexte. C'est un fichier qui a été fait en septembre, parce qu'à l'époque on avait besoin de situer un peu où on allait, et il n'a pas été réutilisé depuis. D'ailleurs, si tu regardes les dates, ça doit s'arrêter à fin septembre. Ce n'est pas un fichier qui est suivi du tout.

**Matthis R.** 20:27
— OK. Je commence à comprendre : vous vous êtes fait un plan jusqu'au lancement, vous vous êtes dit "on fait en sorte que ça passe et on verra plus tard", et du coup on est un peu restés à cet état-là. Vous êtes en train de galérer sur le post-lancement. D'où le fait qu'on se voit aujourd'hui. Très bien, compréhensible, mais c'est le piège typique puisqu'il y a forcément des incidents, les aléas du direct.

### Synthèse gestion de projet

**Matthis R.** (suite)
— Je synthétise. Ce qui manque : entre vous deux et le développeur, il y a ce côté "avance à tâtons, à l'aveugle". Il y a un flux de demandes qui manque de tri, il n'y a pas la partie technique, pas forcément le lien avec les écrans. Entre vision et exécution, sur ce fichier asynchrone qui normalement est un outil de pilotage quotidien, il y a un lien brisé que vous devez compenser par beaucoup d'échanges. En résumé :

- Des spécifications fonctionnelles qui ne sont pas assez claires
- Une priorisation qui n'est pas formalisée avec des délais, des engagements, des vues par rapport à de vrais enjeux (déploiement, lancement, planification réaliste)
- Pas de séparation entre bugs, évolutions et features
- Pas de workflow pour suivre les étapes habituelles : spécifié → en développement → recette → livraison

**Maxime B.** 22:46
— Oui, très conscient de tout ça. Ce travail de PO/PM, ce n'est pas une ressource qu'on a en interne. On le fait avec tout le bon sens qu'on estime avoir, et c'est tout.

**Thibault P.** 23:02
— Oui, et puis surtout, on sait que ce n'est pas toujours évident à entendre, mais imaginez ça vraiment comme un constat.

**Maxime B.** 23:10
— Ça ne nous pose aucun problème d'entendre tout ça.

**Matthis R.** 23:25
— C'est comme ça qu'on avance. Et vraiment, c'est même normal. J'ai vu des dizaines, des centaines de startups, c'est toujours le même problème : on n'a pas cette ressource. C'est bien pour ça qu'on passe par des agences quand on lance un projet, ou quand on internalise. Moi, c'est mon conseil à 1000 % : c'est le PO avant le dev, pour préparer la bonne intégration tech derrière. C'est dur parce que ça implique deux postes si c'est de l'internalisation. Mais c'est mon conseil absolu parce que c'est ça qui va vraiment… À court terme, ça passe. Plus on tire le fil, plus ça dure dans le temps, plus c'est douloureux parce qu'on commence à se prendre la tête entre la tech et le business, on ne se comprend plus et on n'a pas ce lien qui permet de cadrer sur le long terme.

---

## Proposition d'audit — Matthis

**Nathan M.** 24:47
— Matthis doit finir dans quatre minutes. Ce que je vous propose, c'est que Matthis vous présente comment il pense structurer l'audit, et après je reviens sur la tech.

**Matthis R.** 25:10
— On vous propose un audit de deux jours. Je vais m'arrêter sur la première journée qui concerne la partie produit.

### Journée 1 — Produit

**Matthis R.** (suite)
— Ce que je pense qui pourrait être très pertinent, c'est de profiter d'un œil externe comme le nôtre sur un atelier. C'est de repartir un peu sur la vision : redéfinir où est-ce que vous en êtes. Vous êtes dans cette phase de déploiement. Du coup, mon conseil serait de repartir sur les fondamentaux, reposer vos objectifs court, moyen, long terme. Maxime, tu as dit une semaine ou deux pour tout corriger et remettre le paquet sur le commercial — OK, ça veut dire qu'il y a des objectifs tech derrière : quelle feature doit être attaquée ? Moyen et long terme aussi : qu'est-ce qu'on continue à faire sur le produit, est-ce qu'il y a des parcours critiques, des optimisations, l'intégration de solutions externes, de nouveaux enjeux ?

Il faut d'abord être clair en haut sur la vision pour qu'on découle d'un opérationnel qui fait sens. Si en haut la rivière est éclatée et part dans tous les sens, c'est impossible qu'on ait notre petit ruisseau qui coule bien avec la technique.

Ça permettrait de profiter d'une vision externe, de reposer et de retravailler sur un vrai format roadmap. Séparer les différents enjeux : business, déploiement, tech, produit. Réaligner tout ça et comprendre comment ça fait sens entre eux.

La deuxième partie, ce serait de vous aider concrètement. L'audit est en partie actionnable : on produit des formats pour vous guider. Repartir sur les irritants produit — qu'est-ce qui vraiment ne marche pas — reprioriser le backlog (votre cahier des charges), relister les actions fines du produit, et redéfinir comment on cadre une feature et comment on met ça au propre dans Notion.

**Maxime B.** 28:19
— OK, merci. Très bien.

**Thibault P.** 28:23
— Super. J'en profite pour partir si ça vous va.

**Matthis R.** 28:27
— Merci beaucoup. On reparlera au débrief et on sera sûrement amenés à se reparler.

---

## Diagnostic technique — Nathan

**Nathan M.** 29:05
— Est-ce qu'il y a des questions sur ce que Matthis vient de présenter avant que je rentre dans la tech ?

**Maxime B.** 29:14
— Non, globalement je pense qu'on avait à peu près le même constat. On est à peu près conscients de nos problèmes de ce point de vue-là. La partie que tu vas présenter m'intéresse fortement pour voir comment les deux peuvent s'articuler.

### Rappel gestion de projet

**Nathan M.** 29:43
— Pour finaliser sur la partie gestion de projet : vous êtes dans un cas classique. Il n'y a pas rien — on a relevé tout ce qui ne va pas, mais en vrai, il y a plein de bonnes choses aussi.

### Architecture & dette technique

**Nathan M.** 30:41
— Sur la partie orga, c'est ce que Matthis a dit. Vous avez une bonne gestion de projet mais il y a une notion de granularité : vous essayez de faire du product management sans les notions de tech. C'est ce que tu disais, Maxime, sur "il essaie d'estimer mais il ne sait pas". Il y a un vrai enjeu d'affiner les fonctionnalités beaucoup plus précisément pour avoir cette estimation.

Pour illustrer, nous on travaille souvent sur Notion et on fonctionne par sprints. On a les épics avec les grandes catégories de fonctionnalités et toutes les user stories derrière — les fonctionnalités clés qu'on va devoir développer, avec potentiellement les maquettes associées.

**Maxime B.** 31:42
— Moi j'ai envie de chialer quand je vois ça, ça me fout des boutons.

**Nathan M.** 31:48
— Ce ne sera pas à vous de le gérer ! Mais quand tu fais ça, même avec un seul développeur, la vélocité se compte en multiples. Par contre c'est un vrai taf. Du coup ton dev est, admettons, deux fois plus productif, mais il faut passer un mi-temps pour le préparer. On se force typiquement à ne jamais faire des user stories de plus de deux jours et demi, parce que sinon on considère que c'est trop gros et mal découpé. Plus c'est précis, moins tu peux te tromper.

### Diagnostic code

**Nathan M.** 32:46
— Sur la partie diagnostic technique, pour être très transparent, je m'attendais à un truc vraiment éclaté au sol. Ce n'est pas le cas. Il y a de bons fondamentaux, mais il y a aussi des choses qui ne vont pas.

**Ce qui va bien :**

- L'architecture globale fonctionne bien (DDD, etc.)
- Des patterns de développement solides
- On sent une bonne expérience sur le design d'architecture

**Ce qui ne va pas :**

- De la dette technique dans tous les sens
- Des librairies pas du tout à jour, dont certaines avec des failles de sécurité
- Pas assez de librairies utilisées — il repart trop de zéro à chaque fois
- Aucun test automatisé
- Pas de CI/CD (Continuous Integration / Continuous Delivery)

**Maxime B.** 34:49
— Ça veut dire qu'il repart trop de zéro à chaque fois ?

**Nathan M.** 34:52
— Oui, beaucoup trop. Pour faire simple, les deux gros trucs qui ne vont pas : un, il y a des choses pas à jour avec des failles de sécurité ; et deux, il n'y a aucun test et pas de CI/CD.

**Nathan M.** (suite)
— Qu'est-ce qu'on veut dire par test ? Quand tu développes une fonctionnalité, tu fais des tests automatisés. Ça permet que quand tu changes quelque chose ici et que ça casse quelque chose là, ton test va casser et le dev s'en rend compte avant de pousser la fonctionnalité.

**Maxime B.** 36:02
— C'est pour ça, je pense, qu'il ne veut pas s'attaquer au calendrier. Parce que dès qu'on va travailler sur quelque chose d'existant, ça va recasser quelque chose à côté.

**Nathan M.** 36:10
— Oui, complètement. Et pareil, il n'y a pas de flux de CI/CD.

**Maxime B.** 36:23
— C'est quoi ?

**Nathan M.** 36:27
— Continuous Integration et Continuous Delivery. C'est la manière dont tu déploies ton projet. À chaque mise en production, théoriquement tu as tout un tas de tests et de validations avant de mettre en ligne et après, pour s'assurer que c'est clean. Là, on n'en voit aucune. Encore une fois, peut-être qu'on n'y a pas eu accès — c'est à mitiger.

**Maxime B.** 36:55
— Sur les tests, je sais pas. Mais pour le CI/CD, je pense pas.

**Nathan M.** 36:59
— Il y a plus de chances qu'on n'ait pas accès au CI/CD qu'aux tests. Donc il n'y a sans doute pas les deux. Bon, des bons fondamentaux, des patterns de design qui sont OK, des frameworks vieillissants — Laravel, PHP — mais c'est robuste, donc pourquoi pas. À l'inverse, le fait que les librairies ne soient pas à jour avec des failles de sécurité, c'est un problème. Il manque aussi des standards, notamment sur la gestion d'état avec Redux.

En résumé : il y a quand même du déploiement automatique. Une base clean à mon sens, mais qui a mis beaucoup trop de temps à être développée. Pas du tout de tests — c'est une aberration à ce stade du projet. Pas 20 % de tests à minima (le 80/20). Les librairies pas à jour, c'est aussi aberrant. Et le fait qu'il y ait plein de choses développées alors qu'on aurait pu utiliser des librairies, ce n'est pas une aberration technique, c'est une aberration de vélocité : vous avez payé un truc dix jours qu'on aurait pu faire en un jour.

### Analyse des commits & vélocité

**Nathan M.** 40:27
— On a repris l'historique des commits. Il y avait une vélocité plus importante côté agence avant. On a un bug ratio de 40 % sur l'agence, qui est aujourd'hui de 35 %. On l'a mis en vert, mais ça reste beaucoup — il faudrait viser 20 %.

**Nathan M.** 43:05
— Il y a des choses comme le booking et l'authentification où il subit toujours beaucoup de bugs, malgré des refontes. Les choses qui n'ont pas été refondues, il galère à les maintenir. Et même sur celles qu'il a essayé de refondre, il ne s'en sort pas.

### Question de la présence du développeur

**Nathan M.** 43:42
— Et j'avais une question. Yoann, il est à mi-temps ?

**Maxime B.** 43:46
— Non, full time.

**Nathan M.** 43:48
— Il a toujours été full time ?

**Maxime B.** 43:50
— Oui.

**Nathan M.** 43:59
— Il faut creuser parce que peut-être qu'on n'a pas accès à tout. Mais quand on prend purement l'historique de commits, on n'a que 44 % de présence. En gros, c'est deux jours et demi sur cinq. Même en admettant qu'il soit à 70 % (parce qu'il a aussi le rôle de product manager et ne commite pas quand il fait ça), 44 %, s'il c'est bien ça… il y a un sujet. Peut-être qu'il y a des projets qui ne nous ont pas été transmis.

**Maxime B.** 46:03
— Et comment on peut creuser ce point-là ?

**Nathan M.** 46:16
— Déjà, lui demander sur quoi il a bossé, lui demander s'il nous a donné accès à tout.

**Nathan M.** (suite)
— Si je me base purement sur l'historique de commits, en juillet il a commité sur 4 jours sur 23, et en août, 2.

**Maxime B.** 47:34
— Donc 6 jours en tout.

**Nathan M.** 47:54
— Encore une fois, on se base sur l'historique de commits, qui n'est pas censé être du tracking, et on extrapole dessus. C'est vraiment possible qu'on n'ait pas tous les dossiers. C'est pour ça que je mets des pincettes — pas pour vous faire plaisir, mais parce qu'on n'a pas assez d'éléments pour affirmer.

**Nathan M.** (suite)
— Par contre, un gros pic d'activité ce mois-ci. Là, il a vraiment shippé tous les jours, tout un tas de fonctionnalités. En fait, on a extrait les quelque 1 300 commits que vous avez — autant vous dire que c'est l'IA qui a analysé ces commits-là, parce que sinon on aurait passé 10 jours.

### Profil du développeur

**Nathan M.** (suite)
— En résumé, point d'attention, pas de conclusion pour l'instant. On a une présence qui est fragmentée. Même si au final il était full time, ça montre que son implication d'un point de vue code par rapport à la codebase principale est fragmentée. C'est une question de focus : tu vas mieux bosser à faire des blocs de 5 jours en sprint d'une semaine, plutôt qu'un jour par-ci par-là.

Il y a un ratio de vélocité qui n'est pas bon. C'est à la louche, mais dans mon ressenti, je pense que vous pourriez shipper 5 à 6 fois plus vite.

**Maxime B.** 51:09
— Avec un nombre de devs équivalent ?

**Nathan M.** 51:13
— Ouais. C'est pas très juste pour Yoann parce que je mets l'agence dedans.

**Maxime B.** 51:23
— Et il y avait un vrai temps de compréhension de l'URSSAF.

**Nathan M.** 51:28
— Ouais. Et c'est ça qui peut expliquer aussi qu'il ne commite pas quand il est en train de comprendre. C'est de la conception, c'est normal. Il y a de grandes chances que ça révèle surtout que c'est l'organisation qui n'est pas bonne.

**Maxime B.** 52:01
— Oui, exactement.

**Nathan M.** 52:07
— En tout cas, pour moi, il faut viser une productivité de ×5 par rapport à aujourd'hui.

**Maxime B.** 52:13
— Tu parlais la dernière fois de dette technique. Je n'ai pas entendu vraiment en parler, si ce n'est que l'architecture est bonne.

**Nathan M.** 52:51
— Ça dépend des modules. Il y a des modules qui ont plus de dette technique que d'autres. Ce qui est commun à toute l'application, c'est qu'il y a zéro test — ça fait partie de la dette. Grosso modo, votre dev a l'air meilleur en backend qu'en frontend. Les composants backend sont plus propres que ceux côté frontend. Donc il y a plus de dette technique frontend.

**Maxime B.** 53:27
— Frontend, c'est quoi ?

**Nathan M.** 53:27
— Backend, c'est la partie intelligence de l'application. Frontend, c'est ce que vous voyez — l'interface. Sur des apps comme la vôtre, la majeure partie du travail est frontend, au moins 60 %. Donc c'est possible qu'on veuille garder le backend mais refondre le frontend. Le truc qui est sûr, c'est les tests. Les tests, ce n'est jamais agréable à faire, ça ne produit aucune feature visible. Les faire après coup, c'est toujours un sujet.

### Synthèse technique

**Nathan M.** (suite)
— Si on prend de la hauteur : vous avez des gros sujets CESU-URSSAF, KYC, etc. Il y a des choses techniquement complexes qui ont été développées et qui fonctionnent — c'est cool. L'agence a livré un MVP qui était bon. Moi je suis moins critique que Yoann de ce qui a été livré à la base par l'agence.

Le problème, c'est que reprendre ça tout seul, sans cadre PM et avec un peu de juniorité… Ce n'est clairement pas un CTO, on le sent — il n'a pas pris la hauteur pour définir l'architecture technique. Du coup, la vélocité n'est pas bonne.

Notre profil estimé : c'est un mid qui a un bon niveau Laravel/React, qui comprend les patterns, qui est a priori autonome et fiable. Par contre, pas de test, c'est compliqué. La productivité tech n'est pas bonne. Et les outils d'aujourd'hui ne sont plus à jour.

**Nathan M.** 55:39
— Je préfère un mec qui a de bons fondamentaux et qui n'est pas à jour, qu'un mec qui connaît toutes les dernières technos mais qui ne comprend rien aux fondamentaux. Le vrai problème, c'est pas de PM (la priorisation fine n'est pas là), pas de CTO (il n'a jamais été challengé dans le bon sens du terme), une présence fragmentée, et la dette invisible avec zéro test.

---

## Next steps & scénarios

**Nathan M.** 56:16
— On voudrait faire un forfait à 2K€ sur cette prestation d'audit. On le fait au forfait parce que dans les faits, on va devoir creuser. Vu qu'on ne se connaît pas encore, c'est très lisible pour vous.

Derrière, il y a plusieurs scénarios :

### Scénario A — Stabilisation urgente

Géré par nous ou par Yoann (probablement un mix hybride). Ce sont des choses standards pour nous, ça nous coûtera moins cher qu'on le fasse.

### Scénario B — Reprise frontend + mobile

Reprendre le frontend potentiellement, plus la partie gestion mobile. Dans votre roadmap, il y avait le déploiement de l'app mobile. Pour moi, dans l'état, Yoann n'y arrivera pas — c'est lui rajouter un truc en plus alors qu'il prend déjà l'eau.

**Maxime B.** 57:38
— Reprise front, c'est quoi exactement ? C'est une fois que tu es inscrit, le parcours, etc. ? On n'est pas que sur du visuel ?

**Nathan M.** 57:52
— En gros, tu as la partie backend (base de données, logique métier, URSSAF, etc.) et la partie frontend (l'interface, le code HTML/CSS qui interagit avec le backend). Les deux sont séparés : tu peux toucher au frontend sans toucher au backend. Donc ça peut être une option : garder le backend et refondre le frontend.

### Scénario C — Modernisation complète

Reprise complète de l'application.

### Scénario D — App mobile

D'un point de vue frontend, quand on fait une app mobile, c'est quasi que du frontend. Le backend est à peu près le même que pour la version web desktop, mais il faut un frontend spécifique au store iOS et Android. Il faudra se poser la question de la direction, mais c'est trop tôt pour affirmer — d'où le besoin de l'audit.

### Scénario E — CTO/CPO fractionnés

On intervient en suivi/support en tant que CTO ou CPO (ou les deux), pour donner du rythme et faire avancer les choses.

**Thibault P.** 1:00:48
— Ce sont des scénarios probables. Il y aura sûrement des urgences à gérer pour le bien de l'app, et après, de la réflexion sur du moyen et long terme.

---

## Questions & discussion

**Maxime B.** 1:01:47
— Dans tes différents scénarios, ça implique combien de personnes chez vous ?

**Nathan M.** 1:01:56
— Si on fait une refonte complète, on ne va quasiment jamais dépasser un product owner et deux développeurs. On a une logique de roulement, mais en full time, ce sera jamais plus qu'un PO à mi-temps et deux devs full time, pendant une période de 1 à 3 mois — très court comme timeline. Si c'est CTO/CPO, ça peut être un jour par semaine. Ça va vraiment dépendre d'où on met le curseur.

**Maxime B.** 1:02:33
— Et tout ça, c'est l'audit qui nous amènera à définir la priorité.

**Nathan M.** 1:02:42
— C'est ça. Nous on veut se servir de l'audit pour mettre un cadre de gestion de projet beaucoup plus robuste — quoi qu'il arrive, on va se servir de l'audit pour ça. Et effectivement y voir plus clair sur concrètement qu'est-ce qu'il faut. Ce sera une discussion entre vous et nous, une notion d'investissement, on aura le backlog, et se dire finalement qu'est-ce qu'on a envie de prioriser en fonction des enjeux business.

**Maxime B.** 1:03:48
— Est-ce qu'il est envisageable de mettre un budget de 6 mois ? Qu'est-ce que ça impliquerait si on part sur le scénario 1 ?

**Nathan M.** 1:04:10
— Je comprends le besoin derrière. Dans les faits, c'est assez compliqué parce que ce sont toujours des points de détail qui font la complexité. Là typiquement, il se peut qu'on n'ait pas accès à tous les repos.

**Maxime B.** 1:04:25
— Donc vous allez vous baser sur un truc qui ne tient pas la route.

**Nathan M.** 1:04:28
— C'est ça. Il y a quelques années, je t'aurais fait une grosse fourchette, mais pour m'être planté quasiment à chaque fois, je préfère te dire en vrai : je ne sais pas trop. Ce qu'il faut avoir en tête, c'est que si on travaille sur cet audit, vous n'êtes pas pieds et poings liés avec nous. Tout ce travail de structuration, vous en aurez besoin si vous voulez bosser avec d'autres personnes aussi. Je préfère faire un truc un peu light mais qui permet de vraiment répondre à ça, que de donner une cote mal taillée qui va te rassurer mais qui ne va rien donner.

---

## Conclusion

**Nathan M.** 1:05:12
— Comment vous voulez avancer par rapport à ça ?

**Maxime B.** 1:05:16
— On va en parler et on vous revient. Si on part sur l'audit, vous avez des dispos sous quel délai ?

**Nathan M.** 1:05:28
— Thibault vous dit ça.

**Thibault P.** 1:05:29
— Je regarde le planning, il se remplit bien, mais pour un audit il faut que je voie avec l'équipe.

**Maxime B.** 1:05:37
— Vous êtes combien en interne ?

**Thibault P.** 1:05:39
— 25.

**Nathan M.** 1:05:44
— Il y a quasiment 6 ans qu'on existe.

**Thibault P.** 1:06:42
— Écoutez, vous nous dites, vous réfléchissez.

**Maxime B.** 1:06:54
— On réfléchit et on vous revient.

**Thibault P.** 1:06:49
— Si vous voulez partir avec nous sur l'audit, je vois les dispos. On essaie d'aller vite.

**Maxime B.** 1:06:58
— Merci beaucoup.

**Nathan M.** 1:06:59
— Top. N'hésitez pas s'il y a des questions qui viennent entre-temps. Sinon, on avance et on essaie d'aller vite sur cette partie-là.

**Maxime B.** 1:07:07
— OK. Merci les gars. Bonne journée.

**Nathan M.** 1:07:09
— Salut. À la prochaine.

**Maxime B.** 1:07:11
— Ciao.