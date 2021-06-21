# Block Scope

Con var , tiene un [[scope]] de función y solo un enlace compartido para todas sus iteraciones de bucle, es decir, i en cada callback setTimeout significa la misma variable que finalmente es igual a 6 después de que finaliza la iteración del bucle.

Con let tener un scope de bloque y cuando se utiliza en el ciclo for obtiene un enlace nuevo para cada iteración, es decir, el i en cada callback setTimeout significa una variable diferente, cada una de las cuales tiene un valor diferente: la primera es 0, la el siguiente es 1 etc.

Ahora, ¿Pero por qué me devuelve 10 veces 10? ¿No debería devolverme 10 veces 9?  
veamos la declaración del ciclo for:

```
for (var i = 0; i < 10; i++) {
	...
}
```

El ciclo for termina cuando la condición (i < 10) sea falsa, osea que mientras sea verdadera el recorrerá el ciclo. La variable i aumentará su valor en 1 (i++) por cada iteración, osea que tomará estos valores: (0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10). Toma el 10 porque es ese el valor donde la condición (i < 10) es falsa puesto que 10 no es menor que 10, si no que es igual… y el ciclo termina.  
Espero haberles ayudado y que hayan aclarado sus dudas!

Si todavía se les complica entender, les dejo el [enlace](https://platzi.com/blog/la-diferencia-entre-let-y-var/) de la explicación del profesor Richard!!

```js
/\*Block scope

  

Las variables asignadas con var dentro de una función

pueden ser utilizadas dentro de todo el margen de la función

pero las variables inicializadas con las palabras reservadas

var y const solo puede accedidas dentro del bloque\*/

  

const fruits = () \=> {

 if (true) {

 var fruits1 = "apple";

 let fruits2 = "banana";

 const fruits3 = "kiwi";

  

 console.log(fruits2);

 console.log(fruits3);

 }

 console.log(fruits1);

 //   console.log(fruits2);

 //   console.log(fruits3);

};

  

fruits();

  

// con let x1 = 1, x2 = 2

  

let x = 1;

{

 let x = 2;

 console.log(x);

}

console.log(x);

  

//con var  x1 = 2, x2 = 2

  

var x = 1;

{

 var x = 2;

 console.log(x);

}

console.log(x);

  

const anotherFunction = () \=> {

 for (let i = 0; i < 10; i++) {

 setTimeout(() \=> {

 console.log(i);

 }, 1000);

 }

};

  

anotherFunction();
```