# Calculando el promedio en JavaScript

Como se explicó en [[que es promedio, moda y mediana]] el promedio es la sumatoria de todos los número de una seríe o arreglo dividivo para el número total de elementos de dicho arreglo o seríe. En javascript la función reduce nos ayuda a conseguirlo de la siguiente manera.

```js
  

function calcularMediaAritmetica(lista) {

 //   let sumaLista = 0;

 //   for (let i = 0; i < lista.length; i++) {

 //     sumaLista += lista[i];

 //   }

  

 const sumaLista = lista.reduce(function (valorAcumulado = 0, nuevoElemento) {

 return valorAcumulado + nuevoElemento;

 });

  

 const promedioLista = sumaLista / lista.length;

  

 return promedioLista;

}
```