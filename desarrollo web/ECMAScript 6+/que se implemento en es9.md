# ¿Qué se implemento en es9?

## reposo de objetos y propiedades de propagación

Permite desagregar partes de un objeto o incremetar partes de un objeto en otro objeto mediante el código

```js
/\*reposo de objetos y propiedades de propagación

lo que puede extraer las propiedades de un objeto que 

aun no se ha construido\*/

  

const obj ={

 name: 'Cesar',

 age: 28,

 country: 'EC'

};

  

let { country, ...all} = obj;

console.log(all);

  

// Unión de objetos

const obj = {

 name: 'Cesar',

 age: 28

}

const obj1 = {

 ...obj,

 coutnry: 'EC'

}

console.log(obj1);
```

# Promise.prototype.finally()

El método `**finally()**` devuelve una [`Promise`](https://developer.mozilla.org/es/docs/Web/JavaScript/Reference/Global_Objects/Promise). Cuando la promesa se resuelve, sea exitosa o rechazada, la función de callback específicada será ejecutada. Esto ofrece una forma de ejecutar código sin importar como se haya resuelto la promesa.

Esto ayuda a evitar tener código duplicado tanto en el [`then()`](https://developer.mozilla.org/es/docs/Web/JavaScript/Reference/Global_Objects/Promise/then) como en el [`catch()`](https://developer.mozilla.org/es/docs/Web/JavaScript/Reference/Global_Objects/Promise/catch).

## [Sintaxis]

p.finally(alFinalizar);

p.finally(function() {
   // finalizada (exitosa o rechazada)
});

### [Parámetros]

`alFinalizar`

Una [`Function`](https://developer.mozilla.org/es/docs/Web/JavaScript/Reference/Global_Objects/Function) llamada cuando la `Promise` se resuelve con éxito o falla.

### [Valor de retorno]

Devuelve una [`Promise`](https://developer.mozilla.org/es/docs/Web/JavaScript/Reference/Global_Objects/Promise) cuyo `finally` fue fijado a la función específicada en `alFinalizar`.

## [Descripción]

El método `finally()` puede ser de utilidad si quieres hacer algún proceso o limpieza una vez que la promesa termina, sin importar su resultado.

Utilizar `finally()` es muy similar a llamar `.then(onFinally, onFinally)`, sin embargo tiene algunas diferencias:

-   Cuando usamos una función `inline`, se la puede pasar una sola vez, en vez de estar forzado a declararla dos veces, o guardarla en una variable.
-   Un callback `finally` no recibe ningún argumento, ya que no hay una manera fehaciente de determinar si la promesa fue exitosa o fallida. Este caso de uso es precisamente para cuando _no nos importa_ la razón por la que falló o el valor al que resuelve, y no hay necesidad de proveerlos.
-   A diferencia de `Promise.resolve(2).then(() => {}, () => {})` (que va a resolver a `undefined`), `Promise.resolve(2).finally(() => {})` resolverá con un `2`.
-   Del mismo modo, a diferencia de `Promise.reject(3).then(() => {}, () => {})` (que resolverá con `undefined`), `Promise.reject(3).finally(() => {})` será rechazada con un `3`.

**Nota:** Un `throw` (o retornar una promesa rechazada) en el callback `finally` va a rechazar la nueva promesa con la razón de rechazo especificada al llamar `throw()`.

## [Ejemplos]

```
let isLoading = true;

fetch(myRequest).then(function(response) {
    var contentType = response.headers.get("content-type");
    if(contentType && contentType.includes("application/json")) {
      return response.json();
    }
    throw new TypeError("Oops, no hemos obtenido un JSON!");
  })
  .then(function(json) { /* procesar el JSON */ })
  .catch(function(error) { console.log(error); /* esta línea podría arrojar error, e.g. cuando console = {} */ })
  .finally(function() { isLoading = false; });
```

# Expresiones regulares

Las expresiones regulares son patrones que se utilizan para hacer coincidir combinaciones de caracteres en cadenas. En JavaScript, las expresiones regulares también son objetos. Estos patrones se utilizan con los métodos [`exec()`](https://developer.mozilla.org/es/docs/Web/JavaScript/Reference/Global_Objects/RegExp/exec) y [`test()`](https://developer.mozilla.org/es/docs/Web/JavaScript/Reference/Global_Objects/RegExp/test) de [`RegExp`](https://developer.mozilla.org/es/docs/Web/JavaScript/Reference/Global_Objects/RegExp), y con [`match()`](https://developer.mozilla.org/es/docs/Web/JavaScript/Reference/Global_Objects/String/match), [`matchAll()`](https://developer.mozilla.org/es/docs/Web/JavaScript/Reference/Global_Objects/String/matchAll), [`replace()`](https://developer.mozilla.org/es/docs/Web/JavaScript/Reference/Global_Objects/String/replace), [`replaceAll()` (en-US)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/replaceAll "Currently only available in English (US)"), [`search()`](https://developer.mozilla.org/es/docs/Web/JavaScript/Reference/Global_Objects/String/search) y [`split()`](https://developer.mozilla.org/es/docs/Web/JavaScript/Reference/Global_Objects/String/split) métodos de [`String`](https://developer.mozilla.org/es/docs/Web/JavaScript/Reference/Global_Objects/String). Este capítulo describe las expresiones regulares de JavaScript.

ejemplo
```js
const regexData = /(\[0-9\]{4})\-(\[0-9\]{2})\-(\[0-9\]{2})/;

const match = regexData.exec("2018-04-20");

const year = match\[1\];

const month = match\[2\];

const day = match\[3\];

console.log(year, month, day);
```