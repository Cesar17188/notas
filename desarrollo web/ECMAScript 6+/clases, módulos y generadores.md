# Clases, Módulos y Generadores

## ES6

<h3>export default</h3>

Con export default podemos exportar una variable, o función por defecto de un archivo así:

```javascript
function hello() {
	return 'Hello!'
}

export default hello
```

Para importarla no necesitamos hacerlo con su nombre, podemos usar cualquier nombre y por defecto nos traerá la única variable o función que exportó así:

```javascript
import myHello from './module'

console.log(myHello())
```

<h3>export nombrado</h3>

A diferencia del export default en esta ocasión podemos exportar más de una variable o función que se encuentre en nuestro archivo, pero para importarlas debemos hacerlo con el nombre exacto de esa variable entre llaves.

Para exportar lo hacemos así:

```javascript
export function hello() {
	return 'Hello!'
}

export const bye = 'Bye!'
```

Podemos importar solo lo que necesitemos así:

```javascript
import { hello } from './module'

console.log(hello())
```

También podemos importar más de un elemento nombrando cada uno

```javascript
import { hello, bye } from './module'

console.log(hello())
console.log(bye)
```

Podemos cambiarles los nombres

```javascript
import { hello, bye as byeGreeting } from './module'

console.log(hello())
console.log(byeGreeting)
```

Y podemos importar todas las funciones de una sola vez

```javascript
import * as allGreetings from './module'

console.log(allGreetings.hello())
console.log(allGreetings.bye)
```

## Anterior sintaxis

Cuando no nos funcione esta sintaxis porque no la tengamos soportada podemos usar la anterior

Para exportar lo hacemos así:

```javascript
function hello() {
	return 'Hello!'
}

module.exports = hello
```

Para importar así:

```javascript
const hello = require('./module')

console.log(hello())
```

Con la sintaxis antigua también podemos exportar más de una variable o función pasándolas como un objeto.