Lorsque vous utilisez un champ <select> avec multiple, ajoutez des crochets [] à l'attribut name pour indiquer que ce champ envoie un tableau de valeurs.

```
 <fieldset>
        <legend>Veuillez choisir vos promos </legend>
        <select name="promo[]" id="promo"  size="3" multiple >
            <option value="dw1">DEV WEB 1</option>
            <option value="dw2">DEV WEB 2</option>
            <option value="c#">CDA C#</option>
            <option value="java">CDA JAVA</option>
            <option value="TAI">TAI</option>
            <option value="TSSR">TSSR</option>
            <option value="M21">MASTER DEV 1</option>
            <option value="M22">MASTER DEV 2 </option>
        </select>
      </fieldset>
```

le script côté PHP

```
if(isset($_REQUEST['promo'])){
    // un choix à été fait
    // c'est un tableau
    $listepromo = $_REQUEST['promo'] ;
    var_dump( $listepromo)  ;
    foreach ($listepromo as $promo) {
         echo "<tr><td>promo</td><td>" .$promo  . "</td></tr>";
    }
}
else {
    // aucun choix n'a ét fait dand le select
        echo "<tr><td>promo</td><td> aucun choix n'a était fait</td></tr>";
}
```
Ajout des crochets `[]`
    - Cela indique au navigateur que le champ peut contenir plusieurs valeurs et les envoie en tant que tableau.
Vérification en PHP
    - Vérifiez si `$_POST['choix']` est défini.
    - Vérifiez si `$_POST['choix']` est un tableau avec `is_array()`.
Traitement des données
    - Parcourez le tableau avec une boucle `foreach` pour accéder à chaque option sélectionnée.
    - Utilisez `htmlspecialchars()` pour protéger contre les injections XSS si vous affichez les valeurs.

