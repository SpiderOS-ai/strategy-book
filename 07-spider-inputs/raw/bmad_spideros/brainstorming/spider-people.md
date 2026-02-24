# Spider People — Document de Reference Consolide

**Module:** Spider People
**Priorite:** P0 — MVP
**Pricing:** 49EUR/user/mois
**Derniere mise a jour:** 2026-01-14

Ce document consolide le brainstorming valide (5 sessions) et les recherches effectuees.

---

# PARTIE 1: VISION ET POSITIONNEMENT

## Ce que Spider People EST

- Un CRM relationnel qui se remplit tout seul
- Une surcouche au CRM existant (qui peut le remplacer a terme)
- Le systeme qui comprend les gens en profondeur

## Ce que Spider People N'EST PAS

- Un CRM transactionnel (Salesforce, Hubspot)
- Un outil de saisie
- Un simple assistant

## Promesse

> **"Tu parles. Spider retient."**

## Philosophie

Les CRM sont transactionnels, mais la culture PME europeenne est relationnelle. Spider People epouse cette realite.

## Le Secret (vision Spider OS)

> "Les dirigeants PME veulent l'illusion du controle, pas le fardeau de la decision."

Spider People est le point d'entree du Shogunat digital:
- Le dirigeant garde le titre
- Spider gouverne progressivement

## Sequence d'infiltration

| Phase | Timing | Ce qui se passe |
|-------|--------|-----------------|
| **Capture** | Jours 1-3 | Se connecte a tout, aspire la data, le dirigeant ne fait rien |
| **Suggestion** | Semaine 1-2 | Suggere des actions, messages pre-rediges |
| **Decision** | Mois 1-2 | "J'ai prepare le message. Envoyer?" — Spider decide |
| **Controle** | Mois 2+ | Spider gere, le dirigeant ne sait plus faire sans |

---

# PARTIE 2: CIBLES ET PERSONAS

| Persona | Description | Priorite |
|---------|-------------|----------|
| **Dirigeant PME** | Fait du commercial lui-meme, TDAH, trop de bruit, pas le temps, culture de la petite attention | Principal (entry point) |
| **Commercial terrain** | Beaucoup de RDV, besoin de prep rapide, doit remplir le CRM, n'a pas le temps | Principal |
| **Manager commercial** | Veut voir ce que font ses equipes, coacher, sans demander | Secondaire |

## Le contexte Nathan

> "Moi je suis TDAH, j'essaie de creer un cadre qui donne de la clarte. J'ai la culture de la petite attention — je ne veux jamais oublier un anniversaire, jamais oublier une info. Je veux etre comme les meilleurs politiques du monde, le mec qui se souvient de ton prenom et de tes enfants apres 20 ans."

---

# PARTIE 3: JOBS-TO-BE-DONE

## Dirigeant PME

| # | JTBD |
|---|------|
| **1** | **Clarte dans le chaos** — "Quand je recois 80 mails/jour + WhatsApp + calls et que je suis deborde, je veux qu'un systeme trie et me dise ce qui est important, pour que je puisse repondre aux bonnes personnes sans tout lire." |
| **2** | **Ne jamais oublier quelqu'un** — "Quand je revois un contact apres plusieurs mois/annees, je veux avoir tout le contexte (derniers echanges, infos perso, ce qu'on s'est dit), pour que je puisse reprendre la relation comme si on s'etait vu hier." |
| **3** | **CRM sans effort** — "Quand je fais un call ou envoie un mail, je veux que mon pipeline se mette a jour automatiquement, pour que je voie ou en sont mes deals sans rien remplir." |
| **4** | **Brief avant RDV** — "Quand j'ai un RDV dans 30 min avec quelqu'un, je veux recevoir un resume de tout ce qu'on s'est dit avant, pour que j'arrive prepare sans fouiller dans mes mails." |
| **5** | **La petite attention** — "Quand c'est l'anniversaire d'un contact ou un evenement important pour lui, je veux etre prevenu avec un bon pretexte, pour que je puisse envoyer un message personnalise et entretenir la relation." |
| **6** | **Relance sans etre lourd** — "Quand une relation importante refroidit (pas de contact depuis X mois), je veux etre alerte avec un pretexte de reprise de contact, pour que je puisse relancer naturellement sans avoir l'air de sortir de nulle part." |

## Commercial terrain

| # | JTBD |
|---|------|
| **7** | **CRM auto-rempli** — "Quand je rentre de 5 RDV et que je dois tout saisir dans le CRM ce soir, je veux que ce soit deja fait automatiquement, pour rentrer chez moi au lieu de passer 1h sur Hubspot." |
| **8** | **Connaitre vraiment les gens** — "Quand je suis en RDV et que je veux poser LA question qui fait la difference, je veux savoir ce que je sais deja sur cette personne (ses enfants, ses passions, ses problemes), pour creer une vraie connexion." |
| **9** | **Coaching post-call** — "Quand je finis un call, je veux savoir ce que j'ai bien fait et ce que j'ai oublie, pour que je m'ameliore et que je sache quoi faire au prochain call." |

## Manager commercial

| # | JTBD |
|---|------|
| **10** | **Voir sans demander** — "Quand je veux savoir ou en sont mes commerciaux sans leur demander (et sans qu'ils mentent), je veux voir leur activite reelle et leurs deals en cours, pour coacher efficacement." |
| **11** | **Transfert de contexte** — "Quand un commercial quitte l'equipe, je veux recuperer tout son contexte relationnel, pour que le nouveau ne reparte pas de zero." |
| **12** | **Coaching auto** — "Quand mes commerciaux font des calls, je veux qu'ils recoivent du feedback automatique sur ce qu'ils ont bien fait / oublie, pour qu'ils progressent vers une vente consultative sans que je doive tout relire." |

## Meta-Job

> **"Je veux vendre plus, en passant moins de temps sur l'administratif et en ne jamais oublier personne ni rien."**

---

# PARTIE 4: RISQUES ET ANTI-PATTERNS

## Reverse Brainstorming: "Comment faire echouer Spider People?"

| # | Comment ca echoue | Insight (l'inverse) | Criticite |
|---|-------------------|---------------------|-----------|
| **1** | **L'IA se trompe tout le temps** — Elle dit que le prospect est chaud alors qu'il est froid, elle confond les enfants, etc. | La precision doit etre >80% sinon perte de confiance totale | CRITIQUE |
| **2** | **Trop de validations a faire** — L'utilisateur doit corriger 50 trucs par jour, c'est pire qu'un CRM | Valider doit etre rare et rapide (1 tap) | CRITIQUE |
| **3** | **Les insights sont superficiels** — "Marie a 2 enfants" OK, mais ca ne m'aide pas a vendre | Les insights doivent etre actionnables, pas juste informatifs — le scoring doit etre profond | CRITIQUE |
| **4** | **La capture ne marche pas** — WhatsApp se deconnecte, les calls ne sont pas transcrits, etc. | La capture doit etre invisible et fiable a 99% | SERIEUX |
| **5** | **Les commerciaux n'ont pas confiance** — "Mon boss voit tout ce que je fais, je me sens flic" | Positionner comme "ton assistant" pas "ton surveillant" | SERIEUX |
| **6** | **Les alertes sont chiantes** — "Souhaite l'anniversaire de Jean-Michel" tous les jours, ca devient du spam | Les alertes doivent etre rares et pertinentes | MOYEN |
| **7** | **C'est illegal** — Enregistrer sans consentement, RGPD, etc. | Etre clair sur la legalite, se dedouaner, etre best-in-class sur hebergement | MOYEN |
| **8** | **Le CRM existant n'est pas synchro** — Spider dit une chose, Hubspot une autre | Sync bi-directionnelle obligatoire | MOYEN |
| **9** | **Trop complique a setup** — Installer l'app Mac, l'app mobile, connecter Gmail, Aircall, WhatsApp... | Onboarding en 5 min max | MOYEN |
| **10** | **Ca ne marche que sur Mac** — 50% des commerciaux sont sur Windows | Windows = P1 mais critique pour scale | FAIBLE (P1) |

## Les 3 risques projet-killer

1. **L'IA se trompe** — Precision insuffisante = perte de confiance totale
2. **Trop de validations** — Friction excessive = abandon
3. **Insights superficiels** — Scoring pas assez profond = pas de valeur

---

# PARTIE 5: CONCEPTS CLES

## 1. La Toile

L'utilisateur voit sa **Toile** se construire en temps reel:
- Chaque contact = un point
- Chaque interaction = enrichit le point
- La Toile montre les relations, leur profondeur, leur fraicheur

## 2. Le Score de Connaissance

Pour chaque contact, un score de 0-100% (voir Partie 10 pour details complets).

**Wahoo moment:** "Je vois que je connais a peine mon 2eme plus gros client. Merde. Je dois creuser."

## 3. Le Playbook

Process de vente auto-detecte + capitalisation du savoir:
- Etapes du process (detectees puis validees)
- Questions qui marchent (avec exemples reels)
- Objections et reponses
- Patterns de timing
- Tout relie a la data (pas statique)

## 4. Le Score de Confiance

Chaque data a un score de confiance (0-100%):
- Si < seuil → demande de validation utilisateur
- UX fluide pour valider/corriger rapidement (1 tap)
- Ne pas bloquer l'utilisateur

---

# PARTIE 6: CLOISONNEMENT ET DROITS

| Niveau | Voit quoi |
|--------|-----------|
| Commercial | Ses contacts seulement (isole par defaut) |
| Manager | Tous les contacts de son equipe |
| Dirigeant | Tout |
| Contacts prives | Seul le proprietaire (ex: famille) |

**Logique de transfert:** Si un commercial part, son contexte peut etre transfere.

**RGPD:** Cloisonnement important pour limiter l'exposition des donnees.

---

# PARTIE 7: HYPOTHESES ET VALIDATION

## Hypotheses de VALEUR

| ID | Hypothese | Test |
|----|-----------|------|
| **HV1** | Les dirigeants PME veulent vraiment un CRM relationnel | Premier client payant hors Drakkar |
| **HV2** | L'automatisation ne tue pas l'authenticite | Interviews quali — utilisent-ils vraiment les suggestions? |
| **HV3** | Le tri intelligent des messages est un vrai pain | Discovery calls avec 5 prospects |
| **HV4** | Les dirigeants acceptent de donner leurs data | Taux de completion onboarding |
| **HV5** | Les dirigeants suivent les recommandations de l'IA | Taux d'action sur les suggestions |

## Hypotheses de FAISABILITE

| ID | Hypothese | Test |
|----|-----------|------|
| **HF1** | La capture automatique fonctionne techniquement | Drakkar utilise Spider People quotidiennement |
| **HF2** | Le scoring de data atteint >90% de fiabilite | Audit data apres 1 mois d'usage |
| **HF3** | Le scoring de profondeur est pertinent et actionnable | Feedback quali des users |
| **HF4** | iOS n'est pas un bloqueur (VoIP + fallback) | Taux d'usage mobile vs desktop |

## Hypotheses de VIABILITE

| ID | Hypothese | Test |
|----|-----------|------|
| **HB1** | Les PME paieront 49EUR/user/mois | 5 clients payants au meme prix |
| **HB2** | Le bouche-a-oreille Drakkar suffit pour demarrer | Pipeline de 20 prospects qualifies |

## Priorisation par risque

| Rang | Hypothese | Risque si faux |
|------|-----------|----------------|
| 1 | **HF2** — Scoring data >90% | Perte de confiance totale, produit inutilisable |
| 2 | **HV4** — Acceptent de donner leurs data | Pas d'onboarding, pas de produit |
| 3 | **HF3** — Scoring profondeur pertinent | Insights superficiels, pas de valeur |
| 4 | **HV1** — PME veulent CRM relationnel | Pas de marche |
| 5 | **HF1** — Capture fonctionne | Pas de produit |

---

# PARTIE 8: ROADMAP ET INTEGRATIONS

## Priorisation Plateformes

| Phase | Plateforme | Pourquoi |
|-------|------------|----------|
| **P0** | SaaS Web | Point d'entree, zero install, accessible partout |
| **P1** | Desktop Mac | Hub de capture (WhatsApp Web, iMessage, audio systeme) |
| **P2** | App Mobile | Commerciaux terrain, calls VoIP |

## Integrations

### V1 (MVP)

| Integration | Type | Priorite |
|-------------|------|----------|
| Gmail | Mail | P0 |
| Google Calendar | Calendar | P0 |
| Aircall / Noota | Calls + Transcription | P0 |
| WhatsApp (Mac) | Messages | P0 |
| Odoo | CRM sync | P0 |

### V1.5

| Integration | Type | Priorite |
|-------------|------|----------|
| iMessage (Mac) | Messages | P1 |

### V2+

| Integration | Type | Priorite |
|-------------|------|----------|
| Hubspot | CRM sync | P2 |
| Pipedrive | CRM sync | P2 |
| Signal, Telegram | Messages | P2 |

## Roadmap Features

### V1 — Capture + CRM Auto

| Feature | Wahoo moment |
|---------|--------------|
| Capture mail + calendar | — |
| Attribution auto | — |
| CRM auto-rempli | "Mon CRM est rempli, j'ai rien fait" |
| Inbox filtree | "5 trucs, pas 80" |
| Profil contact enrichi | "Je sais tout avant le call" |
| Score de connaissance | "Je vois qui je connais bien / mal" |
| Alertes oublis | "Spider m'a sauve un deal" |
| Message suggere (pas auto) | "1 clic pour relancer" |

### V1.5 — Suggestions

| Feature | Wahoo moment |
|---------|--------------|
| Reponse auto (mails simples) | "Spider a repondu pour moi" |
| Recos "qui contacter quand" | "Spider me dit qui appeler aujourd'hui" |
| Personnes oubliees (liste) | "Je vois tous mes angles morts" |
| WhatsApp capture | Plus de couverture |

### V2 — Coaching + Playbook

| Feature | Wahoo moment |
|---------|--------------|
| Coaching auto post-call | "Mon sales s'ameliore sans moi" |
| Playbook evolutif | "Le savoir se capitalise" |
| Graph reseau (Toile) | "Je vois mon capital relationnel" |
| Dashboard activite equipe | "Je vois tout sans demander" |

---

# PARTIE 9: ANALYSE CONCURRENTIELLE

## Vue d'ensemble

| Concurrent | Positionnement | Focus principal |
|------------|---------------|-----------------|
| **Folk** | CRM relationnel leger | PME, startups, networking |
| **Attio** | CRM customisable | RevOps, data-driven teams |
| **Clay** | Enrichissement + prospection | Outbound, data enrichment |
| **Affinity** | Relationship Intelligence | Private equity, dealmakers |
| **Gong/Chorus** | Conversation Intelligence | Enterprise sales teams |
| **Crystal Knows** | Personality AI | Sales enablement |

## Matrice comparative

| Feature | Spider People | Folk | Attio | Clay | Affinity |
|---------|--------------|------|-------|------|----------|
| **CRM auto-rempli** | Prevu | Partiel | Non | Non | Oui |
| **Capture multi-canal** | Prevu | LinkedIn, Mail | Mail | Non | Mail, Calendar |
| **Transcription calls** | Prevu | Non | Non | Non | Non |
| **Profilage psychologique** | Prevu | Non | Non | Non | Non |
| **Score de connaissance** | Prevu | Non | Non | Non | "Relationship Strength" |
| **Playbook evolutif** | Prevu | Non | Non | Non | Non |
| **Coaching post-call** | Prevu | Non | Non | Non | Non |
| **Inbox filtree** | Prevu | Non | Non | Non | Non |
| **WhatsApp capture** | Prevu | Oui | Non | Non | Non |

## Pricing

| Concurrent | Entry/user/mois |
|------------|-----------------|
| Folk | 17.50 EUR |
| Attio | 36 EUR |
| Hubspot Sales Starter | 45 EUR |
| **Spider People** | **49 EUR** |
| Pipedrive | 15-60 EUR |
| Clay | 134 USD/mois (credits) |
| Affinity/Gong | Enterprise (custom) |

## Gap strategique

**Le "CRM relationnel profond" n'existe pas encore.** Folk est le plus proche mais reste superficiel.

| Gap identifie | Opportunite Spider |
|---------------|-------------------|
| Profilage psychologique profond | DISC + Big Five + dimensions relationnelles |
| Capture calls + transcription | Aircall/Noota + transcription + extraction |
| Playbook evolutif | Questions qui marchent, objections, patterns |
| Coaching post-call auto | Democratiser Gong pour PME |
| Score de connaissance | Beaucoup plus profond qu'Affinity |
| Inbox filtree intelligente | Tri IA des messages importants |

---

# PARTIE 10: SCORE DE CONNAISSANCE

## Philosophie

> "Connaitre quelqu'un n'est pas une question de quantite d'information, mais de profondeur sur les dimensions qui comptent vraiment."

## Architecture a 4 niveaux

### Niveau 1: Surface (40%)
*Donnees observables et factuelles*

| Categorie | Elements | Source | Poids |
|-----------|----------|--------|-------|
| **Identite** | Nom, poste, entreprise, contact | Enrichissement | 10% |
| **Contexte pro** | Enjeux actuels, objectifs, budget | Conversations | 15% |
| **Infos perso** | Famille, passions, anniversaire | Conversations + enrichissement | 15% |

### Niveau 2: Comportement (25%)
*Patterns observables*

| Categorie | Elements | Source | Poids |
|-----------|----------|--------|-------|
| **Style personnalite** | DISC/MBTI/Big Five (au choix user) | Analyse texte/comportement | 10% |
| **Style decision** | Rapide/lent, rationnel/emotionnel | Historique interactions | 10% |
| **Preferences** | Canal, timing, formalite | Patterns d'interaction | 5% |

### Niveau 3: Motivations (20%)
*Drivers profonds*

| Categorie | Elements | Source | Poids |
|-----------|----------|--------|-------|
| **MICE adapte** | Money, Recognition, Security, Growth | Analyse conversations | 10% |
| **Valeurs** | Zone dominante (Schwartz) | Themes abordes | 5% |
| **Frustrations/echecs percus** | Ce que la personne veut compenser | Plaintes detectees | 5% |

### Niveau 4: Vulnerabilites et leviers (15%)
*Deep — pour relations strategiques*

| Categorie | Elements | Source | Poids |
|-----------|----------|--------|-------|
| **Peurs profondes** | Enneagramme si detecte | Detection patterns | 5% |
| **Levier d'influence** | Principe Cialdini dominant | Reponses passees | 5% |
| **Style attachement** | Secure/Anxious/Avoidant | Patterns relationnels | 5% |

## Formule

```
Score = (
  Surface_completude * 0.40 +
  Comportement_precision * 0.25 +
  Motivations_detection * 0.20 +
  Vulnerabilites_insight * 0.15
)
```

## Seuils

| Score | Niveau | Ce qu'on peut faire |
|-------|--------|---------------------|
| **0-25%** | Inconnu | Contact froid, approche generique |
| **25-50%** | Basique | Personnalisation limitee |
| **50-70%** | Connaissance | Personnalisation reelle |
| **70-85%** | Profonde | Anticipation des reactions |
| **85-100%** | Intime | Influence maximale |

## Affichage utilisateur: Multi-frameworks

Le score utilise Big Five en backend (scientifiquement valide), mais l'utilisateur peut choisir son affichage:

| Framework | Description | Pourquoi l'offrir |
|-----------|-------------|-------------------|
| **DISC** | 4 types (D/I/S/C) | Simple, connu en vente |
| **MBTI** | 16 types (INTJ, ENFP...) | Populaire, gamifiable |
| **Big Five** | 5 dimensions continues | Scientifique |
| **Gallup** | 34 forces | Connu en RH |

**Principe:** Backend scientifique (Big Five) + Frontend au choix (gamification).

---

# PARTIE 11: FRAMEWORKS DE PERSONNALITE

## DISC (William Moulton Marston, 1928)

| Dimension | Description | Application vente |
|-----------|-------------|-------------------|
| **D - Dominance** | Leadership, assertivite, resultats | Decision rapide, veut le controle |
| **I - Influence** | Persuasion, enthousiasme, social | Aime les relations, sensible a la reconnaissance |
| **S - Steadiness** | Fiabilite, stabilite, support | Prend son temps, valorise la securite |
| **C - Conscientiousness** | Detail, precision, analyse | Veut des faits, des preuves |

**Precision Crystal Knows:** ~85% IA seule, ~95% avec questionnaire

### Detection via texte

| DISC | Indicateurs |
|------|-------------|
| **D** | Messages courts, directs, peu de small talk |
| **I** | Messages longs, emojis, anecdotes |
| **S** | Reponses mesurees, evite conflits |
| **C** | Questions detaillees, demande donnees |

## Big Five / OCEAN (Standard scientifique)

| Dimension | Description | Impact |
|-----------|-------------|--------|
| **O - Openness** | Creativite, curiosite | Receptif aux nouvelles idees |
| **C - Conscientiousness** | Organisation, fiabilite | Meilleur predicteur performance |
| **E - Extraversion** | Energie sociale | Predicteur leadership |
| **A - Agreeableness** | Cooperation, empathie | Relations stables |
| **N - Neuroticism** | Instabilite emotionnelle | Predicteur negatif satisfaction |

## Enneagramme (Niveau avance - V2)

| Type | Peur fondamentale | Desir fondamental |
|------|-------------------|-------------------|
| **1** Perfectionniste | Etre mauvais | Etre integre |
| **2** Aide | Etre non-aime | Etre apprecie |
| **3** Performeur | Etre sans valeur | Etre admire |
| **4** Individualiste | Etre ordinaire | Etre unique |
| **5** Investigateur | Etre incompetent | Etre competent |
| **6** Loyaliste | Etre seul | Avoir securite |
| **7** Enthousiaste | Etre piege | Etre libre |
| **8** Challenger | Etre vulnerable | Etre en controle |
| **9** Pacificateur | Perte de connexion | Etre en paix |

**Principe:** Declencher la peur ferme la personne. Parler au desir l'ouvre.

---

# PARTIE 12: TECHNIQUES D'INFLUENCE

## Framework MICE (CIA)

| Dimension | Description | Detection |
|-----------|-------------|-----------|
| **M - Money** | Besoin financier | Stress financier, niveau de vie |
| **I - Ideology** | Croyances, valeurs | Frustrations, "ca devrait pas etre comme ca" |
| **C - Coercion** | Vulnerabilites | Secrets, erreurs passees |
| **E - Ego** | Besoin de reconnaissance | "Ils ne voient pas ma valeur" |

**Insight cle (Dr. Charney):**
> "La vraie motivation = compenser un echec percu. L'argent, l'ideologie sont des facilitateurs pour recouvrer l'estime de soi."

## 7 Principes de Cialdini

| Principe | Description | Quand utiliser |
|----------|-------------|----------------|
| **Reciprocity** | On doit rendre ce qu'on recoit | Donner en premier |
| **Commitment** | On reste coherent | Obtenir petits "oui" |
| **Social Proof** | On suit les similaires | "X% ont choisi..." |
| **Authority** | On suit les experts | Montrer credentials |
| **Liking** | On dit oui a ceux qu'on aime | Similitudes, compliments |
| **Scarcity** | On veut ce qui est rare | "Plus que 3 places" |
| **Unity** | On favorise l'in-group | Creer appartenance |

### Sensibilite par profil

| Profil | Principes dominants |
|--------|---------------------|
| Anxieux | Social Proof + Authority |
| Narcissique | Scarcity + Liking |
| Analytique | Authority + Commitment |

## Styles d'attachement

| Style | % population | Caracteristiques | Implication contact |
|-------|--------------|------------------|---------------------|
| **Secure** | 56% | Confort intimite | Contact normal |
| **Anxious** | 19% | Peur abandon | Besoin reassurance frequente |
| **Avoidant** | 25% | Independance | Espacer les contacts |

---

# PARTIE 13: ASPECTS TECHNIQUES

## Transcription — Etat de l'art

| Outil | WER | Usage recommande |
|-------|-----|------------------|
| **Deepgram Nova-3** | ~5.8% | Temps reel (streaming) |
| **Whisper large-v3** | 2-5% | Batch processing |
| **Conditions reelles** | 7-15% | Prevoir marge |

## Extraction LLM

| Type d'extraction | Accuracy attendue |
|-------------------|-------------------|
| Entites nommees (noms, entreprises) | >90% |
| Dates, lieux | >90% |
| Infos personnelles (enfants, passions) | ~80% |
| Sentiment | ~85% |
| Promesses, engagements | ~70% |
| Profil psychologique | ~80% (avec assez de texte) |

## Enrichissement externe

| Outil | Accuracy | Notes |
|-------|----------|-------|
| Clearbit | ~95% | Premium |
| Cognism | 98% (tel) | Fort sur EU |
| Apollo | 85-90% | Budget-friendly |

## Strategie fiabilite >90%

1. **Multi-sources + triangulation** — Si LinkedIn + Mail + Enrichissement concordent → confiance haute
2. **Score de confiance par data** — >90% auto-valide, 70-90% flag, <70% validation swipe
3. **Validation UX Tinder** — 1 tap, max 5-10/jour
4. **Feedback loop** — User valide → modele s'ameliore

---

# PARTIE 14: MARCHE PME FRANCE

## Taille

| Metrique | Valeur |
|----------|--------|
| Marche CRM France 2025 | 3.2 Mrd EUR |
| Croissance annuelle | 11.5% |
| PME France | ~4 millions |
| PME equipees CRM | >70% |
| **Taux d'usage reel** | **30-40%** |

## Opportunite

Le vrai probleme n'est pas l'equipement mais l'usage. Cause principale: **saisie manuelle**.

Spider People resout ce probleme.

## Tendances

- Cloud dominant (74%)
- Mobile en croissance (>50% commerciaux)
- IA integration (50% organisations)

---

# PARTIE 15: KEY INSIGHTS

## Insight 1: La capture n'est pas le produit

La capture est un moyen, pas la valeur. La valeur c'est:
- Les fiches contacts qui se remplissent seules
- Les insights actionnables
- Le playbook qui se capitalise
- Les suggestions pre-redigees

**Action:** Dans le messaging, focus sur la valeur, pas sur "on capture tout".

## Insight 2: Le scoring de profondeur est le vrai differenciateur

Si le scoring est superficiel ("Marie a 2 enfants"), pas de valeur. Si le scoring est profond (traits de caractere, motivations, timing optimal), c'est game-changer.

**Action:** Investir sur la profondeur du score.

## Insight 3: La validation est le point de friction majeur

Dilemme precision vs friction. Solution:
- Score de confiance visible
- Validation uniquement sur donnees incertaines
- UX swipe (1 tap)

## Insight 4: L'objectif ultime = ne plus ouvrir Gmail/WhatsApp

Spider People n'est pas juste un CRM enrichi, c'est une nouvelle facon de gerer ses communications.

**Action:** Designer l'UX pour que l'utilisateur reste dans Spider.

## Insight 5: Le playbook est sous-exploite

Ce n'est pas juste du coaching ponctuel, c'est la capitalisation du savoir commercial de l'entreprise.

**Action:** Mettre le playbook en avant dans le messaging V2.

## Insight 6: Le cloisonnement est critique pour l'adoption

Les commerciaux ont peur que le boss voit tout.

**Action:** Par defaut isole. Communiquer "ton assistant, pas ton surveillant".

## Insight 7: La motivation profonde > les traits de surface

(Recherche) Dr. Charney montre que la vraie question est: "Quel echec percu cette personne cherche-t-elle a compenser?"

**Action:** Detecter frustrations et deceptions, pas juste traits.

## Insight 8: Aucun concurrent ne fait du "relationnel profond"

(Recherche) Folk = leger, Attio = database, Clay = enrichissement. Gap strategique pour Spider People.

**Action:** Creer la categorie "CRM relationnel profond".

---

# PARTIE 16: FEATURES VALIDEES

## Features Green Hat (brainstorming)

| Feature | Description | Priorite |
|---------|-------------|----------|
| **Ghost Mode** | Contacts prives (famille, perso) | Critique |
| **Validation Tinder swipe** | Enrichir/valider data en mode swipe | Haute |
| **Voice Notes → Insights** | Note vocale → data structuree | Critique (fallback iOS) |
| **Deal Doctor** | Comprendre pourquoi perdu/gagne | Haute |
| **Intro Bot** | Detection connexions utiles | Moyenne |
| **Competitor Radar** | Detection mentions concurrents | Moyenne |
| **AI Twin** | Clone IA pour taches simples | Future |

## Wahoo Moments V1

| # | Moment | Feature | Emotion |
|---|--------|---------|---------|
| **1** | "5 trucs, pas 80. Je respire." | Inbox filtree | Clarte |
| **2** | "Mon CRM est rempli. J'ai rien fait." | CRM auto | Magie |
| **3** | "Je sais tout avant le call." | Profil enrichi | Impeccable |
| **4** | "Je vois qui je connais bien / mal." | Score connaissance | Lucidite |
| **5** | "Spider m'a sauve un deal." | Alertes oublis | Sauve |
| **6** | "Message pret, 1 clic, envoye." | Suggestion pre-redigee | Efficacite |

---

# PARTIE 17: STARBURSTING

## WHO — Qui?

| Question | Reponse |
|----------|---------|
| Qui utilise? | Dirigeant PME, commercial terrain, manager |
| Qui sont les contacts? | Prospects, clients, partenaires, investisseurs, amis, famille |
| Qui voit les donnees? | Cloisonnement par defaut |
| Qui paie? | Le dirigeant (49EUR/user/mois) |

## WHAT — Quoi?

| Question | Reponse |
|----------|---------|
| Qu'est-ce qu'on capture? | Calls, mails, messages (WhatsApp, iMessage, Signal, Telegram), calendar |
| Qu'est-ce qu'on extrait? | Insights, promesses, dates, sentiment, profil psy, process de vente |
| Qu'est-ce qu'on ne fait PAS en P0? | Execution automatique (suggestions seulement) |

## WHERE — Ou?

| Question | Reponse |
|----------|---------|
| Ou tourne Spider People? | SaaS (web) + Desktop Mac + Mobile |
| Ou sont stockees les donnees? | Cloud |
| Ou l'utilisateur consulte? | Dans Spider principalement |

## WHEN — Quand?

| Question | Reponse |
|----------|---------|
| Quand Spider capture? | En continu (background) |
| Quand alerter contact qui refroidit? | Configurable (defaut: VIP=1 mois, Important=3 mois, Normal=1 an) |
| Quand demander validation? | Quand confiance < seuil |
| Quand le commercial voit la valeur? | < 1 semaine |

## WHY — Pourquoi?

| Question | Reponse |
|----------|---------|
| Pourquoi Spider People et pas un CRM? | CRM = transactionnel, Spider = relationnel. Zero saisie. |
| Pourquoi maintenant? | L'IA permet enfin d'extraire des insights automatiquement |

## HOW — Comment?

| Question | Reponse |
|----------|---------|
| Comment on capture sans friction? | Desktop Mac = auto, Mobile = VoIP ou note vocale |
| Comment on sync avec le CRM existant? | API bi-directionnelle (Odoo, Hubspot, Pipedrive) |
| Comment on gere la privacy? | Disclaimer + hebergement best-in-class |

---

# PARTIE 18: SIX HATS ANALYSIS

## WHITE HAT — Faits

- Marche CRM global: ~65 milliards $ (2024)
- ~4 millions de PME en France, 80% n'utilisent pas de CRM ou utilisent Excel
- Taux d'adoption CRM chez commerciaux: 30-40% (frein: saisie manuelle)
- Transcription IA mature (Whisper, Deepgram)
- Apple limite l'acces aux calls (workarounds: VoIP, note vocale)

## RED HAT — Emotions

| Persona | Positive | Negative |
|---------|----------|----------|
| Dirigeant | "Enfin quelqu'un qui comprend les relations!" | "Est-ce que ca va marcher?" "Peur data" |
| Commercial | "Plus jamais remplir le CRM!" | "Mon boss voit tout" "Et si l'IA dit des conneries?" |
| Manager | "Je vais enfin voir ce qui se passe" | "Les commerciaux vont mal le prendre" |

## BLACK HAT — Risques

| Risque | Probabilite | Impact | Mitigation |
|--------|-------------|--------|------------|
| Precision IA insuffisante | Moyenne | Critique | Seuil confiance, validation ciblee |
| Fuite de donnees | Faible | Critique | Hebergement France, chiffrement |
| Adoption commerciaux faible | Moyenne | Haute | Positioning "assistant", cloisonnement |
| PME ne paient pas 49EUR | Moyenne | Critique | Validation pricing rapide |

## YELLOW HAT — Benefices

| Benefice | Pour qui | Impact |
|----------|----------|--------|
| Fin saisie CRM | Commercial | +1-2h/jour |
| Memoire parfaite | Tous | Ne jamais oublier |
| Brief avant RDV | Commercial | +20% closing |
| Capitalisation savoir | Entreprise | Playbook survit aux departs |

## GREEN HAT — Creativite

- Ghost Mode (contacts prives)
- Validation Tinder swipe
- Voice Notes → Insights
- Deal Doctor
- AI Twin (vision)

## BLUE HAT — Process

**Confirmations strategiques:**
- Profondeur du profil = differenciateur majeur
- Validite data = critique
- Tout capturer = max de data
- Contact = tout le monde (reseau perso, famille, amis)
- Voix > clavier

---

# PARTIE 19: SCAMPER

## Substitute

| Element actuel | Substitution |
|----------------|--------------|
| Saisie manuelle CRM | Capture automatique |
| Scoring statique | Score dynamique |
| Playbook PDF | Playbook vivant |
| CRM comme source | Spider comme source |

## Combine

| Combinaison | Resultat |
|-------------|----------|
| CRM + Inbox | Hub unifie |
| Playbook + Coaching | Apprentissage contextuel |
| Note vocale + Transcription + Extraction | Parle → Spider structure |

## Adapt

| Source | Adaptation |
|--------|------------|
| Tinder | Validation swipe |
| Spotify Discover | "Contacts a decouvrir cette semaine" |
| LinkedIn | Toile relationnelle |
| Politiciens | Memoire parfaite |
| CIA/renseignement | Profilage profond |

## Modify / Magnify

- Profondeur du profil (au-dela DISC: valeurs, peurs, motivations)
- Validite de la data
- Couverture capture (tout)
- Scope contact (pro + perso + famille)

## Eliminate

- Saisie manuelle
- Formation initiale longue
- Multi-apps

## Reverse

| Paradigme actuel | Inversion |
|------------------|-----------|
| L'humain alimente le CRM | Le CRM alimente l'humain |
| Formation puis action | Action puis feedback |
| Le manager demande | Le manager voit sans demander |

---

# PARTIE 20: NEXT STEPS

1. **PRD Spider People** — `/prd` pour specs detaillees
2. **Architecture** — `/architecture` pour design technique
3. **Prototype Score de Connaissance** — Valider le framework avec utilisateurs test
4. **Discovery calls** — Valider pricing 49EUR et douleur saisie manuelle

---

# PROGRESSION

## Brainstorming

| Session | Status | Date |
|---------|--------|------|
| 1 - JTBD + Reverse | Done | 2026-01-13 |
| 2 - Starbursting | Done | 2026-01-13 |
| 3 - Six Hats | Done | 2026-01-13 |
| 4 - SCAMPER | Done | 2026-01-13 |
| 5 - SWOT | Done | 2026-01-13 |

## Recherches

| Topic | Status | Date |
|-------|--------|------|
| Score de connaissance | Done | 2026-01-14 |
| Fiabilite data | Done | 2026-01-14 |
| Concurrence | Done | 2026-01-14 |
| Marche PME France | Done | 2026-01-14 |
| Techniques CIA/FBI/Psy | Done | 2026-01-14 |

**Status: BRAINSTORMING + RECHERCHES COMPLETE**

---

# SOURCES

## Personnalite / Profilage
- DiSC Profile - How DiSC Works
- Crystal Knows - How Predictions Work (~85% accuracy)
- Humantic AI - 36 types personnalite
- Wikipedia - Big Five Personality Traits
- Wikipedia - Personality Assessment System (Gittinger/CIA)

## Intelligence
- MICE Framework - CIA Spy Recruitment
- From MICE to RASCLS (Burkett, 2013)
- Psychology of Espionage - NOIR (Dr. Charney)
- Jerrold Post - Political Leaders
- FBI Behavioral Analysis Unit

## Influence
- Cialdini's 7 Principles of Persuasion
- Kahneman - Cognitive Biases
- Enneagram Core Motivations/Fears
- Attachment Styles - Cleveland Clinic

## Concurrence
- Folk vs Attio Comparison
- Clay Alternatives
- Affinity Platform
- Gong vs Chorus Comparison

## Technique
- Deepgram - Speech-to-Text Benchmarks
- Whisper vs Deepgram 2025
- UniversalNER - NER Comparison

## Marche
- Moovago - Statistiques CRM 2025
- Apogea - Marche CRM 2026
- Bitrix24 - Tendances CRM France

## Data Enrichment
- Clearbit (~95% accuracy)
- Cognism (98% tel verifies)
- Apollo (85-90%)

---

*Document consolide depuis: brainstorming (5 sessions) + recherches (2 phases)*
*Derniere mise a jour: 2026-01-14*
*Generated by BMAD Method v6*
