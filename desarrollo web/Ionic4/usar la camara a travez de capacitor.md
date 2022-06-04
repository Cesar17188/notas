# Usar la cámara a través de Capacitor

Para lograr un uso correcto de la camara con capacitor primero crearemos la página de settings 

```
ionic generate page settings
```

posteriormente vamos a instalar varias librerias que seran necesarias para el uso de la camara 

esta librería nos permitira el uso de los plugins de la cámara
```
npm install @capacitor/camera
```

esta librería cambiara el modo de vista del window adaptandose a una pwa (progressive web apps), necesario para el uso de plugins como camera o toast
```
npm install @ionic/pwa-elements -save
```

posteriormente hacemos un cambio en nuestro main.ts

main.ts
```ts
import { defineCustomElements } from '@ionic/pwa-elements/loader';

defineCustomElements(window);
```

haremos el cambio en nuestro para enviar desde app-routing.module.ts a nuestro menu-routing.module.ts la page de settings, como un hijo más de menu

menu-routing.module.ts
```ts
const routes: Routes = [

  {
    path: '',
    component: MenuPage,
    children: [
      {
        path: 'settings',
        loadChildren: () => import('../settings/settings.module').then( m => m.SettingsPageModule)
      }
    ]
  }
];
```

posteriormente hacemos el cambio en nuestro menupage para redireccionar con interfaz a settingspage

menu.page.ts
```ts
goToSettings() {
    this.navCtrl.navigateRoot('menu/settings');
  }
```

menu.page.html
```html
<ion-list>
        <ion-item>Home</ion-item>
        <ion-item>Sports</ion-item>
        <ion-item (click)="goToSettings()">Settings</ion-item>
        <ion-item (click)="logout()">
          <ion-icon name="log-out" color="primary" slot="start"></ion-icon>
          Salir 
        </ion-item>
</ion-list>
```

ahora configuraremos nuestro settingspage para tomar una foto y posicionarla como imagen de usuario o cargar una imagen predefinida desde assets

settings.page.ts
```ts
import { Component, OnInit } from '@angular/core';
import { DomSanitizer, SafeResourceUrl } from '@angular/platform-browser';
import{ Camera, CameraResultType, CameraSource  } from '@capacitor/camera';

@Component({
  selector: 'app-settings',
  templateUrl: './settings.page.html',
  styleUrls: ['./settings.page.scss'],
})

export class SettingsPage implements OnInit {
  userImage = 'assets/img/foto1.jpg';
  photo: SafeResourceUrl;
  
  constructor(
    private sanitizer: DomSanitizer
  ) { }

  ngOnInit() {
  }

  async takePhoto() {
    const image = await Camera.getPhoto({
      quality: 100,
      allowEditing: false,
      resultType: CameraResultType.DataUrl,
      source: CameraSource.Camera
    });
    this.photo = this.sanitizer.bypassSecurityTrustResourceUrl(
      image && image.dataUrl
    );
  }
}
```

settings.page.html
```html
<ion-header>
  <ion-toolbar>
    <ion-title>settings</ion-title>
  </ion-toolbar>
</ion-header>

<ion-content>
  <ion-avatar (click)="takePhoto()">
    <img [src]="userImage" alt="" *ngIf="!photo">
    <img [src]="photo" alt="" *ngIf="photo">
  </ion-avatar>
</ion-content>
```