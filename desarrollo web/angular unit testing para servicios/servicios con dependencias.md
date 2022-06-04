# Servicios con dependencias
Angular tiene un concepto importante conocido como inyección de dependencias. Es decir que podemos inyectar servicios, componentes, directivas o pipes a  otros componentes, directivas, pipes, etc. 

En estos casos cuando un servicio depende de otro o un componente depende de otro se debe realizar pruebas de la siguiente manera.

primero crearemos un servicio extra
```
ng g s services/master
```

y vamos a ingrersar el siguiente código

master.service.ts
```ts
import { Injectable } from '@angular/core';

import  { ValueService } from './value.service';

@Injectable({
  providedIn: 'root'
})

export class MasterService {
  constructor(
    private valueService: ValueService
  ) { }

  getValue() {
    return this.valueService.getValue();
  }
}
```

Como se puede observar masterService tiene una inyección de dependencia de valueService.

Para poder realizar las pruebas en valueService ingresar el siguiente código en el master.service.spec.ts

master.service.spec.ts
```ts
import { MasterService } from './master.service';
import { ValueService } from './value.service';

describe('MasterService', () => {
  it('should be return "my value" from the real service', () => {
    const valueService = new ValueService();
    const masterService = new MasterService(valueService);
    expect(masterService.getValue()).toBe('my value');
  });
});
```

como masterService recibe como parametro en su contructor un servicio de valueService, para poder realizar las pruebas desde masterService es necesario crear ambas instancias y enviar en masterService a valueService como parametro.

### Importante
En las pruebas unitarias, todo lo que venga como dependencias lo vamos a ejecutar de forma fake o mock.
Quiere decir que solo se va a verificar la funcionalidad exacta de esa prueba por ejemplo

Si getValue en valueService es probada, su test sera ver si devuelve el valor asignado en la variable privada value.

Mientras que si la función getValue es provada desde masterService, su test verificara si se esta llamando correctamente la función getValue desde ValueService.

Por lo que para probar se debera hacer mocks de todo lo que venga como dependencias. Por que lo único que se debe probar es su ejecución, **no si funciona como tal**

## Mocks o servicios tipo fake

para observar lo que se hace en un mock vamos a crear un archivo dentro de services llamado 'value-fake.service.ts' y añadimos las funcionalidades de value.service

value-fake.service.ts
```ts
export class FakeValueService {

  constructor() { }

  getValue() {
    return 'fake value';
  }

  setValue (value: string) { }

getPromiseValue() {
    return Promise.resolve('fake promise value');
  }

}
```

Ahora lo importamos a nuestro master value y configuramos mediante un *as unknow as ValueService* para verificar que se ejecuta la prueba sin necesidad de observar si las funciones de value service se producen correctamente.

master.service.spec.ts
```ts
import { FakeValueService } from './value-fake.service';

it('should be return "other value" from the fake service', () => {
    const fakeValueService = new FakeValueService();
    const masterService = new MasterService(fakeValueService as unknown as ValueService);
    expect(masterService.getValue()).toBe('fake value');
  });
```

Esta es la forma menos eficiente de hacer pruebas sobretodo de mantenimiento.

Otra forma de hacerlo es con un objeto, por que los objetos en JS funcionan como clases o casi como clases por lo que puedo hacer que se pase directamente con un objeto en master.service.spec.ts.

Por lo que, cuando master service lo ejecute probara un fake que se esta enviando en forma de objeto

master.service.spec.ts
```ts
it('should be return "other value" from the fake object', () => {
    const fake = {getValue: () => 'fake from obj'};
    const masterService = new MasterService(fake as ValueService);
    expect(masterService.getValue()).toBe('fake from obj');
  });
```

Esto es especialemente util al momento de probar funcionalidades que por ejemplo se conectan a una API como google maps. 
Si al momento de hacer pruebas llamamos al API KEY de google maps se puede consumir tantas veces el servicio de manera consecutiva que
1. consumiria mucho saldo por uso de la API KEY
2. podría verse como un ataque de DNS y cancelar tus servicios.

Para evitar todo esto se enviar un fake y con eso evitamos el consumo inutil de servicios.

--- 

Existen métodos para no ejecutar un servicio de dependencia real sino uno fake, con el propósito de emular las respuestas, permitiéndonos centrarnos en el servicio a testear y no en las dependencias.

**Fake Services:** Hacer mocks/clones de los servicios dependencia (método poco mantenible)

Esto es un cascarón del servicio, retornando métodos con valores predefinidos, fakes.

```ts
it('sould return "other value" from the fake service', () => {
    const fakeValueService = new FakeValueService();
    const masterService = new MasterService(fakeValueService as unknown as ValueService);
    expect(masterService.getValue()).toBe('fake value');
  });
```

**Usar objetos como clases:**

Nos permite hacer una función dentro de un objeto en la misma prueba, emulando el método a testear.

```ts
it('sould return "fake from obj" from the fake object', () => {
    const fake = { getValue:()=>'fake from obj' }
    const masterService = new MasterService(fake as ValueService);
    expect(masterService.getValue()).toBe('fake from obj');
  });
```

Estas formas son manuales, hay maneras automatizadas de hacerlo con Spies