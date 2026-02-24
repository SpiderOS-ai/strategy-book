# 07 -- Architecture technique et stack SpiderOS

## Metadata

| Champ | Valeur |
|-------|--------|
| **Auteur** | Nathan + Remy |
| **Date** | 18 fevrier 2026 |
| **Nature** | Specifications techniques : architecture globale et stack cible |
| **Fiabilite** | MIXED -- Nathan previent : "des choses sont peut-etre inventees, particulierement sur l'archi globale." Les choix de stack sont intentionnels et valides ; certains details d'architecture peuvent etre speculatifs. |
| **Contexte cle** | Nathan dit : "a l'air de l'AI coding tout va beaucoup plus vite et la stack est ready de toute facon" |
| **Sources fusionnees** | `spider_archi_globale.md` (infra K8s reelle, namespaces, URLs de services) + `spider_stack_back_front_cible.md` (stack decisions, 59 sections, architecture front/back, Design System, Claude Code setup) |

---

## 1. Vision produit

SpiderOS est une plateforme IA souveraine pour PME/ETI. 4 apps desktop-grade dans le navigateur, un moteur d'intelligence organisationnelle, et une infra 100% France.

```
Sources (Connecteurs)                          Apps (Consommateurs)
+-----------------------+                      +-----------------------+
| Pappers, Google Drive |                      | Platform (dashboard)  |
| ERP, Email, Calendar  |     +----------+     | People (CRM)          |
| Consultant input      | --> |  Spider   | --> | Documents (livrables) |
| Aircall / Noota       |     |  Intel    |     | Builder (IDE AI)      |
+-----------------------+     |  Engine   |     +-----------------------+
                              +----------+
                                   |
                             Knowledge Graph
                              (SurrealDB)
```

---

## 2. Infrastructure souveraine

### 2.1 Clusters Kubernetes

3 clusters Kubernetes (OVH + Scaleway), approche GitOps (ArgoCD).

| Cluster | Role | Localisation |
|---------|------|-------------|
| `spideros-management` | ArgoCD, Jenkins, KubeSphere Console | OVH |
| `spideros-staging` | Developpement, tests E2E, preview | OVH |
| `spideros-production` | Production (HA, monitoring, backups) | OVH |

Disaster Recovery : Scaleway (Paris) -- failover <1h, RPO 15min.

**Domaines :**

- Staging : `*.spideros.dev`
- Production : `*.spideros.ai`
- Management : `*.spideros.co`

### 2.2 Management Cluster

| Service | URL | Namespace |
|---------|-----|-----------|
| KubeSphere Console | `https://kubesphere.spideros.co` | `kubesphere-system` |
| ArgoCD | `https://argocd.spideros.co` | `argocd` |
| Jenkins | `https://jenkins.spideros.co` | `kubesphere-devops-system` |

Namespaces actifs : `argocd`, `kubesphere-system`, `kubesphere-devops-system`, `kubesphere-controls-system`, `cert-manager`, `caddy`.

Note : Harbor et Vault ne sont PAS encore deployes. Les images Docker sont sur OVH Container Registry.

### 2.3 Staging Cluster

Namespaces actifs :

| Namespace | Role |
|-----------|------|
| `kgateway-system` | KGateway (Envoy) -- LoadBalancer: 91.134.108.138 |
| `agentgateway-system` | AgentGateway (AI) -- LoadBalancer: 51.254.239.59 |
| `auth` | Zitadel OIDC |
| `databases` | PostgreSQL, Redis, SurrealDB, TiKV |
| `spider-chat` | AI Chatbot |
| `spider-connector` | OAuth connectors + Nango |
| `spider-content` | Editeur documents |
| `development` | Environnements dev (kubevpn) |

### 2.4 Production Cluster

Memes namespaces que staging, plus `platform` (Platform services).

### 2.5 Orchestration : KubeSphere 4

KubeSphere 4 orchestre les 3 clusters et fournit :
- Multi-cluster Management (vue unifiee)
- DevOps Pipeline (Jenkins integre)
- GitOps (ArgoCD)
- Observability (monitoring et logs)
- Access Control (RBAC centralise)

### 2.6 Souverainete

Zero SaaS US. Alternatives self-hosted pour tout : GlitchTip (erreurs), Umami (analytics), Playwright screenshots (visual regression), Harbor (registre), Vault (secrets), Zitadel (auth). Claude API zero-retention.

---

## 3. Gateways

### 3.1 KGateway (Envoy) -- Gateway principal

Gateway Envoy-based qui gere tout le trafic entrant.

- OAuth2 OIDC via Zitadel (TrafficPolicies)
- HTTPRoutes (routing par hostname/path)
- TLS automatique (Let's Encrypt via cert-manager)
- Rate limiting, auth, headers

### 3.2 AgentGateway -- Gateway LLM/AI

Gateway specialisee pour les workloads AI/LLM.

- Multi-provider (OpenAI, Anthropic, DeepSeek, etc.)
- RAG (injection de contexte automatique)
- Fallback (bascule automatique entre providers)
- Admin UI (configuration via interface web)

```
Client -> KGateway (spideros-gateway)
       -> HTTPRoute (llm-gateway)
       -> AgentGateway (agw)
       -> LLM Provider APIs
```

Note : le fichier stack cible mentionne **Higress** comme gateway IA centralisee (jamais d'appels LLM directs), avec semantic cache, AI routing, et content security. L'archi globale mentionne **AgentGateway**. Il est possible que Higress soit la cible et AgentGateway l'etat actuel, ou que les deux coexistent. A clarifier.

---

## 4. Services d'infrastructure

### 4.1 Zitadel -- Authentification OIDC

Auth OIDC self-hosted, SSO cross-apps, multi-tenancy, machine users, RBAC.

| Env | URL |
|-----|-----|
| Staging | `https://auth-staging.spideros.dev` |
| Production | `https://auth.spideros.ai` |

### 4.2 Nango -- OAuth Connectors

300+ integrations pre-configurees. Gestion des tokens OAuth (refresh automatique). Webhooks pour sync data.

| Env | URL |
|-----|-----|
| Staging | `https://connector-api.spideros.dev` |
| Production | `https://connector-api.spideros.ai` |

### 4.3 PostgreSQL 16 HA (CloudNativePG)

Source de verite relationnelle (tenants, users, audit trail). Patroni failover.

- 1 instance en staging, 3 en production
- Backups automatiques vers S3
- Accessible uniquement depuis le cluster (NetworkPolicies)

### 4.4 SurrealDB + TiKV

Base multi-modele (graph, vector, document, time-series, KV).

**Remplace** Neo4j + MongoDB + Pinecone + InfluxDB + PostGIS + Redis en une seule base. SurrealQL supporte traversee graphe + recherche vectorielle dans la meme requete.

Use cases :
- Knowledge Graph (entites, claims, relations)
- Embeddings (vecteurs 768D)
- Live Queries (WebSocket temps reel)

Pods deployes : `surrealdb`, `tikv-cluster-pd`, `tikv-cluster-tikv`, `tikv-cluster-discovery`.

### 4.5 Redis

Cache pour sessions et donnees temporaires.

### 4.6 Nomic Embed

Embeddings self-hosted 768D FR/EN. Vecteurs stockes dans SurrealDB.

### 4.7 Mem0

Memoire LLM persistante (user/org/session). Exploratoire.

---

## 5. Spider Intelligence Engine

Le moteur d'intelligence organisationnelle. Vit dans `engine/` des backends et dans les packages partages (`@spideros/indexer`).

### 5.1 Pipeline

```
Sources -> Connecteurs -> Extracteur LLM -> Entity Resolver -> Claim Engine -> Analyseur -> LiveViews
```

| Composant | Role | Stack |
|-----------|------|-------|
| **Connecteurs** (7 en V1) | Ingestion depuis sources externes | Python async, adapters par source |
| **Extracteur LLM** | Non-structure -> claims | Haiku 4.5 (volume) -> Sonnet 4.5 (complexe), via Higress |
| **Entity Resolver** | Deduplication (Fellegi-Sunter) | Jaro-Winkler + contexte. Auto-merge >=0.94 |
| **Claim Engine** | Combinaison Dempster-Shafer | Belief/Plausibility, conflits K>0.9 |
| **Analyseur batch** | Communautes, autorite, bus factor | networkx, scikit-learn. Horaire ou post-ingestion |
| **LiveView engine** | Materialisation des 10 livrables | SurrealQL -> transform -> cache -> WebSocket |
| **ATMS simplifie** | Retractation de claims (cascade) | Recompute global en V1 (<2s pour <2000 claims). Incremental en V2 |
| **Alertes** | Anomalies (bus factor, conflits) | Pattern Datadog : rules -> check -> notify |

### 5.2 Data model

- **Entity** : id, type (PERSON/ROLE/PROCESS/SYSTEM/COMPETENCE/...), canonical_name, aliases, tenant_id
- **Claim** : subject_id -> predicate -> object_id, belief dans [0,1], plausibility dans [Bel,1], sources[], depends_on[], status (PROPOSED/VALIDATED/REJECTED/SUPERSEDED)
- **14 predicats** : HOLDS_ROLE, REPORTS_TO, BELONGS_TO, HAS_COMPETENCE, EXECUTES_PROCESS, USES_SYSTEM, COMMUNICATES_WITH, ATTENDS_MEETING, SEQUENCE_AFTER, SIPOC_SUPPLIER, SIPOC_CUSTOMER, CONTAINS_DATA, PORTER_ACTIVITY, RISK_EXPOSURE, TRANSFORMATION_ACTION

**Cout LLM** : ~70 EUR/an pour une PME 150 personnes.

### 5.3 Pipeline RAG (en production)

```
Ingestion :
Nango API -> NangoSyncService (60s interval) -> SurrealDB (raw) -> EmbeddingWorker -> Nomic API -> SurrealDB (vectors)

Retrieval :
Client -> KGateway -> AgentGateway -> RAG Webhook (spider-connector) -> SurrealDB (vector search) -> LLM
```

SurrealDB Databases :

| Database | Tables |
|----------|--------|
| `connectors_raw_data` | `gmail_email`, `sync_metadata` |
| `connectors_embeddings` | `knowledge_base`, `embedding_jobs` |

---

## 6. Les 6 apps

| App | URL | Type | Description |
|-----|-----|------|-------------|
| **People** | people.spideros.ai | B (Next.js + Python) | CRM relationnel -- timeline, audio, charts, tables virtualisees, Score of Knowledge |
| **Builder** | builder.spideros.ai | B (Next.js + Python) | IDE AI-assisted -- Monaco Editor, xterm.js, streaming AI, command palette |
| **Documents** | documents.spideros.ai | B (Next.js + Python) | Editeur de livrables -- Tiptap, reveal.js, export PDF/HTML, AI content generation |
| **Platform** | app.spideros.ai | A/B (Next.js + leger) | Hub post-login, dashboard, 10 livrables Spider Intelligence (L1-L10) |
| **Website** | spideros.ai | A (Next.js seul) | Site corporate -- PUBLIC, pas d'auth |
| **Playbook** | interne | A (Next.js seul) | Documentation DS -- INTERNE, submodule |

**Type A** = Next.js seul. **Type B** = Next.js + backend Python (Litestar + Piccolo).

---

## 7. Les 10 LiveViews

Vues materialisees du Knowledge Graph. Chaque livrable = query SurrealQL + composant React + politique de refresh.

| # | Livrable | Renderer | Refresh |
|---|----------|----------|---------|
| L1 | Organigramme | D3.js tree | On change |
| L2 | Competences | Heatmap grid | On change |
| L3 | Porter | SVG layout | Daily |
| L4 | VSM | D3.js flow | On change |
| L5 | SIPOC | Expandable cards | On change |
| L6 | RACI | Matrix grid | On change |
| L7 | Cartographie SI | D3.js diagram | Daily |
| L8 | SNA | D3.js force graph | Hourly |
| L9 | Diagnostic | Risk matrix | On change |
| L10 | Roadmap | Gantt/timeline | Manual |

L1, L4, L7, L8 necessitent D3.js (Recharts ne suffit pas).

---

## 8. Stack frontend

### 8.1 Architecture -- Colocation

Pattern Cal.com / Bulletproof React. Tout ce qui concerne une route vit avec cette route.

```
apps/people/frontend/src/
+-- app/
|   +-- layout.tsx                 <- SpiderProviders + ZitadelProvider
|   +-- contacts/
|   |   +-- page.tsx               <- Server Component
|   |   +-- _components/           <- UI specifique a cette route
|   |   +-- _lib/                  <- Actions, schemas Zod
|   |   +-- locales/fr.json        <- i18n colocalise
|   |   +-- [id]/
|   +-- pipeline/
|   +-- analytics/
|   +-- callback/page.tsx          <- Seule route publique (OIDC)
+-- features/                      <- Partage entre 2+ routes SEULEMENT
+-- generated/                     <- Hey API (ne pas toucher)
```

**Regle d'ascension** : `_components/` -> `features/` -> `packages/ui/`. Un composant monte quand il est utilise par 2+ routes, puis 2+ apps.

### 8.2 Data layer

| Choix | Role |
|-------|------|
| React Hook Form + Zod | Uncontrolled (perf). Schemas Zod de Hey API |
| Zustand 5 | UI state cross-composant uniquement |
| TanStack Query 5 | Cache, refetch, invalidation, mutations |
| next-intl 4.x | RSC first-class, zero JS client, precompilation AOT |
| Next.js 16 App Router | RSC, Server Actions, Turbopack. Self-hosted K8s |
| Hey API codegen | Pydantic -> OpenAPI -> Hey API -> TS client + hooks + Zod. Zero types manuels |

**Data fetching hybride :**

| Cas | Comment |
|-----|---------|
| Data loading initial | Server Component -> `fetch()` |
| Interactions client | TanStack Query (hooks Hey API) |
| Mutations simples | Server Action |
| Mutations complexes | TanStack Query mutation + invalidation + toast |
| Streaming AI | SSE via `@spideros/api` `client.stream()` |
| LiveViews temps reel | SurrealDB Live Queries (WebSocket) |

### 8.3 Toolchain

| Choix | Role |
|-------|------|
| pnpm 10 | Workspaces natifs, strict par defaut |
| Turborepo | Cache intelligent, `--affected`, task graph |
| Biome 2 | Lint + format (remplace ESLint + Prettier) |
| TypeScript 5.9+ strict | Pas de `any`. Types derives du backend via Hey API |
| Lefthook | Pre-commit (Biome + typecheck) + pre-push (tests) |
| Conventional Commits | Changelogs auto |

---

## 9. Stack backend

### 9.1 Choix techniques

| Choix | Pourquoi |
|-------|----------|
| **Litestar 2.21+** | ASGI async, DTOs natifs, OpenAPI auto, DI 4 niveaux, guards. Mieux architecture que FastAPI |
| **Piccolo ORM** | Async-native, migrations auto, query builder propre |
| **Pydantic 2.0+** | Validation + serialization, source de verite pour OpenAPI -> Hey API codegen |
| **uv** | 100x plus rapide que pip |
| **Ruff** | Linter Python ultra-rapide |

### 9.2 Structure

Architecture flat par couche technique. APIs REST light (5-20 endpoints par app). Complexite lourde dans `engine/` et packages partages.

```
backend/src/
+-- main.py                    <- Litestar app, compose les ALL_* registries
+-- config.py                  <- Pydantic Settings
+-- db.py                      <- Piccolo Engine + connection pool
+-- routes.py                  <- TOUTES les routes (source of truth unique)
+-- dependencies.py            <- ALL_DEPENDENCIES
+-- middlewares.py              <- ALL_MIDDLEWARES
+-- exception_handlers.py      <- ALL_EXCEPTION_HANDLERS
+-- controllers/               <- 1 fichier = 1 ressource (fonctions async pures)
+-- services/                  <- Logique metier
+-- models/                    <- Piccolo Tables
+-- schemas/                   <- Pydantic DTOs in/out (1:1 avec controllers)
+-- exceptions/                <- Hierarchie d'exceptions custom
+-- handlers/                  <- Implementations exception handlers
+-- guards/                    <- Auth middleware + guards nommes
+-- providers/                 <- Factories DI (Litestar Provide())
+-- lib/                       <- StorageBackend ABC, JWT, Fernet
+-- integrations/              <- OAuth Google, connecteurs externes
+-- engine/                    <- Spider Intelligence (claims, resolver, analyzer)
+-- mcp_server.py              <- FastMCP.from_openapi() (dev-only)
```

### 9.3 Patterns cles

- `routes.py` centralise : vision globale de l'API en un fichier
- Controllers = fonctions async pures (pas de classes, pas de decorateurs, testables unitairement)
- Registries `ALL_*` : composition explicite dans `main.py`, rien de cache
- Regle d'ascension backend (miroir du front) : controller -> service -> package partage

---

## 10. Design System -- "The Lake" (`@spideros/ui`)

Package unique consomme par toutes les apps. Les apps composent des composants DS, elles ne stylent pas.

### 10.1 Structure

```
packages/ui/src/
+-- foundations/           <- Tokens CSS (colors, spacing, typography, effects)
|   +-- tokens/            <- .css files (primitives, semantic, gradients)
|   +-- fonts/             <- Kedebideri + JetBrains Mono
|   +-- icons/             <- Phosphor via icon-mapping.ts
+-- atoms/                 <- ~35 composants indivisibles (Button, Input, Badge, Trait...)
+-- molecules/             <- ~15 groupes d'atoms (Card, Dialog, Section, PageHeader...)
+-- organisms/             <- ~15 sections autonomes (Navbar, Hero, Footer...)
+-- templates/             <- Layouts (AppLayout, WebsiteLayout)
+-- providers/             <- SpiderProviders (toast, tooltip)
+-- utils/                 <- cn(), toast wrapper
```

Regle d'import : un layer importe uniquement les layers inferieurs.

### 10.2 Identite visuelle -- "The Lake"

3 couches, ratio strict :

| Couche | % | Couleurs | Usage |
|--------|---|----------|-------|
| **Surface** | ~70% | Cream #FFFEFC, Warm #FAF9F7, Neutral #F4F4F6 | Contenu courant |
| **Depth** | ~25% | Abysse #022C22, Black #0A0A0A | Trust, Footer. Max 2/page, toujours gradient |
| **Electric** | ~5% | Cyan 500 #00D4EE, 400 #00F5FF | Traits, glows, focus. Jamais en fond, body text, icones |

**Typography** : Kedebideri (6 poids 400-900) + JetBrains Mono (code). Echelle : Hero 4.5rem -> H1 3rem -> H2 2.25rem -> H3 1.5rem -> H4 1.25rem -> Body 1rem -> Small 0.875rem. Max 3 niveaux par page.

**Backgrounds** : catalogue ferme. 5 fonds plats + 12 gradients + 2 text gradients.

**Spacing** : grille 4px. Section standard = 96px. Padding interne <= gap externe.

### 10.3 Strategie CSS

| Ou | Comment |
|----|---------|
| `packages/ui/` foundations | CSS Variables (`--color-bg-base`, `--spacing-section-y`) |
| `packages/ui/` composants | CSS Modules + CVA |
| Apps -- layout | Tailwind structurel (`flex`, `grid`, `gap-*`, `py-*`) |
| Apps -- visuels | **Interdit** (pas de `bg-teal-500`, `text-white`) |

### 10.4 Outils DS

| Choix | Role |
|-------|------|
| Style Dictionary 4 + W3C DTCG | Tokens multi-plateforme |
| Base UI (headless) | Accessible, pas de style impose, React 19 |
| CVA | Variants declaratives |
| Phosphor Icons (Iconify) | 9000+ icones, 6 poids |
| Framer Motion | Animations UI |
| Storybook 10 | Stories colocalisees dans `packages/ui/` |

Regle absolue : un import `@base-ui/react` dans une app = erreur. Tout passe par `@spideros/ui`.

---

## 11. Packages partages

| Package | Contenu | Consomme par |
|---------|---------|--------------|
| `@spideros/ui` | DS complet (atoms -> templates + foundations + providers) | Toutes les apps |
| `@spideros/auth` | ZitadelProvider, useAuth(), withAuth, getServerSession | Apps AUTH |
| `@spideros/api` | Client Higress, streaming SSE, wrapper Hey API | Apps avec backend |
| `@spideros/config` | tsconfig, biome.json, presets Tailwind | Toutes les apps |
| `@spideros/i18n` | Labels communs (boutons, erreurs, validation, CRUD) | Toutes les apps |
| `@spideros/mcp` | MCP server Claude (tokens, composants, rules DS) | Claude uniquement |
| `@spideros/indexer` | Pipeline ingestion, extracteur LLM, entity resolver, connecteurs | People, Documents, Platform backends |
| `@spideros/memory` | Client Mem0 (memoire LLM persistante) | Builder, Documents |
| `@spideros/embeddings` | Client Nomic Embed (768D) | Builder, People |

---

## 12. Monorepo

```
spideros/
+-- apps/
|   +-- website/          <- PUBLIC (pas d'auth)
|   +-- playbook/         <- INTERNE (submodule)
|   +-- platform/         <- AUTH (@spideros/auth)
|   +-- builder/          <- AUTH
|   +-- documents/        <- AUTH
|   +-- people/           <- AUTH
|   +-- data/             <- AUTH (submodule)
+-- packages/
|   +-- ui/               <- Design System complet
|   +-- auth/             <- Zitadel (apps AUTH uniquement)
|   +-- api/              <- Hey API + streaming SSE
|   +-- config/           <- tsconfig, biome, tailwind
|   +-- i18n/             <- Labels partages cross-apps
|   +-- mcp/              <- MCP server pour Claude Code
|   +-- indexer/          <- Pipeline ingestion + connecteurs
|   +-- memory/           <- Client Mem0
|   +-- embeddings/       <- Client Nomic Embed
+-- k8s/                  <- Manifests Kubernetes
+-- plugins/              <- spideros-toolchain
+-- .claude/              <- Rules Claude Code
+-- turbo.json
+-- pnpm-workspace.yaml
+-- biome.json
```

Auth vs Public : la distinction se fait par la presence de `@spideros/auth` dans `package.json` + `middleware.ts` qui redirige vers Zitadel.

---

## 13. Securite

### NetworkPolicies

Policies restrictives dans le namespace `platform` :
- `postgres-access-policy` -- Acces PostgreSQL whiteliste
- `surrealdb-access-policy` -- Acces SurrealDB whiteliste
- `default-deny-all` -- Tout bloque par defaut

### Secrets Management

Tous les secrets sont crees manuellement via KubeSphere UI (jamais dans Git).

Secrets principaux : `zitadel-db-credentials`, `zitadel-secrets`, `postgres-superuser`, `postgres-app-credentials`.

### Chiffrement

AES-256 + TLS 1.3. Bout en bout.

---

## 14. CI/CD

### GitOps (ArgoCD)

```
Git Push -> ArgoCD Detecte -> Sync Automatique -> Deploiement
```

### GitHub Actions

lint -> typecheck -> test -> build (avec `--affected`).

Hey API codegen en CI : regenerer -> typecheck -> fail si diff.

### Claude Code & DX

Claude Code est un outil de production. Le setup est versionne dans le repo.

**CTO/Worker pattern** : CTO orchestre (branche `main`/`dev`, worktrees, dispatch, review, merge). Worker execute (une branche = une tache = un contexte isole).

**Plugin `spideros-toolchain`** avec hooks : session start, Biome check, UI reviewer, pre-commit, pre-PR, backup context, session end.

**MCP Server** : resources (tokens CSS, composants, rules DS), tools (validate_page_structure, suggest_component), prompts (create-section, build-landing-page).

---

## 15. Points a completer

| # | Sujet |
|---|-------|
| 1 | Auth avancee (silent refresh, single logout cross-app, `usePermissions()` front) |
| 2 | Error boundaries par route (fallback UI + Sentry + retry pour Monaco/Tiptap) |
| 3 | RFC 7807 standardise (contrat erreur unique entre les 4 backends) |
| 4 | Orchestration ingestion (Temporal vs Celery+Redis vs queue simple) |
| 5 | Palette data-viz (5 hues x 11 steps pour charts/graphes) |
| 6 | Neutral teinte (gris teintes teal, pattern Stripe/Linear) |
| 7 | Alignment foundations (tokens CSS <-> documentation playbook) |
| 8 | Watchlist Paraglide.js (compile-time i18n, immature Next.js) |
| 9 | Clarifier Higress vs AgentGateway (cible vs etat actuel ?) |

---

## 16. Libs specialisees par app

| Lib | App | Usage |
|-----|-----|-------|
| Monaco Editor | Builder | Editeur de code |
| xterm.js | Builder | Terminal navigateur |
| Tiptap | Documents | Rich text WYSIWYG (collaborative Y.js) |
| reveal.js | Documents | Slides/presentations |
| wavesurfer.js | People | Lecteur audio waveform |
| D3.js | Platform, People | Force graphs, tree layouts, flow diagrams |
| Recharts | People, Platform | Charts (Score of Knowledge, dashboards) |
| TanStack Table | People, Platform | Tables tri/filtres/virtualisation |
| TanStack Virtual | People | Virtual lists gros datasets |
| cmdk + react-hotkeys-hook | Toutes | Command palette (Ctrl+K), raccourcis |
| dnd-kit | People, Documents | Drag & drop (pipeline kanban, blocs documents) |

---

## 17. Testing & Qualite

| Choix | Role |
|-------|------|
| Vitest | Unit + component tests, ESM natif |
| Testing Library | Test du comportement, pas de l'implementation |
| Playwright E2E | Multi-browser, scenarios critiques |
| Playwright screenshots | Visual regression souveraine |
| axe-core | WCAG 2.1 AA (Storybook + Vitest) |
| Lighthouse CI | Core Web Vitals en CI |
| react-scanner | Analytics adoption DS |
| GlitchTip | Error tracking (self-hosted) |
| Umami | Analytics privacy-first (self-hosted) |
