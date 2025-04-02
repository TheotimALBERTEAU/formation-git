# 1 LES BASES 
## Le dépôt Git
- Un dépôt Git est un répertoire contenant l'historique d'un projet logiciel.
- Un dépôt local :
  * Est situé sur la machine du développeur ;
  * N'est pas partagé entre plusieurs développeurs.
- Pour créer un dépôt, il faut initialiser un répertoire avec la structure nécessaire.
- Deux cas de figure :
- Le répertoire existe déjà (et contient peut être des fichiers de projet !) :
  * Se positionner dans le répertoire
```cmd
git init
```
  * Le répertoire n'existe pas :
```cmd
git init <nom_répertoire>
```

## Ajout de fichiers au depôt : 
- Pour qu'un fichier passe sous contrôle de version Git, il faut d'abord l'ajouter au dépôt.
- Commande git add
  * Elle va ajouter le(s) fichiers dans la zone d'index, ils sont simplement marqués et ne sont pas encore ajoutés !
- Ajouter un fichier : 
```cmd
git add test.js
```
- Ajouter tous les fichiers du répertoire :
```cmd
git add .
```
- Ajouter de manière interactive :
```cmd
git add -p
```
- A tout moment, la commande ```git status``` permet de connaître l'état du dépôt Git !

## Valider des fichiers dans le dépôt

- Valider les fichiers dans le dépôt consiste à envoyer les fichiers présents dans la zone d'index dans le dépôt.
  * C'est le « commit » !
  * Chaque commit concerne une collection de modifications apportées à un ou plusieurs fichiers.
- Pour le bon suivi de l'historique du projet, chaque commit doit être associé à un message décrivant les modifications qui sont apportées au projet par cette validation.
- Validation avec ouverture de l'éditeur de texte pour la saisie du message :
```cmd
git commit
```
- Validation avec message :
```cmd
git commit -m "Mon commentaire constructif"
```
- Indexation et commit en une seule commande ! :
```
git commit -am "Mon commentaire constructif"
```
- Cela permet d'enregistrer toutes les modifications en cours, même celles non-indexées !
- ATTENTION : Cela ne s'applique qu'aux fichiers déjà existant dans le dépôt

# 2 LES TAGS 
- Qu’est-ce qu’un tag ?
    - Définition et usage
    - Bonnes pratiques d’utilisation des tags



### Qu’est-ce qu’un tag ?
- Alias/Nom défini par un développeur.
    - Il pointe vers un commit pour l’identifier facilement. 
- Les tags sont utilisés pour nommer à des moments précis l’état du dépôt. 
    - Ils permettent d’éviter l’utilisation des hashs SHA-1 qui ne sont pas explicites 
et difficiles à retenir.
- Les tags sont notamment utilisés pour marquer des numéros de version sur 
des commits.


## Bonnes pratiques d’utilisation des tags
- Il est essentiel d’utiliser les tags à bon escient !
- Ils doivent correspondre à un état de mémoire significatif.
    - Version stabilisée à livrer, identification d’une fonctionnalité terminée, numéro 
de patch, …
- Une nomenclature de nommage doit être définie pour un projet.

## Numérotation des versions
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

## Les différents types de tags
### 2 types de tags : 
- Tags légers.
    - Ils stockent le nom du tag sur un commit donné.
- Tags annotés.
    - Ils stockent le nom de la personne qui créé le tag (utilisateur Git).
    - Ils stockent également un message informatif sur le tag.
        - Informations relatives à la version, 

## Création d’un tag
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

## Lister les tags et leurs informations
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

## Supprimer un tag
- Il s’agit simplement de supprimer l’alias positionné sur le commit, et non pas 
le commit en tant que tel !
    - Supprimer un tag n’entraîne donc aucune perte dans l’historique du projet.
    - Commande : 
    ```
    git tag -d <nom du tag>
    ``` 

# 3 LES BRANCHES :

Pour afficher l'arbre des branches dans Git, voici plusieurs méthodes :  

---

### 📌 **1. Afficher l'arbre des commits avec les branches locales et distantes**
```sh
git log --oneline --decorate --graph --all
```
💡 **Explication** :
- `--oneline` : Affiche chaque commit sur une seule ligne.
- `--decorate` : Montre les noms des branches et tags.
- `--graph` : Dessine l'arbre avec des lignes ASCII.
- `--all` : Affiche toutes les branches (locales + distantes).

---

### 📌 **2. Voir les branches en arborescence avec `git branch`**
- **Branches locales uniquement** :
  ```sh
  git branch --sort=-committerdate --format="%(refname:short) → %(upstream)"
  ```
  ➜ Affiche les branches triées par date de commit.

- **Branches locales et distantes avec détails** :
  ```sh
  git branch -a --format="%(refname:short) → %(upstream)"
  ```
  ➜ Montre aussi les branches distantes (`origin/...`).

---

### 📌 **3. Avec `gitk` (interface graphique)**
```sh
gitk --all
```
💡 Ça ouvre une fenêtre interactive pour explorer l’historique.

---

### 📌 **4. Avec `git show-branch`**
```sh
git show-branch --all
```
💡 Affiche un résumé compact des branches et de leurs commits.

---

### 📌 **5. Avec `tig` (si installé)**
Si tu as **`tig`**, un outil en ligne de commande plus lisible :
```sh
tig --all
```