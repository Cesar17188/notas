# Consola, utilidades y debugging

En nodejs tenemos la utilidad consola en ella podemos usar el **[console.info]**, **[console.log]**, **[console.error]**, estamos bastante familiarizados con esta utilidad, sin embargo todo por defecto lo que imprimimos por consola se va por el **stdout**, y todo lo que imprimimos en el console.error se va por el **stderror**. Mediante la **clase Consola** que es diferente a la consola, podemos personalizarlo para decir que en vez se valla por el stdout o stderror, hagamos una cosa completamente diferente.

```js
// En lugar de usar una consola stdout o stderror
/* 
Usaremos el conocimiento de fileystem, para que cada vez que escriba o que imprimaa
El stdout nos quede un archivo de log.

Así mismo cada vez que usemos el stderror, creamos otro archivo log.
*/

const fs = require('fs');

// Cada vez que imprima en el stdout nos cree un archivo de log
const out = fs.createWriteStream("./out.log");
const err = fs.createWriteStream("./err.log");

/* creamos consola personalizada, la cual lo hacemos instanciando la Clase
Console la cual recibe 2 párametros, como primer parametro todo lo que le pasemos en el
console.log o console.info y como segundo párametro, todo lo que llamé con sonsole.error
*/
const consoleFile = new console.Console(out, err);

// Ejecutamos una función de intervalo cada 2 segundos
setInterval(() => {
  // Imprimimos una fecha en el console.log personalizado
  consoleFile.log(new Date());
  // Imprimimos un error en el console.error personalizado
  consoleFile.error(new Error("Ooops!"));
}, 2000)

```

No solo podemos jugar con la clase de la consola para crear nuestra consola personalizada, si no que también vamos a explorar diferentes utilidades de consola.

**console.log por debajo trabaja con una utilidad llamada util format**:

-   %s - String
-   %d - Number
-   %i - parseInt(value, 10)
-   %f - parseFloat(value)
-   %j - JSON
-   %o - Object
-   %c - Css
-   %% - signo de '%'

Estos son pequeños **placeholders** para formatear nuestros datos. `console.log("Un %s y un %s", "Perrito", "Gatito");`

Si accedemos a la consola de node exactamente esto hace la utilidad **util.format()** es decir la consola se alimenta del paquete **[util.format]** y funciona exactamente igual.

Node ocupa este paquete de utilidades para otros paquetes que el expone, pero nos deja la posibilidad de alimentarnos de estas utilidades, es decir si yo por alguna razón quiero hacer uso del **[util.format]** lo podemos hacer.

Alias de console.log:

-   `console.info`

Alias de de console.error:

-   `console.wran`

  
- **console.assert**: Si hay un error nos muestra que existe un error en un assert, en un booleano o verificación:

```js
console.assert(42 == "42");
console.assert(42 === 42);
```

**console.trace**: nos indica la linea donde esta ocurriendo el error que es mucho más especifico.

Una utilidad bastante interesante es una llamada de [debuglog](https://nodejs.org/dist/latest-v8.x/docs/api/util.html#util_util_debuglog_section), lo que tenemos que hacer obtener la utilidad, por la cual node nos la deja abierta para que la hagamos, e invocamos el debuglog, llamando **util.debuglog**. Esto es muy parecido a como funciona el paquete debug de express, pero nosotros básicamente lo que decimos es crear un debuggin.

Vamos a crear un nuevo debuggin que va a exponer un namespace que va a ser _foo_ Nosotros podemos imprimir nuestro mensaje de debug "hello"y esto solo solo se imprime si pasamos la variable de entorno NODE_DEBUG con el namespace.

## Deprecate

Cuando hacemos `util.deprecate` hacemos un wrap de una función que ya está obsoleta y queremos hacer saber a nuestros usuarios que ya no deberia de usar, lo interesante de nuestra función deprecate es que nos permite imprimir un mensaje.

```js
const util = require("util");

const helloPluto = util.deprecate(() => {
  console.log("hello pluto");
}, 'pluto is deprecated. It is not a planet anymore');

helloPluto();
```

Esto es bastante util cuando nosotros estamos haciendo refactory y nosotros queremos hacerle saber al usuario que hay ciertas funcionalidades que quizas en una versión más adelante va a desaparecer por completo.

## Debuggin en node

Para hacer debuggin en node lo que debemos usar es el flag `node --inspect` y luego especificar al archivo que queremos hacer debuggin. En versiones anteriores de node es decir < 12, hacer uso de node debugg, genera un `warning o deprecation warning` que es exactamente igual al `util-deprecate` que aprendimos con anterioridad, esto quiero decir que en futuras versiones de node, esto va a desaparecer. Por lo que la recomendación es empezar a usar el node --inspect desde ahora.

Cuando hacemos el node inspect, el habre un puerto en el localhost:9229 especificado acá en nuestro navegador. Si nos damos cuenta es exactamente la utilidad debuggin que tiene js del lado del cliente.