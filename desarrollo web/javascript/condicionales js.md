# Condicionales: Id, Else, else if

El **operador condicional** (**ternario**) es el único operador en JavaScript que tiene tres operandos. Este operador se usa con frecuencia como atajo para la instrucción [if](https://developer.mozilla.org/es/docs/Web/JavaScript/Referencia/Sentencias/if...else).
### Parámetros

`condición`

Una expresión que se evalúa como true o false.

`expr1`, `expr2`

Expresión con valores de algún tipo.

Si la `condición` es `true`, el operador retorna el valor de la `expr1`; de lo contrario,  devuelve el valor de `expr2`. Por ejemplo, para mostrar un mensaje diferente en función del valor de la variable _`isMember,`_ se puede usar esta declaración:

```js
"La Cuota es de:  " + (isMember ? "$2.00" : "$10.00")
```

También puedes asignar variables dependiendo del resultado de la condición ternaria:

```js
var elvisLives = Math.PI > 4 ? "Sip" : "Nop";
```

También es posible realizar evaluaciones ternarias múltiples (Nota: El operador condicional es asociativo):

```js
var firstCheck = false,
    secondCheck = false,
    access = firstCheck ? "Acceso Denegado" : secondCheck ? "Acceso Denegado" : "Acceso Permitido";

console.log( access ); // muestra "Acceso Permitido"
```

También puede usar operaciones ternarias en espacio vacío con el propósito de realizar diferentes operaciones:

```js
var stop = false, age = 16;

age > 18 ? location.assign("continue.html") : stop = true;
```

También puede realizar más de una operación por caso, separándolas con una coma:

```js
var stop = false, age = 23;

age > 18 ? (
    alert("OK, puedes continuar."),
    location.assign("continue.html")
) : (
    stop = true,
    alert("Disculpa, eres menor de edad!")
);
```

También puede realizar más de una operación durante la asignación de un valor.