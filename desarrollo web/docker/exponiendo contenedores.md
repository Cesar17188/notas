# Exponiendo contenedores

$ docker run -d --name proxy nginx (corro un nginx)  
$ docker stop proxy (apaga el contenedor)  
$ docker rm proxy (borro el contenedor)  
$ docker rm -f <contenedor> (lo para y lo borra)  
$ docker run -d --name proxy -p 8080:80 nginx (corro un nginx y expongo el puerto 80 del contenedor en el puerto 8080 de mi máquina)  
localhost:8080 (desde mi navegador compruebo que funcione)  
$ docker logs proxy (veo los logs)  
$ docker logs -f proxy (hago un follow del log)  
$ docker logs --tail 10 -f proxy (veo y sigo solo las 10 últimas entradas del log)