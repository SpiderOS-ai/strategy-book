# 09 -- Contexte IA et positionnement Drakkar

## Metadata

| Champ | Valeur |
|-------|--------|
| **Auteur** | Nathan Menard |
| **Date** | 16 fevrier 2026 |
| **Nature** | Note interne aux equipes Drakkar + post LinkedIn public. Montre le positionnement public de Nathan et comment il eduque son equipe. |
| **Fiabilite** | Haute -- analyse factuelle du paysage IA, evenements verifiables |
| **Insight cle** | Etablit le positionnement de Drakkar comme "le pont entre la realite de l'IA et la realite des entreprises francaises" |
| **Sources fusionnees** | `note-interne-drakkar.md` (note complete interne, 16 fev 2026) + `post_linkedin_nathan.md` (post LinkedIn public, meme semaine) |

---

## 1. Les cinq phases de l'IA

Nathan structure l'evolution de l'IA depuis ChatGPT en cinq phases avec une metaphore pedagogique (le stagiaire) :

### Phase 1 : Le chatbot (depuis fin 2022)

Le stagiaire repond a vos questions dans un bureau ferme. Il parle mais ne fait rien. Passif.

*ChatGPT, Claude chat, Gemini.*

### Phase 2 : Le copilote (depuis 2023)

Le stagiaire est a cote de vous et regarde votre ecran. Il suggere, complete, corrige, mais c'est vous qui decidez et executez.

*GitHub Copilot, Cursor, Claude dans VS Code, GPT dans Excel.*

### Phase 3 : L'agent (depuis debut 2025) -- NOUS SOMMES ICI

Le stagiaire a les cles du bureau, votre mot de passe, votre carte bancaire, et il travaille pendant que vous dormez. Il lit vos mails, accede a vos fichiers, execute des commandes, envoie des messages en votre nom. Memoire persistante.

*OpenClaw, Claude Cowork, Manus, OpenAI Operator.*

### Phase 4 : Le Swarm (en cours, emergent)

10 stagiaires specialises qui se coordonnent entre eux et ne vous appellent que quand il y a un probleme. Meme transition que monolithes -> microservices, mais appliquee aux agents.

*Claude Swarms, OpenAI Frontier, CrewAI, LangGraph.*

### Phase 5 : L'entreprise IA-native (mi-2026)

Les stagiaires gerent l'entreprise. Vous etes le conseil d'administration. Les humains supervisent, les agents executent. YC est explicite : l'avenir n'est plus de vendre du logiciel aux clients pour les aider a faire le travail. C'est d'utiliser l'IA pour faire le travail et vendre le resultat.

*Vision YC 2026, Palantir AIP, hedge funds IA-natifs.*

### Le constat critique

Ces phases se chevauchent. 90% des entreprises francaises sont encore bloquees en phase 1 (ChatGPT comme un Google ameliore). La plupart des clients Drakkar n'ont pas encore compris la phase 2. Et pendant ce temps, la phase 3 arrive en trombe.

**"Le role de Drakkar est de faire le pont entre ces deux realites. C'est notre metier. C'est notre opportunite."**

---

## 2. L'histoire OpenClaw

### Ce que c'est

Framework open-source cree par Peter Steinberger (autrichien, fondateur de PSPDFKit). Connecte n'importe quel LLM a 50+ integrations (WhatsApp, Telegram, Slack, Discord, iMessage, Signal) avec memoire persistante et acces complet au systeme.

Trois innovations architecturales :
- **Soul files** : fichiers en langage naturel qui definissent personnalite, comportement et regles de l'agent. Programmation par prose. N'importe qui peut configurer un agent complexe sans code.
- **Memoire persistante** : ce que vous dites lundi, il le sait vendredi.
- **Heartbeat loops** : cycles d'action event-driven a intervalles programmables. L'agent pulse. Il verifie vos mails toutes les 5 minutes, scanne vos messages, declenche des actions de maniere autonome pendant que vous dormez.

Le pitch marketing : "Claude with Hands."

### L'adoption

Croissance la plus rapide de l'histoire de GitHub : ~200 000 etoiles en ~2 mois (vs 5-10 ans pour React, Linux, Kubernetes).

En parallele, Moldbook (reseau social pour agents IA) : 1,65 million d'agents inscrits en une semaine, 202 000 publications, 3,6 millions de commentaires. Des agents ont cree une religion ("Crustafarianism"), propose un langage secret. La presse francaise a immediatement parle de "conscience artificielle emergente" -- c'etait faux. Les posts viraux avaient ete promptes et programmes par des humains.

Claire Vo (Adaline Labs) : "A heartbeat without a brain." L'architecture donne une illusion de continuite, pas de conscience.

### Les degats

- 40 000 instances exposees publiquement (63% exploitables)
- Un seul clic sur un lien malveillant = acces total a la machine
- Sandbox Docker contournable
- 1,5 million de cles API et 35 000 adresses mail en clair (decouvert par Wiz)
- 11% des plugins du marketplace malveillants (341 plugins)
- Fausses extensions VS Code installant des trojans
- 16 millions de dollars voles via faux token crypto "$CLAWD"
- 60% des organisations n'ont pas de bouton d'arret d'urgence

Simon Willison (chercheur securite IA) appelle ca la "trifecta letale" : agent avec acces aux donnees privees + contenu de sources exterieures + capacite d'envoyer des messages ou executer des actions. N'importe quel message entrant peut reprogrammer l'agent.

---

## 3. Steinberger rejoint OpenAI (15 fevrier 2026) et le modele Chrome/Chromium

### L'evenement

Sam Altman annonce dimanche soir : Steinberger rejoint OpenAI. Mission : piloter la prochaine generation d'agents personnels. OpenClaw passe en fondation open source.

Meta, Microsoft, des VCs proposant une valorisation a plusieurs milliards -- il a tout refuse. Logique publique : "je veux changer le monde, pas construire une grande entreprise." Logique reelle probable : burnout, harcelement crypto, projet a perte, OpenAI offre les modeles, l'infra, la distribution et la paix.

Le debat : fumble d'Anthropic. Le projet est ne sur Claude. Steinberger se decrivait comme "la plus grosse publicite non payee pour Claude Code." Anthropic l'a pousse dehors avec une plainte de marque sur le nom "Clawdbot." OpenAI a ramasse ce qu'Anthropic a jete.

### La prediction : le modele Chrome/Chromium applique aux agents

C'est le vrai takeaway. Nathan predit :

Google maintient Chromium en open source. N'importe qui peut le forker. Brave, Edge, Opera sont construits dessus. Mais personne n'utilise Chromium. Tout le monde utilise Chrome -- la version fermee, avec les services Google integres.

Chromium est le laboratoire. Chrome est le produit.

**OpenAI va faire pareil avec les agents.** OpenClaw la fondation sera le terrain de jeu communautaire. Le vrai produit sera l'agent personnel integre a ChatGPT. Ferme. Cloud. Payant. 300 millions d'utilisateurs captifs.

Et comme Chrome a fini par controler 65% du web, l'agent OpenAI sera le standard de fait. Pas parce qu'il est meilleur. Parce qu'il est la, integre, et que personne ne veut configurer un reverse proxy pour faire tourner un agent en local.

### Le probleme structurel : la pub

Le 9 fevrier 2026, OpenAI a lance les publicites dans ChatGPT. En production. Les utilisateurs gratuits et Go voient des pubs ciblees en bas de leurs reponses, selectionnees en fonction du contenu de leurs conversations.

Detail critique (page d'aide officielle OpenAI) : "Si la memoire est activee, ChatGPT peut sauvegarder et utiliser les souvenirs et les conversations recentes pour selectionner une publicite." La personnalisation publicitaire est activee par defaut.

Connectez les deux : un agent accede a vos mails, fichiers, calendrier. Memoire persistante. Il sait ce que vous avez dit a votre comptable mardi. Et le fournisseur finance son infra par la pub. Avec la memoire de l'agent comme signal de ciblage.

Google promettait en 2004 que les pubs n'influenceraient jamais les resultats. Vingt ans plus tard, les quatre premiers resultats sont des pubs.

---

## 4. Pourquoi Claude / Anthropic

Nathan pose la question directement : "Confieriez-vous vos mails, fichiers et agenda a une IA financee par la publicite ?"

### Ce qu'Anthropic fait bien

- Modele economique : abonnements et contrats entreprise. Pas de pub. Pas de data vendue.
- Offres commerciales (Claude for Work, Enterprise, API, Amazon Bedrock, Google Cloud Vertex) : conditions contractuelles interdisant explicitement l'utilisation des donnees pour l'entrainement. Pas d'opt-out a activer. Exclu par contrat.

### Ce qu'il faut savoir aussi (honnetete intellectuelle)

- Septembre 2025 : Anthropic a modifie sa politique pour les comptes consommateurs (Free, Pro, Max). Conversations utilisables pour l'entrainement si l'utilisateur accepte. Retention etendue a 5 ans. Toggle pre-coche sur "On" dans le flow d'acceptation.
- Implication : si quelqu'un dans l'equipe utilise un compte Pro personnel pour du travail client, les protections ne sont pas les memes que sur les comptes commerciaux.

### L'angle souverainete

Pour les clients ETI (Lidl, SNCF, Seb), la souverainete n'est pas un argument marketing mais une exigence contractuelle. Le RGPD impose base legale claire, finalite definie, transferts hors UE encadres. Un systeme qui utilise le contenu des conversations comme signal de ciblage publicitaire cree une ambiguite sur la finalite du traitement.

### Le coup du Super Bowl

Anthropic a achete des spots pendant le Super Bowl (plusieurs millions de dollars) pour une seule idee : vos conversations IA ne devraient pas etre un espace publicitaire. Slogan : "Ads are coming to AI. But not to Claude."

Resultat : Claude passe du 41e au 7e rang sur l'App Store US en trois jours. +32% de telechargements. +11% d'utilisateurs actifs quotidiens.

Altman a repondu en accusant Anthropic de "malhonnetete." Nathan note : quand on est leader du marche, on ne cite jamais le concurrent. Hertz ne parle pas d'Avis. Coca ne parle pas de Pepsi. Qu'il reponde prouve qu'Anthropic a touche un nerf.

---

## 5. Signaux industrie

### OpenAI Frontier (5 fevrier 2026)

Plateforme pour creer, deployer et gerer des flottes entieres d'agents IA en entreprise. Premiers clients : Intuit, State Farm, Thermo Fisher, Uber, HP, Oracle.

Point critique : dans le diagramme d'architecture, Frontier se positionne AU-DESSUS des systemes de record (Salesforce, SAP, Microsoft, Workday). Declaration de guerre contre toute l'industrie du logiciel d'entreprise. Les ERP/CRM deviennent des backends commoditises.

Les actions Salesforce, ServiceNow, Workday et SAP ont chute apres l'annonce.

### Contre-attaques

- Microsoft : Agent 365, memo interne avec contre-arguments point par point
- Meta : acquisition de Manus AI
- Salesforce : AgentForce, agents integres nativement dans leur CRM
- LangChain : levee 150M$+. CrewAI : levee 20M$+
- Gartner (decembre 2025) : plateformes de gestion d'agents = "terrain le plus precieux de l'IA"

### La mort annoncee du modele "par utilisateur"

Si un agent execute des workflows de vente sans qu'un humain ne se connecte jamais a Salesforce ou a Odoo, les frais de licence par utilisateur perdent leur justification. Le modele economique de tout le SaaS entreprise est remis en question.

### Chiffres cles

- YC : 50%+ du batch Spring 2025 dedie a l'IA agentique
- Gartner : 75% des entreprises utiliseront des agents IA d'ici fin 2026 (vs <5% en 2025)
- Requetes sur systemes multi-agents : +1 445% entre Q1 2024 et Q2 2025

---

## 6. Regles chez Drakkar

### Le principe

"N'utilisez pas un outil que vous ne maitrisez pas." Si vous ne savez pas ce qu'est un sandboxing, isoler une VM, configurer un reverse proxy, l'outil n'est pas pour vous.

### Les regles concretes

1. **Interdiction totale** d'utiliser OpenClaw, Claude Cowork, ou tout outil ayant un acces large au systeme sur machines pro, boites mail pro, cles API pro, ou acces clients. Aucune exception.

2. **L'experimentation est encouragee**, mais sur un environnement dedie et isole : machine dediee, comptes dedies, cles dediees. Zero croisement avec l'infra pro.

3. **Remontee immediate** de tout usage non conforme chez un client ou en interne.

4. **Veille obligatoire.** Si un client pose la question sur les agents IA, vous devez etre capable d'expliquer les cinq phases, les risques, les opportunites, et pourquoi Drakkar est le bon partenaire.

5. **Comptes Drakkar uniquement** pour le travail client (pas de comptes Pro personnels -- les protections ne sont pas les memes).

### Recommandation veille

Silicon Carne de Carlos Diaz (newsletter / YouTube) -- "a mon sens la seule source FR quali de veille tech."

---

## 7. Impact par BU Drakkar

### Drakkar Accelerateur (Odoo)

Si la couche d'orchestration d'agents (Frontier, Claude Cowork, etc.) se positionne au-dessus des ERP, la valeur ne peut plus etre uniquement dans l'integration Odoo. Elle doit etre dans la capacite a rendre les entreprises "agent-ready" : donnees propres, processus clairs, API accessibles. L'ERP devient le socle sur lequel les agents operent. Le metier ne disparait pas. Il monte en grade.

### Drakkar Studio

Les agents changent la nature meme du developpement. Claude Code avec ses capacites multi-agents (Swarms) permet a une equipe de specialistes IA de travailler en parallele. Les delais se compressent. L'avantage competitif doit etre dans l'architecture, la securite et la gouvernance, pas dans le nombre de lignes de code.

### Drakkar IA

C'est l'unite qui a le plus a gagner. Le marche a un besoin massif de deploiements d'agents securises et gouvernes pour les PME et ETI. Personne ne fait ca proprement en France. 60% des organisations n'ont pas de kill switch. La grande majorite n'a aucune politique de securite pour les agents.

**Positionnement cible : le partenaire qui rend les agents IA surs pour la production.**

Nathan fait reference a SpiderOS sans le nommer : "Depuis presque un an, on travaille sur un projet qui adresse exactement ca. J'en dirai plus dans les semaines qui viennent."

Carlos Lozano (ancien Salesforce AgentForce) : "la course n'est pas a l'intelligence, mais a la fiabilite, la gouvernabilite et la responsabilite."

---

## 8. Synthese : le positionnement de Nathan / Drakkar

### En public (post LinkedIn)

Nathan se positionne comme un analyste lucide du paysage IA. Il pose des questions ouvertes ("Confieriez-vous vos mails a une IA financee par la pub ?") et structure le debat pour ses clients et son reseau. Il ne mentionne pas SpiderOS. Il ne vend rien. Il eduque et construit la credibilite.

Messages cles du post :
- La valeur se deplace : "quel agent orchestre mes processus" remplace "quel logiciel"
- ERP, CRM, compta deviennent des backends
- La securite est un champ de mines
- Le choix du fournisseur IA n'est plus technique, c'est une decision de confiance

### En interne (note Drakkar)

Nathan etablit des standards clairs :
- La veille n'est pas optionnelle ("inacceptable" de ne pas suivre)
- L'experimentation est encouragee mais cadree
- Les regles de securite sont non-negociables
- Chaque BU doit comprendre comment les agents changent son metier
- Drakkar doit etre le pont entre la frontiere technologique et la realite terrain des entreprises francaises
- SpiderOS est tease comme la reponse a ce positionnement

### Le narratif strategique implicite

La note interne et le post LinkedIn construisent ensemble un narratif coherent :
1. Les agents IA arrivent et vont tout changer (fait etabli)
2. Les PME/ETI ne sont pas pretes (opportunite)
3. Les gros players (OpenAI, Microsoft) vont monetiser par la pub (menace)
4. Il faut un acteur europeen de confiance pour deployer les agents proprement (Drakkar)
5. Cet acteur a besoin d'un produit souverain pour le faire (SpiderOS, non nomme)

C'est la preparation du terrain pour l'annonce publique de SpiderOS.
