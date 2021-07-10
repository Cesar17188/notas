# Configurar nuestro entorno con Hadoop

- se puede utilizar maquinas virtuales de ubunto (virtual box es buena opcion)
- se puede trabajar directamente en ubuntu
- se puede trabajar en contenedores de docker [[curso de docker]]


## Crear tu propio dockerfile para tu entorno de pruebas con Hadoop

- clonar el repositorio git@github.com:terranigmark/curso-hadoop-platzi.git
- dentro estaran las isntrucciones
- pero dentro de la carpeta principal crear un archivo de docker-compose.yml. Que contenga lo siguiente

```
version: "3.8" 
services: hadoop-master: 
image: uracilo/hadoop 
container_name: hadoop-master 
hostname: hadoop-master 
ports: - '50070:50070' - '8088:8088' 
stdin_open: true 
tty: true 

slave_1: 
image: uracilo/hadoop
container_name: hadoop-slave1 
hostname: hadoop-slave1 
stdin_open: true tty: true 
depends_on: - hadoop-master 

slave_2: 
image: uracilo/hadoop 
container_name: hadoop-slave2 
hostname: hadoop-slave2 
stdin_open: true 
tty: true depends_on: - hadoop-master 

slave_3: 
image: uracilo/hadoop 
container_name: hadoop-slave3 
hostname: hadoop-slave3 
stdin_open: true 
tty: true 
depends_on: - hadoop-master 

slave_4: 
image: uracilo/hadoop 
container_name: hadoop-slave4 
hostname: hadoop-slave4 
stdin_open: true 
tty: true 
depends_on: - hadoop-master 

slave_5: 
image: uracilo/hadoop 
container_name: hadoop-slave5 
hostname: hadoop-slave5 
stdin_open: true 
tty: true depends_on: - hadoop-master
```

- levantar los servicios de docker con $docker compose up$
- en otra terminal entrar al ejecutable del master con $docker exec hadoop-master$
- Una vez dentro del ejecutable  iniciar los comandos con $./start-hadoop.sh$
- 