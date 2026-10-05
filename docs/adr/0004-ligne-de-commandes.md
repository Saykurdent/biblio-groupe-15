# ADR 0004 : une interface en ligne de commande plutôt qu'un site web

- Statut : proposé
- Date : 2026-10-06
- Décideurs : toutes l'équipe

## Contexte

Biblio sert à une petite association : quelques bénévoles enregistrent les prêts
et les retours, souvent sur un seul ordinateur, à la permanence.
Ce sont eux qui installent et lancent le logiciel, sans informaticien pour les aider.
Il faut choisir comment ils vont utiliser Biblio : en tapant des commandes,
ou à travers un site web dans un navigateur.

## Options

### Option 1 : un site web

- Pour : interface avec des boutons et des formulaires, plus intuitive
  pour un bénévole qui n'a jamais utilisé de terminal.
- Contre : il faut un framework (Flask, Django), un serveur à lancer ou à héberger,
  et gérer la sécurité (comptes, mots de passe, accès depuis Internet).

### Option 2 : une interface en ligne de commande

- Pour : rien d'autre que Python à installer, une commande par action
  (`emprunter 2 3`, `rendre 2`), et facile à tester automatiquement.
- Contre : il faut ouvrir un terminal et retenir les commandes,
  ce qui peut faire peur aux bénévoles débutants.

## Décision

Biblio s'utilise en ligne de commande, avec une commande par action.

## Conséquences

- Plus facile : installation en une étape, pas de serveur ni d'hébergement,
  code plus court et tests simples à écrire (`python -m unittest`).
- Plus difficile : les bénévoles doivent apprendre les commandes,
  une seule personne à la fois peut utiliser la base,
  et on ne peut pas consulter les prêts depuis un téléphone ou un autre lieu.
  La documentation (README) devient indispensable.
