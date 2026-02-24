# A1 - MAPPING CONCURRENTS COMPLET
## La reference competitive definitive de Spider

**Date de compilation:** 21 fevrier 2026
**Sources:** R7-exhaustive-competitor-map.md, R7b-missing-competitors.md, MARKET-SCAN-LIVE.md, THREAT-GEMINI-WORKSPACE.md
**Perimetre:** 181+ acteurs analyses, 8 sections structurees
**Methode:** Synthese et croisement des quatre documents de recherche primaire

---

## GUIDE DE LECTURE

**Niveaux de menace (1 a 5) :**
- 1 = Pas de menace (partenaire ou ecosysteme)
- 2 = Menace faible (chevauchement marginal)
- 3 = Menace moderee (overlap reel, a surveiller)
- 4 = Menace haute (collision possible dans 18 mois)
- 5 = Menace critique (concurrent direct maintenant)

**Cibles Spider pour memoire :**
- PMEs europeennes, 2M-50M EUR de CA, 20-500 employes
- Marche france-first, puis Europe
- Canal: experts-comptables + deploiement direct (FDE model)
- Promesse: Palantir-like operational intelligence pour des budgets PME

---

## SECTION 1 : BIG TECH

### 1.1 Google (Gemini + Workspace Studio)

**Ce qu'ils font aujourd'hui (fevrier 2026)**

Google a transforme Workspace en une veritable plateforme agentique. La liste des capacites reelles en production :

- **Gmail** : tri automatique par urgence, syntheses de fils, redaction de reponses, labeling automatise par IA
- **Sheets** : analyse en langage naturel, generation de formules, creation de tableaux depuis des prompts
- **Calendar** : planification intelligente cross-agenda, "Productivity Planner Gem" croisant Gmail + Calendar + Drive
- **Docs** : "Help Me Write", side panel de synthese et Q&A sur le contenu
- **Meet** : resume de reunions, traduction en temps reel (Business Standard, deploye janvier 2026)
- **Workspace Studio** (GA fevrier 2026) : creation d'agents en langage naturel, workflows cross-apps, actions autonomes, 20 connecteurs pre-built (Salesforce, Jira, Asana, Mailchimp, Slack), webhooks custom

**Tarification** : Business Standard 14$/user/mois -- tout inclus. Pour une PME de 10 personnes : ~130 EUR/mois, Gemini compris.

**Ce qu'ils feront dans 18 mois**

- Levee de la limite de 20 etapes par agent (prevue H2 2026)
- Support des boucles dans Workspace Studio (annonce "later in 2026")
- Connecteurs MCP natifs vers des outils tiers (Pennylane, Odoo) via le protocole ouvert qu'ils ont rejoint
- Expansion des connecteurs pre-built vers des outils europeens/francais
- Agent Designer enterprise (actuellement Gemini Enterprise uniquement) descend vers les PME
- Gemini 4 (probable 2026) avec un contexte encore plus large

**Niveau de menace : 4/5**

**Pourquoi c'est une menace grave**

Workspace Studio est deja en prod et fait ce que Spider promet : agents construits en langage naturel, workflows autonomes cross-apps. Le prix est imbattable (inclu dans l'abonnement existant). Environ 1,1 million de PMEs francaises utilisent deja Google Workspace. Pour ces clients, Gemini est gratuit.

**Pourquoi ce n'est pas fatal**

Trois mots : Pennylane, Odoo, banques. Gemini ne voit que le monde Google. Il ne voit pas les factures Pennylane, les commandes Odoo, les releves bancaires. Il ne peut pas croiser ces donnees pour detecter qu'un client doit 47K EUR et que le ton de ses emails se degrade. Spider voit tout. C'est la fenetre de 12-24 mois.

Les cinq gaps irreductibles de Gemini aujourd'hui :
1. Zero connecteur vers les outils de gestion francais (Pennylane, Odoo, banques)
2. Zero comprehension des processus metier (pas d'ontologie, pas de "process fingerprint")
3. Zero alerting proactif cross-systemes
4. Zero deploiement humain (model 100% self-service vs Spider white-glove)
5. Zero connaissance sectorielle (Gemini ignore tout de la publicite exterieure en Normandie)

**Positionnement Spider contre Google** : "Gemini lit vos emails. Spider comprend votre business."

---

### 1.2 Microsoft (Copilot Studio + M365)

**Ce qu'ils font aujourd'hui**

- Copilot integre dans Word, Excel, Teams, Outlook (Business Standard inclus)
- **Copilot Studio** : platform no-code de construction d'agents bases sur donnees M365
- **Agent Builder** : version allege no-code de Copilot Studio
- Agents autonomes executes dans M365 (Researcher, Analyst)
- Tarification : M365 Business Standard 12,50$/user/mois ; Copilot add-on enterprise +30$/user/mois (soit ~425 EUR/mois pour 10 personnes avec Copilot complet)

**Ce qu'ils feront dans 18 mois**

- Copilot Studio SMB tier : pricing plus accessible pour les PMEs
- Connecteurs MCP (Microsoft est co-fondateur de l'AAIF, standard MCP adopte)
- Agents pre-built pour des workflows PME specifiques (finance, RH, operations)
- Integration plus profonde avec Azure et des outils tiers via Power Automate

**Niveau de menace : 3/5**

**Pourquoi c'est une menace moderee**

M365 domine en France (~45% des PMEs). Copilot Studio est puissant. Mais : pricing enterprise, complexite de configuration, absence de deploiement humain, zero connecteurs vers l'ecosysteme francais (meme probleme que Google). Microsoft n'a jamais reussi a servir les vraies PMEs avec ses produits premium.

**Pourquoi ce n'est pas immediat**

61% des PMEs francaises manquent de competences numeriques (France Num 2023). Copilot Studio requiert de comprendre l'automatisation, de decrire les workflows, de tester et debugger. Un patron de PME en Normandie ne fera pas ca. Spider fait ca pour lui.

---

### 1.3 Anthropic (Claude Cowork)

**Ce qu'ils font aujourd'hui**

Claude Cowork est l'evenement de marche le plus significatif de fevrier 2026. Il apporte les capacites agentiques de Claude Code aux non-developpeurs via l'application desktop Claude. Disponible sur Mac et Windows (70% du marche desktop). 11 plugins open-source lances. Plans Team et Enterprise + Pro subscribers (research preview). Plugin legal deja sorti pour la revue documentaire.

**Ce qu'ils feront dans 18 mois**

- Plugins verticaux (finance, RH, legal, operations) multiplies
- Deploiement general (sortie du mode research preview)
- Plugins specifiques aux outils metier (potentiellement Odoo, Pennylane via MCP)
- Possible offre SMB directe avec tarification simplifiee

**Niveau de menace : 4/5**

**Pourquoi c'est une menace grave**

Cowork a deja declenche un selloff de 285 milliards de dollars sur les actions SaaS en un seul jour ("Black Tuesday for Software", 3 fevrier 2026). Il valide le paradigme que Spider est en train de construire -- agents remplacant des sièges logiciels. Si Anthropic lance des plugins verticaux PME pour Cowork, ils prennent le marche avant Spider.

Anthropic est a la fois **la principale infrastructure de Spider** (le modele Claude est ce qui fait tourner les agents) et **son concurrent le plus dangerous a long terme**.

**Pourquoi ce n'est pas fatal maintenant**

Cowork est horizontal. Il n'a pas de connaissance metier des PMEs, pas de connecteurs vers l'ecosysteme francais, pas de deploiement humain, pas de persistance du contexte business. Spider doit se positionner comme la couche d'orchestration et de customisation AU-DESSUS de Cowork, pas contre lui.

**La reponse strategique** : "Spider utilise Claude. Comme un chirurgien utilise un scalpel. Le scalpel ne fait pas l'operation."

---

### 1.4 OpenAI (Frontier Platform)

**Ce qu'ils font aujourd'hui**

OpenAI Frontier : plateforme enterprise de construction, deploiement et gestion d'agents AI. Lances le 5 fevrier 2026. Premiers clients : HP, Intuit, Oracle, State Farm, Thermo Fisher, Uber. Gere les agents construits HORS OpenAI (couche d'orchestration). Model FDE (Forward Deployed Engineers) inspire de Palantir. Tarification : contrats 6-7 chiffres annuels.

**Ce qu'ils feront dans 18 mois**

- Expansion des clients, potentiellement vers le mid-market
- OpenAI a $850B de valorisation et $100B de nouveau financement : ils ont les moyens de tout faire
- Mais la trajectoire est clairement enterprise. Pas de signaux SMB.

**Niveau de menace : 2/5**

**Pourquoi la menace est faible pour Spider**

Tarification 6-7 chiffres = exclu de facto du marche PME. OpenAI sert HP, Oracle, State Farm. Spider sert les PMEs de 2M-50M EUR. Ce sont des marches sans chevauchement.

**L'opportunite** : Spider peut se positionner explicitement comme "Frontier pour les PMEs" -- meme approche FDE, meme intelligence operationnelle, prix 100x plus accessible.

---

### 1.5 Salesforce (Agentforce)

**Ce qu'ils font aujourd'hui**

Agentforce : 500M$ ARR, croissance 330% YoY, 18 500+ deals signes dont 9 500+ payants (+50% QoQ). "Produit a la croissance la plus rapide de l'histoire de Salesforce." Spring '26 Release (23 fevrier) : AI Sales Workspace, Proactive Service, AgentForce Voice. Tarification : 0,10$/action ou Flex Credits. 10 acquisitions en 6 mois dont Momentum (intelligence conversationnelle). ~1 000 licenciements simultanes.

**Ce qu'ils feront dans 18 mois**

- Potentiel d'un tier "Small Business" Agentforce si la pression du marche SMB augmente
- Expansion des categories d'agents (finance, HR, legal en plus de sales/service)
- Mais Salesforce n'a jamais reussi avec les vraies PMEs

**Niveau de menace : 2/5**

**Pourquoi la menace est faible**

Salesforce a essaye les PMEs avec Essentials, Sales Cloud Starter, etc. Echec systematique. L'ADN Salesforce est enterprise. Le prix plancher, la complexite de deploiement, et le besoin d'un ecosysteme Salesforce pre-existant rendent Agentforce structurellement inaccessible aux PMEs de 2M-50M EUR.

**Ce que Spider apprend de Salesforce** : $500M ARR prouve que le marche des agents payants existe. La preuve de concept est faite a l'echelle enterprise. Spider doit etre la version abordable de ce que Salesforce fait.

---

## SECTION 2 : PLATEFORMES D'AGENTS AI

### 2.1 Dust.tt -- LE CONCURRENT FRANCAIS

**Fiche signalétique**
- HQ : Paris, France
- Fondateurs : Gabriel Hubert et Stanislas Polu (ex-OpenAI)
- Financement : 21,5M$ total (Serie A juin 2024, Sequoia-led)
- Revenue : 7,3M$ (juillet 2025), equipe de 66 personnes
- Cible : equipes tech-savvy, entreprises tech (Clay, Cursor, Persona sont clients)

**Ce qu'ils font aujourd'hui**

Plateforme custom d'agents AI connectes a la donnee interne de l'entreprise. Feature "Skills" lancee le 26 janvier (agents apprenant de nouvelles capacites instantanement). Agent Observability Dashboard lance le 3 fevrier (visibilite temps reel sur performance des agents -- usage trends, execution d'outils, feedback, temps de reponse, comportement de retrieval). Approche FDE (Forward Deployed Engineers) pour le deploiement.

**Ce qu'ils feront dans 18 mois**

- Croissance agressive (objectif 5x selon signaux publics)
- US-first : Sequoia pousse vers le marche americain
- Montee en gamme : leur ICP naturel est tech companies, pas PMEs traditionnelles
- Potentiel de creation d'un tier PME si la concurrence les y pousse
- Possible integration Odoo ou tools ERP si un grand client le demande

**Niveau de menace : 5/5**

**Pourquoi c'est le concurrent le plus critique**

ADN francais + agents AI + Sequoia + narration identique. Dust est la seule entreprise avec exactement le meme positionnement narratif que Spider dans le marche francais. Si Dust decide un jour de construire une integration Odoo ou un "tier PME", c'est une collision directe.

**Pourquoi la collision ne s'est pas encore produite**

Dust monte en gamme et vise les US en premier. Leur ICP est les equipes tech (startups, scale-ups, tech companies). Ils ne visent pas un patron de PME industrielle de Caen qui utilise Odoo et Excel. L'ADN produit est developer/power-user. Spider vise des operationnels qui ne savent pas ce qu'est un "agent".

**La differentiation Spider vs Dust**

| Dimension | Dust | Spider |
|-----------|------|--------|
| ICP | Equipes tech-savvy | PME operationnelles traditionnelles |
| Approche | Self-service + FDE | White-glove first |
| Integration ERP | Aucune Odoo/SAP visible | Odoo-first |
| Langue/marche | Anglais, US-first | Francais, France-first |
| Profondeur metier | Horizontal | Vertical (connaissance sectorielle) |
| Revenue (jul 2025) | 7,3M$ | 0 (en construction) |

**Ce que Spider doit faire** : depasser Dust dans l'execution marche SMB avant qu'ils n'y descendent. La fenetre : 12-18 mois.

---

### 2.2 Lindy AI

**Fiche signalétique**
- HQ : San Francisco (Flo Crivello)
- Financement : 49,9M$ total (Serie B 35M$ janvier 2023)
- Revenue : 5,1M$ (octobre 2024)
- 1 600+ integrations app (Gmail, Zoom, Twilio, Slack, HubSpot, etc.)

**Ce qu'ils font**

Assistant AI qui automatise la gestion email, support client, scheduling, saisie CRM, notes de reunion. En septembre 2025 : integration Claude Sonnet 4.5 pour 30+ heures d'operation autonome sur des taches complexes. Approche proactive (pas juste reactive aux prompts).

**Service-as-Software ou simple outil ?** Simple outil SaaS. Zero deploiement humain.

**Cible les PMEs ?** US-centric, equipes individuelles et petites equipes. Pas les PMEs europeennes traditionnelles.

**Niveau de menace : 3/5**

**Pourquoi surveiller**

Lindy est le plus proche positionnement "AI COO" visible sur le marche. Si Lindy ajoute des connecteurs ERP et entre en Europe, c'est un concurrent direct. Mais aujourd'hui : zero integration Odoo/SAP, zero deploiement manage, zero focus europeen/francais, zero compliance RGPD.

---

### 2.3 Relevance AI

**Fiche signalétique**
- HQ : Sydney, Australie
- Plateforme low-code de "workforce AI" pour l'automatisation business
- Cible : SMB / Mid-market
- Tarification : freemium + tiers payes

**Ce qu'ils font**

Plateforme low-code de creation d'agents AI pour les operations business. Narration proche de Spider : "AI workforce". Mais execution australienne, sans focus europeen ni connecteurs vers l'ecosysteme francais.

**Service-as-Software ou outil ?** Outil. Pas de deploiement humain.

**Niveau de menace : 3/5**

Meme narration, meme segment cible (SMB), mais zero presence europeenne, zero connaissance du tissu PME francais.

---

### 2.4 CrewAI

**Fiche signalétique**
- US, open-source
- Framework multi-agents (role-based crews)
- Cible : developpeurs
- Pas de produit end-user pour les PMEs

**Ce qu'ils font**

Framework d'orchestration multi-agents. Outil pour construire Spider, pas un concurrent de Spider. Aucune PME n'achete "CrewAI" -- elles achevent Spider, qui pourrait etre construit partiellement avec CrewAI.

**Niveau de menace : 1/5** (partenaire technologique)

---

### 2.5 LangChain / LangGraph

**Fiche signalétique**
- 35M$ (Sequoia)
- Framework d'agents le plus mature (v1.0 atteint 2025)
- Clients : Uber, LinkedIn, Klarna
- LangSmith : observabilite pour les apps LLM

**Ce qu'ils font**

LangGraph = framework de construction d'agents (comme React pour le web). LangSmith = monitoring. Outil d'infrastructure, pas produit concurrent. Aucune PME n'achete LangChain.

**Niveau de menace : 1/5** (infrastructure a evaluer pour Spider en interne)

---

### 2.6 AutoGPT / BabyAGI

Agent autonome pionnier, largement obsolete pour la prod. Projets communautaires open-source. Zero menace commerciale.

**Niveau de menace : 1/5**

---

### 2.7 Beam AI

**Fiche signalétique**
- US, $132K levé (quasi-bootstrapped)
- Automatisation agentique pour le back-office repetitif
- Cible : SMB / Mid-market

**Ce qu'ils font**

Agents pour taches repetitives de back-office. Cible similaire a Spider mais stade tres precoce, zero presence europeenne, zero connaissance PME francaise.

**Niveau de menace : 2/5**

---

### 2.8 Bardeen.ai

**Fiche signalétique**
- San Francisco (Artem Harutyunyan et Pascal Weinberger)
- Chrome extension, no-code
- "Work Intelligence Platform" lancee mai 2025
- 300K utilisateurs

**Ce qu'ils font**

Automatisation de workflows via extension Chrome. Agents qui apprennent comment le travail se fait et l'executent. Browser-based, US-focused, individu-oriente. Concurrent de Zapier plus que de Spider.

**Service-as-Software ou outil ?** Outil. Pas de deploiement humain.

**Niveau de menace : 2/5**

---

### 2.9 Sintra AI / Ema AI / Adept AI

Ces trois acteurs ont des positionnements similaires : "AI employees" pour les operations. Tous US-focuses, enterprise pour Adept ($415M) et Ema ($58M+), SMB pour Sintra. Zero presence europeenne documentee, zero connecteurs francais.

**Niveau de menace : 2/5** (collectif, a surveiller)

---

## SECTION 3 : ERP / LOGICIELS OPERATIONNELS

### 3.1 Odoo -- PARTENAIRE ET MENACE SIMULTANEMENT

**Fiche signalétique**
- HQ : Ramillies, Belgique
- ERP open-source modulaire (compta, CRM, stock, RH)
- 15M+ utilisateurs, 100M$+ de revenus, prive
- Janvier 2026 : 20M EUR de nouveau ARR en un seul mois (record)
- Odoo 20 : sortie prevue les 24-26 septembre 2026 a Bruxelles

**Ce qu'ils font aujourd'hui**

ERP modulaire complet pour les PMEs : comptabilite, CRM, gestion des stocks, RH, fabrication, e-commerce. Tarification : gratuit (Community) + a partir de 31 EUR/user/mois. L'ERP de reference pour les PMEs europeennes en croissance.

**Ce qu'ils feront dans 18 mois : Odoo 20 avec AI agentique**

C'est la date cle : **24 septembre 2026**. Odoo 20 est attendu avec des fonctionnalites d'AI agentique ou le systeme execute des workflows de maniere proactive plutot que de simplement repondre a des prompts. La communaute Odoo debat deja de Gemini vs ChatGPT pour l'integration ERP.

**Niveau de menace :** 4/5 (simultanément 1/5 comme partenaire)

**Pourquoi c'est simultanement la plus grande menace et le plus grand partenaire**

MENACE : Si Odoo 20 integre une IA agentique vraiment performante, le wedge de Spider s'effondre. Odoo a la donnee, a la relation client PME, et a l'ecosysteme. Un ERP qui se pilote lui-meme rend Spider inutile.

PARTENAIRE : Aujourd'hui, Odoo est la principale source de donnees de Spider. L'intelligence layer QUE Spider construit AU-DESSUS d'Odoo est exactement ce qu'Odoo n'est pas capable de construire bien. Les integrators Odoo (Apik, Camptocamp, etc.) sont le canal naturel de Spider.

**Roadmap AI Odoo**
L'AI agentique d'Odoo sera probablement "AI-assisted" plutot que vraiment autonome -- des features IA boulonnees sur un ERP traditionnel. Spider part de l'agent-first. La differentiation : Odoo retrofite l'IA. Spider nait avec l'IA.

**Fenetre temporelle critique**

Spider a **6 mois** (mars-septembre 2026) pour etre en marche avec des clients payants avant qu'Odoo ne puisse clamer "nous faisons aussi les agents". La priorite absolue est d'etre installe et reconnu avant Odoo Experience 2026.

**Part de marche France** : Odoo est le leader ERP open-source en France avec une penetration forte dans les PMEs industrielles et de services. Les integrateurs francais (Apik, Camptocamp, Irokoo, Scalizer, Akretion, XCG) controlent les relations clients -- ce sont eux qu'il faut embarquer.

---

### 3.2 SAP Business One

**Fiche signalétique**
- Filiale SAP, Walldorf (Allemagne)
- ERP pour les petites enterprises
- ~150 EUR/user/mois

**AI roadmap** : SAP Business AI existe pour SAP S/4HANA (enterprise). Business One AI est beaucoup plus limite. SAP n'investit pas prioritairement sur le segment <50M EUR.

**Part de marche France PME** : Presence limitee dans le segment 2M-50M EUR, concentree sur les ETIs et grands groupes.

**Niveau de menace : 1/5**

---

### 3.3 Sage

**Fiche signalétique**
- Public (LSE), Newcastle (UK)
- 43 000 clients en France
- Logiciel de comptabilite et de gestion

**AI roadmap** : Sage Copilot existe (formules magiques, analyses, etc.) mais reste ancre dans la comptabilite. Pas de derive agentique documentee pour les operations PME.

**Tarification PME** : A partir de 20 EUR/mois. Tres accessible.

**Part de marche France** : Important en comptabilite (43K clients), negligeable en operations transverses.

**Niveau de menace : 1/5** (marche distinct)

---

### 3.4 Cegid

**Fiche signalétique**
- Lyon, France
- PE-owned ; acquisition EBP en cours (275K clients, 65M EUR CA)
- 750K+ clients post-acquisition
- ERP, comptabilite, paie, retail

**AI roadmap** : Non documentee publiquement. Cegid est oriente integration et consolidation (acquisition EBP). L'AI est un sujet mais pas encore un produit.

**Part de marche France** : Tres significatif, surtout via EBP pour les TPE/PME. La fusion cree un acteur de 750K+ clients PME en France.

**Tarification PME** : Custom, accessible.

**Niveau de menace : 2/5**

La fusion Cegid-EBP cree un geant qui pourrait devenir partenaire ou concurrent. Si Cegid integre Spider dans son ecosysteme ou developpe sa propre IA operationnelle, l'impact est fort.

---

### 3.5 Axonaut

**Fiche signalétique**
- Toulouse, France
- CRM/ERP/facturation tout-en-un pour TPE/PME
- A partir de 49 EUR/mois
- Bootstrapped

**Ce qu'ils font**

Solution all-in-one francaise : CRM, facturation, tresorerie, gestion de projet. Cible exactement les memes TPE/PME que Spider.

**AI roadmap** : Tres limitee. Axonaut est un editeur traditionnel qui n'a pas encore pris le virage AI.

**Part de marche France** : Niche (TPE 1-10 employes), tres peu de presence documentee au-dela.

**Niveau de menace : 2/5**

---

### 3.6 Sellsy

**Fiche signalétique**
- La Rochelle, France
- CRM + facturation + marketing pour PME
- A partir de 29 EUR/user/mois
- 25M$+ leve

**Ce qu'ils font**

Suite commerciale francaise complete pour PMEs. Cible similaire a Spider mais positionnement pur CRM/facturation, pas intelligence operationnelle.

**AI roadmap** : Non documentee.

**Niveau de menace : 2/5**

---

## SECTION 4 : AI VERTICAUX

### Qu'est-ce que Spider peut apprendre de leur strategie de moat ?

Les AI verticaux ont resolu un probleme que Spider doit resoudre : **comment construire une expertise sectorielle inattaquable par les generalists horizontaux**.

---

### 4.1 Harvey (Legal AI)

**Fiche signalétique**
- San Francisco
- AI pour les cabinets d'avocats
- 100M$+ leve (Sequoia, Google, OpenAI)
- Valorisation : 1,5B$+

**Strategie de moat**

Harvey ne "fait pas du legal" avec ChatGPT. Il encode :
- Les sources de droit (codes, jurisprudence, doctrine)
- Les workflows specifiques (due diligence, redaction de contrats, negociation)
- Les conventions du secteur (formats, terminologie, standards de qualite)
- La validation humaine a chaque etape critique

Resultat : un modele generaliste (GPT-4) habille en expert sectoriel qui prend 3-5 ans a reproduire.

**Ce que Spider apprend**

Le moat n'est pas le modele AI. C'est la connaissance metier encodee dans le produit. Pour Spider : construire des templates d'ontologie PME par vertical (publicite exterieure, industrie, distribution, etc.) qui encodent les regles, les saisons, les ratios, les processus specifiques. Cela prend des mois a construire mais des annees a copier.

**Niveau de menace : 1/5** (marche distinct : legal enterprise)

---

### 4.2 Abridge (Medical AI)

**Fiche signalétique**
- Pittsburgh, US
- AI de documentation clinique (transcription de consultations -> notes medicales)
- 150M$+ leve
- Clients : Mayo Clinic, UCSF, Vanderbilt

**Strategie de moat**

Partenariats avec les grands systemes de sante (Mayo, Kaiser). La donnee de validation clinique (des milliers de consultations corrigees par des medecins) est le moat. Impossible a reproduire sans l'acces aux hopitaux partenaires.

**Ce que Spider apprend**

La donnee de validation est le moat, pas le modele. Pour Spider : chaque interaction agent validee ou corrigee par le patron PME est de la donnee de fine-tuning qui ameliore Spider et l'eloigne des concurrents. La boucle de feedback human-in-the-loop est une arme competitive.

**Niveau de menace : 1/5** (marche distinct : sante)

---

### 4.3 Upflow (AR Automation, France)

**Fiche signalétique**
- Paris, France
- Automatisation des comptes clients (accounts receivable) pour B2B
- 8M$+ leve
- A partir de 300$/mois

**Ce qu'ils font**

Automatisation des relances de paiement, workflows de recouvrement, reporting AR. Cible exactement les PMEs francaises B2B. Overlap direct avec le cas Jordan (39,3% de factures impayees).

**Niveau de menace : 3/5**

C'est le concurrent vertical le plus proche de Spider dans le marche cible exact. La differentiation Spider : Upflow fait l'AR. Spider fait l'AR + la compta + le CRM + le marketing + le diagnostic + la cartographie processus. L'integration est le produit.

**Ce que Spider apprend** : Upflow a trouve un acheteur de pain aigu (le cashflow manquant). Spider peut s'en inspirer pour le pitch initial.

---

### 4.4 Agicap (Cash Flow AI, France)

**Fiche signalétique**
- Lyon, France
- Gestion de tresorerie et cash flow pour PME
- 200M$+ leve, 45M EUR de revenus (2024)
- Cible : PME / Mid-market

**Ce qu'ils font**

IA de gestion de tresorerie : previsions de cash, alertes de risque de liquidite, scenarios what-if. S'integre avec les banques et les ERP. Fort dans le marche francais.

**Niveau de menace : 3/5**

Agicap pourrait s'etendre de la tresorerie a l'intelligence financiere operationnelle complete. La probabilite de collision dans 18 mois est evaluee a 20%.

**Ce que Spider apprend** : Agicap a prouve que les PMEs francaises payent pour de l'intelligence financiere. Spider doit convaincre qu'elles payeront pour de l'intelligence operationnelle elargie.

---

### 4.5 HighRadius (O2C Enterprise)

**Fiche signalétique**
- Houston, US
- Plateforme AI pour O2C (Order-to-Cash), tresorerie, et R2R
- 475M$+ leve, unicorn
- 200+ clients Fortune 1000

**Ce qu'ils font**

AI pour les grands comptes : automatisation de l'AR, prevision de tresorerie, reconciliation comptable. Cible enterprise uniquement.

**Niveau de menace : 1/5**

Enterprise uniquement, pricing prohibitif pour les PMEs, zero focus France/Europe pour les PMEs.

**Ce que Spider apprend** : Le marche de l'AR automation enterprise est valide et mature. Le marche PME equivalent est vierge. C'est exactement le gap qu'Upflow et Spider adressent.

---

### 4.6 Chaser (AR pour PMEs, UK)

**Fiche signalétique**
- Londres, UK
- Credit control software pour PMEs
- A partir de 45$/mois

Competitor AR direct pour PMEs, mais UK-focused sans penetration France documentee.

**Niveau de menace : 2/5**

---

## SECTION 5 : BPO / MANAGED SERVICES

### 5.1 Officeo -- LE CONCURRENT COMPORTEMENTAL #1

**Fiche signalétique**
- Paris, France
- N.1 francais de l'assistance administrative aux entreprises
- 6 000+ assistantes administratives freelances, deployables sous 48h
- Tarification : **38-50 EUR/heure HT** (urgence : +25-50%)
- Cible : PMEs, professions liberales, associations, collectivites

**Ce qu'ils font que Spider devrait faire**

- Deploiement rapide (48h, Spider devrait viser 48h aussi)
- Flexibilite totale (paiement a l'heure, pas d'engagement)
- Zero besoin de formation pour le client (on envoie un humain)
- Relation de confiance etablie (modele humain)
- Large gamme de taches (admin, comptable, commercial)

**Comparaison de prix avec Spider**

| Dimension | Officeo | Spider |
|-----------|---------|--------|
| Prix | 38-50 EUR/heure | ~500 EUR/mois flat |
| Disponibilite | Heures de bureau | 24/7 |
| Scalabilite | Lineaire (+ heures = + cout) | Cout marginal quasi-zero |
| Retention connaissance | Nulle (la personne part) | Permanente (dans le systeme) |
| Taux d'erreur | Humain | Plus faible sur repetitif |
| Jugement complexe | Eleve | Limite (pour l'instant) |
| Confiance | Elevee (humain) | A construire |

**Calcul ROI vs Spider** : Une PME qui utilise Officeo 30h/mois pour du back-office paie 1 140-1 500 EUR/mois. Spider a 500 EUR/mois = economie de 640-1 000 EUR/mois. Le pitch est simple : "Vous payez 18K EUR/an pour quelqu'un qui fait de la saisie et des relances. Spider fait ca pour 6K EUR/an, 24/7, et n'oublie jamais rien."

**Niveau de menace : 4/5** (concurrent comportemental primaire)

Officeo n'est pas un concurrent technologique. C'est ce que le patron PME fait AUJOURD'HUI a la place de Spider. Pour convaincre, Spider doit etre moins cher, plus fiable, ET inspirer confiance.

---

### 5.2 3h18

**Fiche signalétique**
- La Rochelle, France
- Externalisation administrative et RH pour PMEs
- Reseau de freelances experts en admin, RH, comptabilite, support commercial
- Tarification : **50-80 EUR/heure HT** (minimum 2h/mois)
- Facturable en charges d'exploitation (pas en cout personnel)

**Ce qu'ils font que Spider devrait faire**

3h18 est plus cher qu'Officeo mais se positionne sur un profil plus qualifie (RH, recrutement). L'argument cle : facturable en charges d'exploitation, pas en masse salariale. Spider doit reprendre cet argument : "Spider ne s'imprime pas sur votre bulletin de salaires. C'est un abonnement SaaS -- deductible, scalable, et sans risque prud'homal."

**Calcul ROI vs Spider** : 3h18 a 60 EUR/h x 20h/mois = 1 200 EUR/mois. Spider a 500 EUR/mois = 700 EUR d'economie. Sur un an : 8 400 EUR recuperes.

**Niveau de menace : 4/5** (concurrent comportemental primaire, plus fort sur RH)

---

### 5.3 DAF Externalisé (multiple acteurs)

**Ce qu'ils font**

Service de Directeur Administratif et Financier a temps partiel pour les PMEs. Typiquement 500-2 000 EUR/mois pour une intervention periodique (1-2 jours/mois). Audit financier, tableaux de bord, pilotage de la tresorerie, relations bancaires.

**Ce que Spider devrait apprendre**

Le DAF externalisé est l'acheteur ideal de Spider, pas le concurrent. Un DAF externalisé qui recommande Spider a ses 20 clients PME devient un canal de distribution puissant. L'argument : "Spider fait le monitoring quotidien, je fais la strategie mensuelle. Ensemble on est imbattables."

**Niveau de menace : 3/5** (concurrent sur le budget, partenaire potentiel sur le canal)

---

### 5.4 Dougs / Wity (Expert-Comptables Digitaux)

**Fiche signalétique**
- Dougs : Lyon, a partir de 49 EUR HT/mois
- Wity : a partir de 29 EUR HT/mois
- Cabinets comptables en ligne pour PMEs et freelances

**Ce qu'ils font**

Comptabilite en ligne, declarations fiscales, bilan annuel. Pas d'intelligence operationnelle, pas d'agents, pas de cross-system analysis.

**Niveau de menace : 1/5**

Canal potentiel (les cabinets comptables digitaux pourraient revendre Spider) plus que concurrent.

---

## SECTION 6 : FRENCH FINTECH / OUTILS PME

### 6.1 Pennylane -- L'ADJACENT LE PLUS DANGEREUX

**Fiche signalétique**
- Paris, France
- 175M EUR leves (29 janvier 2026) -- TCV et Blackstone Growth
- Valorisation : 4,25B$ (licorne)
- 6 000 cabinets comptables partenaires, 800 000 entreprises clientes
- Approche de la rentabilite (EU-Startups, janvier 2026)

**Ce qu'ils font aujourd'hui**

Plateforme comptable tout-en-un pour PMEs, principalement via le canal expert-comptable. Extension vers les paiements : lancement de terminaux de paiement en beta en fevrier 2026 (1 000 entreprises pre-inscrites). Partenariat TOP 14 rugby (presenting partner, 2026-2028). Vision : "Operating System financier pour les TPE/VSB".

**Ce qu'ils feront dans 18 mois**

- Expansion paiements : Pennylane devient une banque d'entreprise complementaire
- Potentiel d'ajout de features AI sur les donnees comptables (analyse, alertes)
- Extension vers l'intelligence operationnelle si un concurrent les y pousse
- Mais : Pennylane est en mode execution SaaS classique. Pas de signaux d'AI agentique.

**Niveau de menace : 4/5**

**Strategie de canal** : Comment Pennylane a reussi

Pennylane a fait quelque chose de brillant : ils ont converti les experts-comptables en force de vente. Chaque cabinet Pennylane amene des dizaines de clients PME. Le CA par client est faible mais le volume est massif (800K entreprises). Spider doit exactement repliquer ce modele : les experts-comptables comme canal primaire.

**Ce qui a fait reussir Pennylane**
1. Canal expert-comptable : confiance transferee du comptable vers le produit
2. Compliance dès le depart : les comptables ne recommandent que des outils conformes
3. Integration dans le workflow existant : Pennylane ne remplace pas le comptable, il l'augmente
4. Pricing accessible : 35 EUR/mois, prix psychologiquement faible
5. Produit simple : une seule promesse (comptabilite en temps reel)

**Potentiel de partenariat avec Spider**

Pennylane a les donnees comptables. Spider a l'intelligence operationnelle. Un partenariat permettrait a Spider d'acceder aux 800K entreprises Pennylane via l'API comptable. C'est le graal : co-sell ou integration profonde.

**Risque** : Si Pennylane decide de construire de l'intelligence operationnelle sur ses donnees, ils ont un avantage de donnees que Spider ne peut pas replicquer. A surveiller en priorite absolue.

---

### 6.2 Qonto

**Fiche signalétique**
- Paris, France
- Banque d'entreprise pour PMEs et freelances
- 622M EUR leves, valorisation 5B$
- A partir de 9 EUR/mois

**Ce qu'ils font**

Compte bancaire professionnel avec API, categories automatiques, integrations comptables, cartes virtuelles. Modele pur fintech, pas d'intelligence operationnelle.

**Potentiel de partenariat Spider**

Les donnees bancaires Qonto sont une source primaire pour Spider : flux de tresorerie, paiements, debit/credit. Un connector Qonto dans Spider serait une feature cle pour les 500K+ clients Qonto.

**Niveau de menace : 1/5** (partenaire ideal)

---

### 6.3 Alan

**Fiche signalétique**
- Paris, France
- Mutuelle sante digitale pour entreprises
- 500M$+ leve, valorisation 3B$

Segment complementaire (RH / avantages salaries). Zero chevauchement avec Spider operations.

**Potentiel de partenariat** : Source de donnees RH (effectifs, statuts). Faible priorite.

**Niveau de menace : 1/5**

---

### 6.4 PayFit

**Fiche signalétique**
- Paris, France
- Gestion de la paie et RH pour PMEs
- 400M$+ leve, licorne

**Ce qu'ils font**

Logiciel de paie et RH : fiches de paie automatiques, gestion des conges, DADS, DUE, pilotage RH. Integration avec les banques et les outils comptables.

**Potentiel de partenariat Spider**

Les donnees de paie PayFit (effectifs, couts salaraux, conges, absences) sont critiques pour l'intelligence operationnelle Spider. Un agent Spider qui monitore les couts de personnel en temps reel et alerte sur les derives necessite PayFit comme source.

**Niveau de menace : 1/5** (partenaire ideal -- meme marche, offres complementaires)

---

### 6.5 Silae

**Fiche signalétique**
- Paris, France
- Logiciel de paie pour cabinets comptables et PMEs
- Leader marche paie France via les cabinets

**Ce qu'ils font**

Silae est le logiciel de paie des experts-comptables. Si Spider veut lire les donnees de paie de ses clients PME via leur comptable, l'integration Silae est strategique.

**Potentiel de partenariat** : Integration via API Silae pour alimenter les agents RH de Spider.

**Niveau de menace : 1/5** (ecosysteme, partenaire potentiel)

---

### 6.6 Agicap (see Section 4.4)

**Niveau de menace : 3/5** (adjacent qui pourrait s'etendre)

---

### 6.7 Spendesk

**Fiche signalétique**
- Paris, France
- Gestion des depenses corporate (cartes, factures, remboursements, budgets, approbations)
- 311M$+ leve, valorisation 1,5B$, 52M$ ARR (mars 2025)
- Atteint la rentabilite en juin 2025
- Spendesk Travel en lancement 2026

**Ce qu'ils font**

Spend management complet : cartes virtuelles, workflow d'approbation, integration comptable. Profond dans le workflow financier PME.

**Potentiel de partenariat Spider**

Donnees de depenses Spendesk = input pour les agents de pilotage des couts Spider. Meme marche cible, offres complementaires.

**Niveau de menace : 1/5** (partenaire ideal)

---

## SECTION 7 : LE VRAI CONCURRENT -- LE FREELANCE + CLAUDE + ZAPIER

### C'est la vraie question que Spider doit repondre

> "Pourquoi payer Spider 500 EUR/mois alors qu'un bon freelance peut faire la meme chose en 2-3 jours avec Claude et Zapier ?"

Cette question est la plus dangereuse. Pas parce que la reponse n'existe pas -- mais parce qu'elle est rarement bien posee.

---

### Ce qu'un freelance competent peut faire en 2-3 jours (reellement)

**Outils utilises** : Claude Opus 4.6 (via Cowork ou API), Zapier, Make, Google Sheets, Notion, parfois n8n

**Jour 1 : Audit et setup (6-8h)**

- Entretien avec le patron PME (2h)
- Mapping des outils existants (Odoo, Gmail, Pennylane)
- Configuration des connexions Zapier/Make (authentification APIs)
- Construction de 2-3 zaps basiques (ex: "nouvelle facture Pennylane impayee a J+30 -> email de relance via Claude")
- Livrable : rapport d'audit + 3 automatisations simples fonctionnelles

**Jour 2 : Automatisations avancees (6-8h)**

- Construction du tableau de bord KPI dans Google Sheets (connectoré a Odoo via API)
- Prompt engineering pour les relances personnalisées (Claude genere les emails)
- Mise en place du workflow de suivi clients (Pipedrive ou Notion database)
- Automatisation des reports hebdomadaires
- Livrable : dashboard operationnel + 5-8 automatisations

**Jour 3 : Tests, documentation et handover (4-6h)**

- Tests de toutes les automatisations
- Documentation (Notion, Google Docs)
- Formation du patron PME (1h)
- Livrable : systeme fonctionnel + documentation + 1h de formation

**Cout** : 1 500-3 000 EUR (selon experience du freelance)
**Maintenance** : 200-500 EUR/mois pour les bugs et evolutions

---

### Ce que le freelance ne peut PAS faire

| Ce que le Freelance + Claude + Zapier ne fait pas | Pourquoi |
|---------------------------------------------------|----------|
| **Persistance de la connaissance metier** | Quand le freelance part, la connaissance part. Zapier n'apprend pas. Claude oublie entre les sessions. |
| **Intelligence croisee multi-systemes en temps reel** | Zapier fait des triggers lineaires. Il ne detecte pas qu'un client doit 47K EUR ET que le ton de ses emails se degrade ET que sa saisonnalite signifie qu'il sera a cours de cash en juillet. |
| **Ontologie metier qui s'ameliore** | Le freelance fait un mapping une fois. Il ne construit pas une representation formelle du business qui s'affine avec chaque interaction. |
| **Alertes proactives basees sur des patterns historiques** | Zapier reagit a des events. Il ne detecte pas des patterns sur 6 mois de donnees. |
| **Deploiement "clé en main" garanti** | Le freelance part. Les zaps cassent (changements d'API, de plans Zapier, d'outils). Qui repare ? |
| **Support continu + SLA** | Le freelance est disponible selon sa charge. Spider offre un SLA. |
| **Scalabilite** | Pour chaque nouveau processus a automatiser, le patron PME doit rappeler le freelance. Spider evolue avec le business. |
| **Compliance RGPD verifiable** | Les donnees passent par Zapier servers (US). Spider peut garantir la souverainte europeenne. |
| **Intelligence sectorielle accumulée** | Le freelance ne sait pas que dans la pub exterieure, les comissions sont 13-15% et le pic septembre. Spider, apres 10 clients dans le secteur, le sait. |

---

### Le calcul complet sur 3 ans

**Option A : Freelance + Claude + Zapier**

| Periode | Cout |
|---------|------|
| Setup initial (3 jours freelance) | 2 500 EUR |
| Maintenance mensuelle | 350 EUR/mois |
| Zapier plan (min 500 tasks/mois) | 50 EUR/mois |
| Claude API ou Cowork | 20-50 EUR/mois |
| Refonte annuelle (3-4 jours/an) | 1 000 EUR/an |
| **Total annee 1** | ~8 200 EUR |
| **Total annee 3** | ~22 600 EUR |

**Option B : Spider**

| Periode | Cout |
|---------|------|
| Diagnostic Eclair (one-shot) | 1 990 EUR |
| Abonnement mensuel | 500 EUR/mois |
| **Total annee 1** | ~7 990 EUR |
| **Total annee 3** | ~21 990 EUR |

**A cout equivalent, Spider offre :**
- Persistance de la connaissance (le freelance part, Spider reste)
- Intelligence qui s'ameliore dans le temps
- Cross-system intelligence (Zapier ne fait pas de raisonnement)
- SLA et support garanti
- Compliance RGPD native
- Connaissance sectorielle accumulee

---

### Pourquoi le freelance gagne quand meme parfois

Il faut etre honnete. Le freelance + Claude + Zapier gagne sur :
1. **Flexibilite extreme** : le patron peut changer d'avis, passer d'un outil a l'autre
2. **Pas d'engagement** : pas de contrat long terme, pas de friction de sortie
3. **Relation humaine** : certains patrons PME preferent parler a une personne
4. **Customisation illimitee** : un bon freelance fait EXACTEMENT ce que le patron veut

**La reponse de Spider** : ce que Spider perd en flexibilite court terme, il le gagne en accumulation long terme. Le bon argument : "Apres 6 mois, Spider connait votre business mieux que n'importe quel freelance qui vient de debarquer."

---

### Le vrai angle : Pourquoi le freelance + Claude + Zapier est INSTABLE

La cle de la reponse : **le freelance + Zapier ne tient pas dans le temps**.

1. **Turnover freelance** : le bon freelance qui a tout configure est rare. Il finit par trouver mieux paye ailleurs. Son successeur repart de zero.
2. **Breaking changes** : Zapier change ses plans, les APIs evoluent, les outils updates. Les zaps cassent regulierement. Qui maintient ?
3. **Accumulation de dette** : plus le systeme grossit, plus il est fragile. 3 ans de zaps empiles = cauchemar de maintenance.
4. **L'AI qui progresse** : Claude aujourd'hui est meilleur que Claude il y a 6 mois. Spider integre les nouvelles versions automatiquement. Le freelance doit refaire le prompt engineering a chaque upgrade.
5. **La connaissance perdue** : quand le patron PME fait appel a un nouveau freelance, il passe 2-3 jours a re-expliquer son business. Spider n'oublie jamais.

---

## SECTION 8 : MATRICE DE COLLISION

### Pour chaque capacite Spider : qui peut le faire, a quel prix, et l'avantage Spider

---

### 8.1 Relances clients (AR / Collections)

| Acteur | Peut-il le faire ? | Prix | Limite |
|--------|-------------------|------|--------|
| **Upflow** | Oui, c'est son coeur de metier | 300$/mois | Que l'AR, pas le reste |
| **Chaser** | Oui, pour PME UK | 45$/mois | Pas France |
| **Gaviti / Growfin** | Oui | SaaS | Zero presence France |
| **Gemini Workspace Studio** | Partiellement (Gmail uniquement, sans donnees Pennylane) | Inclus | Pas de cross-system |
| **Freelance + Zapier** | Oui (zap basique) | ~200 EUR/mois maintenance | Pas d'intelligence, pas de patterns |
| **Officeo** | Oui (humain) | 38-50 EUR/h | Cout lineaire, pas de memoire |
| **Pennylane** | Non (comptabilite, pas relance) | -- | Pas d'agent |
| **Spider** | Oui + croisement donnees multi-sources + patterns comportementaux | 500 EUR/mois (bundled) | **AVANTAGE : intelligence cross-system + memoire cumulative** |

**Avantage Spider** : Spider sait que Schmidt Bayeux paie plus vite a J+15. Il sait que l'email "ton" du client X a change. Il croise la facture impayee avec l'email recus et la saisonnalite. Personne d'autre ne fait ca au prix PME.

---

### 8.2 CRM (Gestion de la relation client)

| Acteur | Peut-il le faire ? | Prix | Limite |
|--------|-------------------|------|--------|
| **HubSpot** | Oui, robuste | Freemium -> 800 EUR/mois | Complexe, configure par le patron |
| **Pipedrive** | Oui | 14-70 EUR/user/mois | Pas d'AI operationnelle |
| **folk CRM** | Oui (startup-friendly) | 17-40 EUR/user/mois | Pas de cross-system |
| **Axonaut** | Oui (basic) | 49 EUR/mois | Tres limite en AI |
| **Sellsy** | Oui (FR) | 29 EUR/user/mois | Pas d'agents autonomes |
| **Gemini + Workspace** | Partiellement (contacts Gmail) | Inclus | Pas de donnees ERP |
| **Freelance + Zapier** | Oui (zap vers CRM) | ~150 EUR/mois | Pas de raisonnement |
| **Spider** | Oui + graphe relationnel enrichi cross-system | 500 EUR/mois (bundled) | **AVANTAGE : relation enrichie avec historique email + factures + interactions** |

**Avantage Spider** : Spider construit un graphe relationnel qui integre les emails, les factures, les appels Noota, les commandes Odoo. Aucun CRM ne fait ca nativement. HubSpot gere le pipeline. Spider comprend la relation dans son integralite.

---

### 8.3 Marketing (Campagnes, contenu, prospection)

| Acteur | Peut-il le faire ? | Prix | Limite |
|--------|-------------------|------|--------|
| **HubSpot Marketing** | Oui, robuste | 800-3 200 EUR/mois | Trop cher pour petites PME |
| **Mailchimp** | Oui (email seulement) | 20-400 EUR/mois | Zero AI operationnel |
| **Clay** | Oui (enrichissement GTM) | 349 EUR/mois+ | US-focused |
| **Apollo.io** | Oui (prospection B2B) | 49 EUR/mois+ | Pas de connaissance sectorielle FR |
| **Gemini + Workspace** | Partiellement (redaction, scheduling) | Inclus | Pas de connaissance metier |
| **Freelance + Claude** | Oui (redaction, segmentation) | ~500 EUR/mois | Pas de persistance |
| **Spider** | Oui + segmentation basee sur donnees operationnelles | 500 EUR/mois (bundled) | **AVANTAGE : segments bases sur le comportement reel (qui a paye, qui a rappele, qui est rentable)** |

**Avantage Spider** : Spider segmente les clients non pas selon leur taille ou leur secteur, mais selon leur comportement reel dans les donnees operationnelles. Les "bons clients" de Spider sont ceux qui paient en 15 jours, commandent regulierement, et ont un taux de marge superieur. Aucun outil marketing ne sait ca.

---

### 8.4 Comptabilite / Finances (Suivi, alertes, analyse)

| Acteur | Peut-il le faire ? | Prix | Limite |
|--------|-------------------|------|--------|
| **Pennylane** | Oui (compta temps reel) | 35 EUR/mois+ | Compta seulement, pas operationnel |
| **Agicap** | Oui (tresorerie) | Custom (cher) | Tresorerie seulement |
| **Axonaut** | Oui (basic) | 49 EUR/mois | Tres limite en intelligence |
| **Sage** | Oui (compta) | 20 EUR/mois+ | Traditionnel, peu d'AI |
| **Gemini + Sheets** | Partiellement (si donnees dans Sheets) | Inclus | Pas de donnees Pennylane/banque |
| **DAF Externalisé** | Oui (expert humain) | 500-2 000 EUR/mois | Pas en temps reel, cher |
| **Freelance + Claude** | Oui (analyse one-shot) | ~300 EUR/analyse | Pas de monitoring continu |
| **Spider** | Oui + croisement compta + ops + email + banque | 500 EUR/mois (bundled) | **AVANTAGE : donnees croisees + alertes proactives + patterns temporels** |

**Avantage Spider** : Spider voit les factures Pennylane ET les emails commerciaux ET les tendances Odoo ET les flux Qonto. Il detecte que le cash sera short en juillet AVANT que ca arrive. Pennylane voit la compta. Spider voit l'avenir.

---

### 8.5 Diagnostic / Audit initial

| Acteur | Peut-il le faire ? | Prix | Limite |
|--------|-------------------|------|--------|
| **Cabinet conseil (Capgemini, etc.)** | Oui (missions de conseil) | 50 000-500 000 EUR | Trop cher pour PME |
| **Consultant independant** | Oui | 5 000-20 000 EUR | One-shot, pas de suivi |
| **DAF Externalisé** | Partiellement (financier seulement) | 2 000-5 000 EUR | Finance uniquement |
| **Odoo Community** | Non (ERP sans intelligence) | Gratuit | Outil, pas diagnostic |
| **Gemini + Workspace** | Non (pas de cross-system) | Inclus | Ne voit pas les donnees metier |
| **Freelance + Claude** | Partiellement (analyse one-shot) | 1 500-3 000 EUR | Sans persistance ni evolution |
| **Spider (Diagnostic Eclair)** | Oui (2h30 → prototype operationnel) | 1 990 EUR | **AVANTAGE : rapide + actionnable + débouche sur abonnement** |

**Avantage Spider** : Le Diagnostic Eclair est unique en son genre. 2h30 d'interview structuree, croisement des donnees disponibles (exports Odoo, fichiers Excel, emails), et livraison d'un prototype fonctionnel + rapport de 30 pages. Aucun concurrent ne fait ca au prix de 1 990 EUR avec cette rapidite.

---

### 8.6 Cartographie des processus (Process Mapping)

| Acteur | Peut-il le faire ? | Prix | Limite |
|--------|-------------------|------|--------|
| **Scribe** | Oui (capture auto de workflows) | 23 EUR/seat/mois | Capture seulement, pas d'intelligence |
| **Tango** | Oui (documentation auto) | Freemium | Idem |
| **Miro / Lucidchart** | Oui (cartographie manuelle) | 10-15 EUR/user/mois | 100% manuel |
| **Consultant BPM** | Oui (expert) | 2 000-10 000 EUR | One-shot |
| **Gemini + Workspace** | Non | -- | Pas de process understanding |
| **Freelance + Claude** | Partiellement (analyse conversationnelle) | 1 000-2 000 EUR | Sans ontologie formelle |
| **Spider** | Oui + ontologie formelle + mise a jour automatique | 500 EUR/mois (bundled) | **AVANTAGE : "speech-to-process" + ontologie qui evolue + connaissance sectorielle** |

**Avantage Spider** : Spider transforme une conversation de 2h30 avec le patron PME en une cartographie formelle des processus de l'entreprise. Cette ontologie s'affine avec le temps (nouvelles interactions, nouveaux patterns). Aucun outil de cartographie ne fait ca -- ils capturent l'existant, ils ne comprennent pas l'implicite.

---

### Synthese : Tableau de collision global

| Capacite Spider | Concurrent le plus fort | Prix concurrent | Avantage Spider | Vulnerable si... |
|----------------|------------------------|-----------------|-----------------|------------------|
| **Relances (AR)** | Upflow (300$/mois) | 300$/mois | Cross-system + memoire cumulative | Upflow integre Pennylane nativement |
| **CRM** | HubSpot (complexe) | 800 EUR/mois | Graphe relationnel enrichi | HubSpot lance un agent cross-ERP |
| **Marketing** | Clay / Apollo (US) | 349 EUR/mois | Segmentation operationnelle | Pennylane lance une feature marketing |
| **Compta/Finance** | Pennylane + Agicap | 35 + custom EUR/mois | Donnees croisees + alertes predictives | Pennylane + Agicap fusionnent |
| **Diagnostic** | Consultant independant | 5 000-20 000 EUR | Vitesse + prix + prototype imm. | Dust lance un "diagnostic SMB" |
| **Process Mapping** | Scribe + consultant | 23 EUR/mois + 5K EUR | Ontologie formelle + evolution auto | Google integre le process mapping dans Workspace |

---

## CONCLUSION STRATEGIQUE

### La fenetre de tir : 12-24 mois

Le mapping complet revele que Spider a une fenetre de 12 a 24 mois ou aucun concurrent n'est positionne exactement comme lui : intelligence operationnelle AI-native, cross-system, pour les PMEs europeennes, avec deploiement human-in-the-loop.

Cette fenetre se ferme a cause de :
- **Septembre 2026** : Odoo 20 avec AI agentique
- **12 mois** : Pennylane probable addition de features AI sur ses donnees
- **18 mois** : Gemini + MCP = potentielle connexion aux outils francais
- **Continu** : YC batchs trimestriels, 149 startups AI assistants deja financees

### Les 5 veritables raisons pour lesquelles Spider gagne (si il les execute)

1. **Le cross-system** : Gemini ne voit que Google. Zapier ne raisonne pas. Spider voit tout et comprend.
2. **Le deploiement humain** : 61% des PMEs francaises n'ont pas les competences numeriques pour configurer des agents. Spider les deploie pour elles.
3. **La memoire cumulative** : Le freelance part. Zapier casse. Claude oublie. Spider accumule.
4. **La connaissance sectorielle** : Apres 10 clients dans un secteur, Spider sait des choses que Gemini ne saura jamais.
5. **Le canal expert-comptable** : La confiance du comptable transferee vers Spider = adoption sans friction.

### Le concurrent reel : le statu quo

Le vrai concurrent de Spider n'est pas Dust, ni Gemini, ni Upflow. C'est **le patron PME qui ne fait rien, ou qui bricole avec Excel et email**. 80% des PMEs dans la cible de Spider n'ont aucun des outils listes dans ce document. Elles gèrent avec un tableau Excel, un email, et beaucoup d'intuition.

Spider ne compete pas d'abord contre des logiciels. Il compete contre l'inertie.

---

*Document compile le 21 fevrier 2026*
*Sources : R7-exhaustive-competitor-map.md (181 acteurs), R7b-missing-competitors.md (21 acteurs complementaires), MARKET-SCAN-LIVE.md (Feb 19-20 2026), THREAT-GEMINI-WORKSPACE.md*
*Prochaine mise a jour recommandee : apres Demo Day YC W26 et annonce Odoo Experience 2026*


---

## SECTION 9 : NOUVEAUX ENTRANTS 2025-2026 (Recherche du 21 fevrier 2026)

> Recherche complementaire couvrant les startups YC W26/S25/X25, les acteurs Service-as-Software, les AI roll-ups, et les startups europeennes physique. 28 acteurs identifies.

### 9.1 YC AI Accounting (concurrents wedge impayes)

| Startup | Batch | Funding | Ce qu'ils font | Menace Spider |
|---------|-------|---------|---------------|---------------|
| **Balance** | W26 | YC | AI accounting firm for SMBs — relance impayes, ferme les comptes | **HAUTE** — meme wedge |
| **Cranston AI** | W26 | YC | Plateforme compta IA full-stack, $21.5K MRR au lancement | MOYENNE |
| **Minerva** | X25 | YC + Amino + Goodwater | AI accounting via WhatsApp/Email/Stripe | MOYENNE — interface WhatsApp interessante |
| **Atlog** | W26 | YC | Agents compta end-to-end + voice AI compliance | BASSE |

### 9.2 YC Operations Agents (economie physique)

| Startup | Batch | Funding | Ce qu'ils font | Menace Spider |
|---------|-------|---------|---------------|---------------|
| **Corvera** | W26 | $2M | "Agentic OS for CPG brands" — orders, demand forecast, procurement, logistics | **HAUTE** — meme structure OS |
| **LineWise** | X25 | $1.1M | AI pour equipes manufacturing — SOP depuis video, troubleshooting guide | MOYENNE |
| **Tiny** | YC | YC | "AI ERP for factories" — cible les 4M usines sur Excel | **HAUTE** — meme segment |
| **Poka Labs** | YC | $500K | Production scheduling pour chimie manufacturiere | BASSE — tres vertical |
| **Toothy AI** | W25 | YC + seed | AI back-office dental — 30x croissance pendant le batch | BASSE mais modele a copier |

### 9.3 Construction AI (le vertical le plus actif)

| Startup | Pays | Funding | Ce qu'ils font | Menace Spider |
|---------|------|---------|---------------|---------------|
| **Brickanta** | Suede | $8M (Northzone) | "AI-native OS for construction" — bids, estimations, procurement. 11 pays, YC S25 | **CRITIQUE** — concurrent europeen direct |
| **Freeda** | France | €3.4M (Frst) | Verification plans construction IA, compliance 48h. 10K plans en 2025 | MOYENNE — narrow mais francais |
| **AI-BOB** | Suede | €2M | Compliance blueprints construction | BASSE |
| **Handoff** | US | YC | Devis construction IA en minutes | BASSE — US only |
| **Scout Out** | US | YC W26 | Estimating residential contractors | BASSE — US only |
| **Karmen** | ? | ? | AI scheduling + invoicing construction | MOYENNE |

### 9.4 Service-as-Software (benchmarks)

| Startup | Investors | Funding | Revenue | Ce qu'ils font | Signal pour Spider |
|---------|-----------|---------|---------|---------------|-------------------|
| **Salient** | a16z | $60M SerA | **$14M ARR, 10 ingenieurs** | AI debt collection (remplace les agents humains) | LE benchmark — $1.4M ARR/ingenieur |
| **Crescendo** | General Catalyst | $50M | **$91M ARR en 15 mois** | AI customer service BPO (acquis PartnerHero) | Trajectoire la plus explosive |
| **Artisan AI** | YC W24, $25M SerA | $37M | $5M ARR | "AI employees" — SDR IA (Ava) | "Stop Hiring Humans" = le pitch provocant |
| **Eudia** | General Catalyst | $105M SerA | ? | AI law firm — acquis un cabinet AZ | Structure $30M build + $75M acquire |

### 9.5 AI Roll-Ups (le modele de l'Acte 3 Spider)

| Entite | Backer | Capital | Resultats | Pourquoi ca compte |
|--------|--------|---------|-----------|-------------------|
| **Crete PA** | Thrive Capital | $500M acquisitions | 30+ cabinets, $300M ARR, 900 employes | Roll-up compta US + OpenAI |
| **Long Lake** | General Catalyst | $670M | **$100M EBITDA en <2 ans**, 18 businesses acquises | Le plus gros resultat GC |
| **Titan** | General Catalyst | $74M | 30% des workloads automatises chez clients | IT services → AI transformation |
| **Dwelly** | General Catalyst | ? | 6 agences acquises UK, 2000+ properties, **EBITDA x2 en 2 mois** | **LE plus proche de Spider en Europe** |
| **Elad Gil** | Personnel | ? | "2 douzaines" d'equipes evaluees, la plupart refusees | Cherche activement des equipes EU pour AI roll-ups |

### 9.6 Startups europeennes economie physique

| Startup | Pays | Funding | Ce qu'ils font | Menace Spider |
|---------|------|---------|---------------|---------------|
| **Augmented Industries** | Allemagne | €4.5M (b2venture) | AI pour techniciens industriels — SOP, troubleshooting, onboarding. Clients : Siemens, BMW, ZF | MOYENNE — grands industriels pas PME |
| **Brickanta** | Suede | $8M (Northzone) | OS construction (voir 9.3) | CRITIQUE |
| **Freeda** | France | €3.4M (Frst) | Plans construction (voir 9.3) | MOYENNE |
| **Dwelly** | UK | GC-backed | Lettings AI roll-up (voir 9.5) | BASSE — immobilier pas meme vertical |

### 9.7 AI ERP (remplacants potentiels)

| Startup | Funding | Ce qu'ils font | Menace Spider |
|---------|---------|---------------|---------------|
| **Campfire** | $35M (Accel, YC) | AI-native ERP remplacant NetSuite. 100 clients. Close mensuel 15j → 3j | MOYENNE — mid-market US, pas PME FR |

### 9.8 Les 5 signaux strategiques

1. **L'Europe a 18 mois de retard.** Tous les acteurs majeurs sont US-first. Brickanta (Suede) et Freeda (France) sont les seuls europeens avec traction dans l'economie physique. **Le marche europeen PME physique est GRAND OUVERT.**

2. **La "Creation Strategy" de General Catalyst EST le playbook.** Crescendo ($91M ARR en 15 mois), Long Lake ($100M EBITDA en <2 ans), Dwelly (EBITDA x2 en 2 mois). **Aucun acteur europeen n'execute ce playbook pour les PME physiques.**

3. **Le wedge compte plus que la vision.** Salient (recouvrement), Toothy (assurance dentaire), Brickanta (estimation BTP). Chacun a domine UN point de douleur avant d'elargir.

4. **Le pricing outcome-based est le standard.** Pas de per-seat. Pas de per-user. Des resultats : appels traites, factures reconciliees, heures economisees.

5. **Elad Gil cherche des equipes pour des AI roll-ups europeens.** Il a vu "deux douzaines" d'equipes et refuse la plupart. Si Spider pitche Gil avec le modele "AI transformation des PME physiques europeennes", c'est peut-etre exactement ce qu'il cherche.
