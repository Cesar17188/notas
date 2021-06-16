# Comprendiendo el estado de docker

```docker
# Hola mundo con docker
$ docker run hello-world (corro el contenedor hello-world)  

# Ver contenedores corriendo en el momento
$ docker ps (muestra los contenedores activos)  

# Ver todos los contenedores corriendo y con un historial
$ docker ps -a (muestra todos los contenedores)

# Inspeccionar la configuración de un contenedor por medio del CONTAINER ID
$ docker inspect <containe ID> (muestra el detalle completo de un contenedor)

# Inspeccionar la configuración de un contenedor por medio del NAME
$ docker inspect <name> (igual que el anterior pero invocado con el nombre)

# Crear un contenedor con un nombre personalizado
$ docker run –-name hello-platzi hello-world (le asigno un nombre custom “hello-platzi”)

# Renombrar un contenedor
#               <old_name>   <new_name>
$ docker rename hello-platzi hola-platzy (cambio el nombre de hello-platzi a hola-platzi)  

# Eliminar todos los contenedores apagados o con un nombre o id especifico si se le incluye
$ docker rm <ID o nombre> (borro un contenedor)  

# Elimina TODOS los contenedores
$ docker container prune (borro todos lo contenedores que esten parados)
```

Puedes crearte un t2.micro en AWS e instalar Docker y conectarte por medio de SSH, para las personas que usan windows y mac si desean tener una experiencia mas nativa en linux sin necesidad de crearte una maquina virtual y consumir recursos de tu propia maquina, esta idea tambien funcionara para personas que tengan maquinas con limitados recurso y/o espacio en disco.