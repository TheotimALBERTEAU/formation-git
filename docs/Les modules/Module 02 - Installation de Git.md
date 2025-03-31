# Module 02 - Installation de Git

- Principes d'installation selon le système d'exploitation
    - Installation sous Linux
    - Installation sous macOS
    - Installation sous Windows
- Validation de l'installation et premières commandes
    - L'aide en ligne de commande
    - Principes et syntaxe des commandes Git
- Configuration post-installation
    - Création de comptes d'utilisateur

## Installation de Git
- Installation sous Linux
    - A partir de paquets existants dans la distribution.
    - A partir des sources.
- Installation sous macOS
    - Avec Homebrew
    - Avec XCode
- Installation sous Windows
    - Avec un installeur

## Installation sous Linux
- A partir des paquets d'une distribution
    - RedHat, CentOS, Fedora
        - sudo yum install git
    - Debian, Ubuntu
        - sudo apt install git
- A partir des sources
    - Installation des dépendances
        - _make, libssl-dev, libz-dev, gettext, libexpat1-dev, libcurl4-openssl-dev, build-essential_
    - Récupération et décompression du code source de Git
        - https://github.com/git/git/archive/v2.27.0.tar.gz
- Compilation et installation
    - cd code_git/git-2.27.0 
    - make prefix=/usr/local all 
    - make prefix=/usr/local install

## Installation sous macOS
- Git est fourni avec l'IDE XCode
    - Aucune installation supplémentaire nécessaire.
- _Command Line Tools for XCode_ permet d'installer   les outils de 
développement en ligne de commande (dont Git !) sans avoir besoin 
d'installer tout XCode.
    - Apple Developer ID nécessaire !
- Avec Homebrew
    - Télécharger et installer Homebrew (Un     gestionnaire de paquets pour macOS)
        - https://brew.sh
    - Dans un terminal
        - brew install git

## Installation sous Windows
 - Un installeur graphique est disponible
    - https://git-scm.com/download/win
- Il installe : 
    - Une intégration à l'explorateur Windows
    - Git Bash, permettant de disposer du shell Bash sous Windows
        - Et donc de certaines commandes Linux.
    - Un gestionnaire de mots de passe
        - Permettant de mémoriser les authentifications aux différents dépôts

 <img src="../img/02-git-bash.png" width="600">

## La ligne de commande
- Git s'utilise en ligne de commande !
    - Terminal Linux ou macOS
    - Git Bash sous Windows (recommandé) ou une simple Invite de commande
- Syntaxe :

```
 git <commande> [<arguments>]

```
   
    
<img src="../img/02-git-commande.png" width="600">
  
  exemple :
```
git --version
```

## L'aide
- **git help**
    - Aide sur la syntaxe générale de Git.
```
git help
```
- **git help commande**
    - Aide sur la syntaxe et l'usage de la commande donnée en argument.
        - Affiche une « man page » dans un navigateur Web.
```
git help <commande>
```
- **git help tutorial**
    - Un tutoriel précis et concis sur Git
```
git help tutorial
```
## Configuration de Git
- Une configuration minimale de Git est nécessaire avant de pouvoir l'utiliser.
- Git dispose de très nombreuses options permettant d'adapter son 
fonctionnement en fonction des usages.
    - **git help** config permet de connaitre les différentes possibilités de configuration 
de l'outil.
- La configuration peut se faire à trois niveaux : 
    - Le niveau système :
        - Les options concernent tous les utilisateurs de la machine.
        - git **config --system** ...



    - Le niveau utilisateur : 
        - Les options ne concernent que l'utilisateur qui les définies.
        - git **config --global** ...


    - Le niveau local :
        - Les options ne sont alors valides que pour le dépôt Git sur lequel les options sont définies.
        - **git config --local** ...

## L'identité utilisateur
- L'identité utilisateur permet de savoir qui apporte les modifications aux 
fichiers du dépôt.
    - Elle doit être définie avant de pouvoir utiliser les commandes Git.
- L'identité est constitué : 
    - D'un nom d'utilisateur.
    - D'une adresse email.
- Sur la ligne de commande :

```
git config --global user.name "Jean Frédéric VINCENT"
git config --global user.email "augure@gmail.com"
```
- NOTE : 
    - L'identité (et autres préférences) est enregistrée dans un fichier nommé 
.gitconfig et stockée dans le répertoire personnel de chaque utilisateur

## L'éditeur de texte
- Git utilise un éditeur de texte pour, par exemple :
    - Rédiger les commentaires associés à chaque commit.
    - Permettre la résolution des conflits.
    - Et de manière générale, pour la saisie de toute information nécessaire lors de 
la manipulation du dépôt.
- L'éditeur par défaut est Vi …
- Une commande git config permettra de choisir un éditeur alternatif est 
d'enregistrer cette préférence.
``` 
git config --global core.editor "'<chemin vers l'editeur>' 
[options]"
```
- Exemple avec Notepad++ :

```
git config --global core.editor "C:\Program Files (x86)\Notepad++\notepad++.exe" -multiInst-notabbar-nosession-noPlugin
```

## Un proxy HTTP(S)
- Lors d’opérations sur un dépôt distant en HTTP ou HTTPS, il peut être 
nécessaire de spécifier un serveur proxy à utiliser pour permettre à Git de 
sortir sur Internet.
```
 git config --global http.proxy http://user:pass@proxyhost:proxyport
```

## Les alias
- Certaines commandes Git sont riches de plusieurs options qui peuvent être 
combinées.
```
git log --graph --decorate--oneline ...
```
- Pour se faciliter la vie, il est possible de créer des alias (des raccourcis) sur ces 
commandes.
- Les alias sont stockés dans la configuration, ils se créés donc avec la 
commande git config.
- Exemple pour la commande précédente : 
```
git config --global alias.ll "log --graph --decorate--oneline ..."
```
- L’alias créé se nomme ll
```
git ll
```