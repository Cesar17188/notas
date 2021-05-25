# Switch

La `switch`declaración se utiliza para realizar diferentes acciones en función de diferentes condiciones.

Utilice la `switch`instrucción para seleccionar uno de los muchos bloques de código que se ejecutarán.

### Sintaxis

switch(_expression_) {  
  case _x_:  
 _// code block_    break;  
  case _y_:  
 _// code block_    break;  
  default:  
    // _code block_  
}

Así es como funciona:

-   La expresión de cambio se evalúa una vez.
-   El valor de la expresión se compara con los valores de cada caso.
-   Si hay una coincidencia, se ejecuta el bloque de código asociado.
-   Si no hay coincidencia, se ejecuta el bloque de código predeterminado.

### Ejemplo

El `getDay()`método devuelve el día de la semana como un número entre 0 y 6.

(Domingo = 0, Lunes = 1, Martes = 2 ..)

Este ejemplo utiliza el número del día de la semana para calcular el nombre del día de la semana:

```js
switch (new Date().getDay()) {  
  case 0:  
    day = "Sunday";  
    break;  
  case 1:  
    day = "Monday";  
    break;  
  case 2:  
     day = "Tuesday";  
    break;  
  case 3:  
    day = "Wednesday";  
    break;  
  case 4:  
    day = "Thursday";  
    break;  
  case 5:  
    day = "Friday";  
    break;  
  case 6:  
    day = "Saturday";  
}
```

El resultado del día será:

`Sunday`