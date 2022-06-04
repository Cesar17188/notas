# Lista de productos

creamos el componente products

```script
ng g c components/products
```

enviamos la lógica de los objetos tipo producto a products

products.component.ts

```ts

import { Product } from 'src/app/models/product.model';


products : Product[] = [

 {

 id: '1',

 name: 'Alambique de cobre',

 price: 950,

 image: './assets/images/alambique.png',

 },

 {

 id: '2',

 name: 'Barril de roble blanco',

 price: 1200,

 image: './assets/images/barril.png'

 },

 {

 id: '3',

 name: 'Ron en las rocas',

 price: 6,

 image: './assets/images/vaso.png'

 },

 {

 id: '4',

 name: 'Buen mojito',

 price: 8,

 image: './assets/images/mojito.png'

 },

 {

 id: '5',

 name: 'Ron con limon',

 price: 7,

 image: './assets/images/ron_limon.png'

 },

 {

 id: '6',

 name: 'Ron Estancos',

 price: 15,

 image: './assets/images/ron.png'

 },

 {

 id: '7',

 name: 'Ingredientets del Ron',

 price: 9,

 image: './assets/images/ingredientes.png'

 }

 ];
 ```

renderizamos el componente product con un ngfor para recorrer los productos

products.component.html
```html
<div class="products--grid">

 <app-product

 [product]="product"

 *ngFor="let product of products"

 ></app-product>

</div>
```

estilizamos con una grilla el div con clase "products--grid" para mejorar la visulización en responsive

```scss

.products--grid {

 display: flex;

 flex-direction: column;

}

  

//tablets

@media screen and (min-width: 40em) and (max-width: 63.9em){

 .products--grid {

 display: grid;

 grid-template-columns: repeat(4, 1fr);

 grid-gap: 15px;

 }

}

  
  

//web

@media screen and (min-width: 64em){

 .products--grid {

 display: grid;

 grid-template-columns: repeat(5, 1fr);

 grid-gap: 15px;

 }

}
```