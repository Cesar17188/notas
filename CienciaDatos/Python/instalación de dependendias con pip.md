# Instalación de dependecias con pip (Package installer for Python)

## ¿Qué es pip en python?
Pip es un instalador de dendencias (o instalador de paquetes) que permite instalar módulos que no vienen pre instalados con python. 
Por ejemplo
* Requests
* BeautifulSoup4
* Pandas
* Numpy
* Pytest

## Si se elimina pip
* aplicar el comando: easy_install.exe pip

## Pasos para instalar dentro del entorno virtual
* Todos los módulos se van a instalar en nuestro entorno virtual
* para instalar cualquier módulo el código es: pip "módulo"
por ejemplo 
* pip install pandas

### Para ver todos los módulos instalados
* pip freeze

### Para compartir nuestro proyecto (las dependencias) si lo subieramos a github

* se debe guardar un archivo con todos los módulos con sus respectivas dependecias para ver cual versión de esos módulos se esta utilizando. Para lo cual hay que escribir el siguiente código: pip freeze > requirements.txt
* Se guardara un archivo con el nombre requirements.txt para ver que se creo ejecutar el código: ls
* Para ver que hay dentro del archivo ejecutar el código: cat requirements.txt

### Para instalar los módulos desde un proyecto externo

* Descargar el proyecto en un entorno virtual
* Revisar que tenga el archivo requirements.txt
* Instalar los módulos con el código: pip install -r requirements.txt


## Hay otros manejadores de instaladores de paquetes

* PYENV