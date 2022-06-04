# CanDeactivate

canDeactivate este guardian permite la salida de una ruta.
Este guardian lo podemos utilizar en caso de: 
* cuando nuestro usuario esta llenando un formulario largo y por algún motivo esta saliendo de esa ruta, se envia un mensaje a ese usuario de si esta seguro de salir sin completar el proceso.
* Si estamos cargando archivos pedimos al usuario que tenga la página abierta hasta que terminé el proceso

en este caso vamos a ponerlo en nuestra página de registro

primero creamos el nuevo guardian
```
ng g g guards/exit
```

esta vez elegimos la interface de canDeactivate

Lo segundo es implementar la lógica del guardian en el cual existe un nuevo atributo component, en este podemos ingresar una lógica con un booleano para ser extendido desde los componentes que se necesiten

exit.guard.ts
```ts
import { Injectable } from '@angular/core';

import { ActivatedRouteSnapshot, CanDeactivate, RouterStateSnapshot, UrlTree } from '@angular/router';

import { Observable } from 'rxjs';

  

export interface OnExit {

 onExit: () => Observable<boolean> | Promise<boolean> | boolean;

}

  

@Injectable({

 providedIn: 'root'

})

export class ExitGuard implements CanDeactivate<unknown> {

 canDeactivate(

 component: OnExit,

 currentRoute: ActivatedRouteSnapshot,

 currentState: RouterStateSnapshot,

 nextState?: RouterStateSnapshot): Observable<boolean | UrlTree> | Promise<boolean | UrlTree> | boolean | UrlTree {

 return component.onExit ? component.onExit() : true;

 }

  

}
```

ponemos el guardian en las rutas de website

website-routing.module.ts
```ts
import { ExitGuard } from './../guards/exit.guard';

const routes: Routes = [
{

 path: 'register',

 canDeactivate: [ExitGuard],

 component: RegisterComponent

}
 ]

 },

];
```

finalmente asignamos al componente register el guardian 

register.component.ts
```ts
import { Component } from '@angular/core';

  

import { OnExit } from './../../../guards/exit.guard';

@Component({

 selector: 'app-register',

 templateUrl: './register.component.html',

 styleUrls: ['./register.component.scss']

})

export class RegisterComponent implements OnExit {

  

 constructor() { }

  

 onExit() {

 const rta = confirm('Logica desde comp, estas seguro de salir?');

 return rta;

 }

  

}
```

de esta manera puedes controlar la salida de componentes