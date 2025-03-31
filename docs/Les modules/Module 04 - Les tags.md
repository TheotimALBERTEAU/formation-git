# Module 04 - Les tags 
- Qu’est-ce qu’un tag ?
    - Définition et usage
    - Bonnes pratiques d’utilisation des tags



## Qu’est-ce qu’un tag ?
- Alias/Nom défini par un développeur.
    - Il pointe vers un commit pour l’identifier facilement. 
- Les tags sont utilisés pour nommer à des moments précis l’état du dépôt. 
    - Ils permettent d’éviter l’utilisation des hashs SHA-1 qui ne sont pas explicites 
et difficiles à retenir.
- Les tags sont notamment utilisés pour marquer des numéros de version sur 
des commits.


# Bonnes pratiques d’utilisation des tags
- Il est essentiel d’utiliser les tags à bon escient !
- Ils doivent correspondre à un état de mémoire significatif.
    - Version stabilisée à livrer, identification d’une fonctionnalité terminée, numéro 
de patch, …
- Une nomenclature de nommage doit être définie pour un projet.

# Numérotation des versions
- Plusieurs méthodes …
    - Pas d’idéal ! Il faut juste rester cohérent !
- Le «versionning sémantique » est courant.
    - Le numéro de version se construit à partir de trois nombres séparés de 
points : **x.y.z**
    - **x**: version majeure. 
        - Modifications importantes dans le fonctionnement de l’application (incompatibilités, 
…).
    - **y**: version mineure. 
        - Ajoute des fonctionnalités tout en conservant une compatibilité avec l’ancien système.
    - **z**: patch. 
        - Corrections de bugs sans ajout de fonctionnalités

# Les différents types de tags
### 2 types de tags : 
- Tags légers.
    - Ils stockent le nom du tag sur un commit donné.
- Tags annotés.
    - Ils stockent le nom de la personne qui créé le tag (utilisateur Git).
    - Ils stockent également un message informatif sur le tag.
        - Informations relatives à la version, 

# Création d’un tag
### Tag léger : 
- Option 1 : 
    - Se positionner sur le commit :
    ```
    git checkout <numéro de commit>
    ```
    -  Créer le tag :
    ```
    git tag <nom du tag>
    ```
- Option 2 :    
    - Créer le tag sans se positionner sur le commit : 
    ```
    git tag <nom du tag> <numéro de commit>
    ```
### Tag annoté : 
-  Ajouter l’option –a à la commande git tag !
-  La saisie d’un message est nécessaire !
    -  Soit de manière interactive
    -  Soit en ajoutant l’option –m "message"

# Lister les tags et leurs informations
- git tag --list
```
git tag --list
```
    - L’option –nx permet d’afficher les x lignes du message d’un tag nommé.
        - Par défaut x vaut 1
- git show <nom du tag>
```
git show <nom du tag>
```
    - Pour un tag léger : 
        - Affiche les détails du commit auquel il est attaché. 
    - Pour un tag annoté : 
        - Affiche les détails du tag puis les détails du commit.

# Supprimer un tag
- Il s’agit simplement de supprimer l’alias positionné sur le commit, et non pas 
le commit en tant que tel !
    - Supprimer un tag n’entraîne donc aucune perte dans l’historique du projet.
    - Commande : 
    ```
    git tag -d <nom du tag>
    ``` 

# git rebase
- Opérations pour rebaser : 
    - git checkout master
    - git rebase fix1
- Situation après le rebase : 

# Les conflits de fusion
- S’il y a eu des changements apportés aux 2 branches sur les mêmes lignes, il 
sera alors impossible de réaliser la fusion sans corriger le conflit au préalable.
- Corriger le(s) fichier(s) en conflit.
    - Penser à retirer les lignes <<<<, ==== et >>>>
- Une fois le conflit résolu, utiliser la commande git add.
- Terminer la fusion avec un git commit