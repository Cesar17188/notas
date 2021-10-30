# Implementación de plugin de Ads: Desplegando en consola

La lista

```
const ALL_ADS: Ad[] = [
  {
    imageUrl:
      'https://static.platzi.com/media/achievements/badge-profesional-javascript-13538df2-24ce-433f-9aa6-e34eed608e70.png',
    title: 'Curso Profesional de JavaScript',
    body:
      'Mejora tus habilidades en Javascript. Conoce Typescript y cómo puedes ocuparlo para mejorar el control de tus variables.',
    url: 'https://platzi.com/cursos/javascript-profesional/',
  },

  {
    imageUrl:
      'https://static.platzi.com/media/achievements/badge-frontend-developer-8a49e681-3e22-408d-b886-2f47dfc9953a.png',
    title: 'Curso de Frontend Developer',
    body:
      'Domina las bases de HTML y CSS. Define la arquitectura de tu código y construye un sitio web usando componentes estáticos. ',
    url: 'https://platzi.com/cursos/frontend-developer/',
  },

  {
    imageUrl:
      'https://static.platzi.com/media/achievements/badge-backend-node-8e6aa8a9-f7cd-42b7-bf4a-e1ee916a942b.png',
    title: 'Curso de Backend con Node.js',
    body:
      'Crea aplicaciones backend utilizando Node.js, Express y Mongo. Entiende cómo funciona Javascript en un servidor y escribe aplicaciones con Node.js.',
    url: 'https://platzi.com/cursos/backend-nodejs/',
  },

  {
    imageUrl:
      'https://static.platzi.com/media/achievements/badge-prework-da6b0493-9908-40f3-ad53-f5d330b995b8.png',
    title:
      'Comienza tus proyectos de desarrollo para JavaScript configurando un entorno de desarrollo cómodo y adaptado a tus necesidades.',
    body:
      'Mejora tus habilidades en Javascript. Conoce Typescript y cómo puedes ocuparlo para mejorar el control de tus variables.',
    url: 'https://platzi.com/cursos/prework/',
  },

  {
    imageUrl:
      'https://static.platzi.com/media/achievements/badge-autenticacion-passport-6d45426a-2b24-4757-8927-7bfaf54529dd.png',
    title: 'Curso de Autenticación con Passport.js',
    body:
      'Genera estrategias de autenticación Sign-In y Sign-Out usando Passport.js. Agrega autenticación con Facebook, Twitter y Google a tus desarrollos.',
    url: 'https://platzi.com/cursos/passport/',
  },

  {
    imageUrl:
      'https://static.platzi.com/media/achievements/badge-backend-frontend-02b2ac18-331a-4959-85bf-0bd3c2aa009c.png',
    title: 'Curso de Backend for Frontend',
    body:
      'La ingeniería de software evoluciona día a día, no te quedes atrás. Ahora que eres un Desarrollador FullStack JavaScript necesitas evolucionar con el software, construye arquitecturas de software modernas.',
    url: 'https://platzi.com/cursos/bff/',
  },

  {
    imageUrl:
      'https://static.platzi.com/media/achievements/badge-react-adec89d0-1c35-4c9c-847e-18c284dc79dd.png',
    title: 'Curso Práctico de React JS',
    body:
      'React es una de las librerías más utilizadas hoy para crear aplicaciones web. Aprende a través de la creación de la interfaz de PlatziVideo todo lo que necesitas para crear increíbles componentes con React.      ',
    url: 'https://platzi.com/cursos/react-ejs/',
  },

  {
    imageUrl:
      'https://static.platzi.com/media/achievements/badge-react-redux-2ca3c0a5-fc53-437f-bfba-69e9ddd5a803.png',
    title: 'Curso de React Router y Redux',
    body:
      'Aprende de forma práctica a implementar React Router para manejar rutas en tus proyectos de frontend como un profesional.',
    url: 'https://platzi.com/cursos/react-router-redux/',
  },
];```
```

## Array.prototype.pop()

-   Idiomas
-   Seguir

El método `**pop()**` elimina el **último** elemento de un array y lo devuelve. Este método cambia la longitud del array.

## Sintaxis

```
arr.pop()
```

## Valor devuelto[

El elemento que ha sido eliminado del array; [`undefined`](https://developer.mozilla.org/es/docs/Web/JavaScript/Referencia/Objetos_globales/undefined "La propiedad global undefined representa el valor primitivo undefined. Es uno de los valores primitivos de JavaScript.") si el array está vacío.

## Descripción

El método `pop` elimina el último elemento de un array y devuelve su valor al método que lo llamó.

`pop` es intencionadamente genérico; este método puede ser [called](https://developer.mozilla.org/es/docs/Web/JavaScript/Referencia/Objetos_globales/Function/call "El método call() llama a una función con un valor this asignado y argumentos provistos de forma individual.") o [applied](https://developer.mozilla.org/es/docs/Web/JavaScript/Referencia/Objetos_globales/Function/apply "El método apply() invoca una determinada función asignando explícitamente el objeto this y un array o similar (array like object) como parámetros (argumentos) para dicha función.") en objectos similares a un array. En objetos que no contengan una propiedad `length`, que refleje su forma en una serie de propiedades numéricas consecutivas en base cero, puede no comportarse de manera significativa.

Si se llama a `pop()` en un array vacío, devuelve [`undefined`](https://developer.mozilla.org/es/docs/Web/JavaScript/Referencia/Objetos_globales/undefined "La propiedad global undefined representa el valor primitivo undefined. Es uno de los valores primitivos de JavaScript.").

## Ejemplos

Eliminando el último elemento de un array.  
El siguiente código crea el array `myFish`, que contiene cuatro elementos, a continuación, elimina su último elemento.

```js
var myFish = ['angel', 'clown', 'mandarin', 'sturgeon'];

var popped = myFish.pop();

console.log(myFish); // ['angel', 'clown', 'mandarin' ] 

console.log(popped); // 'sturgeon'
```