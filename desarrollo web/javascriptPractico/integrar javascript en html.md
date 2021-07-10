# Cómo integrar JavaScript en HTML

### 5. Cómo integrar JavaScript en HTML

Existen varias formas de integrar código javascript en un archivo html:

La primera forma y poco recomendada es que dentro del body declarar un archivo

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>figuras geométricas</title>
  </head>
  <body>
    <h1>Figuras geométricas</h1>
    <script>
	//código js
    </script>
  </body>
</html>
```

La segunda forma es utilizar un atributo source de la etiqueta javascript

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>figuras geométricas</title>
  </head>
  <body>
    <h1>Figuras geométricas</h1>
    <script src="dirección del archivo"></script>
  </body>
</html>

```

#### Cómo acceder a los archivos del proyecto desde el navegador

Para acceder a los archivos de nuestro computador se debe saber la ubicación. Si no posicionamos en la carpeta del proyecto desde la terminal  
se puede utilizar el comando `pwd` y nos dará como resultado la dirección de la carpeta.

Para acceder desde el navegador se debe de escribir el prefijo `file:///` y luego la dirección de la carpeta.

`file:///ubicación-de-la-carpeta/file.html`