# Implementando una capa de servicios en express

Está aquitectura es una versión simplificada de [Clean Architecture](https://translate.google.com/translate?hl=&sl=en&tl=es&u=https%3A%2F%2Fblog.cleancoder.com%2Funcle-bob%2F2012%2F08%2F13%2Fthe-clean-architecture.html)

![[Pasted image 20210830193354.png]]

**¿Por que la comparto o la recomiendo?**

Porque MVC que es la arquitectura tradicional a la que estamos acostumbrados, se queda corta en las aplicaciones modernas, **no nos basta** solo con tener: **modelo, vista y controlador**. Entonces lo que nosotros definimos en una aplicación en express: **los controladores que son toda la capa de middlewares y el router** que se comunican con la API y reciben o envían JSON, luego temos una **capa de servicios**, esta capa es muy importante porque aquí esta el corazón de nuestra aplicación, aquí es donde está toda la logica de negocio y es importante saber que **los controladores NO llaman a otros controladores** los controladores **solo llaman servicios**. Pero **los servicios si pueden llamar otros servicios o llamar librerias**, las librerías **son** la capa que esta adjunta a **librerias externas**, como por ejemplo: **bases de datos, bases de datos que estan en la nube o incluso otras API**.

Diferentes razones y opiniones sobre porque dejar de usar MVC:

-   [Clean coder](https://blog.cleancoder.com/uncle-bob/2012/08/13/the-clean-architecture.html)
-   [Ryan Florence](https://www.youtube.com/watch?v=kp-NOggyz54)
-   [Laravel no es mvc](https://styde.net/porque-laravel-no-es-mvc-y-tu-deberias-olvidarte-de-mvc/)
-   [Twitt sobre mvc por founder de Laravel](https://twitter.com/taylorotwell/status/262290285499936768)

Ahora vamos a ver como implementar [Clean Architecture](https://translate.google.com/translate?hl=&sl=en&tl=es&u=https%3A%2F%2Fblog.cleancoder.com%2Funcle-bob%2F2012%2F08%2F13%2Fthe-clean-architecture.html) en nuestro código

Implementación de la capa de servicios:

```js
const { moviesMock } = require("../utils/mocks/movies");

class MoviesService {
  async getMovies() {
    const movies = await Promise.resolve(moviesMock);
    return movies || [];
  }

  async getMovie() {
    const movie = await Promise.resolve(moviesMock[0]);
    return movie || {};
  }

  async createMovie() {
    const createMovieId = await Promise.resolve(moviesMock[0].id);
    return createMovieId || {};
  }

  async updateMovie() {
    const deletedMovieId = await Promise.resolve(moviesMock[0].id);
    return deletedMovieId;
  }

}

module.exports = MoviesService;
```
Implementación de CRUD en express:
```js
const express = require("express");
const MoviesServices = require('../services/movies');

function moviesApi(app) {
  const router = express.Router();
  app.use("/api/movies", router);

  const moviesService = new MoviesServices();

  router.get("/", async function (req, res, next) {
    const { tags } = req.query;
    try {
      const movies = await moviesService.getMovies({ tags });

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
    const { movieId } = req.params;
    try {
      const movies = await moviesService.getMovie({ movieId });
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
    const { body: movie } = req;
    try {
      const createdMovieId = await moviesService.createMovie({ movie })
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
    const { movieId } = req.params;
    const { body: movie } = req;
    try {
      const updatedMovieId = await moviesService.updateMovie({ movieId, movie })
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