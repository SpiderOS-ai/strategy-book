# Spider Strategy Research — Index

> Recherche stratégique pour Spider : Palantir-like AI-native pour PMEs européennes
> Projet porté par Nathan Menard (Drakkar) — Février 2026

---

## Structure du répertoire

```
spider-strategy/
├── INDEX.md                          ← Ce fichier
├── 01-initial-research/              ← Recherches initiales (Claude + GPT, pré-session)
├── 02-claude-syntheses/              ← Synthèses HTML interactives (Claude Code, session 1)
├── 03-claude-agent-research/         ← Recherches complémentaires (agents Claude Code, session 2-3)
├── 04-external-deep-research/        ← Deep research externe (Perplexity/Compass, session 3)
├── 05-final-synthesis/               ← Playbook final exhaustif (Claude Code, session 4)
├── 06-deep-research-phase2/          ← Deep research Phase 2 : reverse engineering méthode complète (session 6)
```

---

## Légende provenance

| Tag | Source | Description |
|-----|--------|-------------|
| `INIT-CLAUDE` | Claude (conversation directe) | Recherche initiale via prompt Claude |
| `INIT-GPT` | ChatGPT (conversation directe) | Recherche initiale via prompt GPT |
| `SYNTH-CC` | Claude Code (session interactive) | Synthèse HTML générée par Claude Code |
| `AGENT-CC` | Agents Claude Code (background) | Recherche par agents autonomes Claude Code |
| `EXT-DR` | Deep Research externe (Perplexity) | Deep research lancé manuellement par Nathan |
| `EXT-COMPASS` | Compass artifact (Perplexity) | Artifact compagnon d'un deep research |

---

## Chronologie complète

### Phase 1 — Recherche initiale | 17 fév 2026, ~14h00-14h45

Fichiers produits **avant** les sessions Claude Code, par conversations directes avec Claude et GPT.

| # | Fichier | Tag | Heure | Taille | Contenu |
|---|---------|-----|-------|--------|---------|
| — | `01-initial-research/00-prompts-initial-research.md` | — | — | — | **TODO** : prompts originaux utilisés pour générer ces 13 docs (à ajouter par Nathan) |
| 1 | `01-initial-research/00a-claude-pre-gtm-machine.md` | `INIT-CLAUDE` | 14:39 | 25 KB | Machine de pre-GTM : process de validation marché, acquisition premiers clients |
| 2 | `01-initial-research/00b-claude-pre-gtm-delivery-playbook.md` | `INIT-CLAUDE` | 14:43 | 44 KB | Playbook delivery pre-GTM : méthodologie de livraison et itération produit |
| 3 | `01-initial-research/00c-gpt-pre-gtm-playbook-FR.md` | `INIT-GPT` | 14:39 | 39 KB | Playbook pre-GTM version GPT en français |
| 4 | `01-initial-research/01-claude-product-architecture.md` | `INIT-CLAUDE` | 14:39 | 34 KB | Architecture produit Spider : stack technique, modules, intégrations |
| 5 | `01-initial-research/01-gpt-product-architecture.md` | `INIT-GPT` | 14:39 | 48 KB | Architecture produit version GPT : alternative stack et vision |
| 6 | `01-initial-research/02-claude-implementation-gtm.md` | `INIT-CLAUDE` | 14:39 | 32 KB | Implémentation + Go-to-market : roadmap, pricing, canaux |
| 7 | `01-initial-research/02-gpt-implementation-gtm.md` | `INIT-GPT` | 14:39 | 34 KB | Implémentation + GTM version GPT |
| 8 | `01-initial-research/03-claude-competitive-landscape.md` | `INIT-CLAUDE` | 14:39 | 33 KB | Paysage concurrentiel : Palantir, Dataiku, Pigment, etc. |
| 9 | `01-initial-research/03-gpt-competitive-landscape.md` | `INIT-GPT` | 14:39 | 54 KB | Paysage concurrentiel version GPT (plus détaillé) |
| 10 | `01-initial-research/04-claude-market-thesis.md` | `INIT-CLAUDE` | 14:39 | 26 KB | Thèse de marché : TAM/SAM/SOM, timing, wedge strategy |
| 11 | `01-initial-research/04-gpt-market-thesis.md` | `INIT-GPT` | 14:39 | 24 KB | Thèse de marché version GPT |
| 12 | `01-initial-research/05-claude-replication-blueprint.md` | `INIT-CLAUDE` | 14:39 | 40 KB | Blueprint de réplication Palantir : Ontology, FDE model, platform |
| 13 | `01-initial-research/05-gpt-replication-blueprint.md` | `INIT-GPT` | 14:39 | 34 KB | Blueprint réplication version GPT |

### Phase 2 — Synthèses Claude Code | 17 fév 2026, 15h00-16h00

Synthèses interactives HTML générées par Claude Code après lecture et croisement des 13 documents.

| # | Fichier | Tag | Heure | Taille | Contenu |
|---|---------|-----|-------|--------|---------|
| 14 | `02-claude-syntheses/synthesis.html` | `SYNTH-CC` | 15:02 | 103 KB | Synthèse globale : fusion des 13 docs, convergences/divergences, recommandations |
| 15 | `02-claude-syntheses/palantir-architecture.html` | `SYNTH-CC` | 15:23 | 65 KB | Deep-dive architecture Palantir : Ontology, Foundry, AIP, pour guider Spider |
| 16 | `02-claude-syntheses/challenge-roi-envelope.html` | `SYNTH-CC` | 15:58 | 69 KB | Challenge ROI envelope : stress-test du business model Spider |

### Phase 3 — Recherche agents Claude Code | 17 fév 2026, 16h15-16h45

Recherches complémentaires par agents autonomes Claude Code (web search + analyse).
Lancés pour combler les gaps identifiés dans la gap analysis des 13 docs.

| # | Fichier | Tag | Heure | Taille | Contenu |
|---|---------|-----|-------|--------|---------|
| 17 | `03-claude-agent-research/06-research-counter-thesis-data.md` | `AGENT-CC` | 16:34 | 38 KB | Contre-thèse data : APEX benchmark 29.8%, Burry $46, a16z Palantirization, PLTR P/E 206x |
| 18 | `03-claude-agent-research/07-research-smb-ai-failures-french-market.md` | `AGENT-CC` | 16:34 | 25 KB | Échecs AI PME : RAND 80% failure, MIT 95% pilots fail, France Num 26% adoption |
| 19 | `03-claude-agent-research/08-research-odoo-france-erp-market.md` | `AGENT-CC` | 16:37 | 26 KB | Marché ERP France : Odoo 15M users, Sage 43K FR, Cegid 750K post-EBP, marché $3.49B |
| 20 | `03-claude-agent-research/09-research-eu-regulatory-landscape.md` | `AGENT-CC` | 16:38 | 34 KB | Réglementation EU : Spider = risque limité AI Act, SecNumCloud, NIS2, e-invoicing 2026 |
| 21 | `03-claude-agent-research/10-research-odoo-api-ecosystem.md` | `AGENT-CC` | 16:39 | 30 KB | Écosystème API Odoo : JSON-2 remplace XML-RPC (Odoo 20), Nango ≠ Odoo, 123 partners FR |
| 22 | `03-claude-agent-research/11-research-vertical-ai-comparables.md` | `AGENT-CC` | 16:39 | 29 KB | Comparables AI verticaux : DualEntry $100M, Vanta $220M ARR, pas de "Palantir for SMBs" |

### Phase 4 — Deep Research externe | 17 fév 2026, ~17h00-17h25

Deep research lancé par Nathan via Perplexity Pro, à partir des prompts générés en Phase 3.
Les prompts utilisés sont dans `04-external-deep-research/00-prompts-deep-research.md`.

| # | Fichier | Tag | Heure | Taille | Contenu |
|---|---------|-----|-------|--------|---------|
| 23 | `04-external-deep-research/00-prompts-deep-research.md` | `AGENT-CC` | 16:32 | 10 KB | 2 prompts deep research utilisés pour générer les fichiers ci-dessous |
| 24 | `04-external-deep-research/deep-research-report-6-palantir-ontology.md` | `EXT-DR` | 17:26 | 33 KB | Ontology Palantir internals : schema evolution (manual remapping), conflict resolution (dual-track writeback), Elasticsearch indexing, optimistic concurrency, markings-based security |
| 25 | `04-external-deep-research/deep-research-report-7-fde-economics.md` | `EXT-DR` | 17:26 | 30 KB | FDE-to-self-service economics : headcount curve 30-40%→~10%, bootcamp conversion, margin decomposition, AIFD impact |
| 26 | `04-external-deep-research/compass-palantir-ontology-implementation.md` | `EXT-COMPASS` | 17:26 | 23 KB | Artifact compagnon Ontology : stratégies de traduction PostgreSQL, détails implémentation |
| 27 | `04-external-deep-research/compass-fde-transition-economics.md` | `EXT-COMPASS` | 17:26 | 21 KB | Artifact compagnon FDE : données fiabilisées pour modélisation financière |

### Phase 5 — Synthèse finale | 17 fév 2026, ~18h00-19h00

Document unique exhaustif assemblant TOUT ce qu'on sait sur Palantir en un seul playbook HTML interactif.
Corrections de données vérifiées par web search, 10 errata documentés.

| # | Fichier | Tag | Heure | Taille | Contenu |
|---|---------|-----|-------|--------|---------|
| 28 | `05-final-synthesis/05-palantir-complete-playbook.html` | `SYNTH-CC` | 19:00 | 322 KB | **Playbook exhaustif Palantir** — Part A: Architecture (Gotham, Foundry, AIP, Apollo, Ontology deep-dive, 5 engineering decisions, replicability map), Part B: Consulting (FDE model, bootcamps, Acquire/Expand/Scale, AIFD, partnerships), Part C: Commercial (financials FY2025, pricing, competitive landscape, key quotes), Part D: Errata (10 corrections vérifiées avec sources) |
| 29 | `05-final-synthesis/06-palantir-replication-blueprint.html` | `SYNTH-CC` | 20:30 | 43 KB | **Blueprint visuel macro** — Comment recréer Palantir : schémas SVG inline (3 piliers BUILD/DELIVER/SELL, data flow 7 étapes avec équivalents OSS, pipeline delivery Bootcamp→Scale, flywheel revenus), rôles clés (FDE, DS), métriques, pricing, moat, adaptations Spider vs Palantir |

Fichiers intermédiaires de production (dans `05-final-synthesis/`) :
- `shell-template.html` — Template CSS/navigation assemblé
- `part-a-architecture.html` — Part A brute (102 KB)
- `part-b-consulting.html` — Part B brute (70 KB)
- `part-c-commercial.html` — Part C brute (79 KB)
- `part-d-errata.html` — Part D brute (55 KB)

### Phase 6 — Deep Research Phase 2 : Reverse Engineering Méthode | 17 fév 2026, ~21h00+

Deep research pour reverse-engineer la méthode complète Palantir : avant-vente, bootcamp jour par jour, pilot 90 jours, expand/scale, outils Foundry concrets.
Prompts générés par Claude Code, à lancer dans Perplexity Pro.

| # | Fichier | Tag | Heure | Taille | Contenu |
|---|---------|-----|-------|--------|---------|
| 30 | `06-deep-research-phase2/00-prompts-deep-research-phase2.md` | `AGENT-CC` | 21:00 | 16 KB | **4 prompts deep research** — (1) Pre-sales & bootcamp jour par jour avec livrables, (2) Pilot 90j : process mapping, ontology building, pipeline, training, (3) Expand & Scale : captivité, CoE, FDE withdrawal, switching costs, (4) Outils Foundry concrets : Workshop, Pipeline Builder, Ontology Manager, AIP, OSDK, Apollo |
| — | `06-deep-research-phase2/deep-research-report-8-presales-bootcamp-playbook.md` | `EXT-DR` | — | — | **TODO** : résultat Perplexity prompt 1 |
| — | `06-deep-research-phase2/deep-research-report-9-pilot-implementation-methodology.md` | `EXT-DR` | — | — | **TODO** : résultat Perplexity prompt 2 |
| — | `06-deep-research-phase2/deep-research-report-10-expand-scale-captivity-playbook.md` | `EXT-DR` | — | — | **TODO** : résultat Perplexity prompt 3 |
| — | `06-deep-research-phase2/deep-research-report-11-foundry-tools-concrete-ux.md` | `EXT-DR` | — | — | **TODO** : résultat Perplexity prompt 4 |

---

## Résumé quantitatif

| Phase | Nb fichiers | Taille totale | Source |
|-------|-------------|---------------|--------|
| 1 — Initial Research | 13 | ~466 KB | Claude + GPT (conversations) |
| 2 — Synthèses HTML | 3 | ~237 KB | Claude Code (session 1) |
| 3 — Agent Research | 6 | ~182 KB | Claude Code agents (sessions 2-3) |
| 4 — Deep Research | 5 | ~117 KB | Prompts CC + résultats Perplexity Pro (session 3) |
| 5 — Final Synthesis | 2 (+5 intermédiaires) | ~365 KB | Claude Code (sessions 4-5) |
| 6 — Deep Research Phase 2 | 1 (+4 TODO) | ~16 KB | Prompts CC + résultats Perplexity Pro (session 6) |
| **Total** | **30** (+5+4 TODO) | **~1 383 KB** | — |

---

## Findings clés par thème

### Architecture produit Spider
- **Ontology** : 6 primitives (Objects, Properties, Links, Actions, Interfaces, Value Types), 3 couches (Semantic, Kinetic, Dynamic) → fichiers #12, #24, #26
- **Stack** : PostgreSQL (JSONB + pgvector) comme backbone unique → fichiers #4, #5, #14
- **API Odoo** : JSON-2 remplace XML-RPC en oct 2026, Nango ne supporte pas Odoo → fichier #21

### Marché & positionnement
- **Gap confirmé** : aucun "Palantir for SMBs" n'existe nulle part → fichier #22
- **France ERP** : $3.49B, Odoo 15M users, 44.8% sans customisation ERP → fichier #19
- **Pricing validé** : Vanta $220M ARR à $833-$6,667/mois, DualEntry 50%+ premium → fichier #22

### Risques & régulation
- **EU AI Act** : Spider = risque limité/minimal (avantage compétitif) → fichier #20
- **Contre-thèse** : APEX benchmark 29.8% best, 80% AI projects fail → fichiers #17, #18
- **Souveraineté** : SecNumCloud 3.2 exclut hyperscalers US, Mistral €11.7B → fichier #20

### Modèle économique
- **FDE economics** : $220K-$500K/FDE, ratio 1:$2-5M ARR, marge 68%→84% → fichiers #25, #27
- **Challenge ROI** : stress-test du pricing Spider €500-5,000/mois → fichier #16
