# Ejecutar Tareas
**Organización y scripts en paralelo**  
Conforme vamos creando scripts en el package.json, nuestra sección de scripts se puede ir complicando y haciendo más grande, por lo que conviene mantenerla organizada. Además, también puede entrar en juego la necesidad de crear scripts que ejecuten múltiples tareas de forma simultánea, o crear comandos que funcionen en sistemas como GNU/Linux y Mac, pero también en Windows. Para todo ello, existe un paquete llamado **_npm-run-all_** que nos permite realizar esto, entre otras cosas.

Lo primero, es instalar el paquete npm-run-all en nuestro proyecto. Lo instalaremos como dependencia de desarrollo, puesto que es para gestionar proyectos NPM y no tiene relación con la web definitiva en producción:

```
npm install --save-dev npm-run-all
```

Una vez instalado, si necesitamos que se ejecuten múltiples tareas que queremos realizar de forma independiente podemos agruparlas con un namespace utilizando los dos puntos : y luego ejecutar el grupo entero con un npm-run-all <namespace>:*:

"scripts": {
  "build": "npm-run-all build:*",
  "build:html": "pug src/index.pug ...",
  "build:css": "postcss src/index.css ...",
  "build:js": "rollup src/index.js ..."
}


Por defecto, estas tareas se ejecutan secuencialmente. Es decir, hasta que la primera no termine, no se ejecutará la siguiente. Esto puede ser alterado utilizando el flag **_-p_** (parallel) a npm-run-all:


"scripts": {
  "dev": "npm-run-all -p dev:*",
  "dev:html": "pug --watch src/index.pug ...",
  "dev:css": "postcss --watch src/index.css ...",
  "dev:js": "rollup --watch src/index.js ..."
}


Fuente: [https://lenguajejs.com/npm/administracion/scripts-de-npm/](https://lenguajejs.com/npm/administracion/scripts-de-npm/)

Los scripts NPM: Son comandos que podemos establecer para poder ejecutar desde la consola. Estos nos van a dar una serie de salidas según sea el caso.

Podemos crear la cantidad de scripts que necesitemos. Estos scripts van a poder correr de forma nativa dentro de nuestra terminal.

Puedes también especificar scripts con el prefijo “pre” que se ejecutarán automáticamente antes del comando que ejecutaste. Por ejemplo, si defines el comando `build` y `prebuild`, cuando corras `npm run build` el comando `prebuild` se ejecutará primero. Esto sirve para poder ejecutar tareas que hagan algún tipo de preparación necesaria para correr el comando principal. Sin embargo, hay que hacer notar que si el comando pre falla (retorna un valor que no es 0) el comando principal no se ejecutará. Esto es algo bueno ya que si nuestro proceso de preparación no se realiza de forma exitosa, puede que tengamos problemas al querer ejecutar la tarea principal.

En algunas ocaciones, sin embargo, la tarea previa puede fallar sin que eso afecte la ejecución de la tarea principal. En esos casos puedes usar `|| exit 0` para retornar 0:


"presass-build": "(rm css/*.css; rm css/*.css.map) || exit 0"


Ese es un ejemplo de un comando que hice hace un tiempo. `rm` puede fallar si el directorio css está vacio, y en ese caso no hay problema, la tarea principal puede funcionar sin ningún problema ya que `presass-build` tiene el propósito de vaciar ese directorio.

`npm run` agrega el directorio `./node_modules/bin/` al PATH de modo que para ejecutar un comando no es necesario agregar la ruta completa. Esto es algo que hace tiempo me confundió, cuando vi que Laravel ejecuta un comando `setenv` y yo quice buscarlo en mi computadora con `which setenv` y resultó que el comando no existía. Esto es porque en realidad el binario está ubicado en `node_modules/bin/`

ejemplo
```
"dev": "webpack-dev-server --mode development",
"build": "webpack --mode production",
"start": "serve ./dist -s -l 8080"
```

-   dev: Modo desarrollo.
-   build: Compila todo y me crea un directorio dist.
-   start: Toma el directorio dist y lanzo un servidor en modo producción.

Si te aparece un error al ejecutar el comando:

```
npm run deploy
```

Posiblemente es porque no se han instalado las dependencias del proyecto, esto lo puedes solucionar ejecutando:

```
npm install
```

Y luego si puedes ejecutar el comando deploy e iniciar el proyecto con start

esta alerta:  
found 591 vulnerabilities (577 low, 3 moderate, 10 high, 1 critical)

se puede resolver comúnmente con:

```
npm audit fix
```

Aunque algunas dependencias se actualizaran a la ultima version con el parche que resuelve las vulnerabilidades, habrán algunas que te pedirá que las actualices manualmente desde el package.json.

Te recomiendo que valides si al actualizar las dependencias la aplicación final sea compatible con esas nuevas versiones.