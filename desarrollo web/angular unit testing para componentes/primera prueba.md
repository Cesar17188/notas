# Primera prueba

vamos a crear una clase persona con la función de calculo de masa corporal.

primero creamos la clase persona

person.model.ts
```ts
export class Person {
  constructor(
    public name: string,
    public lastName: string,
    public age: number,
    public weigth: number,
    public heigth: number,
  ) {}

  calcIMC(): string {
    const result = Math.round(this.weigth / (Math.pow(this.heigth, 2)));
    // 0 - 18 = down
    // 19 - 24 = normal
    // 25 - 26 = overweigth
    // 27 - 29 = overweigth level 1
    // 30 - 39 = overweigth level 2
    // 40 = overweigth level 3

    switch(true) {
      case result < 0:
        return 'not found';
        break;
      case result >= 0 && result < 19:
        return 'down';
        break;
      case result >= 19 && result < 25:
        return 'normal';
        break;
      case result >= 25 && result < 27:
        return 'overweigth';
        break;
      case result >= 27 && result < 30:
        return 'overweigth level 1';
        break;
      case result >= 30 && result < 40:
        return 'overweigth level 2';
        break;
      case result >= 40:
        return 'overweigth level 3';
        break;
      default:
        return 'not found';
        break;
    }
  }
}
```

y hacemos los casos de prueba para ese modelo

person.model.spec.ts
```ts
import { Person } from './person.model';

describe('Test for Person', () => {
  let person: Person;
  beforeEach(() => {
    person = new Person('Cesar', 'Armendariz', 29, 120, 1.75);
  });

  it('attrs', () => {
    expect(person.name).toEqual('Cesar');
    expect(person.lastName).toEqual('Armendariz');
    expect(person.age).toEqual(29);
    expect(person.weigth).toEqual(120);
    expect(person.heigth).toEqual(1.75);
  });

  describe('test for calcIMC', () => {
    it('should return a string: overweigth level 2', () => {
      // Arrange
      person.weigth = 120;
      person.heigth = 1.78;
      // Act
      const rta = person.calcIMC();
      // Assert
      expect(rta).toEqual('overweigth level 2');
    });

    it('should return a string: not found', () => {
      // Arrange
      person.weigth = -10;
      person.heigth = 1.78;
      // Act
      const rta = person.calcIMC();
      // Assert
      expect(rta).toEqual('not found');
    });

    it('should return a string: down', () => {
      // Arrange
      person.weigth = 40;
      person.heigth = 1.78;
      // Act
      const rta = person.calcIMC();
      // Assert
      expect(rta).toEqual('down');
    });

    it('should return a string: normal', () => {
      // Arrange
      person.weigth = 70;
      person.heigth = 1.78;
      // Act
      const rta = person.calcIMC();
      // Assert
      expect(rta).toEqual('normal');
    });

    it('should return a string: overweigth', () => {
      // Arrange
      person.weigth = 80;
      person.heigth = 1.78;
      // Act
      const rta = person.calcIMC();
      // Assert
      expect(rta).toEqual('overweigth');
    });

    it('should return a string: overweigth level 1', () => {
      // Arrange
      person.weigth = 90;
      person.heigth = 1.78;
      // Act
      const rta = person.calcIMC();
      // Assert
      expect(rta).toEqual('overweigth level 1');
    });

    it('should return a string: overweigth level 3', () => {
      // Arrange
      person.weigth = 150;
      person.heigth = 1.78;
      // Act
      const rta = person.calcIMC();
      // Assert
      expect(rta).toEqual('overweigth level 3');
    });
  });
});
```