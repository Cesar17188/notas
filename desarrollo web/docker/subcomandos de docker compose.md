# Subcomandos de Docker Compose

Comandos:  
$ docker network ls (listo las redes)  
$ docker network inspect docker_default (veo la definición de la red)  
$ docker-compose logs (veo todos los logs)  
$ docker-compose logs app (solo veo el log de “app”)  
$ docker-compose logs -f app (hago un follow del log de app)  
$ docker-compose exec app bash (entro al shell del contenedor app)  
$ docker-compose ps (veo los contenedores generados por docker compose)  
$ docker-compose down (borro todo lo generado por docker compose)