# Closures en programación funcional

Los Closures son funciones que retornan otras funciones y recuerdan el _scope_ en el que fueron creadas, es decir, son funciones que utilizan principios de la programación funcional, no modifica el valor de variables u objetos externos, más bien, utilizan sus propias variables independientes (a partir de los parámetros que reciban estas funciones) para dar resultados correctos.

```js
function buildSum(a) {
	return function(b) {
		return a + b
	}
}

const addFive = buildSum(5)
console.log(addFive(5)) // 10


//////// width arrow funtions

const buildSum = a => b => a + b
```