# Creando tu primer servidor con Express.js

empezaremos creando una carpeta llamada movies-api, aquí es donde vamos a construir todo el backend de nuestro proyecto.

Para comenzar un proyecto en express lo más recomendable es generar un package.json

```npm
npm init o npm init -y
```
Vamos a crear algunos scripts que nos serviran durante el desarrollo:

```
"dev": "DEBUG=app:* nodemon index"
"start": "NODE_ENV=production node index"
```
-   **DEBUG=app***: La variable de entorno debug me imprima todo lo que tenga el namespace de la aplicación.
    
-   **nodemon**: Nos permite que cada vez que hagamos un cambio en el servidor refresque automaticamente, de está manera no tengo que estar bajando y subiendo el código.
    
-   **NODE_ENV=producction**: Arrancar el proyecto en modo producción.
    
-   **node index**: arrancamos el proyecto con nodejs.
    

Como queremos usar una configuración de [eslint](https://github.com/JasanHdz/backendnodejs/blob/master/notes) bien interesante lo que vamos a hacer es crear un archivo _.eslintrc.json_ con la siguiente configuración:

```js
{
  // Todo mi código va a usar la versión de Ecmascript 2018 en adelante
  "parserOptions": {
    "ecmaVersion": 2018
  },
  // Vamos a extender la configuración de eslint recomendada y vamos a usar
  // una configuración compatible con prettier.
  "extends": ["eslint:recommended", "prettier"],
  "env": {
    // Vamos a usar variables de entorno de EcmaScript 6
    "es6": true,
    // Vamos a usar variables de entorno de Node
    "node": true,
    // Vamos a usar variables de entorno moca ¿Por qué?
    // Cuando lleguemos a la hora de hacer testsi utilizamos unas variables globales
    // eslint nos puede sacar un error, pero aqui le estamos especificando que son variables de moca
    "mocha": true
  }, 
  "rules": {
    // La regla de no-console: no va ha ser un error si no un warning 
    // porque aveces necesitamos dejarlo
    "no-console": "warn"
  }
}
```

Por otro lado vamos a configurar nuestro `Prettierrc.json`. [Prettier](https://github.com/JasanHdz/backendnodejs/blob/master/notes) es una configuración muy interesante que nos permite formatear nuestro código es decir:

Muchas veces hay problemas cuando un desarrollador formatea el código de una manera y otro desarrollador formatea el código de otra manera, esto suele ser bastante confunso y suele ser una perdida de tiempo en los call-review. **Prettier** se encargá de que todos los desarrolladores a la hora de hacer commit de su código sea igual, en este ejemplo pondremos algunas reglas, pero cada quien puede acomodarlo a su gusto.

```js
{
  "tabWidth": 2,
  "semi": true,
  "singleQuote": true
}
```

Teniendo esta configuración base lo que vamos a hacer es empezar a instalar nuestras dependencias: **express** para crear nuestro servidor también **dotenv**: sirve para cargar nuestras variables de entorno.

```
npm i express dotenv
```
Ahora vamos a instalar nuestras dependencias de desarrollo, estás dependencias a diferencia de las de producción, son dependencias que solo vamos a manejar acá, cuando nosotros desplegamos nuestra aplicación a producción, no instalamos nuestras dependencias de desarrollo, esto hace que el código sea más liviano en producción.

**devDependencies**:
```
npm i -D nodemon eslint eslint-config-prettier eslint-plugin-prettier prettier
```

Finalmente para que nuestro código haga el formateo automático cada vez que se hace commit y se sube al repositorio, vamos a instalar un hook, esto se instala solo mediante un comando que vamos a ver a continuación:

```
npx mrm lint-staged
```
Con esto el lint-staged automáticamente modifica nuestro packages.json y le dice mira cada vez que hagas un commit, vamos a coger todo el código y lo vamos a formatear con la configuración que hemos establecido de eslint y prettier, y lo vamos a subir nuestro repositorio.

Vamos a crear un nuevo archivo de configuración, es recomendable abstraerlo porque si el día de mañana estamos cargando nuestras variables de entorno de otra manera podemos hacerlo rápidamente haciendo el cambio solo a nuestro archivo de configuración, en esté caso vamos a hacer uso de [dotenv], más adelante vamos a entender que es, pero por ahora solo crearemos un archivo de configuración muy sencillo.
```js
require('dotenv').config();

const config = {
  dev: process.env.NODE_ENV !== 'production',
  port: process.env.PORT || 3000
}

module.exports = { config };
```
Ahora vamos a crear nuestro servidor en express

```js

const express = require('express');
const app = express();

const { config } = require('./config/index');

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

**Challenge**: Crear un servidor que detecte si el año es bisiesto:

```js
const express = require('express');
const app = express();

// Cuando hagamos un request de tipo GET 
app.get('/', (req, res) => {
  // Lo que vamos a enviar a pantalla
  res.send("Envianos el año en la url escribiendo '/año'");
})

app.get('/:year', (req, res) => {
  const year = req.params.year;
  if (year % 4 === 0 && year % 100 !== 0) {
    res.send(`El ${year} Es bisiesto`);
  } else {
    res.send(`Lo siento el año ${year} no es bisiesto :(`);
  }
})

app.listen(2000, function () {
  console.log('Litening http://localhost:2000');
})
```
