# JavaScript en el navegador 

## Ejecutar JavaScript
* En el browser (navegador) podemos ejecutar ECMAScript de la siguiente forma:
  * Por consola (como ya lo vimos)
  * Utilizando la etiqueta script para definir un bloque de JS dentro del HTML
  * Incluir archivos externos de script

### Correr script en la etiqueta script
* HTML tiene una etiqueta llamada script que nos permite embeber código ECMAScript
* Esta etiqueta se puede poner tanto en el `head` como en el `body`
* El lugar donde pongamos este bloque indica en qué momento se ejecute (el HTML se procesa en orden)

**Ejemplos:**
```html
<head>
  <script>
    // Acá puedo escribir todo el código JavaScript que quiero
    console.log('Bienvenidxs al Browser (desde el head)');
  </script>
</head>
```

* Lo mismo puede ir en el body:
```html
<body>
  <script>
    console.log('Bienvenidxs al Browser (desde el body)');
  </script>
</body>
```

#### Prácticas
[Ejercicio 1](../ejercicios/consignas/js-browser/ej1.md)

### Incluir un archivo externo
* Podemos incluir un archivo externo con código ECMAScript de forma similar como hacemos con CSS
* Utilizamos la etiqueta `script` y el atributo `src` con la ruta del documento que queremos vincular
* Esto también puede ir en el `head` o en el `body`, con el mismo criterio.

**Ejemplo:**
```html
<head>
  <script src="script.js"></script>
</head>
```

```js
// archivo script.js
console.log('Bienvenido al browser')
```

* Al utilizar la etiqueta `script` para cargar un docuemento externo el browser bloquea el resto del renderizado del documento hasta que se termine de descargar y ejecutar el código solicitado
* Una vieja práctica es poner la etiqueta `script` antes del cierre del `body`
* Los browsers nuevos soportan dos atributos que nos permiten decirle al browser de que manera tiene que descargar el documento y cuando ejecutarlo
* Estas etiquetas se llaman `async` y `defer`

**Ejemplo:**
```html
<head>
  <script src="script.js" async defer></script>
</head>
```
* Para saber más sobre la carga de documentos y el browser les recomendamos leer los siguientes posts
  * [Agregar interactividad con JavaScript](https://developers.google.com/web/fundamentals/performance/critical-rendering-path/adding-interactivity-with-javascript)
  * [async vs defer (inglés)](http://www.growingwiththeweb.com/2014/02/async-vs-defer-attributes.html)
  * [async vs defer - Video (inglés)](https://www.youtube.com/watch?v=cCrfL84DkEk)

#### Prácticas
[Ejercicio 2](../ejercicios/consignas/js-browser/ej2.md)

## Interactuar con lxs usuarixs
* Los browsers tienen un objeto llamado **window** que representa la ventana del navegador
* Este objeto tiene 3 métodos que nos permiten interactuar con el usuario: alert, prompt y confirm
* Estos métodos son muy comunes por lo cual los browsers tienen ya una referencia para poder utilizarlos como funciones
* Todas estas funcionalidades bloquean el documento hasta que se resuelvan

**Ejemplo:**
```js
// Podemos llamarlos como métodos de windows:
window.alert();
window.prompt();
window.confirm();

// o como funciones
alert();
prompt();
confirm();
```

### Alert
* El método/función `alert` muestra un mensaje en pantalla al usuario
* Acepta como parámetro el mensaje que le queremos mostrar al usuario

**Ejemplo:**
```js
window.alert('Hola, estoy en el browser');
alert('Hola, estoy en el browser');
```

#### Prácticas
[Ejercicio 3](../ejercicios/consignas/js-browser/ej3.md)

### Prompt
* El método/función `prompt` nos permite pedirle un dato al usuario
* Este método acepta un mensaje que será mostrado al usuario
* Retorna un `string` con el valor ingresado por el usuario

**Ejemplo:**
```js
let dni = window.prompt('Ingrese su número de DNI');
dni = prompt('Ingrese su número de DNI');
```

#### Prácticas
[Ejercicio 4](../ejercicios/consignas/js-browser/ej4.md)
[Ejercicio 5](../ejercicios/consignas/js-browser/ej5.md)

### Confirm
* El método/función `confirm` nos permite pedirle al usuario que acepte o cancele una acción
* Este método acepta un mensaje que será mostrado al usuario
* Retorna un valor `boolean` true si el usuario confirma la acción y false si la cancela

**Ejemplo:**
```js
window.confirm('Es Ud. mayor de edad?');
confirm('Es Ud. mayor de edad?');
```

#### Prácticas
[Ejercicio 6](../ejercicios/consignas/js-browser/ej6.md)
[Ejercicio 7](../ejercicios/consignas/js-browser/ej7.md)
[Ejercicio 8](../ejercicios/consignas/js-browser/ej8.md)

## Location
* Existe un objeto llamado `location` que representa la URL del documento
* Dado que es un objeto bastante común podemos accederlo utilizado sólo su nombre

**Ejemplo:**
```js
// Como propiedad del objeto window
window.location

// Como objeto
location
```

* Por medio de sus propiedades podemos acceder a las distintas partes de la URL
  * **href**: muestra la URL como string
  * **protocol**: muestra el protocolo. ej: http, https
  * **host**: retorna un string con el nombre del host y el número de puerto en caso de que tenga uno
  * **hostname**: muestra sólo el nombre del host
  * **port**: el puerto del documento
  * **pathname**: muestra el path del recurso
  * **search**: muestra los parámetros del query string (las variables que pasamos por GET)
  * **hash**: muestra el contenido de hash (lo que tenga numeral #)

**Ejemplo:**
```js
location.href;
location.protocol;
location.host;
location.hostname;
location.port;
location.pathname;
location.search;
location.hash;
```

* Este objeto también nos permite navegar a otro documento estableciendo un valor a la propiedad `href`
* Otra opción es directamente asignar una url como string al objeto location

**Ejemplo:**
```js
location.href = 'http://google.com';
// o
location = 'http://google.com';
```

#### Prácticas
[Ejercicio 9](../ejercicios/consignas/js-browser/ej9.md)


## Timers (temporizadores)
* Entre las APIs del navegador (funciones que provee el browser) existen las funciones `setTimeout` y `setInterval` que nos permiten retrasar o repetir por intervalos la ejecución de un código que elegimos.

### setTimeout / clearTimeout
* Esta función se utiliza cuando queremos que nuestro código se ejecute **una sola vez** en un tiempo establecido
* Acepta como primer parámetro la función que queremos que se ejecuta
* El segundo parámetro acepta un valor numérico con la cantidad de milisegundos que queremos esperar para ejecutar la función pasada como primer parámetro

**Ejemplo:**
```js
const saludar = function() {
  console.log('hola');
}

setTimeout(saludar, 5000);
```

* En este ejemplo establecemos que queremos ejecutar la función saludar dentro de 5 segundos una sola vez
* Si queremos podemos no utilizar la variable saludar y pasar la función anónima directamente

**Ejemplo:**
```js
setTimeout(function() {
  console.log('hola');
}, 5000);
```

* Esta función retorna un valor numérico que es el ID
* Podemos cortar la ejecución de este `setTimeout` utilizando la función `clearTimeout`
* Esta función espera un valor numérico como parámetro

**Ejemplo:**
```js
var idTimeOut = setTimeout(function() {
  console.log('hola');
}, 5000);

// Cortamos la ejecución
clearTimeout(idTimeOut)
```

* En algunos casos podemos necesitar tener que pasarle parámetros a la función que se va a ejecutar
* Esta función acepta todos los parámetros que queremos de la segunda posición en adelante y los pasa como parámetros de la función que se ejecuta

**Ejemplo:**
```js
const saludar = function(nombre, apodo) {
  console.log(`hola ${nombre} ${apodo}`);
}

setTimeout(saludar, 5000, 'Marta', 'Martita');
```

* En este ejemplo vemos que podemos pasarle más de un parámetro a la función saludar desde la función `setTimeout`

#### Prácticas
[Ejercicio 10](../ejercicios/consignas/js-browser/ej10.md)
[Ejercicio 11](../ejercicios/consignas/js-browser/ej11.md)

### setInterval / clearInterval
* Existe otra función que se llama `setInterval` que nos permite ejecutar una función múltiples veces cada una cantidad establecida de tiempo
* Es similar a `setTimeout` con la diferencia que se ejecuta múltiples veces
* Retorna un valor numérico que se utiliza como ID

**Ejemplo:**
```js
const saludar = function() {
  console.log('hola');
}

const id = setInterval(saludar, 1000);
```

* En este caso se va a llamar a la función **saludar** cada 1 segundo
* Este llamado se hace hasta que cortemos la ejecución
* Podemos utilizar la función `clearInterval` para anular el llamado de `setInterval`

**Ejemplo:**
```js
const saludar = function() {
  console.log('hola');
}

const id = setInterval(saludar, 1000);

// se corta la ejecución
clearInterval(id);
```

* También podemos pasarle parámetros de la misma forma que a `setTimeout`

**Ejemplo:**
```js
const saludar = function(nombre, apodo) {
  console.log(`hola ${nombre} ${apodo}`);
}

setInterval(saludar, 1000, 'Marta', 'Martita');
```

#### Prácticas
[Ejercicio 12](../ejercicios/consignas/js-browser/ej12.md)
[Ejercicio 13](../ejercicios/consignas/js-browser/ej13.md)

## Trabajar con elementos

### Estructura de un elemento HTML
* En esta sección es importante hacer un repaso de como está compuesto un elemento HTML

![elemento](../assets/js-browser/elemento.png)

* Todos los elementos tienen las siguientes partes:
  * **Etiqueta de Apertura:** es la declaración de que comienza un elemento
    * **nombre:** especifica que tipo de elemento es, puede ser un párrafo (`p`), título (`h1 a h6`), hiperínculo (`a`) entre otros.
    * **atributos** los atributos de la etiqueta nos permiten describirlos mejor o agregarle alguna funcionalidad. La estructura es siempre la misma y es **nombredeatributo="valor del atributo"**. Algunos atributos son `id`, `class`, `href`, `src`, etc
  * **contenido:** el contenido de un elemento es todo lo que encuentra entre la etiqueta de apertura y la de cierre. Puede ser texto u otros elementos
  * **Etiqueta de cierre:** el browser necesita la etiqueta de cierre para poder saber donde termina un elemento

* Por medio de ECMAScript vamos a poder crear, insertar, modificar y borrar elementos como también modificar sus atributos, valores y contenido utilizando el `DOM`

### DOM
* El document object model, `DOM`, proporciona una representación estructural de un documento HTML, permitiendo la manipulación de su contenido y su presentación visual utilizando JavaScript.
* Esto significa que como programadores tenemos acceso a objetos que tienen propiedades, métodos y eventos disponibles para crear y manipular elementos en un documento web.
* En el DOM encontramos los siguientes tipos de datos:
  * **document:** representa el documento en si mismo. Es el nodo principal.
  * **element:** representa un nodo elemento
  * **attribute:** representan los atributos de los nodos / elementos
  * **nodeList:** es un array con nodos. Sus elementos se pueden acceder por medio items o indice del array.

![DOM](../assets/js-browser/dom.png)

* Podemos leer más sobre el `DOM` en el [sitio del MDN](https://developer.mozilla.org/es/docs/DOM)
