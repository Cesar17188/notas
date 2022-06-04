# Column drop

Un breve resumen de los patrones de diseño para complementar (Texto tomado desde [developers.google.com](https://developers.google.com/web/fundamentals/design-and-ux/responsive/patterns?hl=es)):

**Mostly Fluid**

---

El patrón Mostly fluid consiste, principalmente, en una cuadrícula fluida. Por lo general, en las pantallas grandes o medianas se mantiene el mismo tamaño y simplemente se ajustan los márgenes en las más anchas.

![Captura.PNG](https://static.platzi.com/media/user_upload/Captura-3066e9e2-a8fb-49ad-af1f-0fd156c6d086.jpg)

**Column Drop**

---

En el caso de los diseños con varias columnas de ancho completo, durante el proceso de colocación de columnas éstas únicamente se colocan de forma vertical debido a que el ancho de la ventana es demasiado reducido para el contenido.  

![Captura.PNG](https://static.platzi.com/media/user_upload/Captura-1523b52e-1e3d-4209-975e-34b32559fd55.jpg)

**Layout shifter**

---

El patrón Layout shifter es el más adaptable, ya que posee varios puntos de interrupción en diferentes anchos de pantalla.

La clave para este diseño es el desplazamiento del contenido, en lugar de su reprocesamiento y colocación debajo de otras columnas. Debido a las diferencias significativas entre cada punto de interrupción principal, es más complejo de mantener, y es posible que se deban realizar cambios dentro de los elementos, no solo en el diseño de contenido general.  

![Captura.PNG](https://static.platzi.com/media/user_upload/Captura-66281cc3-7319-4a62-b2c0-180657c93723.jpg)