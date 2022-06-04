# Propiedades físicas y lógicas en CSS + Quiz

https://24ways.org/2016/css-writing-modes/

Para este caso, solo basta con considerar tres cosas:

1.  Seleccionar la sección del modelo de caja que necesitamos (padding, border, margin).
2.  Todas las distancias verticales son con block y las distancias horizontales con inline.
3.  Considerar nuestro modo de escritura, para start y end, donde start es donde empezamos a escribir y end donde terminamos.

Con estas tres consideraciones puedes armar la propiedad que quieras sin necesidad de aprendértelas.

![[Pasted image 20220214181427.png]]


**modelo de caja logico **  
el truco es entender bien el BLOCK que de mueve de abajo hacia arriba y el INLINE que se mueve de izquierda a derecha  
**block-start** se refiere al top  
**block-end** se refiere al bottom  
**inline-start** se refiere al left  
**inline-end** se refiere al ringth

![[Pasted image 20220214181555.png]]
![[Pasted image 20220214181605.png]]
![[Pasted image 20220214181815.png]]
![[Pasted image 20220214181612.png]]


sería la **B. border-block-start**, por lo que veo, la nomenclatura es `border-<alignment-type>-<alignmen-position>` (tipo de alineación (block o inline) y posición de alineación (start o end)), por lo que **block** hace referencia al alineamiento vertical y **inline** hace referencia al alineamiento horizontal. Es más, repítelo cuando te vayas a dormir:  
.  
“Block es vertical, Inline es horizontal”  
.  
Jaja, yo sugeriría algo tipo `border: vertical start 1px dotted #ccc`, acaba siendo igual larga pero… habría que pensar en mejores alternativas 🤔.


<h3>MODELOS DE CAJA (Físicas - Lógicas)</h3>

---

1.  **Propiedades físicas**

---

-   **MARGIN:** margin-top | Margin-left | Margin-right | Margin-bottom
    
-   **PADDING:** padding-top | paddding-left | padding-right | padding-bottom
    
-   **BORDER (-size-style-color):** border-top | border-left | border-right | border-bottom
    
-   **POSITIONS** top | left | right | bottom.
    

---

1.  - **Propiedades Lógicas**

---

-   **MARGIN:** Margin-block-start | Margin-inline-start | Margin-inline-end | Margin-block-end
    
-   **PADDING** padding-block-start | paddding-inline-start | padding-inline-end | padding-block-end
    
-   **BORDER(-size-style-color):** border-block-start | border-inline-start | border-inline-end | border-block-end.
    
-   **POSITIONS:** inset-block-start | inset-inline-start | inset-inline-end | inset-block-end