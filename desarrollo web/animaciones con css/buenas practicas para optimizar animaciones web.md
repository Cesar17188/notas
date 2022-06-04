# Buenas prácticas para optimizar animaciones web

Teniendo en cuenta lo que vimos en la clase de CSS Triggers, te dejo aquí 5 buenas prácticas para optimizar tus animaciones web:

1.  Usa dentro de lo posible propiedades que solo tengan que pasar por el proceso de Composite.
2.  Si necesitas animar alguna propiedad que sea muy costosa (como width, height, left, entre otras), trata de encontrar otra propiedad que sea menos costosa con la que puedas lograr el mismo resultado (o al menos un resultado similar).
3.  Evita animar muchas propiedades al mismo tiempo.
4.  Si necesitas esconder elementos, normalmente se usan las propiedades opacity y visibility en vez de usar la propiedad display (ya que es una propiedad no animable: [Propiedades que pueden ser animadas](https://developer.mozilla.org/es/docs/Web/CSS/CSS_Transitions/Using_CSS_transitions#propiedades_que_pueden_ser_animadas)).
5.  Evita hacer animaciones que ocurran al hacer scroll, ya que el evento que escucha el scroll se ejecuta una gran cantidad de veces. Mejor espera a llegar a cierto punto de la pantalla y ahí ejecutas la animación.
6. considerar reducir o en algunos casos eliminar las animaciones en dispositivos móviles, ya que el rendimiento no es el mismo.

¿Sabían que existe una librería llamada AOS js o en su acrónimo (Animate on scroll library) ?

.  
Esta es una herramienta desarrollada para hacer algunas animaciones en la web al hacer scroll donde tienen diferentes tipos de atributos y características esto seria un gran complemento para nuestro curso.  
.

Aquí les dejo el enlace y una pequeña muestra de como funciona.

[AOS - Animate on scroll library](https://michalsnik.github.io/aos/)

👇

![](https://media.giphy.com/media/rGLr4Jd9Q8FtZmE3MI/giphy.gif)