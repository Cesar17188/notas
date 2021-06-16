# Modo interactivo

Comandos:  
$ docker run ubuntu (corre un ubuntu pero lo deja apagado)  
$ docker ps -a (lista todos los contenedores)  
$ docker run -it ubuntu (lo corre y entro al shell de ubuntu)  
-i: interactivo  
-t: abre la consola
$ exit (para salir de la consola)

<h1>cat /etc/lsb-release (veo la versión de Linux)</h1>

cuando se crea el sistema opertaivo ubuntu con el comando 
$ docker run ubuntu
Con $docker ps -a$ se despliega el contenedor creado, hay que prestar atención a la columna $command$, ya que es el proceso que corre el contendor al arrancar y en la columna $estatus$ vemos que la salida es 0
En linux cuando hay un comando en progreso al terminar regresa un código de estatus de salida. 0 Significa que todo salio bien.

