# Qué es reactividad

**Caso práctico de manejo del Estado**:  
.  
1️⃣ Requerimiento general del producto (lo que el usuario debe ver)

-   La aplicación tiene una lista de elementos y un input de búsqueda
    
-   El usuario escribe su filtro / búsqueda
    
-   La aplicación muestra solo los elementos que cumplen con el filtro  
    .  
    2️⃣ Requerimiento detallado del producto (lo que en realidad debemos construir)
    
-   La aplicación tiene un estado / store global para guardar elementos
    
-   Diferentes elementos de la UI se suscriben al estado global para enviar o recibir actualizaciones  
    – El input de búsqueda envía actualizaciones  
    – La lista de elementos recibe actualizaciones
    
-   El usuario escribe su filtro / búsqueda en el input, el input envía el mensaje al estado, el estado cambia y se lo notifica a la lista de elementos, la lista de elementos cambia y el usuario obtiene su respuesta

👀 **Dato curioso**:  
Una opción al trabajar con el estado es hacerlo inmutable. En vez de actualizar directamente el estado, crear un “nuevo” estado cada vez que hacemos una actualización. Y de esta forma podemos hacer cosas muy cool como viajar en el tiempo entre estados (muy útil para debugging).

_Reactividad:_ Es un paradigma, una forma de pensar nuestras aplicaciociones. Deben seguir 2 reglas:

1.  Responsive, es decir, deben ser _resilientes_ (siempre sabe qué hacer) y _escalables_ (no importa con cuánta información debemos trabajar o cuántos usuarios entran a la aplicación, la aplicación debe poder seguir funcionando sin problemas).
2.  Message Driven (Arquitectura basada en mensajes). Deben de haber emisores y receptores de mensajes. Los mensajes se entregan de manera asíncrona.

_Recuerda:_ La arquitectura no es ajena a la programación.

_Estado:_ Es el lugar donde vamos a guardar la información reactiva de nuestros componentes. Son variables a las que nos suscribimos para recibir una notificación cada vez que cambian sus valores.

_Render_: o renderizado, es el proceso por el cual nuestro HTML, pasan a ser información visual en el DOM.

Estrategias de render: Virtual DOM y No Virtual DOM. Ninguna es mejor, depende del caso en particular.

Componente -> Estado -> Render -> Usuario (y vuelve a “Estado”)