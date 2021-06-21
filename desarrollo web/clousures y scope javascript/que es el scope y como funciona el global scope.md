# Qué es el Scope y cómo funciona el Global Scope

Scope: Es el alcance que va a tener una variable dentro del código. En otras palabras, el [[scope]] se encargará de decidir a que bloques de código va a acceder una variable.

**Global Scope** : No están dentro de funciones o bloques, por lo tanto se puede acceder a ellas de manera global.

-   Con var podemos re-asignar una variable pero es una mala práctica.
    
-   Con let y const no podemos, aparecerá un error.
    
-   Es una mala práctica crear una variable sin las palabras reservadas: var, let y const.  
    Si se asigna una variable dentro de una función sin las palabras reservadas será una variable global.
    
-   La doble asignación de una variable también es una mala práctica.


```js
\*Todas estan dentro del scope global así que 

pueden ser usadas en todo el spectro del programa

pero solo var puede ser reasignada, let y const no*/

  

var hello = "Hello";

var hello = "Hello +";

let world = "Hello World";

let world = 'Hello';

const helloWorld = "Hello World!";

console.log(hello);

  

const anotherFunction = () \=> {

 console.log(hello);

 console.log(world);

 console.log(helloWorld);

};

  

anotherFunction();


/*Se está asignando una variable global dentro 

de una función, lo cual es una mala práctica ya que

puedo acceder desde cualquier parte del programa*/


const helloWorld = () \=> {

 globalVar = 'im global'

}

  
  

helloWorld();

console.log(globalVar);

  
  

const anotherFunction = () \=> {

 var localVar = globalVar = 'Im Global';

}

  

anotherFunction();

console.log(globalVar);
```