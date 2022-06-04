# Técnicas de alineamiento antes de CSS Grid: table-cell y positions

Los valores que recibe la función _**translate**_ se calculan con base en el **tamaño del elemento**. Esto significa que si el elemento tiene un width de 60px, al usar `transform: translate(-100%, 0)` sería lo mismo que si pusiéramos `transform: translate(-60px, 0)`.  
Aplica de igual forma para el eje Y con respecto al height.

```html
<div class="wrapper">
  <div class="container">
    <div class="element1">top left</div>
  </div>

  <div class="container">
    <div class="element2">center left</div>
  </div>

  <div class="container">
    <div class="element3">bottom left</div>
  </div>

  <div class="container">
    <div class="element4">top center</div>
  </div>

  <div class="container">
    <div class="element5">center center</div>
  </div>

  <div class="container">
    <div class="element6">bottom center</div>
  </div>
  
  <div class="container">
    <div class="element7">top right</div>
  </div>
  
  <div class="container">
    <div class="element8">center right</div>
  </div>

  <div class="container">
    <div class="element9">bottom right</div>
  </div>
</div>
```

```css
@import url('https://fonts.googleapis.com/css2?family=Lato&display=swap');

.wrapper {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  grid-gap: 5px;
  font-family: 'Lato', sans-serif;
  width: 550px;
}

.container {
  background: turquoise;
  width: 180px;
  height: 180px;
  position: relative;
}

.element {
  width: 60px;
  height: 60px;
  text-align: center;
  padding-top: 10px;
  box-sizing: border-box;
}

.element1 {
  @extend .element;
  background: papayawhip;
  position: absolute;
  left: 0;
  top: 0;
}

.element2 {
  @extend .element;
  background: papayawhip;
  position: absolute;
  left: 0;
  top: 50%;
  transform: translate(0, -50%);
}

.element3 {
  @extend .element;
  background: papayawhip;
  position: absolute;
  left: 0;
  top: 100%;
  transform: translate(0, -100%);
}

.element4 {
  @extend .element;
  background: pink;
  position: absolute;
  left: 50%;
  transform: translate(-50%,0);
}

.element5 {
  @extend .element;
  background: pink;
  position: absolute;
  left: 50%;
  top: 50%;
  transform: translate(-50%, -50%) ;
}

.element6 {
  @extend .element;
  background: pink;
  position: absolute;
  left: 50%;
  top: 100%;
  transform: translate(-50%, -100%);
}

.element7 {
  @extend .element;
  background: lightcyan;
  position: absolute;
  left: 100%;
  transform: translate(-100%, 0);
}

.element8 {
  @extend .element;
  background: lightcyan;
  position: absolute;
  left: 100%;
  top: 50%;
  transform: translate(-100%, -50%);
}

.element9 {
  @extend .element;
  background: lightcyan;
  position: absolute;
  left: 100%;
  top: 100%;
  transform: translate(-100%, -100%);
}
```