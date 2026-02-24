# QUESTIONS OUVERTES — A discuter

> 21 fevrier 2026. Les questions qui restent apres la these finale.
> Nathan : reponds directement sous chaque question.

---

PRéambule : je me dis qu'en fait, avec Spider on veut cloner Jena Thierry et moi et Drakkar en général. Thierry expert industriel et managmenent, moi tech et stratégie busienss, Jean finances et gestion fine opérations. + les équipes de drakkar au global (dev, design etc) pour répondre aux 3 options dont je parlais à jordan

## Q1 : Le pricing — indolore a 0.5% du CA ?

L'idee : pas un prix fixe (500€, 1500€), pas un prix au ROI (10% du delta). Un prix au CA : 0.5% du chiffre d'affaires mensuel.

Pourquoi c'est potentiellement brillant :
- **Indolore :** Jordan a 1M de CA → 5 000€/an → 416€/mois. Imperceptible.
- **Scale automatiquement :** Quand Jordan passe a 2M grace a Spider → 833€/mois. Spider capture la valeur qu'il cree sans avoir a la negocier.
- **Aligne les incentives :** Si le CA du client baisse, Spider gagne moins. Spider a INTERET a ce que le client aille bien.
- **Decision instantanee :** "0.5% de votre CA" c'est un calcul mental de 2 secondes. Pas de grille tarifaire a comprendre.
- **Franchit la barriere psychologique :** Le patron ne compare pas "500€/mois vs mon assistante a 2500€." Il compare "0.5% vs rien." Et 0.5% c'est rien.

Les risques :
- Les tout petits clients (200K CA) paient 83€/mois → pas viable pour Spider si le cout de service est 200€+/mois
- Les gros clients (5M+ CA) paient 2 000€+/mois → peut devenir "cher" et le client se met a negocier
- Ca necessite un acces au CA REEL du client (via Pennylane ?) → probleme de confiance / transparence
- Reglementairement, indexer le prix sur le CA c'est classique en franchise mais inhabituel en SaaS

Variante possible : 0.5% du CA avec un PLANCHER (minimum 300€/mois) et un PLAFOND (maximum 3 000€/mois). Ca protege Spider en bas et le client en haut.

Autre variante : pas le CA brut mais la MARGE brute. Plus aligne avec la valeur reelle. Mais plus dur a mesurer et le client resistera a partager sa marge.

**Reponse Nathan : Mais complqiué quandm eme. Pourquoi afficher le CA? pourquoi ne pas le faire en auto-diag ou via un huemaiN?
>

---

## Q2 : L'auto-diagnostic comme porte d'entree ?

L'idee : avant meme de parler a un humain, le prospect connecte ses outils (Pennylane, Gmail) et Spider genere un diagnostic AUTOMATIQUE en 24h. Gratuit ou quasi-gratuit. Le dirigeant voit pour la premiere fois son business tel qu'il est reellement.

Pourquoi c'est puissant :
- **Zero friction humaine :** Pas de call de vente, pas de demo. Juste "connectez-vous, on vous montre."
- **Le "wow moment" avant la vente :** Le patron voit ses 39% d'impayes, sa tresorerie previsionnelle, ses clients a risque — AVANT qu'on lui demande quoi que ce soit.
- **Scalable :** Un pipeline LLM peut generer 50 diagnostics/mois sans intervention humaine.
- **Qualifiant :** Les prospects qui reagissent au diagnostic ("putain, je savais pas ca") sont chauds. Ceux qui ignorent ne sont pas le bon ICP.

Les risques :
- La qualite d'un diagnostic auto sans contexte humain sera mediocre (pas de speech-to-process, pas de comprehension du metier)
- Le patron qui recoit un diagnostic avec des erreurs perd confiance
- Le diagnostic gratuit devalue le travail de Spider ("si c'est gratuit, c'est pas serieux")
- Necessite que le pipeline soit CONSTRUIT (pas un script Python — un vrai produit)

Variante possible : pas gratuit. 99€ ou 199€ pour le diagnostic auto. Assez cheap pour que ce soit impulsif. Assez cher pour qualifier les serieux.

Autre variante : le diagnostic est gratuit mais INCOMPLET. "Voici 3 indicateurs sur 10. Pour les 7 autres, on prend rendez-vous." Teaser model.

**Reponse Nathan : Pourquoi aps, ou alors vrai humain mais on vois en fonction?
>

---

## Q3 : Comment Spider gere la QUALITE quand il fait tout ?

Si Spider gere relances + compta + marketing + planification — et qu'un agent se trompe (relance le mauvais client, facture un mauvais montant, envoie un mail marketing avec une erreur), le dommage est OPERATIONNEL et IMMEDIAT. Pas un bug dans un dashboard. Un bug dans la vraie vie du business.

Questions concretes :
- Est-ce que chaque action de l'agent passe par une VALIDATION humaine (le dirigeant ou son assistante approuve avant envoi) ?
- Ou est-ce que l'agent agit de facon autonome avec un "droit a l'erreur" ?
- Quel est le seuil ? (Peut-etre : relances < 500€ = autonome, relances > 500€ = validation humaine ?)
- Comment on gere l'escalade ? (L'agent detecte qu'il n'est pas sur → il alerte un humain Spider)

L'insight UiPath (Dines) : il faut du DETERMINISTE (regles strictes, zero erreur) pour les taches critiques (facturation, compta, juridique) + de l'AGENTIQUE (adaptatif, LLM) pour les taches tolerantes a l'erreur (marketing, relances simples, reporting).

**Reponse Nathan : En fait phase de brouillon ou pas d'action d'envoi, au bout un moment le dirigeant peut prendre la resp. mais du ocup pricing par action? VIte usine à gaz... après il faut peut etre s'inspirer de lcaude ou lovable : abo qui couvre un nombre d'aciton et possiblité d'abonnement.
>

---

## Q4 : Est-ce que ca marche dans TOUS les verticaux physiques ?

Jordan = services (pub exterieure). Les modules (relances, CRM, marketing, compta) s'appliquent naturellement.

Pour un artisan plombier (3 personnes) :
- Devis automatiques ? (oui, gros potentiel)
- Planification interventions ? (oui, enorme gain de temps)
- Relances impayes ? (oui, universel)
- Marketing ? (peut-etre — mais un plombier fait du bouche-a-oreille, pas du email marketing)
- ARPU potentiel : 300-800€/mois ? Plus bas que Jordan.

Pour un industriel (50 personnes) :
- Supply chain / achats ? (oui, enorme complexite)
- Suivi de production ? (oui, mais necessite des capteurs / IoT)
- RH / planning equipes ? (oui)
- Qualite / conformite ? (oui, reglementaire)
- ARPU potentiel : 3 000-10 000€/mois. Mais deploiement en 14 jours ? Probablement pas — plutot 2-3 mois.

Question : est-ce que Spider doit cibler un ARPU (et donc un type de client) ou etre flexible ?

**Reponse Nathan : Flexible je pense, l'IA fais qu'on peut êrtre large.
>

---

## Q5 : Drakkar comme client #0 (dogfooding) ?

Nathan dit au CODIR : "Jean veut un plan de charge. Thierry veut un suivi staffing."

Si Spider automatise Drakkar d'abord :
- Dogfooding (on utilise notre propre produit)
- Preuve tangible ("voici ce qu'on utilise, le staffing est passe de 55% a 80%")
- Acces total aux donnees (pas de negociation avec un client externe)
- Ca RESOUT le probleme Drakkar (qui saigne) avec l'outil Spider

Le risque : ca retarde le vrai test marche (vendre a un inconnu).

**Reponse Nathan : On fais les 2 en aprallèle.
>

---

## Q6 : Le canal comptable — allie ou concurrent ?

Si Spider fait relances + tresorerie + facturation, on est DANS le domaine de l'expert-comptable.

Le comptable peut voir Spider comme :
- Un ALLIE : "Spider m'envoie des donnees plus propres, je passe moins de temps a corriger les erreurs de mes clients, mes clients sont plus satisfaits"
- Un CONCURRENT : "Spider fait le travail que je facture 300€/mois a mon client"

Comment positionner Spider pour que le comptable soit un allie ?
- Spider ne fait PAS la compta (ca reste chez Pennylane / le comptable)
- Spider fait l'OPERATIONNEL (relances, planification, marketing) que le comptable ne fait PAS
- Spider AMELIORE la donnee que le comptable recoit (moins d'erreurs, plus de structure)
- Le comptable touche une COMMISSION sur chaque client Spider qu'il recommande (20-30% du setup ?)

**Reponse Nathan : Exactement : pas la compta, gère l'opréationnel que le compta ne fait pas et améliore la data. Par contre non, pas de com o uautre pour le comptable.
>

---

## Q7 : Le modele fonds — est-ce que c'est le VRAI endgame ?

Tu as dit : "C'est MOI qui cree un fonds et qui rachete les boites."

Si l'endgame c'est Nathan = investisseur qui utilise Spider comme avantage informationnel pour racheter des PME et les transformer :

- Spider n'est PAS un produit a vendre a 500 clients. Spider est un OUTIL INTERNE d'un fonds d'investissement.
- Le "revenu" n'est pas du MRR. C'est des DIVIDENDES et PLUS-VALUES sur les PME rachetees.
- Le modele c'est Berkshire Hathaway (Buffett utilise sa comprehension des businesses pour les acheter) croises avec un AI roll-up a la Gil (racheter, transformer avec l'IA, multiplier la marge).
- Nathan rachete une boulangerie a 3x EBITDA (300K€). Spider la transforme en 14 jours. La marge double. Nathan la revend a 6x le nouvel EBITDA (600K€ → 1.2M€). Plus-value : 900K€.
- × 10 PME/an = 9M€ de plus-value annuelle.

Questions :
- C'est un metier COMPLETEMENT different de fondateur tech. Capital, competences financieres, relation banques. Est-ce que ca te parle ?
- Est-ce qu'on construit Spider comme PRODUIT VENDABLE (option plateforme M&A) ou comme OUTIL INTERNE (option fonds) ? Les deux sont possibles mais les choix d'architecture et de GTM different.
- Timeline : c'est a 5 ans minimum. Comment finance-t-on les 5 ans entre maintenant et le fonds ?
- Est-ce que les deux chemins (plateforme d'abord, fonds ensuite) sont compatibles ? Ou est-ce que choisir l'un tue l'autre ?

**Reponse Nathan : Pour moi la vue c'est outil pour les fonds mais on excluera pas de le faire nous meme en mode service as sa software. Ou meme les deux ene prallèle, on verra.
>

---

## Q8 : Le "speech-to-process" — c'est quoi exactement et c'est reproductible ?

Tu as fait tourner un assistant IA pendant l'appel Jordan qui mappe les process en Figma en temps reel. C'est fait avec quoi ? Claude Code + MCP Figma ? Un outil custom ? C'est reproductible par Thierry / Christian / un FDE ?

Parce que si c'est reproductible, c'est le DIFFERENCIATEUR numero 1 de Spider face a tout le monde. Personne d'autre ne fait de la cartographie de process en temps reel pendant une conversation.

Et si c'est pas reproductible (c'etait un one-shot bricolé), il faut le savoir pour pas construire une strategie dessus.

**Reponse Nathan : Bah phase 1, fais autoamtuquement toute la proposition juste sur base d'un échane comme celui avec spider. Et phase 2 meme le cliet tout suel en guidé. Et oui, playbook de questions et fais avec claude code + mcp branché à spider.
>

---

## Q9 : Combien de mois de tresorerie reste-t-il EXACTEMENT ?

Toute la strategie depend de ce chiffre.

Si 8 mois+ : on peut construire en mode "cafard" (consulting + deploiement un par un).
Si 4-6 mois : urgence cash, il faut vendre des diagnostics / du consulting IA DES maintenant en parallele du proto Jordan.
Si < 4 mois : mode survie, Spider en pause, stabiliser Drakkar d'abord.

Jean pousse pour modeliser ce chiffre au CODIR. Personne n'a le chiffre exact. C'est la question qui determine TOUT.

**Reponse Nathan : 5-6mois
>

---

## Q10 : Le cout reel des credits IA par client par mois ?

Quand Spider fait TOUT le back-office d'un client (relances + CRM + marketing + compta + planning + reporting), combien ca coute en tokens LLM par mois ?

Estimation grossiere :
- Analyse quotidienne des emails (50 emails/jour × 30 jours × ~0.01€/email) = ~15€/mois
- Generation de relances (20 relances/mois × ~0.05€/relance) = ~1€/mois
- Analyse facturation mensuelle (100 factures × ~0.02€) = ~2€/mois
- Reporting hebdo (4 rapports × ~0.50€) = ~2€/mois
- Marketing (10 emails/mois × ~0.10€) = ~1€/mois
- Agent conversationnel (20 interactions/mois × ~0.20€) = ~4€/mois
- **TOTAL ESTIME : ~25-50€/mois par client** (en utilisant Haiku 4.5 pour le gros et Opus pour le critique)

Mais c'est une estimation. Le vrai chiffre depend enormement du volume de donnees du client et de la frequence d'intervention des agents.

Si le cout reel est 25-50€/mois : un pricing a 500€/mois donne 90%+ de marge brute sur les credits IA. Excellent.
Si le cout reel est 200-500€/mois (comme Nathan le suggere) : un pricing a 500€/mois est a marge zero ou negative. Catastrophique.

Remy pourrait poser un calculator de cout par tache par client. C'est prioritaire avant de fixer un prix.

**Reponse Nathan : Peutetre oui... JE sais juste pas comment rendre ça clair. Mais peutetre ok que opaque... idk
>

---

## Q11 : Est-ce que Nathan veut etre fondateur de STARTUP ou fondateur d'EMPIRE ?

C'est pas la meme chose.

**Fondateur de startup :** Lever des fonds. Croitre vite. 500 clients en 3 ans. Viser le milliard de valo. Exit en 5-7 ans. Le modele YC / a16z.

**Fondateur d'empire :** Pas de levee (ou tres peu). Croitre lentement. 50-100 clients en 5 ans. Cash-flow positive des mois 6. Puis utiliser le cash-flow pour racheter des PME (le fonds). Pas d'exit — l'empire croit indefiniment. Le modele Buffett / Arnault / Bolloré.

Les deux sont legitimes. Mais les decisions tactiques sont OPPOSEES :
- Startup → lever, bruler du cash, croitre vite, accepter les pertes
- Empire → autofinancer, etre rentable, croitre lentement, accumuler du capital

Nathan dit "c'est soit rien soit le milliard." C'est un discours de fondateur de startup. Mais la vision "je rachete les boites moi-meme" c'est un discours de fondateur d'empire. Les deux ne vont pas ensemble.

**Reponse Nathan : Je veux etre dieux, je veux créer un novueau jeux. Donc je pense jouer aux deux à la fois.
>

---

*21 fevrier 2026. 11 questions. Les reponses determinent la strategie.*
