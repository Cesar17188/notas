# Proxy

El proxy sirve para interceptar la lectura de propiedades de un objeto (los _get_, y _set_) entre muchas otras funciones. Así, antes de que la llamada llegue al objeto podemos manipularla con una lógica que nosotros definamos.

El objeto **Proxy** se usa para definir un comportamiento personalizado para operaciones fundamentales (por ejemplo, para observar propiedades, cuando se asignan, enumeración, invocación de funciones, etc).

## Métodos del objeto handler[Sección](https://developer.mozilla.org/es/docs/Web/JavaScript/Referencia/Objetos_globales/Proxy#M%C3%A9todos_del_objeto_handler)

El objeto controlador es un objeto marcador de posición que contiene trampas para `Proxy`.

Todas las trampas son opcionales. Si no se ha definido una trampa, el comportamiento predeterminado es reenviar la operación al objetivo.

[`handler.get()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Proxy/handler/get "El método handler.get () es una trampa para obtener un valor de propiedad.")

Una trampa para obtener valores de propiedad.

## Sintaxis[Sección](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Proxy/handler/get#Syntax)

```
var p = new Proxy(target, {
  get: function(target, property, receiver) {
  }
});
```

Los siguientes parámetros se pasan al `get`método. `this`está vinculado al controlador.

`target`

El objeto de destino.

`property`

El nombre o [`Symbol`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Symbol%22) de la propiedad a obtener.

`receiver`

El proxy o un objeto que hereda del proxy.

El `get`método puede devolver cualquier valor.

## Ejemplo

```
const monster1 = {
  secret: 'easily scared',
  eyeCount: 4
};

const handler1 = {
  get: function(target, prop, receiver) {
    if (prop === 'secret') {
      return `${target.secret.substr(0, 4)} ... shhhh!`;
    } else {
      return Reflect.get(...arguments);
    }
  }
};

const proxy1 = new Proxy(monster1, handler1);

console.log(proxy1.eyeCount);
// expected output: 4

console.log(proxy1.secret);
// expected output: "easi ... shhhh!"
```

## Object.keys()

El método `Object.keys()` devuelve un array de las propiedades `names` de un objeto, en el mismo orden como se obtienen en un loop normal.

`Object.keys` devuelve un array cuyos elementos son strings correspondientes a las propiedades enumerables que se encuentran directamente en el object. El orden de las propiedades es el mismo que se proporciona al iterar manualmente sobre las propiedades del objeto.

## Array.prototype.find()

El método `**find()**` devuelve el **valor** del **primer elemento** del array que cumple la función de prueba proporcionada. En cualquier otro caso se devuelve [`undefined`](https://developer.mozilla.org/es/docs/Web/JavaScript/Referencia/Objetos_globales/undefined "La propiedad global undefined representa el valor primitivo undefined. Es uno de los valores primitivos de JavaScript.").

## Distancia de Levenshtein

[Ir a la navegación](https://es.wikipedia.org/wiki/Distancia_de_Levenshtein#mw-head)[Ir a la búsqueda](https://es.wikipedia.org/wiki/Distancia_de_Levenshtein#p-search)

La **distancia de Levenshtein**, **distancia de edición** o **distancia entre palabras** es el número mínimo de operaciones requeridas para transformar una [cadena de caracteres](https://es.wikipedia.org/wiki/Cadena_de_caracteres "Cadena de caracteres") en otra, se usa ampliamente en [teoría de la información](https://es.wikipedia.org/wiki/Teor%C3%ADa_de_la_informaci%C3%B3n "Teoría de la información") y [ciencias de la computación](https://es.wikipedia.org/wiki/Ciencias_de_la_computaci%C3%B3n "Ciencias de la computación"). Se entiende por operación, bien una inserción, eliminación o la sustitución de un carácter. Esta distancia recibe ese nombre en honor al científico ruso [Vladimir Levenshtein](https://es.wikipedia.org/wiki/Vladimir_Levenshtein "Vladimir Levenshtein"), quien se ocupó de esta distancia en [1965](https://es.wikipedia.org/wiki/1965 "1965"). Es útil en programas que determinan cuán similares son dos cadenas de caracteres, como es el caso de los [correctores ortográficos](https://es.wikipedia.org/wiki/Corrector_ortogr%C3%A1fico "Corrector ortográfico").

![[Pasted image 20211004201052.png]]