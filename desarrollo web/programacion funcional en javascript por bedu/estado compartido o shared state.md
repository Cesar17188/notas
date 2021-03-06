# Estado compartido o shared state

Shared State significa que diferentes métodos trabajan a partir de una misma variable. y, así como aprendimos en clases anteriores, cuando modificamos variables con el mismo objeto de referencia podemos encontrarnos con algunos problemas y obtener resultados inesperados a pesar de ejecutar el mismo código y recibir los mismos parámetros:

```js
// Intento #1
const a = {
        value: 2
}

const addOne = () => a.value += 1
const timesTwo = () => a.value *= 2

addOne()
timesTwo()

console.log(a.value) // 6

// Sin embargo, si ejecutamos las mismas funciones en orden invertido
// obtenemos resultados diferentes

timesTwo()
addOne()

console.log(a.value) // 5 !??
```

Para resolver este tipo de problemas debemos utilizar la programación funcional, en vez de modificar la variable original, nuestras funciones deben copiar y modificar sus argumentos:

```js
const b = {
        value: 2
}

const addOne = x => Object.assign({}, x, { value: x.value + 1 })
const timesTwo = x => Object.assign({}, x, { value: x.value * 2 })

addOne(b)
timesTwo(b)

// El resultado siempre es el mismo a pesar de
// ejecutar las funciones en orden diferente

timesTwo(b)
addOne(b)

console.log(b.value)
```