# Valores: Trusthy and Falsy
Usamos la función de JS que es **_Boolean()_** dentro del paréntesis ponemos el valor y nos dice si el mismo el False o True.

–> _**Falsy**_

-   Boolean() —> sin ningun valor es false
-   Boolean(0) —> false
-   Boolean(null) —> false
-   Boolean(NaN) —> false // NaN es Not and Number
-   Boolean(Undefined) —> false
-   Boolean(false) —> false
-   Boolean("") —> false

–> _**Trusthy**_

-   Boolean(1) —> true //cualquier numero que no sea igual a cero es true
-   Boolean(“a”) —> true
-   Boolean(" ") —> true // siendo un espacio el valor es true
-   Boolean(\[\]) —> true // un array nos da un true
-   Boolean({}) —> true // un objeto nos da el valor de true
-   Boolean(function() {}) —> true //una funcion tambien es true
-   Boolean(true) —> true

Todo esto lo vamos a usar en condiciones esto valida si es verdadero o falso para ejecutar cierta acción.

```js
//Ejemplos en los que Boolean devuelve Falso:
Boolean(0); //false
Boolean(null); //false
Boolean(NaN); //false
Boolean(undefined); //false
Boolean(false); //false
Boolean(""); //false

//Ejemplos en los que Boolean devuelve verdadero:
Boolean(1); //true para 1 o cualquier número diferente de cero (0)
Boolean("a"); //true para cualquier caracter o espacio en blanco en el string
Boolean([]); //true aunque el array esté vacío
Boolean({}); //true aunque el objeto esté vacío
Boolean(function(){}); //Cualquier función es verdadera también
```

_**Enlaces a documentación en mozilla de Truthy y Falsy:**_  
[https://developer.mozilla.org/es/docs/Glossary/Falsy](https://developer.mozilla.org/es/docs/Glossary/Falsy)  
[https://developer.mozilla.org/es/docs/Glossary/Truthy](https://developer.mozilla.org/es/docs/Glossary/Truthy)