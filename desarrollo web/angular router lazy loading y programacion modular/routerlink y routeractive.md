# RouterLink y RouterActive

Para poder navegar de forma dinamica desde nuestros componentes y páginas angular nos provee de RouterLink y RouterActive

primero creamos el servicio de categoria

categories.service.ts
```ts
import { Injectable } from '@angular/core';

import { HttpClient, HttpParams } from '@angular/common/http';

  

import { environment } from './../../environments/environment';

import { Category } from '../models/category.model';

@Injectable({

 providedIn: 'root'

})

export class CategoriesService {

  

// concatena la url de existir en cualquier ambiente

private apiUrl = `${environment.API_URL}/api/categories`;

  

 constructor(

 private http: HttpClient

 ) { }

  

 getAll(limit?: number, offset?: number) {

 let params = new HttpParams();

 if (limit && offset){

 params = params.set('limit', limit);

 params = params.set('offset', limit);

 }

 return this.http.get<Category[]>(this.apiUrl, {params});

 }

}
```

un ejemplo podria verse en el nav component

nav.component.ts
```ts
import { CategoriesService } from '../../services/categories.service';

categories: Category[] = [];

constructor(
 private categoriesService: CategoriesService,

 ) { }


ngOnInit(): void {

 this.getAllCategories();

 }

 getAllCategories() {

 this.categoriesService.getAll()

 .subscribe(data => {

 this.categories = data;

 });

 }
```