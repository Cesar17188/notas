# Volumenes

Docker nos ofrece más maneras de manejar datos, aqui veremos volumenes o volumens lo cual fue una evolución que ofrece mucha más seguridad.

La parte de disco que es afectada por docker solo puede ser manejados por usuarios privilegiados por el sistema

**Crear un volumen:**  
```
docker volume create [nombre_del_volument]
```

**Listar los volúmenes**  
Para ver todos los volumenes corriendo
```
docker volume ls
```
**Montamos el contenedor especificándole el volumen **  

entre la coma en src y dst no poner espacio. Puede que nos de un error docker: invalid refence format  
docker run -d --name db --mount src=dbdata (que_queremos_montar),dst=(destino) data/db mongo

**Entramo en el cliente de mongo**  
docker exec -it db bash  
mongo

**Borramo el contenedor anteriormente creado**  
docker rm -f db

**Montamos otro contenedor con el mismo nombre, mismo lugar (src,dst)**  
docker run -d --name db --mount src=dbdata,dst=/data/db mongo  
docker exec -it db bash  
mongo

