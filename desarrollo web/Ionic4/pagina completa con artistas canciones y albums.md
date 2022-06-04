# Página completa con artistas, canciones y álbums

primero haremos que se pueda cargar archivos estaticos .json en la aplicación, cambiando la configuracion en tsconfig.json

tsconfig.json
```json
"compilerOptions": {
	...
	 "experimentalDecorators": true,
	 "resolveJsonModule": true,
	 "moduleResolution": "node",
	...
 },
```

luego ingresamos el archivo json "artists.json" dentro de nuestros servicios, con la información de este [archivo](https://static.platzi.com/media/tmp/class-files/git/ionic/ionic-0b43f4f65e1026d2afe15307334d28bda0307cc3/src/app/services/artists.json)

Luego modificamos nuestro servicio de consumo de API platzi-music, para que consuma el archivo json "artists.json"

platzi-music.service.ts
```ts
import * as dataArtists from './artists.json';

... 

getArtists() {
 return dataArtists;
 }
```

Luego vamos al home page para consumir esta nueva función del servicio de platzi-music

home.page.ts
```ts
export class HomePage {
 artists: any[] = [];

 constructor(
 private musicService: PlatziMusicService
 ) {}

ionViewDidEnter() {
 this.fetchArtist();
 }

 fetchArtist() {
	 this.artists = this.musicService.getArtists().items;
 }
```

Hacemos los cambios en el html del home page para incluir a los artistas

home.page.html
```html
<ion-content fullscreen="true" class="ion-padding">
	 <h1>Artistas</h1>
		 <ion-slides [options]='slideOps' *ngIf="artists.length">
			 <ion-slide *ngFor="let artist of artists">
				 <ion-avatar>
					 <img [src]="artist.images[0].url" alt="">
					 <span>{{artist.name}}</span>
				 </ion-avatar>
			 </ion-slide>
		 </ion-slides>
	 <h1>Albums</h1>
		 <ion-slides [options]='slideOps' *ngIf="albums.length">
			 <ion-slide *ngFor="let album of albums">
				 <ion-avatar class="square-avatar">
					 <img [src]="album.images[0].url" alt="">
					 <span>{{album.name}}</span>
				 </ion-avatar>
			 </ion-slide>
		 </ion-slides>
 <h1>Canciones</h1>
	<ion-slides [options]='slideOps' *ngIf="songs.length">
		<ion-slide *ngFor="let song of songs">
			 <ion-avatar class="square-avatar">
				 <img [src]="song.images[0].url" alt="">
				 <span>{{song.name}}</span>
			 </ion-avatar>
		 </ion-slide>
	 </ion-slides>
</ion-content>
```

finalmente hacemos los cambios en los estilos del home page

home.page.scss
```scss
ion-avatar {
 height: 120px;
 width: 90%;
}

ion-avatar img {
 width: 90px;
 height: 90px;
}

ion-avatar span {
 font-size: 12px;
}

.square-avatar {
 --border-radius: 0;
}
```