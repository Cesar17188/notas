# Técnicas de alineamiento con Flexbox

**Encontré una forma de resolverlo utilizando una única declaración en cada container.**

Como ya mencionaron, existe la propiedad [_place-content_](https://developer.mozilla.org/en-US/docs/Web/CSS/place-content), que es un short-hand de las propiedades:

-   [align-content (CSS-Tricks)](https://css-tricks.com/snippets/css/a-guide-to-flexbox/#align-content).
-   [justify-content (CSS-Tricks)](https://css-tricks.com/snippets/css/a-guide-to-flexbox/#justify-content).

Para que la propiedad _align-content_ nos funcione como deseamos es necesario que los containers contengan la declaración: _flex-wrap: wrap;_. Esta lo que produce es que los elementos hijos de un _flex-container_ puedan saltar a la siguiente línea o columna si su ancho o su alto excede el contenedor. Por defecto la propiedad _flex-wrap_ tiene como valor _no-wrap_, lo cual impide ese “salto”.

-   [Documentación1: flex-wrap (CSS-Tricks)](https://css-tricks.com/snippets/css/a-guide-to-flexbox/#flex-wrap)
-   [Documentación2: flex-wrap (MDN)](https://developer.mozilla.org/en-US/docs/Web/CSS/flex-wrap)

Para que se cumpla la condición de que sea con una sola declaración, se puede agregar el _flex-wrap_ únicamente al selector _.container_, eso hará que todos los containers se vean afectados, ya que utilizan su regla por el _@extend_.  
**_@extend_ es un “superpoder” que le da SASS a CSS, que permite transferir las reglas de un selector a otro/s. En este caso se podría hacer lo mismo con CSS puro, utilizando [selectores de atributo](https://developer.mozilla.org/es/docs/Web/CSS/Attribute_selectors).**

---

Dejo el código de cómo sería con **CSS puro**:

```
@import url("https://fonts.googleapis.com/css2?family=Lato&display=swap");

.wrapper {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  grid-gap: 5px;
  font-family: "Lato", sans-serif;
  width: 550px;
}

[class^="container"] {
  background: turquoise;
  width: 180px;
  height: 180px;
  flex-wrap: wrap;
}

[class^="element"] {
  width: 60px;
  height: 60px;
  text-align: center;
  padding-top: 10px;
  box-sizing: border-box;
}

.element1 {
  background: papayawhip;
}

.element2 {
  background: pink;
}

.element3 {
  background: lightcyan;
}

.container1 {
  display: flex;
  place-content: flex-start;
}

.container2 {
  display: flex;
  place-content: center flex-start;
}

.container3 {
  display: flex;
  place-content: flex-end flex-start;
}

.container4 {
  display: flex;
  place-content: flex-start center;
}

.container5 {
  display: flex;
  place-content: center;
}

.container6 {
  display: flex;
  place-content: flex-end center;
}

.container7 {
  display: flex;
  place-content: flex-start flex-end;
}

.container8 {
  display: flex;
  place-content: center flex-end;
}

.container9 {
  display: flex;
  place-content: flex-end;
}
```

También dejo [mi resolución en CodePen](https://codepen.io/patugarte/pen/GRWWJab?editors=1100) por si quieren revisarla. Espero les sirva 😄