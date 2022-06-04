# Cómo funciona el formato JPG

![[Pasted image 20220210173111.png]]

Asumamos que tenemos una foto de 600*800, si esto estuviera en un formato sin compresión, pesaría 840KB (solo representando un color por pixel).

Para tener una calidad de 32 bit la imagen debe pesar casi 1.9MB, así que podemos comprimir las imágenes y usar formatos como jpeg.

jpg lo que hace es aproximar áreas de color, si un color esta en áreas continuas, solo se declara la zona y el color de esa zona, de esta forma se pueden tener imágenes que pesan mucho menos.

El formato PNG funciona diferente a JPG. Y hay mejoras sobre el algoritmo JPG como JPEG2000.

Hay todo un mundo de formatos y estándares de compresión como:

-   DivX en video
-   gzip en el prótocolo HTTP
-   AAC vs. MP3 en sonido
-   MKV como un metaformato contenedor de otros formatos
-   PSD como un formato cerrado gráfico

¿Qué otros formatos especiales de compresión conoces o te intrigan?

El cálculo que hace @freddier en (min 00:44s) para conocer el tamño en Bytes de la imagen sirve también para determina la cantidad de megapixels que tiene una imagen … normalmente este término se usa para imágenes de cámaras fotográficas digitales. 1 Megapixel es en términos generales un millón de pixeles … o más exactamente 1,048,576 … así pues para estimar el aproximado en megapixels que tiene una foto de 3000 pixeles de ancho por 2000 de alto … basta con multiplicar y dividir el resultado por 1 millón … 3000 x 2000 / 1000000 = 6 Megapixels

Les dejo una tabla de referencia de tamaños:

```
Megapixels  Dimensiones 
---------- -------------
2.0	  			1740 x 1160
3.0	  			2160 x 1440
4.0	  	 		2450 x 1633
6.0       	3000 x 2000
8.0	 			 3504 x 2336
10.0	     3872 x 2592
12.0	   	4256 x 2832
14.0	     4608 x 3072
16.0	     4928 x 3264
18.0	     5184 x 3456
24.0	 	   6016 x 4000
```