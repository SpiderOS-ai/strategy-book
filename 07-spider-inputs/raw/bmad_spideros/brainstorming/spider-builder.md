# Brainstorming Session: Spider Builder

**Date:** 2026-01-13
**Facilitateur:** Creative Intelligence (BMAD)
**Participant:** Nathan Menard
**Duree:** ~45 minutes
**Priorité:** P0 — MVP
**Pricing:** Crédits (modèle Lovable-style)

---

## Objectif

Definir les fonctionnalites, Jobs-to-be-Done, problemes cles et hypotheses pour Spider Builder — le module de developpement AI-assisted de SpiderOS.

## Techniques utilisees

1. **Jobs-to-be-Done Deep Dive** — Comprendre les vrais jobs des utilisateurs
2. **Reverse Brainstorming** — "Comment faire echouer un projet vibe coding ?"
3. **Starbursting** — Explorer systematiquement (Who/What/Where/When/Why/How)

---

# Contexte

## Utilisateurs

| Persona | Role | Priorite |
|---------|------|----------|
| **Remy (CTO)** | Construire SpiderOS et modules | Principal |
| **Devs Drakkar** | Modules clients, maintenance | Principal |
| **Nathan (CEO)** | Voir l'avancement, comprendre les choix | Secondaire |
| **Non-devs** | Mockups pour closer les clients | Secondaire |

## Positionnement marche

- Marche AI coding : **14,62 milliards USD d'ici 2033** (CAGR 15,31%)
- **85% des developpeurs** utilisent deja un outil IA
- Probleme majeur : **1,7x plus d'issues** avec code AI-genere
- Gap identifie : **aucun concurrent n'integre de methodologie**

---

# Jobs-to-be-Done

| # | JTBD |
|---|------|
| **1** | **Ne plus se retrouver avec un projet qui part en vrille** — "Quand mon projet vibe coding grossit et que je me rends compte que l'IA a fait n'importe quoi (vieilles libs, code mal structure, pas de design system, boucles infinies), je veux un cadre qui empeche ca des le depart, pour que je puisse scaler sans avoir a tout jeter." |
| **2** | **Collaborer sans friction** — "Quand j'ai un projet ambitieux et que je veux mettre quelqu'un d'autre dessus, je veux pouvoir transmettre le contexte facilement, pour que ce soit plus rapide que de tout faire moi-meme." |
| **3** | **Ne pas perdre de temps sur la gestion de projet** — "Quand je dois decouper en US, documenter, suivre l'avancement, je veux que ce soit automatise, pour que ca aille aussi vite que le vibe coding." |
| **4** | **L'IA qui respecte les regles** — "Quand l'IA code, je veux qu'elle respecte le design system, le template technique, les conventions, pour qu'elle ne prenne pas de libertes stupides." |
| **5** | **Comprendre et maitriser son projet** — "Quand je travaille sur un projet, je veux voir comment ca fonctionne (agents, flow, choix), avoir une vue step-by-step, pour etre en maitrise de A a Z." |

---

# Problemes cles identifies

## Le probleme fondamental

> "Faut pas se leurrer, quand on fait du vibe coding, les gens ne lisent pas le code."

L'IA dit qu'elle suit les guidelines, mais elle hallucine. Et personne ne verifie. La dette technique s'accumule invisiblement jusqu'au moment ou tout s'effondre.

## Liste des problemes

| # | Probleme | Impact |
|---|----------|--------|
| **P1** | Personne ne lit le code en vibe coding | Dette invisible qui s'accumule |
| **P2** | L'IA dit qu'elle suit les guidelines mais non | Fausse confiance, mauvaises surprises |
| **P3** | Pas de cadrage initial | Decisions arbitraires des le jour 1 |
| **P4** | Contexte qui explose quand ca grossit | L'IA perd le fil, hallucine plus |
| **P5** | Impossible de collaborer | Contexte non transmissible |
| **P6** | Boucles infinies | L'IA tourne en rond sans resoudre |
| **P7** | L'IA ne voit pas visuellement | UI incoherente si pas de design system strict |
| **P8** | Gestion de projet manuelle trop lente | Ecrire les US a la main = plus lent que coder |
| **P9** | Pas de plateforme visuelle | On ne voit rien, BMAD c'est du CLI |

---

# Reverse Brainstorming

## Question : "Comment garantir qu'un projet vibe coding echoue ?"

| Anti-pattern | Probleme reel | Solution Spider Builder |
|--------------|---------------|------------------------|
| Pas de cadre initial | L'IA prend des decisions arbitraires | **Onboarding guide** |
| Guidelines absentes | L'IA ignore conventions | **Rules engine** |
| L'IA choisit les libs | Vieilles libs, hallucinations | **Stack verrouillee** |
| Jamais de review | Dette invisible | **Review continue** |
| Pas de tests | Bugs, regressions | **Tests obligatoires** |
| Contexte qui explose | L'IA perd le fil | **Context manager** |
| Boucles infinies | L'IA tourne en rond | **Loop detection** |
| Travail solo | Impossible de collaborer | **Etat partage** |
| Pas de suivi | On sait pas ou on en est | **Tracking auto** |
| Design system ignore | UI incoherente | **Validation design** |
| Boite noire | Perte de controle | **Transparence** |
| Pas de plateforme | On ne voit rien | **SaaS visuel** |

## Les 3 cercles de l'echec

```
┌─────────────────────────────────────────────────────────┐
│                    ECHEC GARANTI                        │
│                                                         │
│   ┌─────────────────┐                                   │
│   │   DEMARRAGE     │  Pas de cadre                     │
│   │   (Jour 1)      │  Pas de stack definie             │
│   │                 │  Pas de regles                    │
│   └────────┬────────┘                                   │
│            ▼                                            │
│   ┌─────────────────┐                                   │
│   │   EXECUTION     │  Pas de review                    │
│   │   (Pendant)     │  Pas de tests                     │
│   │                 │  Boucles infinies                 │
│   │                 │  Boite noire                      │
│   └────────┬────────┘                                   │
│            ▼                                            │
│   ┌─────────────────┐                                   │
│   │   SCALE         │  Contexte explose                 │
│   │   (Ca grossit)  │  Pas de collab possible           │
│   │                 │  Pas de suivi                     │
│   │                 │  Dette invisible                  │
│   └─────────────────┘                                   │
└─────────────────────────────────────────────────────────┘
```

**Insight cle:** Spider Builder doit intervenir aux 3 moments avec des "gates" qui empechent de passer a la suite si les conditions ne sont pas remplies.

---

# Architecture Spider Builder

```
┌─────────────────────────────────────────────────────────────────┐
│                      SPIDER BUILDER                              │
│                                                                  │
│  ┌──────────────────────────────────────────────────────────┐   │
│  │                    PHASE 1 : SETUP                        │   │
│  │                                                           │   │
│  │  ┌─────────────┐  ┌─────────────┐  ┌─────────────┐       │   │
│  │  │   Wizard    │  │   Visual    │  │   Rules     │       │   │
│  │  │  Onboarding │→ │  Preview    │→ │   Config    │       │   │
│  │  │             │  │  (DA, UI)   │  │             │       │   │
│  │  └─────────────┘  └─────────────┘  └─────────────┘       │   │
│  │                                                           │   │
│  │  Outputs: PRD, Architecture, Design System, Stack         │   │
│  └──────────────────────────────────────────────────────────┘   │
│                              ▼                                   │
│  ┌──────────────────────────────────────────────────────────┐   │
│  │                  PHASE 2 : EXECUTION                      │   │
│  │                                                           │   │
│  │  ┌─────────────┐  ┌─────────────┐  ┌─────────────┐       │   │
│  │  │   Claude    │  │   Agents    │  │   Hooks &   │       │   │
│  │  │   Code ++   │← │   Guards    │← │   Checks    │       │   │
│  │  │             │  │             │  │             │       │   │
│  │  └─────────────┘  └─────────────┘  └─────────────┘       │   │
│  │                                                           │   │
│  │  Guards: Stack, Design System, Tests, Qualite, Loops     │   │
│  └──────────────────────────────────────────────────────────┘   │
│                              ▼                                   │
│  ┌──────────────────────────────────────────────────────────┐   │
│  │              PHASE 3 : PLATEFORME (SaaS)                  │   │
│  │                                                           │   │
│  │  Vue Projet │ Vue Agents │ Vue Qualite │ Vue Collab      │   │
│  │                                                           │   │
│  └──────────────────────────────────────────────────────────┘   │
└─────────────────────────────────────────────────────────────────┘
```

---

# Fonctionnalites par categorie

## Categorie 1 : Setup & Cadrage (GATE #1)

| Feature | Description | Priorite |
|---------|-------------|----------|
| **Wizard onboarding** | Questions guidees pour definir le projet | P0 |
| **Visual preview DA** | Voir fontes, couleurs, exemples avant de coder | P0 |
| **Stack selector** | Choisir/valider les libs approuvees | P0 |
| **Rules config** | Definir les regles du projet (editable) | P0 |
| **PRD auto-genere** | BMAD genere le PRD depuis les inputs | P0 |
| **Architecture auto** | BMAD genere l'archi depuis le PRD | P0 |
| **Wireframing ecrans** | Ecrans principaux avant chaque sprint | P1 |
| **Templates projet** | Ex: "Template SpiderOS" pre-configure | P1 |
| **Import projet** | Analyser un projet existant, deduire les regles | P2 |

## Categorie 2 : Garde-fous Execution (GATE #2)

| Feature | Description | Priorite |
|---------|-------------|----------|
| **Stack guard** | Bloquer si lib non approuvee utilisee | P0 |
| **Design system guard** | Verifier que l'UI respecte la DA | P0 |
| **Loop detection** | Alerter si l'IA tourne en rond | P0 |
| **Test enforcement** | Pas de commit sans tests | P1 |
| **Quality check** | Analyse continue dette technique | P1 |
| **Hallucination detection** | Detecter quand l'IA invente des trucs | P1 |
| **Convention guard** | Verifier patterns, naming, structure | P1 |

## Categorie 3 : Transparence & Controle

| Feature | Description | Priorite |
|---------|-------------|----------|
| **Agent visibility** | Voir quels agents interviennent et pourquoi | P0 |
| **Decision log** | Historique des choix de l'IA | P1 |
| **Rules editor** | Modifier les regles en cours de projet | P1 |
| **Override system** | Forcer une decision si l'IA se trompe | P1 |

## Categorie 4 : Gestion de projet auto

| Feature | Description | Priorite |
|---------|-------------|----------|
| **US auto-link** | Relier le code aux user stories | P0 |
| **Progress tracking** | Voir l'avancement auto | P0 |
| **Status sync** | Fichiers YAML/JSON mis a jour auto | P0 |
| **Sprint view** | Vue type kanban des US | P1 |
| **JTBD forces** | Output obligatoire en setup | P1 |
| **VPC (Value Proposition Canvas)** | Livrable de cadrage | P1 |

## Categorie 5 : Collaboration

| Feature | Description | Priorite |
|---------|-------------|----------|
| **Shared state** | Etat projet partage entre devs | P1 |
| **Context handoff** | Transmettre le contexte a un autre dev | P1 |
| **Multi-session** | Plusieurs devs en parallele | P2 |

## Categorie 6 : Plateforme SaaS

| Feature | Description | Priorite |
|---------|-------------|----------|
| **Project overview** | Vue globale du projet | P1 |
| **Agent activity** | Qui fait quoi en temps reel | P1 |
| **Quality metrics** | Dette, coverage, issues | P1 |
| **Design preview** | Voir l'UI sans ouvrir le code | P1 |
| **Collaboration hub** | Espace partage pour l'equipe | P1 |

---

# MVP Spider Builder

```
MVP = Setup guide + Garde-fous de base + Tracking auto

┌─────────────────────────────────────────────────┐
│                MVP SPIDER BUILDER               │
│                                                 │
│  SETUP (P0)                                     │
│  ├── Wizard onboarding                          │
│  ├── Visual preview (DA, fontes, couleurs)      │
│  ├── Stack selector                             │
│  ├── Rules config                               │
│  └── PRD + Architecture auto (BMAD)             │
│                                                 │
│  GARDE-FOUS (P0)                                │
│  ├── Stack guard                                │
│  ├── Design system guard                        │
│  └── Loop detection                             │
│                                                 │
│  TRACKING (P0)                                  │
│  ├── US auto-link                               │
│  ├── Progress tracking                          │
│  └── Agent visibility                           │
└─────────────────────────────────────────────────┘

V2 = Plateforme SaaS + Collaboration avancee
```

---

# BMAD++ (Surcouche Drakkar)

BMAD est la base, mais Spider Builder ajoute ce qui manque :

| Ajout Drakkar | Description | Pourquoi |
|---------------|-------------|----------|
| **Plateforme visuelle SaaS** | Voir et collaborer | BMAD c'est du CLI, on ne voit rien |
| **Preview DA visuelle** | Fontes, couleurs, exemples avant de coder | L'IA ne peut pas juger le visuel |
| **Wireframing ecrans** | Ecrans principaux avant chaque sprint | Valider l'UX avant de coder |
| **Jobs-to-be-Done forces** | Output obligatoire | Cadrage product |
| **Value Proposition Canvas** | VPC comme livrable | Methodo Drakkar |
| **Hypotheses cles** | Leap of faith documentees | Valider avant de construire |
| **Design system integre** | HeroUI ou autre comme base obligatoire | L'IA suit des rails visuels |
| **Garde-fous techniques** | Hooks, checks, learning | Compenser les hallucinations |
| **Learnings Drakkar** | Ajustements continus | 6 ans d'experience Product Studio |

---

# Hypotheses Leap of Faith

## Hypotheses de VALEUR

| ID | Hypothese | Test |
|----|-----------|------|
| **HV1** | Les devs Drakkar veulent un cadre methodologique (pas juste coder freestyle) | Remy + equipe adoptent Spider Builder vs Claude Code brut |
| **HV2** | Le setup guide (PRD, archi, DA visuelle) fait gagner du temps | Temps projet avec vs sans Spider Builder |
| **HV3** | Les garde-fous reduisent vraiment la dette technique | Moins de "on doit tout refaire" |
| **HV4** | La transparence (voir les agents, les choix) rassure et aide a debugger | Usage du decision log |

## Hypotheses de FAISABILITE

| ID | Hypothese | Test |
|----|-----------|------|
| **HF1** | On peut detecter automatiquement quand l'IA utilise une lib non approuvee | POC technique |
| **HF2** | On peut verifier automatiquement le respect du design system | POC technique |
| **HF3** | On peut detecter les boucles infinies et alerter | POC technique |
| **HF4** | BMAD peut etre enrichi avec nos ajouts sans tout casser | Implementation surcouche |
| **HF5** | Le tracking US ↔ Code peut etre automatise de maniere fiable | POC technique |

## Hypotheses de VIABILITE

| ID | Hypothese | Test |
|----|-----------|------|
| **HB1** | Spider Builder rend l'equipe Drakkar plus productive | Velocite avant/apres |
| **HB2** | Spider Builder est un argument de vente pour les clients | Feedback clients |

## Priorisation par risque

| Rang | Hypothese | Risque si faux |
|------|-----------|----------------|
| 🔴 1 | **HF1** — Detection libs non approuvees | Pas de garde-fou, l'IA hallucine |
| 🔴 2 | **HV1** — Les devs veulent un cadre | Personne n'utilise Spider Builder |
| 🔴 3 | **HF2** — Verification design system | UI incoherente malgre l'outil |
| 🟠 4 | **HV3** — Garde-fous reduisent la dette | L'outil ne resout pas le probleme |
| 🟠 5 | **HF3** — Detection boucles infinies | Frustration continue |
| 🟠 6 | **HF4** — BMAD++ fonctionne | Surcouche bancale |
| 🟡 7 | **HV2** — Setup fait gagner du temps | Nice-to-have |
| 🟡 8 | **HF5** — Tracking US auto | Tracking manuel reste necessaire |
| 🟢 9 | **HV4** — Transparence rassure | Feature secondaire |
| 🟢 10 | **HB1, HB2** — ROI et vente | Business model a ajuster |

---

# Part 8: Architecture Proxy Localhost — Insights Recherche

**Source:** `research-spider-builder-context-2026-01-13.md`

## Approche unique et differenciante

**Constat:** Aucun concurrent majeur (Cursor, Windsurf, Continue.dev, Cody, Aider) n'utilise un proxy localhost pour enrichir automatiquement les prompts avec le contexte projet.

## Comparaison des architectures

| Approche | Complexite | Maintenance | Flexibilite | Exemple |
|----------|------------|-------------|-------------|---------|
| IDE natif (fork) | Tres haute | Elevee | Faible | Cursor, Windsurf |
| Extension VS Code | Moyenne | Moyenne | Moyenne | Continue.dev, Cody |
| CLI + AST | Faible | Faible | Moyenne | Aider |
| **Proxy localhost** | Moyenne | Faible | **Tres haute** | **Spider Builder** |

## Avantages cles de l'approche proxy

| Avantage | Description |
|----------|-------------|
| **Non-invasif** | Claude Code reste intact, pas de fork a maintenir |
| **Transparent** | Un seul changement config, UX identique pour le dev |
| **Flexible** | Enrichissement dynamique, adaptable a tout contexte |
| **Enterprise-ready** | Logging et audit natifs |

## Enrichissement automatique unique

```
Prompt utilisateur: "Ajoute un bouton de login"

Prompt enrichi par Spider Builder:
---
## Contexte Projet
- PRD: Application SaaS de gestion de projets
- Architecture: Next.js + Supabase
- Design System: HeroUI + Tailwind

## User Story Active
US-042: En tant qu'utilisateur, je veux me connecter...

## Fichiers Pertinents (Spider Indexer)
- src/components/auth/LoginForm.tsx
- src/lib/supabase/auth.ts

## ATTENTION - Composants existants
- Button deja defini dans src/components/ui/Button.tsx

## Agent BMAD actif: Developer
---
```

## Spider Builder vs Concurrents

| Feature | Cursor | Windsurf | Continue | **Spider Builder** |
|---------|--------|----------|----------|-------------------|
| Context injection | @-mentions | Auto (Cascade) | Manuel | **Auto + BMAD** |
| Methodologie | Non | Non | Non | **BMAD integre** |
| User story awareness | Non | Non | Non | **Oui** |
| Design system guard | Non | Non | Non | **Oui** |
| Lock-in | Total | Total | Moyen | **Minimal** |

## Avantage competitif

> **Spider Builder = le seul AI coding assistant avec contexte methodologique automatique.**

Les concurrents font du context retrieval (fichiers pertinents). Spider Builder fait du **context enrichissement intelligent** (fichiers + methodologie + user story + garde-fous).

---

# Contexte technique (info)

Elements existants a prendre en compte (pas dans MVP) :

| Element | Description | Status |
|---------|-------------|--------|
| **Spider Vector** | Base de vectorisation | Existe, pourrait vectoriser le code |
| **Module Remy** | Interface Claude Code + hooks/learning/memoire | En dev |

---

# Comparaison concurrentielle

| Critere | Cursor | Claude Code | Lovable | Spider Builder |
|---------|--------|-------------|---------|----------------|
| Coding qualite | +++++ | +++++ | +++ | +++++ |
| Methodologie | - | + | - | +++++ |
| Design system | - | - | ++++ | +++++ |
| Collaboration | + | + | ++ | ++++ |
| Transparence | + | ++ | + | +++++ |
| Plateforme visuelle | - | - | ++++ | +++++ |
| Import projet | +++ | ++++ | - | +++ |

---

# Statistics

| Metrique | Valeur |
|----------|--------|
| Jobs-to-be-Done | 5 |
| Problemes identifies | 9 |
| Anti-patterns (reverse brainstorm) | 12 |
| Features totales | 30+ |
| Features MVP (P0) | 11 |
| Hypotheses leap of faith | 11 |
| Techniques brainstorming utilisees | 3 |
| Recherches integrees | 1 (context management) |

---

# Next Steps

1. ~~**Recherche approfondie** — `/research` sur les solutions techniques (hooks, guards, detection)~~ DONE
2. **POC techniques** — Valider HF1, HF2, HF3 (detection libs, design system, loops)
3. **PRD Spider Builder** — `/prd` pour specs detaillees
4. **Architecture** — `/architecture` pour design technique

---

*Generated by BMAD Method v6 - Creative Intelligence*
*Session duration: ~45 minutes*
