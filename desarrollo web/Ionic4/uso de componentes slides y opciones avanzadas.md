# Uso de componente Slides y opciones avanzadas

home.page.ts
```ts
import { Component } from '@angular/core';

@Component({

 selector: 'app-home',
 templateUrl: 'home.page.html',
 styleUrls: ['home.page.scss'],

})

export class HomePage {

 artists = [ {}, {}, {}, {}, {}, {}, {}, {}, {}, {}, ];

 slideOps = {
	 initialSlide: 2,
	 slidesPerView: 4,
	 centeredSlides: true,
	 speed: 400
 };

 constructor() {}
}
```

home.page.htmll

```html
<ion-header>
	 <ion-toolbar>
		 <ion-buttons slot="end">
			 <ion-menu-button></ion-menu-button>
		 </ion-buttons>
	 </ion-toolbar>
</ion-header>
<ion-content fullscreen="true" class="ion-padding">
	 <h1>Artistas</h1>
		 <ion-slides [options]='slideOps' *ngIf="artists.length">
			 <ion-slide *ngFor="let artist of artists">
				 <ion-avatar>
					 <img src="https://via.placeholder.com/150" alt="">
					 <span>Nombre del artista</span>
				 </ion-avatar>
			 </ion-slide>
		 </ion-slides>
	 <h1>Artistas</h1>
		 <ion-slides [options]='slideOps' *ngIf="artists.length">
			 <ion-slide *ngFor="let artist of artists">
				 <ion-avatar>
					 <img src="https://via.placeholder.com/150" alt="">
					 <span>Nombre del artista</span>
				 </ion-avatar>
			 </ion-slide>
		 </ion-slides>
	 <h1>Artistas</h1>
		 <ion-slides [options]='slideOps' *ngIf="artists.length">
			 <ion-slide *ngFor="let artist of artists">
				 <ion-avatar>
					 <img src="https://via.placeholder.com/150" alt="">
					 <span>Nombre del artista</span>
				 </ion-avatar>
			 </ion-slide>
		 </ion-slides>
</ion-content>
```


El componente ion-slides va a ser desactivado a partir de Ionic 7 y se recomienda trabajar con Swiper, ver [documentación](https://ionicframework.com/docs/api/slides#what-is-swiperjs). Les comparto el código usando Swiper:

```html
<ion-content [fullscreen]="true" class="ion-p adding">
  <h1>Artistas swiper</h1>
  <swiper [config]="slideOps" *ngIf="artists.length">
    <ng-template swiperSlide *ngFor="let artstis of artists">
      <div>
      <ion-avatar>
        <img src="https://via.placeholder.com/150" />
        <span>artista</span>
      </ion-avatar>
      </div>
    </ng-template>
  </swiper>
</ion-content>
```