# COMPLETE AUDIT -- spider-strategy research directory

**Date of audit:** 19 February 2026
**Total files inventoried:** 133 (including raw/binary assets)
**Total text/code files:** ~110
**Combined text size:** ~5.5 MB

---

## ROOT LEVEL

### `INDEX.md` -- 12.6 KB
**Content:** Chronological index of phases 1-6, with file descriptions, tags (INIT-CLAUDE, INIT-GPT, SYNTH-CC, AGENT-CC, EXT-DR), sizes, timestamps, and key findings per theme.
**Quality:** Good, but OUTDATED. It was written after Phase 6 but before 07-spider-inputs was created. It does not mention a single file from 07-spider-inputs. The Phase 6 section still shows 4 files as "TODO" (the deep research results) -- but those results arrived and were processed into the massive syntheses in 06. The INDEX is therefore about 60% accurate. It also does not track any of the 06 synthesis/HTML files produced after the raw research landed.
**Classification: Archive-worthy but needs update before mega livrable.**

### `palantir-apollo-research.md` -- 30.9 KB, 30 KB
**Content:** Focused deep-dive on Palantir's Apollo platform: hub-and-spoke deployment, air-gapped environments, pull-based model, 90K upgrades/week, Kubernetes orchestration. With cited source URLs from palantir.com/docs.
**Quality:** High. Unique coverage -- Apollo is barely touched in other files. This is NOT redundant.
**Classification: Final deliverable. Keep at root or move to 06.**

---

## FOLDER 01 -- Initial Research (13 files, ~466 KB)

These were produced on 17 Feb 2026 ~14h before any Claude Code sessions, via direct Claude and GPT conversations.

| File | Size | Content | Quality |
|------|------|---------|---------|
| `00-prompts-deep-research.md` | 17.7 KB | The actual prompts used to generate files 01-05 (Claude + GPT). Organized by topic. | Archive -- meta-document, needed for reproducibility |
| `00a-claude-pre-gtm-machine.md` | 25.2 KB | Pre-GTM machine: market validation process, first client acquisition method | Intermediate. Partially superseded by SPIDER-FINAL.md |
| `00b-claude-pre-gtm-delivery-playbook.md` | 43.9 KB | Delivery playbook pre-GTM: methodology, iteration loops | Intermediate. Better version exists in Phase 5/6 |
| `00c-gpt-pre-gtm-playbook-FR.md` | 39.2 KB | GPT French pre-GTM playbook | Intermediate / Archive |
| `01-claude-product-architecture.md` | 34.0 KB | Spider product architecture: stack, modules, integrations | Intermediate. Superseded by 07 tech docs |
| `01-gpt-product-architecture.md` | 47.7 KB | GPT version of product architecture | Archive |
| `02-claude-implementation-gtm.md` | 32.1 KB | Implementation + GTM roadmap, pricing, channels | Intermediate / Archive |
| `02-gpt-implementation-gtm.md` | 33.6 KB | GPT version of GTM | Archive |
| `03-claude-competitive-landscape.md` | 33.4 KB | Competitive landscape: Palantir, Dataiku, Pigment | Intermediate. Superseded by SPIDER-POSITIONING-2026.md |
| `03-gpt-competitive-landscape.md` | 54.1 KB | GPT competitive landscape (more detailed) | Archive |
| `04-claude-market-thesis.md` | 25.8 KB | Market thesis: TAM/SAM/SOM, timing, wedge | Intermediate. Superseded by SPIDER-MEGA-RECAP.md |
| `04-gpt-market-thesis.md` | 23.8 KB | GPT market thesis | Archive |
| `05-claude-replication-blueprint.md` | 39.6 KB | Blueprint to replicate Palantir: Ontology, FDE, platform | Intermediate. Superseded by SPIDER-PALANTIR-BLUEPRINT.md |
| `05-gpt-replication-blueprint.md` | 34.0 KB | GPT version of replication blueprint | Archive |

**Overlap:** The GPT and Claude versions of each topic overlap heavily with each other and with later syntheses. None of the 01 files are final deliverables -- they are raw material that was processed.
**Verdict: Entire folder = historical archive. No file from 01 should feed the mega livrable directly.**

---

## FOLDER 02 -- Claude Syntheses (3 files, ~237 KB)

Produced 17 Feb 2026 ~15h, session 1 of Claude Code.

| File | Size | Content | Quality |
|------|------|---------|---------|
| `synthesis.html` | 102.6 KB | Global synthesis fusing all 13 initial docs -- convergences, divergences, recommendations. First HTML artifact. | Intermediate. Superseded by everything in 05 and 06 |
| `palantir-architecture.html` | 64.6 KB | Deep-dive Palantir architecture: Ontology, Foundry, AIP | Intermediate. Superseded by 05-palantir-complete-playbook.html |
| `challenge-roi-envelope.html` | 69.3 KB | ROI stress-test of Spider's business model | Intermediate. Unique angle but the data is older |

**Overlap:** synthesis.html and palantir-architecture.html are ancestral versions of what later became the 322KB playbook. challenge-roi-envelope.html has some unique content (business model stress-test) not replicated elsewhere -- worth preserving.
**Verdict: Archive all. challenge-roi-envelope.html has salvageable unique content.**

---

## FOLDER 03 -- Claude Agent Research (8 files, ~295 KB)

Produced 17 Feb 2026 ~16h, by autonomous Claude Code agents.

| File | Size | Content | Quality |
|------|------|---------|---------|
| `06-research-counter-thesis-data.md` | 38.0 KB | Counter-thesis data: APEX 29.8%, Burry $46, a16z Palantirization, PLTR P/E 206x | High quality research. Unique -- bears risk data |
| `07-research-smb-ai-failures-french-market.md` | 25.4 KB | SMB AI failures: RAND 80% failure, MIT 95% pilots, France Num 26% adoption | High quality. Unique risk data |
| `08-research-odoo-france-erp-market.md` | 25.9 KB | ERP France market: Odoo 15M users, Sage 43K FR, Cegid 750K, $3.49B market | High quality. Market data |
| `09-research-eu-regulatory-landscape.md` | 34.3 KB | EU AI Act: Spider = minimal risk, SecNumCloud, NIS2, e-invoicing 2026 | High quality. Unique regulatory angle |
| `10-research-odoo-api-ecosystem.md` | 29.9 KB | Odoo API ecosystem: JSON-2 replaces XML-RPC (Odoo 20), 123 FR partners | High quality. Specific technical data |
| `11-research-vertical-ai-comparables.md` | 28.6 KB | Vertical AI comparables: DualEntry $100M, Vanta $220M ARR | High quality. Market validation data |
| `12-research-palantir-churn-switching-lockin.md` | 33.7 KB | Palantir churn mechanics, switching costs ($2.5-7.5M), lock-in | High quality |
| `12-research-palantir-competitors-deployment-comparison.md` | 43.3 KB | Palantir vs. competitors deployment comparison | High quality |
| `12-research-palantir-government-contracts.md` | 31.5 KB | Government contracts methodology | Intermediate -- less relevant for SMB focus |
| `13-research-european-data-sovereignty.md` | 46.3 KB | European data sovereignty in depth | High quality |
| `13-research-palantir-fde-training-onboarding.md` | 39.5 KB | FDE training and onboarding details | High quality |
| `13-research-palantir-mafia-ex-fde-startups.md` | 33.5 KB | Palantir Mafia: ex-FDE startups | High quality. Unique intelligence |

**Note:** There are three files numbered 12 and two files numbered 13 -- numbering collision. All content is unique.
**Overlap:** Much of this was synthesized into SYNTHESE-GLOBALE-PHASE2.md, extracted-parts-abcd.md, and PLAYBOOK-DEFINITIF-PALANTIR.md. The raw files are the primary sources.
**Verdict: High quality source material. Archive the folder but flag 06, 07, 09, 10, 11, 12 as particularly valuable for the mega livrable.**

---

## FOLDER 04 -- External Deep Research (5 files, ~117 KB)

Deep research via Perplexity Pro, Phase 4.

| File | Size | Content | Quality |
|------|------|---------|---------|
| `00-prompts-deep-research.md` | 10.1 KB | The 2 prompts used for this phase | Archive -- meta |
| `claude-fde-transition-economics.md` | 20.6 KB | FDE-to-self-service economics: headcount curve 30-40% to 10%, bootcamp conversion, margin decomposition | High quality -- financial modelling data |
| `claude-palantir-ontology-implementation.md` | 23.3 KB | Ontology implementation details: PostgreSQL translation, schema evolution | High quality -- technical |
| `gpt-fde-economics.md` | 30.3 KB | FDE economics from GPT's deep research | Intermediate -- partially redundant with claude version |
| `gpt-palantir-ontology.md` | 33.5 KB | Palantir ontology from GPT | Intermediate -- partially redundant |

**Note:** The INDEX.md lists these with different filenames (deep-research-report-6, compass-...) than what actually exists (claude-..., gpt-...). Filename discrepancy between INDEX and actual files.
**Overlap:** Content was absorbed into PLAYBOOK-DEFINITIF-PALANTIR.md.
**Verdict: Keep as archive. FDE economics files have unique granular data.**

---

## FOLDER 05 -- Final Synthesis (7 files, ~740 KB)

Produced 17 Feb 2026 ~18h-20h, sessions 4-5.

| File | Size | Content | Quality | Classification |
|------|------|---------|---------|----------------|
| `05-palantir-complete-playbook.html` | 331.9 KB | THE master Palantir playbook: Part A Architecture (Gotham/Foundry/AIP/Apollo/Ontology, 5 engineering decisions), Part B Consulting (FDE model, bootcamps, Acquire/Expand/Scale, AIFD), Part C Commercial (FY2025 financials, pricing, competitive), Part D Errata (10 verified corrections). 322KB, 7890 lines. | CROWN JEWEL. Primary reference for everything Palantir. | Final deliverable |
| `06-palantir-replication-blueprint.html` | 69.6 KB | Visual macro blueprint: SVG inline schemas (3 pillars BUILD/DELIVER/SELL, 7-step data flow, pipeline Bootcamp to Scale, revenue flywheel), key roles, metrics, pricing, moat, Spider vs Palantir adaptations | Final deliverable. Companion visual to above. | Final deliverable |
| `part-a-architecture.html` | 101.8 KB | Part A raw fragment before assembly | Production artifact -- superseded |
| `part-b-consulting.html` | 70.0 KB | Part B raw fragment | Production artifact -- superseded |
| `part-c-commercial.html` | 79.0 KB | Part C raw fragment | Production artifact -- superseded |
| `part-d-errata.html` | 55.3 KB | Part D raw fragment | Production artifact -- superseded |
| `shell-template.html` | 24.1 KB | CSS + nav template used to assemble the full playbook | Production artifact |

**Verdict: Keep 05 and 06. The parts A-D + shell = pure assembly artifacts, should be archived/deleted. They add nothing that isn't in 05-palantir-complete-playbook.html.**

---

## FOLDER 06 -- Deep Research Phase 2 (41 files, ~3.8 MB)

The largest and most complex folder. Produced from ~18 Feb 2026 onward.

### A) Prompt files (1 file)

| File | Size | Content |
|------|------|---------|
| `00-prompts-deep-research-phase2.md` | 23.2 KB | 4 deep research prompts: pre-sales bootcamp, pilot 90 days, expand/scale, Foundry tools concrete UX | Meta -- keep for reproducibility |

### B) Raw research inputs from Claude agents (7 files)

| File | Size | Content | Classification |
|------|------|---------|----------------|
| `01-palantir-fde-methodology-deep-dive.md` | 35.8 KB | FDE methodology detailed | Source material |
| `01-palantir-workshop-ui-deep-dive.md` | 45.3 KB | Workshop UI deep dive -- concrete UX of Palantir Workshop | Source material -- unique |
| `12-research-foundry-pipelines-osdk.md` | 38.4 KB | Foundry pipelines + OSDK technical details | Source material |
| `13-research-consulting-vs-palantir-methodology.md` | 42.3 KB | Consulting firms vs Palantir methodology comparison | Source material |
| `14-research-smb-data-platform-deployment.md` | 38.4 KB | SMB data platform deployment patterns | Source material |
| `15-research-ontology-design-patterns.md` | 45.6 KB | Ontology design patterns (detailed) | Source material -- very valuable |
| `16-research-palantir-patents-implementation-details.md` | 47.1 KB | Palantir patent analysis + implementation specifics | Source material -- unique |
| `palantir-demos-transcripts-concrete-evidence.md` | 39.7 KB | AIPCon demo transcripts, concrete evidence from public demos | Source material -- unique |

### C) External deep research results (12 files in /results/)

Three sources (GPT, Claude, Perplexity) each ran the 4 prompts, yielding 12 raw results:

| File | Size | Content |
|------|------|---------|
| `results/gpt-presales-bootcamp-playbook.md` | 42.0 KB | GPT: bootcamp playbook |
| `results/gpt-pilot-implementation-methodology.md` | 51.1 KB | GPT: pilot methodology |
| `results/gpt-expand-scale-captivity-playbook.md` | 30.6 KB | GPT: expand/scale captivity |
| `results/gpt-foundry-tools-concrete-ux.md` | 45.6 KB | GPT: Foundry tools UX |
| `results/claude-bootcamp-playbook.md` | 31.3 KB | Claude: bootcamp |
| `results/claude-pilot-methodology.md` | 27.9 KB | Claude: pilot |
| `results/claude-expand-scale.md` | 26.5 KB | Claude: expand/scale |
| `results/claude-foundry-tools.md` | 27.9 KB | Claude: Foundry tools |
| `results/perplexity-bootcamp-playbook.md` | 45.2 KB | Perplexity: bootcamp |
| `results/perplexity-pilot-methodology.md` | 43.0 KB | Perplexity: pilot |
| `results/perplexity-expand-scale-playbook.md` | 43.0 KB | Perplexity: expand/scale |
| `results/perplexity-foundry-tools.md` | 42.1 KB | Perplexity: Foundry tools |

Plus 4 cross-source synthesis files (in /results/):

| File | Size | Content |
|------|------|---------|
| `results/synthese-1-presales-bootcamp-playbook.md` | 65.3 KB | Merged synthesis of 3 bootcamp sources (691 lines) |
| `results/synthese-2-pilot-implementation-methodology.md` | 67.0 KB | Merged synthesis of 3 pilot sources (649 lines) |
| `results/synthese-03-expand-scale-playbook.md` | 65.2 KB | Merged synthesis of 3 expand/scale sources (619 lines) |
| `results/synthese-04-foundry-tools.md` | 71.6 KB | Merged synthesis of 3 Foundry tools sources (959 lines) |

### D) Intermediate HTML fragments (7 files -- NO `<html>` tag, fragments only)

| File | Size | Content |
|------|------|---------|
| `html-part1.html` | 157.9 KB | Avant-vente & AIP Bootcamp (fragment) |
| `html-part2.html` | 146.0 KB | Pilot Acquire 90 days (fragment) |
| `html-part2-delivery-method.html` | 131.0 KB | Delivery method section (fragment) -- DUPLICATE topic coverage with html-part2.html |
| `html-part3.html` | 120.4 KB | Commercial engine (fragment) |
| `html-part4.html` | 180.2 KB | Foundry tools in detail (fragment) |
| `html-part4-market.html` | 103.6 KB | Market context (fragment) |
| `mega-part1-the-product.html` | 124.0 KB | Mega document Part 1: the product (fragment) |

**Critical observation:** html-part2.html and html-part2-delivery-method.html both cover the delivery/pilot phase -- likely generated in separate attempts. html-part4.html (Foundry) and html-part4-market.html appear to be two different Part 4 versions. These are intermediate assembly fragments that were never stitched into a complete document.

### E) Major synthesis/consolidation files (9 files)

| File | Size | Content | Classification |
|------|------|---------|----------------|
| `PLAYBOOK-DEFINITIF-PALANTIR.md` | 334.5 KB / 4,948 lines | THE master markdown synthesis assembled 18 Feb 2026. Covers all 4 phases: bootcamp, pilot, expand/scale, Foundry tools. Cross-referenced from 20+ sources. Confidence tags. | CROWN JEWEL (markdown). Companion to 05-palantir-complete-playbook.html |
| `PLAYBOOK-DEFINITIF-PALANTIR.html` | 619.4 KB | HTML rendered version of the above | Largest single file in repo. Final deliverable |
| `PALANTIR-FULL-RECAP.md` | 234.5 KB / 4,530 lines | Complete knowledge base compiled from 50+ documents. 7 parts: Architecture, Delivery, Commercial, Market, GTM Synthesis, Errata, Visual Atlas. | Crown jewel -- most comprehensive single MD |
| `PALANTIR-MEGA-PLAYBOOK.html` | 486.7 KB | HTML version -- "The Complete Palantir Playbook -- Mega Document" | Final deliverable |
| `PALANTIR-MEGA-OVERVIEW.html` | 199.7 KB | "The Complete Palantir Playbook -- Visual Atlas" | Final deliverable |
| `PALANTIR-VISUAL-ATLAS.html` | 199.7 KB | EXACT SAME size as PALANTIR-MEGA-OVERVIEW.html. Both have the same title "The Complete Palantir Playbook -- Visual Atlas" | DUPLICATE -- identical files |
| `PALANTIR-PROCESS-MAP.html` | 99.9 KB | "La Methode Palantir -- Process Map" | Final deliverable |
| `PALANTIR-MEGA-OVERVIEW-EXTRACTED.md` | 29.9 KB / 894 lines | Extracted text from visual atlas -- quick reference diagrams | Intermediate |
| `SYNTHESE-GLOBALE-PHASE2.md` | 95.9 KB / 1,583 lines | Deduplicated fusion of all 5 syntheses (GPT+Claude+Perplexity+agents), written in French, dated 18 Feb 2026 | Final deliverable (French) |
| `SYNTHESIS-comprehensive-research.md` | 40.7 KB / 542 lines | English synthesis from 18 research files, covers GTM through SMB replication | Final deliverable (English) |
| `synthese-5-claude-agent-research.md` | 124.2 KB | Synthesis of 8 Claude agent research files (FDE methodology, Workshop UI, Foundry, Ontology, patents, demos, SMB deployment) | High quality source synthesis |
| `extracted-parts-abcd.md` | 107.3 KB | Text extraction from parts A, B, C, D of the 05 playbook | Intermediate -- text version of 05 parts |
| `extracted-playbook-05.md` | 79.0 KB | Full extraction of 05-palantir-complete-playbook.html content | Intermediate -- redundant with source |

**Critical redundancy finding in 06:**
- `PALANTIR-MEGA-OVERVIEW.html` (199.7 KB) and `PALANTIR-VISUAL-ATLAS.html` (199.7 KB) are byte-for-byte identical (same size, same title in HTML).
- `extracted-parts-abcd.md` and `extracted-playbook-05.md` are text extractions of files that already exist as HTML -- pure redundancy.
- `PALANTIR-FULL-RECAP.md` and `PLAYBOOK-DEFINITIF-PALANTIR.md` are both ~330KB comprehensive syntheses covering overlapping territory. They complement rather than duplicate each other: FULL-RECAP covers all 7 parts (Architecture + Delivery + Commercial + Market + GTM + Errata + Atlas), PLAYBOOK-DEFINITIF covers the operational method in greater depth (bootcamp day-by-day, pilot week-by-week).
- The 7 html-part*.html fragment files are intermediate production artifacts, not final deliverables.

---

## FOLDER 07 -- Spider Inputs (everything created 19 Feb 2026)

### Raw inputs (27 files)

| File | Size | Content | Classification |
|------|------|---------|----------------|
| `raw/these.md` | 23.4 KB | Nathan's original thesis text (raw, unprocessed) | Source |
| `raw/prompt.md` | 6.9 KB | Prompt used to kick off the 07 session | Meta |
| `raw/evolution_proposition_deal_nathan.md` | 6.3 KB | Cap table evolution document | Source |
| `raw/appel_jean_nathan.md` | 50.8 KB | Full transcript of Jean-Nathan call (17 Feb 2026) | Source -- critical |
| `raw/reflexion_decotec.md` | 32.2 KB | Detailed Decotec case analysis | Source |
| `raw/contenu_nathan/note-interne-drakkar.md` | 28.3 KB | Nathan's internal note to Drakkar team on AI | Source |
| `raw/contenu_nathan/post_linkedin_nathan.md` | 3.0 KB | Nathan's LinkedIn post on AI phases | Source |
| `raw/jean/26_01_14 - mail.md` | ? | Jean's January 14 email | Source |
| `raw/jean/26_01_28 - mai.md` | ? | Jean's January 28 email | Source |
| `raw/jean/28_02_18 - mail.md` | ? | Jean's February 18 email | Source |
| `raw/tech/spider_archi_globale.md` | 13.2 KB | Spider global architecture | Source |
| `raw/tech/spider_stack_back_front_cible.md` | 32.7 KB | Detailed front/back target stack | Source |
| `raw/bmad_spideros/prd-spideros-2026-01-18.md` | 54.4 KB | Full PRD January 2026 | Source |
| `raw/bmad_spideros/product-brief.md` | 45.5 KB | Product brief | Source |
| `raw/bmad_spideros/ux-design-spideros.md` | 93.6 KB | UX design spec (very detailed, 58 screens) | Source |
| `raw/bmad_spideros/brainstorming/` | 6 files, ~120 KB | Per-module brainstorming (People, Memory, Builder, Chatbot, Content, Documents) | Source |
| `raw/bmad_spideros/research/` | 6 files, ~110 KB | Per-module research (same topics) | Source |
| `raw/cas_jordan/` | Multiple files | Jordan/ComPrivee case: Notion export, invoices PDF, Excel plan, presentation PDF | Source -- critical |
| `raw/cas_twoghether/` | Multiple files | Twoghether case: 4 RDV notes, loss analysis | Source |

### Cleaned inputs (9 files, ~220 KB)

These are the processed/structured versions of the raw inputs above, with context headers:

| File | Size | Content | Classification |
|------|------|---------|----------------|
| `cleaned/01-these-nathan.md` | 26.4 KB | Nathan's thesis -- cleaned and annotated with context header | Final input |
| `cleaned/02-deal-structure.md` | 10.6 KB | Cap table evolution -- structured | Final input |
| `cleaned/03-cas-decotec.md` | 36.1 KB | Decotec case -- cleaned | Final input |
| `cleaned/04-cas-jordan.md` | 38.4 KB | Jordan/ComPrivee case -- cleaned | Final input |
| `cleaned/05-cas-twoghether.md` | 22.0 KB | Twoghether case -- cleaned | Final input |
| `cleaned/06-jean-contexte.md` | 24.7 KB | Jean's context and emails -- structured | Final input |
| `cleaned/07-tech-architecture.md` | 23.0 KB | Tech architecture -- cleaned | Final input |
| `cleaned/08-bmad-product-vision.md` | 17.2 KB | BMAD product vision summary | Final input |
| `cleaned/09-contexte-ia-drakkar.md` | 15.4 KB | AI context + Drakkar positioning note | Final input |

### Top-level synthesis files in 07 (6 files, ~380 KB)

| File | Size | Content | Classification |
|------|------|---------|----------------|
| `SPIDER-MEGA-RECAP.md` | 56.3 KB | Complete internal Spider document: 10 theses, team, cases (Jordan, Decotec, Twoghether), product, market, unknowns, roadmap, directory. Dated 19 Feb. | CROWN JEWEL -- Spider's internal bible |
| `SPIDER-FINAL.md` | 51.4 KB | "The document you give a Thiel or Graham to understand EVERYTHING." Similar structure to MEGA-RECAP but framed as an investor-grade thesis document. More narrative. | CROWN JEWEL -- investor-grade version |
| `SPIDER-FINAL.html` | 112.8 KB | HTML version of SPIDER-FINAL.md with beautiful styling. 18 sections. | Final deliverable |
| `SPIDER-GLOBAL.html` | 79.8 KB | Combined HTML: SPIDER-FINAL + Palantir blueprint section + competitive mapping. "SpiderOS -- Global Strategy." 28 sections. | CROWN JEWEL -- most complete HTML for Spider |
| `SPIDER-PALANTIR-BLUEPRINT.md` | 49.8 KB | "Spider in Palantir mode for SMEs." Detailed translation of Palantir's 4-time machine into Spider equivalents: Bootcamp -> Spider Demo Day, FDE -> Forward Deployed Consultant, Ontology -> Spider Intelligence Engine. With action plan for first 12 weeks. | Final deliverable -- operational blueprint |
| `SPIDER-POSITIONING-2026.md` | 46.8 KB | Competitive cartography 2026 + roadmap 2026-2028. Maps 7 competitor categories (orchestrators, ERP, workflow automation, AI employees, etc.). Identifies Spider's unique void. Fully updated with OpenAI Frontier (launched 5 Feb 2026). | Final deliverable -- strategy document |
| `SPIDER-QUESTIONS-REFLEXIONS.md` | 23.9 KB | Strategic questions v2 with Nathan's answers. Resolved issues (Jean alignment, BMAD, "zero effort" misconception, tech stack) + open questions (pricing, timing, who sells). | Final deliverable -- decision log |
| `answers.md` | 8.4 KB | Nathan's raw answers to the v1 questions (before they were structured into QUESTIONS-REFLEXIONS.md) | Intermediate -- superseded by above |

**Overlap within 07:**
- `SPIDER-MEGA-RECAP.md` and `SPIDER-FINAL.md` overlap heavily (both cover the 10 theses, cases, team, product). FINAL.md is more narrative/investor-grade. MEGA-RECAP is more operational/internal. They are complementary, not identical.
- `SPIDER-FINAL.html` is the HTML render of `SPIDER-FINAL.md`.
- `SPIDER-GLOBAL.html` is a superset of `SPIDER-FINAL.html` -- it includes the Palantir blueprint sections plus competitive map. **SPIDER-GLOBAL.html is the most complete Spider HTML artifact.** SPIDER-FINAL.html is partially redundant with it.
- `answers.md` is a raw scratch file, superseded by `SPIDER-QUESTIONS-REFLEXIONS.md`.

---

## COMPLETE REDUNDANCY MAP

The following files are direct duplicates or strict subsets:

| Redundant file | Superseded by | Reason |
|----------------|---------------|--------|
| `06/PALANTIR-VISUAL-ATLAS.html` (199.7 KB) | `06/PALANTIR-MEGA-OVERVIEW.html` | IDENTICAL -- same byte size, same HTML title |
| `06/extracted-parts-abcd.md` (107 KB) | `05/05-palantir-complete-playbook.html` | Text extraction of the HTML -- no new information |
| `06/extracted-playbook-05.md` (79 KB) | `05/05-palantir-complete-playbook.html` | Same content, different extraction |
| `05/part-a-architecture.html` (102 KB) | `05/05-palantir-complete-playbook.html` | Assembly fragment, fully incorporated |
| `05/part-b-consulting.html` (70 KB) | `05/05-palantir-complete-playbook.html` | Assembly fragment |
| `05/part-c-commercial.html` (79 KB) | `05/05-palantir-complete-playbook.html` | Assembly fragment |
| `05/part-d-errata.html` (55 KB) | `05/05-palantir-complete-playbook.html` | Assembly fragment |
| `05/shell-template.html` (24 KB) | -- | CSS template only, no content |
| `07/answers.md` (8 KB) | `07/SPIDER-QUESTIONS-REFLEXIONS.md` | Raw version of structured Q&A |
| `07/SPIDER-FINAL.html` (113 KB) | `07/SPIDER-GLOBAL.html` | GLOBAL is a superset (28 sections vs 18) |

---

## THE TRUE CROWN JEWELS (what feeds the mega livrable)

**On Palantir (the "how they did it" knowledge base):**

1. `/05-final-synthesis/05-palantir-complete-playbook.html` -- 332 KB -- The definitive Palantir playbook (architecture, consulting, commercial, errata)
2. `/06-deep-research-phase2/PLAYBOOK-DEFINITIF-PALANTIR.md` -- 334 KB -- Operational methodology in markdown (bootcamp day-by-day, pilot week-by-week)
3. `/06-deep-research-phase2/PLAYBOOK-DEFINITIF-PALANTIR.html` -- 619 KB -- HTML render of above
4. `/06-deep-research-phase2/PALANTIR-FULL-RECAP.md` -- 234 KB -- 7-part knowledge base (most comprehensive MD)
5. `/06-deep-research-phase2/PALANTIR-MEGA-PLAYBOOK.html` -- 487 KB -- HTML mega document
6. `/palantir-apollo-research.md` -- 31 KB -- Apollo platform (unique, not covered elsewhere)

**On Spider (the "what we're building" documents):**

7. `/07-spider-inputs/SPIDER-MEGA-RECAP.md` -- 56 KB -- Spider internal bible
8. `/07-spider-inputs/SPIDER-FINAL.md` -- 51 KB -- Investor-grade thesis document
9. `/07-spider-inputs/SPIDER-GLOBAL.html` -- 80 KB -- Complete HTML (thesis + blueprint + competitive map)
10. `/07-spider-inputs/SPIDER-PALANTIR-BLUEPRINT.md` -- 50 KB -- How to run Spider like Palantir (operational)
11. `/07-spider-inputs/SPIDER-POSITIONING-2026.md` -- 47 KB -- Competitive cartography + 2026-2028 roadmap
12. `/07-spider-inputs/SPIDER-QUESTIONS-REFLEXIONS.md` -- 24 KB -- Strategic decisions log with Nathan's answers

**Spider source inputs (for the mega livrable's context sections):**

13. `/07-spider-inputs/cleaned/01-these-nathan.md` -- Nathan's thesis (cleaned)
14. `/07-spider-inputs/cleaned/03-cas-decotec.md` -- Decotec case
15. `/07-spider-inputs/cleaned/04-cas-jordan.md` -- Jordan/ComPrivee case (38 KB)
16. `/07-spider-inputs/cleaned/05-cas-twoghether.md` -- Twoghether case
17. `/07-spider-inputs/cleaned/06-jean-contexte.md` -- Jean's context and alignment

---

## WHAT IS MISSING (gaps for the mega livrable)

1. **The INDEX.md is not updated for 07-spider-inputs** -- none of the 07 files are listed. It also shows 4 Phase 6 research files as "TODO" even though they arrived and were processed.

2. **No merged Spider + Palantir synthesis document** -- SPIDER-PALANTIR-BLUEPRINT.md does this partially but there is no single document that says "here is the Spider playbook, week by week, based on everything we know about Palantir AND our specific cases (Jordan, Decotec, Twoghether)." The mega livrable is this document.

3. **No financial model** -- There is stress-test data (challenge-roi-envelope.html, FDE economics), competitor pricing (Vanta $833-$6,667/month), and Palantir margin data (84% gross). But there is no Spider-specific financial model with scenarios.

4. **No go-to-market execution doc for Spider** -- SPIDER-PALANTIR-BLUEPRINT.md has the first 12 weeks, but it's high-level. There is no "what does Nathan do on Monday morning" operational doc.

5. **No Jean-facing document** -- Multiple docs acknowledge Jean needs a document to explain the strategy. That document does not exist yet.

6. **Pricing model** -- Nathan explicitly said "we know nothing" on pricing. No synthesis document attempts to resolve this (though the raw material exists in the FDE economics research).

7. **The BMAD product specs are partially obsolete** -- raw/bmad_spideros/ documents (PRD, product-brief, UX) are pre-Service-as-Software pivot. No updated product spec exists that reconciles BMAD specs with the new model.

---

## SUMMARY TABLE

| Folder | Files | Total size | Status | Keep for mega livrable? |
|--------|-------|-----------|--------|------------------------|
| Root | 2 | 44 KB | INDEX outdated; apollo research = unique | apollo yes, INDEX needs update |
| 01 | 14 | ~466 KB | Historical archive, all superseded | No |
| 02 | 3 | ~237 KB | Intermediate, superseded | challenge-roi-envelope.html maybe |
| 03 | 12 | ~395 KB | High quality source material | Key figures only |
| 04 | 5 | ~117 KB | Deep research, partially absorbed | FDE economics yes |
| 05 | 7 | ~740 KB | 2 crown jewels + 5 assembly artifacts | Yes (05 + 06 HTML only) |
| 06 | 41 | ~3.8 MB | Complex mix -- 5 crown jewels, 1 exact duplicate, multiple intermediates | PLAYBOOK-DEFINITIF + FULL-RECAP + SYNTHESE-GLOBALE |
| 07 | ~55 | ~1.1 MB | All recent, highest quality for Spider | YES -- all 6 synthesis files + 9 cleaned inputs |
