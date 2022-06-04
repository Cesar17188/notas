# Reactividad básica

La programación reactiva sigue el patrón de diseño Observer; cuando hay un cambio de estado en un objeto, los otros objetos son notificados y actualizados acorde.

Puedes utilizar los eventos del ciclo de vida de un componente para lo que indicas, segun sea el caso podrias utilizar un evento cuando el usuario carga componente (ngOnInit) u en donde lo prefieras incluso en un evento con una validacion personalizada.

![Eventos en Angular](https://miro.medium.com/max/2400/1*F1lr1sJbICqgii3V3l4iVw.png)

-   Conceptos extraídos de:
    -   [https://angular.io/guide/lifecycle-hooks](https://angular.io/guide/lifecycle-hooks)
    -   [https://platzi.com/clases/2486-angular-componentes/41180-ciclo-de-vida-de-componentes/](https://platzi.com/clases/2486-angular-componentes/41180-ciclo-de-vida-de-componentes/)


al crear un observable se puede obtener los datos de cambios generados en la aplicación en general. Esto se puede hacer desde los servicios como por ejemplo

StoreService
store.service.ts
```ts
import { BehaviorSubject } from 'rxjs';

private myShoppingCart: Product[] = [];
private myCart = new BehaviorSubject<Product[]>([]);
myCart$ = this.myCart.asObservable();

addProduct(product: Product) {
 this.myShoppingCart.push(product);
 this.myCart.next(this.myShoppingCart);
 }
```

myCart funciona como un observable al cual debemos subscribirnos para lo cual rxjs nos ayuda a posicionarlo como un observable.
Para que funcione se debe poner al observable con la propiedad next y como parametro el dato que queremos observar los cambios.

luego en el componente donde deseamos subscribirnos debemos hacer lo siguiente

NavComponent
nav.component.ts
```ts
import { StoreService } from '../../services/store.service';

 counter = 0;

 constructor(
 private storeService: StoreService
 ) { }

 ngOnInit(): void {
 this.storeService.myCart$.subscribe(products => {
 this.counter = products.length;
 })
 }
```

lo cual nos subscribir al observador y podremos mirar los cambios en tiempo real y pasarlos a nuestro html como stringInterpolartion

nav.component.html
```html
<span class="counter">{{ counter }}</span>
```