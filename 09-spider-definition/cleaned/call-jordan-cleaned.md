# CALL JORDAN — Transcript nettoye et restructure

> **Date :** 20 fevrier 2026
> **Participants :** Nathan Menard, Jordan Lefranc
> **Duree :** ~60 minutes
> **Source :** Transcription automatique (interpretee, pas mot a mot)
> **Contexte :** Deuxieme call strategie Spider. Jordan est le premier prospect/beta-testeur.

---

## 1. CONTEXTE BUSINESS JORDAN (actualise)

- **Pipe :** 300K€ en cours. Semaine a 115K€ validees (bonne semaine).
- **Equipe :** ~4-5 personnes (Jordan + Eileen + freelances).
- **Clients recents :** Ambassade d'Argentine, centres commerciaux multi-sites.
- **Douleur du moment :** "Les dispos changent. Je refais les plans medias que j'avais deja faits. Je recalcule tout a la mano."
- **Outil metier :** UAG Affichage — base de donnees des 360 000 faces publicitaires de France, 16 000 reseaux. Licence ~55€/mois. Verrouillage par code mensuel.

---

## 2. LE DIAGNOSTIC DE NATHAN (verbatim structure)

### Le probleme de fond
"Notion c'est un peu ton ERP. Tout ce qui est point d'entree, sortie de ce systeme, il est douloureux. Tu arrives a un stade ou Notion n'est pas adapte pour ce que tu veux faire."

### Les 3 options classiques — et pourquoi elles echouent toutes

| Option | Avantage | Inconvenient | Cout estime |
|--------|----------|-------------|-------------|
| **ERP (Odoo)** | Modules cles en main | Pas flexible, grosse montee en competence | Variable, 10K+ implementation |
| **Dev sur-mesure** | Exactement ce qu'on veut | "Un ticket de 50K€ minimum" | 50-100K€ |
| **No-code (Bubble)** | Reduit le cout | Plafond de verre comme Notion | 15-20K€ |

### La 4eme voie : Spider
"On code 10 a 20 fois plus vite qu'avant. On a cree une infrastructure autour de ca. Tu as le meilleur de tous les mondes."

---

## 3. LA PROPOSITION COMMERCIALE

### Ce que Nathan propose
- **0€ de dev** — Nathan le fait lui-meme. Jordan est beta-testeur / etude de cas.
- **Abonnement Spider** — "On a presque aucun truc a moins de 500 balles par mois. Rien qu'en credits IA, ca consomme."
- **Next step :** Prototype montre le **vendredi 27 fevrier** a 11h.

### Reaction Jordan
"C'est clair. Meme si on est amis, tu bosses, ca te prend du temps. On le voit quoi." → Pret a payer au-dessus de l'abonnement minimum.

---

## 4. LES MODULES SPIDER IDENTIFIES POUR JORDAN

### Module 1 : Pipeline UAG → Plan media automatique
- Remplacement de la triple saisie UAG → Google Sheets → Notion → mails
- Fusion du plan media et du Notion en un seul systeme
- Connexion a Pennylane pour la facturation

### Module 2 : Relances automatiques
Nathan fait le parallele avec les impayes : "Un suivi de temps et au bout d'un moment, il faut juste relancer en automatique."
- Relances plans medias (dispos qui changent)
- Relances impayes
- Brouillons de relance mail valides par Jordan

### Module 3 : Construction plan de com semi-automatique
A terme : "Le client parle, paf ca fait la reco automatique et tu as tout presque en temps reel."

---

## 5. LA VISION STRATEGIQUE POUR JORDAN (la plus importante)

### Le modele Service-as-Software explique a Jordan
"On passait du Software as a Service, maintenant c'est Service as a Software. Tu vends du conseil, donc tu vends le resultat. Il se trouve que toi tu as un outil dingue qui automatise tous les trucs de bout en bout."

### La strategie en 2 temps
1. **Court terme :** Automatiser la chaine interne de Jordan → passer de 1M a 2-3M CA en cassant les verrous operationnels.
2. **Long terme :** Retourner le modele → Jordan vend l'OUTIL aux autres agences / franchiseurs. "En fait tu donnes acces a l'outil et tu fais un volume qu'ils n'auraient jamais fait."

### L'analogie Alan
"Quand j'ai capte que moi en tant qu'employeur j'avais juste a ajouter le mail de mon collab et c'etait termine... j'ai pete mon crane. C'est le meme produit, c'est juste la maniere dont tu le consommes."

---

## 6. LE MARCHE DE L'AFFICHAGE PUBLICITAIRE — INSIGHTS CRITIQUES

### Structure du marche
- **UAG :** Monopole de niche. ~20 clients. 55€/mois. Verrouillage par codes. "C'est un monde de mafieux."
- **Regies publicitaires :** JCDecaux, Cadres Blancs, Affiouest, etc. Elles controlent les reseaux.
- **Agences media :** Facturent "des dizaines, centaines de milliers d'euros d'honoraires avec des marges arrieres."
- **Historique disruption :** Tous ceux qui ont essaye de disrupter les regies ont echoue (AddinType, startup belge ~2M leves → echec).

### Pourquoi les tentatives precedentes ont echoue
- AddinType : 1.7M CA, ambitions 100M, s'est fait "sauter par deux coups" car mettait JCDecaux en avant. N'est plus qu'un revendeur de leads.
- Startup belge : 1.5-2M leves, un an d'essai, echec face aux regies.
- Pattern : les regies ecrasent quiconque les menace directement.

### L'angle Spider pour Jordan
"Tu peux arranger les regies, tu n'arranges plus les agences de medias." → L'outil Spider rendrait Jordan ALLIE des regies contre les grosses agences, pas l'inverse.

### Donnees cles du processus Jordan
- 60+ interlocuteurs reguliers
- 10-12 regies en mensuel
- 20 formats d'affichage differents
- Adresses de livraison, quantites, cahiers des charges, tarifs → tout est custom
- 44-45 points de data identifies par Jordan (= requirements fonctionnels Spider)

---

## 7. LE LIEN KAVALIN — POTENTIEL CROISE

- **Kavalin :** Reseau de 185 cabinets.
- Nathan travaille a entrer chez Kavalin via une agence 360 qui les accompagne.
- Kavalin = "plein d'outils partout, il faut les connecter. Ils ont cree une data lake mais que faire avec ?"
- Si Kavalin signe avec Spider, croisement naturel avec Jordan pour l'affichage des 185 cabinets.
- Jordan : "Si c'est un truc comme ca, on va partager le gateau. Carrément."

---

## 8. L'UAG — ANALYSE TECHNIQUE

### Ce que fait l'UAG
- Base de donnees : 360 000 faces publicitaires en France, 16 000 reseaux
- Filtrage : par ville, concessionnaire (JCDecaux, Cities...), format (mobilier urbain, grand format, local)
- Export : fichier sur PC (pas de cloud), cartes pour clients
- Base externe : SQLite ou similaire, stockee en local

### Limites de l'UAG
- Installation manuelle (TeamViewer par le fournisseur)
- Codes de reactivation periodiques
- Pas d'API
- Pas de cloud
- Pas de collaboration
- Export uniquement fichier local ou lien web temporaire

### Opportunite strategique
Nathan identifie que l'UAG est un monopole attaquable : "Ces logiciels en situation de monopole dans des niches que personne attaque. Tu peux disrupter ce truc."

---

## 9. NEXT STEPS CONVENUS

| Action | Responsable | Deadline |
|--------|-------------|----------|
| Envoyer les 44-45 points de data finalises | Jordan | Lundi-mardi 25-26 fev |
| Envoyer un export UAG (vue globale Nantes) | Jordan | Fait pendant le call |
| Construire un prototype Spider | Nathan | Week-end 22-23 fev |
| Call de demo prototype | Nathan + Jordan | **Vendredi 27 fevrier, 11h** |
| Estimer l'abonnement mensuel | Nathan | Pour le call du 27 |
| Week-end a Pornichet (perso) | Tous | 4-5 avril |

---

*Transcript nettoye le 21 fevrier 2026. Source : transcription automatique du call 2 Nathan-Jordan.*
