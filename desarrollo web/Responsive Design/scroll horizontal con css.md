# Scroll horizontal con CSS
[overflow-x](https://developer.mozilla.org/en-US/docs/Web/CSS/overflow-x)

La propiedad de CSS overflow-x establece lo que se muestra cuando el contenido desborda los bordes izquierdo y derecho de un elemento a nivel de bloque. Puede que no sea nada, una barra de desplazamiento o el contenido adicional.

[overscroll-behavior](https://developer.mozilla.org/en-US/docs/Web/CSS/overscroll-behavior)

la propiedad de css overscroll-behabior establece lo que hace un navegador cuando alcanza el límite de un área de desplazamiento. Es una abreviatura de overscroll-behavior-x y overscroll-behavior-y.

[scroll-snap-type](https://developer.mozilla.org/en-US/docs/Web/CSS/scroll-snap-type)

La propiedad CSS scroll-snap-type establece qué tan estrictamente se aplican los puntos de snap en el contenedor de desplazamiento en caso de que haya uno

```css 
.plans-container--slider{

 display: flex;

 height: 316px;

 overflow-x: scroll;

 overscroll-behavior-x: contain;

 scroll-snap-type: x proximity;

 /* gap: 15px; */

}

.plans-container--card {

 position: relative;

 scroll-snap-align: center;

 width: 70%;

 min-width: 230px;

 max-width: 300px;

 height: 250px;

 margin: 50px 10px 0;

 padding: 0 15px;

 background-color: var(--just-white);

 border-radius: 15px;

 box-shadow: 0 4px 8px rgba(89, 73, 30, 0.16);
```