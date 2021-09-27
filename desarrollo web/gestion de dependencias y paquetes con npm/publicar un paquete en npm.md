# Publicar un paquete en NPM

Antes de publicar el paquete debe provarse de forma local para garantizar el funcionamiento que queremos.

para esto vamos a usar un recurso que da NPM para hacer un link a lo que queremos para poderlo implementar ya sea en otros proyectos internos o instalarlo de forma global y poderlo utilizar.

los comandos son los suguientes
1. ubicarnos dentro de la carpeta donde esta el paquete con el comando $pwd$ sabremos si estamos ahi
2. Utilizando permisos de administrador corremos el siguiente comando $npm link$
3. Para llamarlo de forma global vamos a ejecutar el comando que nosotros mismo le pusimos $random-msg$ y podremos ver el resultado.

## otra forma de instalarlo
desde el path

1. ubicarse en el path
2. con el comando con permisos $npm install -g <path>$ y se instala

## publicar paquetes en la red

1. crear una cuenta en la pagina oficial de npm
2. logearnos desde la terminal con los sigueintes comandos

$npm adduser$
$Username: <username>$
$Email: <email>$
3. se logearea desde la terminal
4. con el comando $npm publish$ esto leera la configuracion del package.json y esto se publicara dentro del npm. Que generara documentacion