# Closures

[[closure]] Son funciones que regresan una función o un objeto con funciones que mantienen las variables que fueron declaradas fuera de su scope.

Los **closures** nos sirven para tener algo parecido a variables privadas, característica que no tiene JavaScript por _default_. Es decir encapsulan variables que no pueden ser modificadas directamente por otros objetos, sólo por funciones pertenecientes al mismo.

actualmente javascript ha realizado mejoras en la implementación de la Programación Orientada a Objetos, mejorando la forma en que se realizan clases, para aplicar variables privadas se puede utilizar el caracter `#``

quedando el ejercicio indicado por el profesor de la siguiente forma:

```
      class makeCounter {
        #count;

        constructor(n) {
          this.#count = n;
        }

        get count() {
          return this.#count;
        }

        increase() {
          this.#count += 1;
        }

        decrease() {
          this.#count -= 1;
        }
      }

      let counter = new makeCounter(7);

      console.log("The Count is:", counter.count);
      counter.increase();
      console.log("The Count is:", counter.count);
      counter.decrease();
      counter.decrease();
      counter.decrease();
      counter.decrease();
      console.log("The Count is:", counter.count);

      counter.#count = 0;
```

si intentamos modificar el valor counter nos da la siguiente advertencia:

![Captura de Pantalla 2020-04-06 a la(s) 21.29.18.png](https://static.platzi.com/media/user_upload/Captura%20de%20Pantalla%202020-04-06%20a%20la%28s%29%2021.29.18-e06990f4-6094-4338-b64d-b59c3d281fda.jpg)

![[Pasted image 20210920200933.png]]