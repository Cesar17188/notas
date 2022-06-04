# RETO: Vista de álbums

crearemos una función que recupere los tracks de los albums desde la API por lo que cambiaremos primero nuestro musicService

platzi-music.service.ts
```ts
private urlapi = 'https://platzi-music-api.herokuapp.com';

  

 constructor(

 private http: HttpClient

 ) { }


getAlbumTracks(albumId) {

 return this.http.get(`${this.urlapi}/albums/${albumId}/tracks?country=EC`);

 }
```

ahora incrementaremos la siguiente función en nuestro home.page.ts

home.page.ts
```ts
showAlbums(album) {
	 this.musicService.getAlbumTracks(album.id)
	 .subscribe(songs => {
	 this.modalAlbum(songs, album);
	 }, error => {
		 console.error(error);
	 });
 }

async modalAlbum(songs, album) {
	 const modal = await this.modalController.create({
		 component: SongsModalPage,
		 componentProps: {
			 songs: songs.items,
			 artist: album.name
		 }
	 });
 
 modal.onDidDismiss().then(dataReturned => {
	 this.song = dataReturned.data;
	 });
	 return modal.present();
 }
```

finalmente actualizamos un html de nuestro home page en la seccion de albums

home.page.html
```html
<h1>Albums</h1>
 <ion-slides [options]='slideOps' *ngIf="albums.length">
	 <ion-slide *ngFor="let album of albums">
		 <ion-avatar (click)="showAlbums(album)" class="square-avatar">
			 <img [src]="album.images[0].url" alt="">
			 <span>{{album.name}}</span>
		 </ion-avatar>
	 </ion-slide>
 </ion-slides>
``` 