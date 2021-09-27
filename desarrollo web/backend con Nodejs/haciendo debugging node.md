# Haciendo _debugging_

Para aprovechar por completo la funcionalidad de _debugging_ que implementa Express, lo que recomiendo es cambiar todos los `console.log` por `debug` haciendo uso de un _namespace_ de la siguiente forma:

```javascript
const debug = require("debug")("app:server");
debug("Hello debug");
```

De esta manera si ejecutamos nuestra aplicación con el comando `DEBUG=app:* node index.js` nos mostrará los diferentes logs.

Los _namespaces_ que recomiendo son los siguientes:

-   **app:server** para todo lo relacionado con el inicio del servidor como el mensaje `Listening on http://localshost`
-   **app:db** para todo lo relacionado con _logs_ de las bases de datos, inicialización y ejecución de _scripts_.
-   **app:error** para todo lo relacionado con errores en nuestra aplicación.

> Nótese que esta convención es opcional, es decir, tu puedes seleccionar cualquier _namespace_. Lo más importante es que sea el mismo que se pasará en la opción **DEBUG**.

Express.js por defecto ya trae unos _logs_ de _debugging_ por defecto los podemos activar mediante la variable de entorno `DEBUG=express:*`.

Por lo que recomiendo los _scripts_ en nuestro archivo `package.json` de la siguiente manera:

```javascript
  "scripts": {
    "dev": "DEBUG=express:*,app:* nodemon index",
    "debug": "DEBUG=express:*,app:* npm run start",
  },
```

## Ejecutando el modo _inspect_ en desarrollo

El modulo `inspect` de Node.js nos permite ejecutar un ambiente para hacer _debugging_ de código haciendo uso de la consola de desarrolladores de Google. Para ejecutarlo en modo desarrollo con `nodemon` basta con agregar el flag `--inspect` por lo que recomiendo el siguiente script en nuestro archivo `package.json`

```javascript
  "scripts": {
    "inspect": "DEBUG=express:*,app:* nodemon --inspect index"
  },
```