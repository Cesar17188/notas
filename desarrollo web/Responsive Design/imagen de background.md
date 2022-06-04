# Imagen de background

El shorthand de la imagen de background sería:

```
background: url('./assets/images/bitcoin.svg') center/cover no-repeat;
```

Tener en cuenta que se debe separar el _background-position_ y el _background-size_ por un **slash** `(/)` usando esta forma.

**background-size: cover.**  
Este se usa para expandir la imagen respecto a la dimensión del contenedor que en este caso seria el mismo **div**.  
Y es verdad que es una buena practica cuando las imágenes que agregamos son de un tamaño superior predefinido.  
Pero noto que cuando lo agregamos a este ejemplo , la imagen pierde calidad, siendo incluso **svg**. Y Creo que se genera por el mismo **cover** ,ya que eso sucede con imágenes pequeñas, y en este caso lo toma así debido a que el tamaño de la imagen es de **195px.**

Lo que finalmente quiero decir es que,** si sabemos que la imagen es pequeña**, no seria bueno agregar el background-size: cover.  
Espero les ayude, y si me equivoque en algo por favor corregirme, gracias.