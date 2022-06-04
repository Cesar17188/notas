# Programación funcional: qué es

## ¿Qué es la programación funcional?

<h4>Ideas/conceptos claves</h4>

**Paradigma de programación**.- Es una forma distinta de ver el código cuando estamos creando aplicaciones. Creando un código mas conciso, legible y mas fácil de testear

<h4>Apuntes</h4>

-   Es un paradigma de programación
    -   Existen diferentes como ser la programación orientada a objetos o la procedural

<h3>Programación Funcional vs P.O.O.</h3>

**P.O.O**

-   Se crea una clase ⇒ primera letra en mayuscula
    -   Dentro el constructor que inicializa las propiedades iniciales de nuestro objeto
    -   Se maneja generalmente getters y setters dentro de ellas
-   Luego creamos variables usando la clase
-   Para modificar estos objetos se usan los getters y setters mencionados anteriormente

**Funcional**

-   No se necesita ninguna clase solo se declara el objeto
-   Si deseamos modificar estos objetos creamos funciones que manipulen las propiedades de los objetos

```jsx
// POO
class Person {
	constructor(name, age) {
	  this.name = name
    this.age = age
  }
  getOld() {
	  this.age += 1
  }
}

let person = new Person('Fer', 18)
person.getOld() // 19

// Funcional
const fer = {
	name: 'Fernando',
  age: 18
}

const getOld = person => Object.assign(
  {},
	person,
  { age: person.age + 1}
)

getOld(fer) // 19
```

-   Programación funcional Es de manera declarativa ⇒ Enfocarte en que hay que hacer en vez de como hacerlo

<h3>Imperativo vs Declarativo</h3>

**Imperativo**

-   Cada parte es lo que debemos hacer, en este caso en el ciclo for

```jsx
let array = [1,2,3]
let array2 = []

for (let i = 0; i< array.length; i++) {
  array2.push(array[i]*2) // [2,4,6]
}
```

**Declarativo**

-   El mismo arreglo usamos el método map pero en este caso el map es declarativo por que no estamos siendo específicos que hacer en cada iteración como en el ciclo for

```jsx
let array = [1,2,3]
let array2 = array.map(item => item*2) // [2,4,6]
```

**RESUMEN:** La programación funcional permite escribir código de manera concisa, legible y fácil de testear.


Notas de la clase:

-   🌄 La programación funcional es una nueva forma de pensar y entender nuestro código.
-   👨‍👩‍👧‍👦 El objetivo es crear código más conciso, legible y fácil de probar.
-   🔀 Existen otros paradigmas como la Programación Orientada a Objetos (POO) y la Programación por Procedimientos.
-   🤓 Buscamos resolver el _“qué hay que hacer”_ en vez del _“cómo lo debemos hacer”_ (código declarativo).


https://medium.com/swlh/introduction-to-protocol-oriented-programming-1ff3862f9a3c


**POO 🆚 Programación Funcional**:

```js
// POO
class Person {
        constructor(name, age) {
                this.name = name
                this.age = age
        }
        getOld() {
                this.age += 1
        }
}

let person = new Person('JuanDC', 15)
person.getOld() // 16

// Functional
const juandc = {
        name: 'JuanDC',
        age: 15
}

const getOld = person => Object.assign(
    {},
    person,
    { age: person.age + 1}
)
getOld(juandc) // 16
```