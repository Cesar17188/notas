# EventLoop: asíncrona por diseño

## ¿Qué es un Event Loop? 
[[asincronía]]
Es un proceso con un bucle que gestiona, de forma asíncrona, todos los eventos de tu aplicación

El eventloop es un ciclo que funciona indefinidamente y funciona con:
1. la cola de eventos (Event Queue): Va a tener todo lo que ingrese en el código y se ingresa en una cola de eventos y se envia uno a uno hacia el eventloop. Si el event loop puede resolverlo de inmediato lo resuelve de lo contrario lo envia al Thread Pool y ahi comienza a gestionar de forma asíncrona todo. Por ejemplo todas las conexiones a bases de datos, lecturas de archivos o conecciones muy lentas, no bloquean el hilo principal. El eventloop sigue funcionando y todos los eventos que requieren un proceso de mayor duración seran enviados a hilos independientes donde seran resueltos en el tiempo. 

Node.js te permite ejecutar en paralelo diferentes tareas y te permite ver de forma más eficientes y eficaz cada parte del código.

Por que el Thread Pool hace esto? Cada petición que entra en el Thread Pool  crea un hilo (thread) nuevo en el procesador y se va a encargar de que este proceso se ejecute con el tiempo que necesite ejecutarse y cuando termine se dispara un evento y lo devuelve al eventloop, el cual devuelve al event queue y se ejecuta en la página.