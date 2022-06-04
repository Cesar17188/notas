# Modos de escritura y ejes de alineamiento + Reto

1.  La propiedad writing-mode define si los renglones de texto se disponen horizontal o verticalmente y la dirección en que avanzan los bloques.

**horizontal-tb**  
El contenido fluye horizontalmente de izquierda a derecha y verticalmente de arriba hacia abajo. El próximo renglón horizontal se posiciona debajo del renglón anterior.

**vertical-rl**  
El contenido fluye verticalmente de arriba hacia abajo y horizontalmente de derecha a izquierda. El próximo renglón vertical se posiciona a la izquierda del renglón anterior.

**vertical-lr**  
El contenido fluye verticalmente de arriba hacia abajo y horizontalmente de izquierda a derecha. El próximo renglón vertical se posiciona a la derecha del renglón anterior.

**sideways-rl**  
El contenido fluye verticalmente de arriba hacia abajo y todos los glifos, incluidos aquellos de los sistemas de escritura verticales, se colocan de lado hacia la derecha.

**sideways-lr**  
El contenido fluye verticalmente de arriba hacia abajo y todos los glifos, incluidos aquellos de los sistemas de escritura verticales, se colocan de lado hacia la izquierda.

1.  Cosas a tener en cuenta a la hora de usar writing mode:

-   El modo de escritura.  
    -La dirección.  
    -La orientación del texto.

Para esto hay que ver los elementos bloque y elementos en linea.

**display-block:** (horizontal)

-   Ocupan todo el espacio de su elemento padre (contenedor).  
    -Fuerzan un salto de línea (ocupan todo el ancho disponible).  
    -Respetan el width, el height, el margin-top y el margin-bottom indicados por el usuario.  
    -Algunos son:  
    div, p, h1, h2, h3, h4, h5, h6, hr, ol, ul, table, li.

**display-inline:** (vertical)  
-Son apilables.  
-No tienen ni margin-top ni margin-bottom (por mucho que se lo indiques en el CSS).  
-Si tienen margin-left y margin-right.  
No respetan ni width ni height.  
-Estas medidas dependerán del tamaño en píxels de su contenido.  
-Algunos son: a, span, label, strong, br, input, textarea, abbr,

![CSS-Display.png](https://static.platzi.com/media/user_upload/CSS-Display-d027f777-8a54-4c92-b526-49c222f360fb.jpg)

Por cierto, la propiedad `overflow: hidden;` sirve para **ocultar** cualqueir elemento hijo que se salga del elemento padre (siempre y cuando el elemento padre tenga dicha propiedad). Por ejemplo, si tu elemento padre tiene una altura de 500px, pero dentro tienes un texto que rebasa esos 500px, con un `overflow: hidden;` en el padre puedes hacer que se oculte todo lo que se salga 😄.  
.  
**Sin `overflow: hidden`:**  

![soh.png](https://static.platzi.com/media/user_upload/soh-e9d1dd7d-712a-4236-941f-362b90cd5be2.jpg)  
.  
**Con `overflow: hidden`:**  

![coh.png](https://static.platzi.com/media/user_upload/coh-fd060aab-1de7-4ca8-bcf8-fc37a979a2a5.jpg)  
.  
También es muy útil para usarla como máscaras de recorte 👀.