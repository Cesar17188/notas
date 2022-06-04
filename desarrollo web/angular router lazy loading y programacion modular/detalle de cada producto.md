# Detalle de cada producto

creamos un componente explicito para mostrar un detalle del producto el cual nos da un link directo al producto seleccionado

primero creamos el componente de product-detail

```
ng g c pages/product-detail
```

Agregamos el product-detail a nuestras rutas

app-routing.module.ts
```ts
import { ProductDetailComponent } from './pages/product-detail/product-detail.component';

const routes: Routes = [


 {

 path: 'product/:id',

 component: ProductDetailComponent

 }

];
```

colocamos la lógica del detalle del producto en su componente utilizando el servicio de products para obtener un solo producto mediante su id

product-detail.component.ts
```ts
import { Component, OnInit } from '@angular/core';

import { Location } from '@angular/common';

import { ActivatedRoute } from '@angular/router';

  

import { switchMap } from 'rxjs/operators';

  

import { Product } from 'src/app/models/product.model';

import { ProductsService } from 'src/app/services/products.service';

  

@Component({

 selector: 'app-product-detail',

 templateUrl: './product-detail.component.html',

 styleUrls: ['./product-detail.component.scss']

})

export class ProductDetailComponent implements OnInit {

  

 productId: number | string | null = null;

 product: Product | null = null;

  

 constructor(

 private route: ActivatedRoute,

 private productsService: ProductsService,

 private location: Location

 ) { }

  

 ngOnInit(): void {

 this.route.paramMap

 .pipe(

 switchMap( params => {

 // mucha atención con el nombre del parametro en get debe ser el mismo que en app-routing.module.ts

 this.productId = params.get('id');

 if ( this.productId ) {

 return this.productsService.getProduct(this.productId)

 }

 return [null];

 }))

 .subscribe(data => {

 this.product = data;

 });

 }

  

 goToBack() {

 this.location.back();

 }

  

}
```

product-detail.component.html

```html
<div class="page-product">

 <button (click)="goToBack()">Back</button>

 <div class="detail" *ngIf="product">

 <div class="gallery">

 <swiper [slidesPerView]="1">

 <ng-template swiperSlide *ngFor="let img of product?.images">

 <img [src]="img" alt="img">

 </ng-template>

 </swiper>

 </div>

 <div>

 <h1>{{ product?.title }}</h1>

 <h2> {{ product?.price | currency }}</h2>

 <h2> {{product?.description }}</h2>

 </div>

 </div>

</div>
```

product-detail.component.scss
```scss
.page-product {

 padding: 0 3em;

 .detail {

 display: grid;

 grid-template-columns: repeat(auto-fit, minmax(100px, 1fr));

 grid-gap: 20px;

 .gallery {

 overflow: hidden;

 width: 100%;

 }

 h2, h1 {

 margin-bottom: 5px;

 font-weight: bold;

 font-size: 2em;

 }

 h2 {

 font-size: 1.2em;

 font-weight: normal;

 }

 }

}
```

Finalmente en el componente de product, hacemos un router link para enviar por medio de la imagen a la ruta seleccionada del detalle de cada producto

product.component.html
```html
<a [routerLink]="['/product', product.id]">

 <app-img *ngIf="product.images.length > 0" [img]='product.images[0]'></app-img>

</a>
```