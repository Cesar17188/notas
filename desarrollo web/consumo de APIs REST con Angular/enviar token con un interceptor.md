# Enviar Token con un interceptor

En la mayoria de sistemas, principalmente sistemas empresariales, todos los endpoints viajan con un token por lo que se debe interceptar cualquier petición y agregarle este token en los headers. 

## En donde vamos a guardar nuestro token

### In-memory storage
La memory storage es guardar el token de autorización en los headers, con el riesgo de que si se cierra el navegador o se recarga la página el token se perderia

## localStorage y sessionStorage

localStorage y sessionStorage son propiedades que acceden al objeto Storage y tienen la función de almacenar datos de manera local, la diferencia entre éstas dos es que localStorage almacena la información de forma indefinida o hasta que se decida limpiar los datos del navegador y sessionStorage almacena información mientras la pestaña donde se esté utilizando siga abierta, una vez cerrada, la información se elimina.


### Cookie storage

La cookie storage tiene una persistencia con el token guardado a pesar de cerrar el navegador y tiene más seguridad que el localStorage




## Pasos

1 creamos el interceptor del token
```
ng g interceptor interceptors/token --flat

```

2 Cambiamos el token service para enviar el token desde el local storage al service y guardarlo ahi, además incluimos el la función para obtener el token desde el servicio

token.service.ts
```ts
import { Injectable } from '@angular/core';

  

@Injectable({

 providedIn: 'root'

})

export class TokenService {

  

 constructor() { }

  

 saveToken(token: string) {

 localStorage.setItem('token', token);

 }

  

 getToken() {

 const token = localStorage.getItem('token');

 return token;

 }

}
```

3 modificamos el interceptor para que previo a interceptar la petición cambie los headers de la petición entrante y añada el token de autorización importado desde el token service

token.interceptor.ts
```ts
import { Injectable } from '@angular/core';

import {

 HttpRequest,

 HttpHandler,

 HttpEvent,

 HttpInterceptor

} from '@angular/common/http';

import { Observable } from 'rxjs';

  

import { TokenService } from './../services/token.service';

  

@Injectable()

export class TokenInterceptor implements HttpInterceptor {

  

 constructor(

 private tokenService: TokenService

 ) {}

  

 intercept(request: HttpRequest<unknown>, next: HttpHandler): Observable<HttpEvent<unknown>> {

 request = this.addToken(request);

 return next.handle(request);

 }

  

 private addToken(request: HttpRequest<unknown>) {

 const token = this.tokenService.getToken();

 if (token) {

 const authReq = request.clone({

 headers: request.headers.set('Authorization', `Bearer ${token}`)

 });

 return authReq;

 }

 return request;

 }

}
```

por lo que ya no es necesario enviar el token como parámetro en las funciones de login y auth sino que se intercepta y se coloca automáticamente