# *ngFor para arrays

**Interfaces de typescript**  
_Una interfaz es un modelo que nos indica los atributos de un objeto._

Crear el archivo product.model.ts
```ts
export interface Product {

 name: string;

 price: number;

 image: string;

 category?: string;

}
```

app.component.html
```html
<h1>*ngFor Objs</h1>

<div>

 <div *ngFor="let product of products">

 <img width="250px" [src]="product.image" alt="image">

 <h2>{{product.price | currency}}</h2>

 <p>{{ product.name }}</p>

 </div>

</div>
```


app.component.ts
```ts
import { Product } from './product.model';

products: Product[] = [

 {

 name: 'El mejor alambique de cobre',

 price: 950,

 image: './assets/images/alambique.png',

 category: 'all'

 },

 {

 name: 'Gran barril de roble blanco',

 price: 1200,

 image: './assets/images/barril.png'

 },

 {

 name: 'Ron en las rocas',

 price: 6,

 image: './assets/images/en_rocas.png'

 },

 {

 name: 'Buen mojito',

 price: 8,

 image: './assets/images/mojito.png'

 },

 {

 name: 'Ron en seco',

 price: 7,

 image: './assets/images/ron_seco.png'

 },

 {

 name: 'Ron Estancos',

 price: 15,

 image: './assets/images/ron.png'

 }

 ]
```