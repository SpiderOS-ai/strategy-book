# Echange Nathan / Remy -- 20 fevrier 2026

## Metadata

| Champ | Valeur |
|-------|--------|
| **Date** | 20 fevrier 2026 |
| **Type** | Appel telephonique |
| **Duree** | ~20 minutes |
| **Participants** | Nathan Menard (CEO Drakkar/Spider), Remy Menard (CTO Spider) |
| **Contexte** | Debrief post-CODIR du 19 fevrier. Nathan informe Remy des avancees strategiques et financieres. Discussion technique sur les estimations, l'hebergement et le projet Astrid. |
| **Qualite transcription** | Moyenne -- appel telephonique avec coupures de parole frequentes, phrases fragmentees par la transcription automatique. Deux interlocuteurs uniquement (moins d'erreurs d'attribution que les CODIR). |
| **Nettoyage** | Reconstruction des phrases coupees, suppression des fragments parasites, reattribution si necessaire, reorganisation thematique. |

---

## Resume executif

Nathan appelle Remy au lendemain du CODIR avec Jean et Thierry. L'alignement strategique progresse : Spider va couter 400-500K EUR equivalent en annee 1 (postes de depenses directs + salaire Nathan + temps des equipes internes). La question n'est plus "est-ce qu'on le fait" mais "comment on le finance" (dette bancaire, CIR, subventions innovation). Nathan evoque la possibilite que Remy devienne salarie pour declarer son temps au CIR. Cote equite, Nathan est au taquet de la negociation et ne voit pas ce qu'il peut ceder de plus. Jordan (ami de Nathan, 1M+ EUR CA en affichage publicitaire) est identifie comme premier POC client. Le projet Astrid (site web, ~30K EUR) sera le premier vrai test de production Spider. Discussion technique approfondie sur le systeme d'estimation (temps agent vs temps supervision humaine), l'hebergement Kubernetes, la gestion de projet dans Spider, et les couts Claude Code Max.

---

## 1. Debrief du CODIR (Jean, Thierry, Nathan)

**Nathan :** Le CODIR du 19 fevrier avec Jean et Thierry a bien avance. L'alignement est en cours. Nathan porte le risque principal mais tout le monde converge.

> **Nathan :** "Hier, on a avance avec Jean et Thierry, gros CODIR. C'est cool, ca avance bien, on est en train de s'aligner globalement. De toute facon, c'est un peu moi qui porte le risque. Mais ca va se faire. Il n'y a pas de doute."

**Remy :** Accueille positivement la nouvelle. Note que c'etait dans l'interet de tout le monde de trouver un accord.

> **Remy :** "C'est cool, ca va dans la bonne direction. Si eux ils sont chauds et que tu as reussi, c'est toujours mieux."

> **Remy :** "C'est vrai qu'apres tout, c'etait quand meme dans l'interet de tout le monde de trouver un accord la-dessus."

---

## 2. Investissement Spider : 400-500K EUR equivalent en annee 1

**Nathan :** Detaille la structure des couts de Spider pour l'annee 1.

Decomposition :
- **100-150K EUR minimum** en postes de depenses directs (infra, outils, credits IA, etc.)
- **Salaire de Nathan** (non chiffre dans l'echange)
- **Temps des personnes internes Drakkar** qui vont tester et utiliser Spider (force commerciale notamment)
- **Total equivalent : 400-500K EUR**

> **Nathan :** "Spider, ca va nous couter 100 a 150 000 euros a minima la premiere annee, juste en poste de depenses, plus moi mon salaire, plus en vrai des personnes en interne qui vont devoir tester la force commerciale qu'on va utiliser. Donc en gros, on sait qu'on va investir, je pense, l'equivalent de 400 a 500 000 euros. Et il faut juste qu'on pose l'equilibre global. Mais on sait que c'est ca qu'on veut faire. La question, c'est maintenant le comment."

---

## 3. Financement : CIR, dette bancaire, subventions, statut de Remy

**Nathan :** Explore les pistes de financement pour Spider.

**Options evoquees :**
- **Credit Impot Recherche (CIR)** : Nathan se demande si Spider peut y etre eligible vu la dimension innovation/R&D
- **Subventions innovation** : A explorer vu la nature du projet
- **Dette bancaire** : Envisagee comme option complementaire
- **Statut de Remy** : Question ouverte -- est-ce que Remy devrait devenir "associe salarie" pour pouvoir declarer son temps de travail (probablement au titre du CIR) ? Nathan souligne qu'il faut trouver un equilibre pour que Remy ne soit pas sous-paye.

> **Nathan :** "Je pose aussi des questions de financement. Est-ce qu'on peut avoir du credit impot, typiquement, ou differentes subventions, vu que c'est vraiment de l'innovation. Une des questions -- je n'ai pas du tout les reponses -- c'est : est-ce qu'en fait, il ne faudrait pas que tu sois associe salarie pour qu'on puisse declarer ton temps ? Si c'est le cas, il faudra qu'on voie parce qu'il ne faut pas que tu gagnes que dalle."

**Remy :** Ouvert a la discussion sur son statut.

> **Remy :** "Ok. On pourra en discuter."

---

## 4. Negociations d'equite (mise a jour)

**Nathan :** Il est celui qui fait le plus gros pas dans la negociation en cedant le plus d'equite. Il se sent au maximum de ce qu'il peut conceder. Rien n'est finalise mais il pense que ca va aboutir.

> **Nathan :** "C'est plus moi qui fais le plus gros pas, parce que c'est moi qui lache le plus d'equite dans la bataille. Mais bon, en meme temps, ca aligne tout le monde. On n'a pas finalise, mais je pense que ca va le faire. Je ne sais juste pas comment, sachant que je suis un peu au taquet de la nego. Je ne vois pas trop ce que je peux ceder plus."

---

## 5. Jordan comme premier POC client

**Nathan :** Jordan, un ami de Nathan base a Caen, qui fait de l'affichage publicitaire (1M+ EUR de CA), pourrait etre un bon premier testeur de Spider. L'idee est d'automatiser une partie de son business avec Spider.

> **Nathan :** "Jordan, un de mes potes de Caen, qui a un business -- il fait un million et quelques de CA, il fait de l'affichage publicitaire. Lui, ca pourrait etre un bon testeur."

**Lien avec le business model :** Nathan enchaine sur le modele commercial de Spider : vendre un abonnement + des prestations de creation d'outils automatises. Le systeme d'estimation est crucial pour savoir combien facturer.

> **Nathan :** "Le modele vers lequel on se dirige, c'est de dire : on te vend un abonnement sur le truc, plus un accompagnement. Et donc il faut qu'on soit hyper bons a estimer."

---

## 6. Systeme d'estimation : temps agent vs temps supervision humaine

C'est le sujet technique le plus developpe de l'appel. Nathan et Remy debattent de comment estimer le temps de livraison et le cout d'un projet Spider.

### Le probleme

**Nathan :** Quand Claude donne une estimation (ex: "17 heures"), en realite il le fait en 30 minutes. Il faut trouver un systeme d'estimation fiable et consistant.

> **Nathan :** "Quand Claude me dit 'ca va me prendre 17 heures', en vrai ca lui prend une demi-heure."

### Deux metriques distinctes

**Remy :** Il faut distinguer deux temps differents :
1. **Le temps d'execution de l'agent** (combien de temps l'IA tourne) -- relativement peu important pour le pricing
2. **Le temps de supervision humaine** (prompter, faire les retours, tester) -- c'est CA la vraie metrique pour la facturation

> **Remy :** "Tu t'en prends un peu du temps d'execution. Ce n'est pas trop ca que tu dois calculer, le temps d'execution de l'agent. En fait, tu t'en fous. C'est combien de temps tu vas mettre a lui faire les retours, a le prompter pour qu'il comprenne, a tester ce qu'il a fait. C'est ca en vrai qui compte. Apres, le temps qu'il s'execute, bon."

**Nathan :** Pas d'accord -- le temps agent compte quand meme pour pouvoir dire au client "c'est livre dans 5 jours".

> **Nathan :** "Je trouve que tu ne t'en fous pas, parce qu'a la fin, tu veux quand meme savoir si tu peux lui dire : dans 5 jours, c'est livre ou pas."

**Remy :** Concede qu'il faut les deux estimations, mais note que le temps agent est "hyper petit" par rapport a un projet classique.

> **Remy :** "Tu as les deux estimes en fait. Mais du coup, c'est hyper petit, ca n'a rien a voir avec un projet classique."

### Approche proposee par Nathan : figer le prompt d'estimation

**Nathan :** Idee de figer un prompt d'estimation consistant (ex: "tu es un developpeur de X annees d'experience", ou donner un referentiel). Si l'IA estime de maniere consistante, on peut deduire un ratio reel.

> **Nathan :** "Il faut figer le prompt du style : tu es un developpeur de X annees d'experience, ou bien lui donner un referentiel. Et du coup il va dire des trucs completement aberrants. Mais si on arrive a etre consistant dans la maniere dont il estime, nous on pourra faire un ratio. On va se dire : ok, en fait il evalue a peu pres a fois 10, et donc on connait notre ratio."

### Ratio agent/supervision

**Nathan :** Partage un exemple de ratio qu'il utilisait deja : pour une journee d'agent, il faut compter 1 heure de dev et 1 heure de designer, soit un ratio de 2h humain pour 7h agent.

> **Nathan :** "Pour une journee, je sais que j'ai besoin d'une heure d'un dev et une heure d'un designer. J'avais ce ratio de 1 pour 7 pour chacun, donc 2 pour 7 au final. Ca me permettait d'estimer. C'etait a la louche, mais en vrai, ca marchait plutot bien."

**Nathan :** Propose un format : pour 30 minutes d'agent, 5 minutes de supervision (ratio 1:6). Et tous les "blocs" de 5 heures agent necessitent 30 min a 1h de check humain pour verifier la coherence.

> **Nathan :** "Il y a peut-etre un format a trouver : pour 30 minutes d'agent, 5 minutes de supervision. Et tous les blocs de 5 heures, tu sais que tu as une demi-heure a une heure de check, parce qu'il faut verifier que tout est coherent."

### Complexite IA vs complexite humaine

**Remy :** Souleve un point important : la complexite pour un humain n'est pas la meme que pour une IA. Une feature tres complexe pour un humain peut etre triviale pour l'IA, et inversement.

> **Remy :** "Ce qui est complique aussi, c'est qu'une feature qui serait tres complexe pour un humain, potentiellement l'IA, ca ne va pas du tout etre complexe pour elle. La complexite pour un humain, ce n'est pas du tout la meme que pour une IA."

### Limites de tache agent

**Nathan :** Empiriquement, une tache IA prend entre 2 et 30 minutes. Au-dela de 30 minutes, ca signifie que le scope est trop large et mal decoupe.

> **Nathan :** "Une tache IA, ca lui prend entre 2 et 30 minutes. Ce n'est jamais au-dela. Et meme une demi-heure, c'est trop. Si c'est au-dela, ca veut dire qu'on a vraiment mal scope le truc."

**Remy :** Confirme pour le design : au-dela d'un certain temps, l'agent perd le contexte et commence a "se faire vriller".

> **Remy :** "Le risque, c'est qu'au bout d'un moment, il oublie certains contextes et qu'il n'arrive plus a diviser les blocs entre eux, et il commence a se faire vriller."

### Estimation par plan detaille (proposition Nathan)

**Nathan :** Peut-etre qu'une estimation correcte necessite un gros travail en amont : faire tourner l'agent pendant presque un jour entier pour qu'il produise des plans detailles sur chaque bloc. Ensuite, on peut categoriser.

> **Nathan :** "Peut-etre que meme une estimation, en realite, c'est un travail monstrueux en termes de GPU. Il faut que tu fasses tourner le truc pendant presque un jour entier pour qu'il fasse des plans sur chacun des blocs, et qu'en fonction de ca, tu fasses une categorisation."

### Conclusion sur l'estimation

**Remy :** Pour un premier projet, ce sera forcement a la louche.

> **Remy :** "Pour un premier projet, a mon avis, ca va etre a la louche."

**Nathan :** Accepte l'imprecision mais veut un systeme reference pour pouvoir mesurer les ecarts et apprendre.

> **Nathan :** "Je vois ce projet comme un projet de R&D. Je suis ok avec l'idee qu'il y ait de grandes chances qu'on se plante. J'aimerais bien juste qu'on fasse un systeme que nous on trouve tres bon a l'instant T, pour que si on se plante, on ait un referentiel de combien on s'est plante, pourquoi, ou, comment."

---

## 7. Astrid comme premier vrai projet test

**Nathan :** Le projet Astrid (site web, ~30K EUR) sera le premier vrai test de production avec Spider. C'est un projet de R&D avant tout.

> **Nathan :** "C'est un projet a 30K, et on en a une petite dizaine dans le pipeline."

**Remy :** A besoin d'acces aux maquettes Figma pour pouvoir faire tourner les agents dessus. Il a travaille avec des videos en attendant, mais c'est insuffisant pour les agents.

> **Remy :** "Ils ne m'ont toujours pas donne acces aux maquettes. Je suis tres embete. J'ai fait avec les videos, mais la, si je fais tourner les agents dessus, il faut que je voie les maquettes, que je connecte a Figma et que j'essaye de donner a l'IA le backlog et les maquettes."

**Nathan :** S'engage a appeler Marc d'Astrid pour debloquer l'acces Figma.

> **Nathan :** "Je passe un coup de fil a Marc d'Astrid pour lui dire de donner les acces."

### Spider comme outil de gestion de projet

**Nathan :** Spider doit etre utilise pour gerer ce projet (tracking du temps, des features, etc.). C'est le premier vrai test.

> **Nathan :** "On va mettre le projet la-dessus. Ca va etre le premier test."

**Remy :** Si Spider est utilise pour ce projet, on pourra traquer precisement combien de temps les agents ont mis sur chaque feature et calculer le temps d'execution par feature.

> **Remy :** "Si j'utilise Spider pour ce projet-la, on peut parfaitement traquer combien de temps les agents ont mis sur telle ou telle feature, calculer le temps d'execution des agents pour chaque feature."

**Nathan :** Confirme -- Spider doit devenir l'interface de gestion de projet pour leurs propres projets.

> **Nathan :** "Je pense meme qu'on va faire le projet management sur Spider. C'est une interface pour nous."

**Remy :** Reconnait que la fonctionnalite de gestion de projet dans Spider n'etait pas prioritaire mais qu'elle le devient.

> **Remy :** "Je pense que c'est un truc qui n'etait pas vraiment prioritaire, mais je pense qu'il faut qu'on le fasse au final."

---

## 8. Hebergement et infrastructure (Kubernetes, separation des donnees)

### Separation des donnees client

Discussion sur la strategie d'hebergement : tout sur l'infrastructure Spider, ou possibilite d'heberger chez le client ?

**Remy :** Techniquement, les deux sont faisables. Certains clients auront des enjeux de mettre ca sur leur propre serveur.

> **Remy :** "Nous, soit on met tout sur un cluster, soit -- c'est ce que nous disent certains -- il y aura surement des clients qui auront vraiment des gros enjeux de mettre ca sur leur serveur."

**Nathan :** Pense que ca ne sera pas le cas pour leur cible. Le modele Spider est different d'un outil data/analyse : Spider voit tout, mais le client ne voit que ce qu'il a paye.

> **Nathan :** "C'est ce que Jean se disait : tu as acces a toute la data, il faut que le client puisse faire parler sa data. Et donc la, c'est hyper touchy parce que tu as des risques de qui voit quoi dans la boite. Nous, on fait une retention d'infos. Spider, on voit tout, mais le client ne voit que ce qu'il a paye pour."

### Kubernetes

**Nathan :** Inquiet sur la fiabilite de l'hebergement (crashes, scalabilite).

**Remy :** Rassure Nathan -- Kubernetes est fait exactement pour ca. Utilise par toutes les grosses boites. Auto-scaling : quand un cluster atteint X% de RAM, un autre se deploie automatiquement.

> **Remy :** "On n'aura qu'a se debrouiller avec Kubernetes. Kubernetes, c'est justement fait pour ca et c'est utilise par toutes les grosses boites. Des que tu atteins tel pourcentage de RAM sur ton cluster, tu en deploies un autre."

**Remy :** Le seul vrai risque serait un pic enorme et soudain sans temps de reaction, mais c'est un risque universel, meme sur le cloud.

### Architecture pensee pour la portabilite

**Remy :** La cle, c'est de penser l'architecture des le depart pour la portabilite. Si la donnee de chaque client est bien separee (pas tout dans une seule base), la migration est simple.

> **Remy :** "Si ton systeme est pense pour que tu mettes toute la donnee dans une seule base de donnees pour toutes les boites, tu auras un enfer a migrer. Donc tout est bien separe pour permettre la portabilite."

**Nathan :** Preoccupe par les crashes et la fiabilite, vu que toute la boite sera sur Spider.

> **Nathan :** "Toute la boite va etre la-dessus. Comment on fait pour ne pas avoir de problemes ?"

---

## 9. Couts Claude Code Max

**Nathan :** A un abonnement Claude Code Max. A mi-fevrier, il a deja depense 150$ de credit en usage supplementaire, en plus de l'abonnement de base. Cela doit etre prevu dans les budgets Spider.

> **Nathan :** "La thune que je mets moi, la j'ai l'abonnement Claude Code Max. On est a la moitie du mois, j'ai deja depense je crois 150 dollars de credit en extra usage."

**Nathan :** Justifie la consommation par les mega-recherches strategiques (40+ web searches croisees pour l'etude de marche).

> **Nathan :** "J'ai fait des mega recherches, j'ai lance genre 40 web searches que j'ai croisees entre elles sur l'etude de marche."

**Remy :** Utilise un abonnement perso + open source quand il n'a plus de credit. Suggere que ce n'est pas urgent mais que ca peut etre cool d'avoir un abonnement pro.

> **Remy :** "Moi j'ai un truc pro/perso, il y a aussi de temps en temps quand j'ai plus de credit, et puis sinon pas mal de developpement open source. Mais oui, carrement, ca peut etre cool."

---

## 10. Visites mensuelles de Remy a Nantes

**Nathan :** Remy doit venir a Nantes une fois par mois (billets d'avion pris en charge). Necessite de creer du lien et d'avancer sur des sujets qu'on ne traite pas en visio.

> **Nathan :** "Il va falloir que tu viennes, je pense, une fois par mois. Il faut qu'on cree du lien, il faut qu'on avance, et mine de rien, il y a plein de trucs que tu ne fais pas en visio."

---

## Citations cles supplementaires

**Sur la vision long terme de Spider :**
> **Nathan :** "Ce que je voudrais demain, c'est que Spider auto-detecte les chantiers ou on pourrait creer des outils. Et que de lui-meme, il dise : 'Voila, je pense que ca prend 15 jours.' Et donc, nous, on sait a peu pres combien il faut le facturer."

**Sur la force de frappe Drakkar :**
> **Nathan :** "Ce qui va etre canon, c'est que ces trucs-la, en fait, on aura la force de frappe avec Drakkar pour que -- il va falloir les former, les faire monter -- mais pour qu'eux ils le fassent. Et pour que toi, tu te focuses sur le coeur produit et pas sur ces trucs-la."

**Sur le role de Remy dans Drakkar :**
> **Remy :** "Il faut fonctionner un peu en coups de... Du coup, tu as moins besoin de facturer toi-meme au client. Mais oui, de toute facon, il faudra pouvoir mettre l'outil sur une infra separee de la notre. Et du coup, il y a aussi ca qu'il faudra refacturer -- ce sera peut-etre inclus dans l'abonnement, les couts d'hebergement client."

**Sur les points de story IA :**
> **Remy :** "Ce que j'avais fait, de base je l'avais fini, j'avais plus de points que ca. Mais en fait, je me retrouve a rabaisser les points de certaines features, et ca ne fait pas de sens non plus. Tu ne peux pas mettre 2 a une feature enorme. En fait, il faut adapter l'usage des story points a une appli faite par l'IA."

---

## Decisions prises

| # | Decision | Porteur |
|---|----------|---------|
| 1 | Nathan appelle Marc d'Astrid pour debloquer l'acces Figma pour Remy | Nathan |
| 2 | Remy vient a Nantes une fois par mois (billets d'avion pris en charge) | Nathan + Remy |
| 3 | Le projet Astrid sera le premier test reel de Spider en production | Nathan + Remy |
| 4 | Spider sera utilise comme outil de gestion de projet pour le projet Astrid (tracking temps agent, temps humain, features) | Remy |
| 5 | Prevoir un abonnement Claude Code Max dans les budgets Spider | Nathan |
| 6 | Construire un systeme d'estimation qui traque temps agent et temps supervision humaine pour chaque feature | Remy |

---

## Informations nouvelles pour la strategie Spider

### Chiffres cles
- **Investissement annee 1 :** 400-500K EUR equivalent (100-150K EUR depenses directes + salaire Nathan + temps equipes internes)
- **Cout Claude Code Max :** 150$ d'extra usage a mi-mois (en plus de l'abonnement)
- **Projet Astrid :** ~30K EUR, une dizaine de projets similaires dans le pipeline
- **Jordan :** 1M+ EUR CA, affichage publicitaire, premier POC client potentiel

### Business model emergent
- **Modele :** Abonnement + prestations de creation d'outils automatises
- **Cle de succes :** Etre "hyper bons" a estimer le cout/temps de livraison
- **Vision :** Spider auto-detecte les chantiers d'automatisation chez le client et propose des estimations

### Metriques d'estimation (framework en construction)
- **Deux metriques necessaires :** temps d'execution agent + temps de supervision humaine
- **Tache agent unitaire :** entre 2 et 30 minutes (au-dela = mal scope)
- **Ratio empirique initial Nathan :** 2h humain pour 7h agent (1h dev + 1h designer pour 1 journee agent)
- **Ratio propose :** 30 min agent / 5 min supervision (~1:6), avec blocs de check de 30min-1h tous les 5h agent
- **Point de complexite IA =/= point de complexite humaine** (insight important de Remy)

### Architecture technique
- **Kubernetes** pour l'hebergement (auto-scaling, utilise par les grandes entreprises)
- **Donnees client separees** des le depart (pas de base unique multi-tenant)
- **Hebergement on-premise client** : faisable techniquement mais probablement pas necessaire pour la cible Spider (pas un outil data/analyse)
- **Modele de visibilite :** Spider voit tout, le client ne voit que ce qu'il a paye

### Financement
- **CIR :** Piste a explorer, potentiellement liee au statut de Remy
- **Subventions innovation :** A explorer
- **Dette bancaire :** Option envisagee
- **Statut Remy :** Possibilite d'associe-salarie pour declarer son temps (CIR)

### Organisation
- **Remy :** Doit se concentrer sur le coeur produit, pas sur l'execution des projets clients
- **Drakkar :** Sera la force de frappe pour executer les projets Spider chez les clients (a former et faire monter en competence)
- **Gestion de projet dans Spider :** Devient prioritaire (n'etait pas prevu initialement)
