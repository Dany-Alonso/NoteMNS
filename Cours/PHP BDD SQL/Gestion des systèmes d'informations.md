![[Gestion des systèmes d'informations.excalidraw.svg]]

# MERISE

Merise est une solution enseigné seulement en France et va nous permettre d'élaboré le schéma de nos BDD
La méthode va permettre de répondre à 
- QUOI ?
- QUI ?
- OU ?
- COMMENT ?
- QUAND ?

On va principalement ce servir de QUOI et QUI dans notre domaine

<u>Voici les étapes qu'on va suivre</u> :
1. Dictionnaire des données
	- Sert à lister l'ensemble des données qui sont à notre disposition
2. Etablir la matrice des dépendances fonctionnelles /!\
	- f() A -> B : On dit que A est en DF par rapport à B si, une valeur de B correspond au maximum à une unique valeur de A. On considère que la réciproque est fausse
3. Modèle conceptuel des données (MCD) ou Entités associations => Cœur/Schéma de la BDD
4. Modèle logique des données (MLD)
5. Modèle physique des données (MPD)
6. Implémenter la BDD (mySQL / PhpMyAdmin)
7. SQL

## Dictionnaire des données
L'objectif est de lister toutes les données que l'ont trouve dans un tableau

![[Tableau dictionnaire de données.svg]]

Type E : Donnée Elémentaire
Type P : Donnée Paramètre
Type C : Donnée Calculable

# Modèle conceptuel des données (MCD)

![[MCD.svg]]
## Cardinalité

0 si c'est non (pas de relation)
1 si c'est oui (relation)
N est une variable infini
Toujours 0,N a partir d'une double dépendance fonctionnel.

| min | Max |
| --- | --- |
| 0   | 1   |
| 0   | N   |
| 1   | 1   |
| 1   | N   |
Les tables de liaisons se feront uniquement avec des liaisons composé.
#MERISE #BDD #MCD
