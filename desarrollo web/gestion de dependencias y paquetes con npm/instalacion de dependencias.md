# Instalación de dependencias

¿Cómo es la forma de instalar paquetes?

Dentro de la carpeta del proyecto con el cmd
1. crear la carpeta src ($mkdir src$)
2. entrar en la carpeta src ($cd src$)
3. crear el archivo index.js ($touch index.js$)
4. para saber donde te encuentras escribe el comando $pwd$
5. regresar a la carpeta raiz del proyecto ($cd ..$)

## Instalación de dependencias

Estas dependencias son los recursos que vamos a utilizar dentro de los proyectos, sabiendo que hay una gran cantidad de estos recursos. Para poder instalar paquetes de npm por lo general se suele utilizar un solo comando con el paquete requerido.
ejemplo

$npm install moment$

de esta forma se puede instalar, a partir de la versión 5 de npm, por defecto se instala como una dependencia que es requerida para el momento.

$npm install moment --save$

que significa --save: quiere decir que este paquete que se va a instalar es necesario para la producción, hay que tener cuidado al determinar cuando un paquete es requerido en producción y cuando no lo es. De esta forma se puede ver otro flag

$npm install moment --save-dev$

dev: este flag nos dice que este paquete solo es necesario en nuestro entorno local o en el entorno de desarrollo, partiendo de esta diferencia tomaremos las decisiones para instalar las dependencias que requiere nuestro proyecto. Por que es importante no mandar dependencias que no deban estar en producción, y otras que si deben estar en producción


Como se puede ver en la instalación cuando se corre. El programa se conecta a los servidores de npm, descarga el contenido requerido, crea unos archivos necesarios y luego nos da un output de lo que ha sucedido. en el ejemplo ha instalado moment en la versión moment 2.29.1

En nuestro proyecto, dentro del editor vamos a ver la carpeta node_modules y el archivo package-lock.json

Con la creación de la carpeta node_modules el proyecto puede instalar las dependencias dentro de esta carpeta, en nuestro proyecto. Esta carpeta es necesaria para que el proyecto funcione, pero no debe ser enviada a ningún repositorio y debemos incluirla en el .gitignore apenas se crea. Si no se tiene el archivo .gitignore se debe crear. Dentro del archivo .gitignore se debe ingresar $node_modules/*$

Dentro del archivo package.json podemos ver la dependencias instalada. 

hay diferentes formas de hacer instalaciones, 

$npm install date-fns --save-dev$

una ves instalado el paquete regresamos a nuestro editor de código y vemos en el archivo package.json que se a creado una parte que dice $"devDependencies"$ que son las dependencias que existen solo en ambientes de desarrollo.

Hay otros flag que se pueden utilizar como:

$npm i date-fns -D$ (este paquete se va a instalar como un paquete de desarrollo)

$npm i moment -S$ (este paquete se va a instalar como un paquete del proyecto)

Cuando necesitemos que un paquete corra de forma global significa que cuando nosotros trabajamos en un proyecto, podemos instalar un paquete de forma que pueda reconocer cambios en nuestro entorno de trabajo como $nodemon$.
Para instalar un paquete de forma global utilizar el siguiente comando:

$npm install -g nodemon$

Para poder instalar paquetes de forma global debemos hacerlo con permisos, por lo que se debe correr este comando con los permisos de administrador. para linus o mac es:

$sudo npm install -g nodemon$


Para saber que paquetes estan instalados de forma global ingresar este comando:

$npm list -g --depth 0$


