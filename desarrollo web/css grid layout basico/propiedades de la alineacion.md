# Propiedades de alineación

> Propiedades para la alineación de los items (elementos): ajusta los elementos de la grilla

-   Justify-items: alineación horizontal 
-   Align-items: alineación vertical
-   Place-items: alineación en ambas direcciones a la vez

> Propiedades para la alineación del container(El Contenedor): Ajusta la grilla completa

-   Justify-content: alineación horizontal
-   Align-content: alineación vertical
-   Place-content: alineación en ambas direcciones a la vez 

> Propiedades para la alineación de un solo item individual: son hijas del grid principal

-   Justify-self
-   Align-self
-   Place-self

```html
<!DOCTYPE html>

<html lang="en">

  

<head>

 <meta charset="UTF-8">

 <meta http-equiv="X-UA-Compatible" content="IE=edge">

 <meta name="viewport" content="width=device-width, initial-scale=1.0">

 <link rel="stylesheet" href="./style.css">

 <title>Document</title>

</head>

  

<body>

 <div class="contenedor">

 <div class="item-center">

 </div>

 <div class="item">

 <span></span>

 </div>

 <div class="item">

 <span></span>

 </div>

 <div class="item">

 <span></span>

 </div>

 <div class="item">

 <span></span>

 </div>

 </div>

</body>

  

</html>
```

```css
.contenedor {

 border: 1px solid #00cf00;

 background-color: #005c00;

 display: grid;

 grid-gap: 30px;

 grid-template-columns: 150px 150px;

 grid-template-rows: 150px 150px;

 height: 400px;

 place-content: center;

}

  

.item {

 border: 1px solid #00bcd4;

 font-size: 4rem;

 background-color: #40a540;

 display: grid;

 place-content: end;

}

  

.item span {

 display: block;

 width: 50px;

 height: 80px;

 background-color: #007500;

}

  

.item-center{

 position: absolute;

 place-self: center;

 background-color: #003d00;

 width: 30px;

 height: 30px;

}
```