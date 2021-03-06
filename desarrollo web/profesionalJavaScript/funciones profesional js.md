# Funciones

[[funciones js]]

En Typescript podemos ser explícitos con el tipo de los argumentos y el tipo de retorno de una función.

## TypeScript: funciones y métodos

TypeScript aporta varias características que JavaScript no dispone hasta el momento cuando tenemos que plantear funciones y métodos.

## Parámetros tipados y funciones que retornan un valor.

Podemos indicar a cada parámetro el tipo de dato que puede recibir y también el tipo de dato que retorna la función o método en caso que estemos en una clase:

```js
	function sumar(valor1:number, valor2:number): number {
	  return valor1+valor2;
	}

	console.log(sumar(10, 5));
```

La función sumar recibe dos parámetros de tipo number y retorna un valor de tipo number. Luego si llamamos a esta función enviando un valor distinto a number el compilador nos avisará del error:

```js
	console.log(sumar('juan', 'carlos'));
```

Se genera un error: `"Argument of type '"juan"' is not assignable to parameter of type 'number'`.

Inclusive editores de texto moderno como Visual Studio Code pueden antes de compilarse avisar del error.

El tipado estático favorece a identificar este tipo de errores antes de ejecutar la aplicación. Lo mismo cuando una función retorna un dato debemos indicar al final de la misma dicho tipo:

```js
	function sumar(valor1:number, valor2:number): number {}
```

La función sumar retorna un valor de tipo `number`.

Luego si la función retorna un tipo distinto a `number` se genera un error:

```js
	function sumar(valor1:number, valor2:number): number {
	  return 'Hola mundo';
	}
```

Como estamos retornando un string se genera el error: `Type '"Hola mundo"' is not assignable to type 'number'`.

## [Parámetros opcionales y predeterminados](https://www.typescriptlang.org/docs/handbook/functions.html#optional-and-default-parameters)

En TypeScript, se supone que cada parámetro es requerido por la función. Esto no significa que no se pueda dar `null`o `undefined`, sino que, cuando se llama a la función, el compilador verificará que el usuario haya proporcionado un valor para cada parámetro. El compilador también supone que estos parámetros son los únicos parámetros que se pasarán a la función. En resumen, el número de argumentos dados a una función tiene que coincidir con el número de parámetros que la función espera.

```ts
function buildName(firstName: string, lastName: string) {
    return firstName + " " + lastName;
}

let result1 = buildName("Bob");                  // error, too few parameters
let result2 = buildName("Bob", "Adams", "Sr.");  // error, too many parameters
let result3 = buildName("Bob", "Adams");         // ah, just right

```

En JavaScript, cada parámetro es opcional, y los usuarios pueden dejarlos como mejor les parezca. Cuando lo hacen, su valor es `undefined`. Podemos obtener esta funcionalidad en TypeScript agregando un `?`al final de los parámetros que queremos que sean opcionales. Por ejemplo, supongamos que queremos que el parámetro de apellido anterior sea opcional:

```ts
function buildName(firstName: string, lastName?: string) {
    if (lastName)
        return firstName + " " + lastName;
    else
        return firstName;
}

let result1 = buildName("Bob");                  // works correctly now
let result2 = buildName("Bob", "Adams", "Sr.");  // error, too many parameters
let result3 = buildName("Bob", "Adams");         // ah, just right

```

Cualquier parámetro opcional debe seguir los parámetros requeridos. Si quisiéramos hacer que el primer nombre fuera opcional, en lugar del apellido, tendríamos que cambiar el orden de los parámetros en la función, colocando el primer nombre en la lista.

En TypeScript, también podemos establecer un valor que se asignará a un parámetro si el usuario no proporciona uno, o si el usuario pasa `undefined`en su lugar. Estos se denominan parámetros inicializados por defecto. Tomemos el ejemplo anterior y establezcamos el apellido por defecto `"Smith"`.

```ts
function buildName(firstName: string, lastName = "Smith") {
    return firstName + " " + lastName;
}

let result1 = buildName("Bob");                  // works correctly now, returns "Bob Smith"
let result2 = buildName("Bob", undefined);       // still works, also returns "Bob Smith"
let result3 = buildName("Bob", "Adams", "Sr.");  // error, too many parameters
let result4 = buildName("Bob", "Adams");         // ah, just right

```

Los parámetros inicializados por defecto que vienen después de que todos los parámetros requeridos se tratan como opcionales, y al igual que los parámetros opcionales, se pueden omitir al llamar a su función respectiva. Esto significa que los parámetros opcionales y los parámetros predeterminados finales compartirán elementos comunes en sus tipos, por lo que ambos

```ts
function buildName(firstName: string, lastName?: string) {
    // ...
}

```

y

```ts
function buildName(firstName: string, lastName = "Smith") {
    // ...
}

```

compartir el mismo tipo `(firstName: string, lastName?: string) => string`. El valor predeterminado de `lastName`desaparece en el tipo, solo dejando atrás el hecho de que el parámetro es opcional.

A diferencia de los parámetros opcionales simples, los parámetros inicializados por defecto no _necesitan_ ocurrir después de los parámetros requeridos. Si un parámetro inicializado predeterminado viene antes que un parámetro requerido, los usuarios deben pasar explícitamente `undefined`para obtener el valor inicializado predeterminado. Por ejemplo, podríamos escribir nuestro último ejemplo con solo un inicializador predeterminado en `firstName`:

```ts
function buildName(firstName = "Will", lastName: string) {
    return firstName + " " + lastName;
}

let result1 = buildName("Bob");                  // error, too few parameters
let result2 = buildName("Bob", "Adams", "Sr.");  // error, too many parameters
let result3 = buildName("Bob", "Adams");         // okay and returns "Bob Adams"
let result4 = buildName(undefined, "Adams");     // okay and returns "Will Adams"
```

![[Pasted image 20211015123537.png]]