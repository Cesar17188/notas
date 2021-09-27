# Agregando un comando para coverage

Los Test son muy importantes, pero también es muy importante asegurarnos que estamos probando todos los caminos de una funcionalidad a la hora de hacer test, un comando de **coverage** nos permite identificar en donde estamos fallando y como los podemos corregir.

Para correr nuestro reporte de covegare, lo primero que tenemos que hacer es instalar una nueva herrmienta que se llamá **nyc**. `npm i -D nyc` **nyc**: hace parte de una herramienta llamada [istabul](https://istanbul.js.org/). Luego lo que necesitamos crear es nuestro comando el `packages.json`

```js
{
    "scripts": {
      // El coverast se hace a partir de los test que hallamos creado. con esto
      //  estamos aplicando el coverast sobre nuestro comando de test
    "cover": "nyc npm run test",
// Estás herramientas nos ayudan a crear diferentes reportes, en esté caso
// quiero que me abra el resporte en mi navegador.
    "report": "nyc report --reported=html && open coverage/index.html"
  },
}
```
Estás herramientas nos ayudan a generar diferentes reportes, sean para **environments** de integración continua o sea para nuestros ojos, en esté caso vamos a crear un reporte que va ha estár en html.

Lo otro que debemos hacer es configurar como queremos hacer nuestro coverage, para ello nos vamos al final de nuestro `package.json`, y decimos que para ncy lo que queremos que testee es:
```js
{
  "nyc": {
    "all": true,
    "include": ["routes", "services", "lib", "utils"]
  }
}
```
Estó es muy importante porque nos ayuda a vizualizar el nivel de covertura de nuestra aplicación, en el equipo se puede definir un **minimo aceptable**, **la recomendación** de minimo aceptable **es entre 60 y el 80%** porque tiene poco sentido obsecionarse por obtener el 100%, porque **es mucho más importante crear producto que simplemente estar creando test**.

En esté modulo podimoss vizualizar:

-   Como crear test para nuestros endpoints, servicios y utilidades.
-   Agregando un comando para coverage
-   Debuggin inspect

Challenge: Termina el resto de los test de las rutas, servicios y utilidades.

**Hacer test puede ser mucho más complicado que incluso estár escribiendo código pero te recomiendo que tengas mucha pasiencia**.