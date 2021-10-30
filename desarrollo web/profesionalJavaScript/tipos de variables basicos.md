# Tipos básicos

-   **boolean**. Valor verdadero o falso.
-   **number**. Números.
-   **string**. Cadenas de texto.
-   **string[]**. Arreglo del tipo cadena de texto.
-   **Array**. Arreglo multi-tipo, acepta cadenas de texto o números.
-   **enum**. Es un tipo especial llamado enumeración.
-   **any**. Cualquier tipo.
-   **object**. Del tipo objeto.

## Tipos básicos

## [Boolean](https://www.typescriptlang.org/docs/handbook/basic-types.html#boolean)

El tipo de datos más básico es el valor verdadero / falso simple, que JavaScript y TypeScript llaman un `boolean`valor.

```ts
let isDone: boolean = false;
```

## [Numero](https://www.typescriptlang.org/docs/handbook/basic-types.html#number)

Como en JavaScript, todos los números en TypeScript son valores de coma flotante. Estos números de coma flotante obtienen el tipo `number`. Además de los literales hexadecimales y decimales, TypeScript también admite literales binarios y octales introducidos en ECMAScript 2015.

```ts
let decimal: number = 6;
let hex: number = 0xf00d;
let binary: number = 0b1010;
let octal: number = 0o744;
```

## [String](https://www.typescriptlang.org/docs/handbook/basic-types.html#string)

Otra parte fundamental de la creación de programas en JavaScript para páginas web y servidores es trabajar con datos textuales. Como en otros idiomas, usamos el tipo `string`para referirnos a estos tipos de datos textuales. Al igual que JavaScript, TypeScript también utiliza comillas dobles ( `"`) o comillas simples ( `'`) para rodear los datos de cadena.

```ts
let color: string = "blue";
color = 'red';

```

También puede usar _cadenas de plantillas_ , que pueden abarcar varias líneas y tener expresiones incrustadas. Estas cadenas están rodeadas por el carácter backtick / backquote ( `` ` ``), y las expresiones incrustadas son de la forma `${ expr }`.

```ts
let fullName: string = `Bob Bobbington`;
let age: number = 37;
let sentence: string = `Hello, my name is ${ fullName }.

I'll be ${ age + 1 } years old next month.`;

```

Esto es equivalente a declarar `sentence`así:

```ts
let sentence: string = "Hello, my name is " + fullName + ".\n\n" +
    "I'll be " + (age + 1) + " years old next month.";

```

## [Array](https://www.typescriptlang.org/docs/handbook/basic-types.html#array)

TypeScript, como JavaScript, le permite trabajar con matrices de valores. Los tipos de matriz se pueden escribir de una de dos maneras. En el primero, usa el tipo de elementos seguido de `[]`para denotar una matriz de ese tipo de elemento:

```ts
let list: number[] = [1, 2, 3];

```

La segunda forma usa un tipo de matriz genérico `Array<elemType>`:

```ts
let list: Array<number> = [1, 2, 3];
```

## [Tuple](https://www.typescriptlang.org/docs/handbook/basic-types.html#tuple)

Los tipos de tupla le permiten expresar una matriz con un número fijo de elementos cuyos tipos son conocidos, pero no necesitan ser los mismos. Por ejemplo, es posible que desee representar un valor como un par de ay `string`a `number`:

```ts
// Declare a tuple type
let x: [string, number];
// Initialize it
x = ["hello", 10]; // OK
// Initialize it incorrectly
x = [10, "hello"]; // Error

```

Al acceder a un elemento con un índice conocido, se recupera el tipo correcto:

```ts
console.log(x[0].substring(1)); // OK
console.log(x[1].substring(1)); // Error, 'number' does not have 'substring'

```

El acceso a un elemento fuera del conjunto de índices conocidos falla con un error:

```ts
x[3] = "world"; // Error, Property '3' does not exist on type '[string, number]'.

console.log(x[5].toString()); // Error, Property '5' does not exist on type '[string, number]'.
```

## [Enum](https://www.typescriptlang.org/docs/handbook/basic-types.html#enum)

Una adición útil al conjunto estándar de tipos de datos de JavaScript es `enum`. Como en lenguajes como C #, una enumeración es una forma de dar nombres más amigables a conjuntos de valores numéricos.

```ts
enum Color {Red, Green, Blue}
let c: Color = Color.Green;

```

Por defecto, las enumeraciones comienzan a numerar a sus miembros a partir de `0`. Puede cambiar esto configurando manualmente el valor de uno de sus miembros. Por ejemplo, podemos comenzar el ejemplo anterior en `1`lugar de `0`:

```ts
enum Color {Red = 1, Green, Blue}
let c: Color = Color.Green;

```

O, incluso establezca manualmente todos los valores en la enumeración:

```ts
enum Color {Red = 1, Green = 2, Blue = 4}
let c: Color = Color.Green;

```

Una característica útil de las enumeraciones es que también puede pasar de un valor numérico al nombre de ese valor en la enumeración. Por ejemplo, si tuviéramos el valor `2`pero no estuviéramos seguros de a qué se asignó en la `Color`enumeración anterior, podríamos buscar el nombre correspondiente:

```ts
enum Color {Red = 1, Green, Blue}
let colorName: string = Color[2];

console.log(colorName); // Displays 'Green' as its value is 2 above
```

## [Any](https://www.typescriptlang.org/docs/handbook/basic-types.html#any)

Es posible que necesitemos describir el tipo de variables que no sabemos cuando estamos escribiendo una solicitud. Estos valores pueden provenir de contenido dinámico, por ejemplo, del usuario o de una biblioteca de terceros. En estos casos, queremos inhabilitar la verificación de tipos y dejar que los valores pasen por las comprobaciones en tiempo de compilación. Para hacerlo, los etiquetamos con el `any`tipo:

```ts
let notSure: any = 4;
notSure = "maybe a string instead";
notSure = false; // okay, definitely a boolean

```

El `any`tipo es una forma poderosa de trabajar con JavaScript existente, lo que le permite activar y desactivar gradualmente la verificación de tipos durante la compilación. Puede esperar `Object`jugar un papel similar, como lo hace en otros idiomas. Sin embargo, las variables de tipo `Object`solo le permiten asignarles cualquier valor. No puede invocar métodos arbitrarios en ellos, incluso los que realmente existen:

```ts
let notSure: any = 4;
notSure.ifItExists(); // okay, ifItExists might exist at runtime
notSure.toFixed(); // okay, toFixed exists (but the compiler doesn't check)

let prettySure: Object = 4;
prettySure.toFixed(); // Error: Property 'toFixed' doesn't exist on type 'Object'.

```

El `any`tipo también es útil si conoce alguna parte del tipo, pero quizás no toda. Por ejemplo, puede tener una matriz, pero la matriz tiene una combinación de diferentes tipos:

```ts
let list: any[] = [1, true, "free"];

list[1] = 100;
```

## [Object](https://www.typescriptlang.org/docs/handbook/basic-types.html#object)

`object`es un tipo que representa el tipo no primitivo, es decir, todo lo que no es `number`, `string`, `boolean`, `symbol`, `null`, o `undefined`.

Con el `object`tipo, las API como `Object.create`se pueden representar mejor. Por ejemplo:

```ts
declare function create(o: object | null): void;

create({ prop: 0 }); // OK
create(null); // OK

create(42); // Error
create("string"); // Error
create(false); // Error
create(undefined); // Error
```

![[Pasted image 20211015122628.png]]