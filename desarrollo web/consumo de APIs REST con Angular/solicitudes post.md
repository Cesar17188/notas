# Solicitudes POST
Creación del módelo dto (data transfer object) en el módelo del producto para heredar las características del modelo de producto que se necesitan e ignorar las que no

model.product.ts
```ts
import { Category } from "./category.model";

export interface Product {

 id: number;

 title: string;

 price: number;

 description: string;

 images: string[];

 category: Category;

}

  

export interface CreateProductDTO extends

// toma el modelo del producto y omite 'id' y 'category' ademas ingresa el cetegoryId
Omit<Product, 'id' | 'category'>{

 categoryId: number;

}
```

creación del servicio post en el productService

product.service.ts
```ts
import { Product, CreateProductDTO } from '../models/product.model';

createProduct(dto: CreateProductDTO) {

 return this.http.post<Product>(this.apiUrl, dto);

 }
```

creación de la función para crear productos en el products component

products.component.ts
```ts
 createNewProduct() {

 const product: CreateProductDTO = {

 title: 'Nuevo producto',

 description: 'bla bla bla',

 images: ['https://placeimg.com/640/480/any?random=$%7BMath.random()%7D'],

 price: 1000,

 categoryId: 2

 }

 this.productsService.createProduct(product)

 .subscribe(data => {

 console.log('created: ', data);

// vamos a nuestro array de productos y lo ingresamos a nuestro array en la primera posicion
 this.products.unshift(data);

 });

 }
 ```