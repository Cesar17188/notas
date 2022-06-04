# Funciones compuestas o Function Composition

Conocemos como **Function Composition** a las funciones que obtenemos como resultado de combinar otras dos o más funciones, el resultado de cada función es el argumento de la siguiente y así sucesivamente.

main.js
```js

// convierne en string las clases que necesitemos en un tag html
const attrsToString = (obj = {}) => {
  const keys = Object.keys(obj);
  const attrs = []

  for (const element of keys){
    let attr = element;
    attrs.push(`${attr}="${obj[attr]}"`);
  }
  return attrs.join('');
}

// Crea un tag nuevo dentro de la estructura table html
const tag = t => content => `<${t}>${content}</${t}>`
```