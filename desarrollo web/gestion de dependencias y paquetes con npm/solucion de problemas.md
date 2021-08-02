# Solución de problemas

Cuando se trabaja con proyectos, puedes encontrar muchisimos errores, que pueden ser desde errores de configuración, sistema operativo, espacios, no configurar correctamente tu github, etc, etc

Para poder solucionar estos errore que son ajenos a la aplicación de node podemos hacer lo siguiente.

Activar el modo verbose

para activar el modo verbose correr el siguiente comando $npm run build --dd$ lo cual nos permitira ver todo lo que esta sucediendo.

Esto nos permitira ver los errores que esten pasando dentro del proyecto y nos permite debuggear el proyecto.

En caso de que las dependencias con las que se este trabajando no sean las correctas ya sea por desactualizaciones o por  no uso de las mismas, se puede eliminar la carpeta node_modules e instalar denuevo las dependencias con el comando $npm install$.

O se puede limpiar el cache con el comando
$npm cache clean --force$
y para verificarlo podemos correr el comando
$npm cache verify$

Uno de los errores que tambien se puede dar es que unos de los paquetes este corrupto o incompleto y para esto se puede usar el siguiente comando.

primero eliminamos las carpetas node_modules
en mac o linux
$rm -rf node_modules$
en windows
hay que instalar el paquete de forma global con permisos
$npm install -g rimraf$
con el paquete instalado se puede borrar la carpeta node_modules
$rinraf node_modules$
una ves que esta carpeta este eliminada se puede comprobar con el comando $ls$ e instalar las dependencias denuevo con el comando $npm install$