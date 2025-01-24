# Connexion BDD

- Voici le bloc code pour la connexion à la BDD, en terme de sécurité il est IMPERATIF de changer le nom d'utilisateur (root) et d'ajouter un mdp (rien içi). Pour l'examen faire un floutage avec n'importe qu'elle chaine de caractère pour exprimer la sécurité

- <span style="background:#d4b106">Faille injection SQL</span> hyper importante, à présenter lors du sujet de fin d'année en expliquant bien qu'il faut une requête préparée 

Exemple :
``` php
<?php

// Connexion base de donnée
try {
    $db = new PDO("mysql:host=localhost;dbname=bdshop;charset=utf8", "root", "");
} catch (Exception $e) {
    die($e->getMessage());                                  // "Server maintenance" pour le client qu'il ne panique pas mais sinon sa sert à debugg si soucis
}
$stmt = $db->prepare("SELECT*FROM table_product");          // stmt = statement. WHERE product_id= :id" pourra être utilisé avec la suite pour sécurisé la commande
// $stmt->bindValue(":id", 42);                             // Pour sécurisé sur une requete préparait
$stmt->execute();                                           // Execute la requête SQL qui est demandé dans le prepare()
$recordset = $stmt->fetchAll();                             // Récupère dans la variable recordset (un tableau indexé), tout les tableaux associatifs
// $row = $stmt->fetch();                                   // Renvoi un seul résultat donc inutile de le parcourir par la suite (suffira d'appeler la variable)
?>
```

Récupération d'un chemin absolu sur un server
``` php
<?php echo $_SERVER["DOCUMENT_ROOT"] . "/include/connect.php"; ?> // Permet de récupérer le chemin sur un serveur puis en ajoute vers le dossier qu'on fait
```



#faille #SQL #Php #BDD 