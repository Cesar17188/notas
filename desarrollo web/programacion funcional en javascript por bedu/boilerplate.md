# Boilerplate: Base para el proyecto del curso
HTML
``` html
<!doctype html>
<html>
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1, shrink-to-fit=no">
  <link rel="stylesheet" href="https://use.fontawesome.com/releases/v5.6.3/css/all.css" integrity="sha384-UHRtZLI+pbxtHCWp1t77Bi1L4ZtiqrqD80Kn4Z8NTSRyMA2Fd33n5dQ8lWUE00s/" crossorigin="anonymous">
  <link rel="stylesheet" href="css/bootstrap.min.css">
  <link rel="stylesheet" href="css/main.css">
  <title>Calories Counter</title>
</head>
<body>
  <div class="container">
    <div class="row justify-content-center container-counter">
      <div class="col-md-9 container-counter--column">
        <div class="card my-5 bg-light text-center">
          <div class="card-header">
            <h1 id="header">Calories Counter</h1>
          </div>
          <div class="card-body">
            <table class="table table-hover">
              <thead>
                <tr>
                  <th scope="col">Description</th>
                  <th scope="col">Calories</th>
                  <th scope="col">Carbs</th>
                  <th scope="col">Protein</th>
                  <th></th>
                </tr>
              </thead>
              <tbody>
              </tbody>
              <thead class="thead-light">
                <tr>
                  <th>Totals</th>
                  <th>0</th>
                  <th>0</th>
                  <th>0</th>
                  <th></th>
                </tr>
              </thead>
            </table>
          </div>
          <div class="form-container">
            <form action="javascript:void(0)">
              <div>
                <input type="text" name="description" id="description" placeholder="Description">
                    <input type="number" min="0" name="calories" id="calories" placeholder=" Calories">
                    <input type="number" min="0" name="carbs" id="carbs" placeholder="Carbs">
                    <input type="number" min="0" name="protein" id="protein" placeholder="Protein">
              </div>
              <button class="add" id="add">
                +
              </button>
            </form>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>

  <script src="js/jquery-3.3.1.min.js"></script>
  <script src="js/bootstrap.min.js"></script>
  <script src="js/main.js"></script>
</body>
</html>
```

CSS
```css
:root {
    --background: #e9ecef;
    --border: #dee2e6;
    --black: rgb(50, 50, 50);
    --invalid: red;
    --button-default: gainsboro;
    --remove-hover: red;
    --ok: dodgerblue;
    --edit:limegreen ;
    --button: dodgerblue;
    --button-hover: rgb(28, 125, 221);
}

* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

html {
    font-size: 62.5%;
}

body, h1 {
    font-family: Arial, Helvetica, sans-serif;
    color: var(--black);
}

.container-counter {
    height: 80vh;
}

.container {
    border-radius: 1rem;
    margin: auto;
    margin-top: 10rem;
    overflow: hidden;
    max-width: 100rem;
    border: 1px solid var(--border);
}

.container-counter--column {
    height: 80%;
}

/* .my-5 {
    height: 80%;
} */
[class*=-container] {
    padding: 2rem;
}

#header {
    text-align: center;
    font-size: 4rem;
    background-color: var(--background);
    border-bottom: 1px solid var(--border);
    padding: 1rem;
}

table {
    text-align: center;
    width: 100%;
}

table th{
    font-size: 1.2rem;
}

table, th, td {
    border-bottom: 1px solid var(--border);
    border-top: 1px solid var(--border);
    border-collapse: collapse;
    padding: 0.75rem
}

#total {
    font-weight: bold;
}

tbody tr:nth-child(odd) {
    background-color: var(--background);
    border-spacing: 1rem;
}

.form-container {
    background-color: var(--background);
    border-top: 1px solid var(--border);
}

.form-container form {
    display: flex;
    flex-wrap: wrap;
    justify-content: space-between;
}

input {
    border: var(--border);
    border-radius: 5px;
    font-size: 1rem;
    padding: 0 0.5rem;
    margin: 0.25rem;
    height: 2em;
    transition: 0.3s;
}

table input {
    width: 100px;
    text-align: center;
    color: var(--black);
    -webkit-appearance: none;
    -moz-appearance: textfield;
    background: transparent;
}

table input.enabled {
    background: white;
    /* box-shadow: 0 2px 5px var(--edit); */
    -webkit-appearance: scrollbartrack-vertical;
    -moz-appearance: scrollbartrack-vertical ;
}

.form-container div input:focus  {
    box-shadow: 0 0 10px var(--ok);
}

.form-container div input:invalid,
.form-container div input.is-invalid,
table input.is-invalid  {
    box-shadow: 0 0 10px var(--invalid);
}

button {
    margin: 0.25rem;
    border: none;
    border-radius: 5px;
    color: white;
    font-weight: bold;
    height: 2rem;
    width: 2rem;
    cursor: pointer;
    transition: 0.3s;
}

button:hover{
    transform: scale(1.2);
}

button:active{
    transform: scale(0.8);
}

button.add {
    background-color: var(--button);
}

button.remove::before{
    content: "X";
}

button.remove {
    background-color: var(--button-default);
}
  
button.remove:hover {
    background-color: var(--remove-hover);
}

button.edit::before{
    content: "MOD";
}

button.edit {
    width: max-content;
    background-color: var(--button-default);
}

button.edit:hover {
    background-color: var(--edit);
}
```

JS
```js
const compose = (...functions) => data =>
  functions.reduceRight((value, func) => func(value), data)
```
