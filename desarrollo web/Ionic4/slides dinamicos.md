# Slides dinámicos
como convertir los slides en una forma más dinamica en caso de que la información venga de algun backend. 

Por lo que hay que setear toda la información desde el controlador ts de home o cualquier componentes que tenga en esa vista.

home.page.ts
```ts
slides = [

 {

 imageSrc: 'assets/img/logo.png',

 imageAlt: 'Platzi Music Logo',

 title: 'Escucha tu música',

 subtitle: 'EN CUALQUIER LUGAR',

 description:

 'Los mejores álbunes, las mejores canciones. Escucha y comparte en cualquier momento, a todas horas.',

 icon: 'play',

 },

 {

 imageSrc: 'assets/img/logo.png',

 imageAlt: 'Platzi Music Logo',

 title: 'Disfruta de nuestro reproductor',

 subtitle: 'DE VIDEOS INCREÍBLES',

 description:

 'Entra la modo video de nuestro reproductor y obtén acceso a clips. documentales y making offs increíbles de tu artista favorito',

 icon: 'videocam',

 },

 {

 imageSrc: 'assets/img/logo.png',

 imageAlt: 'Platzi Music Logo',

 title: 'Accede al exclusivo',

 subtitle: 'MODO DEPORTE',

 description:

 'Crea una playlist basada en tu actividad física. Ten reportes y acceso a lo que necesites, integrado con GPS!',

 icon: 'bicycle',

 },

 {

 imageSrc: 'assets/img/logo.png',

 imageAlt: 'Platzi Music Logo',

 title: 'Busca nuevas canciones',

 subtitle: 'EN LA RADIO DE TU AUTOR FAVORITO',

 description:

 'Mira las playlist que se generan con los ritnos y generos parecidos a los de autor favorito',

 icon: 'albums',

 },

 ];
```

home.page.html
```html
<ion-content [fullscreen]="true">

 <ion-slides pager="true" [options]="slideOps">

 <ion-slide *ngFor="let slide of slides">

 <ion-icon name="close"></ion-icon>

 <img src="{{slide.imageSrc}}" alt="{{slide.imageAlt}}">

 <h1>{{slide.title}}</h1>

 <h2>{{slide.subtitle}}</h2>

 <p>

 {{slide.description}}

 </p>

 <ion-icon name="{{slide.icon}}"></ion-icon>

 </ion-slide>

 </ion-slides>

</ion-content>
```