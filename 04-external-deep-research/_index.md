# External Deep Research — Index

> Recherches approfondies produites par des modèles externes (Claude et GPT) via des prompts de deep research structurés, ciblant deux zones d'incertitude critiques : l'implémentation technique de l'Ontologie Palantir et les économies de la transition FDE-vers-self-service.

---

## `00-prompts-deep-research.md`
**Rôle :** Document source des deux prompts de deep research envoyés à des modèles externes, avec le contexte de ce qu'on savait déjà et les gaps précis à combler.
**Findings clés :**
- Prompt #1 : 5 questions techniques précises sur l'Ontologie Palantir (versioning de schéma, résolution de conflits, indexing OSV2, modèle transactionnel des Actions, sécurité PBAC)
- Prompt #2 : 5 questions économiques sur la transition FDE-heavy → self-service (courbe headcount FDE, funnel bootcamp, décomposition de la marge, impact AIFD, métriques d'autonomie client)
- Matrice de gaps restants : souveraineté des données EU (résolu), marché SMB français (résolu), competitive landscape (résolu), blueprint GTM Spider (résolu) — les deux prompts ciblent les deux seuls gaps restants non couverts par les 13 documents agents

---

## `claude-fde-transition-economics.md`
**Rôle :** Modèle quantitatif de la transition Palantir de services-lourds vers platform-driven revenue, construit à partir des filings SEC et materials IR, avec tags de fiabilité [CONFIRMED/ESTIMATED/SPECULATIVE].
**Findings clés :**
- Courbe FDE headcount : de ~30-40% des effectifs en 2016 à ~8-12% en 2025 ; le "flip" FDE>SWE a eu lieu vers 2016-2017 ; le ratio cible est 1 FDE par $2-5M ARR — le revenue par FDE a été multiplié par 8-12x en 9 ans
- Funnel bootcamp : ~22% de conversion (estimation analysts, non confirmé Palantir) ; coût par bootcamp $12-36K (SPECULATIVE) ; CAC résultant $110-165K ; compression du cycle de vente de 9 mois à 6 semaines [CONFIRMED]
- Décomposition de la marge : l'expansion de 68% → 84% inclut ~5-7pp d'effet comptable (FDE classés en S&M pas en COGS depuis l'IPO) — la vraie marge ajustée hors SBC était déjà 81% en 2020 ; l'amélioration "réelle" est 81% → 84%
- AIFD : pas de réduction d'effectif FDE observée (4,414 employés fin sept. 2025 vs 3,936 fin 2024) — l'IA est un multiplicateur de productivité (revenue/employé : $448K → $1.01M en 5 ans), pas un outil de licenciement

---

## `claude-palantir-ontology-implementation.md`
**Rôle :** Deep dive technique sur les 5 mécanismes d'implémentation de l'Ontologie Palantir — versioning de schéma, résolution de conflits, indexing OSV2, modèle transactionnel Actions, et sécurité PBAC — avec stratégies PostgreSQL équivalentes.
**Findings clés :**
- Schema evolution : l'Ontologie est une couche d'abstraction sémantique au-dessus de datasets Parquet ; les changements "breaking" bloquent la sauvegarde jusqu'à définition d'une migration explicite ; "Ontology as Code" permet l'export/import JSON — PostgreSQL peut faire mieux avec Flyway + migrations versionnées + rollback
- Résolution de conflits : double-track — "edits layer" (user edit wins par COALESCE au read-time) + "writeback dataset" (developer-managed merge logic) ; OSV2 applique l'overlay immédiatement, persist toutes les 6 heures — reproduisable en PostgreSQL avec une table `object_edits` + vue matérialisée
- Indexing OSV2 : Elasticsearch/Lucene-based (confirmé par job postings + sémantique des analysers) ; limite documentée : 3 hops max en Search Around, structs max 10 champs, streaming 2MB/s par object type ; Meilisearch recommandé comme companion pour l'alternative PostgreSQL au scale PME
- Security PBAC : markings = MAC (mandatory access control) à granularité objet + propriété ; AIP exécute avec les permissions de l'utilisateur invoquant, pas de plane de permission AI séparé ; PostgreSQL peut approcher via RLS + FORCE ROW LEVEL SECURITY + application-layer enforcement, mais les 3 gaps irréductibles (no superuser bypass, no auto marking propagation, no PBAC) nécessitent un gateway applicatif

---

## `gpt-fde-economics.md`
**Rôle :** Version GPT de la recherche sur les économies FDE, avec sources primaires SEC et IR explicitées, méthodologie de modélisation détaillée, et blueprint quantitatif pour Spider.
**Findings clés :**
- Effectifs confirmés : 2,391 employés fin 2019 (S-1/A) → 3,936 fin 2024 (10-K) → 4,414 sept. 2025 (10-Q) ; en 2019 : 929 "software engineers and other technical staff" — le reste inclut les FDEs mais la frontière est floue car les SWEs "rotate between field and development"
- Bootcamp economics : coût par bootcamp estimé £/$25-70K (commercial) à £/$50-150K (gouvernement) basé sur les catégories S&M des filings ; Palantir confirme dans le 10-K que les bootcamps sont en S&M et non en COGS, ce qui gonfle mécaniquement le gross margin reporté
- Automation confirmée : 10-K 2020 confirme "more than five-fold decrease in time to begin working" grâce à Apollo ; Q3 2025 : AIFD peut migrer un data warehouse legacy en 5 jours vs "2 ans pour des SIs" [CONFIRMED] — mais headcount continue de croître, c'est un multiplicateur pas un réducteur
- Blueprint Spider : 5 KPIs à tracer — (1) coût humain de déploiement par $1M ARR (cible <€50K vs Palantir $80K) ; (2) time-to-self-sufficiency (cible <2 semaines vs 12-36 mois Palantir historique) ; (3) marge brute vraie >85% ; (4) NDR >130% ; (5) revenue/employé >€500K dès Year 2

---

## `gpt-palantir-ontology.md`
**Rôle :** Version GPT du deep dive ontologie, avec extraction directe de la documentation officielle Palantir (URLs vérifiables), analyse des brevets USPTO, et traduction PostgreSQL concrète pour chaque mécanisme.
**Findings clés :**
- Schema evolution confirmée : Foundry détecte les "breaking schema changes" et bloque la sauvegarde jusqu'à migration définie ; une pipeline de remplacement (Funnel batch) se construit en parallèle et cutover atomique une fois hydratée — pattern "remplacement d'index" à reproduire en PostgreSQL via materialized views + atomic pointer flip
- Conflict resolution documentée : Strategy 1 = "user edits always win" (défaut) ; Strategy 2 = "most recent value" configurable par datasource avec colonne timestamp UTC requise ; dans OSV2, les edits sont visibles immédiatement via l'API publique (read-after-write consistency) grâce à un index live mis à jour avant flush des 6h
- Actions : atomicité confirmée ("single transaction" ; edits appliqués atomiquement à la fin de l'appel) ; OCC (optimistic concurrency) avec version checks ; 2 types de side effects — writeback webhooks (avant commit, faillent l'action entière) vs side-effect webhooks (après commit, best-effort, at-least-once) ; PostgreSQL excède Palantir sur les garanties transactionnelles avec le transactional outbox pattern
- Security : markings = MAC conjunctif (doit satisfaire ALL markings) ; propagation automatique à travers la lineage des datasets ; AIP s'exécute "on behalf of" l'utilisateur invoquant — pas de permission AI spéciale ; lien-visibilité : les objets inaccessibles sont supprimés des résultats de traversal (non-leak par design), à spécifier et tester explicitement dans une alternative open-source
