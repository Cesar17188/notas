# Compose en equipo: override

**docker-compose.override.yml** es un archivo que se encarga de sobreescribir tu configuración de **docker-compose.yml** , se puede usar para tener segura tu configuración y para no guardar los cambios en el repositorio de git.  
Un equivalente podría ser los archivos de declaración de variables de entorno, donde hay un archivo **.env** declarando su nombre y valor, y hay una copia **.env.example** con solo las variables sin valor. En **.gitignore** se declara que los cambios en **.env** no serán guardados, pero mandamos el archivo de ejemplo al repositorio.

Comandos:  
$ touch docker-compose.override.yml (creo el archivo override)  
$ docker-compose up -d (crea los servicios/contenedores)  
$ docker-compose exec app bash (entro al bash del contenedor app)  
$ docker-compose ps (veo los contenedores del compose)  
$ docker-compose up -d --scale app=2 (escalo dos instancias de app, previamente tengo que definir un rango de puertos en el archivo compose)  
$ docker-compose down (borro todo lo creado con compose)