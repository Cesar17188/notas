# Solicitudes GET

Cuando nos conectamos a una API manejamos uno verbos sobre HTTP 

## GET
nos sirve para obtener información general de objetos tambien nos sirve para obtener información detallada de un objeto.

app.module.ts
```ts
import { HttpClientModule } from '@angular/common/http';

@NgModule({

 imports: [

 HttpClientModule

 ]
```

product.service.ts
```ts

import { Injectable } from '@angular/core';

import { HttpClient } from '@angular/common/http';

import { Product } from '../models/product.model';

@Injectable({

 providedIn: 'root'

})

export class ProductsService {

  

 private apiUrl = 'https://young-sands-07814.herokuapp.com/api/products';

  

 constructor(

 private httpClient: HttpClient

 ) { }

  

 getAllProducts() {

 return this.httpClient.get<Product[]>(this.apiUrl);

 }
 ```


products.components.ts
```ts
import { Product } from 'src/app/models/product.model';

  
  

import { StoreService } from '../../services/store.service';

import { ProductsService } from '../../services/products.service';

products : Product[] = [];

 showProductDetail = false;

  

 constructor(

 private storeService: StoreService,

 private productsService: ProductsService

 ) {

 this.myShoppingCart = this.storeService.getShoppingCart();

 }

  

 ngOnInit(): void {

 this.productsService.getAllProducts()

 .subscribe(data => {

 this.products = data;

 })

 }

  

 onAddtoShoppingCart(product: Product) {

  

 this.storeService.addProduct(product);

 this.total = this.storeService.getTotal();

 }

  

 toggleProductDetail() {

 this.showProductDetail = !this.showProductDetail;

 }
```