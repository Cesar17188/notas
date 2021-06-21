# Local Scope

El [[scope]] se puede definir como el alcance que puede tener una variable en tu codigo.

**El Local Scope:** se refiere a la variable o funcion que esta dentro de un bloque o funcion especifica. Solo se pueden acceder a ellas (ejecutar o llamar) dentro del entrono en donde conviven.

**El ambito lexico:** se refiere a que una funcion puede acceder a una funcion o variable fuera de ella. Cada nivel interno puede acceder a sus niveles externos hasta poder alcanzarlas.

Lexical Scope / Ámbito Léxico: El intérprete de [[javascript]] funciona desde el ámbito de ejecución actual y funciona hasta encontrar la variable en cuestión. Si la variable no se encuentra en ningún ámbito, se genera una excepción.

Este tipo de búsqueda se llama ámbito léxico. El alcance de una variable se define por su ubicación dentro del código fuente, y las funciones anidadas tienen acceso a las variables declaradas en su alcance externo. No importa de dónde se llame una función, o incluso cómo se llama, su alcance léxico depende solo de dónde se declaró la función.

```js
/\* SCOPE LOCAL

  

Las variables inicializadas con la palabra reservada

let o const dentro de un bloque de código solo pueden ser

accedidas dentro de ese mismo bloque de código.

Si se intenta acceder a esas variables desde fuera del bloque

de código no se podrá utilizar.\*/

  

const helloWorld = () \=> {

 const hello = "Hello World";

 console.log(hello);

};

  

helloWorld();

  

console.log(hello);

  
  

/\*Si inicializamos una variable con la palabra reservada var

fuera de un bloque de código es una variable global

y creamos otra variable con el mísmo nombre de identificador

dentro de un bloque de código, la variable global no se reasigna,

y la variable local actua solo dentro del bloque de código

donde fue creada \*/

  

var scope = 'I am global';

  

const functionScope = () \=> {

 var scope = 'I am just a local';

 const func = () \=> {

 return scope;

 }

 console.log(func());

};

  

functionScope();

console.log(scope);

```