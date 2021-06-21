# El sistema de capas

EL sistema de capas de docker les permite crear imagenes públicas y estas imagenes tiene su Dockerfile público, lo cual nos permite entrer y ver como esta hecho.

1. entramos a https://hub.docker.com/
2. buscamos la imagen de ubuntu

La importancia de entender el sistema de capas consiste en la optimización de la construcción del contenedor para reducir espacio ya que cada comando en el dockerfile crea una capa extra de código en la imagen.

Agregando Capas

Con docker commit se crea una nueva imagen con una capa adicional que modifica la capa base.

Ejemplo: crear una nueva imagen a partir de la imagen de Ubuntu.

docker pull ubuntu

docker images

docker run -it cf0f3ca922e0 bin/bash

(modificar el contenedor: Ej apt-get install nmap)

docker commit deddd39fa163 ubuntu-nmap

## Comandos de la clase

![carbon (5).png](https://static.platzi.com/media/user_upload/carbon%20%285%29-2a059b67-fd31-42a9-b7dd-5d62b79c22df.jpg)