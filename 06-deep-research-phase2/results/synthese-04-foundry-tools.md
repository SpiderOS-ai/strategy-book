## Synthese 4 — Foundry Tools: Comment ca marche concretement

---

### 1. Ontology Manager — Anatomie de l'interface

L'Ontology Manager (OMA) est accessible depuis la sidebar de navigation de Foundry. C'est l'application centrale ou les developpeurs definissent le modele de donnees type — Object Types, Properties, Links, Interfaces — consomme par le reste de la plateforme.

**Layout general :**

- **Top bar** : recherche globale sur les ressources ontologiques, creation de nouvelles ressources, et switching/creation de branches (GPT).
- **Sidebar gauche** : navigateur de ressources, avec une vue "Discover" configurable affichant favoris, types recemment consultes et groupes (GPT). Claude et Perplexity decrivent egalement une arborescence hierarchique de tous les Object Types, Link Types et Interfaces avec recherche.
- **Zone centrale** : panneau affichant la configuration de l'entite selectionnee, avec onglets (Overview, Properties, Links/Datasources, Actions, Permissions, Interfaces) (GPT, Claude, Perplexity).
- **Top toolbar** : boutons "+ Create" / "New" pour creer de nouvelles entites ontologiques (Claude, Perplexity).

[CONTRADICTION] **Localisation du bouton de creation** : GPT decrit le bouton de creation dans la top bar. Claude le situe dans le toolbar. Perplexity le place en haut a droite de la homepage avec un dropdown "New". Les trois decrivent le meme workflow mais situent le bouton differemment dans l'UI.

**Vues d'entites distinctes dans l'OMA** (GPT) :
- **Object type view** : sous-sidebar gauche avec pages (Overview, Properties, Datasources, Interfaces...) et panneau droit avec le contenu de la page selectionnee.
- **Property editor view** : interface d'edition dediee ouverte en selectionnant une propriete.
- **Link type view** : ouverte depuis le graphe de types de liens, avec pages Overview/Datasources.
- **Action type view** et **Function type view** : chacune avec ses propres onglets d'observabilite ; les fonctions sont editees dans un code repository, pas en inline.

**Modele mental** (GPT) : l'Ontology Manager se comporte comme un **schema IDE git-branch-aware** ou tout est stage puis commite dans l'ontologie.

La homepage de l'OMA affiche une table searchable de tous les Object Types existants, groupes par labels configurables (Perplexity).

---

### 2. Creation d'un Object Type — Pas a pas

Palantir documente deux methodes : un **assistant guide** (chemin principal) et une **completion manuelle** si on sort tot de l'assistant (GPT, Perplexity).

**Workflow complet :**

1. **Cliquer** sur "New > Create object type" / "+ Create Object Type" depuis l'Ontology Manager (GPT, Claude, Perplexity).
2. **Entrer un display name** (ex: "Customer") et un **API name** (auto-genere, ex: `customer`, mais editable). Optionnellement choisir une icone et ecrire une description (Claude, Perplexity).
3. **Selectionner un backing dataset** — parcourir ou rechercher dans le catalogue de donnees Foundry et pointer vers un dataset. **Chaque Object Type est adosse a exactement un dataset** (Claude, Perplexity). Si on n'a pas encore de dataset, Foundry peut generer un dataset vide a l'emplacement choisi (Object Storage V2 uniquement) (Perplexity).
4. **Definir le primary key** — selectionner la colonne qui identifie uniquement chaque instance d'objet. Le primary key doit etre unique, deterministe, pas aleatoire (GPT, Claude, Perplexity). Le timestamp comme primary key est explicitement deconseille (GPT).
5. **Mapper les colonnes vers des proprietes** — l'UI auto-detecte les colonnes et suggere des mappings (Claude). Un bouton specifique "Add all unmapped columns as new properties" infere IDs, display names et base types depuis le schema du dataset source (GPT, Perplexity). L'editeur a deux panneaux : colonnes datasource a gauche, proprietes mappees a droite (Perplexity).
6. **Configurer le title key** — la propriete qui sert de nom d'affichage dans les UIs (ex: `full_name` pour un Employee) (GPT, Claude, Perplexity).
7. **Optionnellement generer des actions standard** — l'assistant peut auto-creer des Action Types edit/create/delete et les assigner a un utilisateur/groupe (Perplexity).
8. **Choisir un projet** d'enregistrement et cliquer "Create" (cela stage les changements seulement). Puis cliquer **"Save"** en haut a droite de l'Ontology Manager pour appliquer a l'ontologie (GPT, Perplexity).

**Si on quitte l'assistant tot** (GPT) : l'object type reste "unsaved" jusqu'a ce qu'on complete manuellement la checklist : ajouter metadata, ajouter un backing datasource, ajouter des proprietes, mapper les proprietes, configurer primary et title keys.

---

### 3. Proprietes — Systeme de types et editeur

Une propriete est la definition de schema d'une caracteristique d'un object type ; mapper une propriete a une colonne fait apparaitre les valeurs reelles dans les apps (GPT).

**Types de base supportes :**

| Categorie | Types |
|---|---|
| **Texte / Booleens** | `String`, `Boolean` |
| **Numeriques** | `Integer`, `Short`, `Byte`, `Long`, `Float`, `Double`, `Decimal` |
| **Temporels** | `Date`, `Timestamp` |
| **Geospatiaux** | `GeoPoint`/`Geohash`, `GeoShape`, `GeotimeSeriesReference` (Perplexity) |
| **Complexes** | `Array` (pas de null ; pas de nested arrays en OSv2), `Struct` (pas de nesting ; champs ne peuvent pas etre des arrays), `Vector` (pour embeddings ML) |
| **Speciaux** | `Attachment`, `MediaReference`, `Timeseries`, `Marking`, `CipherText`/`Cipher` |

[CONTRADICTION] **Types Set et Map** : Claude liste `Set` et `Map` comme types supportes. GPT et Perplexity ne les mentionnent pas dans les types de proprietes ontologiques. GPT cite explicitement une liste "load-bearing" qui ne contient ni Set ni Map.

[CONTRADICTION] **Geohash vs GeoPoint** : GPT utilise `Geopoint`, Claude utilise `GeoPoint (lat/lng)`, Perplexity utilise `Geohash (GeoPoint)`. Le type sous-jacent semble etre le meme mais la denomination differe.

**Contraintes sur les types** (GPT) :
- `Long` a des problemes de representation JavaScript ; souvent recommande d'utiliser String a la place.
- `Decimal` ne peut pas etre primary key.
- `Timestamp` comme primary key est deconseille.
- `Array` : pas d'elements null, pas de nested arrays en OSv2.
- `Struct` : pas de nesting, champs ne peuvent pas etre des arrays, max 10 champs (GPT), semantiques de requete non-intuitives pour les arrays de structs.

**Editeur de proprietes** (GPT) : L'editeur de metadata de propriete expose : display name, description, status (experimental/active/deprecated), API name, designation de cle (title/primary), formatage de valeur, formatage conditionnel, type classes, render hints (toggles searchable/sortable affectant le comportement d'indexation), et visibilite (prominent/hidden).

L'edition de proprietes peut etre faite individuellement ou en **bulk** (GPT). L'edition bulk supporte : changement de base type, ajout/suppression de type classes, render hints, visibilite et formatage.

**Struct** : cree en choisissant "Struct" comme base type, en selectionnant une colonne backing, puis en ajoutant des champs dans une section "Struct fields" (GPT). Permet des champs JSON-like imbriques — ex: une struct Address avec `street`, `city`, `zip` (Perplexity). Mais n'est **pas** un type "nested JSON" general : c'est une feature de schema contrainte (GPT).

**Media references** : "juste un base type", mais necessite que le dataset de support contienne une colonne de reference media et que l'object type ait une media source configuree dans son onglet Capabilities pointant vers le media set correspondant (GPT).

---

### 4. Link Types — Relations et cardinalites

Un link type est la definition de schema d'une relation entre deux object types ; une instance de lien est analogue a une ligne jointe representant une instance de relation (GPT).

**Creation** :
- Naviguer vers Ontology Manager > `New > Link type`, ou depuis la page Overview d'un object type > "Create new link type" depuis le graphe de types de liens (Perplexity).
- L'assistant guide propose : selectionner la cardinalite, configurer les cles, nommer la relation.

**Cardinalites supportees** : 1:1, 1:N, N:1, M:N (GPT, Claude, Perplexity).

**Mecanique des cles etrangeres** :
- Pour 1:1 ou M:1 : definir une **foreign key** sur un object type qui refere au **primary key** de l'autre. Exemple : `Flight.tailNumber` (FK) -> `Aircraft.tailNumber` (PK) (Perplexity).
- Pour M:N : un **troisieme backing dataset** (table de jonction) est requis. Ce dataset ne necessite que les colonnes primary key des deux object types. Chaque ligne represente une instance de lien (GPT, Perplexity).

[CONTRADICTION] **Les liens sont-ils stockes comme des edges dans un graph database ?** Claude affirme explicitement : "links are not stored as edges in a graph database. They are resolved at query time by joining on the specified foreign key columns in the backing datasets." GPT dit que "links are not virtual edges" mais explique qu'ils sont crees en ajoutant des backing datasources aux object types. Perplexity precise que la cardinalite est "a modeling hint" et que one-to-one n'est pas enforce au niveau data. La distinction est subtile : les trois s'accordent sur le fait que c'est un mecanisme relationnel (join), pas un graphe, mais Claude est le plus categorique et le seul a affirmer que la resolution se fait "at query time".

**Object-backed link types** (GPT) : construct de modelisation de premiere classe. On peut representer une relation comme son propre object type pour stocker des metadonnees sur la relation elle-meme (exemple : un objet Flight Manifest liant Aircraft et Flight, avec des proprietes supplementaires comme Pilot). Regle : "si vous avez besoin d'attributs sur l'edge, Foundry vous dit de promouvoir l'edge en un object-backed link."

**L'UI auto-cree le lien inverse** (Claude). Apres soumission, il faut **sauvegarder dans l'Ontology Manager** pour appliquer (GPT).

**Dans les bindings TypeScript** (GPT) : le cote "1" donne un `SingleLink` et on appelle `get()` ou `getAsync()`.

---

### 5. Interfaces — Types abstraits et polymorphisme

Les interfaces decrivent la "forme" et les capacites des object types, permettant le **polymorphisme** sur plusieurs implementations (GPT, Claude, Perplexity).

**Creation** (GPT, Perplexity) :
- Selectionner New > Interface (ou via la page Interfaces).
- Fournir display name et API name, description optionnelle et icone.
- Ajouter des proprietes a l'interface, marquer chacune required ou optional.

**Proprietes d'interface** : contraintes de proprietes abstraites que les object types implementants doivent mapper sur des proprietes concretes (Perplexity).

**Contraintes de link type d'interface** (Perplexity) : liens abstraits avec une cardinalite (`ONE` ou `MANY`), description, API name, et une entite liee qui peut etre une autre interface ou un object type concret. Flag `required` pour indiquer si chaque object type implementant doit fournir au moins une implementation d'un lien donne.

**Exemple** (Perplexity) : une interface `Facility` declare un lien optional one-to-many vers `Airline`. `Airport` et `Seaport` peuvent tous deux implementer `Facility`, chacun fournissant son propre lien concret vers `Airline`.

**Implementation** (GPT) :
- Depuis l'onglet Interfaces d'un object type, selectionner "Implement new interface", choisir l'interface, puis mapper les proprietes requises de l'interface sur des proprietes existantes de l'objet (les proprietes optionnelles peuvent etre omises).
- Si l'interface declare des contraintes de link type requis, il faut mapper des link types qui satisfont chaque contrainte ; on peut choisir un link type existant ou en creer un nouveau pendant le mapping.

**Cas d'usage concret** (Claude) : un widget map Workshop peut afficher tous les objets "HasLocation" (interface avec `latitude: Double`, `longitude: Double`) quel que soit le type concret — cela active les requetes polymorphiques.

**Limitation** (GPT) : l'implementation des interfaces dans Pipeline Builder supporte le mapping de proprietes, mais **ne supporte pas le mapping de contraintes de link type** ; cela doit etre fait dans Ontology Manager.

---

### 6. Functions — Logique calculee et proprietes computees

Foundry distingue le schema ontologique (types, proprietes, liens, actions) de la logique executable (Functions, Actions, AIP Logic) (GPT).

**Environnement** : les Functions sont ecrites en **TypeScript** dans un **Functions Repository** / Code Repository dedie. L'Ontology Manager expose un "Function type view" mais les modifications se font dans le repository de code, avec un bouton "Open in Code Repository" (GPT, Perplexity).

**API TypeScript v1** (Claude, Perplexity) :
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

Les fonctions utilisent le decorator `@Function()`, l'acces type-safe auto-genere a l'ontologie via `@foundry/ontology-api`, la traversee de liens, et peuvent etre exposees comme proprietes computees sur des Object Types ou comme handlers d'Actions via `@Action()` (Claude).

**API TypeScript v2** (Perplexity) : utilise `@osdk/functions` avec `createEditBatch`, `Edits.Object<T>` et `Edits.Link<T>` types pour les edits batch.

**Edit Functions** (Perplexity) : annotees avec `@OntologyEditFunction()` et `@Edits(ObjectType)`. Peuvent creer des objets (`Objects.create().ticket(primaryKey)`), modifier des proprietes (`employee.lastName = newName`), set/remove links, et supprimer des objets.

**Capacites** (GPT) : lecture de proprietes, traversee de liens, edits ontologiques, resultat utilisable dans Workshop et Actions. L'Object Table de Workshop supporte les "derived columns generated on-the-fly via a Function" (GPT).

**Gestion des timestamps** (Perplexity) : utiliser `Timestamp.fromISOString(...)` depuis l'API functions de Foundry.

Les fonctions alimentent les Action Types (writeback), les valeurs computees Workshop, et les integrations AIP Logic (Perplexity).

---

### 7. Framework de decision — Object Type vs Property vs Link vs Struct

**Analogie fondamentale** (Perplexity) : Object Type = Dataset, Object = Row, Property = Column, Link = Join.

**Heuristique FDE** (Claude) : "Can someone walk up to this entity and ask questions about it in isolation?" Si oui, c'est un Object Type. (Perplexity) : "Will someone ever search for, filter on, or take an action on this entity independently?" Si oui -> Object Type.

**Creer un Object Type quand** :
- L'entite a sa propre identite et cycle de vie : elle a un primary key stable, est creee/modifiee independamment, ou a des edits de writeback qu'on veut preserver (GPT).
- L'entite a besoin d'etre liee depuis plusieurs endroits (GPT).
- La "relation" elle-meme a besoin d'attributs -> object-backed link types (GPT).
- L'entite a ses propres proprietes independamment consultees/filtrees (Perplexity).
- Les utilisateurs doivent prendre des actions dessus independamment (Perplexity).
- Elle a **plus de 2-3 attributs** (Claude).
- Elle a besoin de permissions independantes (Claude).

**Garder comme Property quand** :
- C'est un attribut concernant uniquement l'objet parent et n'a pas besoin de son propre cycle de vie (GPT).
- Attribut simple de 1-3 champs, unique a son parent, jamais query independamment, change toujours avec le parent (Claude).
- On beneficie de render hints, formatage et controles de searchabilite au niveau propriete (GPT).

**Utiliser un Link quand** :
- La relation est navigationnelle et queryable comme une relation, pas juste un string foreign key (GPT).
- L'entite est partagee entre plusieurs parents (Claude, Perplexity).

**Utiliser un Struct quand** :
- On veut un groupe borne, schema'd de champs imbriques qui se comporte comme "une propriete" (GPT).
- Groupe logiquement lie de champs qui appartiennent a l'objet parent mais avec structure nestee (Perplexity).
- On peut vivre avec les contraintes strictes : profondeur 1 (pas de nesting), max 10 champs, types de champs limites, semantiques de requete non-intuitives pour les arrays de structs (GPT).

### Exemple pratique : "Customer Address"

**Adresse comme simple attribut (Property)** : quand l'adresse est single-valued, change rarement, n'est pas une entite independante. Implementation : quelques proprietes comme `street`, `postcode`, `city`, `country` mappees directement depuis le backing dataset (GPT, Claude).

**Adresse comme sous-structure bornee (Struct)** : quand on veut "adresse" comme un seul champ conceptuel mais avec des composants structures, en restant dans les contraintes de struct. Si les adresses n'ont pas besoin de cycle de vie independant, liens ou actions (GPT, Claude, Perplexity).

**Adresse comme entite de premiere classe (Object Type lie)** : quand les adresses ont leur propre cycle de vie — adresses multiples par client, historique, workflows de validation, geo-enrichissement, deduplication, ou permissions au niveau adresse. Lien Customer <-> Address ; la relation peut etre "one-to-many" ou "many-to-many" si partagee (GPT, Claude, Perplexity).

**Extra Foundry** (GPT) : si on a besoin de metadata sur la relation elle-meme (ex: "address type", "valid from/to", "verified by", "source system"), les object-backed links sont le pattern canonique.

### Principes de design FDE

- **Start from user workflows, not data models** (Claude).
- **Ne pas sur-normaliser** — Foundry favorise la **denormalisation** pour la performance de requete (Claude).
- **Choisir des primary keys stables et immutables** ; les composite keys doivent etre concatenes en une seule colonne (Claude).
- **Linker avec parcimonie** — chaque lien ajoute de la complexite de requete (Claude).
- **Utiliser les interfaces** pour les preoccupations transversales plutot que dupliquer des proprietes (Claude).
- Modeler pour les **workflows operationnels d'abord**, puis pour l'analytique. L'app layer de Foundry recompense les types semantiques et navigables bien plus que les "raw tables with dozens of columns" (GPT).

---

### 8. Evolution de schema — Migrations et propagation

#### Changements non-breaking (pas de migration)

Ajouter une nouvelle propriete, changer display names, descriptions, title key, render hints, type classes, visibilite, reordonner les proprietes — juste editer dans l'Ontology Manager et sauvegarder (GPT, Claude, Perplexity). Supprimer ou changer des champs qui n'ont jamais recu d'edits est egalement non-breaking (GPT).

#### Changements breaking

- Changer les datasources d'entree (GPT, Perplexity)
- Changer le primary key (GPT, Perplexity)
- Changer le type d'une propriete (GPT, Perplexity)
- Changer le property ID si la propriete a des edits (GPT)
- Supprimer des proprietes editees ou des champs de struct (GPT, Perplexity)
- Changer le type d'un champ de struct (GPT, Perplexity)

#### Le split Object Storage : OSv1 vs OSv2

**OSv1 (Phonograph)** : ne peut PAS migrer les user edits en cas de changements breaking ; les changements de schema sont decourages et peuvent necessiter un unregister/reregister des datasources, risquant la perte d'historique d'edits (GPT).

[CONTRADICTION] **Existence d'un outil de migration** : Claude affirme que "Foundry's ontology has no built-in migration tool comparable to Flyway or Liquibase. Schema changes are manual." GPT et Perplexity decrivent un **framework de migration integre dans OSv2** qui detecte automatiquement les changements breaking, affiche un warning, introduit un onglet Migrations dans le flux "Review changes", et bloque la sauvegarde jusqu'a ce qu'une option de migration soit specifiee. La contradiction s'explique probablement par le fait que Claude decrit l'etat general/OSv1 tandis que GPT et Perplexity decrivent la fonctionnalite OSv2 specifique.

#### Framework de migration OSv2

Quand on fait un changement breaking, l'Ontology Manager le detecte automatiquement et bloque la sauvegarde jusqu'a ce qu'on selectionne une migration depuis l'onglet **Migrations** (GPT, Perplexity) :

| Migration | Cas d'usage |
|---|---|
| **Drop all property edits** | Supprimer une propriete sans remplacement |
| **Drop all struct field edits** | Restructuration de struct |
| **Drop all edits** | Reset complet vers l'etat datasource |
| **Move edits** | Renommer une propriete ou deplacer vers un nouveau backing dataset |
| **Cast property to new type** | Changer `String` -> `Integer`, etc. (Perplexity) |
| **Move struct field edits** | Restructuration au sein d'un struct (Perplexity) |
| **Revert migration** | Annuler une migration precedemment appliquee (Perplexity) |

**Limite** : max 500 migrations de schema a la fois ; les migrations de propriete primary key ne sont pas supportees par le framework (Perplexity).

#### Le pattern "replacement pipeline"

Quand on sauvegarde un changement breaking dans l'Ontology Manager (GPT, Perplexity) :
1. Une nouvelle version de schema est creee en backend.
2. Un **"replacement Funnel batch pipeline"** est orchestre pour mettre a jour l'index de l'object type.
3. La nouvelle version devient queryable une fois le remplacement termine et la nouvelle version declaree entierement hydratee par les object databases.

Ce mecanisme est **versionne via un pipeline de rebuild d'index**, pas une mutation in-place (GPT).

#### Le pattern "side-by-side" pour Claude

Claude decrit un pattern alternatif (pour les cas hors OSv2 ou pour des changements majeurs) :
1. Creer une nouvelle version du backing dataset avec le nouveau schema.
2. Creer un nouvel Object Type (ex: `CustomerV2`).
3. Migrer tous les consommateurs (Workshop apps, Functions, OSDK clients).
4. Tester dans une branche de developpement.
5. Basculer et deprecier l'ancien type.

#### Branching et ontology-as-code

Foundry supporte le **branching de datasets et de code** — on peut faire des changements de schema sur une branche, pointer l'Ontology Manager vers cette branche pour tester, valider, puis merger (Claude, GPT).

Pour les utilisateurs avances, les definitions de schema ontologique peuvent etre **exportees en JSON**, editees en externe, et reimportees, permettant des workflows "ontology as code" (GPT). C'est puissant mais operationnellement risque : on bypass les guardrails UI sauf si on les replique dans le process (GPT).

Certaines equipes maintiennent les definitions ontologiques dans des code repositories utilisant l'Ontology API, permettant des review workflows avant que les changements atteignent la production (Claude).

---

### 9. Pipeline Builder — ETL visuel

#### Interface

Pipeline Builder est un constructeur **base sur un graphe DAG** avec une vue canvas comme element principal (GPT, Claude, Perplexity).

**Layout** :
- **Panneau/sidebar gauche** : parcours/recherche de datasets d'entree (GPT, Claude, Perplexity).
- **Canvas central** : noeuds connectes par des edges montrant le flux de donnees, avec outils de panning/drag-select/layout (GPT, Claude, Perplexity).
- **Panneau/sidebar droit** : configuration du noeud selectionne (Claude) ; panneau Outputs montrant datasets outputs + outputs orientees ontologie (object types et link types), incluant edition de schema et erreurs (GPT).
- **Panneau de preview en bas** : echantillonnage des donnees du noeud selectionne ; click-droit sur un noeud dataset pour ouvrir la preview complete (GPT, Claude, Perplexity). Claude precise que la preview se met a jour **en temps reel** quand on modifie chaque etape.

#### Creation d'un pipeline

1. Ouvrir Pipeline Builder et creer un nouveau pipeline.
2. Ajouter des datasets d'entree comme noeuds source (drag depuis la sidebar ou bouton "Add datasets") (GPT, Claude, Perplexity).
3. Chainer des noeuds de transformation — cliquer sur le "+" en sortie d'un noeud pour ajouter des transforms (Claude).
4. Configurer un noeud de dataset output avec un chemin Foundry (Claude).
5. Sauvegarder, puis Build / Deploy pour les schedules de production (Perplexity).

Compiler le graphe visuel produit un **plan d'execution Spark optimise** (Claude).

#### Noeuds de transformation disponibles

Pipeline Builder distingue deux primitives de transformation dans l'UI (GPT) :
- **Expressions** : colonne in, colonne out (ex: "Split string", "Cast", "Concatenate strings").
- **Transforms** : table in, table out (ex: Pivot, Filter).

**Catalogue complet** :

| Categorie | Noeuds |
|---|---|
| **Structural** | Filter (conditions AND/OR composees), Join (inner, left/right/full outer, cross, semi/anti — avec previews et onglet Errors), Union (retient les doublons, combine toutes les lignes), Sort, Limit, Deduplicate (avec strategie de ranking) |
| **Reshaping** | Aggregate (SUM, COUNT, AVG, MIN, MAX, COUNT DISTINCT, STDDEV, PERCENTILE, COLLECT_LIST — group-by, batch seulement), Pivot (valeurs pivot fournies avant runtime pour schema connu), Unpivot, Flatten/Explode (pour arrays) |
| **Colonnes** | Select/Rename, Add Column (expression builder avec manipulation string, math, fonctions date, CASE WHEN), Cast Types, Window Functions (ROW_NUMBER, RANK, LAG, LEAD, running aggregates) |
| **Nettoyage** | Clean String, Trim Whitespace, Cast to Timestamp, Normalize Column Names (Perplexity) |
| **Custom Code** | Noeud PySpark ouvrant un editeur Monaco (Claude) |
| **Avances** | Geospatial joins, window aggregation pour streaming, media transforms, noeuds LLM (GPT) |

**Parametres et fonctions reutilisables** : Pipeline Builder supporte les parametres (variables) et fonctions reutilisables (Perplexity).

**Features AI** (Perplexity) : auto-naming des noeuds selon leur logique, auto-generation d'expressions regex depuis des descriptions en langage naturel.

**Controle de version** (Perplexity) : branching integre (comme git). On travaille sur une branche, on voit un diff vs main dans l'onglet Changes, et on merge quand c'est pret.

#### Peut-on mixer noeuds visuels et code PySpark ?

[CONTRADICTION] **Mixing visuel et code dans Pipeline Builder** :
- **Claude** affirme : "Mixing visual and code nodes is fully supported. You can insert a Custom Code node at any point, write PySpark that receives the upstream DataFrame, and return a transformed DataFrame that feeds into downstream visual nodes." Et fournit un exemple de code.
- **GPT** dit explicitement le contraire : "Not inside a single Pipeline Builder transform board in the way tools like Databricks notebooks mix code and UI." Le mixing se fait "at the dataset boundary, not inside a node." Pipeline Builder est l'outil "no-code" ; Code Repositories est pour les stages de code specialise. Les deux consomment et produisent des Foundry datasets, donc on peut inserer des datasets code-repo avant, apres, ou au milieu d'un pipeline Pipeline Builder.
- **Perplexity** prend une position intermediaire : "Pipeline Builder doesn't directly embed PySpark code inside visual nodes. However, the pattern is to prototype in Pipeline Builder and shift complex parts into Code Workbook or Code Repositories." Les output datasets sont les memes et alimentent le meme lineage.

Cette contradiction est significative : Claude decrit un "Custom Code node" avec editeur Monaco, tandis que GPT et Perplexity disent que le mixing se fait au niveau dataset boundary.

---

### 10. Code Repositories — API transforms et code reel

#### L'API Python transforms

L'API Python transforms Foundry (de la librairie `transforms`, open-sourcee sous `palantir/transforms-python`) est basee sur des decorators (GPT, Claude, Perplexity).

**`@transform`** — la forme la plus generale. Injecte des objets `TransformInput` et `TransformOutput` (Claude, Perplexity) :
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

**`@transform_df`** — le pattern le plus courant et une convenience wrapper qui injecte/retourne des DataFrames directement (Claude, Perplexity) :
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

**`@transform_pandas`** — meme chose mais pour des Pandas DataFrames (Perplexity).

**Syntaxe du decorator** (GPT) : `@transform.using(...)` pour declarer Inputs et Outputs ; les parametres de la fonction matchent ces declarations. Les inputs peuvent etre charges comme des dataframes Polars ou pandas pour le compute single-node par defaut ; Spark est disponible pour le compute distribue.

**Pipeline et registration** : chaque sous-projet Python transforms expose un `transforms.api.Pipeline` qui enregistre les datasets et localise/execute la logique de transform pendant les builds. L'enregistrement automatique via `discover_transforms()` est le defaut recommande pour la plupart des repos (GPT, Perplexity).

**Pattern typique "join and write"** (GPT) :
1. Declarer deux Inputs et un Output.
2. Lire les inputs comme Spark dataframes (ou Polars si petit).
3. Effectuer joins/cleans.
4. Ecrire le dataframe output vers le dataset cible.
Le mapping ontologique est une etape separee : on ecrit un dataset, puis on le mappe comme backing datasource.

Les transforms Spark peuvent prendre **plusieurs inputs et outputs** (explicitement documente) (GPT).

---

### 11. Scheduling des pipelines

Le scheduling Foundry est **dataset-centric** : les schedules executent des builds pour garder les pipelines a jour (GPT, Perplexity).

**Trois modes de declenchement** :
- **Time-based (Cron)** : expressions cron standard, ex: `"0 2 * * *"` pour daily a 2h. Constructeur cron visuel dans l'onglet Builds (Claude, Perplexity). Selecteur hourly/daily/weekly/monthly avec heures specifiques (Claude).
- **Event-driven (sur mise a jour des donnees)** : se declenche quand des datasets upstream specifiques sont mis a jour ("Build on upstream change") — configure en ajoutant des "trigger datasets" au schedule. Cree des chaines de build en cascade (Claude, Perplexity, GPT).
- **Logique mise a jour** : se declenche quand la logique a ete mise a jour (GPT).
- **Hybride** : event-based avec fallback timer (Perplexity).
- **Manuel** : le bouton "Build" declenche une execution ad-hoc (Claude).
- **Combinaison** de toute condition (GPT).

**Cibles de schedule** : un seul dataset, dependencies, dependents, datasets connectant deux datasets, ou combinaisons (GPT).

**Point d'entree UI** : depuis un dataset preview > Actions > "Manage Schedules", qui ouvre un graphe Data Lineage avec le panneau schedules a droite et un bouton "Create schedule" (GPT). Les schedules peuvent aussi etre crees depuis Data Lineage ou le Build Schedules UI (Perplexity).

**Dependency resolver** : Foundry resout automatiquement les upstream datasets et les build dans le bon ordre. Les transforms independants s'executent en **parallele** quand "Allow parallel builds" est active (Perplexity).

**Retry logic** et alerting sont egalement configurables (Perplexity).

Les schedules sont attaches aux datasets dans le build graph, et **Data Lineage est le control plane operationnel** pour eux (GPT).

---

### 12. Traitement incremental

Le traitement incremental est une feature de premiere classe : il utilise l'historique de build des transforms pour eviter de recalculer un output entier a chaque execution (GPT).

**Decorator `@incremental()`** (Claude, Perplexity) :
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

**Modes de sortie** (Claude) : `append`, `replace` (retombe au full recompute), et `modify` (upsert). `require_incremental=True` empeche un full recompute accidentel.

**Au niveau API** (GPT) : le decorator `incremental()` convertit les TransformInput/Output/Context normaux en contreparties incrementales (IncrementalTransformInput/Output/Context) en lisant l'historique de build depuis les output datasets.

**Contraintes** (GPT) :
- Foundry interdit explicitement que l'input et l'output soient le meme dataset (pour eviter les dependances cycliques).
- Le "simple default" ne fonctionne en securite que quand les lignes output ajoutees sont purement une fonction des lignes input ajoutees.
- Pour une logique complexe (joins, aggregations, distinct), utiliser incremental avec le decorator `transform()` complet pour controler les modes read et write.

**Cascading snapshots** (Perplexity) : si une quelconque input est snapshotted, le transform incremental se snapshotte automatiquement.

**`semantic_version`** (Perplexity) : incrementer ce numero force un full snapshot recompute, utile apres des changements de logique de code.

**Decorator `@configure`** (Perplexity) : controle les profils de ressources (nombre d'executors, memoire) et peut differer entre les runs snapshot et incremental.

---

### 13. Testing et CI pour le code pipeline

**Unit tests** (GPT, Claude, Perplexity) : Foundry supporte les tests **pytest** pour les repositories Python (batch pipelines uniquement) et peut executer les tests comme partie des checks.

**Module `transforms.testing`** (Claude) : fournit `mock_transform()` pour les tests unitaires avec des sessions Spark locales.

**Data quality checks** (Claude) : l'objet `Check` permet de definir des validations sur les outputs :
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

**CI integre** (Claude) : pousser sur une branche execute pytest automatiquement, et les PRs ne peuvent pas merger si les tests echouent.

**Mecaniques CI** (GPT) : `condaPackRun`, environment caching, et style checks optionnels via Gradle plugins. La sante du pipeline est traitee comme partie du processus de build et release, pas "best effort".

Palantir fournit aussi un framework de unit testing pour les transforms PySpark avec mock DataFrames, execution de la logique de transform et assertions de resultats (Perplexity).

---

### 14. Data Lineage — Tracabilite et securite

#### Tracking automatique

Foundry suit automatiquement le lineage au niveau **dataset-transform-dataset**. Chaque declaration `Input()`/`Output()` cree un edge de lineage. Il n'y a **pas d'opt-in** — ce tracking est obligatoire (Claude, Perplexity).

Au niveau transaction, Foundry enregistre : quelles transactions d'entree ont ete consommees, quel code de transform (avec git commit hash) a ete execute, et quelles transactions de sortie ont ete produites (Claude).

#### Lineage au niveau colonne

[CONTRADICTION] **Column-level lineage** : Claude affirme que le lineage au niveau colonne est "infere en parsant le Catalyst logical plan de Spark" et que pour Pipeline Builder "each visual node's column flow is tracked explicitly." Claude decrit aussi un clic sur une colonne specifique pour voir un chemin surligne montrant exactement quelles colonnes upstream ont contribue. GPT dit que la fonctionnalite "find datasets with a given column" existe dans Data Lineage (recherche column-aware), mais precise que le lineage au niveau **cellule ou ligne** ("this exact field value came from that raw record") n'est PAS decrit comme une feature standard. Perplexity ne mentionne pas le column-level lineage.

#### Visualisation

Data Lineage est une application interactive pour visualiser comment les datasets circulent dans Foundry (GPT, Perplexity).

**Elements UI** (GPT, Perplexity) :
- Graphe de lineage interactif (DAG horizontal).
- Parametres de branche.
- Panneau lateral (Search & Browse ; Properties and Histogram ; Manage Builds ; Manage Schedules ; Related Artifacts).
- Panneau de details de noeud (dataset : nom, owner, last build time, health status).
- Outils de graphe et "Save graph".
- Noeuds datasets connectes par des edges de transform (Claude).

**Navigation** (Perplexity) :
- Rechercher un dataset, object type ou ressource et l'ajouter comme noeud.
- Cliquer sur les fleches gauche/droite pour expander parents (ancetres) ou enfants (descendants).
- Outil Expand avec controles de niveau — un niveau, plusieurs niveaux, ou jusqu'aux sources brutes.
- "Find relation between two nodes" montre tous les noeuds intermediaires.
- Coloration par type de transform, health status, groupements custom, ou couleurs assignees manuellement.
- Outils de layout : automatique, hierarchique, vertical, par niveau, ou par groupe de couleur.
- Outil Find pour chercher des noeuds ou noms de colonnes dans les datasets sur le graphe.

On peut **declencher des builds et definir des schedules** directement depuis le graphe de lineage (Perplexity).

#### Markings et propagation de securite

Les **markings** sont le mecanisme de controle d'acces obligatoire de Foundry ; un marking definit des criteres d'eligibilite pour l'acces (GPT).

**Propagation automatique** (Claude) : si Source A porte "SENSITIVE" et Source B porte "CONFIDENTIAL", leur output de join **herite automatiquement des deux markings**. C'est enforce au niveau plateforme — un developpeur ne peut pas manuellement baisser la classification d'un dataset derive en dessous de ce que le lineage implique.

Data Lineage peut **simuler l'impact de changements de markings** et indique explicitement les noeuds qui "stop propagating markings" via du code ; le panneau de proprietes du noeud affiche que l'acces aux donnees a ete modifie via du code (GPT).

**Mecanique de retrait** (GPT) : `stop_propagating` et `stop_requiring` sont des proprietes de transform input et ne peuvent pas etre ajoutees sur les outputs.

**Acces restreint** (Claude) : les utilisateurs qui n'ont pas acces aux datasets upstream voient ces noeuds de lineage comme des placeholders "restricted".

**Declassification** (Claude) : les transforms de "declassification" approuves (ex: pipelines d'anonymisation) peuvent reduire les markings, mais necessitent une approbation de gouvernance explicite et sont logues dans un audit trail immutable.

Le lineage dans Perplexity est integre avec le modele de permissions Foundry — on ne voit que les noeuds auxquels on a acces (Perplexity).

#### Rollback et provenance

**Pipeline rollback** (GPT) : utilise la provenance de donnees d'une transaction de dataset upstream pour identifier les datasets et transactions downstream et calculer un etat de rollback, evitant un rollback multi-etapes manuel.

**UX du rollback** (GPT) : selectionner un dataset dans un graphe de lineage, choisir une branche, selectionner une transaction dans History, puis "Rollback to transaction".

**Tracabilite** : la baseline est au niveau dataset et transaction (GPT). Le lineage au niveau cellule ou ligne n'est pas decrit comme une feature standard dans les docs publiques (GPT).

---

### 15. Workshop — Constructeur d'applications operationnelles

#### Interface

Workshop est un **constructeur d'applications no-code base sur un canvas** avec un systeme de grille/layout (Claude, Perplexity).

**Layout** :
- **Sidebar gauche** : listing des widgets par categorie (Claude, Perplexity).
- **Canvas central** : drag-and-drop pour placer les widgets dans un module layout avec sections (Claude, Perplexity).
- **Panneau de configuration droit** : configuration du widget selectionne (Claude, Perplexity).
- **Mode preview** pour tester (Claude).
- **Top toolbar** : controles pour ajouter des widgets, gerer les variables et previewer (Perplexity).

Les applications supportent **plusieurs pages, modules reutilisables et visibilite basee sur les roles** (Claude).

#### Bibliotheque de widgets

**Categorie completes** (Claude, Perplexity combinee) :

| Categorie | Widgets |
|---|---|
| **Core display** | Object Table, Object List, Object View, Property List, Links, Object Set Title, Details Panel, Card Sets |
| **Visualisation** | Charts (bar, line, area, pie, scatter), Chart XY, Pie Chart, Waterfall Chart, Vega Chart, Map (geospatial lat/lng ou GeoShape), Gantt Chart, Pivot Table, Timeline, KPI/Metric Card, Stepper, Status Tracker, Markdown |
| **Media** | Media Preview, PDF Viewer, Video Display, Audio + Transcription Display, Image Annotation, Spreadsheet Display |
| **Filtrage/Input** | Property Filter, Filter List, Object Dropdown, String Selector, Date Range Picker / Date and Time Picker, Slider, Search Bar, Toggle, Dropdown, Geo Filter (draw on map), Object Selector, Numeric Input, Text Input, Exploration Filter Pills, Exploration Search Bar, Prominent Term, User Select |
| **Actions** | Action Button, Button Group, Form, Bulk Action Button, Inline Action, Media Uploader, Audio Recorder |
| **AIP** | AIP Analyst, AIP Agent, AIP Generated Content (Perplexity) |
| **Layout** | Container, Tabs, Column Layout, Conditional Visibility, Header |
| **Meta** | Free-form Analysis, Data Freshness, Edit History, Action Log Timeline, Linked Compass Resources, Comments (Perplexity) |

#### Binding d'une table a un Object Type

1. Glisser un widget **Object Table** (Claude, Perplexity).
2. Dans le panneau de config, selectionner un Object Type (ex: "Flight") (Claude) ou creer/selectionner une **variable Object Set** (Perplexity).
3. Optionnellement specifier un filtre Object Set (Claude).
4. Selectionner quelles proprietes apparaissent comme colonnes — toggle, puis **drag to reorder** (Claude, Perplexity). Ou sous Column Configuration, "Add all properties" puis reorganiser en drag (GPT).
5. Configurer largeurs de colonnes, tri par defaut, filtrage par colonne (Claude).
6. Activer la selection de lignes et configurer le comportement au clic (Claude).
7. Configurer la pagination (25/50/100) (Claude).

Workshop ne bind **pas aux datasets directement** dans les widgets operationnels principaux ; il bind aux **object sets et object types** dans l'ontologie (GPT).

#### Filtres

Le widget **Filter List** rend des filtres par type de propriete sous forme d'histogrammes, charts de distribution, pickers et selecteurs type-ahead ; inclut la recherche par mot-cle (GPT).

La configuration du Filter List devient plus riche une fois l'object set peuple car il peut inferer quels types de propriete existent et activer la recherche par mot-cle et le filtrage par presence d'objet lie (GPT).

Des widgets separes existent pour Date and Time Picker, geo filters (draw on map), etc. (GPT, Claude, Perplexity).

Connecter un Filter List a la meme variable Object Set que la Table permet un filtrage automatique (Perplexity).

#### Actions et boutons — Writeback

Les **Actions** Foundry sont des building blocks natifs de l'ontologie pour creer, editer, supprimer et lier des objets (GPT, Claude, Perplexity).

**Definition et gouvernance** : les Actions sont administrees dans l'Ontology Manager ; creer/editer des actions peut necessiter l'appartenance a des groupes administratifs specifiques (ex: `actions-admins`) (GPT).

**Wiring d'un bouton** :
1. Glisser un **Button Group** widget (Claude, Perplexity).
2. Configurer le label (Claude).
3. Selectionner un Action Type de l'ontologie (ex: "Modify Flight Destination") (GPT, Claude, Perplexity).
4. Binder chaque parametre (valeur statique, variable Workshop, ou input de formulaire) (Claude, Perplexity).
5. Configurer le dialogue de confirmation, messages de succes/erreur, et comportement post-action (refresh data, navigate, clear selection) (Claude).
6. Le bouton respecte les permissions au niveau ontologie — les utilisateurs sans permission d'execution voient le bouton desactive ou cache (Claude).

**Inline Action widget** : fournit des interfaces formulaire ou table pour creer/modifier/supprimer des objets ou liens ; configurable dans Workshop ou Ontology Manager (GPT).

Les Button Group widgets peuvent aussi declencher des Workshop events, URLs et exports (GPT).

#### Variables — Systeme nerveux du cross-widget linking

Les **Workshop Variables** sont le mecanisme central de communication inter-widget (Claude, Perplexity). On definit des variables avec noms et types (string, number, object reference, object set, boolean, date) (Claude).

Tout widget peut **ecrire** dans une variable (selection de table, input de filtre, clic de bouton) et tout widget peut **lire** depuis une variable (Claude).

**Pattern canonique** (Claude) : Table A (Customers) configuree pour qu'au clic de ligne, elle ecrive `selectedCustomer` dans une variable. Table B (Orders) a son Object Set filtre par `Orders where customer = {{selectedCustomer}}`. Un Details Panel lit `selectedCustomer` pour afficher toutes les proprietes. Une Map surligne la localisation du client selectionne. Un seul widget filtre peut controler plusieurs tables, charts et maps via des variables partagees.

**Workshop Events** sont le tissu connectif (GPT) : les events peuvent etre declenches par les widgets incluant Button Group et Object Table sur selection de ligne, permettant de wirer "click row in table A" en "set variable that filters widget B". C'est ce qui se rapproche le plus d'un "reactive state management layer" : variables + events (GPT).

Les boutons peuvent aussi declencher un **"Send to AIP Assist"** event qui ouvre la sidebar Assist et soumet un prompt statique ou derive de variable (GPT).

---

### 16. Workshop vs Quiver vs Contour vs Slate

| Dimension | Workshop | Quiver | Contour | Slate |
|---|---|---|---|---|
| **Usage** | Apps operationnelles avec writeback | Dashboards et KPIs | Exploration ad-hoc | Apps custom full HTML/CSS/JS |
| **Writeback** | Oui (Ontology Actions) | Non (read-only) | Non (peut sauver comme nouveau dataset) | Oui (via API / code) |
| **Code requis** | Non | Non | Non | HTML/JS/CSS |
| **Utilisateur cible** | Business ops, managers | Executifs, analystes | Data analystes | Developpeurs |
| **Vitesse de build** | Rapide | Tres rapide | N/A (outil d'exploration) | Lent |
| **Custom UI** | Limite a la bibliotheque de widgets | Limite | N/A | Controle total |
| **Multi-page** | Oui | Non (dashboard unique) | Non (analysis boards) | Oui |
| **Formulaires/Input** | Oui | Non | Non | Oui (code) |
| **Source de donnees** | Ontology objects | Ontology objects + time series (Perplexity) | Raw datasets (tabulaire) (Perplexity) | APIs arbitraires + datasets (Perplexity) |
| **Maintenance** | Faible | Faible | Faible | Elevee (outil plus ancien, plus fragile) (Perplexity) |

**Regles de decision** (les trois sources convergent) :
- **Les utilisateurs doivent agir/changer le monde** (actions, edits) -> **Workshop** (GPT, Claude, Perplexity).
- **Dashboard de monitoring sans writeback** / **Comprendre le monde** -> **Quiver** (GPT, Claude, Perplexity).
- **Exploration ad-hoc** / **Decouvrir le monde** (et "save as dataset") -> **Contour** (GPT, Claude, Perplexity). Recommande quand certaines/toutes les donnees ne sont pas encore mappees dans l'ontologie (GPT).
- **UI pixel-perfect, custom styling/behaviour, librairies JS tierces (D3, Leaflet)** -> **Slate** (GPT, Claude, Perplexity).
- **Choix par defaut pour les nouvelles apps** -> **Workshop** (Claude).

**Specificites Quiver** (Claude) : optimise pour l'analytique — creation de dashboard plus rapide, meilleures fonctions d'aggregation et time-series, capacites de drill-down, et plus de types de charts — mais pas d'actions.

**Specificites Contour** (Claude, GPT) : permet aux analystes de pivoter, filtrer, joindre et agreger interactivement sans vues predefinies, travaillant sur les raw datasets comme sur les objets Ontology.

**Specificites Slate** (GPT, Claude, Perplexity) : precede Workshop et donne un controle HTML/JS/CSS complet avec templating Handlebars-like, mais Palantir oriente activement les nouveaux developpements vers Workshop, qui a rapidement absorbe des capacites qui necessitaient auparavant Slate.

**Quiver dans Workshop** (Perplexity) : les templates Quiver peuvent etre **embarques dans les applications Workshop** pour du contenu analytique au sein de workflows operationnels.

---

### 17. AIP Logic — Fonctions alimentees par LLM

#### Ce que c'est

AIP Logic est un **environnement de developpement no-code** pour construire, tester et releaser des fonctions alimentees par des LLMs, gouverne par la securite plateforme (permissions utilisateur et permissions de fonction) (GPT, Perplexity).

[CONTRADICTION] **Runtime LLM vs code deterministe** : Claude affirme que "the LLM is used at development time to generate code; the deployed function runs deterministically without any LLM." Le process selon Claude : decrire la fonction en langage naturel -> le LLM genere du TypeScript -> tester -> deployer comme Function Foundry standard (deterministe). GPT et Perplexity decrivent AIP Logic comme des fonctions qui UTILISENT des blocs LLM au runtime, avec des blocs "Use LLM" qui ont des templates de prompt et des traces de raisonnement intermediate. Perplexity cite une quote directe : "I explicitly gave it access to this object... you can pick a lot of different objects here." GPT decrit un debugger montrant les "model's intermediate reasoning traces" pour les blocs. Cette contradiction est fondamentale sur l'architecture d'AIP Logic.

#### Layout UI (GPT, Perplexity)

- **Gauche** : Inputs, Blocks, Outputs configuration.
- **Milieu** : Debugger.
- **Droite** : Run panel.

#### Workflow de creation

1. **Acceder** AIP Logic via la navigation workspace ou le raccourci de recherche ; ou creer un nouveau Logic depuis Files via +New > AIP Logic. Les fichiers Logic doivent etre sauves dans un dossier projet (GPT).
2. **Definir les inputs** : strings prompts, ontology objects, object lists, object sets, plus primitives (string, boolean, timestamp, struct, media reference, etc.) (GPT, Perplexity).
3. **Composer des blocks** : Create variable, Apply action, Execute function, Use LLM, plus boucles et conditionnels (GPT). Perplexity ajoute : calculators, object lookups, link traversals, semantic search comme "data tool blocks".
4. **Chainer les blocks** : l'output d'un block alimente le suivant (Perplexity).
5. **Run et debug** : l'execution ouvre le Debugger montrant les traces de raisonnement intermediaires du modele pour les blocks ; le Run panel stocke l'historique des runs et permet de creer des tests (GPT, Perplexity).
6. **Publier** : publier la fonction Logic ; pour les edits ontologiques, il faut publier et l'appeler via une Action, et configurer un outil "Apply actions" dans un block Use LLM (GPT).

**Testing** : apres publication, on peut configurer des **Evaluations** pour tester la logique, comparer des modeles, et examiner la variance entre les runs (GPT).

#### Comment AIP accede a l'Ontologie

AIP Logic recoit des **objets Ontologie types**, pas des donnees brutes (Claude, Perplexity). On accorde explicitement a chaque block LLM l'acces a des object types et proprietes specifiques (Perplexity) :

> "I explicitly gave it access to this object... you can pick a lot of different objects here or narrow it down. This is an explicit access from an LLM to certain ontology... I can give it access to certain properties -- not just from a security standpoint but also from an LLM [hallucination reduction] standpoint. If you give it access to everything you're going to have more hallucinations." (Perplexity)

Le LLM navigue les relations via les link types de l'Ontologie — il sait traverser d'un objet aux objets lies (Perplexity).

Le package `@foundry/ontology-api` auto-genere des interfaces TypeScript depuis le schema Ontologie, ce qui signifie que les actions du LLM sont contraintes aux operations Ontologie valides (Claude).

#### Guardrails et gouvernance (4 couches)

1. **Securite plateforme** : AIP Logic herite du modele de permissions Foundry ; l'acces LLM est scope par ce que les permissions autorisent (GPT, Perplexity).
2. **Restrictions de tooling / acces donnees** : les blocks definissent quels outils le modele peut appeler (fonctions, actions, etc.). Chaque fonction declare explicitement quels Object Types et proprietes le LLM peut voir (GPT, Perplexity). En configurant un agent AIP, on **whitelist** explicitement quelles Functions il peut appeler, quels Object Types il peut lire, et quelles Actions il peut executer (Claude).
3. **Mediation par Actions / Human-in-the-loop** : les edits ontologiques doivent passer par des Actions, qui sont permission-checked et auditables. Pour les actions a haut risque, une approbation humaine peut etre requise avant execution — l'agent propose, l'humain confirme (GPT, Claude, Perplexity).
4. **Audit logging** : chaque action et chaine de raisonnement de l'agent est capturee dans un log immutable (Claude, Perplexity). Les guardrails peuvent encoder des lois et reglementations — restreignant l'acces base sur la sensibilite des donnees (ex: bloquer l'acces aux donnees employees protegees) (Perplexity).

**Observabilite** (GPT) : tracing au niveau workflow, avec une "Trace view" montrant une timeline d'operations incluant si les spans proviennent de Functions, Actions, Automations ou appels LLM.

**Widget AIP Analyst dans Workshop** (GPT) : on peut restreindre ontologie, groupes d'object types, ressources preload, et outils disponibles directement dans la configuration du widget.

#### Modeles supportes

AIP est model-agnostique, supportant **GPT-4/4o, Claude 3.5 Sonnet/Opus, Gemini Pro, Llama 3, Mistral**, et des modeles custom fine-tunes (Claude). Pour les clients gouvernementaux, les modeles tournent entierement on-premises (Claude).

---

### 18. AIP Assist — Experience in-product

AIP Assist est un outil de support plateforme avec une **sidebar in-app**. Il est explicitement context-aware (conscient de l'app Foundry dans laquelle on se trouve) et est concu pour **ne pas acceder aux donnees utilisateur** (GPT).

**Integrations documentees** (GPT) :
- **Dans Workshop** : les widgets Button peuvent declencher un event "Send to AIP Assist" qui ouvre la sidebar Assist et soumet un prompt statique ou derive de variable ; les builders peuvent definir un Agent Assist par defaut pour ce workflow.
- **Dans Ontology Manager** : lors de la mise a jour d'une ontologie, l'onglet Errors inclut "Explain with AIP Assist" sur une erreur, produisant des suggestions de corrections et explications.

---

### 19. OSDK — SDK Ontologie auto-genere

#### Ce que c'est

L'OSDK (Ontology SDK) est le generateur de code schema-driven de Palantir qui produit des **clients types fortement statiques TypeScript ou Python** specifiques a votre Ontologie. Ce n'est pas un wrapper REST generique — il genere des types qui mirrorent exactement vos Object Types, Link Types et Actions (GPT, Claude, Perplexity).

**Langages supportes** : TypeScript (NPM), Python (Pip/Conda), Java (Maven), et **OpenAPI** pour tout autre langage (Perplexity). GPT mentionne TypeScript, Python et Java avec OpenAPI pour les autres.

#### Generation et scope

- Les apps OSDK sont creees et gerees dans **Developer Console** (GPT, Perplexity).
- **Wizard de creation** : choisir "client-facing application", configurer les OAuth redirect URLs, selectionner "Yes, generate an Ontology SDK", selectionner une ontologie, puis choisir quels object types et action types inclure dans le package SDK (GPT).
- Le code genere inclut des classes typees pour chaque Object Type, accesseurs de proprietes, traversees de liens, et invocations d'Actions. Les noms de proprietes et descriptions de l'Ontology Manager apparaissent comme JSDoc/docstrings dans l'IDE (Perplexity).
- Les tokens sont scopes aux entites que l'app est autorisee a acceder, plus les permissions propres de l'utilisateur (GPT).
- Pour d'autres langages, Developer Console peut exporter une **spec OpenAPI** pour les APIs de l'application (GPT).

**CLI de generation** (Claude) :
```bash
npx @osdk/cli generate \
  --foundry-url https://your-stack.palantirfoundry.com \
  --ontology-rid ri.ontology.main.ontology.xxx \
  --output-dir ./src/ontology
```

#### Usage TypeScript typique

**Requete avec filtrage et pagination** (Claude, Perplexity) :
```typescript
import { createClient } from "@osdk/client";
import { MaintenanceTicket } from "./ontology/objects/MaintenanceTicket";

const client = createClient(foundryUrl, ontologyRid, auth);

const tickets = await client(MaintenanceTicket)
  .where({ priority: "HIGH", status: { $ne: "CLOSED" } })
  .orderBy(t => t.createdDate.desc())
  .take(50);

for (const ticket of tickets.data) {
  console.log(ticket.ticketId);     // string - entierement type
  console.log(ticket.priority);      // "HIGH" | "MEDIUM" | "LOW"
}

// Traverser les liens
const asset = await tickets.data[0].$link.asset.get();

// Executer des actions
await client(updateTicketStatus).applyAction({
  ticket: tickets.data[0].$primaryKey,
  newStatus: "IN_PROGRESS",
});
```

**Hooks React** (avec `@osdk/react`) (GPT, Perplexity) :
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

**Filtrage, ordering, pivotTo, streamUpdates** (GPT) : `useOsdkObjects`, filtrage via `where`, ordering via `orderBy`, pivoting vers des objets lies via `pivotTo`, et WebSocket real-time updates via `streamUpdates`.

**Filtrage OR** (Perplexity) :
```typescript
import OSDK from "@slate-internal/sdk";
const result = await ObjType
  .where(query => {
    const conditions = names.map(n => query.name.eq(n));
    return OSDK.Op.or(...conditions);
  })
  .fetchPage();
```

**Java OSDK** (Perplexity) :
```java
List<Restaurant> result = client.ontology()
    .objects()
    .Restaurant()
    .where(RestaurantFilter.restaurantName().isNull(false))
    .fetchStream()
    .toList();
```

#### Authentication

Supportee : **OAuth 2.0 confidential client** (backend), **OAuth 2.0 public client** (browser SPA avec redirect flow), et **bearer token** (developpement) (Claude).

Auth et creation de client documentes dans le repo public `osdk-ts` : creer un OAuth client (public ou confidential), puis `createClient(stackUrl, ontologyRid, auth)` (GPT).

#### Ecosysteme NPM

`@osdk/client`, `@osdk/api`, `@osdk/oauth`, `@osdk/cli`, et optionnellement `@osdk/react` pour les hooks. Le repo open-source est `palantir/osdk-ts` (Claude).

**Platform API bindings** via `foundry-platform-typescript`, installable comme `@osdk/foundry.{namespace}`, utilisable soit aux cotes d'un client ontologie soit standalone (GPT).

#### Bootstrap pour frontends externes

Palantir documente le CLI `@osdk/create-app`, incluant les parametres requis (application RID, foundry URL, client ID, registry URL, etc.) et requirements de version Node (GPT).

**En une phrase** : les requetes OSDK retournent des objets ontologie fortement types dont les champs sont generes depuis les API names des proprietes ontologiques, et les relations peuvent etre traversees dans la couche requete (ex: `pivotTo`) plutot qu'en joignant des tables brutes (GPT).

---

### 20. Apollo — Deploiement, approbations, rollback et air-gap

#### Architecture hub-and-spoke

Architecture officielle (GPT, Claude, Perplexity) :

1. **Apollo Hub** (central, heberge par Palantir comme SaaS) : maintient le statut et les requirements de chaque environnement de deploiement. Contient le moteur d'orchestration et le catalogue. Stocke les settings d'environnement incluant les entites qui doivent exister, les release channels souscrits, et les fenetres de maintenance (GPT, Perplexity).
2. **Remote Apollo Hubs** (Perplexity) : deployes dans les reseaux air-gapped ou isoles. Synchronises avec le Hub principal via des Apollo bundles.
3. **Spoke Environments** / **Apollo Deployment Platform** : executent un Spoke Control Plane et reportent le statut au Hub (GPT). Deploye aux cotes du software gere dans chaque environnement, au-dessus de Kubernetes (Perplexity).
4. **Apollo Agents** : deployes dans le Spoke, executent les Plans emis par le Hub, puis reportent le "Reported State" (GPT). Polllent le control plane pour les changements d'etat desire, telechargent les artifacts des registries, et orchestrent les deploiements Kubernetes (Claude).
5. **Apollo SDK** (Perplexity) : framework pour les developpeurs pour publier les metadata de release. Aucun changement de code requis dans l'application elle-meme.
6. **Apollo Catalog** (Perplexity) : couche metadata bridgeant les artifact stores et les environnements geres. Source de verite pour toutes les versions de software disponibles.

**Modele pull-based** (Claude) : essentiel pour la securite — aucune connexion entrante vers les reseaux clients n'est requise.

#### Moteur d'orchestration constraint-based

Le moteur evalue continuellement les Plans possibles pour chaque Spoke, verifie les contraintes, et emet les Plans dont les contraintes sont satisfaites (GPT, Perplexity). Compare l'etat cible vs l'etat observe a travers tous les environnements (Perplexity). Quand ils different, il calcule un **Apollo Plan** specifiant quoi upgrader, ou et comment (Perplexity).

Les Plans pour roll off un release rappele ou executer des commandes "break-glass" sont **priorises** (GPT).

#### Mecanismes de controle des mises a jour

**Release Channels** : les environnements souscrivent a des canaux (ex: `canary` -> `beta` -> `stable` -> `government-stable`). Les nouvelles versions se deploient d'abord dans les environnements internes Palantir, puis aux clients canary, puis progressivement aux canaux stables (Claude). Les channels peuvent auto-ajouter les nouvelles releases ou etre curates manuellement (GPT). Les features passent de develop -> stable automatiquement apres adjudication (Perplexity).

**Promotion pipelines** (GPT) : definissent comment les releases passent d'un canal a un autre et les criteres a chaque etape, permettant un rollout stable.

**Canary Analysis** (Perplexity) : les nouvelles features sont d'abord deployes dans les environnements canary depuis la branche develop. Apollo monitore les metriques de performance et etats d'erreur apres chaque rollout, promouvant ou rappelant automatiquement les releases (Perplexity).

**Blue/Green Deployment** (Perplexity) : zero-downtime — deploie une seconde instance, deplace lentement le traffic. Fournit un signal de qualite precoce.

**Fenetres de maintenance et suppression** (Perplexity) : au niveau produit ou environnement, bloquent les upgrades pendant les periodes sensibles. Auto-creees quand des seuils de failure sont atteints.

#### Approbation des changements

Apollo a un systeme de **change request** avec statuts : Pending Approvals, Approved, Rejected, Cancelled (GPT). Sauf si un environnement est marque DEV, Apollo requiert au moins un approbateur pour les changements ; des equipes de compliance et des requirements de reviewers speciaux peuvent etre configures pour les domaines regules (GPT).

**Controle client** (Claude) : subscription de release channel, portes d'approbation automatiques vs manuelles, fenetres de maintenance, et vitesse de rollout. Les clients gouvernementaux peuvent etre **plusieurs versions derriere** les environnements commerciaux par design.

#### Deploiements air-gapped et reseaux classifies

**Mecanisme 1 : Apollo Bundles (sneakernet)** (Perplexity) : generes sur le Hub SaaS, contenant uniquement les nouvelles versions nettes de software, configurations et metadata (diffs intelligemment compresses). Graves sur media physique, transportes vers le reseau classifie, et charges dans le Remote Hub. Les metadata AV sont incluses ; les payloads sont scannes et verifies en integrite a plusieurs checkpoints.

**Mecanisme 2 : Binary Transfer Service (BTS)** (GPT, Perplexity) : automatise le transfert de bundles via des **Cross Domain Solutions (CDS)** accreditees. BTS poll le Apollo Catalog pour les nouvelles releases, verifie les resultats de scan securite et checksums cryptographiques, et transfere les artifacts vers le hub distant automatiquement.

[CONTRADICTION] **Sneakernet** : GPT dit que les docs publiques "do not describe sneakernet mechanics in detail" et que c'est credible mais les specifiques operationnels dependent de la posture securite du client. Claude decrit avec confiance des "signed, encrypted deployment bundles" transferes via "government-approved cross-domain solutions or physical media (the sneakernet approach)". Perplexity donne des details precis sur les Apollo Bundles (diffs compresses, media physique, checkpoints de verification).

**Signed, encrypted bundles** (Claude) : contenant container images, Kubernetes manifests et configuration.

**Operation deconnectee** (GPT, Claude) : les environnements peuvent se deconnecter d'un Hub pendant des periodes (ex: vehicules en mouvement) et se reconnecter pour les upgrades plus tard. L'agent opere sans connectivite internet sortante (Claude).

**One-way data flow** (Claude) : pour les niveaux de classification les plus eleves, le flux de donnees est unidirectionnel — les mises a jour entrent, mais un minimum ou aucune telemetrie ne sort.

Le Remote Hub opere alors de maniere autonome, utilisant sa copie locale du catalogue pour orchestrer les upgrades dans le reseau classifie (Perplexity).

**Classifications supportees** (Claude) : jusqu'a TS/SCI.

**Cross-domain delivery** (GPT) : un document partenaire (Everfox) decrit "Palantir Mission Manager" combinant Apollo avec "Palantir Binary Transfer Solution" et cross domain solutions pour le deploiement entre environnements multi-sensibilite ou classifies.

#### Echelle de la flotte

- **300+ environnements** de deploiement a travers on-premise, cloud public et prive (GPT, Claude).
- **"over 3,500 updates across more than 300 independent environments in a single week"** et **"we typically ship software updates multiple times per day"** (Claude, citant le S-1 de Palantir).
- **250+ equipes d'ingenierie** deploient en continu (Perplexity).
- Les microservices individuels sont versions independamment — une "release" est souvent un bump de version d'un seul service, pas une mise a jour monolithique de plateforme (Claude). Apollo effectue la resolution de dependances pour s'assurer que des versions compatibles se deploient ensemble (Claude).

#### Cadence de release

Les equipes de developpement releasent "continuously and independently" et roulent les mises a jour de maniere asynchrone entre les services (GPT). La cadence est **specifique au produit et contrainte par les politiques** plutot que "weekly for everyone" (GPT).

**Vitesse de patch** : 3.5 minutes en moyenne pour patcher un service, moins de 5 minutes pour remedier les problemes de production (Perplexity).

Apollo peut remedier les vulnerabilites en "quelques heures" — la reference est la remediation log4j a travers 200+ environnements (GPT).

#### Mecanismes de rollback

**Rollback declaratif** (Claude) : le control plane remet la version desiree a l'etat precedent connu-bon et les agents reconcilent.

**Declenchement automatique** (Claude) : quand les health checks (Kubernetes probes + endpoints de sante applicatifs custom) echouent.

**Strategies de recall** (Perplexity) :
- **Stay on current version** — pause des nouvelles installations pendant l'investigation.
- **Stay on current with exceptions** — des environnements specifiques recoivent le fix.
- **Any version newer than recalled** — attendre un fix.
- **Roll back to specific known-good version** — forcer le downgrade sur toute la flotte.

Les recalls peuvent etre declenches par les administrateurs, developpeurs, ou **automatiquement par Apollo** quand le monitoring de sante detecte des releases unhealthy (Perplexity).

L'orchestration priorise les Plans pour roll off les releases rappeles (GPT). Les artifacts sont immutables et versionnes, garantissant que les cibles de rollback restent disponibles (Claude).

**Canary analysis** peut stopper les rollouts avant qu'ils atteignent les canaux stables (Claude).

Apollo documente "recalling releases" et "define a roll-off strategy" comme objectifs de premiere classe du getting-started (GPT).

#### Configuration layered et drift detection

**Modele en couches** (Claude) : defaults de base, niveau plateforme, specifique a l'environnement, et overrides specifiques au client — avec detection de drift et remediation.

#### Certifications securite

Apollo est cle pour l'obtention par Palantir des accreditations **FedRAMP, DoD IL5, IL6, et ICD 503** (Perplexity). Il encode les SLAs de vulnerabilite InfoSec, s'integre aux scanners d'images container pour auto-rappeler les produits avec des CVEs connues, et genere des **SBOMs** (Software Bills of Materials) complets depuis son Catalogue (Perplexity).

---

### Recapitulatif des contradictions identifiees

1. **[CONTRADICTION] Types Set et Map** : presents chez Claude, absents chez GPT et Perplexity.
2. **[CONTRADICTION] Outil de migration integre** : Claude dit qu'il n'existe pas ; GPT et Perplexity decrivent un framework OSv2 detaille.
3. **[CONTRADICTION] Mixing visuel et code dans Pipeline Builder** : Claude affirme le support total via Custom Code nodes ; GPT et Perplexity disent que le mixing se fait au niveau dataset boundary.
4. **[CONTRADICTION] AIP Logic runtime** : Claude dit que le LLM genere du code deterministe a la conception ; GPT et Perplexity decrivent des blocs LLM executant au runtime avec traces de raisonnement.
5. **[CONTRADICTION] Sneakernet / deploiement air-gap** : GPT dit que les details ne sont pas publiquement documentes ; Claude et Perplexity donnent des details precis sur les mecanismes.
6. **[CONTRADICTION] Column-level lineage** : Claude decrit le parsing du Catalyst plan Spark et le tracking explicite par noeud Pipeline Builder ; GPT et Perplexity ne decrivent qu'un lineage dataset/transaction.
