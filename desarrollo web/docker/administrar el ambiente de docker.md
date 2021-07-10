# Administrando tu ambiente de Docker
Comandos:  
$ docker ps -a (veo todos los contenedores de mi máquina)  
$ docker container prune (borra todos los contenedores inactivos)  
$ docker rm -f $(docker ps -aq) (borra todos los contenedores que estén corriendo o apagados)  
$ docker network ls (lista todas las redes)  
$ docker volume ls (lista todos los volumes)  
$ docker image ls (lista todas las imágenes)  
$ docker system prune (borra todo lo que no se esté usando)  
$ docker run -d --name app --memory 1g platziapp (limito el uso de memoria)  
$ docker stats (veo cuantos recursos consume docker en mi sistema)  
$ docker inspect app (puedo ver si el proceso muere por falta de recursos)

![[Pasted image 20210626203840.png]]