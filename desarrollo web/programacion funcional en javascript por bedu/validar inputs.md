# Proyecto: Validar inputs

JS
```js
  description.keypress(() => {
    description.removeClass('is-invalid');
  });

  calories.keypress(() => {
    calories.removeClass('is-invalid');
  });

  carbs.keypress(() => {
    carbs.removeClass('is-invalid');
  });

  protein.keypress(() => {
    protein.removeClass('is-invalid');
  });


  const validateInputs = () => {
    description.val() ? '' : description.addClass('is-invalid');
    calories.val() ? '' : calories.addClass('is-invalid');
    carbs.val() ? '' : carbs.addClass('is-invalid');
    protein.val() ? '' : protein.addClass('is-invalid');

    if(description.val() && description.val() && carbs.val() && protein.val()) {
      console.log('Ok');
    }
  }
```

html
```html
<button class="add" id="add" onclick="validateInputs()">
                +
              </button>
```
