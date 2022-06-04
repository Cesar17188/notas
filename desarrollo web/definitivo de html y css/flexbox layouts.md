# Flexbox layouts

**Flex** es un tipo de _display_ que permite que el contenedor padre sea flexible a los cambios que puedan tener los elementos hijos en su alineación.

Una vez tengamos el elemento padre con `display: flex` tenemos otras propiedades que podremos usar para nuestro beneficio.

-   **Flex-direction:** Te permite elegir la alineación de los elementos hijos sea en vertical (_column_) u horizontal (_row_), esta alineación viene por defecto.
-   **Justify-content:** Esta propiedad nos permite alinear el contenido de forma horizontal
    -   Valores:
        -   **Flex-start:** Alinear items del flex desde el comienzo.
        -   **Flex-end:** Alinear items desde el final.
        -   **Center:** Alinear items en el centro del contenedor.
        -   **Space-between:** Distribuir items uniformemente, el primer items al inicio, el último al final.
        -   **Space-around:** Distribuir items uniformemente, estos tienen el mismo espacio a su alrededor.
        -   **Space-evenly:** Distribuye uniformemente el espacio entre los items y su alrededor.
-   **Align-items:** Sirve para alinear los elementos hijos de forma vertical.
    -   Valores:
        -   **Flex-start:** Se alinean desde arriba.
        -   **Flex-end:** Se alinean desde abajo.
        -   **Center:** Alinea los item al centro del _eje y_ del contenedor.
        -   **Stretch:** Estira el alto de los elementos hijos al 100% del alto del elemento padre.
        -   **Baseline:** Escala el alto del elemento al tamaño de su contenido.
-   **Flex-wrap:** Permite que un elemento cuyo tamaño sea mayor al de la página haga un salto de línea sin salirse del contenedor, pues este se agranda.
-   **Order:** Especifica el orden utilizado para disponer los elementos en su contenedor flexible. Los elementos estarán dispuestos en orden ascendente según el valor de order.
-   **Flex-grow:** Especifica qué cantidad del espacio restante dentro del contenedor flexible, debería ocupar el ítem en cuestión según su dirección principal, esta última determinada por **`flex-direction`**.
-   **Flex-basis:** Especifica el tamaño inicial de un elemento flexible.