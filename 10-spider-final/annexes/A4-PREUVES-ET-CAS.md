# A4 — PREUVES ET CAS : Annexe Complete

> **Document de reference interne — Spider Strategy**
> **Date de redaction :** 21 fevrier 2026
> **Sources :** 12 fichiers primaires (transcripts bruts, cas nettoyes, CODIR, echanges, theses, questions)
> **Objectif :** Centraliser TOUT ce qu'on sait — chiffres, verbatims, preuves, limites — pour que le mega livrable soit honnete.
> **Fiabilite :** Haute sur les donnees operationnelles (chiffres reels, transcripts). Moyenne sur les chiffres financiers Drakkar (estimations en cours de modelisation par Jean). Basse sur les projections Spider (aucun client paye encore).

---

## 1. LES 10 THESES DE NATHAN — Statuts au 21 fevrier 2026

Les 10 theses sont extraites du manifeste fondateur (`01-these-nathan.md`). Chaque these est resumee et son statut evalue a partir de l'ensemble du corpus.

---

### These 1 — Le tacite est le dernier tresor

**Resume :** Le savoir non-codifiable des PME/ETI europeennes (relationnel, savoir-faire, sur-mesure) est le seul actif non-reproductible qu'elles possedent. Il disparait avec chaque depart en retraite, chaque transmission ratee. C'est la matiere premiere de Spider.

**Statut : CONFIRMEE — mais le timing de la capture est plus tard que prevu**

**Preuves :**
- Decotec : Christophe (normes/reglementaire) part fin 2025 avec toute la connaissance normative. Frederic (peinture) part dans 18 mois. Aucune fiche process. Aucun tutorat. La PME investit 1,3M EUR dans une plaqueuse mais pas 30K EUR dans la captation du savoir. Nathan dans l'analyse post-mortem : "Le paradoxe : ils investissent en machines mais pas en methodes."
- Decotec : "Dans 10 ans, 50% des effectifs seront partis a la retraite" — ecrit sur les tableaux blancs de l'atelier du 9 fevrier.
- Jordan : Les 44-45 "points de data" qu'il liste correspondent aux regles non-ecrites qu'aucun outil ne capture (tarifs negocies par reseau, regles de priorite entre Medialine et Cityz, exceptions par client).

**Nuance importante :** Chez Jordan, ce que Spider capture en Phase 0 est majoritairement de la **donnee structuree** (726 lignes CSV, commissions, montants). Le vrai tacite (les regles implicites) emerge du fonctionnement quotidien sur 3-12 mois, pas le jour 1. Nathan reconnait dans QUESTIONS-NATHAN : "la vraie question c'est comment on reprocess d'autres choses que process initial pour faire parler la data dans un contexte pertinent."

---

### These 2 — La vente B2B est un mensonge que tout le monde entretient

**Resume :** Les appels d'offres et criteres de selection sont du theatre. La decision est prise avant que le process commence, sur la base de la confiance visceralle entre personnes. Le commercial garde le vrai savoir dans sa tete, le CRM ne capturant que le theatre.

**Statut : CONFIRMEE — prouvee par perte directe (Twoghether)**

**Preuves :**
- Twoghether : Drakkar avait un meilleur diagnostic technique (ratio d'inefficience 6.4x documente, 0% de couverture de tests, audit PDF complet). The Tribe a gagne. Maxime : "C'est vraiment une histoire de feeling notamment de la part d'Angelique qui va financer ca." Puis : "On avait la capacite suite a un point avec The Tribe de se projeter vraiment." La decision etait emotionnelle, pas rationnelle.
- Twoghether / Benoit Vasseur : "Angelique nous a dit que tu avais ete tres smart dans l'approche" — les qualites de Nathan ont ete reconnues APRES la perte. La competence etait visible mais n'a pas suffi.
- Jordan : "On se connait bien et c'est pour ca que je te fais confiance." La relation d'amitie est le vrai catalyseur du deal — pas le pitch Spider.

**Nuance :** La these s'applique surtout aux deals > 10K EUR. Pour des abonnements a 500 EUR/mois, la friction de confiance est plus basse. Le risque inverse : l'amitie avec Jordan cree un biais de confirmation — Jordan ne dira peut-etre pas "ca ne marche pas" aussi vite qu'un inconnu.

---

### These 3 — Les US nous ont impose leurs regles

**Resume :** Toute la stack B2B (Salesforce, HubSpot, Notion, Monday) est concue pour la mentalite transactionnelle americaine. Elle ne capture pas le relationnel europeen. Spider serait le premier outil concu POUR la mentalite europeenne.

**Statut : CONFIRMEE comme diagnostic, NON-TESTEE comme avantage concurrentiel**

**Preuves du diagnostic :**
- Jordan utilise UaG (logiciel francais de niche, ~20 clients en France), Notion (americain mais utilise a l'europeenne comme un ERP), Google Sheets (concu comme outil de calcul, torde en outil de gestion). Aucun CRM. "Mon boulot c'est une usine a gaz."
- Decotec : ERP Odoo en cours de migration, lots production 4-5-6 jamais faits, CRM quasi-inexploite, donnees produit "completement eclatees". La compta analytique par gamme — montee par l'ancien DAF — a ete perdue avec son depart. Exactement ce que T3 predit : les outils existent, le tacite ne se transfpre pas.
- Nathan dans CODIR 1 : "J'aime pas Odoo, je trouve que c'est pas un tres bon outil. C'est un tres bon outil comptable. Mais a part ca j'y trouve pas grand chose."

**Ce qui n'est pas teste :** Est-ce que les PME percevront Spider comme "concu pour elles" ou comme "encore un outil etranger" ? La these suppose que la mentalite europeenne est un avantage concurrentiel. Ce n'est pas prouve avant les premiers retours clients reels.

---

### These 4 — Ils veulent la couronne, pas le fardeau

**Resume :** Les dirigeants PME (familiaux, repreneurs corporate, heritiers) veulent le titre sans la gouvernance. Ils diagnostiquent correctement mais refusent d'agir. Le tacite meurt parce que personne ne paie le prix de le sauver.

**Statut : CONFIRMEE — cas fondateur Decotec, nuancee par Jordan**

**Preuves :**
- Decotec / Laurent de Bray : Parfaitement lucide sur la crise RH ("la boite les a uses"), la probleme commercial (4 commerciaux sous le seuil de rentabilite), la faille de gouvernance (refuse le titre de directrice a Isabelle). Entre le diagnostic et l'action : un gouffre. Nathan : "Laurent est un excellent diagnosticien et un mauvais decideur. Ou plus exactement : il decide de ne pas decider." Mail de rupture 3 jours apres l'atelier le plus reussi.
- Decotec : Le precedent symbolique ultime — 80 prospects donnes a Eric (directeur commercial), 2-3 devenus clients. Laurent le sait. Aucune consequence.
- Nathan dans la these : "Spider vend ce qu'ils veulent. Livre ce dont ils ont besoin. Vend : tranquillite, zero effort, rien ne change. Livre : restructuration, capture, dependance."

**Nuance Jordan :** Jordan est le contre-exemple partiel. Il dit explicitement : "En fait, je pense que je n'arrive pas a developper la boite. C'est que je suis bloque dans mon espece de plafond de verre qui est de gestion [...] je perds enormement de temps a tout faire." Il VEUT changer. Mais Jordan est un ami proche de Nathan, jeune (entrepreneur actif), et dans un secteur de croissance. Ce n'est pas le profil T4 typique (dirigeant familial de 50 ans).

---

### These 5 — Le ratio est catastrophique

**Resume :** Tous les outils existants (CRM, ERP, consultants) exigent un aveu public de faiblesse que le dirigeant refusera toujours. Spider inverse le ratio : zero effort, zero aveu, benefice immediat.

**Statut : CONFIRMEE comme diagnostic, NON-TESTEE comme proposition commerciale**

**Preuves du diagnostic :**
- Decotec : 3 ans de consulting Drakkar. Rapports de qualite. SWOT precis. Chiffrage a 10M EUR de potentiel. Rupture 3 jours apres l'atelier. Le probleme n'etait pas la competence de Drakkar — c'etait que Laurent ne pouvait pas implementer sans "admettre" sa fragilite a ses equipes.
- Nathan dans CODIR 2 : "Ce qu'on vend c'est degueulasse. On est juste des implementeurs comme les autres. Il n'y a zero difference parce qu'on est incapable d'assumer une difference."
- Jordan : "Je ne peux pas envoyer des trucs a 50 000 balles en calculant tout a la mano. C'est un encreux de process." La douleur est la. L'acceptation de l'aide aussi. Mais Jordan n'est pas T4.

**Ce qui n'est pas teste :** La proposition "Spider capture pendant qu'ils dorment" n'a ete testee sur aucun client reel. Le pitch "zero effort" peut lui-meme creer de la mefiance : "si c'est si facile, pourquoi ca coute 500 EUR/mois ?"

---

### These 6 — L'IA rend possible ce qui etait un reve

**Resume :** L'IA generative peut desormais capturer le tacite depuis des emails, calls, conversatins — techniquement impossible avant 2023. Les Americains ne le feront pas car ils ne voient pas le probleme europeen.

**Statut : PARTIELLEMENT CONFIRMEE — capacite prouvee, gap americain speculatif**

**Preuves de la capacite :**
- Speech-to-process : Nathan a fait tourner un assistant IA pendant l'appel Jordan qui a mappe les process en Figma en temps reel. "J'ai coupe un moment. J'ai un assistant et j'en ai relance un autre juste pour qu'il fasse les process et il a processe sur Figma son business en cours de call." (CODIR 1, verbatim)
- Estimation des campagnes Jordan en 2h30 : "Note de cadrage strategique pour determiner les enjeux et ROI potentiel + prototype visuel + offre commerciale" — depuis les exports bruts de Notion et Sheets. (QUESTIONS-NATHAN, reponse Nathan)
- Remy dans l'echange du 20 fevrier : confirmation que Spider peut traquer "combien de temps les agents ont mis sur telle ou telle feature" et generer des estimations de cout par tache.

**Nuance :** Nathan reconnait dans QUESTIONS-NATHAN : "Le moat c'est vraiment notre capacite a recreer les process a partir de data brut [...] Puis derriere capturer le tacit." Mais il ajoute : "Bcp plus peur qu'un autre acteur fasse mieux que nous et que pas un vrai moat." La concurrence IA est ouverte, pas fermee.

---

### These 7 — Triple convergence, 24 mois

**Resume :** Crise economique (PME doivent prospecter pour la premiere fois depuis 2008) + vague de transmission (700 000 entreprises, departs retraite massifs) + IA mature = fenetre unique 2026-2028.

**Statut : CONFIRMEE comme analyse, NON-TESTEE comme urgence marche**

**Preuves :**
- Decotec : CA passe de 30M a 22M EUR en 3 ans (-27%). Departs retraite : 10-12 par an pendant 4 ans = 40-48 personnes. Age moyen 50 ans. Confirme la vague de transmission et la crise simultanement.
- Nathan dans CODIR 1 : "L'Europe est en train de mourir." Thierry : "Les boites sont prises a la gorge [...] les mecs aujourd'hui, ils veulent bien te suivre sur n'importe quoi."
- Benoit Vasseur (The Tribe, 70+ personnes) : "Les gens sont paumes et n'investissent plus. A quoi bon investir si c'est perime dans 2 ans." — Signal de l'attentisme, pas de l'urgence.

**Nuance critique :** Benoit situe l'impact IA "dans 2 ans". Nathan pense que c'est plus tot. Si Benoit (qui gere 70 personnes dans la tech) ne voit pas l'urgence, les dirigeants PME sont encore plus loin. Nathan reconnait : "je vis dans une microbulle YC [...] encore enorme inertie sur les boites francaises."

---

### These 8 — Le code est mort, le service est le produit

**Resume :** Le paradigme bascule du SaaS (tu achetes un outil, tu fais le travail) au Service as Software (tu achetes un resultat, le logiciel fait le travail). Le moat n'est pas le code — c'est la data capturee. Palantir l'a prouve.

**Statut : CONFIRMEE comme vision, NON-TESTEE comme business model**

**Preuves :**
- Nathan dans CODIR 2 : "Mainteant, avec un call, tu peux arriver avec la solution, et tu n'as qu'a la vendre, la pricer tout de suite, et dire est-ce que tu veux ca, et les gens appuient sur le bouton, pour 20 000-30 000 euros."
- Cas Twoghether perdu : La perte a confirme que le marche agence (dev sur-mesure) "est completement disrupte par l'IA." Nathan a dit a Benoit : "Au final on serait arrive sur un pricing similaire, mais [...] avec la vitesse a laquelle l'IA compresse les couts de delivery, je me demande combien de temps [ca tient]."
- Jordan sur le cout du dev : Nathan lui presente les 3 options (ERP = 10K+, dev sur-mesure = 50K min, no-code = 15-20K). "En fait, en reflechissant pas mal a tout ca [...] je me dis mais en fait, la, en fait, le cas que tu as [...] En fait, ce n'est pas tres loin des cas de visage que je suis en train de developper sur la startup."

**Ce qui n'est pas prouve :** Le prix que le marche accepte. 990 EUR/mois ? 500 EUR/mois ? Prix au CA (0.5%) ? Nathan dans QUESTIONS-OUVERTES : "Aucune idee, je pense qu'il faut adapter au cas mais en meme temps c'est chiant et pas scalable."

---

### These 9 — Le Shogunat Digital

**Resume :** Spider prend le pouvoir operationnel reel (capture, analyse, suggestions) pendant que le dirigeant garde le titre. Restructuration invisible. Le dirigeant croit decider — il signe ce qu'on lui prepare.

**Statut : CROYANCE DE NATHAN — non testee empiriquement**

**Position de Nathan dans QUESTIONS-NATHAN :** "Oui, j'y crois vraiment. Je pense que tellement puissant qu'ils seront trop content et finiront pas supprimer leur cerveau et nous laisser gerer, tout est une question de puissance. Mais je me trompe peut-etre. Et effectivement, progressif, pas tout de suite."

**Le paradoxe non resolu (identifie dans QUESTIONS-NATHAN) :**
Le Diagnostic Eclair (qui MONTRE les problemes pour vendre) cree de la transparence. Le Shogunat (Spider resout silencieusement) cree de l'opacite. Les deux sont necessaires a des moments differents. Si le dirigeant ne veut pas que son enterprise soit "vue" par un systeme — si le bordel est une FEATURE pour lui — alors le diagnostic cree de la menace, pas de la valeur.

**Nuance Decotec :** Laurent ne voulait pas que quelqu'un SACHE. Savoir oblige a agir. Il a fui le consulting Drakkar precisement parce que le diagnostic le confrontait a ses propres blocages. Le Shogunat suppose que le dirigeant accepte que quelqu'un d'autre prenne les decisions. Mais si la prise de decision elle-meme est ce qu'il protege (son pouvoir, son titre), Spider est une menace, pas un soulagement.

---

### These 10 — Toile, Data, Mycelium, Pouvoir

**Resume :** En 3 phases — Toile (capturer le tacite de 1000 PME, creer le switching cost), Mycelium (intelligence inter-entreprises, le reseau rend chacun plus fort), Pouvoir (creer de nouvelles metriques de valorisation M&A type "Spider Score" qui redefinissent le reel) — Spider devient le monopole definitif.

**Statut : VISION DE LONG TERME — irrelevante pour l'execution 2026**

**Position de Nathan dans QUESTIONS-NATHAN :** "On s'en fout, c'est un doc interne. Je veux la vision complete." Sur le Mycelium / Phase 3 / M&A : "Dans 5 ans, pas 18 mois." Sur l'endgame fonds : "Pour moi la vue c'est outil pour les fonds mais on excluera pas de le faire nous-memes en mode service as software. Ou meme les deux en parallele, on verra."

**Ce qui est prouve :** Le potentiel M&A interest existe dans le CODIR 1. Nathan : "Dans 5 ans, c'est le plus gros outil de M&A europeen. Parce qu'en fait t'as toute l'adaptation de toutes les boites de tout le monde." Thierry comprend : "Une depossede d'entreprise de fonds d'intelligence native."

**Ce qui n'est pas prouve :** Rien. Zero client. Zero donnee capturee. Zero reseau. L'horizon est 2030+. Ne pas mentionner publiquement avant 50+ clients.

---

## 2. CAS JORDAN / COMPRIVEE

### Profil

**Jordan Lefranc**, CEO ComPrivee, agence de publicite exterieure basee a Herouville-Saint-Clair (pres de Caen, Normandie). Ami proche de Nathan. Lien : rencontre avant Spider, confiance etablie sur plusieurs annees. Il est aussi sur le point de lancer **Verian Advisory**, structure de conseil international en surcouche de ComPrivee — tout systeme construit doit etre duplicable.

**Entite legale :** SARL, capital 10 000 EUR, SIREN 852.110.592.

**Equipe (4-5 personnes) :**

| Personne | Role | Outils principaux |
|----------|------|-------------------|
| Jordan | CEO / Direction commerciale | UaG, Sheets, Notion |
| Eline | Marketing / Digital / CM | Notion, Sheets |
| Audrey | Coordination admin | Sheets, Notion, Pennylane |
| Freelance 1 | Support operationnel (nouveau) | — |
| Freelance 2 | Occasionnel (motion design) | — |

---

### Chiffres cles (2025, donnees reelles Notion export)

| Metrique | Valeur |
|---------|--------|
| CA total | 1 145 304,61 EUR |
| Marge brute | 311 325,71 EUR |
| Taux de marge moyen | 27,2% |
| Lignes campagnes | 726 |
| Clients uniques | 73 |
| Reseaux publicitaires | 32 |
| Imprimeur unique | Publitex (173 commandes) |

**Saisonnalite (pics) :** Septembre (125 campagnes — Foire de Caen, rentree) et Mars (111 — Salon de l'Habitat). Quasi-zero en decembre (11).

**Distribution statuts campagnes :**
- Termine : 655 (90,2%)
- Reporte : 32 (4,4%)
- Annule : 14 (1,9%)
- Pas commence : 13 (1,8%)
- En cours : 12 (1,7%)

**Facturation et paiement — le signal cle :**
- Facturees : 686 (94,5%)
- **Payees : 441 (60,7%) — 285 non payees (39,3%)**
- 39,3% d'impayes est le premier argument ROI concret pour Spider.

**Taux de commission :**
- 13% : 365 lignes (50,3%)
- 15% : 304 lignes (41,9%)
- 20% : 24 lignes (3,3%)

**Frais de gestion (Gestion) :**
- 85 EUR : 250 lignes (campagnes simples)
- 150 EUR : 140 lignes (campagnes complexes)

**Top 5 clients par CA :**

| Client | Campagnes | CA HT (EUR) | Marge (EUR) | Marge % |
|--------|-----------|-------------|-------------|---------|
| CAO Paris | 13 | 79 173 | 17 901 | 22,6% |
| Grin | 24 | 61 122 | 17 129 | 28,0% |
| Caen evenements | 27 | 58 366 | 8 575 | 14,7% |
| Schmidt Mondeville | 36 | 50 156 | 12 594 | 25,1% |
| Game Fest | 9 | 44 937 | 14 180 | 31,6% |

**Clients a marge exceptionnelle :** Leicht (86,5%), Frivole (88,5%), Le Tablier et Medialine (100% — services purs sans achat d'espace). Ces clients valident la these que le shift vers les services geres cree les meilleures marges.

**Top reseaux par depense espace :**

| Reseau | Lignes | EUR Espace |
|--------|--------|-----------|
| Cadres Blancs | 101 | 151 699 |
| JCDecaux | 43 | 119 298 |
| Cityz | 63 | 107 742 |
| Oxialive | 89 | 60 974 |
| Giraudy | 43 | 59 111 |

---

### Le process operationnel : 9 etapes, aucune connexion automatique

**Le probleme fondamental : triple saisie en 3 outils deconnectes.**

| Saisie | Outil | Contenu | Qui |
|--------|-------|---------|-----|
| 1ere | Google Sheets | Plan media complet : dates, reseaux, quantites, tarifs, totaux | Jordan / Audrey / Eline |
| 2eme | Notion | Memes donnees + statuts, livraisons, adresses, suivi (33+ champs) | Jordan / Eline / Audrey |
| 3eme | Pennylane | Donnees de facturation extraites manuellement de Notion | Audrey |

**Les 9 etapes du workflow :**

1. **Brief client** — Email/telephone, pas de formulaire standard
2. **Analyse et recommandation** — Consultation UaG (base de 360 000 faces, 16 000 reseaux), appels aux regies. Dependance aux delais de reponse des reseaux.
3. **Construction du plan media** — 100% manuel sur Google Sheets. Logos inseres un par un. Calculs a la main. "Je calcule tout au telephone. C'est une enormie blague. Je ne peux pas envoyer des trucs a 50 000 balles en calculant tout a la mano." (Jordan, call du 20 fev)
4. **Validation client** — Lien Drive, allers-retours email. Pas de versioning.
5. **Commandes reseaux** — Recontact manuel, verification des dispos (qui peuvent avoir change). "Il se passe 15 jours, tu refais le point avec le client, il te revalide tout, sauf que quand tu repasses commande, il t'en manque 20-30%. Donc tu recommences, tu recherches, tu refais les tarifs, tu refais les negociations." (Jordan, call du 20 fev)
6. **Saisie Notion** — Double saisie ligne par ligne (33+ champs par campagne).
7. **Production creative (D-28)** — Relances manuelles au client pour les visuels. Commandes Publitex. Enregistrements radio.
8. **Lancement et suivi** — Suivi livraisons, photos, rapports assembles manuellement.
9. **Facturation** — Triple saisie : transfert Notion → Pennylane, tout re-saisi manuellement.

**Les 5 outils — aucune connexion entre eux :**

| Outil | Role | Limite cle |
|-------|------|-----------|
| Google Sheets | Construction plan media | Pas de BDD tarifs, zero connexion Notion |
| Notion | Dashboard operationnel (CRM interne) | Sature a 800+ campagnes x 33+ champs, lent sur Mac |
| Pennylane | Facturation et comptabilite | Zero connexion entrante, 100% saisie manuelle |
| UaG Affichage | Donnees marche affichage (base externe) | Pas d'API, installation manuelle via TeamViewer, codes mensuels, pas de cloud |
| Email | Communication clients et reseaux | Pas de centralisation |

**UaG (L'Usine a Gaz) — detail technique :**
- Base de donnees : 360 000 faces publicitaires en France, 16 000 reseaux
- Prix : ~55 EUR/mois. Verrouillage par code mensuel.
- Installation : TeamViewer par le fournisseur a chaque mise a jour
- Export : fichier local uniquement (pas de cloud), ou lien web temporaire
- Usage de Jordan : filtrage par ville + concessionnaire + format → export → selection experte → contact reseau → devis → insertion dans Sheets
- Nathan : "C'est un logiciel en situation de monopole dans une niche que personne n'attaque."
- ~20 clients en France. Jordan estime que les 19 autres concurrents "ne prendront jamais la peine de l'appeler meme si c'etait 4 fois moins cher."

**Les 44-45 points de data identifies par Jordan** (lors du call du 20 fev) = requirements fonctionnels Spider. Jordan devait les envoyer lundi 25 fev apres relecture avec Eline.

---

### Le call du 20 fevrier 2026 — Ce qui s'est dit

**Contexte :** Deuxieme call strategique Nathan-Jordan. ~60 minutes. Nathan depuis Nantes (espace coworking), Jordan depuis ses bureaux.

**Ce que Nathan a diagnostique :**
- "Notion c'est un peu ton ERP. Tout ce qui est point d'entree, sortie de ce systeme, il est douloureux. Tu arrives a un stade ou Notion n'est pas adapte pour ce que tu veux faire."
- Les 3 options classiques (ERP a 10K+, dev sur-mesure a 50K min, no-code a 15-20K) toutes insuffisantes pour le cas Jordan.
- La 4eme voie Spider : "On code 10 a 20 fois plus vite qu'avant. On a cree une infrastructure autour de ca. Tu as le meilleur de tous les mondes."

**Ce qui a ete propose :**
- **0 EUR de dev** — Nathan fait lui-meme. Jordan est beta-testeur / etude de cas.
- **Abonnement Spider** — "On a presque aucun truc a moins de 500 balles par mois. Rien qu'en credits IA, ca consomme." Prix exact a definir pour le call du 27 fev.
- **Module 1 :** Pipeline UAG → Plan media automatique. Remplacement de la triple saisie. Fusion plan media / Notion en un systeme. Connexion Pennylane pour facturation automatique.
- **Module 2 :** Relances automatiques (plans medias quand dispos changent + impayes). Brouillons valides par Jordan.
- **Module 3 (vision) :** "Le client parle, paf ca fait la reco automatique et tu as tout presque en temps reel."

**Vision strategique partagee avec Jordan (2 temps) :**
1. Court terme : Automatiser la chaine interne → passer de 1M a 2-3M CA en cassant les verrous operationnels.
2. Long terme : Retourner le modele → Jordan vend L'OUTIL aux autres agences. "Tu passes de 12 a 15 points ou j'en sais rien. Si tu fais d'un coup 10 fois plus de volume, ok tu perds une partie, mais si tu fais 10 fois plus de volume, tu t'en fous."

**Reaction de Jordan :**
- "Carrément, je suis chaud." → Ouverture totale.
- "Meme si on est amis, tu bosses, ca te prend du temps. On le voit quoi." → Pret a payer au-dela du minimum.
- "Moi, mon idee, de base, quand j'ai ecrit ca il y a 7 ans, c'etait d'aller emmerder les plus gros." → Ambition de scale confirmee.
- Sur le marche de l'affichage : "Les regies font exprès de rendre tout complique. C'est une telle malle financière que [...] tout le monde se gave a mort."

**Analyse du marche de l'affichage par Jordan :**
- Tentatives de disruption passees : AddinType (1,7M CA, objectif 100M, s'est fait "sauter par deux coups" par JCDecaux, maintenant revendeur de leads). Startup belge (1,5-2M leves, un an, echec face aux regies).
- Pattern : "Si tu commences a essayer de casser la gueule aux regies, ca ne marche pas."
- Angle Spider pour Jordan : "Tu peux arranger les regies, tu n'arranges plus les agences de medias." Spider rendrait Jordan allie des regies contre les grosses agences, pas l'inverse.

**Potentiel Kavalin (opportunite croisee) :**
- Kavalin : reseau de 185 cabinets.
- Nathan travaille a entrer chez Kavalin via une agence 360.
- Si Kavalin signe avec Spider, croisement naturel avec Jordan pour l'affichage des 185 cabinets.
- Jordan : "Si c'est un truc comme ca, on va partager le gateau."

---

### Next steps (convenus pendant le call)

| Action | Responsable | Deadline |
|--------|-------------|----------|
| Envoyer les 44-45 points de data (finalises avec Eline) | Jordan | Lundi-mardi 25-26 fev |
| Envoyer export UaG (vue globale Nantes) | Jordan | Fait pendant le call |
| Construire prototype Spider | Nathan | Week-end 22-23 fev |
| Call de demo prototype | Nathan + Jordan | **Vendredi 27 fevrier, 11h** |
| Estimer l'abonnement mensuel | Nathan | Pour le call du 27 |
| Week-end a Pornichet (perso) | Tous | 4-5 avril |

---

### Ce que ca prouve — et ce que ca NE prouve PAS

**Ce que ca prouve :**
- La douleur est reelle (triple saisie, 726 campagnes, calculs manuels pour des plans a 50K EUR).
- Un ami fait confiance a Nathan pour gerer son systeme operationnel.
- Le diagnostic en 2h30 est faisable (note de cadrage + prototype visuel + offre commerciale depuis les exports bruts).
- Les donnees existent et sont structurees (726 lignes CSV avec 35 champs = base de travail solide).
- L'angle impayes (39,3%) est un argument ROI quantifiable et immediat.

**Ce que ca NE prouve PAS :**
- Que Jordan PAIERA. L'offre n'est pas encore signee.
- Que le deuxieme client (un inconnu, pas un ami) dira oui au meme pitch.
- Que le ROI est positif au prix Spider prevu : eliminer la triple saisie = ~3 800 EUR/an d'economie (211h x 18 EUR), Spider a 500 EUR/mois = 6 000 EUR/an. ROI negatif sans inclure la recuperation des impayes.
- Que la stack Spider (vs Nathan + Claude Code) est necessaire pour Phase 0.
- Que l'ontologie affichage publicitaire se transfere au client 2, 3, 4.
- Que Jordan restera client au-dela du premier mois.

---

## 3. CAS DECOTEC — Le cas fondateur de la these

### Profil

Decotec / Decotheque : PME industrielle de **155 salaries** fabricant des meubles de salle de bain haut de gamme dans la Sarthe. Labels EPV (Entreprise du Patrimoine Vivant) et French Fab. Cycle de livraison de 9 jours (avantage concurrentiel rare). 5 ateliers end-to-end (menuiserie, peinture, composite, assemblage, serrurerie/metallerie).

**Dirigeants :**
- **Laurent de Bray** (DG/Proprietaire) : Confond controle et pilotage. "Decide de ne pas decider."
- **Isabelle de Bray** (Direction marketing/com/RH) : La plus lucide. Pas de titre de directrice (Laurent refuse). Sous-exploitee.
- **Eric Boutry** (Directeur commercial) : "Cultivateur, pas defricheur." Premiere declaration en atelier : "J'ai garde mes clients."

---

### Chiffres cles

| Metrique | Valeur |
|---------|--------|
| CA 2025 | ~22M EUR |
| CA historique (2022) | ~30M EUR |
| Attrition CA (3 ans) | -8M EUR (-27%) |
| Effectif total | 155 salaries |
| Effectif production | ~140 |
| Arrets maladie permanents | ~10 |
| Mi-temps therapeutiques | ~10 |
| Base de travail effective | **~90 sur 140** |
| Departs retraite | 10-12/an pendant 4 ans (2025-2029) = **40-48 personnes** |
| Age moyen | 50 ans |
| Taux horaire facture | 64 EUR/h |
| Taux horaire reel | 70 EUR/h |
| **Perte par heure** | **-6 EUR** |

---

### Le probleme du tacite : 40+ departs retraite

C'est le cas d'ecole de la These 1 appliquee a l'extreme.

**La bombe a retardement RH :**
- Christophe (normes/reglementaire) : parti fin 2025 avec TOUTE la connaissance normative. Ne transmet pas. Pas de fiches process, pas de procedures ecrites.
- Frederic (peinture) : part dans 18 mois. "Energique mais incapable de structurer/formaliser."
- Flux continu de departs dans les ateliers composite, poncage, assemblage.
- Pas de responsable methodes industrielles. Pas de processus de capitalisation.
- Note ecrite au tableau blanc de l'atelier : **"10 ans → 50% effectifs a la retraite → Captation savoir"**

**Le paradoxe de l'investissement :**
- Investissement plaqueuse : 1,3M EUR
- Investissement cobots et robots : significatif
- Investissement captation du savoir : 0 EUR
- Nathan : "Ils investissent 1,3M EUR dans une plaqueuse mais pas 30K EUR dans une demarche de captation du savoir."

**Pourquoi le savoir n'a pas ete transmis (analyse 5 pourquoi) :**
1. Parce que Christophe et Frederic partent sans avoir transmis.
2. Parce qu'aucun processus de capitalisation n'existe.
3. Parce qu'il n'y a ni responsable methodes, ni DAF pour chiffrer le cout.
4. Parce que Laurent concentre toutes les decisions sans deleguer.
5. Parce que la gouvernance est celle d'une PME patrimoniale ou le dirigeant confond controle et pilotage.

**Cause racine (verbatim Nathan) : "Le goulot d'etranglement de Decotec n'est pas la menuiserie. C'est Laurent."**

---

### Ce qui s'est passe — chronologie

| Date | Evenement |
|------|-----------|
| 2022 | CA ~30M EUR (point haut) |
| 2023-2025 | Erosion du CA (-27%), hausse des prix, perte de volume |
| Nov 2025 | Lancement gamme Levento |
| Fin 2025 | Depart retraite Christophe (normes/reglementaire) |
| 2025 | Depart Olivier Decaux (directeur de site, conflit) |
| 04 fev 2026 | Reunion de preparation Thierry-Isabelle |
| 09 fev 2026 | Journee strategique SWOT + Vision (atelier de qualite) |
| **12 fev 2026** | **Mail de rupture Isabelle → Thierry (3 jours apres l'atelier)** |

**Le mail de rupture (12 fevrier) :** Decotec veut evaluer d'autres integrateurs pour les lots Odoo production. Motif : besoin d'un "pool d'experts indus-prod" et d'un "chef de projet experimente en production."

**La vraie lecture du mail :** Decotec cherche un prestataire qui FASSE le travail de transformation a sa place. "Ils veulent un integrateur qui comprenne leur production (= qui leur dise comment l'organiser), qui ait un pool d'experts (= qui porte la reflexion strategique a leur place), qui ait un chef de projet experimente (= qui manage le changement chez eux)." Autrement dit : externaliser le pilotage de leur propre coeur de metier.

**Question centrale : "Qui est le directeur de la transformation chez Decotec ?" Reponse : personne.**

---

### Pourquoi c'est le cas fondateur de la these Spider

**Ce que Decotec detruit comme hypothese :**
- Nathan croyait que les PME voulaient croitre et avaient besoin d'aide. Decotec a prouve que le dirigeant PME ne veut pas croitre — il veut maintenir le statu quo.
- Trois ans de consulting Drakkar. Rapports de qualite. SWOT precis. Chiffrage coherent. Rupture 3 jours apres le meilleur atelier. Le consulting seul ne change rien.

**Ce que Decotec CONFIRME pour Spider :**
- T4 (ils veulent la couronne, pas le fardeau) : confirme a 100%.
- T5 (le ratio est catastrophique) : confirme. Le consulting exige l'aveu. Laurent ne l'a jamais fait.
- T9 (le Shogunat) : confirme comme besoin. Decotec veut quelqu'un qui DECIDE A SA PLACE sans qu'il ait a admettre qu'il ne peut pas decider.
- Spider doit fonctionner MALGRE la gouvernance dysfonctionnelle, pas APRES sa reforme.

**Verbatim Nathan sur l'implication Spider :** "Le produit doit travailler MALGRE une gouvernance dysfonctionnelle, pas necessiter une reforme de gouvernance comme prealable."

---

### Limites du cas

- Decotec est un cas industriel lourd (155 personnes, 5 ateliers, production physique). Jordan est un cas de services (5 personnes, operations numeriques). Les deux confirment T4 mais pour des raisons differentes.
- Drakkar a perdu le client. Thierry est convaincu que l'intervention etait de qualite. Nathan reconnait que l'equipe n'a "pas ete assez directe sur la gouvernance." Les deux peuvent etre vrais simultanement.
- Prediction a 80% sur la suite Decotec (Nathan) : ils prendront un integrateur "industriel", deploieront Odoo production, depenseront 150-250K EUR supplementaires, et n'auront pas de ROI mesurable parce que le modele de donnees ne sera pas pense et les process ne seront pas formalises.

---

## 4. CAS TWOGHETHER — Le deal perdu contre The Tribe

### Le deal

**Twoghether :** Plateforme de mise en relation de particuliers pour services a la personne. Differenciateur : connexion directe API URSSAF (toute prestation declaree). Equipe de 3 : Angelique (fondatrice/financement, famille aisee), Maxime (commercial), Yoann (developpeur unique).

**Pourquoi Drakkar s'est interesse :** Maxime avait "bien matche" avec Nathan lors d'une rencontre anterieure. Drakkar = potentiel CTO/CPO fractionne + refonte front-end + securite.

**Timeline :** 4 RDV de novembre 2025 a fevrier 2026. Audit technique complet (2K EUR). Rapport PDF confidentiel. Perte ~10 fevrier 2026. Concurrent gagnant : **The Tribe** (CEO Benoit Vasseur, 70+ personnes).

---

### Les chiffres de l'audit Drakkar (ce que Drakkar savait)

| Metrique | Valeur |
|---------|--------|
| Couverture tests | **0%** |
| Ratio d'inefficience | **6,4x** (88 jours optimal vs 566 jours reels) |
| Presence developpeur | **44%** des jours ouvres |
| Duree projet | **36 mois** |
| Vulnerabilites securite | 45 (dont 1 critique) |
| Lignes de code | ~63K (32K TypeScript, 31K PHP) |
| Bug ratio commits | 41% du total |

**Vulns critiques identifiees :** axios CVE-2025-27152, react-scripts (CRA) projet abandonne par Facebook, Laravel 10 EOL fevrier 2025, moment.js obsolete.

**Profil Yoann (dev unique) :** Mid-level (3-5 ans). Bon executant dans un systeme dysfonctionnel. 0 tests. 0 CI/CD. Aucune utilisation d'IA (Copilot, ChatGPT). Ses modules crees from scratch (KYC, ADS) ont un bug ratio 2x meilleur que le code herite (17-25% vs 40-61%). "Avec un PM, un cadre clair et de l'outillage moderne, sa velocite doublerait."

---

### Ce que ca revele sur la vente B2B

**Pourquoi Drakkar a perdu — 5 raisons :**

1. **Sous-investissement en avant-vente.** Drakkar : audit a 2K EUR. The Tribe : jours entiers avec lead devs + product designers + PM + Benoit en direct.
2. **Pas de projection.** Drakkar : "Faisons un bilan d'abord, on verra." The Tribe : "Voila la roadmap, voila ou on vous emmene."
3. **Effet "boule dans le ventre".** Maxime (verbatim) : "Ca nous a laisse une espece de boule dans le ventre en disant putain, mais est-ce qu'on y arrivera ?" Le diagnostic honnete a effraye au lieu de rassurer.
4. **Le marche de la reassurance.** Angelique (fondatrice, finance le deal) s'est sentie "plus safe" avec The Tribe. Maxime : "C'est vraiment une histoire de feeling."
5. **Matthis sous-exploite.** The Tribe : experts metier longuement. Drakkar : Matthis 30 minutes.

**La lecon strategy (Nathan verbatim dans le debrief Slack) :** "The Tribe ils sont plus chers et moins bons sur ces sujets [...] Ils vont placer LEURS equipes. Ils vont les saigner le plus possible. Nous on va mettre de l'agilite pour qu'ils aillent au mieux. Et ils n'ont pas les moyens de se payer une agence de 70+ personnes en vrai."

Nathan reconnait dans l'appel Maxime : "Je pense qu'on n'a pas joue au meme jeu entre les autres et nous. Eux forcément ils l'ont fait un peu plus commercial, a essayer de vous projeter."

---

### La confiance vs la competence

**Verbatim Maxime** (ce que Drakkar aurait du entendre) : "Peut-etre que sur les petites equipes, il y a cette notion de rassurant a amener un peu plus."

**La vraie lecon :** Les acheteurs ne choisissent pas le meilleur prestataire. Ils choisissent le prestataire avec lequel ils se sentent le plus en securite pour traverser ce qu'ils savent etre une periode difficile. Dans des contextes de forte incertitude (startup, dette technique, peu de cash), la reassurance emotionnelle prime sur la rigueur analytique.

---

### Ce que ca confirme pour Spider

**Confirmation de T2 (B2B = mensonge) :** Prouvee. La decision etait emotionnelle. "C'est une histoire de feeling."

**Confirmation du pivot :** Nathan a dit a Benoit Vasseur : "Au final [...] je pense que ces scopes a 50-100k, potentiel 200k+ si ca marche bien, pour l'instant ca tient... Mais avec la vitesse a laquelle l'IA compresse les couts de delivery, je me demande combien de temps. [...] Nous on prend la deuxieme [voie], focus PME/ETI."

**La bulle de Nathan :** "Hallucine que Benoit ne se rende pas compte en 2026" mais realise qu'il "vit dans une microbulle YC [...] encore enorme inertie sur les boites francaises." Signal d'autocritique important pour calibrer le timing marche.

**Lecon commerciale pour Spider :** "Vendre la vision, pas le diagnostic. Les gens n'achetent pas un bilan de sante, ils achetent la promesse de guerison." → Coherent avec le pivot "arriver avec le prototype" que Nathan veut tester sur Jordan et Beaulieu.

---

## 5. L'EQUIPE ET LE DEAL

### Cap table Spider (structure finale validee le 2 fevrier 2026)

| Actionnaire | % Spider | Role | Justification |
|-------------|----------|------|---------------|
| Nathan Menard | **51%** | Vision, produit, fundraising | Lead founder, leve sous son nom, majorite non-negociable apres le trauma Drakkar |
| Jean Le Tulzo | **20%** | CFO, structuration offre, ops | Co-fondateur brique consulting/FDE. Passage de ~8% indirect a 20% direct apres CODIR du 31 jan |
| Remy Menard | **14%** | CTO, infrastructure | Construit la tech. Augmente de 10% a 14% en reconnaissance de son role central |
| Thierry Menard | **10%** | Lead FDE, scale consulting | Credibilite industrielle, vente senior. Passage de ~3% indirect a 10% direct |
| Drakkar Group | **5%** | Financement (100K EUR) | Regime mere-fille, lien corporate. Reduit de 20% a 5%. |

**Cap table Drakkar (contexte) :**

| Actionnaire | % Drakkar |
|-------------|-----------|
| Nathan Menard | 47% |
| Jean Le Tulzo | 38% |
| Thierry Menard | 15% |

**Subsidiaires Drakkar :** Studio (100%, en transfert), Accelerateur (87,5% — Nicolas Guimier 12,5%), Academie (100%).

---

### Profils — Forces et faiblesses

**Nathan Menard (26 ans, CEO, 51% Spider)**
- Forces : Vision strategique (10-40 sessions de recherche Palantir, maitrise de l'IA coding, speed de construction x10-20 vs norme), architecture Spider, capacite a coder ET strategiser, energie et ambition declares ("soit rien, soit ca s'approche du milliard").
- Faiblesses : **Bottleneck de tout** — marketing, ventes, studio, Spider, immobilier (SCI), CODIR. Nathan dans CODIR 2 : "Je deviens le bottleneck de tout. [...] Je peux litteralement plus physiquement bosser plus que ca." Burnout latent documente. Gestion de l'equipe parfois polarisante ("On a quand meme vraiment des chevres [...] leur ratio est 3 a 10x"). Risque de perte de focus entre Drakkar et Spider.

**Jean Le Tulzo (38 ans, COO/CFO, 20% Spider)**
- Forces : Structuration financiere et juridique (SCI, pacte d'associes, CIR, financement bancaire), 38% Drakkar = ancrage institutionnel, gestion des relations complexes (Zalina, CET, Nadine, Nico), vision "paliers d'IA" claire (copilot → agent → architecte humain). Passage de defenseur a co-fondateur apres le CODIR du 31 janvier.
- Faiblesses : Attention divisee (38% Drakkar + 20% Spider). Jean dans CODIR 2 : "Je ne vois pas comment on peut tenir en attendant le futur du groupe." Porte l'inquietude sur la tresorie. Pas de role commercial direct. A besoin d'un chiffre precis sur le burn avant de faire quoi que ce soit.

**Thierry Menard (53 ans, Operations, 10% Spider)**
- Forces : Experience industrielle (ex-Airbus COMEX, head manufacturing), credibilite senior dans les PME industrielles, methode de workshops rapides (3-4 workshops de 15 jours avec specialists, resolution de problemes quotidiens, creation de "biais cognitifs"), temoignage direct sur Palantir/Airbus (usage reel, limites reelles), vision long terme la plus systemique des trois.
- Faiblesses : Plus conservateur sur les timelines. Drakkar Accelerateur "5K en dessous" de l'objectif de production — gestion de ce deficit prend du temps. Pas d'IA coding. Peut freiner le rythme de Nathan.

**Remy Menard (CTO, 14% Spider)**
- Forces : Construit le coeur technique de Spider. Kubernetes maitrise. Architecture multi-tenant separee. Comprehension fine de la complexite IA vs complexite humaine (insight sur les story points). Propose deja la convergence Odoo Intelligence → Spider.
- Faiblesses : Pas encore salarie formellement (Nathan le paie de sa poche, "ca commence a vraiment etre un probleme"). Pas encore a Nantes (visites mensuelles a mettre en place). Besoin des maquettes Figma pour Astrid. Acces Figma non encore debloque.

---

### Le probleme du bus factor Nathan

**Defini dans CODIR 2, confirme dans QUESTIONS-NATHAN :**

> "Le bus factor de Nathan = 1. Si Nathan tombe malade, Spider s'arrete. Si Nathan est trop fatigue, Drakkar ralentit. Si Nathan est le seul a pouvoir faire le Diagnostic Eclair et le prototype → ce n'est pas une startup, c'est un freelance tres cher."

**Les 4 domaines ou Nathan est bottleneck (CODIR 2) :**
1. Marketing — "level up marketing"
2. Ventes — "level up sales"
3. Studio — "level up le studio"
4. Spider — "level up Spider"

**Le seul remede identifie :** Construire des systemes qui reduisent son implication. Mais construire ces systemes requiert son implication — le paradoxe classique du fondateur.

**Gate test pour ce probleme (QUESTIONS-NATHAN) :** FDE #1 fait le client 5 SEUL. Si ca marche → startup. Si ca echoue → consulting. Test a faire en mois 3-6.

---

## 6. LA SITUATION DRAKKAR

### Ce que les CODIRs revelent

**Sources :** CODIR 1 (19 fev, Museum d'Histoire Naturelle, 3h11), CODIR 2 (19 fev, dejeuner, 1h09), Echange Remy (20 fev, ~20 min).

---

### Burn rate et tresorie

**Le chiffre que personne n'a (au moment du CODIR) :**

Jean dans CODIR 2 : "C'est 20 000 par mois. Sur nos fonds propres, on ne sait tenir a rien." Puis : "Au moins ca coute 40 000. Peut-etre pas moins ?"

Nathan dans CODIR 2 : "50 000. [...] On a un probleme. Mais il faut poser ca pour savoir ou on en est."

**Estimation actuelle (non confirmee) : 20K-50K EUR/mois de burn.**

**Remy, echange du 20 fev :** Nathan dit que Spider va couter "l'equivalent de 400 a 500 000 euros" en annee 1 (100-150K EUR en depenses directes + salaire Nathan + temps equipes internes Drakkar).

**Tresorie (reponse Nathan dans QUESTIONS-OUVERTES Q9) : 5-6 mois.** → Action requise maintenant, pas dans 6 mois.

**Studio (Drakkar) :**
- Objectif hebdomadaire : 20K+ EUR
- Realite : 16-17K EUR/semaine
- Utilisation staffing : 55-60% au lieu de 80% cible

---

### Staffing et modele de vente

**Le diagnostic de Nathan (CODIR 2, verbatim) :**
- "Ce qu'on vend c'est degueulasse. On est juste des implementeurs comme les autres. Il n'y a zero difference parce qu'on est incapable d'assumer une difference."
- "On a quand meme vraiment des chevres [...] tu mets un mec competent, il produit 5 fois plus que pratiquement tous nos gars. [...] Le ratio compare a ce qu'on vise a Drakkar, c'est 3 a 10x."
- "L'equipe a avance de 10% pendant que le marche a avance de 100%."

**Evaluations individuelles :**
- **Mathis (studio lead) :** "Incapable de deleguer. Ne transmet pas." → Thierry coach Mathis sur ce sujet.
- **Baptiste (studio) :** Nathan veut le sortir. L'equipe desaccorde. Nathan : "le studio a besoin de POs, pas de devs."
- **Loan :** Jean pense qu'il ne fera pas la transition IA. Nathan pousse back : "il a 22 ans, il progresse."
- **Hugo / Clement :** Potentiel vers project management et quality engineering.
- **Charlotte, Julie, Farah, Jeremy :** Thierry : "J'ai completement confiance pour les emmener sur le conseil, audit, entreprise. Ce sont des gens qui vont rapporter leur croute."
- **Christian (arrive mai 2026) :** Comptabilite + ERP + coding. Debat : Drakkar clients ou Spider team ? Thierry prefere Spider.
- **Gwen (office management) :** Nathan : "la prochaine internance, un agent IA, pas une personne."

**Le modele de vente actuel est juge mort :** Nathan dans CODIR 2 : "On vend du conseil, on vend des pourquoi, et en fait on ne vend pas des reponses." → Pivot vers prototype/outcome selling. Premier test : Jordan (vendredi 27 fev). Deuxieme test : Beaulieu.

---

### Nathan en burnout — etat documente

**Verbatims CODIR 2 :**
- "Je peux litteralement plus physiquement bosser plus que ca."
- "Je deviens le bottleneck de tout."
- "En regardant juste aujourd'hui, tout ce qu'on a fait, c'est ajouter des choses sur mon assiette, rien n'a ete enleve."
- "Si je vois que le sujet n'est pas cadre, n'est pas traite, je ne peux pas le lacher mentalement."

**Thierry (inquietude sincere) :** "Quand est-ce que tu dors ? [...] Tu as fait un marathon et tu regardes la camera... t'es cool, mais..."

**Jean :** "C'est juste comment tu prends soin de toi avant d'etre force de le faire."

**Conclusion des binomes operationnels (CODIR 2) pour reduire la charge :**
- Nathan + Jean : transformation IA, outils d'efficience, modele financier
- Jean + Thierry : efficience operationnelle, comprehension financiere de l'equipe
- Nathan + Thierry : differenciation vente, outils pre-decouverte, prototype-based selling

---

## 7. L'INFRA SPIDEROS — Ce qui existe vs ce qui est planifie

### Ce qui EXISTE reellement (au 21 fevrier 2026)

Sources : QUESTIONS-NATHAN (reponses de Nathan), echange Remy 20 fev, CODIR 1.

**Design System "The Lake" :** Quasiment termine. Tokens CSS existent. Composants atoms/molecules/organisms definis. Nathan : "Quasiment termine. Part du principe que full complet."

**Builder (app interne) :** Existe mais pas termine. Utilise par Nathan/Remy pour le dev avec la methodologie BMAD.

**Kubernetes (hebergement) :** 3 clusters operationnels. Remy : "Kubernetes, c'est justement fait pour ca et c'est utilise par toutes les grosses boites. Des que tu atteins tel pourcentage de RAM sur ton cluster, tu en deploies un autre." Architecture multi-tenant separee des le depart (chaque client = base de donnees isolee).

**Claude Code Max (Nathan) :** Abonnement actif. 150 USD d'extra usage a mi-fevrier. Usage : mega-recherches strategiques (40+ web searches croises pour etude de marche).

**Nango (connecteurs OAuth, 300+ integrations) :** Choisi comme plateforme. Pas encore branche sur des donnees reelles Jordan.

**Zitadel (authentification) :** Mentionne dans l'architecture. Statut de livraison non confirme dans le corpus.

**Speech-to-process (Claude Code + MCP Figma) :** Operationnel. Nathan l'a fait tourner pendant l'appel Jordan (20 fev). "Playbook de questions, fait avec Claude Code + MCP branche a Spider." Phase 1 : genere automatiquement toute la proposition sur base d'un echange. Phase 2 : le client le fait seul en guide.

**Odoo Intelligence (outil interne Drakkar) :** Couche IA construite pour l'usage interne de Drakkar. Probleme d'adoption : l'equipe ne comprend pas comment ca fonctionne. Solution Nathan : permettre a chaque utilisateur de modifier son propre system prompt. Remy a propose la convergence Odoo Intelligence → Spider.

---

### Ce qui est PLANIFIE mais pas construit

**Les 6 apps Spider :**
- Website (spideros.ai) : squelette probable
- Playbook (design system) : le plus avance
- Builder : existe mais non termine
- **People, Documents, Platform : designs/specs, pas de code fonctionnel** (confirmation Nathan dans QUESTIONS-NATHAN)

**Claims Engine :** "Non, on a rien. Un de mes prochains sujets sur lesquels je veux avancer." (Nathan dans QUESTIONS-NATHAN). Le document tech decrit Dempster-Shafer, Fellegi-Sunter, 14 predicats — c'est un design doc, pas du code.

**Connecteurs (Notion, Sheets, Pennylane) :** Pas encore branches sur des donnees reelles. Jordan Phase 0 = prototype qui "donne l'illusion" sans connexion reelle. Nathan : "Aucun des deux [branche ou importe], je veux d'abord faire un proto qui donne l'illusion. S'il signe, on fera directement la connexion."

**Entity Resolver, LiveViews, Agents en production :** Architecture definie, pas construite. Nathan : "15-20% construit, 80-85% a faire" (estimation Claude dans QUESTIONS-NATHAN que Nathan n'a pas contredite).

**Gestion de projet dans Spider :** Pas prevu initialement, devient prioritaire pour le projet Astrid. Remy : "Je pense que c'est un truc qui n'etait pas vraiment prioritaire mais je pense qu'il faut qu'on le fasse au final."

---

### Architecture technique etablie

| Composant | Choix | Statut |
|-----------|-------|--------|
| Frontend | Next.js 16 | Architecture definie |
| Backend | Litestar (Python) | Architecture definie |
| Base relationnelle | PostgreSQL | Architecture definie |
| Base graph | SurrealDB | Architecture definie |
| Cache distribue | TiKV | Architecture definie |
| Hebergement | Kubernetes (3 clusters) | **OPERATIONNEL** |
| Auth | Zitadel | Architecture definie |
| Connecteurs | Nango (300+ integrations) | Choisi, pas branche |
| Design system | "The Lake" | **QUASI-COMPLET** |
| Speech-to-process | Claude Code + MCP Figma | **OPERATIONNEL** |

---

### Le premier vrai projet : Astrid

**Astrid :** Site web, ~30K EUR. Premier test de production Spider. "On a une petite dizaine de projets similaires dans le pipeline."

Bloquage actuel : Remy n'a pas acces aux maquettes Figma. Nathan doit appeler Marc d'Astrid pour debloquer.

Spider sera utilise comme outil de gestion de projet pour Astrid (tracking temps agent, temps supervision humaine, features). C'est le premier test du systeme d'estimation agent vs humain.

---

### Le systeme d'estimation agent/humain (en construction)

**Deux metriques a tracker :**
1. Temps d'execution agent (combien de temps l'IA tourne)
2. Temps de supervision humaine (prompter, faire les retours, tester)

**Ratios empiriques Nathan :**
- Tache agent unitaire : 2-30 minutes. Au-dela = mal scope.
- Ratio initial (approximatif) : 2h humain pour 7h agent (1h dev + 1h designer pour 1 journee agent)
- Proposition : 30 min agent / 5 min supervision (~1:6), avec blocs de check de 30min-1h tous les 5h agent

**Insight cle de Remy :** "La complexite pour un humain, ce n'est pas du tout la meme que pour une IA." Une feature complexe pour un humain peut etre triviale pour l'IA, et inversement.

**Status honnete (Remy) :** "Pour un premier projet, ca va etre a la louche."

**Status objectif (Nathan) :** "Je vois ce projet comme un projet de R&D. Je suis ok avec l'idee qu'il y ait de grandes chances qu'on se plante. J'aimerais bien juste qu'on fasse un systeme que nous on trouve tres bon a l'instant T, pour que si on se plante, on ait un referentiel de combien on s'est plante, pourquoi, ou, comment."

---

## 8. LES REPONSES DE NATHAN — Synthese

Sources : QUESTIONS-NATHAN (reponses de Nathan le 20 fev) + QUESTIONS-OUVERTES (reponses Nathan le 21 fev)

---

### Sur le pricing

**Q : Prix fixe (500 EUR/mois) ou prix au ROI ou prix au CA (0.5%) ?**

Nathan : "En fait pas de pricing fixe je pense, on fait en fonction du ROI. [...] Aucune idee, je pense qu'il faut adapter au cas mais en meme temps c'est chiant et pas scalable. Peut-etre ok au debut. Ou alors membership + extra usage comme Claude Code avec le plan Max ? No idea."

Sur le 0.5% du CA : "Mais complique quand meme. Pourquoi afficher le CA ? Pourquoi ne pas le faire en auto-diag ou via un humain ?"

**Conclusion :** Pas de reponse definitive sur le pricing. Le modele le plus probable (implicite dans les CODIR) : abonnement de base (~500 EUR/mois) + upsell par module + setup fee. A tester sur Jordan.

---

### Sur le moat

**Q : Quel est le vrai moat de Spider ?**

Nathan : "Le moat c'est vraiment notre capacite a recreer les process a partir de data brut, ca c'est le plus sans aucun effort (ex : software qui ecoute tout genre screenpipe puis derriere connexion auto API ?). Puis derriere capturer le tacit."

Et : "Bcp plus peur qu'un autre acteur fasse mieux que nous et que pas un vrai moat."

**Ce que ca signifie :** Nathan reconnait que le moat declare (data capturee + ontologie + effet reseau) n'existe pas encore. Il doit etre construit par l'execution, pas declare par la these. La vraie peur : un concurrent plus rapide.

---

### Sur l'endgame

**Q : Startup (lever, croitre vite, exit) ou Empire (autofinancer, racheter des PME, accumulation) ?**

Nathan : "Je veux etre dieux, je veux creer un nouveau jeux. Donc je pense jouer aux deux a la fois."

Sur l'endgame fonds : "Pour moi la vue c'est outil pour les fonds mais on excluera pas de le faire nous-memes en mode service as software. Ou meme les deux en parallele, on verra."

Sur Drakkar : "Phase 2 decision a prendre, pour moi Drakkar sort a ce moment la et potentielle levee de fonds. Faudra meme se poser la question de fusion ou autre a ce moment-la. Moment cle."

---

### Sur la tresorie

**Q : Combien de mois de tresorie exactement ?**

Nathan : "5-6 mois."

**Implication :** L'urgence est reelle. La fenetre pour valider le modele avant la crise de tresorie est courte. Jordan doit signer. Astrid doit livrer. Les 10-15 prospects Drakkar doivent etre approaches des la semaine du 24 fevrier.

---

### Sur le speech-to-process

**Q : C'est quoi exactement et c'est reproductible ?**

Nathan : "Phase 1 : fait automatiquement toute la proposition juste sur base d'un echange comme celui avec Spider. Phase 2 : meme le client tout seul en guide. Et oui, playbook de questions et fait avec Claude Code + MCP branche a Spider."

**Ce qui est prouve :** Le speech-to-process a tourne pendant l'appel Jordan (CODIR 1, verbatim Nathan). Le workflow existe.

**Ce qui n'est pas confirme :** Reproductible par un FDE (Thierry, Christian) sans Nathan ? Pas encore teste.

---

### Sur le business model Spider en semaine 1

**Q : Nathan fait le travail, ou un systeme tourne ?**

Nathan : "Oui [Nathan fait le travail]. D'ailleurs les clients paieront des setup-fee assez vite. J'ai vraiment en tete : Step 1 : prototype → offre a laquelle il ne peut pas dire non. Step 2 : une fois implemente, vu qu'on a toute la data, on propose des upsells a haute valeur ajoutee. Setup fee + abonnement."

**Ce que ca confirme :** Phase 0 = consulting augmente par l'IA, pas un produit automatise. C'est le modele correct (YC : "do things that don't scale"). Mais Nathan doit etre transparent avec Jordan : "Phase 0, je fais le travail moi-meme avec les meilleurs outils IA. Je construis le produit EN servant les clients."

---

### Sur le moat reel vs le moat narratif

**Q : Quelle est la difference entre ce qu'on dit et ce qu'on a ?**

Nathan : "Le moat c'est vraiment notre capacite a recreer les process a partir de data brut [...] sans aucun effort [...] Puis derriere capturer le tacit."

**Ce que ca signifie objectivement :** Aujourd'hui, RIEN n'empeche un freelance competent avec Claude + Zapier de faire exactement ce que Spider fait pour Jordan. Le moat n'existe pas encore. Il se construit par l'execution : ontologie qui se transfere entre clients du meme vertical, donnees accumulees sur 3-12 mois, patterns cross-clients.

---

### Sur les questions non resolues (QUESTIONS-OUVERTES)

**Q3 (qualite agents) :** Nathan propose "phase de brouillon" puis autonomie progressive. Possiblement un modele a la Claude Code (abonnement + nombre d'actions, extra usage paye). Pas de reponse definitive.

**Q4 (verticaux physiques) :** Nathan : "Flexible je pense, l'IA fait qu'on peut etre large." Risque : perte de focus sur le wedge vertical initial (agences de services).

**Q5 (dogfooding Drakkar comme client 0) :** Nathan : "On fait les 2 en parallele." Correct strategiquement — Drakkar = laboratoire interne, Jordan = premier test externe.

**Q7 (endgame fonds) :** Nathan : "Outil pour les fonds, ou mode service as software, ou les deux en parallele, on verra." L'ambiguite reste entiere.

**Q10 (cout credits IA par client) :** Nathan : "Je sais juste pas comment rendre ca clair. Mais peut-etre ok que opaque... idk." Remy doit poser un calculator de cout par tache avant de fixer un prix definitif.

**Q11 (startup ou empire) :** Nathan : "Je veux etre dieux, je veux creer un nouveau jeux. Donc je pense jouer aux deux a la fois." Reponse qui fuit la question. Les decisions tactiques sont opposees selon qu'on optimise pour la vitesse (startup) ou l'accumulation (empire).

---

*Annexe A4 finalisee le 21 fevrier 2026.*
*Sources primaires : 12 fichiers / ~150 000 mots de corpus brut.*
*Ce document centralise les faits. Les interpretations et recommandations sont dans les autres annexes.*
