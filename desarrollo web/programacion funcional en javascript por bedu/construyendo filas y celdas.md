# Proyecto: Construyendo filas y celdas
main.js
```js
const tableRowTag = tag('tr');
// const tableRow = items => tableRowTag(tableCells(items));
const tableRow = items => compose(tableRowTag, tableCells)(items);

const tableCell = tag('td');
const tableCells = items => items.map(tableCell).join('');
```