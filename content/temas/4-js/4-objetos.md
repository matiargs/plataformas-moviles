---
title: "4.4: Objetos"
---

Los objetos son estructuras que podemos definir para agrupar valores correspondientes a una entidad.

Los objetos se componen de propiedades con sus respectivos valores. Estas propiedades proporcionan información sobre el objeto.

## Declaración y creación de Objetos

```js
let objetoAlumno = {
    nombre: "Juan",
    apellido: "Pérez",
    "edad": 18,
    "Un.Campo.Apodo": "Jota Pe",
};

let objetoVacio = {};
```

Acceder los valores dentro de los campos (atributos, claves) de un objeto

```js
// acceso por sintáxis de punto
alumno.edad;

// acceso por sintáxis de corchetes
alumno["edad"]
alumno["Un.Campo.Apodo"]

// el acceso por corchetes se puede usar para acceder a campos con nombres calculados
let campoImportante = "nombre";
alumno[campoImportante]
campoImportante = "apellido";
alumno[campoImportante]
```

Asignación de valores

```js
// sintaxis de punt
alumno.edad = 19;

// sintáxis de corchetes
alumno["edad"] = 18;
alumno["Un.Campo.Apodo"] = "Juampi";
```

Tipos de valores dentro de los campos de un objeto

```js
let objetoConDatosDeDistintosTipos = {
    unValorBooleano: true,
    unValorNumerico: 2,
    unValorString: "aaaaa",
    unValorLista: [],
    unValorObjeto: {},
}
```

