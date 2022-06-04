# Controlar la navegación con Guards

ionic por defecto trae la rutas rutas predefinidas, por lo que cuando la aplicación se abra se va a ver directamente el componente home.

Sin embargo se quiere visualizar primero el componente intro para lo cual haremos lo siguiente con los guards de angular

lo primero es generar el guard

```
ionic generate guard guards/intro
```

dentro del guard para poder hacer una redirección se debe aplicar el siguiente código

intro.guard.ts
```ts
import { Injectable } from '@angular/core';

import { ActivatedRouteSnapshot, CanActivate, RouterStateSnapshot, Router } from '@angular/router';

import { Storage } from '@ionic/storage-angular';

  

@Injectable({

 providedIn: 'root'

})

export class IntroGuard implements CanActivate {

 constructor(

 private storage: Storage,

 private router: Router,

 ) {
 // fundamental para poder ejecutar una solicitud de información al local storage

 this.storage.create();

 }

 async canActivate(

 route: ActivatedRouteSnapshot,

 state: RouterStateSnapshot,): Promise<boolean> {

 const isIntroShowed = await this.storage.get('isIntroShowed');

 if(isIntroShowed) {

 return true;

 } else {

 this.router.navigateByUrl('/intro');

 }

 }

}
```

debido a esto es necesario implmentar en nuestro archivo de rutas el guardian en nuestro modulo home

app-routing.module.ts
```ts
import { IntroGuard } from './guards/intro.guard';

const routes: Routes = [

 {

 path: 'home',

 loadChildren: () => import('./home/home.module').then( m => m.HomePageModule),

 canActivate: [IntroGuard]

 },

];
```