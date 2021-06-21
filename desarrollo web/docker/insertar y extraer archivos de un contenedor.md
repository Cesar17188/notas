# Insertar y extraer archivos de un contenedor 

Comandos:

$ touch prueba.txt (creo un archivo en mi máquina)  
$ docker run -d --name copytest ubuntu tail -f /dev/null (corron un ubuntu y le agrego el tail para que quede activo)  
$ docker exec -it copytest bash (entro al contenedor)  
$ mkdir testing (creo un directorio en el contenedor)  
$ docker cp prueba.txt copytest:/testing/test.txt (copio el archivo dentro del contenedor)  
$ docker cp copytest:/testing localtesting (copio el directorio de un contenedor a mi máquina)  
con “docker cp” no hace falta que el contenedor esté corriendo