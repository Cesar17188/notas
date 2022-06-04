# Conoce a los Guardianes

Los Guards en Angular, son de alguna manera: middlewares que se ejecutan antes de cargar una ruta y determinan si se puede cargar dicha ruta o no.

Es la forma en que se protegen las rutas, quiere decir que ciertas rutas van a tener acceso o no de acuerdo a una condición, por ejemplo que el modulo de cms solo debe estar para modulos administrativos

Primero creamos un guardian

```
ng g g guards/auth
```

nos preguntara la interface del guardian que queremos implementar: 
* CanActivate: darle acceso a una ruta a un usuario de acuerdo a un condicional
* CanActivateChild: darle acceso a los componentes hijos de una ruta
* CanDeactivate: desactivar el acceso a la ruta
* CanLoad: darle permiso de carga

Cada uno tiene un uso en específico
Por ahora solo seleccionamos el canActivate

luego de esto podemos ver como funciona nuestro guardian en donde siempre devolvera un booleano que permitira el acceso (true) o no (false)

Para que esto se active es necesario hacer una interfaz con un condicional, en este caso sera por el rol que el usuario tenga junto con si tiene un token de acceso.

paso a paso
Cambiar el modelo de usuario para agregar roles
user.model.ts
```ts
export interface User {

 id: string;

 name: string;

 email: string;

 password: string;

 role: 'customer' | 'admin';

}

  
  

export interface CreateUserDTO extends

Omit<User, 'id'>{}
```

vamos a enviar los datos al componente de profile
website/pages/profile
profile.components.ts

```ts
import { Component, OnInit } from '@angular/core';

import { AuthService } from './../../../services/auth.service';

import { User } from './../../../models/user.model';

  

@Component({

 selector: 'app-profile',

 templateUrl: './profile.component.html',

 styleUrls: ['./profile.component.scss']

})

export class ProfileComponent implements OnInit {

  

 user: User | null = null;

  

 constructor(

 private authService: AuthService

 ) { }

  

 ngOnInit(): void {

 this.authService.getProfile()

 .subscribe(data => {

 this.user = data;

 })

 }

  

}

```

profile.components.html
```html
<div *ngIf="user">

 <h1>My Profile</h1>

 <p>Nombre: {{user.name}}</p>

 <p>Email: {{user.email}}</p>

 <p>Role: {{user.role}}</p>

</div>
```

administramos el guardian que protegera la ruta del profile
auth.guard.ts
```ts
import { Injectable } from '@angular/core';

import { ActivatedRouteSnapshot, CanActivate, RouterStateSnapshot, UrlTree } from '@angular/router';

import { Observable } from 'rxjs';

  

import { TokenService } from '../services/token.service';

  

@Injectable({

 providedIn: 'root'

})

export class AuthGuard implements CanActivate {

  

 constructor(

 private tokenService: TokenService

 ) { }

  
  

 canActivate(

 route: ActivatedRouteSnapshot,

 state: RouterStateSnapshot): Observable<boolean | UrlTree> | Promise<boolean | UrlTree> | boolean | UrlTree {

 const token = this.tokenService.getToken();

 return token ? true : false;

 }

  

}
```

finalmente protegemos la ruta desde el website-routing.module.ts
```ts
import { AuthGuard } from './../guards/auth.guard';

  

const routes: Routes = [

 {

 path: 'profile',

 canActivate: [AuthGuard],

 component: ProfileComponent

 },

 ]

 },

];
```