# Gestión de paquetes: NPM y package.json

**npm** (Node Package Manager) es un administrador de paquetes que permiten ejecutar funciones ya realizadas y validadas y de esta manera acelerar y asegurar la calidad de neustro proceso de desarrollo.

Podemos buscar modulos para casi todo en:

[npm](https://www.npmjs.com/)

```
// Para instalar un modulo de npm en nuestro proyecto
$ npm install is-odd

// Para requerir el modulo
const isOdd = require('is-odd');
console.log(isOdd(3)); // true

// Para revisar que los paquetes no estan actualizados a nivel global dentro de nuestro proyecto
npm outdated -g --depth=0
/* 
Va a imprimir algo así:
Package         Current  Wanted  Latest  Location
firebase-tools    8.0.1   8.0.2   8.0.2  global
npm              6.13.7  6.14.4  6.14.4  global
*/

// Para actualizar todos los paquetes a nivel global dentro del proyecto
npm update -g
```