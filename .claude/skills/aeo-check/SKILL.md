---
name: aeo-check
description: Vérifie qu'une page HTML publiée sur Auditum Memoria respecte le pattern SEO/AEO du site (auditum-memoria.com). À invoquer sur toute page nouvellement écrite, migrée depuis l'ancien site Obsidian Publish, ou modifiée en profondeur, avant commit.
---

# AEO Check — Auditum Memoria

Vérifie la page fournie contre la checklist ci-dessous. Rapport qualitatif par point (pas de score global) — dire précisément ce qui est présent, absent, ou non applicable et pourquoi, plutôt qu'un chiffre. Voir `CLAUDE.md` à la racine pour les conventions du projet avant d'appliquer.

## Checklist (dérivée de SEO_AEO_Page_Pattern.md + GEO-16 + Aggarwal et al. 2024)

- [ ] Le titre répond à une requête de recherche plausible, pas juste un intitulé interne
- [ ] La première phrase (`.exec-def`) définit la page à elle seule, compréhensible hors contexte (BLUF)
- [ ] Un seul sujet par page — pas de dérive vers plusieurs thèmes non liés
- [ ] Ton direct, sans hedging ("on pense peut-être que"), sans langage promotionnel ("absolument essentiel", "le meilleur choix")
- [ ] Terminologie cohérente avec le reste du corpus (mêmes termes pour les mêmes concepts d'une page à l'autre)
- [ ] Liens internes (`.link-internal`) présents pour tout terme à sens propriétaire stabilisé — voir la typologie à 3 catégories dans CLAUDE.md avant d'en ajouter
- [ ] Liens externes (`.link-external`) vers sources à forte autorité perçue (.edu, .gov, recherche évaluée par les pairs, Wikipédia en dernier recours) — jamais vers du contenu marketing/SEO commercial
- [ ] Un seul lien externe par affirmation vérifiable citée, placé inline au plus près du terme — pas de liste de sources séparée en fin de page
- [ ] Pas de bourrage de mots-clés ni de répétition mécanique de termes (dégrade la citabilité, -9% mesuré)
- [ ] Supporting Evidence : présent **seulement si réellement nécessaire** (rare) — ne pas l'ajouter par réflexe de conformité
- [ ] Knowledge Graph (bloc dédié fin de page) : **volontairement absent** par choix éditorial — ne pas le suggérer sauf preuve empirique nouvelle contredisant cette décision (voir CLAUDE.md)
- [ ] Meta-bar conforme au pattern v2.1.0 (lang-switch fusionné, pas de bloc séparé)
- [ ] Si contenu traduit : noms de fichiers FR/EN/DE cohérents entre eux (voir règle critique de nommage dans CLAUDE.md)

## Sortie attendue

Pour chaque point : ✓ présent / ✗ absent / — non applicable, avec une phrase de justification si absent ou non applicable. Ne pas transformer ceci en score chiffré. Terminer par une liste des corrections concrètes à apporter, s'il y en a — pas de note globale du type "8/13".
