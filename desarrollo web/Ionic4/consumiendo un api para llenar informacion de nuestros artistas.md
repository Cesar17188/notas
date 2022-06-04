# Consumiendo un API para llenar información de nuestros artistas

Creamos un servicio para consumir el API requerido de platzi-music-service

```
ionic generate service services/platzi-music
```

Luego lo configuramos para consumir el API

platzi-music.service.ts
```ts
import { Injectable } from '@angular/core';
import { HttpClient } from '@angular/common/http';

@Injectable({
 providedIn: 'root'
})

export class PlatziMusicService {

 private urlapi = 'https://platzi-music-api.herokuapp.com/browse/new-releases';

 constructor(
 private http: HttpClient
 ) { }

 getNewreleases(): any {
 return this.http.get(this.urlapi);
 }
}
```

Posteriormente hacemos el cambio en home page para consumir el servicio de platzi-music

home.page.ts
```ts
import { PlatziMusicService } from '../services/platzi-music.service';

@Component({
 selector: 'app-home',
 templateUrl: 'home.page.html',
 styleUrls: ['home.page.scss'],
})

export class HomePage {
	 artists: any[] = [];
	 songs: any[] = [];
	 albums: any[] = [];

 slideOps = {
	 initialSlide: 2,
	 slidesPerView: 4,
	 centeredSlides: true,
	 speed: 400
 };

 constructor(
	 private musicService: PlatziMusicService
 ) {}

// renderiza cambios en la entrada directamente en la vista
 ionViewDidEnter() {
	 this.fetchNewReleases();
 }

 fetchNewReleases() {
	 this.musicService.getNewreleases()
	 .subscribe(release => {
	 this.artists = release.albums.items;
	 this.songs = this.artists.filter(e => e.album_type ==='single');
	 this.albums = this.artists.filter(e => e.album_type ==='album');
	 console.log(this.artists);
	 });
  }
}
```

Gracias a esto, se pueden hacer cambios directamente en el html de home page

home.page.html
```html
<ion-header>
	 <ion-toolbar>
		 <ion-buttons slot="end">
			 <ion-menu-button></ion-menu-button>
		 </ion-buttons>
	 </ion-toolbar>
</ion-header>
<ion-content fullscreen="true" class="ion-padding">
	 <h1>Albums</h1>
		 <ion-slides [options]='slideOps' *ngIf="albums.length">
			 <ion-slide *ngFor="let album of albums">
		 <ion-avatar>
			 <img [src]="album.images[0].url" alt="">
			 <span>{{album.name}}</span>
		 </ion-avatar>
	 </ion-slide>
 </ion-slides>
 <h1>Canciones</h1>
	 <ion-slides [options]='slideOps' *ngIf="songs.length">
		 <ion-slide *ngFor="let song of songs">
			 <ion-avatar>
				 <img [src]="song.images[0].url" alt="">
				 <span>{{song.name}}</span>
			 </ion-avatar>
		 </ion-slide>
	 </ion-slides>
</ion-content>
```

Para poder consumir datos desde un api o un backend es necesario tener un servicio que logre esta funcionalidad

**TIP**

–  
Angular tiene su propia librería **HttpClient** (con mucho más poder) para manejar peticiones **HTTP**

En el siguiente enlace pueden encontrar una explicación muy buena [(Peticiones Http en Angular)](https://academia-binaria.com/comunicaciones-http-en-Angular/)

–  
Hacen uso de conceptos más avanzados (pero hoy día cotidianos) como son _**observables**_ de la librería **RxJs**, aquí pueden leer más a fondo y con ejemplos reales que pueden acomodar para uso en sus propios proyectos. [(Vigilancia y Seguridad en Angular)](https://academia-binaria.com/vigilancia-y-seguridad-en-Angular/)

–  
Por último, un concepto que es **MUY ÚTIL** y la razón por la que dejo esta información. **_Interceptores,_** un mecanismo usado en aplicaciones realmente profesionales, les permite por ejemplo _**interceptar**_ la petición HTTP antes del llamado al API y luego del llamado al API. Esto es muy potente a la hora de trabajar en ámbitos profesionales. [Punto 3. Gestor de Credenciales](https://academia-binaria.com/formularios-reactivos-con-Angular/)



Link del API:  
[https://platzi-music-api.now.sh/browse/new-releases](https://platzi-music-api.now.sh/browse/new-releases)
