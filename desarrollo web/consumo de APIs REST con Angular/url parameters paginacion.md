# Url Parameters / Paginación

dentro de las URL existe los endpoints como '/products' luego de esto se puede enviar ciertos apendices al backend que sirven para hacer filtros en el que se puede enviar por ejemplo un rango de precio o un precio especifico para retornar los productos con ese precio.

Tambien puede usarse para algo muy importante que es la paginación.

Dentro de las api existen dos indicadores **LIMIT** y **OFFSET** lo cual limit nos indica cuantos objetos se van a ver y offset desde donde empieza a recorrer el arreglo para mostrar. 

Se puede utilizar enviado parametros por medio de HttpParams que es importado desde HttpClient

product.service.ts
```ts
import { HttpClient, HttpParams } from '@angular/common/http';


getAllProducts(limit?: number, offset?: number) {

 let params = new HttpParams();

 if (limit && offset) {

 params = params.set('limit', limit);

 params = params.set('offset', limit);

 }

 return this.http.get<Product[]>(this.apiUrl, {params});

 }


getProductsByPage(limit: number, offset: number) {

 return this.http.get<Product[]>(`${this.apiUrl}`, {

 params: {limit, offset}

 });

 }
```

products.component.html
```html
<div class="products--grid">

 <app-product

 [product]="product"

 *ngFor="let product of products"

 (addedProduct)="onAddtoShoppingCart($event)"

 (showProduct)="onShowDetail($event)"

 ></app-product>

 <button (click)="loadMore()">Load More</button>

</div>
```