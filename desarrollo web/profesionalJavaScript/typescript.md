# TypeScript
# Introducción

**TypeScript** es un _superset_ de JavaScript que añade tipos a nuestras variables ayudando así a la detección de errores de forma temprana y mejorando el autocompletado.

Los navegadores no entienden TypeScript así que lo vamos a transpilar a JavaScript usando **Parcel**.

## TypeScript

**TypeScript** es un lenguaje de programación libre y de [código abierto](https://es.wikipedia.org/wiki/C%C3%B3digo_abierto "Código abierto") desarrollado y mantenido por [Microsoft](https://es.wikipedia.org/wiki/Microsoft "Microsoft"). Es un superconjunto de [JavaScript](https://es.wikipedia.org/wiki/JavaScript "JavaScript"), que esencialmente añade tipos estáticos y objetos basados en clases. [Anders Hejlsberg](https://es.wikipedia.org/wiki/Anders_Hejlsberg "Anders Hejlsberg"), diseñador de [C#](https://es.wikipedia.org/wiki/C "C") y creador de [Delphi](https://es.wikipedia.org/wiki/Embarcadero_Delphi "Embarcadero Delphi") y [Turbo Pascal](https://es.wikipedia.org/wiki/Turbo_Pascal "Turbo Pascal"), ha trabajado en el desarrollo de TypeScript.[1](https://es.wikipedia.org/wiki/TypeScript#cite_note-1)​ TypeScript puede ser usado para desarrollar aplicaciones JavaScript que se ejecutarán en el lado del cliente o del servidor ([Node.js](https://es.wikipedia.org/wiki/Node.js "Node.js")).

TypeScript extiende la sintaxis de JavaScript, por tanto cualquier código JavaScript existente debería funcionar sin problemas. Está pensado para grandes proyectos, los cuales a través de un compilador de TypeScript se traducen a código JavaScript original.

## [Introducción](https://www.typescriptlang.org/docs/handbook/basic-types.html#introduction)

Para que los programas sean útiles, necesitamos poder trabajar con algunas de las unidades de datos más simples: números, cadenas, estructuras, valores booleanos y similares. En TypeScript, admitimos casi los mismos tipos que esperaría en JavaScript, con un tipo de enumeración conveniente para ayudar a las cosas.

## TypeScript en 5 minutos

Comencemos creando una aplicación web simple con TypeScript.

## [Instalación de TypeScript](https://www.typescriptlang.org/docs/handbook/typescript-in-5-minutes.html#installing-typescript)

Hay dos formas principales de obtener las herramientas TypeScript:

-   Vía npm (el administrador de paquetes Node.js)
-   Al instalar los complementos de Visual Studio de TypeScript

Visual Studio 2017 y Visual Studio 2015 Update 3 incluyen TypeScript de forma predeterminada. Si no instaló TypeScript con Visual Studio, aún puede [descargarlo](https://www.typescriptlang.org/#download-links) .

Para usuarios de NPM:

```shell
> npm install -g typescript

```

## [Construyendo su primer archivo TypeScript](https://www.typescriptlang.org/docs/handbook/typescript-in-5-minutes.html#building-your-first-typescript-file)

En su editor, escriba el siguiente código JavaScript en `greeter.ts`:

```ts
function greeter(person) {
    return "Hello, " + person;
}

let user = "Jane User";

document.body.textContent = greeter(user);
```

## [Compilando su código](https://www.typescriptlang.org/docs/handbook/typescript-in-5-minutes.html#compiling-your-code)

Utilizamos una `.ts`extensión, pero este código es solo JavaScript. Podría haber copiado / pegado esto directamente desde una aplicación JavaScript existente.

En la línea de comando, ejecute el compilador TypeScript:

```shell
tsc greeter.ts

```

El resultado será un archivo `greeter.js`que contiene el mismo JavaScript que usted introdujo. ¡Estamos funcionando con TypeScript en nuestra aplicación JavaScript!

Ahora podemos comenzar a aprovechar algunas de las nuevas herramientas que ofrece TypeScript. Agregue una `: string`anotación de tipo al argumento de la función ‘persona’ como se muestra aquí:

```ts
function greeter(person: string) {
    return "Hello, " + person;
}

let user = "Jane User";

document.body.textContent = greeter(user);
```

## [Numero](https://www.typescriptlang.org/docs/handbook/basic-types.html#number)

Como en JavaScript, todos los números en TypeScript son valores de coma flotante. Estos números de coma flotante obtienen el tipo `number`. Además de los literales hexadecimales y decimales, TypeScript también admite literales binarios y octales introducidos en ECMAScript 2015.

```ts
let decimal: number = 6;
let hex: number = 0xf00d;
let binary: number = 0b1010;
let octal: number = 0o744;
```


![[Pasted image 20211013121500.png]]
