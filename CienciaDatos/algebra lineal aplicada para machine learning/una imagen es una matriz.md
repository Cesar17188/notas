# Una imagen es una matriz

Cuando leemos una imagen usando la biblioteca PIL obtenemos la instancia de un objeto de la clase Image. Este objeto viene con unos métodos asociados que nos permiten la manipulación de la imagen. En este caso usamos el método `convert` que nos permite transformar una imagen de un modo a otro, estos modos son RGB, RGBA, CMYk, etc. ([aquí](https://pillow.readthedocs.io/en/stable/handbook/concepts.html#concept-modes) dejo documentación sobre los modos disponibles para esta función). Aquí se usó el modo ‘LA’ que da como resultado una imagen con 2 canales, uno representando la escala de grises y otro representando el canal de transparencia. Ambos canales están representados con 8 bits, lo cual quiere decir que sus valores pueden ir entre 0 y 255.  
  
Esta transformación fue necesaria ya que aunque la imagen que vemos desde un principio está en escala de grises, en realidad al ser leída desde un archivo JPG tiene los 3 canales RGB. Esto se puede comprobar con el método `getbands()`.  
  

![3bandas.png](https://static.platzi.com/media/user_upload/3bandas-71d18c3f-7356-475a-8c42-08fead4da740.jpg)  
  
Después de la transformación vemos que esta cantidad de canales ha cambiado. Los tres canales (RGB) se han mapeado a uno solo (L) representando los diferentes tonos de grises en la imagen. El canal de transparencia no es últi al haber obtenido la imagen desde un archivo JPG.  
  

![2bandas.png](https://static.platzi.com/media/user_upload/2bandas-2bb82a10-943a-4f95-82c7-0c38a6c37eb7.jpg)  
  
Otro método que usamos fue `getdata`. Este método nos entrega un objeto que contiene la secuencia de valores que componen la imagen. Cuando no se especifica un canal (band) el método devuelve los valores de todos los canales de la imagen. Por ejemplo, para la imagen original cada elemento de la secuencia tendrá una tupla con 3 valores, los 3 valores de cada canal. En total habrá 12763008 valores dado que la imagen tiene un tamaño de 3693x3456.  
  
Algo importante es que esta secuencia de valores tiene un tipo de dato definido dentro de la biblioteca PIL, por lo cual para manipularlo de forma convencional es necesario transformarlo a una lista de python usando el método `list()`.  
  

![valoresoriginales.png](https://static.platzi.com/media/user_upload/valoresoriginales-b814905b-d036-427c-aa2b-cb74482cca29.jpg)  
  

![valores_grises.png](https://static.platzi.com/media/user_upload/valores_grises-2e4500d9-02e2-41e7-9e8a-8b907d327727.jpg)  
  
El resultado muestra que el canal de transparencia siempre tiene un valor de 255 (por haber sido leído desde JPG). Esto se pudo haber evitado si hubiéramos usado sólo el modo ‘L’. Finalmente hay que aclarar que en el código se usa el parámetro `band=0` justamente para obtener sólo los valores del canal de grises.

Si alguien le interesa ver que hace la función SVD:  
[https://www.youtube.com/watch?v=EGSbpqlW9BY](https://www.youtube.com/watch?v=EGSbpqlW9BY)  
[https://www.youtube.com/watch?v=CyMp5F4eqUc](https://www.youtube.com/watch?v=CyMp5F4eqUc)