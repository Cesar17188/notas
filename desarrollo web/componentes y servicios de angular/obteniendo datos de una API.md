# Obteniendo datos de una API
en pasos:
En el servicio:  
1- crear el servicio desde la terminal  
2- importar el modulo HttpCliente en el servcio e inyectar e servicio en el constructor.  
3 en el servicio se crea el metodo para hace la petición de la API:  
return this.http.get<Product[]>(‘[https://fakestoreapi.com/products](https://fakestoreapi.com/products)’);

En el componente:  
1- importar el servicio  
2- inyectar el servicio en el constructor: private productsService: ProductsService  
3- crear el metodo en el ngOnInit  
this.productsService.getAllProducts()  
.subscribe(data => {  
this.products = data;

Por ultimo ya estaba creado un array tipado y se debe ajustar los campos con los campos de la API.

app.module.ts
```ts
import { HttpClientModule } from '@angular/common/http';


imports: [

 BrowserModule,

 AppRoutingModule,

 FormsModule,

 HttpClientModule

 ],
```

productService
creación
```ts
ng g s services/products
```

código
```ts
import { Injectable } from '@angular/core';

import { HttpClient } from '@angular/common/http';

import { Product } from '../models/product.model';

@Injectable({

 providedIn: 'root'

})

export class ProductsService {

  

 constructor(

 private httpClient: HttpClient

 ) { }

  

 getAllProducts() {

 return this.httpClient.get<Product[]>('https://fakestoreapi.com/products');

 }

}
```

Modelos
rating.model.ts
```ts
export interface Rating {

 rate: number;

 count: number;

}
```

product.model.ts
```ts
import { Rating } from "./rating.model";

  

export interface Product {

 id: string;

 title: string;

 price: number;

 description: string;

 category: string;

 image: string;

 rating: Rating;

}
```



Products component
products.component.ts
```ts
import { ProductsService } from '../../services/products.service';

products : Product[] = [];

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

```


ProductComponent
product.component.ts

```ts
@Input() product: Product = {

 id: '',

 price: 0,

 image: '',

 title: '',

 description: '',

 category: '',

 rating: {

 rate: 0,

 count: 0

 }

 };
```

