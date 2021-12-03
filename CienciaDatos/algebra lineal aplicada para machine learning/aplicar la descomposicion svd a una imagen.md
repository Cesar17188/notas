# Apliquemos la descomposición SVD a una imagen

-   Podemos reconstruir una imagen a partir de una parte de los vectores y valores singulares. No se necesitan todos los vectores ni valores para reconstruirla.

getdata() Devuelve el contenido de esta imagen como un objeto de secuencia que contiene valores de píxeles. El objeto de secuencia se aplana, de modo que los valores para la línea uno siguen directamente después de los valores de la línea cero, y así sucesivamente.

Tenga en cuenta que el objeto de secuencia devuelto por este método es un tipo de datos PIL interno, que solo admite ciertas operaciones de secuencia. Para convertirlo a una secuencia ordinaria (por ejemplo, para imprimir), use list (im.getdata ()).  
.  
fuente: [https://www.geeksforgeeks.org/python-pil-image-getdata/](https://www.geeksforgeeks.org/python-pil-image-getdata/)

Veo que muchos preguntan que es lo que hace band=0, y que hay un poco de confusión a la hora de explicarlo así que voy a intentar aclararlo.

```
imagen_gr = imagen.convert('LA')
```

Convierte la imagen RGB a escala de grises, pero entrega una imagen con 2 canales(o bandas) L y A:

L tiene la información de la imagen en escala de grises.

A tiene la información de transparencia de la imagen, como estamos trabajando con una imagen JPG todos los valores en esta matriz son 255.

```
imagen_mat = np.array(list(imagen_gr.getdata(band=0)),float)
```

Aquí estamos tomando la información del canal(banda) L, que es el que es la que tiene la información que nos importa, la información de la imagen en escala de grises.

Algunos se están confundiendo y piensan que solo esta tomando la banda de R de una imagen RGB, pq ese es el ejemplo que da la documentación, pero recuerden que aquí convertimos esa información a una imagen a escala de grises antes, si quieren pueden graficar la banda=1 que es la que da la información de la transparencia y se darán cuenta que solo es un canal sin información importante., lo pueden hacer con el siguiente código.

```
imagen_gr = imagen.convert('LA')
imagen_A = np.array(list(imagen_gr.getdata(band=1)),float)
imagen_A.shape = (imagen_gr.size[1], imagen_gr.size[0])
plt.imshow(imagen_A)
```

Espero haya quedado claro y sirva para entender un poco el uso de esta librería.