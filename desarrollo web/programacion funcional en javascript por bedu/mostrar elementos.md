# Proyecto: Mostrar elementos

main.js
```js

const add = () => {
    const newItem = {
      description: description.val(),
      calories: parseInt(calories.val()),
      carbs: parseInt(carbs.val()),
      protein: parseInt(protein.val())
    }
    list.push(newItem);
    cleanInputs();
    updateTotals();
    renderItems();
  }

  const renderItems = () => {
    $('tbody').empty();
    list.map(item => {
      $('tbody').append(tableRow([item.description, item.calories, item.carbs, item.protein]));
    })
  }
```