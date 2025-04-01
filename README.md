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