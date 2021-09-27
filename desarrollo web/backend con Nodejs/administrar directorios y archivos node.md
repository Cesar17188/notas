# Administrar directorios y archivos

Leer el nombre de los archivos que estan dentro de un directorio

```js
// leer cuales son los archivos que estan dentro de un directorio
const fs = require('fs');
// dirname: directorio actual
const files = fs.readdir(__dirname, (err, files) => {
  if (err) {
    console.log(err);
  }
  console.log(files);
})
```
Creamos directorios o carpetas con **mkdir desde node**.

```js
// Creamos direcorios o carpetas.
const fs = require('fs');
fs.mkdir("ejemplo/documents/node", { recursive: true }, err => {
  if (err) {
    console.log(err);
  }
});
```
**Copiar archivos con Nodejs**.
```js
const fs = require('fs');

// Primer parametro el archivo que queremos copiar
// Segundo parametro el archivo que queremos crear
fs.copyFile("naranja.txt", "limon.txt", err => {
  if (err) {
    console.log(err);
  }
  console.log("naranja.txt fue copiado como limon.txt");
})
```
