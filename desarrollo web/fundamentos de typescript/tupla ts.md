# Tupla

Una tupla en TypeScript es un array de elementos que están tipados. De esta manera cada vez que haya que insertar un elemento se validará que dicho elemento coincida con el tipo de dato establecido en la tupla.

```
// Tipo tuple
// Tuplas: permiten expresar un arreglo con un numero fijo de elementos

export {}; // -> user ya fue declarado en otro archivo

// [1, 'user']
let user: [number, string]; // -> user ya fue declarado en otro archivo
user = [1, 'luixaviles'];

console.log('user : ', user);
console.log('username : ', user[1]);
console.log('username.length : ', user[1].length);
console.log('id : ', user[0]);

// Tuplas con varios valores
// id, username, isPro
let userInfo: [number, string, boolean];
userInfo = [2, 'paparazzi', true];
console.log('userInfo : ', userInfo);

// Arreglo de Tuplas
let array: [number, string][] = [];
array.push([1, 'luixaviles']);
array.push([2, 'paparazzi']);
array.push([3, 'lensQueen']);   // indice: 2
console.log('array : ', array);

// Uso de funciones array
// lensQueen --> lensQueen001
array[2][1] = array[2][1].concat('001');  // --> concatena
console.log('array : ', array);
```

-   Expresar o representar un conjunto de elementos.
-   Es demasiado parecido a un Array y concretamente es un registro de datos, que pueden ser una estructura, una función, una variable, una constante
-   Dependiendo del tipo de datos que se encuentre en el registro de la tupla, se puede ejecutar métodos para el tipo de valor.

```
//Tuple

let userOfMine: [number, string]; 
userOfMine = [3, 'rosita'];

console.log(
    'substract of the string -> ', userOfMine[1].substr(3, 3), // Ejecuta los métodos del tipo de valor, en este caso un string 
    'substract of the string -> ', userOfMine[0]  // Ejecuta métodos de los tipos de valor number
);

//Múltiples tuplas explícitas
let tuples: Array<[number, string, boolean]> = [
    [1,'jhonsi', true],
    [2, 'afelipelds', false],
    [4, 'ivy', false],
];

tuples[2][1]= tuples[2][1].concat(' fullstack');

console.log(tuples);

```