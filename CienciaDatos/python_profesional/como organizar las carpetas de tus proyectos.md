# Cómo organizar las carpetas de tus proyectos

📁Un **módulo** es cualquier archivo de Python. Generalmente, contiene código que puedes reutilizar.

🗄 Un paquete es un conjunto de módulos. Siempre posee el archivo **`__init__.py`**.  
Una ejemplo de organizar los archivos de 🐍Python es de la siguiente manera.
- ![[Pasted image 20210811163137.png]]

Si están usando WSL o una terminal Unix, pueden instalar con `sudo apt-get install tree` para ver un árbol de sus carpetas.  
Luego puedo ingresar a la carpeta de mi proyecto y ejecutar el comando `tree`.

Se vería algo así:

![](https://i.imgur.com/qCVtw4H.png)

Yo pongo `tree -I venv` para ignorar la carpeta venv que esta llena de cosas. Si no lo pongo verás todos los directorios de tu proyecto.

![](https://i.imgur.com/H9wQKS3.png)