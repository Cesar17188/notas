# OOCSS, BEM, SMACSS, ITCSS Y Atomic Design

Son metódologias de CSS para que nuestro código mantenga la comprensión y la mantenibilidad en el tiempo

## OOCSS

css orientado a objetos, separa el diseño del contenido

```html
<!DOCTYPE html>
<html lang="en">
<head>
 <meta charset="UTF-8">
 <meta http-equiv="X-UA-Compatible" content="IE=edge">
 <meta name="viewport" content="width=device-width, initial-scale=1.0">
 <title>Document</title>
</head>

<style>
 .globalwidth {
 width: 100%;
 }
 .header {
 }
 .footer {
 }
</style>

<body>
 <header class="header globalwidth">Header</header>
 <footer class="footer globalwidth"\>Footer</footer>
</body>
</html>
```

## BEM 
Block element modify. Separa los bloques elementos y modificadores en el ejemplo esta el bloque header, el elemento button y el modificador de color

```html
<body>
 <header class="header">
 <button class="header__button--red">RED</button>
 <button class="header__button--yellow">YELLOW</button>
 </header>
</body>
```

## SMACSS

arquitectura de CSS escalable y modular. Basada en 5 pasos. 
1. Separar nuestro CSS en componentes base. Que son los que vamos a estar utilizando constanmente en el arcivo
2. Layaut Que son elementos estaticos como el header y el footer
3. Modulo son componentes que estamos utilizando mas de una vez
4. Estados. Son los cambios conforme se interactue en la página web
5. Temas. Los temas son cambios totales en los estilos y colores de la página en su totalidad

## ITCSS
Triangulo invertido de CSS. Esta métodología divide los archivos de CSS en varias partes para que no se cobinen entre si. Esto es más o menos en 
- AJUSTES
- HERRAMIENTAS
- GENERICOS
- ELEMENTOS
- OBJETOS
- COMPONENTES 
- UTILIDADES

## Atomic Design
Es para lograr el css más escalable. Basado en un módelo átomo que crece conforme se van juntando