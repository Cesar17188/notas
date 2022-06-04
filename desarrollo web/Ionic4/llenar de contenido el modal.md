# Llenar de contenido el Modal

vamos a cambiar el page ts de nuestro songs modal para que por medio de los parametros recibidos desde el home.page se pueda observar las canciones y el artista seleccionado

songs-modal.page.ts
```ts
import { Component } from '@angular/core';
import { ModalController, NavParams } from '@ionic/angular';

@Component({
 selector: 'app-songs-modal',
 templateUrl: './songs-modal.page.html',
 styleUrls: ['./songs-modal.page.scss'],
})
export class SongsModalPage {
 songs: any[] = [];
 artist = '';

 constructor(
	 private navParams: NavParams,
	 private modalController: ModalController
 ) { }

 ionViewDidEnter() {
	 this.songs = this.navParams.data.songs;
	 this.artist = this.navParams.data.artist;
 }

 async selectSong(song) {
	 await this.modalController.dismiss(song);
 }
}
```

ingresamos la información maquetada a nuestro a html del modal songs-modal

songs-modal.page.html
```html
<ion-header>
	 <ion-toolbar>
		 <ion-title>{{artist + ' - Top tracks'}}</ion-title>
		 <ion-buttons slot="end">
			 <ion-button (click)="selectSong('')">Cerrar</ion-button>
		 </ion-buttons>
	 </ion-toolbar>
</ion-header>

<ion-content>
	 <ion-list>
		 <ion-item *ngFor="let song of songs; index as i" (click)="selectSong(song)">
			 <ion-avatar>
				 {{i+1}}
				 <ion-label>
					 <h2>{{ song.name }}</h2>
					 <p>{{ song.popularity }}</p>
				 </ion-label>
			 </ion-avatar>
		 </ion-item>
	 </ion-list>
</ion-content>
```

finalmente estilizamos nuestro songs-modal desde el scss

songs-modal.page.scss
```scss
ion-avatar {
 width: 100%;
 display: grid;
 grid-template-columns: 20px auto;
 align-items: center;
}

  

ion-avatar ion-label {
 display: grid;
 grid-template-rows: auto auto;
 transform: translateX(15px);
}
```