# Construyendo una imagen propia

El proceso se basa en un archivo llamado docker file.  El proceso es parecido a:
1. Partiendo de un docker file (es un archivo que describe lo que yo quiero que pase cuando se cree una imagen)
2. Con un comando que se llama build el resultado de hacer eso va a ser una imagen
 Una imagen nos sirve para correr contenedores
 
 Puedes subir tu docker file a un repo GIT y cargarlo desde ahi para construir la imagen. Sin pasar por dockerhub
 
 ![Screenshot from 2020-11-06 19-53-30.png](https://static.platzi.com/media/user_upload/Screenshot%20from%202020-11-06%2019-53-30-a305c998-0991-44ad-9319-80cacb1a4bc7.jpg)
 
 Retagear una imagen
 
 ![](https://i.ibb.co/JBL946b/Screenshot-at-Feb-05-15-26-18.png)
 
 El código de creación

![carbon (3).png](https://static.platzi.com/media/user_upload/carbon%20%283%29-975f4d64-9144-4a75-a8ba-0eceba66db50.jpg)

$ mkdir imagenes (creo un directorio en mi máquina)  
$ cd imagenes (entro al directorio)  
$ touch Dockerfile (creo un Dockerfile)  
$ code . (abro code en el direcotrio en el que estoy)

##Contenido del Dockerfile##  
FROM ubuntu:latest  
RUN touch /ust/src/hola-platzi.txt (comando a ejecutar en tiempo de build)  
##fin##

$ docker build -t ubuntu:platzi . (creo una imagen con el contexto de build <directorio>)  
$ docker run -it ubuntu:platzi (corro el contenedor con la nueva imagen)  
$ docker login (me logueo en docker hub)  
$ docker tag ubuntu:platzi miusuario/ubuntu:platzy (cambio el tag para poder subirla a mi docker hub)  
$ docker push miusuario/ubuntu:platzi (publico la imagen a mi docker hub)
	
	
	