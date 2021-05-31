# Ejemplo hoisting

Una estricta definición de hoisting sugiere que las declaraciones de variables y funciones son físicamente movidas al comienzo del código,asignandolas en memoria dentro de un contexto de ejecucion.
[[hoisting]]

ejemplo

Lo que escribes:

```javascript
console.log(nombre);
apellido();

var nombre = "Diego";

function apellido(){
	console.log("De Grada");
}
```

Como el motor de JavaScript lo interpreta:

```javascript
var nombre = undefined;
function apellido(){
	console.log("De Grada");
}

console.log(nombre);
apellido();
nombre = "Diego";
```

Si te preguntas cuál pone más arriba, ¿Las variables o las funciones?  
La respuesta es las variables. Probemos esto:

```javascript
var nombre;
function nombre(){}

typeof nombre; // Output: "function"
```

¿Y si ponemos primero la función y luego la variable?

```javascript
function nombre(){}
var nombre;

typeof nombre; // Output: "function"
```

Pero, si declaras una variable y le asignas un valor en la misma linea el resultado es diferente:

```javascript
var nombre = "Platzi";
function nombre(){}

typeof nombre; // Output: "string"
```

Esto es porque JavaScript hace hoisting solo de la declaración de la variable. JavaScript trata la declaración y asignación en una sola linea como dos pasos, por lo que si escribimos:

```javascript
var nombre = "Platzi";
```

El motor lo interpreta así:

```javascript
var nombre = undefined;
nombre = "Plazi";
```

Así que cuando escribimos:

```javascript
var nombre = "Platzi";
function nombre(){}

typeof nombre; // Output: "string"
```

Como lo interpreta el motor de JavaScript es así:

```javascript
var nombre = undefined;
function nombre(){}

nombre = "Platzi";

typeof nombre; // Output: "string"
```

Es decir que “se deja atrás” la asignación.  
Obviamente ningún desarrollador debería de escribir código así de confuso, esto es solo para saber como funciona JavaScript y su engine, ese conocimiento te hace un mejor desarrollador y te destaca de entre otros.