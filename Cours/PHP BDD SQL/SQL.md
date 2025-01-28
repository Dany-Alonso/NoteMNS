*Basé sur la BDD vente2025*

# Requête SQL

## SELECT * FROM

``` SQL
SELECT * FROM article
WHERE prix_ht > 250
```
*Liste des articles dont le PU est supérieur à 250 €*

## ORDER BY
``` SQL
SELECT * FROM article
WHERE prix_ht > 250
ORDER BY prix_ht DESC
```
*Trier par l'ordre des prix avec "ORDER BY", deux possibilité (DESC - de plus grand au plus petit, ASC - le contraire)*

## AND, OR, BETWEEN, IN

### AND
``` SQL
SELECT * FROM article
WHERE num_famille = 8
AND quantite_stock > 100;
```
*Liste des articles de la famille 8 et dont la q-te en stock est supérieur à 100*

### OR
``` SQL
SELECT * FROM article
WHERE num_famille = 8
OR num_famille = 10
ORDER BY num_famille ASC
```
*On désire des articles de la famille de 8 ou 10*

### BETWEEN
``` SQL
SELECT description_article, quantite_stock FROM article
WHERE quantite_stock >=50
AND quantite_stock <=100
ORDER BY description_article ASC;

ou

SELECT description_article, quantite_stock
FROM article
WHERE quantite_stock BETWEEN 50 and 100
ORDER BY description_article ASC;
```
*On désire avoir le nom des articles dont la quantité en stock est comprise entre 50 et 10*

### IN
``` SQL
SELECT * FROM article
WHERE Num_famille IN (2,7,8,9,10)
```
*liste des articles des famille 2, 7, 8, 9, 10*

## Sous requête

``` SQL
SELECT * FROM client
WHERE Num_client NOT IN
(SELECT Num-client FROM commande)
```

## COUNT, SUM

``` SQL
SELECT num_famille, COUNT(*) AS "nb_articles", SUM(quantite_stock) AS "Quantité_en_stock"
FROM article
GROUP BY num_famille;
```
*Nombre d'article (COUNT) et quantité en stock (SUM pour faire la somme) pour chaque famille (GROUP BY num-famille) dans le where pour trier et est nécessaire quand il y a un SUM ou COUNT*
### COUNT

``` SQL
Select COUNT(*) FROM commandes;
```
*combien il y a des commandes*

``` SQL
SELECT num_client, COUNT(*) AS "nb_commandes" FROM commandes
GROUP BY num_client
ORDER BY num_client ASC;
```
*commandes par client*

### SUM

``` SQL
SELECT SUM(quantite_cde) FROM ligne_commande;
```
*Combien d'articles on été commandés en total*
  

# SGBDR et jointure

## INNER JOIN

``` SQL
SELECT description_article, nom_famille FROM article
INNER JOIN famille_article ON article.num_famille = famille_article.num_famille;
```

``` SQL
SELECT nom_client, prenom_client, num_commande, date_commande FROM commandes
INNER JOIN clients on commandes.num_client = clients.num_client
ORDER BY NOM_CLIENT ASC, num_commande ASC;
```

# Comment travailler avec des dates

## Timestamp

Timestamp stock en une variable les secondes depuis la créations d'Unix, laquelle on reconverti en date.

Toujours faire les requêtes en date américaines sinon cela ne fonctionne pas

Exemple :
```SQL
SELECT * FROM COMMANDES
WHERE date_commande BETWEEN '2020-01-01' and '2020-12-31'
ORDER BY date_commande DESC

ou

SELECT * FROM COMMANDES
WHERE year(date_commande) = 2020
ORDER BY date_commande DESC

ou

SELECT * FROM COMMANDES
WHERE date_commande >= '2020-01-01' 
and <= '2020-12-31'
ORDER BY date_commande DESC
```
*Cette requête nous sort les commandes de l'année 2020 du 1 janvier au 31 décembre trier dans l'ordre décroissant.*

# Requête jointure SQL

Voici une requête SQL pour sortir le numéro de clients, nom de clients et prénom de clients qui ont commandé en 2020, on utilise <span style="background:#fff88f">INNER JOIN table2 ON table1.id = table2.fk</span>
```SQL
SELECT DISTINCT clients.num_client, clients.nom_client, clients.prenom_client 
FROM clients
INNER JOIN commandes ON clients.num_client = commandes.num_client
WHERE year(commandes.date_commande) = 2020
ORDER BY clients.nom_client ASC , clients.prenom_client ASC
```
Il est utile de préciser la table ciblé en suffixe lorsqu'on ne maitrise pas encore la BDD (table.id => clients.num_client).

# HAVING

```SQL
SELECT DISTINCT clients.num_client, clients.nom_client , count(*) AS NBCDE FROM clients
INNER JOIN commandes ON clients.num_client = commandes.num_client
GROUP BY clients.num_client , clients.nom_client
HAVING nbcde > 28;
```
*Having permet de faire un filtre sur les fonctions SUM() et COUNT()*


On peut y ajouter une sous requête pour avoir le 28 non pas en brut mais en relation avec un client choisis (qui renverra le nombre de commande de ce clients) via php (avec les prepare) :
``` SQL
SELECT DISTINCT clients.num_client, clients.nom_client , count(*) AS NBCDE FROM clients
INNER JOIN commandes ON clients.num_client = commandes.num_client
GROUP BY clients.num_client , clients.nom_client
HAVING nbcde > (SELECT COUNT(*) AS nbcde FROM commandes
WHERE clients.num_client = 23);
```

#SQL  #JointureSQL #Timestamp #Having 

