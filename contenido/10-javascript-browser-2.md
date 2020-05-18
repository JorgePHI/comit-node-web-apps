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

## XMLHttpRequest / AJAX
* AJAX significa **Asynchronous Javascript and XML**.
* Es una forma de mandar y recibir datos sin tener que recargar la página.
* Utilizando AJAX podemos: 
  * Refrescar el contenido de una página sin recargarla, alterando dinámicamente su contenido (DOM)
  * Recibir y enviar información a un servidor
* ECMASCript tiene un objeto llamado `XMLHttpRequest` que nos permite realizar llamados de AJAX
  * Su nombre, igual que la sigla AJAX, incluye "XML" porque es el formato en el que originalmente se manejaban los datos. Nosotrxs vamos a usar JSON.
  * Para disparar el pedido (request) vamos a utilizar dos métodos del objeto XMLHttpRequest: `open` para indicar la URL de destino y qué método HTTP utilizar (GET, POST, PUT, DELETE, etc.) y `send` que efectúa el request.
  * Para recibir la respuesta vamos a usar algún listener con un callback asociado a alguno de los eventos de retorno.
  * Uno de esos eventos es el `readystatechange` que nos permite manejar todo el ciclo de vida del request hasta obtener un response. Se dispara con cada cambio del "ready state", reflejado en la propiedad `readyState`, que contiene un número informando el estado del objeto:
    * 0 si no se inicializó
    * 1 si está cargando
    * 2 si ya se envió el pedido
    * 3 si esta descargando la respuesta
    * 4 si terminó
  * Si no necesitamos monitorear cada uno de esoso pasos, podemos agregar el listener al evento `load`, que se va a disparar cuando haya terminado de procesarse la respuesta.
  * Otra propiedad del objeto XMLHttpRequest es `status` y nos permite saber cual es el status code de la respuesta. Es un dato que tenemos que evaluar para saber si se pudo ejecutar correctamente la petición o no.
  * Si el `status` es 200 entonces significa que el pedido fue satisfactorio. Algunos status codes típicos de errores son 400, 401, 403, 404 y 500. Podemos encontrar una lista completa y detallada en https://developer.mozilla.org/es/docs/Web/HTTP/Status.
  * Para obtener el contenido de la respuesta utilizamos la propiedad `responseText`.
  * Si el retorno está en formato JSON, lo podemos convertir en un objeto de ECMAScript y utilizarlo en nuestro código. Si no hubo respuesta, será `null`.


**Ejemplo de request:**
```js
var xmlhttp = new XMLHttpRequest();

xmlhttp.addEventListener("readystatechange", function() {
  if (this.readyState == 4 && this.status == 200) {
    console.log(this.responseText);
  }
};

xmlhttp.open("GET", "url", true);

xmlhttp.send();
```

El mismo ejemplo pero con el evento "load"
```js
var xmlhttp = new XMLHttpRequest();

xmlhttp.addEventListener("load", function() {
  if (this.status == 200) {
    console.log(this.responseText);
  }
};

xmlhttp.open("GET", "url", true);

xmlhttp.send();
```
