# Deteniendo contenedores correctamente: SHELL vs. EXEC

Comandos:  
$ docker build -t loop . (construyo la imagen)  
$ docker run -d --name looper loop (corro el contenedor)  
$ docker stop looper (le envía la señal SIGTERM al contenedor)  
$ docker ps -l (muestra el ps del último proceso)  
$ docker kill looper (le envía la señal SIGKILL al contenedor)  
$ docker exec looper ps -ef (veo los procesos del contenedor)

**Diferencias entre RUN, CMD y ENTRYPOINT**  
[https://dockertips.com/comandos-run-cmd-y-entrypoint-en-el-dockerfile](https://platzi.com/clases/2066-docker/32867-deteniendo-contenedores-correctamente-shell-vs-exe/url)