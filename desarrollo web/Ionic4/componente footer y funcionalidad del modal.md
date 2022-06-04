# Componente Footer y funcionalidad del Modal

aplicamos unos cambios a nuestro ts del home page

home.page.ts
```ts
// Recomiendo crear una interface de tipo Song para evitar errores futuros, esto es previo al decorador @component
interface Song {
 name?: string;
}


// esta es una variable para tomar el objeto resultante despues de salir del modal

song: Song = {
 name: ''
 };

async modalSong(songs, artist) {
 const modal = await this.modalController.create({
 component: SongsModalPage,
 componentProps: {
 songs: songs.tracks,
 artist: artist.name
 }
 });

 modal.onDidDismiss().then(dataReturned => {
 this.song = dataReturned.data;
 });
 return modal.present();
 }

```

Ingresamos nuestro footer en el page de home con el nombre la canción

home.page.html
```html
<ion-footer>
 <ion-text color="danger" *ngIf="!song?.name">
 <h2>Aquí aparecerá nuestra canción</h2>
 </ion-text>
 <ion-text color="primary" *ngIf="song?.name">
 <h2>{{ song?.name }}</h2>
 </ion-text>
</ion-footer>
```