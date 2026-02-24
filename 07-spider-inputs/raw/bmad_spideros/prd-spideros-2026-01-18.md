# Product Requirements Document: SpiderOS

**Date:** 2026-01-18
**Author:** Nathan Menard
**Version:** 1.0
**Project Type:** web-app
**Project Level:** 4 (40+ stories)
**Status:** Draft

---

## Document Overview

This Product Requirements Document (PRD) defines the functional and non-functional requirements for SpiderOS. It serves as the source of truth for what will be built and provides traceability from requirements through implementation.

**Related Documents:**
- Product Brief: `docs/product-brief.md`
- Brainstorming Spider Memory: `docs/brainstorming/spider-memory.md`
- Brainstorming Spider People: `docs/brainstorming/spider-people.md`
- Brainstorming Spider Builder: `docs/brainstorming/spider-builder.md`
- Brainstorming Spider Content: `docs/brainstorming/spider-content.md`

---

## Executive Summary

L'IA ne voit pas votre entreprise. Vos vraies donnees sont eparpillees : mails, fichiers, tetes des equipes. **SpiderOS** tisse une toile par-dessus — sans migration. L'IA voit enfin. Des modules s'y branchent pour automatiser : standards ou sur mesure.

SpiderOS est un moteur (desktop + mobile) qui :
1. **Se connecte** a tout automatiquement (mail, telephone, fichiers, apps)
2. **Detecte** et agrege la data eparpillee
3. **Tisse une toile** entre toutes les sources
4. **Permet des automatisations** par-dessus

**Zero setup.** L'IA detecte, l'IA s'adapte.

---

## Product Goals

### Business Objectives

| Objectif | Cible Year 1 (2026) |
|----------|---------------------|
| **Prouver le concept** | Technologie "toile" validee sur cas reels |
| **Modules live** | 5-6 modules fonctionnels |
| **Clients payants** | 10 (hors Drakkar) |
| **ARR** | 100K EUR minimum |
| **Dogfooding** | Drakkar utilise Spider quotidiennement |

### Success Metrics

| Critere | Cible | Comment on mesure |
|---------|-------|-------------------|
| Clients payants | 10 (hors Drakkar) | Contrats signes |
| ARR | 100K EUR minimum | MRR x 12 |
| Dogfooding Drakkar | 100% de l'equipe utilise Spider | Usage actif |
| Modules live | 5-6 modules fonctionnels | En production, utilises |
| La toile fonctionne | Data connectee et exploitable | Recherches cross-sources |
| Fiabilite extraction IA | >80% de precision | Audit qualite data |
| Adoption sans friction | Onboarding < 10 min | Time-to-value mesure |
| Taux completion onboarding | > 70% | Analytics |
| Pricing valide | 5+ clients a 49 EUR/user | Contrats |

---

## Functional Requirements

Functional Requirements (FRs) define **what** the system does - specific features and behaviors.

Each requirement includes:
- **ID**: Unique identifier (FR-001, FR-002, etc.)
- **Priority**: Must Have / Should Have / Could Have / Won't Have (MoSCoW)
- **Description**: What the system should do
- **Acceptance Criteria**: How to verify it's complete

---

### Spider Memory (Infrastructure)

### FR-001: Stockage Vectoriel Massif

**Priority:** Must Have

**Description:**
Spider Memory doit pouvoir stocker et indexer des millions de documents (emails, transcriptions, fichiers) sous forme vectorisee pour permettre des recherches semantiques rapides.

**Acceptance Criteria:**
- [ ] Support de 10+ ans d'historique email par tenant
- [ ] Indexation incrementale des nouveaux documents
- [ ] Schema multi-tenant avec isolation des donnees
- [ ] Support LanceDB comme moteur vectoriel

**Dependencies:** None

---

### FR-002: Recherche Semantique Performante

**Priority:** Must Have

**Description:**
Les modules doivent pouvoir effectuer des recherches semantiques sur les donnees vectorisees avec un temps de reponse inferieur a 500ms.

**Acceptance Criteria:**
- [ ] Temps de reponse < 500ms pour 95% des requetes
- [ ] Support de requetes en langage naturel ("contacts avec resistance prix")
- [ ] Ranking par pertinence
- [ ] Filtrage par metadata (date, source, contact)

**Dependencies:** FR-001

---

### FR-003: API Memory pour Modules

**Priority:** Must Have

**Description:**
Spider Memory expose une API interne que les modules (People, Builder, Chatbot, Content) appellent pour indexer et rechercher des donnees.

**Acceptance Criteria:**
- [ ] API REST documentee
- [ ] Endpoints: index, search, delete
- [ ] Authentification module-to-module
- [ ] Rate limiting par module

**Dependencies:** FR-001

---

### FR-004: Score de Confiance par Donnee

**Priority:** Must Have

**Description:**
Chaque information extraite par l'IA doit avoir un score de confiance (0-100%) visible par l'utilisateur pour eviter les erreurs embarrassantes.

**Acceptance Criteria:**
- [ ] Score calcule a l'extraction
- [ ] Score visible dans l'UI
- [ ] Seuil configurable pour demande de validation
- [ ] Decay temporel si donnee pas validee

**Dependencies:** FR-005

---

### FR-005: Extraction et Structuration Automatique

**Priority:** Must Have

**Description:**
Spider Memory doit extraire automatiquement des informations structurees depuis les sources brutes (emails, transcriptions, documents).

**Acceptance Criteria:**
- [ ] Extraction entites nommees (noms, entreprises, lieux)
- [ ] Extraction dates et evenements
- [ ] Extraction promesses et engagements
- [ ] Extraction informations personnelles (famille, passions)
- [ ] Precision > 80%

**Dependencies:** FR-001

---

### FR-006: Memory Dashboard (Transparence)

**Priority:** Should Have

**Description:**
L'utilisateur peut voir tout ce que Spider Memory sait sur lui ou ses contacts, avec possibilite de corriger ou supprimer des informations.

**Acceptance Criteria:**
- [ ] Vue centralisee de toutes les donnees par contact
- [ ] Filtres par source, date, type
- [ ] Edition inline des donnees
- [ ] Historique des modifications

**Dependencies:** FR-001, FR-004

---

### FR-007: Systeme de Validation Flashcards

**Priority:** Should Have

**Description:**
Les donnees avec un score de confiance faible sont presentees a l'utilisateur sous forme de flashcards (swipe) pour validation rapide.

**Acceptance Criteria:**
- [ ] Interface swipe (valider/invalider)
- [ ] Maximum 5-10 validations par jour
- [ ] Feedback loop pour ameliorer le modele
- [ ] Priorisation par importance de la donnee

**Dependencies:** FR-004

---

### FR-008: Mode Oublie-Moi

**Priority:** Should Have

**Description:**
L'utilisateur peut demander la suppression de donnees specifiques ou de toutes les donnees d'un contact (conformite RGPD).

**Acceptance Criteria:**
- [ ] Bouton "Supprimer ces donnees" par element
- [ ] Bouton "Oublier ce contact" global
- [ ] Confirmation avant suppression
- [ ] Suppression effective < 30 jours

**Dependencies:** FR-006

---

### FR-009: Recherche Cross-Modules

**Priority:** Could Have

**Description:**
Une recherche unifiee permet de trouver des informations dans tous les modules (People, Builder, Chatbot) depuis une seule interface.

**Acceptance Criteria:**
- [ ] Barre de recherche globale
- [ ] Resultats groupes par module
- [ ] Liens directs vers les elements trouves

**Dependencies:** FR-002, FR-003

---

### Spider People (CRM Relationnel)

### FR-010: Capture Automatique Emails

**Priority:** Must Have

**Description:**
Spider People capture automatiquement tous les emails envoyes et recus via l'integration Gmail, sans action de l'utilisateur.

**Acceptance Criteria:**
- [ ] Connexion OAuth Gmail
- [ ] Sync initial de l'historique (configurable: 1 an, 5 ans, tout)
- [ ] Sync incrementale en temps reel
- [ ] Extraction du contenu et metadata

**Dependencies:** FR-048

---

### FR-011: Capture Automatique Calls

**Priority:** Must Have

**Description:**
Spider People capture automatiquement les appels telephoniques via Aircall ou Noota, avec transcription.

**Acceptance Criteria:**
- [ ] Integration Aircall API
- [ ] Integration Noota API
- [ ] Recuperation des transcriptions
- [ ] Association automatique au contact

**Dependencies:** FR-050, FR-051

---

### FR-012: Capture Automatique Calendrier

**Priority:** Must Have

**Description:**
Spider People capture les evenements du calendrier Google pour alimenter le contexte relationnel.

**Acceptance Criteria:**
- [ ] Connexion OAuth Google Calendar
- [ ] Sync des evenements passes et futurs
- [ ] Detection des participants
- [ ] Association aux contacts

**Dependencies:** FR-049

---

### FR-013: Attribution Automatique aux Contacts

**Priority:** Must Have

**Description:**
Chaque email, call ou evenement est automatiquement attribue au bon contact dans Spider People.

**Acceptance Criteria:**
- [ ] Matching par email
- [ ] Matching par numero de telephone
- [ ] Gestion des alias
- [ ] Precision > 90%

**Dependencies:** FR-010, FR-011, FR-012

---

### FR-014: Creation Automatique Fiches Contacts

**Priority:** Must Have

**Description:**
Quand un nouveau contact est detecte (email, call), une fiche est automatiquement creee et enrichie.

**Acceptance Criteria:**
- [ ] Detection de nouveau contact
- [ ] Creation fiche avec infos de base
- [ ] Enrichissement via extraction (FR-005)
- [ ] Pas de doublons

**Dependencies:** FR-013, FR-005

---

### FR-015: Score de Connaissance

**Priority:** Must Have

**Description:**
Chaque contact a un score de connaissance (0-100%) qui indique a quel point l'utilisateur connait cette personne, sur 4 niveaux : Surface, Comportement, Motivations, Vulnerabilites.

**Acceptance Criteria:**
- [ ] Score calcule automatiquement
- [ ] Affichage visuel (jauge, pourcentage)
- [ ] Detail par dimension
- [ ] Suggestions pour ameliorer le score

**Dependencies:** FR-005, FR-004

---

### FR-016: Brief Avant RDV

**Priority:** Must Have

**Description:**
Avant un RDV, l'utilisateur recoit un resume automatique du contact : derniers echanges, infos cles, points a creuser.

**Acceptance Criteria:**
- [ ] Notification push avant le RDV (configurable: 30min, 1h)
- [ ] Resume genere en < 3 secondes
- [ ] Derniers echanges (emails, calls)
- [ ] Infos cles extraites
- [ ] Suggestions de sujets a aborder

**Dependencies:** FR-005, FR-012

---

### FR-017: Inbox Filtree Intelligente

**Priority:** Must Have

**Description:**
Spider People filtre les messages entrants et met en avant les 5-10 plus importants, au lieu de 80 emails non tries.

**Acceptance Criteria:**
- [ ] Algorithme de priorisation (VIP, deals, urgence)
- [ ] Vue "A traiter" avec les priorites
- [ ] Vue "Tout" avec l'historique complet
- [ ] Marquage "traite"

**Dependencies:** FR-010

---

### FR-018: Messages Suggeres Pre-Rediges

**Priority:** Must Have

**Description:**
Spider People suggere des messages pre-rediges bases sur le contexte du contact et l'historique des echanges.

**Acceptance Criteria:**
- [ ] Suggestion de reponse contextuelle
- [ ] Ton adapte au contact
- [ ] Edition avant envoi
- [ ] Envoi en 1 clic

**Dependencies:** FR-005, FR-015

---

### FR-019: Alertes Contacts Qui Refroidissent

**Priority:** Should Have

**Description:**
Spider People alerte l'utilisateur quand un contact important n'a pas ete contacte depuis longtemps (configurable).

**Acceptance Criteria:**
- [ ] Seuils configurables par priorite (VIP: 1 mois, Important: 3 mois, Normal: 1 an)
- [ ] Notification avec pretexte de reprise
- [ ] Historique des alertes

**Dependencies:** FR-015

---

### FR-020: Alertes Anniversaires et Evenements

**Priority:** Should Have

**Description:**
Spider People alerte l'utilisateur des anniversaires et evenements importants de ses contacts.

**Acceptance Criteria:**
- [ ] Detection anniversaires (extraction)
- [ ] Detection evenements (changement de poste, etc.)
- [ ] Notification avec suggestion de message
- [ ] Score de confiance sur la date

**Dependencies:** FR-005, FR-004

---

### FR-021: Extraction Profil Psychologique

**Priority:** Should Have

**Description:**
Spider People extrait un profil psychologique du contact (DISC, Big Five) depuis l'analyse des conversations.

**Acceptance Criteria:**
- [ ] Detection traits de personnalite
- [ ] Affichage framework au choix (DISC, MBTI, Big Five)
- [ ] Precision ~80%
- [ ] Mise a jour incrementale

**Dependencies:** FR-005

---

### FR-022: Sync Bidirectionnelle CRM

**Priority:** Should Have

**Description:**
Spider People se synchronise avec le CRM existant (Odoo) de maniere bidirectionnelle.

**Acceptance Criteria:**
- [ ] Integration Odoo API
- [ ] Sync contacts, deals, notes
- [ ] Gestion des conflits
- [ ] Mapping des champs configurable

**Dependencies:** FR-052

---

### FR-023: Cloisonnement Donnees par Role

**Priority:** Must Have

**Description:**
Les donnees sont cloisonnees par utilisateur et role : un commercial ne voit que ses contacts, un manager voit son equipe, un dirigeant voit tout.

**Acceptance Criteria:**
- [ ] Isolation par defaut
- [ ] Roles: Commercial, Manager, Dirigeant
- [ ] Partage explicite possible
- [ ] Audit trail des acces

**Dependencies:** FR-056

---

### FR-024: Mode Ghost (Contacts Prives)

**Priority:** Should Have

**Description:**
L'utilisateur peut marquer des contacts comme "prives" (famille, amis) qui ne sont visibles que par lui, meme pour un manager.

**Acceptance Criteria:**
- [ ] Flag "prive" par contact
- [ ] Invisible pour les autres utilisateurs
- [ ] Pas d'export dans les rapports
- [ ] Exclusion des stats

**Dependencies:** FR-023

---

### FR-025: Playbook Auto-Detecte

**Priority:** Could Have

**Description:**
Spider People detecte automatiquement le process de vente (etapes, questions qui marchent, objections) depuis l'analyse des deals.

**Acceptance Criteria:**
- [ ] Detection des etapes recurrentes
- [ ] Extraction des questions efficaces
- [ ] Capture des objections et reponses
- [ ] Playbook editable

**Dependencies:** FR-005, FR-011

---

### FR-026: Coaching Post-Call

**Priority:** Could Have

**Description:**
Apres un call, Spider People fournit un feedback automatique : ce qui a ete bien fait, ce qui a ete oublie vs le playbook.

**Acceptance Criteria:**
- [ ] Analyse automatique de la transcription
- [ ] Comparaison vs playbook
- [ ] Suggestions d'amelioration
- [ ] Historique des feedbacks

**Dependencies:** FR-025, FR-011

---

### FR-027: Dashboard Activite Equipe

**Priority:** Could Have

**Description:**
Le manager peut voir l'activite de son equipe sans demander : calls, emails, deals en cours.

**Acceptance Criteria:**
- [ ] Vue equipe aggregee
- [ ] Metriques par commercial
- [ ] Filtres par periode
- [ ] Respect du cloisonnement (FR-023)

**Dependencies:** FR-023

---

### FR-028: Capture WhatsApp (Mac)

**Priority:** Should Have

**Description:**
Spider People capture les messages WhatsApp via l'app desktop Mac.

**Acceptance Criteria:**
- [ ] Integration WhatsApp Web/Desktop
- [ ] Capture en background
- [ ] Attribution aux contacts
- [ ] Support images et documents

**Dependencies:** Desktop Mac (P1)

---

### Spider Builder (AI Coding)

### FR-029: Wizard Onboarding Projet

**Priority:** Must Have

**Description:**
Spider Builder guide l'utilisateur a travers un wizard de questions pour definir le projet avant de coder.

**Acceptance Criteria:**
- [ ] Questions sur les objectifs
- [ ] Questions sur les contraintes techniques
- [ ] Questions sur le design
- [ ] Generation des outputs (PRD, archi, regles)

**Dependencies:** None

---

### FR-030: Generation PRD Automatique (BMAD)

**Priority:** Must Have

**Description:**
Spider Builder genere automatiquement un PRD depuis les inputs du wizard onboarding, en utilisant la methodologie BMAD.

**Acceptance Criteria:**
- [ ] PRD structure (objectifs, FRs, NFRs)
- [ ] Format Markdown
- [ ] Editable par l'utilisateur
- [ ] Versionning

**Dependencies:** FR-029

---

### FR-031: Generation Architecture Automatique

**Priority:** Must Have

**Description:**
Spider Builder genere automatiquement une architecture technique depuis le PRD.

**Acceptance Criteria:**
- [ ] Diagrammes (composants, data)
- [ ] Stack technique
- [ ] Structure de fichiers
- [ ] Format Markdown

**Dependencies:** FR-030

---

### FR-032: Stack Selector

**Priority:** Must Have

**Description:**
Spider Builder permet de selectionner et verrouiller les librairies approuvees pour le projet.

**Acceptance Criteria:**
- [ ] Liste des libs approuvees
- [ ] Selection par categorie
- [ ] Verrouillage des versions
- [ ] Alerte si lib non approuvee utilisee

**Dependencies:** None

---

### FR-033: Rules Config Projet

**Priority:** Must Have

**Description:**
Spider Builder permet de definir et editer les regles du projet (conventions, patterns, interdictions).

**Acceptance Criteria:**
- [ ] Editeur de regles
- [ ] Templates de regles par type de projet
- [ ] Export/import des regles
- [ ] Application automatique aux prompts

**Dependencies:** None

---

### FR-034: Stack Guard

**Priority:** Must Have

**Description:**
Spider Builder bloque ou alerte si l'IA tente d'utiliser une librairie non approuvee.

**Acceptance Criteria:**
- [ ] Detection a la generation de code
- [ ] Alerte visuelle
- [ ] Suggestion d'alternative approuvee
- [ ] Override possible avec justification

**Dependencies:** FR-032

---

### FR-035: Design System Guard

**Priority:** Should Have

**Description:**
Spider Builder verifie que le code UI genere respecte le design system defini.

**Acceptance Criteria:**
- [ ] Verification des composants utilises
- [ ] Verification des couleurs/styles
- [ ] Alerte si ecart
- [ ] Suggestion de correction

**Dependencies:** FR-033

---

### FR-036: Loop Detection

**Priority:** Should Have

**Description:**
Spider Builder detecte quand l'IA tourne en boucle sans resoudre un probleme et alerte l'utilisateur.

**Acceptance Criteria:**
- [ ] Detection de patterns repetitifs
- [ ] Alerte apres N iterations
- [ ] Suggestion d'intervention humaine
- [ ] Log des boucles pour debug

**Dependencies:** None

---

### FR-037: US Auto-Link

**Priority:** Should Have

**Description:**
Spider Builder lie automatiquement le code genere aux user stories correspondantes.

**Acceptance Criteria:**
- [ ] Detection de l'US active
- [ ] Marquage du code genere
- [ ] Vue tracabilite code ↔ US
- [ ] Mise a jour du statut US

**Dependencies:** FR-030

---

### FR-038: Progress Tracking Automatique

**Priority:** Should Have

**Description:**
Spider Builder met a jour automatiquement l'avancement du projet (US, epics, sprints).

**Acceptance Criteria:**
- [ ] Calcul automatique de l'avancement
- [ ] Fichiers YAML/JSON mis a jour
- [ ] Vue kanban optionnelle
- [ ] Historique

**Dependencies:** FR-037

---

### FR-039: Agent Visibility

**Priority:** Could Have

**Description:**
L'utilisateur peut voir quels agents BMAD interviennent et pourquoi.

**Acceptance Criteria:**
- [ ] Liste des agents actifs
- [ ] Log des decisions
- [ ] Explication des choix
- [ ] Override possible

**Dependencies:** None

---

### FR-040: Proxy Localhost Enrichissement

**Priority:** Must Have

**Description:**
Spider Builder fonctionne comme un proxy localhost qui enrichit automatiquement les prompts envoyes a Claude Code avec le contexte projet (PRD, archi, design system, US active).

**Acceptance Criteria:**
- [ ] Proxy transparent (1 config)
- [ ] Injection du contexte pertinent
- [ ] Pas de degradation de latence significative
- [ ] Logging des enrichissements

**Dependencies:** FR-030, FR-031, FR-033

---

### Spider Content (Generation Contenu)

### FR-041: Generation Photos Produit

**Priority:** Must Have

**Description:**
Spider Content genere des photos produit professionnelles a partir d'images existantes ou de descriptions.

**Acceptance Criteria:**
- [ ] Upload d'images produit
- [ ] Generation de variantes (fond, angle, style)
- [ ] Qualite professionnelle (utilisable catalogue)
- [ ] Export haute resolution

**Dependencies:** None

---

### FR-042: Generation Videos UGC/Avatars

**Priority:** Must Have

**Description:**
Spider Content genere des videos UGC avec avatars IA pour les reseaux sociaux.

**Acceptance Criteria:**
- [ ] Selection d'avatar
- [ ] Script textuel ou vocal
- [ ] Multi-langues
- [ ] Export formats reseaux sociaux

**Dependencies:** None

---

### FR-043: Systeme Brand Kit

**Priority:** Must Have

**Description:**
Spider Content extrait et stocke la charte graphique (couleurs, logos, polices) depuis une URL ou des fichiers.

**Acceptance Criteria:**
- [ ] Extraction depuis URL
- [ ] Upload manuel
- [ ] Stockage brand kit par client
- [ ] Application automatique aux generations

**Dependencies:** None

---

### FR-044: Extraction Catalogue E-commerce

**Priority:** Should Have

**Description:**
Spider Content extrait automatiquement le catalogue produit depuis un site e-commerce pour faciliter les generations.

**Acceptance Criteria:**
- [ ] Crawl de pages produit
- [ ] Extraction images, titres, descriptions
- [ ] Stockage structure
- [ ] Selection pour generation

**Dependencies:** None

---

### FR-045: Multi-Langues

**Priority:** Should Have

**Description:**
Spider Content genere du contenu dans plusieurs langues (FR, EN, ES, DE minimum).

**Acceptance Criteria:**
- [ ] Selection de langue cible
- [ ] Qualite equivalente toutes langues
- [ ] Adaptation culturelle
- [ ] Voix natives pour video

**Dependencies:** FR-042

---

### FR-046: Animation Mascotte/Personnage Fictif

**Priority:** Could Have

**Description:**
Spider Content permet d'animer une mascotte ou un personnage fictif pour des videos explicatives.

**Acceptance Criteria:**
- [ ] Import de mascotte/personnage
- [ ] Animation lip-sync
- [ ] Expressions configurables
- [ ] Export video

**Dependencies:** FR-042

---

### FR-047: Templates Prets a l'Emploi

**Priority:** Should Have

**Description:**
Spider Content propose des templates de contenu prets a l'emploi pour les debutants.

**Acceptance Criteria:**
- [ ] Bibliotheque de templates
- [ ] Categories (reseaux sociaux, email, catalogue)
- [ ] Personnalisation facile
- [ ] Preview avant generation

**Dependencies:** None

---

### Integrations P0

### FR-048: Integration Gmail

**Priority:** Must Have

**Description:**
Spider People se connecte a Gmail via OAuth pour capturer les emails.

**Acceptance Criteria:**
- [ ] OAuth 2.0 Google
- [ ] Sync initiale configurable
- [ ] Sync incrementale temps reel
- [ ] Gestion des erreurs/deconnexions

**Dependencies:** None

---

### FR-049: Integration Google Calendar

**Priority:** Must Have

**Description:**
Spider People se connecte a Google Calendar via OAuth pour capturer les evenements.

**Acceptance Criteria:**
- [ ] OAuth 2.0 Google
- [ ] Sync bidirectionnelle
- [ ] Detection participants
- [ ] Alertes avant RDV

**Dependencies:** None

---

### FR-050: Integration Aircall

**Priority:** Must Have

**Description:**
Spider People se connecte a Aircall pour capturer les appels et transcriptions.

**Acceptance Criteria:**
- [ ] API Aircall
- [ ] Recuperation historique calls
- [ ] Transcriptions automatiques
- [ ] Webhooks temps reel

**Dependencies:** None

---

### FR-051: Integration Noota

**Priority:** Must Have

**Description:**
Spider People se connecte a Noota pour recuperer les transcriptions de meetings.

**Acceptance Criteria:**
- [ ] API Noota
- [ ] Recuperation transcriptions
- [ ] Association aux contacts
- [ ] Sync automatique

**Dependencies:** None

---

### FR-052: Integration Odoo

**Priority:** Should Have

**Description:**
Spider People se synchronise avec Odoo CRM de maniere bidirectionnelle.

**Acceptance Criteria:**
- [ ] API Odoo
- [ ] Sync contacts, deals, notes
- [ ] Gestion conflits
- [ ] Mapping configurable

**Dependencies:** None

---

### Plateforme Core

### FR-053: Authentification Utilisateurs

**Priority:** Must Have

**Description:**
SpiderOS gere l'authentification des utilisateurs avec support OAuth et SSO.

**Acceptance Criteria:**
- [ ] Login email/password
- [ ] OAuth Google
- [ ] SSO (SAML) pour enterprise
- [ ] 2FA optionnel

**Dependencies:** None

---

### FR-054: Onboarding Guide

**Priority:** Must Have

**Description:**
SpiderOS guide les nouveaux utilisateurs a travers un onboarding en moins de 10 minutes.

**Acceptance Criteria:**
- [ ] Wizard step-by-step
- [ ] Connexion des sources (email, calendar, calls)
- [ ] Premier contact enrichi visible rapidement
- [ ] Completion < 10 minutes

**Dependencies:** FR-048, FR-049, FR-050

---

### FR-055: Gestion Multi-Tenant

**Priority:** Must Have

**Description:**
SpiderOS supporte plusieurs organisations (tenants) avec isolation complete des donnees.

**Acceptance Criteria:**
- [ ] Creation de tenant
- [ ] Isolation des donnees stricte
- [ ] Gestion des utilisateurs par tenant
- [ ] Facturation par tenant

**Dependencies:** None

---

### FR-056: Gestion Droits et Roles

**Priority:** Must Have

**Description:**
SpiderOS gere les droits et roles des utilisateurs (Admin, Manager, User).

**Acceptance Criteria:**
- [ ] Roles configurables
- [ ] Permissions granulaires
- [ ] Invitation d'utilisateurs
- [ ] Audit trail

**Dependencies:** FR-055

---

### FR-057: Systeme de Credits

**Priority:** Should Have

**Description:**
Spider Content et Spider Builder fonctionnent avec un systeme de credits (modele Lovable-style).

**Acceptance Criteria:**
- [ ] Compteur de credits par tenant
- [ ] Decompte a l'usage
- [ ] Packs de credits a acheter
- [ ] Alertes seuil bas

**Dependencies:** FR-055

---

### FR-058: Extension Chrome

**Priority:** Should Have

**Description:**
Une extension Chrome permet de capturer des informations depuis le web (LinkedIn, sites entreprise).

**Acceptance Criteria:**
- [ ] Installation Chrome Web Store
- [ ] Capture profil LinkedIn
- [ ] Enrichissement contact
- [ ] Sync avec Spider People

**Dependencies:** FR-014

---

### FR-059: Hebergement Cloud EU

**Priority:** Must Have

**Description:**
SpiderOS est heberge sur un cloud europeen pour conformite RGPD et souverainete.

**Acceptance Criteria:**
- [ ] Provider cloud EU (Scaleway)
- [ ] Donnees en France
- [ ] Certifications RGPD
- [ ] Documentation compliance

**Dependencies:** None

---

### Marketing & Site Web

### FR-060: Homepage SpiderOS

**Priority:** Must Have

**Description:**
Le site web SpiderOS presente le produit, la proposition de valeur et les modules.

**Acceptance Criteria:**
- [ ] Hero section avec messaging clair
- [ ] Presentation des modules
- [ ] Temoignages/social proof
- [ ] CTA vers demo/signup

**Dependencies:** None

---

### FR-061: Pages Modules

**Priority:** Must Have

**Description:**
Chaque module (People, Builder, Content) a sa page dediee avec features, pricing, et CTA.

**Acceptance Criteria:**
- [ ] Page Spider People
- [ ] Page Spider Builder
- [ ] Page Spider Content
- [ ] Features detaillees
- [ ] Screenshots/demos

**Dependencies:** FR-060

---

### FR-062: Page Pricing

**Priority:** Must Have

**Description:**
Une page pricing presente les tarifs de chaque module et les packs de credits.

**Acceptance Criteria:**
- [ ] Pricing Spider People (49 EUR/user/mois)
- [ ] Pricing Spider Builder (credits)
- [ ] Pricing Spider Content (credits)
- [ ] Comparaison des plans
- [ ] FAQ pricing

**Dependencies:** FR-060

---

### FR-063: Formulaire Contact/Demo

**Priority:** Should Have

**Description:**
Un formulaire permet aux prospects de demander une demo ou de contacter l'equipe.

**Acceptance Criteria:**
- [ ] Formulaire avec champs essentiels
- [ ] Notification email a l'equipe
- [ ] Confirmation au prospect
- [ ] Integration CRM

**Dependencies:** FR-060

---

### FR-064: Blog/Ressources

**Priority:** Could Have

**Description:**
Un blog ou section ressources pour le content marketing (SEO, education).

**Acceptance Criteria:**
- [ ] CMS integre
- [ ] Categories (product, use cases, guides)
- [ ] SEO optimise
- [ ] Partage social

**Dependencies:** FR-060

---

## Non-Functional Requirements

Non-Functional Requirements (NFRs) define **how** the system performs - quality attributes and constraints.

---

### Performance

### NFR-001: Recherche Semantique Memory

**Priority:** Must Have

**Description:**
Les recherches semantiques dans Spider Memory doivent repondre rapidement.

**Acceptance Criteria:**
- [ ] Temps de reponse < 500ms pour 95% des requetes
- [ ] Support de requetes complexes (multi-criteres)
- [ ] Pas de degradation avec le volume

**Rationale:**
La performance est critique pour l'UX (brief avant RDV, suggestions temps reel).

---

### NFR-002: Brief Avant RDV

**Priority:** Must Have

**Description:**
Le brief avant RDV doit etre genere rapidement.

**Acceptance Criteria:**
- [ ] Generation en < 3 secondes
- [ ] Disponible dans la notification push

**Rationale:**
L'utilisateur consulte le brief juste avant le RDV, la latence doit etre minimale.

---

### NFR-003: Temps de Chargement Pages

**Priority:** Must Have

**Description:**
Les pages web de l'application doivent charger rapidement.

**Acceptance Criteria:**
- [ ] LCP (Largest Contentful Paint) < 2 secondes
- [ ] TTI (Time to Interactive) < 3 secondes

**Rationale:**
UX et SEO dependent de la performance web.

---

### NFR-004: Onboarding Completion

**Priority:** Must Have

**Description:**
L'onboarding doit pouvoir etre complete rapidement.

**Acceptance Criteria:**
- [ ] Completion possible en < 10 minutes
- [ ] Minimum de frictions

**Rationale:**
Critical pour l'adoption - les PME n'ont pas de temps.

---

### Fiabilite / Precision IA

### NFR-005: Precision Extraction Donnees

**Priority:** Must Have

**Description:**
L'extraction automatique de donnees par l'IA doit etre fiable.

**Acceptance Criteria:**
- [ ] Precision > 80% sur les entites (noms, dates, lieux)
- [ ] Precision > 70% sur les promesses et engagements
- [ ] Precision ~80% sur le profil psychologique

**Rationale:**
Si l'IA se trompe trop, perte de confiance totale.

---

### NFR-006: Attribution Contacts

**Priority:** Must Have

**Description:**
L'attribution automatique des communications aux contacts doit etre precise.

**Acceptance Criteria:**
- [ ] Precision > 90% sur l'attribution
- [ ] Detection et gestion des alias

**Rationale:**
Des erreurs d'attribution rendent le CRM inutilisable.

---

### NFR-007: Transcription Calls

**Priority:** Should Have

**Description:**
La transcription des appels doit etre de qualite suffisante.

**Acceptance Criteria:**
- [ ] WER (Word Error Rate) < 10% en conditions reelles
- [ ] Support du francais natif

**Rationale:**
La transcription alimente l'extraction et le coaching.

---

### NFR-008: Disponibilite Systeme

**Priority:** Must Have

**Description:**
SpiderOS doit etre disponible de maniere fiable.

**Acceptance Criteria:**
- [ ] Uptime 99.5% (hors maintenance planifiee)
- [ ] Maintenance planifiee hors heures ouvrables EU

**Rationale:**
SpiderOS devient critique pour les operations quotidiennes.

---

### Securite / RGPD

### NFR-009: Hebergement Donnees

**Priority:** Must Have

**Description:**
Les donnees doivent etre hebergees en Europe.

**Acceptance Criteria:**
- [ ] Serveurs en France (Scaleway)
- [ ] Pas de transfert hors UE
- [ ] Documentation compliance

**Rationale:**
Conformite RGPD et souverainete.

---

### NFR-010: Chiffrement Donnees

**Priority:** Must Have

**Description:**
Les donnees doivent etre chiffrees en transit et au repos.

**Acceptance Criteria:**
- [ ] TLS 1.3 pour les communications
- [ ] Chiffrement AES-256 au repos
- [ ] Gestion des cles securisee

**Rationale:**
Protection des donnees sensibles (emails, calls).

---

### NFR-011: Authentification

**Priority:** Must Have

**Description:**
L'authentification doit etre securisee et flexible.

**Acceptance Criteria:**
- [ ] OAuth 2.0 standard
- [ ] Support SSO (SAML) pour enterprise
- [ ] 2FA optionnel

**Rationale:**
Securite et compatibilite enterprise.

---

### NFR-012: Isolation Multi-Tenant

**Priority:** Must Have

**Description:**
Les donnees de chaque tenant doivent etre strictement isolees.

**Acceptance Criteria:**
- [ ] Isolation au niveau base de donnees
- [ ] Pas de leak possible entre tenants
- [ ] Tests de penetration valides

**Rationale:**
Confidentialite critique pour clients B2B.

---

### NFR-013: Droit a l'Oubli RGPD

**Priority:** Must Have

**Description:**
Les utilisateurs peuvent demander la suppression de leurs donnees.

**Acceptance Criteria:**
- [ ] Suppression effective < 30 jours sur demande
- [ ] Documentation du processus
- [ ] Confirmation au demandeur

**Rationale:**
Conformite RGPD.

---

### NFR-014: Consentement Capture

**Priority:** Must Have

**Description:**
La capture de donnees (emails, calls) requiert un consentement explicite.

**Acceptance Criteria:**
- [ ] Consentement a l'onboarding
- [ ] Information claire sur ce qui est capture
- [ ] Possibilite de revoquer

**Rationale:**
Conformite RGPD et transparence.

---

### Scalabilite

### NFR-015: Volume Emails par Tenant

**Priority:** Should Have

**Description:**
Le systeme doit supporter de gros volumes d'emails historiques.

**Acceptance Criteria:**
- [ ] Support 10+ ans d'historique
- [ ] Millions d'emails par tenant
- [ ] Pas de degradation de performance

**Rationale:**
Les dirigeants ont souvent 10+ ans d'historique email.

---

### NFR-016: Contacts par Tenant

**Priority:** Should Have

**Description:**
Le systeme doit supporter un grand nombre de contacts.

**Acceptance Criteria:**
- [ ] Jusqu'a 50,000 contacts par tenant
- [ ] Recherche et filtres rapides

**Rationale:**
Gros clients PME/ETI avec beaucoup de contacts.

---

### NFR-017: Utilisateurs Simultanes

**Priority:** Should Have

**Description:**
Le systeme doit supporter plusieurs utilisateurs simultanement.

**Acceptance Criteria:**
- [ ] 100 utilisateurs par tenant sans degradation
- [ ] Pas de conflits de donnees

**Rationale:**
Equipes commerciales de 10-50 personnes.

---

### Usabilite

### NFR-018: Formation Requise

**Priority:** Must Have

**Description:**
Le produit doit etre utilisable sans formation.

**Acceptance Criteria:**
- [ ] Zero formation requise
- [ ] UX auto-explicative
- [ ] Tooltips et aide contextuelle

**Rationale:**
Les PME ne forment pas leurs equipes.

---

### NFR-019: Taux Completion Onboarding

**Priority:** Must Have

**Description:**
L'onboarding doit avoir un bon taux de completion.

**Acceptance Criteria:**
- [ ] Taux de completion > 70%
- [ ] Tracking des abandons

**Rationale:**
Critique pour l'adoption.

---

### NFR-020: Validation Donnees UX

**Priority:** Should Have

**Description:**
La validation des donnees par l'utilisateur doit etre rapide et facile.

**Acceptance Criteria:**
- [ ] 1 tap maximum (swipe style)
- [ ] Maximum 5-10 validations par jour

**Rationale:**
Trop de validations = friction = abandon.

---

### NFR-021: Browser Support

**Priority:** Must Have

**Description:**
L'application web doit fonctionner sur les navigateurs majeurs.

**Acceptance Criteria:**
- [ ] Chrome (2 dernieres versions)
- [ ] Safari (2 dernieres versions)
- [ ] Firefox (2 dernieres versions)

**Rationale:**
Compatibilite utilisateurs.

---

### Compatibilite

### NFR-022: APIs Integrations

**Priority:** Must Have

**Description:**
Les APIs doivent etre documentees et standards.

**Acceptance Criteria:**
- [ ] REST API documentee (OpenAPI)
- [ ] Versioning d'API
- [ ] Rate limiting

**Rationale:**
Integrations tierces et extensibilite.

---

### NFR-023: Mobile Responsive

**Priority:** Should Have

**Description:**
L'application web doit etre utilisable sur mobile.

**Acceptance Criteria:**
- [ ] Web app responsive
- [ ] UX adaptee mobile
- [ ] Pas d'app native pour P0

**Rationale:**
Commerciaux terrain sur mobile.

---

### NFR-024: Desktop Mac

**Priority:** Should Have

**Description:**
Une app desktop Mac sera necessaire pour la capture avancee.

**Acceptance Criteria:**
- [ ] App Mac pour capture WhatsApp, iMessage
- [ ] Prevue pour P1
- [ ] Distribution hors App Store

**Rationale:**
Certaines captures necessitent le desktop.

---

## Epics

Epics are logical groupings of related functionality that will be broken down into user stories during sprint planning (Phase 4).

Each epic maps to multiple functional requirements and will generate 2-10 stories.

---

### EPIC-001: Moteur Vectorisation

**Description:**
Infrastructure de stockage et recherche vectorielle pour Spider Memory.

**Functional Requirements:**
- FR-001 (Stockage vectoriel massif)
- FR-002 (Recherche semantique)
- FR-003 (API Memory)
- FR-005 (Extraction et structuration)

**Story Count Estimate:** 6-8

**Priority:** Must Have

**Business Value:**
Fondation technique de toute la plateforme SpiderOS. Sans Memory, aucun module ne peut fonctionner.

---

### EPIC-002: Qualite & Confiance Donnees

**Description:**
Systemes pour garantir la fiabilite des donnees extraites par l'IA.

**Functional Requirements:**
- FR-004 (Score de confiance)
- FR-007 (Systeme flashcards)

**Story Count Estimate:** 3-5

**Priority:** Must Have

**Business Value:**
Evite les erreurs embarrassantes qui detruisent la confiance. Critical pour l'adoption.

---

### EPIC-003: Transparence Memory

**Description:**
Interfaces pour que l'utilisateur voie et controle ce que Spider sait.

**Functional Requirements:**
- FR-006 (Memory Dashboard)
- FR-008 (Mode oublie-moi)
- FR-009 (Recherche cross-modules)

**Story Count Estimate:** 4-6

**Priority:** Should Have

**Business Value:**
Rassure les utilisateurs, conformite RGPD, differentiation.

---

### EPIC-004: Capture Automatique

**Description:**
Capture automatique des emails, calls et calendrier sans action utilisateur.

**Functional Requirements:**
- FR-010 (Capture emails)
- FR-011 (Capture calls)
- FR-012 (Capture calendrier)
- FR-028 (Capture WhatsApp)

**Story Count Estimate:** 6-8

**Priority:** Must Have

**Business Value:**
Zero saisie = proposition de valeur core de Spider People.

---

### EPIC-005: CRM Auto-Rempli

**Description:**
Creation et enrichissement automatique des fiches contacts.

**Functional Requirements:**
- FR-013 (Attribution automatique)
- FR-014 (Creation fiches)
- FR-022 (Sync CRM)

**Story Count Estimate:** 5-7

**Priority:** Must Have

**Business Value:**
"Mon CRM est rempli, j'ai rien fait" = wahoo moment principal.

---

### EPIC-006: Intelligence Relationnelle

**Description:**
Comprendre en profondeur chaque contact (score, profil, brief).

**Functional Requirements:**
- FR-015 (Score de connaissance)
- FR-016 (Brief avant RDV)
- FR-021 (Profil psychologique)

**Story Count Estimate:** 5-8

**Priority:** Must Have

**Business Value:**
Differenciateur majeur vs concurrents. CRM "profond" pas superficiel.

---

### EPIC-007: Inbox & Suggestions

**Description:**
Filtrage intelligent et suggestions de messages pre-rediges.

**Functional Requirements:**
- FR-017 (Inbox filtree)
- FR-018 (Messages suggeres)

**Story Count Estimate:** 4-6

**Priority:** Must Have

**Business Value:**
"5 trucs, pas 80" = clarte dans le chaos.

---

### EPIC-008: Alertes & Relances

**Description:**
Alertes proactives pour ne jamais oublier un contact ou un evenement.

**Functional Requirements:**
- FR-019 (Contacts qui refroidissent)
- FR-020 (Anniversaires et evenements)

**Story Count Estimate:** 3-4

**Priority:** Should Have

**Business Value:**
"Spider m'a sauve un deal" = la petite attention qui fait la difference.

---

### EPIC-009: Gestion Droits & Privacy

**Description:**
Cloisonnement des donnees et mode contacts prives.

**Functional Requirements:**
- FR-023 (Cloisonnement par role)
- FR-024 (Mode Ghost)

**Story Count Estimate:** 3-5

**Priority:** Must Have

**Business Value:**
Critical pour l'adoption equipes. "Mon assistant, pas mon surveillant."

---

### EPIC-010: Coaching & Playbook

**Description:**
Detection automatique du playbook et coaching post-call.

**Functional Requirements:**
- FR-025 (Playbook auto-detecte)
- FR-026 (Coaching post-call)
- FR-027 (Dashboard equipe)

**Story Count Estimate:** 5-8

**Priority:** Could Have

**Business Value:**
Capitalisation du savoir commercial. Differenciateur long terme.

---

### EPIC-011: Setup & Cadrage Projet

**Description:**
Onboarding guide et generation automatique PRD/archi pour Spider Builder.

**Functional Requirements:**
- FR-029 (Wizard onboarding)
- FR-030 (PRD automatique)
- FR-031 (Architecture automatique)
- FR-032 (Stack selector)
- FR-033 (Rules config)

**Story Count Estimate:** 6-8

**Priority:** Must Have

**Business Value:**
Evite les projets vibe coding qui partent en vrille des le jour 1.

---

### EPIC-012: Garde-fous Execution

**Description:**
Verification automatique du respect des regles pendant le coding.

**Functional Requirements:**
- FR-034 (Stack guard)
- FR-035 (Design system guard)
- FR-036 (Loop detection)

**Story Count Estimate:** 4-6

**Priority:** Must Have

**Business Value:**
Compense les hallucinations de l'IA. Dette technique evitee.

---

### EPIC-013: Tracking & Transparence

**Description:**
Suivi automatique de l'avancement et visibilite sur les agents.

**Functional Requirements:**
- FR-037 (US auto-link)
- FR-038 (Progress tracking)
- FR-039 (Agent visibility)

**Story Count Estimate:** 4-5

**Priority:** Should Have

**Business Value:**
Gestion de projet automatisee, pas de friction administrative.

---

### EPIC-014: Proxy Enrichissement

**Description:**
Proxy localhost qui enrichit les prompts Claude Code automatiquement.

**Functional Requirements:**
- FR-040 (Proxy localhost)

**Story Count Estimate:** 3-4

**Priority:** Must Have

**Business Value:**
Avantage competitif unique. Seul AI coding avec contexte methodologique auto.

---

### EPIC-015: Generation Photos

**Description:**
Generation de photos produit professionnelles par IA.

**Functional Requirements:**
- FR-041 (Photos produit)
- FR-043 (Brand kit)
- FR-047 (Templates)

**Story Count Estimate:** 5-7

**Priority:** Must Have

**Business Value:**
Remplace les shootings photo a 10% du cout.

---

### EPIC-016: Generation Videos

**Description:**
Generation de videos UGC avec avatars IA.

**Functional Requirements:**
- FR-042 (Videos UGC)
- FR-046 (Animation mascotte)

**Story Count Estimate:** 4-6

**Priority:** Must Have

**Business Value:**
Contenu video sans equipe production ni talents.

---

### EPIC-017: Brand Intelligence

**Description:**
Extraction intelligente de la marque et du catalogue.

**Functional Requirements:**
- FR-044 (Catalogue e-commerce)
- FR-045 (Multi-langues)

**Story Count Estimate:** 3-5

**Priority:** Should Have

**Business Value:**
"Comprend votre marque" = differentiation vs concurrents qui "extraient".

---

### EPIC-018: Integrations Email & Calendar

**Description:**
Connexion a Gmail et Google Calendar.

**Functional Requirements:**
- FR-048 (Gmail)
- FR-049 (Google Calendar)

**Story Count Estimate:** 4-5

**Priority:** Must Have

**Business Value:**
Fondation de la capture automatique.

---

### EPIC-019: Integrations Calls

**Description:**
Connexion a Aircall et Noota pour les appels et transcriptions.

**Functional Requirements:**
- FR-050 (Aircall)
- FR-051 (Noota)

**Story Count Estimate:** 3-4

**Priority:** Must Have

**Business Value:**
Capture des calls = mine d'or pour le CRM.

---

### EPIC-020: Integration CRM

**Description:**
Synchronisation bidirectionnelle avec Odoo.

**Functional Requirements:**
- FR-052 (Odoo)

**Story Count Estimate:** 2-4

**Priority:** Should Have

**Business Value:**
Coexistence avec le CRM existant.

---

### EPIC-021: Auth & Onboarding

**Description:**
Authentification et onboarding des nouveaux utilisateurs.

**Functional Requirements:**
- FR-053 (Auth)
- FR-054 (Onboarding)

**Story Count Estimate:** 4-6

**Priority:** Must Have

**Business Value:**
Premiere impression. Critique pour l'adoption.

---

### EPIC-022: Multi-Tenant & Securite

**Description:**
Gestion multi-tenant, roles et hebergement EU.

**Functional Requirements:**
- FR-055 (Multi-tenant)
- FR-056 (Roles)
- FR-059 (Cloud EU)

**Story Count Estimate:** 5-7

**Priority:** Must Have

**Business Value:**
Fondation B2B. Conformite RGPD.

---

### EPIC-023: Systeme Credits

**Description:**
Systeme de credits pour Content et Builder.

**Functional Requirements:**
- FR-057 (Credits)

**Story Count Estimate:** 3-4

**Priority:** Should Have

**Business Value:**
Business model usage-based.

---

### EPIC-024: Extension Chrome

**Description:**
Extension pour capturer des infos depuis le web.

**Functional Requirements:**
- FR-058 (Extension Chrome)

**Story Count Estimate:** 2-3

**Priority:** Should Have

**Business Value:**
Enrichissement depuis LinkedIn et sites web.

---

### EPIC-025: Site Web Marketing

**Description:**
Site web public SpiderOS avec homepage, pages modules, pricing.

**Functional Requirements:**
- FR-060 (Homepage)
- FR-061 (Pages modules)
- FR-062 (Pricing)
- FR-063 (Contact/demo)
- FR-064 (Blog)

**Story Count Estimate:** 5-7

**Priority:** Must Have

**Business Value:**
Distribution. Sans site web, personne ne sait que SpiderOS existe.

---

## User Stories (High-Level)

User stories follow the format: "As a [user type], I want [goal] so that [benefit]."

Detailed stories will be created during sprint planning (Phase 4).

---

## User Personas

### Dirigeant PME (Principal)

| Dimension | Description |
|-----------|-------------|
| **Profil** | CEO/fondateur de PME, 2-50M EUR CA, 20-200 employes |
| **Comportement** | Bon en relationnel, culture "pompier", TDAH frequent |
| **Douleur** | 80 mails/jour, oublie des contacts importants, CRM vide |
| **Objectif** | "Voir ma boite" sans rien changer a ses habitudes |
| **Citation** | "Je veux etre comme les meilleurs politiques, le mec qui se souvient de ton prenom apres 20 ans." |

### Commercial Terrain

| Dimension | Description |
|-----------|-------------|
| **Profil** | Commercial dans PME, 5+ RDV/semaine |
| **Comportement** | En deplacement, peu de temps administratif |
| **Douleur** | Doit remplir le CRM le soir, oublie des infos |
| **Objectif** | CRM rempli automatiquement, briefing avant RDV |
| **Citation** | "Je veux rentrer chez moi au lieu de passer 1h sur Hubspot." |

### Manager Commercial

| Dimension | Description |
|-----------|-------------|
| **Profil** | Responsable equipe commerciale 5-20 personnes |
| **Comportement** | Doit coacher sans surveiller |
| **Douleur** | Ne sait pas ce que font ses commerciaux sans demander |
| **Objectif** | Voir l'activite sans demander, coacher avec data |
| **Citation** | "Je veux que mes commerciaux progressent sans que je doive tout relire." |

### Developpeur (Spider Builder)

| Dimension | Description |
|-----------|-------------|
| **Profil** | Dev ou CTO utilisant l'IA pour coder |
| **Comportement** | Vibe coding, ne lit pas toujours le code genere |
| **Douleur** | Projets qui partent en vrille, dette technique invisible |
| **Objectif** | Cadre qui empeche les derives sans ralentir |
| **Citation** | "Faut pas se leurrer, quand on fait du vibe coding, les gens ne lisent pas le code." |

### Equipe Marketing PME (Spider Content)

| Dimension | Description |
|-----------|-------------|
| **Profil** | CM seul ou petite equipe, multi-reseaux |
| **Comportement** | Doit publier regulierement, peu de ressources |
| **Douleur** | Shootings chers, videos impossibles sans equipe |
| **Objectif** | Generer du contenu pro a cout reduit |
| **Citation** | "J'ai besoin de 20 visuels mais pas de budget photographe." |

---

## User Flows

### Flow 1: Onboarding (Spider People)

1. Signup (email/OAuth)
2. Connexion Gmail
3. Connexion Google Calendar
4. Connexion Aircall/Noota
5. Sync initiale (background)
6. Premier contact enrichi visible
7. Wahoo moment: "Mon CRM est rempli!"

### Flow 2: Brief avant RDV

1. RDV dans 30 min (detection calendrier)
2. Notification push
3. Click → Brief affiche
4. Resume derniers echanges + infos cles + suggestions
5. Utilisateur prepare en 2 min

### Flow 3: Message suggere

1. Email recu d'un contact
2. Spider analyse le contexte
3. Suggestion de reponse affichee
4. Utilisateur edite si besoin
5. Envoi en 1 clic

---

## Dependencies

### Internal Dependencies

| Dependance | Impact |
|------------|--------|
| Spider Memory | Tous les modules dependent de Memory pour la recherche semantique et le contexte |
| LightStar Template | Architecture technique commune |
| Design System | UI coherente entre modules |

### External Dependencies

| Dependance | Type | Risque |
|------------|------|--------|
| Gmail API | Integration | Faible (API stable) |
| Google Calendar API | Integration | Faible (API stable) |
| Aircall API | Integration | Moyen (dependance tierce) |
| Noota API | Integration | Moyen (dependance tierce) |
| Odoo API | Integration | Faible (optionnel P0) |
| LLM (Claude) | Core | Moyen (cout, disponibilite) |
| Embeddings | Core | Faible (plusieurs options) |
| Scaleway | Infra | Faible (provider stable) |

---

## Assumptions

| Hypothese | Risque si faux | Mitigation |
|-----------|----------------|------------|
| Les dirigeants connectent leurs outils (mail, telephone) | Pas de data = pas de valeur | Prouver la valeur immediate des la connexion |
| L'extraction IA est assez fiable (>80%) | Perte de confiance totale | Score de confiance visible, validation ciblee |
| Le pricing 49 EUR/user est accepte | Business model casse | Pivot si necessaire (usage, flat, freemium) |
| Le mode "zero setup" fonctionne | Adoption impossible | MVZ sur APIs d'abord |
| On peut tisser la toile (connecter toute la data) | Pas de produit | C'est le plus gros challenge technique |
| Drakkar = force commerciale + delivery | SpiderOS ralentit | Gouvernance claire, Remy full-time |
| On a le droit legal de capturer ces donnees | Risque juridique | Validation legale RGPD, consentement explicite |

---

## Out of Scope

| Element | Raison |
|---------|--------|
| Levee de fonds | Sauf si necessaire apres 18 mois |
| Marche hors Europe | Focus France d'abord |
| App mobile native | Web responsive d'abord, mobile P2 |
| Windows | Mac d'abord pour desktop, Windows P1 |
| Spider RH | P1, pas P0 |
| Spider Chatbot externe | MVP interne d'abord |
| Pricing au token | A explorer plus tard |

---

## Open Questions

| Question | Responsable | Deadline |
|----------|-------------|----------|
| Quelle techno vector DB finale? (LanceDB valide?) | Remy | Fev 2026 |
| Quelle strategie embeddings? | Remy | Fev 2026 |
| Architecture multi-tenant precise? | Remy | Fev 2026 |
| Validation legale RGPD capture? | Nathan | Jan 2026 |
| Pricing credits exact (Content/Builder)? | Nathan | Fev 2026 |

---

## Approval & Sign-off

### Stakeholders

| Nom | Role | Responsabilite |
|-----|------|----------------|
| Nathan Menard | CEO SpiderOS | Vision produit, validation finale |
| Remy Menard | CTO SpiderOS | Architecture technique, faisabilite |
| Drakkar | Investisseur + Beta tester | Feedback terrain |

### Approval Status

- [ ] Product Owner (Nathan)
- [ ] Engineering Lead (Remy)
- [ ] Design Lead
- [ ] QA Lead

---

## Revision History

| Version | Date | Author | Changes |
|---------|------|--------|---------|
| 1.0 | 2026-01-18 | Nathan Menard | Initial PRD |

---

## Next Steps

### Phase 3: Architecture

Run `/architecture` to create system architecture based on these requirements.

The architecture will address:
- All functional requirements (FRs)
- All non-functional requirements (NFRs)
- Technical stack decisions
- Data models and APIs
- System components

### Phase 4: Sprint Planning

After architecture is complete, run `/sprint-planning` to:
- Break epics into detailed user stories
- Estimate story complexity
- Plan sprint iterations
- Begin implementation

---

**This document was created using BMAD Method v6 - Phase 2 (Planning)**

*To continue: Run `/workflow-status` to see your progress and next recommended workflow.*

---

## Appendix A: Requirements Traceability Matrix

| Epic ID | Epic Name | Functional Requirements | Story Count (Est.) |
|---------|-----------|-------------------------|-------------------|
| EPIC-001 | Moteur Vectorisation | FR-001, FR-002, FR-003, FR-005 | 6-8 |
| EPIC-002 | Qualite & Confiance Donnees | FR-004, FR-007 | 3-5 |
| EPIC-003 | Transparence Memory | FR-006, FR-008, FR-009 | 4-6 |
| EPIC-004 | Capture Automatique | FR-010, FR-011, FR-012, FR-028 | 6-8 |
| EPIC-005 | CRM Auto-Rempli | FR-013, FR-014, FR-022 | 5-7 |
| EPIC-006 | Intelligence Relationnelle | FR-015, FR-016, FR-021 | 5-8 |
| EPIC-007 | Inbox & Suggestions | FR-017, FR-018 | 4-6 |
| EPIC-008 | Alertes & Relances | FR-019, FR-020 | 3-4 |
| EPIC-009 | Gestion Droits & Privacy | FR-023, FR-024 | 3-5 |
| EPIC-010 | Coaching & Playbook | FR-025, FR-026, FR-027 | 5-8 |
| EPIC-011 | Setup & Cadrage Projet | FR-029, FR-030, FR-031, FR-032, FR-033 | 6-8 |
| EPIC-012 | Garde-fous Execution | FR-034, FR-035, FR-036 | 4-6 |
| EPIC-013 | Tracking & Transparence | FR-037, FR-038, FR-039 | 4-5 |
| EPIC-014 | Proxy Enrichissement | FR-040 | 3-4 |
| EPIC-015 | Generation Photos | FR-041, FR-043, FR-047 | 5-7 |
| EPIC-016 | Generation Videos | FR-042, FR-046 | 4-6 |
| EPIC-017 | Brand Intelligence | FR-044, FR-045 | 3-5 |
| EPIC-018 | Integrations Email & Calendar | FR-048, FR-049 | 4-5 |
| EPIC-019 | Integrations Calls | FR-050, FR-051 | 3-4 |
| EPIC-020 | Integration CRM | FR-052 | 2-4 |
| EPIC-021 | Auth & Onboarding | FR-053, FR-054 | 4-6 |
| EPIC-022 | Multi-Tenant & Securite | FR-055, FR-056, FR-059 | 5-7 |
| EPIC-023 | Systeme Credits | FR-057 | 3-4 |
| EPIC-024 | Extension Chrome | FR-058 | 2-3 |
| EPIC-025 | Site Web Marketing | FR-060, FR-061, FR-062, FR-063, FR-064 | 5-7 |

**Total: 25 Epics, 64 FRs, 100-145 stories estimees**

---

## Appendix B: Prioritization Details

### Functional Requirements by Priority

| Priority | Count | % |
|----------|-------|---|
| Must Have | 38 | 59% |
| Should Have | 19 | 30% |
| Could Have | 7 | 11% |
| **Total** | **64** | 100% |

### Non-Functional Requirements by Priority

| Priority | Count | % |
|----------|-------|---|
| Must Have | 17 | 71% |
| Should Have | 7 | 29% |
| **Total** | **24** | 100% |

### Epics by Priority

| Priority | Count | Stories Est. |
|----------|-------|--------------|
| Must Have | 17 | ~80-100 |
| Should Have | 6 | ~20-30 |
| Could Have | 2 | ~10-16 |
| **Total** | **25** | **100-145** |

### MVP Scope (Must Have Only)

Pour le MVP (lancement Fev 2026), focus sur les 17 Epics "Must Have":
- Spider Memory: EPIC-001, EPIC-002
- Spider People: EPIC-004, EPIC-005, EPIC-006, EPIC-007, EPIC-009
- Spider Builder: EPIC-011, EPIC-012, EPIC-014
- Spider Content: EPIC-015, EPIC-016
- Integrations: EPIC-018, EPIC-019
- Plateforme: EPIC-021, EPIC-022
- Marketing: EPIC-025

**Estimation MVP: ~80-100 stories**
