# Automatización de procesos

**Que es gulp.js?** 📖🖥💥

Es una herramienta de construcción en JavaScript construida sobre flujos de nodos . Estos flujos facilitan la conexión de operaciones de archivos a través de canalizaciones . Gulp lee el sistema de archivos y canaliza los datos disponibles de un complemento de un solo propósito a otro a través del .pipe()operador, haciendo una tarea a la vez. Los archivos originales no se ven afectados hasta que se procesan todos los complementos. Se puede configurar para modificar los archivos originales o para crear nuevos. Esto otorga la capacidad de realizar tareas complejas mediante la vinculación de sus numerosos complementos. Los usuarios también pueden escribir sus propios complementos para definir sus propias tareas. [Wikipedia](https://en.wikipedia.org/wiki/Gulp.js).

👉 [Empezando con Gulp.js](https://semaphoreci.com/community/tutorials/getting-started-with-gulp-js)  
👉 [Automatiza tu flujo de trabajo con GulpJS](https://platzi.com/blog/automatizacion-gulp-js/)


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
 "test": "echo \"Error: no test specified\" && exit 1",
 "start": "gulp",
 "build": "gulp build",
 "serve": "gulp serve"
 },

 "keywords": [],
 "author": "Cesar Armendariz <cesareli17188@gmail.com>",
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
 console.log("construyendo el sitio");
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

