# ¿Qué es la inyección de dependencias?

## Singleton

En ingeniería de software, singleton o instancia única es un patrón de diseño que permite restringir la creación de objetos pertenecientes a una clase o el valor de un tipo a un único objeto. Su intención consiste en garantizar que una clase solo tenga una instancia y proporcionar un punto de acceso global a ella.  
Wikipedia.

## Inyección de Dependencias

Inyección de Dependencias (Dependency Injection o DI) es un patrón de diseño en el que una clase requiere instancias de una o más clases y en vez de generarlas dentro de su propio constructor, las recibe ya instanciadas por un mecanismo externo.

## **Conociendo los servicios**

Es la forma en la que Angular hace modular nuestra aplicación y apartar nuestra lógica de negocio.

Los services tienne decodadores y le dicen a angular como debe de coportarse esa clase y hace que se pueda inyectar en otros componentes y servicios.

---

## ¿Qué es la inyección de dependencias?

En la clase pasada creamos un servicio gracias al generador de servicios de angular: ng generate s components/StoreService

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/fbc6d5fd-db20-4864-877c-2cfa8bd6dee8/Untitled.png)

Angular marca on un decorador a los servicios, en este caso sería inyectable. Para que se puedan inyectar en diferentes archivos

Tambien tiene un ambiente o dominio o un alcancé como scope, en este caso es providenIn: ‘’root’, significa que en el modulo que estemos trabajando sin necesidad de estar directamente en el modulo.

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/4760bc07-97bd-40d9-9163-ba1347984c42/Untitled.png)

Los servicios pueden ser inyectados en componentes.

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/f549a4fc-c03b-41ef-a539-dc1b2a0c4190/Untitled.png)

La sintaxis es ir a nuestro componente y es importar nuestro servicio y desde el constructor le damos un modo de acceso. Ya sea privado o publico. Esto depende de como lo queramos manejar en nuestro componente. Le ponemos un tipado en este caso “storeService”;

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/87dbaba9-75eb-4112-a8fe-b030a558ebc0/Untitled.png)

Yo puedo tener varios servicios y como cualquier aplicación podemos tener varios componentes. En este ejemplo tengo dos servicios y tres componentes. El componente A y B están requiriendo del servicio A, mientras que el componente C y B del servicio B. A su vez los componentes pueden inyectas varios servicios a la vez (como en este caso, el componente B).

Cada componente crea una instancia del servicio.

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/b46b407b-2a52-448a-b88d-8dae39cd438e/Untitled.png)

El patrón Singleton se refiere a que si se crea una instancia de algún elemento o instancia en particular y otro componente lo requiere no crea otra instancia sino que guarda la necesaria y devuelve esa referencia a los demás componentes que lo necesiten.

Otro caso que se puede dar en que un servicio puede inyectar a otro. En este escenario el servicio A necesita del servicio B. Los componentes pueden inyectar servicios y los servicios pueden inyectar servicios.

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/1dc2be2c-da4a-416a-bff4-f2a1efbf4a14/Untitled.png)

Donde si hay que tener precaución es no tener una doble inyección

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/60a63a41-2e69-495a-a592-b6f8a707d302/Untitled.png)

Si ambos servicios depende de ellos nos dará un error ya que se bloquean y nos daría un error de referencia circular en Angular