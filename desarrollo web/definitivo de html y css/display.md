# Display

En un elemento con display:inline no puedo usar margin ni padding arriba ni abajo, solo derecha e izquierda. Tampoco se puede aplicar width o height.

En un elemento con display:block el contenido del elemento toma el 100% del width, se puede usar margin y padding por todos los lados.

En un elemento con display:inline-block, se puede usar margin y padding por todos lados, así como darle width y height, y el contenido es del mismo tamaño que el elemento.

Etiquetas como p y div vienen por Default con un display:block
Etiquetas como span viene por Default con un display:inline

Los elementos _**inline**_ sólo ocupan el espacio necesario para mostrar sus contenidos.

```
Elementos inline:
<a> <span> <img> <b> <i> <small> <cite> <code> <em> <strong> <br> <button> <input> <label> <select> <textarea>
```

Mientras los elementos _**block**_ ocupa todo el espacio disponible hasta el final de su línea, aunque sus contenidos no ocupen todo el sitio.

```
Elementos block:
<div> <article> <section> <header> <footer> <aside> <table> <p> <video> <ul> <ol> <h1> <h2> <h3> <h4> <h5> <h6>
```

Los elementos _**inline-block**_ conservan las propiedades mas importantes de los elementos inline y block.

**Block**: Estos toman el 100% del width, por lo que un elemento no puede posicionarse a un lado de el.  
Se le puede poner el width deseado, height deseado, añadir margin, padding sin problema. Pero recordando que ocupara este elemento todo el largo de una Fila por asi decirlo.

**Inline**: Estos elementos solo ocuparan el ancho dependiento de su contenido. Por lo tanto estos elementos si permiten que si un elemento cabe a lado suyo, se posicione este ahi.  
Las *_desventajas_ es que no se les puede modificar el width, height, ni colocar margin u padding tanto top, como bottom.

**inline-block**: Este tiene la combinación de los 2 anteriores. Haciéndolo un mejor candidato para usarlo.  
Permite modificar su width, height, añadirle margin, padding sin problemas y lo mejor es que mientras que haya espacio a un lado suyo, este permitirá posicionar mas elementos ahi.

**Ejemplo**  
Puedes verlo [Online](https://ijcode1.github.io/Curso-Definitivo-de-HTML-y-CSS/display/) [Repositorio](https://github.com/iJCode1/Curso-Definitivo-de-HTML-y-CSS/tree/master/display)  

![displays.jpg](https://static.platzi.com/media/user_upload/displays-26ca720e-334b-4485-8921-78f3f248dd71.jpg)

**Codigo HMTL**

```
<!DOCTYPE html>
<html lang="es">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width= device-width, initial-scale=1.0" />
    <link rel="stylesheet" href="./style.css" />
    <title>iJCode - Display</title>
  </head>
  <body>
    <h2 class="title">
      Elementos "< p >" con Display Block: Ocupa todo el Width del Viewport
    </h2>
    <div class="block">
      <p>Soy un Parrafo con display:block</p>
    </div>
    <div class="block">
      <p>Soy un Parrafo con display:block</p>
    </div>

    <h2 class="title">Elementos " < p > " con display: inline</h2>
    <div class="inline">
      <p>Soy un parrafo pero con display: inline</p>
      <p>Soy un segundo parrafo pero con display: inline</p>
    </div>

    <h2 class="title">Elements inline-block</h2>
    <nav>
      <ul>
        <li>Menu</li>
        <li>Cursos</li>
        <li>Tutoriales</li>
        <li>Tienda</li>
        <li>Contacto</li>
      </ul>
    </nav>
  </body>
</html>
```

**Codigo CSS**

```
* {
  box-sizing: border-box;
  margin: 0px;
  padding: 0px;
}

html {
  font-size: 62.5%;
}

.title {
  width: 100%;
  text-align: center;
  margin: 1rem auto;
  font-size: 2rem;
  color: #322f3d;
}

.block {
  height: 60px;
  background-color: #87556f;
  width: 350px;
  margin-bottom: 2rem;
}

.block > p {
  font-size: 1.6rem;
  background-color: #1a1a2e;
  color: white;
  padding: 1rem 1rem;
  border: 2px solid #be5683;
  padding: 0.5rem 1rem;
  display: block;
}

.inline {
  height: 60px;
  background-color: #87556f;
}

.inline p {
  font-size: 1.6rem;
  color: white;
  border: 2px solid #be5683;
  background-color: #1a1a2e;
  display: inline;
  padding: 0.5rem 1rem;
  margin-right: 2rem;
  width: 1000px;
  height: 700px;
  margin-top: 50px;
  margin-bottom: 50px;
}

nav {
  background-color: #221f3b;
  height: 50px;
}

ul {
  margin: 0 auto;
  text-align: center;
  height: inherit;
}

ul > li {
  display: inline-block;
  font-size: 1.6rem;
  background-color: #6f4a8e;
  color: #ffe4e4;
  padding: 1rem 2rem;
  margin: 6px auto;
}
```