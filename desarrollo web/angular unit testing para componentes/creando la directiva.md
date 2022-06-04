# Creando la Directiva
Se va a hacer pruebas a las directivas 

lo primero es crear la directiva

creamos un componente para hacer funcionar como routing
```
ng g c components/others
```

y creamos la directiva
```
ng g d directives/highligth
```

insertamos el componente others en nuestro app-routing.module.ts y en nuestro app.component.html

app-routing.module.ts
```ts
import { ProductsComponent } from './components/products/products.component';
import { PicoPreviewComponent } from './components/pico-preview/pico-preview.component';
import { PeopleComponent } from './components/people/people.component';
import { OthersComponent } from './components/others/others.component';

const routes: Routes = [
  {
    path: 'products',
    component: ProductsComponent
  },
  {
    path: 'pico-preview',
    component: PicoPreviewComponent
  },
  {
    path: 'people',
    component: PeopleComponent
  },
  {
    path: 'others',
    component: OthersComponent
  }
];
```

app.component.html
```html
<header class="container">
  <h1>Angular Testing</h1>
  <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Beatae illum saepe odio suscipit id sapiente consequuntur, ipsa laboriosam eius debitis quidem nisi quos veritatis eum soluta adipisci repellat commodi. Esse.</p>
  <nav>
    <ul>
      <li><a routerLink="/">Home</a></li>
      <li><a routerLink="/people">People</a></li>
      <li><a routerLink="/products">Products</a></li>
      <li><a routerLink="/others">others</a></li>
      <li><a routerLink="/pico-preview">Pico Preview</a></li>
    </ul>
  </nav>
</header>
<router-outlet></router-outlet>
```

finalmente incorporamos FormsModule en nuestro app.module.ts
```ts
import { ReactiveFormsModule, FormsModule } from '@angular/forms';

NgModule({
  imports: [
    FormsModule
  ],
```

ahora en la directiva inicializamos los cambios al dom con js

highlighth.directive.ts
```ts
import { Directive, ElementRef, Input, OnChanges } from '@angular/core';

@Directive({
  selector: '[highligth]'
})

export class HighligthDirective implements OnChanges{
  defaultColor = 'gray';
  @Input('highligth') bgColor = '';

  constructor(
    private element: ElementRef
  ) {
    this.element.nativeElement.style.backgroundColor = this.defaultColor;
  }

  ngOnChanges(): void {
    this.element.nativeElement.style.backgroundColor = this.bgColor || this.defaultColor;
  }
}
```

ahora podemos implementarla en nuestro componente others

others.component.ts
```ts
import { Component, OnInit } from '@angular/core';

@Component({
  selector: 'app-others',
  templateUrl: './others.component.html',
  styleUrls: ['./others.component.scss']
})

export class OthersComponent implements OnInit {
  color = 'blue';
  constructor() { }

  ngOnInit(): void {
  }
}
```

others.component.html
```html
<section class="container">
  <h3>Directiva</h3>
  <h5 highligth>Hay un valor default</h5>
  <h5 highligth="yellow">Hay un valor</h5>
  <input [(ngModel)]="color" type="text" [highligth]="color">
</section>
```