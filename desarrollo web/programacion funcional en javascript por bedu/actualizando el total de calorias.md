# Proyecto: Actualizando el total de calorías

index.html
```html
<thead class="thead-light">
                <tr>
                  <th>Totals</th>
                  <th id="totalCalories">0</th>
                  <th id="totalCarbs">0</th>
                  <th id="totalProtein">0</th>
                  <th></th>
                </tr>
              </thead>
```

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
    console.log(list);
  }

  const updateTotals = () => {
    let calories = 0, carbs = 0, protein = 0;
    list.map(item => {
      calories += item.calories,
      carbs += item.carbs,
      protein += item.protein
    });
    $('#totalCalories').text(calories);
    $('#totalCarbs').text(carbs);
    $('#totalProtein').text(protein);
  }
```