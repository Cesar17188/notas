# Qué son funciones puras

Las funciones puras siempre devuelven el mismo resultado cuando reciben los mismos parámetros. En cambio, otras funciones que dependen de factores externos (como el tiempo o una petición HTTP) no siempre pueden devolver el mismo resultado aunque reciban los mismos parámetros, incluso, pueden no necesitar recibir parámetros para ejecutarse correctamente.

Ejemplos de funciones puras:

```js
const double = x => x*2
double(2) // siempre es 4
double(3) // siempre es 6

const isGreaterThan = (value, comparison) => value > comparison
isGreaterThan(5, 6) // siempre devuelve false
isGreaterThan(8, 6) // siempre devuelve true
```

Ejemplos de funciones que NO son puras:

```js
const time = () => new Data().toLocalTimeString()
time() // siempre devuelve un resultado diferente
```