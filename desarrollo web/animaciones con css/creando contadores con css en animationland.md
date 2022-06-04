# Creando contadores con CSS en Animationland
**Counter CSS**

`counter-reset`: Crea o reinicia un contador.  
`counter-increment`: Incrementa un valor del contador.  
`content`: Inserta el contenido generado (debe usarse con un pseudoelemento).  
`counter()`: Función que agrega el valor de un contador a un elemento.

```html
<!DOCTYPE html>

<html lang="en">

<head>

 <meta charset="UTF-8">

 <meta http-equiv="X-UA-Compatible" content="IE=edge">

 <meta name="viewport" content="width=device-width, initial-scale=1.0">

 <title>Contadores</title>

 <style>

 body {

 counter-reset: game;

 }

 input:checked {

 counter-increment: game;

 }

 .total-count::after {

 content: counter(game);

 }

 </style>

</head>

<body>

 <ul>

 <li>

 <input type="checkbox">

 <div class="shield"></div>

 </li>

 <li>

 <input type="checkbox">

 <div class="shield"></div>

 </li>

 <li>

 <input type="checkbox">

 <div class="shield"></div>

 </li>

 <li>

 <input type="checkbox">

 <div class="shield"></div>

 </li>

 <li>

 <input type="checkbox">

 <div class="shield"></div>

 </li>

 <li>

 <input type="checkbox">

 <div class="shield"></div>

 </li>

 <li>

 <input type="checkbox">

 <div class="shield"></div>

 </li>

 <li>

 <input type="checkbox">

 <div class="shield"></div>

 </li>

 </ul>

 <h3 class="total-count">Score: </h3>

</body>

</html>
```