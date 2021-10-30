# Crear plantillas de proyecto personalizadas

Como se crea una estructura de archivos, carpetas, etc. Utilizando cookiecutter de una forma muy sencilla.

En la terminal seguimos los siguientes pasos:
1. abrimos la carpeta que contiene cookiecutter [[instalar cookiecutter]]
2. desplegamos el contenido en vscode con el comando $code .$
3. nos dirigimos a vscode y eliminamos nuestra carpeta de prueba de cookiecutter
4. creamos una nueva carpeta que tendra el contenido que estara dentro de la plantilla. Todo lo que este por fuera no importara
5. creamos la carpeta con el siguiente nombre por los comandos de jinja ${{cookiecutter.project_slug}}$
6. dentro de esta carpeta se puede definir archivos o un readme.md, se puede crear carpetas para datos, notebooks, etc. Es decir puedes definir toda la estructura de carpetas

dentro del README.md se puede poner varaibles que se pueden poner dentro de los archivos de ambiente siempre con la estructura {{ cookiecutter. }} antes del nombre de la variable

```
# {{ cookiecutter.project_title }}

  

By: {{ cookiecutter.project_author_name }}

  

{{ cookiecutter.project_description }}

  

## License
```

Se puede crear nuevos archivos, como un archivo de ambiente donde estaran las dependencias que se necesitaran para correr el ambiente. 