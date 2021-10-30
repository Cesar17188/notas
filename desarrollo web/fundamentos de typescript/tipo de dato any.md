# Any

**Tipo: Any**

-   Usado para capturar valores dinámicos
-   Los valores pueren cambiar de tipo en el tiempo:  
    – APIs externas  
    – Librerías de terceros
	 
	 Litimar el uso del tipo `any` y `null` a casi **nulo** es fundamental, para tener aplicaciones escalabres y robustas 👩🏽‍💻

<h5>Tipo Any</h5>

-   Usado para capturar valores dinámicos
-   Los valores pueden cambiar de tipo en el tiempo:
    -   APIs externas
    -   Librerías de terceros

Any no es recomendado. Solamente debería usarse cuando no sabemos qué tipo de dato almacenará nuestra variable.

```ts
// type Any --> For dynamic variables
// Explicit type
let idUser: any;
idUser = 1; // Number
idUser = '1'; // String
console.log('iduser ', idUser);
console.log(typeof idUser);

// Inferred type
let otherId;
otherId = '1';
otherId = 1;
// otherId = true;
console.log('otherId ', otherId);
console.log(typeof otherId);

let suprise: any = 'Hello typescript';
// suprise.sayHello(); // Error
const res = suprise.substring(10);
console.log(`res ${res}`);
```