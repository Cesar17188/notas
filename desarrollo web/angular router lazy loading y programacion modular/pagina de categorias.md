# Página de categorías
app-routing.module.ts
```ts
{

 path: 'category/:id',

 component: CategoryComponent

 },
```

product.service.ts
```ts

private apiUrl = `${environment.API_URL}/api`;


getByCategory(categoryId: string | number , limit?: number, offset?: number) {

 let params = new HttpParams();

 if (limit && offset != null) {

 params = params.set('limit', limit);

 params = params.set('offset', limit);

 }

 return this.http.get<Product[]>(`${this.apiUrl}/categories/${categoryId}/products`, { params })

 }
```


category.component.ts
```ts
import { Component, OnInit } from '@angular/core';

import { ActivatedRoute } from '@angular/router';

import { Product } from 'src/app/models/product.model';

  

import { ProductsService } from '../../services/products.service';

@Component({

 selector: 'app-category',

 templateUrl: './category.component.html',

 styleUrls: ['./category.component.scss']

})

export class CategoryComponent implements OnInit {

  

 products: Product[] = [];

 limit = 10;

 offset = 0;

  

 categoryId: number | string | null = null;

  

 constructor(

 private route: ActivatedRoute,

 private productsService: ProductsService

 ) { }

  

 ngOnInit(): void {

 this.route.paramMap.subscribe(params => {
 // mucha atención con el nombre del parametro en get debe ser el mismo que en app-routing.module.ts

 this.categoryId = params.get('id');

 if ( this.categoryId !== null ) {

 this.productsService.getByCategory(this.categoryId, this.limit, this.offset)

 .subscribe(data => {

 this.products = data;

 });

 }

 })

 }

  

 onLoadMore() {

 this.productsService.getAllProducts(this.limit, this.offset)

 .subscribe(data => {

 this.products = this.products.concat(data);

 this.offset += this.limit;

 });

 }

  

}
```


category.component.html
```html
<app-products [products] = "products" (loadMore)="onLoadMore()"></app-products>
```