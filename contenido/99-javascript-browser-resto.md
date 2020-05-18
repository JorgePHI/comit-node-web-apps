


**Ejemplo de pedido por POST enviando datos:**
```js
// Creamos el objeto
var xmlhttp = new XMLHttpRequest();

// Establecemos encabezado
xhttp.setRequestHeader("Content-type", "application/x-www-form-urlencoded");

// Armamos los valores que queremos enviar
const params = “nombres=Laura&apellidos=Acosta”

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