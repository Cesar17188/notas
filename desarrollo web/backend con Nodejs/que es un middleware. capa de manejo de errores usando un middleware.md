# ¿Qué es un middleware? Capa de manejo de errores usando un middleware

Un **middleware** es una pieza de software que está en medio de otras 2, se le suele describir como **software glue**, es decir pegamento de software y es porque nos ayuda a conectar otras piezas de software, pensemos por un momento en la población y en el agua, que es un recurso natural, si queremos que esté recurso natural llegue a la población deberíamos insertar en el medio, en esté caso un middleware que sería un sistema de tuberias, el sistema de tuberías nos permite conectar el agua a la población, pero nosotros podemos seguir agregando middlewares, podemos agregar un middleware que se encargue de purificar el agua y luego podríamos poner otro middleware que se encargue de contar el consumo del agua.

**En express** especificamente, la manera en como funcionan los **middlewares** es mediante la firma del: **request-object, response-object y la funcionalidad next**.

![[Pasted image 20210904181129.png]]

nosotros hemos visto algo muy similar en nuestro código: **el req, res y la funcionalidad next**, lo que nos permite es que en el middleware podemos hacer cualquier ejecución de código, _podemos modificar el request-object, podemos modificar el response-object_ y la manera en como llamamos al siguiente middleware es a travez de la funcionalidad next, si por alguna razón le pasamos un párametro a la funcionalidad next, se ejecutan los middlewares de error.

Nosotros lo que vamos a hacer como ejemplo del mundo real es, crear toda una capa de manejo de errores de un middleware, pero **los middleware en next del formato err, tienen una firma diferente, y es que en vez de recibir los 3 párametros, van a recibir un 4 párametros** que va a ser el `error`, de está manera podemos manipular el error y decir como lo imprimimos y llamar el next con un error o no para saber si llamamos nuestro siguiente middleware de manejo de error, te voy a enseñar como puedes hacerlo en tu código:

1.  En nuestra carpeta de utilidades vamos a crear una nueva carpeta que se llamará middleware.
2.  Creamos un archivo llamado `errorHandlers.js`
3.  Vamos a traer nuestro archivo de configuración porque dependiendo si estamos en modo desarrollo o modo producción, quiero que el error que nos imprima incluya el stack del error o no, recuerda que el stack es toda la configuración relaciona al error.
4.  Crearemos una funcion que va a ser nuestro middleware que se encargará de imprimir nuestros errores, el cual recibe: **err, req, res, next**.
5.  El otro middleware que vamos a crear es que nos va a ayudar a darle manejo al error, por defecto express, como imprime los errores es en formato html, como nosotros estamos implementando una api lo más necesario es que sean en formato JSON.
6.  Para poder determinar si agregamos el stack o no es crear otra función de ayuda, esto no es un middleware que se llamará _withErrorStack_, en ella vamos a recibir: **err, stack**

```js
const { config } = require('../../config/index');

function withErroStack(err, stack) {
  if (config.dev) {
    return {
      err,
      stack
    };
  }
  return err;
}

function logErrors(err, req, res, next) {
  console.log(err);
  next(err);
}

function errorHandler(err, req, res, next) { // eslint-disable-line
  res.status(err.status || 500);
  res.json(withErroStack(err.message, err.stack));
}

module.exports = {
  logErrors,
  errorHandler
};
```
Ahora vamos a ir a nuestro index y así como agregamos nuestro middleware del `bodyParser`, podemos agregar los `otros middlewares`.
```js
const express = require('express');
const app = express();

const { config } = require('./config/index');
const moviesApi = require('./routes/movies.js');

const { logErrors, errorHandler } = require('./utils/middleware/errorHandlers')

// middleware de bodyparser
app.use(express.json());

moviesApi(app);

// Los middlewares de error, siempre tienen que ir al final de las rutas, 
// las rutas también son middlewares
app.use(logErrors);
app.use(errorHandler);


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

De está manera podemos implementar una capa del manejo de errores usando un middleware en express, a continuación dejaremos una lectura de las capas de manejo de errores, en ella no solo sabrás como implementar la capa de manejo de errores para código asincrono, sino también para código sincrono.