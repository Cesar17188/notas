# Demo de especificidad y orden en selectores

1.  Los **!important** estarán por encima de los demás estilos. Sin embargo, son mala práctica y no se deberían usar.
2.  Los estilos embebidos en el HTML, es decir **inline styles** están por encima de las **clases y IDs**. Sin embargo, también se deberían evitar.
3.  Los **IDs** están por encima de las **clases**. Los **IDs** son específicos, si se usa uno en un archivo HTML ya no se podrá repetir más en ese mismo archivo. Mientras que las **clases** si se pueden repetir en cualquier elemento.
4.  Un **estilo de etiqueta** es el último valor que el navegador tiene en cuenta antes de tomar los estilos por defecto de esa etiqueta. Los **estilos de etiqueta** son los que menos peso tienen.

```html
<!DOCTYPE html>

<html lang="en">

  

<head>

 <meta charset="UTF-8">

 <meta http-equiv="X-UA-Compatible" content="IE=edge">

 <meta name="viewport" content="width=device-width, initial-scale=1.0">

 <title>Demo</title>

 <link rel="stylesheet" href="./style.css">

</head>

  

<body>

 <header class="page-header">

 <h1 id="page-title" class="title">Empresa</h1>

 <nav>

 <ul id="main-nav" class="nav">

 <li><a href="#">Home</a></li>

 <li><a href="#">Cursos</a></li>

 <li><a href="#">Instructores</a></li>

 <li><a href="#" class="blog">Blog</a></li>

 </ul>

 </nav>

 </header>

</body>

  

</html>
```
CSS
```css
*{

 margin: 0;

 padding: 0;

 box-sizing: border-box;

}

h1 {

 font-family: serif;

 color: purple;

 margin-bottom: 10px;

}

  

#page-title {

 font-family: Arial, Helvetica, sans-serif;

}

  

.title {

 font-size: 18px;

 font-family: monospace;

}

  

#main-nav {

 margin-top: 10px;

 list-style: none;

 list-style-type: none;

 padding-left: 0px;

}

  

#main-nav li {

 display: inline-block;

}

  

#main-nav a {

 color: white;

 background-color: #13a4a4;

 padding: 5px;

 border-radius: 2px;

 text-decoration: none;

}

  

#main-nav .blog {

 background-color: red;

}
```