# Calculando la mediana en JavaScript

Como se explicó en [[que es promedio, moda y mediana]] la mediana son los valores o el valor que se encuentra en la mitad de la seríe o arreglo. Para poder ejecutar esta funcionalidad primero se debe ordenar la lista y para ellos la función sort nos ayuda a ordenar el arreglo y se calcula en javascript de la siguiente manera.

```js
function calcularMediaAritmetica(lista) {

 const sumaLista = lista.reduce(function (valorAcumulado = 0, nuevoElemento) {

 return valorAcumulado + nuevoElemento;

 });

  

 const promedioLista = sumaLista / lista.length;

  

 return promedioLista;

}

    

function calcularMediana(lista) {

 listaOrdenada = lista.sort(function (a, b) {

 return a - b;

 });

  

 const mitadLista = parseInt(listaOrdenada.length / 2);

  

 let mediana;

  

 if (esPar(listaOrdenada.length)) {

 const elemento1 = listaOrdenada[mitadLista - 1];

 const elemento2 = listaOrdenada[mitadLista];

  

 const promedioElemento1y2 = calcularMediaAritmetica([elemento1, elemento2]);

  

 mediana = promedioElemento1y2;

 } else {

 mediana = listaOrdenada[mitadLista1];

 }

  

 return mediana;

}

  

function esPar(numerito) {

 if (numerito % 2 === 0) {

 return true;

 } else {

 return false;

 }

}
```