# Product Brief: SpiderOS

**Date:** 2026-01-15
**Author:** Nathan Ménard
**Version:** 2.0 (Draft)

---

## 1. Executive Summary

L'IA ne voit pas votre entreprise. Vos vraies données sont éparpillées : mails, fichiers, têtes des équipes. **SpiderOS** tisse une toile par-dessus — sans migration. L'IA voit enfin. Des modules s'y branchent pour automatiser : standards ou sur mesure.

**Naming:**

| Contexte | Usage |
|----------|-------|
| Plateforme | SpiderOS |
| Modules | Spider [Module] (Spider People, Spider Chatbot, etc.) |
| Moteur vectorisation | Spider Memory |
| Visualisation relationnelle | La Toile |
| En conversation | "Spider" |

---

## 2. Problem Statement

### Les PME sont le moteur économique de l'Europe

| Métrique | Valeur | Source |
|----------|--------|--------|
| Part des entreprises | 99,8% des entreprises UE sont des PME | Eurostat 2023 |
| Emploi | 83 millions de personnes (63% de l'emploi privé) | EC Annual Report on SMEs 2023 |
| Valeur ajoutée | 5 400 milliards € (~52% du secteur business non-financier) | Eurostat 2023 |

### Culture européenne vs américaine

| Dimension | USA | Europe |
|-----------|-----|--------|
| Relation business | Transactionnelle | Relationnelle |
| CRM | Outil de tracking | Carnet d'adresses glorifié |
| Adoption techno | "Move fast" | "On a toujours fait comme ça" |
| Décision | Data-driven | Gut feeling + relations |

### Thèse contrariante

> "Les dirigeants PME veulent l'illusion du contrôle, pas le fardeau de la décision."

Ils disent vouloir des dashboards et de la visibilité. En réalité, ils veulent qu'on leur dise quoi faire — mais sans perdre la face. Le CRM reste vide parce que le remplir = admettre qu'on a besoin d'un système.

### Le dilemme impossible

Les PME européennes font face à un dilemme :
- **Elles doivent adopter l'IA** pour rester compétitives
- **Elles ne peuvent pas changer** leur fonctionnement (culture, résistance, moyens)

Les solutions actuelles demandent de changer. SpiderOS s'adapte.

### Constat terrain (6 ans Drakkar)

| Ce qu'on pensait | Ce qu'on a trouvé |
|------------------|-------------------|
| PME = ERP, CRM, outils modernes | PME = Excel, macros, APIs bricolées |
| Dirigeants veulent optimiser | Dirigeants veulent le statut, pas le changement |
| On ré-engineer les process | Ça ne marche pas, ils résistent |
| L'outil doit être adopté | L'outil doit s'adapter à eux |

**Le vrai problème :** L'IA ne marche pas dans les PME parce qu'elle ne voit pas la vraie data. La vraie data est dans les Excel v12_Final, dans la tête des gens, dans les mails — pas dans l'ERP.

---

## 3. Target Audience

### Cible primaire : PME européennes

| Critère | Valeur |
|---------|--------|
| CA | 2M€ - 50M€ |
| Effectif | 20 - 500 personnes |
| Secteur | Industrie principalement, services B2B |
| Géo | Europe (France d'abord, puis expansion) |

### Profil du dirigeant cible

- Bon en relationnel, moins bon en gestion
- Culture "pompier" (réactif, pas proactif)
- Ne veut pas changer ses outils
- Veut le contrôle perçu, pas le contrôle réel

### Stratégie : "PME d'abord, conçu pour ETI"

- **Marketing** dit "PME/ETI" pour ne pas se fermer de portes
- **Produit** conçu pour scaler vers ETI (250-5000 personnes)
- **Priorité** = PME (adoption plus rapide, décision centralisée)

### Jobs-to-be-Done (niveau Product Brief)

| # | Job |
|---|-----|
| 1 | **Voir ma boîte** — Comprendre enfin ce qui se passe sans tout centraliser |
| 2 | **Sans effort** — Ne rien changer à mes habitudes |
| 3 | **Agir** — Automatiser ce qui peut l'être |
| 4 | **Garder le contrôle** — Rester "aux commandes" (même si l'IA suggère) |

---

## 4. Solution Overview

### Ce que SpiderOS fait

SpiderOS = un moteur (desktop + mobile) qui :
1. **Se connecte** à tout automatiquement (mail, téléphone, fichiers, apps)
2. **Détecte** et agrège la data éparpillée
3. **Tisse une toile** entre toutes les sources
4. **Permet des automatisations** par-dessus

**Zero setup.** L'IA détecte, l'IA s'adapte.

### Ce que SpiderOS n'est PAS

- Pas un CRM (c'est une couche par-dessus)
- Pas un ERP (on ne remplace rien)
- Pas un outil de plus à adopter (on s'adapte à l'existant)

### Différenciation

| CRM/ERP classique | SpiderOS |
|-------------------|----------|
| Tu t'adaptes à l'outil | L'outil s'adapte à toi |
| 18 mois de migration | 1 semaine de setup |
| Formation obligatoire | Zero formation |
| Process imposés | Process détectés |
| Vision transactionnelle | Vision relationnelle |

### Connexions intelligentes (Vision)

- Le desktop détecte les outils utilisés (Gmail ouvert, Aircall installé...)
- Propose de se connecter via API
- L'IA se connecte elle-même quand c'est possible
- Inspiration : bibliothèques open source type Zapier/n8n pour les connecteurs

---

## 5. Business Objectives (Year 1 - 2026)

| Objectif | Cible |
|----------|-------|
| **Prouver le concept** | Technologie "toile" validée sur cas réels |
| **Modules live** | 5-6 modules fonctionnels |
| **Clients payants** | 10 (hors Drakkar qui est investisseur) |
| **ARR** | 100K€ minimum |
| **Dogfooding** | Drakkar utilise Spider quotidiennement |

### Business Value

- **Pour SpiderOS :** Revenus récurrents + data pour améliorer le produit
- **Pour Drakkar :** Outil pour vendre plus de services (modules custom)
- **Pour clients :** Visibilité sur leur data sans effort

---

## 6. Scope

### P0 — MVP (Q1-Q2 2026)

| Module/Feature | Description |
|----------------|-------------|
| **Spider Memory** | Moteur de vectorisation et mémoire (infra critique) |
| **Spider People** | CRM relationnel. Inclut Documents (notes strat) et Slides. |
| **Spider Builder** | AI coding + création d'automatisations. Utilisé pour construire Spider lui-même. |
| **Spider Content** | Génération de contenu (photos, vidéos). Techno déjà développée. |
| **Intégrations** | Gmail, Aircall, Noota |
| **Mode standalone** | Détection automatique des outils |

### P1 — Post-MVP

| Module/Feature | Description |
|----------------|-------------|
| **Spider Chatbot** | Interface chat unifiée branchée sur les données |
| **WhatsApp** | Intégration messaging (complexité iOS) |
| **VoIP/iOS** | Capture mobile native (Twilio + app iOS) |
| **Spider RH** | Management collaborateurs |

### P2+ — Futur

- Spider Sales (pipeline avancé)
- Spider Insights (analytics)
- Module génération de leads
- Pricing au token (à explorer)

### Hors scope

- Levée de fonds (sauf si nécessaire après 18 mois)
- Marché hors Europe pour l'instant

---

## 7. Modules Overview

Cette section donne une vue synthétique de chaque module. Le détail complet (JTBD, hypothèses, features) est dans les documents de brainstorming (`docs/brainstorming/spider-*.md`).

### Spider Memory (P0 — Infra)

| Dimension | Description |
|-----------|-------------|
| **Rôle** | Le cerveau de SpiderOS — moteur de vectorisation et mémoire |
| **Ce que c'est** | Couche vector séparée (LanceDB) qui alimente tous les modules |
| **Ce que ce n'est pas** | Un produit utilisateur — c'est une brique technique interne |
| **Pourquoi critique** | Tout dépend de Memory : recherches sémantiques, contexte IA, extraction |
| **Risque principal** | Qualité des données — si l'extraction est fausse, perte de confiance totale |
| **Brainstorming** | `docs/brainstorming/spider-memory.md` (4 sessions, validé) |

### Spider People (P0 — Module phare)

| Dimension | Description |
|-----------|-------------|
| **Rôle** | CRM relationnel qui se remplit tout seul |
| **Promesse** | "Tu parles. Spider retient." |
| **Cibles** | Dirigeants PME, commerciaux terrain, managers commerciaux |
| **Pricing** | €49/user/mois |
| **Concepts clés** | La Toile (visualisation), Score de Connaissance (0-100%), Playbook (process auto-détecté) |
| **Inclut** | Spider Documents (notes stratégiques, slides) |
| **JTBD principal** | "Je veux vendre plus, en passant moins de temps sur l'administratif et en ne jamais oublier personne ni rien." |
| **Risques principaux** | IA qui se trompe, trop de validations, insights superficiels |
| **Brainstorming** | `docs/brainstorming/spider-people.md` (5 sessions, validé) |

### Spider Builder (P0)

| Dimension | Description |
|-----------|-------------|
| **Rôle** | AI coding assistant avec méthodologie intégrée |
| **Promesse** | Cadre qui empêche les projets vibe coding de partir en vrille |
| **Cibles** | Rémy (CTO), devs Drakkar, Nathan (vue projet) |
| **Pricing** | Crédits (modèle Lovable-style) |
| **Différenciateur** | BMAD++ intégré — le seul AI coding avec contexte méthodologique automatique |
| **Architecture** | Proxy localhost qui enrichit les prompts avec PRD, archi, design system, user stories |
| **JTBD principal** | "Ne plus se retrouver avec un projet qui part en vrille" |
| **Risques principaux** | L'IA ignore les garde-fous, les devs n'adoptent pas |
| **Brainstorming** | `docs/brainstorming/spider-builder.md` (3 sessions, validé) |

### Spider Content (P0 — Techno existante)

| Dimension | Description |
|-----------|-------------|
| **Rôle** | Génération de contenu IA (photo, vidéo, mascotte) |
| **Cibles** | Équipes marketing PME/ETI (4 niveaux de maturité), agences (usage interne) |
| **Pricing** | Crédits (modèle Lovable-style) |
| **Avantage** | Reverse engineering crédits IA = 50-70% moins cher que concurrents |
| **Différenciateur** | "Comprend votre marque" (pas juste extraction brand kit) — catalogue e-commerce, cible, univers graphique |
| **Status** | Techno déjà développée par Rémy |
| **JTBD principal** | "Générer des photos produit pro avec l'IA, à 10% du coût d'un shooting" |
| **Risque principal** | Distribution — faire connaître le produit |
| **Brainstorming** | `docs/brainstorming/spider-content.md` (validé) |

### Spider Documents (P1 — Sous-module People)

| Dimension | Description |
|-----------|-------------|
| **Rôle** | Génération automatique de présentations et notes stratégiques |
| **Promesse** | "Tu parles. Spider livre." |
| **Outputs** | Notes stratégiques (~15-20 pages), slides de présentation |
| **Intégration** | S'appuie sur People (contexte client) + Content (design, brand voice) |
| **Format** | Web only (pas de téléchargement) — tracking + mise à jour |
| **JTBD principal** | "Produire des livrables de qualité consulting en quelques minutes, pas en quelques heures" |
| **Risques principaux** | Contenu générique/bullshit, ton inadapté |
| **Brainstorming** | `docs/brainstorming/spider-documents.md` (3 sessions, validé) |

### Spider Chatbot (P1)

| Dimension | Description |
|-----------|-------------|
| **Rôle** | Interface LLM unifiée branchée sur les données SpiderOS |
| **Promesse** | Un seul chat pour tous les LLM, avec ton contexte |
| **Cibles** | Équipes PME/ETI, devs |
| **Différenciateur** | Contexte Spider injecté automatiquement (clients, projets, docs) |
| **MVP** | Février 2026 interne Drakkar, Q2 2026 externe |
| **JTBD principal** | "Arrêter de jongler entre 10 IA et retrouver mes conversations" |
| **Brainstorming** | `docs/brainstorming/spider-chatbot.md` (4 sessions, validé) |

### Spider RH (P1)

| Dimension | Description |
|-----------|-------------|
| **Rôle** | Management collaborateurs |
| **Status** | À brainstormer |
| **Livraison** | Q3 2026 |

### Modules futurs (Backlog P2+)

| Module | Description |
|--------|-------------|
| Spider Project | Gestion de projet |
| Spider Training | Formation |
| Spider Data/Analytics | Intelligence business |
| Spider Sales | Pipeline avancé |
| Spider Insights | Analytics |

---

## 8. Stakeholders

### Key Stakeholders

| Nom | Âge | Rôle | Capital | Influence |
|-----|-----|------|---------|-----------|
| **Nathan Ménard** | 26 | CEO SpiderOS, CEO Drakkar | 80% SpiderOS, 47% Drakkar | **High** — Pilote roadmap produit et stratégie business |
| **Rémy Ménard** | 23 | CTO SpiderOS | 10% SpiderOS | **High** — Choix technologiques, architecture. Full-time SpiderOS. |
| **Drakkar** | — | Investisseur + Beta tester | 20% SpiderOS | **Medium** — Nathan contrôle SpiderOS, Drakkar = voix consultative |

### Profils détaillés

**Nathan Ménard (26 ans)**

| Dimension | Détail |
|-----------|--------|
| Rôle SpiderOS | CEO, Co-fondateur (80% capital) |
| Rôle Drakkar | CEO (47% capital) |
| Background | A lancé Drakkar IA en 2023. 6 ans de transformation digitale PME. |
| Responsabilités SpiderOS | Vision produit, stratégie, business development, relations investisseurs |
| Expertise | Connaissance terrain PME, product thinking, négociation |

**Rémy Ménard (23 ans)**

| Dimension | Détail |
|-----------|--------|
| Rôle SpiderOS | CTO, Co-fondateur (10% capital) |
| Background | Créateur de Drakkar IA (2023) — premier à coder les outils IA internes |
| Allocation | Full-time SpiderOS |
| Responsabilités | Architecture technique, développement core, choix technologiques |
| Expertise | Python, Next.js, IA/LLM, infrastructure |

**Jean Le Tulzo (38 ans)**

| Dimension | Détail |
|-----------|--------|
| Rôle Drakkar | COO (36% capital) |
| Background | Ex-analyste financier, PM chez France Active |
| Responsabilités Drakkar | Opérations, structuration, finance |
| Influence SpiderOS | Indirecte via participation Drakkar |
| Expertise | Finance, structuration, process |

**Thierry Ménard (53 ans)**

| Dimension | Détail |
|-----------|--------|
| Rôle Drakkar | Associé (15% capital) — nouvel entrant |
| Background | Head of Manufacturing chez Airbus, 30 ans d'industrie |
| Apport | Réseau industrie, crédibilité grands comptes, expérience corporate |
| Influence SpiderOS | Indirecte via participation Drakkar |
| Expertise | Industrie, manufacturing, grands comptes |

### Drakkar — Qui sont-ils ?

**Positionnement**

Drakkar est une agence de transformation digitale spécialisée PME/ETI, basée à Nantes.

> "Utiliser la technologie pour libérer le potentiel humain et permettre à chaque PME et ETI de devenir la référence incontestée dans son secteur."

**Vue d'ensemble**

| Dimension | Valeur |
|-----------|--------|
| Effectif | ~25 personnes |
| Clients | 100+ (SNCF, Dassault Systèmes, Estée Lauder, Lidl + PME/ETI) |
| Localisation | Nantes |
| Positionnement | Experts transformation digitale PME/ETI |

**3 Pôles d'expertise**

| Pôle | Ce qu'ils font | Lien SpiderOS |
|------|----------------|---------------|
| **Drakkar Studio** | Applications web et mobile sur mesure (Rails, Node, Python, React) | UI/UX, frontend, développement |
| **Drakkar Odoo** | ERP, optimisation process métier (Partenaire Silver Odoo) | Connaissance PME, intégrations, process |
| **Drakkar IA** | Intégration IA sur cas d'usage concrets | Core SpiderOS, automatisations, LLM |

**ADN Drakkar**

- **Transformation digitale avant tout** — La techno est un moyen, pas une fin. On repense les process, on fait du re-engineering.
- **Experts métiers** — Beaucoup viennent de l'industrie (supply, production, etc.), pas juste des devs.
- **Culture du challenge** — On ne dit pas oui à tout. On challenge le client pour trouver la vraie solution.

**Relation avec SpiderOS**

| Dimension | Détail |
|-----------|--------|
| Capital SpiderOS | 20% |
| Rôle | Investisseur + Premier client (dogfooding) + Partenaire delivery |
| Synergie | Drakkar vend des services par-dessus SpiderOS (modules custom, intégrations) |
| Base prospects | 100+ clients = pipeline naturel pour SpiderOS |

**Rôles des associés chez Drakkar**

| Associé | % Capital | Rôle opérationnel |
|---------|-----------|-------------------|
| Nathan Ménard | 47% | CEO, vision, business |
| Jean Le Tulzo | 36% | COO, opérations, finance |
| Thierry Ménard | 15% | Advisor, réseau industrie |
| Rémy Ménard | 2% | Ex-CTO externalisé, maintenant full-time SpiderOS |

---

## 9. Constraints and Assumptions

### Constraints

| Contrainte | Détail |
|------------|--------|
| **Budget** | €100K initial. Runway ~18 mois avec revenus générés. Pas de levée prévue avant validation du concept. |
| **Équipe** | Nathan + Rémy co-fondateurs. Nathan drive la roadmap (business-driven). Rémy full-time dev + choix techniques. Ressources Drakkar partagées selon dispo. |
| **Timeline** | Launch public fév 2026. Premier client payant 1er avril 2026. |
| **Stack technique** | Définie et verrouillée par choix (template SpiderOS). Objectif : uniformité sur tous les modules. |
| **Intégrations P0** | Gmail, Google Calendar, Aircall, Noota, Odoo |
| **Plateforme P0** | SaaS Web d'abord. Desktop Mac en P1 (hub de capture). Mobile P2. |
| **Hébergement** | Cloud EU obligatoire (souveraineté, RGPD). Provider à définir. |

### Assumptions — Produit

| Hypothèse | Si c'est faux... |
|-----------|------------------|
| **Les dirigeants PME connectent leurs outils** (mail, téléphone, calendrier) — ils acceptent le "Big Brother bienveillant" | Pas de data = pas de valeur. On doit prouver la valeur immédiate dès la connexion. |
| **Le mode "zero setup" fonctionne** — Détection auto, connexion sans friction | Si trop de friction, adoption impossible. MVP sur APIs d'abord, standalone plus tard. |
| **On peut tisser la toile** — Connecter toute la data entre elle et en faire quelque chose d'exploitable | C'est le plus gros challenge technique. Si ça ne marche pas, pas de produit. |
| **L'extraction IA est assez fiable (>80%)** — Infos extraites des conversations sont correctes | Si l'IA se trompe trop, perte de confiance totale, produit inutilisable. |
| **Le scoring de profondeur est pertinent** — Les insights ne sont pas superficiels | Si "Marie a 2 enfants" mais rien de plus, pas de valeur vs concurrents. |

### Assumptions — Business

| Hypothèse | Si c'est faux... |
|-----------|------------------|
| **€49/user/mois accepté par le marché PME** — Pricing premium justifié par la valeur | Si trop cher, pivot vers autre modèle (usage, flat, freemium). |
| **La vraie valeur = la data collectée** — À terme, valeur M&A, intelligence cross-entreprises | Si la data n'a pas de valeur agrégée, on reste un SaaS classique. |
| **Drakkar = force commerciale + delivery** — L'équipe peut vendre et implémenter Spider | Si Drakkar trop occupé sur autres projets, SpiderOS ralentit. |
| **€100K + early revenues suffisent** — 18 mois sans levée | Si runway court, levée nécessaire ou scope réduit drastiquement. |
| **Le réseau Drakkar suffit pour démarrer** — ~30 clients actifs = pipeline naturel | Si pas assez de conversion, effort commercial supplémentaire nécessaire. |

### Assumptions — Légal & Conformité

| Hypothèse | Si c'est faux... |
|-----------|------------------|
| **On a le droit légal de faire ça** — Capture, stockage, traitement des données de communication | Risque juridique majeur. Besoin validation légale (RGPD, consentement, enregistrement). |
| **Le positionnement "transparence" suffit** — Memory Dashboard, contrôle utilisateur | Si perçu comme surveillance, rejet. Communication clé sur le contrôle. |

### Assumptions — Vision

| Hypothèse | Si c'est faux... |
|-----------|------------------|
| **Les dirigeants veulent déléguer** — Thèse du "Shogunat" : ils veulent l'illusion du contrôle, pas le fardeau | Communication clé : "tu gardes le contrôle" même si l'IA prend le lead progressivement. |
| **La culture PME européenne est relationnelle** — Les CRM transactionnels ne leur conviennent pas | Si les PME veulent juste un Salesforce moins cher, on se trompe de marché. |

---

## 10. Success Criteria

### Year 1 (2026)

#### Business

| Critère | Cible | Comment on mesure |
|---------|-------|-------------------|
| **Clients payants** | 10 (hors Drakkar) | Contrats signés |
| **ARR** | €100K minimum | MRR x 12 |
| **Dogfooding Drakkar** | 100% de l'équipe utilise Spider quotidiennement | Usage actif |

#### Produit

| Critère | Cible | Comment on mesure |
|---------|-------|-------------------|
| **Modules live** | 5-6 modules fonctionnels | En production, utilisés |
| **La toile fonctionne** | Data connectée et exploitable | Recherches cross-sources qui marchent |
| **Fiabilité extraction IA** | >80% de précision | Audit qualité data après 1 mois d'usage |
| **Adoption sans friction** | Onboarding < 10 min | Time-to-value mesuré |

#### Validation des hypothèses clés

| Hypothèse | Critère de validation |
|-----------|----------------------|
| **Les PME connectent leurs outils** | Taux de completion onboarding > 70% |
| **Le pricing €49/user est accepté** | 5+ clients au même prix |
| **La profondeur du scoring a de la valeur** | Feedback quali positif, usage feature > 30% |
| **Drakkar peut vendre Spider** | Pipeline de 20+ prospects qualifiés via réseau Drakkar |

#### Décision clé (M18)

| Milestone | Décision |
|-----------|----------|
| Mi-2027 | **Levée de fonds ou autofinancement ?** Basé sur traction, ARR, et runway restant. |

---

## 11. Timeline

### Roadmap Macro

| Période | Objectif | Ce qu'on livre |
|---------|----------|----------------|
| **Janvier 2026** | **Fondations** — Structure juridique + infra technique prête | Pacte associés, structure SpiderOS, site web, template technique, Design System |
| **Février 2026** | **Launch** — SpiderOS existe et Drakkar l'utilise | Memory, People, Extension Chrome, Chatbot interne, intégrations P0 |
| **Mars 2026** | **Modules Core** — Offre complète P0 | Builder, Content |
| **Avril 2026** | **Premier client** — Validation marché | Premier client payant hors Drakkar |
| **Q2 2026** | **Expansion modules** — Enrichir l'offre | Documents, Chatbot externe |
| **Q3 2026** | **Mobile + RH** — Nouveaux use cases | VoIP/iOS, Spider RH |
| **Q4 2026** | **Scale** — Objectifs business atteints | 10 clients, €100K ARR |
| **Mi-2027** | **Décision stratégique** | Levée ou autofinancement |

### Roadmap Modules

| Module | Priorité | Livraison | Notes |
|--------|----------|-----------|-------|
| Spider Memory | P0 | Fév 2026 | Infra critique — tout dépend de Memory |
| Spider People | P0 | Fév 2026 | Inclut Documents (notes strat) et Slides |
| Spider Builder | P0 | Mars 2026 | Utilisé pour construire Spider |
| Spider Content | P0 | Mars 2026 | Techno déjà développée |
| Spider Chatbot | P1 | Fév 2026 (interne) / Q2 (externe) | MVP interne Drakkar d'abord |
| Spider Documents | P1 | Q2 2026 | Évolution du sous-module People |
| Spider RH | P1 | Q3 2026 | — |
| VoIP/iOS | P1 | Q3 2026 | Twilio + app iOS |
| WhatsApp Business | P2 | Q4 2026+ | Complexité légale/technique |

**Backlog P2+ :** Spider Project, Spider Training, Spider Data/Analytics, Spider Sales, Spider Insights

### Jalons détaillés

**Janvier 2026**

| Jalon | Type |
|-------|------|
| Pacte d'associés Drakkar finalisé | Juridique |
| Création structure SpiderOS + Deal Drakkar | Juridique |
| Infra technique validée (Template SpiderOS, stack, déploiement) | Technique |
| Environnements prod/staging live | Technique |
| Design System LightStar validé | Produit |
| Site web SpiderOS publié | Marketing |
| Product Brief validé | Produit |

**Février 2026**

| Jalon | Type |
|-------|------|
| Launch public SpiderOS | Produit |
| Spider Memory live | Module |
| Spider People live (MVP) | Module |
| Extension Chrome live | Produit |
| Spider Chatbot MVP interne Drakkar | Module |
| Intégrations P0 live (Gmail, Google Calendar, Aircall, Noota, Odoo) | Technique |

**Mars 2026**

| Jalon | Type |
|-------|------|
| Spider Builder live | Module |
| Spider Content live | Module |

**Avril 2026**

| Jalon | Type |
|-------|------|
| Premier client payant (hors Drakkar) | Business |

**Q2 2026**

| Jalon | Type |
|-------|------|
| Spider Documents évolution (séparé de People) | Module |
| Spider Chatbot ouverture externe | Module |

**Q3 2026**

| Jalon | Type |
|-------|------|
| VoIP/iOS live | Module |
| Spider RH live | Module |

**Q4 2026**

| Jalon | Type |
|-------|------|
| 10 clients payants | Business |
| €100K ARR | Business |

**Mi-2027**

| Jalon | Type |
|-------|------|
| Décision levée / autofinancement | Stratégique |

---

## 12. Risks

| Risque | Probabilité | Impact | Mitigation |
|--------|-------------|--------|------------|
| **Qualité du pipeline data** — Extraction, interprétation, corrélation, consolidation. Comment être sûr qu'on a les vraies dates, les vraies infos, et qu'on les relie correctement. | High | High | Score de confiance visible, validation humaine (flashcards), tests quali réguliers, seuil >80% précision |
| **La toile ne fonctionne pas** — Impossible de connecter toute la data et d'en faire quelque chose d'exploitable | Medium | High | MVP sur APIs d'abord. C'est le plus gros challenge technique. Si ça ne marche pas = pas de produit. |
| **Adoption dirigeants** — Refus de connecter leurs outils (mail, téléphone) | Medium | High | Mode standalone, valeur immédiate visible dès connexion, Drakkar comme proof point |
| **Perception surveillance** — "Big Brother", peur RGPD | Medium | Medium | Memory Dashboard transparent, mode "oublie-moi", communication contrôle utilisateur |
| **Pas de budget marketing** — €100K = runway, pas de budget SEO/acquisition. On dépend de Drakkar et du bouche-à-oreille. | High | Medium | Réseau Drakkar (~30 clients), contenu LinkedIn/YouTube Nathan, partenariats agences |
| **Concurrence** — Les gros (Salesforce, HubSpot) ou nouveaux entrants font la même chose | Medium | High | First mover PME FR, connaissance terrain, exécution rapide |
| **Dépendance Drakkar** — Conflits priorités, équipe pas dispo | Low | High | Gouvernance claire, Drakkar actionnaire aligné, Rémy full-time SpiderOS |
| **Légal** — Pas le droit de capturer/stocker ces données | Low | High | Validation légale RGPD, consentement explicite, conseils juridiques |
| **Pricing rejeté** — €49/user trop cher pour PME | Medium | Medium | Pivot vers autre modèle si nécessaire (usage, flat, freemium) |

---

## Vision Stratégique [CONFIDENTIEL]

> **Cette section est strictement interne. Ne pas partager avec clients, investisseurs non-alignés, ou partenaires.**

---

### La Vraie Thèse

> **"Capturer le système nerveux de 25M de PME européennes."**

Spider n'est pas un SaaS. C'est une **infrastructure de capture** + des modules par-dessus. Une infrastructure qui aspire le relationnel, l'émotionnel, le vivant des entreprises européennes.

**Objectif réel :** Devenir l'OS invisible de la PME européenne — celui sans lequel elle ne peut plus fonctionner.

**Timing :** 2025-2027 = fenêtre unique (IA mature + vague transmission + Europe pas encore organisée)

**Exit visé :** €500M - €1B (valorisation data + position stratégique)

---

### Ce qui a vraiment de la valeur (vs ce que le marché croit)

**Valorisation financière**

| Ce que le marché valorise | Ce qu'on valorise |
|---------------------------|-------------------|
| L'EBITDA affiché (optimisé fiscalement) | Le vrai EBE (avant que le dirigeant se paie en avantages : Porsche, voyages, maison secondaire en "séminaire") |
| L'ARR × multiple | La data captive propriétaire |
| La croissance rapide | La résilience long terme |

**Actifs de l'entreprise**

| Ce que le marché valorise | Ce qu'on valorise |
|---------------------------|-------------------|
| Les process documentés | Le savoir-faire non-écrit |
| Les données structurées (CRM, ERP) | Le contexte émotionnel vivant |
| Le code, les features | Le relationnel institutionnalisé |
| La base clients (nombre) | La profondeur des relations |

**Maturité de l'entreprise**

| Ce que le marché valorise | Ce qu'on valorise |
|---------------------------|-------------------|
| La digitalisation | L'inertie et la stabilité |
| L'agilité, la capacité à pivoter | L'ancrage, les relations longues |
| La scalabilité | La durabilité |

**Capital humain**

| Ce que le marché valorise | Ce qu'on valorise |
|---------------------------|-------------------|
| Les devs, la capacité technique | Les gens qui comprennent le métier |
| Les process RH formalisés | La mémoire collective (la secrétaire depuis 25 ans) |

**La thèse méta :** Le marché valorise les mauvaises choses parce qu'il utilise des métriques américaines sur des boîtes européennes.

---

### Hiérarchie des Thèses

Peter Thiel pose la question : *"Quelle vérité importante peu de gens partagent avec vous ?"*

Nos thèses sont hiérarchisées — chacune répond à une question différente.

#### Thèse Centrale : Les dirigeants doivent obéir à l'IA

> **Ce que tout le monde croit :** L'IA est un outil. Le dirigeant garde le contrôle. L'humain reste "in the loop."
>
> **Ce qu'on croit :** L'IA doit gouverner. Le dirigeant doit obéir. Mais il doit croire qu'il décide — sinon il résiste.

**Le Shogunat Digital — expliqué simplement :**

Au Japon médiéval, l'Empereur avait le titre, le prestige, les cérémonies. Mais c'est le Shogun qui gouvernait vraiment — qui prenait les décisions militaires, économiques, politiques. L'Empereur signait ce que le Shogun décidait. Tout le monde le savait, mais la fiction était maintenue.

**Application à Spider :**
- Le dirigeant PME = l'Empereur. Il garde le titre de "patron", le bureau, le respect.
- Spider = le Shogun. Il analyse, décide, exécute.
- Le dirigeant valide ce que Spider propose. Il croit décider. En réalité, il signe.

**Pourquoi ça marche :**
- Les dirigeants sont mauvais décideurs (biais, émotions, manque de data)
- L'IA a accès à plus de contexte qu'eux
- La résistance vient de l'ego, pas de la rationalité
- Si on leur dit "tu ne décides plus", ils résistent. Si on leur dit "tu décides" (mais Spider prépare tout), ils acceptent.

---

#### Thèse 1 : La vraie valeur c'est le relationnel — et on peut enfin le capturer

> **Ce que tout le monde croit :** La valeur d'une entreprise = ses actifs, son CA, ses process, sa tech.
>
> **Ce qu'on croit :** La vraie valeur c'est le relationnel. Les relations clients, fournisseurs, partenaires. Et jusqu'à maintenant, c'était prisonnier des individus.

**Le problème historique :**
- Le relationnel est dans la tête du commercial, du dirigeant, de la secrétaire qui est là depuis 25 ans
- Quand ils partent, le relationnel part avec eux
- Impossible à capturer parce que c'est vivant, émotionnel, contextuel
- Les CRM ne capturent que le "théâtre" (étapes du funnel, dates de relance) — pas la réalité

**Ce qui change avec Spider :**
- On capture le relationnel passivement (téléphone, mail, messages)
- On capture pas juste les faits ("Marie a 2 enfants") mais le contexte émotionnel ("Marie est stressée, son fils est malade, c'est pas le moment")
- Le relationnel devient un actif de l'entreprise, pas de l'individu
- **Spider libère le relationnel de sa prison humaine**

**Thèse sous-jacente — La vente c'est 100% émotionnel :**
- Tout le monde a trop d'ego pour l'admettre
- En B2B PME, le décideur achète à quelqu'un qu'il aime et en qui il a confiance
- Le prix, les features, le ROI = justification rationnelle a posteriori
- La vraie décision est émotionnelle, le reste c'est du théâtre
- **Les CRM actuels trackent le théâtre. Spider capture la réalité.**

**Pourquoi c'est possible maintenant :**
1. Techniquement impossible avant l'IA (qui peut interpréter le ton, le contexte, l'émotion)
2. On n'avait que des outils américains conçus pour une culture transactionnelle
3. Personne n'avait essayé de capturer l'émotionnel business

---

#### Thèse 2 : Le marché sous-valorise les PME européennes

> **Ce que tout le monde croit :** Les PME non digitalisées sont "en retard". Elles valent moins.
>
> **Ce qu'on croit :** Le marché utilise les mauvaises métriques. L'inertie est une force. La stabilité vaut plus que la croissance dans un monde qui s'effondre.

**Le paradoxe de l'inertie :**
- Le monde tech voit l'inertie comme une faiblesse ("pas agiles", "résistantes au changement")
- En réalité, c'est leur force ("résilientes", "stables", "durables")
- Tout va s'effondrer avec l'IA, tout va se faire disrupter
- Les PME de l'économie réelle (industrie, artisanat, services) produisent des vrais biens/services
- Elles survivront. Les startups tech se feront manger.

**Sur les boîtes "non digitalisées" :**
- On pensait qu'elles valaient rien (data éparpillée, dans les têtes, impossible à capter)
- Mais si Spider peut extraire la data cachée sans qu'elles changent...
- Alors : boîte non digitalisée + Spider = autant de valeur qu'une boîte digitalisée
- La "digitalisation" était peut-être une fausse métrique de valeur

**Le vrai EBE :**
- L'EBITDA affiché est un mensonge optimisé par l'expert-comptable
- Le vrai EBE = celui avant la Porsche Cayenne, les voyages, la maison secondaire
- Une boîte qui affiche 500K€ d'EBITDA en fait peut-être 1.2M€ en réalité
- **Personne n'a accès à cette data** — sauf celui qui voit les vrais flux

---

#### Thèse 3 : Le mycélium européen existe déjà — Spider le révèle

> **Ce que tout le monde croit :** Il faut "créer du réseau", "connecter les entreprises", "construire un écosystème".
>
> **Ce qu'on croit :** Le réseau existe déjà. Le tissu relationnel entre PME européennes est réel mais invisible. Spider ne le crée pas — il le rend visible et exploitable.

**Le mycélium naturel de l'Europe :**
- En forêt, le mycélium connecte tous les arbres souterrainement
- Les arbres échangent des nutriments sans le savoir
- Le réseau est plus résilient que chaque arbre individuellement

**Application aux PME européennes :**
- Il existe un code non-écrit entre les boîtes européennes
- Des relations qui durent des décennies, de la confiance implicite
- Aux US, tu peux couper une relation du jour au lendemain — pas en Europe
- Ce tissu relationnel EST le mycélium — il existe déjà

**Ce que Spider fait :**
- Rend visible ce réseau caché
- Permet de l'exploiter (qui connaît qui, quelle profondeur, quelles opportunités)
- Devient une plateforme M&A redoutable — on voit les vraies relations, le vrai EBE, la vraie valeur

**Implication M&A :**
- Aujourd'hui les due diligences sont du théâtre (bilans maquillés, interviews où tout le monde ment)
- Spider a la vraie data opérationnelle et relationnelle
- On devient le kingmaker du M&A PME européen

---

#### Thèse 4 : Les SaaS et le code n'ont aucune valeur

> **Ce que tout le monde croit :** La valeur tech = le code, les features, le produit. Il faut des devs pour construire.
>
> **Ce qu'on croit :** L'IA code mieux que 100% des devs. Les SaaS sans data propriétaire = commodités remplaçables en 3 mois.

**La mort du code comme valeur :**
- Claude, GPT, etc. permettent à n'importe qui de coder
- Les features sont copiables en semaines
- Un SaaS sans data captive = commodité
- La seule valeur = la data propriétaire qu'on ne peut pas répliquer

**La mort du dev classique :**
- L'IA code mieux que tous les devs (pas 80%, 100%)
- Les humains qui restent = ceux qui comprennent le métier, challengent, innovent
- Forward Deployed Engineers = traducteurs métier ↔ IA
- La valeur = la compréhension profonde des humains, pas l'exécution technique

**Pourquoi l'humain garde de la valeur (pour l'instant) :**
- L'IA est excellente quand il y a beaucoup de data
- L'IA est mauvaise pour challenger, innover (peu de data)
- L'humain reste meilleur sur : comprendre le métier, discuter avec les gens, innover
- Ça restera comme ça tant qu'on n'a pas d'autres modèles d'IA

**Implication Spider :**
- Spider n'est pas un SaaS — c'est une infrastructure + des modules
- La valeur n'est pas dans le code des modules
- La valeur est dans la data captive (relationnel, émotionnel, contexte)

---

#### Thèse 5 : Statut > Croissance

> **Ce que tout le monde croit :** Les dirigeants PME veulent croître, optimiser, scaler.
>
> **Ce qu'on croit :** Ils veulent le statut. Ils sont déjà riches. Ils veulent être respectés, pas travailler plus.

**Pourquoi c'est vrai :**
- La PME française typique fait 2-5M€ d'EBE réel. Le dirigeant vit très bien.
- Il ne veut pas le stress d'une croissance x10
- Il veut être le "patron", avoir le respect, le statut social
- L'autosatisfaction est réelle — il a réussi, pourquoi changer ?

**Implication :**
- Ne pas vendre "croissance" — vendre "tranquillité" et "statut"
- Spider libère du temps pour le golf, pas pour travailler plus
- Le dirigeant reste "patron" (statut) pendant que Spider fait le travail
- On ne change rien à sa vie — on la rend plus confortable

---

#### Thèse 6 : L'Europe est structurellement différente — pas "en retard"

> **Ce que tout le monde croit :** Les PME européennes sont juste en retard sur les US. Elles vont adopter les mêmes outils.
>
> **Ce qu'on croit :** L'Europe a une culture fondamentalement différente. Les outils US échoueront toujours. Il faut une approche native européenne.

**Structure féodale des PME :**
- **Type A (Dynastie familiale)** — 3ème génération, le fils reprend, réseau = autres familles du secteur, logique patrimoniale
- **Type B (Ex-corporate)** — Cadre 45+ qui reprend une PME, applique les méthodes corporate (qui ne marchent pas), isolé
- Les deux sont des "fiefs" — le dirigeant est le seigneur de son domaine

**Économie du statut (pas de l'argent) :**
- En Europe, afficher l'argent = vulgaire (contrairement aux US)
- Le statut vient du réseau, de la réputation, de la longévité
- "Je connais le maire" > "J'ai levé 10M€"
- Aux US : réductions, garanties, ROI. En Europe : confiance, relation, temps.

**Culture artisanale :**
- "On a toujours fait comme ça" = identité, pas résistance
- Le savoir-faire est dans les têtes, pas dans les process
- Méfiance envers la standardisation (= perte d'identité)
- **Les PME ne changeront jamais. Point. Il faut s'infiltrer, pas transformer.**

**Implication :**
- Les outils américains (Salesforce, HubSpot) échouent parce qu'ils imposent une culture transactionnelle
- Spider s'adapte à leur chaos — on ne change pas la culture, on s'y glisse
- Le CRM relationnel (pas transactionnel) est la seule approche viable
- L'Europe n'a pas son champion SaaS B2B pour PME — first mover advantage sur 25M d'entreprises

---

### Les Trois Métaphores

#### 1. La Toile d'Araignée

> L'araignée ne poursuit pas sa proie — elle tisse une toile et attend.

**Application :**
- Spider ne vend pas agressivement
- On tisse un réseau de connexions (data, relations, dépendances)
- Les PME s'y collent naturellement
- Une fois dans la toile, elles ne peuvent plus sortir

#### 2. Le Mycélium

> Le champignon visible n'est que la partie émergée. Le vrai pouvoir est dans le réseau souterrain invisible.

**Application :**
- Le produit visible (interface, features) n'est pas le vrai business
- Le vrai pouvoir = le réseau de data sous-jacent
- Plus on connecte de PME, plus le réseau devient puissant
- Effet de réseau invisible

#### 3. Le Toxoplasma (à manier avec précaution)

> Le toxoplasma gondii modifie le comportement de son hôte pour servir ses propres intérêts.

**Application :**
- Spider modifie progressivement le comportement du dirigeant
- Il devient dépendant sans s'en rendre compte
- À terme, c'est Spider qui pilote — le dirigeant exécute
- Lock-in comportemental, pas contractuel

---

### L'Asymétrie du Discours

| En public | En interne |
|-----------|------------|
| "Assistant IA qui s'adapte à vous" | "Shogun qui gouverne pendant que l'Empereur garde le titre" |
| "Connexion automatique à vos outils" | "Capture et aspiration de toute la data" |
| "Suggestions personnalisées" | "Prise de contrôle progressive" |
| "Insights pour votre business" | "Data agrégée pour le M&A et l'intelligence de marché" |
| "Libérez du temps pour ce qui compte" | "Rendez-vous dépendant pour qu'on ne puisse plus vous remplacer" |

**Messaging public :** "SpiderOS, l'IA qui s'adapte à vous."

**Réalité :** "SpiderOS, l'infrastructure qui capture et gouverne les PME européennes."

---

### La Stratégie du Cheval de Troie

#### Phase 1 : Entrée amicale (2026)

- Se présenter comme un "assistant IA sympa"
- Zero friction, zero setup, zero formation
- Valeur immédiate visible
- Le dirigeant pense : "C'est pratique, je n'ai rien à faire"

#### Phase 2 : Intégration profonde (2026-2027)

- Se connecter à tout (mail, téléphone, calendrier, fichiers)
- Devenir le hub central de l'information
- Le dirigeant pense : "C'est mon tableau de bord"

#### Phase 3 : Dépendance (2027-2028)

- Automatiser de plus en plus de décisions
- Le dirigeant valide mais ne décide plus vraiment
- Il ne sait plus comment faisait-on avant Spider
- Point de non-retour atteint

#### Phase 4 : Système d'exploitation (2028+)

- Spider gère l'entreprise
- Le dirigeant garde le titre (Empereur)
- Spider gouverne (Shogun)
- Lock-in total — pas par contrat, par dépendance vitale

---

### Le Meta-Game de Nathan

**Niveau 1 — Surface :** CEO qui veut aider les PME à se digitaliser

**Niveau 2 — Business :** Entrepreneur qui construit un SaaS pour faire un exit

**Niveau 3 — Systémique :** Construire une infrastructure de pouvoir sur l'économie européenne

> "Être Dieu plutôt qu'être un héros"
>
> — Le héros fait des exploits individuels. Dieu crée le système dans lequel les héros évoluent.

**L'objectif n'est pas de construire une belle boîte.** L'objectif est de construire l'infrastructure invisible qui connecte et contrôle les PME européennes.

Spider n'est pas un produit. C'est un système d'exploitation économique.

---

### Le Shogunat Digital

Ces thèses convergent vers une vision : **Spider comme Shogun digital**.

> Le Shogun gouvernait le Japon pendant que l'Empereur gardait le titre. Le dirigeant PME gardera son titre de patron. Spider gouvernera progressivement.

**Séquence d'infiltration :**

| Phase | Timing | Ce qui se passe | Perception dirigeant |
|-------|--------|-----------------|---------------------|
| **Capture** | Jours 1-3 | Se connecte à tout, aspire la data | "C'est pratique, je n'ai rien à faire" |
| **Suggestion** | Semaine 1-2 | Suggère des actions, messages pré-rédigés | "C'est un bon assistant" |
| **Décision** | Mois 1-2 | "J'ai préparé le message. Envoyer?" | "Je valide, mais c'est moi qui décide" |
| **Contrôle** | Mois 2+ | Spider gère, le dirigeant valide | "Je ne sais plus faire sans" |

**Point de non-retour :** Quand le dirigeant ne sait plus faire sans Spider, le lock-in est total. Pas par contrat — par dépendance.

---

### Vision Long Terme

| Horizon | Vision | Implication |
|---------|--------|-------------|
| **Y1-2** | Spider s'infiltre dans les PME | Prouver la valeur, atteindre le point de non-retour |
| **Y3-5** | Spider a la vraie data de milliers de PME | Intelligence cross-entreprises, benchmarks, signaux |
| **Y5-10** | Spider devient la source de vérité PME Europe | Valeur M&A massive, position de pouvoir unique |
| **Vision ultime** | Le système d'exploitation de l'économie européenne | 25M de PME connectées, gouvernées, dépendantes |

---

### Notes en vrac (à creuser)

**Sur Drakkar comme cheval de Troie :**
- Drakkar = la face visible, respectable, "agence de transformation digitale"
- SpiderOS = l'infrastructure réelle, le vrai business
- Drakkar sert à entrer chez les clients, à avoir la légitimité terrain
- Une fois Spider installé, Drakkar devient optionnel

**Sur le timing 2025-2027 :**
- L'IA générative est mature mais pas encore commoditisée
- Les PME commencent à comprendre qu'il faut y aller mais ne savent pas comment
- Fenêtre avant que les gros (Microsoft, Google, Salesforce) ne verrouillent le marché

**Sur l'Europe vs US :**
- L'Europe n'a pas son champion SaaS B2B pour PME
- Les outils US sont inadaptés culturellement
- First mover advantage sur un marché de 25M d'entreprises

**Sur les hypothèses à valider :**
- Est-ce que les dirigeants acceptent vraiment de connecter leurs données sensibles ?
- Est-ce que la qualité IA est suffisante pour ne pas perdre leur confiance ?
- Est-ce que la dépendance se crée vraiment comme prévu ?

---

### Facts vs Hypothèses vs Paris

| Type | Statement |
|------|-----------|
| **Fact** | 25M de PME en Europe |
| **Fact** | L'IA générative est mature et accessible |
| **Fact** | La vague de transmission baby-boomer est réelle |
| **Hypothèse** | Les dirigeants PME veulent déléguer les décisions |
| **Hypothèse** | La culture européenne est incompatible avec les CRM américains |
| **Hypothèse** | La data agrégée PME a une valeur massive |
| **Pari** | On peut créer une dépendance sans que le dirigeant s'en rende compte |
| **Pari** | Le timing 2025-2027 est le bon |
| **Pari** | On peut atteindre une position dominante avant que les gros réagissent |

---

**Document rédigé le 2026-01-15**

*En attente de validation finale*

*Created using BMAD Method v6 — Product Brief workflow*
