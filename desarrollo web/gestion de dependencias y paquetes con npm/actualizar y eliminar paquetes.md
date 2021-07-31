# Actualizar y eliminar paquetes

Para actualizar o darnos cuentas si hay una actualización de los paquetes instalados.

1. en la terminar vamos a listar los paquetes de este proyecto

$npm list$

Partiendo del listado y sabiendo lo que esta sucediendo en los paquetes corremos el comando

$npm outdate$
Para verificar que paquetes podrían estar desactualizados. nos mostrara la versión instalada, la versión actual y la última versión en los servidores de npm

Tener las dependencias actualizadas de nuestros proyectos nos va a dar la seguridad de trabajar con garantias de que se puede utilizar todas las herramientas sin crashear el código.

El comando para ver todo el output para saber que es lo que esta pasando con el npm

$npm outdate --dd$

para actualizar los paquetes a su última versión correr el código

$npm update$

Hay opciones de actualizar un paquete a su última versión

$npm install json-server@latest$

Como desistalar los paquetes

$npm uninstall json-server$

Como eliminar o desistalar un paquete sin quitarlo del archivo package.json

$npm uninstall webpack --no-save$

El paquete de npm para visual studio code analiza el archivo de package.json lo compara contra la carpeta de node_modules y avisa si uno de estos paquetes no esta instalado, esta ayuda sirve para darnos cuenta de que si bien tenemos paquetes en este archivo no se instalaron correctamente o estamos haciendo un cambio o una versión no esta bien establecida