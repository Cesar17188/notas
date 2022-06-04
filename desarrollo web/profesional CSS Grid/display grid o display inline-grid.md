# Creando nuestro contenedor: ¿display: grid o display: inline-grid?

![[Pasted image 20220217172443.png]]

<h4>**Ideas/conceptos claves**</h4>

**Display** ⇒ Desplegar, colocar a la vista, exhibir, lucir, Mostar, presentar

**Outer** ⇒ Denota cómo se comporta un elemento en relación a los otros

**Inner** ⇒ como se comportan los hijos directos del elemento

<h4>**Apuntes**</h4>

-   Display ⇒ Define el tipo de visualización de un elemento
    -   Valores:
        -   Inner
        -   Outer
-   Los valores block e inline definen dos cosas
    -   Valor externo (**Outer**)
    -   Valor interno (**Inner**)
-   Cuando usamos `display: grid;` estamos diciendo `display: block grid;`
    -   Es decir que su comportamiento externo sera de tipo bloque
-   Un elemento que tenga los atributos de bloque puede tener:
    -   Margin y padding
    -   width
    -   height
-   Si pensamos en `display: inline-flex;` su relación con otros elementos no sera de bloque sino de línea
-   Siempre volvemos al flujo normal del documento

**RESUMEN:** La diferencia entre grid e inline-grid es el comportamiento externo que tienen con otros elementos, usando grid sera de tipo bloque y usando inline-grid sera de tipo inline

Por cierto, la principal diferencia que yo veo entre `inline` y `block` es que `inline` va a tomar el ancho de sus hijos, es decir, es como si el contenedor se desinflara y acabara midiendo lo mismo que miden los contenedores hijos, en cambio, los block son como un contanador completamente inflado que se extiende a más no poder 🤔.  
.  
Es por eso que cuando ponemos un botón después de haber puesto un input, ambos salen en la misma linea, porque su width se limita al tamaño de los hijos 🤔