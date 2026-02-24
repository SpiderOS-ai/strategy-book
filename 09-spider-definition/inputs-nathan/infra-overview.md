# SpiderOS — Infrastructure Overview

> Pour : onboarding, chefs de projet, Claude Code contexte rapide
> Derniere MAJ : 2026-02-20
> Detail complet : voir `infra-complete.md`

---

## En une phrase

3 clusters K8s souverains (OVH), GitOps (ArgoCD), 11 apps Next.js + Python, auth Zitadel via KGateway, 2 gateways (Envoy + LLM), 3 bases de donnees, moteur IA Spider Core.

---

## Les 11 apps

| App | Type | Statut |
|-----|------|--------|
| Website | A (Next.js seul) | deploye |
| Playbook | A | deploye |
| Auth Form | A | deploye |
| Chat | B (Next.js + Python) | deploye |
| Connector | B | deploye |
| Content | B | deploye |
| Data | A | deploye |
| Platform | A/B | planifie |
| People | B | planifie |
| Builder | B | planifie |
| Documents | B | planifie |

---

## Architecture

```
Client → KGateway (Envoy) → App
                           → AgentGateway → LLM (OpenAI/Anthropic/DeepSeek)

3 clusters K8s (OVH) :
  management (ArgoCD, Jenkins, KubeSphere)
  staging (*.spideros.dev)
  production (*.spideros.ai)
```

---

## Stack resumee

| Couche | Choix |
|--------|-------|
| Frontend | Next.js 16, TypeScript strict, Tailwind (layout only), Base UI headless |
| Backend | Litestar, Piccolo ORM, Pydantic, uv, Ruff |
| Design System | `@spideros/ui` — CSS Modules, CVA, tokens CSS |
| Data | TanStack Query, React Hook Form + Zod, Hey API codegen |
| Auth | Zitadel OIDC via KGateway (auth geree au niveau gateway) |
| Databases | PostgreSQL 16 HA, SurrealDB + TiKV, Redis |
| AI | AgentGateway multi-provider, Nomic Atlas embeddings (cloud), pipeline RAG, Agno, LangChain |
| CI/CD | GitHub Actions + Turborepo, ArgoCD GitOps |
| DX | pnpm 10, Biome 2, Claude Code + spideros-toolchain |

---

## Souverainete

Zero SaaS US. Self-hosted : Zitadel, KGateway, AgentGateway, PostgreSQL, SurrealDB, ArgoCD.
Cloud temporaire : Nomic Atlas (self-hosted GPU prevu).
Pas encore deploye : Harbor, Vault, GlitchTip, Umami, Scaleway DR.
