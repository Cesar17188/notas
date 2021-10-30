# IntersectionObserver

Sirve para observar elementos y si cruzan un umbral que nosotros definimos nos lo va a notificar para tomar acción.

El umbral se define por el porcentaje que tiene intersección con el _viewport_, con la parte visible de nuestra página.

## Intersection Observer API

La API Observador de Intersección, provee una vía para, de forma asíncrona, observar cambios en la intersección de un elemento con un elemento ancestro o con el [viewport](https://developer.mozilla.org/es/docs/Glossary/viewport "viewport: Un viewport representa la región poligonal (normalmente rectangular) en gráficas de computación que está siendo visualizada en ese instante. En términos de navegadores web, se refiere a la parte del documento que usted está viendo, la cual es actualmente visible en su ventana (o la pantalla, si el documento está siendo visto en modo pantalla completa). El contenido fuera del viewport no es visible en la pantalla hasta que sea desplazado dentro de él.") del documento de nivel superior.

La información sobre intersección es necesaria por muchas razones, tales como:

-   Lazy-loading de imágenes u otro contenido a medida que la página se desplaza.
-   Implementación de “scroll infinito” de sitios web, donde más y más contenido se carga y muestra a medida que usted hace scroll, de forma que el usuario no tiene que pasar páginas.
-   Informes de visualizaciones de anuncios para calcular ingresos por publicidad.
-   Decidir si deben realizarse tareas o procesos de animación basados en si el usuario verá o no el resultado.

## [Creando un intersection observer](https://developer.mozilla.org/es/docs/Web/API/Intersection_Observer_API#Creando_un_intersection_observer)

Crear el intersection observer llamando a su constructor y pasándole una función callback para que se ejecute cuando un nivel (threshold) sea cruzado en una u otra dirección:

```js
var options = {
  root: document.querySelector('#scrollArea'),
  rootMargin: '0px',
  threshold: 1.0
}

var observer = new IntersectionObserver(callback, options);
```

Un threshold de 1.0 significa que cuando el 100% del elemento target está visible dentro del elemento especificado por la opción `root`, la función callback es invocada.

## Opciones de Intersection observer

El objeto `options` pasado al constructor [`IntersectionObserver()`](https://developer.mozilla.org/es/docs/Web/API/IntersectionObserver/IntersectionObserver "La documentación acerca de este tema no ha sido escrita todavía . ¡Por favor  considera contribuir !") le deja controlar las circunstancias bajo las cuales la función callback del observer es invocada. Tiene los siguientes campos:

`root`

El elemento que es usado como viewport para comprobar la visibilidad de elemento target. Debe ser un elemento ascendiente del target. Por defecto se toma el viewport del navegador si no se especifica o si se especifica como `null`.

`rootMargin`

Margen alrededor del elemeto root. Puede tener valores similares a los de CSS [`margin`](https://developer.mozilla.org/es/docs/Web/CSS/margin "La propiedad CSS margin establece el margen para los cuatro lados. Es una abreviación para evitar tener que establecer cada lado por separado con las otras propiedades de margen:  margin-top, margin-right, margin-bottom y margin-left.") property, e.g. "`10px 20px 30px 40px"` (top, right, bottom, left). Los valores pueden ser porcentajes. Este conjunto de valores sirve para aumentar o encoger cada lado del cuadro delimitador del elemento root antes de calcular las intersecciones. Por defecto son todos cero.

`threshold`

Es un número o un array de números que indican a que porcentaje de visibilidad del elemento target, la función callback del observer debería ser ejecutada. Si usted quiere que se detecte cuando la visibilidad pasa la marca del 50%, debería usar un valor de 0.5. Si quiere ejecutar la función callback cada vez que la visibilidad pase otro 25%, usted debería especificar el array [0, 0.25, 0.5, 0.75, 1]. El valor por defecto es 0 (lo que significa que tan pronto como un píxel sea visible, la función callback será ejecutada). Un valor de 1.0 significa que el umbral no se considera pasado hasta que todos los pixels son visibles.

## Determinando un elemento para ser observado

Una vez usted ha creado el observer, necesita darle un elemento target para observar:

```js
var target = document.querySelector('#listItem');
observer.observe(target);
```

Cuando el elemento target encuentra un threshold especificado por el `IntersectionObserver`, la función callback es invocada. La función callback recibe una lista de objetos [`IntersectionObserverEntry`](https://developer.mozilla.org/es/docs/Web/API/IntersectionObserverEntry "La documentación acerca de este tema no ha sido escrita todavía . ¡Por favor  considera contribuir !") y el observer:

```js
var callback = function(entries, observer) { 
  entries.forEach(entry => {
    // Cada entry describe un cambio en la intersección para
    // un elemento observado
    //   entry.boundingClientRect
    //   entry.intersectionRatio
    //   entry.intersectionRect
    //   entry.isIntersecting
    //   entry.rootBounds
    //   entry.target
    //   entry.time
  });
};
```

Asegúrese de que su función callback se ejecute sobre el hilo principal. Debería operar tan rápidamente como sea posible; si alguna cosa necesita tiempo extra para ser realizada, use [`Window.requestIdleCallback()`](https://developer.mozilla.org/es/docs/Web/API/Window/requestIdleCallback "El método window.requestIdleCallback() encola la función que será ejecutada en periodos de inactividad del navegador permitiendo a los desarrolladores ejecutar en segundo plano tareas de baja prioridad del bucle de eventos, sin perjudicar la latencia de eventos principales como animaciones o respuestas a entradas. La funciones son ejecutadas normalmente en orden FIFO (primero en entrar primero en salir) salvo que se alcance el timeout definido de la función antes de que el navegador la ejecute.").

También, note que si especifica la opción `root`, el elemento target debe ser un descendiente del elemento root.

![[Pasted image 20211012182236.png]]