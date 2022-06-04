# Componente para producto

Crear un nuevo componente de nombre product en la carpeta de components

```script
ng g c components/product
```

Crear una interfaz y exportarla

```ts
export interface Product {

 id?: string;

 name?: string;

 price?: number;

 image?: string;

}
```

app.component.ts

```ts
import { Product } from './models/product.model';


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

app.component.html
```html
<app-product [product]="product" *ngFor="let product of products"></app-product>
```

PRODUCT 

product.component.ts
```ts

import { Product } from '../../models/product.model';


 @Input() product: Product = {

 id: '',

 price: 0,

 image: '',

 name: ''

 };
```

```html
<img width="200px" [src]="product.image" alt="">

<h2>{{product.price | currency}}</h2>

<p>{{product.name}}</p>
```