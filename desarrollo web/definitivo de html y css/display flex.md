# Display Flex

Flexbox es una herramienta fundamental ❤️ dejo este juego que te ayuda a entender y diferenciar cada una de las propiedades que ofrece: [https://flexboxfroggy.com/#es](https://flexboxfroggy.com/#es)

Flexbox junto con CSS-Grid son lo más importantes y útil de todo CSS

_**Mini guía de flexbox:**_

**Propiedades en contenedores padre:**  
display:flex;  
flex-direccion: row | column | row-reverse | column-reverse  
flex-wrap: nowrap | wrap | wrap-reverse  
**_Esta siguiente propiedad es un atajo para escribir el flex-direccion y el flex-wrap en una sola línea de código_**  
flex-flow: _Primero escribes dirección_ | _Luego escribes flex-wrap_  
**_Posicionar horizontal_**  
justify-content: flex-star | flex-end | center | space-around | space-between  
**_Posicionar manera vertical_**  
aling-items: flex-star | flex-end | center | stretch | baseline

aling-content: flex-star | flex-end | center | stretch | space-around | space-between “**Aling-conten solo se utiliza varias filas de elementos, pero si es una sola línea usamos aling-items**”

**_Propiedades en elemento hijo_**

order: ; Esto se utiliza para cambiar el orden de nuestros elementos sin cambiar el orden real semantico y correcto de html. Sencillamente colocando números.

aling-self: aling-items: flex-star | flex-end | center | stretch | baseline **“Muy importante, si en el padre del elemento tiene declarado flex-direccion:row; esta propiedad lo acomodara verticalmente. Y si es flex.direccion: column lo ordenara horizontalmente”**

**Flex** es un tipo de **display** que permite que el contenedor padre sea flexible a los cambios que puedan tener los elementos hijos en su alineación.

Una vez tengamos el elemento padre con display **flex** tenemos otras propiedades que podremos usar para nuestro beneficio.

-   **Flex-direction:** Te permite elegir la alineación de los elementos hijos sea en vertical (_column_) u horizontal (_row_), esta alineación viene por defecto.
-   **Justify-content:** Esta propiedad nos permite alinear el contenido de forma horizontal
    -   Valores:
        -   **Flex-start:** Alinear items del flex desde el comienzo.
        -   **Flex-end:** Alinear items desde el final.
        -   **Center:** Alinear items en el centro del contenedor.
        -   **Space-between:** Distribuir _items_ uniformemente, el primer _items_ al inicio, el último al final.
        -   **Space-around:** Distribuir items uniformemente, estos tienen el mismo espacio a su alrededor.
        -   **Space-evenly:** Distribuye uniformemente el espacio entre los items y su alrededor.
-   **Flex-wrap:** Permite que un elemento cuyo tamaño sea mayor al de la página haga un salto de línea sin salirse del contenedor, pues este se agranda.