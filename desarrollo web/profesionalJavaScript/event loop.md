# Event Loop

El **Event Loop** hace que Javascript parezca ser multihilo a pesar de que corre en un solo proceso.

Javascript se organiza usando las siguientes estructuras de datos:

-   **Stack**. Va apilando de forma organizada las diferentes instrucciones que se llaman. Lleva así un rastro de dónde está el programa, en que punto de ejecución nos encontramos.
-   **Memory Heap**. De forma desorganizada se guarda información de las variables y del scope.
-   **Schedule Tasks**. Aquí se agregan a la cola, las tareas programadas para su ejecución.
-   **Task Queue**. Aquí se agregan las tares que ya están listas para pasar al stack y ser ejecutadas. El stack debe estar vacío para que esto suceda.
-   **MicroTask Queue**. Aquí se agregan las promesas. Esta Queue es la que tiene mayor prioridad.

El Event Loop es un loop que está ejecutando todo el tiempo y pasa periódicamente revisando las queues y el stack moviendo tareas entre estas dos estructuras.

La explicaión del profesor es asombrosa. Explicar cómo funciona el EventLoop de una forma tan sencilla es asombroso.  
.  
Aquí dejo un resumen de todo el funcionamiento de lo que vimos en esta clase.  
.

Las funciones son empujadas al **call stack** cuando son invocadas y se sacan cuando **devuelven un valor**

.  

![](https://i.imgur.com/PO5JkWi.gif)

.

**`setTimeOut`** es proveído por el navegador, la **Web API** se encarga del **callback** que le pasemos.

.  

![](https://i.imgur.com/ahBEKn5.gif)

.  
Cuando el timer ha terminado (1000ms en este caso), el **callback** se pasa al **callback queue**  
.  

![](https://i.imgur.com/rYkNwPA.gif)

.  
El **Event Loop** mira hacia el **callback queue** y al **call stack**. Si el call stack está vacío, este empuja el primer elemento de la cola en el stack.

.  

![](https://i.imgur.com/IIhomCu.gif)  
.  
El callback es añadido al call stack para luego ser ejecutado. Una vez retorna un valor, este es sacado de call stack.

.  

![](https://i.imgur.com/HMbjl9o.gif).  
.  
Este pequeño resumen es sacado del post de **[@lydiahallie](https://twitter.com/lydiahallie) ** **[✨♻️ JavaScript Visualized: Event Loop](https://dev.to/lydiahallie/javascript-visualized-event-loop-3dif)** donde también se explica muy bien como funciona el _Event Loop_

![[Pasted image 20210930201642.png]]