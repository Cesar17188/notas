# Objetos y Tipos de Memoria en JavaScript

Un objeto es una referencia a un espacio en memoria, cada vez que creamos un objeto, este se guarda en la memoria (no sabemos exactamente dónde) y podemos acceder a su valor gracias a las coordenadas.

Existen dos tipos de memoria: Stack y Heap.  
La memoria **Stack** es mucho más rápida y nos permite almacenar los datos de forma ““ordenada”” y en JavaScript la utilizamos para guardar datos primitivos, como booleanos, números o _strings_. En cambio, los objetos utilizan la memoria **Heap**, una memoria que nos permite guardar grandes cantidades de información pero con un poco menos de velocidad.

Estos dos conceptos nos van a ayudar mucho a la hora de copiar objetos cuando utilizamos la programación funcional.