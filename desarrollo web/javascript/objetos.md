# Objects

Objetos: JS es un lenguaje que está diseñado en un paradigma de objetos.

Ejemplo de Objeto:

```js
var miAuto = {
marca: "Toyota",
modelo: "Corolla",
año: 2020
}
```

Acceder a una propiedad del objeto:

```js
miAuto.marca 
// "Toyota"
```

Se pueden agregar propiedades que van a ser una función, se les llama métodos de objetos.

```js
var miAuto = {
marca: "Toyota",
modelo: "Corolla",
año: 2020, 
detallesDelAuto: function () {
	console.log(`Auto ${this.modelo} ${this.año}`);
}

// miAuto.detallesDelAuto();
//Auto Corolla 2020
```

¿Quién es this?  
Es una variable que hace referencia al objeto. En este caso: this = miAuto.

# nuevo operador

El **`new`operador** permite a los desarrolladores crear una instancia de un tipo de objeto definido por el usuario o de uno de los tipos de objeto integrados que tiene una función de constructor.

```js
function Car(make, model, year) {
  this.make = make;
  this.model = model;
  this.year = year;
}

const car1 = new Car('Eagle', 'Talon TSi', 1993);

console.log(car1.make);
// expected output: "Eagle"
```

## [Sintaxis]

```
new constructor[([arguments])]
```

### [Parámetros]

`constructor`

Una clase o función que especifica el tipo de instancia del objeto.

`arguments`

Una lista de valores con los `constructor`que se llamará.

## [Descripción]

La **`new`**palabra clave hace las siguientes cosas:

1.  Crea un objeto JavaScript simple y en blanco.
2.  Agrega una propiedad al nuevo objeto ( `__proto__`) que se vincula al objeto prototipo de la función constructora
    
    **Nota: Las** propiedades / objetos agregados al prototipo de la función de construcción son, por lo tanto, accesibles para todas las instancias creadas a partir de la función de constructor (usando `new`).
    
3.  Vincula la instancia de objeto recién creada como `this`contexto (es decir, todas las referencias a `this`en la función constructora ahora se refieren al objeto creado en el primer paso).
4.  Devuelve `this`si la función no devuelve un objeto.

La creación de un objeto definido por el usuario requiere dos pasos:

1.  Defina el tipo de objeto escribiendo una función que especifique su nombre y propiedades. Por ejemplo, una función de constructor para crear un objeto `Foo`podría verse así:
    
    ```js
    function Foo(bar1, bar2) {
          this.bar1 = bar1;
          this.bar2 = bar2;
        }
    ```
    
2.  Cree una instancia del objeto con `new`.
    
    ```js
    var myFoo = new Foo('Bar 1', 2021);
    ```