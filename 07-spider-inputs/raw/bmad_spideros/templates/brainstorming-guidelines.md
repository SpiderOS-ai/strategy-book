# Guidelines Brainstorming SpiderOS

## Methodologie BMAD adaptee pour SpiderOS

Ce document definit comment mener les sessions de brainstorming pour chaque module SpiderOS.

---

## Principe fondamental : "Diverge Then Converge"

1. **Diverge** : Generer beaucoup d'idees avec plusieurs techniques
2. **Converge** : Affiner, prioriser, extraire les insights

On fait **plusieurs sessions** par module pour une exploration complete.

---

## Sessions de brainstorming (ordre recommande)

| Session | Techniques | Objectif | Duree |
|---------|------------|----------|-------|
| **1** | Jobs-to-be-Done + Reverse Brainstorming | Comprendre les vrais besoins et identifier les risques | 30-45 min |
| **2** | Starbursting (Who/What/Where/When/Why/How) | Explorer toutes les dimensions du module | 20-30 min |
| **3** | Six Thinking Hats | Analyser sous 6 angles (faits, emotions, risques, benefices, creativite, process) | 30-40 min |
| **4** | SCAMPER | Generer des variations creatives | 20-30 min |
| **5** | SWOT (optionnel) | Positionnement concurrentiel si pertinent | 15-20 min |

**Note :** On peut faire plus ou moins de sessions selon le module. L'objectif est d'avoir une vision complete avant de passer au PRD.

---

## Techniques disponibles (reference BMAD)

### Pour explorer les problemes

| Technique | Description | Quand l'utiliser |
|-----------|-------------|------------------|
| **5 Whys** | Poser "Pourquoi ?" 5 fois | Cause racine d'un probleme |
| **Starbursting** | Questions Who/What/Where/When/Why/How | Nouveau module, exploration large |
| **Six Thinking Hats** | 6 perspectives differentes | Decision complexe |

### Pour generer des solutions

| Technique | Description | Quand l'utiliser |
|-----------|-------------|------------------|
| **SCAMPER** | Substitute/Combine/Adapt/Modify/Put to other uses/Eliminate/Reverse | Ameliorer un concept existant |
| **Mind Mapping** | Arbre hierarchique d'idees | Organiser beaucoup d'idees |
| **Brainwriting** | Generation silencieuse en rounds | Eviter le biais de groupe |

### Pour analyser les risques

| Technique | Description | Quand l'utiliser |
|-----------|-------------|------------------|
| **Reverse Brainstorming** | "Comment faire echouer ?" | Identifier les pieges |
| **SWOT** | Forces/Faiblesses/Opportunites/Menaces | Positionnement concurrentiel |

### Pour comprendre les utilisateurs

| Technique | Description | Quand l'utiliser |
|-----------|-------------|------------------|
| **Jobs-to-be-Done** | "Quand je..., je veux..., pour que..." | Comprendre les vrais besoins |
| **Empathy Mapping** | Ce que l'utilisateur dit/pense/fait/ressent | Personas profonds |

---

## Combinaisons obligatoires pour SpiderOS

Chaque module SpiderOS doit avoir au minimum :

1. **Jobs-to-be-Done** — OBLIGATOIRE (comprendre les vrais besoins)
2. **Reverse Brainstorming** — OBLIGATOIRE (identifier les risques)
3. **Une technique d'exploration** — Au choix (Starbursting, Six Thinking Hats, etc.)

---

## Structure des fichiers

### Pendant les sessions

Chaque session est sauvegardee incrementalement dans :
```
docs/brainstorming/spider-[module].md
```

Le fichier est mis a jour apres chaque session avec les nouvelles sections.

### Tracking de progression

Pour chaque module, on track ou on en est :

```markdown
## Progression Brainstorming

| Session | Status | Date |
|---------|--------|------|
| 1 - JTBD + Reverse | Done | YYYY-MM-DD |
| 2 - Starbursting | Done | YYYY-MM-DD |
| 3 - Six Hats | In Progress | - |
| 4 - SCAMPER | Not Started | - |
| 5 - SWOT | Not Started | - |
```

---

## Comment relancer une session

Quand on revient sur un module en cours de brainstorming :

1. Lire le fichier `docs/brainstorming/spider-[module].md`
2. Regarder la section "Progression Brainstorming"
3. Reprendre a la prochaine session non completee
4. Continuer a enrichir le meme fichier

---

## Quand le brainstorming est termine

Un brainstorming de module est considere **complet** quand :

- [ ] Jobs-to-be-Done definis (minimum 4)
- [ ] Reverse Brainstorming fait (minimum 6 anti-patterns)
- [ ] Au moins une technique d'exploration supplementaire
- [ ] Hypotheses Leap of Faith definies
- [ ] Key Insights extraits (minimum 3)
- [ ] Integrations SpiderOS identifiees
- [ ] Next Steps clairs

Ensuite on peut passer au **PRD** (`/prd`).

---

## Modules SpiderOS a brainstormer

| Module | Status | Fichier |
|--------|--------|---------|
| Spider Builder | Done | `docs/brainstorming/spider-builder.md` |
| Spider Content | Done | `docs/brainstorming/spider-content.md` |
| Spider People | Done | `docs/brainstorming/spider-people.md` |
| Spider Memory | Not Started | - |
| Spider Chatbot | Not Started | - |
| Spider Documents | Not Started | - |
| Spider Vector | Not Started | - |

---

## Commande pour lancer

```
/brainstorm
```

Puis preciser le module et ou on en est.

---

*Guidelines BMAD pour SpiderOS - Creative Intelligence*
*Derniere mise a jour : 2026-01-13*
