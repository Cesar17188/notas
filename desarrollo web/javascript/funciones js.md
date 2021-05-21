# Funciones

Las funciones son las tareas que va a llevar a cabo el navegador. Existen 2 tipos de funciones  
1) Declarativas  
2) De expresión  

### Funciones Declarativas:

En las funciones declarativas, utilizamos la palabra reservada function al inicio para poder declarar la función:

```js
function saludar(nombre) {
	console.log(`Hola ${nombre}`);
}

saludar('Diego');

```

#### Expresión de función:

En la expresión de función, la declaración se inicia con la palabra reservada var, donde se generará una variable que guardará una función anónima.

```js
var nombre = function(nombre){
    console.log(`Hola ${nombre}`)
}

nombre(‘Diego’);

```

En la expresión de función, la función podría o no llevar nombre, aunque es más común que se hagan anónimas.

### Diferencias:

A las funciones declarativas se les aplica hoisting, y a la expresión de función, no. Ya que el hoisting solo se aplica en las palabras reservadas var y function.

___________________________________________________________

Lo que quiere decir que con las funciones declarativas, podemos mandar llamar la función antes de que ésta sea declarada, y con la expresión de función, no, tendríamos que declararla primero, y después mandarla llamar.
Ambas pueden llevar parámetros, que son los datos que necesitan para ejecutarse.  
Cada parámetro va separado por una coma.  
Cada instrucción que tenga la función debe terminar con ; .  
Si queremos que una función nos dé un numero o dato tenemos que usar la siguiente sintaxis:

_return El dato que queremos que nos dé;_

```js
Las funciones declarativas tienen la siguiente sintaxis:
```

_function Nombre de la función (Parámetros de la función) {Instrucciones}_

```js
Un ejemplo de una función puede ser una suma:
```

\_  
function suma (a,b) {return a+b;}\_

```js
Las funciones de expresión son aquellas que guardamos en una variable, por lo tanto, no es necesario nombrarlas y tienen la siguiente sintaxis:
```

\_var Nombre de la variable = function(Parametros){Instrucciones}.  
\_

Un ejemplo de una función de expresión sería:

_var suma = function(a,b){return a+b;}_

```js
Para ejecutar las funciones debemos usar la siguiente sintaxis:
```

\_Nombre de la funcion(Parametros función); \_

Si la función no tiene ningún parámetro, únicamente se escribe:

\_Nombre de la función(); \_