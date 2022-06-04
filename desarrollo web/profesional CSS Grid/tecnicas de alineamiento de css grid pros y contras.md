# Técnicas de alineamiento de CSS Grid: pros y contras

https://www.wextensible.com/temas/css3-alinear/block.html

Las técnicas de alineamiento vistas son pertenecientes a CSS2 pero se siguen utilizando a la fecha, claro que estas cuentan con sus ventajas y desventajas.

Margin

-   Ventajas: El valor auto alinea horizontalmente cualquier elemento con cualquier ancho.
-   Desventajas: Alinear verticalmente, ya que, en cada caso, deberán calcularse estos valores.

line-height

-   Ventajas: correcta alineación.
-   Desventajas: si el texto ocupa más de una linea el elemento toma un alto más grande de lo necesario para los cálculos.

table-cell

-   Ventajas: La alineación vertical no esta condicionada por fuentes, tamaños de fuentes o alturas de linea.
-   Desventajas: vertical-align sólo se aplica a elementos inline.

La mayor limitante de todas ellas es que contienen muchas propiedades físicas:

-   margin-top
-   padding-bottom
-   border-right
-   left