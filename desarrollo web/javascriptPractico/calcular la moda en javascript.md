# Calcular la moda en JavaScript

Como se explicó en [[que es promedio, moda y mediana]] la moda es el conteo del mayor número de repeticiones de los elementos en una lista. Para poder ejecutar esta funcionalidad primero se debe transormar la lista o arreglo en un objeto y para ello la función map nos ayuda a tranformarlo y crear un objeto llave valor con la sumatoria como valor y el elemento del arreglo como llave. Para poder obtener un valor que se pueda calcular es necesario convertir el objeto en un arreglo y para eso la función Object.entries nos ayudara y se calcula en javascript de la siguiente manera.

```js
function calcularModa(lista) {

 const listaCount = {};

  

 lista.map(function (elemento) {

 if (listaCount[elemento]) {

 listaCount[elemento] += 1;

 } else {

 listaCount[elemento] = 1;

 }

 });

  

 const listaArray = Object.entries(listaCount).sort(function (

 elementoA,

 elementoB

 ) {

 return elementoA[1] - elementoB[1];

 });

  

 const moda = listaArray[listaArray.length - 1];

  

 return moda;

}
```