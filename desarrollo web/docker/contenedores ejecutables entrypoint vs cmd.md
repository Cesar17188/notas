# Contenedores ejecutables: ENTRYPOINT vs CMD

Comandos:  
$ docker buils -t ping . (construyo la imagen)  
$ docker run --name pinger ping <hostname> (ahora le puedo pasar un parámetro, previamente tengo que agregar el ENTRYPOINT en el Dockerfile)
	
	Les recomiendo leer esta sección de la documentación de Docker: [Best practices for writing Dockerfiles](https://docs.docker.com/develop/develop-images/dockerfile_best-practices/).
	
	**Para reforzar:**   
[https://phoenixnap.com/kb/docker-cmd-vs-entrypoint](https://platzi.com/clases/2066-docker/32868-contenedores-ejecutables-entrypoint-vs-cmd/url)