# Datos en docker

![](https://i1.wp.com/cdn-images-1.medium.com/max/800/1*bo6IOrBjaHbtkPgTKT08NA.png?w=1170&ssl=1)

**Host:** Donde Docker esta instalado.  
**Bind Mount:** Guarda los archivos en la maquina local persistiendo y visualizando estos datos (No seguro).  
**Volume:** Guarda los archivos en el area de Docker donde Docker los administra (Seguro).  
**TMPFS Mount:** Guarda los archivos temporalmente y persiste los datos en la memoria del contenedor, cuando muera sus datos mueren con el contenedor.