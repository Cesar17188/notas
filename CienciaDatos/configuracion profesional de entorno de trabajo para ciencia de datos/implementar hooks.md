# Implementar hooks

Es una herramienta llamada hooks o ganchos, son cosas que se van a generar antes o despues de la plantilla de datos. Por ejemplo virificar que el nombre de un paquete de python que se va a utilizar sea valido. O otro ejemplo es que despues de crear la plantilla de datos y en lugar de utilizar git para manejar las versiones, se puede eliminar esta tarea repetitiva haciendo que cookiecutter las haga cada vez que se inicie el proyecto.

Subproceso para instalar las librerias en requirements.txt

```
subprocess.call(['pip', 'install', '-r', 'requirements.txt'])
```

Excelente y entendido

**Example: Validating template variables**

[Using Pre/Post-Generate Hooks](https://cookiecutter.readthedocs.io/en/1.7.2/advanced/hooks.html)

```
import re
import sys


MODULE_REGEX = r'^[_a-zA-Z][_a-zA-Z0-9]+$'

module_name = '{{ cookiecutter.module_name }}'

if not re.match(MODULE_REGEX, module_name):
    print('ERROR: %s is not a valid Python module name!' % module_name)

    # exits with status 1 to indicate failure
    sys.exit(1)
```

### Código

cookiecutter.json code:

```json
{
    "project_title": "Cookiecutter Personal",
    "project_slug": "{{ cookiecutter.project_title.lower().replace(' ', '_') }}",
    "project_description": "Something cool",
    "project_author_name": "Your name",
    "project_packages": ["All", "Minimal"],
    "python_version": "3.7"
}
```

pre_gen_project.py code:

```python
import os
import sys

project_slug = "{{ cookiecutter.project_slug }}"

ERROR_COLOR = "\x1b[31m" # To change the terminal color
MESSAGE_COLOR = "\x1b[34m"
RESET_ALL = "\x1b[0m"

if project_slug.startswith("x"):
    print(f'{ERROR_COLOR}ERROR: {project_slug=} is not a valid name for this template.{RESET_ALL}')

    sys.exit(1)

print(f"{MESSAGE_COLOR}Let's do it! You're going to create something awesome!")
print(f"Creating project at { os.getcwd() }{RESET_ALL}")
```

post_gen_project.py code:

```python
import subprocess

MESSAGE_COLOR = "\x1b[34m"
RESET_ALL = "\x1b[0m"

print(f"{MESSAGE_COLOR}Almost done!")
print(f"Initializing a git repository...{RESET_ALL}")

subprocess.call(['git', 'init'])
subprocess.call(['git', 'add', '*'])
subprocess.call(['git', 'commit', '-m', 'Initial commit'])

print(f"{MESSAGE_COLOR}The beginning of your destiny is defined now! Create and have fun!{RESET_ALL}")
```