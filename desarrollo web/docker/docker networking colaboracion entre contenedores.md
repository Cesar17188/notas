# Docker networking: colaboración entre contenedores

Comandos:  
$ docker network ls (listo las redes)  
$ docker network create --atachable plazinet (creo la red)  
$ docker inspect plazinet (veo toda la definición de la red creada)  
$ docker run -d --name db mongo (creo el contenedor de la BBDD)  
$ docker network connect plazinet db (conecto el contenedor “db” a la red “platzinet”)  
$ docker run -d -name app -p 3000:3000 --env MONGO_URL=mondodb://db:27017/test platzi (corro el contenedor “app” y le paso una variable)  
$ docker network connect plazinet app (conecto el contenedor “app” a la red “plazinet”)