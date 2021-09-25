# Implementando Boom

En esta sección aprenderemos a como podemos implementar Boom en nuestro código de express. Lo que haremos será usar boom en nuetros errorsHandlers que definimos con anterioridad, también aprovecharemos para crear nuestro error `404` de tal manera que _cuando hagan un **request** a un **endpoint** que no existe, respondamos correctamente_, te mostraré como hacerlo en el codigó.

1.  primero necesitamos instalar Boom `npm i @hapi/boom`
2.  Nos diponemos a ir a nuestro middleware manejador de errores, en el vamos a incluir la dependecia de boom.

```js
const boom = require('@hapi/boom');
```
3.  Como ya nos va a llegar un error boom, vamos a hacer un [spread-operator](https://developer.mozilla.org/es/docs/Web/JavaScript/Referencia/Operadores/Spread_operator) al error porque ahora el error no solo trae el mensaje, si no que trae unas propiedades como vimos, el **error, statusCode y message**, entonces es necesario hacer esté pequeño cambio
4.  Crearemos un tercer middleware que se llamará **wrapErrors()** porque es posible que en algún punto el error que nos llegué no sea de tipo boom y nosotros queremos que apartir de ahí todos los errores tengan la estructura boom.

```js
function wrapErrors(err, req, res, next) {
  // Es posible que el error que nos llegue no sea de tipo Boom,
  // nosotros queremos que apartir de ahi todos los errores tengan la estructura boom
  if (!err.isBoom) {
    next(boom.badImplementation(err));
  }
  // Si el error que estamos pasando por acá es de tipo boom, 
  // llamamos al siguiente middleware con el error
  next(err);
}
```
5.  Ahora apartir del error que ya va a ser de tipo boom, debemos sacar el output:

```js
function errorHandler(err, req, res, next) { // eslint-disable-line
  // Apartir del error que ya va ha ser de tipo boom debemos sacar el output, 
  // es la manera como le da menejo boom y ahoi podemos sacar el status code del error y el payload
  const { output: { statusCode, payload } } = err;
  // ahora no necesitamos manejar error.status, sino simplemente statusCode
  res.status(statusCode);
  // acá en lugar de pasar el error message pasamos el payload 
  res.json(withErroStack(payload, err.stack));
}
```
6.  Ahora tenemos que exportar wrapErrors
7.  Ahora lo que debemos hacer es actualizar nuestro archivo index el middleware, en esté caso lo que debemos hacer es ponerlo antes errorHandler.
8.  Otra cosa que debemos hacer es ir al validationHandler y donde estabamos devolviendo un error, es devolver un error de Boom

```js
// Para devolver un error de Boom, requerimos boom
const boom = require('@hapi/boom');
/*
....
*/
function validationHandler(schema, check = "body") {
  return function (req, res, next) {
    const error = validate(req[check], schema);
    // Estó nos va a devolver un error de que los datos no son validos
    error ? next(boom.badRequest(error)) : next();
  }
}
```
También vamos a crear un middleware para menejar los erroes `404`, el cual vamos a llamar `notFoundHandler.js`.

```js
const boom = require('@hapi/boom');

function notFoundHandler(req, res) { // eslint-disable-line
  const { output: { statusCode, payload } } = boom.notFound();

  res.status(statusCode).json(payload);
}
```

Está función es un **middleware** pero no recibe el next, porque para que pueda funcionar, lo más importante es que estó debe ir al final de las rutas, el `notFound` lo que hace es que se ejecuta cuando ya paso por todas las rutas

Ahora solo lo requerimos en nuestro archivo index y lo agregamos al final de las rutas.

```js
// routes
moviesApi(app);

// Catch 404
app.use(notFoundHandler);
```

Ahora si intentamos hacer una llamada con una ruta inexistente nos marcará el error 404 de Boom.
