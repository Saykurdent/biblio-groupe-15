# Biblio

## Sommaire

- [Prérequis](#prérequis)
- [Installation](#installation)
- [Utilisation](#utilisation)
- [Tests](#tests)
- [Structure du projet](#structure-du-projet)
- [Contribuer](#contribuer)
- [Auteurs](#auteurs)

## Prérequis

Avant de commencer, assurez-vous d’avoir installé :

- [Python 3](https://www.python.org/)
- [Git](https://git-scm.com/)

## Installation

### 1. Cloner le dépôt

Vous pouvez récupérer le projet soit avec GitHub Desktop, soit via Git CLI.

```bash
git clone https://github.com/Saykurdent/biblio-groupe-15.git
```

### 2. Initialiser la base de démonstration

Depuis la racine du projet, exécutez :

```bash
python biblio.py init
```

Résultat attendu :

```text
Base initialisee : 6 livres, 3 membres.
```

> Sous Linux/macOS, utilisez `python3`.  
> Sous Windows, si `python` ne fonctionne pas, utilisez `py`.

## Utilisation

Les commandes doivent être lancées depuis la racine du dépôt, après avoir initialisé la base avec :

```bash
python biblio.py init
```

### Lister les livres

```bash
python biblio.py livres
```

Résultat attendu :

```text
[1] L'Etranger (Albert Camus) : disponible
[2] Dune (Frank Herbert) : emprunte
[3] Le Petit Prince (Antoine de Saint-Exupery) : disponible
[4] Fondation (Isaac Asimov) : disponible
[5] Les Miserables (Victor Hugo) : disponible
[6] Neuromancien (William Gibson) : disponible
```

### Chercher un livre

```bash
python biblio.py chercher "Dune"
```

Résultat attendu :

```text
[2] Dune (Frank Herbert)
```

### Emprunter un livre

```bash
python biblio.py emprunter <id_livre> <id_membre>
```

Exemple :

```bash
python biblio.py emprunter 3 1
```

Résultat attendu :

```text
Emprunt enregistre : livre 3, membre 1.
```

### Rendre un livre

```bash
python biblio.py rendre <id_livre>
```

Exemple :

```bash
python biblio.py rendre 3
```

Résultat attendu :

```text
Retour enregistre pour le livre 3.
```

### Lister les retards

```bash
python biblio.py retards
```

Résultat attendu :

```text
Dune, emprunte par Alice Martin : 254 jours de retard
```

## Tests

Pour vérifier le bon fonctionnement du projet, lancez :

```bash
python -m unittest discover -s tests -t .
```

Résultat attendu :

```text
Ran 4 tests in 0.1s

OK
```

> Sous macOS ou Linux, utilisez `python3`.  
> Sous Windows, si `python` ne fonctionne pas, utilisez `py`.

## Structure du projet

```text
biblio-tp/
├── biblio.py               # programme principal
├── README.md               # documentation du projet
├── docs/
│   ├── adr/                # décisions techniques (ADR)
│   └── circulation.md      # gestion de la circulation des livres
├── tests/
│   └── test_biblio.py      # tests automatisés
```

## Contribuer

Les contributions sont les bienvenues. Vous pouvez proposer des améliorations, signaler des bugs ou suggérer des idées directement dans ce projet. En le clonant, et en proposant vos modifications depuis votre branche via une PULL REQUEST.

## Auteurs

Arthur, Maxime, Ethan, Djibril