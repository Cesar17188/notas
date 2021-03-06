# Herencia Prototipal

Por default los objetos en JavaScript tienen cómo prototipo a **Object** que es el punto de partida de todos los objetos, es el prototipo padre. Object es la raíz de todo, por lo tanto tiene un prototipo padre _undefined_.

Cuando se llama a una función o variable que no se encuentra en el mismo objeto que la llamó, se busca en toda la prototype chain hasta encontrarla o regresar _undefined_.

La función **hasOwnProperty** sirve para verificar si una propiedad es parte del objeto o si viene heredada desde su prototype chain.

Ya vimos como funciona la herencia, cuando asignamos métodos a `hero` pudimos acceder a el a pesar de que cuando buscamos en la consola nos apareciera como un objeto vacío, sin embargo en `__proto__` estaba la referencia a los métodos. Esta es una de las mejores características que tiene JavaScript.

‌

Vamos a inspeccionar a esto hasta a llegar a `Object`. ¡Vamos al código!

‌

## Al código

‌

Vamos a tener este código base.

```
function Persona(name) {
        this.name = name
      }
      Persona.prototype.saludar = function() {
        console.log(`Hola, me llamo ${this.name}`);
      }
      const miPersona = new Persona('Augusto')
      miPersona.saludar()
```

‌

Si llamamos a con el `console.log` `Persona.name` nos dará la propiedad `name` de la instancia. Si llamamos `Persona.saludar` nos dará la propiedad de la clase. Ahora, si llamamos a `Persona.toString` nos sale que es una función que hemos heredado, pero ¿de donde sale esta función?

‌

## Usemos hasOwnProperty

‌

Esto lo vamos a usar para saber si alguna propiedad pertenece a la clase. De esta forma lo sabremos:

```
> miPersona.hasOwnProperty('name')
< true
```

```
> miPersona.hasOwnProperty('saludar')
< false
```

Vemos que `name` sí forma parte de `miPersona` pero su método `saludar` no. Vamos a ver cómo es que entonces accedemos a `saludar`.

```
> miPersona
< Persona {name: "Augusto"}
    name: "Augusto"
    __proto__:
        saludar: ƒ ()
        constructor: ƒ Persona(name)
        __proto__:
            constructor: ƒ Object()
            hasOwnProperty: ƒ hasOwnProperty()
            isPrototypeOf: ƒ isPrototypeOf()
            propertyIsEnumerable: ƒ propertyIsEnumerable()
            toLocaleString: ƒ toLocaleString()
            toString: ƒ toString()
            valueOf: ƒ valueOf()
            __defineGetter__: ƒ __defineGetter__()
            __defineSetter__: ƒ __defineSetter__()
            __lookupGetter__: ƒ __lookupGetter__()
            __lookupSetter__: ƒ __lookupSetter__()
            get __proto__: ƒ __proto__()
            set __proto__: ƒ __proto__()     
```

‌

Entonces vemos que usando esto en nuestra consola nos aparecerá que en el `__proto__` es donde está el método saludar, y en el `__proto__` del `__proto__` está la función `toString()`.

‌

Podemos acceder al proto de la siguiente forma: `miPersona.__proto__`, pero esto puede variar dependiendo del navegador, no en todos aparece de esa forma, solo es una representación de la herencia. La forma correcta de acceder al proto es de la siguiente forma:

```
> Object.getPrototypeOf(miPersona)
< {saludar: ƒ, constructor: ƒ}
```

‌

Podemos comprobar que es el mismo objeto que `prototype` de la siguiente forma:

```
> Object.getPrototypeOf(miPersona) === Persona.prototype 
< true
```

‌

Hace referencia al mismo lugar de memoria. Ese objeto es idéntico al que está en `Persona.prototype`. Esto significa que no es una copia. Esto quiere decir que si le agregamos un método a `Persona` inmediatamente está disponible en `miPersona`, esto por que el lenguaje lo encadena y representa la misma cosa.

‌

El lenguaje busca el método en el objeto, sino existe se va al **proto** y si no está en el **proto** se va al **proto** del **proto**, allí acaba. El ultimo **proto** es `Object`, es el punto de partida de todos los objetos de JavaScript. El **proto** de **Object** no existe, es aquí cuando la búsqueda se detiene, si ejecutamos una función que no existe en el **proto** nos saldrá un error. ¿Vale la pena entenderlo? Pos su puesto, nos ofrece un panorama completo de las herencias comprender esto.

![[Pasted image 20210925194150.png]]