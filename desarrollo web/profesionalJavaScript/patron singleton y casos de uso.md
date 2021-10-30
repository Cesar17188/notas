# Patrón Singleton y Casos de Uso

Es un patrón que te asegura que una clase solo tiene una instancia. Esta única instancia puede ser consumida por cualquier otro objeto.

![[Pasted image 20211019203627.png]]

Diagrama [UML](https://es.wikipedia.org/wiki/UML "UML") de una [clase](https://es.wikipedia.org/wiki/Clase_(programaci%C3%B3n_orientada_a_objetos) "Clase (programación orientada a objetos)") que implementa el patrón singleton.

En [ingeniería de _software_](https://es.wikipedia.org/wiki/Ingenier%C3%ADa_de_software "Ingeniería de software"), _**singleton**_ o **instancia única** es un [patrón de diseño](https://es.wikipedia.org/wiki/Patr%C3%B3n_de_dise%C3%B1o "Patrón de diseño") que permite restringir la creación de [objetos](https://es.wikipedia.org/wiki/Programaci%C3%B3n_orientada_a_objetos "Programación orientada a objetos") pertenecientes a una [clase](https://es.wikipedia.org/wiki/Clase_(programaci%C3%B3n_orientada_a_objetos) "Clase (programación orientada a objetos)") o el valor de un tipo a un único objeto.

Su intención consiste en garantizar que una clase solo tenga una [instancia](https://es.wikipedia.org/wiki/Instancia_(inform%C3%A1tica) "Instancia (informática)") y proporcionar un punto de acceso global a ella.

El patrón _singleton_ se implementa creando en nuestra clase un [método](https://es.wikipedia.org/wiki/M%C3%A9todo_(inform%C3%A1tica) "Método (informática)") que crea una instancia del objeto solo si todavía no existe alguna. Para asegurar que la clase no puede ser instanciada nuevamente se regula el alcance del [constructor](https://es.wikipedia.org/wiki/Constructor_(inform%C3%A1tica) "Constructor (informática)") (con [modificadores de acceso](https://es.wikipedia.org/w/index.php?title=Modificador_de_acceso&action=edit&redlink=1 "Modificador de acceso (aún no redactado)") como protegido o privado).

El patrón _singleton_ se implementa creando en nuestra clase un [método](https://es.wikipedia.org/wiki/M%C3%A9todo_(inform%C3%A1tica) "Método (informática)") que crea una instancia del objeto solo si todavía no existe alguna. Para asegurar que la clase no puede ser instanciada nuevamente se regula el alcance del [constructor](https://es.wikipedia.org/wiki/Constructor_(inform%C3%A1tica) "Constructor (informática)") (con [modificadores de acceso](https://es.wikipedia.org/w/index.php?title=Modificador_de_acceso&action=edit&redlink=1 "Modificador de acceso (aún no redactado)") como protegido o privado).

La instrumentación del patrón puede ser delicada en programas con múltiples hilos de ejecución. Si dos [hilos de ejecución](https://es.wikipedia.org/wiki/Hilo_(inform%C3%A1tica) "Hilo (informática)") intentan crear la instancia al mismo tiempo y esta no existe todavía, solo uno de ellos debe lograr crear el objeto. La solución clásica para este problema es utilizar [exclusión mutua](https://es.wikipedia.org/wiki/Exclusi%C3%B3n_mutua_(inform%C3%A1tica) "Exclusión mutua (informática)") en el método de creación de la clase que implementa el patrón.

Las situaciones más habituales de aplicación de este patrón son aquellas en las que dicha clase controla el acceso a un recurso físico único (como puede ser el [ratón](https://es.wikipedia.org/wiki/Rat%C3%B3n_(inform%C3%A1tica) "Ratón (informática)") o un archivo abierto en modo exclusivo) o cuando cierto [tipo de datos](https://es.wikipedia.org/wiki/Tipo_de_datos "Tipo de datos") debe estar disponible para todos los demás objetos de la [aplicación](https://es.wikipedia.org/wiki/Aplicaci%C3%B3n_(inform%C3%A1tica) "Aplicación (informática)").

El patrón _singleton_ provee una única instancia global gracias a que:

-   La propia clase es responsable de crear la única instancia.
-   Permite el acceso global a dicha instancia mediante un método de clase.
-   Declara el constructor de clase como privado para que no sea instanciable directamente.
-   Al estar internamente autoreferenciada, en lenguajes como Java, el recolector de basura no actúa.

## Javascript

Una implementación del patrón singleton en [Javascript](https://es.wikipedia.org/wiki/Javascript "Javascript") es la siguiente:

```js
Singleton = function Singleton$constructor() {
    return { 
        getInstance : function Singleton$getInstance() {
            return this;
        }
    };
}();
```