# Conceptos fundamentales de Docker: imágenes

**Profundizando en el concepto de imágen**  
Es bueno profundizar un poco más en el concepto de una imágen en Docker para entender su función, para posteriormente poder realizar una por nuestra cuenta desde 0, cuando no haya una imágenque cumpla con nuestras necesidades.  
.  
**Imágen**  
Una imágen contiene distintas capas de datos (distribución, diferente software, librerías y personalización).  
.  
Podemos llegar a la conslusión, que una imágen se conforma de distintas capas de personalización, en base a una capa inicial (base image), la dicha capa, es el más puro estado del SO.  
.  
La siguiente ilustración nos mostraría la representación gráfica, del concepto de una imágen en Docker.

![image-in-docker](https://static.packt-cdn.com/products/9781788992329/graphics/0ee3d4cf-2133-4143-a7c4-690274483841.png)

Si observamos, partimos desde la base del SO, y vamos agregando capas de personalización hasta obtener la imágen que necesitamos:

1.  distribución debian
2.  se agrega el editor emacs
3.  se agrega el servidor Apache
4.  se agregan los permisos de escritura para la carpeta /var/www de Apache

_Hay que tener en cuenta, que todo parte del Kernel de Linux, en caso de utilizar alguna distrubución de Linux_  
.

**Historico de una imágen**  
Podemos observar la historia de nuestra imágen, con el siguiente comando

```bash
$ docker history [imagen]
```

De esta manera podemos ver las capas de personalización que fuerón agregadas, para la construcción de la imágen que conocemos.

## Agregar nuevas imagenes al docker
Por defecto al correr la linea de código docker pull, va a utilizar la página docker hub https://hub.docker.com/ para traer las imagenes de donde se van a crear los sistemas base en los nuevos contenedores. Sin embargo podemos importar las imagenes desde cualquier repositorio que queramos

```
docker pull ubuntu:20.04
```


**Las imágenes son plantillas del cual Docker crea contenedores**

Listar imágenes

`docker image ls`

Especifica la versión(tag) de la imagen que se quiere descargar de Docker Hub  
`docker pull ubuntu:21.04`