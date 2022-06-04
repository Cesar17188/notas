# Componentes con Inputs
Para hacer pruebas a componentes que tienen inputs podemos hacerlo de la siguiente manera

person.component.ts
```ts
import { Person } from 'src/app/models/person.model';

@Input() person!: Person;
```


person.component.html
```html
<section class="container">
  <h3>Hola, {{person?.name}}</h3>
  <p>Mi altura es {{person?.heigth}} cm</p>
</section>
```

person.component.spect.ts
```ts
it('should the name be "Cesar"', () => {
    component.person = new Person('Cesar', 'Armendariz', 29, 120, 1.75);
    expect(component.person.name).toEqual('Cesar');
  });

  it('should have <p> with "Mi altura es {person.heigth}"</p>', () => {
    // Arrange
    component.person = new Person('Valentina', 'Armendariz', 29, 120, 1.75);
    const personDebug: DebugElement = fixture.debugElement;
    const expectedMsg = `Mi altura es ${component.person.heigth} cm`;
    const pDebug: DebugElement = personDebug.query(By.css('p'));
    const pElement: HTMLElement = pDebug.nativeElement;
    // Act
    fixture.detectChanges();
    // Assert
    expect(pElement?.textContent).toContain(expectedMsg);
  });

  it('should have <h3> with "Hola, {person.name}"</h3>', () => {
    // Arrange
    component.person = new Person('Valentina', 'Armendariz', 29, 120, 1.75);
    const expectedMsg = `Hola, ${component.person.name}`;
    const personDebug: DebugElement = fixture.debugElement;
    const h3Debug: DebugElement = personDebug.query(By.css('h3'));
    const h3: HTMLElement = h3Debug.nativeElement;
    // Act
    fixture.detectChanges();
    //Assert
    expect(h3?.textContent).toContain(expectedMsg);
  });
```