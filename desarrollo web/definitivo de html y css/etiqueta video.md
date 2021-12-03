# Etiqueta video

```html
<!DOCTYPE html>

<html lang="en">

  

<head>

 <meta charset="UTF-8">

 <meta http-equiv="X-UA-Compatible" content="IE=edge">

 <meta name="viewport" content="width=device-width, initial-scale=1.0">

 <title>Document</title>

</head>

  

<body>

 <main>

 <section>

 <video controls preload="auto">

 <source src="./Bleach001.mp4#t=10,60">

 <source src="./Bleach001.m4v#t=10,60">

 </video>

 </section>

 </main>

</body>

  

</html>
``` 

La etiqueta **<video>**, tiene algunos atributos como:  


1.  **controls:** agrega al video los controles necesarios para reproducir, pausar y adelantar.
    
2.  **preload = auto:** hace que el navegador descargue el video, en el momento en el que se acceda a la página.
    

La etiqueta **<source>,** se puede colocar dentro de una etiqueta **<video>** varias veces, para especificar diferentes rutas. Esto para asegurar que cualquier navegador pueda mostrar el video.
	
	
	
	Añado un par de cosas más sobre el atributo **preload**

-   preload="metadata"  
    Carga previa de los metadatos
-   preload="none"  
    No existe carga de vídeo previa
	
	![[Pasted image 20211123142235.png]]
	
	Documentación : [https://www.w3schools.com/tags/tag_video.asp](https://www.w3schools.com/tags/tag_video.asp)

Atributos de una etiqueta **source**

![CapturaSource.PNG](https://static.platzi.com/media/user_upload/CapturaSource-9e2cb340-1dae-4eeb-bb56-ef7c43226249.jpg)
	
	Documentación : [https://www.w3schools.com/tags/tag_source.asp](https://www.w3schools.com/tags/tag_source.asp)
	
	