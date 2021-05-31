# Async Await

La declaración de función `**async**` define una _función asíncrona_, la cual devuelve un objeto [`AsyncFunction`](https://developer.mozilla.org/es/docs/Web/JavaScript/Reference/Global_Objects/AsyncFunction).

Es posible definir también funciones asíncronas a través de una [expresión de función async](https://developer.mozilla.org/es/docs/Web/JavaScript/Reference/Operators/async_function).

```js
function resolveAfter2Seconds() {
  return new Promise(resolve => {
    setTimeout(() => {
      resolve('resolved');
    }, 2000);
  });
}

async function asyncCall() {
  console.log('calling');
  const result = await resolveAfter2Seconds();
  console.log(result);
  // expected output: "resolved"
}

asyncCall();
```

## sintaxis

async function _name_(\[_param_\[, _param_\[, ... _param_\]\]\]) {
   _statements_
}

### Parámetros

`name`

El nombre de la función.

`param`

El nombre de un argumento que se debe pasar a la función.

`statements`

Las declaraciones que conforman el cuerpo de la función.

### Valor de retorno

Un objeto [`AsyncFunction`](https://developer.mozilla.org/es/docs/Web/JavaScript/Reference/Global_Objects/AsyncFunction), que representa una función asíncrona que ejecuta el código contenido dentro de la función.

## [Descripción]

Cuando se llama a una función `async`, esta devuelve un elemento [`Promise`](https://developer.mozilla.org/es/docs/Web/JavaScript/Reference/Global_Objects/Promise). Cuando la función `async` devuelve un valor, `Promise` se resolverá con el valor devuelto. Si la función `async` genera una excepción o algún valor, `Promise` se rechazará con el valor generado.

Una función `async` puede contener una expresión [`await`](https://developer.mozilla.org/es/docs/Web/JavaScript/Reference/Operators/await), la cual pausa la ejecución de la función asíncrona y espera la resolución de la `Promise` pasada y, a continuación, reanuda la ejecución de la función `async` y devuelve el valor resuelto.

La finalidad de las funciones `async`/`await` es simplificar el comportamiento del uso síncrono de promesas y realizar algún comportamiento específico en un grupo de `Promises`. Del mismo modo que las `Promises` son semejantes a las devoluciones de llamadas estructuradas, `async`/`await` se asemejan a una combinación de generadores y promesas.
Ejemplo
```js
function resolveAfter2Seconds(x) {
  return new Promise(resolve => {
    setTimeout(() => {
      resolve(x);
    }, 2000);
  });
}


async function add1(x) {
  const a = await resolveAfter2Seconds(20);
  const b = await resolveAfter2Seconds(30);
  return x + a + b;
}

add1(10).then(v => {
  console.log(v);  // prints 60 after 4 seconds.
});


async function add2(x) {
  const p_a = resolveAfter2Seconds(20);
  const p_b = resolveAfter2Seconds(30);
  return x + await p_a + await p_b;
}

add2(10).then(v => {
  console.log(v);  // prints 60 after 2 seconds.
});
```