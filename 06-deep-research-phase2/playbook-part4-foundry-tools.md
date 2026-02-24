# PARTIE 4 — FOUNDRY : L'OUTIL EN DÉTAIL

---

## 4.1 Architecture Globale

### 4.1.1 Rubix — La Couche d'Abstraction Infrastructure

Rubix est la couche d'abstraction Kubernetes propriétaire de Palantir. Elle masque le cluster K8s sous-jacent (EKS, AKS, GKE, OpenShift, bare-metal) et fournit une surface de déploiement standardisée pour les microservices de Foundry. [CONFIRMED]

**Caractéristiques techniques :**

- Environ **150+ microservices** par instance Foundry [CONFIRMED]
- Chaque microservice est déployé, versionné et monitoré indépendamment via Apollo
- Rubix gère : service discovery, load balancing, gestion des secrets, health checks
- **Éphéméralité des noeuds** : chaque noeud est recyclé dans les **48 heures** (exigence architecturale stricte empêchant l'accès persistant d'un attaquant)
- Isolation des workloads : sécurité multi-tenant pour le code auteur (PySpark des clients)
- Chiffrement partout : chaque interaction requiert authentification, autorisation, journalisation immutable
- Conformité : FedRAMP High, DoD DISA IL-5/IL-6, CMMC
- Sécurité réseau via Cilium (segmentation réseau), pod security contexts, patterns d'infrastructure immutable

**k8s-spark-scheduler** (open-source `palantir/k8s-spark-scheduler`) : Kubernetes Scheduler Extender fournissant du **gang scheduling** pour Spark. Garantit qu'un driver n'est schedulé que s'il y a de l'espace pour tous ses executors. Algorithmes de détection de demande pour requêter de nouveaux noeuds proactivement. Modes bin-packing : `distribute-evenly` ou `tightly-pack`.

**Autoscaling intelligent :** algorithmes de détection de demande, distribution de workloads optimisant les coûts (AWS, Azure, GCP, Oracle). Apollo calcule et transmet des plans de déploiement pour des rollouts **zero-downtime blue/green**.

### 4.1.2 Les 4 Plateformes

| Plateforme | Année | Cible | Description |
|------------|-------|-------|-------------|
| **Gotham** | 2008 | Renseignement et défense | Produit originel. Architecture EAV/CR (Entity-Attribute-Value with Classes and Relationships). 6 applications : Graph, Gaia, Browser, Object Explorer, Dossier, Inbox. Subsystèmes : AtlasDB (ACID sur Cassandra), RevDB (temporal queries), Horizon (in-memory analytics), Raptor (federated search). |
| **Foundry** | 2016 | Entreprise commerciale | OS d'entreprise généraliste. Généralise l'architecture Gotham pour la supply chain, le manufacturing, la santé, la finance, l'énergie. Substrat sur lequel AIP s'exécute. Principal moteur de revenus. |
| **AIP** | 2023 | Couche IA | Artificial Intelligence Platform. Les LLMs reçoivent des **objets Ontologie typés**, pas du texte brut. Composants : AIP Logic, Agent Studio, Language Model Service (50+ modèles). |
| **Apollo** | Continu | Déploiement | Plateforme de livraison continue. Modèle pull constraint-based. Hub-spoke. 300+ environnements. Disponible standalone (~$100/install/mois). |

**Interopérabilité :** Gotham tourne désormais sur Foundry comme couche de base. Un système de mapping de types cross-plateforme permet de traiter les entités Gotham et Foundry comme synonymes. [CONFIRMED]

### 4.1.3 Le Data Flow en Boucle Fermée — 7 Étapes

Le pattern architectural définissant de Palantir est la **boucle fermée en 7 étapes**. Contrairement aux outils BI traditionnels qui s'arrêtent à la visualisation (étape 6), Palantir ferme la boucle en écrivant les décisions dans les systèmes source (étape 7). [CONFIRMED]

> "Les outils BI s'arrêtent à l'étape 6. Palantir ferme la boucle."

| Étape | Nom | Ce qui se passe | Technologie clé |
|-------|-----|----------------|-----------------|
| **1** | Sources | Les données brutes proviennent des systèmes opérationnels | ERP (SAP, Oracle), CRM (Salesforce), capteurs IoT, fichiers, bases de données, APIs |
| **2** | Data Connection | 150+ connecteurs natifs ingèrent les données via 3 architectures de connexion | Framework Data Connection (direct, proxy agent, worker air-gapped) |
| **3** | Pipelines | Les données sont transformées, nettoyées, enrichies et façonnées pour l'Ontologie | Pipeline Builder (DAG visuel), Code Repos, Spark/Flink/DuckDB |
| **4** | Ontologie | Les données transformées sont mappées sur des Object Types, Properties et Links typés | OMS, Object Storage V2, pipeline Funnel, Elasticsearch |
| **5** | AIP / Agents | Les agents IA raisonnent sur des objets Ontologie typés via architecture tool-use | AIP Logic, Agent Studio, Language Model Service (50+ modèles) |
| **6** | Applications | Les applications opérationnelles rendent les objets Ontologie dans des interfaces dédiées | Workshop (app builder low-code), Quiver, Contour, Slate |
| **7** | Actions | Les décisions sont exécutées comme des Actions Ontologie, qui écrivent dans les systèmes source | Actions Service, connecteurs writeback, webhooks, appels API |

**Flux traditionnel BI :** Sources -> Pipelines -> Dashboard -> FIN

**Flux Palantir :** Sources -> Pipelines -> Ontologie -> IA -> App -> Action -> Sources (boucle)

---

## 4.2 L'Ontologie — Le Coeur du Système

L'Ontologie est le noyau de tout produit Palantir. Ce n'est pas un simple catalogue de métadonnées ou un registre de schéma — c'est un **modèle de données opérationnel vivant** à travers lequel toutes les données sont accédées, toutes les actions exécutées, toute l'IA raisonne, et toute la sécurité est appliquée. [CONFIRMED]

### 4.2.1 Les 6 Primitives

L'Ontologie est construite à partir d'exactement six types primitifs. Tout dans Palantir — chaque widget UI, chaque outil d'agent IA, chaque endpoint API, chaque règle de sécurité — opère sur ces six primitives :

#### 1. Object Types (Tables / Classes d'Entités)

Les définitions d'entités fondamentales du domaine métier. Chaque Object Type définit une classe d'entités avec un ensemble fixe de propriétés typées.

- **Analogie** : une table dans une base de données relationnelle, ou une classe d'entités
- **Exemples** : `Client`, `Commande`, `Produit`, `Entrepôt`, `Expédition`
- Chaque Object Type est adossé à **exactement un dataset** (backing dataset)
- L'ID du type d'objet ne peut pas être modifié après le premier déploiement
- Identifié par un `ontologyRid` stable et immutable ; les noms sont des alias mutables

#### 2. Properties (Colonnes / Attributs)

Attributs typés appartenant à un Object Type. Chaque propriété a un nom, un type, et des métadonnées (searchable, sortable, display name).

- **Analogie** : une colonne dans une table
- **Exemples** : `name` (String), `amount` (Double), `date` (Date), `status` (String), `geolocation` (GeoPoint)

**Types de base supportés :**

| Catégorie | Types |
|-----------|-------|
| **Texte / Booléens** | `String`, `Boolean` |
| **Numériques** | `Integer`, `Short`, `Byte`, `Long`, `Float`, `Double`, `Decimal` |
| **Temporels** | `Date`, `Timestamp` |
| **Géospatiaux** | `GeoPoint`/`Geohash`, `GeoShape`, `GeotimeSeriesReference` |
| **Complexes** | `Array` (pas de null ; pas de nested arrays en OSv2), `Struct` (pas de nesting ; champs ne peuvent pas être des arrays ; max 10 champs), `Vector` (pour embeddings ML) |
| **Spéciaux** | `Attachment`, `MediaReference`, `Timeseries`, `Marking`, `CipherText`/`Cipher` |

[CONTRADICTION] **Types Set et Map** : une source (Claude) liste `Set` et `Map` comme types supportés. Les autres sources ne les mentionnent pas dans les types de propriétés ontologiques et citent explicitement une liste "load-bearing" qui ne contient ni Set ni Map.

**Contraintes sur les types :**
- `Long` : problèmes de représentation JavaScript ; souvent recommandé d'utiliser String à la place
- `Decimal` : ne peut pas être primary key
- `Timestamp` : comme primary key est déconseillé
- `Array` : pas d'éléments null, pas de nested arrays en OSv2
- `Struct` : pas de nesting (profondeur 1), max 10 champs, types de champs limités, sémantiques de requête non-intuitives pour les arrays de structs (indexation ElasticSearch object field)

#### 3. Link Types (Foreign Keys / Relations)

Relations dirigées et typées entre Object Types. Chaque lien a un nom, une cardinalité, et peut porter ses propres propriétés.

- **Analogie** : une clé étrangère / un join entre tables
- **Exemples** : `"commandé par"`, `"contient"`, `"assigné à"`, `"expédié depuis"`
- **Cardinalités supportées** : 1:1, 1:N, N:1, M:N
- Les liens ne sont PAS stockés comme des edges dans un graph database — ils sont résolus au moment de la requête par jointure sur les colonnes de clé étrangère spécifiées dans les backing datasets
- L'UI auto-crée le lien inverse

[CONTRADICTION] **Résolution des liens** : une source affirme catégoriquement que les liens sont résolus "at query time by joining on foreign key columns." D'autres sources disent que les liens sont créés en ajoutant des backing datasources aux object types. Les sources s'accordent sur le fait que c'est un mécanisme relationnel (join), pas un graphe, mais le moment exact de la résolution fait débat.

#### 4. Action Types (Stored Procedures / Endpoints API)

Opérations typées qui mutent l'Ontologie. Les Actions sont le **SEUL moyen** d'écrire des données via la couche Ontologie. Elles incluent des règles de validation, des effets de bord, et un audit logging.

- **Analogie** : une stored procedure ou un endpoint API d'écriture
- **Exemples** : `"approuver commande"`, `"assigner tâche"`, `"escalader cas"`, `"mettre à jour statut"`
- **Composants** : paramètres (inputs requis), logique (créer/modifier/supprimer objets et liens), critères de soumission (règles métier), permissions, writeback dataset

#### 5. Interfaces (Classes Abstraites / Protocoles)

Types abstraits que les Object Types peuvent implémenter. Les Interfaces définissent un contrat (ensemble de propriétés et liens) que plusieurs Object Types partagent, permettant des requêtes et composants UI polymorphiques.

- **Analogie** : une interface Java ou un protocole Swift
- **Exemples** : `Trackable` (implémenté par Order, Shipment, Asset), `Assignable` (implémenté par Task, Incident), `HasLocation` (avec `latitude: Double`, `longitude: Double`)
- Non adossées à des datasets, non instanciables
- Propriétés d'interface : contraintes abstraites que les Object Types implémentants doivent mapper sur des propriétés concrètes
- Contraintes de link type : liens abstraits avec cardinalité (`ONE` ou `MANY`), pouvant être marqués `required`

#### 6. Functions (Colonnes Calculées / UDFs)

Computations TypeScript ou Python enregistrées dans l'Ontologie. Les Functions reçoivent des objets Ontologie typés en entrée et retournent des résultats typés. Appelables depuis les UIs, workflows, agents et autres fonctions.

- **Analogie** : une colonne calculée ou une User-Defined Function
- **Exemples** : `calculateRiskScore(client)`, `estimateDeliveryTime(shipment)`, `findNearestWarehouse(order)`
- Écrites en **TypeScript** dans un Functions Repository / Code Repository dédié
- L'Ontology Manager expose un "Function type view" mais les modifications se font dans le repository de code

### 4.2.2 Les 3 Couches

Les six primitives sont organisées en trois couches architecturales :

#### Couche 1 : SEMANTIC — WHAT — Le Modèle de Données

Définit les entités métier, leurs propriétés et leurs relations. C'est la colonne vertébrale structurelle. Répond à la question : "Qu'est-ce qui existe dans le monde ?"

- Définitions d'Object Types avec propriétés typées
- Définitions de Link Types avec contraintes de cardinalité
- Contrats d'Interface pour l'accès polymorphique
- Versioning de schéma avec identifiants stables (`ontologyRid`)

#### Couche 2 : KINETIC — HOW — Les Flux Temps Réel

Définit comment les données circulent dans le système et comment le système agit sur le monde. C'est la couche opérationnelle.

- Action Types avec règles de validation et effets de bord
- Functions (computations TypeScript/Python)
- Writeback vers les systèmes source (ERP, CRM, bases de données)
- Webhooks pour l'intégration event-driven
- Flux streaming temps réel (Flink-powered)

#### Couche 3 : DYNAMIC — GUARDRAILS — Sécurité & Gouvernance

Définit les contraintes qui gouvernent tout accès et toute mutation. Cette couche est pervasive — elle s'applique à chaque lecture, chaque écriture, chaque inférence IA, chaque rendu UI.

- RBAC (Role-Based Access Control) par objet, par propriété, par ligne
- Markings obligatoires (labels de classification qui voyagent avec les données)
- Audit logging complet de chaque accès et mutation
- Tracking de provenance de la source à la sortie dérivée
- Indexation temps réel pour la recherche et la découverte

### 4.2.3 Backend Services

| Service | Responsabilité | Détail technique |
|---------|---------------|------------------|
| **OMS** (Ontology Metadata Service) | Stockage de schéma | Stocke toutes les définitions : Object Types, Properties, Link Types, Action Types, Interfaces, Functions. Source unique de vérité pour "ce qui existe dans l'Ontologie." [CONFIRMED] |
| **Object Storage V2** | Persistance et indexation | Deux sous-composants : (1) **Data Funnel** — Pipeline batch : `génération de changelog` -> `merge avec edits` -> `build des artefacts de recherche` -> `cutover atomique vers le nouvel index`. (2) **Object Databases** — Stores indexés optimisés pour les lectures rapides. [CONFIRMED] |
| **OSS** (Object Set Service) | Moteur de requête | Gère toutes les opérations de lecture : requêtes de recherche, filtrage, agrégation, résolution d'Object Set. Un "Object Set" est une collection dynamique, évaluée paresseusement, d'objets matchant un prédicat — l'abstraction de requête fondamentale utilisée par toutes les UIs, APIs et agents IA. [CONFIRMED] |
| **Actions Service** | Écritures transactionnelles | Exécute toutes les mutations via l'Ontologie. Utilise la **concurrence optimiste** : les lectures sont lock-free, les écritures sont validées au moment du commit. Si un conflit est détecté, la transaction est rejetée et le client doit retenter. [CONFIRMED] |

**Pipeline Funnel — 5 étapes batch :**
1. **Source Read** — lire les dernières données du backing dataset
2. **Diff / Changelog Generation** — comparer avec la version précédente pour identifier les objets changés, ajoutés et supprimés
3. **Merge with User Edits** — appliquer le log d'edits pour résoudre les conflits entre données pipeline et modifications utilisateur
4. **Build Search Artifacts** — construire les documents Elasticsearch avec toutes les propriétés indexées, références de liens et champs calculés
5. **Atomic Cutover** — swapper l'ancien index avec le nouveau atomiquement

Pour les sources streaming (Flink), le Funnel opère en mode quasi temps réel avec mises à jour incrémentales.

### 4.2.4 Ontology Manager UI

#### Anatomie de l'Interface (3 zones)

L'Ontology Manager (OMA) est accessible depuis la sidebar de navigation de Foundry. C'est l'application centrale où les développeurs définissent le modèle de données.

| Zone | Contenu |
|------|---------|
| **Top bar** | Recherche globale sur les ressources ontologiques, création de nouvelles ressources ("+ Create" / "New"), switching/création de branches |
| **Sidebar gauche** | Navigateur de ressources avec vue "Discover" configurable (favoris, types récemment consultés, groupes). Arborescence hiérarchique de tous les Object Types, Link Types et Interfaces avec recherche. |
| **Zone centrale** | Panneau affichant la configuration de l'entité sélectionnée, avec onglets : Overview, Properties, Links/Datasources, Actions, Permissions, Interfaces |

[CONTRADICTION] **Localisation du bouton de création** : une source décrit le bouton dans la top bar, une autre dans le toolbar, une troisième en haut à droite de la homepage avec un dropdown "New". Les trois décrivent le même workflow mais situent le bouton différemment dans l'UI.

**Vues d'entités distinctes :**
- **Object type view** : sous-sidebar gauche avec pages (Overview, Properties, Datasources, Interfaces) et panneau droit avec le contenu de la page sélectionnée
- **Property editor view** : interface d'édition dédiée ouverte en sélectionnant une propriété
- **Link type view** : ouverte depuis le graphe de types de liens, avec pages Overview/Datasources
- **Action type view** et **Function type view** : chacune avec ses propres onglets d'observabilité ; les fonctions sont éditées dans un code repository, pas en inline

**Modèle mental** : l'Ontology Manager se comporte comme un **"schema IDE git-branch-aware"** où tout est staged puis commité dans l'ontologie.

#### Création d'un Object Type — Step-by-Step (6 étapes)

Palantir documente deux méthodes : un **assistant guidé** (chemin principal) et une **complétion manuelle** si on sort tôt de l'assistant.

1. **Cliquer** sur "New > Create object type" / "+ Create Object Type" depuis l'Ontology Manager
2. **Entrer un display name** (ex: "Customer") et un **API name** (auto-généré, ex: `customer`, mais éditable). Optionnellement choisir une icône et écrire une description
3. **Sélectionner un backing dataset** — parcourir ou rechercher dans le catalogue de données Foundry et pointer vers un dataset. **Chaque Object Type est adossé à exactement un dataset.** Si on n'a pas encore de dataset, Foundry peut générer un dataset vide à l'emplacement choisi (Object Storage V2 uniquement)
4. **Définir le primary key** — sélectionner la colonne qui identifie uniquement chaque instance d'objet. Le primary key doit être unique, déterministe, pas aléatoire. Le timestamp comme primary key est explicitement déconseillé
5. **Mapper les colonnes vers des propriétés** — l'UI auto-détecte les colonnes et suggère des mappings. Un bouton "Add all unmapped columns as new properties" infère IDs, display names et base types depuis le schema du dataset source. L'éditeur a deux panneaux : colonnes datasource à gauche, propriétés mappées à droite
6. **Configurer le title key** — la propriété qui sert de nom d'affichage dans les UIs (ex: `full_name` pour un Employee)

**Étapes optionnelles :**
- Générer des actions standard — l'assistant peut auto-créer des Action Types edit/create/delete et les assigner à un utilisateur/groupe
- Choisir un projet d'enregistrement et cliquer "Create" (cela stage les changements seulement). Puis cliquer **"Save"** en haut à droite de l'Ontology Manager pour appliquer à l'ontologie

**Si on quitte l'assistant tôt** : l'object type reste "unsaved" jusqu'à ce qu'on complète manuellement la checklist : ajouter metadata, ajouter un backing datasource, ajouter des propriétés, mapper les propriétés, configurer primary et title keys.

#### Définition des Properties (types disponibles)

**Éditeur de métadonnées de propriété :** display name, description, statut (experimental/active/deprecated), API name, désignation de clé (title/primary), formatage de valeur, formatage conditionnel, type classes, render hints (toggles searchable/sortable affectant le comportement d'indexation), et visibilité (prominent/hidden).

L'édition peut être faite individuellement ou en **bulk** (changement de base type, ajout/suppression de type classes, render hints, visibilité, formatage).

**Struct** : créé en choisissant "Struct" comme base type, en sélectionnant une colonne backing, puis en ajoutant des champs dans une section "Struct fields". Permet des champs JSON-like structurés — ex: une struct Address avec `street`, `city`, `zip`. Mais n'est **pas** un type "nested JSON" général : c'est une feature de schema contrainte (profondeur 1, max 10 champs).

**Media references** : "juste un base type", mais nécessite que le dataset de support contienne une colonne de référence media et que l'object type ait une media source configurée dans son onglet Capabilities pointant vers le media set correspondant.

#### Création des Links (cardinalité)

**Création :** Naviguer vers Ontology Manager > `New > Link type`, ou depuis la page Overview d'un object type > "Create new link type" depuis le graphe de types de liens.

**Cardinalités supportées :** 1:1, 1:N, N:1, M:N

**Mécanique des clés étrangères :**
- Pour 1:1 ou M:1 : définir une **foreign key** sur un object type qui réfère au **primary key** de l'autre. Exemple : `Flight.tailNumber` (FK) -> `Aircraft.tailNumber` (PK)
- Pour M:N : un **troisième backing dataset** (table de jonction) est requis. Ce dataset ne nécessite que les colonnes primary key des deux object types. Chaque ligne représente une instance de lien.

**Object-backed link types** : construct de modélisation de première classe. On peut représenter une relation comme son propre object type pour stocker des métadonnées sur la relation elle-même (exemple : un objet Flight Manifest liant Aircraft et Flight, avec des propriétés supplémentaires comme Pilot). Règle : "si vous avez besoin d'attributs sur l'edge, Foundry vous dit de promouvoir l'edge en un object-backed link."

**Dans les bindings TypeScript** : le côté "1" donne un `SingleLink` et on appelle `get()` ou `getAsync()`.

L'UI auto-crée le lien inverse. Après soumission, il faut **sauvegarder dans l'Ontology Manager** pour appliquer.

**Convention de nommage API** : côté pluriel en pluriel (`subordinates`, pas `subordinate`). Noms sémantiques distincts pour liens multiples entre mêmes types.

#### Interfaces (types abstraits)

**Création :**
1. Sélectionner New > Interface (ou via la page Interfaces)
2. Fournir display name et API name, description optionnelle et icône
3. Ajouter des propriétés à l'interface, marquer chacune `required` ou `optional`

**Propriétés d'interface** : contraintes de propriétés abstraites que les object types implémentants doivent mapper sur des propriétés concrètes.

**Contraintes de link type d'interface** : liens abstraits avec une cardinalité (`ONE` ou `MANY`), description, API name, et une entité liée qui peut être une autre interface ou un object type concret. Flag `required` pour indiquer si chaque object type implémentant doit fournir au moins une implémentation d'un lien donné.

**Exemple** : une interface `Facility` déclare un lien optionnel one-to-many vers `Airline`. `Airport` et `Seaport` peuvent tous deux implémenter `Facility`, chacun fournissant son propre lien concret vers `Airline`.

**Implémentation :**
1. Depuis l'onglet Interfaces d'un object type, sélectionner "Implement new interface"
2. Choisir l'interface, puis mapper les propriétés requises de l'interface sur des propriétés existantes de l'objet (les propriétés optionnelles peuvent être omises)
3. Si l'interface déclare des contraintes de link type requis, mapper des link types qui satisfont chaque contrainte

**Cas d'usage concret** : un widget map Workshop peut afficher tous les objets "HasLocation" (interface avec `latitude: Double`, `longitude: Double`) quel que soit le type concret — cela active les requêtes polymorphiques.

**Limitation** : l'implémentation des interfaces dans Pipeline Builder supporte le mapping de propriétés, mais **ne supporte pas le mapping de contraintes de link type** ; cela doit être fait dans Ontology Manager.

#### Functions (TypeScript computed)

**Environnement** : les Functions sont écrites en **TypeScript** dans un Functions Repository / Code Repository dédié.

**API TypeScript v1 :**

```typescript
import { Function } from "@foundry/functions-api";
import { Objects, Customer } from "@foundry/ontology-api";

export class CustomerFunctions {
  @Function()
  public getCustomerOrderCount(customer: Customer): Integer {
    const orders = customer.orders.all();  // traverse un lien
    return orders.length;
  }

  @Function()
  public getHighValueCustomers(): Customer[] {
    return Objects.search()
      .customer()
      .filter(c => c.totalSpend.gt(10000))
      .all();
  }
}
```

Les fonctions utilisent le decorator `@Function()`, l'accès type-safe auto-généré à l'ontologie via `@foundry/ontology-api`, la traversée de liens, et peuvent être exposées comme propriétés computées sur des Object Types ou comme handlers d'Actions via `@Action()`.

**API TypeScript v2** : utilise `@osdk/functions` avec `createEditBatch`, `Edits.Object<T>` et `Edits.Link<T>` types pour les edits batch.

**Edit Functions** : annotées avec `@OntologyEditFunction()` et `@Edits(ObjectType)`. Peuvent créer des objets (`Objects.create().ticket(primaryKey)`), modifier des propriétés (`employee.lastName = newName`), set/remove links, et supprimer des objets.

**Capacités** : lecture de propriétés, traversée de liens, edits ontologiques, résultat utilisable dans Workshop et Actions. L'Object Table de Workshop supporte les "derived columns generated on-the-fly via a Function".

**Gestion des timestamps** : utiliser `Timestamp.fromISOString(...)` depuis l'API functions de Foundry.

Les fonctions alimentent les Action Types (writeback), les valeurs computées Workshop, et les intégrations AIP Logic.

### 4.2.5 Decision Framework — Object Type vs Property vs Link vs Struct

**Analogie fondamentale :** Object Type = Dataset, Object = Row, Property = Column, Link = Join

**Heuristique FDE :** "Can someone walk up to this entity and ask questions about it in isolation?" Si oui, c'est un Object Type. Variante : "Will someone ever search for, filter on, or take an action on this entity independently?" Si oui -> Object Type.

#### Quand créer un Object Type

- L'entité a sa propre identité et cycle de vie (primary key stable, créée/modifiée indépendamment)
- L'entité a besoin d'être liée depuis plusieurs endroits
- La "relation" elle-même a besoin d'attributs -> object-backed link types
- L'entité a ses propres propriétés indépendamment consultées/filtrées
- Les utilisateurs doivent prendre des actions dessus indépendamment
- Elle a **plus de 2-3 attributs**
- Elle a besoin de permissions indépendantes

#### Quand garder comme Property

- Attribut concernant uniquement l'objet parent, pas de cycle de vie propre
- Attribut simple de 1-3 champs, unique à son parent, jamais requêté indépendamment, change toujours avec le parent
- On bénéficie de render hints, formatage et contrôles de searchabilité au niveau propriété

#### Quand utiliser un Link

- La relation est navigationnelle et queryable comme une relation, pas juste un string foreign key
- L'entité est partagée entre plusieurs parents

#### Quand utiliser un Struct

- Groupe borné de champs imbriqués qui se comporte comme "une propriété"
- Groupe logiquement lié de champs appartenant à l'objet parent mais avec structure nestée
- On peut vivre avec les contraintes strictes : profondeur 1 (pas de nesting), max 10 champs, types de champs limités, sémantiques de requête non-intuitives pour les arrays de structs

#### L'exemple Customer Address

**Adresse comme simple attribut (Property) :** quand l'adresse est single-valued, change rarement, n'est pas une entité indépendante. Implémentation : quelques propriétés comme `street`, `postcode`, `city`, `country` mappées directement depuis le backing dataset.

**Adresse comme sous-structure bornée (Struct) :** quand on veut "adresse" comme un seul champ conceptuel mais avec des composants structurés, en restant dans les contraintes de struct. Si les adresses n'ont pas besoin de cycle de vie indépendant, liens ou actions.

**Adresse comme entité de première classe (Object Type lié) :** quand les adresses ont leur propre cycle de vie — adresses multiples par client, historique, workflows de validation, géo-enrichissement, déduplication, ou permissions au niveau adresse. Lien Customer <-> Address ; la relation peut être "one-to-many" ou "many-to-many" si partagée.

**Extra Foundry** : si on a besoin de metadata sur la relation elle-même (ex: "address type", "valid from/to", "verified by", "source system"), les object-backed links sont le pattern canonique.

#### Principes de design FDE

- **Start from user workflows, not data models**
- **Ne pas sur-normaliser** — Foundry favorise la **dénormalisation** pour la performance de requête
- **Choisir des primary keys stables et immutables** ; les composite keys doivent être concaténés en une seule colonne
- **Linker avec parcimonie** — chaque lien ajoute de la complexité de requête
- **Utiliser les interfaces** pour les préoccupations transversales plutôt que dupliquer des propriétés
- Modeler pour les **workflows opérationnels d'abord**, puis pour l'analytique

### 4.2.6 Schema Evolution

#### OSv1 vs OSv2

**OSv1 (Phonograph)** : ne peut PAS migrer les user edits en cas de changements breaking ; les changements de schema sont découragés et peuvent nécessiter un unregister/reregister des datasources, risquant la perte d'historique d'edits.

**OSv2** : introduit un **framework de migration intégré** qui détecte automatiquement les changements breaking, affiche un warning, introduit un onglet Migrations dans le flux "Review changes", et bloque la sauvegarde jusqu'à ce qu'une option de migration soit spécifiée.

[CONTRADICTION] **Existence d'un outil de migration** : une source affirme que "Foundry's ontology has no built-in migration tool comparable to Flyway or Liquibase. Schema changes are manual." D'autres sources décrivent un framework de migration intégré dans OSv2 détaillé. La contradiction s'explique probablement par le fait que la première source décrit l'état général/OSv1 tandis que les autres décrivent la fonctionnalité OSv2 spécifique.

#### Breaking vs Non-Breaking Changes

**Changements non-breaking (pas de migration nécessaire) :**
- Ajouter une nouvelle propriété
- Changer display names, descriptions, title key, render hints, type classes, visibilité
- Réordonner les propriétés
- Supprimer ou changer des champs qui n'ont jamais reçu d'edits

**Changements breaking :**
- Changer les datasources d'entrée
- Changer le primary key
- Changer le type d'une propriété
- Changer le property ID si la propriété a des edits
- Supprimer des propriétés éditées ou des champs de struct
- Changer le type d'un champ de struct

#### Framework de migration OSv2

Quand on fait un changement breaking, l'Ontology Manager le détecte automatiquement et bloque la sauvegarde jusqu'à ce qu'on sélectionne une migration depuis l'onglet **Migrations** :

| Migration | Cas d'usage |
|-----------|-------------|
| **Drop all property edits** | Supprimer une propriété sans remplacement |
| **Drop all struct field edits** | Restructuration de struct |
| **Drop all edits** | Reset complet vers l'état datasource |
| **Move edits** | Renommer une propriété ou déplacer vers un nouveau backing dataset |
| **Cast property to new type** | Changer `String` -> `Integer`, etc. (~30 conversions supportées) |
| **Move struct field edits** | Restructuration au sein d'un struct |
| **Revert migration** | Annuler une migration précédemment appliquée |

**Limite** : max 500 migrations de schema à la fois ; les migrations de propriété primary key ne sont pas supportées par le framework.

#### Replacement Pipeline Pattern

Quand on sauvegarde un changement breaking :
1. Une nouvelle version de schema est créée en backend
2. Un **"replacement Funnel batch pipeline"** est orchestré pour mettre à jour l'index de l'object type
3. La nouvelle version devient queryable une fois le remplacement terminé et la nouvelle version déclarée entièrement hydratée par les object databases

Ce mécanisme est **versionné via un pipeline de rebuild d'index**, pas une mutation in-place.

#### Pattern Side-by-Side (pour changements majeurs)

Pour les cas hors OSv2 ou pour des changements majeurs :
1. Créer une nouvelle version du backing dataset avec le nouveau schema
2. Créer un nouvel Object Type (ex: `CustomerV2`)
3. Migrer tous les consommateurs (Workshop apps, Functions, OSDK clients)
4. Tester dans une branche de développement
5. Basculer et déprécier l'ancien type

#### Branching et Ontology-as-Code

Foundry supporte le **branching de datasets et de code** — on peut faire des changements de schema sur une branche, pointer l'Ontology Manager vers cette branche pour tester, valider, puis merger.

Pour les utilisateurs avancés, les définitions de schema ontologique peuvent être **exportées en JSON**, éditées en externe, et réimportées, permettant des workflows "ontology as code". C'est puissant mais opérationnellement risqué : on bypass les guardrails UI.

---

## 4.3 Pipeline Builder & Code Repositories

### 4.3.1 Pipeline Builder (Visuel)

Pipeline Builder est un constructeur **basé sur un graphe DAG** avec une vue canvas comme élément principal. [CONFIRMED]

#### UI : canvas, noeuds, connexions

| Zone | Contenu |
|------|---------|
| **Panneau/sidebar gauche** | Parcours/recherche de datasets d'entrée |
| **Canvas central** | Noeuds connectés par des edges montrant le flux de données, avec outils de panning/drag-select/layout. Les utilisateurs tirent des cercles de sortie blancs pour dessiner des connexions |
| **Panneau/sidebar droit** | Configuration du noeud sélectionné ; panneau Outputs montrant datasets outputs + outputs orientées ontologie (object types et link types) |
| **Panneau de preview en bas** | Échantillonnage des données du noeud sélectionné ; la preview se met à jour en temps réel |

**Supports additionnels :** Folders, Color Groups, Text Nodes, Checkpoints, Job Groups.

#### 80+ transforms disponibles (par catégorie)

**Types de noeuds Input :**
- Foundry datasets (batch ou streaming)
- Données générées/synthétiques
- Dataset syncs

**Transforms (70+ disponibles) :**

| Catégorie | Noeuds |
|-----------|--------|
| **Structural** | Filter (conditions AND/OR composées), Sort, Limit, Top rows, Drop duplicates, Deduplicate (avec stratégie de ranking) |
| **Jointures** | Inner, Left, Right, Full Outer, Cross, Semi, Anti, Mapping, KNN |
| **Agrégation/Windowing** | Aggregate (SUM, COUNT, AVG, MIN, MAX, COUNT DISTINCT, STDDEV, PERCENTILE, COLLECT_LIST — group-by, batch seulement), Aggregate over window, Project over window, Window Functions (ROW_NUMBER, RANK, LAG, LEAD, running aggregates) |
| **Reshaping** | Pivot (valeurs pivot fournies avant runtime pour schema connu), Unpivot, Flatten/Explode (pour arrays), Array elements to columns, Flatten struct |
| **Combinaison** | Union by name (retient les doublons, combine toutes les lignes), Narrow/Wide union |
| **Colonnes** | Select/Drop columns, Rename, Add Column (expression builder avec manipulation string, math, fonctions date, CASE WHEN), Cast Types, Normalize column names |
| **Nettoyage** | Clean String, Trim Whitespace, Cast to Timestamp, Normalize Column Names |
| **Géospatial** | Geo distance join, Geometry intersection join, Geometry KNN join |
| **Parsing de fichiers** | CSV, JSON, Excel, XML, Parse shapefile |
| **Avancé** | Split on condition, Pattern mining, Time-bounded drop duplicates, noeuds LLM (AI-powered data enrichment), OCR transforms |

**Types de noeuds Output :**
- Foundry dataset
- Media set
- Virtual table
- Ontology entity outputs (object types et link types)
- Geotemporal series sync

#### 7 Types de Joins

1. **Inner** — lignes matchant dans les deux tables
2. **Left** — toutes les lignes de gauche + matches de droite
3. **Right** — toutes les lignes de droite + matches de gauche
4. **Full Outer** — toutes les lignes des deux tables
5. **Cross** — produit cartésien
6. **Semi** — lignes de gauche qui ont un match à droite (pas de colonnes droite)
7. **Anti** — lignes de gauche qui n'ont PAS de match à droite

Les joins incluent des previews et un onglet Errors.

#### 300+ Fonctions d'Expression (500+ selon certaines sources)

**Catégories :**
- Arithmétique (add, subtract, multiply, divide, modulo, abs, ceil, floor, round, power, sqrt, log)
- String (concat, substring, trim, upper, lower, replace, split, regex_extract, regex_replace, length, contains, starts_with, ends_with, pad, reverse)
- Array (array_contains, array_size, array_sort, array_distinct, array_union, array_intersect, array_except, array_element_at, array_flatten, array_zip)
- Date/Time (date_add, date_sub, date_diff, date_format, date_trunc, extract, current_date, current_timestamp, months_between, to_date, to_timestamp)
- Géospatial (geo_distance, geo_within, geo_intersection, geo_buffer)
- Type Casting (cast, to_string, to_integer, to_double, to_boolean, to_date, to_timestamp)
- Avancé (Parse JSON, Cipher encrypt, Text to embeddings LLM-powered, Case/When, Coalesce, If/Else, Levenshtein distance)

**Features additionnelles :**
- Paramètres et fonctions réutilisables
- Auto-naming des noeuds selon leur logique (AI feature)
- Auto-génération d'expressions regex depuis des descriptions en langage naturel (AI feature)
- Contrôle de version intégré (branching comme git). Onglet Changes avec diff vs main, merge quand prêt
- Data expectations (health checks et tests unitaires)
- Stratégies d'échantillonnage

[CONTRADICTION] **Mixing visuel et code dans Pipeline Builder** : une source affirme que "Mixing visual and code nodes is fully supported" via un "Custom Code node" avec éditeur Monaco. D'autres sources disent explicitement le contraire : "Not inside a single Pipeline Builder transform board." Le mixing se fait "at the dataset boundary, not inside a node." Pipeline Builder est l'outil "no-code" ; Code Repositories est pour les stages de code spécialisé. Cette contradiction est significative — le consensus est que le mixing se fait au niveau dataset boundary.

### 4.3.2 Code Repositories

IDE web basé sur Git pour les utilisateurs nécessitant un contrôle programmatique au-delà du Pipeline Builder visuel. [CONFIRMED]

**Langages supportés :**
- **Python** (PySpark, Pandas, Polars, DuckDB)
- **Java**
- **SQL**
- **Mesa** (langage propriétaire de Palantir pour la résolution de contraintes)

#### L'API @transform (avec exemples de code)

L'API Python transforms Foundry (librairie `transforms`, open-sourcée sous `palantir/transforms-python`) est basée sur des decorators.

**`@transform`** — la forme la plus générale. Injecte des objets `TransformInput` et `TransformOutput` :

```python
from transforms.api import transform, Input, Output

@transform(
    source_a=Input("/datasets/source_a"),
    source_b=Input("/datasets/source_b"),
    output=Output("/datasets/joined_output")
)
def my_transform(source_a, source_b, output):
    df_a = source_a.dataframe()
    df_b = source_b.dataframe()
    joined = df_a.join(df_b, on="customer_id", how="left")
    cleaned = joined.filter(joined.status != "CANCELLED")
    output.write_dataframe(cleaned)
```

**`@transform_df`** — convenience wrapper qui injecte/retourne des DataFrames directement :

```python
from transforms.api import transform_df, Input, Output
from pyspark.sql import functions as F

@transform_df(
    Output("/Company/Ontology/Backing Datasets/clean_customer_orders"),
    raw_orders=Input("/Company/Data/Raw/SAP/orders"),
    customer_master=Input("/Company/Data/Clean/customer_master"),
)
def compute_clean_customer_orders(raw_orders, customer_master):
    orders_clean = (
        raw_orders
        .filter(F.col("order_status") != "CANCELLED")
        .withColumn("order_date", F.to_date("order_date_str", "yyyyMMdd"))
        .withColumn("order_amount", F.col("order_amount_raw").cast("double"))
    )
    result = orders_clean.join(
        customer_master.select("customer_id", "customer_name", "segment"),
        on="customer_id", how="left"
    )
    return result.withColumn("is_high_value",
        F.when(F.col("order_amount") > 10000, True).otherwise(False))
```

**`@transform_pandas`** — même chose mais pour des Pandas DataFrames.

**Objets Input/Output :**
- `Input(path, alias, branch, description)` — `.dataframe()`, `.filesystem()` (read-only FileSystem), `.rid`, `.branch`, `.txrange`
- `Output(path, alias, sever_permissions, description)` — `.write_dataframe(df)`, `.set_mode("replace"|"modify")`, `.abort()`, `.filesystem()`

#### Incremental Transforms

Le traitement incrémental est une feature de première classe : il utilise l'historique de build des transforms pour éviter de recalculer un output entier à chaque exécution.

**Decorator `@incremental()`** :

```python
from transforms.api import transform, Input, Output, incremental

@incremental()
@transform(
    output=Output("/path/to/output"),
    source=Input("/path/to/source"),
)
def incremental_pipeline(source, output):
    new_data = source.dataframe()  # Seulement les nouvelles lignes depuis le dernier run
    output.write_dataframe(new_data, mode="append")
```

**Modes de sortie :**
- `append` — ajoute les nouvelles lignes
- `replace` — retombe au full recompute
- `modify` — upsert

**Mécanismes clés :**
- `ctx.is_incremental` : boolean indiquant si incrémental ou snapshot
- `source.dataframe(mode="current")` : lit le snapshot complet
- `source.dataframe(mode="previous")` : lit le dernier état commis
- `require_incremental=True` : empêche un full recompute accidentel
- `semantic_version` : l'incrémenter force un full snapshot recompute (utile après des changements de logique)
- Cascading snapshots : si une quelconque input est snapshotted, le transform incrémental se snapshotte automatiquement

**Contraintes :**
- Foundry interdit explicitement que l'input et l'output soient le même dataset (éviter les dépendances cycliques)
- Le "simple default" ne fonctionne en sécurité que quand les lignes output ajoutées sont purement une fonction des lignes input ajoutées
- Pour une logique complexe (joins, aggregations, distinct), utiliser incrémental avec le decorator `transform()` complet

**Decorator `@configure`** : contrôle les profils de ressources (nombre d'executors, mémoire) et peut différer entre les runs snapshot et incrémental.

#### Testing et CI

**Unit tests** : Foundry supporte les tests **pytest** pour les repositories Python (batch pipelines uniquement) et peut exécuter les tests comme partie des checks.

**Module `transforms.testing`** : fournit `mock_transform()` pour les tests unitaires avec des sessions Spark locales.

**Data quality checks** : l'objet `Check` permet de définir des validations sur les outputs :

```python
@transform_df(
    Output("/path/to/output", checks=[
        Check(lambda df: df.filter(df.amount < 0).count() == 0,
              "No negative amounts", on_error=CheckSeverity.WARN),
        Check(lambda df: df.count() > 0,
              "Output is non-empty", on_error=CheckSeverity.FAIL),
    ]),
    source=Input("/path/to/source"),
)
def my_checked_transform(source):
    return source.filter(source.status == "active")
```

**CI intégré** : pousser sur une branche exécute pytest automatiquement, et les PRs ne peuvent pas merger si les tests échouent. Mécaniques CI : `condaPackRun`, environment caching, et style checks optionnels via Gradle plugins. La santé du pipeline est traitée comme partie du processus de build et release.

### 4.3.3 Data Lineage

#### Traçabilité Automatique

Foundry suit automatiquement le lineage au niveau **dataset-transform-dataset**. Chaque déclaration `Input()`/`Output()` crée un edge de lineage. Il n'y a **pas d'opt-in** — ce tracking est obligatoire. [CONFIRMED]

Au niveau transaction, Foundry enregistre :
- Quelles transactions d'entrée ont été consommées
- Quel code de transform (avec git commit hash) a été exécuté
- Quelles transactions de sortie ont été produites

#### Graph de Lineage

Data Lineage est une application interactive pour visualiser comment les datasets circulent dans Foundry.

**Éléments UI :**
- Graphe de lineage interactif (DAG horizontal) zoomable/pannable
- Chaque noeud = une ressource Foundry (dataset, transform, object type)
- Paramètres de branche
- Panneau latéral : Search & Browse, Properties and Histogram, Manage Builds, Manage Schedules, Related Artifacts
- Panneau de détails de noeud : nom, owner, last build time, health status
- Outils de graphe et "Save graph"

**Navigation :**
- Rechercher un dataset, object type ou ressource et l'ajouter comme noeud
- Cliquer sur les flèches gauche/droite pour expander parents (ancêtres) ou enfants (descendants)
- Outil Expand avec contrôles de niveau — un niveau, plusieurs niveaux, ou jusqu'aux sources brutes
- "Find relation between two nodes" montre tous les noeuds intermédiaires
- Coloration par type de transform, health status, groupements custom, ou couleurs assignées manuellement
- Outils de layout : automatique, hiérarchique, vertical, par niveau, ou par groupe de couleur
- Outil Find pour chercher des noeuds ou noms de colonnes dans les datasets sur le graphe
- Export SVG

On peut **déclencher des builds et définir des schedules** directement depuis le graphe de lineage.

**Monocle** : nom interne de Palantir pour l'outil de lineage/visualisation d'architecture étendu couvrant le stack opérationnel complet (flux data-to-ontology, actions et logique, dépendances applicatives, santé des pipelines).

[CONTRADICTION] **Column-level lineage** : une source affirme que le lineage au niveau colonne est "inféré en parsant le Catalyst logical plan de Spark" et que pour Pipeline Builder "each visual node's column flow is tracked explicitly." D'autres sources disent que la fonctionnalité "find datasets with a given column" existe (recherche column-aware), mais le lineage au niveau cellule ou ligne n'est PAS décrit comme une feature standard.

#### Interaction avec les Markings de Sécurité

Les **markings** sont le mécanisme de contrôle d'accès obligatoire de Foundry.

**Propagation automatique** : si Source A porte "SENSITIVE" et Source B porte "CONFIDENTIAL", leur output de join **hérite automatiquement des deux markings**. C'est enforcé au niveau plateforme — un développeur ne peut pas manuellement baisser la classification d'un dataset dérivé.

Data Lineage peut **simuler l'impact de changements de markings** et indique les noeuds qui "stop propagating markings" via du code.

**Mécanique de retrait** : `stop_propagating` et `stop_requiring` sont des propriétés de transform input et ne peuvent pas être ajoutées sur les outputs.

**Accès restreint** : les utilisateurs sans accès aux datasets upstream voient ces noeuds comme des placeholders "restricted".

**Déclassification** : les transforms de "déclassification" approuvés (ex: pipelines d'anonymisation) peuvent réduire les markings, mais nécessitent une approbation de gouvernance explicite et sont logués dans un audit trail immutable.

**Pipeline rollback** : utilise la provenance de données d'une transaction de dataset upstream pour identifier les datasets et transactions downstream et calculer un état de rollback. UX : sélectionner un dataset dans un graphe de lineage, choisir une branche, sélectionner une transaction dans History, puis "Rollback to transaction".

### 4.3.4 Scheduling

Le scheduling Foundry est **dataset-centric** : les schedules exécutent des builds pour garder les pipelines à jour.

**Types de déclencheurs :**

| Type | Description |
|------|-------------|
| **Time-based (Cron)** | Expressions cron standard (5 champs) + fuseau horaire. Constructeur cron visuel dans l'onglet Builds. Sélecteur hourly/daily/weekly/monthly. GUI + prompt en langage naturel AIP pour générer le cron. |
| **Event-driven** | Se déclenche quand des datasets upstream spécifiques sont mis à jour ("Build on upstream change"). Crée des chaînes de build en cascade. |
| **Logique mise à jour** | Se déclenche quand la logique de transform a été mise à jour. |
| **Compound triggers** | AND ("All of these triggers") ou OR ("Any of these triggers") — combinaison de toute condition. |
| **Hybride** | Event-based avec fallback timer. |
| **Manuel** | Bouton "Build" pour une exécution ad-hoc. |

**Types de build :** Single build, Full build (récursif amont), Connecting build (chemin entre inputs spécifiés et outputs cibles).

**Cibles de schedule** : un seul dataset, dependencies, dependents, datasets connectant deux datasets, ou combinaisons.

**Point d'entrée UI** : depuis un dataset preview > Actions > "Manage Schedules", ou depuis Data Lineage, ou le Build Schedules UI.

**Dependency resolver** : Foundry résout automatiquement les upstream datasets et les build dans le bon ordre. Les transforms indépendants s'exécutent en **parallèle** quand "Allow parallel builds" est activé.

**Retry logic** et alerting sont configurables.

### 4.3.5 Data Connectors

#### 400+ Connecteurs

Couvrant bases de données, applications SaaS, stockage cloud et systèmes enterprise.

#### 3 Modes d'Architecture

| Mode | Description | Cas d'usage |
|------|-------------|-------------|
| **Foundry Worker (Cloud-Side)** | Recommandé pour systèmes accessibles cloud. Traitement sur infrastructure compute gérée de Foundry. | Cloud databases, SaaS APIs, object storage (S3, GCS, ADLS) |
| **Foundry Worker avec Agent Proxy** | Recommandé pour on-prem/réseaux privés. Agent léger sur host Linux client (RHEL 8+, Ubuntu 22.04+) agit comme tunnel réseau uniquement ; tout le compute reste sur les workers Foundry. | On-premise databases behind firewalls, VPN-protected systems |
| **Agent Worker (legacy/air-gapped)** | L'agent exécute le compute sur le host client. Pour syncs fichiers spécifiques, micro-batching, ou filtrage lourd avant sortie du réseau. | Air-gapped government/military environments, SCADA/ICS networks |

**Installation agent :** Download depuis Foundry, installation sur host Linux 64-bit, enregistrement automatique, configuration certificat si proxy. Config dans `<agent-manager-install-directory>/var/conf/runtime.yml`.

#### SAP Certified Add-On

**Palantir Foundry Connector 2.0 for SAP Applications** :
- Installation via SAINT
- Développé avec Diskover Limited
- Supporte S/4HANA, ECC, Business Warehouse, SLT Replication Server
- Trois composants : PALANTIR (objets partagés), PALCONN (connecteur), PALODATA (optionnel, SLT OData APIs)
- Intégration SAP SLT pour **change data capture (CDC)** via triggers base de données

#### Connecteurs par catégorie

**Bases de données SQL (JDBC) :** Amazon Athena, Hive, IBM Db2, Informix, MariaDB, MSSQL, MySQL, Oracle, PostgreSQL, SQLite, Sybase, Vertica + connecteur JDBC custom.

**SaaS :** Salesforce (sync bidirectionnel, objets standard et custom), et 400+ autres.

**Avancé :** Webhooks, Listeners (Google Pub/Sub, Jira, Slack), External Connections from Code (compute pushdown), Virtual Tables, Private Link (AWS/Azure/GCP), Streaming syncs.

**Temps de connexion typique :** non publiquement documenté avec précision, mais les bootcamps de 1-5 jours incluent la connexion aux données, suggérant des heures à quelques jours pour les connecteurs standard.

**Failure modes :** retry logic configurable, alerting, detection de datasets obsolètes via Data Lineage.

---

## 4.4 Workshop — Application Builder

### 4.4.1 UI & Widgets

Workshop est un **constructeur d'applications no-code basé sur un canvas** avec un système de grille/layout. [CONFIRMED]

**Layout :**
- **Sidebar gauche** : listing des widgets par catégorie
- **Canvas central** : drag-and-drop pour placer les widgets dans un module layout avec sections
- **Panneau de configuration droit** : configuration du widget sélectionné
- **Mode preview** pour tester
- **Top toolbar** : contrôles pour ajouter des widgets, gérer les variables et previewer

Les applications supportent **plusieurs pages, modules réutilisables et visibilité basée sur les rôles**.

#### 50+ Widgets en 6 Catégories (liste complète)

**1. Widgets d'Affichage de Base (Core Display)**

| Widget | Description |
|--------|-------------|
| **Object Table** | Affichage tabulaire. Supports : sélection de colonnes (y compris time series), colonnes dérivées de Functions, tri simple/multiple, largeurs configurables, édition inline (writeback au niveau cellule), événements de sélection de ligne, actions clic droit personnalisées |
| **Object List** | Liste déroulante de cartes. Multi-select toggle, réordonnancement drag-and-drop, propriétés configurables par carte |
| **Object View** | Page de détail pour un objet unique. Mode "full" (pleine page) ou "panel" (sidebar). Support d'interface de configuration pour passer des variables |
| **Property List** | Propriétés en format clé-valeur |
| **Links** | Objets liés pour un objet donné |
| **Object Set Title** | Titre résumant le set d'objets courant (ex. "47 Flights") |
| **Details Panel** | Panneau de détails d'un objet |
| **Card Sets** | Ensembles de cartes |

**2. Widgets de Visualisation**

| Widget | Description |
|--------|-------------|
| **Chart XY** | Bar, line, scatter. Configuré par ajout de "layers" ; bar chart supporte "Stacked", "Percentage", "Grouped" |
| **Pie Chart** | Pie ou donut, regroupé par type de propriété |
| **Waterfall Chart** | Graphique en cascade |
| **Vega Chart** | Visualisations entièrement personnalisables via grammaire JSON Vega/Vega-Lite (échappatoire pour tout type de graphique) |
| **Map** | Géospatial via MapboxGL. Deux modes : configuration locale ou import de Map Template. Supporte clustering, heatmaps, sélection interactive |
| **Gantt Chart** | Événements dans une vue Gantt interactive. Utilisations : planification, allocation de ressources |
| **Pivot Table** | Groupement dynamique et agrégation. Supports : groupement par lignes (1+ propriétés), groupement par colonnes (max 1 propriété), groupement date dynamique (jour/semaine/mois/année), agrégations (count, cardinality, average, max, min, sum) |
| **Timeline** | Événements sur axe temporel horizontal |
| **KPI / Metric Card** | KPI configurable, souvent Function-backed |
| **Stepper** | Suivi de progression d'une tâche à travers des étapes |
| **Status Tracker** | Statuts d'un processus sur vue timeline |
| **Markdown** | Rendu de texte Markdown |

**3. Widgets Media**

| Widget | Description |
|--------|-------------|
| **Media Preview** | Images, audio, vidéo, documents (URL, RID Foundry, Base64) |
| **PDF Viewer** | Rendu PDF avec recherche par mots-clés |
| **Video Display** | Lecture vidéo |
| **Audio and Transcription Display** | Lecture audio + affichage de transcriptions |
| **Image Annotation** | Dessin de rectangles pour annoter des zones d'intérêt |
| **Spreadsheet Display** | Fichiers tableur depuis une propriété media reference |

**4. Widgets de Filtrage / Input**

| Widget | Description |
|--------|-------------|
| **Filter List** | Le plus riche. Supports : recherche par mots-clés, histogramme de distribution des propriétés, dropdowns single/multi-select, graphiques de distribution, pickers de date, timeline |
| **Property Filter** | Filtre par propriété |
| **Object Dropdown** | Sélection d'un objet unique dans une liste |
| **String Selector** | Dropdown, radio buttons, ou checkboxes |
| **Date and Time Picker** | Saisie date/heure |
| **Date Range Picker** | Sélection de plage de dates |
| **Slider** | Curseur numérique |
| **Search Bar** | Barre de recherche |
| **Toggle** | Interrupteur booléen |
| **Dropdown** | Menu déroulant |
| **Geo Filter** | Dessin sur carte pour filtrage géographique |
| **Object Selector** | Sélection d'objets |
| **Numeric Input** | Saisie numérique |
| **Text Input** | Texte libre |
| **Exploration Filter Pills** | Pilules de filtre interactives ajoutables/retirables dynamiquement |
| **Exploration Search Bar** | Barre de recherche full-text |
| **Prominent Term** | Termes fréquents/importants dans un object set |
| **User Select** | Sélection d'un utilisateur Foundry |

**5. Widgets d'Actions**

| Widget | Description |
|--------|-------------|
| **Action Button / Button Group** | Déclencheur d'action principal. Peut : exécuter une Action (writeback), déclencher un événement Workshop (changement de page, set de variable, ouverture/fermeture d'overlay), ouvrir une URL, démarrer un export d'object set. Trois layouts. Personnalisation : icônes, styles minimaux, styles tag |
| **Inline Action** | Formulaire surfaçant les paramètres d'Action Type directement inline. Interface formulaire et table. Validation live avec messages d'erreur personnalisés. UI automatiquement générée depuis les définitions de paramètres |
| **Bulk Action Button** | Action sur une sélection multiple d'objets |
| **Form** | Formulaire |
| **Media Uploader** | Upload de media |
| **Audio Recorder** | Enregistrement audio |

**6. Widgets AIP (IA/LLM)**

| Widget | Description |
|--------|-------------|
| **AIP Agent** | Assistant IA interactif (interface chat) avec outils enterprise. Configuré via AIP Agent Studio. Quatre types d'outils : recherche sémantique Ontologie (KNN ou vecteur), Actions, applications Workshop, Functions. Peut lire et écrire des variables Workshop |
| **AIP Analyst** | Analyse plus orientée analytique, configurable pour accès aux données, disponibilité d'outils, personnalisation UI |
| **AIP Generated Content** | Sortie d'appel LLM. Peut rendre une réponse streamée. Trois modes : Direct-to-LLM, LLM-via-prompt-function, AIP Logic function |
| **AIP Interactive** | Widget assistant interactif pour workflows opérationnels |

**7. Widgets Meta / Layout / Embedding**

| Widget | Description |
|--------|-------------|
| **Container** | Conteneur de layout |
| **Tabs** | Onglets de navigation |
| **Column Layout** | Layout en colonnes |
| **Conditional Visibility** | Visibilité conditionnelle |
| **Header** | En-tête |
| **Free-form Analysis** | Analyse ad-hoc dans le module Workshop |
| **Data Freshness** | Dernière mise à jour |
| **Edit History** | Historique des edits sur les objets |
| **Action Log Timeline** | Timeline des actions exécutées |
| **Linked Compass Resources** | Ressources Compass liées |
| **Comments** | Section de commentaires threadés |
| **Resource List** | Ressources Foundry |
| **Iframe** | Intégration d'application web. Communication bidirectionnelle via `@osdk/workshop-iframe-custom-widget` npm |
| **Embedded Module** | Intégration d'un autre module Workshop avec mapping de variables parent/enfant |
| **Custom Widgets** | Composants frontend entièrement custom (React, TypeScript). Packageés en "widget sets". Max 50 paramètres et 50 événements par widget |

#### Système de Variables (12 types, 6 mécanismes)

Les **Workshop Variables** sont le mécanisme central de communication inter-widget.

**12 types de variables :**
1. Object set
2. Object set filter
3. String
4. Numeric
5. Boolean
6. Date
7. Timestamp
8. GeoPoint
9. GeoShape
10. Array
11. Struct
12. Time series set

**6 mécanismes de définition :**
1. **Static** : valeur fixe définie manuellement
2. **Function** : calculée dynamiquement par une Function TypeScript sur Objects (FOO)
3. **Object set aggregation** : dérivée de l'agrégation d'un object set
4. **Object property** : liée à la valeur d'une propriété d'un objet unique
5. **Object set definition** : en spécifiant un type d'objet, des filtres de propriétés, et des traversées de liens
6. **Variable transformation** : série d'opérations référençant d'autres variables (style pipeline)

**Évaluation paresseuse** : les variables calculent **paresseusement en mode vue** — elles ne recalculent que quand affichées par un widget visible.

**Trois comportements de recomputation :**
- Automatic : recalcule quand les dépendances amont changent
- Event-triggered : recalcule uniquement déclenchée explicitement par un événement
- Load & event : recalcule au chargement initial du module ET sur événement

**Graphe de dépendances visuel** dans l'éditeur montrant comment les variables connectent aux widgets.

**Système d'événements :**
Open/Close overlay, Switch to page, Expand/Collapse/Toggle section, Switch to tab, Reset variable value, Recompute variable, Set variable value, Stream LLM response into variable, Send to AIP Assist, Open Workshop module.

**Limitation critique :** les événements n'attendent PAS que les computations aval des événements précédents soient complètes avant d'exécuter l'événement suivant.

### 4.4.2 Construction Step-by-Step

#### Binding d'un Table Widget à un Object Type

1. Glisser un widget **Object Table** depuis la sidebar gauche
2. Dans le panneau de config droit, sélectionner un Object Type (ex: "Flight") ou créer/sélectionner une **variable Object Set**
3. Optionnellement spécifier un filtre Object Set
4. Sélectionner quelles propriétés apparaissent comme colonnes — toggle, puis **drag to reorder**. Ou sous Column Configuration, "Add all properties" puis réorganiser en drag
5. Configurer largeurs de colonnes, tri par défaut, filtrage par colonne
6. Activer la sélection de lignes et configurer le comportement au clic
7. Configurer la pagination (25/50/100)

Workshop ne bind **pas aux datasets directement** dans les widgets opérationnels principaux ; il bind aux **object sets et object types** dans l'ontologie.

#### Ajout d'un Action Button

1. Ajouter un widget **Button Group**
2. Section "On click" dans la configuration
3. Sélectionner un Action Type de l'ontologie (ex: "Modify Flight Destination")
4. Le système affiche automatiquement tous les paramètres d'Action. Pour chaque paramètre : valeur par défaut (liée à une variable Workshop), visibilité (Visible/Hidden/Disabled)
5. Configurer le dialogue de confirmation, messages de succès/erreur, et comportement post-action (refresh data, navigate, clear selection)
6. Le bouton respecte les permissions au niveau ontologie — les utilisateurs sans permission d'exécution voient le bouton désactivé ou caché

Les Button Group widgets peuvent aussi déclencher des Workshop events, URLs et exports.

**Inline Action widget** : formulaire surfaçant les paramètres d'Action Type directement inline. Validation live.

**Flux de soumission :**
1. Validation contre les critères de soumission
2. Si échec : messages d'erreur inline
3. Si succès : exécution de l'action
4. Toast de confirmation vert
5. Mise à jour des données objet
6. Toutes les actions commitées **transactionnellement** à l'Ontologie

**Édits inline :** édition au niveau cellule directement dans l'Object Table widget, style "spreadsheet" avec writeback.

#### Filtres et Inter-Widget Linking

**Pattern canonique de linking :**

1. Table A (Customers) configurée pour qu'au clic de ligne, elle écrive `selectedCustomer` dans une variable
2. Table B (Orders) a son Object Set filtré par `Orders where customer = {{selectedCustomer}}`
3. Un Details Panel lit `selectedCustomer` pour afficher toutes les propriétés
4. Une Map surligne la localisation du client sélectionné
5. Un seul widget filtre peut contrôler plusieurs tables, charts et maps via des variables partagées

Le widget **Filter List** rend des filtres par type de propriété sous forme d'histogrammes, charts de distribution, pickers et sélecteurs type-ahead ; inclut la recherche par mot-clé. Connecter un Filter List à la même variable Object Set que la Table permet un filtrage automatique.

**Workshop Events** sont le tissu connectif : les events peuvent être déclenchés par les widgets incluant Button Group et Object Table sur sélection de ligne. C'est ce qui se rapproche le plus d'un "reactive state management layer" : variables + events.

Les boutons peuvent aussi déclencher un **"Send to AIP Assist"** event qui ouvre la sidebar Assist.

#### Layout, Routing, State Management

**Hiérarchie de layout :** Module -> Header -> Pages -> Sections -> Widgets/Layouts (Columns/Rows/Tabs) + Overlays (Drawers/Modals)

**Système de dimensionnement :** Auto (max), Absolute (pixels fixes), Flex (proportionnel).

**Module Interface :** API pour un module Workshop. N'importe quelle variable peut être ajoutée à l'interface. Quand un module A intègre un module B, A mappe ses variables aux variables d'interface de B. Variables complètement partagées entre parent et enfant. Initialisables depuis des query parameters URL.

**Routing :** l'ID de page courant est écrit dans l'URL ; les variables d'interface configurées sont écrites comme query parameters URL ; permet le bookmark, le partage et le deep-linking.

**Sauvegarde d'état :** sauvegarde persistante de l'état de toutes les variables ; restaurable ou partageable.

### 4.4.3 Patterns d'Application

#### Inbox / Task Triage (pattern canonique)

- **Panneau gauche** : Filter List
- **Centre** : Object Table avec alertes filtrées
- **Panneau droit** : Object View (détails de l'élément sélectionné)
- **Bas** : Button Group avec actions (approuver, rejeter, escalader)
- **Cas d'usage** : triage de réclamations, investigation d'alertes, gestion de commandes, gestion de cas, admission patient

#### COP (Common Operating Picture)

- Widget **Map** central
- **Metric Cards** (KPIs)
- **Chart XY** (tendances)
- **Filter List** / Exploration Filter Pills
- Cours officiel : "APPDEV 06: Building a Common Operating Picture in Workshop"

#### Scenarios / Analyse What-If

Un Scenario est un "fork" des données Ontologie généré en appliquant des actions (optionnellement via modèles ML). Modifications de paramètres, exécution de modèle, résultats projetés sans affecter les données live. Application transactionnelle. Intégré avec Vertex (framework de modélisation de Palantir).

---

## 4.5 Workshop vs Quiver vs Contour vs Slate

| Dimension | Workshop | Quiver | Contour | Slate |
|-----------|----------|--------|---------|-------|
| **Usage** | Apps opérationnelles avec writeback | Dashboards, KPIs, time series | Exploration ad-hoc tabulaire | Apps custom full HTML/CSS/JS |
| **Source de données** | Objets Ontologie uniquement | Objets Ontologie + time series | Datasets bruts (tabulaire) | APIs arbitraires + datasets bruts |
| **Writeback** | Oui (Ontology Actions) | Non (read-only) | Non (peut sauver comme nouveau dataset) | Oui (via API / code) |
| **Code requis** | Non (TypeScript Functions pour logique avancée) | Non | Non (point-and-click) | HTML/JS/CSS (templating Handlebars) |
| **Utilisateur cible** | Business ops, managers | Exécutifs, analystes, capteurs | Data analystes | Développeurs |
| **Vitesse de build** | Rapide | Très rapide | N/A (outil d'exploration) | Lent |
| **Custom UI** | Limité à la bibliothèque de widgets + custom widgets | Limité | N/A | Contrôle total (HTML/CSS/JS) |
| **Multi-page** | Oui | Non (dashboard unique) | Non (analysis boards) | Oui |
| **Formulaires/Input** | Oui | Non | Non | Oui (code) |
| **Ontologie requise** | Oui | Oui | Non | Non |
| **Mobile** | Layouts mobiles natifs et design responsive | Non | Non | Limité (CSS responsive manuel) |
| **Intégration AIP** | Complète (AIP Agent, Analyst, Generated Content) | AIP Generate pour ajout/config de cartes | Limitée | Limitée (via Functions et Iframe) |
| **Maintenance** | Faible — Palantir gère les mises à jour de widgets | Faible | Faible | Élevée (outil plus ancien, plus fragile) |
| **Échelle données** | Workflows opérationnels enterprise | ~50,000 lignes agrégation | Très grands datasets (millions+ lignes) | Variable |
| **Idéal pour** | Inbox/triage, COPs, gestion de tâches, dashboards opérationnels | Analytics centrées objet, time series, données capteurs | Exploration ad-hoc, analyse de très grands datasets | Dashboards pixel-perfect, apps legacy nécessitant contrôle HTML |

**Quand utiliser chaque outil :**
- **Les utilisateurs doivent agir/changer le monde** (actions, edits) -> **Workshop**
- **Dashboard de monitoring sans writeback** / **Comprendre le monde** -> **Quiver**
- **Exploration ad-hoc** / **Découvrir le monde** -> **Contour** (recommandé quand les données ne sont pas encore dans l'ontologie)
- **UI pixel-perfect, custom styling/behaviour, librairies JS tierces** (D3, Leaflet) -> **Slate**
- **Choix par défaut pour les nouvelles apps** -> **Workshop**

**Quiver dans Workshop** : les templates Quiver peuvent être **embarqués dans les applications Workshop** pour du contenu analytique au sein de workflows opérationnels.

---

## 4.6 AIP (Artificial Intelligence Platform)

### 4.6.1 AIP Logic

AIP Logic est un **environnement de développement no-code** pour construire, tester et releaser des fonctions alimentées par des LLMs, gouverné par la sécurité plateforme. [CONFIRMED]

#### Les 5 Types de Blocs

| Type de bloc | Description |
|-------------|-------------|
| **Use LLM** | Envoie un prompt (avec contexte Ontologie injecté) à un modèle de langage et capture la réponse structurée. Templates de prompt, traces de raisonnement intermédiaires. |
| **Apply Action** | Exécute un Action Type Ontologie (ex: "approve order", "update status"), qui peut écrire dans les systèmes source |
| **Execute Function** | Exécute une Function Ontologie typée (computation TypeScript ou Python) et retourne son résultat dans le workflow |
| **Conditional** | Branche le workflow selon une condition évaluée contre le contexte courant |
| **Loop** | Itère sur un ensemble d'objets ou résultats, appliquant les blocs suivants à chaque élément |

**Blocs additionnels** : calculateurs, object lookups, traversées de liens, recherche sémantique ("data tool blocks"), création de variables.

**Layout UI :**
- **Gauche** : Inputs, Blocks, Outputs configuration
- **Milieu** : Debugger (montrant les traces de raisonnement intermédiaires du modèle pour les blocs)
- **Droite** : Run panel (historique des runs, création de tests)

[CONTRADICTION] **Runtime LLM vs code déterministe** : une source affirme que "the LLM is used at development time to generate code; the deployed function runs deterministically without any LLM." D'autres sources décrivent AIP Logic comme des fonctions qui UTILISENT des blocs LLM au runtime, avec des blocs "Use LLM" qui ont des templates de prompt et des traces de raisonnement intermédiaires, et un debugger montrant les "model's intermediate reasoning traces." Cette contradiction est fondamentale sur l'architecture d'AIP Logic. Le consensus des sources multiples penche vers l'exécution LLM au runtime.

#### Runtime : LLM at Dev-Time vs at Runtime

Le consensus basé sur les sources multiples et les démos AIPCon : AIP Logic utilise les LLMs **au runtime**, pas uniquement au dev-time. Les blocs "Use LLM" envoient des prompts au moment de l'exécution, et le debugger montre les traces de raisonnement intermédiaires du modèle. La télémétrie de production montre 5,000+ function runs avec traces complètes.

**Workflow de création :**
1. Accéder AIP Logic via la navigation workspace ou +New > AIP Logic
2. Définir les inputs : strings prompts, objets ontologie, object lists, object sets, plus primitives
3. Composer des blocs : Create variable, Apply action, Execute function, Use LLM, boucles, conditionnels
4. Chaîner les blocs : l'output d'un bloc alimente le suivant
5. Run et debug : le Debugger montre les traces de raisonnement intermédiaires
6. Publier : pour les edits ontologiques, il faut publier et l'appeler via une Action
7. Configurer des **Évaluations** pour tester la logique, comparer des modèles, examiner la variance entre les runs

### 4.6.2 Agent Studio

Agent Studio permet la construction d'agents IA autonomes qui interagissent avec l'Ontologie via un ensemble contrôlé d'outils. L'architecture utilise le paradigme tool-use/function-calling. [CONFIRMED]

#### Les 4 Outils

| Outil | Ce qu'il fait |
|-------|---------------|
| **Query Objects** | Rechercher et récupérer des objets Ontologie matchant des filtres et contraintes spécifiés |
| **Apply Actions** | Exécuter des Action Types Ontologie pour créer, modifier ou supprimer des objets et déclencher le writeback |
| **Call Function** | Invoquer des Functions Ontologie typées (computations) et recevoir des résultats structurés |
| **Calculator** | Effectuer des opérations arithmétiques et mathématiques sans approximation LLM |

**Seuls les outils explicitement configurés sont accessibles** à chaque agent. Un agent ne peut pas découvrir ou invoquer des outils qui n'ont pas été whitelistés dans sa configuration. C'est une contrainte de sécurité fondamentale.

### 4.6.3 Language Model Service

Palantir opère un gateway LLM model-agnostique supportant **50+ modèles** : [CONFIRMED]

| Provider | Modèles |
|----------|---------|
| **OpenAI** | GPT-4o, GPT-4.1 |
| **Anthropic** | Claude 3.5, Claude Opus/Sonnet 4 |
| **Meta** | Llama 3.x, Llama 4 |
| **Mistral AI** | Modèles Mistral |
| **Google** | Gemini 2.5 Pro/Flash |
| **xAI** | Grok |
| **BYOM** | Les clients peuvent intégrer des modèles propriétaires ou fine-tunés |

Pour les clients gouvernementaux, les modèles tournent entièrement on-premises.

### 4.6.4 Guardrails — 4 Niveaux de Contrôle

| Niveau | Guardrail | Description |
|--------|-----------|-------------|
| **1** | Constrained Action Types | Définit QUELLES actions l'IA est autorisée à prendre. L'IA ne peut pas effectuer d'opération non explicitement listée dans ses Action Types permis. |
| **2** | Tool Scoping | Définit QUELS outils l'agent peut accéder. Seuls les outils explicitement configurés sont visibles ; l'agent ne peut pas en découvrir d'autres. |
| **3** | Permission-Bounded | L'IA hérite des permissions de l'utilisateur invocateur. Elle ne peut pas voir ou modifier des données que l'utilisateur ne peut pas voir ou modifier. Pas d'escalade de privilèges. |
| **4** | Staging Review | L'humain approuve avant exécution. Les actions sont stagées pour revue, et un humain doit explicitement confirmer avant que les effets de bord ne soient commités. |

**Comment AIP accède à l'Ontologie :** AIP Logic reçoit des objets Ontologie typés, pas des données brutes. On accorde explicitement à chaque bloc LLM l'accès à des object types et propriétés spécifiques :

> "I explicitly gave it access to this object... you can pick a lot of different objects here or narrow it down. This is an explicit access from an LLM to certain ontology... I can give it access to certain properties -- not just from a security standpoint but also from an LLM [hallucination reduction] standpoint."

Le package `@foundry/ontology-api` auto-génère des interfaces TypeScript depuis le schema Ontologie, ce qui signifie que les actions du LLM sont contraintes aux opérations Ontologie valides.

**Observabilité** : tracing au niveau workflow, avec une "Trace view" montrant une timeline d'opérations incluant si les spans proviennent de Functions, Actions, Automations ou appels LLM.

### 4.6.5 AIP Assist — Expérience In-Product

AIP Assist est un outil de support plateforme avec une **sidebar in-app**. Il est explicitement context-aware (conscient de l'app Foundry dans laquelle on se trouve) et est conçu pour **ne pas accéder aux données utilisateur**.

AIP Assist n'est **PAS** un générateur d'applications Workshop. C'est une sidebar d'aide contextuelle entraînée sur la documentation de la plateforme.

**Intégrations documentées :**
- **Dans Workshop** : les widgets Button peuvent déclencher un event "Send to AIP Assist" qui ouvre la sidebar Assist et soumet un prompt statique ou dérivé de variable ; les builders peuvent définir un Agent Assist par défaut
- **Dans Ontology Manager** : lors de la mise à jour d'une ontologie, l'onglet Errors inclut "Explain with AIP Assist" sur une erreur, produisant des suggestions de corrections et explications

**Generative Frontend (en développement)** : une fonctionnalité "Generative Frontend AIP Assist" cible les applications OSDK React. Statut : expérimental. Utilise l'extension Continue dans VS Code Workspaces.

---

## 4.7 OSDK (Ontology SDK)

L'OSDK est le générateur de code schema-driven de Palantir qui produit des **clients types fortement statiques** spécifiques à votre Ontologie. Ce n'est pas un wrapper REST générique — il génère des types qui mirrorent exactement vos Object Types, Link Types et Actions. [CONFIRMED]

**Langages supportés :** TypeScript (NPM), Python (Pip/Conda), Java (Maven), et **OpenAPI** pour tout autre langage.

**Génération :**
1. Les apps OSDK sont créées et gérées dans **Developer Console**
2. Wizard de création : choisir "client-facing application", configurer les OAuth redirect URLs, sélectionner quels object types et action types inclure dans le package SDK
3. Le code généré inclut des classes typées pour chaque Object Type, accesseurs de propriétés, traversées de liens, et invocations d'Actions
4. Les noms de propriétés et descriptions de l'Ontology Manager apparaissent comme JSDoc/docstrings dans l'IDE

**CLI de génération :**

```bash
npx @osdk/cli generate \
  --foundry-url https://your-stack.palantirfoundry.com \
  --ontology-rid ri.ontology.main.ontology.xxx \
  --output-dir ./src/ontology
```

**Écosystème NPM :** `@osdk/client`, `@osdk/api`, `@osdk/oauth`, `@osdk/cli`, `@osdk/react`. Repo open-source : `palantir/osdk-ts`.

**Authentication :** OAuth 2.0 confidential client (backend), OAuth 2.0 public client (browser SPA), et bearer token (développement).

### Exemples de Code TypeScript

**Query avec filtrage et pagination :**

```typescript
import { createClient } from "@osdk/client";
import { MaintenanceTicket } from "./ontology/objects/MaintenanceTicket";

const client = createClient(foundryUrl, ontologyRid, auth);

const tickets = await client(MaintenanceTicket)
  .where({ priority: "HIGH", status: { $ne: "CLOSED" } })
  .orderBy(t => t.createdDate.desc())
  .take(50);

for (const ticket of tickets.data) {
  console.log(ticket.ticketId);     // string - entièrement typé
  console.log(ticket.priority);      // "HIGH" | "MEDIUM" | "LOW"
}
```

**Traverser les liens :**

```typescript
const asset = await tickets.data[0].$link.asset.get();
const departments = await employee.$link.department.fetchPage({ $pageSize: 100 });
```

**Exécuter des actions :**

```typescript
await client(updateTicketStatus).applyAction({
  ticket: tickets.data[0].$primaryKey,
  newStatus: "IN_PROGRESS",
});

// Batch
await client(CreateEmployee).batchApplyAction([...]);

// Validation only
const validation = await client(CreateEmployee).applyAction({...}, { $validateOnly: true });
```

**Hooks React (avec `@osdk/react`) :**

```typescript
import { Todo } from "@my/osdk";
import { useOsdkObjects } from "@osdk/react/experimental";

function TodoList() {
  const { data, isLoading, error } = useOsdkObjects(Todo, {
    orderBy: { createdAt: "desc" },
  });
  // ...
}
```

**Agrégations :**

```typescript
const grouped = await client(MyObject).aggregate({
  $select: { $count: "unordered" },
  $groupBy: { category: "exact", region: "exact" }
});
```

**Filtrage OR :**

```typescript
import OSDK from "@slate-internal/sdk";
const result = await ObjType
  .where(query => {
    const conditions = names.map(n => query.name.eq(n));
    return OSDK.Op.or(...conditions);
  })
  .fetchPage();
```

**Subscribe (WebSocket real-time updates) :** `streamUpdates` pour des mises à jour temps réel.

### Exemples Python et Java

**Python OSDK :** `.get()`, `.page()`, `.iterate()`, `.where()` avec opérateurs d'égalité, null check, string prefix, full-text search, range, boolean composition (AND/OR/NOT), ordering, `.count()`, `.avg()`, `.approximate_distinct()`, `.group_by()`.

**Java OSDK :**

```java
List<Restaurant> result = client.ontology()
    .objects()
    .Restaurant()
    .where(RestaurantFilter.restaurantName().isNull(false))
    .fetchStream()
    .toList();
```

**Platform API bindings** via `foundry-platform-typescript` (installable comme `@osdk/foundry.{namespace}`).

---

## 4.8 Apollo — Déploiement

### Architecture Hub-and-Spoke

1. **Apollo Hub** (central, hébergé par Palantir comme SaaS) : maintient le statut et les requirements de chaque environnement. Contient le moteur d'orchestration et le catalogue. Stocke les settings d'environnement incluant les entités qui doivent exister, les release channels souscrits, et les fenêtres de maintenance.
2. **Remote Apollo Hubs** : déployés dans les réseaux air-gapped ou isolés. Synchronisés avec le Hub principal via des Apollo bundles.
3. **Spoke Environments / Apollo Deployment Platform** : exécutent un Spoke Control Plane et reportent le statut au Hub. Déployé au-dessus de Kubernetes.
4. **Apollo Agents** : déployés dans le Spoke, exécutent les Plans émis par le Hub, puis reportent le "Reported State". Pollent le control plane pour les changements d'état désiré, téléchargent les artifacts des registries, et orchestrent les déploiements Kubernetes.
5. **Apollo SDK** : framework pour les développeurs pour publier les metadata de release.
6. **Apollo Catalog** : couche metadata bridgeant les artifact stores et les environnements gérés. Source de vérité pour toutes les versions de software disponibles.

Les spokes peuvent eux-mêmes être hubs d'autres spokes, permettant des topologies hiérarchiques.

### Modèle Pull (pas Push)

Apollo utilise un **modèle pull constraint-based**, fondamentalement différent des systèmes CI/CD push-based comme Jenkins ou ArgoCD. Au lieu d'un système central poussant des artifacts vers des cibles, Apollo définit des **Plans** declaratifs d'état désiré. Chaque spoke agent pull indépendamment le plan et converge son environnement local.

Essentiel pour la sécurité — **aucune connexion entrante vers les réseaux clients n'est requise**.

### Constraint-Based (pas Desired-State simple)

Le moteur évalue continuellement les Plans possibles pour chaque Spoke, vérifie les contraintes, et émet les Plans dont les contraintes sont satisfaites. Compare l'état cible vs l'état observé à travers tous les environnements. Quand ils diffèrent, il calcule un **Apollo Plan** spécifiant quoi upgrader, où et comment.

Les Plans pour roll off un release rappelé ou exécuter des commandes "break-glass" sont **priorisés**.

### Échelle Opérationnelle

| Métrique | Valeur | Confiance |
|----------|--------|-----------|
| Déploiements par mois | **360,000+** | CONFIRMED |
| Environnements gérés | **300+** | CONFIRMED |
| Microservices déployés | **500+** indépendamment | CONFIRMED |
| Équipes d'ingénierie | **250+** déploient en continu | CONFIRMED |
| Temps de déploiement | **3.5 minutes** | CONFIRMED |
| Équipe engineering Apollo | **<20 ingénieurs** | CONFIRMED |

### Rollback en 4.9 Minutes

**Rollback declaratif** : le control plane remet la version désirée à l'état précédent connu-bon et les agents reconcilent. Temps : **<5 minutes** (confirmé).

**Déclenchement automatique** : quand les health checks (Kubernetes probes + endpoints de santé applicatifs custom) échouent.

**Stratégies de recall :**
- **Stay on current version** — pause des nouvelles installations pendant l'investigation
- **Stay on current with exceptions** — des environnements spécifiques reçoivent le fix
- **Any version newer than recalled** — attendre un fix
- **Roll back to specific known-good version** — forcer le downgrade sur toute la flotte

Les recalls peuvent être déclenchés par les administrateurs, développeurs, ou **automatiquement par Apollo**.

**Vitesse de patch** : 3.5 minutes en moyenne pour patcher un service, moins de 5 minutes pour remédier les problèmes de production. Apollo peut remédier les vulnérabilités en "quelques heures" (référence : remédiation log4j à travers 200+ environnements).

### Air-Gapped : Sneakernet, Bundles Chiffrés

**Mécanisme 1 : Apollo Bundles (sneakernet)** : générés sur le Hub SaaS, contenant uniquement les nouvelles versions nettes de software, configurations et metadata (diffs intelligemment compressés). Gravés sur media physique, transportés vers le réseau classifié, et chargés dans le Remote Hub. Les metadata AV sont incluses ; les payloads sont scannés et vérifiés en intégrité à plusieurs checkpoints.

**Mécanisme 2 : Binary Transfer Service (BTS)** : automatise le transfert de bundles via des **Cross Domain Solutions (CDS)** accréditées. BTS poll le Apollo Catalog pour les nouvelles releases, vérifie les résultats de scan sécurité et checksums cryptographiques, et transfère les artifacts vers le hub distant automatiquement.

**Opération déconnectée** : les environnements peuvent se déconnecter d'un Hub pendant des périodes (ex: véhicules en mouvement) et se reconnecter pour les upgrades plus tard.

**One-way data flow** : pour les niveaux de classification les plus élevés, le flux de données est unidirectionnel — les mises à jour entrent, mais un minimum ou aucune télémétrie ne sort.

**Classifications supportées** : jusqu'à TS/SCI.

[CONTRADICTION] **Sneakernet** : une source dit que les docs publiques "do not describe sneakernet mechanics in detail." D'autres sources donnent des détails précis sur les Apollo Bundles (diffs compressés, media physique, checkpoints de vérification).

### Break-Glass Mechanism

Mécanisme de dérogation d'urgence permettant aux opérateurs autorisés de bypasser les contraintes normales de déploiement et workflows d'approbation en situation de crise. Essentiel pour les déploiements militaires et d'infrastructure critique. [CONFIRMED]

### $100/installation/mois Standalone

Apollo est disponible comme produit standalone sur les **Azure et AWS Marketplaces** à environ **~$100/install/month**. C'est le seul produit Palantir disponible indépendamment du stack Foundry complet. [CONFIRMED]

### Mécanismes de Contrôle Additionnels

**Release Channels** : les environnements souscrivent à des canaux (ex: `canary` -> `beta` -> `stable` -> `government-stable`). Les features passent de develop -> stable automatiquement après adjudication.

**Canary Analysis** : les nouvelles features sont d'abord déployées dans les environnements canary. Apollo monitore les métriques de performance et états d'erreur, promouvant ou rappelant automatiquement les releases.

**Blue/Green Deployment** : zero-downtime — déploie une seconde instance, déplace lentement le traffic.

**Fenêtres de maintenance** : au niveau produit ou environnement, bloquent les upgrades pendant les périodes sensibles. Auto-créées quand des seuils de failure sont atteints.

**Change requests** : système avec statuts Pending Approvals, Approved, Rejected, Cancelled. Sauf DEV, Apollo requiert au moins un approbateur.

**Certifications sécurité** : FedRAMP High (upgraded from Moderate, Dec 2024), DoD IL5, DoD IL6, ICD 503. Apollo encode les SLAs de vulnérabilité InfoSec, s'intègre aux scanners d'images container, et génère des **SBOMs** complets. [CONFIRMED]

---

## 4.9 Compute Architecture

### 5 Moteurs

| Moteur | Mode | Architecture | Workload optimal | Volume |
|--------|------|-------------|-----------------|--------|
| **Apache Spark** | Batch | Distribué (driver + executors) | ETL large-scale, reprocessing historique, ML feature engineering | GB à TB+ |
| **Apache Flink** | Streaming | Distribué (JobManager + TaskManagers avec checkpointing) | Real-time event processing, CDC, agrégations continues | Flux continus |
| **DuckDB** | In-process | Single-process, embedded | Requêtes analytiques rapides sur datasets petits-moyens | MB à low GB |
| **Polars** | In-process | Single-process, Rust-powered DataFrame library | Opérations DataFrame haute-performance | MB à low GB |
| **Virtual Tables** | Pushdown | Fédéré (requête envoyée au moteur externe) | Requêter des données dans des warehouses externes sans les déplacer | Any (données ne bougent pas) |

**Mesa** (propriétaire) : langage de résolution de contraintes pour les problèmes d'optimisation (scheduling, routing, allocation de ressources).

### Logique de Sélection

| Caractéristique | Moteur sélectionné | Justification |
|----------------|-------------------|---------------|
| Données > 10 GB, batch | Apache Spark | Exécution distribuée pour parallélisme |
| Flux continu d'événements | Apache Flink | Stream processing stateful avec exactly-once semantics |
| Données < 10 GB, requêtes analytiques | DuckDB | Démarrage rapide, pas d'overhead cluster, analytique columnar |
| Opérations DataFrame complexes | Polars | Performance Rust avec évaluation paresseuse |
| Données dans un warehouse externe | Virtual Tables | Éviter le mouvement de données ; leverager l'optimisation du moteur externe |
| Problème d'optimisation par contraintes | Mesa | Solveur propriétaire pour scheduling/routing/allocation |

---

## 4.10 Sécurité

### Cell-Level ACL, AES-256-GCM

- **Cell-level ACL** : contrôle d'accès au niveau de la cellule individuelle (intersection ligne + colonne), pas seulement au niveau table ou ligne [CONFIRMED]
- **AES-256-GCM** : données chiffrées au repos et en transit via AES-256 en Galois/Counter Mode [CONFIRMED]

### Markings et PBAC

Palantir combine **Purpose-Based Access Control (PBAC)** avec des **markings obligatoires (MAC — Mandatory Access Control)**.

**Couche 1 : Markings de Ressource Obligatoires**
- Chaque élément de données peut porter des **markings binaires, conjonctifs**
- Les markings sont binaires (un utilisateur a le marking ou non) et conjonctifs (tous les markings requis doivent être présents)
- Les markings suivent des **règles d'héritage** — les données dérivées héritent de l'union des markings de toutes les données source
- Empêche l'information de couler "vers le bas" vers des contextes moins classifiés

**Couche 2 : ACL au Niveau Ontologie**
- **Per-object RLS (Row-Level Security)** — les objets individuels peuvent avoir des règles d'accès
- **Per-property column suppression** — des propriétés spécifiques peuvent être cachées à des utilisateurs spécifiques (ex: voir qu'un Patient existe mais pas son SSN)
- **Restricted views avec dynamic row predicates** — vues filtrant les objets selon des prédicats évalués au runtime

### Propagation à travers les Links

**Link-Visibility Semantics** (détail d'implémentation critique) : la visibilité des liens doit être explicitement définie et testée. Sans implémentation soigneuse, un attaquant peut inférer l'existence d'objets classifiés à travers :
1. Les résultats de traversée qui incluent des liens vers des objets que l'utilisateur ne peut pas voir
2. Les comptages d'edges qui révèlent le nombre de connexions cachées
3. Les requêtes "exists" qui confirment l'existence d'un objet lié sans révéler son contenu

Palantir adresse explicitement ces vecteurs de fuite.

### Permission pour AI vs Humains

**Couche 3 : Contrôles de Contexte d'Exécution pour l'IA**
- **Contexte d'identité** : l'agent IA opère sous l'identité de l'utilisateur invocateur, héritant de ses permissions exactes
- **Scoping de contexte de purpose** : l'accès de l'IA peut être encore restreint à un purpose spécifique (ex: "cet agent est pour l'optimisation supply chain et ne peut pas accéder aux données RH même si l'utilisateur le peut")
- **Empêche l'IA de devenir un canal d'exfiltration cross-domaine** : même si un utilisateur a accès aux données RH et finance, un agent scopé à finance ne peut pas surfacer les données RH

### Brevets Sécurité

**US9081975B2 / US9836523B2 — Partage entre Nexus à Schemas de Classification Différents (2015) :**
- Structure de classification : markings (Top Secret, Secret, Confidential, Restricted, Unclassified) + classifications d'origine
- Règles de traduction **asymétriques** (aller et retour peuvent différer)
- Traduction par chemin le plus court pour minimiser la dégradation de précision
- Invariant de réplication : données exportées et réimportées doivent conserver leurs markings originaux

**US9857960B1 — Collaboration de Données (2018) :**
- Cinq critères de rédaction progressifs : classification, provenance, type d'objet, type de propriété, type de media
- Résolution d'import par déconfliction basée sur timestamp

**US20230306000A1 — Partage d'Actifs Data (2023) :**
- Partage par mise à jour des markings de namespace — pas de déplacement de données
- **Révocation transitive de permissions** : quand l'accès amont est refusé, les datasets dérivés en aval héritent automatiquement des restrictions via la chaîne de lineage
- Minimisation de données : filtrage au niveau colonne et ligne appliqué automatiquement

**US11593317B2 — Journalisation d'Activité Inviolable (2023) :**
- Architecture double-datastore : logs dans un repository append-only immutable et un journal système accessible client
- Journalisation en chunks de 50 Ko, chiffrés, compressés, hashés (SHA-1 ou SHA-512)
- Hash comme adresse (stockage adressable par contenu, similaire au object store de git)
- Détection multi-couche : détection d'intrusion, sécurité kernel, journalisation des frappes clavier, audit d'appels système

**US20240346388A1 — Entraînement LLM Conscient de la Sécurité (2024, en attente) :**
- Segmentation des datasets d'entraînement par niveau de permission
- Entraînement de modèles séparés par tier de sécurité
- Routage à l'inférence selon le niveau de permission des requêtes
- Fondamentalement plus sécurisé que les systèmes RAG avec filtrage post-génération

---

## 4.11 Brevets Techniques Clés

### Brevets Ontologie

**US7962495B2 / US9589014B2 — Ontologie Dynamique (2006) :**
- L'ontologie est incarnée dans un schema de base de données — pas un concept abstrait
- Object Types identifiés par des URIs (héritage RDF/web sémantique)
- Parser definitions éditables à l'exécution — ontologie genuinement dynamique
- Contraintes de type explicites validant les données entrantes
- Structure modifiable sans reconstruire le datastore sous-jacent

**US20200293561A1 — Object Platform for Datasets (2020) :**
- Cinq moteurs : datastore, definition engine, association engine, cache engine, interface engine
- Les objets sont une **couche de vue** sur des données relationnelles/tabulaires
- Stratégie de caching : architecture de vues matérialisées
- Résolution de conflits via commit logs avec "timestamps and vector clocks"
- Trois APIs : Object Search API, Object Load API, Object Modify API

**US10754822B2 — Migration d'Ontologie (2020) :**
- Migration basée sur des "stacks" (environnements de déploiement)
- Traduction d'identifiants de datasets entre stacks, pas déplacement de données
- Sélection de migration selective d'objets spécifiques

**US10061828B2 — Réplication Multi-Master Cross-Ontology (2016) :**
- Trois approches de mapping : One-to-One, One-to-Many, Drop Lists
- Validation pre-export par simulation de transformations aller-retour
- Digest cryptographique pour prévenir la dérive silencieuse des mappings
- Solution pour le partage inter-agences (CIA/NSA)

**US10248722 — Support Multi-Langue pour Ontologie Dynamique :**
- Système de types à trois piliers (object types, property types, link types)
- Support multi-langue pour déploiements internationaux/coalition

### Brevets Pipeline

**US9946738B2 / US10853338B2 — Universal Data Pipeline (2014/2018) :**
- **Principe d'immutabilité** : les données ne sont JAMAIS écrasées. Nouvelles versions créées à côté des historiques
- Delta encoding : versions stockées comme "differences or deltas between dataset versions"
- Protocole de transaction en trois phases : initiation, opérations d'écriture, engagement
- DAGs de dépendances avec parcours en profondeur post-order
- Rebuild en cascade via file de messages
- Build Catalog pour traçabilité complète

**US20210149857A1 — Branching de Pipeline (2020) :**
- Branche master avec pointeurs vers snapshots + logique
- Création de branche test avec sémantique copy-on-write
- Opération merge remplaçant la logique master

**US20250094439A1 — Optimisation de Réponse LLM pour Génération de Pipeline (2024, en attente) :**
- Langage informatique propriétaire optimisé pour l'efficacité de tokens LLM — "2x to 100x more efficient than conventional languages"
- Parsers ANTLR pour parser les sorties LLM en code de pipeline executable
- Instructions de "mistake context" dans les prompts (prévention d'erreurs few-shot)

### Brevets Workshop

**US11500620B2 — Workshop : Workflow Application and UI Builder (2022) :**
- Architecture widget : composants modulaires dans des containers de layout
- Type safety : le builder valide que les inputs/outputs adhèrent aux data object types spécifiques
- Function registry : logique workflow stockée séparément, référencée par les widgets
- Preview WYSIWYG en temps réel

**US11842171B2 — Function Access System (2023) :**
- Cinq composants : Ontology Data Store, API Generation Engine, Function Data Store, Function Manager Engine, Data Object Data Store
- Régénération automatique d'API sur changements d'ontologie
- Fonctions multi-langages (C, Java, Python, Ruby, JavaScript)
- Exécution sandboxée avec limites de ressources
- Contrôle d'accès appliqué au niveau API, pas au niveau données

### Brevets Apollo

**US10263845B2 — Déploiement de Configuration Continue (2019) :**
- Repository de configuration hiérarchique central
- Pre-caching : les sous-serveurs cachent les objets avant les fenêtres de maintenance
- Génération context-aware : un seul objet de définition génère différents objets par système
- Capacité de réseau maillé : les systèmes peuvent requêter des objets depuis des sous-serveurs pairs
- Exécution automatisée : objets contenant des APIs et handlers

**US11444854 — Métriques d'Utilisation Logiciel (2022) :**
- Télémétrie centralisée depuis tous les environnements de déploiement

**Déploiement canary/feature flagging :** utilisateurs assignés à des "tracks" avec différentes versions des mêmes composants.

### Brevets AI/LLM

**EP4443310A1 — Interfaces Système IA (2024) :**
- Architecture en trois couches : Orchestrator Selector -> Service Orchestrators -> Data Processing Services
- LLMs servent deux rôles : sélection de service et formatage de requête
- In-prompt training : exemples directement dans les prompts
- Architecture plugin : services exposés via APIs
- Injection de contexte : permissions utilisateur, analyses précédentes, schemas de données

**US20240419658A1 — Système IA Basé sur Profils (2024) :**
- Profil à quatre composants : Knowledge Bases, Functions, Plugins, Templates
- Plugins activent avant (pour peupler le prompt) et après (pour traiter les résultats)

**US20240346388A1 — Entraînement LLM Conscient de la Sécurité (2024, en attente) :**
- Segmentation des datasets d'entraînement par niveau de permission
- Modèles séparés par tier de sécurité, combinés via modèle ensemble à l'inférence

---

## 4.12 Analyse de Réplicabilité

### Par Couche : de 95% (Data Processing) à 30% (Operational Ontology)

| Couche | Réplicabilité OSS | Alternatives principales | Analyse du gap |
|--------|-------------------|-------------------------|----------------|
| **Data Processing** | ~95% | Apache Spark, Apache Flink, DuckDB | Quasi-identique. Palantir utilise ces moteurs exacts. Le gap est dans la couche de gestion unifiée. |
| **Storage** | ~95% | Apache Iceberg, Apache Parquet | Quasi-identique. Palantir utilise Parquet en interne. |
| **Orchestration** | ~80% | Apache Airflow, Dagster | Alternatives solides. Gap : l'orchestration de Palantir est ontology-aware. |
| **Data Integration** | ~75% | Airbyte (~300 connecteurs) | Airbyte dépasse Palantir en nombre de connecteurs. Gap : architectures agent-based proxy et air-gapped worker manquantes. |
| **App Building** | ~65% | Retool, Appsmith | Bonnes plateformes low-code. Gap : pas ontology-native. |
| **AI / LLM** | ~60% | LangChain, LlamaIndex | Équivalents framework-level. Gap : pas d'injection de contexte Ontologie typé, pas d'architecture guardrail multi-niveau, pas d'héritage de permissions. |
| **CI/CD** | ~50% | ArgoCD + Terraform | ArgoCD est pull-based (GitOps). Gap : pas de planning constraint-based, pas d'opération autonome hub-spoke, pas de readiness air-gap/edge. |
| **Metadata** | ~45% | DataHub, Apache Atlas | Catalog-oriented, pas opérationnel. Ils décrivent les données ; ils ne gouvernent pas l'accès et la mutation runtime. |
| **Security** | ~40% | Apache Ranger + OPA | Row-level security possible. Gap : pas de cell-level ACL, pas de markings obligatoires, pas de link-visibility semantics, pas de contrôles de contexte d'exécution IA. |
| **Operational Ontology** | ~30% | Aucun équivalent | La couche la plus dure à répliquer. Aucun projet open-source ne combine entités typées + actions + fonctions + interfaces + sécurité + indexation temps réel en un modèle opérationnel unifié. C'est le coeur du IP. |

### Stratégies PostgreSQL pour Chaque Couche

> Principe directeur : "Copy the contracts, not the code."

| # | Stratégie | Guidance d'implémentation |
|---|-----------|--------------------------|
| **1** | Stable Ontology IDs + Name Aliases | Chaque Object Type, Property et Link Type reçoit un UUID stable. Les noms sont des alias mutables. Toutes les références internes utilisent l'UUID. |
| **2** | Funnel-Like Orchestrator | Implémenter comme composant logique : changelog generation -> merge-with-user-edits -> build search artifacts -> atomic cutover. Peut démarrer comme fonction PostgreSQL + background job. |
| **3** | User Edits as Append-Only Log | Table append-only dédiée avec résolution de conflits explicite. Défaut : "user edits win." Support alternative : "most recent value." Le log n'est jamais tronqué. |
| **4** | Actions as Atomic Commits | Transactions PostgreSQL avec concurrence optimiste (check de colonne version au commit). Deux classes d'effets de bord : writeback transactionnel (même transaction DB) et best-effort (async, via job queue, at-least-once). |
| **5** | Expose Constraints as Product Behavior | Rendre les contraintes visibles : property hints indexés, caps de profondeur de traversée, limites de throughput, sémantiques at-least-once. Ce sont des contrats produit, pas des détails d'implémentation. |
| **6** | Multi-Datasource per Object Type | Un seul Object Type peut être adossé à plusieurs sources. La logique de merge et résolution de conflits sont explicites et auditables. |
| **7** | Edit-Only Properties | Propriétés sans source pipeline — valeurs purement user-entered. Stockées exclusivement dans le log d'edits. |

---

## 4.13 Contradictions Techniques

| # | Sujet | Description |
|---|-------|-------------|
| **1** | **Types Set et Map** | Une source (Claude) liste `Set` et `Map` comme types de propriétés supportés. Les autres sources ne les mentionnent pas et citent explicitement une liste "load-bearing" qui ne les contient pas. |
| **2** | **Outil de migration intégré** | Une source dit qu'il n'existe pas d'outil de migration comparable à Flyway. D'autres sources décrivent un framework de migration OSv2 détaillé avec 7 types de migrations, onglet dédié, et blocage automatique. Résolution probable : distinction OSv1 (pas d'outil) vs OSv2 (framework complet). |
| **3** | **Mixing visuel et code dans Pipeline Builder** | Une source affirme le support total via Custom Code nodes avec éditeur Monaco. D'autres disent explicitement que le mixing se fait au niveau dataset boundary, pas inside a node. Pipeline Builder est l'outil no-code ; Code Repositories est pour le code. |
| **4** | **AIP Logic runtime** | Une source dit que le LLM génère du code déterministe au dev-time, pas au runtime. D'autres décrivent des blocs LLM exécutant au runtime avec traces de raisonnement, confirmé par les démos AIPCon. Le consensus penche vers l'exécution LLM au runtime. |
| **5** | **Sneakernet / déploiement air-gap** | Une source dit que les détails ne sont pas publiquement documentés. D'autres donnent des détails précis sur les Apollo Bundles (diffs compressés, media physique, checkpoints de vérification) et le Binary Transfer Service. |
| **6** | **Column-level lineage** | Une source décrit le parsing du Catalyst plan Spark et le tracking explicite par noeud Pipeline Builder. D'autres ne décrivent qu'un lineage dataset/transaction et disent que le lineage cellule/ligne n'est PAS une feature standard. |
| **7** | **GeoPoint vs Geohash** | Les dénominations varient (`Geopoint`, `GeoPoint (lat/lng)`, `Geohash (GeoPoint)`) mais le type sous-jacent semble être le même. |
| **8** | **Localisation du bouton de création dans Ontology Manager** | Trois sources placent le bouton à des endroits différents (top bar, toolbar, haut à droite avec dropdown). Le workflow décrit est le même. |
| **9** | **Nombre de connecteurs** | Certaines sources indiquent "150+ native connectors", d'autres "400+ connectors". La différence peut s'expliquer par le comptage (connecteurs natifs vs total incluant JDBC custom, webhooks, etc.). |
| **10** | **Nombre de fonctions d'expression** | "300+ built-in functions" dans certaines sources vs "500+ fonctions built-in" dans d'autres. L'écart peut refléter des mises à jour de version ou des méthodes de comptage différentes. |
