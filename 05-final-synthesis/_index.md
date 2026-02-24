# 05-final-synthesis — Index

> Deux documents HTML de synthèse finale constituant le résultat consolidé du reverse engineering complet de Palantir : un playbook exhaustif et un blueprint de réplication, tous deux sous forme de pages web interactives.

---

## `05-palantir-complete-playbook.html`
**Rôle :** Playbook exhaustif du reverse engineering Palantir, présenté comme une application web interactive avec sidebar de navigation, dark theme GitHub-style, sections collapsibles et badges de confiance sur les données.
**Findings clés :**
- Couvre l'intégralité de la méthode Palantir de l'avant-vente (bootcamp) au support long-terme (scale phase), organisée en sections navigables.
- Interface conçue comme un outil de référence opérationnel : sticky sidebar, scroll-spy, confidence badges (confirmed / estimated / speculative) sur chaque assertion.
- Chaque section repose sur la fusion de sources primaires (ex-FDEs, SEC filings, documentation officielle, AIPCon transcripts) avec annotation de la source par fact.

---

## `06-palantir-replication-blueprint.html`
**Rôle :** Blueprint de réplication de Palantir pour un builder — "How to Replicate Palantir" — présentant les composants architecturaux, les décisions techniques et les prérequis non-négociables pour reproduire le modèle.
**Findings clés :**
- Identifie les 6 conditions nécessaires à la réplication du modèle FDE : plateforme produit (pas des services purs), tolérance à la marge négative à l'acquisition, ingénieurs top-1%, clients enterprise capables de payer premium, tolérance organisationnelle au chaos, et primauté des compétences sociales sur les compétences techniques.
- Structure le blueprint en sections numérotées avec cards, diagrammes SVG et métriques chiffrées (KPIs FY2025 : $4.475B revenue, 139% NDR, 56x expansion multiple, 84% gross margin).
- Met en évidence le fossé architectural moat : l'Ontologie comme couche de métadonnées partagée entre les 4 plateformes (Gotham, Foundry, AIP, Apollo), rendant la réplication partielle presque sans valeur.

---
