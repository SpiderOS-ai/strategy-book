# 06-deep-research-phase2 — Index

> Phase 2 du reverse engineering Palantir : 35 fichiers issus de recherches croisées (GPT-4o, Claude, Perplexity Pro Deep Research), organisés en prompts source, résultats bruts par modèle, synthèses fusionnées, playbooks opérationnels et documents HTML de visualisation.

---

## `00-prompts-deep-research-phase2.md`
**Rôle :** Les 4 prompts de deep research envoyés aux LLMs pour générer tous les documents de cette phase.
**Findings clés :**
- Prompt 1 : reverse engineering du bootcamp AIP jour par jour (avant-vente, 5 jours, post-bootcamp).
- Prompt 2 : déploiement pilote 90 jours artefact par artefact (discovery, ontologie, actions, formation, handoff).
- Prompt 3 : playbook expand & scale — comment Palantir rend le client captif puis autonome.
- Prompt 4 : fonctionnement concret de Foundry (Workshop, Pipeline Builder, Ontology Manager, AIP Logic, OSDK, Apollo).

---

## `01-palantir-fde-methodology-deep-dive.md`
**Rôle :** Analyse opérationnelle exhaustive du rôle FDE (Forward Deployed Engineer) chez Palantir, basée sur des témoignages de première main.
**Findings clés :**
- Le modèle Delta/Echo (FDSE + Deployment Strategist) opère sous doctrine Auftragstaktik : autonomie totale des équipes terrain avec objectifs de haut niveau seulement.
- L'accès aux données est le vrai bottleneck des pilots : 8-12 semaines de "guerre politique" pour obtenir l'accès, puis 1 semaine de construction en urgence.
- Palantir est la "founder factory" la plus prolifique de Silicon Valley : plus d'ex-Palantir que d'ex-Googlers par batch YC, malgré 50x moins d'employés.

---

## `01-palantir-workshop-ui-deep-dive.md`
**Rôle :** Deep dive UI-level sur Workshop (le builder d'applications low-code de Foundry) : widgets, data binding, actions, et comparaison avec les outils alternatifs.
**Findings clés :**
- Workshop dispose de 50+ widgets (Table, Chart, Map, Form, Button, Timeline, KPI Card…) liés directement aux Object Types de l'Ontologie via un système de variables.
- La décision Workshop vs Slate vs Quiver vs Contour suit une matrice claire : Workshop pour les workflows opérationnels, Quiver pour les KPI dashboards, Contour pour l'exploration ad hoc, Slate pour le HTML/JS custom.
- AIP Assist génère ~80% de la structure d'une application Workshop à partir d'une description en langage naturel.

---

## `12-research-foundry-pipelines-osdk.md`
**Rôle :** Documentation technique détaillée de Pipeline Builder, Code Repositories (@transform API), Data Lineage, scheduling, connecteurs (400+), OSDK TypeScript/Python, et infrastructure Rubix/Kubernetes.
**Findings clés :**
- Pipeline Builder propose 70+ types de nœuds visuels et 500+ fonctions built-in, avec prévisualisation à chaque nœud sans rebuild complet.
- L'OSDK est un client type-safe auto-généré depuis le schéma de l'Ontologie : `client(MyObjectType).where({...}).fetchPage()` en TypeScript, avec support des filtres, agrégations, links et actions.
- Rubix (K8s propriétaire) recycle chaque nœud en 48h maximum pour raison de sécurité, avec gang scheduling Spark garantissant qu'un driver n'est schedulé que si tous ses executors ont des ressources disponibles.

---

## `13-research-consulting-vs-palantir-methodology.md`
**Rôle :** Comparaison structurée entre la méthodologie MBB (McKinsey/BCG/Bain) et le modèle FDE Palantir, chapitre par chapitre.
**Findings clés :**
- Palantir a remplacé chaque artefact consulting par son équivalent exécutable : l'issue tree devient l'ontologie, la war room devient le Workshop dashboard, le deck de recommandations devient l'application en production.
- Le bootcamp (1-5 jours, gratuit, produit un prototype fonctionnel) contre le rapid diagnostic McKinsey (2-6 semaines, $250K-$1M, produit un PowerPoint) — facteur de compression 5-10x.
- Le modèle "consulting avec un compilateur" : mêmes éléments de valeur (client intimacy, structured problem solving, stakeholder management) mais sans le handoff gap ni les économies linéaires headcount.

---

## `14-research-smb-data-platform-deployment.md`
**Rôle :** Analyse du déploiement de plateformes data chez les PME européennes (5-100M EUR, 50-200 employés) — le segment cible de Spider — avec benchmarks Odoo, HubSpot, Salesforce et SaaS vertical.
**Findings clés :**
- 70-90% des PME utilisent Excel comme seul outil analytique (proxy Gartner : 87% des organisations ont une maturité BI "bas niveau", soit spreadsheet-based).
- Implémentation Odoo pour 50 utilisateurs : ~$80-130K an 1 ; les PME françaises ont un taux d'adoption cloud de 22.9% vs 38.9% moyenne EU — headwind structurel.
- Le CFO est le champion primaire des outils data en PME ; le modèle d'onboarding optimal est hybride (white-glove initial + self-serve ongoing) pour un ACV cible de 20-80K EUR.

---

## `15-research-ontology-design-patterns.md`
**Rôle :** Analyse des patterns de design ontologique chez Palantir et dans les standards industriels, pour informer la stratégie d'ontologies verticales templatisées de Spider.
**Findings clés :**
- Les 6 primitives de l'Ontologie Palantir (Object Types, Properties, Link Types, Action Types, Interfaces, Functions) correspondent directement aux concepts de base de données relationnelle (table, colonne, jointure) mais avec une couche sémantique opérationnelle.
- La règle de décision Object vs Property : une entité mérite son propre Object Type si elle a plusieurs propriétés propres, des relations avec d'autres entités, ou des actions qui lui sont attachées ; sinon c'est une Property.
- Les patterns industriels (OWL, FIBO pour la finance, HL7 FHIR pour la santé) révèlent que les ontologies verticales well-designed réduisent le temps de déploiement de 60-70% par rapport à partir de zéro.

---

## `16-research-palantir-patents-implementation-details.md`
**Rôle :** Analyse de 3 438+ brevets Palantir (95% grant rate), extrayant les détails d'implémentation non disponibles dans la documentation publique.
**Findings clés :**
- Les objets Ontologie sont des "materialized views over tabular data" (patent US20200293561A1) : l'Ontologie ne stocke pas de données, elle mappe vers des datasets existants via des métadonnées.
- Apollo (patent US10263845B2) utilise un modèle pull constraint-based : les nœuds tirent les mises à jour qui correspondent à leurs contraintes, pas de push central — 360 000+ déploiements/mois, rollback moyen en 4.9 minutes.
- Le patent EP4443310A1 décrit l'architecture 3 couches d'AIP : Orchestrator Selector → Service Orchestrators → Data Processing Services, avec les LLMs recevant des objets typés, jamais de données brutes.

---

## `PALANTIR-FULL-RECAP.md`
**Rôle :** Knowledge base complète compilée depuis 50+ documents de recherche en 6 phases — la source de vérité consolidée couvrant produit, delivery, commercial et marché avec métriques FY2025.
**Findings clés :**
- Métriques FY2025 clés : $4.475B revenue (+56% YoY), 139% NDR Q4 2025, 954 clients (+34% YoY), multiple d'expansion 56x, 84% gross margin, $1.01M revenue/employee, 1 300+ bootcamps conduits.
- Stack 4 plateformes : Gotham (2008, renseignement, EAV/CR), Foundry (2016, enterprise data OS), AIP (2023, couche IA), Apollo (CD continu) — toutes partageant l'Ontologie comme abstraction commune.
- Prix G-Cloud UK : Level 0 = £250K (pilote), Level 4 = £5M (enterprise-wide), Level 5 = £10M (digital twin) ; services pro à £317K/personne/an ; support à £21.5K/core.

---

## `PALANTIR-MEGA-OVERVIEW.html`
**Rôle :** Visual Atlas interactif du playbook complet Palantir — 30+ diagrammes SVG couvrant architecture produit, delivery, commercial et marché.
**Findings clés :**
- Présente la "big picture" en 3 colonnes BUILD / DELIVER / SELL avec boucles de feedback entre les trois systèmes.
- Visualise le cycle de vie client Acquire → Expand → Scale avec courbes de cohorte, marges par phase et trajectory ACV.
- Affiche les métriques FY2025 en hero section : $4.475B, 139% NDR, 56x expansion multiple, 84% gross margin.

---

## `PALANTIR-MEGA-PLAYBOOK.html`
**Rôle :** Document HTML mega (619 KB) rassemblant l'intégralité du playbook en 4 parties : produit, delivery, commercial, marché — avec navigation sticky et 30+ diagrammes SVG.
**Findings clés :**
- Partie 1 (Produit) : anatomie complète des 4 plateformes, des 6 primitives ontologiques, du data flow en boucle fermée 7 étapes, et de la sécurité multi-niveau.
- Partie 2 (Delivery) : playbook FDE de l'avant-vente au handoff CoE, avec artefacts produits à chaque étape et cadences de réunion.
- Partie 3 (Commercial) : structure de pricing, contrats multi-années, mécanismes de lock-in, réponse aux menaces de churn, et paysage concurrentiel.

---

## `PALANTIR-PROCESS-MAP.html`
**Rôle :** Carte de processus visuelle de la méthode Palantir — diagrammes SVG illustrant les flux de travail de chaque phase (bootcamp, pilot, expand, scale).
**Findings clés :**
- Cartographie le data flow de 7 étapes (Sources → Connection → Pipelines → Ontologie → AIP → Applications → Actions) avec les technologies clés à chaque nœud.
- Visualise les rôles et responsabilités au sein du pod FDE (AE + DS + FDSE) avec les interactions client à chaque étape.
- Présente le cycle Acquire/Expand/Scale avec les jalons de décision et les métriques de succès par phase.

---

## `PLAYBOOK-DEFINITIF-PALANTIR.html`
**Rôle :** Version HTML du playbook définitif (322 KB) — rendu visuel riche du document Markdown équivalent, avec mise en forme optimisée pour la lecture.
**Findings clés :**
- Même contenu que `PLAYBOOK-DEFINITIF-PALANTIR.md` mais avec typographie JetBrains Mono/DM Sans, navigation par ancres, et tables formatées pour lecture à l'écran.
- Couvre les 4 parties (avant-vente, pilot 90 jours, expand/scale, Foundry tools) avec ~5 000 lignes de contenu opérationnel.

---

## `PLAYBOOK-DEFINITIF-PALANTIR.md`
**Rôle :** Playbook définitif Markdown (322 KB) assemblé le 18 février 2026 depuis 20+ documents sources — la référence principale du corpus pour le reverse engineering opérationnel de Palantir.
**Findings clés :**
- Chaque fait est annoté par source (GPT), (Claude), (Perplexity) avec niveau de confiance [CONFIRMED], [ESTIMATED], [SPECULATIVE] et [CONTRADICTION] pour les divergences.
- Couvre le bootcamp AIP jour par jour (Day 1-5 avec agenda heure par heure), le pilot 90 jours phase par phase, et les mécanismes d'expansion avec backlogs de use cases formalisés.
- Contient les données de pricing les plus granulaires disponibles : coût FDE par $1M d'ARR ($700K en 2016, $80-150K estimé 2025), structure G-Cloud UK, et modèles contractuels gouvernementaux vs commercial.

---

## `SYNTHESE-GLOBALE-PHASE2.md`
**Rôle :** Synthèse globale dédupliquée de la Phase 2 — fusion de 5 synthèses issues de 20+ documents sources, écrite en français, avec toutes les métriques et contradictions inter-sources conservées.
**Findings clés :**
- Définitions officielles S-1 du cycle Acquire/Expand/Scale : Expand = revenu >$100K avec marge négative ; Scale = revenu >$100K avec marge positive — ce sont des états comptables, pas des paliers calendaires ou tarifaires.
- Courbe d'expansion par cohorte : 1x (an 1), 1.3-1.5x (an 2), 2-2.5x (an 3), 3.5-6x (an 5), 8-10x+ (an 7+) — base S-1 Palantir.
- NDR trimestriel tracé de Q3 2023 (107%) à Q4 2025 (139%), confirmant l'accélération structurelle du modèle d'expansion.

---

## `palantir-demos-transcripts-concrete-evidence.md`
**Rôle :** Transcriptions et analyses des événements AIPCon 1-3 (2023-2024), earnings calls, DevCon et demos clients — preuves concrètes du fonctionnement de la plateforme en production.
**Findings clés :**
- AIPCon 1 (juin 2023) : Shyam Sankar démontre "300 minutes → 3 minutes" sur un scénario supply chain avec AIP Terminal, et montre pour la première fois AIP Logic IDE avec chain-of-thought debugging.
- AIPCon 3 (juin 2024) : Tampa General Hospital annonce un deal de $50M sur 7 ans pendant l'événement ; Karp : "LLMs are like genies of the lamp. AIP is the lamp that controls them."
- SwissRE démo : "I haven't seen another application that can do that. Foundry is the only application that integrates all the processes and closes the loop."

---

## `playbook-part1-presales-bootcamp.md`
**Rôle :** Partie 1 du playbook définitif — avant-vente et AIP Bootcamp, avec sourcing pipeline, qualification ICP, scoping call, staffing bootcamp et déroulé jour par jour.
**Findings clés :**
- Volume bootcamps : ~50 (mi-2023) → 560+ organisations (fin Q4 2023) → 1 300+ (juin 2024) → ~5 bootcamps/jour en 2024 (Bloomberg confirmed).
- Le scoping call DS de 60-90 minutes est la porte critique avant tout bootcamp : si les données sont trop verrouillées ou les stakeholders non engagés, le bootcamp ne se fait pas.
- Coût pour Palantir estimé à $12-36K par bootcamp (personnel chargé) ; coût pour le client : gratuit.

---

## `playbook-part2-pilot-90days.md`
**Rôle :** Partie 2 — Pilot "Acquire" 90 jours : modèle économique, composition d'équipe, phases de déploiement semaine par semaine, artéfacts produits.
**Findings clés :**
- En 2019, Palantir perdait $65.4M de contribution sur les clients Acquire avec seulement $600K de revenus moyens par client — investissement R&D délibéré, pas erreur de gestion.
- 4 phases qui se chevauchent : Foundation/Discovery (S1-3), Ontology & Integration (S2-6), Application & Action Design (S4-10), Training & Handoff (S8-12).
- Coût FDE par $1M d'ARR : ~$700K en 2016, ~$280K en 2020, ~$80-150K estimé 2025 — la plateforme permet de réduire l'intensité humaine tout en augmentant la valeur.

---

## `playbook-part3-expand-scale.md`
**Rôle :** Partie 3 — Expand & Scale : mécanismes d'identification des opportunités d'expansion, formation du Center of Excellence, graduation FDE, et lock-in structurel.
**Findings clés :**
- 3 mécanismes d'expansion : proximité physique (FDE observent les adjacences), cartographie des parties prenantes (Impro framework de Keith Johnstone), et analytique d'usage plateforme (forte adoption = signal d'expansion).
- Le "Use Case Backlog" est un processus gouverné : revue mensuelle (roadmap), trimestrielle (SteerCo), avec portail de requêtes dans Foundry pour les nouvelles demandes.
- Coût de sortie estimé à $2.5-7.5M pour un client mûr : ontologie multi-départements, 100+ applications construites, politiques RBAC, CoE formé — la complexité accumulée est le vrai lock-in.

---

## `playbook-part4-foundry-tools.md`
**Rôle :** Partie 4 — Foundry en détail : architecture Rubix/Kubernetes, les 4 plateformes, data flow 7 étapes, ontologie 6 primitives, Workshop, Pipeline Builder, AIP, OSDK.
**Findings clés :**
- Le data flow Palantir ferme la boucle là où le BI traditionnel s'arrête : Sources → Pipelines → Ontologie → IA → Apps → **Actions → Sources** (writeback dans les systèmes source).
- Les 6 primitives ontologiques (Object Types, Properties, Link Types, Action Types, Interfaces, Functions) sont la seule couche d'abstraction — tout widget UI, tout outil agent IA, tout endpoint API opère sur ces 6 primitives.
- Workshop utilise un système de variables (Object Set Variables, String Variables, Boolean Variables…) pour lier les widgets entre eux sans code — cliquer une ligne dans Table A filtre Table B via une variable partagée.

---

## `results/gpt-presales-bootcamp-playbook.md`
**Rôle :** Résultat brut GPT-4o Deep Research sur le prompt pre-sales & bootcamp.
**Findings clés :**
- Reconstruit le playbook opérationnel depuis les sources publiques (SEC filings, UK service collateral, job descriptions) avec labels explicites (evidenced / best-fit inference).
- Confirme que les bootcamps sont gratuits et positionnés comme "evaluation-to-procurement bridge" plutôt que projet de discovery payant.

---

## `results/gpt-pilot-implementation-methodology.md`
**Rôle :** Résultat brut GPT-4o sur le prompt pilot 90 jours.
**Findings clés :**
- Reconstruit le système opérationnel implicite dans la documentation Foundry et les descriptions de rôles FDE/DS publiques.
- Met en avant le template de requirements fonctionnels Palantir : `[User Type] [Interface] [Decision] [Decision Inputs] [Action]` — approche decision-centric, pas feature-list.

---

## `results/gpt-expand-scale-captivity-playbook.md`
**Rôle :** Résultat brut GPT-4o sur le prompt expand & scale.
**Findings clés :**
- Cite directement les définitions S-1 d'Acquire/Expand/Scale avec les chiffres exacts de marge (55% Scale en 2019, 68% Scale H1 2020).
- Détaille le mécanisme de "graduation" FDE : retrait progressif conditionné à la démonstration de capacités par le client, pas un calendrier fixe.

---

## `results/gpt-foundry-tools-concrete-ux.md`
**Rôle :** Résultat brut GPT-4o sur le prompt Foundry tools.
**Findings clés :**
- Analyse l'Ontology Manager comme un "schema IDE git-branch-aware" avec staging/commit des changements avant déploiement en production.
- Décrit le workflow de création d'un Object Type : wizard guidé → nom → backing dataset → primary key → mapping colonnes → title key → save.

---

## `results/perplexity-bootcamp-playbook.md`
**Rôle :** Résultat brut Perplexity Pro Deep Research sur le prompt pre-sales & bootcamp.
**Findings clés :**
- Source la plus riche en citations directes d'executives (Karp, Sankar, Mabrey, Taylor) avec références tracées.
- Détaille la préparation pré-bootcamp en 4 workstreams parallèles : ingestion données, construction ontologie, identification use cases, logistique participants.

---

## `results/perplexity-pilot-methodology.md`
**Rôle :** Résultat brut Perplexity Pro Deep Research sur le prompt pilot 90 jours.
**Findings clés :**
- Confirme avec sources le témoignage Nabeel Qureshi : "s'installe à Toulouse pendant un an, travaille à l'usine 4 jours par semaine" — l'immersion physique totale est la norme, pas l'exception.
- Fournit les fourchettes ACV pilot ($100-500K) avec la médiane $250-350K post-bootcamp.

---

## `results/perplexity-expand-scale-playbook.md`
**Rôle :** Résultat brut Perplexity Pro Deep Research sur le prompt expand & scale.
**Findings clés :**
- Détaille les rôles du Center of Excellence (Platform Owner, Permissions Manager, Data Engineers, App Developers, Analysts) avec les tracks de formation associés.
- Source les données de switching cost estimé ($2.5-7.5M) avec décomposition par composante (ontologie, applications, RBAC, formation CoE).

---

## `results/perplexity-foundry-tools.md`
**Rôle :** Résultat brut Perplexity Pro Deep Research sur le prompt Foundry tools.
**Findings clés :**
- Décrit l'interface Ontology Manager avec ses vues distinctes (homepage table, object type view, property editor, link type view, action type view).
- Confirme les 400+ connecteurs Data Connection avec les 3 architectures (Foundry Worker, Agent Proxy, Agent Worker) et les spécificités du connecteur SAP Certified Add-On.

---

## `results/claude-bootcamp-playbook.md`
**Rôle :** Résultat brut Claude Deep Research sur le prompt pre-sales & bootcamp.
**Findings clés :**
- Reconstruction la plus détaillée du déroulé jour par jour avec agenda heure par heure pour chaque jour du bootcamp (Day 1 : problem framing, Day 2-3 : co-building, Day 4 : stress testing, Day 5 : executive demo).
- Détaille les artefacts produits à chaque jour : Jour 2 = prototype Workshop fonctionnel, Jour 5 = présentation executive avec ROI quantifié et deployment roadmap.

---

## `results/claude-pilot-methodology.md`
**Rôle :** Résultat brut Claude Deep Research sur le prompt pilot 90 jours.
**Findings clés :**
- Source la plus précise sur la composition d'équipe : 1 DS + 2-4 FDEs standard, avec mention des DS issus de McKinsey/BCG/Bain et des FDEs travaillant 50-70h/semaine avec 50-80% de déplacements.
- Décrit les 4 phases en détail avec les artéfacts formels : ontology schema, data pipelines, Workshop apps, custom configurations, data flow diagrams, weekly field notes.

---

## `results/claude-expand-scale.md`
**Rôle :** Résultat brut Claude Deep Research sur le prompt expand & scale.
**Findings clés :**
- Détaille la courbe d'expansion par cohorte (1x → 8-10x+ sur 7 ans) issue du S-1 avec interprétation économique du hockey stick.
- Décrit les 3 mécanismes de stickiness structurel : data integration dependencies (combien de systèmes connectés), ontology complexity (combien d'Object Types), et institutional knowledge captured (decision logs, audit trails).

---

## `results/claude-foundry-tools.md`
**Rôle :** Résultat brut Claude Deep Research sur le prompt Foundry tools.
**Findings clés :**
- Fournit des exemples de code OSDK TypeScript complets et fonctionnels : `fetchPage`, `where` avec filtres, `aggregate`, `$link` pour les relations, `applyAction`.
- Détaille l'architecture Apollo : constraint-based pull model, hub-spoke mesh, 3.5 minutes deployment moyen, 4.9 minutes rollback moyen, fonctionnement air-gapped autonome.

---

## `results/synthese-1-presales-bootcamp-playbook.md`
**Rôle :** Synthèse fusionnée GPT+Claude+Perplexity sur le thème pre-sales & bootcamp — dédupliquée avec annotations de source et signalement des contradictions.
**Findings clés :**
- Converge sur le volume bootcamps : 560+ organisations fin Q4 2023, 1 300+ juin 2024, ~5 bootcamps/jour en 2024.
- [CONTRADICTION] documentée sur le nombre de participants côté client : Claude dit 8-12, Perplexity dit 5-20 — probablement des phases différentes du même processus.

---

## `results/synthese-2-pilot-implementation-methodology.md`
**Rôle :** Synthèse fusionnée sur le pilot 90 jours — fusion de 3 sources avec contradictions documentées.
**Findings clés :**
- [CONTRADICTION] sur la taille d'équipe : Claude indique 1 DS + 2-4 FDEs, Perplexity indique 4-5 personnes (2-3 FDSE + 1-2 DS) — les deux convergent sur un total 3-5 personnes.
- Présente les 4 phases qui se chevauchent avec les semaines de début et fin de chaque phase.

---

## `results/synthese-03-expand-scale-playbook.md`
**Rôle :** Synthèse fusionnée sur expand & scale avec données financières S-1 vérifiées.
**Findings clés :**
- Précision critique : le "multiple 56x" du S-1 représente le revenu agrégé des clients acquis en H1 2020, pas la conversion d'un seul pilote.
- NDR NDR plancher récent à 107% (Q3 2023), NDR pic US Commercial à 150% (cohorte 2021), NDR Q4 2025 à 139%.

---

## `results/synthese-04-foundry-tools.md`
**Rôle :** Synthèse fusionnée sur les outils Foundry — fusion GPT+Claude+Perplexity avec annotations UI précises.
**Findings clés :**
- [CONTRADICTION] sur la localisation du bouton "Create" dans l'Ontology Manager : GPT = top bar, Claude = toolbar, Perplexity = top-right dropdown — trois descriptions du même workflow, positions d'UI légèrement différentes.
- Documente le workflow complet de création d'un Object Type en 8 étapes avec les variantes entre l'assistant guidé et la complétion manuelle.

---
