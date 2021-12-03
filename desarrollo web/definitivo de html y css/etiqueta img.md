# Etiqueta img

Hay una forma de poder generar la estructura básica de nuestro index sin que tengamos que codearlo todo:  
¡ + tab o html:5 + Tab  
Se recomienda descargar los tamaños de imágenes grande, mediano y pequeña. Luego las tratamos en Tinypng.  
La etiqueta imagen nos ayuda a poder renderizar las imágenes, tiene 2 atributos, el primero es source src para decirle en donde se encuentra la imagen que queremos enseñar. Tenemos dos formas, podemos sacar la imagen de alguna carpeta o podemos sacar la imagen de alguna url que tengamos en internet. El segundo atributo es alt que es una descripción que le vamos a dar a la imagen y esto nos sirve para dos cosas: primero, cuando la imagen no se logre renderizar va poder decir ahí cual es la descripción de esa imagen en caso de que no se vea, el segundo es que el alt nos ayuda para temas de accesibilidad. Ambos son importantes

```
<img src="" alt="">
<img src="./small.jpg" alt="Es una imagen de un perrito" />
```

La etiqueta de imagen no es la única que tenemos, hay otra que se llama figure, esto nos ayuda para poder generar un contenedor para la imagen.

```
<figure>
  <img src="./small.jpg" alt="Es una imagen de un perrito" />
</figure>
```