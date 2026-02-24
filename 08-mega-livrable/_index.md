# 08-mega-livrable — Index

> Livrable stratégique final Spider — proposition argumentée (pas une compilation) structurée en 7 sections, soutenue par 8 recherches primaires, un audit de qualité interne, et des fragments de sections pour navigation rapide.

---

## Fichiers racine

---

## `CADRAGE-MEGA-LIVRABLE.md`
**Rôle :** Document de mandat du mega livrable — définit la posture, le périmètre et l'état des recherches.
**Findings clés :**
- Posture : proposition stratégique argumentée, pas une compilation de documents existants.
- Tableau de statut des recherches R1-R8 avec phases restantes à compléter (phases 3-5).
- Définit les règles éditoriales : chaque claim doit être tagué [PROVEN], [PLAUSIBLE], [SPECULATIVE] ou [UNKNOWN].

---

## `SPIDER-MEGA-LIVRABLE.md`
**Rôle :** Le livrable stratégique principal — 3023 lignes, 7 sections couvrant monde/Palantir/Spider/challenge/marché/plan/annexes.
**Findings clés :**
- Section 0-3 : contexte mondial (Carlota Perez, fin de la phase de frénésie IA fév 2026), 5 leçons Palantir + ce que Spider ne prend PAS, thèse Spider 10 thèses + 3 cas + équipe + deal.
- Section 4-5 : challenge (5 Pourquoi sur T1/T4/T7/T8, analyse 7 Powers de Hamilton Helmer, counter-positioning) + marché (TAM/SAM/SOM, trajectoires concurrentes, fenêtre 18 mois).
- Section 6-7 : plan complet (business model 490 EUR/mois + 1990 EUR setup, ICP 5-50 salariés 500K-10M EUR CA CEO-solo, GTM expert-comptable first) + tableau de décision Palantir vs Spider + annexes (glossaire, questions ouvertes pour Nathan).

---

## `SPIDER-MEGA-LIVRABLE.html`
**Rôle :** Rendu HTML du livrable principal — export pour partage et présentation.
**Findings clés :**
- Export HTML de SPIDER-MEGA-LIVRABLE.md, identique en contenu.
- Non résumable séparément — se référer au .md pour le contenu.

---

## audit/

---

## `audit/AUDIT-INVENTAIRE.md`
**Rôle :** Audit complet des 133 fichiers du corpus stratégique Spider — cartographie de la dette documentaire.
**Findings clés :**
- 133 fichiers inventoriés sur 8 dossiers. Joyaux identifiés : 7 Palantir + 6 Spider (dont SPIDER-FINAL, Blueprint, R3, R5).
- Carte de redondance : 10 fichiers doublons/subsets détectés (SPIDER-GLOBAL ≈ SPIDER-FINAL, answers.md ⊂ QUESTIONS-REFLEXIONS, sections/ ⊂ MEGA-LIVRABLE).
- Lacunes identifiées : pas de modèle financier, pas de doc GTM exécution, _index.md de 07 obsolète.

---

## `audit/AUDIT-QUALITE.md`
**Rôle :** Audit de qualité interne brutal des docs Spider vs standard Thiel/Graham/YC.
**Findings clés :**
- SPIDER-FINAL : points forts (thèses solides, cas Jordan quantifié, kill criteria) + points faibles (7 Powers absent, GTM peu précis, Decotec mal utilisé comme "proof").
- SPIDER-PALANTIR-BLUEPRINT : point fort (mapping concret) + faibles (FDE salaire irréaliste, overengineering ontologique).
- SPIDER-POSITIONING : cartographie honnête + faible sur les trajectoires 18 mois des concurrents (corrigé dans R2).

---

## research/

---

## `research/R1-past-failures.md`
**Rôle :** Analyse des tentatives passées dans "IA pour opérations PME" — qui a essayé et pourquoi ça a échoué.
**Findings clés :**
- Échecs documentés : Domo, Looker, Sisense, ThoughtSpot (trop complexes pour PME), tentative SMB de Palantir (abandonnée), vague knowledge management (Jive, Confluence, Guru), IBM Watson, startups françaises IA-pour-PME.
- 5 leçons cross-coupantes : adoption requiert onboarding humain, PME ne paie pas pour "insights" abstraits, échec = surestimation de la sophistication utilisateur.
- Spider évite ces erreurs via le Service-as-Software (l'IA fait le travail, pas le client).

---

## `research/R2-competitor-trajectories.md`
**Rôle :** Trajectoires sur 18 mois des 8 concurrents clés — niveaux de collision risk pour Spider.
**Findings clés :**
- Dust.tt : recrute des FDEs, expansion US, collision LOW-MEDIUM (positionnement similaire mais marché différent).
- Odoo 19/20 : HIGH threat mais gérable (partenaire potentiel + concurrent vertical).
- Pennylane (175M EUR levés) et Qonto : LOW risk + opportunité de partenariat comptable.
- 11x.ai et Artisan : scandales et churn — NEGLIGIBLE. Lindy : US-focused, LOW. Zapier : intégration MCP, MEDIUM.

---

## `research/R3-french-pme-buying.md`
**Rôle :** Comportement d'achat des PME françaises pour SaaS B2B — cycles, décideurs, canaux, objections.
**Findings clés :**
- Cycle de vente moyen 4.4 mois. CEO seul décide dans 95% des cas pour entreprises 10-30 salariés si <500 EUR/mois.
- Canaux de découverte : réseau professionnel 39%, expert-comptable 15% (croissance la plus rapide +5 pts en 2 ans).
- 7 objections communes documentées avec taux de conversion post-objection par canal. Benchmark : Pennylane, Qonto, PayFit, Alan, Silae.

---

## `research/R4-comparable-gtm.md`
**Rôle :** Stratégies GTM de 6 acteurs comparables — patterns répétables extraits.
**Findings clés :**
- Gusto : cold calls, 20% conversion, wedge Californie uniquement au départ. Rippling : stealth 2 ans, 200% NDR.
- Pennylane : accountant-first, 6 000 cabinets × 133 clients chacun = distribution massive sans marketing direct.
- 6 patterns GTM récurrents : wedge géographique, canal intermédiaire (comptable/avocat), under-promise/over-deliver, land-and-expand.

---

## `research/R5-unit-economics.md`
**Rôle :** Benchmarks économiques unitaires — CAC, LTV, churn, marges brutes par modèle.
**Findings clés :**
- CAC par canal : cold outbound 3-5K EUR, référence réseau 500-1500 EUR, inbound 1-2K EUR.
- Churn SMB : 3-7%/mois. NDR SMB sain : 90-97%. Ratio LTV:CAC cible : >3x à 18 mois.
- Marges : SaaS pur 75-85%, modèle hybride 65-75%. Évolution Palantir : 68%→82% sur 6 ans (preuve que le modèle hybride converge vers SaaS margins).

---

## `research/R6-market-strategy-take.md`
**Rôle :** Prise de position stratégique sur l'évolution du marché B2B SaaS/ERP.
**Findings clés :**
- "SaaSpocalypse" : 2T USD effacés des valorisations SaaS depuis 2021. 3 mouvements simultanés : foundation models qui descendent, shift du pricing, ERP devenant backend.
- 95% des agents IA en production échouent en moins de 6 mois — paradoxe de concentration qui aide Spider.
- Endgame M&A plateforme analysé : Spider comme cible d'acquisition potentielle (Odoo, Pennylane, Salesforce) si PMF prouvé.

---

## `research/R7-exhaustive-competitor-map.md`
**Rôle :** Cartographie exhaustive de 150+ acteurs sur 12 catégories — top 20 les plus pertinents pour Spider.
**Findings clés :**
- Dust.tt = seul concurrent direct français avec positionnement AI agents explicite.
- Odoo = PARTENAIRE/ADJACENT avec HIGH threat (concurrent si Odoo descend vers SMB IA).
- Pennylane = ADJACENT avec HIGH threat + opportunité de partenariat canal comptable.
- 12 catégories couvrent : AI agents, BI/analytics, ERP, CRM, automatisation, knowledge management, process mining, etc.

---

## `research/R7b-missing-competitors.md`
**Rôle :** Complétion de la cartographie — acteurs manquants dans R7, focus mémoire organisationnelle.
**Findings clés :**
- Screenpipe (mémoire personnelle via capture écran) : ADJACENT, pas une menace directe.
- Rewind/Limitless : acquis par Meta — mort comme produit indépendant, NEGLIGIBLE.
- Microsoft Recall : outil individuel, LOW relevance pour Spider B2B.
- Granola.ai (notes de réunions) : source de données potentielle, pas un concurrent. Outils infra (Nango, Airbyte, LangGraph, Temporal) : écosystème complémentaire.

---

## `research/R8-global-ai-take.md`
**Rôle :** État de l'IA en février 2026 — capacités réelles, limites réelles, et 5 impératifs stratégiques pour Spider.
**Findings clés :**
- Modèles : 80.9% SWE-bench (Claude), 100% AIME (GPT-5.2). Mais : 50% de succès seulement sur tâches >2h, <20% sur usage général ordinateur.
- Cadre Carlota Perez appliqué : fin de la phase de frénésie (fév 2026) = début de la phase de déploiement. Fenêtre de 18-24 mois pour les builders.
- 5 impératifs stratégiques pour Spider : spécialisation verticale, durée de vie du contexte, fiabilité >exactitude, supervision humaine, intégration données existantes.

---

## sections/

---

## `sections/S0-S3-monde-palantir-spider.md`
**Rôle :** Fragment des sections 0-3 du mega livrable — contexte mondial, Palantir, thèse Spider.
**Findings clés :**
- Contenu identique au début de SPIDER-MEGA-LIVRABLE.md (sections 0, 1, 2, 3).
- Fichier de navigation rapide — existe pour accès isolé aux premières sections sans ouvrir les 3023 lignes.
- Ne pas traiter comme source séparée : tout le contenu est dans SPIDER-MEGA-LIVRABLE.md.

---

## `sections/S4-S5-challenge-marche.md`
**Rôle :** Fragment des sections 4-5 — analyse du challenge et du marché.
**Findings clés :**
- Section 4 : 5 Pourquoi sur T1 (savoir tacite non capturé), T4 (PME paye mal), T7 (switching costs élevés), T8 (fenêtre courte).
- Verdict challenge : GTM doit cibler les PME en CRISE (Decotec, Jordan en croissance rapide) — pas les PME confortables.
- Fichier de navigation rapide — source dans SPIDER-MEGA-LIVRABLE.md.

---

## `sections/S6-S7-plan-cross.md`
**Rôle :** Fragment des sections 6-7 — plan business model, ICP, GTM et kill criteria.
**Findings clés :**
- Business model : 490 EUR/mois entry (vs 500 EUR pour rester sous le seuil décision CEO-solo), 1990 EUR setup fee.
- ICP : 5-50 salariés, 500K-10M EUR CA, CEO seul, déjà utilisateur Sheets+Notion ou Odoo+Pennylane.
- Architecture revenus 4 couches : setup fee → abonnement mensuel → upsell verticaux → Mycelium (données cross-clients). Fichier de navigation rapide — source dans SPIDER-MEGA-LIVRABLE.md.

---
