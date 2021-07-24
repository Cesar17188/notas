# Crear una página web para calcular descuentos

Se puede lograr ingresar valores desde el teclado con la etiqueta en html $input$ y dentro de ella hay que definir tipo de datos, el nombre el identificador. etc. La construcción para este ejercicio fue la siguiente.

## HTML

```html
<!DOCTYPE html>

<html lang="en">

  

<head>

 <meta charset="UTF-8">

 <meta http-equiv="X-UA-Compatible" content="IE=edge">

 <meta name="viewport" content="width=device-width, initial-scale=1.0">

 <link rel="stylesheet" href="./styles.css">

 <title>Porcentajes y descuentos | Curso práctico de JS de platzi</title>

</head>

  

<body>

 <header class="header">

 <h1 class="header_title">

 Porcentajes y descuentos

 </h1>

 <p class="header_subtitle">producto a comprar</p>

 </header>

  

 <section class="descuentos">

 <div class="descuentos_producto">

 <div class="descuento_producto_title">

 <h1>Producto</h1>

 <p>descripción</p>

 </div>

 <div class="descuento_producto_normal">

 <img class="image" src="./image/case2.png" alt="">

 <p class="decuento_producto_normal_precio" id="precioOriginal"></p>

 </div>

 </div>

 <div class="descuentos_producto">

 <div class="descuento_producto_title">

 <h1>Descuentos</h1>

 <p>tipo de descuento</p>

 </div>

 <div class="descuentos_producto_selector">

 <input type="radio" name="descuentos" value="1" checked>descuento normal

 <input type="radio" name="descuentos" value="2">tengo cupones

 <button class="descuentos_producto_selector_button" onclick="tipoDescuento()">ver descuento</button>

 </div>

 <div id="descuento_normal">

 <p>descuento normal 15%</p>

 <div>

 <p>total ahorro</p>

 <p id="total_ahorro"></p>

 <p>total a pagar</p>

 <p id="num_desc"></p>

 </div>

 </div>

 <div id="descuento_cupon">

 <p>descuento con cupones</p>

 <div>

 <p>Ingresa tu cupón</p>

 <input class="descuento_cupon_input" id="calc_desc" type="text" placeholder="cupon_1">

 <button class="descuentos_producto_selector_button" onclick="calcular_descuento()"

 type="button">cálcular

 descuento</button>

 </div>

 <div>

 <p>% total ahorro</p>

 <p id="total_ahorro_cupon"></p>

 <p>total a pagar</p>

 <p id="num_desc_cupon"></p>

 </div>

 </div>

 </div>

 </section>

  

 <footer class="footer">

 <p class="footer_title">descuentos</p>

 </footer>

 <script src="./descuentos.js"></script>

</body>

  

</html>
```

## CSS

```css
body {

 margin: 0px;

 padding: 0px;

 font-family: "Mulish", sans-serif;

}

  

.header {

 width: 100%;

 background-color: #3b479d;

 color: white;

 text-align: center;

}

  

.header_title {

 margin: 0px;

}

  

.header_subtitle {

 margin: 0px;

 padding: 20px 0px;

}

  

.descuentos {

 display: grid;

 grid-template-columns: 50% 50%;

 color: white;

 background: linear-gradient(#3b479d, #030708);

}

.descuentos_producto {

 border: 3px solid white;

 border-radius: 25px;

 margin: 0px 5px 30px 0px;

}

  

.descuento_producto_normal {

 display: grid;

 grid-template-columns: 50% 50%;

}

  

.descuento_producto_title {

 text-align: center;

}

  

.image {

 width: 250px;

}

  

.decuento_producto_normal_precio {

 align-items: center;

 justify-items: center;

}

  

.descuentos_producto_selector {

 text-align: center;

 align-items: center;

}

  

.descuentos_producto_selector_button {

 text-decoration: none;

 padding: 6px;

 font-weight: 400;

 font-size: 13px;

 color: #ffffff;

 background-color: #01095d;

 border-radius: 6px;

 border: 1px solid #3d0979;

 cursor: pointer;

}

  

.descuentos_producto_selector_button:hover {

 color: #090282;

 background-color: white;

}

  

.descuento_cupon_input {

 text-decoration: none;

 color: white;

 border: 2px solid #060163;

 background-color: #270263;

 padding: 4px;

}

  

#descuento_normal {

 display: none;

 text-align: center;

}

#descuento_cupon {

 display: none;

 text-align: center;

}

  

.footer {

 height: 10px;

 width: 100%;

 color: white;

 background: #030708;

 padding: 50px;

}

  

.footer_title {

 margin: 0;

}
```