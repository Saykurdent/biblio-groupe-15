# Contribuer à Biblio

Ce guide explique comment proposer une modification dans le projet, de l'issue jusqu'au merge.
Il s'applique à tout le monde, y compris aux membres de l'équipe.

## Avant de coder

- Vérifier dans l'onglet Issues que le sujet n'est pas déjà traité. S'il l'est, commenter l'issue existante plutôt que d'en créer une autre.
- Sinon, ouvrir une issue avec le modèle adapté :
  - « Signaler un bug » : titre qui dit ce qui se passe et où, étapes numérotées en partant de `python biblio.py init`, résultat attendu, résultat observé copié dans un bloc de code ;
  - « Proposer une évolution » : le besoin et pour qui ;
  - « Poser une question » : quand on ne sait pas si c'est un bug ou un comportement normal.
- Un seul problème par issue.
- Pas de code sans issue : son numéro sert à nommer la branche et à fermer l'issue depuis la PR.

## Branches

- Personne ne pousse directement sur `main`, qui est protégée.
- Avant de créer une branche : sur `main`, Fetch origin puis Pull origin.
- Nommage (voir l'ADR sur la convention de branches) : `type/<n° issue>-mots-cles`, avec le type `fix`, `feat` ou `docs`.
  - `fix/3-double-emprunt`
  - `fix/7-recherche-apostrophe`
  - `docs/12-readme`
- Une branche ne sert qu'à une seule issue. Elle est supprimée après le merge.

## Commits

- Format : `type: message`, au présent, qui dit ce que fait le commit.
  - `fix: refuse l'emprunt d'un livre déjà prêté`
  - `fix: passe le texte de recherche en paramètre SQL`
  - `docs: ajoute la section utilisation du README`
- Un commit ne traite qu'un seul sujet.
- Avant de pousser : Pull origin, puis Push origin. Si le push est refusé, refaire Pull origin puis Push origin.

## Pull requests

- Règle de base : une issue, une branche, une PR.
- La base de la PR est notre dépôt, branche `main`, jamais le dépôt d'origine.
- La description suit le modèle du dépôt :
  - Contexte, avec `Closes #n` ;
  - Changements ;
  - Impact ;
  - Comment tester (les commandes exactes depuis `init`) ;
  - Checklist cochée.
- Choisir un relecteur dans *Reviewers*.
- Le merge est bloqué tant qu'il manque une approbation ou que le check `tests` est rouge.

## Review

- L'auteur d'une PR ne l'approuve jamais lui-même. CODEOWNERS désigne au moins deux relecteurs possibles pour chaque partie du dépôt.
- Le relecteur teste la PR en suivant « Comment tester », puis lance `python -m unittest`.
- Chaque commentaire suit la forme `étiquette : constat, raison, suggestion`. Les étiquettes possibles sont :
  - `bloquant` : empêche le merge ;
  - `suggestion` : amélioration conseillée ;
  - `question` : demande d'explication ;
  - `détail` : point mineur.
- On choisit *Request changes* dans ces cas :
  - le check `tests` est rouge ;
  - un secret (token, mot de passe) est écrit dans le code ;
  - une requête SQL est construite par concaténation au lieu d'un paramètre `?` (voir l'ADR sur les requêtes paramétrées) ;
  - la PR mélange plusieurs sujets ;
  - le comportement décrit dans l'issue n'est pas respecté ;
  - il manque `Closes #n`.

  Il faut toujours expliquer le refus dans un commentaire.
- L'auteur corrige sur la même branche, répond au commentaire, puis clique sur *Resolve conversation*.
- Une fois la PR approuvée, l'auteur merge et supprime la branche.

## Definition of Done

Une tâche est terminée quand toutes les cases sont cochées :

- [ ] le besoin décrit dans l'issue est couvert ;
- [ ] le comportement est vérifié à la main depuis `python biblio.py init` ;
- [ ] `python -m unittest` passe en local, et le check `tests` est vert sur la PR ;
- [ ] la PR est approuvée par une autre personne que l'auteur ;
- [ ] la documentation (README, ADR, CONTRIBUTING) est à jour si le comportement a changé ;
- [ ] la PR est mergée dans `main` et la branche est supprimée ;
- [ ] l'issue est fermée, automatiquement grâce à `Closes #n` ou à la main sinon.

Sous macOS ou Linux, utiliser `python3`. Sous Windows, si `python` ne marche pas, utiliser `py`.

## Signaler un blocage

Une PR sans relecteur, un conflit qu'on n'arrive pas à résoudre, une attente envers quelqu'un, une échéance proche : on ne reste pas bloqué en silence.

1. Ouvrir une issue avec le modèle « Signaler un blocage ». Le titre commence par `Bloqué :`.
2. Remplir les cinq champs :
   - la tâche, avec le lien vers l'issue ou la PR ;
   - le blocage, avec l'erreur exacte copiée ;
   - ce qui a déjà été essayé ;
   - ce dont on a besoin, en mentionnant la personne avec `@pseudo` ;
   - l'échéance.
3. La personne mentionnée répond en commentaire avec une action concrète : qui fait quoi, et quand.
4. L'auteur ferme l'issue une fois débloqué.
