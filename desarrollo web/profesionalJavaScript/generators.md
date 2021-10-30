# Generators

Los generadores[[generadores python]] son funciones especiales, pueden pausar su ejecución y luego volver al punto donde se quedaron recordando su _scope_.

Algunas de sus características:

-   Los generadores regresan una función.
-   Empiezan suspendidos y se tiene que llamar _next_ para que ejecuten.
-   Regresan un _value_ y un _boolean done_ que define si ya terminaron.
-   _yield_ es la instrucción que regresa un valor cada vez que llamamos a _next_ y detiene la ejecución del generador.

El objecto Generador es retornado por [generator function](https://developer.mozilla.org/es/docs/Web/JavaScript/Referencia/Statements/function* "La documentación acerca de este tema no ha sido escrita todavía . ¡Por favor  considera contribuir !") y conforma tanto un protocolo iterable como un protocolo iterador.

## [Sintaxis](https://developer.mozilla.org/es/docs/Web/JavaScript/Referencia/Objetos_globales/Generador#Sintaxis)

```
function* gen() { 
  yield 1;
  yield 2;
  yield 3;
}

var g = gen(); // "Generator { }"
```

## [Métodos](https://developer.mozilla.org/es/docs/Web/JavaScript/Referencia/Objetos_globales/Generador#M%C3%A9todos)

[`Generator.prototype.next()`](https://developer.mozilla.org/es/docs/Web/JavaScript/Referencia/Objetos_globales/Generator/next "La documentación acerca de este tema no ha sido escrita todavía . ¡Por favor  considera contribuir !")

Retorna el valor ofecido por la expresión [`yield`](https://developer.mozilla.org/es/docs/Web/JavaScript/Referencia/Operators/yield "La documentación acerca de este tema no ha sido escrita todavía . ¡Por favor  considera contribuir !")

[`Generator.prototype.return()`](https://developer.mozilla.org/es/docs/Web/JavaScript/Referencia/Objetos_globales/Generator/return "La documentación acerca de este tema no ha sido escrita todavía . ¡Por favor  considera contribuir !")

Retorna el valor dado y finaliza el generador.

[`Generator.prototype.throw()`](https://developer.mozilla.org/es/docs/Web/JavaScript/Referencia/Objetos_globales/Generator/throw "La documentación acerca de este tema no ha sido escrita todavía . ¡Por favor  considera contribuir !")

Lanzá un error al generador

## [Ejemplo](https://developer.mozilla.org/es/docs/Web/JavaScript/Referencia/Objetos_globales/Generador#Ejemplo)

[Un iterador infinito](https://developer.mozilla.org/es/docs/Web/JavaScript/Referencia/Objetos_globales/Generador#Un_iterador_infinito)

```js
function* idMaker() {
	    var index = 0;
	    while(true)
	        yield index++;
	}

	var gen = idMaker(); // "Generator { }"

	console.log(gen.next().value); // 0
	console.log(gen.next().value); // 1
	console.log(gen.next().value); // 2
	// ...
```

![[Pasted image 20211004203527.png]]