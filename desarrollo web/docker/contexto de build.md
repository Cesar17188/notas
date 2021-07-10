# El contexto de build

Comandos:  
$ docker build -t prueba .(creo la imagen)  
$ docker run -d --rm --name app prueba (corro el contenedor)  
en el archivo .dockerignore puedo poner todo lo que no quiero que copie del contexto de build  
$ docker exec -it app bash (entro al contenedor y verifico que no se haya copiado lo que está en el .dockerignore)

Mas informacion sobre docker ignore en la documentacion oficial  
[https://docs.docker.com/engine/reference/builder/#dockerignore-file](https://docs.docker.com/engine/reference/builder/#dockerignore-file)

Entonces, para omitir archivos locales hacia un contenedor, usamos **.dockerignore** que funciona de igual manera que .gitignore.