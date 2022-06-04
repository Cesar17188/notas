# Preferencias de movimiento reducido

.  
En relacion a la accesibilidad, cuando hablamos de transiciones, hay personas que pueden no querer ver las transiciones. Tu te podrías preguntar, ¿Quién no quiere ver las transiciones, si estas son geniales? Bueno, hay personas diversas en la viña del Señor…  
.  
El punto es que en el navegador hay un opción para “_deshabilitar_” este tipo de movimientos. Cuando esta opción este prendida, nosotros tendríamos que haber puesto un media queria, mejor conocido como `@media`. Y si, los media queries no solo sirven para hacer responsive design!  
.  
La manera en como lo hacemos es la siguiente:

```
@media (prefers-reduced-motion: no-preference){
	Your: code;
}
```

En el apartado de `Your: code;`, solo tendríamos que cambiar el código para que ya no haya transiciones tan alocadas y el usuario pueda ver algo menos escandaloso. En la clase dan un muy buen ejemplo practico


### [Preferencias de Usuario](https://lenguajecss.com/css/responsive-web-design/preferencias-usuario/) @media (propiedad: valor) {}

Dentro del apartado de media queries disponemos de una mecánica para detectar ciertas preferencias de usuario, o lo que es lo mismo, si el usuario ha indicado algunas preferencias por ciertos detalles en su dispositivo, sistema operativo o navegador que utiliza.

#### [prefers-color-scheme](https://developer.mozilla.org/en-US/docs/Web/CSS/@media/prefers-color-scheme)

sistema que permite seleccionar un tema claro o un tema oscuro  
_**Valores:**_ dark, light

#### [prefers-reduced-motion](https://developer.mozilla.org/en-US/docs/Web/CSS/@media/prefers-reduced-motion)

_**Valores**_  
**no-preference**  
Indica que el usuario no ha dado a conocer ninguna preferencia al sistema.  
**reduce**  
Indica que el usuario ha notificado al sistema que prefiere una interfaz que elimine o reemplace los tipos de animación basada en movimiento que provocan incomodidad para las personas con trastornos del movimiento [vestibular](https://vestibular.org/article/what-is-vestibular/desorden-vestibular-vertigo-en-espanol/) que puede causarles mareos, náuseas, dolores de cabeza o algo peor.

**Entonces, ¿debería ir a lo seguro y deshacerme de toda mi animación?**  
Hacerlo sería una opción dramática y no necesariamente válida. Si se usan correctamente, las animaciones pueden incluso ayudar a la accesibilidad al ayudar a abordar los problemas de accesibilidad cognitiva.

Informate mas sobre la sensibilidad del movimiento [Link](https://alistapart.com/article/designing-safer-web-animation-for-motion-sensitivity/)

```html
<!DOCTYPE html>

<html lang="en">

<head>

 <meta charset="UTF-8">

 <meta http-equiv="X-UA-Compatible" content="IE=edge">

 <meta name="viewport" content="width=device-width, initial-scale=1.0">

 <title>Preferencias de movimiento reducido</title>

 <style>

 .card {

 width: 200px;

 height: 200px;

 transform-style: preserve-3d;

 position: relative;

 transition: transform 0.5s;

 transform-style: preserve-3d;

 }

 /* .card:hover {

 transform: rotateY(180deg);

 } */

 .card:hover .back {

 opacity: 1;

 }

 .face {

 border-radius: 20px;

 width: 100%;

 height: 100%;

 position: absolute;

 backface-visibility: hidden;

 }

 .face.front {

 background: pink;

 }

 .face.back {

 background: papayawhip;

 /* transform: rotateY(180deg); */

 transition-duration: 0.6s;

 z-index: 2;

 opacity: 0;

 }

 @media (prefers-reduced-motion: no-preference) {

 .card {

 transition: transform 0.5s;

 transform-style: preserve-3d;

 }

 .card:hover {

 transform: rotateY(180deg);

 }

 .face {

 backface-visibility: hidden;

 }

 .back {

 transform: rotateY(180deg);

 opacity: 1;

 }

 }

 </style>

<script async src='/cdn-cgi/bm/cv/669835187/api.js'></script>

</head>

<body>

 <div class="card">

 <div class="face front"></div>

 <div class="face back"></div>

 </div>

  

 <script type="text/javascript">(function(){window['__CF$cv$params']={r:'6d1b9943be82325e',m:'Bf4JoTo6jZN1b4Nf.XgKXZy_yk3eKZw6zf.yX7NaWx8-1642884040-0-AZRfZIKsgmFnBi1Em0WhG4TTiXuI7SVYhzWn4TUWpABZ7Jli8RWNNH41H5l4e7O8nfb1bHmyE+11v/IOotvXZ1BFppK9pt/Yxr4GOs/80SLogyqGArvzn3yREXv1xYgfLFfJimyekN4yYzWpj9Jmb48Nn9zAUcdMzHQu91lLYyJBG1dee3nnRXNpYqlpLjTBzBoedzRXwHZKSRu4WU6MBBaxnh5dqcckd9zq8iYgcneNCWZb5Gal6uOlY5ij2sps+w==',s:[0xf4a262b688,0x72d2a314ec],}})();</script>

</body>

</html>
```