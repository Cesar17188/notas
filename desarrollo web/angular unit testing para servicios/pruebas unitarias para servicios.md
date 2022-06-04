# Pruebas unitarias para servicios

primero creamos nuestro servicio

```
ng g s services/value
```

posteriormente ingresamos parametros y funcionalidades al servicio

value.service.ts
```ts
import { Injectable } from '@angular/core';
import { of } from 'rxjs';

@Injectable({
  providedIn: 'root'
})

export class ValueService {

	private value = 'my value';

  constructor() { }

  getValue() {
    return this.value;
  }

  setValue (value: string) {
    this.value = value;
  }

  getPromiseValue() {
    return Promise.resolve('value');
  }

  getObservableValue() {
    return of('observable value');
  }
}
```

configuramos nuestro set de pruebas para verificar funcionalidad el servicio con **FOCUS** en el.

value.service.spec.ts
```ts
import { ValueService } from './value.service';

fdescribe('ValueService', () => {
  let service: ValueService;
  
  beforeEach(() => {
    service = new ValueService();
  });

  it('should be create', () => {
    expect(service).toBeTruthy();
  });

  describe('Test for getValue', () => {
    // AAA
    it('Should return "my value"', () => {
      expect(service.getValue()).toBe('my value');
    });
  });

  describe('Test for setValue', () => {
    // AAA
    it('Should change the value', () => {
      expect(service.getValue()).toBe('my value');
      service.setValue('change');
      expect(service.getValue()).toBe('change');
    });
  });

  describe('Test for getPromiseValue', () => {
    // AAA
    it('Should return "promise value" from promise', (doneFn) => {
      service.getPromiseValue()
      .then((value) => {
        // assert
        expect(value).toBe('promise value');
        doneFn();
      });
    });

    it('Should return "promise value" from promise using async', async() => {
     const rta = await service.getPromiseValue();
     expect(rta).toBe('promise value');
    });
  });
});
```

finalmente corremos el comando 
```
ng test
```
para verificar fallas dentro del servicio