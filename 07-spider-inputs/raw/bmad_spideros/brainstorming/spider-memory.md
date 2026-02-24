# Brainstorming Session: Spider Memory

**Date:** 2026-01-14
**Facilitateur:** Creative Intelligence (BMAD)
**Participant:** Nathan Menard
**Duree:** En cours
**Priorite:** P0 — Infra MVP critique

---

## Objectif

Definir Spider Memory comme brique technique centrale de SpiderOS — le moteur de memoire et vectorisation qui alimente tous les modules.

## Techniques Utilisees

1. **Jobs-to-be-Done** — Besoins des modules envers Memory
2. **Reverse Brainstorming** — Comment Memory fait foirer les modules
3. **Starbursting** — Done
4. **Six Thinking Hats** — Done
5. **SCAMPER** — Done

---

# Contexte

## Positionnement

**Ce que Spider Memory EST :**
- Le cerveau de SpiderOS — il voit et retient tout
- Une brique technique interne (pas un produit utilisateur direct)
- Le systeme qui transforme la data brute en contexte actionnable
- Un service partage entre tous les modules

**Ce que Spider Memory N'EST PAS :**
- Un CRM, un chatbot, un outil de creation (ce sont les modules consommateurs)
- Une simple base de donnees
- Un RAG classique

## Architecture

Spider Memory = **couche vector separee** de LightStar (PostgreSQL)

```
┌──────────────────┐     ┌──────────────────┐
│    LightStar     │     │  Spider Memory   │
│   (PostgreSQL)   │     │    (LanceDB)     │
│                  │     │                  │
│  - Users         │     │  - Embeddings    │
│  - Contacts      │     │  - Resumes IA    │
│  - Deals         │     │  - Recherche     │
│  - Metadata      │     │    semantique    │
└────────┬─────────┘     └────────┬─────────┘
         │                        │
         └────────────┬───────────┘
                      │
              Les modules appellent
              les deux separement
```

**Note Remy (Spider Content) :** "En vrai elle est pas super utile je pourrais parfaitement utiliser pgvector dans mon cas mais c'est plus pour unifier les infras que j'ai fait ca, en gros je sauvegarde plein de resumes sur les marques par exemple le public cible et de l'identite visuelle de ta marque et ensuite quand tu pose une question dans le chat ca va vectoriser la demande et venir piocher dans les bons resumes pour parametrer au mieux les generations de videos et d'images"

---

# Les 5 Axes de Spider Memory

| Axe | Ce que ca permet |
|-----|------------------|
| **1. Stockage massif + perf** | Millions de mails, calls, docs — retrouves en millisecondes |
| **2. Recherches dynamiques** | Croiser des dimensions semantiques que la DB ne peut pas exprimer |
| **3. Contexte pour l'IA** | Injecter le bon contexte quand un module agit |
| **4. Extraction & structuration** | Transformer le non-structure en donnees exploitables |
| **5. Qualification** | Score de confiance, fraicheur, validation |

---

# Criticite par Module

| Module | Besoin Spider Memory (vector) | Criticite |
|--------|-------------------------------|-----------|
| **Spider People** | Critique — recherches dynamiques, millions de mails, extraction profil | 🔴 Must have |
| **Spider Builder** | Critique — contexte code, recherche semantique, graphe deps | 🔴 Must have |
| **Spider Chatbot** | Critique — RAG, historique (a creuser au brainstorming dedie) | 🔴 Must have |
| **Spider Content** | Nice to have — RAG brand, mais pgvector suffirait | 🟡 Unification infra |

---

# Jobs-to-be-Done par Module

## Spider People → Spider Memory

### Axe 1 : Stockage massif + perf

| JTBD |
|------|
| 10 ans de mails d'un dirigeant, 5000 contacts, historique complet — brief en 200ms |

### Axe 2 : Recherches dynamiques

| JTBD |
|------|
| "Tous les contacts ou on a senti une resistance prix" |
| "Les deals qui ressemblent a celui-la" |
| "Quand on a deja eu cette objection" |
| "Trouve-moi des patterns de closing reussi" |

### Axe 3 : Contexte pour l'IA

| JTBD |
|------|
| Brief avant RDV (resume derniers echanges + infos cles + points a creuser) |
| Coaching post-call (compare ce qui a ete dit vs le playbook) |
| Suggestion de message pre-redige avec le bon contexte |

### Axe 4 : Extraction & structuration

| JTBD |
|------|
| Profil psychologique (MBTI, DISC, motivations) depuis les conversations |
| Infos perso (enfants, anniversaire, preferences) |
| Promesses faites, objections soulevees |
| Playbook : detecter les patterns (etapes du process, questions qui marchent, timing optimal) |
| Pretextes de contact (anniversaire, evenement, timing relance) |
| Score de connaissance (0-100%) : quelles dimensions remplies, lesquelles manquent |

### Axe 5 : Qualification

| JTBD |
|------|
| "Cet anniversaire vient d'un mail de 2019, confiance 60%" — eviter de passer pour un toccard |
| Score de confiance sur chaque info extraite |
| Fraicheur des donnees visible |

---

## Spider Builder → Spider Memory

### Axe 1 : Stockage massif + perf

| JTBD |
|------|
| Gros monorepo, des milliers de fichiers — contexte pertinent en ms |

### Axe 2 : Recherches dynamiques

| JTBD |
|------|
| "Ou est-ce qu'on gere l'auth ?" |
| "Fichiers similaires a celui-la" |
| "Patterns utilises pour les API" |

### Axe 3 : Contexte pour l'IA

| JTBD |
|------|
| Injecter les bons fichiers quand Claude code |
| Graphe de dependances pour impact analysis |

### Axe 4 : Extraction & structuration

| JTBD |
|------|
| Structure du projet, conventions |
| Dependances entre fichiers |

### Axe 5 : Qualification

| JTBD |
|------|
| "Ce fichier a change il y a 2h" — fraicheur du contexte |

---

## Spider Content → Spider Memory

**Note :** Nice to have, pgvector suffirait. Utilise pour unifier l'infra.

### Axe 3 : Contexte pour l'IA

| JTBD |
|------|
| RAG sur les resumes brand (public cible, identite visuelle) pour parametrer les generations |

---

## Spider Chatbot → Spider Memory

**Note :** Brainstorming Chatbot complete. Spider Memory = P1 pour Chatbot (pas V1).

### Axe 1 : Stockage massif + perf

| JTBD |
|------|
| Historique de toutes les conversations d'un utilisateur — retrouver un echange d'il y a 3 mois en ms |
| Base de connaissances entreprise (docs Notion, Confluence, etc.) indexee pour RAG |

### Axe 2 : Recherches dynamiques

| JTBD |
|------|
| "Retrouve la conversation ou on a parle de ce sujet" |
| "Questions similaires deja posees par l'equipe" |
| "Sujets recurrents dans les conversations" |

### Axe 3 : Contexte pour l'IA

| JTBD |
|------|
| Memoire utilisateur cross-conversations — l'IA se souvient du contexte accumule |
| Memoire entreprise — injecter les docs pertinents pour enrichir les reponses (RAG) |
| Contexte Spider People — enrichir les reponses avec les infos clients |

### Axe 4 : Extraction & structuration

| JTBD |
|------|
| FAQ emergente depuis les conversations (quelles questions reviennent souvent ?) |
| Patterns d'usage — comment les equipes utilisent l'IA |
| Prompts efficaces — detecter les prompts qui generent de bonnes reponses |

### Axe 5 : Qualification

| JTBD |
|------|
| "Cette reponse vient d'un doc de 2023" — sourcer les informations RAG |
| Score de fraicheur sur les docs indexes |
| Confiance sur les infos injectees |

### Priorite pour Chatbot

| Phase | Besoin Spider Memory |
|-------|---------------------|
| **MVP (P0)** | Memoire utilisateur simple (stockee cote Chatbot, pas Memory) |
| **P1** | RAG docs internes, memoire entreprise via Spider Memory |
| **P2** | Analytics avances, patterns, FAQ emergente |

---

# Reverse Brainstorming

## "Comment Spider Memory fait foirer Spider People et Spider Builder ?"

### Spider People

| # | Comment ca echoue | Insight (l'inverse) |
|---|-------------------|---------------------|
| **1** | **Recherche trop lente** — 3 secondes pour un brief avant RDV, l'utilisateur abandonne | Perf < 500ms obligatoire |
| **2** | **Extraction fausse** — "Marie a 3 enfants" alors qu'elle en a 2, perte de confiance totale | Score de confiance visible + validation ciblee |
| **3** | **Contexte IA hors sujet** — Le brief parle d'un autre Jean-Pierre | Attribution precise des donnees aux contacts |
| **4** | **Recherche semantique nulle** — "Resistance prix" ne trouve rien alors que c'est partout | Qualite des embeddings + chunking intelligent |
| **5** | **Donnees perimees** — Brief base sur des infos de 2019 sans le signaler | Fraicheur visible, prioriser le recent |
| **6** | **Playbook jamais construit** — Trop peu de data ou patterns pas detectes | Seuil minimum de conversations pour patterns |

### Spider Builder

| # | Comment ca echoue | Insight (l'inverse) |
|---|-------------------|---------------------|
| **7** | **Contexte code obsolete** — Claude utilise une ancienne version du fichier | Delta indexing en temps reel (watch mode) |
| **8** | **Mauvais fichiers injectes** — Claude recoit des fichiers non pertinents | Selection fine du contexte, pas tout envoyer |
| **9** | **Graphe de deps faux** — Impact analysis rate des fichiers impactes | Parsing AST fiable multi-langage |
| **10** | **Index trop gros** — Monorepo enorme, ca rame | Chunking intelligent, index incremental |
| **11** | **Recherche semantique trop floue** — "Ou on gere l'auth" retourne 50 fichiers | Ranking pertinent, top-k intelligent |

### Spider Chatbot

| # | Comment ca echoue | Insight (l'inverse) |
|---|-------------------|---------------------|
| **12** | **RAG hors sujet** — L'IA cite un doc qui n'a rien a voir avec la question | Relevance scoring strict, top-k intelligent |
| **13** | **Docs obsoletes** — RAG base sur un doc de 2021 sans le signaler | Fraicheur visible, sourcing transparent |
| **14** | **Memoire entreprise trop bruyante** — Trop de contexte injecte, reponse confuse | Selection fine du contexte, pas tout injecter |
| **15** | **Latence RAG** — 5 secondes de plus pour chaque reponse | Cache intelligent, pre-indexation |
| **16** | **Pas de sourcing** — L'utilisateur ne sait pas d'ou vient l'info | Citation des sources obligatoire |

---

# Session 2 : Starbursting

**Note :** Beaucoup de questions techniques restent ouvertes — c'est normal, les recherches viendront. L'objectif ici est de poser les bonnes questions.

## WHO — Qui ?

| Question | Reponse |
|----------|---------|
| **Qui utilise Spider Memory ?** | Les modules SpiderOS (People, Builder, Chatbot, Content) + l'equipe technique SpiderOS |
| **Qui administre ?** | L'equipe technique SpiderOS |
| **Qui indexe les donnees ?** | Les modules eux-memes via l'API Memory |
| **Qui est impacte si Memory tombe ?** | Tous les modules — c'est comme perdre la DB d'un SaaS |
| **Qui paie le cout infra ?** | SpiderOS (mutualise) |

## WHAT — Quoi ?

| Question | Reponse |
|----------|---------|
| **Qu'est-ce qu'on vectorise ?** | A definir — certaines donnees en DB classique, d'autres vectorisees |
| **Quelle techno vector DB ?** | A rechercher |
| **Quels embeddings ?** | A rechercher |
| **Quelle granularite chunking ?** | A rechercher |
| **Quels metadata stocker ?** | A definir selon les besoins des modules |
| **Quelle taille max de donnees par tenant ?** | A definir |
| **Comment gerer les differents types de contenu (texte vs code vs images) ?** | A rechercher |

## WHERE — Ou ?

| Question | Reponse |
|----------|---------|
| **Ou est heberge ?** | Cloud EU obligatoire, idealement Scaleway (souverainete) |
| **Ou sont les donnees brutes vs vectors ?** | A definir (LightStar vs Memory) |
| **Multi-tenant comment ?** | A reflechir — equilibre rapidite dev vs robustesse |
| **Backup ou ?** | A definir |

## WHEN — Quand ?

| Question | Reponse |
|----------|---------|
| **Quand indexer ?** | A l'ingestion (mail recu, call termine, doc ajoute) |
| **Quand re-indexer ?** | Delta indexing pour le code |
| **Quand purger ?** | Politique retention RGPD — a definir |
| **Quand Memory est necessaire pour chaque module ?** | A clarifier par module |

## WHY — Pourquoi ?

| Question | Reponse |
|----------|---------|
| **Pourquoi pas juste pgvector ?** | A valider — peut-etre suffisant pour certains cas |
| **Pourquoi une brique separee ?** | Unification infra, mais a challenger |
| **Pourquoi pas un SaaS (Pinecone, etc.) ?** | Souverainete, cout — a evaluer |

## HOW — Comment ?

| Question | Reponse |
|----------|---------|
| **Comment les modules appellent Memory ?** | API a definir |
| **Comment garantir la perf ?** | A rechercher |
| **Comment gerer le multi-tenant sans leak ?** | A definir |
| **Comment monitorer ?** | A definir |
| **Comment migrer si on change d'embeddings ?** | A rechercher |

---

# Session 3 : Six Thinking Hats

**Angle choisi :** Marketing + grandes questions. Spider Memory c'est le "cerveau de Spider" — comment on le vend sans faire peur ?

## Chapeau Blanc — Faits

| Fait |
|------|
| Spider Memory alimente tous les modules (People, Builder, Chatbot, Content) |
| C'est ce qui permet la "magie" — le contexte, la memoire cross-module |
| Recherches en millisecondes (pas secondes) grace a la vectorisation |
| Aucun concurrent ne propose une memoire unifiee cross-modules comme ca |
| Le terme "memoire" parle a tout le monde (vs "vector database") |

## Chapeau Rouge — Emotions / Intuitions

| Ressenti positif | Crainte |
|------------------|---------|
| "Spider se souvient de tout" — magique, pratique | "Spider se souvient de tout" — flippant, surveillance |
| Le contexte automatique — gain de temps enorme | Ou va ma data ? Est-ce que je suis en controle ? |
| L'IA qui te connait vraiment — relation personnalisee | "Comment il sait ca ?" — effet creepy |
| Vitesse impressionnante (millisecondes) | Qu'est-ce qui se passe si la data fuite ? |

## Chapeau Noir — Risques

| Risque marketing / perception |
|-------------------------------|
| Percu comme intrusif / surveillance |
| Vraies questions legales RGPD — on peut se faire attaquer la-dessus |
| Confusion entre memoire utile et espionnage |

| Risque technique |
|------------------|
| **Qualite des donnees** — le plus gros risque. Si c'est faux, errone, mal score → perte de confiance totale |
| Garbage in, garbage out |
| Migration future si mauvais choix techno |

## Chapeau Jaune — Opportunites / Benefices

| Opportunite |
|-------------|
| **Differenciateur unique** — personne ne propose une memoire unifiee cross-modules |
| **Effet "magie"** — l'utilisateur ne comprend pas comment ca marche, mais ca marche |
| **Vitesse** — recherches en millisecondes, UX impressionnante |
| **Cross-module** — "trouve tout ce qui concerne ce client" dans People + Chatbot + Docs |
| **Argument souverainete** — data en Cloud EU, on controle tout |
| **Lock-in positif** — plus tu utilises Spider, plus il te connait, plus tu restes |

## Chapeau Vert — Creativite / Idees Nouvelles

| Idee |
|------|
| **"Memory Dashboard"** — vue centralisee de toutes les datas, tous modules confondus, avec filtres |
| **Transparence totale** — l'utilisateur voit tout ce que Spider sait, peut tout corriger |
| **Mode "oublie-moi"** — supprimer les donnees qui plaisent pas |
| **Confidence visible** — afficher le score de confiance ("80% sur que son anniv est le 12 mars") |
| **Flashcards / Tinder-like** — valider/invalider des infos chaque jour pour ameliorer la qualite |
| **Pop-ups de validation** — Spider notifie "J'ai trouve que Marie a 2 enfants, tu confirmes ?" |
| **Cross-module search** — "Trouve tout ce qui concerne X" partout |
| **Memory insights** — analytics personnels ("Ce mois-ci vous avez beaucoup parle de Y") |
| **(P2) Enrichissement externe** — scrapping ou autres sources pour completer la data |

## Chapeau Bleu — Process / Prochaines etapes

| # | Etape | Qui |
|---|-------|-----|
| **1** | **Page marketing** — expliquer Spider Memory, le "cerveau de Spider", sans faire peur. Travailler le discours transparence/controle. | Nathan |
| **2** | **UX Spider Memory** — maquetter le Memory Dashboard, le systeme flashcards, la vue "ce que Spider sait sur X", les filtres cross-modules | Nathan |
| **3** | **Recherches techniques** — vector DB, embeddings, chunking, architecture multi-tenant, perf | Remy |
| **4** | **Definir l'API Memory** — contract entre modules, comment People/Builder/Chatbot appellent Memory | Remy + Nathan |
| **5** | **Travailler la transparence des le design** — confidence score visible, mode "oublie-moi", correction des donnees | UX |

---

# Session 4 : SCAMPER

## Substitute — Que peut-on remplacer ?

| Element actuel | Substitution possible |
|----------------|----------------------|
| Recherche SQL classique | Recherche semantique ("trouve les contacts ou on a senti une resistance prix") |
| Data dispersee dans chaque module | Memoire centralisee cross-modules |
| L'utilisateur doit se souvenir | Spider se souvient pour lui |

## Combine — Que peut-on fusionner ?

| Elements | Combinaison |
|----------|-------------|
| Donnees People + Chatbot + Builder + Content | Vue unifiee "tout ce que Spider sait sur X" |
| Memoire + Transparence | Memory Dashboard ou tu vois ET tu corriges |
| Extraction automatique + Validation humaine | Systeme flashcards + pop-ups de validation |

## Adapt — Que peut-on adapter d'ailleurs ?

| Source d'inspiration | Adaptation pour Spider Memory |
|----------------------|-------------------------------|
| Tinder (swipe) | Flashcards pour valider/invalider les donnees |
| Google Photos ("C'est bien Marie ?") | Pop-ups de confirmation sur les extractions |
| Notion / Obsidian (liens entre notes) | Liens entre donnees cross-modules |

## Modify — Que peut-on modifier / amplifier ?

| Element | Modification |
|---------|--------------|
| Score de confiance | Decay temporel — confiance diminue si donnee pas validee depuis longtemps |
| Donnees statiques | Donnees vivantes — se mettent a jour automatiquement |
| Memoire passive | Memoire proactive — Spider suggere des actions basees sur ce qu'il sait |

## Put to other uses — Quels autres usages ?

| Usage principal | Usage alternatif |
|-----------------|------------------|
| Contexte pour l'IA | Analytics — comprendre les patterns (sujets recurrents, contacts actifs) |
| Memoire individuelle | **Memoire equipe** — partager le contexte entre collegues |
| Recherche interne | Formation — "comment on a gere ce type de situation avant ?" |
| Donnees brutes | **Coaching par module** — People (playbook), Chatbot (suggestions), etc. |

## Eliminate — Que peut-on supprimer du scope ?

| A eliminer | Pourquoi |
|------------|----------|
| Analytics avances au debut | MVP = memoire qui marche, analytics plus tard |
| Enrichissement externe (scrapping) | P2, pas MVP |
| Multi-tenant complexe des le debut | Commencer simple, robustifier ensuite |

## Reverse — Et si on faisait l'inverse ?

| Situation normale | Inversion | Insight |
|-------------------|-----------|---------|
| Spider extrait automatiquement | L'utilisateur saisit manuellement ? | Non, mais lui laisser la possibilite de corriger/ajouter |
| Memoire invisible | Memoire tres visible (Memory Dashboard) | La transparence rassure |
| Spider garde tout | Mode ephemere / "oublie cette conversation" | Donner le controle (dans les faits Spider garde quand meme, mais l'utilisateur se sent en controle) |
| Donnees partagees equipe par defaut | Donnees privees par defaut | Prive par defaut, partage explicite |

---

# Hypotheses Leap of Faith

## Hypotheses de VALEUR

| ID | Hypothese | Test |
|----|-----------|------|
| **HV1** | Les recherches semantiques cross-modules apportent une valeur unique | Usage feature > 20% des recherches |
| **HV2** | Le score de confiance evite les erreurs embarrassantes | Reduction incidents "mauvaise info" > 50% |
| **HV3** | La transparence (Memory Dashboard) rassure les utilisateurs | NPS utilisateurs avec dashboard > sans |
| **HV4** | Le systeme flashcards ameliore la qualite des donnees | Taux de donnees validees > 60% |

## Hypotheses de FAISABILITE

| ID | Hypothese | Test |
|----|-----------|------|
| **HF1** | On peut faire des recherches en millisecondes avec la vectorisation | Benchmark perf |
| **HF2** | L'extraction automatique est assez fiable pour etre utile | Score de precision > 80% |
| **HF3** | Le multi-tenant peut etre simple au debut et robustifie plus tard | Architecture evolutive validee |

## Hypotheses de VIABILITE

| ID | Hypothese | Test |
|----|-----------|------|
| **HB1** | Le cout Memory est absorbable dans le prix SpiderOS | < 10% du cout total infra |
| **HB2** | Le discours marketing "cerveau de Spider" fonctionne sans faire peur | Test messaging aupres de prospects |

---

# Key Insights

## Insight 1 : Le discours marketing est crucial

**Finding :** "Spider se souvient de tout" peut etre magique ou flippant selon comment on le presente.

**Implication :** Travailler le discours transparence/controle avant le lancement.

**Recommandation :** Page marketing qui rassure + Memory Dashboard des le MVP.

**Priorite :** Critique

---

## Insight 2 : La qualite des donnees est le plus gros risque

**Finding :** Si Spider dit "Marie a 3 enfants" alors qu'elle en a 2, perte de confiance totale.

**Implication :** Chaque info extraite doit avoir un score de confiance visible.

**Recommandation :** Score de confiance + systeme flashcards pour validation humaine.

**Priorite :** Critique

---

## Insight 3 : La transparence rassure

**Finding :** Les utilisateurs ont peur de perdre le controle sur leurs donnees.

**Implication :** Leur montrer exactement ce que Spider sait, leur permettre de corriger/supprimer.

**Recommandation :** Memory Dashboard avec vue complete, filtres, corrections, mode "oublie-moi".

**Priorite :** Haute

---

## Insight 4 : La memoire equipe est un differenciateur

**Finding :** Personne ne propose une memoire unifiee cross-modules partageable en equipe.

**Implication :** Le lock-in positif : plus tu utilises Spider, plus il te connait, plus tu restes.

**Recommandation :** Prive par defaut, partage explicite, mais la fonctionnalite equipe est cle.

**Priorite :** Haute

---

## Insight 5 : Memory alimente le coaching de chaque module

**Finding :** People (playbook), Chatbot (suggestions), Builder (contexte code) — tout depend de Memory.

**Implication :** Memory est vraiment le "cerveau" qui rend les autres modules intelligents.

**Recommandation :** Bien definir l'API Memory comme contract entre modules.

**Priorite :** Haute

---

# Statistics

| Metrique | Valeur |
|----------|--------|
| JTBD definis | 25+ (par module et axe) |
| Hypotheses leap of faith | 9 |
| Failure modes identifies | 16 |
| Key insights | 5 |
| Techniques appliquees | 4 |

---

# Progression Brainstorming

| Session | Status | Date |
|---------|--------|------|
| 1 - JTBD + Reverse | Done | 2026-01-14 |
| 2 - Starbursting | Done (valide interactivement) | 2026-01-14 |
| 3 - Six Hats | Done (valide interactivement) | 2026-01-14 |
| 4 - SCAMPER | Done (valide interactivement) | 2026-01-14 |

**Status: COMPLETE**

---

# Next Steps

| # | Etape | Qui |
|---|-------|-----|
| **1** | **Page marketing** — expliquer Spider Memory, le "cerveau de Spider", sans faire peur | Nathan |
| **2** | **UX Spider Memory** — maquetter le Memory Dashboard, flashcards, corrections | Nathan |
| **3** | **Recherches techniques** — vector DB, embeddings, chunking, architecture, perf | Remy |
| **4** | **Definir l'API Memory** — contract entre modules | Remy + Nathan |

---

# A Rechercher

- [ ] **Quelle techno vector DB ?** — LanceDB candidat, a valider
- [ ] **Quels embeddings ?** — A rechercher selon les besoins
- [ ] **Quelle granularite chunking ?** — A rechercher
- [ ] **Architecture multi-tenant ?** — Equilibre simplicite / robustesse
- [ ] **Hebergement cloud EU ?** — Scaleway ideal, a confirmer

---

*Generated by BMAD Method v6 - Creative Intelligence*
*Sessions 1-4 completees et validees interactivement le 2026-01-14*
