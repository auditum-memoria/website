# CLAUDE.md — Auditum Memoria (auditum-memoria.com)

Ce fichier consigne les conventions et décisions prises en discussion (claude.ai chat), non déductibles du seul état du repo. À lire avant toute modification.

## Le projet

Site statique HTML/CSS, sans build system, sans JS de framework. Feuille de style partagée : `css/style.css`. Fond bleu marine sombre (`#0a0e27`), typographie système + monospace pour les métadonnées.

Structure logique :
```
website/
├── index.html (menu racine — EN uniquement)
├── welcome.html (EN, canonique/historique)
├── welcome-fr.html / welcome-de.html
├── css/style.css
├── board-whisperer-framework/
│   ├── (overview.html — pas encore construit)
│   └── candrian-case/ (structure existante, pas encore construite)
└── existential-topology/
    ├── index.html (sous-menu de section — EN uniquement, pas encore construit)
    ├── grounds-monetary-immorality.html (Grounds I — EN, live)
    ├── grounds-monetary-immorality-fr.html / -de.html
    ├── genealogy-silence-norm.html (Genealogy I — EN, live)
    ├── genealogy-silence-norm-fr.html / -de.html
    ├── stance-blackmail-deterrence.html (Stance I — EN, live)
    ├── stance-blackmail-deterrence-fr.html / -de.html
    ├── mechanics-norm-accusation.html (Mechanics I — EN, live)
    ├── mechanics-norm-accusation-fr.html / -de.html
    ├── stance-shame-dignity.html (Stance II — EN, live)
    ├── stance-shame-dignity-fr.html / -de.html
    └── concept-theatre-normatif.html (Concept — FR, glossaire, pas encore écrit)
```

**Existential Topology n'est pas un sous-ensemble de Board Whisperer Framework.** Rattachement reconsidéré le 8 juillet 2026 : c'est une branche indépendante du Laboratoire (Auditum Memoria), au même rang que Board Whisperer Framework — d'où son emplacement à la racine du repo (`existential-topology/`) et non sous `board-whisperer-framework/`. Raisons : le corpus est né après le Framework, se déclare lui-même autonome dans son document fondateur (SMET), et pèse aujourd'hui presque autant que le Framework en volume.

## Convention de nommage des langues — RÈGLE CRITIQUE

**Nom de fichier sans suffixe = EN** — langue de référence. L'anglais a été retenu plutôt que l'allemand ou le français car c'est la langue qui touche le plus de monde hors de Suisse, y compris les personnes marginalisées visées par le corpus. `-fr` = français (traduction — le FR n'est pas la langue de référence même s'il s'agit de la langue maternelle de l'auteur, et même quand le texte a été rédigé en FR puis traduit vers l'EN). `-de` = allemand (traduction).

**Erreur corrigée le 8 juillet 2026** : une version antérieure de ce document indiquait par erreur "nom nu = FR". C'était faux et a produit une vraie confusion sur les fichiers `grounds-*` (contenu EN publié sous un nom de fichier nu, FR égaré sous un nom bâtard `grounds-fr-with-switch.html`). Règle définitive : **nom nu = EN, toujours.**

**Bug déjà rencontré (deux fois)** : les liens du `.lang-switch` dans chaque page doivent pointer vers le nom de fichier **exact** tel que committé sur GitHub. Un décalage casse silencieusement le switch (404 → "Something went wrong"). **Toujours vérifier que les trois fichiers EN/FR/DE d'un même texte se référencent mutuellement avec des noms identiques à ceux réellement présents dans le dossier avant de committer.**

## Menus vs contenu — ce qui se traduit, ce qui ne se traduit pas

- **Menus** (`index.html` racine, `existential-topology/index.html`, tout futur sous-menu de section) → **anglais uniquement, jamais traduits**. Raison : structure encore trop mouvante, traduire à chaque changement serait contre-productif.
- **welcome.html** → référence EN. `welcome-fr.html` et `welcome-de.html` existent en parallèle (traductions).
- **Textes de contenu** (Grounds, Genealogy, Stance, Mechanics...) → EN comme référence, traduits FR/DE via le `.lang-switch` fusionné dans le meta-bar.

## CSS — meta-bar fusionné (v2.1.0)

Le sélecteur de langue ne vit plus dans un bloc séparé au-dessus du meta-bar — il est intégré à l'intérieur, aligné à droite sur la même ligne que catégorie/version/date (`.meta-bar` en `flex`, `justify-content: space-between`, avec `.meta-left` pour le texte et `.lang-switch` pour les liens de langue). Voir `css/style.css` pour le pattern exact. Toutes les pages `grounds-*`, `genealogy-*`, `stance-*`, `mechanics-*` et `welcome-*` utilisent désormais ce pattern (migration terminée le 8 juillet 2026).

## Taxonomie des documents — PAS ENCORE STABILISÉE

Le champ `category` affiché dans le meta-bar de chaque page (ex: "Grounds I", "Genealogy I", "Stance I", "Stance II", "Mechanics I", "Concept") n'est pas uniforme à travers le corpus — plusieurs familles de labels coexistent sans nomenclature figée. Ne pas tenter de les uniformiser sans consigne explicite : c'est un choix éditorial encore ouvert, pas un oubli à corriger.

**"Foundations"** (dans l'arborescence Existential Topology) est un nom de **regroupement structurel**, pas un label affiché sur les pages elles-mêmes. Ne pas confondre les deux niveaux.

## Front-matter — deux couches distinctes, portée volontairement limitée

1. **Meta-bar HTML visible** : catégorie, version, date (+ heure), rien de plus.
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

Table des Fondations (titres réels — les titres de l'arborescence V2 ci-dessus sont des intitulés de travail périmés, ne pas les utiliser comme titres affichés). Le fichier listé est le nom **sans suffixe**, c'est-à-dire la version **EN** (référence) ; `-fr.html` et `-de.html` existent en parallèle pour chaque ligne :

| # | Titre réel (source FR) | Label | Fichier (EN, référence) |
|---|---|---|---|
| 1 | Un critère qu'on juge suspect, et qu'on utilise pourtant pour juger | Grounds I | `grounds-monetary-immorality.html` |
| 2 | Généalogie d'une règle de silence : origine, fonction et transgression inégale | Genealogy I | `genealogy-silence-norm.html` |
| 3 | Chantage ou dissuasion légitime : de la publication comme arme | Stance I | `stance-blackmail-deterrence.html` |
| 4 | De la norme à l'accusation : anatomie d'un déplacement rhétorique | Mechanics I | `mechanics-norm-accusation.html` |
| 5 | L'absence de honte : quand la dignité protège malgré l'atteinte | Stance II | `stance-shame-dignity.html` |

Glossaire : 1 seule entrée écrite à ce stade — *Théâtre normatif* (`concept-theatre-normatif.html`, pas encore créé). ~11 autres termes du glossaire restent à écrire.

## Liens internes et externes

Tous les liens `class="link-internal"` et `class="link-external"` du corpus Fondations pointent actuellement vers `href="#"` (placeholder) — aucune URL réelle n'a encore été assignée, y compris pour les liens externes vers des sources académiques (Bourdieu, Billig, McGuire...). Ne pas inventer d'URL : demander à l'auteur avant d'en ajouter une réelle. Seul le texte visible du lien se traduit d'une langue à l'autre, jamais la cible.

## Backlog — décisions prises, application reportée (ne pas appliquer sans consigne explicite)

- **Liens sortants** : politique écrite (V1.0, priorité aux sources académiques/institutionnelles, placement inline). Candidats identifiés : *pre-litigation*, *generative*. Un lien placeholder (`href="#"`) sur "précontentieux"/"pre-litigation" serait bienvenu mais non urgent — ne pas l'ajouter sans consigne explicite.
- **Unification des documents** : PAS de fusion systématique voulue. Travail ciblé uniquement sur les vrais doublons (V1/V2/V3 d'un même document) ou familles qui se recoupent clairement. Fichiers séparés = norme, plus faciles à maintenir. Éviter toute réécriture longue via IA générative (risque de perte d'info).
- **Linter/générateur AEO×GEO** : fondations empiriques posées (5 tactiques gagnantes : Cite Sources, Statistics, Quotation, Fluency, Authoritative Voice — étude Aggarwal et al. 2024, KDD). 3 questions ouvertes non tranchées : sensibilité au type de document, score global vs rapport qualitatif, cible HTML publié vs markdown source.

## Convention de commit

Chaque commit doit avoir :
- un titre précis, pas générique (pas "fix bug" ou "update files" —
  dire quoi exactement a changé)
- un corps de message qui reprend le "pourquoi" donné dans l'instruction,
  pas seulement le "quoi" — si l'instruction contient une "Raison :",
  elle doit apparaître dans le message de commit, pas seulement guider
  le code
- ce "pourquoi" doit être explicité même quand l'instruction ne contient
  pas de "Raison :" formelle — le titre et le corps doivent rester
  compréhensibles dans 3 mois en ne relisant que l'historique git, sans
  avoir à reconstruire le contexte de mémoire
- si plusieurs corrections indépendantes sont faites dans le même commit,
  chacune est listée séparément dans le corps du message, pas fusionnée
  en une phrase vague

## Heure dans last_updated

Chaque fois qu'une page est créée ou modifiée, le champ "Updated" du
meta-bar doit inclure l'heure (format "July 10, 2026, 14:32"), pas
seulement la date. L'heure à utiliser est celle du moment de la
création/modification du fichier, pas une tentative de deviner l'heure
exacte du merge — approximatif mais présent vaut mieux qu'absent.

## Mode de travail de l'utilisateur

Travaille principalement depuis un smartphone. Préfère accumuler un batch de modifications plutôt que des éditions ponctuelles rapides. Pas de moralisation, pas de conseils non sollicités — formaliser, cartographier, structurer, pas orienter.
