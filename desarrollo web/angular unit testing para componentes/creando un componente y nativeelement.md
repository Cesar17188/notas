# Creando un componente & nativeElement

Dentro de las pruebas de componentes, en el momento que creamos un nuevo componente, Angular nos da ya un archivo para realizar pruebas que contiene las siguientes funcionalidades.

person.component.ts
```ts
import { ComponentFixture, TestBed } from '@angular/core/testing';

// importación del modulo, servicio o componente del que se quiere hacer pruebas
import { PersonComponent } from './person.component';

describe('PersonComponent', () => {

  let component: PersonComponent;
  // Ambien para interactuar con el componente de prueba, por lo que se obtienen una instacia de nuestro componente
  let fixture: ComponentFixture<PersonComponent>;
// Pequeño ambiente de pruebas para nuestros componentes que se correra de manera asincrona 
  beforeEach(async () => {
    await TestBed.configureTestingModule({
      declarations: [ PersonComponent ]
    })
    .compileComponents();
  });

// Componente de pruebas que nos devolvera las pruebas del componente con todos sus elementos a probarse, por lo que cualquier componente creado tendra todos los métodos y atributos para ser probados
  beforeEach(() => {
    fixture = TestBed.createComponent(PersonComponent);
    component = fixture.componentInstance;
    fixture.detectChanges(); //life cycle
  });
  // prueba sobre si se puede crear
  it('should create', () => {
    expect(component).toBeTruthy();
  });
});
```

Las prácticas interesantes de pruebas hacia componentes es probar el render y el comportamiento del mismo render y la interfaz gráfica

```ts
it('should have <p> with "Soy un párrafo"</p>', () => {
    const personElement: HTMLElement = fixture.nativeElement;
    const p = personElement.querySelector('p');
    expect(p?.textContent).toEqual('Soy un párrafo');
  });
```