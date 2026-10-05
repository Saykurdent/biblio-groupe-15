# ADR 0001 : Choix de SQLite pour la persistance des données

* Statut : accepté
* Date : 2026-10-05
* Décideurs : Ethan et Djibril

## Contexte

L'application de gestion de bibliothèque est destinée à être installée et utilisée localement par des bénévoles qui n'ont pas nécessairement de compétences poussées en administration système. Le système doit garantir l'intégrité des transactions (notamment pour éviter les conflits lors de deux opérations simultanées, comme deux emprunts en même temps) tout en restant extrêmement simple à déployer et à maintenir.

## Options envisagées

1. **Fichier plat JSON**
   * *Avantages* : Très simple, lisible directement, aucun outil externe nécessaire.
   * *Inconvénients* : Aucune gestion native de la concurrence (conflits d'écriture/race conditions si deux prêts surviennent simultanément) requêtes complexes à coder manuellement en Python.

2. **Serveur PostgreSQL (client/serveur)**
   * *Avantages* : Excellente gestion des accès concurrents, scalabilité.
   * *Inconvénients* : Nécessite l'installation, la configuration d'un service/serveur dédié sur la machine des bénévoles (ports, utilisateurs, authentification réseau)

3. **Base de données embarquée SQLite**
   * *Avantages* : Intégré nativement dans la bibliothèque standard Python (`sqlite3`) sans aucune dépendance ni installation de serveur requise, stockage dans un fichier unique facile à sauvegarder.
   * *Inconvénients* : Moins adapté pour des accès concurrents (non requis dans notre périmètre actuel).

## Décision

Nous choisissons **SQLite** pour stocker les données de l'application.

Ce choix offre le meilleur compromis :
* **Zéro configuration pour les bénévoles** : le module est inclus avec Python, la base se crée automatiquement via le script `biblio.py init`.
* **Fiabilité des opérations** : SQLite gère nativement les verrous et les transactions, ce qui empêche les corruptions si deux actions ou prêts surviennent en parallèle.

## Conséquences

* **Positives** :
  * Déploiement immédiat via un simple clonage Git et Python.
  * Sauvegarde simplifiée (il suffit de copier le fichier `.db`).
  * Requêtage SQL standard, puissant et performant pour lister livres, membres et retards.
  * Robustesse face aux crashs et intégrité des données garantie.
* **Négatives / Limites** :
  * Si la bibliothèque souhaite un jour centraliser la base sur un serveur distant multi-postes via le réseau, une migration vers PostgreSQL ou la mise en place d'une API sera nécessaire.