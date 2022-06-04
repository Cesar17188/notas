# Transformar peticiones

Algunas veces vamos a necesitar de transformar peticiones, es decir que el backend nos envie unos datos pero se necesita agregar más información por que en el front-end se quiere dar algún ordenamiento o agregar un campo extra.

cambiamos la extructura del modelo para incrementar un parametro nuevo

products.model.ts
```ts
export interface Product {

 id: number;

 title: string;

 price: number;

 description: string;

 images: string[];

 category: Category;

 taxes?: number;

}
```

luego vamos al servicio donde implementaremos **map** para cambiar los datos recibidos desde el backend

product.service.ts
```ts

import { retry, catchError, map } from 'rxjs/operators';

getAllProducts(limit?: number, offset?: number) {

 let params = new HttpParams();

 if (limit && offset) {

	 params = params.set('limit', limit);

	 params = params.set('offset', limit);

 }

 return this.http.get<Product[]>(this.apiUrl, { params })

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

finalmente cambiamos el product component

product.component.ts
```ts
 @Input() product: Product = {

 id: 0,

 price: 0,

 images: [],

 title: '',

 description: '',

 category: {

 id: 0,

 name: '',

 typeImg: ''

 },

 taxes: 0

 };
```

product.component.html
```html
<p *ngIf="product.taxes"> Iva: {{ product?.taxes | currency}}</p>
```

RxJS map() operator is a transformation operator used to transform the items emitted by an Observable by applying a function to each item.  
[Documentación](https://angular.io/guide/rx-library)