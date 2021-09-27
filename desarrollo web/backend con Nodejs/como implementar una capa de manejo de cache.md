# ¿Cómo implementar una capa de manejo de caché?

Lo primero que vamos a hacer es crear un archivo en utilidades llamado `time.js`, donde vamos a establecer unos tiempos.

```js
// el cache se mide en segundos
const FIVE_MINUTES_IN_SECONDS = 300;
const SIXTY_MINUTES_IN_SECONDS = 3600;

module.exports = {
  FIVE_MINUTES_IN_SECONDS,
  SIXTY_MINUTES_IN_SECONDS
};
```
Teniendo esos tiempos ahora puedo manejar mi utilidad menejo de cache, en la misma carpeta de utilidades, crearemos un archivo que se va llamar **cacheResponse.js**, importamos nuestra configuración porque una de las cosas más molestas de desarrollo es el cache activado, porque muchas veces estamos haciendo modificaciones en nuestro código y notamos que recibimos la misma respuesta y estó es culpa del cache.

Lo mas sano para el desarrollador es verificar si no tenemos el cache activado.

Para ello nuestra funcionalidad solo se va a ejecutar response, si no estamos en modo desarrollo. Le vamos a pasar el `response` porque es el que modificamos para agregar el cache, y los segundos que queremos aplicar.
```js
const { config } = require('../config/index');

function cacheResponse(res, seconds) {
  if (!config.dev) {
    res.set('Cache-Control', `public, max-age=${seconds}`);
  }
}

module.exports = cacheResponse;
```
Ahora debemos ir a nuestras rutas y agregarle cache a las rutas necesarias. **No todas las rutas deben tener cache** _las rutas que deben requerir cache deben ser las rutas en las que estamos requeriendo recursos_ Porque si vamos a crear un recurso, es decir una pelicula nueva, no debería de haber cache porque sucedio en ese momento. Pero si estamos requeriendo peliculas es posible que agregar peliculas sea un proceso que no sea inmediato, que lo hagá muy de vez en cuando, entonces tiene sentido dejar eso en el cache.

Lo que vamos a hacer es agregar cache solo a la lista de peliculas y cuando vamos a obtener una lista especifica.

```js
// Traer todas las peliculas
  router.get('/', async function (req, res, next) {
    cacheResponse(res, FIVE_MINUTES_IN_SECONDS);
    const { tags } = req.query;
  //  ... try{} catch(){}
  });

  // Obtener movie por id
  router.get(
    '/:movieId',
    validationHandler(joi.object({ movieId: movieIdSchema }), 'params'),
    async function (req, res, next) {
      cacheResponse(res, SIXTY_MINUTES_IN_SECONDS);
      const { movieId } = req.params;
      // try {} catch() {}
    }
  );
```
