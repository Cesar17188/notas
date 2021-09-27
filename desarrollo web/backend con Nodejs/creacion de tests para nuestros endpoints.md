# Creación de test para nuestros endpoints

En esté modulo aprenderemos a crear test con nodejs, la primer suit de test que vamos a crear es para nuestros endpoints que están úbicados a la capa de rutas, **su única responsabilidad de test es probar que le llegan los datos y devuelven los datos correspondientes**, vamos a ver como se hace en el código.

1.  Lo primero es instalar nuestras dependencias para los test `npm i -D mocha supertest sinon proxyquire`

-   **mocha**: es quien nos ayuda a correr los test.
-   **supertest**: es una utilidad que nos ayuda a levantar un servidor temporal.
-   **sinon** es una utilidad que nos ayuda a hacer mocks para test
-   **proxyquire**: es una utilidad que nos ayuda a inyectar los mocks cuando requeramos los paquetes.

2.  Antes de proceder con los test vamos a hacer una pequeña modificación en movies mocks. No solo teniendo estos mocks que nos van a hacer utiles para los test, voy a crear una pequeña utilidad, la cual nos ayudará a crear las peliculas filtradas.

Como nuestro objetivo es hacer test de las rutas, nosotros nunca vamos a hacer que llegue hasta los servicios. Solo vamos a testear las rutas, y eso lo vamos a hacer con **sinon** y **proxyquire**.
```js
function filteredMoviesMock(tag) {
  return moviesMock.filter(movie => movie.tags.includes(tag));
}
```
Luego vamos a crear un Mock de nuestros servicios, lo que hace esté mock es que cada vez que llamemos a getMovies() va a retornar la promesa que sería el Mock de las peliculas.
```js
class MoviesServicesMock {
  async getMovies() {
    return Promise.resolve(moviesMock);
  }
}
```
Y vamos a hacer un mock de método createMovie, y va a retornar la primera pelicual de nuestro MoviesMock
```js
class MoviesServicesMock {
  // ...
  async createMovie() {
      return Promise.resolve(moviesMock[0]);
    }
}
```
Y exportamos ambas utilidades:
```js
module.exports = {
  moviesMock,
  filteredMoviesMock,
  MoviesServicesMock
};
```
3.  El próximo va a ser en nuestra carpeta de utilidades, es crear un test server, esté es un server que su única misión va a ser levantar un server para pruebas. **Los Test siempre se deben correr independientes del server original** y más porque en esté caso no queremos levantar todo lo que tienen nuestro server, solo queremos un server muy pequeño que nos ayude a probar.

```js
const express = require('express');
const supertest = require('supertest');

// va a recibir una ruta
function testServer(route) {
// creamos una nueva app
  const app = express();
  // ha está app le vamos a pasar la ruta.
  route(app);
  // retornamos supertest y envolvemos nuestra app.
  return supertest(app);
}

module.exports = testServer;
```
Con estó ya tenemos lo necesario para empezar a crear nuestros test, entonces vamos a crear una carpeta que se llamé test y en esté caso como queremos hacer test a las rutas se va a llamar `routes.movies.test.js`, es buena práctica que esté archivo finalice en **.test.js**

```js
// obtenemos el assert que es el que se encargá de verificar si es verdad o no nuestra
// comparación en los test
const assert = require('assert');
// Proxyquire lo que nos permite es que cada vez que hagamos un require
// podemos elegir que en vez de que nos traega el paquete real, nos traega un mock
const proxyquire = require('proxyquire');

// Traemos los mocks porque son los que nos van ayudar a verficar que esté funcionando
// correctamente.
const { moviesMock, MoviesServicesMock } = require('../utils/mocks/movies');
// necesitamos el testServer para correr nuestro server.
const testServer = require('../utils/testServer');

// Describimos nuestros test con la palabra describe, esto es lo que va a imprimir la consola
// la cual recibe como callback una función, en esté caso vamos a hacer los test del get de las movies
describe('routes - movies', function () {
  // Para poder probar los test de las movies necesitamos obtener la ruta que vamos a probar
  // en esté caso nuestra ruta será intervenida por proxyquire, que va ser la ruta de las movies
  // Lo que vamos a hacer es que ese archivo que nos llega de rutas, el cúal tiene una dependencia
  // nuestro servicio real, nosotros no queremos que cuando estemos llamando nuestras rutas
  // que llame nuestros servicios, porque el objetivo de estos test es que las rutas hagan su trabajo
  // ya más adelante haremos una prueba directa a los servicios
  const route = proxyquire('../routes/movies', {
    // La inclusión de esté servicio como está escrita allá, será remplazada por MoviesServicesMock
    '../services/movies': MoviesServicesMock
    // Es decir, cada vez que llamemos la ruta, quien va a servir de los Servicios es MoviesServiceMock
  });

  // creamos un request que va ser pasando testServer y le pasamos está ruta.
  // Aquí lo que estamos haciendo es usando nuestro testServer y lo único que estamos cargando
  // es está única ruta, así hacemos que el test sea especifico para esa ruta.

  const request = testServer(route);

  // teniendo estó ya podemos definir la situación que sería 
  describe('GET - /movies', function () {
    // debería responder con un status 200, recibe un callback con el done, 
    // que es para indicar cuando finalize el test
    it('should respond with status 200', function (done) {
      // aquí es donde hacemos nuestro assert, hacemos un request gracias a supertest
      // exactemente que cuando llamos a nuestra api, y llamamos expect(200, done)
      request.get('/api/movies/').expect(200, done);
    });
  });
});
```

Ahora vamos a hacer una pequeña prueba corriendo esté test, par ello lo que vamos a hacer es configurar un script donde podamos correr los test.

Esté test llamará a mocha y como esta en la carpeta de test y los archivos finalizan en **.test.js** debería ser capaz de leerlos sin problema, y si nos damos cuenta nuestro test está pasando sin problema.

Vamos a escribir otro test, esté test que vamos a escribir, es el test que nos va edificar que responda con la lista de peliculas.

```js
// test que nos responde con la lista de las peliculas, el truco está que nosotros debemos 
    // asegurar que nuestras rutas estén devolviendo los datos como deberían ser, 
    it('should respond with the list of movies', function (done) {
      // acá cambia un poco la manera en como lo hacemos, porque sería igual, la misma petición 
      // pero en vez de llamar el expect, finalizamos está petición, la cual tiene un callback,
      // que recibe un error-first y  el response
      request.get('/api/movies/').end((err, res) => {
        // acá llamamos al assert, el cual debería ser exactamente igual 
        // queremos corroborrar cual fue la respuesta del body, debería traer las movies
        assert.deepEqual(res.body, {
          // debería ser igual a data y el mensaje
          data: moviesMock,
          message: 'movies listed'
        });

        // done sirve para que el test se de cuenta, cuando finalizo, como estó
        //  tiene un callback tenemos que decirle que el test finalizo acá
        // si no lo pasamos el test nuca sabra cuando finaliza y le dara un timeout.
        done();
      }) 
    });
```
Si volvemos a correr nuestros test y funcionará bien si los mensajes de los test son iguales a de las rutas.

Los Test son muy importante hacerlos en el código, porque si en un futuro hacen cambios, el test nunca se rompan, por ejemplo si en un futuro por alguna razón, llegarán y sin ninguna intención, cambiarán el mensaje que sería un error, si corremos nuestros test nos van a fallar y nos va a decir que no es exactamente igual.

**Los test son una buena manera de poder asegurar que nuestro código tiene calidad y que si en el futuro hay cambios, no se va a poder romper nuestro código**.