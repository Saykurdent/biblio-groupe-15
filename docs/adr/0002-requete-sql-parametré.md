# ADR 0002 : Requêtes SQL paramétrées obligatoires

* Statut : accepté
* Date : 2026-10-05
* Décideurs : Arthur, Maxime, Djibril, Ethan

## Contexte

Les commandes du programme reçoivent des données saisies par l'utilisateur (titre de livre, identifiants). Il faut éviter les failles de sécurité et les bugs quand un texte contient des apostrophes (ex. *L'Étranger*).

## Options envisagées

1. **Concaténation ou f-strings (`f"SELECT ... WHERE titre = '{titre}'"`)** : simple à écrire, mais dangereux (injections SQL) et plante sur les apostrophes.
2. **Requêtes SQL paramétrées (`"SELECT ... WHERE titre = ?", (titre,)`)** : sécurisé nativement par SQLite, gère automatiquement les apostrophes et bloque les injections.

## Décision

Nous imposons l'utilisation exclusive des **requêtes SQL paramétrées** (avec le symbole `?`). L'usage des f-strings ou de `+` pour insérer des variables dans du SQL est interdit.

## Conséquences

* **Positives** : protection totale contre les injections SQL et plus aucun bug sur les titres avec apostrophes.
* **Négatives** : penser à passer les arguments sous forme de tuple dans les appels `execute()`.