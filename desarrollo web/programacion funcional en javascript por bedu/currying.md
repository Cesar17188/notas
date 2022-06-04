# Currying
Gracias a los closures es posible implementar el **Currying**, descomponer funciones complejas en otras funciones más pequeñas donde cada función recibe un solo argumento. A continuación un ejemplo:

```js
// Sin Currying
function sumThreeNumbers(a, b, c) {
        return a + b + c
}

console.log(sumThreeNumbers(1, 2, 3)) // 6

function sumThreeNumbers(a) {
        return function(b) {
                return function(c) {
                        return a + b + c
                }
        }
}

console.log(sumThreeNumbers(1)(2)(3)) // 6
```