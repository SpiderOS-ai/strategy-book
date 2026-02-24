# 07-spider-inputs — Index

> Corpus des inputs primaires ayant servi à construire la thèse Spider : documents de synthèse investor-grade, fichiers nettoyés structurés, et sources brutes (transcripts, thèse originale, cas clients, architecture, BMAD).

---

## Fichiers racine

---

## `SPIDER-FINAL.md`
**Rôle :** Document de thèse investor-grade Spider — "the document you give a Thiel or Graham."
**Findings clés :**
- 10 thèses sur 4 axes (L'Actif → L'Impasse → La Brèche → Le Monopole), architecture 2 couches (Service Layer + Intelligence Layer).
- Cas Jordan documenté comme proof of concept (726 campagnes, triple saisie, prototype 2h30).
- Roadmap 18 mois, hypothèses H1-H9 testables, kill criteria explicites. Daté 19 fév 2026.

---

## `SPIDER-MEGA-RECAP.md`
**Rôle :** Bible interne opérationnelle Spider — version complète avec toutes les dimensions.
**Findings clés :**
- Structure identique à SPIDER-FINAL mais plus détaillée : thèses + équipe + 3 cas (Jordan, Decotec, Twoghether) + produit + marché + inconnues + répertoire.
- Inclut les unknowns critiques (pricing, timing window, Jean/Thierry alignment) et la direction du répertoire des fichiers sources.
- Source de vérité interne vs SPIDER-FINAL qui est la version investisseur.

---

## `SPIDER-PALANTIR-BLUEPRINT.md`
**Rôle :** Blueprint d'exécution — traduction de la machine Palantir (4 phases) en équivalents Spider pour PME/ETI.
**Findings clés :**
- Mapping complet Bootcamp→Diagnostic Éclair, Pilot→4 semaines 490 EUR/mois, Expand→upsell vertical, Scale→SaaS autonome.
- Plan d'action 12 premières semaines avec jalons concrets.
- Règle de conversion : "diviser l'échelle par 1000, diviser le temps par 10, multiplier l'IA par 10."

---

## `SPIDER-POSITIONING-2026.md`
**Rôle :** Cartographie concurrentielle 2026 + roadmap de positionnement 2026-2028.
**Findings clés :**
- 7 catégories de compétiteurs mappées, actualisée avec le lancement OpenAI Frontier (5 fév 2026).
- Dust.tt identifié comme seul concurrent direct français avec positionnement AI agents.
- Roadmap en 3 phases : PMF (agences Normandie, 5 clients) → Scale FR → European Expansion.

---

## `SPIDER-QUESTIONS-REFLEXIONS.md`
**Rôle :** Q&A stratégique v2 avec réponses directes de Nathan — questions résolues et questions ouvertes.
**Findings clés :**
- Questions résolues : alignment Jean (partiel), scope BMAD (fonctionnel valide, business model obsolète), misconception "zero effort."
- Questions ouvertes : pricing (490 vs 500), timing window (18 mois max), motion de vente, rôle Thierry.
- Montre la pensée non filtrée de Nathan sur les points de friction stratégiques.

---

## `answers.md`
**Rôle :** Réponses brutes de Nathan aux questions v1 — supersédé par QUESTIONS-REFLEXIONS.md.
**Findings clés :**
- Version non filtrée avec la voix directe : "je m'en fous du moyen, je veux créer un empire."
- Contient des formulations franches sur Jean, le pricing, et la vision long terme qui ont été lissées dans v2.
- À lire en complément de QUESTIONS-REFLEXIONS pour comprendre le niveau de conviction sous-jacent.

---

## `SPIDER-FINAL.html` / `SPIDER-GLOBAL.html`
**Rôle :** Rendus HTML de SPIDER-FINAL.md et d'un document global — non résumables séparément.
**Findings clés :**
- Exports HTML des fichiers markdown correspondants, utilisés pour partage/présentation.

---

## cleaned/

---

## `cleaned/01-these-nathan.md`
**Rôle :** Thèse fondatrice de Nathan nettoyée — le manifeste Spider avec en-tête de contexte.
**Findings clés :**
- Vision centrale : le savoir tacite des PME européennes comme "dernier trésor européen non numérisé."
- Triple convergence de fenêtre 2026-2028 : LLMs capables, coûts d'inférence en chute, génération fondatrice en age de décision.
- Formulation originale de "Spider sauvera l'Europe malgré elle."

---

## `cleaned/02-deal-structure.md`
**Rôle :** Document d'évolution du cap table Spider — du deal initial à la structure finale.
**Findings clés :**
- Structure initiale : Nathan ~70%, Remy ~10%, Drakkar 20%. Structure finale : Nathan 51%, Jean 20%, Remy 14%, Thierry 10%, Drakkar 5%.
- CODIR 31 jan identifié comme point de bascule émotionnel clé dans la négociation.
- Répartition Drakkar (cap table Drakkar) : Nathan 47%, Jean 38%, Thierry 15%.

---

## `cleaned/03-cas-decotec.md`
**Rôle :** Autopsie de 3 ans de relation client Drakkar/Decotec — genèse de la thèse Spider.
**Findings clés :**
- PME industrielle 155 salariés, CA 22M EUR (en baisse depuis 30M). Rupture le 12 fév 2026.
- Insight fondateur extrait : "les dirigeants PME veulent régner, pas gouverner" — ils délèguent l'exécution mais pas le pouvoir.
- Prouve qu'une relation de 3 ans de conseil n'empêche pas l'échec si le produit ne change pas la structure de pouvoir.

---

## `cleaned/04-cas-jordan.md`
**Rôle :** Premier beta test Spider — cas ComPrivee (affichage publicitaire, Normandie).
**Findings clés :**
- 726 campagnes, 73 clients, triple saisie (Sheets→Notion→Pennylane), workflow 9 étapes, 39.3% d'impayés non détectés.
- Prototype construit en 2h30 — validation empirique de la thèse "temps de déploiement compressé par l'IA."
- Jordan (Antoine Soulé) = ICP parfait : CEO seul, entreprise en croissance rapide, douleur quantifiée, réseaux Drakkar.

---

## `cleaned/05-cas-twoghether.md`
**Rôle :** Deal perdu face à The Tribe — double leçon sur le marché et les biais de Nathan.
**Findings clés :**
- Perdu au profit de The Tribe (70+ personnes) malgré une offre techniquement supérieure selon Nathan.
- Leçon 1 : le modèle studio/agence est disrupté MAINTENANT, pas dans 2 ans.
- Leçon 2 : Nathan vit dans une bulle YC — le client a choisi l'émotion sur la compétence. Signal sur la motion de vente nécessaire.

---

## `cleaned/06-jean-contexte.md`
**Rôle :** Évolution stratégique de Jean Le Tulzo — du "DRK Data Copilot" BI-centrique vers l'alignement Spider.
**Findings clés :**
- Note du 22 jan (DRK Data Copilot) : vision BI-centrée, dashboards, très éloignée de Spider.
- Mail du 18 fév : beaucoup plus aligné, mais Nathan garde la mise en garde : "les réflexions de Jean ne sont surtout pas à prendre dans ce qu'est Spider."
- Tension productive documentée : Jean apporte l'opérationnel PME, Nathan tient la vision produit.

---

## `cleaned/07-tech-architecture.md`
**Rôle :** Specs techniques SpiderOS — infrastructure K8s, stack, namespaces actifs.
**Findings clés :**
- 3 clusters K8s : OVH (prod), Scaleway (staging), local (dev). GitOps ArgoCD. SurrealDB pour le knowledge graph.
- Auth : Zitadel OIDC. Connecteurs : Nango. BDD : PostgreSQL + Redis.
- Namespaces actifs documentés par cluster — architecture prête pour la production, pas un prototype.

---

## `cleaned/08-bmad-product-vision.md`
**Rôle :** Vision produit BMAD de janvier 2026 — 6 modules, business model pré-pivot.
**Findings clés :**
- 6 modules : Memory (P0 — knowledge graph), People (CRM), Builder (IDE IA), Chatbot (LLM gateway), Content (éditeur), Documents.
- Business model obsolète (pré-pivot SaaS) mais scope fonctionnel toujours valide.
- Source pour comprendre les ambitions produit initiales avant la compression Palantir.

---

## `cleaned/09-contexte-ia-drakkar.md`
**Rôle :** Cadre IA en 5 phases de Nathan + analyse OpenClaw + positionnement Drakkar comme pont.
**Findings clés :**
- 5 phases : chatbot → copilot → agent → swarm → entreprise IA-native. Spider cible la transition phase 3→4.
- OpenClaw : 200K étoiles GitHub en 2 mois — signal sur la vitesse d'adoption des frameworks d'agents.
- Drakkar positionné comme "traducteur entre la réalité IA et les PME françaises" — pas un ESN, pas un éditeur.

---

## raw/

---

## `raw/appel_jean_nathan.md`
**Rôle :** Transcript complet de l'appel stratégique Jean-Nathan du 17 fév 2026.
**Findings clés :**
- Couverture : perte Twoghether, mort du modèle studio/ESN, pivot vers AI agents et Service-as-Software.
- Jean reconnaît explicitement que le modèle Drakkar actuel n'est pas scalable sans IA.
- Moment clé : accord sur le fait que Spider doit "faire le travail, pas vendre du conseil."

---

## `raw/these.md`
**Rôle :** Thèse originale brute de Nathan — le manifeste "Spider sauvera l'Europe malgré elle."
**Findings clés :**
- Texte non filtré avec accents et formatage original — version avant nettoyage dans cleaned/01.
- Révèle la conviction fondatrice et la formulation raw du positionnement anti-ERP.
- Utile pour retrouver la voix authentique de Nathan dans les documents de pitch.

---

## `raw/reflexion_decotec.md`
**Rôle :** Document interne Drakkar du 13 fév 2026 sur le cas Decotec — format brut.
**Findings clés :**
- Même contenu que cleaned/03 mais sans en-tête de contexte ajouté.
- Écrit à chaud 1 jour après la rupture — proximité émotionnelle visible dans le ton.
- Version de référence pour cleaned/03 si besoin de vérifier le contenu original.

---

## `raw/prompt.md`
**Rôle :** Méta-document — le prompt original donné pour démarrer la session 07-spider-inputs.
**Findings clés :**
- Explique le contexte et l'index de chaque fichier fourni dans la session.
- Documente l'intention de chaque source : pourquoi chaque fichier existe dans le corpus.
- Utile pour comprendre la logique éditoriale du dossier raw/.

---

## `raw/evolution_proposition_deal_nathan.md`
**Rôle :** Recap de l'évolution du deal — structure initiale → CODIR → structure finale proposée.
**Findings clés :**
- Trace l'historique complet des négociations cap table avec les points de pivot.
- Citation mentor : "Tu construis des options, pas un empire" — signal sur la tension fondateur/investisseur.
- Complète cleaned/02 avec la chronologie émotionnelle des négociations.

---

## `raw/bmad_spideros/`
**Rôle :** Dossier contenant le PRD, product brief, UX design et documents BMAD SpiderOS de jan 2026.
**Findings clés :**
- Inclut prd.md, product-brief.md, ux-design.md et sous-dossiers brainstorming/, research/, templates/.
- Business model dans ces docs est obsolète (pré-pivot SaaS) mais l'architecture fonctionnelle est valide.
- Source primaire pour comprendre les décisions produit initiales documentées en méthodologie BMAD.

---

## `raw/cas_jordan/`
**Rôle :** Dossier du cas ComPrivee/Jordan — explications + fichiers binaires (non lus).
**Findings clés :**
- Contient explications.md avec le contexte détaillé du cas Jordan.
- Fichiers .pdf, .xlsx, .docx présents (données campagnes, factures) — non résumables en texte.
- La synthèse du cas est dans cleaned/04-cas-jordan.md.

---

## `raw/cas_twoghether/`
**Rôle :** Dossier du cas Twoghether perdu — 4 fichiers RDV + sous-dossier perte/.
**Findings clés :**
- Transcripts/notes des 4 rendez-vous avec Twoghether avant la décision finale.
- Sous-dossier perte/ contient l'analyse post-mortem du deal perdu.
- La synthèse du cas est dans cleaned/05-cas-twoghether.md.

---

## `raw/contenu_nathan/`
**Rôle :** Contenus de communication de Nathan — note interne Drakkar et post LinkedIn.
**Findings clés :**
- note-interne-drakkar.md : communication interne sur l'évolution stratégique de Drakkar vers l'IA.
- post_linkedin_nathan.md : formulation publique du positionnement Nathan/Spider.
- Utile pour aligner le discours externe avec la thèse interne.

---

## `raw/jean/`
**Rôle :** 3 mails de Jean Le Tulzo — évolution de sa pensée stratégique sur Spider/Drakkar.
**Findings clés :**
- Séquence chronologique de mails montrant l'alignement progressif de Jean.
- Complète raw/appel_jean_nathan.md et cleaned/06 avec les formulations écrites de Jean.
- Source primaire pour comprendre le niveau d'adhésion réel de Jean à la vision Spider.

---

## `raw/tech/`
**Rôle :** Documents techniques bruts — architecture globale SpiderOS et stack back/front cible.
**Findings clés :**
- spider_archi_globale.md : architecture système complète de SpiderOS.
- spider_stack_back_front_cible.md : décisions de stack front et back avec justifications.
- Sources primaires pour cleaned/07-tech-architecture.md.

---
