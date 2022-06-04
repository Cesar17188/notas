# Proyecto: creando product component
Normalmente utilizamos nuestras dependencias para conectar nuestros servicios y los servicios conectar con nuestros components.

primero creamos el componente product
```
ng g c components/product
```

luego hacemos que obtenga el producto a renderizar con un Input


product.component.ts
```ts
import { Component, Input, OnInit } from '@angular/core';
import { Product } from 'src/app/models/product.model';

@Component({
  selector: 'app-product',
  templateUrl: './product.component.html',
  styleUrls: ['./product.component.scss']
})

export class ProductComponent implements OnInit {

  @Input() product!: Product;

  constructor() { }

  ngOnInit(): void {
  }

}
```

hacemos que se renderize en el html

product.component.html
```html
<div>
  <figure>
    <img [src]="product.images[0]" alt="">
    <figcaption>
      {{product.title}} - {{product.price}}
    </figcaption>
  </figure>
  <p>{{ product.description }}</p>
</div>
```

finalmente lo integramos en products component

products.component.html
```html
<section class="container">
  <h1>Products Component</h1>
  <div class="my-grid">
    <app-product
      *ngFor="let product of products"
      [product]="product">
  </app-product>
  </div>
</section>
```