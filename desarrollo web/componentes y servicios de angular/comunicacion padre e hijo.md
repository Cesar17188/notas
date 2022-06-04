# Comunicación padre e hijo
comunicaremos el componente padre **products** con el componente hijo **product**

primero creamos un botón que lanzara el evento en el hijo para enviar un producto al padre

product.component.html

```html
<button (click)="onAddToCart()">Add cart</button>
```

importamos Output y eventEmiter para enviar la salida con un evento y generamos el evento con el Output. Luego Creamos la función para el botón Add Cart

product.component.ts

```ts
import { Component, OnInit, Input, Output, EventEmitter } from '@angular/core';

@Output() addedProduct = new EventEmitter<Product>();

onAddToCart() {

 this.addedProduct.emit(this.product);

 }
```

En el componente html del padre **products** creamos un eventBinding para recibir el producto con una función (onAddtoShoppingCart) para manejar ese producto enviado desde el hijo. 
Ademas de parrafos que nos mostraran posteriormente el número de productos ingresados al carrito de compras y el total a pagar

```html
<p>

 La cantidad {{ myShoppingCart.length }}

</p>

<p>

 total: {{total | currency}}

</p>
 <app-product

 [product]="product"

 *ngFor="let product of products"

 (addedProduct)="onAddtoShoppingCart($event)"

 ></app-product>
```

en el ts de products creamos un array de productos vacio que recibira los productos enviados desde el hijo **product**, ademas una variable total para sumar el costo total de los productos seleccionados.

Se crea tambien una función para añadir al array de productos los productos llegados desde el hijo y para sumar el total a pagar

```ts
myShoppingCart: Product[] = [];

 total: number = 0;
 
onAddtoShoppingCart(product: Product) {

 this.myShoppingCart.push(product);

 this.total = this.myShoppingCart.reduce((sum, item) => sum + item.price, 0);

 }
```