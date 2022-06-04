# Manejo de errores

Con el manejo de observables debemos ver como es el manejo de errores

Se puede obtener un manejo de errores desde el servicio para el manejo de excepciones en el backend

product.service.ts
```ts

import { HttpClient, HttpParams, HttpErrorResponse, HttpStatusCode } from '@angular/common/http';

import { retry, catchError } from 'rxjs/operators';

import { throwError } from 'rxjs';




getProduct(id: number) {

	 return this.http.get<Product>(`${this.apiUrl}/${id}`)

	 .pipe(

		 catchError((error: HttpErrorResponse) => {

		 switch(error.status) {
	
		 case HttpStatusCode.Conflict:

			return throwError(() => new Error ('Ups algo esta fallando en el server'));

		 case HttpStatusCode.NotFound:

			 return throwError(() => new Error ('El producto no existe'));

		 default:

			 return throwError(() => new Error ('Ups algo salio mal'));
	
			 }

		 })

	 )

 }
```

Tambien se puede hacer manejo de errores desde el front end, utilizano la libreria sweetalert2
[sweetalert2](https://sweetalert2.github.io/#download)
[sweetalert2 Github](https://github.com/sweetalert2/ngx-sweetalert2)

Lo primero es importar la sweetalert2 en nuestro app.module.ts

app.module.ts
```ts
import { SweetAlert2Module } from '@sweetalert2/ngx-sweetalert2';

@NgModule({

	imports: [
		SweetAlert2Module
	],
})


```

despues activamos el manejo de errores con sweetalert2 en nuestro products.component

products.component.ts
```ts

import Swal from 'sweetalert2';

export class ProductsComponent implements OnInit {
 statusDetail: 'loading' | 'success' | 'error' | 'init' = 'init';
}


onShowDetail(id: number) {

 this.statusDetail = 'loading';

 this.productsService.getProduct(id)

 .subscribe({

	 next: (v) => this.showDetailOk(v),

	 error: (e) => this.showDetailError(e),

	 complete: () => console.info('complete')

	 });

 }

  

 showDetailOk(data: Product) {

	 this.statusDetail = 'success';

	 console.log('producto obtenido: ', data);

	 this.toggleProductDetail();

	 this.productChosen = data;

 }

  

 showDetailError(e: any) {

	 this.statusDetail = 'error';

	 this.toggleProductDetail();

	 Swal.fire({

		 title: 'Error!',

		 text: e,

		 icon: 'error',

		 confirmButtonText: 'Ok',

	 });

 }
```