# Iniciar un proyecto con npm

Es muy importante iniciar un proyecto cada vez que estas desarrollando una aplicación web o un desarrollo de software o lo que se este creando con código. 

Pasos

1. Ingresar a la términal
2. Ubicarse en la carpeta donde se va a crear el proyecto
3. ingresar a la carpeta donde se va a crear el proyecto
4. se debe iniciar con un $git init$ el repositorio local para posteriormente enviarlo a un manejador de versiones online como github, o bitbucket o gitlab
5. Para iniciar el proyecto se debe ingresar el comando $npm init$, el cual nos permite crear el archivo package.json del proyecto que nos permite tener una configuración establecida, una descripción del proyecto y ciertos valores que necesita
6. Se observara la documentación inicial sobre el manejo de npm
7. Se debe ingreesar el nombre del paquete en el que estas trabajando (se da una referencia de nombre) (dar enter)
8. Hay una versión inicializada (dar enter)
9. Hay  una descripción donde pondermos la descripción del proyecto en el que estamos trabajando
10. Hay un entry point, es muy importante ya que es el punto de entrada de nuestro proyecto por lo que se debe establecer el directorio donde se lo va a encontrar y el nombre que va a tener (src/index.js)
11. Hay un test command, se puede saltar y configurar esta opción más adelante
12. hay un git repositoriy se pude saltar de forma automatica
13. hay keywords, son palabras en las que se enfoca el proyecto como por ejemplo: javascript, node, package
14. Hay un author donde se debe dejar el autor del proyecto y si se quiere el email entre <> (Cesar Armendariz <cesareli17188@gmail.com>)
15. Hay licencias las cuales se puede aplicar a los proyectos pero por lo general se trabaja con MIT la cual permite trabajar con este tipo de recursos open source
16. Despues de aceptar todo aparece la información ordenada y lista para ejecutarse con el último enter
17. para ver el documento creado abrir la carpeta en un editor de código (code .)

## Otras forma de iniciar
Si queremos emitir un mvp rápido, podemos utilizar lo siguiente

1. npm init -y 

se creara la estructura rapida sin pedir información


otra forma con variables declaradas es

1. npm set init.author.email "cesareli17188@gmail.com"
2. npm set init.author.name "Cesar Armendariz"
3. npm set init.license "MIT"
4. npm init -y 
