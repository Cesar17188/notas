# Tu primera prueba en Angular

Generalmente solemos hacer pruebas de debugging utilizando el console.log.
Más sin embargo se debe utilizar las pruebas en Jasmine, para lo cual seguiremos los siguiente pasos en el ejemplo

1. Creamos un archivo en la carpeta app llamada calculator.ts, el cual contendra el siguiente código

calculator.ts
```ts
export class Calculator {
  multiply (a: number, b:number) {
    return a * b;
  }

  divide (a: number, b: number)  {
    if (b === 0) {

      return null;

    } else {

      return a / b;

    }
  }
}
```

2. Importamos calculator a nuestro app.component.ts para usarlo al lanzar la aplicación, observamos si los resultados son los esperados utilizando el console.log 

app.component.ts
```ts
import { Calculator } from './calculator';

 ngOnInit(): void {
    const calculator = new Calculator();
    const rta = calculator.multiply(3,3);
    console.log(rta === 9);
    const rta2 = calculator.divide(3, 0);
    console.log(rta2 === null);
    console.log(rta2);
  }
}
```

3. Finalmente creamos el archivo de pruebas calculator.spec.ts para poder ejecutar las pruebas correctamente desde jasmine

calculator.spec.ts
```ts
import { Calculator } from './calculator';

describe('Test for Calculator', () => {
  it('#multiply should return a nine', () => {
    //Arrange
    const calculator = new Calculator();
    //Act
    const rta = calculator.multiply(3,3);
    //Assert
    expect(rta).toEqual(9);
  });
});
```

y ejecutamos el comando ng test en nuestra terminal para observar las pruebas realizadas

Según el cual tendremos dos funcionalidades multiplicar y dividir, en dividir contamos con la condición de que si se divide para 0 

`describe` - define una suite de tests. Una colección de tests. Recibe dos parámetros, un `string` con el nombre de la suite y una `function()` donde se definen los tests.

`it` - define un test en particular. Recibe como parámetro el nombre del test y una función a ejecutar por el test.

`expect` - Lo que esperar recibir ese test. Con `expect` se hace la comprobación del test.

[Tests Unitarios con Jasmine | Coding Potions](https://codingpotions.com/angular-testing)

