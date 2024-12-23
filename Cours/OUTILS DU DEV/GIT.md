[Cours sur GIT](https://metz-numeric-school.gitbook.io/cours-dev/git)
# <font color="#f79646">Git est un outil de versionning</font>
**Déf :** <span style="background:#d4b106">C'est un logiciel qui agit sur une arborescence de fichiers afin de conserver toutes les versions des fichiers, ainsi que les différences entres ces même fichiers</span>

> [!WARNING]
> Cela fonctionne seulement pour les fichiers suivis.

## <font color="#fac08f">Configuration de Git via GitBash</font>

**Configurer son nom d'utilisateur et son adresse e-mail :**
```bash
# Entrez ces commandes dans GitBash ou un terminal
git config --global user.name "Votre Nom"
git config --global user.email "votre.email@example.com"
```

**Vérifiez la configuration :** 
```bash
# Entrez cette commande dans GitBash ou un terminal
git config --list
```


## <font color="#fac08f">Initialisation d'un projet</font>

###### **Créer un dossier, ce dossier sera l'endroit où l'on commencera nos dossier projets**

*Créer un dossier et y naviguer :*
```bash
# Création d'un dossier
mkdir mon-projet

# Naviguer jusqu'à un dossier
cd mon-projet
```

###### **Ensuite dans ce même dossier on initialise le dépôt git**

*Initialiser un dépôt :*
```bash
get init
```

###### **Toujours avoir un fichier README.md, il sert à expliquer le projet**

*Fichier README.md :*
```bash
# "echo" sert à écrire dans le fichier readme.md et ">>" indique au terminal une création de fichier
echo "# Mon Projet" >> README.md
# la commande permet d'ajouter tout nouveau fichier dans le suivi git (içi on utile un . pour prendre directement tout les nouveaux fichiers)
git add .
```

###### **Faire un premier commit**

*Commande pour commit :*
```bash
git commit -a -m "Premier commit : Ajoute du fichier README.md"
```

>[!TIPS]
> - Créer un dossier "repositories" à la racine du disque dur permet un gain de temps sur l'arborescence.
> - Commande terminal pour ouvrir un projet dans VSC
> ```code .```



# <font color="#f79646">Travailler avec GitHub</font>

## <font color="#fac08f">Création d'un dépôt sur GitHub</font>

1. Sur GitHub connectez-vous 
2. Cliquez sur le bouton "+" et sélectionnez "New repository".
3. Donnez un nom à votre dépôt et cliquez sur "Create repository"


## <font color="#fac08f">Lier le dépôt local à GitHub</font>

1. *Ajouter l'URL du dépôt GitHub comme remote :*
```bash
git remote add origin https://github.com/votre-nom-utilisateur/mon-projet.git
```

2. *Pousser le contenu local vers GitHub :*
```bash
# master ou main selon les préréglages définis
git push -u origin master
```

>[!NOTE]
>`-u` crée une association entre la branche locale et la branche distante, facilitant les futurs `git push` et `git pull`.



# <font color="#f79646">Bonnes pratiques</font>

## <font color="#fac08f">Commit Atomique</font>

>[!IMPORTANT]
>**1 seul commit par tâche**

<u>Exemple</u> : Créer un formulaire de contact


## <font color="#fac08f">Nomination de branche</font>

>[!IMPORTANT]
>MESSAGE CLAIR ET SIGNIFICATIF / PERTINENT

**Nom de branche pour une nouvelle fonctionnalité :**
- *feature/nouvelle-fonctionnalité*

**Nom de branche pour fix un bug :**
- bugfix/correction-du-bug*

**Nom de branche pour améliorer le code :**
- refactor/form-control*


## <font color="#fac08f">Mise à jour régulière des branches</font>

**Rebaser souvent la branche avec `main` pour éviter les conflits**
```bash
git checkout main
git pull
git checkout votre-branche
git merge main
```

>[!tips]
>Résolvez directement les conflits qui ce produisent


## <font color="#fac08f">GitIgnore</font>

**Ce place à la racine du projet (comme .git) en tant que fichier.**
**Il permet d'exclure certains fichier ou dossier du dépôt.**


## <font color="#fac08f">Etiqueter les versions</font>

**Ajout de tag que le projet est stable**
<u>Exemple</u> : v1.0.0

**La nomenclature pour lire une version est la suivante :**

- 1er X : Upgrade majeure
>[!NOTE]
> La release ce fait souvent sur une autre branche GIT
- 2eme X : Update mineure (ajout de fonctionnalités par exemple)
- 3eme x : Multiple patch

*Pour ajouter un tag :*
```bash
git tag -a vX.X.X -m "message"
git tag vX.X.X
```

*Pour push le tag :*
```bash
git push origin VX.X.X
```



# <font color="#f79646">Conventions de commits</font>

## <font color="#fac08f">Type de commits</font>

  **[Les différents type de commits](https://metz-numeric-school.gitbook.io/cours-dev/git#conventions-de-commits-conventional-commits)**

> [!tips]
> L'optional body représente les détails
> L'optionnal footer représente des infos importantes



# <font color="#f79646">Installer Git-Cliff</font>

Dans un terminal :
```bash
# Pour rechercher git-cliff
winget search git-cliff

# Après avoir vérifier que c'est bien git-cliff
winget install git-cliff

# Initialiser git-cliff
git cliff --init

# Générer un changelog
git cliff -o CHANGELOG.md
```
  
