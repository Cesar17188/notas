# Proyecto: Eliminar elementos

main.js
```js

// en la seccion de variables
const trashIcon = tag({tag: 'i', attrs: {class: 'fas fa-trash-alt'}})('');

// En la sección de funciones
 const renderItems = () => {
    $('tbody').empty();
    list.map((item, index) => {
      const removeButton = tag({
        tag: 'button',
        attrs: {
          class: 'btn btn-outline-danger',
          onclick: `removeItem(${index})`
        }
      })(trashIcon);
      $('tbody').append(tableRow([item.description, item.calories, item.carbs, item.protein, removeButton]));
    })
  }
  const removeItem = (index) => {
    list.splice(index, 1);
    updateTotals();
    renderItems();
  }
```