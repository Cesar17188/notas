# ¿Cómo trabajar con archivos?
Lectura y escritura

Existen muchisimos tipos de archivos pero podemos separarlos en dos tipos:
* Los archivos de texto: Tienen bytes por dentro que representan letras, simbolos, números
	* .json: Compartir información entre servicios, este archivo guarda la información
	* .py para editar los scripts
	* .xml: Comparitr información
	* .js: Archivos de código para crear páginas web
	* .css: Archivos de código para crear páginas web
	* .csv: Archivos de datos
* Los archivos binarios: Representan cosas mucho más complejas como datos especificos de imagenes y videos
	* .png archivos de imagenes
	* .jpg archivos de imagenes
	* .mp3 archivos de audio
	* .mp4 archivos de video
	* .avi archivos de video
	* .dll archivos de windows para controlar archivos de sistema

Con [[Python]] generalmente no trabajamos con archivos binarios de hecho con programación no trabajamos con este tipo de archivos. [[Python]] generalmente trabajara con archivos de texto (o archivos planos).

Para abrir archivos de texto con [[Python]] tenemos 3 modos de apertura
* R -> Lectura
* W -> Escritura (sobreescribir): si escribimos en un archivo y luego entramos con W lo que se hace es eliminar el archivo y reemplazar por un nuevo archivo
* A -> Escritura (agregar al final): el archivo se abre y lo que ingreso se añade al final sin eliminar el archivo existente

con el código

```python
with open('./ruta/del/archivo.txt', 'r') as f:
```

La palabra clave with: es un manejador contextual en python y controla el flujo del archivo. Lo que hace es que si cerramos el programa o si el programa se cierra inesperadamente el archivo no se rompa.
Luego tenemos la función open que abre el archivo con los paramétros
* La ruta del archivo
* modo de apertura('r', 'w', 'a')

Finalmente esta el keyword as que nos sirve para darle un nombre hipotetico al nombre del archivo dentro del programa para interactuar con el con ese nombre.