# Simulando el clic
Realizar pruebas en el render mientras corre, como por ejemplo si se da un click de la siguiente manera.

Primero crearemos un componente que envie al Input del componente person la información necesaria

```
ng g c components/people
```

enviaremos la información desde people

people.component.ts
```ts
import { Person } from 'src/app/models/person.model';

person: Person = new Person('Name', 'LastName', 30, 80, 1.69);
```

people.component.html
```html
<section class="container">
  <app-person [person]="person"></app-person>
</section>
```

hay que cambiar las rutas de acceso desde app-routing.module.ts

app-routing.module.ts
```ts
import { ProductsComponent } from './components/products/products.component';
import { PicoPreviewComponent } from './components/pico-preview/pico-preview.component';
import { PeopleComponent } from './components/people/people.component';

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
  }
];
```

Ademas el ingreso desde app.component.html

app.component.html
```html
<ul>
      <li><a routerLink="/">Home</a></li>
      <li><a routerLink="/people">People</a></li>
      <li><a routerLink="/products">Products</a></li>
      <li><a routerLink="/pico-preview">Pico Preview</a></li>
    </ul>
```

ahora con la información en person podemos realizar cambios como el ingreso de un botón y realizar pruebas con el

person.componen.ts
```ts
@Input() person!: Person;
  imc = '';
  
  constructor() { }
  ngOnInit(): void {
  }

  calcIMC() {
    this.imc = this.person.calcIMC();
  }
```

Y realizar las nuevas pruebas en person.component.spec.ts
```ts
it('should display a text with IMC when call calcIMC', () => {
    // Arrange
    const expectedMsg = 'overweigth level 3';
    component.person = new Person('Juan', 'Perez', 30, 120, 1.65); // overweight level 3
    const button = fixture.debugElement.query(By.css('button.btn-imc')).nativeElement;
    // Act
    component.calcIMC();
    fixture.detectChanges();
    // Assert
    expect(button.textContent).toContain(expectedMsg);
  });

  it('should display a text with IMC when do click', () => {
    // Arrange
    const expectedMsg = 'overweigth level 3';
    component.person = new Person('Juan', 'Perez', 30, 120, 1.65); // overweight level 3
    const buttonDe = fixture.debugElement.query(By.css('button.btn-imc'));
    const buttonEl = buttonDe.nativeElement;
    // Act
    buttonDe.triggerEventHandler('click', null);
    fixture.detectChanges();
    // Assert
    expect(buttonEl.textContent).toContain(expectedMsg);
  });
```