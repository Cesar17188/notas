# Variables de entorno, CORS y HTTPS

### Como usar las variables de entorno para diferentes ambientes

Ya vimos cómo en nuestro ambiente local podemos hacer uso de las variables de entorno usando el archivo `.env` y la librería `dotenv.` Generalmente lo que se recomienda es usar el mismo para los diferentes ambientes como **Staging (Pruebas)** y **Producción**.

Para ello se debe acceder al servidor remoto:

1.  Duplicar el archivo `.env.example` y renombrarlo por `.env.`
2.  Cargar las respectivos valores de las variables de entorno.
3.  Usar valores y servicios diferentes para cada ambiente, esto quiere decir que las credenciales de desarrollo, staging y producción deben ser completamente diferente.
4.  Si se quiere tener un backup de estos valores se recomienda usar las notas seguras de aplicaciones como [1Password](https://1password.com/) o [LastPass](https://www.lastpass.com/es).

Como lo hemos dicho antes no se debe hacer commit del archivo `.env` y este debe estar en el `.gitignore`, ademas se recomienda manejar solo un archivo `.env`. Más información: [https://github.com/motdotla/dotenv#faq](https://github.com/motdotla/dotenv#faq)

## ¿Cuando no es posible acceder al servidor remoto?

Algunos servicios como [Heroku](https://www.heroku.com/) o [Now](https://zeit.co/home) no nos permiten acceder a un servidor remoto pues la administración del servidor es controlada por los mismos servicios, sin embargo cada servicio tiene sus mecanismos para establecer las variables de entorno:

-   [Configuración de variables de entorno en Heroku](https://devcenter.heroku.com/articles/config-vars)
-   [Configuración de variables de entorno en Now](https://zeit.co/docs/v2/serverless-functions/env-and-secrets)

### Variables de entorno de forma nativa

El uso del archivo .env junto con la biblioteca dotenv es un mecanismo que nos facilita la configuración de variables de entorno pero si por alguna razón las quisiéramos cargar de manera nativa, es decir desde el sistema operativo recomiendo este tutorial de [Digital Ocean](https://www.digitalocean.com/community/tutorials/how-to-read-and-set-environmental-and-shell-variables-on-a-linux-vps)

### Habilitando CORS en producción

El Intercambio de Recursos de Origen Cruzado (Cross-Origin Resource Sharing) es un mecanismo que agrega unos encabezados (Headers) adicionales HTTP para permitir que un user agent (generalmente un navegador) obtenga permisos para acceder a los recursos de un servidor en un origin distinto (dominio) del que pertenece.

**Por ejemplo una solicitud de origen cruzado seria** hacer una petición AJAX desde una aplicación que se encuentra en [https://dominio-a.com](https://dominio-a.com/) para cargar el recurso [https://api.dominio-b.com/data.json](https://api.dominio-b.com/data.json).

-   Por razones de seguridad, los navegadores restringen las solicitudes HTTP de origen cruzado iniciadas dentro de un script.

Si necesitamos permitir request desde un dominio diferente al del servidor podemos usar el middleware `cors` para permitirlo, pero es importante no dejarlo expuesto a todos los dominios.

## Habilitar CORS para todos los request (No recomendado en producción)

```js
const express = require("express");
const cors = require("cors");
const app = express();

app.use(cors());

app.get("/products/:id", function(req, res, next) {
  res.json({ msg: "This is CORS-enabled for all origins!" });
});

app.listen(8000, function() {
  console.log("CORS-enabled web server listening on port 8000");
});
```

## Habilitar CORS para los request específicos de un cliente (Recomendado para producción)

```js
const express = require("express");
const cors = require("cors");
const app = express();

const corsOptions = { origin: "http://example.com" };

app.use(cors(corsOptions));

app.get("/products/:id", function(req, res, next) {
  res.json({ msg: "This is CORS-enabled for only example.com." });
});

app.listen(8000, function() {
  console.log("CORS-enabled web server listening on port 8000");
});
```

Debemos tener en cuenta que para aplicaciones `server-side` es poco probable que necesiten el uso de CORS debido a que las aplicaciones conviven en el mismo dominio. Sin embargo, es buena practica habilitarlo para los llamados externos de nuestra API.

Más información sobre el middleware CORS en [https://expressjs.com/en/resources/middleware/cors.html](https://expressjs.com/en/resources/middleware/cors.html)

## Cómo funciona y por qué es importante el uso de HTTPS

El **Protocolo Seguro de Transferencia** de Hipertexto (HTTPS) es un protocolo HTTP que **funciona** en el puerto **443** y utiliza un **cifrado** basado en **SSL** (Secure Sockets Layer) / **TLS** (Transmission Layer security) con el fin de crear un canal de comunicación seguro entre el cliente y el servidor.

## Por qué usar HTTPS
Una de las razones por la cual siempre debemos usar sitios con HTTPS es que sin este cualquier individuo podría efectuar ataques conocidos como [man-in-the-middle](https://en.wikipedia.org/wiki/Man-in-the-middle_attack) o [eavesdropping](https://en.wikipedia.org/wiki/Eavesdropping) y obtener nuestro usuario y contraseña en el momento en que intentamos acceder a este servicio que no tiene HTTPS establecido.

### [](https://github.com/JasanHdz/backendnodejs/tree/master/notes#c%C3%B3mo-funciona)Cómo funciona

1.  El cliente envía un mensaje al servidor y este responde con su certificado público.
2.  El cliente comprueba que este certificado sea valido y toma la llave publica.
3.  El cliente genera una cadena llamada pre-master secret y la cifra usando la llave publica del servidor y se lo envía.
4.  El servidor usa su llave privada para comprobar el pre-master secret.
5.  En ese momento tanto el cliente como el servidor usan el pre-master secret para generar un master secret que es usado como una llave simétrica.
6.  Teniendo este par de llaves ya se pueden enviar mensajes seguros entre ellos.

### Cómo habilitar HTTPS en nuestro servidor

Dependiendo el servicio de hosting que estemos usando puede ofrecernos o no una instalación de certificados de seguridad SSL/TLS que pueden tener algún costo. Sin embargo existen servicios como [Let’s Encrypt](https://letsencrypt.org/) que permiten la instalación de este certificado completamente gratis. Servicios como Now y Heroku ofrecen HTTPS por defecto.

Más información:

-   [https://letsencrypt.org/how-it-works/](https://letsencrypt.org/how-it-works/)
-   [https://www.digitalocean.com/community/tutorials/how-to-secure-nginx-with-let-s-encrypt-on-ubuntu-16-04](https://www.digitalocean.com/community/tutorials/how-to-secure-nginx-with-let-s-encrypt-on-ubuntu-16-04)
-   [https://devcenter.heroku.com/articles/ssl](https://devcenter.heroku.com/articles/ssl)
-   [https://devcenter.heroku.com/articles/automated-certificate-management](https://devcenter.heroku.com/articles/automated-certificate-management)
-   [https://zeit.co/docs/v1/features/certs](https://zeit.co/docs/v1/features/certs)

