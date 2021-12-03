# Etiqueta form e input

Esta clase fue muy valiosa ya que muchas veces habia visto videos de Formularios, pero jamas tan bien explicados como lo hizo Diego^^

```html
<!DOCTYPE html>

<html lang="en">

  

<head>

 <meta charset="UTF-8">

 <meta http-equiv="X-UA-Compatible" content="IE=edge">

 <meta name="viewport" content="width=device-width, initial-scale=1.0">

 <title>Formularios</title>

</head>

  

<body>

 <form action="">

 <label for="nombre">

 <span>¿Cual es tu nombre?</span>

 <input id="nombre" type="text" placeholder="Cesar">

 </label>

 <label for="inicio-platzi">

 <span>¿Qué día comenzaste en platzi?</span>

 <input id="inicio-platzi" type="date" placeholder="01/01/2020">

 </label>

 <label for="horario">

 <span>¿En qué horario estudias?</span>

 <input id="horario" type="time" placeholder="08:00">

 </label>

 </form>

</body>

  

</html>
```

Comenzemos.  
Es importante utilizar la etiqueta **<form></form>** para indicar que utilizaremos un formulario, ademas de la semantica y buenas practicas.  
Dentro de estas etiquetas indicaremos los elementos del Formulario como lo son…  
**<label></label>** que sera como nuestro “Contenedor” en esta ocasión. dentro de el pondremos la etiqueta **<span></span> (No es necesario)** para colocar un texto haciendo alusión al contenido esperado (nombre, contraseña, fecha etc…) y viene una de las etiquetas importantes la cual es **<input>** aqui es importante aclarar que hay muchos tipos de Input, los que veran en este ejemplo son **text, password, date, time** pero hay muchos mas…  
Tambien esta el atributo **placeholder** para colocar un texto como guia dentro de la caja (Input) y este al hacer click sobre el se eliminara.  
y Creo que es lo mas rescatable!  
Recuerden aun nos queda mucho por aprender 😄

**Codigo:**  

![Screen Shot 2020-08-27 at 19.05.08.png](https://static.platzi.com/media/user_upload/Screen%20Shot%202020-08-27%20at%2019.05.08-bec71ab9-233e-4d9c-bb41-9f3a837e15fe.jpg)

**Resultado:**  

![Screen Shot 2020-08-27 at 19.02.14.png](https://static.platzi.com/media/user_upload/Screen%20Shot%202020-08-27%20at%2019.02.14-3587cd31-e5f5-43e6-93e0-bdaa8ad93009.jpg)