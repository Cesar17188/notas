# Default Params y Concatenación

funcion que recibe muchos parametros, para evitar confundirnos en la posicion de algun parametro podemos simplemente recibir un solo parametro en la funcion y que este sea un objeto, luego hacemos [destructuring](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Destructuring_assignment) para poder obtener sus elementos de manera mas facil.

```js
//Funcion recibiendo todos los parametros  sin un objeto
function saveUser( name, lastName, age, country, 
city, postalCode, userName, password ){
	//...
}

//Al recibir todos los parametros de esta forma
//podemos equivocarnos al momento de invocar esta funcion
saveUser('pepe', 'perez', 20, 'Toronto', 
'Canada', 0000,  'peperez', '123pass' ) 

// intercambiamos el parametro Country por el parametro City accidentalmente

//funcion recibiendo solo 1 objeto como parametro
function saveUser({ name, lastName, age, 
country, city, postalCode = 0000, userName, password }){
	//...
}
saveUser({ name: 'pepe', lastName: "perez",
age: 20, city: 'Toronto', country: 'Canada',
userName: 'peperez', password:'123pass' })

//aqui intercambiamos la posicion de country y 
//city nuevamente, pero esta vez no importa 
//ya que todo se esta pasando dentro de un objeto, 
//adicionalmente no estamos enviando el elemento 
//postalCode pero su valor por defecto es 0000
```