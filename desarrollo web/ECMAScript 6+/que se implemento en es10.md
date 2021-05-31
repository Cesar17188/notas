# ¿Qué se implemento en es10?

Se desarrolla en 2019

# Array.prototype.flat()

El método `**flat()**` crea una nueva matriz con todos los elementos de sub-array concatenados recursivamente hasta la profundidad especificada.

## [Sintaxis](https://developer.mozilla.org/es/docs/Web/JavaScript/Reference/Global_Objects/Array/flat#sintaxis "Permalink to Sintaxis")

var newArray = arr.flat(\[depth\]);

### [Parámetros](https://developer.mozilla.org/es/docs/Web/JavaScript/Reference/Global_Objects/Array/flat#par%C3%A1metros "Permalink to Parámetros")

`depth` Optional

El nivel de profundidad que especifica qué tan profunda debe aplanarse una estructura de matriz anidada. El valor predeterminado es 1.

### [Valor de retorno](https://developer.mozilla.org/es/docs/Web/JavaScript/Reference/Global_Objects/Array/flat#valor_de_retorno "Permalink to Valor de retorno")

Una nueva matriz con los elementos de la sub-matriz concatenados en ella.

## [Ejemplos](https://developer.mozilla.org/es/docs/Web/JavaScript/Reference/Global_Objects/Array/flat#ejemplos "Permalink to Ejemplos")

### [Aplanar matrices anidadas](https://developer.mozilla.org/es/docs/Web/JavaScript/Reference/Global_Objects/Array/flat#aplanar_matrices_anidadas "Permalink to Aplanar matrices anidadas")

```js
var arr1 = [1, 2, [3, 4]];
arr1.flat();
// [1, 2, 3, 4]

var arr2 = [1, 2, [3, 4, [5, 6]]];
arr2.flat();
// [1, 2, 3, 4, [5, 6]]

var arr3 = [1, 2, [3, 4, [5, 6]]];
arr3.flat(2);
// [1, 2, 3, 4, 5, 6]
```

## Array.flatMap()

```js
/\*Array.flatMap() Nos permite mapear cada elemento, luego 

pasarle una función y mostrar el resultado\*/

  

let array = \[1,2,3,4,5\];

  

console.log(array.flatMap(value \=> \[value, value\*2\]));
```

## trimStart(), trimEnd()
```js
/\*trimStart(),  trimEnd()

eliminar los espacios en blanco de un string\*/

  

let hello = "                 hello world";

console.log(hello);

console.log(hello.trimStart());

  

let hello = 'hello World              ';

console.log(hello);

console.log(hello.trimEnd());
```

## fromEntries()
```js
/\*fromEntries

Nos permite obtener los valores desde un arreglo 

y transformarlo en un objeto\*/

  

let entries = \[\['name','oscar'\], \['age',28\]\];

  

console.log(Object.fromEntries(entries))
```

## Symbol description

```js
/\*Objeto de tipo símbolo

nos permite ver la descripción del objeto

es decir lo que contiene el objeto seleccionado\*/

  

let mySymbol = \`My Symbol\`;

let symbol = Symbol(mySymbol);

console.log(symbol.description)
```