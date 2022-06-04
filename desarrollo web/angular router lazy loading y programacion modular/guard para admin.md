# Guard para Admin

lo primero que debemos hace es crear un guardian para administradores

```
ng g g guards/admin
```

denuevo seleccionamos la interfaz de canActivate

Y con esto vamos a verificar que el usuario sea un administrador

admin.guard.ts
```ts
import { Injectable } from '@angular/core';

import { ActivatedRouteSnapshot, CanActivate, RouterStateSnapshot, UrlTree, Router } from '@angular/router';

import { map, Observable } from 'rxjs';

  

import { AuthService } from '../services/auth.service';

  

@Injectable({

 providedIn: 'root'

})

export class AdminGuard implements CanActivate {

  

 constructor(

	 private authService: AuthService,

	 private router: Router

 ){}

  

 canActivate(

	 route: ActivatedRouteSnapshot,

	 state: RouterStateSnapshot): Observable<boolean | UrlTree> | Promise<boolean | UrlTree> | boolean | UrlTree {

 return this.authService.user$

	 .pipe(

		 map(user => {

		 if(user?.role === 'admin') {

			 return true;

		 } else {

			 this.router.navigate(['/home']);

			 return false;

		 }

	 })

	 )

  } 

}
```

con esto importamos nuestro guardian en el app-routing.module.ts y lo colocamos en nuestro módulo cms

app-routing.module.ts
```ts
import { AdminGuard } from './guards/admin.guard';


const routes: Routes = [

{

 path: 'cms',

 canActivate: [AdminGuard],

 loadChildren: () => import('./cms/cms.module').then( m => m.CmsModule )

 }

];
```

finalmente podemos hacer un cambio en el profile para que nos muestre un link de acceso al modulo cms si es un usuario administrador

profile.component.html
```html
<a *ngIf="user.role === 'admin'" routerLink="/cms">Ir al CMS</a>
```