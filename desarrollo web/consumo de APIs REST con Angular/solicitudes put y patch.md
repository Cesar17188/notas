# Solicitudes PUT y PATCH

debido a que los métodos PUT y PATCH actualizan parcialmente un item de la base de datos se podría mandar de manera opcional los parámetros dentro del módelo.

Para conseguir este efecto es buena práctica extender los parámetros de los modelos anteriores y aplicarle **Partial** que vuelve opcionales todos los datos dentro del módelo

product.model.ts
```ts
export interface UpdateProductDTO extends

Partial<CreateProductDTO>{ }
```

creamos la función de actualización en el servicio de productos incluyendo el nuevo modelo UpdateProductDTO

product.service.ts
```ts
import { Product, CreateProductDTO, UpdateProductDTO } from '../models/product.model';

 private apiUrl = 'https://young-sands-07814.herokuapp.com/api/products';

 updateProduct(id: number, dto: UpdateProductDTO) {

	 return this.http.put<Product>(`${this.apiUrl}/${id}`, dto);

 }
```

Creamos la función de actualización en el products component importando el servicio y nuevo modelo

products.component.ts
```ts
import { Product, CreateProductDTO, UpdateProductDTO } from 'src/app/models/product.model';

updateProduct () {

 const changes: UpdateProductDTO = {

 title: 'change title',

 }

 // actualiza el producto en la base de datos
 const id = this.productChosen.id;

 this.productsService.updateProduct(id, changes)

 .subscribe(data => {

// realiza el cambio dentro de nuestro array local para tener el cambio en tiempo real
 const productIndex = this.products.findIndex(item => item.id === this.productChosen.id);
 this.products[productIndex] = data;

 });

 }
```

Ingresar el botón de acción para editar un producto en nuestro slide de productos

products.componen.html
```html
<button class="editButton" (click)="updateProduct()">Editar</button>
```
estilazación del botón
```scss
.editButton {

 font-size: 1rem;

 width: 140px;

 height: 35px;

 border-width: 1px;

 color: #fff;

 border-color: rgba(48, 59, 104, 1);

 font-weight: bold;

 border-top-left-radius: 8px;

 border-top-right-radius: 8px;

 border-bottom-left-radius: 8px;

 border-bottom-right-radius: 8px;

 box-shadow: 0px 10px 14px -7px rgba(50, 53, 105, 1);

 text-shadow: 0px 1px 0px rgba(74, 144, 226, 1);

 background: linear-gradient(rgba(35, 42, 245, 1), rgba(34, 44, 124, 1));

  

 &:hover {

 background: linear-gradient(rgba(34, 44, 124, 1), rgba(35, 42, 245, 1));

 }

 }
```