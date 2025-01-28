# Normalize CSS

``` CSS
	* {
		margin: 0;
		padding: 0;
	}
```
*D'autre normalize plus complet existe sur internet*
# Sélecteurs Hiérarchiques
## Voisins directs

``` CSS
	p + a {
		border: 2px solid blue;
		border-radius: 5px;
	}
```
## Tout les voisins

``` CSS
	p ~ ul {
		text-transform: uppercase;
	}
```

# Les sélecteurs descendants

```CSS
	p > ul {
		color: silver;
		text-decoration: underline;
	}
```

# Sélecteurs de types

```CSS
talbe{

}

input{

}
```

# Sélecteurs de classes

```CSS
.nom de la classe{

}
```

# LE BEM
*Block Element Modifier*

<span style="background:#d4b106">C'est une convention de nommage des classes qui permet de structuré notre CSS tout en prenant en compte la structure du HTML qui en découle.</span>

Par exemple pour une feuille CSS
```CSS
.menu {
}
.menu__affiche{

}
.menu__affiche--is-open{

}
```

le code html serait :
```HTML
<div class="menu">
	<div class="menu__affiche">Affiche 1</div>
	<div class="menu__affiche menu__affiche--is-open">Affiche 1</div>
	<div class="menu__affiche">Affiche 1</div>
</div>
```

# Sélecteurs d'attributs

Permet d'appliquer un style en fonction d'un attribut présent dans une balise HTML

```CSS
a[nom_attribut]{

}
```

```CSS
a[nom_attribut = valeur]{

}
```

# Pseudos classes

nom-élément::pseudo classe :
```CSS
p::first-letter {
text-transform:uppercase;
}
```
#CSS #normalize #sélecteurs #VoisinsDirect #Voisins #BEM
