# Pseudo-clases y pseudo-elementos en las animaciones

También es bueno tener en cuenta que las pseudo-clases y los pseudo-elementos son distintos entre sí, ambos se escriben como una extensión de nuestro selector después de dos puntos: `:hover`, `after`; sin embargo, una pseudo-clase es básicamente un estado que podemos manipular, por ejemplo, el estado hover, el estado active, el estado visited, etc.  
.  
Un pseudo-elemento, como su nombre lo dice, es un elemento que no está declarado explícitamente desde nuestro HTML, pero lo podemos crear con CSS, por ejemplo `before` y `after`, ¿cómo sabes que es un pseudo-elemento y no una pseudo-clase? ¡Fácil! Simplemente preguntate: ¿existe el estado `before`? Verás que la respuesta es “no”, no existe ningún estado `before` porque este es un pesudo-elemento, por el contrario, si te preguntas: ¿existe el estado `:hover`? Aquí la respuesta es “sí”, porque `hover` sí es una pseudo-clase 😄  
.  
En este link puedes encontrar una lista de pseudo-clases diponibles:

[Indice de las pseudo-clases estándar](https://developer.mozilla.org/es/docs/Web/CSS/Pseudo-classes#indice_de_las_pseudo-clases_est%C3%A1ndar)

Y en este otro verás una lista de los pseudoelementos disponibles 😉:

[Lista de pseudoelementos](https://developer.mozilla.org/es/docs/Web/CSS/Pseudo-elements#lista_de_pseudoelementos)


Una nota importante con la pseudo clase hover es que hay dispositivos a los que no se le puede hacer hover porque no tienen puntero (siendo los celulares el ejemplo más claro) y es posible que añadirle estilos que dependan de un hover pueda ser contraproducente para la funcionalidad de estos elementos.  
.  
Lo bueno es que ahora CSS tiene un media query llamado **hover** que permite agregarle estilos solamente en dispositivos que permiten hacer hover.  
.  
Por ejemplo si tenemos algún tag a que queremos que al hacer hover tenga un background-color distinto pero sólo queremos que pase en equipos que acepten hover podríamos usar esta línea de código:

```
@media (hover: hover) {
  a:hover {
    background: yellow;
  }
}
```

Es importante tener esto en cuenta por ejemplo en caso de que hagamos una card que sólo muestra el contenido completo si haces hover sobre esta. Esto obviamente no sería posible desde un celular, entonces lo que se haría sería dejar todas las propiedades de la card sin animaciones y en el media query de hover poner todo lo respecto a su animación para que pueda ser accesible a través de un celular o una tablet sin problemas.


#### Lecturas recomendadas

[![](https://www.google.com/s2/favicons?domain=https://htmlcolorcodes.com//assets/images/favicon.png)HTML Color Codeshttps://htmlcolorcodes.com/
](https://htmlcolorcodes.com/)[

![](https://www.google.com/s2/favicons?domain=https://developer.mozilla.org/en-US/docs/Web/CSS/:hover/favicon-48x48.97046865.png)

:hover - CSS: Cascading Style Sheets | MDN

https://developer.mozilla.org/en-US/docs/Web/CSS/:hover

](https://developer.mozilla.org/en-US/docs/Web/CSS/:hover)[

![](https://www.google.com/s2/favicons?domain=https://developer.mozilla.org/en-US/docs/Web/CSS/:focus/favicon-48x48.97046865.png)

:focus - CSS: Cascading Style Sheets | MDN

https://developer.mozilla.org/en-US/docs/Web/CSS/:focus

](https://developer.mozilla.org/en-US/docs/Web/CSS/:focus)[

![](https://www.google.com/s2/favicons?domain=https://developer.mozilla.org/en-US/docs/Web/CSS/:active/favicon-48x48.97046865.png)

:active - CSS: Cascading Style Sheets | MDN

https://developer.mozilla.org/en-US/docs/Web/CSS/:active

](https://developer.mozilla.org/en-US/docs/Web/CSS/:active)[

![](https://www.google.com/s2/favicons?domain=https://developer.mozilla.org/en-US/docs/Web/CSS/:disabled/favicon-48x48.97046865.png)

:disabled - CSS: Cascading Style Sheets | MDN

https://developer.mozilla.org/en-US/docs/Web/CSS/:disabled





](https://developer.mozilla.org/en-US/docs/Web/CSS/:disabled)