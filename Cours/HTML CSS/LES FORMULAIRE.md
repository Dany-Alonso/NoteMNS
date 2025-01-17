
# Balise principale

- `<form>` : Conteneur principal d'un formulaire HTML.
les attributs
**`action`** :

- Définit l’URL où les données du formulaire seront envoyées.
- Exemple :    `<form action="process.php">`
    
- Si omis, les données sont envoyées à la même page que celle contenant le formulaire.

**`method`** :
- Indique la méthode HTTP utilisée pour envoyer les données.
- Valeurs possibles :
    - `GET` : Les données sont ajoutées à l'URL de la requête (visible dans la barre d'adresse).
    - `POST` : Les données sont envoyées dans le corps de la requête (plus sécurisé pour les données sensibles).

**`enctype`** :
- Définit le type d’encodage des données envoyées.
- Valeurs possibles :
    - `application/x-www-form-urlencoded` (par défaut) : Convient à la plupart des formulaires.
    - `multipart/form-data` : Nécessaire pour le téléchargement de fichiers (`<input type="file">`).
    - `text/plain` : Envoie les données en texte brut (rarement utilisé).
---
# Champs de saisie 

(balise `<input>` avec différents types)
- **Texte et mot de passe :**
       - `<input type="text">` : Champ de texte classique.
    - `<input type="password">` : Champ pour mot de passe (les caractères saisis sont masqués).
- **Données numériques :**
       - `<input type="number">` : Champ pour entrer un nombre (avec options pour un intervalle et des incréments).
    - `<input type="range">` : Curseur permettant de sélectionner une valeur dans une plage.
- **Options booléennes :**
       - `<input type="checkbox">` : Case à cocher.
    - `<input type="radio">` : Bouton radio (sélection unique parmi un groupe).
- **Données temporelles :**
       - `<input type="date">` : Sélecteur de date.
    - `<input type="datetime-local">` : Sélecteur de date et heure locales.
    - `<input type="month">` : Sélecteur de mois et année.
    - `<input type="time">` : Sélecteur d'heure.
    - `<input type="week">` : Sélecteur de semaine.
- **Entrée de fichiers et données spécifiques :**
       - `<input type="file">` : Champ pour télécharger un fichier.
    - `<input type="email">` : Champ pour e-mail (validation automatique du format).
    - `<input type="url">` : Champ pour URL (validation automatique du format).
    - `<input type="tel">` : Champ pour numéro de téléphone.
    - `<input type="color">` : Sélecteur de couleur.
- **Champs masqués et boutons :**
       - `<input type="hidden">` : Champ caché pour transmettre des données au serveur.
    - `<input type="submit">` : Bouton pour envoyer le formulaire.
    - `<input type="reset">` : Bouton pour réinitialiser le formulaire.
    - `<input type="button">` : Bouton générique sans action définie (souvent manipulé via JavaScript).
    - `<input type="image">` : Bouton de soumission sous forme d'image.

---

# Autres balises pour formulaires :

- **Zone de texte multi-ligne :**
    
    - `<textarea>` : Champ de saisie multi-lignes.
```
<label for="commentaire">commentaires</label>

<textarea id="commentaire" name="commentaire" rows="5" cols="33">
dites nous tout 
</textarea>

```
- **Menus déroulants :**
        - `<select>` : Liste déroulante.
        - `<option>` : Options dans la liste.
        - `<optgroup>` : Groupe d'options dans une liste.
- **Boutons :**
        - `<button>` : Bouton personnalisable (peut servir pour soumettre, réinitialiser ou toute autre action).
- **Étiquettes et structure :**
       - `<label>` : Associe un texte descriptif à un champ de formulaire.
    - `<fieldset>` : Regroupe des champs de formulaire.
    - `<legend>` : Titre pour un groupe de champs (utilisé avec `<fieldset>`).
- **Avancé (HTML5) :**
       - `<datalist>` : Liste d'options pré-remplies pour `<input>`.
    - `<keygen>` (déprécié) : Utilisé pour générer une clé cryptographique.
    - `<output>` : Champ pour afficher une valeur calculée ou générée.

---

### **Attributs communs utiles :**
- `required` : Rend le champ obligatoire.
- `placeholder` : Affiche un texte indicatif dans un champ.
- `readonly` : Rend le champ non modifiable.
- `disabled` : Désactive un champ.
- `pattern` : Définit une expression régulière pour valider la saisie.
- `maxlength` et `minlength` : Contrôle la longueur de la saisie.
- `min` et `max` : Définit les valeurs minimales et maximales (numérique et date).
- `step` : Définit l'incrémentation pour les valeurs numériques.


# Mise en application 

## Créer un formulaire simple 
```
    <form action="traitement_form.php">
        votre email <input type="email" name="email" placeholder="veillez saisir votre email"><br>
        nom <input type="text" size="10" maxlength="25" minlength="25" name="nom"><br>
        prenom <input type="text" size="20" name="prenom">
        <br>né le<input type="date" name="daten">

        <input type="submit" name="validation" >

    </form>
```

## Créer la page traitement_form.php


```
<h1>affichage des données reçu depuis le formulaire</h1>

<table style=" border: 1px solid black">
    <thead>
        <tr>
            <th>champ</th>
            <th>valeur reçue</th>
        </tr>
    </thead>
<?php
echo "<tr><td>nom du client  : </td><td>" .           $_REQUEST['nom'] . "</td></tr>";
echo "<tr><td>prénom du client  :  </td><td>" .    $_REQUEST['prenom'] . "</td></tr>";
echo "<tr><td>courriel  :  </td><td>" .            $_REQUEST['email']. "</td></tr>" ;
echo "<tr><td>date naiss  : </td><td>" .            $_REQUEST['daten']. "</td></tr>" ;
?>
</table>
<hr><a href="formulaire.html">retour</a>
```

nb : ces fichiers doivent  être déposés dans un dossier à la racine du répertoire de WAMP ou de votre serveur Web. De plus à chaque fois que vous modifier votre formulaire pensez à adapter le script php en conséquence 

# Quelques exemples

## sur le champ nom , ajoutez l'attribut value="Doe" 
```
<input type="text" size="10" maxlength="25" minlength="25" name="nom" value="doe">
```

Que constatez vous lors de l'ouverture du formulaire ? 


## sur le champ nom ajoutez l'attribut "readonly"
```
<input type="text"  readonly size="10" maxlength="25" minlength="25" name="nom" value="quirin">
```
Que constatez-vous ?



## sur le champ email , ajoutez  l'attribut required 
```
<input type="email"  required name="email" placeholder="veillez saisir votre email">
```
que constatez vous lorsque vous validez le formulaire sans avoir saisi  l'email au  préalable


## Password
A faire : ajouter un champ password dans votre formulaire et afficher le mot de passe dans le  fichier php

```
`<input type="password" name="mdp" required >`
```

Que constatez vous lors de la saisie ? 
Que se passe t'il lorsque vous validez le formulaire


## Traitement des nombres 
 testez les types suivants ( pensez à modifier votre script php )

```
<input type="number" id="note" name="note" min="1" max="20" />
```

```
<input type="range" id="taux" name="taux" min="0" max="100" value="90" step="10" />
```


## traitements des cases à cocher et les boutons radio

### les boutons radio

```
<fieldset>
  <legend>quelle est votre promo</legend>

  <div>
    <input type="radio" id="devweb" name="promo" value="devweb" checked />
    <label for="devweb">devweb</label>
  </div>

  <div>
    <input type="radio" id="cda" name="promo" value="cda" />
    <label for="cda">cda</label>
  </div>

  <div>
    <input type="radio" id="tssr" name="promo" value="tssr" />
    <label for="tssr">tssr</label>
  </div>
</fieldset>
```

regardez bien ce qui se passe du côté serveur quand vous sélectionnez un champ

Que constatez vous sur l'attribut name de ces 3 champs ?


### les cases à cocher
```
<fieldset>
  <legend>Quel langage vous maitrisez</legend>

  <div>
    <input type="checkbox" id="css" name="css" checked />
    <label for="css">css</label>
  </div>

  <div>
    <input type="checkbox" id="html" name="html" />
    <label for="html">html</label>
  </div>
</fieldset>
```

regardez bien ce qui se passe du côté serveur quand vous sélectionnez un champ et que vous validez le formulaire
Que se passe t'il si vous ne sélectionnez pas une des  options.
Que constatez vous sur l'attribut name de ces 2 champs ?

Que permet de faire l'attribut checked ?

## les listes déroulantes

### le select

représente un contrôle qui fournit une liste d'options parmi lesquelles l'utilisateur pourra choisir.

```
<label for="club">choisissez votre club préféré</label>

<select name="club" id="club">
  <option value="">--Please choose an option--</option>
  <option value="fcmetz">METZ</option>
  <option value="asnl">NANCY</option>
  <option value="ol">LYON</option>
  <option value="om">MARSEILLES</option>
  <option value="psg">PARIS</option>
  <option value="losc">LILLE</option>
</select>


```

Modifiez votre script PHP,  faites des tests. Regardez les différentes valeurs reçues
###  option

L'élément HTML option, utilisé dans un formulaire, permet de représenter un contrôle au sein d'un élément select, optgroup ou datalist. Cet élément peut donc représenter des éléments d'un menu dans un document HTML.

### sur le select positionnez l'attribut size=-1
que constatez vous ?

sur le select positionnez l'attribut size=3
que constatez vous ?

Sur une option positionnez l'attribut "selected"
que constatez vous ?

## organisez un peu votre select

```
<label for="langage">Choisissez votre langage</label>
<select id="language">
  <optgroup label="front">
    <option>HTML</option>
    <option>CSS</option>
    <option>JS</option>
  </optgroup>
  <optgroup label="back">
    <option>PHP</option>
    <option>JS</option>
    <option>JAVA</option>
  </optgroup>
</select>
```


## DATALIST

```
 <label for="fruits">choisissez un fruit</label>
<input list="list_fruits" id="fruits" name="fruits" />
<datalist id="list_fruits">
  <option value="banane">banane</option>
  <option value="pomme">pomme</option>
  <option value="cerise">cerise</option>
  <option value="pamplemousse">pamplemousse</option>
  <option value="poire">poire</option>
</datalist>
```

que se passe t'il lors de  la saisie d'une valeur , la lettre p par exemple

#formulaire #balise #attribut #html 