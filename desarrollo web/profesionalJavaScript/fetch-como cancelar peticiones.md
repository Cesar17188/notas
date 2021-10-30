# Fetch - Cómo cancelar peticiones

La peticiones AJAX permitieron en su tiempo hacer peticiones asíncronas al servidor sin tener que detener la carga de la página. Hoy en día se utiliza la función **fetch** para esto.

Con **fetch** tenemos algo llamado **AbortController** que nos permite enviar una señal a una petición en plena ejecución para detenerla.

## AbortController.abort ()

El método `abort()` de la la interfaz [`AbortController`](https://developer.mozilla.org/en-US/docs/Web/API/AbortController " AbortController representa un objeto controlador que le permite abortar una o más solicitudes DOM cuando lo desee."). Esta interfaz anula una solicitud DOM (por ejemplo, una solicitud Fetch) antes de que se haya completado. Esto puede abortar las [solicitudes de recuperación](https://developer.mozilla.org/en-US/docs/Web/API/WindowOrWorkerGlobalScope/fetch), el consumo de cualquier respuesta [`Body`](https://developer.mozilla.org/en-US/docs/Web/API/Body "La combinación del cuerpo de la API Fetch representa el cuerpo de la respuesta / solicitud, lo que le permite declarar cuál es su tipo de contenido y cómo debe manejarse.")y las transmisiones.

## [Sintaxis](https://developer.mozilla.org/en-US/docs/Web/API/AbortController/abort#Syntax)[](https://developer.mozilla.org/en-US/docs/Web/API/AbortController/abort#Syntax)

```js
controller.abort();
```

## Ejemplos

En el siguiente fragmento, nuestro objetivo es descargar un video usando la [API Fetch](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API) .

Primero creamos un controlador usando el [`AbortController()`](https://developer.mozilla.org/en-US/docs/Web/API/AbortController/AbortController "El constructor AbortController () crea una nueva instancia de objeto AbortController.")constructor, luego tomamos una referencia a su [`AbortSignal`](https://developer.mozilla.org/en-US/docs/Web/API/AbortSignal "La interfaz AbortSignal representa un objeto de señal que le permite comunicarse con una solicitud DOM (como Fetch) y abortarla si es necesario a través de un objeto AbortController.")objeto asociado usando la [`AbortController.signal`](https://developer.mozilla.org/en-US/docs/Web/API/AbortController/signal "La propiedad de solo lectura de la señal de la interfaz AbortController devuelve una instancia de objeto AbortSignal, que se puede utilizar para comunicarse con / cancelar una solicitud DOM según se desee.")propiedad.

Cuando se inicia la [solicitud de búsqueda](https://developer.mozilla.org/en-US/docs/Web/API/WindowOrWorkerGlobalScope/fetch) , pasamos el `AbortSignal`como una opción dentro del objeto de opciones de la solicitud (ver más `{signal}`abajo). Esto asocia la señal y el controlador con la solicitud de recuperación y nos permite abortarla llamando [`AbortController.abort()`](https://developer.mozilla.org/en-US/docs/Web/API/AbortController/abort "El método abort () de la interfaz AbortController cancela una solicitud DOM (por ejemplo, una solicitud Fetch) antes de que se haya completado.  Esto puede abortar las solicitudes de recuperación, el consumo de cualquier cuerpo de respuesta y las secuencias."), como se ve a continuación en el segundo detector de eventos.

```js
var controller = new AbortController();
var signal = controller.signal;

var downloadBtn = document.querySelector('.download');
var abortBtn = document.querySelector('.abort');

downloadBtn.addEventListener('click', fetchVideo);

abortBtn.addEventListener('click', function() {
  controller.abort();
  console.log('Download aborted');
});

function fetchVideo() {
  ...
  fetch(url, {signal}).then(function(response) {
    ...
  }).catch(function(e) {
    reports.textContent = 'Download error: ' + e.message;
  })
}
```

**Nota** : Cuando `abort()`se llama, la `fetch()`promesa se rechaza con un `AbortError`.

Puede encontrar un ejemplo de trabajo completo en GitHub: vea [abort-api](https://github.com/mdn/dom-examples/tree/master/abort-api) ( [vea también cómo se ejecuta en vivo](https://mdn.github.io/dom-examples/abort-api/) ).

![[Pasted image 20211012172026.png]]