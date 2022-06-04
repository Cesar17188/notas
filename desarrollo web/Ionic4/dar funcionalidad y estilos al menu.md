# Dar funcionalidad y estilos al menú
hacemos los siguientes cambios en el menu page

menu.page.ts
```ts
import { Component, OnInit } from '@angular/core';
import { MenuController, NavController } from '@ionic/angular';
import { Storage } from '@ionic/storage-angular';

@Component({
 selector: 'app-menu',
 templateUrl: './menu.page.html',
 styleUrls: ['./menu.page.scss'],
})

export class MenuPage implements OnInit {

 constructor(
	 private menu: MenuController,
	 private navCtrl: NavController,
	 private storage: Storage
 ) { }

 ngOnInit() {
 }

 closeMenu() {
	 this.menu.close();
 }

 logout() {
	 this.storage.remove('isUserLoggedIn');
	 this.navCtrl.navigateRoot('/login');
 }
}
```

menu.page.html

```html
<ion-split-pane contentId="content">
	 <ion-menu contentId="content" side="end">
		 <ion-header>
			 <ion-toolbar>
				 <ion-title>Menu</ion-title>
				 <ion-buttons slot="start">
					 <ion-button (click)="closeMenu()">
						 <ion-icon name="arrow-forward" size="large"></ion-icon>
					 </ion-button>
				 </ion-buttons>
			 </ion-toolbar>
		 </ion-header>
		 <ion-content>
			 <ion-list>
				 <ion-item>Home</ion-item>
				 <ion-item>Sports</ion-item>
				 <ion-item>Settings</ion-item>
				 <ion-item (click)="logout()">
					 <ion-icon name="log-out" color="primary" slot="start"></ion-icon>
					 Salir
					 </ion-item>
			</ion-list>
		 </ion-content>
	 </ion-menu>
	 <ion-router-outlet id="content" main></ion-router-outlet>
</ion-split-pane>
```