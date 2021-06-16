# ¿Cómo funciona docker?

![](https://ualmtorres.github.io/SeminarioDockerPresentacion/images/DockerEngine.png)

Componentes DENTRO del circulo de Docker:

-   Docker daemon: Es el centro de docker, el corazón que gracias a el, podemos comunicarnos con los servicios de docker.
-   REST API: Como cualquier otra API, es la que nos permite visualizar docker de forma “gráfica”. (expone la interfaz necesaria para poder comunicarse con el _docker daemon_).
-   Cliente de docker: Gracias a este componente, podemos comunicarnos con el corazón de docker (Docker Daemon) que por defecto es la línea de comandos.

Dentro de la arquitectura de Docker encontramos:

1.  Contenedores: Es la razón de ser de Docker, es donde podemos encapsular nuestras imagenes para llevarlas a otra computadora, o servidor, etc.
2.  Imagenes: Son las encapsulaciones de x contenedor. Podemos correr nuestra aplicación en Java por medio de una imagen, podemos utilizar Ubuntu para correr nuestro proyecto, etc.
3.  Volumenes de datos: Podemos acceder con seguridad al sistema de archivos de nuestra máquina.
4.  Redes: Son las que permiten la comunicación entre contenedores.