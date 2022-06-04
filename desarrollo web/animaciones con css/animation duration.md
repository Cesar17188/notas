# Animation duration

Estas propiedades son de las más fáciles 👀. Simplemente debes decirle cuánto va a durar la animación y cuántas veces se va a repetir esa animación, es todo 👀. Únicamente con esas dos propiedades ya tienes suficiente paa que una animación empiece a correr 😄  
.  
Otro ejemplo de animación sencillo, además de el de la clase, podría ser el lanzamiento de algún objeto:

![Throw Animation](https://media.giphy.com/media/iHu3HYAwoXTxSwf1m1/giphy.gif)

Cuando lanzamos un objeto es normal que a veces gire y se eleve un poco en el aire, para hacer una animación similar, solo necesitariamos 3 puntos:

**Punto A:** El inicio de la animación, el objeto tendrá un `left` inicial y un `transform` inicial:

```css
0% {
    left: 50px;
    transform: rotate(0deg);
}
```

**Punto B:** A la mitad de la animación el objeto debió elevarse un poco, por tanto le cambiamos su propiedad en `bottom`:

```css
50% {
    bottom: 60%;
}
```

**Punto C:** Al final de la animación el objeto debió caer y debió de haber dado unas cuantas vueltas, también debió de haberse movido, por lo que modificamos las propiedades `left` y `transform`, el `bottom` no lo modificamos porque por defecto volverá a su estado inicial:

```css
100% {
    left: 1080px;
    transform: rotate(360deg);
}
```

Al final nuestro Keyframe podría quedar así y esto simularía un objeto que es lanzado 👀.

```css
@keyframes throw {
  
  0% {
    left: 50px;
    transform: rotate(0deg);
  }
  
  50% {
    bottom: 60%;
  }
  
  100% {
    left: 1080px;
    transform: rotate(360deg);
  }
  
}
```

Obviamente necesitariamos tener un objeto al cual aplicarle la animación, este objeto debe tener un `position: absolute;` con respecto al contenedor padre, ya hice la tarea, así que pueden ver el código completo de esta animación aquí 👇👀.  
.  
[Animación del lanzamiento de un objeto](https://codepen.io/retaxmaster/pen/eYvGVOK)  
.  
Casi todos son estilos para que se vea más bonito y para preparar los elementos en su posición incial

```html
<!DOCTYPE html>

<html lang="en">

 <head>

 <meta charset="UTF-8" />

 <meta http-equiv="X-UA-Compatible" content="IE=edge" />

 <meta name="viewport" content="width=device-width, initial-scale=1.0" />

 <title>Contexto de apilamiento</title>

 <style>

 body {

 margin: 0;

 height: 100vh;

 width: 100%;

 display: grid;

 place-items: center;

 }

 .phone {

 position: relative;

 border: 8px solid black;

 border-radius: 40px;

 height: 600px;

 width: 300px;

 background-color: #ccefff;

 box-shadow: 0 19px 38px rgba(0, 0, 0, 0.3),

 0 15px 12px rgba(0, 0, 0, 0.22);

 }

 .layer-1 {

 position: absolute;

 z-index: 1;

 height: 450px;

 width: 80px;

 bottom: 0;

 right: 60px;

 }

 .layer-2 {

 position: absolute;

 z-index: 2;

 height: 450px;

 width: 80px;

 bottom: 0;

 left: 60px;

 }

 .layer-3 {

 position: absolute;

 z-index: 3;

 border-radius: 20px;

 left: 0;

 right: 0;

 margin: 0 auto;

 width: 220px;

 height: 400px;

 background-color: burlywood;

 bottom: 0;

 box-shadow: rgba(0, 0, 0, 0.15) 0px 5px 15px 0px;

 }

 .layer-4 {

 position: absolute;

 z-index: 4;

 height: 350px;

 width: 80px;

 bottom: 0;

 left: 30px;

 }

 .layer-5 {

 position: absolute;

 z-index: 5;

 border-radius: 20px;

 left: 0;

 right: 0;

 width: 200px;

 height: 300px;

 background-color: burlywood;

 bottom: 0;

 box-shadow: rgba(0, 0, 0, 0.15) 0px 5px 15px 0px;

 }

 .layer-6 {

 position: absolute;

 z-index: 6;

 height: 250px;

 width: 80px;

 bottom: 0;

 right: 35px;

 }

 .layer-7 {

 position: absolute;

 z-index: 7;

 border-radius: 20px;

 left: 20;

 right: 0;

 width: 150px;

 height: 200px;

 background-color: burlywood;

 bottom: 0;

 box-shadow: rgba(0, 0, 0, 0.15) 0px 5px 15px 0px;

 }

 .layer-8 {

 position: absolute;

 z-index: 8;

 width: 200px;

 height: 110px;

 background-color: green;

 bottom: 0;

 left: 0;

 right: 0;

 margin: 0 auto;

 }

 .layer-9 {

 position: absolute;

 z-index: 9;

 width: 120px;

 height: 90px;

 background-color: white;

 bottom: 0;

 left: 0;

 }

 .layer-10 {

 position: absolute;

 z-index: 10;

 width: 110px;

 height: 90px;

 background-color: white;

 bottom: 0;

 right: 0;

 }

  

 .left-ear--outer {

 background: white;

 border-radius: 90%;

 width: 20px;

 height: 50px;

 position: absolute;

 left: 10px;

 }

 .left-ear--inner {

 background: pink;

 border-radius: 95%;

 width: 10px;

 height: 50px;

 position: absolute;

 left: 15px;

 top: 8px;

 }

 .right-ear--outer {

 background: white;

 border-radius: 90%;

 width: 20px;

 height: 50px;

 position: absolute;

 right: 10px;

 }

 .right-ear--inner {

 background: pink;

 border-radius: 95%;

 width: 10px;

 height: 50px;

 position: absolute;

 right: 15px;

 top: 8px;

 }

 .head {

 width: 100%;

 height: 80px;

 left: 0;

 right: 0;

 margin: 0 auto;

 border-radius: 50%;

 background: white;

 position: absolute;

 top: 30px;

 }

 .head__eye {

 background: gray;

 border-radius: 50%;

 width: 8px;

 height: 8px;

 position: absolute;

 top: 15px;

 animation-name: blink;

 animation-duration: 2s;

 animation-iteration-count: infinite;

 }

  

 @keyframes blink {

 0% {

 height: 8px;

 }

 5% {

 transform: translate(0px, 4px);

 height: 2px;

 }

 10% {

 transform: translate(0px, 0px);

 height: 8px;

 }

 }

  

 .head__eye--left {

 left: 26px;

 }

 .head__eye--right {

 right: 26px;

 }

 .zigzag:after {

 content: "";

 width: 100%;

 height: 20px;

 position: absolute;

 top: 0;

 height: 30px;

 background: linear-gradient(135deg, #67a167 25%, transparent 25%) -50px 0,

 linear-gradient(-135deg, #67a167 25%, transparent 25%) -50px 0,

 linear-gradient(45deg, #67a167 25%, transparent 25%),

 linear-gradient(-45deg, #67a167 25%, transparent 25%);

 background-size: 30px 88px;

 border-radius: 20px;

 }

 .zigzag::before {

 content: "";

 position: absolute;

 /* left: -0px; */

 top: 15px;

 width: 100%;

 height: 40px;

 background: linear-gradient(135deg, #a6543d 25%, transparent 25%) -50px 0,

 linear-gradient(-135deg, #a6543d 25%, transparent 25%) -50px 0,

 linear-gradient(45deg, #a6543d 25%, transparent 25%),

 linear-gradient(-45deg, #a6543d 25%, transparent 25%);

 background-size: 30px 100px;

 background-position: 140px 0 0 30px 0;

 }

 </style>

 </head>

 <body>

 <div class="phone">

 <!-- bunny 1 -->

 <div class="layer-1">

 <div class="left-ear--outer"></div>

 <div class="left-ear--inner"></div>

 <div class="right-ear--outer"></div>

 <div class="right-ear--inner"></div>

 <div class="head">

 <div class="head__eye head__eye--left"></div>

 <div class="head__eye head__eye--right"></div>

 </div>

 </div>

 <div class="layer-2">

 <div class="left-ear--outer"></div>

 <div class="left-ear--inner"></div>

 <div class="right-ear--outer"></div>

 <div class="right-ear--inner"></div>

 <div class="head">

 <div class="head__eye head__eye--left"></div>

 <div class="head__eye head__eye--right"></div>

 </div>

 </div>

 <div class="layer-3">

 <div class="zigzag"></div>

 </div>

 <div class="layer-4">

 <div class="left-ear--outer"></div>

 <div class="left-ear--inner"></div>

 <div class="right-ear--outer"></div>

 <div class="right-ear--inner"></div>

 <div class="head">

 <div class="head__eye head__eye--left"></div>

 <div class="head__eye head__eye--right"></div>

 </div>

 </div>

 <div class="layer-5">

 <div class="zigzag"></div>

 </div>

 <div class="layer-6">

 <div class="left-ear--outer"></div>

 <div class="left-ear--inner"></div>

 <div class="right-ear--outer"></div>

 <div class="right-ear--inner"></div>

 <div class="head">

 <div class="head__eye head__eye--left"></div>

 <div class="head__eye head__eye--right"></div>

 </div>

 </div>

 <div class="layer-7">

 <div class="zigzag"></div>

 </div>

 <div class="layer-8"></div>

 <div class="layer-9"></div>

 <div class="layer-10"></div>

 </div>

 </body>

</html>
```