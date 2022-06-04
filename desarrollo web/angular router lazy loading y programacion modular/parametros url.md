# Parámetros URL

hasta ahora solo se ha leido parametros que vienen directamente en el routing cuando lo definimos

Pero los parametros url que son opcionales, para leer estos parámetros debemos verificar como leer los parámetros adjuntos  la url donde estemos, recordando que la url encadena información utilizando '& y ?'  lo cual nos sirve para poder obtener información

enviaremos por medio de Input parametros de tipo query o peticiones hacia el product component por lo que hay que hacer los siguientes cambios. 

Con esto logramos que la página sea completamente shearable y podamos compartirla.

product.component.ts
```ts
@Input()

 set productId(id: number | string | null) {

 if(id) {

 this.onShowDetail(id);

 }

 };

onShowDetail(id: number | string) {

 this.statusDetail = 'loading';

 this.productsService.getProduct(id)

 .subscribe({

 next: (d) => this.showDetailOk(d),

 error: (e) => this.showDetailError(e),

 complete: () => console.info('complete')

 });

 }

  

 showDetailOk(data: Product) {

 this.statusDetail = 'success';

 console.log('producto obtenido: ', data);
 // Enfasis aqui

 if(!this.showProductDetail) {

 this.showProductDetail = true;

 }

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

luego vamos a los componentes padre

home.component.ts

```ts
import { ActivatedRoute } from '@angular/router';

productId: string | number | null = null;

  

 constructor(

 private route: ActivatedRoute

 ) { }

  

 ngOnInit(): void {

 this.route.queryParamMap.subscribe(params => {

 this.productId = params.get('product');

 console.log(this.productId);

 })

 }
```

category.component.ts
```ts
productId: number | string | null = null;

ngOnInit(): void {

 this.route.queryParamMap.subscribe(params => {

 this.productId = params.get('product');

 console.log(this.productId);

 })

 }
```

home.component.html , category.component.html
```html
<app-products

[productId]="productId"

[products]="products"

(loadMore)="onLoadMore()"

></app-products>
```

