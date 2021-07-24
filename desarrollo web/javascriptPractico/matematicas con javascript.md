# reto: Matemáticas con javascript

## Código JS
```js
// Código del cuadrado

console.group("Cuadrados");

  

function perimetroCuadrado(lado) {

 return lado * 4;

}

  

function areaCuadrado(lado) {

 return lado * lado;

}

console.groupEnd();

  

// Código del triángulo

console.group("Triángulos");

  

function perimetroTriangulo(lado1, lado2, base) {

 return lado1 + lado2 + base;

}

  

function areaTriangulo(base, altura) {

 return (base * altura) / 2;

}

  

console.groupEnd();

  

// Código del círculo

console.group("Círculos");

  

//Diámetro

function diametroCirculo(radio) {

 return radio * 2;

}

  

//Pi

const PI = Math.PI;

  

//Circunferencia

function perimetroCirculo(radio) {

 const diametro = diametroCirculo(radio);

 return diametro * PI;

}

  

//Área

function areaCirculo(radio) {

 return PI * Math.pow(radio, 2);

}

  

console.groupEnd();

  

// Funciones de interacción con HTML

  

// Cuadrado

function calcularPerimetroCuadrado() {

 const input = document.getElementById("InputCuadrado");

 const value = input.value;

 const perimetro = perimetroCuadrado(value);

 alert(`El perímetro del cuadrado es ${perimetro}`);

}

  

function calcularAreaCuadrado() {

 const input = document.getElementById("InputCuadrado");

 const value = input.value;

 const area = areaCuadrado(value);

 alert(`El área del cuadrado es ${area}`);

}

  

// Triangulo

function calcularPerimetroTriangulo() {

 const input_1 = document.getElementById("InputTriangulo1");

 const value_1 = parseInt(input_1.value);

 const input_2 = document.getElementById("InputTriangulo2");

 const value_2 = parseInt(input_2.value);

 const base = document.getElementById("InputTrianguloBase");

 const value_base = parseInt(base.value);

  

 const perimetro = perimetroTriangulo(value_1, value_2, value_base);

 alert(`El perímetro del triangulo es: ${perimetro}`);

}

  

function calcularAreaTriangulo() {

 const base = document.getElementById("InputTrianguloBase");

 const value_base = base.value;

 const altura = document.getElementById("InputTrianguloAltura");

 const value_altura = altura.value;

  

 const area = areaTriangulo(value_base, value_altura);

 alert(`El área del triangulo es: ${area}`);

}

  

// Círculo

function calcularPerimetroCirculo() {

 const input = document.getElementById("InputRadio");

 const value = input.value;

 const perimetro = perimetroCirculo(value);

 alert(`El perímetro del círculo es ${perimetro}`);

}

  

function calcularAreaCirculo() {

 const input = document.getElementById("InputRadio");

 const value = input.value;

 const area = areaCirculo(value);

 alert(`El área del círculo es ${area}`);

}
```

## HTML
```html
<!DOCTYPE html>

<html lang="en">

  

<head>

 <meta charset="UTF-8">

 <meta http-equiv="X-UA-Compatible" content="IE=edge">

 <meta name="viewport" content="width=device-width, initial-scale=1.0">

 <link href="https://fonts.googleapis.com/css2?family=Mulish&display=swap" rel="stylesheet">

 <link rel="stylesheet" href="./styles.css">

 <title>Figuras Geométricas | Curso Práctico de JavaScript en Platzi</title>

</head>

  

<body>

 <header class="header">

 <h1 class="header_title">

 Figuras geométricas

 </h1>

 <p class="header_subtitle">Primer taller Curso práctico de JavaScript</p>

 </header>

  

 <div class="operaciones">

 <section class="operacion">

 <h2 class="operacion_title">Calcula el área y perímetro de un cuadrado</h2>

 <form class="operacion_formulario" action="">

 <img class="operacion_img" src="./image/cuadrado.png" alt="cuadrado">

 <label class="operacion_cuadrado_formulario_lado" for="InputCuadrado">

 Escribe cuánto mide cada lado de tu cuadrado

 </label>

 <input class="operacion_cuadrado_formulario_input_lado" id="InputCuadrado" placeholder="5"

 type="number">

 <div class="operacion_cuadrado_formulario_buttons">

 <button class="operacion_cuadrado_formulario_buttons_perimetro" type="button"

 onclick="calcularPerimetroCuadrado()">

 Calcular el perímetro

 </button>

 <button class="operacion_cuadrado_formulario_buttons_area" type="button"

 onclick="calcularAreaCuadrado()">

 Calcular el área

 </button>

 </div>

 </form>

 </section>

  

 <section class="operacion">

 <h2 class="operacion_title">Calcula el área y perímetro de un triángulo</h2>

 <form class="operacion_formulario" action="">

 <img class="operacion_triangulo_img" src="./image/triangulo.png" alt="triangulo">

 <div class="operacion_triangulo_formulario_inputs">

 <label class="operacion_triangulo_formulario_lado" for="InputTriangulo1">

 Escribe cuánto mide cada lado 1 de tu triángulo

 </label>

 <input class="operacion_triangulo_formulario_input_lado" id="InputTriangulo1" placeholder="5"

 type="number">

 <label for="InputTriangulo2">

 Escribe cuánto mide cada lado 2 de tu triángulo

 </label>

 <input id="InputTriangulo2" placeholder="5" type="number">

 <label for="InputTrianguloBase">

 Escribe cuánto mide la base de tu triángulo

 </label>

 <input id="InputTrianguloBase" placeholder="5" type="number">

 <label for="InputTrianguloAltura">

 Escribe cuánto mide la altura de tu triángulo

 </label>

 <input id="InputTrianguloAltura" placeholder="5" type="number">

 </div>

 <div class="operacion_triangulo_formulario_buttons">

 <button type="button" onclick="calcularPerimetroTriangulo()">

 Calcular el perímetro

 </button>

 <button type="button" onclick="calcularAreaTriangulo()">

 Calcular el área

 </button>

 </div>

 </form>

 </section>

  

 <section class="operacion">

 <h2 class="operacion_title">Calcula el área y perímetro de un círculo</h2>

 <form class="operacion_formulario" action="">

 <img class="operacion_img" src="./image/circulo7.png" alt="circulo">

 <label class="operacion_cuadrado_formulario_lado" for="InputRadio">

 Escribe cuánto mide el radio de tu círculo

 </label>

 <input class="operacion_cuadrado_formulario_input_lado" id="InputRadio" placeholder="5" type="number">

 <div class="operacion_cuadrado_formulario_buttons">

 <button type="button" onclick="calcularPerimetroCirculo()">

 Calcular el perímetro

 </button>

 <button type="button" onclick="calcularAreaCirculo()">

 Calcular el área

 </button>

 </div>

 </form>

 </section>

 </div>

  

 <footer class="footer">

 <p class="footer_title">Operaciones</p>

 </footer>

  

 <script src="./figuras.js"></script>

</body>

  

</html>
```

## CSS
```css
body {

 padding: 0px;

 margin: 0px;

 font-family: "Mulish", sans-serif;

}

  

.header {

 background-color: #3b479d;

 color: white;

}

  

.header_title {

 margin: 0px;

 width: 95%;

 height: 45px;

 text-align: center;

}

  

.header_subtitle {

 margin: 10px 0px 0px;

 width: 95%;

 height: 30px;

 text-align: center;

 font-size: 14px;

}

  

.operaciones {

 display: flex;

 width: 100%;

 align-items: center;

 justify-content: center;

 flex-direction: column;

 min-height: calc(100vh - 200px);

 padding: 0px 30px;

 color: white;

 background: linear-gradient(#3b479d, #030708);

}

  

.operacion {

 width: 100%;

}

  

.operacion_title {

 margin: 0px;

 margin-left: -50px;

 width: 100%;

 text-align: center;

 padding-bottom: 20px;

}

  

.operacion_img {

 width: 100px;

}

  

.operacion_formulario {

 display: grid;

 grid-template-columns: 20% 20% 20% 20% 20%;

 grid-template-rows: 20% 20% 20% 20% 20%;

 justify-items: center;

 align-items: start;

 justify-content: space-between;

}

  

.operacion_cuadrado_formulario_lado {

 grid-row-start: 2;

 grid-column-start: 2;

}

  

.operacion_cuadrado_formulario_input_lado {

 grid-column-start: 3;

 grid-row-start: 2;

}

  

.operacion_cuadrado_formulario_buttons {

 grid-column-start: 4;

 grid-row-start: 2;

}

  

.operacion_triangulo_img {

 width: 100px;

 grid-row-start: 2;

 grid-column-start: 1;

}

  

.operacion_triangulo_formulario_inputs {

 grid-column-start: 2;

}

  

.operacion_triangulo_formulario_buttons {

 grid-column-start: 4;

 grid-row-start: 2;

 justify-content: center;

 align-items: center;

}

  

.footer {

 width: 100%;

 color: white;

 background: #030708;

}

  

.footer_title {

 margin: 0;

}

  

/*# sourceMappingURL=styles.css.map */
```