# SpiderOS — Stack cible

> Date : 2026-02-18
> Sources : stack-decisions.md (59 sections), stack-infra.md, architecture.md, Spider_Architecture_Technique.html, audit Studio Kit (front + backend AdonisJS), spideros-template (GitHub), apps/data/, playbook refacto-ds, setup Claude Code
> **Synthèse opérationnelle unique** de toute la documentation technique SpiderOS.

---

## 1. Vision produit

SpiderOS est une plateforme IA souveraine pour PME/ETI — **4 apps desktop-grade dans le navigateur**, un moteur d'intelligence organisationnelle, et une infra 100% France.

```
Sources (Connecteurs)                          Apps (Consommateurs)
┌──────────────────────┐                      ┌──────────────────────┐
│ Pappers, Google Drive │                      │ Platform (dashboard)  │
│ ERP, Email, Calendar  │     ┌──────────┐    │ People (CRM)          │
│ Consultant input      │ ──→ │  Spider   │ ──→│ Documents (livrables) │
│ Aircall / Noota       │     │  Intel    │    │ Builder (IDE AI)      │
└──────────────────────┘     │  Engine   │    └──────────────────────┘
                              └──────────┘
                                   ↓
                             Knowledge Graph
                              (SurrealDB)
```

### Les 6 apps

| App | URL | Type | Description |
|-----|-----|------|-------------|
| **People** | people.spideros.ai | B (Next.js + Python) | CRM relationnel — timeline, audio, charts, tables virtualisées, Score of Knowledge |
| **Builder** | builder.spideros.ai | B (Next.js + Python) | IDE AI-assisted — Monaco Editor, xterm.js, streaming AI, command palette |
| **Documents** | documents.spideros.ai | B (Next.js + Python) | Éditeur de livrables — Tiptap, reveal.js, export PDF/HTML, AI content generation |
| **Platform** | app.spideros.ai | A/B (Next.js + léger) | Hub post-login, dashboard, 10 livrables Spider Intelligence (L1-L10) |
| **Website** | spideros.ai | A (Next.js seul) | Site corporate — PUBLIC, pas d'auth |
| **Playbook** | interne | A (Next.js seul) | Documentation DS — INTERNE, submodule |

**Type A** = Next.js seul. **Type B** = Next.js + backend Python (Litestar + Piccolo).

---

## 2. Infra souveraine

```
┌─────────────────────────────────────────────────────────┐
│                    OVH + Scaleway (FR)                   │
│    OVH : prod (Roubaix/Gravelines/Strasbourg)           │
│    Scaleway : DR (Paris) — failover <1h, RPO 15min      │
├─────────────────────────────────────────────────────────┤
│   management          staging           production       │
│   (ArgoCD, Harbor,    (preview,         (HA, monitoring,│
│    Vault, builds)      tests E2E)        backups 15min) │
├─────────────────────────────────────────────────────────┤
│                    Higress Gateway                        │
│   OAuth2 · Rate limit · AI routing · Semantic cache      │
│   Multi-provider failover · Content security             │
├──────┬──────┬──────┬──────┬──────┬──────┬───────────────┤
│websit│playbk│platfm│buildr│ docs │people│   Zitadel     │
│      │      │      │      │      │      │   (OIDC SSO)  │
├──────┴──────┴──────┴──────┴──────┴──────┴───────────────┤
│   PostgreSQL 16 HA    SurrealDB        Nomic Embed       │
│   (source vérité)     (graph+vec+doc)  (768D, FR/EN)     │
│   Patroni failover    Live queries WS   Self-hosted GPU  │
│                       Mem0 (mémoire LLM)                 │
└─────────────────────────────────────────────────────────┘
```

| Composant | Rôle |
|-----------|------|
| KubeSphere 4 / K8s | Orchestration 3 clusters |
| ArgoCD | GitOps — git push → deploy auto |
| Higress | Gateway IA centralisée (jamais d'appels LLM directs) |
| PostgreSQL 16 HA | Source de vérité relationnelle (tenants, users, audit trail) |
| SurrealDB | Graph + vector + document + time-series + KV. Knowledge Graph + embeddings. **Remplace Neo4j** (préconisé dans Spider_Architecture_Technique) **+ MongoDB + Pinecone + InfluxDB + PostGIS + Redis** en une seule base. Queries Cypher → SurrealQL (traversée graphe + recherche vectorielle dans la même requête). Louvain/Bradley-Terry côté Python (networkx/scikit-learn) |
| Nomic Embed | Embeddings self-hosted 768D FR/EN, vecteurs dans SurrealDB |
| Mem0 | Mémoire LLM persistante (user/org/session) |
| Zitadel | Auth OIDC self-hosted, SSO cross-apps |

**Souveraineté** : zéro SaaS US. Alternatives self-hosted pour tout (GlitchTip, Umami, Playwright screenshots, Harbor, Vault, Zitadel). Claude API zero-retention.

---

## 3. Monorepo

```
spideros/
├── apps/
│   ├── website/          ← PUBLIC (pas d'auth)
│   ├── playbook/         ← INTERNE (submodule)
│   ├── platform/         ← AUTH (@spideros/auth)
│   ├── builder/          ← AUTH
│   ├── documents/        ← AUTH
│   ├── people/           ← AUTH
│   └── data/             ← AUTH (submodule)
│
├── packages/
│   ├── ui/               ← Design System complet
│   ├── auth/             ← Zitadel (apps AUTH uniquement)
│   ├── api/              ← Hey API + streaming SSE
│   ├── config/           ← tsconfig, biome, tailwind
│   ├── i18n/             ← Labels partagés cross-apps
│   ├── mcp/              ← MCP server pour Claude Code
│   ├── indexer/          ← Pipeline ingestion + connecteurs
│   ├── memory/           ← Client Mem0
│   └── embeddings/       ← Client Nomic Embed
│
├── .claude/              ← Rules Claude Code
├── plugins/              ← spideros-toolchain
├── turbo.json
├── pnpm-workspace.yaml
└── biome.json
```

**Auth vs Public** : la distinction se fait par la présence de `@spideros/auth` dans `package.json` + `middleware.ts` qui redirige vers Zitadel. Website et Playbook n'ont ni l'un ni l'autre.

---

## 4. Architecture frontend

### 4.1 Structure d'une app — Colocation

**Tout ce qui concerne une route vit avec cette route.** Pattern Cal.com / Bulletproof React.

```
apps/people/frontend/src/
├── app/
│   ├── layout.tsx                ← SpiderProviders + ZitadelProvider
│   ├── contacts/
│   │   ├── page.tsx              ← Server Component
│   │   ├── _components/          ← UI spécifique à cette route
│   │   ├── _lib/                 ← Actions, schemas Zod
│   │   ├── locales/fr.json       ← i18n colocalisé
│   │   └── [id]/
│   │       ├── page.tsx
│   │       └── _components/
│   ├── pipeline/
│   ├── analytics/
│   └── callback/page.tsx         ← Seule route publique (OIDC)
│
├── features/                     ← Partagé entre 2+ routes SEULEMENT
│   ├── score-of-knowledge/       ← contacts/ + analytics/
│   └── integrations/             ← gmail/, aircall/, calendar/
│
└── generated/                    ← Hey API (ne pas toucher)
```

### 4.2 Règles de colocation

1. **Route = unité de travail.** Un dev ouvre un dossier route et a tout sous les yeux
2. **`_components/` et `_lib/` sont privés.** Préfixe `_` = natif Next.js, exclus du routing
3. **Règle d'ascension** : `_components/` → `features/` → `packages/ui/`. Un composant monte quand il est utilisé par 2+ routes, puis 2+ apps
4. **`features/` est minimal.** Barrel exports (`index.ts`) obligatoires = API publique
5. **`generated/` ne se touche pas.** Hey API génère, `_lib/` ou `features/` wrappent

### 4.3 i18n — next-intl + colocation

**Lib** : next-intl 4.x — 1.5M+ DL/semaine, RSC first-class, precompilation AOT (v4.8 : ~650 bytes runtime).

**Pourquoi colocalisé** : avec RSC, les JSON restent côté serveur — la structure des fichiers n'a aucun impact bundle. La colocation gagne en DX (cohérent avec `_components/`, moins de merge conflicts).

```
├── i18n/
│   ├── request.ts       ← getRequestConfig() — merge dynamique des locales/*.json
│   └── routing.ts
└── app/
    ├── contacts/
    │   └── locales/fr.json      ← Labels de la route
    └── pipeline/
        └── locales/fr.json
```

**3 couches** (même règle d'ascension) :

| Couche | Où | Quoi |
|--------|----|------|
| Route | `app/contacts/locales/fr.json` | Labels spécifiques |
| Feature | `features/*/locales/fr.json` | Labels partagés entre routes |
| Package | `@spideros/i18n` | Labels communs cross-apps (boutons, erreurs, CRUD) |

**Règles** : Server Components → `getTranslations()` (zéro JS client). Client Components → `useTranslations()` via provider, namespaces minimaux. Precompilation AOT activée. Outillage : i18n-ally ou inlang pour vue centralisée.

### 4.4 Features par app

| App | `features/` | Routes principales |
|-----|-------------|-------------------|
| **People** | `score-of-knowledge/`, `integrations/` (gmail, aircall, calendar), `audio/` (wavesurfer.js) | `contacts/`, `pipeline/`, `analytics/`, `settings/` |
| **Builder** | `editor/` (Monaco), `terminal/` (xterm.js), `chat/` (streaming SSE) | Fichier ouvert (dynamique), `settings/` |
| **Documents** | `tiptap/`, `slides/` (reveal.js), `export/` (PDF/HTML), `ai/` | Document ouvert (dynamique), `templates/`, `settings/` |
| **Platform** | `livrables/` (10 LiveViews L1-L10), `alertes/` | `dashboard/`, `settings/`, livrable par ID |

### 4.5 Pattern LiveView — les 10 livrables

Vues matérialisées du Knowledge Graph. Chaque livrable = query SurrealQL + composant React + politique de refresh.

| # | Livrable | Renderer | Refresh |
|---|----------|----------|---------|
| L1 | Organigramme | D3.js tree | On change |
| L2 | Compétences | Heatmap grid | On change |
| L3 | Porter | SVG layout | Daily |
| L4 | VSM | D3.js flow | On change |
| L5 | SIPOC | Expandable cards | On change |
| L6 | RACI | Matrix grid | On change |
| L7 | Cartographie SI | D3.js diagram | Daily |
| L8 | SNA | D3.js force graph | Hourly |
| L9 | Diagnostic | Risk matrix | On change |
| L10 | Roadmap | Gantt/timeline | Manual |

L1, L4, L7, L8 nécessitent **D3.js** (Recharts ne suffit pas).

---

## 5. Architecture backend

### 5.1 Stack

| Choix | Pourquoi |
|-------|----------|
| **Litestar 2.21+** | ASGI async, DTOs natifs, OpenAPI auto, DI 4 niveaux, guards. Mieux architecturé que FastAPI |
| **Piccolo ORM** | Async-native, migrations auto, query builder propre. Pas besoin de repository pattern |
| **Pydantic 2.0+** | Validation + serialization, source de vérité pour OpenAPI → Hey API codegen |
| **uv** | 100x plus rapide que pip |
| **Ruff** | Linter Python ultra-rapide |

### 5.2 Structure — base spideros-template

Architecture **flat par couche technique**. Les APIs REST restent light (5-20 endpoints par app) — la complexité lourde (connecteurs, intelligence engine) vit dans `engine/` et les packages partagés.

**Le template GitHub (`SpiderOS-ai/spideros-template`) fournit la quasi-totalité de la structure.** On ajoute 3 choses : `tests/factories/`, `engine/`, convention schemas 1:1.

```
backend/
├── src/
│   │
│   │  ── Assemblage ──
│   ├── main.py                    ← Litestar app, compose les ALL_* registries
│   ├── config.py                  ← Pydantic Settings (env vars typées, fail-fast)
│   ├── db.py                      ← Piccolo Engine + connection pool
│   ├── piccolo_conf.py            ← Config Piccolo (migrations, admin)
│   ├── routes.py                  ← TOUTES les routes (source of truth unique)
│   ├── dependencies.py            ← ALL_DEPENDENCIES (agrège providers/)
│   ├── middlewares.py             ← ALL_MIDDLEWARES
│   ├── exception_handlers.py      ← ALL_EXCEPTION_HANDLERS (agrège handlers/)
│   │
│   │  ── Code métier ──
│   ├── controllers/               ← 1 fichier = 1 ressource (fonctions async pures)
│   ├── services/                  ← Logique métier (quand controller grossit)
│   ├── models/                    ← Piccolo Tables (1 fichier = 1 table)
│   ├── schemas/                   ← Pydantic DTOs in/out (1:1 avec controllers)
│   │
│   │  ── Auth & erreurs ──
│   ├── exceptions/                ← Hiérarchie d'exceptions custom par domaine
│   ├── handlers/                  ← Implémentations exception handlers
│   ├── guards/                    ← Auth middleware + guards nommés
│   ├── providers/                 ← Factories DI (Litestar Provide())
│   │
│   │  ── Utilitaires ──
│   ├── lib/                       ← StorageBackend ABC, JWT, Fernet (= utils/ dans le template)
│   ├── integrations/              ← OAuth Google, connecteurs externes
│   ├── mailers/                   ← Templates email
│   ├── migrations/                ← Piccolo migrations auto
│   │
│   │  ── SpiderOS-spécifique ──
│   ├── engine/                    ← Spider Intelligence (claims, resolver, analyzer)
│   └── mcp_server.py              ← FastMCP.from_openapi() (dev-only)
│
├── tests/                         ← Miroir controllers/ + factories/
├── scripts/                       ← Seeding, export OpenAPI
└── pyproject.toml
```

### 5.3 Patterns clés

**`routes.py` centralisé** — vision globale de l'API en un fichier :

```python
ALL_ROUTES = [
    route("/api/auth/login", http_method="POST", tags=["Auth"])(auth.login),
    route("/api/auth/me", http_method="GET", guards=[require_auth], tags=["Auth"])(auth.get_me),
    route("/api/contacts", http_method="GET", guards=[require_auth], tags=["Contacts"])(contacts.list),
]
```

**Controllers = fonctions async pures** — pas de classes, pas de décorateurs, testables unitairement :

```python
async def list(request: Request, db: Engine) -> list[ContactOut]:
    return [ContactOut(**c) for c in
            await Contact.select().where(Contact.tenant_id == request.user.tenant_id)]
```

**Registries `ALL_*`** — composition explicite dans `main.py`, rien de caché :

```python
app = Litestar(
    route_handlers=ALL_ROUTES, dependencies=ALL_DEPENDENCIES,
    middleware=ALL_MIDDLEWARES, exception_handlers=ALL_EXCEPTION_HANDLERS,
)
```

### 5.4 Scaling

Les APIs REST restent light : même People mature ≈ 18 endpoints. Les connecteurs sont de l'ingestion batch, l'analytics est du compute — pas du REST.

| Seuil | Action |
|-------|--------|
| Controller grossit | Extraire la logique dans `services/` |
| Service grossit | Le splitter (`auth.py` → `auth.py` + `oauth.py`) |
| Code partagé cross-apps | Monter dans un package (`@spideros/indexer`, etc.) |

**Règle d'ascension backend** (miroir du front) : controller → service → package partagé. Même principe que `_components/` → `features/` → `packages/ui/`.

### 5.5 Diff exact vs spideros-template

| Catégorie | Détail |
|-----------|--------|
| **Identique** | Toute l'architecture : main.py, config.py, db.py, routes.py, registries ALL_*, controllers/, services/, models/, schemas/, exceptions/, handlers/, guards/, providers/, integrations/, mailers/, migrations/, mcp_server.py, piccolo_conf.py, tests/, scripts/ |
| **Ajouts SpiderOS** | `engine/` (Spider Intelligence), `tests/factories/` (builders par model), convention schemas 1:1 avec controllers |
| **Renommages cosmétiques** | `utils/` → `lib/`, drop suffixe `_controller`/`_service`, split `guards/auth.py` en 2 fichiers |

---

## 6. Spider Intelligence Engine

Le moteur d'intelligence organisationnelle. Vit dans `engine/` des backends et dans les packages partagés.

### 6.1 Pipeline

```
Sources → Connecteurs → Extracteur LLM → Entity Resolver → Claim Engine → Analyseur → LiveViews
```

| Composant | Rôle | Stack |
|-----------|------|-------|
| **Connecteurs** (7 en V1) | Ingestion depuis sources externes | Python async, adapters par source |
| **Extracteur LLM** | Non-structuré → claims | Haiku 4.5 (volume) → Sonnet 4.5 (complexe), via Higress |
| **Entity Resolver** | Déduplication (Fellegi-Sunter) | Jaro-Winkler + contexte. Auto-merge ≥0.94 |
| **Claim Engine** | Combinaison Dempster-Shafer | Belief/Plausibility, conflits K>0.9 |
| **Analyseur batch** | Communautés, autorité, bus factor | networkx, scikit-learn. Horaire ou post-ingestion |
| **LiveView engine** | Matérialisation des 10 livrables | SurrealQL → transform → cache → WebSocket |
| **ATMS simplifié** | Rétractation de claims (cascade) | Recompute global en V1 (<2s pour <2000 claims). Incrémental en V2 |
| **Alertes** | Anomalies (bus factor, conflits) | Pattern Datadog : rules → check → notify |

### 6.2 Data model

- **Entity** : id, type (PERSON/ROLE/PROCESS/SYSTEM/COMPETENCE/...), canonical_name, aliases, tenant_id
- **Claim** : subject_id → predicate → object_id, belief ∈ [0,1], plausibility ∈ [Bel,1], sources[], depends_on[], status (PROPOSED/VALIDATED/REJECTED/SUPERSEDED)
- **14 prédicats** : HOLDS_ROLE, REPORTS_TO, BELONGS_TO, HAS_COMPETENCE, EXECUTES_PROCESS, USES_SYSTEM, COMMUNICATES_WITH, ATTENDS_MEETING, SEQUENCE_AFTER, SIPOC_SUPPLIER, SIPOC_CUSTOMER, CONTAINS_DATA, PORTER_ACTIVITY, RISK_EXPOSURE, TRANSFORMATION_ACTION

**Coût LLM** : ~70€/an pour une PME 150 personnes.

---

## 7. Design System — `@spideros/ui`

Package unique consommé par toutes les apps. Les apps composent des composants DS, elles ne stylent pas.

### 7.1 Structure

```
packages/ui/src/
├── foundations/           ← Tokens CSS (colors, spacing, typography, effects)
│   ├── tokens/            ← .css files (primitives, semantic, gradients)
│   ├── fonts/             ← Kedebideri + JetBrains Mono
│   └── icons/             ← Phosphor via icon-mapping.ts
├── atoms/                 ← ~35 composants indivisibles (Button, Input, Badge, Trait...)
├── molecules/             ← ~15 groupes d'atoms (Card, Dialog, Section, PageHeader...)
├── organisms/             ← ~15 sections autonomes (Navbar, Hero, Footer...)
├── templates/             ← Layouts (AppLayout, WebsiteLayout)
├── providers/             ← SpiderProviders (toast, tooltip)
└── utils/                 ← cn(), toast wrapper
```

**Règle d'import** : un layer importe uniquement les layers inférieurs.

### 7.2 Comment un composant est construit

```
atoms/button/
├── button.tsx           ← CVA variants + wrapper Base UI (ou custom)
├── button.module.css    ← Tokens CSS uniquement, jamais de valeurs en dur
├── button.stories.tsx   ← Storybook
└── index.ts
```

Exemple concret :

```tsx
// button.tsx
const buttonVariants = cva(styles.button, {
  variants: {
    variant: { primary: styles.primary, secondary: styles.secondary, ghost: styles.ghost },
    size: { sm: styles.sm, md: styles.md, lg: styles.lg },
  },
  defaultVariants: { variant: "primary", size: "md" },
});
```

```css
/* button.module.css */
.button { border-radius: var(--radius-md); font-weight: 500; }
.primary { background: var(--color-primary); color: white; }
.sm { padding: var(--spacing-1) var(--spacing-3); font-size: var(--text-sm); }
```

### 7.3 Les 3 niveaux d'abstraction

```
Apps ──→ @spideros/ui ──→ Base UI (headless, ~90%) ou Custom (~10%)
         CSS Modules        Accessibilité, ARIA, keyboard
         + tokens            Aucun style
```

**Règle absolue** : un import `@base-ui/react` dans une app = erreur. Tout passe par `@spideros/ui`.

### 7.4 Stratégie CSS

| Où | Comment |
|----|---------|
| `packages/ui/` foundations | CSS Variables (`--color-bg-base`, `--spacing-section-y`) |
| `packages/ui/` composants | CSS Modules + CVA |
| Apps — layout | Tailwind structurel (`flex`, `grid`, `gap-*`, `py-*`) |
| Apps — visuels | **Interdit** (pas de `bg-teal-500`, `text-white`) |

### 7.5 Identité visuelle — "The Lake"

3 couches, ratio strict :

| Couche | % | Couleurs | Usage |
|--------|---|----------|-------|
| **Surface** | ~70% | Cream #FFFEFC, Warm #FAF9F7, Neutral #F4F4F6 | Contenu courant |
| **Depth** | ~25% | Abysse #022C22, Black #0A0A0A | Trust, Footer. Max 2/page, toujours gradient |
| **Electric** | ~5% | Cyan 500 #00D4EE, 400 #00F5FF | Traits, glows, focus. **Jamais en fond, body text, icônes** |

**Backgrounds** : catalogue fermé.
- **5 fonds plats** : cream, warm, neutral, white, noir
- **12 gradients** : warm (radial, subtle), neutral (radial, subtle), bridge (depth-tint, depth-emergence), depth (abysse, abysse-vertical, abysse-deep, abysse-radial), primary (2)
- **2 text gradients** : primary, secondary
- Source : `packages/ui/src/foundations/tokens/colors.gradients.css`

**Typography** : Kedebideri (6 poids 400–900, personnalité dans les titres, neutre en body) + JetBrains Mono (code). Échelle : **Hero 4.5rem → H1 3rem → H2 2.25rem → H3 1.5rem → H4 1.25rem** → Body 1rem → Small 0.875rem. Max 3 niveaux par page.

**Spacing** : grille 4px. Section standard = 96px. Padding interne ≤ gap externe.

---

## 8. Packages partagés

| Package | Contenu | Consommé par |
|---------|---------|--------------|
| `@spideros/ui` | DS complet (atoms → templates + foundations + providers) | Toutes les apps |
| `@spideros/auth` | ZitadelProvider, useAuth(), withAuth, getServerSession | Apps AUTH |
| `@spideros/api` | Client Higress, streaming SSE, wrapper Hey API | Apps avec backend |
| `@spideros/config` | tsconfig, biome.json, presets Tailwind | Toutes les apps |
| `@spideros/i18n` | Labels communs (boutons, erreurs, validation, CRUD) | Toutes les apps |
| `@spideros/mcp` | MCP server Claude (tokens, composants, rules DS) | Claude uniquement |
| `@spideros/indexer` | Pipeline ingestion, extracteur LLM, entity resolver, connecteurs. **C'est ici que vit la complexité hors-REST** | People, Documents, Platform backends |
| `@spideros/memory` | Client Mem0 (mémoire LLM persistante) | Builder, Documents |
| `@spideros/embeddings` | Client Nomic Embed (768D) | Builder, People |

---

## 9. Choix techniques détaillés

### 9.1 Toolchain

| Choix | Pourquoi |
|-------|----------|
| pnpm 10 | Workspaces natifs, strict par défaut |
| Turborepo | Cache intelligent, `--affected`, task graph |
| Biome 2 | Lint + format en 1 outil. Remplace ESLint + Prettier |
| TypeScript 5.9+ strict | Pas de `any`. Types dérivés du backend via Hey API |
| Lefthook | Pre-commit (Biome + typecheck) + pre-push (tests) |
| Conventional Commits | Changelogs auto |

### 9.2 Data layer

| Choix | Pourquoi |
|-------|----------|
| React Hook Form + Zod | Uncontrolled (perf). Schémas Zod de Hey API via `@hookform/resolvers/zod` |
| Zustand 5 | UI state cross-composant uniquement. Pas pour server state ni form state |
| TanStack Query 5 | Cache, refetch, invalidation, mutations. Hooks générés par Hey API |
| next-intl 4.x | RSC first-class, zéro JS client, precompilation AOT |
| Next.js 16 App Router | RSC, Server Actions, Turbopack. Self-hosted K8s |
| Hey API codegen | `Pydantic → OpenAPI → Hey API → TS client + hooks + Zod`. Zéro types manuels |

**Data fetching hybride** :

| Cas | Comment |
|-----|---------|
| Data loading initial | Server Component → `fetch()` |
| Interactions client | TanStack Query (hooks Hey API) |
| Mutations simples | Server Action |
| Mutations complexes | TanStack Query mutation + invalidation + toast |
| Streaming AI | SSE via `@spideros/api` `client.stream()` |
| LiveViews temps réel | SurrealDB Live Queries (WebSocket) |

### 9.3 DS — outils

| Choix | Pourquoi |
|-------|----------|
| Style Dictionary 4 + W3C DTCG | Tokens multi-plateforme (primitives → sémantiques → composants) |
| Base UI (headless) | Accessible, pas de style imposé, React 19. Remplace Hero UI du template |
| CVA | Variants déclaratives |
| Phosphor Icons (Iconify) | 9000+ icônes, 6 poids |
| Framer Motion | Animations UI |
| Storybook 10 | Stories colocalisées dans `packages/ui/`. Addons a11y + vitest |

### 9.4 Libs utilitaires

| Lib | Usage |
|-----|-------|
| date-fns | Dates modulaires, tree-shakable |
| es-toolkit | Lodash moderne, TypeScript-first |
| Sonner | Toasts via SpiderProviders |
| react-dropzone | Upload headless |
| dnd-kit | Drag & drop (pipeline kanban, blocs documents) |
| cmdk + react-hotkeys-hook | Command palette (Ctrl+K), raccourcis |

### 9.5 Libs spécialisées par app

| Lib | App | Usage |
|-----|-----|-------|
| Monaco Editor | Builder | Éditeur de code |
| xterm.js | Builder | Terminal navigateur |
| Tiptap | Documents | Rich text WYSIWYG (collaborative Y.js) |
| reveal.js | Documents | Slides/présentations |
| wavesurfer.js | People | Lecteur audio waveform |
| D3.js | Platform, People | Force graphs, tree layouts, flow diagrams |
| react-markdown | Builder | Rendu markdown en preview (read-only) |
| Recharts | People, Platform | Charts (Score of Knowledge, dashboards) |
| TanStack Table | People, Platform | Tables tri/filtres/virtualisation |
| TanStack Virtual | People | Virtual lists gros datasets |

### 9.6 Testing & Qualité

| Choix | Pourquoi |
|-------|----------|
| Vitest | Unit + component tests, ESM natif |
| Testing Library | Test du comportement, pas de l'implémentation |
| Playwright E2E | Multi-browser, scénarios critiques |
| Playwright screenshots | Visual regression souveraine |
| axe-core | WCAG 2.1 AA (Storybook + Vitest) |
| Lighthouse CI | Core Web Vitals en CI |
| react-scanner | Analytics adoption DS |
| Sentry → GlitchTip | Error tracking (GlitchTip self-hosted si besoin souveraineté) |
| Umami | Analytics privacy-first, self-hosted |

### 9.7 Auth & Sécurité

| Choix | Pourquoi |
|-------|----------|
| Zitadel self-hosted | OIDC natif, SSO cross-apps, souverain |
| oidc-client-ts + react-oidc-context | Standard OIDC côté client |
| `@spideros/auth` | ZitadelProvider, useAuth(), withAuth, getServerSession |
| Cookies HttpOnly | Sécurisé, pas accessible JS |
| @t3-oss/env-nextjs + Zod | Validation env au build, fail-fast |
| AES-256 + TLS 1.3 | Chiffrement bout en bout |
| RBAC via Zitadel | Rôles, audit trail complet |

### 9.8 IA

| Choix | Pourquoi |
|-------|----------|
| Higress AI Gateway | Routing multi-provider, semantic cache, RAG, failover |
| SSE streaming | `@spideros/api` `client.stream()`, unidirectionnel |
| WebSocket LiveViews | SurrealDB Live Queries pour L1-L10 |
| Mem0 | Mémoire conversationnelle persistante (exploratoire) |
| Nomic Embed | Embeddings self-hosted, search sémantique |

### 9.9 CI/CD

| Choix | Pourquoi |
|-------|----------|
| GitHub Actions + `--affected` | lint → typecheck → test → build |
| ArgoCD (GitOps) | git push → sync auto → deploy |
| Hey API codegen en CI | Régénérer → typecheck → fail si diff |
| Turborepo generators | Scaffolding Atomic Design |

---

## 10. Claude Code & DX

Claude Code est un **outil de production** — le setup est versionné dans le repo.

### 10.1 CTO / Worker

| Rôle | Quand | Ce qu'il fait |
|------|-------|---------------|
| **CTO** | Branche `main`/`dev` | Orchestre : worktrees, dispatch, review, merge |
| **Worker** | Worktree | Exécute : une branche = une tâche = un contexte isolé |

### 10.2 Plugin `spideros-toolchain`

**Hooks** :

| Hook | Déclencheur | Action |
|------|-------------|--------|
| Session start | Ouverture | Rappel rôle, charge contexte |
| Biome check | Écriture fichier | `biome check --fix` auto |
| UI reviewer | Écriture dans `packages/ui/` | Vérifie conformité DS |
| Pre-commit | Commit | Lint + typecheck + tests affected |
| Pre-PR | Création PR | Versions, changelog, pas de TODO |
| Backup context | Fin de session longue | Sauvegarde le contexte de travail |
| Session end | Fermeture | Résumé + lessons.md |

**Agents** : `ds-reviewer` (conformité DS), `front-architect` (architecture page/feature).

**Skills** : `/safe-commit`, `/ds-audit`, `/ds-design-guide`, `/doc-check`.

**Commande CTO** : `/new-task` — crée un worktree, configure la branche, initialise le contexte Worker.

### 10.3 MCP Server

| Type | Contenu |
|------|---------|
| Resources | Tokens CSS, composants, sections, rules DS |
| Tools | `validate_page_structure`, `suggest_component`, `suggest_section` |
| Prompts | `create-section`, `build-landing-page`, `add-component` |

### 10.4 Rules (`.claude/rules/`)

| Rule | Scope |
|------|-------|
| `workflow.md` | Global — commits step-by-step, plan mode 3+ étapes |
| `app-conventions.md` | Apps — DS mandatory, Tailwind layout-only |
| `ds-conventions.md` | `packages/ui/` — tokens, CSS Modules only |
| `ds-design-guide.md` | `packages/ui/` — The Lake, 95/5, contraintes cyan |

---

## 11. Ce qui vient de Studio Kit

Patterns transférés depuis Studio Kit (`drakkr/studio-kit`) :

| # | Pattern | Transposition SpiderOS |
|---|---------|----------------------|
| 1 | Storybook (argTypes, compound, MDX) | Templates pour `@spideros/ui` (0 stories aujourd'hui) |
| 2 | GitHub Actions CI + Turbo `--affected` | Pipeline à implémenter |
| 3 | SpiderProviders centralisés | Centraliser toast/tooltip dans le DS |
| 4 | Composants form 2 couches | Ajouter atoms form agnostiques dans `@spideros/ui` |
| 5 | i18n colocation | `locales/fr.json` par route, merge runtime (pas de build step avec RSC) |
| 6 | Mutations custom par feature | `onSuccess` (invalidation) + `onError` (toast i18n) par module |
| 7 | Testing factories (backend) | `tests/factories/` avec builders par Piccolo model |
| 8 | Schemas 1:1 (backend) | `schemas/auth.py` miroir de `controllers/auth.py` |
| 9 | Guards nommés (backend) | `guards/require_auth.py` injectable dans `routes.py` |

---

## 12. Points à compléter

| # | Sujet | Contexte |
|---|-------|----------|
| 1 | **Auth avancée** | Silent refresh, single logout cross-app, `usePermissions()` front |
| 2 | **Error boundaries par route** | Fallback UI + Sentry + retry pour Monaco/Tiptap |
| 3 | **RFC 7807 standardisé** | Contrat erreur unique entre les 4 backends |
| 4 | **Orchestration ingestion** | Temporal vs Celery+Redis vs queue simple |
| 5 | **Palette data-viz** | 5 hues × 11 steps pour charts/graphes |
| 6 | **Neutral teinté** | Gris teintés teal (pattern Stripe/Linear) |
| 7 | **Alignment foundations** | Tokens CSS ↔ documentation playbook |
| 8 | **Watchlist Paraglide.js** | Compile-time i18n, immature Next.js. Réévaluer si bundle client devient problème |

---

## Annexe — Couverture des sources

| Source | Sections couvertes |
|--------|--------------------|
| stack-decisions.md §1-8 | Souveraineté, Toolchain |
| stack-decisions.md §9-15, §28 | Design System |
| stack-decisions.md §16-21, §36, §58 | Data layer, Hey API |
| stack-decisions.md §22-27, §29-32 | Testing & Qualité |
| stack-decisions.md §33-35, §48, §53 | CI/CD, Auth env vars |
| stack-decisions.md §37-47 | Libs utilitaires + spécialisées |
| stack-decisions.md §49-51 | IA, Auth |
| stack-decisions.md §54-57 | Backend, Souveraineté |
| Spider_Architecture_Technique.html | Engine, data model, pipeline, LiveViews, alertes |
| Playbook refacto-ds | The Lake, backgrounds, typography, spacing, effects |
| Setup Claude Code | CTO/Worker, hooks, agents, skills, MCP, rules |
| spideros-template (GitHub) | Structure backend, routes.py, registries, guards, MCP |
| Studio Kit audit | Storybook, CI, providers, forms, i18n, factories, schemas |
