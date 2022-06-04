# Problemas de parpadeo
El “parpadeo” se da porque cuando queremos hacer :hover en el item si este se mueve hay momentos donde no estamos haciendo :hover (ya que se va de donde esta nuestro puntero).

Al contener al item y hacer :hover en su container, por mas que el item se mueva, nunca dejamos de hacer :hover en el container ya que este no se mueve.

.  
En algunas ocasiones hay un leve parpadeo cuando transformamos un elemento. En este caso lo vimos cuando al momento de hacer `:hover` sobre el elemento hijo, se llevaba acabo un translado en el eje Y.  
.  
Este leve parpadeo en algunas ocasiones no se nota, ya que son algunos factores externos los que provocan este error. Sin embargo, los pequeños detalles hacen la diferencia, no solo en las relaciones de pareja, sino en UX tambien.  
.  
Por lo tanto, para solucionar esto y que todos tus usuarios tenga la mejor experiencia posible, hay que agregarle el `:hover` al elemento padre para que el hijo sea el que haga la accion. Esto se hace de la siguiente manera:

```
.parent_element:hover child_element{
	Your: transformations;
}
```

```html
<!DOCTYPE html>

<html lang="en">

<head>

 <meta charset="UTF-8">

 <meta http-equiv="X-UA-Compatible" content="IE=edge">

 <meta name="viewport" content="width=device-width, initial-scale=1.0">

 <title>UX Problemas de parpadeo</title>

 <style>

 div {

 width: 100px;

 height: 100px;

 border-radius: 50%;

 }

 .container:hover .item{

 transform: translateY(15px);

 }

 .item {

 background-color: brown;

 }

 </style>

</head>

<body>

 <div class="container">

 <div class="item"></div>

 </div>

</body>

</html>
```