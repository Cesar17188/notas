# Creando pipe

Crearemos un pipe y haremos pruebas del mismo

primero creamos el pipe

```
ng g p pipes/reverse
```

los pipes son los unicos que se pueden a poder probar de forma directa, sin necesidad de crear componentes o servicios embebidos. Sin embargo se puede probar tambien embebiendo componentes

las pruebas se las puede realizar de forma directa

reverse.pipe.ts
```ts
import { Pipe, PipeTransform } from '@angular/core';

@Pipe({
  name: 'reverse'
})
export class ReversePipe implements PipeTransform {

transform(value: string): string {
    return value.split('').reverse().join('');
  }
}
```

reverse.pipe.spec.ts
```ts
import { ReversePipe } from './reverse.pipe';

describe('ReversePipe', () => {
  it('create an instance', () => {
    const pipe = new ReversePipe();
    expect(pipe).toBeTruthy();
  });

  it('should transform "roma" to "amor"', () => {
    const pipe = new ReversePipe();
    const rta = pipe.transform('roma');
    expect(rta).toEqual('amor');
  });

  it('should transform "123" to "321"', () => {
    const pipe = new ReversePipe();
    const rta = pipe.transform('123');
    expect(rta).toEqual('321');
  });
});
```