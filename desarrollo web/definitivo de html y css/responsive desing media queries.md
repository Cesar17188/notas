# Responsive design: media queries

¿Qué es Responsive Design?  
Son todas esas técnicas que usamos para adaptar nuestras aplicaciones web a la mayor cantidad de pantallas  
250px-Diseno-web-responsive-design.jpg  
Patrones en Reponsive Design:

Mostly Fluid  
Colocación de columnas  
Layout shifter  
Tiny tweaks  
Off canvas  
Para mas información: [https://mediaqueri.es](https://mediaqueri.es/)

Conceptos nuevos:

Viewport: área visible del navegador  
Portrait: vertical  
Landscape: horizontal  
Mobile first: empezar un websit desde la menor resolución soportada  
Deskto first: empezar un websit desde la mayor resolución soportada  
¿Cúal es mejor?: Técnicamente Mobile First

Se debe optimizar para todos los dispositivos. Hay tiene que tener en claro un par de conceptos:

-   **Break points:** cuando la pantalla sea de cierto tamaño, se generará un cambio para reposicionar o redimensionar los contenedores.
-   **Media Queries:** son condicionales. No es la mejor práctica pero aplicándolo al CSS: `@media (min-width: #;) {"código que se aplicará"}` y se aplican para cada tamaño de dispositivo. El pixelaje dado será el **break point**.

Lo más importante es diseñar para movil. Por lo que se debe diseñar con **mobile first**. Es decir, primero diseñar para celular, luego un break point para tablet y finalmente un break point para PC.

Para aplicar **media queries** con buenas prácticas, hay que hacerlo en el **header**. Porque así solo se descarga el código necesario según el dispositivo, mientras que en CSS se descarga todo sin importar nada.

En la tag `link` se colocan los atributos `href`, `rel` y, a partir del segundo archivo, el break point `media="screen and (min-width: #px"`. El **style.css** debe estar hecho para mobile. Luego se pueden crear otros archivos como tablet.css o desktop.css.