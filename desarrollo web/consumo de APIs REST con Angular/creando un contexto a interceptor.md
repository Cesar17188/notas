# Creando un contexto a interceptor

Para poder elegir que peticiones especificamente quiero interceptar en lugar de todas

time.interceptor.ts
```ts
import { Injectable } from '@angular/core';

import {

 HttpRequest,

 HttpHandler,

 HttpEvent,

 HttpInterceptor,

 HttpContext,

 HttpContextToken,

} from '@angular/common/http';

import { Observable } from 'rxjs';

import { tap } from 'rxjs/operators';

  

const CHECK_TIME = new HttpContextToken<boolean>(() => false);

  

export function checkTime() {

 return new HttpContext().set(CHECK_TIME, true);

}

  

@Injectable()

export class TimeInterceptor implements HttpInterceptor {

  

 constructor() {}

  

 intercept(request: HttpRequest<unknown>, next: HttpHandler): Observable<HttpEvent<unknown>> {

 if(request.context.get(CHECK_TIME)) {

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

 return next.handle(request);

 }

  

}
```

product.service.ts
```ts
import { checkTime } from '../interceptors/time.interceptor';

 getAllProducts(limit?: number, offset?: number) {

 let params = new HttpParams();

 if (limit && offset) {

 params = params.set('limit', limit);

 params = params.set('offset', limit);

 }

 return this.http.get<Product[]>(this.apiUrl, { params, context: checkTime() })

 .pipe(

 retry(3),

 map(products => products.map(item => {

 return {

 ...item,

 taxes: .12 * item.price

 }

 }))

 );

 }
```