# Evitando el callback hell

Se refiere cuando tenemos varias peticiones en donde una depende de la otra, como dependen cada una de ellas se empieza a anidar, anidar y anidar, haciendo que el código sea dificil de leer y mantener.

En las promesas se puede evitar esto con el .then o en el async await con varios await, pero para hacerlo con observadores se hace de la siguiente manera.

se puede utilizar switchmap para peticiones dependientes y zip para peticiones independientes. Se recomienda enviar la lógica en el servicio principal y utilizar subscribe en los componentes para verificar los cambios

product.service.ts
```ts
import { retry, catchError, map, switchMap } from 'rxjs/operators';
import { throwError, zip } from 'rxjs';


ReadAndUpdate(id: number) {

	 return this.getProduct(id)

	 .pipe(

		 switchMap((product) => this.updateProduct(product.id, {title: 'change'}))

		 )

	 }



fetchReadAndUpdate(id: number, dto: UpdateProductDTO) {

 return zip(

	 this.getProduct(id),

	 this.updateProduct(id, dto)

	 )

 }
```

para luego invocarlo desde el componente

products.component.ts
```ts

readAndUpdate(id: number) {

	 this.productsService.ReadAndUpdate(id)

	 .subscribe(data => {

		 console.log(data);

	 });

	 
	 this.productsService.fetchReadAndUpdate(id, {title:'nuevo'})

	 .subscribe(response => {

		 const read = response[0];

		 const update = response[1];

	 });

 }```