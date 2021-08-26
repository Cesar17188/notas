# Sistema operativo y sistema de archivos

## Utilidades del sistema operativo

```js
const os = require('os');

// método para conocer los cpus de nuestra maquina
console.log("CPU info", os.cpus());
// Conocer la ip de nuestra máquina.
console.log("IP addrees", os.networkInterfaces().lo.map(i => i.address));

// Conocer la memoria libre de nuestro sistema
console.log("Free memory", os.freemem());

// Conocer tipo de sistema operativo tenemos
console.log("Type ", os.type());

// Conocer la versión
console.log("SO version", os.release());

// Imprimir la dirección del usuario
console.log("Usr info", os.userInfo());
```

## Utilidades con el sistema de archivos

En node las utilidades, la mayoria pueden funcionar de manera sincrona y asincrona, de manera **sincrona**, quiere decir que el **va a esperar a hasta que se ejecuta ese proceso y hasta que no de una respuesta no va a continuar con la siguiente linea**.

En node **cuando se ejecuta de manera sincrona necesitamos usar callbacks** porque es la manera en la que el sabe cuando ya terminamos, ejecute mi código que quiero procesar despues de que hizo todo lo que tenia que hacer esté modulo

Usando la **readFileSync** que lee los datos de manera sincrona.

```js
const fs = require('fs');

/*Cuando usamos la manera asincrona es muy recomendable usar un bloque
try catch porque es la manera en que podemos capturar un error
*/

try {
  // leer mi archivo
  // Con process.argv 'argumentos en vector' es poder leer lo que nosotros pasamos por la terminal
  const file = process.argv[2];

  // leer nuestro contenido
  const content = fs.readFileSync(file).toString();

  const lines = content.split('\n').length;
  console.log(lines);
} catch (err) {
  console.log(err);
  console.log("Necesitas especificar el archivo que quieres leer");
}
```

Vamos a hacer lo mismo de manera asincrona, pero esta vez no tenemos que especificar que es _readFileSync_ sino que es simplemente **readFile**, porque **por defecto Nodejs trata de ser asincrono**.

```js
const fs = require('fs');

const file = process.argv[2];

if (!file) {
  throw new Error('Debes indicar el archivo que quieres leer');
}
// Como primer parametro recibe el archivo y como segundo parametro recibe el callback
// un callback es error first callback
const content = fs.readFile(file, (err, content) => {
  if (err) {
    console.log(err);
  }
  const lines = content.toString().split('\n').length;
  console.log(lines);
})
```
El **módulo file system** no solo nos permite leer archivos sino que en el también podemos **crear carpetas, leer directorios, crear archivos, eliminar archivos, etc**. Es todo lo que un usuario puede hacer con archivos y carpetas.

También podemos visitar la documentación de Nodejs 12.0 sobre [FileSystem](https://nodejs.org/api/fs.html#fs_file_system)