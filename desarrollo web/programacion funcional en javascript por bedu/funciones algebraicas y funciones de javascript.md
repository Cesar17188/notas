# Funciones Algebraicas y Funciones de JavaScript
Por lo general, utilizamos las funciones de JavaScript para realizar algunas operaciones o una secuencia de procedimientos. También podemos convertir una función algebraica a una función pura de JavaScript: definimos una función `F` que recibe el parámetro `X` y devuelve el valor de `X*2`.

```math
F(x) = 2 * x
```

Por supuesto, la manera de utilizar este tipo de funciones es asignando el valor de `X`:

```math
F(2) = 2 * 2
F(2) = 4
```

Estas funciones siempre van a devolver el mismo resultado, es decir, si entregamos el parámetro `2`, siempre vamos a recibir un `4`, si entregamos el parámetro `3`, siempre vamos a recibir `6` y así sucesivamente.

Las funciones en JavaScript funcionan de la misma manera:

```js
const double = (x) => x*2
double(2) // 4
```

