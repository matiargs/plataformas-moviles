---
title: "4.3: Listas"
---

Vimos el tipo de datos lista (array) en JavaScript, y algunos ejemplos de código.

## Definir listas

```js
let listaDeNumeros = [1, 23, 56, 1234];
let listaDeStrings = ['a', 'abc'];
let listaDeFloats = [1.23, 2.34, 3.45];
let listaDeBooleanos = [false, false, true];
let listaDeMultiplesTipos = [1, 'a', 1.23, false];
let listaVacia = [];
```

## Operaciones sobre listas

Acceder a Valores de una lista

```js
// acceder a un elemento determinado
let primerElemento = listaDeNumeros[0];

// conocer la longitud de una lista
let cantidadElementos = listaDeNumeros.length

// acceder a último elemento?
```

### Agregar elementos

Se pueden usar los métodos `push()` y `unshift()` de listas.

```js
let nuevoValor = 33;

// agregar elemento al final de la lista
listaDeNumeros.push(nuevoValor);

// agregar elemento al inicio de la lista
listaDeNumeros.unshift(nuevoValor);
```

> Info: Existe otra forma de agregar o eliminar elementos usando posiciones, pero puede traer problemas:
> 
> ```js
> // agegar un nuevo elemento al final de la lista
> let nuevoValor = 42;
> let nuevaPosicion = listaDeNumeros.length;
> listaDeNumeros[nuevaPosicion] = nuevoValor;
> console.log("lista con nuevo valor: ", listaDeNumeros);
> ```
>
> Esta opción puede traer complicaciones, dejando listas inconsistentes al agregar o eliminar elementos
>
> ```js
> // agregar otro elemento
> listaDeNumeros[99] = nuevoValor;
> console.log("lista con nuevo valor en posición 99", listaDeNumeros);
>
> // eliminar elemento de una lista
> delete listaDeNumeros[99];
> console.log("lista con nuevo valor eliminado", listaDeNumeros);
>
> // en este punto la longitud de la lista quedó inconsistente
> console.log(listaDeNumeros.length);
> ```

### Quitar elementos

Se pueden usar los métodos `pop()` y `shift()` de listas para eliminar elementos.

```js
// remover de la lista el ultimo elemento
listaDeNumeros.pop();

// remover de la lista y obtener el ultimo elemento
let ultimoNumero = listaDeNumeros.pop();


// remover de la lista el primer elemento
listaDeNumeros.shift();

// remover de la lista y obtener el primer elemento
let primerNumero = listaDeNumeros.shift();
```


## Recorridos sobre Listas

Calcular la suma de todos los valores de una lista de números

```js
// calcular la suma total de listaDeNumeros
let sumaTotal = 0;
for(i = 0; i < listaDeNumeros.length; i++) {
    console.log("Posición: ", i);
    console.log("Valor en posición: ", listaDeNumeros[i]);
    sumaTotal = sumaTotal + listaDeNumeros[i];
    console.log("Suma hasta el momento: ", sumaTotal);
}
console.log("Suma total: ", sumaTotal);

// calcular la suma total de listaDeNumeros (otra versión)
let sumaTotalv2 = 0;
listaDeNumeros.forEach((e) => {sumaTotalv2 += e})
console.log("Suma total (v2): ", sumaTotalv2);
```

Multiplicar todos los valores

```js
// multiplicar todos los numeros por 5
let listaPor5 = [];
for (let i = 0; i < listaDeNumeros.length; i++) {
    // accedo al valor en posición actual y lo multiplico por 5
    let valorActual = listaDeNumeros[i];
    let resultadoPosicionActual = valorActual * 5;
    
    // modifico el valor en la lista
    listaPor5[i] = resultadoPosicionActual; 
}
console.log("lista resultado: ", listaPor5);

// multiplicar por 5
let listaPor5opcion2 = listaDeNumeros.map((e) => {return e * 5});
console.log("lista resultado v2: ", listaPor5opcion2);
```

## Filtrar Listas

Se puede usar el método `filter()` filtrar los elementos de una lista. La función de filtro que recibe `filter()` debe devolver `true` para que el elemento permanezca en la lista resultante y `false` para que sea eliminado de la lista resultante.

```js
let listaDePreposiciones = ['a', 'ante', 'bajo', 'cabe', 'con', 'contra', 'de', 'desde', 'durante', 'en', 'entre', 'hacia', 'hasta', 'mediante', 'para', 'por', 'según', 'sin', 'so', 'sobre', 'tras', 'versus', 'vía'];

// me quedo con las palabras de al menos 3 letras de largo
let listaFiltrada = listaDePreposiciones.filter((elementoActual) => {
    return elementoActual.length > 3;
})
console.log("lista de preposiciones filtrada", listaFiltrada)
console.log("lista de preposiciones original", listaDePreposiciones)
```

## Ordenar Listas

Se puede usar el método `sort()` de listas para ordenarlas.

```js
let listaDesordenada = [4,6,2,1,9];
let listaOrdenada = listaDesordenada.sort();

console.log("lista ordenada", listaOrdenada)
```

Al método [`.sort()`](https://developer.mozilla.org/es/docs/Web/JavaScript/Reference/Global_Objects/Array/sort) se le puede pasar como parámetro una función que defina el criterio por el que queremos ordenar la lista. Esta funcion "criterioDeOrdenamiento" recibe 2 elementos de la lista, y devuelve como resultado un número para decidir cual de los 2 elementos debe aparecer antes en la lista.

- Si devuelve un número negativo es que los elementos tienen que intercambiar posiciones.
- Si devuelve un numero positivo es para que los elementos mantengan su posición en la lista.

Con strings la comparación se puede hacer con [`localeCompare()`](https://developer.mozilla.org/es/docs/Web/JavaScript/Reference/Global_Objects/String/localeCompare)

## Existencia de elemento en lista

Podemos necesitar averiguar si un elemento es parte de la lista. Para eso debemos recorrer la lista y consultar cada elemento (hasta encontrar el elemento buscado).

```js
let listaDeNombres = ["Mateo", "Sofía", "Benjamín", "Valentina", "Thiago"];

function existeElementoEnLista(elemento, lista) {
	let encontrado = false;
	// queremos saber si elemento está en lista
	for(let i = 0; i < lista.length; i++) {
		// accedemos a valor en posicion i
		let valorActual = lista[i];

		// si es el que buscamos
		if (valorActual == elemento) {
			encontrado = true;
		}
	}
	return encontrado;
}

console.log("Existe 'Martina' en lista?", existeElementoEnLista("Martina", listaDeNombres));

// Otra opción para consultar existencia de elemento en lista
console.log("Existe 'Lautaro' en lista?", listaDeNombres.includes("Lautaro"));
```

---

> Comentario extra: Para intercambiar 2 posiciones de una lista es necesario usar una letiable temporal
>
>     let temporal = nuevaLista(0);
>     nuevaLista[0] = nuevaLista[1];
>     nuevaLista[1] = temporal;

## Listas dentro de listas

Se pueden definir listas dentro de otras listas

```js
let listaAnidada = [ 1, 2, 3, [7, 8, 9], 4, 5, 6 ]
listaAnidada[3][1] // accedo al 8
```

## Otra Forma de pensar Operaciones

Vimos los conceptos de los métodos:

- `Array.filter()`
- `Array.map()`
- `Array.reduce()`
- `Array.sort()`

También vimos que se puede seguir usando el `for(;;)` de toda la vida, y existe una alternativa `Array.foreach()`.
