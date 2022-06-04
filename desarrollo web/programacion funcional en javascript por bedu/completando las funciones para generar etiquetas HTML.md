# Completando las funciones para generar etiquetas HTML

index.js
```js

const attrsToString = (obj = {}) => {
  const keys = Object.keys(obj);
  const attrs = []
  for (const element of keys){
    let attr = element;
    attrs.push(`${attr}="${obj[attr]}"`);
  }
  return attrs.join('');
}

const tagAttrs = obj => (content = '') =>
`<${obj.tag}${obj.attrs ? ' ' : ''}${attrsToString(obj.attrs)}>${content}</${obj.tag}>`

const tag = t => {
  if(typeof t === 'string') {
    tagAttrs({tag: t});
  } else {
    tagAttrs(t);
  }
}
```