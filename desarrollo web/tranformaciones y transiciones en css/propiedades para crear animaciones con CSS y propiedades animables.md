
# Propiedades para crear animaciones con CSS y propiedades animables

## Propiedades animables
Animable: que sus valores cambian gradualmente durante un periodo de tiempo determinado

Básicamente la propiedad `transform()` nos permité modificar **cualquier** elemento que tengamos, podemos agrandarla, achicarla, escalarla, moverla, girarla, etc. Solo con esta propiedad ya tenemos las suficiente herramientas para manipular nuestro elemento, es decir, con ella ya podemos hacer que nuestro elemento se mueva a X posición, o que gire X grados 😄.  
.  
Sin embargo, únicamente con esta propiedad no lograremos ver ninguna animación, es decir, si tu usas la propiedad, verás que al cargar la página, el elemento aparecerá ya con la propiedad apicada, por ejemplo, si lo moviste 6 pixeles a la derecha entonces el elemento ya aparecerá movido, y es aquí donde entra `transition`. Esta propiedad permite generar ese movimiento, pero para ello necesita un punto inicial y un punto final.  
.  
Imagina que quieres mover un elemento 6 píxeles a la derecha, entonces, tu estado inicial va a ser 0 píxeles (cuando aún no se ha movido) y tu estado final va a ser 6 píxeles (cuando ya se movió), y la propiedad `transition` se encargará se que ese movimiento se vea suave, es decir, lo animará 👇

![animation](https://media.giphy.com/media/gCSOFQybTbM3pome6c/giphy.gif)

## Propiedades
* ``Transform``
* ``Transition``
* ``Animation``

La propiedad `transition` por si sola nos puede ser de mucha ayuda al momento de aparecer elementos en la pantalla.  
.  
Por ejemplo, si tuviéramos un menu de navegación en la version mobile de nuestro sitio web y quisiéramos que aparezca en la pantalla de manera suave al hacer click, bastaría con aplicar la siguiente declaración al menu: `transition: all 300ms ease-in-out`  
.  
**PERO** aquí viene lo interesante… para que la transición funcione correctamente, la propiedad que esperamos que cambie de manera suave **tiene que contener un valor que pueda aumentar o disminuir progresivamente**, por ejemplo, de 0 a 1.  
.  
**¿Qué quiere decir todo esto?** Que si intentamos hacer que este menu aparezca suavemente solamente haciendo lo siguiente:  
.

```
.menu {
	display: none;
}
.menu.active {
	display: block;
}
```

.  
**ESTO NO FUNCIONARÍA.**  
.  
Para que funcione, una buena opción sería hacer lo siguiente:  
.

```
.menu {
	opacity: 0;
	visibility: hidden;
}
.menu.active {
	opacity: 1;
	visibility: visible;
}
```

.  
De esta manera, el valor ‘‘progresivo’’ del opacity (0 a 1) nos ayuda a que la transición pueda ejecutarse perfectamente. **¿Y el visibility?** Sin esta propiedad, lo único que estaríamos haciendo es hacer invisible el menu, pero el elemento seguiría ahí. Por eso, al agregar un visibility: hidden, podemos quitar el elemento del DOM para evitar interactuar accidentalmente con el mientras este esta invisible.  
.  
Y así como este ejemplo, podemos darnos cuenta que estas transiciones funcionan perfectamente si quisiéramos que un elemento del DOM cambie suavemente el color, opacidad e incluso el tamaño, **todas propiedades con valores '‘progresivos’**’. 😃



