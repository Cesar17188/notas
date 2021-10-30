# ¿Cómo funciona el Patrón Observer?

En esta clase Richard Kaufman, tu profesor en el Curso profesional de JavaScript, nos explica el funcionamiento del patrón observer y como implementarlo.

El patrón observer se compone de un sujeto que ofrece mecanismos de suscripción y desuscripción a múltiples observadores que quieren ser notificados de los cambios en dicho sujeto. Cada observador expone un método de update que es usado por el sujeto para notificar cualquier cambio a todos los suscritos.

Es uno de los patrones más utilizados, algunos ejemplos típicos son:

-   Newsletter
-   Sockets
-   Listeners en páginas web

## Observer (patrón de diseño)

**Observador** (en [inglés: Observer](https://en.wikipedia.org/wiki/Observer_pattern "en:Observer pattern")) es un [patrón de diseño](https://es.wikipedia.org/wiki/Patr%C3%B3n_de_dise%C3%B1o "Patrón de diseño") de _[software](https://es.wikipedia.org/wiki/Software "Software")_ que define una dependencia del tipo _uno a muchos_ entre objetos, de manera que cuando uno de los objetos cambia su estado, notifica este cambio a todos los dependientes. Se trata de un _patrón de comportamiento_ (existen de tres tipos: creación, estructurales y de comportamiento), por lo que está relacionado con algoritmos de funcionamiento y asignación de _responsabilidades_ a [clases](https://es.wikipedia.org/wiki/Clase_(inform%C3%A1tica) "Clase (informática)") y [objetos](https://es.wikipedia.org/wiki/Objeto_(programaci%C3%B3n) "Objeto (programación)").

Los patrones de comportamiento describen no solamente estructuras de relación entre objetos o clases sino también _esquemas de comunicación_ entre ellos y se pueden clasificar en función de que trabajen con clases (método plantilla) u objetos (cadena de responsabilidad, comando, iterador, recuerdo, observador, estado, estrategia, visitante).

La variación de la encapsulación es la base de muchos patrones de comportamiento, por lo que cuando un aspecto de un programa cambia frecuentemente, estos patrones definen un objeto que encapsula dicho aspecto. Los patrones definen una clase abstracta que describe la encapsulación del objeto.

Este patrón también se conoce como el patrón de publicación-inscripción o modelo-patrón. Estos nombres sugieren las ideas básicas del patrón, que son: el objeto de datos, que se le puede llamar Sujeto a partir de ahora, contiene atributos mediante los cuales cualquier objeto observador o vista se puede suscribir a él pasándole una _referencia_ a sí mismo. El Sujeto mantiene así una lista de las referencias a sus observadores. Los observadores a su vez están obligados a implementar unos métodos determinados mediante los cuales el Sujeto es capaz de notificar a sus observadores suscritos los cambios que sufre para que todos ellos tengan la oportunidad de refrescar el contenido representado. De manera que cuando se produce un cambio en el Sujeto, ejecutado, por ejemplo, por alguno de los observadores, el objeto de datos puede recorrer la lista de observadores avisando a cada uno. Este patrón suele utilizarse en los [entornos de trabajo](https://es.wikipedia.org/wiki/Framework "Framework") de interfaces gráficas orientados a objetos, en los que la forma de capturar los eventos es suscribir _listeners_ a los objetos que pueden disparar eventos.

El patrón observador es la clave del patrón de arquitectura [Modelo Vista Controlador](https://es.wikipedia.org/wiki/Modelo_Vista_Controlador "Modelo Vista Controlador") (MVC).[1](https://es.wikipedia.org/wiki/Observer_(patr%C3%B3n_de_dise%C3%B1o)#cite_note-jont-1)​ De hecho el patrón fue implementado por primera vez en el MVC de [Smalltalk](https://es.wikipedia.org/wiki/Smalltalk "Smalltalk") basado en un entorno de trabajo de interfaz.[2](https://es.wikipedia.org/wiki/Observer_(patr%C3%B3n_de_dise%C3%B1o)#cite_note-gang-2)​ Este patrón está implementado en numerosos [bibliotecas](https://es.wikipedia.org/wiki/Biblioteca_(inform%C3%A1tica) "Biblioteca (informática)") y sistemas, incluyendo todos los _toolkits_ de [GUI](https://es.wikipedia.org/wiki/GUI "GUI").

Patrones relacionados: [publicador-subscriptor](https://es.wikipedia.org/w/index.php?title=Publicador-Subscriptor_(patr%C3%B3n_de_dise%C3%B1o)&action=edit&redlink=1 "Publicador-Subscriptor (patrón de diseño) (aún no redactado)"), [mediador](https://es.wikipedia.org/wiki/Mediator_(patr%C3%B3n_de_dise%C3%B1o) "Mediator (patrón de diseño)"), _[singleton](https://es.wikipedia.org/wiki/Singleton "Singleton")_.

## Objetivo

Definir una dependencia uno a muchos entre objetos, de tal forma que cuando el objeto cambie de estado, todos sus objetos dependientes sean notificados automáticamente. Se trata de desacoplar la clase de los objetos clientes del objeto, aumentando la modularidad del lenguaje, creando las mínimas dependencias y evitando bucles de actualización ([espera activa](https://es.wikipedia.org/w/index.php?title=Espera_espera_activa&action=edit&redlink=1 "Espera espera activa (aún no redactado)") o [sondeo](https://es.wikipedia.org/wiki/Polling "Polling")). En definitiva, normalmente, se usará el patrón observador cuando un elemento _quiere_ estar pendiente de otro, sin tener que estar comprobando de forma continua si ha cambiado o no.

## Motivación

Si se necesita consistencia entre clases relacionadas, pero con independencia, es decir, con un bajo [acoplamiento](https://es.wikipedia.org/wiki/Acoplamiento_inform%C3%A1tico "Acoplamiento informático").

## Estructura

[

![EstructuraPatronObservador.png](https://upload.wikimedia.org/wikipedia/commons/thumb/9/97/EstructuraPatronObservador.png/600px-EstructuraPatronObservador.png)](https://commons.wikimedia.org/wiki/File:EstructuraPatronObservador.png)

## Participantes

Habrá sujetos concretos cuyos cambios pueden resultar interesantes a otros y observadores a los que al menos les interesa estar pendientes de un elemento y en un momento dado, reaccionar ante sus notificaciones de cambio. Todos los sujetos tienen en común que un conjunto de objetos quieren estar pendientes de ellos. Cualquier elemento que quiera ser observado tiene que permitir indicar:

1.  “Estoy interesado en tus cambios”.
2.  “Ya no estoy interesado en tus cambios”.

El observable tiene que tener, además, un mecanismo de aviso a los interesados.

A continuación se detallan a los participantes de forma desglosada:

-   **Sujeto (_subject_):**

El sujeto proporciona una interfaz para agregar (_attach_) y eliminar (_detach_) observadores. El Sujeto conoce a todos sus observadores.

-   **Observador (_observer_):**

Define el método que usa el sujeto para notificar cambios en su estado (_update_/_notify_).

-   **Sujeto concreto (_concrete subject_):**

Mantiene el estado de interés para los observadores concretos y los notifica cuando cambia su estado. No tienen porque ser elementos de la misma jerarquía.

-   **Observador concreto (_concrete observer_):**

Mantiene una referencia al sujeto concreto e implementa la interfaz de actualización, es decir, guardan la referencia del objeto que observan, así en caso de ser notificados de algún cambio, pueden preguntar sobre este cambio.