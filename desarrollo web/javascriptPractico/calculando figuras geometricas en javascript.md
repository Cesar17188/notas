# Calculando figuras geométricas en JavaScript

Utilizando el Teorema de Pitágoras para calcularla, ya que es un triángulo isósceles y conocemos la base y la altura. Esto funcionaria también con triángulos equiláteros.  
El código quedaría de la siguiente manera:  
const alturaTriangulo = Math.sqrt((base/2) * * 2 + 6 * * 2);

Les dejo también una foto para que se entienda mejor 😃

![Altura.png](https://static.platzi.com/media/user_upload/Altura-9a76f2e8-8c67-4590-adcf-f8bce134a811.jpg)

se puede incluir variables en el texto usando estas comillas `` y agregando la variable de este manera ${ladoCuadrado}

```js
const ladoCuadrado = 5;
console.log(`los lados de cuadrado miden ${ladoCuadrado}`)
```

## **Encapsula los console 😃**

```js
// Abres
console.group("nombre que desees");
// Se encapsulan todos los console.log en el grupo actual
// Cierras
console.groupEnd();
```

Ejemplo 
 
```js
// Código del cuadrado

console.group("Cuadrados");

const ladoCuadrado = 5;

console.log(`Los lados del cuadrado miden: ${ladoCuadrado} cm`);

  

const perimetroCuadrado = ladoCuadrado * 4;

console.log(`El perimetro del cuadrado es: ${perimetroCuadrado} cm`);

  

const areaCuadrado = ladoCuadrado * ladoCuadrado;

console.log(`El área del cuadrado es: ${areaCuadrado} cm^2`);

console.groupEnd();

  

// Código del triángulo

console.group("Triángulo")

const ladoTriangulo1 = 6;

const ladoTriangulo2 = 6;

const baseTriangulo = 4;

console.log(

 `Los lados del triángulo miden: ${ladoTriangulo1} cm, ${ladoTriangulo2} cm, ${baseTriangulo} cm`

);

  

console.groupEnd();
```