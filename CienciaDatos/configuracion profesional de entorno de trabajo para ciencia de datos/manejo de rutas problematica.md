# Manejo de rutas: problemática

El manejo de archivos y como solucionar problemas es de lo que tratará este módulo

## Problemática

resulta que estando trabajando en cualquiera de los 3 S.O. actuales (windows, linux, mac) o incluse wsl (windows subsystem for linux) pueden haber diferencias entre como estos S.O. manejan los archivos.

Por ejemplo uno muy distintivo es windows que usa '/' en lugar de '-' por lo que esto hace que las rutas no sean compatibles entre sistemas operativos.

Por lo que cuando decides que quieres iniciar un nuevo proyecto, necesitas pensar en que no solo vas a estar tu, va a haber otras personas con las que debes trabajar y es posible que alguna de ellas utilice otro S.O. 

Para solventar esto hay que crear un entorno de trabajo con los siguientes pasos:

1. abrir la terminal
2. crear un proyecto nuevo puedes utilizar una nueva carpeta, creada con el comando $mkdir$
3. pero como ya tenemos la plantilla lista utilizamos el comando $cookiecutter$ [[distribuir plantilla de proyecto]] para evitar la creación del nuevo proyecto
4. para abrir el proyecto utilizamos el comando $code [nombre del proyecto]$
5. luego desde la terminal del proyecto y teniendo el archivo $environment.yml$ corremos el comando $conda env create --file environment.yml$
6. luego activamos el ambiente con $conda activate$ [nombre del ambiente]
7. luego vamos a nuestro notebook de jupyter
8. en la esquina superior derecha encontraras $select kernel$ clic en select kernel y seleccionar el ambiente con el nombre creado
9. Si no aparece recargar visual studio code
10. Con esto ya puedo ingresar cualquier comando de python que sea valido
