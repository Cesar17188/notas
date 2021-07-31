# Instalación de dependencias con force

Hay un flag que utilizamos para ver el output que retorna sin tener que instalarla en nuestro proyecto.

$npm install react --dry-run$

este comando simula la instalación y te devuelve el output de la instalación

Hay otra forma de instalar paquetes desde el servidor de npm y es con force

$npm install webpack -f$

esta forma de instalación funciona directamente

Se puede cambiar del entorno de producción al entorno del desarrollo directamente en el archivo package.json

Si se elimina la carpeta de node_modules se puede recuperar todos los paquetes corriendo el código

$npm install$ 

que leera el archivo package.json e instalara todas las dependencias que hemos utilizado y se encuentras en el archivo package.json


la última forma de instalar un paquete es instalarlo con una versión especifica

$npm install json-server@0.15.0$