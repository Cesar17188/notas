# Implementando Joi

En esté modulo vamos a implementar joi con nuestra capa de validación de datos.

1.  Necesitamos instalar **joi** como una dependencia `npm i @hapi/joi`
2.  Vamos a ir a nuestro middleware de validationHandler.
3.  Vamos a requerir joi. Recuerdan que teniamos la funcionalidad validate retornando false, ahora la vamos a implementar.

```js
const joi = require('@hapi/joi');

//* validate va a recibir la data que va a validar, y va a recibir un schema
function validate(data, schema) {
  // vamos a obtener un error en caso de que el schema no sea valido con la data
  // ANTIGUA IMPLEMENTACIÓN DE JOIN
  // const { error } = joi.validate(data, schema);

  // NUEVA IMPLEMENTACIÓN DE JOI ahora el schema valida la data
  const { error } = schema.validate(data, { errors: { stack: true } });
  return error;
}
```
4.  Ahora lo que debemos de hacer es crear el schema para nuestros datos, en esté caso vamos a crear un schema que valide la estrucutura de nuestras peliculas, como recuerdan en nuestro mock teniamos una serie de atributos, como el titulo, año, cover, etc. Entonces lo que debemos de hacer es crear un schema que por ejemplo:

-   A la hora de escribir un string tenga cierto tamaño o cierto minimo de tamaño y lo mismo para el resto de atributos.
-   Si vamos a ocupar en la duration numeros, tenemos que asegurarnos que sean números.
-   Si vamos usar una url debemos asegurarnos que sea una url.

5.  Para ello en nuestras utilidades vamos a crear una nueva carpeta que se a llamar schemas, para guardar nuestros esquemas.

```js
const joi = require('@hapi/joi');

// llamamos join.string para indicar que es un string
/**
 * llamamos regex porque los ids de mongodb tienen cierta estructura y es una muy buena
 * forma de validarlo mediante un regex, porque son una collection de caracteres alphanumericos
 * que tienen un minimo de 24 caracteres.
 * 
 * /^[0-9]: inicia con cualquiera de los caracteres alphanumericos del 0 al 9
 * /^[0-9a-fA-F]: de la a minuscula a la f minuscula, y de la A mayuscula a la F mayúscula
 * /^[0-9a-fA-F]{24}$/: puede tener un tamaño de 24 y así es com debe terminar.
 */

const movieIdSchema = joi.string().regex(/^[0-9a-fA-F]{24}$/);
const movieTitleSchema = joi.string().max(80);
const movieYeartSchema = joi.number().min(1888).max(2077);
const movieCoverSchema = joi.string().uri();
const movieDescriptionSchema = joi.string().max(300);
const movieDurationSchema = joi.number().min(1).max(300);
const movieContentRatingSchema = joi.string().max(5);
const movieSourceSchema = joi.string().uri();
const movieTagsSchema = joi.array().items(joi.string().max(50))

const createMovieSchema = {
  title: movieTitleSchema.required(),
  year: movieYeartSchema.required(),
  cover: movieCoverSchema.required(),
  description: movieDescriptionSchema.required(),
  duration: movieDurationSchema.required(),
  contentRating: movieContentRatingSchema.required(),
  source: movieSourceSchema.required(),
  tags: movieTagsSchema
};

// Solo vamos a actualizar una parte de la pelicula
const updateMovieSchema = {
  title: movieTitleSchema,
  year: movieYeartSchema,
  cover: movieCoverSchema,
  description: movieDescriptionSchema,
  duration: movieDurationSchema,
  contentRating: movieContentRatingSchema,
  source: movieSourceSchema,
  tags: movieTagsSchema
}

module.exports = {
  movieIdSchema,
  createMovieSchema,
  updateMovieSchema
}
```
Ahora lo que debemos hacer es aplicar estos esquemas en nuestras rutas, para ello debemos ir a nuestras routes movies, y lo primero que debemos hacer es importar los schemas.

Inicialmente para el GET no le vamos a aplicar ninguna regla de validation, pero para el GET cuando recibe un id, es decir el especifico si lo vamos a hacer, primero traer nuestro validationHandler el cual también debemos de requerir.

Recuerden que nuestro **validationHandler** va a **recibir** un **schema** y también **va a recibir de donde va a sacar los datos**, por defecto va a sacarlo del body, pero en el caso del getMovieId lo vamos a sacar de los parametros porque el id viene de los parametros.

```js
 router.get("/:movieId", validationHandler(joi.object({ movieId: movieIdSchema }), 'params'), async function (req, res, next) { 
  //  .......
 }
```

Muy similar va ha ser para el post, el post en esté caso en vez de usar los parametros en esté caso va ha sacar del body, y va a sacar el _createMovieSchema_ fijense que el middleware lo vamos a poner entre la ruta y entre la definición de la ruta y así mismo nosotros podemos poner varios middleware como es el caso del PUT.

```js
 // create
  router.post("/", validationHandler(joi.Object(createMovieSchema)), async function (req, res, next) {
    // ....
  }
```

Porque el PUT no solo recibe el párametro si no que también recibe el cuerpo, primero podría validar el cuerpo y segundo podría validar el id, pero primero validaremos el id, aunque cualquiera de los 2 funciona en esté caso, que debería de venir en los párametros id y en el body debería venir la pelicula, en esté caso no es createMovie, sino seria updatedMovie.

```js
// PUT - actualizar
  router.put("/:movieId", validationHandler(joi.Object({ movieId: movieIdSchema }), 'params'), validationHandler(updateMovieSchema) ,async function (req, res, next) {
    // ....
  }
```
