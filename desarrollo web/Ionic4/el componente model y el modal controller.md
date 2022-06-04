# El componente Modal y el Modal Controller

crearemos una nueva page llamada songs-modal

```
ionic generate page songs-modal
```

importamos el modulo de songs-modal en nuestro modulo raiz app.module.ts

app.module.ts
```ts
import { SongsModalPageModule } from './songs-modal/songs-modal.module';

@NgModule({
 imports: [
	 SongsModalPageModule,
 ],
})
```

cambiamos el consumo del API en el servicio de platzi-music

platzi-music.service.ts
```ts
import { Injectable } from '@angular/core';
import { HttpClient } from '@angular/common/http';
import * as dataArtists from './artists.json';

@Injectable({
 providedIn: 'root'
})

export class PlatziMusicService {
 private urlapi = 'https://platzi-music-api.herokuapp.com';
 
 constructor(
 private http: HttpClient
 ) { }

 getNewreleases(): any {
	 return this.http.get(`${this.urlapi}/browse/new-releases`);
 }
 
 getArtists() {
	 return dataArtists;
 }

 getArtistTopTracks(artistId) {
	 return this.http.get(`${this.urlapi}/artists/${artistId}/top-tracks?country=EC`);
 }
}
```

posteriormente ingresamos el modal y consumimos la nueva función de nuestro servicio platzi-music en la page home

home.page.ts
```ts
import { SongsModalPage } from '../songs-modal/songs-modal.page';


showSongs(artist) {
 this.musicService.getArtistTopTracks(artist.id)
 .subscribe(songs => {
	 this.modalSong(songs, artist);
 }, error => {
	 console.error(error);
	 });
 }

 async modalSong(songs, artist) {
	 const modal = await this.modalController.create({
		 component: SongsModalPage,
		 componentProps: {
			 songs: songs.tracks,
			 artist: artist.name
		 }
	 });
	 return await modal.present();
 }
```