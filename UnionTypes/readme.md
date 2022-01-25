## Le type "union"

> Le **type union** permet de dire que notre variable (sortie de fonction, etc.) pourra **être d'un type ou d'un autre**, selon la définition que nous lui avons donné, et qu'elle ne sera **pas limité à un seul type**.

---

Imaginons une fonction qui combine deux valeurs entre elles et nous retourne le résultat.

```ts
function combine1(a: number, b: number) {
	return a + b;
}
```

Appelons notre fonction et voyons ce qu'elle nous donne.

```ts
const nbComb = combine1(2, 2);
console.log(nbComb); // Affiche: 4
```

Pas de surprise, **2 + 2 = 4**.

---

Cependant, nous avons utilisé des types **number** dans notre fonction.
<br> Que ce passerait-il si nous voulions combiner (concatener) des chaines de charactère (type **string**) ?

On pourrait écrire une autre fonction comme ceci:

```ts
function combine2(a: string, b: string) {
	return a + b;
}
```

Voyons le résultat:

```ts
const strComb = combine2("Hello ", "World");
console.log(strComb); // Affiche: 'Hello World'
```

Encore une fois, rien d'anormale.

---

Mais, aurait-il été possible d'avoir une seul fonction 'combine()' qui pourrait géré les différent types que l'on lui envoie ?
<br>**Oui !** La solution: les types **`union`**.

Voyez la fonction suivante:

```ts
function combine(a: number | string, b: number | string) {
	if (typeof a === "number" && typeof b === "number") {
		// Si nos deux arguments sont de type number, on fait une addition
		return a + b;
	}
	// Sinon, on fait un concaténation
	return a.toString() + b.toString();

	// Biensur, sans faire de if/else, cela fonctionnera.
	// Mais pour faire du code propre, et, surtout,
	// éviter que notre éditeur nous fasse la tête,
	// mieux vaut faire des vérifications.
}
```

Découpons, _un peu_, cette fonction et concentrons nous sur la première ligne :

A la création de notre fonction, vous pouvez remarquer
que le type que l'on assigne à nos paramètres est écrit de façon particulière:

> `number | string`

Ceci n'est autre que la manière d'écrire un type **union**.

Le symbole **`|`**, _et les types écrit de chaque côté de ce dernier_, nous permet
de dire que nos paramètres, variables, retours de fonction, etc.,
pourront être **soit d'un type, soit de l'autre**.

Et nous pouvons ainsi, selon nos besoin, enchainer plusieur types à la suite, comme ici:

> `number | string | boolean | etc...`

---

Voyons notre nouvelle fonction à l'oeuvre:

```ts
const nbComb = combine(5, 5); // Que des types number
console.log(nbComb); // Affiche: 10
```

```ts
const strComb = combine("Godbye ", "World"); // Que des types string
console.log(strComb); // Affiche: 'Goodbye World'
```

```ts
const someComb = combine(1, "2"); // Un 'number' et un 'string'
console.log(someComb); // Affiche: 12
```

Les résultats sont bon et notre éditeur de code est content.

En parlant d'éditeur, veuillez y observer le type que prend nos variables et nos sorties de fonction, quand l'on passe notre souris dessus.

---

Remerciement à **<a href="https://www.youtube.com/c/Academind">Academind</a>**.
