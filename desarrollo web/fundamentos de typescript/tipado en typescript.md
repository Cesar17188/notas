# Tipado en TypeScript

Explicito: Define una sintaxis para la creación de variables con tipo de dato  

```ts
miVariableExplicita : string = 'Esta variable es explícita' // el `:` permite especificar el tipo del dato
```

**nombreVariable : Tipo de dato ** 

Inferido: TypeScript tiene la habilidad de deducir el tipo en funcion de un valor.

```ts
miVariableInferida = "Esta variable será un string" // TS deduce el tipo de miVariableInferida y el valor, a partir de la inicialización de la misma
```

## **Tipo de datos primitivos**  
-   Number
-   Boolean
-   String
-   Array
-   Tuple
-   Enum
-   Any
-   Void
-   Null
-   Undefined
-   Never
-   Object

Encontré más claro y fácil de digerir la documentación oficial que pueden encontrar acá: [https://www.typescriptlang.org/docs/handbook/basic-types.html](https://www.typescriptlang.org/docs/handbook/basic-types.html)

#### Number, Boolean y String

<h5>Tipo Number</h5>

Aquí podemos utilizar valores numéricos como:

-   Enteros
-   Flotantes
-   Hexadecimales
-   Octales
-   Binarios

<h5>Tipo Boolean</h5>

-   El tipo de dato más simple en TypeScript
-   Dos únicos valores: true y false

<h5>Tipo String</h5>

-   El tipo de dato para trabajar con datos de texto
-   Así como en JS, se pueden usar comillas simples y dobles ‘’, “”
-   Permiten definir múltiples líneas de texto
-   Pueden contener expresiones o variables embebidas
-   Se debe usar el caracter backtick/backquote(`) y para expresiones ${expr}

```typescript
//*Number
//*Explícito
let phone: number;
phone = 1234567890;
//!phone = 'hola'; /*Esto produce un error*/

//*Inferido
let phoneNumber = 12345;
phoneNumber = 123;
//!phoneNumber = true; /*Esto también produce un error*/

let hex: number = 0xf00d; //* Hexadecimal
let binary: number = 0b1010; //* Binario
let octal: number = 0o777; //* Octal

//*Boolean
//* Explícito
let isPro: boolean;
isPro = true;
//!isPro = 1; /*Esto produce un error*/

//* Inferido
let isUserPro = false;
isUserPro = true;
//!isUserPro = 0; /*Esto también produce un error*/

//*Strings
//*Explícito
let username: string;
username = "Miguel";
//!username = true; /*Esto da un error */

//*Inferido
let my_name = "Miguel";

//*Template String
//*Uso de ``
let userInfo: string;
userInfo = `
  User Info:
  username: ${username}
  firstName: ${username + ' Reyes'}
  phone: ${phone}
  isPro: ${isPro}
`;
console.log(`userInfo ${userInfo}`);
```

### Tipos de datos

Dentro de los tipos explícitos que maneja TypeScript, tenemos:

1.  **Number**. Este tipo de dato incluye valores numéricos, hexadecimales, binarios y octales.
    
    ```tsx
    // Explícito
    let phone: number
    phone = 3315015804
    
    let hex: number = 0xf00d
    let binary: number = 0b1010
    let octal: number = 0o744
    
    // Implícito
    let phoneNumber = 3315015804
    ```
    
2.  **Boolean**. Es el tipo de dato más simple en TypeScript ya que solo acepta dos tipos de valores que son `true` o `false`.
    
    ```tsx
    // Explícito
    let isTrue: boolean = true
    
    // Implícito
    let isFalse = false
    ```
    
3.  **String**. Es el tipo de dato para trabanar con datos textuales o cadenas, para definir este tipo de dato se puede usar comilla dobles `""` o simples `''`.
    
    ```tsx
    // Explícito
    let userName: string = 'Alejandra'
    
    // Implícito
    let lastName = 'Camacho'
    ```
    
    Dentro del tipo de dato _string_ también podemos crear _templates_ de la siguiente forma:
    
    ```tsx
    // Template string
    // Uso de back-tick ``
    let userInfo: string = `
      User info:
      firstName: ${firstName}
      lastName: ${lastName}
      phone: ${phone}
      isValid: ${isTrue}
    `
    ```


Recomiendo mucho este vídeo donde hablan de los modelos primitivos de JavaScript: [https://www.youtube.com/watch?v=cC65D2q5f8I](https://www.youtube.com/watch?v=cC65D2q5f8I)

Interesante la sintaxis de TypeScripe, estaba acostumbrado a Tipo Nombre; Como en todos los lenguajes de tipado que he usado (C++ y Java)

ATENCIÓN. Cuando escribas tu código JavaScript en TypeScript y lo transpiles luego, debes acostumbrarte a no hacer «retoques» a mano en el JavaScript. Si tienes que cambiar o retocar cualquier cosa, por nimia que te parezca, hazlo en el TypeScript original y vuelve a transpilar, siguiendo las reglas de TypeScript. De otro modo, podrías estar infringiéndolas y encontrarte cometiendo los mismos errores una y otra vez. Cuando escribimos un código en TypeScript y, para poder usarlo, debemos transpilarlo a JavaScript, si hemos cometido errores de sintaxis el transpilador nos lanzará mensajes de error que nos ayudarán a escribir un código limpio y bien organizado.