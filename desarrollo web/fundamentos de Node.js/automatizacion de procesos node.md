# Automatizaci贸n de procesos

**Que es gulp.js?** 馃摉馃枼馃挜

Es una herramienta de construcci贸n en JavaScript construida sobre flujos de nodos . Estos flujos facilitan la conexi贸n de operaciones de archivos a trav茅s de canalizaciones . Gulp lee el sistema de archivos y canaliza los datos disponibles de un complemento de un solo prop贸sito a otro a trav茅s del .pipe()operador, haciendo una tarea a la vez. Los archivos originales no se ven afectados hasta que se procesan todos los complementos. Se puede configurar para modificar los archivos originales o para crear nuevos. Esto otorga la capacidad de realizar tareas complejas mediante la vinculaci贸n de sus numerosos complementos. Los usuarios tambi茅n pueden escribir sus propios complementos para definir sus propias tareas. [Wikipedia](https://en.wikipedia.org/wiki/Gulp.js).

馃憠 [Empezando con Gulp.js](https://semaphoreci.com/community/tutorials/getting-started-with-gulp-js)  
馃憠 [Automatiza tu flujo de trabajo con GulpJS](https://platzi.com/blog/automatizacion-gulp-js/)


Proceso

- Iniciar una carpeta con un proyecto npm $npm init -y$
- Instalar gulp con el comando $npm i gulp$
- verificar los archivos de package.json y la creacion del archivo gulp.js

### package.json
```json
{

 "name": "automatizacion",
 "version": "1.0.0",
 "description": "",
 "main": "index.js",
 "scripts": {
 "test": "echo \"Error:聽no聽test聽specified\" &&聽exit聽1",
 "start": "gulp",
 "build": "gulp聽build",
 "serve": "gulp聽serve"
 },

 "keywords": [],
 "author": "Cesar聽Armendariz聽<cesareli17188@gmail.com>",
 "license": "MIT",
 "dependencies": {
 "gulp": "^4.0.2",
 "gulp-server-livereload": "^1.9.2"
 }
}
```

### gulp.js
```js
const gulp = require("gulp");
const server = require("gulp-server-livereload");

  

gulp.task("build", function (cb) {
 console.log("construyendo聽el聽sitio");
 setTimeout(cb, 1200);
});

  

gulp.task("serve", function (cb) {
 gulp.src("www").pipe(
 server({
 livereload: true,
 open: true,
 })
 );
});

  
gulp.task("default", gulp.series("build", "serve"));

```

