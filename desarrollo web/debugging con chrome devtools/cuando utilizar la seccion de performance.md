# ¿Cuando utilizar la sección de Performance?

El performance hace que los proyectos se puedan abrir en cualquier dispositivo en tiempo real, con cualquier red. Es lo que nos asegura que el usuario tenga la mejor experiencia


Bueno según lo que he podido investigar (corregidme si estoy equivocado) es que el problema esta en la forma en que obtiene una nueva posición para el elemento.

**_Algoritmo no optimizado_**

```
var pos = m.classList.contains('down') ? m.offsetTop + distance : m.offsetTop - distance;
```

Aquí podemos observar que obtiene la posición del elemento con respecto al contenedor más cercano en posición relativa (en este caso body) y esto lo hace para cada iteración y cada elemento teniendo que cada vez volver a consultar esa posición para generar una nueva.

**_Algoritmo optimizado_**

```
var pos = parseInt(m.style.top.slice(0, m.style.top.indexOf('px')));
m.classList.contains('down') ? pos += distance : pos -= distance;
```

Aquí para obtener la posición lee el estilo top anterior del elemento y a partir de ese genera una nueva posición.

La diferencia es que el primer algoritmo (offsetTop) consume mucho más recursos ya que debe consultar del DOM en cada iteración (es una nueva operación para cada elemento y cada iteración), mientras que con el segundo algoritmo (style.top) solamente consulta la posición anterior del estilo almacenado (no debe hacer una nueva operación).



El enlace es este: [https://googlechrome.github.io/devtools-samples/jank/](https://googlechrome.github.io/devtools-samples/jank/)

