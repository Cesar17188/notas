# Implementando un CRUD en Express.js

**CRUD** viene de las siglas: _create read updated and delete_ esto significa **crear, leer, actualizar y eliminar**.

Nosotros vamos a obtener las rutas mediante el verbo GET. A continuación se muestran las rutas que vamos a ocupar para trabajar:

![[Pasted image 20210830175101.png]]

Ahora vamos a implementar un crud en nuestro código:

Para crear una ruta necesitamos de `express` pues es quien nos define el router, luego vamos a usar en esté caso un archivo de `mocks`, los **mocks son archivos falsos, de datos falsos**, pero más adelante vamos a aprender cuando nos conectemos con servicios y como conectarnos a la base de datos para traer archivos reales, en este ejemplo lo estamos haciendo, porque lo que nos interesa ahora es entender como se definen las rutas y esos archivos de mocks nos van a servir más adelante para escribir test y verificar.

```js
/**
 * Para crear una ruta necesitamos de express pues es quien nos define el router
 */
const express = require("express");
const { moviesMock } = require();

/** vamos a recibir una aplicación de express, lo que nos permite ser dinamicos y obtener el control,
 * sobre que aplicación va a consumir nuestra ruta.
*/

function moviesApi(app) {
  // creamos el router
  const router = express.Router();
  // le decimos a la aplicación que le vamos a pasar como parametro le vamos a decir la ruta de inicio
  app.use("/api/movies", router)

  // Apartir de aqui lo que hacemos es alimentar el router con las otras rutas
  // Cuando se le asigna un get al home, y el home va a ser api/movies, que fue el que definimos arriba

/* nos va a devolver las salidas, como estamos escribiendo código asincrono debemos usar la palabra
   clave async, recuerden que una ruta recibe el request, el response object y en este caso vamos a 
   recibir la funcionalidad next, esto hace parte de la teoria de middleware que vamos a explicar 
   más adelante
*/
  router.get("/", async function (req, res, next) {
    // como es código asincron es muy importante utilizar el try catch
    try {
      // es importante que como nuestro codigo es un await debemos envolverlo
      // en una promesa para que puedamos hacer uso de nuestro código asincrono con la palabra await
      const movies = await Promise.resolve(moviesMock);

      // Usamos response, definimos el estatus, que como hablamos con anterioridad va a ser 200 de ok
      // definimos su estructura json
      res.status(200).json({
        data: movies,
        message: 'movies listend'
      })
    } catch (error) {
      next(error);
    }
  })
}

// Ahora tenemos que exportarla, porque aquí estamos definiendo la ruta pero no la estamos usando
// en nuestra aplicación de express

module.exports = moviesApi;
```

Ahora nos vamos a nuestro archivo index, removemos las rutas de ejemplo que creamos con anterioridad, e importamos nuestra ruta, como es una función debemos ejecutarla y pasarle nuestra aplicación de express.

Con esto sería suficiente, pero es muy importante crear nuestro archivo de mocks, usamos una aplicación que se llama `mockroo` que nos ayuda a crear mocks fácilmente de una estructura.

El archivo de mocks estará disponible en este repositorio.

## Métodos idempotentes del CRUD

Acabamos de ver como podemos listar las peliculas, ahora lo que vamos a ver es el resto de métodos de `CRUD`, para eso vamos a mirar el código.

Como vemos en el siguiente coódigo los método del CRUD tienen una estrucutura muy similar, para eso vamos a copiar el método get 4 veces y le haremos algunas modificaciones

```js
/**
 * Para crear una ruta necesitamos de express pues es quien nos define el router
 */
const express = require("express");
const { moviesMock } = require("../utils/mocks/movies");

/** vamos a recibir una aplicación de express, lo que nos permite ser dinamicos y obtener el control,
 * sobre que aplicación va a consumir nuestra ruta.
*/

function moviesApi(app) {
  // creamos el router
  const router = express.Router();
  // le decimos a la aplicación que le vamos a pasar como parametro le vamos a decir la ruta de inicio
  app.use("/api/movies", router)

  // Apartir de aqui lo que hacemos es alimentar el router con las otras rutas
  // Cuando se le asigna un get al home, y el home va a ser api/movies, que fue el que definimos arriba

  /* nos va a devolver las salidas, como estamos escribiendo código asincrono debemos usar la palabra
     clave async, recuerden que una ruta recibe el request, el response object y en este caso vamos a 
     recibir la funcionalidad next, esto hace parte de la teoria de middleware que vamos a explicar 
     más adelante
  */
  router.get("/", async function (req, res, next) {
    // como es código asincron es muy importante utilizar el try catch
    try {
      // es importante que como nuestro codigo es un await debemos envolverlo
      // en una promesa para que puedamos hacer uso de nuestro código asincrono con la palabra await
      const movies = await Promise.resolve(moviesMock);

      // Usamos response, definimos el estatus, que como hablamos con anterioridad va a ser 200 de ok
      // definimos su estructura json
      res.status(200).json({
        data: movies,
        message: 'movies list'
      })
    } catch (error) {
      next(error);
    }
  })

  // Obtener movie por id
  router.get("/:movieId", async function (req, res, next) {
    try {
      const movies = await Promise.resolve(moviesMock[0]);
      res.status(200).json({
        data: movies,
        message: 'movies retrieved'
      })
    } catch (error) {
      next(error);
    }
  })

  // create
  router.post("/", async function (req, res, next) {
    try {
      const createdMovieId = await Promise.resolve(moviesMock[0].id);
      res.status(201).json({
        data: createdMovieId,
        message: 'movie created'
      })
    } catch (error) {
      next(error);
    }
  })

  // PUT - actualizar
  router.put("/:movieId", async function (req, res, next) {
    try {
      const updatedMovieId = await Promise.resolve(moviesMock[0].id);
      res.status(200).json({
        data: updatedMovieId,
        message: 'movie updated'
      })
    } catch (error) {
      next(error);
    }
  })

  // delete
  router.delete("/:movieId", async function (req, res, next) {
    try {
      const deleteMovieId = await Promise.resolve(moviesMock[0].id);
      res.status(200).json({
        data: deleteMovieId,
        message: 'movies deleted'
      })
    } catch (error) {
      next(error);
    }
  })

}
// Ahora tenemos que exportarla, porque aquí estamos definiendo la ruta pero no la estamos usando
// en nuestra aplicación de express

  module.exports = moviesApi;
```

Antes de continuar ya que es un buen momento para hacer commit, me gustaría hablar de algo que se llama el `gitignore`, es un archivo de configuración que le dice a git que archivos no debemos compartir, hay archivos inecesarios como `node_modules` entre otras, que no tiene sentido compartirla con las demás, pues esos archivos se generan por el sistema operativo o por carpeta o por usuario. La herramienta de [ignore.io](http://gitignore.io/) me permite definir precisamente esos hambientes, como nuestro proyecto es de node vamos a seleccionar ese tag, y como no sabemos quien va a poder usar esté proyecto, podemos agregar las 3 sistemas operativos, windows, mac y linux.
