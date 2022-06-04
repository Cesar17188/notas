# Evitando doble subscribe

Cuando se obtiene el parametro de una url lo más común es que luego del subcribe se haga una petición que hara otro subscribe para obtener la data. Sin embargo esto se debe evitar ya que provocariamos un callback hell.

Para evitar estas malas prácticas debemos utilizar cosas como un switchmap

category.component.ts
```ts
import { switchMap } from 'rxjs';

ngOnInit(): void {

 this.route.paramMap

 .pipe(

 switchMap( params => {

 // mucha atención con el nombre del parametro en get debe ser el mismo que en app-routing.module.ts

 this.categoryId = params.get('id');

 if ( this.categoryId ) {

 return this.productsService.getByCategory(this.categoryId, this.limit, this.offset)

 }

 return [];

 }))

 .subscribe(data => {

 this.products = data;

 });

 }
```