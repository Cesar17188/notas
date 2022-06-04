# El problema de CORS

[CORS](https://developer.mozilla.org/en-US/docs/Web/HTTP/CORS)


Funciona para habilitar dominios y que permitan la comunicación con la api desde varios dominios. Es realmente fundamental que se habiliten los dominios para que la base de datos pueda enviar y recibir información de dominios cruzados.

En desarrollo se puede habilitar un archivo proxy para comunicarse con el dominio.

proxy.config.json
```json
{

 "/api/*": {

 "target": "https://young-sands-07814.herokuapp.com",

 "secure": true,

 "logLevel": "debug",

 "changeOrigin": true

 }

}
```
package.json
```json
 "scripts": {

 "ng": "ng",

 "start": "ng serve",

 "start:proxy": "ng serve --proxy-config ./proxy.config.json",

 "build": "ng build",

 "watch": "ng build --watch --configuration development",

 "test": "ng test",

 "lint": "ng lint"

 },
 ```

para correr con el nuevo proxy
```npm
npm run start:proxy
```

