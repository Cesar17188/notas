# Arquitectura orientada a eventos

https://nodejs.org/api/events.html#events_class_eventemitter

Uno de los paradigmas de programación en nodejs más populares es la arquitectura orientada a eventos, los eventos nos permiten manipular el código asincrono de una mejor manera. Respasemos algunos ejemplos de callback

Concepto **Error First Callback**: _cuando un callback tiene un error lo que vamos a enviar como primer párametro es el error_.

Usando **Callback** [[callback]] | [[callbacks node]]
```js
const asyncCallback = function (cb) {
  setTimeout(() => {
    if (Math.random() < 0.5) {
      // Concepto Error First Callback: 
      return cb(null, 'Hola mundo');
    } else {
      cb(new Error('Hello Error'));
    }
  }, 2000)
}

asyncCallback((err, msg) => {
  // Verificar si existe el error
  if (err) {
    console.log('Error', err);
  } else {
    console.log('mensage', msg);
  }
})
```

Usando **Promesas**: [[promesas]] | [[promesas node]]
```js
// resolve: se encarga de resolver la promesa
// reject: se encarga de enviar un error en caso de que algo suceda
const promise = new Promise((resolve, reject) => {
  setTimeout(() => {
    if (Math.random() < 0.5) {
      // Concepto Error First Callback: 
      // En lugar de retornar un callback podemos llamar a Resolve
      // Como resolve ya no es Callback y ya no es Error First Callback, 
      //ya no hay necesidad de pasar Objeto null
      resolve('Hola mundo');
    } else {
      reject(new Error('Hello Error'));
    }
  }, 2000)
});

// Lo bueno de las promesas es que se pueden encadenar  
// Encadenamos el mensage para que antes de mostrarlo, se muestre en UpperCase
promise.then(msg => msg.toUpperCase())
  .then(msg => console.log('message', msg))
  .catch(err => console.log('Error', err));
```
Aún hay una mejor manera de hacer estó, lo importante de las promesas es que esto se empieza a generar un código en cascada que es dificil de leer con el tiempo, ahora recientemente se puede usar [async await](https://developer.mozilla.org/es/docs/Web/JavaScript/Referencia/Operadores/await) que es una manera de escribir código asincrono que se vea sincrono.

Lo que requiere [async await](https://developer.mozilla.org/es/docs/Web/JavaScript/Referencia/Operadores/await) es que nuestra función devuelva una promesa, que es como una serie de **wrapper** que hacemos, en esté caso nosotros vamos a convertir esa promesa en una función:
[[async await]] | [[async await node]]

```js
const promiseFunction = () => new Promise((resolve, reject) => {
  setTimeout(() => {
    if (Math.random() < 0.5) {
      resolve('Hola mundo');
    } else {
      reject(new Error('Hello Error'));
    }
  }, 2000)
});

async function asyncAwait() {
  try {
    const msg = await promiseFunction();
    console.log('message', msg);
  } catch (error) {
    console.log('error', error);
  }
}

asyncAwait();
```

## Event Emiter
Hay una forma aún más poderosa de ejecutar el código anterior y es con la clase event-emitter. [EventEmitter](https://nodejs.org/dist/latest-v10.x/docs/api/events.html#events_class_eventemitter) no es exclusivo, podemos usar promesas y código asincrono, pero ya vamos a ver cuales son sus ventajas:

```js
// Creamos un Event Emitter
const EventEmitter = require('events');

// Podemos crear un logger propio
class Logger extends EventEmitter {
  // Método execute recibe un callback
  execute(cb) {
    console.log('Before');
    // Emitimos un Evento 
    this.emit('start');
    cb();
    // Emitimos otro evento
    this.emit('finish');
    console.log('Afther');
  }
}

const logger = new Logger();

// Cada vez que ocurra algún evento, hagá algo
logger.on('start', () => console.log('STARTING'));
// Podemos Suscribirnos al evento multiples veces sin niguna restricción 
logger.on('finish', () => console.log('Finishing'));

logger.on('finish', () => console.log("It's Done"));

// logger.execute(() => console.log("Hello World"));

/*
Algo muy importante es que si ejecutamos código asincrono, como un setTimeout,
el orden no va ha permanecer, porque como es código asincrono precisamente se va 
ha ejecutar despues de todas las emisiones, en ese caso la manera de controlarlo es
usando callbacks, si lo ejecutamos veremos que nuestro hello world se ejecuta despues,
porque queda de manera asincrona.
*/
logger.execute(() => setTimeout(() => console.log("Hello World"), 500));
```