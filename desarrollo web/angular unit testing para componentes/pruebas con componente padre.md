# Pruebas con componente padre
Esto serviria para probar el flujo total del componente padre, por ejemplo ver la funcionalidad de un ngFor dentro del componente padre.


people.component.html
```html
<section class="container">
  <h3>Selected Person</h3>
  <div *ngIf="selectedPerson" class="selectedPerson">
    <ul>
      <li>Name: {{selectedPerson.name}}</li>
      <li>Age: {{selectedPerson.age}}</li>
    </ul>
  </div>
  <h3>Count ({{people.length}})</h3>
  <app-person
  *ngFor="let person of people"
  [person]="person"
  (onSelected)="choose($event)"></app-person>
</section>
```

people.component.ts
```ts
  it ('should raise selected event when clicked', () => {
    // Arrange
    const buttonDe = fixture.debugElement.query(By.css('app-person .btn-choose'));
    // Act
    buttonDe.triggerEventHandler('click', null);
    fixture.detectChanges();
    // Assert
    expect(component.selectedPerson).toEqual(component.people[0]);
  });

  it ('should render the selected person', () => {
    // Arrange
    const buttonDe = fixture.debugElement.query(By.css('app-person .btn-choose'));
    // Act
    buttonDe.triggerEventHandler('click', null);
    fixture.detectChanges();
    const liDe = fixture.debugElement.query(By.css('.selectedPerson ul > li'));
    // Assert
    expect(component.selectedPerson).toEqual(component.people[0]);
    expect(liDe.nativeElement.textContent).toContain(component.selectedPerson?.name);
  });
```