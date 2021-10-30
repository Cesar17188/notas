# Interfaces

Nos permiten declarar la forma exacta de un objeto, definiendo los tipos de sus propiedades y si son opcionales o no.

## Interfaces

## [Introducción](https://www.typescriptlang.org/docs/handbook/interfaces.html#introduction)

Uno de los principios centrales de TypeScript es que la verificación de tipos se centra en la _forma_ que tienen los valores. Esto a veces se llama “tipificación de pato” o “subtipo estructural”. En TypeScript, las interfaces cumplen la función de nombrar estos tipos y son una forma poderosa de definir contratos dentro de su código, así como contratos con código fuera de su proyecto.

## [Nuestra primera interfaz](https://www.typescriptlang.org/docs/handbook/interfaces.html#our-first-interface)

La forma más fácil de ver cómo funcionan las interfaces es comenzar con un ejemplo simple:

```ts
function printLabel(labeledObj: { label: string }) {
    console.log(labeledObj.label);
}

let myObj = {size: 10, label: "Size 10 Object"};
printLabel(myObj);

```

El verificador de tipos verifica la llamada a `printLabel`. La `printLabel`función tiene un único parámetro que requiere que el objeto pasado tenga una propiedad llamada `label`de tipo `string`. Tenga en cuenta que nuestro objeto en realidad tiene más propiedades que esto, pero el compilador solo verifica que _al menos_ las requeridas estén presentes y coincidan con los tipos requeridos. Hay algunos casos en que TypeScript no es tan indulgente, que cubriremos en un momento.

Podemos escribir el mismo ejemplo nuevamente, esta vez usando una interfaz para describir el requisito de tener la `label`propiedad que es una cadena:

```ts
interface LabeledValue {
    label: string;
}

function printLabel(labeledObj: LabeledValue) {
    console.log(labeledObj.label);
}

let myObj = {size: 10, label: "Size 10 Object"};
printLabel(myObj);

```

La interfaz `LabeledValue`es un nombre que ahora podemos usar para describir el requisito en el ejemplo anterior. Todavía representa tener una sola propiedad llamada `label`que es de tipo `string`. Tenga en cuenta que no tuvimos que decir explícitamente que el objeto que pasamos `printLabel`implementa esta interfaz como podríamos tener que hacerlo en otros idiomas. Aquí, lo único que importa es la forma. Si el objeto que pasamos a la función cumple con los requisitos enumerados, entonces está permitido.

Vale la pena señalar que el verificador de tipo no requiere que estas propiedades vengan en ningún tipo de orden, solo que las propiedades que requiere la interfaz están presentes y tienen el tipo requerido.

## [Propiedades opcionales](https://www.typescriptlang.org/docs/handbook/interfaces.html#optional-properties)

No todas las propiedades de una interfaz pueden ser necesarias. Algunos existen bajo ciertas condiciones o pueden no estar allí en absoluto. Estas propiedades opcionales son populares cuando se crean patrones como “bolsas de opciones” donde se pasa un objeto a una función que solo tiene un par de propiedades rellenadas.

Aquí hay un ejemplo de este patrón:

```ts
interface SquareConfig {
    color?: string;
    width?: number;
}

function createSquare(config: SquareConfig): {color: string; area: number} {
    let newSquare = {color: "white", area: 100};
    if (config.color) {
        newSquare.color = config.color;
    }
    if (config.width) {
        newSquare.area = config.width * config.width;
    }
    return newSquare;
}

let mySquare = createSquare({color: "black"});

```

Las interfaces con propiedades opcionales se escriben de manera similar a otras interfaces, con cada propiedad opcional indicada por un `?`al final del nombre de la propiedad en la declaración.

La ventaja de las propiedades opcionales es que puede describir estas propiedades posiblemente disponibles y al mismo tiempo evitar el uso de propiedades que no forman parte de la interfaz. Por ejemplo, si hubiéramos escrito mal el nombre de la `color`propiedad `createSquare`, obtendríamos un mensaje de error informándonos:

```ts
interface SquareConfig {
    color?: string;
    width?: number;
}

function createSquare(config: SquareConfig): { color: string; area: number } {
    let newSquare = {color: "white", area: 100};
    if (config.clor) {
        // Error: Property 'clor' does not exist on type 'SquareConfig'
        newSquare.color = config.clor;
    }
    if (config.width) {
        newSquare.area = config.width * config.width;
    }
    return newSquare;
}

let mySquare = createSquare({color: "black"});
```

![[Pasted image 20211015124342.png]]