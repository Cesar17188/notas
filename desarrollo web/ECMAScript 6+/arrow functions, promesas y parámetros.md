# Arrow functions, promesas y parámetros

# Funciones Flecha (Arrow functions)

Una **expresión de función flecha** es una alternativa compacta a una `expresión de función` tradicional, pero es limitada y no se puede utilizar en todas las situaciones.

**Diferencias y limitaciones:**

-   No tiene sus propios enlaces a `this` o `super` y no se debe usar como [métodos](https://developer.mozilla.org/es/docs/Glossary/Method).
-   No tiene `argumentos` o palabras clave `new.target`.
-   No apta para los métodos `call`, `apply` y `bind`, que generalmente se basan en establecer un [ámbito o alcance](https://developer.mozilla.org/es/docs/Glossary/Scope)
-   No se puede utilizar como [constructor](https://developer.mozilla.org/es/docs/Glossary/Constructor).
-   No se puede utilizar `yield` dentro de su cuerpo.

```js
const materials = [
  'Hydrogen',
  'Helium',
  'Lithium',
  'Beryllium'
];

console.log(materials.map(material => material.length));
// expected output: Array [8, 6, 7, 9]
```

### [Comparación de funciones tradicionales con funciones flecha](https://developer.mozilla.org/es/docs/Web/JavaScript/Reference/Functions/Arrow_functions#comparaci%C3%B3n_de_funciones_tradicionales_con_funciones_flecha "Permalink to Comparación de funciones tradicionales con funciones flecha")

Observa, paso a paso, la descomposición de una "función tradicional" hasta la "función flecha" más simple:  
**Nota**: Cada paso a lo largo del camino es una "función flecha" válida

```js
// Función tradicional
function (a){
  return a + 100;
}

// Desglose de la función flecha

// 1. Elimina la palabra "function" y coloca la flecha entre el argumento y el corchete de apertura.
(a) => {
  return a + 100;
}

// 2. Quita los corchetes del cuerpo y la palabra "return" — el return está implícito.
(a) => a + 100;

// 3. Suprime los paréntesis de los argumentos
a => a + 100;
```

### [Sintaxis básica](https://developer.mozilla.org/es/docs/Web/JavaScript/Reference/Functions/Arrow_functions#sintaxis_b%C3%A1sica "Permalink to Sintaxis básica")

Un parámetro. Con una expresión simple no se necesita `return`:

```js
param => expression
```

Varios parámetros requieren paréntesis. Con una expresión simple no se necesita `return`:

```js
(param1, paramN) => expression
```

Las declaraciones de varias líneas requieren corchetes y `return`:

```js
param => {
  let a = 1;
  return a + b;
}
```

Varios parámetros requieren paréntesis. Las declaraciones de varias líneas requieren corchetes y `return`:

```js
(param1, paramN) => {
   let a = 1;
   return a + b;
}
```

### [Sintaxis avanzada](https://developer.mozilla.org/es/docs/Web/JavaScript/Reference/Functions/Arrow_functions#sintaxis_avanzada "Permalink to Sintaxis avanzada")

Para devolver una expresión de objeto literal, se requieren paréntesis alrededor de la expresión:

```js
params => ({foo: "a"}) // devuelve el objeto {foo: "a"}
```

Los `parámetros rest` son compatibles:

```js
(a, b, ...r) => expression
```

Se admiten los `parámetros predeterminados`:

```js
(a=400, b=20, c) => expression
```

`Desestructuración` dentro de los parámetros admitidos:

```js
([a, b] = [10, 20]) => a + b;  // el resultado es 30
({ a, b } = { a: 10, b: 20 }) => a + b; // resultado es 30
```

# Usar promesas

Una [`Promise`](https://developer.mozilla.org/es/docs/Web/JavaScript/Reference/Global_Objects/Promise) (promesa en castellano) es un objeto que representa la terminación o el fracaso de una operación asíncrona. Dado que la mayoría de las personas consumen `promises` ya creadas, esta guía explicará primero cómo consumirlas, y luego cómo crearlas.

Esencialmente, una promesa es un objeto devuelto al cuál se adjuntan funciones `callback`, en lugar de pasar callbacks a una función.

Considera la función `crearArchivoAudioAsync()`, el cuál genera de manera asíncrona un archivo de sonido de acuerdo a un archivo de configuración, y dos funciones callback, una que es llamada si el archivo de audio es creado satisfactoriamente, y la otra que es llamada si ocurre un error. El código podría verse de la siguiente forma:

```js
function exitoCallback(resultado) {
  console.log("Archivo de audio disponible en la URL " + resultado);
}

function falloCallback(error) {
  console.log("Error generando archivo de audio " + error);
}

crearArchivoAudioAsync(audioConfig, exitoCallback, falloCallback);
```

... las funciones modernas devuelven un objeto `promise` al que puedes adjuntar funciones de retorno (callbacks). Si `crearArchivoAudioAsync` fuera escrita de manera tal que devuelva un objeto `promise`, usarla sería tan simple como esto:

```js
crearArchivoAudioAsync(audioConfig).then(exitoCallback, falloCallback);
```

Lo cuál es la versión corta de:

```js
const promesa = crearArchivoAudioAsync(audioConfig);
promesa.then(exitoCallback, falloCallback);
```

Llamamos a esto una _llamada a función asíncrona_. Esta convención tiene varias ventajas. Exploraremos cada una de ellas.

## [Encadenamiento](https://developer.mozilla.org/es/docs/Web/JavaScript/Guide/Using_promises#encadenamiento "Permalink to Encadenamiento")

Una necesidad común es el ejecutar dos o más operaciones asíncronas seguidas, donde cada operación posterior se inicia cuando la operación previa tiene éxito, con el resultado del paso previo. Logramos esto creando una cadena de objetos `promises`.

Aquí está la magia: la función `then()` devuelve una promesa nueva, diferente de la original:

```js
const promesa = hazAlgo();
const promesa2 = promesa.then(exitoCallback, falloCallback);
```

o

```js
let promesa2 = hazAlgo().then(exitoCallback, falloCallback);
```

Esta segunda promesa (`promesa2`) representa no sólo la terminación de `hazAlgo()`, sino también de `exitoCallback` o `falloCallback` que pasaste, las cuales pueden ser otras funciones asíncronas devolviendo una promesa. Cuando ese es el caso, cualquier función callback añadida a `promesa2` se queda en cola detrás de la promesa devuelta por `exitoCallback` o `falloCallback`.

Básicamente, cada promesa representa la terminación de otro paso (asíncrono on no) en la cadena.

En el pasado, hacer varias operaciones asíncronas en fila conduciría a la clásica pirámide de funciones callback:

```js
hazAlgo(function(resultado) {
  hazAlgoMas(resultado, function(nuevoResultado) {
    hazLaTerceraCosa(nuevoResultado, function(resultadoFinal) {
      console.log('Obtenido el resultado final: ' + resultadoFinal
    }, falloCallback);
  }, falloCallback);
}, falloCallback);
```

Con las funciones modernas, adjuntamos nuestras functiones callback a las promesas devueltas, formando una cadena de promesa:

```js
hazAlgo().then(function(resultado) {
  return hazAlgoMas(resultado);
})
.then(function(nuevoResultado) {
  return hazLaTerceraCosa(nuevoResultado);
})
.then(function(resultadoFinal) {
  console.log('Obtenido el resultado final: ' + resultadoFinal);
})
.catch(falloCallback);
```

Los argumentos a `then` son opcionales, y `catch(falloCallBack)` es un atajo para `then(null, falloCallBack)`. Es posible que veas esto expresado con [funciones de flecha](https://developer.mozilla.org/es/docs/Web/JavaScript/Reference/Functions/Arrow_functions) :

```js
hazAlgo()
.then(resultado => hazAlgoMas(resultado))
.then(nuevoResultado => hazLaTerceraCosa(nuevoResultado))
.then(resultadoFinal => {
  console.log(`Obtenido el resultado final: ${resultadoFinal}`);
})
.catch(falloCallback);
```

**Importante**: Devuelve siempre resultados, de otra forma las funciones callback no se encadenarán, y los errores no serán capturados.