# Creación de tests para nuestras utilidades

Vamos a crear test para nuestras utilidades pero esta vez vamos a hacerlo haciendo uso de td, la técnica de **td** trata primero crear los test y luego la funcionalidad, personalmente considero que hay algunos casos que vale la pena usar **td**, por ejemplo cuando se tiene muy claro cuál es la lógica de negocio, si tu tienes muy clara la lógica de negocio, muy fácil puedes crear los test y luego solucionarlo en la funcionalidad, si no es claro la verdad no va a funcionar td para nada, otro caso donde **es muy común hacer td es cuando tienes un bug**, escribes un test que va a fallar porque existe el bug, corriges el bug y luego el test debería pasar, así aseguras que ese bug no va a volver a suceder porque ya tienes un test que lo impide, vamos a ver como se hace en el código. Lo que vamos a solucionar en esté caso es una utilidad que vamos a crear para que imprima los mesajes de nuestras rutas, recuerden que nosotros en nuestra ruta simpre devolvemos un mensaje.

Nosotros quisieramos automatizar estó, entonces vamos a crear una utilidad que haga eso, la cual vamos a llamar **buildMessage** y como estamos haciendo **td**, lo único que vamos a definir es el cuerpo de la utilidad, que en esté caso va a recibir una entidad, porque así lo definí en mi lógica de negocio, la cúal vamos a exportar. Por ahora está utilidad no hace nada, primero vamos a escribir los test y a media que vamos resolviendo los test es lo que nos va a determinar como solucionamos esa utilidad.

1.  En la carpeta test vamos crear un nuevo archivo llamado _utils.buildMessage.test.js_.

```js
function buildMessage(entity, action) {
  if (action === 'list') {
    return `${entity}s ${action}ed`;
  }
  return `${entity} ${action}d`;
}

module.exports = buildMessage;
```
Lo que vamos a definir en nuestros test es que cuando enviemos ciertos mensajes, obtengamos cierta respuesta.
```js
// nos permite verificar si el test es correcto o no.
const assert = require('assert');

const buildMessage = require('../utils/buildMessage');

// vamos a definir en nuestros test que cuando enviemos cierto mensaje obtengamos cierta respuesta.L0
describe.only('utils - buildMessage', function () {
  describe('When recieves an entity and acction', function () {
    it('should return the respective message', function () {
      const result = buildMessage('movie', 'create');
      const expect = "movie created";
      assert.strictEqual(result, expect);
    });
  });

  describe('when recives an entity and an action and is a list', function () {
    it('should return the respective message with the entity in plural', function () {
      const result = buildMessage('movie', 'list');
      const expect = 'movies listed';
      assert.strictEqual(result, expect);
    });
  });
});
```
Con esté ejemplo introductorio de TD, nos hemos dado cuenta como nos puede ayudar a hacer `refactori` de una forma mucho más segura, o incluso evitar que halla bugs en un futuro cuando por alguna razón sucede.