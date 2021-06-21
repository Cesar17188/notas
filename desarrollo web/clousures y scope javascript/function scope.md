# Function scope

Un pequeño resumen sobre como actúan las diferentes variables:

-   Las [[variables js]] escritas con la palabra clave **var** pueden ser redeclaradas, pero esto a futuro puede darnos problemas, así que es mejor no usarla.
    
-   Las variables escritas con la palabra clave **let** no pueden ser redeclaradas, si lo haces mostrara un _**“error: esta variable ya ha sido declarada”**_ , pero su valor puede ser reasignado:
    

```
let fruit = "apple";
fruit = "banana";

console.log(fruit); // banana
```

-   Las variables escritas con la palabra clave **const** no pueden ser redeclaradas o reasignadas, ya que const quiere decir que su valor será constante, es decir que no va a cambiar.

```js
/*FUNCTION SCOPE

Si inicializamos y definimos una variable dentro del scope

local de una función, solo podra ser utilizada dentro del

scope de esa función, si le intentamos llamar o utilizar 

como si fuera una variable global se desplegará un error 

en la interpretación

*/

  

const fruits = () \=> {

 var fruit = 'apple';

 console.log(fruit);

};

  

fruits();

console.log(fruit);

  

/*

Un pequeño resumen sobre como actúan 

las diferentes variables:

  

Las variables escritas con la palabra

clave var pueden ser redeclaradas, 

pero esto a futuro puede darnos problemas, 

así que es mejor no usarla.

  

Las variables escritas con la palabra 

clave let no pueden ser redeclaradas, 

si lo haces mostrara un “error: 

esta variable ya ha sido declarada” , 

pero su valor puede ser reasignado:

*/

  

const anotherFunction = () \=> {

 var x = 1;

 var x = 2;

 let y = 1;

 y = 2;

 console.log(x);

 console.log(y);

}

  

anotherFunction();
```