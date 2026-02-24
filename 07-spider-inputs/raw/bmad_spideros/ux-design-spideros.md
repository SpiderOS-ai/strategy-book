# UX Design: SpiderOS

**Date:** 2026-01-18
**Designer:** Claude (UX Designer Agent)
**Version:** 1.0
**Project Type:** web-app
**Status:** Draft

---

## Document Overview

Ce document definit le design UX complet de SpiderOS, incluant les user flows, wireframes, accessibilite, composants et design tokens.

**Scope:**
- **Plateformes:** Web (desktop + mobile responsive)
- **Accessibilite:** WCAG 2.1 AA
- **Niveau de detail:** Complet (wireframes, interactions, composants, design tokens, handoff)
- **Design System:** A creer (nouveau)

**Documents sources:**
- PRD: `docs/prd-spideros-2026-01-18.md`
- Product Brief: `docs/product-brief.md`
- Brainstorming modules: `docs/brainstorming/`

---

## Design Scope Summary

### Modules a designer

| Module | Ecrans (Est.) | Priorite |
|--------|---------------|----------|
| **Plateforme Core** | 8-10 | Must Have |
| **Spider People** | 12-15 | Must Have |
| **Spider Memory** | 4-6 | Must Have |
| **Spider Builder** | 8-10 | Must Have |
| **Spider Content** | 8-10 | Must Have |
| **Site Web Marketing** | 5-7 | Must Have |
| **Total** | **45-58** | - |

### Personas cibles

| Persona | Module principal | Contexte d'usage |
|---------|------------------|------------------|
| Dirigeant PME | Spider People | Desktop bureau, mobile RDV |
| Commercial terrain | Spider People | Mobile 60%, desktop 40% |
| Manager commercial | Spider People | Desktop 90% |
| Developpeur | Spider Builder | Desktop 100% |
| Equipe marketing | Spider Content | Desktop 90% |

---

## Part 1: User Flows

### Flow 1: Onboarding Global SpiderOS

**Entry Point:** Signup depuis site web ou invitation email

**Happy Path:**
```
[Landing Page]
   |
   v
[Signup] --> Email/Password ou OAuth Google
   |
   v
[Verification Email]
   |
   v
[Choix Module Initial]
   |  - Spider People (CRM)
   |  - Spider Builder (Coding)
   |  - Spider Content (Contenu)
   v
[Onboarding Module]
   |
   v
[Dashboard Module]
   |
   v
[Wahoo Moment!]
```

**Decision Points:**
- A signup: OAuth Google vs email/password
- A choix module: Le dirigeant peut activer plusieurs modules

**Error Cases:**
- Email deja utilise → "Compte existant, connectez-vous"
- OAuth echoue → Fallback email/password
- Verification expiree → Renvoyer email

**Exit Points:**
- Success: Dashboard module choisi
- Abandon: Landing page (tracking pour relance)

---

### Flow 2: Onboarding Spider People

**Entry Point:** Apres choix "Spider People" ou activation module

**Happy Path:**
```
[Intro Spider People]
   |  "Votre CRM va se remplir tout seul"
   v
[Connexion Gmail] --> OAuth Google
   |
   v
[Connexion Google Calendar] --> OAuth Google
   |
   v
[Connexion Calls (optionnel)]
   |  - Aircall
   |  - Noota
   |  - "Plus tard"
   v
[Sync en cours]
   |  Animation + progression
   |  "On analyse vos 5 dernieres annees..."
   v
[Premier contact enrichi]
   |  Fiche contact avec infos extraites
   |  Score de connaissance visible
   v
[Wahoo!] --> "Mon CRM est rempli!"
   |
   v
[Dashboard People]
```

**Duration cible:** < 10 minutes (NFR-004)

**Decision Points:**
- Connexion calls: Optionnel, peut etre fait plus tard
- Scope sync: Configurable (1 an, 5 ans, tout)

**Error Cases:**
- Gmail refuse OAuth → Instructions depannage
- Sync echoue partiellement → Retry automatique + notification

**Exit Points:**
- Success: Dashboard avec contacts enrichis
- Skip calls: Dashboard avec emails/calendar seulement

---

### Flow 3: Brief Avant RDV

**Entry Point:** Notification push 30min avant RDV (configurable)

**Happy Path:**
```
[Notification Push]
   |  "RDV avec Jean Dupont dans 30min"
   |  "Voir le brief"
   v
[Brief Screen]
   |  - Resume contact (photo, poste, entreprise)
   |  - Score de connaissance (jauge)
   |  - Derniers echanges (3-5)
   |  - Infos cles extraites
   |  - Sujets a aborder (suggestions)
   v
[Actions rapides]
   |  - "Voir fiche complete"
   |  - "Appeler"
   |  - "Envoyer message"
   v
[Retour Dashboard / Fermer]
```

**Performance:** Generation < 3 secondes (NFR-002)

**Decision Points:**
- Click notification → Brief direct
- Voir fiche → Navigation vers fiche contact complete

**Error Cases:**
- Pas de donnees sur le contact → "Nouveau contact, voulez-vous l'enrichir?"
- Contact non identifie → "Qui est [nom]?" (recherche)

---

### Flow 4: Inbox Filtree + Reponse Suggeree

**Entry Point:** Ouverture Spider People ou notification nouvelle priorite

**Happy Path:**
```
[Inbox Filtree]
   |  Vue "A traiter" (5-10 priorites)
   |  Badges: VIP, Deal, Urgent
   v
[Select Email]
   |
   v
[Email Detail]
   |  - Contenu email
   |  - Infos contact (sidebar)
   |  - Score confiance
   v
[Suggestion Reponse]
   |  "Reponse suggeree" (carte)
   |  Ton adapte au contact
   v
[Editer / Accepter]
   |
   v
[Envoyer]
   |
   v
[Marquer traite]
   |
   v
[Prochain email ou Dashboard]
```

**Decision Points:**
- Inbox filtree vs Tout: Toggle en haut
- Editer suggestion vs envoyer directement

**Error Cases:**
- Suggestion non pertinente → "Regenerer" ou ecrire manuellement

---

### Flow 5: Validation Flashcards

**Entry Point:** Dashboard ou notification "5 infos a valider"

**Happy Path:**
```
[Flashcard Stack]
   |  "L'anniversaire de Jean est le 15 mars"
   |  Source: Email du 10/01
   |  Confiance: 65%
   v
[Swipe]
   |  Gauche = Invalide
   |  Droite = Valide
   |  Haut = Ne sait pas
   v
[Prochaine Flashcard]
   |  ... (max 5-10 par jour)
   v
[Termine!]
   |  "Merci! Spider apprend de vos corrections"
   v
[Dashboard]
```

**Limite:** Max 5-10 validations/jour (NFR-020)

**Error Cases:**
- Doute sur l'info → "Ne sait pas" (skip)
- Toutes traitees → "Revenir demain"

---

### Flow 6: Onboarding Spider Builder

**Entry Point:** Activation module Spider Builder

**Happy Path:**
```
[Intro Spider Builder]
   |  "Cadrez votre projet avant de coder"
   v
[Wizard - Objectifs]
   |  "Quel type de projet?"
   |  "Quel est l'objectif principal?"
   v
[Wizard - Contraintes]
   |  "Quelles contraintes techniques?"
   |  "Quel est votre niveau?"
   v
[Wizard - Stack]
   |  Selection des libs approuvees
   |  Templates de regles
   v
[Generation PRD]
   |  Progress bar
   |  "Generation du PRD..."
   v
[Review PRD]
   |  Editable
   |  "Valider" / "Modifier"
   v
[Generation Architecture]
   |  "Generation de l'architecture..."
   v
[Review Architecture]
   |  Diagrammes
   |  Structure fichiers
   v
[Setup Proxy]
   |  Instructions 1-click
   |  "Configurer Claude Code"
   v
[Ready to Build!]
   |
   v
[Dashboard Builder]
```

**Decision Points:**
- Niveau de detail wizard: Rapide vs detaille
- Stack: Templates vs custom

---

### Flow 7: Generation Photo Produit (Spider Content)

**Entry Point:** Dashboard Content → "Nouvelle photo"

**Happy Path:**
```
[Nouvelle Generation]
   |  "Photo produit" / "Video UGC"
   v
[Upload Produit]
   |  Drag & drop image
   |  Ou URL catalogue
   v
[Selection Style]
   |  Templates: Studio, Lifestyle, Flat lay
   |  Couleur fond
   v
[Brand Kit]
   |  Selection ou creation
   |  Logo, couleurs, fonts
   v
[Generation]
   |  Progress
   |  "Generation en cours..."
   v
[Preview]
   |  4 variantes
   |  Zoom, compare
   v
[Select / Regenerer]
   |
   v
[Export]
   |  Resolution
   |  Format (JPG, PNG, WebP)
   v
[Telecharger / Bibliotheque]
```

**Decision Points:**
- Style: Template vs custom
- Export: Direct vs bibliotheque

---

### Flow 8: Memory Dashboard (Transparence)

**Entry Point:** Navigation → "Memory" ou clic "Voir ce que Spider sait"

**Happy Path:**
```
[Memory Dashboard]
   |  Stats globales
   |  - X contacts
   |  - Y documents indexes
   |  - Z infos extraites
   v
[Recherche / Filtres]
   |  Par contact, date, type, source
   v
[Liste Resultats]
   |  Infos groupees par contact
   |  Score confiance visible
   v
[Detail Info]
   |  Source originale
   |  Date extraction
   |  Score confiance
   |  Historique modifs
   v
[Actions]
   |  "Modifier" (edition inline)
   |  "Supprimer"
   |  "Voir source"
   v
[Confirmation]
   |
   v
[Retour Dashboard]
```

**Error Cases:**
- Suppression → Double confirmation
- Pas de resultats → "Aucune info pour ces criteres"

---

## Part 2: Screen Inventory

### Plateforme Core

| ID | Ecran | Flow | Priority |
|----|-------|------|----------|
| CORE-01 | Landing Page (Site web) | Marketing | Must |
| CORE-02 | Signup | Auth | Must |
| CORE-03 | Login | Auth | Must |
| CORE-04 | Forgot Password | Auth | Must |
| CORE-05 | Verification Email | Auth | Must |
| CORE-06 | Module Selector | Onboarding | Must |
| CORE-07 | Settings | Settings | Must |
| CORE-08 | Profile | Settings | Must |
| CORE-09 | Billing | Settings | Should |
| CORE-10 | Team Management | Admin | Must |

### Spider People

| ID | Ecran | Flow | Priority |
|----|-------|------|----------|
| PPL-01 | Onboarding Intro | Onboarding | Must |
| PPL-02 | Connexion Gmail | Onboarding | Must |
| PPL-03 | Connexion Calendar | Onboarding | Must |
| PPL-04 | Connexion Calls | Onboarding | Should |
| PPL-05 | Sync Progress | Onboarding | Must |
| PPL-06 | Dashboard | Main | Must |
| PPL-07 | Inbox Filtree | Main | Must |
| PPL-08 | Email Detail | Main | Must |
| PPL-09 | Contact List | Contacts | Must |
| PPL-10 | Contact Detail | Contacts | Must |
| PPL-11 | Brief Avant RDV | Briefing | Must |
| PPL-12 | Flashcards Validation | Validation | Should |
| PPL-13 | Calendar View | Calendar | Should |
| PPL-14 | Search Results | Search | Must |
| PPL-15 | Alerts Center | Alerts | Should |

### Spider Memory

| ID | Ecran | Flow | Priority |
|----|-------|------|----------|
| MEM-01 | Memory Dashboard | Transparence | Should |
| MEM-02 | Search Results | Search | Should |
| MEM-03 | Info Detail | Detail | Should |
| MEM-04 | Delete Confirmation | RGPD | Should |
| MEM-05 | Contact Memory View | Transparence | Should |
| MEM-06 | Forget Me | RGPD | Should |

### Spider Builder

| ID | Ecran | Flow | Priority |
|----|-------|------|----------|
| BLD-01 | Onboarding Intro | Onboarding | Must |
| BLD-02 | Wizard - Objectifs | Onboarding | Must |
| BLD-03 | Wizard - Contraintes | Onboarding | Must |
| BLD-04 | Wizard - Stack | Onboarding | Must |
| BLD-05 | PRD Review | Documents | Must |
| BLD-06 | Architecture Review | Documents | Must |
| BLD-07 | Dashboard | Main | Must |
| BLD-08 | Project Settings | Settings | Must |
| BLD-09 | Rules Editor | Config | Must |
| BLD-10 | Progress Tracking | Tracking | Should |

### Spider Content

| ID | Ecran | Flow | Priority |
|----|-------|------|----------|
| CNT-01 | Dashboard | Main | Must |
| CNT-02 | New Photo | Generation | Must |
| CNT-03 | New Video | Generation | Must |
| CNT-04 | Brand Kit Editor | Brand | Must |
| CNT-05 | Template Gallery | Templates | Should |
| CNT-06 | Generation Progress | Generation | Must |
| CNT-07 | Preview & Export | Export | Must |
| CNT-08 | Media Library | Library | Must |
| CNT-09 | Catalogue Import | Import | Should |
| CNT-10 | Credits Dashboard | Billing | Should |

### Site Web Marketing

| ID | Ecran | Flow | Priority |
|----|-------|------|----------|
| WEB-01 | Homepage | Marketing | Must |
| WEB-02 | Page Spider People | Product | Must |
| WEB-03 | Page Spider Builder | Product | Must |
| WEB-04 | Page Spider Content | Product | Must |
| WEB-05 | Pricing | Marketing | Must |
| WEB-06 | Contact / Demo | Lead | Should |
| WEB-07 | Blog (listing) | Content | Could |

**Total: 52 ecrans identifies**

---

## Part 3: Wireframes

### CORE-01: Landing Page (Homepage)

#### Desktop (1024px+)

```
┌─────────────────────────────────────────────────────────────────────┐
│ [Logo SpiderOS]     People   Builder   Content   Pricing   [Login]  │
├─────────────────────────────────────────────────────────────────────┤
│                                                                     │
│                    L'IA NE VOIT PAS                                 │
│                    VOTRE ENTREPRISE                                 │
│                                                                     │
│     Vos vraies donnees sont eparpillees. SpiderOS tisse            │
│     une toile par-dessus — sans migration. L'IA voit enfin.         │
│                                                                     │
│              [Demarrer gratuitement]   [Voir la demo]               │
│                                                                     │
├─────────────────────────────────────────────────────────────────────┤
│                                                                     │
│     ┌───────────────┐ ┌───────────────┐ ┌───────────────┐          │
│     │  [Icon]       │ │  [Icon]       │ │  [Icon]       │          │
│     │               │ │               │ │               │          │
│     │ SPIDER PEOPLE │ │ SPIDER BUILDER│ │ SPIDER CONTENT│          │
│     │               │ │               │ │               │          │
│     │ CRM qui se    │ │ Cadrez vos    │ │ Photos et     │          │
│     │ remplit seul  │ │ projets IA    │ │ videos IA pro │          │
│     │               │ │               │ │               │          │
│     │ [En savoir +] │ │ [En savoir +] │ │ [En savoir +] │          │
│     └───────────────┘ └───────────────┘ └───────────────┘          │
│                                                                     │
├─────────────────────────────────────────────────────────────────────┤
│                                                                     │
│     COMMENT CA MARCHE                                               │
│                                                                     │
│     1. Connectez        2. Spider tisse      3. Automatisez        │
│        vos sources         la toile             par-dessus         │
│                                                                     │
│     Mail, tel,          Liens entre           Modules standards    │
│     fichiers...         toutes les data       ou sur mesure        │
│                                                                     │
├─────────────────────────────────────────────────────────────────────┤
│                                                                     │
│     ILS UTILISENT SPIDEROS                                          │
│                                                                     │
│     [Logo] [Logo] [Logo] [Logo]                                     │
│                                                                     │
│     "SpiderOS a change notre facon de gerer nos relations."        │
│                              - CEO, PME X                           │
│                                                                     │
├─────────────────────────────────────────────────────────────────────┤
│                                                                     │
│     PRET A COMMENCER?                                               │
│                                                                     │
│     [Demarrer gratuitement]                                         │
│                                                                     │
├─────────────────────────────────────────────────────────────────────┤
│ Logo    People | Builder | Content | Pricing | Contact | Legal     │
│         © 2026 SpiderOS. Heberge en France.                        │
└─────────────────────────────────────────────────────────────────────┘
```

#### Mobile (320-767px)

```
┌─────────────────────┐
│ ☰  [Logo SpiderOS]  │
├─────────────────────┤
│                     │
│   L'IA NE VOIT PAS  │
│   VOTRE ENTREPRISE  │
│                     │
│ Vos vraies donnees  │
│ sont eparpillees.   │
│ SpiderOS tisse une  │
│ toile par-dessus.   │
│                     │
│ [Demarrer gratuit]  │
│                     │
│ [Voir la demo]      │
│                     │
├─────────────────────┤
│ ┌─────────────────┐ │
│ │  SPIDER PEOPLE  │ │
│ │  CRM qui se     │ │
│ │  remplit seul   │ │
│ │  [En savoir +]  │ │
│ └─────────────────┘ │
│                     │
│ ┌─────────────────┐ │
│ │  SPIDER BUILDER │ │
│ │  Cadrez vos     │ │
│ │  projets IA     │ │
│ │  [En savoir +]  │ │
│ └─────────────────┘ │
│                     │
│ ┌─────────────────┐ │
│ │  SPIDER CONTENT │ │
│ │  Photos et      │ │
│ │  videos IA pro  │ │
│ │  [En savoir +]  │ │
│ └─────────────────┘ │
│                     │
├─────────────────────┤
│ COMMENT CA MARCHE   │
│                     │
│ 1. Connectez        │
│    vos sources      │
│                     │
│ 2. Spider tisse     │
│    la toile         │
│                     │
│ 3. Automatisez      │
│    par-dessus       │
│                     │
├─────────────────────┤
│ PRET A COMMENCER?   │
│                     │
│ [Demarrer gratuit]  │
│                     │
├─────────────────────┤
│ © 2026 SpiderOS     │
│ Heberge en France   │
└─────────────────────┘
```

---

### CORE-02: Signup

#### Desktop

```
┌─────────────────────────────────────────────────────────────────────┐
│                          [Logo SpiderOS]                            │
├─────────────────────────────────────────────────────────────────────┤
│                                                                     │
│   ┌─────────────────────────────────────────────────────────────┐   │
│   │                                                             │   │
│   │                    Creer votre compte                       │   │
│   │                                                             │   │
│   │   [G] Continuer avec Google                                 │   │
│   │                                                             │   │
│   │   ─────────────── ou ───────────────                        │   │
│   │                                                             │   │
│   │   Email                                                     │   │
│   │   ┌─────────────────────────────────────────────────────┐   │   │
│   │   │                                                     │   │   │
│   │   └─────────────────────────────────────────────────────┘   │   │
│   │                                                             │   │
│   │   Mot de passe                                              │   │
│   │   ┌─────────────────────────────────────────────────────┐   │   │
│   │   │                                             [👁]    │   │   │
│   │   └─────────────────────────────────────────────────────┘   │   │
│   │   Min 8 caracteres, 1 majuscule, 1 chiffre                  │   │
│   │                                                             │   │
│   │   [ ] J'accepte les CGU et la Politique de confidentialite  │   │
│   │                                                             │   │
│   │   [          Creer mon compte          ]                    │   │
│   │                                                             │   │
│   │   Deja un compte? Se connecter                              │   │
│   │                                                             │   │
│   └─────────────────────────────────────────────────────────────┘   │
│                                                                     │
│   Donnees hebergees en France. RGPD compliant.                     │
│                                                                     │
└─────────────────────────────────────────────────────────────────────┘
```

---

### PPL-06: Dashboard Spider People

#### Desktop

```
┌─────────────────────────────────────────────────────────────────────┐
│ [Logo]  People  Memory  Builder  Content     🔔 [Avatar] ▼          │
├─────────────────────────────────────────────────────────────────────┤
│                                                                     │
│  Bonjour Nathan                                     Lun 18 Jan      │
│                                                                     │
│  ┌────────────────────────────────────────────────────────────────┐ │
│  │  PROCHAIN RDV                                                  │ │
│  │  ┌──────────────────────────────────────────────────────────┐  │ │
│  │  │  [Photo]  Jean Dupont - CEO Acme Corp                    │  │ │
│  │  │           Dans 2h (14:00)                                 │  │ │
│  │  │           Score: ████████░░ 78%                          │  │ │
│  │  │                                                          │  │ │
│  │  │  [Voir le brief]                                         │  │ │
│  │  └──────────────────────────────────────────────────────────┘  │ │
│  └────────────────────────────────────────────────────────────────┘ │
│                                                                     │
│  ┌─────────────────────────┐  ┌─────────────────────────────────┐   │
│  │  A TRAITER (5)          │  │  CONTACTS QUI REFROIDISSENT     │   │
│  │  ───────────────────────│  │  ─────────────────────────────  │   │
│  │  [VIP] Marie L.         │  │  Pierre M. - 45 jours           │   │
│  │  Demande de devis       │  │  Sophie B. - 32 jours           │   │
│  │                         │  │  [Voir tout]                    │   │
│  │  [DEAL] Startup X       │  │                                 │   │
│  │  Negociation finale     │  │  ANNIVERSAIRES                  │   │
│  │                         │  │  ─────────────────────────────  │   │
│  │  [!] Thomas D.          │  │  Jean D. - Demain               │   │
│  │  Rappel urgent          │  │  Marie L. - 25 Jan              │   │
│  │                         │  │                                 │   │
│  │  [Voir tout]            │  │                                 │   │
│  └─────────────────────────┘  └─────────────────────────────────┘   │
│                                                                     │
│  ┌────────────────────────────────────────────────────────────────┐ │
│  │  VALIDATIONS (3)                                    [Valider]  │ │
│  │  3 informations a confirmer                                    │ │
│  └────────────────────────────────────────────────────────────────┘ │
│                                                                     │
│  ┌────────────────────────────────────────────────────────────────┐ │
│  │  ACTIVITE RECENTE                                              │ │
│  │  ─────────────────────────────────────────────────────────────  │ │
│  │  Aujourd'hui                                                   │ │
│  │  • 3 emails recus, 2 traites                                   │ │
│  │  • 1 call avec Marie L. (45 min)                               │ │
│  │  • 2 nouveaux contacts ajoutes                                 │ │
│  │                                                                │ │
│  │  Hier                                                          │ │
│  │  • 5 emails traites                                            │ │
│  │  • RDV avec Startup X (compte-rendu genere)                    │ │
│  └────────────────────────────────────────────────────────────────┘ │
│                                                                     │
└─────────────────────────────────────────────────────────────────────┘
```

#### Mobile

```
┌─────────────────────┐
│ ☰ People       🔔 👤│
├─────────────────────┤
│                     │
│ Bonjour Nathan      │
│ Lun 18 Jan          │
│                     │
├─────────────────────┤
│ PROCHAIN RDV        │
│ ┌─────────────────┐ │
│ │ [Photo] Jean D. │ │
│ │ CEO Acme Corp   │ │
│ │ Dans 2h         │ │
│ │ ████████░░ 78%  │ │
│ │ [Voir brief]    │ │
│ └─────────────────┘ │
├─────────────────────┤
│ A TRAITER (5)    >  │
├─────────────────────┤
│ [VIP] Marie L.      │
│ Demande de devis    │
│                     │
│ [DEAL] Startup X    │
│ Negociation finale  │
│                     │
│ [!] Thomas D.       │
│ Rappel urgent       │
├─────────────────────┤
│ VALIDATIONS (3)  >  │
│ 3 infos a confirmer │
├─────────────────────┤
│ ALERTES          >  │
│ Pierre M. - 45j     │
│ Jean D. - Anniv     │
└─────────────────────┘

[Bottom Nav]
┌─────────────────────┐
│ 🏠   📧   👥   📅   │
│Home Inbox Contacts  │
└─────────────────────┘
```

---

### PPL-07: Inbox Filtree

#### Desktop

```
┌─────────────────────────────────────────────────────────────────────┐
│ [Logo]  People  Memory  Builder  Content     🔔 [Avatar] ▼          │
├─────────────────────────────────────────────────────────────────────┤
│                                                                     │
│  Inbox            [A traiter (5)] [Tout (127)]           [🔍]      │
│                                                                     │
│  ┌────────────────────────────────┬────────────────────────────────┐│
│  │ EMAIL LIST                     │ EMAIL DETAIL                   ││
│  │                                │                                ││
│  │ ┌────────────────────────────┐ │ De: Marie Laurent              ││
│  │ │ [VIP] Marie Laurent       │ │ A: moi                         ││
│  │ │ Demande de devis          │ │ Date: Aujourd'hui 10:32        ││
│  │ │ Aujourd'hui 10:32       ● │ │                                ││
│  │ └────────────────────────────┘ │ ─────────────────────────────  ││
│  │                                │                                ││
│  │ ┌────────────────────────────┐ │ Bonjour Nathan,                ││
│  │ │ [DEAL] Olivier Martin     │ │                                ││
│  │ │ RE: Proposition           │ │ Suite a notre echange de la    ││
│  │ │ Aujourd'hui 09:15       ● │ │ semaine derniere, pourriez-    ││
│  │ └────────────────────────────┘ │ vous m'envoyer un devis pour   ││
│  │                                │ la prestation dont nous avons  ││
│  │ ┌────────────────────────────┐ │ discute?                       ││
│  │ │ [!] Thomas Durand         │ │                                ││
│  │ │ Rappel urgent             │ │ Cordialement,                  ││
│  │ │ Hier 18:45              ● │ │ Marie                          ││
│  │ └────────────────────────────┘ │                                ││
│  │                                │ ─────────────────────────────  ││
│  │ ┌────────────────────────────┐ │                                ││
│  │ │ Sophie Bernard            │ │ REPONSE SUGGEREE               ││
│  │ │ Question technique        │ │ ┌──────────────────────────┐   ││
│  │ │ Hier 14:22              ○ │ │ │ Bonjour Marie,           │   ││
│  │ └────────────────────────────┘ │ │                          │   ││
│  │                                │ │ Merci pour votre message.│   ││
│  │ ┌────────────────────────────┐ │ │ Je vous envoie le devis  │   ││
│  │ │ Pierre Moreau             │ │ │ dans la journee.         │   ││
│  │ │ Suivi projet              │ │ │                          │   ││
│  │ │ Lun 15 Jan              ○ │ │ │ Bien cordialement,       │   ││
│  │ └────────────────────────────┘ │ │ Nathan                   │   ││
│  │                                │ └──────────────────────────┘   ││
│  │                                │                                ││
│  │                                │ [Editer]    [Envoyer]          ││
│  │                                │                                ││
│  └────────────────────────────────┴────────────────────────────────┘│
│                                                                     │
└─────────────────────────────────────────────────────────────────────┘
```

---

### PPL-10: Fiche Contact Detail

#### Desktop

```
┌─────────────────────────────────────────────────────────────────────┐
│ [Logo]  People  Memory  Builder  Content     🔔 [Avatar] ▼          │
├─────────────────────────────────────────────────────────────────────┤
│  < Retour                                                           │
│                                                                     │
│  ┌────────────────────────────────────────────────────────────────┐ │
│  │                                                                │ │
│  │   [Photo]      Jean Dupont                                     │ │
│  │   Grande       CEO @ Acme Corp                                 │ │
│  │                Paris, France                                   │ │
│  │                                                                │ │
│  │   [📧 Email]  [📞 Appeler]  [💬 Message]  [...]               │ │
│  │                                                                │ │
│  └────────────────────────────────────────────────────────────────┘ │
│                                                                     │
│  ┌─────────────────────────────────────────────────────────────────┐│
│  │ [Resume] [Echanges] [Infos] [Memory]                           ││
│  └─────────────────────────────────────────────────────────────────┘│
│                                                                     │
│  ┌─────────────────────────┐  ┌─────────────────────────────────┐   │
│  │  SCORE DE CONNAISSANCE  │  │  INFOS CLES                      │   │
│  │  ─────────────────────  │  │  ────────────────────────────    │   │
│  │                         │  │                                  │   │
│  │  ████████████████░░ 78% │  │  Anniversaire: 15 mars   [✓ 85%] │   │
│  │                         │  │  Enfants: 2 (Paul, Marie) [? 65%]│   │
│  │  Surface      ██████░░  │  │  Passion: Golf           [✓ 90%] │   │
│  │  Comportement ████████  │  │  Bureau: Tour Montparnasse      │   │
│  │  Motivations  ██████░░  │  │                                  │   │
│  │  Vulnerab.    ████░░░░  │  │  [Voir tout] [Modifier]          │   │
│  │                         │  │                                  │   │
│  │  [Ameliorer le score]   │  │                                  │   │
│  └─────────────────────────┘  └─────────────────────────────────┘   │
│                                                                     │
│  ┌────────────────────────────────────────────────────────────────┐ │
│  │  DERNIERS ECHANGES                                 [Voir tout] │ │
│  │  ────────────────────────────────────────────────────────────  │ │
│  │                                                                │ │
│  │  📧 Email - Aujourd'hui 10:32                                  │ │
│  │  "Suite a notre echange..."                                    │ │
│  │                                                                │ │
│  │  📞 Appel - Hier (35 min)                                      │ │
│  │  "Discussion sur le projet Alpha, Jean interesse mais..."     │ │
│  │                                                                │ │
│  │  📅 RDV - 10 Jan (1h)                                          │ │
│  │  "Presentation initiale, bonne reception"                      │ │
│  │                                                                │ │
│  └────────────────────────────────────────────────────────────────┘ │
│                                                                     │
│  ┌────────────────────────────────────────────────────────────────┐ │
│  │  PROFIL PSYCHOLOGIQUE (DISC)                          [?]     │ │
│  │  ────────────────────────────────────────────────────────────  │ │
│  │                                                                │ │
│  │  ████████░░ Dominant (D)     - Direct, oriente resultats      │ │
│  │  ██████░░░░ Influent (I)     - Sociable, persuasif            │ │
│  │  ████░░░░░░ Stable (S)       - Patient, fiable                │ │
│  │  ██░░░░░░░░ Consciencieux (C)- Analytique, precis             │ │
│  │                                                                │ │
│  │  Conseils de communication:                                    │ │
│  │  • Allez droit au but, evitez les details                     │ │
│  │  • Presentez des resultats concrets                           │ │
│  │  • Laissez-le decider rapidement                              │ │
│  │                                                                │ │
│  └────────────────────────────────────────────────────────────────┘ │
│                                                                     │
└─────────────────────────────────────────────────────────────────────┘
```

---

### PPL-11: Brief Avant RDV

#### Mobile (context principal d'usage)

```
┌─────────────────────┐
│ < Retour       [X]  │
├─────────────────────┤
│                     │
│     [Photo]         │
│   Jean Dupont       │
│   CEO @ Acme Corp   │
│                     │
│   RDV dans 28 min   │
│                     │
├─────────────────────┤
│ SCORE CONNAISSANCE  │
│ ████████████░░ 78%  │
│                     │
│ Vous le connaissez  │
│ bien. Axes a        │
│ creuser: famille,   │
│ motivations.        │
│                     │
├─────────────────────┤
│ DERNIERS ECHANGES   │
├─────────────────────┤
│ 📧 Hier             │
│ "Confirme pour      │
│ demain 14h..."      │
│                     │
│ 📞 10 Jan (35 min)  │
│ "Interesse par      │
│ notre solution,     │
│ mais budget         │
│ limite..."          │
│                     │
│ 📅 5 Jan (1h)       │
│ "Presentation       │
│ initiale OK"        │
│                     │
├─────────────────────┤
│ INFOS CLES          │
├─────────────────────┤
│ • Golf: Passion     │
│   (en a parle 3x)   │
│ • 2 enfants: Paul,  │
│   Marie             │
│ • Budget: ~50k max  │
│ • Decision: rapide  │
│                     │
├─────────────────────┤
│ SUJETS A ABORDER    │
├─────────────────────┤
│ 1. Demander des     │
│    nouvelles du     │
│    tournoi de golf  │
│                     │
│ 2. Revenir sur      │
│    l'objection      │
│    budget           │
│                     │
│ 3. Proposer option  │
│    echelonnement    │
│                     │
├─────────────────────┤
│                     │
│ [Voir fiche]        │
│ [Appeler]           │
│                     │
└─────────────────────┘
```

---

### PPL-12: Flashcards Validation

#### Mobile

```
┌─────────────────────┐
│ Validations    [X]  │
│ 3/5 restantes       │
├─────────────────────┤
│                     │
│                     │
│  ┌───────────────┐  │
│  │               │  │
│  │   Jean D.     │  │
│  │   [Photo]     │  │
│  │               │  │
│  │  ─────────────│  │
│  │               │  │
│  │  "L'anniver-  │  │
│  │  saire de     │  │
│  │  Jean est le  │  │
│  │  15 mars"     │  │
│  │               │  │
│  │  ─────────────│  │
│  │               │  │
│  │  Source:      │  │
│  │  Email du     │  │
│  │  10 janvier   │  │
│  │               │  │
│  │  Confiance:   │  │
│  │  ████░░ 65%   │  │
│  │               │  │
│  └───────────────┘  │
│                     │
│                     │
│   ← Swipe →         │
│                     │
│  ❌        ↑        ✓│
│  Faux   Passer   Vrai│
│                     │
├─────────────────────┤
│                     │
│ Conseil: Swipez     │
│ vite! 5 par jour    │
│ max.                │
│                     │
└─────────────────────┘
```

---

### BLD-07: Dashboard Spider Builder

#### Desktop

```
┌─────────────────────────────────────────────────────────────────────┐
│ [Logo]  People  Memory  Builder  Content     🔔 [Avatar] ▼          │
├─────────────────────────────────────────────────────────────────────┤
│                                                                     │
│  Projet: SpiderOS                                    [⚙ Settings]  │
│                                                                     │
│  ┌────────────────────────────────────────────────────────────────┐ │
│  │  PROGRESSION                                                   │ │
│  │  ━━━━━━━━━━━━━━━━━━━━━━━━━━━━░░░░░░░░░░ 65%                   │ │
│  │                                                                │ │
│  │  42/65 stories completees  •  Sprint 3/5  •  8 stories en cours│ │
│  └────────────────────────────────────────────────────────────────┘ │
│                                                                     │
│  ┌─────────────────────────┐  ┌─────────────────────────────────┐   │
│  │  STORY ACTIVE           │  │  GARDE-FOUS                      │   │
│  │  ─────────────────────  │  │  ────────────────────────────    │   │
│  │                         │  │                                  │   │
│  │  US-042                 │  │  ✓ Stack Guard         OK        │   │
│  │  Inbox filtree          │  │  ✓ Design System       OK        │   │
│  │                         │  │  ⚠ Loop Detection      1 alert   │   │
│  │  ████████░░ 80%         │  │                                  │   │
│  │                         │  │  [Voir details]                  │   │
│  │  [Voir la story]        │  │                                  │   │
│  └─────────────────────────┘  └─────────────────────────────────┘   │
│                                                                     │
│  ┌────────────────────────────────────────────────────────────────┐ │
│  │  DOCUMENTS PROJET                                              │ │
│  │  ────────────────────────────────────────────────────────────  │ │
│  │                                                                │ │
│  │  📄 PRD                  📐 Architecture       📋 Rules        │ │
│  │  Mis a jour: 15 Jan     Mis a jour: 10 Jan   12 regles         │ │
│  │  [Ouvrir]               [Ouvrir]             [Ouvrir]          │ │
│  │                                                                │ │
│  │  📦 Stack               📊 Tracking                            │ │
│  │  18 libs approuvees     Sprint 3 en cours                     │ │
│  │  [Gerer]                [Voir kanban]                          │ │
│  │                                                                │ │
│  └────────────────────────────────────────────────────────────────┘ │
│                                                                     │
│  ┌────────────────────────────────────────────────────────────────┐ │
│  │  PROXY STATUS                                                  │ │
│  │  ────────────────────────────────────────────────────────────  │ │
│  │                                                                │ │
│  │  ● Proxy actif sur localhost:3000                              │ │
│  │  127 requetes enrichies aujourd'hui                            │ │
│  │  Dernier enrichissement: il y a 2 min                          │ │
│  │                                                                │ │
│  │  [Configurer]  [Voir logs]                                     │ │
│  │                                                                │ │
│  └────────────────────────────────────────────────────────────────┘ │
│                                                                     │
└─────────────────────────────────────────────────────────────────────┘
```

---

### CNT-01: Dashboard Spider Content

#### Desktop

```
┌─────────────────────────────────────────────────────────────────────┐
│ [Logo]  People  Memory  Builder  Content     🔔 [Avatar] ▼          │
├─────────────────────────────────────────────────────────────────────┤
│                                                                     │
│  Spider Content                               Credits: 847    [+]   │
│                                                                     │
│  ┌─────────────────────────────────────────────────────────────────┐│
│  │  NOUVELLE GENERATION                                            ││
│  │                                                                 ││
│  │  ┌─────────────────┐  ┌─────────────────┐  ┌─────────────────┐  ││
│  │  │     [Icon]      │  │     [Icon]      │  │     [Icon]      │  ││
│  │  │                 │  │                 │  │                 │  ││
│  │  │  Photo Produit  │  │   Video UGC     │  │  Video Avatar   │  ││
│  │  │                 │  │                 │  │                 │  ││
│  │  │  10 credits     │  │  50 credits     │  │  30 credits     │  ││
│  │  │                 │  │                 │  │                 │  ││
│  │  │  [Creer]        │  │  [Creer]        │  │  [Creer]        │  ││
│  │  └─────────────────┘  └─────────────────┘  └─────────────────┘  ││
│  │                                                                 ││
│  └─────────────────────────────────────────────────────────────────┘│
│                                                                     │
│  ┌─────────────────────────────────────────────────────────────────┐│
│  │  BRAND KITS                                         [+ Nouveau] ││
│  │  ─────────────────────────────────────────────────────────────  ││
│  │                                                                 ││
│  │  ┌─────────────┐  ┌─────────────┐  ┌─────────────┐              ││
│  │  │ [Preview]   │  │ [Preview]   │  │             │              ││
│  │  │             │  │             │  │     +       │              ││
│  │  │ Acme Corp   │  │ StartupX    │  │   Ajouter   │              ││
│  │  │ 12 assets   │  │ 8 assets    │  │             │              ││
│  │  │             │  │             │  │             │              ││
│  │  │ [Ouvrir]    │  │ [Ouvrir]    │  │             │              ││
│  │  └─────────────┘  └─────────────┘  └─────────────┘              ││
│  │                                                                 ││
│  └─────────────────────────────────────────────────────────────────┘│
│                                                                     │
│  ┌─────────────────────────────────────────────────────────────────┐│
│  │  GENERATIONS RECENTES                               [Voir tout] ││
│  │  ─────────────────────────────────────────────────────────────  ││
│  │                                                                 ││
│  │  ┌─────────┐ ┌─────────┐ ┌─────────┐ ┌─────────┐ ┌─────────┐   ││
│  │  │[Preview]│ │[Preview]│ │[Preview]│ │[Preview]│ │[Preview]│   ││
│  │  │         │ │         │ │         │ │         │ │         │   ││
│  │  │ Photo   │ │ Video   │ │ Photo   │ │ Photo   │ │ Video   │   ││
│  │  │ Hier    │ │ 15 Jan  │ │ 14 Jan  │ │ 14 Jan  │ │ 12 Jan  │   ││
│  │  └─────────┘ └─────────┘ └─────────┘ └─────────┘ └─────────┘   ││
│  │                                                                 ││
│  └─────────────────────────────────────────────────────────────────┘│
│                                                                     │
└─────────────────────────────────────────────────────────────────────┘
```

---

### MEM-01: Memory Dashboard

#### Desktop

```
┌─────────────────────────────────────────────────────────────────────┐
│ [Logo]  People  Memory  Builder  Content     🔔 [Avatar] ▼          │
├─────────────────────────────────────────────────────────────────────┤
│                                                                     │
│  Spider Memory                                                      │
│  Ce que Spider sait                                                 │
│                                                                     │
│  ┌────────────┐  ┌────────────┐  ┌────────────┐  ┌────────────┐    │
│  │    847     │  │   12,453   │  │   34,782   │  │    92%     │    │
│  │  Contacts  │  │ Documents  │  │ Infos      │  │ Confiance  │    │
│  │  indexes   │  │ analyses   │  │ extraites  │  │ moyenne    │    │
│  └────────────┘  └────────────┘  └────────────┘  └────────────┘    │
│                                                                     │
│  ┌─────────────────────────────────────────────────────────────────┐│
│  │  RECHERCHER                                                     ││
│  │  ┌─────────────────────────────────────────────────────┐       ││
│  │  │ Recherche semantique...                      [🔍]   │       ││
│  │  └─────────────────────────────────────────────────────┘       ││
│  │                                                                 ││
│  │  Filtres: [Contact ▼] [Type ▼] [Source ▼] [Date ▼] [Confiance ▼]││
│  │                                                                 ││
│  └─────────────────────────────────────────────────────────────────┘│
│                                                                     │
│  ┌─────────────────────────────────────────────────────────────────┐│
│  │  DONNEES PAR CONTACT                                [Voir tout] ││
│  │  ─────────────────────────────────────────────────────────────  ││
│  │                                                                 ││
│  │  ┌──────────────────────────────────────────────────────────┐   ││
│  │  │ [Photo] Jean Dupont                                      │   ││
│  │  │         47 infos  •  Score: 78%  •  Derniere MàJ: 2h     │   ││
│  │  │         [Voir] [Modifier] [Supprimer donnees]            │   ││
│  │  └──────────────────────────────────────────────────────────┘   ││
│  │                                                                 ││
│  │  ┌──────────────────────────────────────────────────────────┐   ││
│  │  │ [Photo] Marie Laurent                                    │   ││
│  │  │         32 infos  •  Score: 65%  •  Derniere MàJ: 1j     │   ││
│  │  │         [Voir] [Modifier] [Supprimer donnees]            │   ││
│  │  └──────────────────────────────────────────────────────────┘   ││
│  │                                                                 ││
│  │  ┌──────────────────────────────────────────────────────────┐   ││
│  │  │ [Photo] Thomas Durand                                    │   ││
│  │  │         28 infos  •  Score: 55%  •  Derniere MàJ: 3j     │   ││
│  │  │         [Voir] [Modifier] [Supprimer donnees]            │   ││
│  │  └──────────────────────────────────────────────────────────┘   ││
│  │                                                                 ││
│  └─────────────────────────────────────────────────────────────────┘│
│                                                                     │
│  ┌─────────────────────────────────────────────────────────────────┐│
│  │  ⚠ DONNEES A FAIBLE CONFIANCE                                  ││
│  │  23 informations avec confiance < 60%                          ││
│  │  [Valider maintenant]                                          ││
│  └─────────────────────────────────────────────────────────────────┘│
│                                                                     │
└─────────────────────────────────────────────────────────────────────┘
```

---

## Part 4: Accessibility (WCAG 2.1 AA)

### Global Accessibility Requirements

#### Perceivable

| Critere | Implementation | Statut |
|---------|----------------|--------|
| **1.1.1 Non-text Content** | Toutes les images ont un alt text descriptif | Required |
| **1.3.1 Info and Relationships** | Structure semantique HTML5 (header, nav, main, footer) | Required |
| **1.3.2 Meaningful Sequence** | Ordre de lecture logique, DOM order = visual order | Required |
| **1.4.1 Use of Color** | L'information n'est jamais vehiculee par la couleur seule | Required |
| **1.4.3 Contrast (Minimum)** | Ratio 4.5:1 pour texte, 3:1 pour UI | Required |
| **1.4.4 Resize Text** | Zoom 200% sans perte de contenu | Required |
| **1.4.10 Reflow** | Pas de scroll horizontal a 320px | Required |

#### Operable

| Critere | Implementation | Statut |
|---------|----------------|--------|
| **2.1.1 Keyboard** | Toutes les fonctions accessibles au clavier | Required |
| **2.1.2 No Keyboard Trap** | Focus peut toujours sortir d'un composant | Required |
| **2.4.1 Bypass Blocks** | "Skip to main content" link | Required |
| **2.4.3 Focus Order** | Tab order logique | Required |
| **2.4.4 Link Purpose** | Liens avec texte descriptif | Required |
| **2.4.6 Headings and Labels** | Hierarchie H1-H6 coherente | Required |
| **2.4.7 Focus Visible** | Indicateur de focus visible (outline 2px) | Required |
| **2.5.5 Target Size** | Zones tactiles min 44x44px | Required |

#### Understandable

| Critere | Implementation | Statut |
|---------|----------------|--------|
| **3.1.1 Language of Page** | `lang="fr"` sur `<html>` | Required |
| **3.2.1 On Focus** | Pas de changement de contexte au focus | Required |
| **3.2.2 On Input** | Pas de changement de contexte a l'input | Required |
| **3.3.1 Error Identification** | Erreurs identifiees clairement | Required |
| **3.3.2 Labels or Instructions** | Labels pour tous les inputs | Required |
| **3.3.3 Error Suggestion** | Suggestions de correction | Required |

#### Robust

| Critere | Implementation | Statut |
|---------|----------------|--------|
| **4.1.1 Parsing** | HTML valide | Required |
| **4.1.2 Name, Role, Value** | ARIA labels ou natif HTML | Required |

### Accessibility per Screen Type

#### Forms (Login, Signup, etc.)

```html
<!-- Structure accessible form -->
<form role="form" aria-labelledby="form-title">
  <h1 id="form-title">Creer votre compte</h1>

  <div class="form-group">
    <label for="email">Email</label>
    <input
      type="email"
      id="email"
      aria-required="true"
      aria-describedby="email-help"
    />
    <span id="email-help" class="help-text">
      Votre email professionnel
    </span>
  </div>

  <!-- En cas d'erreur -->
  <div class="form-group has-error">
    <label for="password">Mot de passe</label>
    <input
      type="password"
      id="password"
      aria-invalid="true"
      aria-describedby="password-error"
    />
    <span id="password-error" class="error-text" role="alert">
      Le mot de passe doit contenir au moins 8 caracteres
    </span>
  </div>

  <button type="submit">Creer mon compte</button>
</form>
```

#### Cards (Contact, Email, etc.)

```html
<article class="contact-card" aria-labelledby="contact-name">
  <img src="photo.jpg" alt="" /> <!-- decorative if name present -->
  <h3 id="contact-name">Jean Dupont</h3>
  <p>CEO @ Acme Corp</p>
  <div class="score" role="meter" aria-valuenow="78" aria-valuemin="0" aria-valuemax="100">
    Score: 78%
  </div>
  <a href="/contacts/jean" aria-label="Voir la fiche de Jean Dupont">
    Voir la fiche
  </a>
</article>
```

#### Modals

```html
<div
  role="dialog"
  aria-modal="true"
  aria-labelledby="modal-title"
  aria-describedby="modal-desc"
>
  <h2 id="modal-title">Confirmer la suppression</h2>
  <p id="modal-desc">
    Voulez-vous vraiment supprimer ces donnees? Cette action est irreversible.
  </p>
  <button>Annuler</button>
  <button>Supprimer</button>
</div>
```

#### Flashcards (Swipe)

```html
<section aria-label="Validation des informations" role="region">
  <p>3 sur 5 validations restantes</p>

  <article
    class="flashcard"
    role="group"
    aria-labelledby="flashcard-title"
    tabindex="0"
  >
    <h2 id="flashcard-title">Jean Dupont</h2>
    <p>"L'anniversaire de Jean est le 15 mars"</p>
    <p>Source: Email du 10 janvier</p>
    <p>Confiance: 65%</p>
  </article>

  <!-- Keyboard accessible alternatives to swipe -->
  <div role="group" aria-label="Actions de validation">
    <button aria-label="Marquer comme faux">Faux</button>
    <button aria-label="Passer cette information">Passer</button>
    <button aria-label="Marquer comme vrai">Vrai</button>
  </div>

  <!-- Touch instruction (hidden to screen readers if buttons visible) -->
  <p aria-hidden="true">Swipez: gauche = faux, droite = vrai</p>
</section>
```

### Keyboard Navigation Map

| Ecran | Tab Order | Raccourcis |
|-------|-----------|------------|
| **Dashboard** | Header → Cards → Actions → Footer | `G + D` = Go to Dashboard |
| **Inbox** | Header → Email list → Email detail → Actions | `J/K` = Next/Prev email |
| **Contact** | Header → Info → Tabs → Content → Actions | `E` = Edit |
| **Flashcards** | Header → Card → Buttons | `←` Faux, `↑` Passer, `→` Vrai |
| **Modal** | Focus trap: First → Last → First | `Esc` = Close |

### Color Contrast Verification

| Element | Foreground | Background | Ratio | Pass? |
|---------|------------|------------|-------|-------|
| Body text | #333333 | #FFFFFF | 12.6:1 | AA |
| Primary button | #FFFFFF | #0066CC | 5.9:1 | AA |
| Error text | #CC0000 | #FFFFFF | 5.9:1 | AA |
| Placeholder | #666666 | #FFFFFF | 5.7:1 | AA |
| Disabled | #999999 | #F5F5F5 | 2.8:1 | UI only |
| Link | #0066CC | #FFFFFF | 5.9:1 | AA |

---

## Part 5: Component Library

### Button Component

**Variants:**

| Variant | Usage | Example |
|---------|-------|---------|
| **Primary** | Actions principales (CTA) | "Creer mon compte", "Envoyer" |
| **Secondary** | Actions secondaires | "Annuler", "Plus tard" |
| **Tertiary** | Actions discretes | "En savoir plus", liens inline |
| **Destructive** | Actions dangereuses | "Supprimer", "Oublier ce contact" |
| **Ghost** | Actions minimales | Icones seules, fermer |

**Specs:**

```
Button - Primary
├── Height: 48px (touch-friendly)
├── Padding: 16px 24px
├── Border-radius: 8px
├── Font: 16px, 600 weight
├── Background: Primary (--primary)
├── Text: White (#FFFFFF)
├── Min-width: 120px (desktop), 100% (mobile CTA)
│
├── States:
│   ├── Default: bg --primary
│   ├── Hover: bg --primary-dark (darken 10%)
│   ├── Focus: outline 2px --primary, offset 2px
│   ├── Active: bg --primary-darker (darken 20%)
│   ├── Disabled: opacity 50%, cursor not-allowed
│   └── Loading: spinner icon, disabled
│
└── Accessibility:
    ├── Min touch target: 44x44px
    ├── Focus indicator visible
    └── aria-disabled when disabled
```

### Card Component

**Variants:**

| Variant | Usage |
|---------|-------|
| **Contact Card** | Liste contacts, resultats recherche |
| **Email Card** | Liste emails inbox |
| **Info Card** | Dashboard stats |
| **Action Card** | Choix module, nouvelle generation |
| **Alert Card** | Notifications, alertes |

**Contact Card Specs:**

```
Contact Card
├── Structure:
│   ├── Photo (48x48px, cercle)
│   ├── Name (H3, 16px, 600)
│   ├── Role + Company (14px, --text-secondary)
│   ├── Score bar (optional)
│   └── Quick actions (icons)
│
├── Sizing:
│   ├── Desktop: 300px width (grid)
│   ├── Mobile: 100% width (list)
│   └── Padding: 16px
│
├── States:
│   ├── Default: elevation-1
│   ├── Hover: elevation-2
│   ├── Selected: border --primary
│   └── Focus: outline 2px
│
└── Responsive:
    ├── Desktop: 3 columns
    ├── Tablet: 2 columns
    └── Mobile: 1 column (list view)
```

### Form Input Component

**Variants:**

| Variant | Usage |
|---------|-------|
| **Text** | Nom, email, general |
| **Password** | Mot de passe (avec toggle visibility) |
| **Search** | Barre de recherche |
| **Textarea** | Messages, descriptions |
| **Select** | Dropdowns |

**Specs:**

```
Input - Text
├── Height: 48px
├── Padding: 12px 16px
├── Border: 1px solid --border
├── Border-radius: 8px
├── Font: 16px (prevent zoom mobile)
├── Background: #FFFFFF
│
├── States:
│   ├── Default: border --border
│   ├── Focus: border --primary (2px)
│   ├── Error: border --error
│   ├── Disabled: bg --bg-disabled
│   └── Filled: border --border-strong
│
├── Structure:
│   ├── Label (above, required)
│   ├── Input field
│   ├── Help text (optional, below)
│   └── Error message (below, red)
│
└── Accessibility:
    ├── label[for] linked to input[id]
    ├── aria-required="true" if required
    ├── aria-invalid="true" if error
    └── aria-describedby for help/error text
```

### Badge Component

**Variants:**

| Variant | Color | Usage |
|---------|-------|-------|
| **VIP** | Gold (#FFD700) | Contacts VIP |
| **Deal** | Green (#00AA44) | Opportunites |
| **Urgent** | Red (#CC0000) | Alertes urgentes |
| **New** | Blue (#0066CC) | Nouveaux elements |
| **Score** | Variable | Score de confiance |

**Specs:**

```
Badge
├── Height: 24px
├── Padding: 4px 8px
├── Border-radius: 12px (pill)
├── Font: 12px, 600 weight
├── Text-transform: uppercase
│
└── Accessibility:
    └── aria-label descriptif si icone seule
```

### Navigation Component

**Desktop:**

```
Navigation (Desktop)
├── Height: 64px
├── Position: fixed top
├── Background: #FFFFFF
├── Shadow: elevation-1
│
├── Structure:
│   ├── Logo (left, 40x40px)
│   ├── Nav items (center)
│   │   ├── People | Memory | Builder | Content
│   │   └── Active: underline, --primary
│   ├── Notifications (right, bell icon)
│   └── Avatar + dropdown (right)
│
└── Mobile:
    ├── Hamburger menu (left)
    ├── Logo (center)
    └── Avatar (right)
```

**Mobile Bottom Nav:**

```
Bottom Navigation (Mobile)
├── Height: 64px
├── Position: fixed bottom
├── Background: #FFFFFF
├── Shadow: elevation-2 (top)
│
├── Items: 4-5 max
│   ├── Icon (24x24px)
│   ├── Label (10px)
│   └── Active: --primary, filled icon
│
└── Accessibility:
    ├── role="navigation"
    └── aria-current="page" on active
```

### Score Meter Component

**Pour afficher le Score de Connaissance et Score de Confiance:**

```
Score Meter
├── Structure:
│   ├── Label (optional)
│   ├── Progress bar
│   │   ├── Background: --bg-secondary
│   │   ├── Fill: gradient based on value
│   │   └── Height: 8px
│   └── Value (percentage)
│
├── Colors by value:
│   ├── 0-30%: --error (red)
│   ├── 31-60%: --warning (orange)
│   ├── 61-80%: --primary (blue)
│   └── 81-100%: --success (green)
│
└── Accessibility:
    ├── role="meter"
    ├── aria-valuenow, aria-valuemin, aria-valuemax
    └── aria-label descriptif
```

### Modal Component

```
Modal
├── Overlay: rgba(0,0,0,0.5)
├── Container:
│   ├── Max-width: 480px (small), 640px (medium), 800px (large)
│   ├── Background: #FFFFFF
│   ├── Border-radius: 16px
│   ├── Padding: 24px
│   └── Shadow: elevation-3
│
├── Structure:
│   ├── Close button (top right)
│   ├── Title (H2)
│   ├── Content
│   └── Actions (buttons, bottom right)
│
└── Accessibility:
    ├── role="dialog"
    ├── aria-modal="true"
    ├── aria-labelledby (title)
    ├── Focus trap
    └── Escape to close
```

### Toast / Notification Component

```
Toast
├── Position: bottom-right (desktop), bottom-center (mobile)
├── Max-width: 400px
├── Padding: 16px
├── Border-radius: 8px
├── Shadow: elevation-2
│
├── Variants:
│   ├── Success: --success bg
│   ├── Error: --error bg
│   ├── Warning: --warning bg
│   └── Info: --primary bg
│
├── Structure:
│   ├── Icon (left)
│   ├── Message (center)
│   └── Close button (right, optional)
│
├── Behavior:
│   ├── Auto-dismiss: 5s
│   └── Swipe to dismiss (mobile)
│
└── Accessibility:
    ├── role="alert" or "status"
    ├── aria-live="polite" or "assertive"
    └── Focus on dismissable action if critical
```

---

## Part 6: Design Tokens

### Colors

```css
:root {
  /* Primary Palette */
  --primary: #0066CC;
  --primary-light: #3385D6;
  --primary-dark: #004C99;
  --primary-darker: #003366;

  /* Semantic Colors */
  --success: #00AA44;
  --success-light: #E6F7ED;
  --warning: #FF8800;
  --warning-light: #FFF3E0;
  --error: #CC0000;
  --error-light: #FFEBEE;
  --info: #0066CC;
  --info-light: #E3F2FD;

  /* Neutral Palette */
  --white: #FFFFFF;
  --gray-50: #F9FAFB;
  --gray-100: #F3F4F6;
  --gray-200: #E5E7EB;
  --gray-300: #D1D5DB;
  --gray-400: #9CA3AF;
  --gray-500: #6B7280;
  --gray-600: #4B5563;
  --gray-700: #374151;
  --gray-800: #1F2937;
  --gray-900: #111827;

  /* Semantic Aliases */
  --text-primary: var(--gray-800);
  --text-secondary: var(--gray-600);
  --text-tertiary: var(--gray-500);
  --text-inverse: var(--white);

  --bg-primary: var(--white);
  --bg-secondary: var(--gray-50);
  --bg-tertiary: var(--gray-100);
  --bg-disabled: var(--gray-100);

  --border: var(--gray-300);
  --border-strong: var(--gray-400);
  --border-focus: var(--primary);

  /* Special */
  --badge-vip: #FFD700;
  --badge-deal: #00AA44;
  --badge-urgent: #CC0000;
  --badge-new: #0066CC;
}
```

### Typography

```css
:root {
  /* Font Family */
  --font-primary: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, Arial, sans-serif;
  --font-mono: "SF Mono", Monaco, "Cascadia Code", monospace;

  /* Font Sizes */
  --text-xs: 12px;
  --text-sm: 14px;
  --text-base: 16px;
  --text-lg: 18px;
  --text-xl: 20px;
  --text-2xl: 24px;
  --text-3xl: 30px;
  --text-4xl: 36px;
  --text-5xl: 48px;

  /* Font Weights */
  --font-normal: 400;
  --font-medium: 500;
  --font-semibold: 600;
  --font-bold: 700;

  /* Line Heights */
  --leading-tight: 1.25;
  --leading-snug: 1.375;
  --leading-normal: 1.5;
  --leading-relaxed: 1.625;
  --leading-loose: 2;
}

/* Typography Scale */
.heading-1 {
  font-size: var(--text-4xl);
  font-weight: var(--font-bold);
  line-height: var(--leading-tight);
}

.heading-2 {
  font-size: var(--text-3xl);
  font-weight: var(--font-semibold);
  line-height: var(--leading-tight);
}

.heading-3 {
  font-size: var(--text-2xl);
  font-weight: var(--font-semibold);
  line-height: var(--leading-snug);
}

.heading-4 {
  font-size: var(--text-xl);
  font-weight: var(--font-semibold);
  line-height: var(--leading-snug);
}

.body-large {
  font-size: var(--text-lg);
  font-weight: var(--font-normal);
  line-height: var(--leading-relaxed);
}

.body {
  font-size: var(--text-base);
  font-weight: var(--font-normal);
  line-height: var(--leading-normal);
}

.body-small {
  font-size: var(--text-sm);
  font-weight: var(--font-normal);
  line-height: var(--leading-normal);
}

.caption {
  font-size: var(--text-xs);
  font-weight: var(--font-normal);
  line-height: var(--leading-normal);
}
```

### Spacing

```css
:root {
  /* Base unit: 4px */
  --space-1: 4px;
  --space-2: 8px;
  --space-3: 12px;
  --space-4: 16px;
  --space-5: 20px;
  --space-6: 24px;
  --space-8: 32px;
  --space-10: 40px;
  --space-12: 48px;
  --space-16: 64px;
  --space-20: 80px;
  --space-24: 96px;

  /* Semantic Spacing */
  --padding-card: var(--space-4);
  --padding-section: var(--space-6);
  --padding-page: var(--space-6);

  --gap-items: var(--space-4);
  --gap-sections: var(--space-8);

  /* Layout */
  --container-max: 1200px;
  --sidebar-width: 280px;
  --header-height: 64px;
  --bottom-nav-height: 64px;
}
```

### Shadows

```css
:root {
  --elevation-1: 0 1px 3px rgba(0, 0, 0, 0.1), 0 1px 2px rgba(0, 0, 0, 0.06);
  --elevation-2: 0 4px 6px rgba(0, 0, 0, 0.1), 0 2px 4px rgba(0, 0, 0, 0.06);
  --elevation-3: 0 10px 15px rgba(0, 0, 0, 0.1), 0 4px 6px rgba(0, 0, 0, 0.05);
  --elevation-4: 0 20px 25px rgba(0, 0, 0, 0.1), 0 10px 10px rgba(0, 0, 0, 0.04);
}
```

### Border Radius

```css
:root {
  --radius-sm: 4px;
  --radius-md: 8px;
  --radius-lg: 12px;
  --radius-xl: 16px;
  --radius-2xl: 24px;
  --radius-full: 9999px;
}
```

### Transitions

```css
:root {
  --transition-fast: 150ms ease;
  --transition-normal: 250ms ease;
  --transition-slow: 350ms ease;
}
```

### Breakpoints

```css
/* Mobile First Approach */
/* Base styles: 320px+ (mobile) */

/* Tablet: 768px+ */
@media (min-width: 768px) { }

/* Desktop: 1024px+ */
@media (min-width: 1024px) { }

/* Large Desktop: 1280px+ */
@media (min-width: 1280px) { }
```

### Z-Index Scale

```css
:root {
  --z-base: 0;
  --z-dropdown: 100;
  --z-sticky: 200;
  --z-fixed: 300;
  --z-modal-backdrop: 400;
  --z-modal: 500;
  --z-popover: 600;
  --z-tooltip: 700;
  --z-toast: 800;
}
```

---

## Part 7: Developer Handoff

### Implementation Priorities

#### Phase 1 - Foundation (Sprint 1-2)

1. **Design System Setup**
   - Implementer les design tokens (CSS custom properties)
   - Creer les composants de base (Button, Input, Card)
   - Mettre en place le grid system responsive

2. **Auth & Core**
   - Login, Signup, Forgot Password
   - Navigation (header, mobile bottom nav)
   - Page layout template

#### Phase 2 - Spider People MVP (Sprint 3-5)

1. **Onboarding**
   - Wizard connexion sources
   - Progress sync

2. **Dashboard**
   - Layout dashboard
   - Cards "A traiter", "Prochain RDV", "Alertes"

3. **Inbox**
   - Liste emails filtree
   - Detail email + suggestion reponse

4. **Contacts**
   - Liste contacts
   - Fiche contact detail
   - Brief avant RDV (mobile-first)

#### Phase 3 - Spider Builder MVP (Sprint 6-7)

1. **Wizard Onboarding**
2. **Documents (PRD, Architecture)**
3. **Dashboard + Guards**

#### Phase 4 - Spider Content MVP (Sprint 8-9)

1. **Dashboard Content**
2. **Generation Photo**
3. **Brand Kit Editor**

#### Phase 5 - Polish (Sprint 10)

1. **Memory Dashboard**
2. **Flashcards Validation**
3. **Animations et micro-interactions**

### Responsive Implementation

```css
/* Mobile-first base styles */
.container {
  padding: var(--space-4);
  width: 100%;
}

.grid {
  display: flex;
  flex-direction: column;
  gap: var(--space-4);
}

/* Tablet: 768px+ */
@media (min-width: 768px) {
  .container {
    padding: var(--space-6);
  }

  .grid {
    flex-direction: row;
    flex-wrap: wrap;
  }

  .grid > * {
    flex: 0 0 calc(50% - var(--space-4));
  }
}

/* Desktop: 1024px+ */
@media (min-width: 1024px) {
  .container {
    max-width: var(--container-max);
    margin: 0 auto;
  }

  .grid > * {
    flex: 0 0 calc(33.333% - var(--space-4));
  }
}
```

### Component Implementation Examples

#### Button Component (React/Vue pattern)

```tsx
// Types
type ButtonVariant = 'primary' | 'secondary' | 'tertiary' | 'destructive' | 'ghost';
type ButtonSize = 'sm' | 'md' | 'lg';

interface ButtonProps {
  variant?: ButtonVariant;
  size?: ButtonSize;
  disabled?: boolean;
  loading?: boolean;
  fullWidth?: boolean;
  children: React.ReactNode;
  onClick?: () => void;
  type?: 'button' | 'submit';
  'aria-label'?: string;
}

// CSS Classes
.btn {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  gap: var(--space-2);
  font-weight: var(--font-semibold);
  border-radius: var(--radius-md);
  transition: all var(--transition-fast);
  cursor: pointer;
  min-height: 44px; /* touch target */
}

.btn:focus-visible {
  outline: 2px solid var(--primary);
  outline-offset: 2px;
}

.btn--primary {
  background: var(--primary);
  color: var(--white);
}

.btn--primary:hover:not(:disabled) {
  background: var(--primary-dark);
}

.btn--md {
  height: 48px;
  padding: 0 var(--space-6);
  font-size: var(--text-base);
}

.btn--full-width {
  width: 100%;
}

.btn:disabled {
  opacity: 0.5;
  cursor: not-allowed;
}
```

#### Score Meter Component

```tsx
interface ScoreMeterProps {
  value: number; // 0-100
  label?: string;
  showValue?: boolean;
  size?: 'sm' | 'md' | 'lg';
}

// Implementation
<div
  role="meter"
  aria-valuenow={value}
  aria-valuemin={0}
  aria-valuemax={100}
  aria-label={label || `Score: ${value}%`}
  className="score-meter"
>
  <div
    className="score-meter__fill"
    style={{ width: `${value}%` }}
    data-level={getScoreLevel(value)}
  />
  {showValue && <span className="score-meter__value">{value}%</span>}
</div>

// CSS
.score-meter {
  height: 8px;
  background: var(--gray-200);
  border-radius: var(--radius-full);
  overflow: hidden;
}

.score-meter__fill {
  height: 100%;
  transition: width var(--transition-normal);
}

.score-meter__fill[data-level="low"] { background: var(--error); }
.score-meter__fill[data-level="medium"] { background: var(--warning); }
.score-meter__fill[data-level="high"] { background: var(--primary); }
.score-meter__fill[data-level="excellent"] { background: var(--success); }
```

### Accessibility Testing Checklist

- [ ] **Keyboard Navigation**
  - Tab through all interactive elements
  - Enter/Space activates buttons
  - Arrow keys navigate within components
  - Escape closes modals/dropdowns

- [ ] **Screen Reader Testing**
  - Test with VoiceOver (Mac) / NVDA (Windows)
  - All images have alt text
  - Form labels announced correctly
  - Error messages announced

- [ ] **Visual Testing**
  - Color contrast passes (4.5:1 text, 3:1 UI)
  - Zoom to 200% - no content loss
  - 320px viewport - no horizontal scroll
  - Focus indicators visible

- [ ] **Automated Testing**
  - Run axe-core on all pages
  - Run WAVE browser extension
  - Run Lighthouse accessibility audit

### Assets Needed

**Icons:**
- Utiliser une bibliotheque comme Lucide Icons ou Heroicons
- Format SVG, 24x24px standard
- Inclure aria-hidden="true" si decoratif

**Images:**
- Placeholder avatars (SVG ou generated)
- Logos modules Spider (SVG)
- Illustrations onboarding (optional)

**Fonts:**
- System fonts (pas de web fonts pour perf)
- Font stack: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif

---

## Part 8: Validation

### Requirements Coverage

| FR ID | Requirement | Screen(s) |
|-------|-------------|-----------|
| FR-001 | Stockage vectoriel | Backend (pas d'UI directe) |
| FR-002 | Recherche semantique | MEM-02, PPL-14 |
| FR-003 | API Memory | Backend |
| FR-004 | Score de confiance | PPL-10 (badge), MEM-01 |
| FR-005 | Extraction auto | Backend + PPL-10 |
| FR-006 | Memory Dashboard | MEM-01, MEM-02, MEM-03 |
| FR-007 | Flashcards validation | PPL-12 |
| FR-008 | Mode oublie-moi | MEM-06 |
| FR-009 | Recherche cross-modules | Header search |
| FR-010 | Capture emails | PPL-02 (onboarding) |
| FR-011 | Capture calls | PPL-04 (onboarding) |
| FR-012 | Capture calendrier | PPL-03 (onboarding) |
| FR-014 | Creation fiches contacts | PPL-10 |
| FR-015 | Score de connaissance | PPL-10 |
| FR-016 | Brief avant RDV | PPL-11 |
| FR-017 | Inbox filtree | PPL-07 |
| FR-018 | Messages suggeres | PPL-08 |
| FR-029 | Wizard onboarding Builder | BLD-02, BLD-03, BLD-04 |
| FR-030 | Generation PRD | BLD-05 |
| FR-031 | Generation architecture | BLD-06 |
| FR-041 | Generation photos | CNT-02 |
| FR-042 | Generation videos | CNT-03 |
| FR-043 | Brand kit | CNT-04 |
| FR-053 | Authentification | CORE-02, CORE-03 |
| FR-054 | Onboarding | CORE-06, PPL-01 |
| FR-060 | Homepage | CORE-01 / WEB-01 |

### Accessibility Compliance Summary

| Critere WCAG | Statut | Notes |
|--------------|--------|-------|
| 1.1.1 Non-text Content | Prevu | Alt text requis sur toutes images |
| 1.3.1 Info and Relationships | Prevu | HTML semantique |
| 1.4.3 Contrast | Prevu | Palette verifiee 4.5:1 |
| 2.1.1 Keyboard | Prevu | Tab order defini |
| 2.4.7 Focus Visible | Prevu | Focus outline 2px |
| 3.3.1 Error Identification | Prevu | Erreurs en rouge + texte |
| 4.1.2 Name Role Value | Prevu | ARIA labels definis |

### Sign-off Checklist

- [ ] Product Manager reviewed (Nathan)
- [ ] System Architect reviewed (Remy)
- [ ] Design covers all Must Have FRs
- [ ] Accessibility WCAG 2.1 AA compliant
- [ ] Responsive on desktop + mobile
- [ ] Design tokens documented
- [ ] Components specified
- [ ] Developer handoff complete
- [ ] Ready for implementation

---

## Next Steps

### Recommended Actions

1. **Review with Product Manager**
   - Valider que tous les FRs sont couverts
   - Confirmer la priorite des ecrans
   - Approuver la direction design

2. **Architecture Review**
   - Run: `/architecture`
   - Valider la faisabilite technique
   - Identifier les contraintes backend

3. **Prototype (optionnel)**
   - Creer un prototype Figma si necessaire
   - Tester avec utilisateurs reels

4. **Sprint Planning**
   - Run: `/sprint-planning`
   - Decouper en stories implementables
   - Estimer les efforts

5. **Implementation**
   - Run: `/dev-story`
   - Commencer par le design system
   - Puis les composants de base

---

## Appendix A: Screen Count Summary

| Module | Must Have | Should Have | Could Have | Total |
|--------|-----------|-------------|------------|-------|
| Core | 8 | 2 | 0 | 10 |
| Spider People | 10 | 5 | 0 | 15 |
| Spider Memory | 0 | 6 | 0 | 6 |
| Spider Builder | 8 | 2 | 0 | 10 |
| Spider Content | 6 | 4 | 0 | 10 |
| Site Web | 5 | 1 | 1 | 7 |
| **Total** | **37** | **20** | **1** | **58** |

---

## Appendix B: Mobile-First Screens Priority

Les ecrans suivants sont concus mobile-first car ils sont principalement utilises sur mobile :

1. **PPL-11: Brief Avant RDV** - Commercial en deplacement
2. **PPL-12: Flashcards Validation** - Quick actions, swipe
3. **PPL-06: Dashboard People** - Check rapide avant RDV
4. **PPL-07: Inbox** - Reponses rapides

---

*Generated by BMAD Method v6 - UX Designer*
*Design Date: 2026-01-18*
