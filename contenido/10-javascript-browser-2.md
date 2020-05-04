# AJAX

Antes de utilizar AJAX para requerir y recibir datos por HTTP, vamos a ver el formato de datos que vamos a utilizar: **JSON**.

## JSON

* JSON significa **JavaScript Object Notation** y es un formato para intercambiar datos de forma simple
* Es fácil de leer y escribir
* En su estructura es muy parecido a un objeto literal de ECMAScript con algunas diferencias
* Los nombres de las propiedades se escriben entre comillas dobles y los valores de string también

**Ejemplo:**
```js
var objetoEnFormatoJSON = { 
  "atributo": "valor", 
  "atributo1": 1, 
  "atributo2": [], 
  "atributo3": null, 
  "atributo4": false
};
```

* ECMAScript tiene un objeto `JSON` que tiene los métodos `stringify()` y `parse()`
  * **stringify:** permite pasar un objeto o valor de javascript al formato JSON
  * **parse:** toma una cadena de caracteres en formato JSON y lo transforma en un objeto o valor de ECMASCript
* Gracias a estos 2 métodos se puede utilizar el formato JSON para intercambiar datos en formato de texto
* Teniendo una variable en formato JSON se accede a sus atributos de la siguiente manera:

**Ejemplo:**
```js
// Ejemplo stringify
const usuarix = {
  username: 'pepe',
  password: '12345',
  email: 'pepe@gmail.com',
  hijxs: ['maria', 'juan']
}

const usuarixJSON = JSON.stringify(usuarix); // retorna un JSON del objeto usuarix
console.log(usuarixJSON);
/*
{
  "username":"pepe",
  "password":"12345",
  "email":"pepe@gmail.com",
  "hijxs":["maria","juan"]
}
*/

// Ejemplo parse

const usuarixDeJSONaJS = JSON.parse(usuarixJSON); // retorna un objeto de ECMAScript
console.log(usuarixDeJSONaJS);

/*
{
  username: "pepe", 
  password: "12345", 
  email: "pepe@gmail.com", 
  hijxs: ["maria", "juan"]
}
*/
```

* En este ejemplo podemos ver que de forma muy fácil podemos transformar un objeto de ECMAScript a JSON y viceversa

#### Prácticas
[Ejercicio 51](../ejercicios/consignas/js-browser/ej51.md)
