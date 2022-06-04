# Animation direction, fill mode y play state

### **PROPIEDAD ANIMATION-DIRECTION**

Mediante esta propiedad indicamos cómo debe ejecutarse una animación: hacia delante (del principio al final), hacia atrás (del final al principio), una vez hacia delante y otra hacia detrás, etc. La animación habrá sido definida en una regla `@keyframes` y va a ser aplicada a un elemento seleccionado mediante un selector CSS. El valor por defecto para esta propiedad es **normal** (implica que la animación se ejecutará hacia delante). Sus valores posibles son cualquiera de estas palabras clave:

-   **normal:** la animación se ejecutará hacia delante. Si se repite, cuando vuelve a empezar parte de la situación inicial.
    
-   **reverse:** la animación se ejecutará hacia detrás. Si se repite, cuando vuelve a empezar parte de la situación inicial.
    
-   **alternate:** la animación se ejecutará una vez en un sentido y otra vez en otro, comenzando hacia delante, luego hacia detrás y así sucesivamente el número de repeticiones especificado.
    
-   **alternate-reverse:** la animación se ejecutará una vez en un sentido y otra vez en otro, comenzando hacia detrás, luego hacia delante y así sucesivamente el número de repeticiones especificado.
    

Si se desean aplicar varias animaciones, se especificarán sus direcciones separadas por comas, siendo cada valor correspondiente a la animación cuyo nombre figura en el mismo orden en la propiedad animation-name.

Esta propiedad puede no ser reconocida por los navegadores antiguos o requerir del uso de prefijos específicos o no ser reconocida por algunos navegadores actuales. Consulta en Mozilla Developer Network para conocer si debes aplicar prefijos o si la propiedad será reconocida por un navegador concreto.

### **PROPIEDAD ANIMATION-PLAY-STATE**

Esta propiedad permite detener una animación que se está ejecutando (ponerla en pausa). Su valor por defecto es running y sus dos valores posibles son:

-   **running:** la animación está en ejecución
-   **paused:** la animación está en pausa

Esta propiedad puede no ser reconocida por los navegadores antiguos o requerir del uso de prefijos específicos para algunos navegadores actuales. Consulta en Mozilla Developer Network para conocer si debes aplicar prefijos.

Ejemplo: .pubMov:hover{ animation-play-state:paused; } con esta regla damos lugar a que la animación se detenga si el usuario pone el puntero del ratón sobre el elemento animado.

### **PROPIEDAD ANIMATION-FILL-MODE**

Esta propiedad permite detener definir cómo debe comenzar y cómo debe quedar un elemento que tiene una animación. Su valor por defecto es none (implica que el elemento comenzará y quedará en el estado que tenía antes de que comenzara la animación) y sus valores posibles son:

-   **none:** el elemento comenzará y quedará en el estado previo a la animación.
    
-   **forwards:** el elemento quedará en el estado final de la animación.
    
-   **backwards:** el elemento se pondrá en el estado indicado para el comienzo de la animación inmediatamente y esperará en ese estado hasta que se cumpla el tiempo indicado en animation-delay. Una vez se cumpla ese tiempo la animación continuará la ejecución desde ese estado inicial.
    
-   **both:** combinación de las dos opciones anteriores.
    

Esta propiedad puede no ser reconocida por los navegadores antiguos o requerir del uso de prefijos específicos para algunos navegadores actuales. Consulta en Mozilla Developer Network para conocer si debes aplicar prefijos.

**Ejemplo**: .pubMov:hover{ animation-fill-mode: forwards; } con esta regla damos lugar a que cuando la animación se detenga quede en el último estado definido (el correspondiente a to ó 100% dentro de la regla @keyframes).

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

 counter-reset: score;

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

  

 input[type=checkbox] {

 appearance: none;

 cursor: pointer;

 height: 50px;

 margin: 0;

 position: relative;

 top: 0;

 width: 80px;

 z-index: 2;

 }

 input[type=checkbox]:focus {

 appearance: none;

 outline: none;

 }

 input:checked {

 counter-increment: score;

 }

 .score::after {

 content: counter(score);

 }

 @keyframes bunny {

 0% {

 top: 0;

 }

 25% {

 top: 80px;

 }

 100% {

 top: 0;

 }

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

 .layer-1 {

 position: absolute;

 z-index: 1;

 height: 450px;

 width: 80px;

 bottom: 0;

 right: 60px;

  

 /* After 4 */

 animation-name: layer;

 animation-duration: 1s;

 animation-timing-function: ease-in-out;

 animation-iteration-count: infinite;

 }

 .layer-1 input[type=checkbox] {

 /* After 4*/

 animation-name: bunny;

 animation-duration: 1s;

 animation-timing-function: ease-in-out;

 animation-iteration-count: infinite;

 }

 .layer-2 {

 position: absolute;

 z-index: 2;

 height: 450px;

 width: 80px;

 bottom: 0;

 left: 60px;

  

 /* After 4 */

 animation-name: layer;

 animation-duration: 1.5s;

 animation-timing-function: ease-in-out;

 animation-iteration-count: infinite;

 }

 .layer-2 input[type=checkbox] {

 /* After 4*/

 animation-name: bunny;

 animation-duration: 1.5s;

 animation-timing-function: ease-in-out;

 animation-iteration-count: infinite;

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

 overflow: hidden;

 background-color: burlywood;

 bottom: 0;

 box-shadow: rgba(0, 0, 0, 0.15) 0px 5px 15px 0px;

 }

 .layer-4 {

 /* After 3 */

 position: absolute;

 z-index: 4;

 height: 350px;

 width: 80px;

 bottom: 0;

 left: 15px;

  

 /* After 4 */

 animation-name: layer;

 animation-duration: 1.5s;

 animation-timing-function: ease-in-out;

 animation-iteration-count: infinite;

 }

 .layer-4 input[type=checkbox] {

 /* After 4*/

 animation-name: bunny;

 animation-duration: 0.5s;

 animation-timing-function: ease-in-out;

 animation-iteration-count: infinite;

 }

 .layer-5 {

 position: absolute;

 z-index: 5;

 border-radius: 20px;

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

 right: 30px;

  

 /* After 4 */

 animation-name: layer;

 animation-duration: 2s;

 animation-timing-function: ease-in-out;

 animation-iteration-count: infinite;

 }

 .layer-6 input[type=checkbox] {

 /* After 4*/

 animation-name: bunny;

 animation-duration: 2s;

 animation-timing-function: ease-in-out;

 animation-iteration-count: infinite;

 }

 .layer-7 {

 position: absolute;

 z-index: 7;

 border-radius: 20px;

 overflow: hidden;

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

 height: 120px;

 bottom: 0;

 left: 0;

 right: 0;

 margin: 0 auto;

 }

 .layer-8__left-lawn {

 background-color: darkgreen;

 border-radius: 40px 40px 0 0;

 bottom: 0;

 display: inline-block;

 height: 70%;

 left: 0;

 position: absolute;

 width: 80px;

 }

 .layer-8__center-lawn {

 background-color: darkgreen;

 border-radius: 40px 40px 0 0;

 bottom: 0;

 display: inline-block;

 height: 100%;

 left: 60px;

 position: absolute;

 width: 80px;

 }

 .layer-8__right-lawn {

 background-color: darkgreen;

 border-radius: 40px 40px 0 0;

 bottom: 0;

 display: inline-block;

 height: 80%;

 left: 130px;

 position: absolute;

 width: 80px;

 }

 .layer-9 {

 position: absolute;

 z-index: 9;

 width: 120px;

 height: 100px;

 bottom: 0;

 }

 .layer-9__left-cloud {

 background-color: white;

 border-radius: 40px 40px 0 25px;

 display: inline-block;

 height: 100%;

 left: 0;

 position: absolute;

 width: 80px;

 }

 .layer-9__right-cloud {

 background-color: white;

 border-radius: 0 40px 30px 0;

 bottom: 0;

 display: inline-block;

 height: 60%;

 left: 80px;

 position: absolute;

 width: 40px;

 }

 .layer-10 {

 position: absolute;

 z-index: 10;

 width: 120px;

 height: 100px;

 bottom: 0;

 right: 0;

 }

 .layer-10__left-cloud {

 background-color: white;

 border-radius: 40px 0 0 30px;

 bottom: 0;

 display: inline-block;

 height: 60%;

 right: 80px;

 position: absolute;

 width: 40px;

 }

 .layer-10__right-cloud {

 background-color: white;

 border-radius: 40px 40px 25px 0;

 display: inline-block;

 height: 100%;

 right: 0px;

 position: absolute;

 width: 80px;

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

  

 .title {

 display: flex;

 justify-content: center;

 margin: 45px 0 10px;

 }

  

 .title img {

 width: 60%;

 }

  

 .score {

 color: lightcoral;

 font-family: Arial, Helvetica, sans-serif;

 font-size: 16px;

 margin: 0;

 text-align: center;

 }

 </style>

 <script async src="/cdn-cgi/bm/cv/669835187/api.js"></script>

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

 <div class="layer-3">

 <div class="zigzag"></div>

 </div>

 <div class="layer-4">

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

 <div class="layer-5">

 <div class="zigzag"></div>

 </div>

 <div class="layer-6">

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

 <div class="layer-7">

 <div class="zigzag"></div>

 </div>

 <div class="layer-8">

 <div class="layer-8__left-lawn"></div>

 <div class="layer-8__center-lawn"></div>

 <div class="layer-8__right-lawn"></div>

 </div>

 <div class="layer-9">

 <div class="layer-9__left-cloud"></div>

 <div class="layer-9__right-cloud"></div>

 </div>

 <div class="layer-10">

 <div class="layer-10__left-cloud"></div>

 <div class="layer-10__right-cloud"></div>

 </div>

  

 <h1 class="title">

 <img src="https://i.ibb.co/J3Kn71r/cbd152ddb203fe23ad78261749534e7d.png" alt="AnimationLand">

 </h1>

 <h2 class="score">

 Score:

 </h2>

 </div>

 <script type="text/javascript">

 (function(){window['__CF$cv$params']={r:'6d5dd3367f4e3262',m:'xa71dE63pjztJKHeE_nGSPmSLiaksn3yqyVWBpJl6s8-1643578475-0-AZZQABBvJ/b4vwg3s8+/tIyvCOKRg4ASsosj+Wb+wF29rwluWY2a4XbxgH2X5gjm41JzaCjhStks5L2Aesfts3A4iljMnNHYExYZOgmZa9DXS+rlWSWNgy/+XxK6Fhf6uNgWFjcprnC+cZWuHXnCgMXdGhsOnIx3xKqlqeIH7Zu8VaV8TyMv+Y82rpFa6Uf+nBQEQlZI/CHQFa9vSOJkLlU=',s:[0x1f09291f10,0xc23a4f029c],}})();

 </script>

 </body>

</html>```