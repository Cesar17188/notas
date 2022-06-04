# Proyecto: Agregar elementos a la lista

agregarmos cambios al main.js

main.js
```js
const validateInputs = () => {
    description.val() ? '' : description.addClass('is-invalid');
    calories.val() ? '' : calories.addClass('is-invalid');
    carbs.val() ? '' : carbs.addClass('is-invalid');
    protein.val() ? '' : protein.addClass('is-invalid');
    if(description.val() && description.val() && carbs.val() && protein.val()) {
      add();
    }
  }


  const add = () => {
    const newItem = {
      description: description.val(),
      calories: parseInt(calories.val()),
      carbs: parseInt(carbs.val()),
      protein: parseInt(protein.val())
    }
    list.push(newItem);
    cleanInputs();
    console.log(list);
  }

  
  const cleanInputs = () => {
    description.val(''),
    calories.val(''),
    carbs.val(''),
    protein.val('')
  }
```