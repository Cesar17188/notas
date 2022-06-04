# Transition property y duration

¡La propiedad `transition` es la que hace toda la magía! Si ya tienes un elemento con un estado inicial y otro elemento con un estado final, entonces simplemente basta con que le ponas esta propiedad y se animará sin problema 😉  
.  
Es decir, pasaras de tener esto:

![Transition no animated](https://media.giphy.com/media/6cnPXsppWlEPdbaaCt/giphy.gif)

A tener esto:

![Transition animated](https://media.giphy.com/media/gCSOFQybTbM3pome6c/giphy.gif)

Sí, así de fácil 😄

![[Pasted image 20220119130126.png]]

```html
<!DOCTYPE html>

<html lang="en">

<head>

 <meta charset="UTF-8">

 <meta http-equiv="X-UA-Compatible" content="IE=edge">

 <meta name="viewport" content="width=device-width, initial-scale=1.0">

 <title>Transition Property Duration</title>

 <style>

 .container {

 background-color: papayawhip;

 width: 400px;

 height: 100px;

 display: flex;

 justify-content: space-between;

 margin: 30px

 }

 .container:hover .box{

 transform: scale(1.2);

 }

 .box {

 background-color: blue;

 width: 100px;

 height: 100px;

 }

 .box1 {

 background-color: firebrick;

 transition: transform 500ms;

 }

 .box2 {

 background-color: darkred;

 transition: transform 1s;

 }

 .box3 {

 background-color: forestgreen;

 transition: transform 1.5s;

 }

 </style>

</head>

<body>

 <div class="container">

 <div class="box box1"></div>

 <div class="box box2"></div>

 <div class="box box3"></div>

 </div>

</body>

</html>
```