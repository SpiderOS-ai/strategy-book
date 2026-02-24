# Research Spider Memory - Consolidation Complète

> **Date de consolidation** : 2026-01-14
> **Sources** : databases.md, embeddings.md, infrastructure.md, spider-memory-research-2026-01-14.md
> **Statut** : Recherche consolidée

---

## Table des Matières

1. [Résumé Exécutif](#résumé-exécutif)
2. [Bases de Données Vectorielles](#bases-de-données-vectorielles)
3. [Modèles d'Embedding](#modèles-dembedding)
4. [Stratégies de Chunking](#stratégies-de-chunking)
5. [Architecture Multi-Tenant](#architecture-multi-tenant)
6. [Infrastructure Cloud EU](#infrastructure-cloud-eu)
7. [Stratégies d'Indexation](#stratégies-dindexation)
8. [Concurrents RAG](#concurrents-rag)
9. [Discours Commercial](#discours-commercial)
10. [Recommandations Stratégiques](#recommandations-stratégiques)

---

## Résumé Exécutif

Spider Memory est le moteur de vectorisation interne de SpiderOS, servant tous les modules : Spider Builder (code), Spider People (emails/documents), Spider Chatbot (conversations), et Spider Content (marketing).

### Décisions Clés

| Composant | Choix | Raison |
|-----------|-------|--------|
| **Vector DB** | LanceDB | Embedded, gratuit, self-hosted, multi-modal |
| **Embeddings texte** | BGE-M3 (self-hosted) | 100+ langues, gratuit, 63.0 MTEB |
| **Embeddings code** | voyage-code-3 (API) | Meilleur pour code (97.3% MRR) |
| **Chunking** | Recursive 400-512 tokens | 85-90% recall, simple |
| **Multi-tenant** | Namespace par tenant | Simple, scalable, évolutif |
| **Infrastructure** | Clever Cloud + Scaleway | Partenariat, auto-scaling, Object Storage EU |

### Insights Clés

1. **LanceDB** = meilleur ratio simplicité/performance (embedded, pas de serveur)
2. **Architecture hybride embeddings** : voyage-code-3 pour le code, BGE-M3 pour le reste
3. **Delta indexing** obligatoire pour le code (re-index total intenable)
4. **Le discours "transparence + contrôle"** est la clé pour rassurer les utilisateurs

---

## Bases de Données Vectorielles

### Comparatif Global

| Critère | LanceDB | Pinecone | Weaviate | Qdrant | Chroma | Milvus |
|---------|---------|----------|----------|--------|--------|--------|
| **Local-first** | *** | - | ** | ** | *** | * |
| **Performance** | *** | *** | ** | *** | ** | *** |
| **Scalabilité** | *** | *** | ** | *** | * | *** |
| **Coût** | *** | * | ** | *** | *** | ** |
| **TypeScript SDK** | *** | ** | ** | ** | * | ** |
| **Cloud EU** | * | ** | ** | *** | * | ** |

Légende : *** Excellent, ** Bon, * Limité, - Non disponible

### LanceDB (Recommandé)

**Caractéristiques :**
- Architecture embedded (comme SQLite), pas de serveur requis
- Performance : <10ms pour 1M+ vecteurs
- Format Lance optimisé pour vecteurs (basé Apache Arrow)
- SDK natif Python + TypeScript
- Utilisé par CodeRabbit, Continue.dev, Midjourney, Runway

**Points forts :**
- Zero infrastructure à gérer
- Multi-modal natif (texte, images, audio)
- Scale via object storage (S3/Scaleway)
- Coût = 0 (open-source Apache 2.0)

**Trade-offs acceptables :**
- Performance légèrement inférieure à Qdrant (40-60ms vs 20-30ms)
- Recall 88% vs 95% — compensable avec du reranking

### Qdrant (Alternative Cloud EU)

**Points forts :**
- Partenariats européens : OVHcloud, Scaleway, STACKIT
- Performance/coût excellent
- Free tier généreux (1GB gratuit)

**Recommandation :** Pour besoins cloud européen avec conformité RGPD native.

### pgvector

**Utilisation :** Cas simples (Spider Content), limité au-delà de 50M vectors, pas multi-modal.

---

## Modèles d'Embedding

### Benchmark MTEB (Novembre 2025)

| Rang | Modèle | Score MTEB | Dimensions | Prix/1M tokens | Self-hosting |
|------|--------|------------|------------|----------------|--------------|
| 1 | **Cohere embed-v4** | 65.2 | 1024 | $0.10 | Non |
| 2 | OpenAI text-embedding-3-large | 64.6 | 3072 | $0.13 | Non |
| 3 | Voyage voyage-3-large | 63.8 | 1536 | $0.18 | Non |
| 4 | **BGE-M3** (open-source) | 63.0 | 1024 | Gratuit | **Oui** |
| 5 | Voyage **voyage-code-3** | ~65* | 1024 | $0.18 | Non |

*Score sur benchmarks code

### Pour le Code : voyage-code-3

| Modèle | MRR | nDCG | Recall@1 |
|--------|-----|------|----------|
| **voyage-code-3** | 0.973 | 0.970 | 0.950 |
| OpenAI 3-small | 0.950 | 0.945 | 0.910 |
| BGE-M3 | ~0.85 | ~0.86 | ~0.75 |
| CodeBERT | 0.117 | 0.477 | 0.065 |

**Justification :** voyage-code-3 a une performance quasi-parfaite sur le code. L'écart de 2.3% en MRR vs OpenAI justifie le coût supplémentaire.

### Pour le Texte Multilingue : BGE-M3

**Points forts :**
- Gratuit et self-hostable
- 100+ langues (dont français)
- Triple retrieval : dense, sparse, multi-vector
- Contexte long (8192 tokens)
- Performances proches des modèles commerciaux (63.0 vs 65.2)

**Ressources requises :**
- RAM : 4-8 GB (CPU) ou 4 GB VRAM (GPU)
- Latence CPU : ~100-200ms/batch
- Latence GPU : ~10-20ms/batch

### Architecture Recommandée

```
                    +------------------+
                    |   Spider Memory  |
                    |    (Routeur)     |
                    +--------+---------+
                             |
              +--------------+--------------+
              |                             |
    +---------v---------+       +-----------v-----------+
    |   Index Code      |       |   Index Texte         |
    |   voyage-code-3   |       |   BGE-M3 (local)      |
    |   (API externe)   |       |   FR/EN multilingue   |
    +-------------------+       +-----------------------+
```

---

## Stratégies de Chunking

### Par Type de Contenu

| Type | Stratégie | Taille chunk | Overlap |
|------|-----------|--------------|---------|
| **Mails** | Recursive + metadata | 400-512 tokens | 10-20% |
| **Code** | AST-based / Recursive | Par fonction/classe | Minimal |
| **Documents** | Structure-aware (Markdown) | 400-512 tokens | 10-20% |
| **Conversations** | Semantic chunking | Variable | Par échange |

### Baseline : Recursive Chunking (400-512 tokens)

**Pourquoi :**
- 85-90% recall dans les benchmarks
- Préserve la structure (paragraphes → phrases)
- Simple à implémenter (LangChain default)
- Fonctionne pour 80% des cas

```
Optimal settings: 256-512 tokens avec 10-20% overlap
```

### Pour les Cas Critiques : Semantic Chunking

**Quand l'utiliser :**
- Knowledge bases techniques
- Documents légaux/complexes
- Quand la précision > vitesse

**Gain :** +70% d'amélioration de recall vs fixed-size

### Pour le Code (Spider Builder)

**Recommandation :** AST-based chunking
- Parse le code en arbre syntaxique
- Chunk par fonction/classe/module
- Évite de couper du code en plein milieu

---

## Architecture Multi-Tenant

### Patterns Disponibles

| Pattern | Isolation | Complexité | Coût |
|---------|-----------|------------|------|
| **Namespace par tenant** | Logique | Simple | Bas |
| Shard par tenant | Physique | Moyen | Moyen |
| Database par tenant | Totale | Élevée | Élevé |

### Recommandation : Namespace par Tenant

**Pourquoi :**
- Simple à implémenter — Un namespace = un tenant
- Isolation suffisante — Les requêtes sont automatiquement scopées
- Scalable — Weaviate supporte 1M+ tenants par cluster
- Migration possible — On peut promouvoir un tenant en shard dédié si besoin

**Implémentation LanceDB :**
```
lancedb://
  └── spideros/
      └── tenant_{id}/
          ├── people_vectors/
          ├── chatbot_vectors/
          └── builder_vectors/
```

---

## Infrastructure Cloud EU

### Comparatif

| Critère | Clever Cloud | Scaleway | OVH |
|---------|-------------|----------|-----|
| **Type** | PaaS | IaaS/PaaS | IaaS |
| **Billing** | Per-second | Per-hour | Variable |
| **Auto-scaling** | Natif | Manuel | Manuel |
| **PostgreSQL** | Managed + PGPool II | Managed (pgvector) | Managed |
| **SecNumCloud** | Via Cloud Temple | Non | Oui |

### Verdict Infrastructure

| Composant | Choix recommandé | Raison |
|-----------|-----------------|--------|
| **Compute (apps)** | Clever Cloud | Partenariat, auto-scaling, PaaS |
| **Object Storage** | Scaleway | Prix (~0.0075€/GB/mois), performance, DX |
| **PostgreSQL** | Clever Cloud ou Scaleway | Managed, pgvector |
| **Vector DB cloud** | Qdrant + Scaleway | Hybrid Cloud natif |
| **SecNumCloud** | OVH ou Cloud Temple | Compliance grands comptes |

### Estimation Coûts (10TB de documents/assets)

| Provider | Prix/mois |
|----------|-----------|
| Scaleway | ~75€ |
| OVH Standard | ~119€ |
| OVH High Perf | ~390€ |
| AWS S3 | ~230€ |

---

## Stratégies d'Indexation

### Par Type de Donnée

| Type | Volatilité | Stratégie | Pattern |
|------|------------|-----------|---------|
| **Code** | Très haute | Delta indexing, watch mode | Hash detection, re-index fichiers modifiés uniquement |
| **Emails** | Zero (append-only) | Index once, never re-index | Append au vecteur |
| **Documents** | Basse | Version-based indexing | Nouvelle version = nouveau vecteur |
| **Conversations** | Append-only | Streaming index | Index au fil de l'eau |

### Delta Indexing (Best Practice)

```
1. DÉTECTER les changements
   - Merkle tree (hash de fichiers)
   - CDC (Change Data Capture) pour DB
   - File system watcher

2. TRAITER incrémentalement
   - MERGE/upsert operations (pas OVERWRITE)
   - Reuse cached embeddings pour fichiers inchangés
   - Buffer writes, periodic merge

3. MAINTENIR l'index
   - Soft delete plutôt que hard delete
   - Compaction périodique en off-peak
   - Re-indexation partielle si fragmentation
```

### Reference : GitHub Copilot

- Chunks sémantiques de 100-250 tokens
- Embeddings 512 dimensions
- Index SQLite local
- 750 fichiers indexés en 30-60 secondes
- **+37.6% retrieval quality** avec nouveau modèle (Sept 2025)

---

## Concurrents RAG

### Notion AI

- Data lake sur S3 (200+ milliards de blocks)
- Challenge : permissions computées "on-the-fly" via tree traversal
- Embeddings : OpenAI text-embedding-3 ou SBERT

**Insight :** L'enjeu n'est pas le RAG basique mais la gestion des permissions à scale.

### Slack AI

- Architecture **federated, real-time** : Pas de stockage des données sources
- **Escrow VPC** : LLMs hosted sur AWS, provider n'a jamais accès aux données
- RAG sans training sur customer data

**Insight :** Architecture federated = pas de copie des données, requête en temps réel. Peut réduire les coûts de stockage et simplifier la compliance.

### GitHub Copilot

- Modèle propriétaire fine-tuné code
- Training data : 36.7% Python, 19% Java, 13.8% C++, 8.9% JS/TS
- Index local SQLite, 512-dimensional vectors
- Limite actuelle : 2500 fichiers max

**Insight :** Pour le code, un modèle spécialisé fait une énorme différence.

### Matrice Comparative

| Aspect | Notion AI | Slack AI | GitHub Copilot | Spider Memory |
|--------|-----------|----------|----------------|---------------|
| **Scale** | 200B+ blocks | Federated | 2500 files max | Target: millions |
| **Storage** | Data lake S3 | Aucun (federated) | SQLite local | Hybride |
| **Embeddings** | OpenAI/generic | Non spécifié | Proprietary code | voyage-code + BGE-M3 |
| **Architecture** | Centralized | Federated | Local | Hybride |

---

## Discours Commercial

### Le Problème à Résoudre

> "Spider se souvient de tout" peut être **magique** ou **flippant** selon comment on le présente.

**Stats clés :**
- 71% des consommateurs font davantage confiance aux marques transparentes sur leurs données
- 73% sont plus fidèles aux marques qui expliquent comment elles utilisent l'IA
- 94% ne feraient pas affaire avec une entreprise qui ne protège pas leurs données
- 92% font confiance aux marques qui expliquent clairement l'usage des données

### Framework : "Transparence + Contrôle"

#### 1. Transparence Totale

**Messages clés :**
- "Tu vois exactement ce que Spider sait"
- "Chaque info a un score de confiance visible"
- "Les sources sont toujours citées"

**Feature :** Memory Dashboard

#### 2. Contrôle Absolu

**Messages clés :**
- "C'est ta mémoire, pas celle de Spider"
- "Corrige, supprime, exporte — c'est toi qui décides"
- "Mode incognito disponible"

**Feature :** Édition/suppression/export des données

#### 3. Utilité Évidente

**Messages clés :**
- "Brief en 200ms avant ton RDV"
- "Retrouve ce que tu cherches par le sens, pas par des mots-clés"
- "L'IA qui te connaît vraiment"

**Feature :** Recherches sémantiques, briefs automatiques

### Messaging à Éviter vs Recommandé

| ❌ À éviter | ✅ Dire plutôt |
|-------------|----------------|
| "Spider sait tout sur tes contacts" | "Spider t'aide à te souvenir" |
| "Surveillance intelligente" | "Mémoire assistée" |
| "On analyse tous tes mails" | "On structure tes échanges" |
| "IA omnisciente" | "IA contextuelle" |

### Tagline Options

1. **"Le cerveau de Spider — ta mémoire, amplifiée"**
2. **"Oublie d'oublier"**
3. **"La mémoire que tu contrôles"**

### Structure Page Marketing

```
1. PROBLÈME
   "Tu passes X heures par semaine à chercher des infos que tu as déjà vues"

2. SOLUTION (sans faire peur)
   "Spider Memory structure et retrouve pour toi — en millisecondes"

3. TRANSPARENCE (rassurer)
   "Tu vois tout. Tu corriges tout. Tu supprimes ce que tu veux."
   "Tes données restent en Europe. Point."

4. BÉNÉFICES CONCRETS
   - Brief avant RDV en 200ms
   - "Trouve les contacts où on a senti une résistance prix"
   - Score de confiance sur chaque info

5. CALL TO ACTION
   "Essaie la recherche sémantique" (feature safe, pas creepy)
```

---

## Recommandations Stratégiques

### Architecture Recommandée

```
+------------------+     +-------------------+
|  Spider Memory   |     |   PostgreSQL      |
|    (LanceDB)     |<--->|   (Métadonnées)   |
+------------------+     +-------------------+
         |
         v
+------------------+     +-------------------+
| Stockage Local   |     | Sync Optionnel    |
|   (SSD/NVMe)     |     | (S3-compatible)   |
+------------------+     +-------------------+
```

### Plan d'Implémentation

#### Phase 1 (Immédiat) : MVP

1. **LanceDB** comme vector store principal
2. **Cohere embed-v4** ou **BGE-M3** pour embeddings texte
3. **voyage-code-3** pour embeddings code
4. **Recursive chunking** 400-512 tokens
5. **Namespace par tenant**
6. **Memory Dashboard** dès le MVP (clé du messaging)

#### Phase 2 (3-6 mois) : Consolidation

1. Migration complète vers BGE-M3 self-hosted
2. Évaluer Qdrant + Scaleway si besoins cloud EU
3. Implémenter delta indexing complet pour Builder
4. Score de confiance sur chaque info

#### Phase 3 (6-12 mois) : Scale

1. Architecture hybride LanceDB + cloud si nécessaire
2. Préparer option SecNumCloud pour clients exigeants
3. Semantic chunking pour cas critiques
4. Sharding pour gros tenants

### Estimation des Coûts (10M documents)

*Hypothèse : 500 tokens/doc en moyenne = 5 milliards de tokens*

| Solution | Coût initial | Qualité |
|----------|--------------|---------|
| **BGE-M3 self-hosted** | $0 (+ infra ~$200-500/mois) | Très bonne |
| OpenAI 3-small (batch) | $50 | Bonne |
| OpenAI 3-large (batch) | $325 | Excellente |
| Cohere embed-v4 | $500 | Excellente |
| Voyage-code-3 (code uniquement) | $180 (après 200M gratuits) | Excellente |

### Recommandation par Priorité

| Priorité | Solution |
|----------|----------|
| **Coût minimal** | BGE-M3 self-hosted |
| **Simplicité maximale** | OpenAI 3-small |
| **Qualité maximale** | Cohere embed-v4 + voyage-code-3 |
| **Code source critique** | voyage-code-3 |
| **Confidentialité** | BGE-M3 self-hosted |

### Recommandation par Module

| Module | Sensibilité | Infrastructure |
|--------|-------------|----------------|
| **Builder** | Moyenne (code) | Clever Cloud ou local |
| **People** | **Haute** (emails, RH) | Clever Cloud ou OVH SecNumCloud |
| **Content** | Faible (marketing) | Scaleway |
| **Chatbot** | Haute (conversations) | Clever Cloud ou OVH SecNumCloud |

---

## Key Insights Consolidés

### Insight 1 : LanceDB = le bon choix pour le MVP
Embedded, zero infrastructure, self-hosted, gratuit.

### Insight 2 : Architecture hybride embeddings
voyage-code-3 pour le code, BGE-M3 pour le reste. Le modèle d'embedding fait une énorme différence pour le code (+37.6% chez GitHub).

### Insight 3 : Delta indexing non-négociable pour le code
GitHub Copilot, CodeRabbit, Continue.dev — tous utilisent du delta indexing.

### Insight 4 : pgvector peut suffire pour volumes modérés
Pour < 10M vecteurs, PostgreSQL + pgvector peut suffire.

### Insight 5 : Le messaging "contrôle utilisateur" est le différenciateur
Memory Dashboard dès le MVP, pas en P2.

### Insight 6 : Architecture federated (Slack AI) peut simplifier la compliance
Moins de données stockées = moins de risque RGPD.

---

## Sources

### Vector Databases
- LanceDB Official, AWS Architecture Blog, CodeRabbit Case Study
- Pinecone Pricing, Qdrant + Scaleway/OVHcloud
- Weaviate, Milvus documentation

### Embeddings
- MTEB Leaderboard, Voyage AI, BGE-M3 Hugging Face
- OpenAI Embedding Models, Cohere Embed

### Chunking & RAG
- Weaviate Chunking Strategies
- Firecrawl Best Chunking Strategies 2025
- LangCopilot Document Chunking Guide

### Concurrents
- Notion AI (ZenML), Slack Engineering
- GitHub Copilot (GitHub Blog, InfoQ)

### Marketing & Trust
- California Management Review - Privacy
- Mistral Memory Announcement, Notion AI Memory Guide

---

## Changelog Consolidation

| Date | Action |
|------|--------|
| 2026-01-14 | Consolidation de databases.md, embeddings.md, infrastructure.md, spider-memory-research-2026-01-14.md |
| 2026-01-14 | Harmonisation des sections et suppression doublons |
| 2026-01-14 | Ajout table des matières et résumé exécutif |
