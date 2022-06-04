# Animation name y keyframe
En esta clase vimos cual es la diferencia entre las animaciones y las transiciones, ya que uno se puede llegar a confundir bastante, esto debido a que ambas suenan bastante similar e incluso se podría llegar a pensar que son sinónimos.  
.

#### Diferencia entre transiciones y animaciones

Las transiciones solo pueden ir de un punto A a uno B en determinado tiempo. Sin embargo, en las animaciones, en el lapso de tiempo que va del punto A al B (osea, en el punto intermedio), puede haber ciertos movimientos.  
.  

![](https://cssanimation.rocks/images/posts/transitions-animations/transitions-animations.gif)  
.

#### Keyframes

Entonces, sabiendo cual es la diferencia entre las animaciones y transiciones, es hora de saber como los @keyframes nos ayudan a animar a nuestros elementos.  
.  
Un keyframe no es mas que una linea del tiempo que empieza desde el punto A y termina en el punto B. Nosotros le podemos decir a ese keyframe en que parte del “camino” modifique al elemento. Además de que nosotros le decimos cuantos segundos tiene que durar ese “viaje”.

Animation puede tener solo un valor, o varios

-   animation-name: Con esta le colocamos un nombre a la fracción de código que queremos animar, para que el keyframe sepa a quién debemos animar.
-   keyframes: Se va de A a B con ciertas manipulaciones de por medio. Está es la diferencia crucial, que podemos manipular el tiempo desde el inicio hasta el final usando palabras clave como from y to para decir que solo desde el inicio hasta el final.

No es necesario llegar de 0 a 100.

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

 }

  

 @keyframes blink {

 0% {

 }

 5% {

  

 }

 10% {

  

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

</html>```