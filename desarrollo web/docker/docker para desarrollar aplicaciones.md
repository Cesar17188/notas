# Usando Docker para desarrollar aplicaciones

Comandos:

$ git clone [https://github.com/platzi/docker](https://github.com/platzi/docker)  
$ docker build platziapp . (creo la imagen local)  
$ docker image ls (listo las imagenes locales)  
$ docker run --rm -p 3000:3000 platziapp (creo el contenedor y cuando se detenga se borra, lo publica el puerto 3000)  
$ docker ps (veo los contenedores activos)

Explicación del docker file

![carbon (13).png](https://static.platzi.com/media/user_upload/carbon%20%2813%29-61ed207f-53ce-4792-8c09-8fe7225679be.jpg)

**Usando Docker para desarrollar**  
Ejemplo como utilizar docker para el desarrollo

1.  Creamos una carpeta y nos posicionamos dentro de esa carpeta.
2.  Luego Clonamos un proyecto de github y nos posicionamos dentro del proyecto clonado
3.  Verificamos que los archivos estén allí
4.  Realizamos la construcción de la imagen,

> Parámetro -t o tag : Indica el tag de la imagen a construir.  
> Parámetro . : indica el directorio de trabajo

1.  Verificar que la imagen ha sido creada.
2.  Crear el contenedor basado en la imagen anteriormente creada y:

> Parámetro --rm para que, al detenerse. el contenedor se borre  
> Parámetro -p indicar que el puerto del host:contenedor están asociados.

1.  Comprobar que el contenedor recién creado este activo
2.  Comprobar que el contenedor puede recibir petición desde el navegador, mostrará un error porque la nuestro contenedor no está asociado a ninguna bases de mong.

Ejecución de los pasos

1.  mkdir docker-pj && cd docker-pj
2.  $ git clone [https://github.com/platzi/docker](https://github.com/platzi/docker) && cd docker
3.  ll
4.  code .
5.  $ sudo docker build -t platziapp .
6.  $ sudo docker image ls
7.  $ sudo docker run --rm -p 3000:3000 platziapp
8.  $ sudo docker ps
9.  localhost:3000

**Explicación de docker file**  

![Dockerfile-clase-19.png](https://static.platzi.com/media/user_upload/Dockerfile-clase-19-4abc3fc7-e088-45d5-9f52-05c2b6df5e60.jpg)