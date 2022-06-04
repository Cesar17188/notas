# Directiva con ngModel

Ahora se va a probar las directiva con los Inputs, por lo que se va a simular con los inputs y las directivas en las pruebas

highligth.directive.spec.ts
```ts
import { FormsModule } from '@angular/forms';

@Component({
  template: `
  <h5 class="title" highligth>Hay un valor default</h5>
  <h5 highligth="yellow">Hay un valor</h5>
  <p  highligth="blue">parrafo</p>
  <p>otro parrafo</p>
  <input [(ngModel)]="color" [highligth]="color">`,
})
class HostComponent {
  color = 'pink';
}

  it('should the h5.title be defaultColor', () => {
    // Arrange
    const titleDe = fixture.debugElement.query(By.css('.title'));
    const dir = titleDe.injector.get(HighligthDirective);
    expect(titleDe.nativeElement.style.backgroundColor).toEqual(dir.defaultColor);
  });

  it('should bind <input> and change the bgColor', () => {
    // Arrange
    const inputDe = fixture.debugElement.query(By.css('input'));
    const inputEl: HTMLInputElement = inputDe.nativeElement;
    // Act
    // Assert
    expect(inputEl.style.backgroundColor).toEqual('pink');
    inputEl.value = 'red';
    inputEl.dispatchEvent(new Event('input'));
    fixture.detectChanges();
    expect(inputEl.style.backgroundColor).toEqual('red');
    expect(component.color).toEqual('red');
  });
```