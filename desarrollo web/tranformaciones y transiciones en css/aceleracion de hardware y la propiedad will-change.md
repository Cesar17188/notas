# Aceleración de hardware y la propiedad will-change
Hay algunas propiedades que no son buenas de _animar o transicionar_, pero esto porque pasa, no todas las propiedades son lo mismo?  
.  
La principal diferencia es que algunas propiedades tienen que lidiar con sus posiciones en la pantalla, lo que significa que el navegador tiene que modificar al DOM y mover algunos pixeles para que algunas propiedades funcionen, esto se debe a que el CSS `engine` funciona en 5 pasos:

-   **Parse**: Aquí solo identifica todas las etiquetas del `archivo.html`
-   **Style**: Aquí el `engine` agrega las etiquetas que vienen el el `documento.css`
-   **Layout**: Aquí el `engine` identifica donde debería aparecer un nodo en la pantalla (aqui es donde se lidia con pixeles, tamaño de monitor, etc.)
-   **Paint**: Aquí también se lidia con pixeles, ya que si un elemento tiene el background rojo, todos los pixeles dentro de ese elemento cambian.
-   **Composite & render**: Esto es la parte final, aqui ya solo se renderiza y se muestran todos los pixeles en la pantalla.

.  
Sabiendo esto, si nuestros elementos a _transicionar_ lidian con pixeles y cambian de cierta forma el DOM, van a causar un mayor esfuerzo a nuestra computadora. Lo que se hace es trabajar con elementos que no dañen al DOM, como lo son `opacity` y `transform.`  
.  
Por ultimo, porque nosotros somo buena onda y el navegador nos cae bien, le podemos decir que se ponga trucha y que empiece a prepararse para optimizar ciertas transformaciones que nosotros sabemos se van a tener que hacer, eso lo hacemos con la propiedad `will-change`


En esta paginas pueden informarse más sobre la propiedad will-change:  
Ingles:  
[https://developer.mozilla.org/en-US/docs/Web/CSS/will-change](https://developer.mozilla.org/en-US/docs/Web/CSS/will-change)  
Español:  
[https://escss.blogspot.com/2014/05/will-change-propiedad-css.html](https://escss.blogspot.com/2014/05/will-change-propiedad-css.html)

```html
<!DOCTYPE html>

<html lang="en">

<head>

 <meta charset="UTF-8">

 <meta http-equiv="X-UA-Compatible" content="IE=edge">

 <meta name="viewport" content="width=device-width, initial-scale=1.0">

 <title>Will change</title>

 <style>

 button {

 width: 100px;

 height: 30px;

 background-color: cornsilk;

 }

 .better {

 will-change: transform;

 transition: transform 500ms;

 }

 .better:hover {

 transform: translateY(5px);

 }

 .worst {

 will-change: margin-top;

 transition: margin-top 500ms;

 }

 .worst:hover {

 margin-top: 5px;

 }

 </style>

</head>

<body>

 <div class="container">

 <button class="better"></button>

 <button class="worst"></button>

 </div>

</body>

</html>
```