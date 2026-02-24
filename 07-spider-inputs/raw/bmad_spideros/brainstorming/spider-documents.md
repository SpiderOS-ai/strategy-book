# Brainstorming Session: Spider Documents

**Date:** 2026-01-13
**Facilitateur:** Creative Intelligence (BMAD)
**Participant:** Nathan Menard
**Duree:** ~45 minutes
**Priorite:** P1 (sous-module de Spider People)

---

## Objectif

Definir les Jobs-to-be-Done, risques et architecture pour Spider Documents — le sous-module de Spider People qui genere automatiquement des presentations commerciales et notes strategiques a partir des donnees capturees.

## Techniques Utilisees

1. **Jobs-to-be-Done** — Comprendre les vrais besoins par persona
2. **Reverse Brainstorming** — "Comment faire echouer Spider Documents?"
3. **Starbursting** — Explorer toutes les dimensions (Who/What/Where/When/Why/How)

---

# Contexte

## Positionnement

**Ce que Spider Documents N'EST PAS:**
- Un Google Slides / PowerPoint
- Un outil de design generique
- Un generateur de contenu bullshit

**Ce que Spider Documents EST:**
- Un generateur de livrables strategiques (notes, slides) a partir des donnees Spider
- Une capacite transverse qui s'appuie sur Spider People + Spider Content
- Le systeme qui transforme une conversation en livrable de qualite consulting

**Promesse:** "Tu parles. Spider livre."

## Integration dans l'ecosysteme Spider

Spider Documents s'appuie sur:
- **Spider People** → connaissance client, transcriptions, contexte relationnel
- **Spider Content** → generation d'images, design system extrait, brand voice
- **Playbook** → methodologie de l'entreprise, structure des livrables

## Extension future

- **Spider Project** → livrables de gestion de projet (comptes-rendus, rapports d'avancement)
- Autres modules qui ont besoin de generer des documents

---

# Exemple de reference: Note Strategique Drakkar

## Structure type (~15-20 pages)

1. **Ambition & blocages** — contexte macro du client
2. **Forces** — ce qu'il ne faut pas casser
3. **Causes profondes** — analyse "5 Whys" pour chaque symptome
4. **Question centrale** — le dilemme strategique
5. **Ce qui ne change pas** — ancrage
6. **Architecture recommandee** — options + reco
7. **Qui on est** — legitimite
8. **Approche** — methodologie (zones de liberte)
9. **Proposition** — volets de travail
10. **Mise en oeuvre** — comment ca se passerait
11. **Ce qu'on attend** — engagement client
12. **Prochaine etape** — call to action

## Ce qui prend du temps aujourd'hui

- Structurer les infos de la decouverte (transcription → structure)
- Faire les analyses "5 Whys"
- Creer les schemas ASCII (cartographies, arbres de causes, matrices)
- Rediger dans le bon ton (direct, pas bullshit)
- Transformer en slides avec un design pro

## Wahoo moment prospect

> "Putain, ils ont compris mon business en 2h mieux que des consultants en 2 semaines."

---

# Cibles et Personas

| Persona | Description | Priorite |
|---------|-------------|----------|
| **Commercial/Consultant** | Fait des decouvertes, doit produire des livrables (notes, slides) | Principal |
| **Manager commercial** | Veut que son equipe produise des livrables de qualite, uniformes | Secondaire |
| **Dirigeant** | Veut que l'image de la boite soit pro, fier des presentations | Secondaire |

---

# Jobs-to-be-Done

## Commercial/Consultant

| # | JTBD |
|---|------|
| **1** | **Note strategique sans effort** — "Quand je finis une decouverte de 2h et que je dois rediger une note strategique, je veux qu'elle soit generee automatiquement a partir de la transcription, pour passer 10 min a valider au lieu de 3h a rediger." |
| **2** | **Slides pro garanties** — "Quand je dois transformer ma note en presentation client, je veux des slides avec un design pro verrouille, pour que je ne puisse pas faire moche meme si j'essaie." |
| **3** | **Contexte client integre** — "Quand je genere un livrable, je veux qu'il integre tout ce que Spider sait sur ce client (historique, enjeux, profil), pour que ce soit personnalise sans effort." |

## Manager commercial

| # | JTBD |
|---|------|
| **4** | **Qualite uniforme** — "Quand mes commerciaux produisent des livrables, je veux qu'ils respectent tous le meme niveau de qualite et de structure, pour que l'image de la boite soit coherente." |
| **5** | **Playbook applique** — "Quand un commercial genere une note, je veux qu'elle suive notre methodologie (ex: 5 Whys, zones de liberte), pour capitaliser notre savoir-faire." |

## Dirigeant

| # | JTBD |
|---|------|
| **6** | **Effet Wahoo prospect** — "Quand un prospect recoit notre note strategique, je veux qu'il se dise 'putain ils ont compris mon business', pour closer plus facilement." |

## Meta-Job

> **"Je veux produire des livrables de qualite consulting en quelques minutes, pas en quelques heures."**

---

# Reverse Brainstorming

## Question: "Comment faire echouer Spider Documents?"

| # | Comment ca echoue | Insight (l'inverse) | Criticite |
|---|-------------------|---------------------|-----------|
| **1** | **La note generee est generique/bullshit** — On sent que c'est du ChatGPT, pas de profondeur, pas les vrais enjeux du client | La note doit refleter ce qui a ete DIT, pas des generalites. Besoin de la transcription reelle + contexte Spider People | CRITIQUE |
| **2** | **Le ton est corporate/consultant** — "Il conviendrait d'envisager..." au lieu de "Votre probleme c'est X" | Le ton doit etre parametrable par entreprise (brand voice extraite par Spider Content) | CRITIQUE |
| **3** | **Les slides sont moches malgre le template** — Mauvais placements, texte qui deborde, images pixelisees | Le template doit etre "fool-proof", contraintes fortes sur le contenu | SERIEUX |
| **4** | **Le playbook n'est pas suivi** — La note ne fait pas les "5 Whys", ne suit pas la structure methodologique | Spider doit connaitre le playbook et l'appliquer systematiquement | SERIEUX |
| **5** | **Trop de validation manuelle** — Le commercial passe 1h a corriger des erreurs, autant le faire soi-meme | Le contenu genere doit etre >80% bon du premier coup | SERIEUX |
| **6** | **Pas de lien avec le contexte client** — La note ne mentionne pas l'historique, les enjeux deja connus | Integration profonde avec Spider People obligatoire | MOYEN |
| **7** | **Export foireux** — PDF mal formate, PowerPoint qui pete sur Mac vs Windows | Qualite technique de l'export irreprochable | MOYEN |
| **8** | **Le design system n'est pas respecte** — Couleurs approximatives, logo mal place | Extraction design system par Spider Content doit etre precise | MOYEN |

## Les 3 risques projet-killer

1. **Contenu generique/bullshit** — Si la note ne reflete pas la vraie conversation, perte de credibilite totale
2. **Ton inadapte** — Si ca sonne "IA corporate", le prospect le sent immediatement
3. **Template pas fool-proof** — Si le commercial peut quand meme faire moche, on a echoue

---

# Starbursting (Who/What/Where/When/Why/How)

## WHO — Qui?

| Question | Reponse |
|----------|---------|
| Qui utilise Spider Documents? | Operationnels: commerciaux, consultants, dirigeant (s'il fait des propales) |
| Qui recoit les livrables? | Prospects, clients |
| Qui definit les templates/playbook? | Admin, accompagne par Drakkar partenaire |
| Qui valide avant envoi? | Commercial lui-meme (P0), logique manager possible en P1 |

## WHAT — Quoi?

| Question | Reponse |
|----------|---------|
| Quels livrables en P0? | Note strategique + Slides + Proposition commerciale |
| Qu'est-ce qu'on utilise comme input? | Transcriptions (Noota/Aircall), profil contact Spider People, contexte entreprise, playbook |
| Format d'export? | Web uniquement (liens partageables comme slides.drakkar.io) |
| Qu'est-ce que le playbook? | Process commercial complet: etapes, cibles, offres (a creuser dans Spider People) |

## WHERE — Ou?

| Question | Reponse |
|----------|---------|
| Acces principal? | Vue pipeline (on voit les deals, on genere depuis la) |
| Module separe? | Oui, pour voir tous les livrables envoyes + tracker les vues |
| Ou le prospect consulte? | Lien web, tout est traque (ouvertures, temps passe par section) |

## WHEN — Quand?

| Question | Reponse |
|----------|---------|
| Temps de generation? | Background + notif quand pret (on s'en fout du temps exact) |
| Metrique cle? | Nombre d'allers-retours (le moins possible) |
| Temps de validation objectif? | ~10 min (vs 1h+ aujourd'hui) |
| Delai envoi apres decouverte? | ~1 semaine (aujourd'hui), mais si Spider permet 24-48h = avantage competitif |
| Apprentissage? | Spider apprend de chaque note ce que le commercial aime/n'aime pas |

## WHY — Pourquoi?

| Question | Reponse |
|----------|---------|
| Pourquoi Spider Documents? | Automatisation + integration donnees Spider + design garanti |
| Pourquoi les commerciaux utiliseraient? | Gain de temps enorme (3h → 10 min), qualite garantie |
| Pourquoi un dirigeant paierait? | ROI = plus de deals closes (effet wahoo), image coherente |

## HOW — Comment?

| Question | Reponse |
|----------|---------|
| Comment garantir qualite (pas bullshit)? | Meme logique que Builder (BMAD, comprendre contexte) + Playbook + coaching commercial (bonnes questions = bonne data) + feedback loop |
| Comment editer? | Interface visuelle drag & drop + espace de prompt pour modifier ("refais cette section") |
| Design system? | Sous-module Spider Content utilise partout dans Spider OS |
| Templates? | Definis par entreprise, potentiellement ameliores avec designers |
| Vue admin? | Voir/gerer tout le design system visuellement |

---

# SCAMPER

## S - Substitute (Substituer)

| Substituer | Par | Decision |
|------------|-----|----------|
| Template fixe | Template evolutif (sections qui se rajoutent, socle commun visible) | OUI - a faire |

## C - Combine (Combiner)

| Combiner | Avec | Decision |
|----------|------|----------|
| Note + Slides | Generation ensemble | OUI - prevu |
| Pre-brief + Note finale | Questions playbook → livrable | OUI - prevu |

## A - Adapt (Adapter)

| Adapter pour | Decision |
|--------------|----------|
| Compte-rendu de projet (Spider Project) | OUI - futur |
| Audit technique | OUI - futur, bonne idee |
| Executive summary (1 page auto) | OUI - pas P0 |
| Templates par type de livrable (user definit) | OUI - a faire |

## M - Modify/Magnify (Amplifier)

| Amplifier | Decision |
|-----------|----------|
| Tracking (temps par section, retours en arriere, lu vs survole) | OUI - a faire |
| Hyper-personnalisation (infos perso du contact) | NON - trop touchy |
| Generation temps reel (draft evolue pendant decouverte) | OUI - pas P0, mais canon |

## P - Put to other uses (Autres usages)

| Reutiliser pour | Decision |
|-----------------|----------|
| Base de formation (meilleures notes = cas d'ecole) | OUI - futur (Spider Training) |
| Benchmark (notes qui closent vs pas) | OUI - futur (Spider Data) |
| Offre partenaire (vendre creation templates) | NON - pas convaincu |

## E - Eliminate (Eliminer)

| Eliminer | Decision |
|----------|----------|
| Export fichier (tout en web) | OUI - deja prevu |
| Edition libre (design freestyle) | OUI - mais modification texte possible |
| Validation manager | OUI pour P0 - reviendra en P1 |

## R - Reverse (Inverser)

| Inverser | Decision |
|----------|----------|
| Client genere son brief | NON - trop B2C |
| Slides d'abord, note ensuite | NON - on s'en fout, les deux arrivent ensemble |
| Feedback prospect integre (commentaires sur la note) | OUI - bonne idee |

---

# Key Insights

## Insight 1: Spider Documents est une capacite transverse

**Finding:** Documents s'appuie sur People (data), Content (design), Playbook (structure). Demain ca s'etend a Project, Training, etc.

**Implication:** L'architecture doit etre modulaire des le depart. Le moteur de generation de documents est reutilisable.

**Priorite:** Critique

---

## Insight 2: Le playbook est le chainon manquant

**Finding:** Le playbook (process commercial, etapes, questions) n'est pas assez defini dans Spider People. Or c'est lui qui structure les livrables.

**Implication:** Impossible de faire de bons Documents sans bon Playbook. A creuser dans People.

**Priorite:** Critique

---

## Insight 3: L'edition doit etre contrainte mais flexible

**Finding:** Pas de freestyle design (sinon moche), mais le commercial doit pouvoir modifier le texte et donner du feedback par section.

**Implication:** UX d'edition specifique: drag & drop + prompt + modification texte, mais pas de changement de design.

**Priorite:** Haute

---

## Insight 4: Le tracking est un differenciateur

**Finding:** Pas juste les vues, mais temps par section, retours en arriere, ce qui est lu vs survole.

**Implication:** Ca donne des insights au commercial ("il a passe 10 min sur pricing, 0 sur notre approche"). Ca alimente aussi le benchmark futur.

**Priorite:** Haute

---

## Insight 5: Le feedback prospect boucle la boucle

**Finding:** Si le prospect peut commenter sur la note, ca alimente Spider People (nouvelles infos, objections, questions).

**Implication:** Le livrable devient un outil de collecte de data, pas juste un output.

**Priorite:** Moyenne (pas P0)

---

## Insight 6: Web only = tracking garanti

**Finding:** Pas d'export PDF/PPT. Tout en liens web.

**Implication:** On force la consultation trackee. Pas de "je te l'envoie en PDF" qui echappe au tracking.

**Priorite:** Haute

---

# Statistics

| Metrique | Valeur |
|----------|--------|
| JTBD definis | 6 |
| Anti-patterns (reverse brainstorm) | 8 |
| Risques projet-killer | 3 |
| Key insights | 6 |
| Techniques appliquees | 3 |

---

# Progression Brainstorming

| Session | Status | Date |
|---------|--------|------|
| 1 - JTBD + Reverse | Done | 2026-01-13 |
| 2 - Starbursting | Done | 2026-01-13 |
| 3 - SCAMPER | Done | 2026-01-13 |

---

# Next Steps

1. **Creuser le Playbook dans Spider People** — Concept central pas assez defini
2. **PRD Spider Documents** — `/prd` pour specs detaillees
3. **Integration avec Spider Content** — Design system, brand voice
4. **Maquettes UX** — Interface d'edition (drag & drop + prompt)

---

*Generated by BMAD Method v6 - Creative Intelligence*
*Session duration: ~45 minutes*
