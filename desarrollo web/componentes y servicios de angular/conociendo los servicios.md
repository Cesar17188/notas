# Conociendo los servicios
Los servicios es el lugar en donde se define la lógica del negocio de la aplicación, con el objetivo que se reutilizable e independiente de los componentes.

Esta forma es en la que Angular nos permite modular nuestra aplicación y apartar toda nuestra lógica de negocio que no tiene que ver con la UI sino a la lógica de negocio a travez de código, manipular datos, hacer servicios compartidos que puedan ser utilizados a travez de toda la aplicación por varios componentes.

se crea a travez de la términal

``` 
ng g s services/store
```

dentro del servicio se puede manejar la lógica y luego exportarla a los componentes

store.service.ts
```ts

import { Injectable } from '@angular/core';

import { Product } from '../models/product.model';

  

@Injectable({

 providedIn: 'root'

})

export class StoreService {

  

 private myShoppingCart: Product[] = [];

  

 constructor() { }

  

 getShoppingCart () {

 return this.myShoppingCart;

 }

 addProduct(product: Product) {

 this.myShoppingCart.push(product);

 }

  

 getTotal() {

 return this.myShoppingCart.reduce((sum, item) => sum + item.price, 0);

 }

}
```

products component

products.component.ts

```ts
import { StoreService } from '../../services/store.service';

 constructor(

 private storeService: StoreService

 ) {

 this.myShoppingCart = this.storeService.getShoppingCart();

 }
 

onAddtoShoppingCart(product: Product) {

 this.storeService.addProduct(product);

 this.total = this.storeService.getTotal();

 }
```

