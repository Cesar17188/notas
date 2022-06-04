# Implementando redirects

## Guards

Los Guards en Angular, son de alguna manera: middlewares que se ejecutan antes de cargar una ruta y determinan si se puede cargar dicha ruta o no. Existen 4 tipos diferentes de Guards (o combinaciones de estos) que son los siguientes:

-   (CanActivate) Antes de cargar los componentes de la ruta.
-   (CanLoad) Antes de cargar los recursos (assets) de la ruta.
-   (CanDeactivate) Antes de intentar salir de la ruta actual (usualmente utilizado para evitar salir de una ruta, si no se han guardado los datos).
-   (CanActivateChild) Antes de cargar las rutas hijas de la ruta actual.


https://www.codigocorrecto.com/programacion/angular-2020-como-usar-guard-canactivate-ejemplo-de-uso/

vamos a permitir a nuestro usuarios cerrar sesion y tambien a redireccionar a la pagina de home cuando no tenga autorización de entrada al profile

primero vamos a añadir al token services una forma de eliminar el token de autorización en el momento de cerrar sesión

token.services.ts
```ts
removeToken() {

 localStorage.removeItem('token');

 }
```

Posteriormente añadimos el remove token a nuestro servicios de autenticación para hacer un logout
auth.service.ts
```ts
logout() {

 this.tokenService.removeToken();

 }
```

El guardian debe tomar este condicional de si existe o no un token de autorización y de no existir debe redireccionar a la página home, para lo cual debe importar el Router de angular/router
auth.guard.ts
```ts

import { Router } from '@angular/router';

canActivate(

 route: ActivatedRouteSnapshot,

 state: RouterStateSnapshot): Observable<boolean | UrlTree> | Promise<boolean | UrlTree> | boolean | UrlTree {

 const token = this.tokenService.getToken();

 if (!token) {

 this.router.navigate(['/home']);

 return false;

 }

 return true;

 }
 
 ```

finalmente hacemos los cambios en el componente nav para los ajustes de vista del usuario

nav.component.ts
```ts
import { Router } from '@angular/router';

logout() {

 this.authService.logout();

 this.profile = null;

 this.router.navigate(['/home']);

 }
```

nav.component.html
```html
<div class="info">

 <button *ngIf="!profile; else userProfile" (click)="login()">Login</button>

 <ng-template #userProfile>

 <a routerLink="/profile">{{ profile?.email }}</a>

 <button (click)="logout()">Logout</button>

 </ng-template>

 <div>

 <a href="#">

 <img src="./assets/svg/icon_shopping-cart.svg" alt="shopping_cart">

 <span class="counter">{{ counter }}</span>

 </a>

 </div>

 </div>
```
