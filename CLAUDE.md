# CLAUDE.md — Auditum Memoria (auditum-memoria.com)

Ce fichier consigne les conventions et décisions prises en discussion (claude.ai chat), non déductibles du seul état du repo. À lire avant toute modification.

## Le projet

Site statique HTML/CSS, sans build system, sans JS de framework. Feuille de style partagée : `css/style.css`. Fond bleu marine sombre (`#0a0e27`), typographie système + monospace pour les métadonnées.

Structure logique :
```
website/
├── index.html                  (menu racine — EN uniquement)
├── welcome.html                (EN, canonique/historique)
├── welcome-fr.html / welcome-de.html
├── css/style.css
└── board-whisperer-framework/
    ├── (overview.html — pas encore construit)
    ├── candrian-case/          (structure existante, pas encore construite)
    └── existential-topology/
        ├── index.html          (sous-menu de section — EN uniquement)
        ├── grounds-monetary-immorality.html      (Grounds I — FR, live)
        ├── genealogy-silence-norm.html            (Genealogy I — FR)
        ├── stance-blackmail-deterrence.html        (Stance I — FR)
        ├── mechanics-norm-accusation.html          (Mechanics I — FR)
        ├── stance-shame-dignity.html                (Stance II — FR)
        └── concept-theatre-normatif.html            (Concept — FR, glossaire)
```

## Convention de nommage des langues — RÈGLE CRITIQUE

**Nom de fichier sans suffixe = FR** (sauf `welcome.html` et les menus, qui restent EN pour raisons historiques — voir plus bas).
`-en` = anglais, `-de` = allemand.

**Bug déjà rencontré et corrigé une fois** : les liens du `.lang-switch` dans chaque page doivent pointer vers le nom de fichier **exact** tel que committé sur GitHub. Un décalage (ex: fichier nommé `grounds-en-with-switch.html` alors que le lien attend `grounds-monetary-immorality-en.html`) casse silencieusement le switch (404 → "Something went wrong"). **Toujours vérifier que les trois fichiers FR/EN/DE d'un même texte se référencent mutuellement avec des noms identiques à ceux réellement présents dans le dossier.**

## Menus vs contenu — ce qui se traduit, ce qui ne se traduit pas

- **Menus** (`index.html` racine, `existential-topology/index.html`, tout futur sous-menu de section) → **anglais uniquement, jamais traduits**. Raison : structure encore trop mouvante, traduire à chaque changement serait contre-productif.
- **welcome.html** → reste EN (référence historique). `welcome-fr.html` et `welcome-de.html` existent en parallèle.
- **Textes de contenu** (Grounds, Genealogy, Stance, Mechanics...) → traduits FR/EN/DE via le `.lang-switch` fusionné dans le meta-bar.

## CSS — meta-bar fusionné (v2.1.0)

Le sélecteur de langue ne vit plus dans un bloc séparé au-dessus du meta-bar — il est intégré à l'intérieur, aligné à droite sur la même ligne que catégorie/version/date (`.meta-bar` en `flex`, `justify-content: space-between`, avec `.meta-left` pour le texte et `.lang-switch` pour les liens de langue). Voir `css/style.css` pour le pattern exact ; les pages `grounds-*` et `welcome-*` plus anciennes utilisent encore l'ancien pattern (lang-switch séparé) et devront être migrées.

## Taxonomie des documents — PAS ENCORE STABILISÉE

Le champ `category` affiché dans le meta-bar de chaque page (ex: "Grounds I", "Genealogy I", "Stance I", "Stance II", "Mechanics I", "Concept") n'est pas uniforme à travers le corpus — plusieurs familles de labels coexistent sans nomenclature figée. Ne pas tenter de les uniformiser sans consigne explicite : c'est un choix éditorial encore ouvert, pas un oubli à corriger.

**"Foundations"** (dans l'arborescence Existential Topology) est un nom de **regroupement structurel**, pas un label affiché sur les pages elles-mêmes. Ne pas confondre les deux niveaux.

## Front-matter — deux couches distinctes, portée volontairement limitée

1. **Meta-bar HTML visible** : catégorie, version, date (+ heure — backlog, voir plus bas), rien de plus.
2. **YAML source (Obsidian, futur balisage Schema.org)** : portée volontairement réduite. Champs conservés : `document`, `category`, `knowledge_system`, `family`, `language`, `status`, `version`, `last_updated`, `keywords`, `canonical_slug`. **Explicitement exclus** : `evidentiary_basis`, `related_concepts` (jugés too much, ne pas les réintroduire sans consigne explicite).

## Arborescence Existential Topology (V2)

```
INGÉNIERIE DE LA TOPOLOGIE EXISTENTIELLE (cadre englobant : Théâtre Normatif)
├── 0. GLOSSAIRE
│   ├── Théâtre Normatif : Théâtre normatif · Orthonormation · Police interpersonnelle · Moi symbolique
│   ├── Dignité : ontologique · existentielle · conditionnelle/amortie
│   ├── Capital et Protection : Capital amorti · Amortissement existentiel · Souveraineté existentielle
│   └── Ressentiment : incarné · structurel
├── FONDATIONS (5 textes — TOUS LIVE, voir table ci-dessous)
└── OBSERVATIONS
    └── Humiliation comme filtre d'intégrabilité (draft V1, cas Candrian — pas encore écrit)
```

Table des Fondations (titres réels — les titres de l'arborescence V2 ci-dessus sont des intitulés de travail périmés, ne pas les utiliser comme titres affichés) :

| # | Titre réel | Label | Fichier |
|---|---|---|---|
| 1 | Un critère qu'on juge suspect, et qu'on utilise pourtant pour juger | Grounds I | `grounds-monetary-immorality.html` |
| 2 | Généalogie d'une règle de silence : origine, fonction et transgression inégale | Genealogy I | `genealogy-silence-norm.html` |
| 3 | Chantage ou dissuasion légitime : de la publication comme arme | Stance I | `stance-blackmail-deterrence.html` |
| 4 | De la norme à l'accusation : anatomie d'un déplacement rhétorique | Mechanics I | `mechanics-norm-accusation.html` |
| 5 | L'absence de honte : quand la dignité protège malgré l'atteinte | Stance II | `stance-shame-dignity.html` |

Glossaire : 1 seule entrée écrite à ce stade — *Théâtre normatif* (`concept-theatre-normatif.html`). ~11 autres termes du glossaire restent à écrire.

## Backlog — décisions prises, application reportée (ne pas appliquer sans consigne explicite)

- **Heure dans `last_updated`** : actuellement incohérent (certaines pages l'ont, d'autres non). À uniformiser un jour, pas maintenant.
- **Liens sortants** : politique écrite (V1.0, priorité aux sources académiques/institutionnelles, placement inline). Candidats identifiés : *pre-litigation*, *generative*. Un lien placeholder (`href="#"`) sur "précontentieux"/"pre-litigation" serait bienvenu mais non urgent.
- **Liens internes** : politique écrite (V1.0), 3 cas distincts (sens propriétaire stabilisé / néologisme sans équivalent / candidat futur). Seuls "Public Definition" et "Lab" identifiés comme Cas 1 à ce stade.
- **Unification des documents** : PAS de fusion systématique voulue. Travail ciblé uniquement sur les vrais doublons (V1/V2/V3 d'un même document) ou familles qui se recoupent clairement. Fichiers séparés = norme, plus faciles à maintenir. Éviter toute réécriture longue via IA générative (risque de perte d'info).
- **Linter/générateur AEO×GEO** : fondations empiriques posées (5 tactiques gagnantes : Cite Sources, Statistics, Quotation, Fluency, Authoritative Voice — étude Aggarwal et al. 2024, KDD). 3 questions ouvertes non tranchées : sensibilité au type de document, score global vs rapport qualitatif, cible HTML publié vs markdown source.

## Mode de travail de l'utilisateur

Travaille principalement depuis un smartphone. Préfère accumuler un batch de modifications plutôt que des éditions ponctuelles rapides. Pas de moralisation, pas de conseils non sollicités — formaliser, cartographier, structurer, pas orienter.
