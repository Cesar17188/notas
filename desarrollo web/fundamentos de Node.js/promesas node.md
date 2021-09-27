# Promesas

[[promesas]]
[[arrow functions, promesas y parámetros]]

Las promesas son una sintaxis mas elegante y legible de realizar callbacks, creando así un código mucho más escalable y entendible para todas las personas.  
Una promesa al final no deja de ser un callback, solo que, con la novedad de tener estados, las promesas cuentan con 3 estados, **resuelta, en progreso y en fallo. ** 
Para utilizar una promesa solo debemos de instanciar una nueva, una promesa en si es una función que recibe dos parámetros, resolve y reject, que son los dos estados de una promesa.  
Utilizamos resolve para retornar el valor deseado cuando una función se ejecute y utilizamos reject para cuando una función retorna un valor no deseado.  
```js
New Promise( (resolve, reject) => {  
…code  
If(code === true){  
resolve(correctValue);  
}else {  
Reject(wrongValue);  
}  
});
```
Para poder obtener los valores que retorna una función debemos utilizar su propiedad .then, esta propiedad es una función que recibe un callback el cual tendrá como parámetro el valor retornado con resolve o reject.  
Siempre que usemos una promesa además de realizar la propiedad .then debemos invocar la propiedad .catch, la cual es un callback que recibe como parámetro el error ocurrido en caso de haber sucedió uno.
```js
myPromise(‘Parameter’)  
.then( data => console.log(data) )  
.catch( err => console.log(err) );
```