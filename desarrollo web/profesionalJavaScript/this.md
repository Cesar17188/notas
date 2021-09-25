# this

_this_ se refiere a un objeto, ese objeto es el que actualmente está ejecutando un pedazo de código.

No se puede asignar un valor a _this_ directamente y este depende de en que scope nos encontramos:

-   Cuando llamamos a _this_ en el **Global Scope o Function Scope**, se hace referencia al objeto _window_. A excepción de cuando estamos en **strict mode** que nos regresará _undefined_.
-   Cuando llamamos a _this_ desde **una función** que está contenida en un objeto, _this_ se hace referencia a ese objeto.
-   Cuando llamamos a _this_ desde una **“clase”**, se hace referencia a la instancia generada por el constructor.

![[Pasted image 20210921180056.png]]

https://www.instagram.com/p/B3Ujh2XBWtG/

https://filisantillan.com/blog/this-en-diferentes-situaciones-y-su-comportamiento/