# Architecture des Services SpiderOS

## Vue d'ensemble

SpiderOS déploie une infrastructure cloud souveraine sur 3 clusters Kubernetes (OVH \+ Scaleway), avec une approche GitOps pour la gestion automatisée des déploiements.

**Domaines :**

- **Staging :** `*.spideros.dev`  
- **Production :** `*.spideros.ai`  
- **Management :** `*.spideros.co`

## Clusters Kubernetes

| Cluster | Rôle | Localisation |
| :---- | :---- | :---- |
| `spideros-management` | ArgoCD, Jenkins, KubeSphere Console | OVH |
| `spideros-staging` | Développement, tests E2E, preview | OVH |
| `spideros-production` | Production (HA, monitoring, backups) | OVH |

### Management Cluster — Services Centralisés

| Service | URL | Namespace |
| :---- | :---- | :---- |
| **KubeSphere Console** | `https://kubesphere.spideros.co` | `kubesphere-system` |
| **ArgoCD** | `https://argocd.spideros.co` | `argocd` |
| **Jenkins** | `https://jenkins.spideros.co` | `kubesphere-devops-system` |

**Namespaces actifs :**

```
argocd                      ← GitOps controller
kubesphere-system           ← KubeSphere core
kubesphere-devops-system    ← Jenkins + CI/CD
kubesphere-controls-system  ← KubeSphere controllers
cert-manager                ← TLS certificates
caddy                       ← Reverse proxy (internal)
```

**Note :** Harbor et Vault ne sont PAS encore déployés. Les images Docker sont stockées sur OVH Container Registry.

### Staging Cluster — Environnement de Développement

**Namespaces actifs :**

```
kgateway-system       ← KGateway (Envoy) - LoadBalancer: 91.134.108.138
agentgateway-system   ← AgentGateway (AI) - LoadBalancer: 51.254.239.59
auth                  ← Zitadel OIDC
databases             ← PostgreSQL, Redis, SurrealDB, TiKV
spider-chat           ← AI Chatbot
spider-connector      ← OAuth connectors + Nango
spider-content        ← Éditeur documents
development           ← Environnements dev (kubevpn)
kubevpn               ← Dev connectivity
```

### Production Cluster — Environnement de Production

**Namespaces actifs :**

```
kgateway-system       ← KGateway (Envoy)
agentgateway-system   ← AgentGateway (AI)
auth                  ← Zitadel OIDC
databases             ← PostgreSQL, Redis, SurrealDB, TiKV
spider-chat           ← AI Chatbot
spider-connector      ← OAuth connectors + Nango
spider-content        ← Éditeur documents
platform              ← Platform services
```

---

## KubeSphere — Plateforme de Gestion

**KubeSphere 4** orchestre les 3 clusters et fournit :

- **Multi-cluster Management** — Vue unifiée des 3 clusters  
- **DevOps Pipeline** — Jenkins intégré pour CI  
- **GitOps (ArgoCD)** — CD automatique  
- **Observability** — Monitoring et logs  
- **Access Control** — RBAC centralisé

**Console :** `https://kubesphere.spideros.co`

---

## Gateways

### KGateway (Envoy) — Gateway Principal

**KGateway** est notre gateway Envoy-based qui gère tout le traffic entrant.

**Fonctionnalités :**

- **OAuth2 OIDC** — Authentification via Zitadel (TrafficPolicies)  
- **HTTPRoutes** — Routing par hostname/path  
- **TLS automatique** — Certificats Let's Encrypt via cert-manager  
- **TrafficPolicies** — Rate limiting, auth, headers

**Namespace :** `kgateway-system`

### AgentGateway — Gateway LLM/AI

**AgentGateway** est un gateway spécialisé pour les workloads AI/LLM.

**Fonctionnalités :**

- **Multi-provider** — OpenAI, Anthropic, DeepSeek, etc.  
- **RAG** — Injection de contexte automatique  
- **Fallback** — Bascule automatique entre providers  
- **Admin UI** — Configuration via interface web

**Architecture :**

```
Client → KGateway (spideros-gateway)
       → HTTPRoute (llm-gateway)
       → AgentGateway (agw)
       → LLM Provider APIs
```

**Namespace :** `agentgateway-system`

**URLs :**

- Staging: `https://llm.spideros.dev`  
- Admin UI: Port-forward vers `agw` service

---

## Services d'Infrastructure

### 1\. Zitadel — Authentification OIDC

**Zitadel** gère l'identité des utilisateurs et les permissions.

**URLs :**

- Staging: `https://auth-staging.spideros.dev`  
- Production: `https://auth.spideros.ai`

**Fonctionnalités :**

- OAuth 2.0 / OIDC — Authentification standard  
- Multi-tenancy — Organisations indépendantes  
- Machine Users — Comptes de service inter-services  
- RBAC & Permissions  
- Console Web à `/ui/console`

**Base de données :** PostgreSQL dédié par environnement

**Namespace :** `auth`

### 2\. Nango — OAuth Connectors

**Nango** gère les intégrations OAuth avec les services externes (Gmail, Aircall, Calendar, etc.).

**URLs :**

- Staging: `https://connector-api.spideros.dev`  
- Production: `https://connector-api.spideros.ai`

**Fonctionnalités :**

- 300+ intégrations pré-configurées  
- Gestion des tokens OAuth (refresh automatique)  
- Webhooks pour sync data

**Namespace :** `spider-connector`

### 3\. PostgreSQL 16 HA (CloudNativePG)

PostgreSQL haute disponibilité, source de vérité relationnelle.

**Accès interne :** | Service | URL | Port | |---------|-----|------| | PostgreSQL (RW) | `postgres-cluster-rw.databases.svc.cluster.local` | 5432 | | PostgreSQL (RO) | `postgres-cluster-r.databases.svc.cluster.local` | 5432 |

**Configuration :**

- 1 instance en staging, 3 en production (Patroni failover)  
- Backups automatiques vers S3  
- Accessible uniquement depuis le cluster (NetworkPolicies)

**Namespace :** `databases`

### 4\. SurrealDB \+ TiKV

Base multi-modèle (graph, vector, document, time-series, KV).

**Accès interne :** `surrealdb.databases.svc.cluster.local:8000`

**Pods déployés :**

- `surrealdb` — Serveur SurrealDB  
- `tikv-cluster-pd` — Placement Driver  
- `tikv-cluster-tikv` — Stockage KV distribué  
- `tikv-cluster-discovery` — Service discovery

**Use cases :**

- Knowledge Graph (entités, claims, relations)  
- Embeddings (vecteurs 768D)  
- Live Queries (WebSocket temps réel)

**Namespace :** `databases`

### 5\. Redis

Cache Redis pour sessions et données temporaires.

**Accès interne :** `redis.databases.svc.cluster.local:6379`

**Namespace :** `databases`

### 6\. Cert-Manager

Génération automatique de certificats TLS via Let's Encrypt.

**Issuer :** `letsencrypt-prod`

Tous les HTTPRoutes avec hostname obtiennent automatiquement un certificat HTTPS.

---

## CI/CD Pipeline (ArgoCD GitOps)

### Workflow

```
Git Push → ArgoCD Détecte → Sync Automatique → Déploiement
```

**ApplicationSets déployés :**

- `cnpg-operator-all-clusters.yaml` — Opérateur PostgreSQL  
- `database-infrastructure-all-clusters.yaml` — Clusters PostgreSQL et TiKV  
- `surrealdb-all-clusters.yaml` — SurrealDB  
- `zitadel-all-clusters.yaml` — Authentification  
- `agentgateway-all-clusters.yaml` — Gateway AI

**Avantages :**

- Déploiements automatiques  
- Rollback facile (revert Git)  
- Self-healing (ArgoCD recrée les ressources supprimées)

---

## Services Applicatifs

### Auth Form — Formulaire d'Authentification

Interface Next.js standalone pour login/signup. Affiché par KGateway quand l'utilisateur n'est pas authentifié.

| Environnement | URL |
| :---- | :---- |
| Staging | `https://auth.spideros.dev` |
| Production | `https://auth.spideros.ai` |

**Flux :**

1. KGateway détecte utilisateur non authentifié  
2. Redirect vers Auth Form  
3. Auth Form → OAuth flow avec Zitadel  
4. Zitadel retourne JWT token  
5. Redirect vers app avec cookie `_oauth2_proxy`

### Spider Chat — AI Chatbot

Chatbot IA avec streaming SSE et RAG.

| Environnement | URL |
| :---- | :---- |
| Staging | `https://chat-dev.spideros.dev` |
| Production | `https://chat.spideros.ai` |

**Stack :** Next.js \+ Python (backend)

### Spider Connector — OAuth Integrations

Gestion des connecteurs externes (Gmail, Aircall, Calendar).

| Environnement | URL |
| :---- | :---- |
| Staging | `https://connector.spideros.dev` |
| Production | `https://connector.spideros.ai` |

**Stack :** Next.js \+ Python (Litestar) \+ Nango

### Spider Content — Éditeur de Documents

(ex-ContentFlow).

| Environnement | URL |
| :---- | :---- |
| Staging | `https://content.spideros.dev` |
| Production | `https://content.spideros.ai` |

---

## Pipeline RAG

### Stack

| Composant | Technologie | Rôle |
| :---- | :---- | :---- |
| OAuth Connectors | Nango (self-hosted K8s) | Connexions Gmail, Aircall, Calendar |
| Sync Service | Python Litestar \+ `NangoSyncService` | Pull data depuis Nango → SurrealDB |
| Embeddings | Nomic Atlas API (`nomic-embed-text-v1.5`) | 768D vectors |
| Vector Store | SurrealDB (`connectors_embeddings` DB) | Stockage chunks \+ embeddings |
| RAG Webhook | Python Litestar (`agno_rag/webhook.py`) | Context injection pour AgentGateway |
| LLM Gateway | AgentGateway (`AgentgatewayPolicy`) | Appelle webhook avant chaque requête LLM |

### Connexions

```
Ingestion:
Nango API → NangoSyncService (60s interval) → SurrealDB (raw) → EmbeddingWorker → Nomic API → SurrealDB (vectors)

Retrieval:
Client → KGateway → AgentGateway → RAG Webhook (spider-connector) → SurrealDB (vector search) → LLM
```

### SurrealDB Databases

| Database | Tables |
| :---- | :---- |
| `connectors_raw_data` | `gmail_email`, `sync_metadata` |
| `connectors_embeddings` | `knowledge_base`, `embedding_jobs` |

### AgentGateway Config

Le webhook RAG est configuré via `AgentgatewayPolicy` :

- Target: `HTTPRoute/llm-gateway`  
- Webhook: `backend-spider-connector:8000` (namespace: `spider-connector`)

---

## Sécurité

### NetworkPolicies

Policies restrictives dans le namespace `platform` :

- `postgres-access-policy` — Accès PostgreSQL whitelisté  
- `surrealdb-access-policy` — Accès SurrealDB whitelisté  
- `default-deny-all` — Tout bloqué par défaut

### Secrets Management

**Tous les secrets sont créés manuellement via KubeSphere UI** (jamais dans Git).

**Secrets principaux :**

- `zitadel-db-credentials` — PostgreSQL pour Zitadel  
- `zitadel-secrets` — Masterkey chiffrement  
- `postgres-superuser` — Superuser PostgreSQL  
- `postgres-app-credentials` — User applicatif

### ReferenceGrants

Les HTTPRoutes cross-namespace nécessitent des ReferenceGrants pour accéder aux TLS secrets.

---

## URLs des Services

### Management (`*.spideros.co`)

| Service | URL | Status |
| :---- | :---- | :---- |
| KubeSphere Console | `https://kubesphere.spideros.co` | ✅ Running |
| ArgoCD | `https://argocd.spideros.co` | ✅ Running |
| Jenkins | `https://jenkins.spideros.co` | ✅ Running |

### Staging (`*.spideros.dev`)

| Service | URL | Namespace |
| :---- | :---- | :---- |
| KGateway (LoadBalancer) | `91.134.108.138` | `kgateway-system` |
| AgentGateway (LoadBalancer) | `51.254.239.59` | `agentgateway-system` |
| Zitadel | `https://auth-staging.spideros.dev` | `auth` |
| Auth Form | `https://auth.spideros.dev` | `auth` |
| Spider Chat | `https://chat-dev.spideros.dev` | `spider-chat` |
| Spider Connector | `https://connector.spideros.dev` | `spider-connector` |
| Spider Content | `https://content.spideros.dev` | `spider-content` |
| LLM Gateway | `https://llm.spideros.dev` | `agentgateway-system` |

### Production (`*.spideros.ai`)

| Service | URL |
| :---- | :---- |
| Zitadel | `https://auth.spideros.ai` |
| Auth Form | `https://auth.spideros.ai` |
| Spider Chat | `https://chat.spideros.ai` |
| Spider Connector | `https://connector.spideros.ai` |
| Spider Content | `https://content.spideros.ai` |

| Service | URL | Port |
| :---- | :---- | :---- |
| PostgreSQL RW | `postgres-cluster-rw.databases.svc.cluster.local` | 5432 |
| PostgreSQL RO | `postgres-cluster-r.databases.svc.cluster.local` | 5432 |
| SurrealDB | `surrealdb.databases.svc.cluster.local` | 8000 |
| TiKV PD | `tikv-cluster-pd.databases.svc.cluster.local` | 2379 |

---

## Monitoring

**KubeSphere** fournit :

- Métriques CPU/RAM/Disk  
- Logs agrégés  
- Events Kubernetes  
- Alerting (à configurer)

---

## Monorepo SpiderOS

Le code source est organisé dans un monorepo : `https://github.com/SpiderOS-ai/main`

```
spideros/
├── k8s/                       ← Ce repo (manifests K8s)
├── apps/
│   ├── website/               ← Site corporate
│   ├── playbook/              ← Documentation DS
│   ├── platform/              ← Hub post-login
│   ├── builder/               ← IDE AI-assisted
│   ├── documents/             ← Éditeur livrables
│   ├── people/                ← CRM relationnel
│   ├── chat/                  ← AI chatbot
│   ├── connector/             ← OAuth connectors
│   ├── auth-form/             ← Formulaire auth
│   └── data/                  ← Data analysis
├── packages/
│   ├── ui/                    ← Design System
│   ├── auth/                  ← Zitadel client
│   ├── api/                   ← Hey API + streaming
│   ├── surrealdb-migrations/  ← DB migrations
│   └── ...
└── ...
```

---

**Dernière mise à jour :** 2026-02-18  
