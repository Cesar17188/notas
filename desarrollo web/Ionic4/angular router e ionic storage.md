# Angular Router e Ionic Storage

https://github.com/ionic-team/ionic-storage

Como angular Ionic tambien dispone de un router, por lo que moveremos los slides a un componente llamado intro y luego moveremos el contenido de la aplicación a otro componente

para crear una nueva página en ionic se utiliza el comando

```
ionic generate page intro
```

dentro de la aplicación se han generado 6 archivos nuevos dentro de la carpeta app/intro que son:
* intro.module.ts
* intro.page.scss
* intro.page.html
* intro.page.spec.ts
* intro.page.ts

y se actualiza el app-routing.module.ts


movemos el contenido de la carpeta home a la carpeta intro. Es decir:

* home.page.ts -> intro.page.ts
* home.page.html -> intro.page.html
* home.page.scss -> intro.page.scss

Ahora si ingresamos la ruta de nuestro localhost de home a intro apareceran nuestros slides

ahora para poder hacer una ruta de acceso funciona similar a angular, es decir,
si queremos ir del componente intro al componente home es necesario implementar el siguiente código en nuestros componentes intro

intro.page.ts
```ts
import { Router } from '@angular/router';

constructor(

 private router: Router,

 ) { }


finish() {

 this.router.navigateByUrl('/home');

 }
```

intro.page.html
```html
<ion-content padding>

 <ion-slides pager="true" [options]="slideOps">

 <ion-slide *ngFor="let slide of slides">

 <ion-icon name="close" (click)="finish()"></ion-icon>

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


Con el método finish queremos hacer que si el usuario ya vio el intro una vez ya no deba verla denuevo, para eso podemos implementar el código

primero debemos instalar ionic/storage mediante el siguiente código

https://github.com/ionic-team/ionic-storage

```
npm install @ionic/storage-angular
```

posteriormente debemos importalo al IonicStorageModule

app.module.ts
```ts
import { IonicStorageModule } from '@ionic/storage-angular';

@NgModule({
  imports: [
    IonicStorageModule.forRoot()
  ]
})
export class AppModule { }
```

para luego importarlo al componente intro y hacer una inyección de dependencia

intro.page.ts
```ts

import { Storage } from '@ionic/storage-angular';

constructor(

 private storage: Storage,

 ) { }


finish() {
 this.storage.create();
 this.storage.set('isIntroShowed', true);
 }
```

con el this.storage.create y this.storage.set('isIntroShowed', true) nos permite guardar variables en el local storage