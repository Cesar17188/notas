# Uso de interceptores

Los interceptores van a estar en medio de cada solicitud hecah desde la aplicación hacia el backend, la vana interceptar, la agregan algo que tenemos en código como por ejemplo los tokens en las peticiones

Los interceptors en Angular nos brindan un mecanismo para interceptar y/o mutar las solicitudes y respuestas http.  

![18-interceptors.png](https://static.platzi.com/media/user_upload/18-interceptors-1c1ac484-55f3-443f-a313-151c014fe693.jpg)

Para qué sirve multi: true?

Prácticamente permite “construir” multiples dependencias para un mismo token. Es una forma de extender un token en particular para un objeto (provider), angular utiliza esta forma para hacer hooks conectables.

lo primero es crear el interceptor

```
ng g interceptor interceptors/time --flat

```

luego incluimos una lógica que va a tomar el tiempo que demora cada request al backend

time.interceptors.ts
```ts
import { Injectable } from '@angular/core';

import {

 HttpRequest,

 HttpHandler,

 HttpEvent,

 HttpInterceptor

} from '@angular/common/http';

import { Observable } from 'rxjs';

import { tap } from 'rxjs/operators';

  

@Injectable()

export class TimeInterceptor implements HttpInterceptor {

  

 constructor() {}

  

 intercept(request: HttpRequest<unknown>, next: HttpHandler): Observable<HttpEvent<unknown>> {

 const start = performance.now();

 return next

 .handle(request)

 .pipe(

 tap(() => {

 const time = (performance.now() - start) + 'ms';

 console.log(request.url, time);

 })

 );

 }

}
```

finalmente importarmos el interceptor al app.module de forma manual

app.module.ts
```ts
import { TimeInterceptor } from './interceptors/time.interceptor';

@NgModule({
providers: [
	{ provide: HTTP_INTERCEPTORS, useClass: TimeInterceptor, multi: true }
]
})
```