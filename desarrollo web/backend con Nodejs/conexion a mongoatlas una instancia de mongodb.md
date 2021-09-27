# Conexión a MongoAtlas una instancia de MongoDB

Ya que tenemos nuestra cuenta en mongodb atlas nos disponemos a crear la conexión en nuestra aplicación.

1.  instalar el paquete `npm i mongodb`
2.  Vamos a crear 2 archivos: `.env.example` y el archivo `.env`

El archivo .env.example es necesario para que cualquier otro desarrollador que tome nuestro proyecto sepa que variables de entorno debe alimentar localmente, mientras que el archivo `.env` van a ser las variables de entorno y va a ser alimentada por el archivo de configuración, **esté nunca debe ser subido a base de datos, porque si no estamos exponiendo nuestras credenciales y cualquiera que tenga acceso al repositorio podría tomarlas**, ya se han problemas por situaciones como está.
```js
# CONFIG
PORT=3000
CORS=*


# MONGO
DB_USER=
DB_PASSWORD=
DB_HOST=
DB_NAME=
```
Ahora lo que hace falta es alimentar nuestro archivo de configuración con estás variables de entorno, lo que vamos a hacer es ir a nuestro archivo `.env.example` y copiar las variables de entorno, ir a nuestro archivo de configuración y agregarlas, las copiamos del `env.examples` para no borrar los valores y que fuera más sencillo.

archivo de configuración:
```js
require('dotenv').config();

const config = {
  dev: process.env.NODE_ENV !== 'production',
  port: process.env.PORT || 3000,
  cors: process.env.CORS,
  dbUser: process.env.DB_USER,
  dbPassword: process.env.DB_PASSWORD,
  dbHost: process.env.DB_HOST,
  dbName: process.env.DB_NAME
};

module.exports = { config };
```

Ya nuestro archivo de configuración tiene estas nuevas variables de entorno, entonces lo que vamos a hacer así como hemos echo con nuestra capa de rutas y nuestra capa de servicios, es crear una capa de librerías, en esté caso crearemos una carpeta que se llamará **lib**

En el lo que vamos a requerir es el cliente de mongo, eso lo hacemos ya con la **librería** que instalamos con anterioridad que es **mongodb** está librería es la oficial para conectarse a mongo, luego traemos nuestro archivo de configuración porque es desde ahí donde vamos a construir nuestra uri.

```js
const { MongoClient, ObjectId } = require('mongodb');
const { config } = require('../config');

// aquí vamos a crear las diferentes constantes
// encodeURIComponent nos garantizá que si por alguna razón hay algunos caracteres especiales
// no tengamos problemas a la hora de conectarnos.
const USER = encodeURIComponent(config.dbUser);
const PASSWORD = encodeURIComponent(config.dbPassword);
const DB_NAME = config.dbName;

// Ahora ya podemos comenzar a escribir nuestra uri de mongo
const MONGO_URI = `mongodb+srv://${USER}:${PASSWORD}@${config.dbHost}:${config.dbPort}/${DB_NAME}?retryWrites=true&w=majority`;
// mongodb+srv://db_user_platzivideos:<password>@cluster0-nnl4g.mongodb.net/test?retryWrites=true&w=majority
class MongoLib {
  constructor() {
    this.client = new MongoClient(MONGO_URI, { useNewUrlParser: true });
    this.dbName = DB_NAME;
  }

  connect() {
    // Usamos patron Singleton: la idea es que cada vez que nos conectemos a nuestra base de datos
    // no nos cree un nuevo cliente. Si no que si el cliente ya está y la conexión ya esta abierta, usemos esa misma conexión
    if (!MongoLib.connection) {
      MongoLib.connection = new Promise((resolve, reject) => {
        this.client.connect(err => {
          if (err) {
            reject(err);
          }

          console.log('Connected succesfully to mongo');
          resolve(this.client.db(this.dbName));
        });
      });
    }

    return MongoLib.connection;
  }
}
```