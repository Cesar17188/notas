# Modularidad
La **modularidad** va muy relacionada con las clases y es un principio de la Programación Orientado a Objetos y va de la mano con el Diseño Modular que significa dividir un sistema en partes pequeñas y estas serán nuestros módulos pudiendo funcionar de manera independiente.

La **modularidad** de nuestro código nos va a permitir

-   Reutilizar
-   Evitar colapsos
-   Hacer nuestro código más mantenible
-   Legibilidad
-   Resolución rápida de problemas

Una buena práctica es separando las clases en archivos diferentes.

Modular: Dividir un sitema y así crear módulos independientes, lo que permite evitar un colapso masivo en nuestro código y mejorar la legibilidad.

![[Pasted image 20220503145907.png]]

**Herencia:**  
Es esa gran forma de **reutilizar** el código.  
Por ejemplo si tenemos una clase persona con atributos como nombre, teléfono, email, y métodos cambiarEmail(), y necesitamos crear un clase llamada cliente, esta clase puede heredar de la clase persona todos sus métodos y atributos y también puede tener sus propios atributos como podría ser numeroCliente .