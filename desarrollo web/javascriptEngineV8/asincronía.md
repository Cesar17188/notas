# Asincronía

Por default corre una tarea a la vez – Sincronismo  
Ahora veremos que es el asincronismo  
Memory Heap: Espacio donde se guardan funciones y variables  
Call Stack: Donde se apilan todas las tareas que tenemos que hacer con Javascript  
Web API´s (Ofrecidas por el navegador para manipular lo siguiente)

-   Dom(document)
-   AJAX(XMLHttpRequest)
-   Timeout(setTimeout)  
    Call Back Queue: El orden en que se van a ejecutar a funciones  
    Al momento de usar asincronismo sacamos funciones del Call Back Queue que no serán ejecutadas por javascript y serán ejecutadas por el navegador despues  
    Ejemplo

```
console.log('taco 1')
console.log('taco 2')
console.log('taco 3')
setTimeout(()=>{
    console.log('torta 1')
},1000)
console.log('taco 4')
setTimeout(()=>{
    console.log('torta 2')
},500)
setTimeout(()=>{
    console.log('torta 3')
},0)

```

![](https://res.cloudinary.com/practicaldev/image/fetch/s--BLtCLQcd--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_66%2Cw_880/https://devtolydiahallie.s3-us-west-1.amazonaws.com/gif14.1.gif)