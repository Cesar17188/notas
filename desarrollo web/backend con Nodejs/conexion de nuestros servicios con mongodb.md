# Conexión de nuestros servicios con MongoDB

Ya que implementaste las acciones en la librería de mongo, nos vamos a disponer a coger la capa de servicios, remover los mocks e implementar esa librería y en está ocación ya tendremos persistencia de datos.

```js
const MongoLib = require('../lib/mongo');

class MoviesService {
  constructor() {
    this.collection = 'movies';
    this.mongoDB = new MongoLib();
  }
  async getMovies({ tags }) {
    const query = tags && { tags: { $in: tags } };
    const movies = await this.mongoDB.getAll(this.collection, query);
    return movies || [];
  }

  async getMovie({ movieId }) {
    const movie = await this.mongoDB.get(this.collection, movieId);
    return movie || {};
  }

  async createMovie({ movie }) {
    const createMovieId = await this.mongoDB.create(this.collection, movie)
    return createMovieId || {};
  }

  async updateMovie({ movieId, movie } = {}) {
    const updateMovie = await this.mongoDB.updated(this.collection, movieId, movie);
    return updateMovie;
  }

  async deletedMovie({ movieId }) {
    const deletedMovieId = await this.mongoDB.delete(this.collection, movieId);
    return deletedMovieId;
  }


}

module.exports = MoviesService;
```
Si vamos a crear un registro por medio de [postman](https://github.com/JasanHdz/backendnodejs/blob/master/notes) cuando hacemos el send, vamos a tener un error y es porque el aún no sabe como leer los datos que le estamos pasando, **por defecto express necesita parcear estos datos JSON**. La manera de **corregirlo es agregando un Middleware desde el index.js**

```js
const express = require('express');
const app = express();

const { config } = require('./config/index');
const moviesApi = require('./routes/movies.js');

// middleware de bodyparser
app.use(express.json());
moviesApi(app);

// Cuando hagamos un request a nuestra aplicación, nos imprima un hello world
app.get('/', (req, res) => {
  res.send("Hello world");
})

app.get('/json', (req, res) => {
  res.json({hello: 'world'});
})

app.listen(config.port, function () {
  console.log(`Listening http://localhost:${config.port}`);
})
```

Una vez funcionando nos damos cuenta que nuestro servicio está siendo persistente con la base de datos.