# Grid y las relaciones padre e hijos inmediatos + Quíz
![[Pasted image 20220215164622.png]]
<h4>**Ideas/conceptos claves**</h4>

**CSS Grid** se puede utilizar para lograr muchos diseños diferentes. También se destaca por permitir dividir una página en áreas o regiones principales, por definir la relación en términos de tamaño, posición y capas entre partes de un control construido a partir de primitivas HTML.

<h4>**Apuntes**</h4>

-   Grid nos permite crear rejillas que tenga **filas** y **columnas**
    
-   En este momento se tiene una mayor complejidad en el diseño web
    
-   Siempre se tendrá un Contenedor **(padre)**
    
    -   Los items **(elementos hijos)** serán los que estarán dentro de este contenedor
        -   Los hijos también pueden ser padres
    -   Todos los padres tienen que tener:
    
    ```css
    display: grid;
    ```
    

**RESUMEN:** Usar CSS Grid consiste en tener un elemento padre el cual se definirá la propiedad display grid, sus elementos hijos serán afectados por esta regla, siendo posicionados según la forma establecida la grilla.