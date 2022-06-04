# Solicitudes DELETE

creación de la función eliminación en el product service
product.service.ts
```ts
deleteProduct(id: number) {

 return this.http.delete<boolean>(`${this.apiUrl}/${id}`);

 }
```

creación del método de eliminación en el products component ts

products.component.ts
```ts
deleteProduct() {

 const id = this.productChosen.id;

 this.productsService.deleteProduct(id)

 .subscribe(() => {

 const productIndex = this.products.findIndex(item => item.id === this.productChosen.id);

 this.products.splice(productIndex, 1);

 this.showProductDetail = false;

 alert('Producto eliminado');

 });

 }
```

creación del botón de eliminación en el products component html

products.component.html
```html
<button class="deleteButton" (click)="deleteProduct()">delete</button>
```

estilización del botón de eliminación

```scss
.deleteButton {

 font-size: 1rem;

 width: 140px;

 height: 35px;

 border-width: 1px;

 color: #fff;

 border-color: rgba(248, 231, 28, 1);

 font-weight: bold;

 border-top-left-radius: 8px;

 border-top-right-radius: 8px;

 border-bottom-left-radius: 8px;

 border-bottom-right-radius: 8px;

 box-shadow: 0px 10px 14px -7px rgba(138, 134, 88, 1);

 text-shadow: 0px 1px 0px rgba(71, 70, 51, 1);

 background: linear-gradient(rgba(248, 231, 28, 1), rgba(125, 119, 56, 1));

  

 &:hover {

 background: linear-gradient(rgba(125, 119, 56, 1), rgba(248, 231, 28, 1));

 }

 }
```