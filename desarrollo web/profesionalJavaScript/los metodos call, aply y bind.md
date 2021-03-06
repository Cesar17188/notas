# Los métodos call, apply y bind

Estas funciones nos sirven para establecer el valor de _this_, es decir cambiar el contexto que se va usar cuando la función sea llamada.

Las funciones **call, apply y bind** son parte del prototipo Function. Toda función usa este prototipo y por lo tanto tiene estas tres funciones.

-   **functionName.call()**. Ejecuta la función recibiendo como primer argumento el _this_ y los siguientes son los argumentos que recibe la función que llamó a call.
-   **functionName.apply()**. Ejecuta la función recibiendo como primer argumento el _this_ y como segundo un arreglo con los argumentos que recibe la función que llamó a apply.
-   **functionName.bind()**. Recibe como primer y único argumento el _this_. No ejecuta la función, sólo regresa otra función con el nuevo this integrado.

Es cierto que `this` no es un valor que podemos asignar directamente, pero sí existen unos métodos que son parte del prototipo de `function`, se llaman: `call`, `apply` y `bing`. Estos nos ayudarán a establecer `this` en el contexto de una llamada a una función.

‌

Crearemos un nuevo archivo en la carpeta de ejercicios para aprender más sobre esto.

‌

## Call

‌

Para empezar crearemos una función.

```
function saludar() {
        console.log(`Hola, me llamo ${this.name} ${this.apellido}`);
      }
```

‌

En este caso no tenemos la función dentro de algún objeto o clase y sin embargo estamos utilizando `this`. Con la ayuda de `Call` vamos a establecer cual va a ser el `this`. Para esto crearemos un objeto.

```
const augusto = {
          name: 'Augusto',
          apellido: 'Barco'
      }
```

‌

Al tener el objeto vamos a llamar a `saludar` pero mediante `call`. Todas las funciones tienen los tres métodos antes mencionados, son tres funciones que ya vienen empaquetadas.

```
saludar.call(augusto)
```

‌

Con esto establecemos que `this` va a ser el objeto `augusto`. También podemos pasar parámetros aparte del contexto que ya le podemos dar con el `call`. Por ejemplo:

```
function caminar(metros, direccion) {
        console.log(
          `${this.name} ${this.apellido} caminó ${metros} hacia el ${direccion}`
        );
      }

      caminar.call(augusto, 1000, "sur");
```

‌

Esto nos dará como resultado: `//Augusto Barco caminó 1000 hacia el sur`. Aparte del contexto que le pasamos le mandamos dos argumentos.

‌

## Apply

‌

Esta hace la misma funcionalidad de `call`, pero sus argumentos los pasamos de una forma ligeramente diferente.

```
caminar.apply(augusto, [800, "sureste"]);
```

‌

Acá le pasamos los parámetros extras como si fueran un arreglo. Eso nos sirve cuando le tenemos que pasar una lista larga de parámetros a nuestra función, podremos manejar mejor esto usando `apply`. También le podemos pasar una instancia de un arreglo.

```
const parametros = [800, "sureste"];
caminar.apply(augusto, parametros);
```

‌

Igual nos dará el mismo resultado.

‌

## Truco para distinguirlos

‌

Podemos usar las iniciales de cada tipo de asignador de `this`. Ejemplo:

‌

-   **Call**: **c** de **comas**, esto por que le pasamos todos los valores separados por comas.
    
-   **Apply**: **a** de **arreglo**, acá le pasamos todos los parámetros por arreglos.
    

‌

## Bind

‌

A diferencia de los dos anteriores que vimos, `bind` no va a llamar a la función automáticamente. Lo que va a hacer es construir una nueva función con el `this` integrado, cuando la llamemos va a funcionar.

```
const daniel = {
        name: "Daniel",
        apellido: "Sánchez"
      };
      saludar.bind(daniel);
```

‌

Si hacemos esto la función no se va a llamar, por esto tenemos que meterla en una constante y ejecutarla luego.

```
const saludarConDaniel = saludar.bind(daniel); 
      saludarConDaniel();
```

‌

Ahora vamos a ver cómo hacemos para pasar más parámetros a esta función, queremos usar la opción de caminar.

```
const danielCamina = caminar.bind(daniel);
  danielCamina(200, "oeste");
```

‌

Con esto ya tendremos nuestro: `//Daniel Sánchez caminó 200 hacia el oeste`.

‌

También podemos pasar un parámetro cuando llamamos con `bind` y así establecer uno ya predefinido y el otro lo pasamos cuando ejecutamos.

```
const danielCamina = caminar.bind(daniel, 200); 
  danielCamina("oeste"); 
```

‌

Nos dará el mismo resultado pero guardando ya un parámetro que es la `distancia`. A esta técnica se le llama **Function currying**.

‌

## Conclusión

‌

Tenemos varias formas de establecer el valor de `this`, con los tres métodos que vimos. Cada uno tiene su forma de hacerlo. Con `call` y `apply` establecen el `this` y llaman de una vez a la función. Con `bind` se establece el contexto pero luego hay que ejecutarla como si fuera una nueva función que hay que guardar en una constante.

‌

## Nodelist

‌

Aveces tenemos objetos que se parecen a otros. Cuando llamamos a varios elemento usando el `getElementByClassName` nos trae un `Nodelist`, es muy parecido al `Array` pero no trae todos los métodos, como por ejemplo el `foreach`. Usemos el siguiente código:

```
<u>
        <li><button class="call-to-action">Aprender</button></li>
        <li><button class="call-to-action">Aprender más</button></li>
        <li><button class="call-to-action">¡Nunca pares de aprender!</button></li>
    </u>
```

‌

Usaremos estos botones para probar el `foreach`. Vamos a darle funcionalidad. Traeremos estos botones con `getElemenetByClassName` y que cuando le demos **click** a cada uno de estos botones abra una ventana que diga _‘Nunca pares de aprender’._

```
const buttons = document.getElementsByClassName("call-to-action");
      buttons.forEach(element => {
          element.onclick = ()=> {
              alert('Nunca pares de aprender')  
          }
      });
```

‌

Nos va a decir que `buttons` no es una función. Esto pasa porque `buttons` es un `Nodelist`. Se parecen a los arreglos pero no del todo, por lo menos tienen la propiedad `lenght` que nos puede servir para hacer el trabajo que queremos. Vamos a llamar el `foreach` a través del `Array` y le asignaremos el contexto de `buttons` con `call`.

```
Array.prototype.forEach.call(buttons, element => {
        element.onclick = () => alert("Nunca pares de aprender");
      });
```

‌

De esta forma el `foreach` entenderá a `buttons` como el contexto y lo usará como el elemento que iterará cada vez que se le dé `click`.

![[Pasted image 20210921182317.png]]