# El componente Slides

para contruir los slides podemos valernos de componentes predefinidos lo cual nos hace más facil la creación

home.page.html
```html
<ion-content [fullscreen]="true">

 <ion-slides pager="true" [options]="slideOps">

 <ion-slide>

 <img src="assets/img/logo.png" alt="Platzi Music Logo">

 <h1>Escucha tu música</h1>

 <h2>EN CUALQUIER LUGAR</h2>

 <p>

 Los mejores álbunes, las mejores canciones. Escucha y comparte

 en cualquier momento, a todas horas.

 </p>

 <ion-icon name="play-outline"></ion-icon>

 </ion-slide>

 <ion-slide>

 <h1>Slide 2</h1>

 </ion-slide>

 <ion-slide>

 <h1>Slide 3</h1>

 </ion-slide>

 </ion-slides>

</ion-content>
```
con ion-slide se puede crear slides facilmente. Ademas con ion-icon se puede copiar los iconos de https://ionic.io/ionicons para ingresar solo el nombre del icono que se requiera

dentro de la carpeta theme en la ruta principal, estan los colores que se pueden usar como parte del css, el scss es como cualquier scss


home.page.scss
```scss
#container {

 text-align: center;

  

 position: absolute;

 left: 0;

 right: 0;

 top: 50%;

 transform: translateY(-50%);

}

  

#container strong {

 font-size: 20px;

 line-height: 26px;

}

  

#container p {

 font-size: 16px;

 line-height: 22px;

  

 color: #8c8c8c;

  

 margin: 0;

}

  

#container a {

 text-decoration: none;

}

  

ion-content {

 padding: 1em;

 --background: var(--ion-color-success);

 font-family: "Perpetua", sans-serif;

}

ion-slides {

 background-color: white;

 height: 100%;

 max-width: 800px;

 color: black;

}

.swiper-slide {

 flex-direction: column;

 margin-bottom: 64px;

 background-color: white;

}

ion-slide {

 > h1, h2 {

 margin: 0;

 color: var(--ion-color-primary);

 }

 > p {

 font-style: italic;

 font-size: 22px;

 padding: 1em 1em 1em 1em;

 }

 > ion-icon {

 color: var(--ion-color-success);

 font-size: 48px;

 }

 > ion-icon[name="close"] {

 float: right;

 color: var(--ion-color-primary);

 font-size: 48px;

 }

 >img {

 max-height: 50%;

 max-width: 60%;

 margin: 64px 0;

 }

}
```

para poder darle algunos estilos y opciones a neustros slides se puede ingresar en el ion-slides las opciones como variable y luego en el ts del component home poner esas opciones

home.page.ts
```ts 
 slideOps = {

 initialSlide: 0,

 slidesPerView: 1,

 centeredSlides: true,

 speed: 400

 };
 ```