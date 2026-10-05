# Circulation de l'information : groupe 15

Groupe 15 : un seul membre actif pour cette séance, toutes les sections sont rédigées par la même personne.

## 1. Rôles
Rédigé par : maxime-kun

- **Issues** : je reproduis les messages des bénévoles (reçus sur Discord) et j'ouvre les issues sur GitHub.
- **Relecture des pull requests** : un camarade d'un autre groupe ou l'enseignant (@Hika-Li), puisque je ne peux pas relire mon propre code.
- **Merge** : je merge seulement après une relecture approuvée.

## 2. Où circule chaque information
Rédigé par : maxime-kun

| Information | Qui la produit | Qui la valide | Où elle est stockée | Durée de vie |
|---|---|---|---|---|
| Code source | Moi | Relecteur de la PR | Dépôt GitHub `biblio-groupe-15` | Permanente (historique Git) |
| Bug signalé | Bénévoles (Discord), puis moi | Moi, après reproduction | GitHub Issues | Jusqu'à la fermeture de l'issue |
| Décision technique | Moi | Enseignant | `docs/adr/` dans le dépôt | Permanente |
| Documentation d'installation | Moi | Un camarade qui la teste | `README.md` | Mise à jour à chaque changement |
| Question rapide entre membres | Moi ou un camarade | Personne | Discord | Courte (quelques jours) |
| Compte rendu de réunion | Moi | Personne | GitHub Issues (commentaire) ou `docs/` | Permanente |

## 3. Règles de l'équipe
Rédigé par : maxime-kun

- **Titre d'issue** : ce qui se passe et où (ex. « emprunter accepte un membre inexistant »), jamais le message Discord recopié.
- **Contenu d'une issue** : commit, système, version de Python, étapes numérotées depuis `python3 biblio.py init`, attendu et observé copié.
- **Modèles** : Signaler un bug, Proposer une évolution, Poser une question (pour un comportement normal : répondre puis fermer).
- **Labels** : `securite` pour tout problème de sécurité, sans mode d'emploi d'attaque.
- **Tri** : je trie les issues. **Assignation** : laissée vide, chacun s'assigne quand il prend une issue.
- **Mon environnement** : Linux, Python 3.12.3, commandes lancées avec `python3`, Git en ligne de commande.
- À partir de la séance 2 : aucun push direct sur `main`, tout passe par une pull request relue.
