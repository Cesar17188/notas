# Despliegue en Now

En está sección aprenderas a como desplegar tu aplicación en un servicio llamado now. [now](https://github.com/JasanHdz/backendnodejs/blob/master/notes) es un servicio serverless es decir no tenemos que preocuparnos en infraestructura, ya que a media que tu aplicación tiene cierta demanda, now se encarga de escalar la aplicación por nosotros.

Para hacer uso del servicio de now debemos ir a: [https://zeit.co/download](https://zeit.co/download)

Los más recomedable es descargar la aplicación de escritorio pues no solo nos muestra un menú donde podemos ver el status de nuestras descargas, sino que también nos descarga una utilidad de terminal.

La descarga es muy fácil pues NOW CLI se descarga usando `npm` o `yarn`. con npm `npm i -g now` con yarn `yarn global add now`

Ahora lo primero que tenemos que hacer es considerar nuestras variables de entorno, pues si instalamos nuestra aplicación si pasarselas al despliegue no van a tener ningún valor, lo que vamos a hacer es que las vamos a sacar de el archivo `.env`.

La manera en como now nos permite administrar nuestras variables de entorno, es mediante algó llamado secrets, `un secret lo que hace es guardar nuestra variable de entorno y nunca más nos deja acceder a ese resultado`, así podemos cuidarnos de que nadie venga nuestra máquina y nos saque el valor de la variable de entorno, la manera en como se hace es con `now secret add nombreVariableEntorno`, y así sucesivamente con todas nuestras variables de entorno.

El archivo `now.json` que usaremos para el despliegue quedaría de la siguiente manera:

```js
{
  "name": "platzivideo",
  "version": "2",
  "builds": [{"src": "index.js", "use": "@now/node"}],
  "routes": [{ "src": "/(.*)", "dest": "/index.js" }],
  "env": {
    "DB_USER": "@platzivideos-db-user",
    "DB_PASSWORD": "@platzivideos-db-password",
    "DB_HOST": "@platzivideos-db-host",
    "DB_NAME": "@platzivideos-db-name"
  }
}
```
Si al desplegar nuestra aplicación con now dev nos muestra un error cuando se conecta a la base de datos de mongo como:

`(node:414) DeprecationWarning: current Server Discovery and Monitoring engine is deprecated, and will be removed in a future version. To use the new Server Discover and Monitoring engine, pass option { useUnifiedTopology: true } to the MongoClient constructor. Connected succesfully to mongo` Tenemos que agregar el nuevo motor de descubrimiento al monitoreo del servidor. `{ useUnifiedTopology: true }`, lo hacemos de la siguiente manera:
```js
constructor() {
    this.client = new MongoClient(MONGO_URI, { useNewUrlParser: true, useUnifiedTopology: true });
    this.dbName = DB_NAME;
  }
```
Una vez hecho esto, podemos probar nuestra servidor usando now dev, para que lo ejecute de manera local, y escribimos solo now para enviar el servicio a producción, y cada vez que hallá cambios, solo volvemos a hacer now al proyecto.

--- 

Parece que ahora Now se llama Vercel, así que les dejo los pasos que seguí para hacer mi despliegue:

-   Instalar vercel globalmente: `npm i -g vercel`
-   Añadir las variables de entorno para conectarse a la bd de mongo a la lista de variables secretas de vercel:

```powershell
vercel secrets add platzivideos-db-user ...
vercel secrets add platzivideos-db-password ...
vercel secrets add platzivideos-db-host ...
vercel secrets add platzivideos-db-name ...
```

-   En vez de los `...` se deben colocar las variables de entorno respectivas (las mismas del archivo **_.env_**).
-   Talvez necesites crear una cuenta en Vercel ya que te pedirá un email cuando hagas esto.
-   Para ver las variables secretas guardadas (no se ven los valores): `vercel secrets ls`
-   Ahora añadimos un archivo **_vercel.json_** en la raíz del proyecto con el siguiente contenido:

```json
{
  "name": "platzivideo",
  "version": 2,
  "builds": [
    {
      "src": "index.js",
      "use": "@vercel/node"
    }
  ],
  "routes": [
    {
      "src": "/(.*)",
      "dest": "/index.js"
    }
  ],
  "env": {
    "DB_USER": "@platzivideos-db-user",
    "DB_PASSWORD": "@platzivideos-db-password",
    "DB_HOST": "@platzivideos-db-host",
    "DB_NAME": "@platzivideos-db-name"
  }
}
```

-   Antes de desplegar podemos probar la app con `vercel dev`. Una vez ejecutado este comando se nos preguntarán algunas cosas que podemos responder por defecto (dando enter y enter). Al final la aplicación quedará desplegada como si estuviera en producción pero localmente.
-   Si todo anda bien, hacemos el despliegue: `vercel`. El proceso tardará unos segundo y cuando finalice se mostrará la URL del proyecto ya desplegado.

Para configurar una URL más amigable: `vercel alias <url_actual> <alias>`

-   Para hacer esto es necesario que tengas acceso a la URL alias dentro de tu cuenta.  
    Aquí esta mi app desplegada [https://movies-api-silk.vercel.app/api/movies](https://movies-api-silk.vercel.app/api/movies)