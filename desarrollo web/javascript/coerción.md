# Coerción
Coerción es la forma en la que podemos cambiar un tipo de valor a otro, existen dos tipos de coerción:  
* Coerción implícita = es cuando el lenguaje nos ayuda a cambiar el tipo de valor.  
* Coerción explicita = es cuando obligamos a que cambie el tipo de valor.

ParseInt vs Number

ParseInt: Analiza la cadena desde el primer dígito, hasta que encuentre algo que no sea dígito y devuelve lo que haya analizado.  
Ejemplo:  
parseInt(“123hui”) //123  
Number: Busca convertir toda la cadena en un número, por lo que al encontrarse con un elemento que no sea diginto nos dara como resultado NAN.  
Ejemplo:  
Number(“123hui”) //NaN

es necesario cuando solicitemos que un usuario ingrese un valor número, transformar el ingreso del usuario a un tipo númerico para realizar los cálculos matemáticos.
