# Angular TestBed

Angular tiene un herramienta que nos permite hacer pruebas en su propio entorno. 

esto se refeire al testBed que nos permite crear una instancia del serivicio o componente que se va a probar y a partir de ahi todo se mantiene de la misma manera.

tomando el ejemplo a valueService

value.service.spec.ts
```ts
import { TestBed } from '@angular/core/testing';


describe('ValueService', () => {
  let service: ValueService;

  beforeEach(() => {
    TestBed.configureTestingModule({
      providers: [ ValueService ]
    });
    service = TestBed.inject(Value);
  });
```