# Keywords especiales

-   fr : Es una unidad de medida especial de css grid para darle ancho o alto a filas y columnas 1fr representa una fraccion del total de columnas o filas.
    
-   min-content : Ajusta el ancho de la celda lo mínimo posible sin romper su contenido.
    
-   max-content : Ajusta el ancho de la celda lo máximo posible para mostrar su contenido.
    
-   auto-fill : Agrega columnas “fantasma” que rellenan el espacio sobrante del contenedor.
    
-   auto-fit : Ensancha las columnas para que ocupen todo el espacio del contenedor.
    

**auto-fill y auto-fit** ayudan a la grilla a ocupar el 100% del espacio disponible.

```html
<!DOCTYPE html>

<html lang="en">

  

<head>

 <meta charset="UTF-8">

 <meta http-equiv="X-UA-Compatible" content="IE=edge">

 <meta name="viewport" content="width=device-width, initial-scale=1.0">

 <link rel="stylesheet" href="./style.css">

 <title>Keywords Especiales</title>

</head>

  

<body>

 <div class="contenedor">

 <div class="item item-1">1</div>

 <div class="item item-2">2</div>

 <div class="item item-3">3</div>

 <div class="item item-4">4</div>

 </div>

 <div class="contenedor-2">

 <div class="item item-1">1</div>

 <div class="item item-2">2</div>

 <div class="item item-3">3</div>

 <div class="item item-4">4</div>

 </div>

</body>

  

</html>
```

CSS
```
.contenedor {

 border: 5px solid #EDEBD7;

 background-color: #A39594;

 display: grid;

 grid-template-columns: repeat(auto-fit, minmax(100px, 1fr)); 

}

  

.contenedor-2 {

 border: 5px solid #EDEBD7;

 background-color: #A39594;

 display: grid;

 margin-top: 100px;

 grid-template-columns: repeat(auto-fill, minmax(100px, 1fr)); 

}

  

.item {

 border: 5px solid #E3B23C;

 font-size: 2rem;

}
```