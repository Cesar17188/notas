# Bind mounts

Los contenedores son entidades autocontenidas que no pueden acceder ( a menos que se lo permitamos) al sistema operativo de la máquina que esta ejecutandolos, de hecho ellos no saben que estan adentro de una máquina, no saben que tienen algo por fuera, desde el punto de vista del contenedor.

Aveces tenemos aplicaciones que generan datos, que usan datos que nos interesa como usuarios del sistemas poder manejar o acceder para comunicarnos con otros contenedores o con el sistema operativo. A esta operación se la denomina Bind mounts lo cual se realiza con la siguientes instrucciones


$ mkdir dockerdata (creo un directorio en mi máquina)  
$ docker run -d --name db mongo  
$ docker ps (veo los contenedores activos)  
$ docker exec -it db bash (entro al bash del contenedor)  
$ mongo (me conecto a la BBDD)

```
> shows dbs (listo las BBDD)  
> use platzi ( creo la BBDD platzi)  
> db.users.insert({“nombre”:“guido”}) (inserto un nuevo dato)  
> db.users.find() (veo el dato que cargué)  
> $ docker run -d --name db -v <path de mi maquina>:<path dentro del contenedor(/data/db mongo)> (corro un contenedor de mongo y creo un bind mount)
```

## En windows
	
ERROR(14) del contenedor —resuelto  
Estoy siguiendo el curso desde windows 10 en una distro de ubuntu 20.04 WSL2.  
Tuve el siguiente problema: al poner la ruta local, el contenedor arrojaba un error(14).  
Esta era mi ruta local:
	
```
docker run -d --name db -v /mnt/d/dockerPlatzi/mongodata:/data/db mongo
```
	
Con ese error el contenedor no se mantenía ejecutando, se finalizaba.
Para buscar el error hice lo siguiente, ejecuté el comando
	
```
docker logs db
``` 
	
me salía un error largo, que a lo que entendía no tenía permisos.  
Creí que era por windows mismo y la ruta en la que estaba posicionado.
**Encontré dos soluciones:**
**La primera** es que se debe de crear un volumen en docker con el siguiente comando.

```
	docker volume create --name mongodata
```

luego continuando con los comandos que se dan en este video, se reemplazaría la ruta local que obtienes del pwd por el nombre del volumen que has creado. Algo así:
	
```
	docker run -d --name db --v mongodata:/data/db mongo
```

**La segunda** es cambiar la ruta en la que te encuentras.  
Hice un cambio de ruta en la línea de comandos de la siguiente manera:

```
	cd ~
```

Este comando nos lleva al home (~) de la distribucion (de esta afirmación no estoy del todo seguro)
Luego en esa ruta creas la carpeta para hacer las pruebas de la clase

```
	mkdir mongodata
```

Finalmente, introducirías el comando para ejecutar poniendo la ruta local de la siguiente manera:
	
```
	docker run -d --name db --v ~/mongodata:/data/db mongo
```