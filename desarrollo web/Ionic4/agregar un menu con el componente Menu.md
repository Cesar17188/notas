# Agregar un menú con el componente Menu

primero generamos una nueva página con

```
ionic generate page menu
```

Ahora vamos a hacer un cambio en el routing module principal para que sea la page de menu la que se carge por defecto y que el routing module de home sea cargado desde menu como contenido

Los cambios empiezan en el app-routing.module.ts

app-rotuing.module.ts
```ts
const routes: Routes = [
 {
	 path: '',
	 redirectTo: 'menu',
	 pathMatch: 'full'
 },
 {
	 path: 'menu',
	 loadChildren: () => import('./menu/menu.module').then( m => m.MenuPageModule),
	 canActivate: [LoginGuard, IntroGuard]
 },
];
```

posteriormente hacemos los cambios en el routing de la page de menu

menu-routing.module.ts
```ts
const routes: Routes = [
 {
	 path: '',
	 component: MenuPage,
	 children: [
		 {
			 path: 'home',
			 loadChildren: () => import('../home/home.module').then( m => m.HomePageModule)
		 }
	 ]
 }
];
```

finalmente hacemos el cambio en el html de la page de menu

menu.page.html
```html
<ion-split-pane contentId="content">
	 <ion-menu contentId="content" side="end">
		 <ion-header>
			 <ion-toolbar>
				 <ion-title>Menu</ion-title>
				 <ion-buttons>
					 <ion-button icon-only (click)="closeMenu()">
					   <ion-icon name="arrow-back-outline" size="large"></ion-icon>
					 </ion-button>
				 </ion-buttons>
			 </ion-toolbar>
		 </ion-header>
 
		 <ion-content>
			 <ion-list>
				 <ion-item>Home</ion-item>
				 <ion-item>Settings</ion-item>
			 </ion-list>
		 </ion-content>
	 </ion-menu>
	 <ion-router-outlet id="content" main></ion-router-outlet>
</ion-split-pane>
```

