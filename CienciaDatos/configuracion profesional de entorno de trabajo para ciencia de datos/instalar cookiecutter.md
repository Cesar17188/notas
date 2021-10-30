# Instalar Cookiecutter

Es un manejador de plantillas multiplataformal, por lo que las plantillas se pueden utilizar en cualquier lenguaje de programación o formato de marcado.
Además puede ser utilizado como una herramienta de línea de comandos o como una librería de Python

## ¿Cómo funciona cookiecutter?

cookiecutter va a detectar una sintaxis especial en tus documentos, en tus sistemas de carpetas y archivos, ya sea de forma local (ya sea que este dentro de la computadora) o una carpeta que este en la nube (por ejemplo en un repositorio de github). Va a procesar esta estructura, va a ver ciertas variables, va a buscar ciertas variables, va a buscar valores para reemplazar, y finalmente te va a entregar un nuevo proyecto, con la estructura definida en la plantilla subsistituyendo todos esos valores.

Detras de escenas, cookiecutter, funciona con Jinja que es un motor de plantillas que es muy extensible y muy bonito por que te permite escribir plantillas, como si estuvieras escribiendo python. Por lo que si sabes python, escribir plantillas con Jinja se te va a hacer muy simiar, por que su sintaxis se basa en tres bloques principales.

```python
{{cookiecutter.saluda}}
Hola, científico de datos
{% if cookiecutter.eres_asombroso %}
¡Genial, por su puesto que lo eres!
	{%endif%}
{#¡Has aprendido bastante!#}
```

Los bloques de expresión son aquellos donde se definen dos pares de {{}} y dentro vas a tener una variable que quiere que se incluya en tu plantilla.

Los bloques declarativos son aquellos en los que se pueden utilizar condicionales, foor loops o más. Estos se definen por {% % } y dentro se describe la acción que se quiere hacer, y para cerrar este bloque, siempre es necesario colocar un {%endif%} o un {%endfor%}

Finalmente tienes los bloques de tipo comentario, que son los bloques que tienes en tu plantilla pero cuando la corras ya no estarán en tu plantilla. Por lo que son muy útiles para dejar recomendaciones para el futuro.

## Instalar Cookiecuter

1. Es muy facil hacerlo instalando Conda
2. Abrir el bash de Anaconda
3. correr $conda config --add channels conda-forge$
4. crear una ambiente [[crear un entorno virtual]] que contenga a cookiecutter
5. correr $conda create --name cookiecutter-personal cookiecutter=1.7.3$
6. conda te mostrara las dependencias y te hara una pregunta de comprobación
7. das enter
8. empezara a descargar e instalar las dependencias
9. para activar el ambiente correr $conda activate cookiecutter-personal$
10. para desactivar $conda deactivate$
11. Activado el ambiente, hay que definir donde estará alojado el ambiente, esto sirve para tener un control de lo que se hace
12. correr el comando $conda env export --from-history --file environment.yml$ donde ya se habrá definido el todo lo necesario para replicar el análisis


## ¿Cómo utilizar cookiecutter?

- Pegamos el siguiente código en la terminal
- $cookiecutter https://github.com/platzi/curso-entorno-avanzado-ds --checkout cookiecutter-personal-platzi$