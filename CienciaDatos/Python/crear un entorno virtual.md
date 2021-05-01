# ¿Cómo crear un entorno virtual?

* Ingresamos a la consola de preferencia una que maneje un entorno parecido a linux
* Dirigimos al directorio donde vamos a guardar el entorno virtual
* Inicialiamos nuestro control de versiones git como el comando:  git init
* Creamos el entorno virtual llamando al módulo venv(virtual environment) con el código: py -m venv "nombre del entorno"
* Al momento se va a crear una carpeta con un python aislado donde se podra instalar los módulos que necesitamos sin dañar a los módulos globales o de otros entornos virtuales
* Para mirar el entorno virtual creado poner el código: ls
* Para ver que hay dentro del entorno virtual el código: ls "nombre del entorno virtual"
* Cada entorno virtual tendra la carpeta Scripts que es la que se utiliza para arracar el entorno virtual 
* *Para activar el entorno virtual en un sistema linux o mac ingresar el código: source "nombre del entorno virtual"/bin/activate*
* *Para activar el entorno virtual en un sistema windows ingresar el código: . \"nombre del entorno virtual"\Scripts\activate*
* Esto mostrara el entorno virtual que se esta utilizando 
* Para salir del entorno virtual escribir el código: deactivate
* Para acortar el código de ingreso es util crear un alias y para ello se debe escribir el código: alias "nombre del alias"=.\"nombre el entorno virtual"\Scripts\activate    (esto funciona en un sistema windows)
* Luego escribir en la consola el código: "nombre del alias"

Ahora es necesaria la [[instalación de dependendias con pip]] para trabajar con el entorno virtual