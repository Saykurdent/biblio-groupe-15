# ADR 0003 : Convention de nommage des branches Git

* Statut : accepté
* Date : 2026-10-05
* Décideurs : Toute l'équipe

## Contexte

Plusieurs personnes travaillent sur le projet. Sans règle claire, les noms de branches deviennent vite désordonnés, ce qui rend difficile de savoir qui fait quoi ou à quel ticket (issue) correspond une branche.

## Options envisagées

1. **Nommage libre (ex. `modif-sql`, `test-emprunt`)** : très rapide et sans contrainte, mais illisible dans la liste des branches et impossible de faire le lien direct avec une issue GitHub.
2. **Format structuré `type/n°-mots-cles` (ex. `feat/12-recherche-titre`, `fix/4-bug-retard`)** : un peu plus contraignant à l'écriture, mais lie immédiatement la branche au type de tâche et au numéro de l'issue associée.

## Décision

Nous adoptons le format obligatoire suivant pour toutes les branches :  
`<type>/<n°_issue>-<mots-cles>`

* **Types autorisés** : `feat` (nouvelle fonctionnalité), `fix` (correction de bug), `docs` (documentation/ADR), `refactor` (nettoyage de code), `test` (tests unitaires).
* **Exemples** : `feat/14-rendre-livre`, `fix/2-crash-apostrophe`, `docs/8-adr-sql`.

## Conséquences

* **Positives** : un simple coup d'œil à la liste des branches (`git branch`) permet de retrouver l'issue GitHub correspondante et de comprendre son but.
* **Négatives** : obligation de créer ou de consulter l'issue sur GitHub avant de créer sa branche locale.