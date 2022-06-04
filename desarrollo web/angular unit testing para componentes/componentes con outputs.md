# Componentes con Outputs
Se puede realizar las pruebas sobre parámetros de salida como los outputs, de la siguiente manera

primero creamos el output de salida y el evento que lo dispara

person.component.ts
```ts
import { Component, Input, OnInit, Output, EventEmitter } from '@angular/core';
import { Person } from 'src/app/models/person.model';


export class PersonComponent implements OnInit {

  @Input() person!: Person;
  @Output() onSelected = new EventEmitter<Person>();
  imc = '';

  onClick() {
    this.onSelected.emit(this.person);
  }
}
```

luego creamos el botón que dispara el evento

person.component.html
```html
<button class="btn-choose" (click)="onClick()">Choose</button>
```

creamos la prueba

person.component.spec.ts
```ts
 it('should raise selected event when do click', () => {
    // Arrange
    const expectedPerson = new Person('Juan', 'Perez', 30, 120, 1.65);
    component.person = expectedPerson;
    const buttonDe = fixture.debugElement.query(By.css('button.btn-choose'));
    let selectedPerson: Person | undefined;
    component.onSelected
    .subscribe(person => selectedPerson = person);
    // Act
    buttonDe.triggerEventHandler('click', null);
    fixture.detectChanges();
    // Assert
    expect(selectedPerson).toEqual(expectedPerson);
  })
```