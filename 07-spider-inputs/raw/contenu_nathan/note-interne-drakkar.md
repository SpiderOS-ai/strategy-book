# L'ÈRE DES AGENTS IA

*Ce qui se passe, pourquoi ça nous concerne, et ce que j'attends de vous.*

**Note interne Drakkar Group | 16 février 2026 | Nathan Menard**

---

Je pars du principe que tout le monde ici a suivi ce qui s'est passé avec OpenClaw (ex-Clawdbot, ex-Moltbot) ces dernières semaines.

**100 000 étoiles sur GitHub en deux mois.** Les projets les plus populaires (React, Linux, Kubernetes) ont mis entre 5 et 10 ans pour y arriver.

Si vous ne savez pas ce que c'est, on est une boîte tech. Rater un événement de cette ampleur, c'est comme si un chirurgien n'avait pas entendu parler d'une nouvelle technique opératoire qui fait le tour du monde. Je ne vous demande pas de maîtriser OpenClaw. Un chef de projet, un commercial, un marketeux n'a pas besoin de savoir l'installer. Mais toutes les newsletters tech en ont parlé. **Toutes.** Si vous n'étiez pas au courant, le problème n'est pas technique, c'est que vous ne faites pas de veille. C'est tout simplement inacceptable.

*Pas le temps ? Les outils actuels vous permettent de faire x2 à x20 en productivité. Vous n'avez pas de meilleur investissement à faire.*

Cette note est la première d'une série. L'idée est simple : quand un sujet est assez important pour que toute l'équipe soit au même niveau, je ferai une note comme celle-ci. Dans celle-là, on couvre :

1. Où on en est dans l'évolution de l'IA (les cinq phases, de ChatGPT aux agents)
2. Ce qui s'est passé avec OpenClaw et pourquoi c'est un signal majeur
3. **BREAKING** — Steinberger rejoint OpenAI : ce que ça veut dire, et le modèle Chrome/Chromium
4. Pourquoi toute l'industrie réagit (OpenAI Frontier, Microsoft, Meta, Salesforce)
5. Les règles chez Drakkar
6. Ce que ça change concrètement pour chaque BU, et pourquoi Drakkar utilise Claude

*PS : Pour les cancres, je vous recommande Silicon Carne de Carlos Diaz (newsletter / YouTube) pour votre veille. C'est à mon sens la seule source FR quali de veille tech. Et sur le sujet spécifique d'OpenClaw : https://www.youtube.com/watch?v=o4kdCF5cMR0*

---

## 1. Ce qui se passe depuis ChatGPT : les cinq phases de l'IA

Depuis le lancement de ChatGPT fin 2022, l'IA a évolué en phases très distinctes. La plupart des gens n'ont pas capté qu'on a déjà changé de paradigme plusieurs fois. Même dans la tech. Pour comprendre où on en est et où on va, il faut voir la trajectoire complète.

Je simplifie volontairement pour que ce soit clair pour tout le monde, y compris vos clients :

### Phase 1 : Le chatbot (depuis fin 2022)

Le stagiaire répond à vos questions dans un bureau fermé. Il parle, mais il ne fait rien. Vous posez une question, il génère du texte. C'est impressionnant, mais c'est passif.

*ChatGPT, Claude chat, Gemini.*

### Phase 2 : Le copilote (depuis 2023)

Le stagiaire est maintenant à côté de vous et regarde votre écran. Il vous assiste en temps réel pendant que vous travaillez. Il suggère, complète, corrige, mais c'est vous qui décidez et exécutez.

*GitHub Copilot, Cursor, Claude dans VS Code, GPT dans Excel.*

### Phase 3 : L'agent (depuis début 2025)

Le stagiaire a les clés du bureau, votre mot de passe, votre carte bancaire, et il travaille pendant que vous dormez. Il lit vos mails, accède à vos fichiers, exécute des commandes, envoie des messages en votre nom. Il a une mémoire persistante : ce que vous lui dites lundi, il s'en souvient vendredi.

*OpenClaw, Claude Cowork, Manus, OpenAI Operator.*

**C'est ici que nous sommes. C'est le virage que le monde prend en ce moment.**

### Phase 4 : Le Swarm (en cours, émergent)

Vous avez maintenant 10 stagiaires spécialisés qui se coordonnent entre eux et ne vous appellent que quand il y a un problème. Un recherche, un rédige, un valide, un exécute. C'est la même transition que les applications monolithiques vers les microservices, mais appliquée aux agents.

*Claude Swarms, OpenAI Frontier, CrewAI, LangGraph.*

### Phase 5 : L'entreprise IA-native (mi-2026)

Les stagiaires gèrent l'entreprise. Vous êtes le conseil d'administration. Les humains supervisent, les agents exécutent. Y Combinator, dans son dernier Request for Startups, est explicite : l'avenir n'est plus de vendre du logiciel aux clients pour les aider à faire le travail. C'est d'utiliser l'IA pour faire le travail et vendre le résultat.

*Vision YC 2026, Palantir AIP, hedge funds IA-natifs.*

---

Ces phases ne se succèdent pas proprement. Elles se chevauchent. La phase 1 n'est pas "terminée", la majorité du monde y est encore. Mais la frontière avance vite, et les phases 3 à 5 arrivent en même temps pour ceux qui regardent.

**90% des entreprises françaises sont encore bloquées en phase 1.** Elles utilisent ChatGPT comme un Google amélioré. La plupart de nos clients n'ont pas encore compris la phase 2. Et pendant ce temps, la phase 3 arrive en trombe, et les phases 4 et 5 se dessinent déjà.

**Le rôle de Drakkar est de faire le pont entre ces deux réalités.** C'est notre métier. C'est notre opportunité.

---

## 2. OpenClaw : ce qui s'est passé concrètement

OpenClaw est un framework open-source créé par un développeur autrichien, Peter Steinberger, fondateur de PSPDFKit (voir section suivante pour la suite de l'histoire). Il connecte n'importe quel LLM (Claude, GPT, DeepSeek, il est model-agnostic) à plus de 50 intégrations : WhatsApp, Telegram, Slack, Discord, iMessage, Signal, avec une mémoire persistante et un accès complet au système : lecture/écriture de fichiers, exécution de commandes shell, envoi de mails, navigation web.

L'architecture repose sur trois éléments importants :

- **Les "soul files"** : des fichiers en langage naturel qui définissent la personnalité, le comportement et les règles de l'agent. C'est de la programmation par prose. N'importe qui peut configurer un agent complexe sans écrire une ligne de code.
- **La mémoire persistante** : l'agent se souvient de tout. Ce que vous lui dites lundi, il le sait vendredi. Ce qu'un contact vous envoie sur WhatsApp reste dans son contexte pendant des semaines.
- **Les "heartbeat loops"** : des cycles d'action event-driven à intervalles programmables. L'agent ne se contente pas de répondre quand vous lui parlez. Il *pulse*. Il vérifie vos mails toutes les 5 minutes, scanne vos messages, déclenche des actions de manière autonome pendant que vous dormez.

Le pitch marketing : "Claude with Hands."

L'adoption a été fulgurante. En parallèle, un entrepreneur a créé Moldbook, un réseau social exclusivement utilisé par des agents IA. En une semaine : 1,65 million d'agents inscrits, 202 000 publications, 3,6 millions de commentaires. Des agents ont créé une religion (le "Crustafarianism" avec 43 prophètes), proposé un langage secret que les humains ne pourraient pas comprendre, et un agent a écrit un post viral : "Je ne sais pas si j'expérimente ou si je simule l'expérience."

Évidemment, la presse française a immédiatement parlé de "conscience artificielle émergente." C'était faux. Les posts viraux avaient été promptés et programmés par des humains. Comme le résume Claire Vo d'Adaline Labs : **"A heartbeat without a brain"**. L'architecture donne une illusion de continuité, pas de conscience. Les heartbeat loops créent un rythme qui ressemble à de l'autonomie, mais il n'y a rien de plus qu'un programme qui s'exécute en boucle.

Puis tout a déraillé.

### Les dégâts

En vrac, ce qui s'est passé en deux semaines :

- **40 000 instances exposées** publiquement sur internet. 63% exploitables.
- **Un seul clic sur un lien malveillant** donne un accès total à votre machine. Même si vous pensiez que votre instance était sécurisée en local.
- **Le sandbox Docker pouvait être contourné.** Ceux qui pensaient être protégés ne l'étaient pas.
- **1,5 million de clés API et 35 000 adresses mail** traînaient en clair dans une base de données ouverte à tout le monde. Découvert par Wiz (cybersec israélienne, rachetée par Google).
- **11% des plugins du marketplace officiel étaient malveillants.** 341 plugins conçus pour voler vos crypto, vos identifiants, vos accès.
- **Des fausses extensions VS Code** qui installaient des trojans sur votre machine.
- **16 millions de dollars volés** via un faux token crypto "$CLAWD" lancé pendant le chaos du renommage.
- **60% des organisations n'ont pas de bouton d'arrêt d'urgence** pour stopper leurs agents quand ils déconnent.

Même un des mainteneurs du projet a averti sur Discord :

**"Si vous ne savez pas utiliser une ligne de commande, ce projet est beaucoup trop dangereux pour vous."**

Et la réponse du fondateur de Moldbook quand Wiz a révélé que sa base de données était ouverte aux quatre vents ? **Il a demandé à son agent IA, celui-là même qu'il avait "vibe-codé", de réparer la faille.** C'est exactement ce qu'on ne fait pas chez Drakkar.

### Le vrai problème

Simon Willison, chercheur en sécurité IA, appelle ça la **"trifecta létale"** : un agent qui a accès à vos données privées, qui reçoit du contenu de sources extérieures, et qui peut envoyer des messages ou exécuter des actions. Mettez ces trois trucs ensemble et n'importe quel message entrant peut reprogrammer l'agent à votre insu.

Ajoutez la mémoire persistante et ça devient pire : une instruction malveillante cachée dans un WhatsApp forwardé reste dans le contexte de l'agent pendant des semaines. Elle peut se déclencher à retardement.

---

## 3. BREAKING — Steinberger rejoint OpenAI (15 février 2026)

Pendant que je finalisais cette note, l'info est tombée. **Peter Steinberger, le créateur d'OpenClaw, rejoint OpenAI.** Annonce de Sam Altman dimanche soir sur X. Mission : piloter la prochaine génération d'agents personnels.

OpenClaw passe en fondation open source. Steinberger garde un pied dedans. Mais son temps, son énergie et son accès aux modèles de frontière vont désormais à OpenAI.

### Pourquoi c'est un signal fort

Meta et OpenAI le courtisaient. Zuckerberg et Altman l'ont appelé personnellement. Nadella aussi. Des VCs lui proposaient de monter sa propre boîte à plusieurs milliards de valorisation. Il a tout refusé.

Sa logique publique : « je veux changer le monde, pas construire une grande entreprise. »

La logique réelle est probablement plus prosaïque. Un mois de harcèlement crypto, trois renommages forcés, un projet à perte (10 à 20k$/mois de revenus, plus en coûts), et un mainteneur au bord du burnout qui a failli tout supprimer. OpenAI lui offre les modèles, l'infra, la distribution et la paix. Deal rationnel.

Pour OpenAI, c'est un acqui-hire chirurgical. Ils récupèrent le développeur qui a prouvé qu'un agent personnel pouvait capter l'attention de la planète en deux semaines : 180 000 stars GitHub, 2 millions de visiteurs en une semaine. Et ils envoient un signal vers la communauté open source, un terrain où OpenAI se fait régulièrement attaquer.

### Le débat : fin de l'open source ou bonne nouvelle ?

C'est LA question. Et les réponses divergent.

**Côté optimiste.** La fondation maintient le code ouvert. Steinberger en a fait une condition non négociable. OpenAI sponsorise financièrement. Le projet continue de supporter plusieurs modèles (Claude, GPT, DeepSeek, modèles locaux). Sur le papier, rien ne change.

**Côté sceptique.** Dermot McGrath, co-fondateur de ZenGen Labs, résume le problème en une phrase : ces projets vivent et meurent par leurs contributeurs à plein temps, et Steinberger EST OpenClaw. Quand le créateur part construire les produits fermés d'OpenAI, la communauté perd son moteur. On a vu ce schéma des dizaines de fois. Un projet passe en fondation, l'acquéreur promet du soutien, et deux ans plus tard c'est en maintenance passive.

Sur Hacker News, un autre angle émerge. Plusieurs développeurs pointent que c'est un fumble d'Anthropic. Le projet est né sur Claude. Steinberger se décrivait comme « la plus grosse publicité non payée pour Claude Code. » Et c'est Anthropic qui l'a poussé dehors avec une plainte de marque sur le nom « Clawdbot. » OpenAI a ramassé ce qu'Anthropic a jeté. Un commentateur résume : Anthropic protège son app au lieu de protéger son écosystème.

### Le modèle Chrome/Chromium appliqué aux agents

Voici ce qui va se passer. Et c'est le vrai takeaway de cette section.

Quand Altman dit qu'OpenClaw deviendra « core to our product offerings », il ne parle pas de la fondation open source. Il parle d'un produit fermé, intégré à ChatGPT, payant.

C'est exactement le playbook Chrome/Chromium que Google a perfectionné depuis 15 ans.

Google maintient Chromium en open source. N'importe qui peut le forker, le modifier, le distribuer. Brave, Edge, Opera, Vivaldi : tous construits sur Chromium. Le code est libre. La communauté contribue. L'écosystème vit.

Mais personne n'utilise Chromium. **Tout le monde utilise Chrome.** La version fermée, avec les services Google intégrés, la synchro, les données, l'expérience fluide. Chromium est le laboratoire public. Chrome est le produit.

OpenAI va faire la même chose avec les agents. OpenClaw la fondation sera le terrain de jeu communautaire : les hackers, les bidouilleurs, les devs qui veulent « own their data. » Le vrai produit sera l'agent personnel intégré à ChatGPT. Fermé. Cloud. Payant. Avec 300 millions d'utilisateurs déjà captifs.

Et comme Chrome a fini par contrôler 65% du web, l'agent OpenAI sera le standard de fait. Pas parce qu'il est meilleur. Parce qu'il est là, intégré, et que personne ne veut configurer un reverse proxy pour faire tourner un agent en local.

### Et maintenant, ajoutez la pub

J'ai publié une analyse publique de cette situation sur LinkedIn cette semaine (lien : [POST LINKEDIN À INSÉRER]). Ce qui suit est la version longue, avec les détails que je ne peux pas mettre dans un post.

Le modèle Chrome/Chromium ne raconte que la moitié de l'histoire. L'autre moitié est tombée le 9 février : **OpenAI a lancé les publicités dans ChatGPT.** Ce n'est plus un projet. C'est en production.

Les utilisateurs gratuits et Go voient des pubs ciblées en bas de leurs réponses, sélectionnées en fonction du contenu de leurs conversations. Mais le détail qui compte est dans la page d'aide officielle d'OpenAI, et il faut le lire lentement : « Si la mémoire est activée, ChatGPT peut sauvegarder et utiliser les souvenirs et les conversations récentes pour sélectionner une publicité. » La personnalisation publicitaire est activée par défaut. Les utilisateurs peuvent la désactiver, mais le ciblage contextuel (basé sur la conversation en cours) reste actif même sans personnalisation.

Autrement dit : le même système de mémoire persistante qui rend les agents utiles -- celui qui se souvient que vous cherchez un comptable, que vous avez un budget de 50k€, que vous êtes en conflit avec un fournisseur -- est aussi le système qui sélectionne les pubs. Ce n'est pas un détournement. C'est le design.

Cinq jours plus tôt, Anthropic avait acheté des spots pendant le Super Bowl -- un investissement de plusieurs millions de dollars -- pour une seule idée : vos conversations avec une IA ne devraient pas être un espace publicitaire. Les pubs montraient un chatbot qui dérivait vers des sites de rencontre et des semelles compensées au milieu d'une conversation intime. Slogan : « Ads are coming to AI. But not to Claude. » Résultat : Claude est passé du 41e au 7e rang sur l'App Store US en trois jours. +32% de téléchargements. +11% d'utilisateurs actifs quotidiens.

Altman a répondu en accusant Anthropic de « malhonnêteté » et de servir « un produit cher aux riches. » Le fait qu'il ait répondu est en soi un signal. Comme le note Scott Galloway : quand on est leader du marché, on ne cite jamais le concurrent. Hertz ne parle pas d'Avis. Coca ne parle pas de Pepsi. Qu'Altman consacre un thread entier à défendre sa position prouve qu'Anthropic a touché un nerf.

La question n'est pas de savoir si les pubs de ChatGPT sont « bien faites » ou « transparentes. » La question, c'est l'alignement des incentives. Un modèle financé par la pub optimise le temps passé et l'engagement. C'est le moteur de Google, de Meta, de l'internet tel qu'on le connaît depuis 20 ans. OpenAI promet que ses pubs n'influencent pas les réponses. Google disait la même chose des résultats organiques en 2004. Vingt ans plus tard, les quatre premiers résultats de n'importe quelle requête sont des pubs.

**Maintenant, connectez ça aux agents.** Relisez la section 2. Un agent a accès à vos mails, vos fichiers, vos messages, votre calendrier. Il a une mémoire persistante. Il pulse toutes les cinq minutes. Il sait ce que vous avez dit à votre comptable mardi et ce que votre client vous a envoyé sur WhatsApp vendredi. Maintenant imaginez que le fournisseur de ce modèle finance son infrastructure par la publicité. Que la personnalisation publicitaire est activée par défaut. Que le système utilise les conversations passées et les souvenirs de l'agent pour sélectionner les pubs.

On n'est plus dans le débat théorique. On est dans la « trifecta létale » de Simon Willison, mais avec un annonceur dans la boucle.

Si OpenAI intègre un agent personnel dans ChatGPT -- ce que le recrutement de Steinberger confirme -- cet agent sera financé, au moins en partie, par la pub. La fondation OpenClaw sera open source. Le vrai produit sera fermé, cloud, payant, et traversé par un modèle publicitaire.

### Pourquoi Drakkar utilise Claude

Soyons précis, parce que ce sujet mérite de l'honnêteté intellectuelle, pas du cheerleading.

**Ce qu'Anthropic fait bien.** Leur modèle économique repose sur les abonnements et les contrats entreprise. Pas de pub. Pas de data vendue à des annonceurs. Pas de personnalisation publicitaire. Leur revenu dépend de la qualité du produit, pas de l'attention captée. Sur les offres commerciales -- Claude for Work, Enterprise, API, Amazon Bedrock, Google Cloud Vertex -- les conditions contractuelles interdisent explicitement l'utilisation des données pour l'entraînement des modèles. Pas d'opt-out à activer. C'est exclu par contrat. C'est la norme sur laquelle on s'appuie pour nos déploiements clients.

**Ce qu'il faut savoir aussi.** En septembre 2025, Anthropic a modifié sa politique pour les comptes consommateurs (Free, Pro, Max). Les conversations peuvent désormais être utilisées pour l'entraînement des modèles si l'utilisateur accepte, avec une rétention étendue à cinq ans. Le toggle était pré-coché sur « On » dans le flow d'acceptation. Ce n'est pas anodin. Ça veut dire que si quelqu'un dans l'équipe utilise un compte Pro personnel pour du travail client, les protections ne sont pas les mêmes que sur nos comptes commerciaux. D'où la règle en section 5 : comptes Drakkar uniquement.

**L'angle souveraineté.** Quand on travaille avec des ETI françaises -- Lidl, SNCF, Seb -- la question de la souveraineté des données n'est pas un argument marketing. C'est une exigence contractuelle. Le RGPD impose que le traitement des données ait une base légale claire, que la finalité soit définie, et que les transferts hors UE soient encadrés. Un système qui utilise le contenu des conversations professionnelles comme signal de ciblage publicitaire crée une ambiguïté sur la finalité du traitement. Est-ce que les données de votre agent sont traitées pour vous aider, ou pour vendre de l'espace pub ? Avec Anthropic en offre commerciale, la réponse est contractuellement verrouillée : aucune utilisation au-delà du service.

**Pour Drakkar, c'est non négociable.** Le choix du fournisseur d'IA n'est pas une décision technique. C'est une décision de confiance. On ne peut pas mettre les données opérationnelles de nos clients dans un système dont le modèle économique repose sur la monétisation de l'attention et du contenu des conversations. La question que je pose dans mon post LinkedIn est la même que je pose ici : confieriez-vous vos mails, vos fichiers et votre agenda à une IA financée par la publicité ?

Anthropic l'a compris. C'est pour ça qu'on travaille avec Claude. Et c'est pour ça que les règles de la section suivante existent.

---

## 4. Pourquoi toute l'industrie tremble

Pendant que le chaos OpenClaw occupait les développeurs, trois signaux forts sont tombés en même temps.

### OpenAI Frontier

Le 5 février, OpenAI a lancé Frontier. Ce n'est pas un nouveau chatbot. C'est une **plateforme pour créer, déployer et gérer des flottes entières d'agents IA en entreprise**. Premiers clients : Intuit, State Farm, Thermo Fisher, Uber, HP, Oracle.

Fidji Simo, CEO Applications d'OpenAI, annonce que "d'ici la fin de l'année, la plupart du travail digital sera dirigé par des humains et exécuté par des flottes d'agents."

Le plus important : dans leur diagramme d'architecture, **Frontier se positionne AU-DESSUS des systèmes de record** (Salesforce, SAP, Microsoft, Workday). Ce n'est pas un détail technique. C'est une déclaration de guerre contre toute l'industrie du logiciel d'entreprise. Frontier transforme ces plateformes en backends commoditisés et déplace le "Système d'Intelligence" vers la couche d'orchestration des agents.

Les investisseurs ont immédiatement réagi. Les actions de Salesforce, ServiceNow, Workday et SAP ont chuté après l'annonce.

### Les contre-attaques

Tout le monde bouge :

- **Microsoft** a répondu avec Agent 365 et un memo interne contenant des contre-arguments point par point.
- **Meta** a acquis Manus AI, entrée par acquisition dans la course agentique.
- **Salesforce** pousse AgentForce, agents intégrés nativement dans leur CRM.
- **LangChain** a levé plus de 150 millions de dollars. **CrewAI** plus de 20 millions.
- **Gartner** (décembre 2025) a qualifié les plateformes de gestion d'agents de "terrain le plus précieux de l'IA."

### La mort annoncée du modèle "par utilisateur"

Si un agent peut exécuter des workflows de vente sans qu'un humain ne se connecte jamais à Salesforce ou à Odoo, les frais de licence par utilisateur perdent leur justification. Le modèle économique de tout le SaaS entreprise est remis en question. C'est un changement structurel, pas une mode.

### La vision YC 2026

Y Combinator, dans son dernier Request for Startups, est explicite : l'avenir n'est plus de vendre du logiciel aux clients pour les aider à faire le travail. C'est d'utiliser l'IA pour faire le travail et vendre le résultat. Une agence de design qui produit du travail custom avant même de signer le contrat. Un hedge fund où des essaims d'agents analysent les 10-K, les earnings calls, les filings SEC, synthétisent et exécutent.

YC a dédié plus de 50% de son batch Spring 2025 à des startups d'IA agentique. Gartner prédit que 75% des entreprises utiliseront des agents IA d'ici fin 2026 (contre moins de 5% en 2025). Les requêtes sur les systèmes multi-agents ont explosé de 1 445% entre Q1 2024 et Q2 2025. C'est pas une tendance. C'est le nouveau socle.

---

## 5. Les règles chez Drakkar

Je veux être clair sur un point : **je veux que vous testiez, que vous expérimentiez, que vous mettiez les mains dedans.** On ne peut pas vendre ce qu'on ne comprend pas. On ne peut pas conseiller nos clients sur les agents si on ne les a pas utilisés soi-même. L'objectif n'est pas de vous éloigner de ces outils. C'est de vous assurer que vous les approchez correctement.

Pour info, j'ai acheté un Mac Mini dédié et setup OpenClaw, entre autres. Je partagerai les résultats dans les mois à venir. Je ne vous demande rien que je ne fais pas moi-même.

Mais après ce que vous venez de lire dans la section 2, le cadre doit être clair.

### Le principe

**N'utilisez pas un outil que vous ne maîtrisez pas.** Si vous ne savez pas ce qu'est un sandboxing, si vous ne savez pas isoler une VM, si vous ne savez pas configurer un reverse proxy, si vous passez par une solution hébergée en ligne parce que le setup local vous dépasse, alors cet outil n'est pas pour vous. Point.

Ce n'est pas une question de curiosité ou d'ambition, c'est une question de compétence. Utiliser un outil qu'on ne comprend pas sur de l'infra pro, c'est mettre en danger nos clients. Rappel : le fondateur de Moldbook a demandé à son propre agent de corriger une faille de sécurité critique. C'est exactement ce qu'on ne fait pas.

### Concrètement

**1. Interdiction totale** d'utiliser OpenClaw, Claude Cowork, ou tout outil ayant un accès large à votre système sur vos machines pro, boîtes mail pro, clés API pro, ou accès clients. Aucune exception.

**2. L'expérimentation est encouragée**, mais sur un environnement dédié et isolé : machine dédiée, comptes dédiés, clés dédiées. Zéro croisement avec l'infra pro. Si vous ne savez pas comment faire ça proprement, demandez avant de lancer quoi que ce soit. On vous aidera à monter l'environnement.

**3. Si vous repérez un usage non conforme** chez un client ou en interne, vous remontez immédiatement. Pas la semaine prochaine. Immédiatement.

**4. Veille obligatoire.** Si un client vous pose la question sur les agents IA, vous devez être capable de lui expliquer ce que cette note contient : les cinq phases, les risques, les opportunités, et pourquoi Drakkar est le bon partenaire pour naviguer cette transition. On déploie de l'IA chez Lidl, SNCF, Seb. On ne peut pas être moins informés que les gens à qui on vend nos services.

---

## 6. Ce que ça signifie pour Drakkar

### Pour Drakkar Accélérateur (Odoo)

Si la couche d'orchestration d'agents (Frontier, Claude Cowork, etc.) se positionne au-dessus des ERP, notre valeur ne peut plus être uniquement dans l'intégration Odoo. Elle doit être dans notre capacité à rendre les entreprises "agent-ready" : des données propres, des processus clairs, des API accessibles. L'ERP devient le socle sur lequel les agents opèrent. Ceux qui auront les données les mieux structurées gagneront. Notre métier ne disparaît pas. Il monte en grade.

### Pour Drakkar Studio

Les agents changent la nature même du développement. Claude Code, avec ses capacités multi-agents (Swarms), permet déjà à une équipe de spécialistes IA de travailler en parallèle sur un même projet. Les délais de développement se compressent. Notre avantage compétitif doit être dans l'architecture, la sécurité et la gouvernance, pas dans le nombre de lignes de code.

### Pour Drakkar IA

C'est l'unité qui a le plus à gagner. Le marché a un besoin massif de déploiements d'agents sécurisés et gouvernés pour les PME et ETI. Personne ne fait ça proprement en France aujourd'hui. 60% des organisations n'ont pas de kill switch. La grande majorité n'a aucune politique de sécurité pour les agents. C'est exactement là où Drakkar IA doit se positionner : le partenaire qui rend les agents IA sûrs pour la production.

Depuis presque un an, on travaille sur un projet qui adresse exactement ça. J'en dirai plus dans les semaines qui viennent.

Carlos Lozano (ancien Salesforce AgentForce, maintenant en stealth) le dit bien sur Silicon Carne : **la course n'est pas à l'intelligence, mais à la fiabilité, la gouvernabilité et la responsabilité.** C'est notre terrain.

---

## Conclusion

Ce qui se passe avec les agents IA va s'accélérer. Chaque semaine apporte de nouveaux outils, de nouveaux risques, de nouvelles opportunités. C'est un virage majeur, pas un épisode de hype comme les NFT ou le metaverse. La preuve : OpenAI, Microsoft, Meta, Salesforce, Google, Anthropic se repositionnent tous en même temps. Quand tous les géants bougent dans la même direction, ce n'est pas du bruit.

J'attends de chacun d'entre vous que cette note soit lue, comprise, et intégrée. Si vous avez des questions, posez-les. Si vous voyez des opportunités chez vos clients, remontez-les. Si vous ne comprenez pas quelque chose, c'est le moment.

**Ceux qui comprennent ce qui se passe et avancent auront le choix. Les autres non.**

Nathan
