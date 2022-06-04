# Creando el Home
home.component.ts
```ts
import { Product } from 'src/app/models/product.model';

  

import { ProductsService } from '../../services/products.service';

@Component({

 selector: 'app-home',

 templateUrl: './home.component.html',

 styleUrls: ['./home.component.scss']

})

export class HomeComponent implements OnInit {

  

 products : Product[] = [];

 limit = 10;

 offset = 0;

  

 constructor(

 private productsService: ProductsService

 ) { }

  

 ngOnInit(): void {

 this.productsService.getAllProducts(this.limit, this.offset)

 .subscribe(data => {

 this.products = data;

 this.offset += this.limit;

 })

 }

  

 loadMore() {

 this.productsService.getAllProducts(this.limit, this.offset)

 .subscribe(data => {

 this.products = this.products.concat(data);

 this.offset += this.limit;

 });

 }

  

}
```

home.component.html
```html
<app-products [products] = "products"></app-products>
```


se eliminan de app.products.ts
ngOnInit() y loadMore() para pasar a ser inyección con Input y Output desde el componente padre home


para el loadMore se hace un output de carga de evento con un booleano que diga true o false para cargar más productos

products.component.ts
```ts
@Output() loadMore = new EventEmitter();

onLoadMore() {

 this.loadMore.emit();

 }
```

products.component.html
```html
<button (click)="onLoadMore()">Load More</button>
```

home.component.ts
```ts

limit = 10;

offset = 0;



onLoadMore() {

 this.productsService.getAllProducts(this.limit, this.offset)

 .subscribe(data => {

 this.products = this.products.concat(data);

 this.offset += this.limit;

 });

 }
```


home.component.html
```html
<app-products [products] = "products" (loadMore)="onLoadMore()"></app-products>
```