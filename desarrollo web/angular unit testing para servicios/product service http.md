# Product Service Http
El product component se conectara a un servicio que hara llamadas a una API real de la siguiente manera

primero utilizaremos modelos y servicios de otro proyecto de la escuela de angular [angular-router](https://github.com/platzi/Angular-router/tree/production) en la rama de producción donde buscaremos dentro de la carpeta src/app/models todos los modelos y los copiaremos al proyecto de testing con la misma ruta

Posteriormente haremos lo mismo con el servicio de products que estara en la ruta src/app/services/products.service.ts
con los siguientes cambios

products.service.ts
```ts
import { Injectable } from '@angular/core';
import { HttpClient, HttpParams, HttpErrorResponse, HttpStatusCode } from '@angular/common/http';
import { retry, catchError, map } from 'rxjs/operators';
import { throwError, zip } from 'rxjs';

import { Product, CreateProductDTO, UpdateProductDTO } from './../models/product.model';
import { environment } from './../../environments/environment';


@Injectable({
  providedIn: 'root'
})

export class ProductsService {

  private apiUrl = `${environment.API_URL}/api/v1`;

  constructor(
    private http: HttpClient
  ) { }

  getByCategory(categoryId: string, limit?: number, offset?: number){
    let params = new HttpParams();
    if (limit && offset != null) {
      params = params.set('limit', limit);
      params = params.set('offset', offset);
    }
    return this.http.get<Product[]>(`${this.apiUrl}/categories/${categoryId}/products`, { params })
  }

  getAllSimple() {
    return this.http.get<Product[]>(`${this.apiUrl}/products`);
  }

  getAll(limit?: number, offset?: number) {
    let params = new HttpParams();
    if (limit && offset != null) {
      params = params.set('limit', limit);
      params = params.set('offset', offset);
    }
    return this.http.get<Product[]>(`${this.apiUrl}/products`, { params })
    .pipe(
      retry(3),
      map(products => products.map(item => {
        return {
          ...item,
          taxes: .19 * item.price
        }
      }))
    );
  }

  fetchReadAndUpdate(id: string, dto: UpdateProductDTO) {
    return zip(
      this.getOne(id),
      this.update(id, dto)
    );
  }

  getOne(id: string) {
    return this.http.get<Product>(`${this.apiUrl}/products/${id}`)
    .pipe(
      catchError((error: HttpErrorResponse) => {
        if (error.status === HttpStatusCode.Conflict) {
          return throwError('Algo esta fallando en el server');
        }
        if (error.status === HttpStatusCode.NotFound) {
          return throwError('El producto no existe');
        }
        if (error.status === HttpStatusCode.Unauthorized) {
          return throwError('No estas permitido');
        }
        return throwError('Ups algo salio mal');
      })
    )
  }

  create(dto: CreateProductDTO) {
    return this.http.post<Product>(`${this.apiUrl}/products`, dto);
  }

  update(id: string, dto: UpdateProductDTO) {
    return this.http.put<Product>(`${this.apiUrl}/products/${id}`, dto);
  }
  delete(id: string) {
    return this.http.delete<boolean>(`${this.apiUrl}/products/${id}`);
  }
}
```

posteriormente haremos cambios a nuestros environments del proyecto para conectar con la API

environments.prod.ts
```ts
export const environment = {
  production: true,
  API_URL: 'https://api.escuelajs.co'
};
```

environments.ts
```ts
export const environment = {
  production: false,
  API_URL: 'https://api.escuelajs.co'
};
```

posteriormente haremos una inyección de dependencia en nuestro product component

product.component.ts
```ts
import { Component, OnInit } from '@angular/core';

import { Product } from './../../models/product.model';

import { ProductsService } from './../../services/product.service';


export class ProductsComponent implements OnInit {

  products: Product[] = [];

  constructor(
    private productsService: ProductsService
  ) { }

  ngOnInit(): void {
    this.getAllProducts();
  }

  getAllProducts() {
    this.productsService.getAllSimple()
    .subscribe(products => {
      this.products = products;
    });
  }
}
```

finalmente estilizaremos en product component html y scss

product.component.html
```html
<section class="container">
  <h1>Products Component</h1>
  <div class="my-grid">
    <figure *ngFor="let product of products">
      <img [src]="product.images[0]" alt="">
      <figcaption>
        {{product.title}} - {{product.price}}
      </figcaption>
    </figure>
  </div>
</section>
```

product.component.scss
```scss
.my-grid {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  grid-template-rows: auto;
  grid-gap: 15px
}
```