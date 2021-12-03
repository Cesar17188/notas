# Propiedades del contenedor

•Display grid: para decirle al contenedor que tenga esa propiedad y así aplicarle estilos de grid

•Grid-template: define cuantas y de qué tamaño son las filas o columnas

•Gaps: el espacio entre cada celda

•Grid-auto: aplica el cambio para todas las columnas o filas

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

 <div class="item">

 <p>1</p>

 </div>

 <div class="item">

 <p>2</p>

 </div>

 <div class="item">

 <p>3</p>

 </div>

 <div class="item">

 <p>4</p>

 </div>

 <div class="item">

 <p>5</p>

 </div>

 <div class="item">

 <p>6</p>

 </div>

 </div>

</body>

  

</html>
```

CSS

```css
* {

 padding: 0;

 margin: 0;

 box-sizing: border-box;

}

html {

 font-size: 62.5%;

}

.contenedor {

 margin: 20px 20px;

 padding: 10px;

 border: 5px solid #18259b;

 background-color: #ffffff;

 border-radius: 15px;

 display: grid;

 grid-template-rows: 100px 100px 100px;

 grid-auto-columns: 100px;

 grid-auto-flow: column;

 gap: 20px;

 justify-content: center;

}

  

.item {

 border:1px solid #162c26;

 display: flex;

 justify-content: flex-end;

 align-items: flex-end;

 text-align: center;

 color: #ffffff;

 font-weight: bold;

 border-radius: 15px;

 transform: scale(1);

 transition: 0.15s;

}

  

.item:hover{

 transform: scale(1.2);

}

  

.item p {

 width: 2.5rem;

 height: 3.5rem;

 font-size: 3rem;

 border: 1px solid #162c26;

 border-radius: 10px;

}

  

.item:nth-child(3n + 1) {

 background: #add901;

}

  

.item:nth-child(3n + 1) p{

 background: #01700a;

}

  
  

.item:nth-child(3n + 2) {

 background: #139e01;

}

  

.item:nth-child(3n + 2) p{

 background: #0b5f00;

}

  

.item:nth-child(3n + 3) {

 background: #1b6d02;

}

  

.item:nth-child(3n + 3) p{

 background: #071f00;

}
```