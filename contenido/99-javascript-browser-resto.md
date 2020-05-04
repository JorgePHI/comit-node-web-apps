
### XMLHttpRequest / AJAX
* AJAX significa **Asynchronous Javascript and XML**
* Es una forma de mandar y recibir datos sin tener que recargar todo el documento
* Nos permite crear widgets dinámicos
* Utilizando AJAX podemos: 
  * Refrescar el contenido de una página sin recargarla
  * Pedir, recibir y enviar información a un servidor
* ECMASCript tiene un objeto llamado `XMLHttpRequest` que nos permite realizar llamados de AJAX
  * Este objeto tiene un método `open` que acepta varios parámetros para configurar el request que queremos realizar
  * Otro de sus métodos es `send` y permite ejecutar el request
  * Tambien tiene un event handler que se llama `onreadystatechange` que nos permite menejar todo el ciclo de vida del request hasta obtener un response
  * La propiedad `readyState` retorna un número informando el estado del objeto:
    * 0 si no se inicializó
    * 1 si está cargando
    * 2 si ya se envió el pedido
    * 3 si esta descargando la respuesta
    * 4 si terminó
  * Otra de sus propiedades es `status` y nos permite saber cual es el status de la respuesta
    * Si el `status` es 200 entonces significa que el pedido fue satisfactorio
  * Para obtener la respuesta utilizamos la propiedad `responseText`
  * Si el server retorna un objeto JSON lo podemos convertir en un objeto de ECMAScript y utilizarlo en nuestro código. Retorna null si no obtiene una respuesta
  

**Ejemplo De pedido:**
```js
var xmlhttp = new XMLHttpRequest();

xmlhttp.onreadystatechange = function() {
		if (xmlhttp.readyState == 4 && xmlhttp.status == 200) {
			console.log(xmlhttp.responseText);
		}
};

xmlhttp.open("GET", "url", true);

xmlhttp.send();
```

**Ejemplo de pedido por POST enviando datos:**
```js
// Creamos el objeto
var xmlhttp = new XMLHttpRequest();

// Establecemos encabezado
xhttp.setRequestHeader("Content-type", "application/x-www-form-urlencoded");

// Armamos los valores que queremos enviar
const params = “nombres=Nicolas&apellidos=Isnardi”

// Abrimos el request
xhttp.open("POST", "ajax_info.txt", true);

// Enviamos el request con los parámetros que necesitamos enviar
xhttp.send(params);
```

* Pueden leer más sobre AJAX en el [sitio de MDN](https://developer.mozilla.org/es/docs/AJAX)
* Pueden leer más sobre el objeto XMLHttpRequest  en el [sitio de MDN](https://developer.mozilla.org/es/docs/Web/API/XMLHttpRequest)

#### Prácticas
[Ejercicio 52](../ejercicios/consignas/js-browser/ej52.md)

* **Investigar** el nuevo método `fetch`
* Pueden leer más sobre este método en el [sitio de MDN](https://developer.mozilla.org/es/docs/Web/API/Fetch_API/Utilizando_Fetch)