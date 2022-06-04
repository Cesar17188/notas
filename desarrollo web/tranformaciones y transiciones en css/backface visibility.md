# Backface visibility
Con la propiedad `backface-visibility` podemos hacer cosas geniales como tarjetitas que se voltean 😈. Por ejemplo, estas tarjetitas que hice para un blog de Platzi donde aprendemos a hacer un juego con Vue 👀👇  
.  

![Backface](https://media.giphy.com/media/pdJ4jhBTW07fEC6zdH/giphy.gif)  
.  
El concepto es simple, puede costar un poquito entenderlo al inicio, pero al cuando lo entiendes se vuelve sencillo:  
.  
Tenemos un elemento, ese elemento tiene una parte de adelante y una parte de atrás, no importa si el elemento es plano. La propiedad `backface-visibility` mostrará u ocultará esa cara de atrás dependiendo de lo que esta propiedad indique.  
.  
¿Esto que significa? Bueno, que si pones tu `backface-visibility` como `hidden`, la parte de atrás de tu tarjeta no se verá, pero la de adelante sí; es decir, si tu le pusieras un `transform: rotateX(180deg)` no verías nada, porque justamente estarías viendo la cara de atrás del elemento, que está oculta por el `backface-visibility` ☝👀.  
.  
Por cierto, si quieres ver el blog donde hago el juego usando estas propiedades de `backface-visibility` puedes mirarlo aquí: [Guía desde cero: tu propio juego de Rick and Morty con Vue.js](https://platzi.com/blog/juego-rick-morty-vuejs/)