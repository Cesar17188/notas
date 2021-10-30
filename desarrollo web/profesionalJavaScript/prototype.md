# Prototype

En Javascript todo son objetos, no tenemos clases, no tenemos ese plano para crear objetos.

Todos los objetos “heredan” de un prototipo que a su vez hereda de otro prototipo y así sucesivamente creando lo que se llama la **prototype chain**.

La keyword _new_ crea un nuevo objeto que “hereda” todas las propiedades del prototype de otro objeto. No confundir prototype con **proto** que es sólo una propiedad en cada instancía que apunta al prototipo del que hereda.

Este es uno de los temas más tedioso de JavaScript, se aleja totalmente a cómo se manejan las clases y objetos en otros lenguajes de programación. Las clases son como un plano, se crean y se llaman, si se quiere crear otra clase, se hace y luego se instancia, así funcionaría en otros lenguajes de programación, pero en JavaScript todo es un objeto.

‌

## ¿Cómo logramos las clases si todo es un objeto?[](https://platzi.com/clases/1642-javascript-profesional/22164-prototype/#como-logramos-las-clases-si-todo-es-un-objeto)

‌

Esta pregunta es interesante, se supone que para crear una clase e **instanciarla** tiene que ser por un objeto, pero **JavaScript** no cuenta con clases.

‌

Para entender todo este tema lo vamos a hacer partiendo de un objeto pequeño hasta llegar a lo más tedioso de las herencias en JavaScript. Crearemos un archivo para empezar a testear en nuestra carpeta de ejercicios.

‌

## Objeto común y corriente[](https://platzi.com/clases/1642-javascript-profesional/22164-prototype/#objeto-comun-y-corriente)

‌

Vamos a crear un objeto que será un super héroe.

```
const heroe = {
        name: "Super-Man"
      };
      heroe.saludar = function() {
        console.log(`Hola a todos, soy ${this.name}`);
      };
      heroe.saludar();
```

‌

Si queremos crear otro objeto similar como un `bat-man` tenemos que repetir el proceso.

```
const bat = {
        name: "Bat-Man"
      };
      bat.saludar = function() {
        console.log(`Hola a todos, soy ${this.name}`); 
      };
      bat.saludar();  
```

‌

Esto es muy tedioso, nadie quiere estar escribiendo lo mismo a cada rato, es ineficiente.

‌

## Más eficiente[](https://platzi.com/clases/1642-javascript-profesional/22164-prototype/#mas-eficiente)

‌

Podemos crear una función que nos construya estos objetos que llamamos dos veces, así ahorrar tiempo y código.

```
function Hero(params) {
        const hero = {
          name: params
        };
        hero.saludar = function() {
          console.log(`Hola a todos, soy ${this.name}`);
        };
        return hero;
      }
      const heroe = Hero("Super-Man");
      heroe.saludar();
      const bat = Hero("Bat-man");
      bat.saludar();
```

‌

Ahora simplemente podemos ahorrarnos el estar creando una función por cada `heroe`, pero resulta que dentro de la función está otra que se llama `saludar()`, esta sí se llama por cada héroe que **instanciamos** de la función `Hero()`. Podemos crear un objeto aparte que tenga todas las funciones y que la función `Hero` haga referencia a ese nuevo objeto.

```
Const heroMethods = {
        saludar: function() {
          console.log(`Hola a todos, soy ${this.name}`);
        }
      };
      function Hero(params) {
        const hero = {
          name: params
        };
        hero.saludar = heroMethods.saludar;
        return hero;
      }
```

‌

Esto nos trae mucha eficiencia de computo. No estaremos creando a cada rato la misma función sino que haremos referencia al mismo lugar de memoria.

‌

Existe una mejor forma de hacer todo esto, por esto te presento a: `Object.create`.

‌

## Object.create[](https://platzi.com/clases/1642-javascript-profesional/22164-prototype/#object-create)

‌

Esta es una función que recibe un objeto como parámetro y devuelve uno nuevo.

```
const newObject = Object.create(heroMethods);
```

‌

Podemos usarlo para traer los métodos de `heroMethods` de forma más sencilla.

```
function Hero(params) {
        const hero = Object.create(heroMethods);
        return hero;
      }
```

‌

Y establecemos a `name` en la función `Hero` para recuperarlo, ya que no forma parte de `hero`.

```
function Hero(params) {
        const hero = Object.create(heroMethods);
        hero.name = params;
        return hero;
      }
```

‌

## Entendamos a object.create[](https://platzi.com/clases/1642-javascript-profesional/22164-prototype/#entendamos-a-object-create)

‌

Para entenderlo del todo vamos a la consola y usaremos las variables globales que tenemos definidas.

‌

En la consola si ponemos `heroMethods` nos arrojará nuestra función `saludar`.

```
    > heroMethods    
    < {saludar: ƒ}
```

‌

Ahora si creamos una constante y hacemos referencia a este objeto con `objetct.create` pasa algo interesante.

```
   > const newHero = Object.create(heroMethods)
   < undefined
   > newHero
   < {}
```

‌

Nos arroja un objeto vacío, pero si escribimos `newHero.saludar` la función sí existe.

```
   > newHero.saludar
   < ƒ () {
             console.log(`Hola a todos, soy ${this.name}`);
           }
```

‌

**¿Entonces por qué nos da un objeto vacío?** Si abrimos este objeto veremos una propiedad que se llama `__proto__`.

```
   > newHer
   < {}
       __proto__: 
           saludar: ƒ ()
```

‌

Podemos ver que cuenta con esta propiedad y en ella se encuentra nuestra función `saludar`. A esto se le llama herencia `prototipal`.

‌

## Prototype[](https://platzi.com/clases/1642-javascript-profesional/22164-prototype/#prototype-1)

‌

El mejor lugar para colocar nuestros métodos es dentro de la función `Hero`. Para esto pondremos nuestros métodos en el `proto` de `hero`. Para lograr esto lo tenemos que hacer con `prototype`.

```
Hero.prototype.saludar = function() {
        console.log(`Hola a todos, soy ${this.name}`);
      };
```

‌

Y ahora llamaremos a este método que está en el proto con Object.create.

```
function Hero(params) {
        const hero = Object.create(Hero.prototype);
        hero.name = params;
        return hero;
      }

Hero.prototype.saludar = function() {
        console.log(`Hola a todos, soy ${this.name}`);
      };
```

‌

## New[](https://platzi.com/clases/1642-javascript-profesional/22164-prototype/#new)

‌

Esta palabra es azúcar sintáctico, ya no tendremos que usar `Object.create` ni retornar la función `Hero` para que nuestro mensaje aparezca en consola. Al usar `New` automáticamente nuestra función `Hero` usa el `portotype` como `this`, ya no tendremos que llamar a `Hero.prototype` con `Object.create` para contar con la función `saludar`. Las partes que no necesitaremos las comentaré.

```
function Hero(params) {
        //const hero = Object.create(Hero.prototype);
        //hero.name = params;
        this.name = params;
        //return hero;
      }

      Hero.prototype.saludar = function() {
        console.log(`Hola a todos, soy ${this.name}`);
      };

      const heroe = new Hero("Super-Man");
      heroe.saludar();
      const bat = new Hero("Bat-man");
      bat.saludar();
```

‌

Al final podemos hacer lo mismo sin el `keyword new` pero usándolo nos facilitará muchas cosas. También existen otros `keywords` como `class` que nos ayudará mucho a ahorrar líneas de código.

https://static.platzi.com/media/user_upload/JS%20%E2%80%93%208-5c8d63da-0488-4936-b9ae-c35476e2e55e.jpg