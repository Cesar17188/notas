# ¿Qué se implemento en es7?

## método include

Array.prototype.includes()

El método `**includes()**` determina si una matriz incluye un determinado elemento, devuelve `true` o `false` según corresponda.

```js
const array1 = [1, 2, 3];

console.log(array1.includes(2));
// expected output: true

const pets = ['cat', 'dog', 'bat'];

console.log(pets.includes('cat'));
// expected output: true

console.log(pets.includes('at'));
// expected output: false
```

## Asignación

Operador de asignación simple que asigna un valor a una variable. EL operador de asignación evalua al valor asignado. Encadenando el operador de asignación es posible en orden de asignar un solo valor a multiples variables. Vea el ejemplo.

```js
**Operador:** x = y
```

Ejemplos

```js
// Asumiendo las siguientes variables
//  x = 5
//  y = 10
//  z = 25


x = y     // x es 10
x = y = z // x, y, z son todas 25
```