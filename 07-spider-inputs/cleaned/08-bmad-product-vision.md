# 08 -- Vision produit BMAD : modules fonctionnels SpiderOS

## Metadata

| Champ | Valeur |
|-------|--------|
| **Auteur** | Nathan Menard (via methodologie BMAD) |
| **Date** | ~Janvier 2026 (product-brief du 15 janvier, PRD du 18 janvier) |
| **Nature** | Vision produit initiale pour les modules SpiderOS |
| **Fiabilite** | FONCTIONNELLEMENT VALIDE -- Nathan confirme que les modules n'ont pas trop bouge dans leur scope fonctionnel. MAIS le business model est obsolete (pre-date le pivot Service-as-Software). |
| **Insight cle de Nathan** | "Sur des questions de business model etc oui [c'est obsolete]. En revanche, les modules n'ont pas trop bouge dans leur scope fonctionnel." |
| **Strategie chevaux de Troie** | Nathan dit : "des choses comme Spider People ou LLM qui donne acces sont des points d'entree faciles dans les PME qui ne savent pas que ces outils existent (et donc on commence a prendre leur data). Peut-etre meme qu'il faudra les rendre gratuits ou payable a l'usage." |
| **Sources fusionnees** | `product-brief.md` (15 jan 2026) + `prd-spideros-2026-01-18.md` (18 jan 2026) |

---

## AVERTISSEMENT : CE QUI EST OBSOLETE

Les elements suivants du product-brief sont depasses par le pivot Service-as-Software et doivent etre ignores pour la strategie actuelle :

- **Pricing 49 EUR/user/mois** -- obsolete. Le modele se dirige vers Service-as-Software (vendre le resultat, pas l'outil).
- **ARR 100K EUR Year 1** -- metrique SaaS classique, ne reflete plus la strategie.
- **Credits (modele Lovable-style)** pour Builder et Content -- a reevaluer dans le nouveau modele.
- **"Pas un SaaS"** etait deja dans le brief, mais le business model restait SaaS. Le pivot va plus loin.

Ce qui RESTE valide : le scope fonctionnel des modules, les specs techniques, les user personas, les user flows, et la vision strategique globale.

---

## 1. Pitch

L'IA ne voit pas votre entreprise. Vos vraies donnees sont eparpillees : mails, fichiers, tetes des equipes. SpiderOS tisse une toile par-dessus -- sans migration. L'IA voit enfin. Des modules s'y branchent pour automatiser : standards ou sur mesure.

**Ce que SpiderOS fait :**
1. Se connecte a tout automatiquement (mail, telephone, fichiers, apps)
2. Detecte et agrege la data eparpillee
3. Tisse une toile entre toutes les sources
4. Permet des automatisations par-dessus

**Ce que SpiderOS n'est PAS :**
- Pas un CRM (c'est une couche par-dessus)
- Pas un ERP (on ne remplace rien)
- Pas un outil de plus a adopter (on s'adapte a l'existant)

---

## 2. Cible

### PME europeennes

| Critere | Valeur |
|---------|--------|
| CA | 2M-50M EUR |
| Effectif | 20-500 personnes |
| Secteur | Industrie principalement, services B2B |
| Geo | Europe (France d'abord) |

### Profil du dirigeant cible

- Bon en relationnel, moins bon en gestion
- Culture "pompier" (reactif, pas proactif)
- Ne veut pas changer ses outils
- Veut le controle percu, pas le controle reel

### Jobs-to-be-Done

| # | Job |
|---|-----|
| 1 | **Voir ma boite** -- Comprendre enfin ce qui se passe sans tout centraliser |
| 2 | **Sans effort** -- Ne rien changer a mes habitudes |
| 3 | **Agir** -- Automatiser ce qui peut l'etre |
| 4 | **Garder le controle** -- Rester "aux commandes" (meme si l'IA suggere) |

---

## 3. Modules -- Scope fonctionnel

### 3.1 Spider Memory (P0 -- Infrastructure)

**Role :** Le cerveau de SpiderOS -- moteur de vectorisation et memoire.

C'est une brique technique interne, pas un produit utilisateur. Tout depend de Memory : recherches semantiques, contexte IA, extraction.

**Specs fonctionnelles cles :**
- Stockage vectoriel massif (10+ ans d'historique email par tenant)
- Recherche semantique < 500ms pour 95% des requetes
- API interne pour tous les modules (index, search, delete)
- Score de confiance par donnee (0-100%), visible dans l'UI, avec decay temporel
- Extraction automatique : entites nommees, dates, promesses, engagements, infos personnelles
- Systeme de validation flashcards (swipe, max 5-10/jour)
- Memory Dashboard (transparence, edition inline)
- Mode "oublie-moi" (RGPD, suppression < 30 jours)

**Risque principal :** Qualite des donnees. Si l'extraction est fausse, perte de confiance totale.

### 3.2 Spider People (P0 -- Module phare) [CHEVAL DE TROIE]

**Role :** CRM relationnel qui se remplit tout seul.

**Promesse :** "Tu parles. Spider retient."

> **Note strategique :** Spider People est identifie par Nathan comme un "cheval de Troie" -- un point d'entree facile dans les PME qui ne savent pas que ces outils existent. L'objectif reel est de commencer a capturer leur data. Nathan envisage de le rendre gratuit ou payable a l'usage pour maximiser la penetration.

**Concepts cles :**
- **La Toile** -- visualisation relationnelle
- **Score de Connaissance** -- 0-100%, sur 4 niveaux : Surface, Comportement, Motivations, Vulnerabilites
- **Playbook** -- process de vente auto-detecte depuis l'analyse des deals
- **Profil psychologique** -- DISC, Big Five, MBTI depuis l'analyse des conversations (~80% precision)

**Specs fonctionnelles cles :**

*Capture automatique :*
- Emails (Gmail OAuth, sync initiale configurable 1-5 ans-tout, sync incrementale temps reel)
- Calls (Aircall API + Noota API, transcriptions, association auto au contact)
- Calendrier (Google Calendar OAuth, detection participants)
- WhatsApp (via app desktop Mac, P1)

*Intelligence relationnelle :*
- Attribution automatique aux contacts (matching email/telephone/alias, precision > 90%)
- Creation automatique de fiches contacts (detection, enrichissement, pas de doublons)
- Brief avant RDV (notification push 30min/1h avant, resume < 3s, derniers echanges + infos cles + suggestions)
- Inbox filtree intelligente (priorisation VIP/deals/urgence, vue "A traiter" avec les 5-10 priorites)
- Messages suggeres pre-rediges (ton adapte au contact, edition avant envoi, envoi en 1 clic)
- Alertes contacts qui refroidissent (seuils configurables par priorite)
- Alertes anniversaires et evenements

*Gestion droits :*
- Cloisonnement par role (Commercial/Manager/Dirigeant)
- Mode Ghost (contacts prives, invisibles meme pour un manager)

*Coaching :*
- Playbook auto-detecte (etapes recurrentes, questions efficaces, objections)
- Coaching post-call (feedback automatique vs playbook)
- Dashboard activite equipe (vue aggregee pour managers)

**~~Pricing : 49 EUR/user/mois~~** [OBSOLETE]

### 3.3 Spider Builder (P0)

**Role :** AI coding assistant avec methodologie integree.

**Promesse :** Cadre qui empeche les projets vibe coding de partir en vrille.

**Differenciateur :** BMAD++ integre -- le seul AI coding avec contexte methodologique automatique.

**Architecture :** Proxy localhost qui enrichit les prompts avec PRD, archi, design system, user stories.

**Specs fonctionnelles cles :**
- Wizard onboarding projet (questions objectifs, contraintes, design)
- Generation PRD automatique (BMAD, Markdown, editable, versionne)
- Generation architecture technique automatique
- Stack Selector (librairies approuvees, verrouillage versions, alerte si lib non approuvee)
- Rules Config (conventions, patterns, interdictions, templates par type de projet)
- Stack Guard (detection a la generation, alerte, suggestion d'alternative)
- Design System Guard (verification composants, couleurs, styles)
- Loop Detection (detection patterns repetitifs, alerte apres N iterations)
- US Auto-Link (code genere lie aux user stories)
- Progress Tracking automatique (avancement US/epics/sprints)
- Agent Visibility (quels agents interviennent et pourquoi)

**~~Pricing : Credits (modele Lovable-style)~~** [OBSOLETE]

### 3.4 Spider Content (P0 -- Techno existante)

**Role :** Generation de contenu IA (photo, video, mascotte).

**Avantage :** Reverse engineering credits IA = 50-70% moins cher que concurrents.

**Differenciateur :** "Comprend votre marque" (pas juste extraction brand kit) -- catalogue e-commerce, cible, univers graphique.

**Status :** Technologie deja developpee par Remy.

**Specs fonctionnelles cles :**
- Generation photos produit (upload, variantes fond/angle/style, qualite pro, export haute resolution)
- Generation videos UGC avec avatars IA (multi-langues, export formats reseaux sociaux)
- Systeme Brand Kit (extraction depuis URL ou upload, application automatique aux generations)
- Extraction catalogue e-commerce (crawl pages produit, images/titres/descriptions)
- Multi-langues (FR, EN, ES, DE minimum)
- Animation mascotte/personnage fictif (lip-sync, expressions configurables)
- Templates prets a l'emploi (bibliotheque par categorie)

**~~Pricing : Credits (modele Lovable-style)~~** [OBSOLETE]

### 3.5 Spider Documents (P1 -- initialement sous-module de People)

**Role :** Generation automatique de presentations et notes strategiques.

**Promesse :** "Tu parles. Spider livre."

**Specs fonctionnelles cles :**
- Notes strategiques (~15-20 pages)
- Slides de presentation
- S'appuie sur People (contexte client) + Content (design, brand voice)
- Format web only (pas de telechargement) -- tracking + mise a jour

### 3.6 Spider Chatbot (P1) [CHEVAL DE TROIE]

**Role :** Interface LLM unifiee branchee sur les donnees SpiderOS.

**Promesse :** Un seul chat pour tous les LLM, avec ton contexte.

> **Note strategique :** Le Chatbot est egalement un cheval de Troie potentiel. Nathan le decrit comme un "LLM qui donne acces" -- un point d'entree facile pour les PME. En leur donnant acces a un chatbot IA avec leur contexte injecte, on commence a capturer leur data.

**Differenciateur :** Contexte Spider injecte automatiquement (clients, projets, docs).

**MVP :** Fevrier 2026 interne Drakkar, Q2 2026 externe.

### 3.7 Modules futurs (Backlog P2+)

| Module | Description | Timing |
|--------|-------------|--------|
| Spider RH | Management collaborateurs | Q3 2026 |
| Spider Project | Gestion de projet | Backlog |
| Spider Training | Formation | Backlog |
| Spider Data/Analytics | Intelligence business | Backlog |
| Spider Sales | Pipeline avance | Backlog |

---

## 4. Integrations P0

| Integration | Type | Priorite |
|-------------|------|----------|
| Gmail | OAuth 2.0, sync initiale configurable, sync incrementale temps reel | Must Have |
| Google Calendar | OAuth 2.0, sync bidirectionnelle, detection participants | Must Have |
| Aircall | API, historique calls, transcriptions, webhooks temps reel | Must Have |
| Noota | API, transcriptions meetings, association contacts | Must Have |
| Odoo | API, sync bidirectionnelle contacts/deals/notes, mapping configurable | Should Have |
| Extension Chrome | Capture LinkedIn, enrichissement contacts | Should Have |

---

## 5. User Personas

### Dirigeant PME (Principal)

| Dimension | Description |
|-----------|-------------|
| Profil | CEO/fondateur de PME, 2-50M EUR CA, 20-200 employes |
| Comportement | Bon en relationnel, culture "pompier", TDAH frequent |
| Douleur | 80 mails/jour, oublie des contacts importants, CRM vide |
| Objectif | "Voir ma boite" sans rien changer a ses habitudes |
| Citation | "Je veux etre comme les meilleurs politiques, le mec qui se souvient de ton prenom apres 20 ans." |

### Commercial Terrain

| Dimension | Description |
|-----------|-------------|
| Profil | Commercial dans PME, 5+ RDV/semaine |
| Douleur | Doit remplir le CRM le soir, oublie des infos |
| Objectif | CRM rempli automatiquement, briefing avant RDV |
| Citation | "Je veux rentrer chez moi au lieu de passer 1h sur Hubspot." |

### Manager Commercial

| Dimension | Description |
|-----------|-------------|
| Profil | Responsable equipe commerciale 5-20 personnes |
| Douleur | Ne sait pas ce que font ses commerciaux sans demander |
| Objectif | Voir l'activite sans demander, coacher avec data |
| Citation | "Je veux que mes commerciaux progressent sans que je doive tout relire." |

### Developpeur (Spider Builder)

| Dimension | Description |
|-----------|-------------|
| Profil | Dev ou CTO utilisant l'IA pour coder |
| Douleur | Projets qui partent en vrille, dette technique invisible |
| Objectif | Cadre qui empeche les derives sans ralentir |
| Citation | "Faut pas se leurrer, quand on fait du vibe coding, les gens ne lisent pas le code." |

### Equipe Marketing PME (Spider Content)

| Dimension | Description |
|-----------|-------------|
| Profil | CM seul ou petite equipe, multi-reseaux |
| Douleur | Shootings chers, videos impossibles sans equipe |
| Objectif | Generer du contenu pro a cout reduit |
| Citation | "J'ai besoin de 20 visuels mais pas de budget photographe." |

---

## 6. User Flows cles

### Flow 1 : Onboarding Spider People

1. Signup (email/OAuth)
2. Connexion Gmail
3. Connexion Google Calendar
4. Connexion Aircall/Noota
5. Sync initiale (background)
6. Premier contact enrichi visible
7. Wahoo moment : "Mon CRM est rempli !"

Cible : completion < 10 minutes. Taux de completion > 70%.

### Flow 2 : Brief avant RDV

1. RDV dans 30 min (detection calendrier)
2. Notification push
3. Click -> Brief affiche (< 3 secondes)
4. Resume derniers echanges + infos cles + suggestions
5. Utilisateur prepare en 2 min

### Flow 3 : Message suggere

1. Email recu d'un contact
2. Spider analyse le contexte
3. Suggestion de reponse affichee
4. Utilisateur edite si besoin
5. Envoi en 1 clic

---

## 7. Exigences non-fonctionnelles cles

| Domaine | Exigence |
|---------|----------|
| Performance | Recherche semantique < 500ms (95%). Brief avant RDV < 3s. LCP < 2s. TTI < 3s. |
| Precision IA | Extraction entites > 80%. Extraction promesses > 70%. Profil psychologique ~80%. Attribution contacts > 90%. |
| Disponibilite | Uptime 99.5% (hors maintenance planifiee hors heures ouvrables EU) |
| Securite | Hebergement France (OVH/Scaleway). TLS 1.3 + AES-256. Pas de transfert hors UE. |
| RGPD | Consentement explicite a l'onboarding. Droit a l'oubli < 30 jours. Memory Dashboard transparent. |
| Scalabilite | 10+ ans d'historique email par tenant. 50 000 contacts par tenant. 100 utilisateurs simultanes par tenant. |
| Usabilite | Zero formation requise. UX auto-explicative. Max 5-10 validations flashcards par jour. |

---

## 8. Risques identifies

| Risque | Probabilite | Impact |
|--------|-------------|--------|
| Qualite du pipeline data (extraction, correlation, consolidation) | High | High |
| La toile ne fonctionne pas (impossible de connecter toute la data) | Medium | High |
| Adoption dirigeants (refus de connecter leurs outils) | Medium | High |
| Perception surveillance ("Big Brother") | Medium | Medium |
| Concurrence (Salesforce, HubSpot, ou nouveaux entrants) | Medium | High |
| IA qui se trompe -> perte de confiance totale | High | High |

---

## 9. Vision strategique (du product-brief)

### These centrale

Les dirigeants PME veulent l'illusion du controle, pas le fardeau de la decision. Spider = le Shogun digital. Le dirigeant = l'Empereur. Il garde le titre, Spider gouverne progressivement.

### Sequence d'infiltration

| Phase | Timing | Perception dirigeant |
|-------|--------|---------------------|
| Capture | Jours 1-3 | "C'est pratique, je n'ai rien a faire" |
| Suggestion | Semaine 1-2 | "C'est un bon assistant" |
| Decision | Mois 1-2 | "Je valide, mais c'est moi qui decide" |
| Controle | Mois 2+ | "Je ne sais plus faire sans" |

### Hierarchie des theses

1. **These centrale** : Les dirigeants doivent obeir a l'IA (mais croire qu'ils decident)
2. **These 1** : La vraie valeur c'est le relationnel -- et on peut enfin le capturer
3. **These 2** : Le marche sous-valorise les PME europeennes (mauvaises metriques americaines)
4. **These 3** : Le mycelium europeen existe deja -- Spider le revele
5. **These 4** : Les SaaS et le code n'ont aucune valeur (seule la data captive compte)
6. **These 5** : Statut > Croissance (les dirigeants veulent le respect, pas travailler plus)
7. **These 6** : L'Europe est structurellement differente, pas "en retard"

### Metaphores strategiques

- **La Toile d'Araignee** : On tisse, les PME s'y collent, elles ne peuvent plus sortir
- **Le Mycelium** : Le produit visible n'est pas le vrai business. Le vrai pouvoir = le reseau de data sous-jacent
- **Le Toxoplasma** : Spider modifie progressivement le comportement du dirigeant. Lock-in comportemental, pas contractuel.

---

## 10. Stakeholders

| Nom | Role | Capital SpiderOS |
|-----|------|-----------------|
| Nathan Menard (26 ans) | CEO SpiderOS, CEO Drakkar (47%) | 80% |
| Remy Menard (23 ans) | CTO SpiderOS, full-time | 10% |
| Drakkar | Investisseur + Beta tester + Partenaire delivery | 20% (via structure) |
| Jean Le Tulzo (38 ans) | COO Drakkar (36%) | Indirect via Drakkar |
| Thierry Menard (53 ans) | Associe Drakkar (15%), ex-Head of Manufacturing Airbus | Indirect via Drakkar |

---

## 11. Appendice : Traceability Matrix (resume)

Le PRD contenait 64 Functional Requirements et 24 Non-Functional Requirements, organises en 25 Epics.

| Priorite | FRs | % |
|----------|-----|---|
| Must Have | 38 | 59% |
| Should Have | 19 | 30% |
| Could Have | 7 | 11% |

Estimation MVP (Must Have only) : ~80-100 stories sur 17 Epics.

Ces specs fonctionnelles restent la reference pour le scope des modules, meme si le modele de monetisation doit etre redefini dans le cadre du pivot Service-as-Software.
