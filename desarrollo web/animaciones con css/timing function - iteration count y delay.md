# Animation timing function, iteration count y delay

-   **Animation Timing Function:** Básicamente es la aceleración con la cual correrá nuestra animación.
-   **Animation Iteration Count:** Es el número de veces que se repetirán nuestra animación.
-   **Animation Delay:** Es el tiempo que nuestra animación tardará en empezar.

.  
La función `cubic-bezier()` me encanta porque podemos definir velocidades personalizadas :3. Me gustaría complementar la clase con otro ejemplo práctico de animación, por ejemplo, esta animación que hice al principio de un objeto saltando:  
.  

![Animation](https://media.giphy.com/media/p1ZLyNFGfKSDAH88Th/giphy.gif)  
.  
Si quisiera hacer esta animación en CSS quedaría algo así, tomando en cuenta sus 4 puntos:  
.  
**Punto A:** Simplemente inicia con un `left` inicial:

```css
0% {
    left: 50px;
}
```

**Punto B:** Para este punto nuestro objeto simplemente se movió unos cuantos píxeles a la derecha y se encogió un poco:

```css
40% {
    left: 400px;
    height: 65px;
    width: 130px;
    bottom: 40%;
}
```

**Punto C:** Aquí el objeto ya dio el salto hacia más a la derecha y se hizo un poquito más grande, por lo que debería estar en su punto más alto:

```css
60% {
    left: 780px;
    height: 140px;
    width: 100px;
    bottom: calc(40% + 150px);
  }
```

**Punto D:** Al final el objeto cae de nuevo, obviamente moviéndose aún más a la derecha 😉

```css
90%, 100% {
    left: 1080px;
    bottom: 40%;
}
```

Aquí puse al 90% y al 100% juntitos porque quiero que tanto en el 90% commo en el 100% se conserven los mismos valores :3  
.  
Al final tendría este resultado:  
.  

![Jump Animation](https://media.giphy.com/media/8dkG7h9AX72Pc71wLQ/giphy.gif)  
.  
Así de fácil es crear animaciones con CSS, simplemente necesitas pensar qué acción estará haciendo tu objeto en cada punto y con base en ello puedes empezar a programar la animación :3.  
.  
Obviamente necesitariamos tener un objeto al cual aplicarle la animación, este objeto debe tener un `position: absolute;` con respecto al contenedor padre, ya hice la tarea, así que pueden ver el código completo de esta animación aquí 👇👀.  
.  
[Animación de un objeto saltando](https://codepen.io/retaxmaster/pen/KKWXyJw)


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

 animation-name: layer;

 animation-duration: 1s;

 animation-timing-function: ease-in-out;

 animation-iteration-count: infinite;

 }

  

 @keyframes layer {

 0% {

 bottom: 0;

 }

 25% {

 bottom: -80px;

 }

 100% {

 bottom: 0;

 }

 }

 .layer-1 input[type=checkbox] {

  

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

 <input type="checkbox">

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