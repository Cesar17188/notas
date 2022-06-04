# Variables

**Para que nos sirven?**  
Nos servirán para guardar valores que reiteradamente ocuparemos en el desarrollo de nuestro proyecto. Realmente se le ve mas utilidad en proyectos grandes. Pero claro, es importante conocerlo desde ahora.

**Como se declara?**  
Normalmente se declara dentro de **:root** ta que serán variables globales.  
y se declaran de la siguiente manera:

```
:root {
  --primary-color: #322f3d;
  --secondary-color: #8d93ab;
  --font-color: white;
  --font: 1.8rem;
  --titles: 3rem;
}
```

Indicando con **– (Doble guión)** y seguido del **Nombre de la variable** y el **valor **que este tendra.

**Como utilizar las variables?**  
Se utilizaran las variables gracias a la _Función_ **var()** y se usa de la siguiente manera.

```
header {
  background-color: var(--primary-color);
  width: 100%;
  height: 10rem;
  color: var(--font-color);
  font-size: var(--titles);
  text-align: center;
}
```

Espero les guste el mini resumen. Saludos 😃

Adicionalmente **`var()`** tambien puede recibir un valor por defecto en caso de no poder encontrar la variable.

```css
var( <custom-property-name> , <declaration-value>? )
```

También funcionan las variables al aplicar márgenes:

![](https://css-tricks.com/wp-content/uploads/2016/10/grid.gif)