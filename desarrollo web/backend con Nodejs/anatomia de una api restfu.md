# Anatomía de una API Restful

**Rest**: que significa _**representational state transfer (rest)**_ es un estilo de arquitectura _para construir web services_, no es un standart pero si existe una especificación creada por [Roy Fielding](https://es.wikipedia.org/wiki/Roy_Fielding) el es el confundador de apache server y director de Apache Software fundation también actualmente trabaja como director de adobe.

**Las peticiones HTTP van acompañadas de un “verbo” que define el tipo de petición:**

-   **GET**: Lectura de datos.
-   **PUT**: Reemplazar datos.
-   **PATCH**: Actualizar datos en un recurso específico.
-   **POST**: Creación de datos.
-   **DELETE**: Eliminación de datos.

No es recomendable habilitar un [endpoint](https://code.tutsplus.com/es/tutorials/a-beginners-guide-to-http-and-rest--net-16340) de tipo PUT y DELETE para toda nuestra colección de datos, sólo hacerlos para recursos específicos, ya que no queremos que por error se puedan borrar todos nuestros datos.