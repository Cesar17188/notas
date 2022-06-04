# Limitaciones de CSS y el problema de los elementos flotantes
<h4>**Ideas/conceptos claves**</h4>

**columnas falsas** es una técnica que hace una ilusión cuando una columna es más pequeña que otra se la rellena de un background de tipo imagen

<h4>**Apuntes**</h4>

-   Los primeros diseños de CSS eran una mezcla entre elementos flotantes y posicionados
    
    -   Haciendo que se tengan limitaciones de control
    -   Provocando que la información no se vea uniforme
-   Existía una frustración por la falta de columnas de altura completa
    
    -   Para solucionarlo se creó una técnica de **columnas falsas**
-   Se empieza hablar de Diseño Responsivo
    
    -   Ethan Marcotte ⇒ Tecnica de diseño responsivo
    
    ```css
    @media screen and (max-width: 400px) {
      .figure,
      li#f-mycroft {
        margin-right: 3.317535545023696682%;    /* 21px / 633px */
        width: 48.341232227488151658%;          /* 306px / 633px */
      }  li#f-watson,
      li#f-moriarty {
        margin-right: 0;
      }
    }
    ```
    
-   Se empieza a trabajar con elementos flotantes
    
    -   El problema está que solo funciona cuando se calcula con precisión el ancho y si el contenido tiene la misma altura
    -   La solución fue que se comenzó a trabajar con columnas a través de contenedores para cada una y no con elementos independientes
    -   Tambien se comienza a usar display: table que también se pueden utilizar para elementos que no son elementos de tablas
-   Existen una gran cantidad de técnicas que son simplemente trucos
    
    -   Por ello CSS se ha visto difícil y frágil porque no había herramientas de diseño

**RESUMEN:** En el principio usar CSS implicaba usar trucos, comenzando desde las columnas, columnas de tamaño completo, el diseño responsivo, etc. Era de esta manera debido a que no se tenían muchas herramientas