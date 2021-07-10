# Configuración del entorno de desarrollo

1. Entrar a un navegador y buscar las herramientas necesarias para empezar
	1. github.com (red social de programación, plataforma web donde colaboramos con otros equipos del mundo)
	2. Github tienes la cuenta de comunidades (platzi en este caso), aqui estaran todos los cursos que se han trabajado con código
	3. vamos a crear un nuevo repositorio en este caso con el nombre platzi-curso-practico-javascript
	4. podemos poder una descripción
	5. hay que ver si queremos crear un repositorio publico o privado (hay que seleccionar cualquier opción)
	6. La primera de las últimas 3 opciones es sobre si queremos crear un readme file (es un archivo donde se puede poner toda la documentación, instrucciones o una descripción detallada sobre el proyecto)
	7. La segunda es sobre un .gitignore (nos permite decirle a git que archivos o carpetas no queremos incluir en el repositorio)
	8. El tercer paso es la licencia (trata sobre la autoria del proyecto ya que al ser creado el proyecto con una licencia cualquiera sabra de donde salió el código). Hay muchas licencias es necesario saber cual es la que va con el proyecto. En los casos de opensource generalmente se utiliza la licencia MIT que es la más básica
	9. Crear el repositorio
2. Conectar el repositorio de GITHUB con nuestro entorno de trabajo en GIT
	1. Dentro de nuestro repositorio en GITHUB del proyecto creado, damos clic en el botón de code con la opción de SSH(llaves públicas y privadas es recomendable tenerlas), copiamos la url
	2. Vamos al editor de código para clonar el proyecto (se puede hacer desde una terminal ubicando donde nosotros queramos el proyecto) desde la terminal de visual studio code
	3. ubicamos la carpeta donde queremos guardar el proyecto
	4. escribimos el código $git clone <repositorio>$ y damos enter
	5. mi proyecto de git y mi repositorio en github quedan conectados y podemos traer todos los archivos e incluso las personas que estan colaborando en el proyecto. Ademas permitira enviar desde mi computadora los cambios que haga
	6. entramos a la carpeta con el código $cd <nombre de la carpeta del proyecto>$
	7. traer la carpeta al editor de código al area de trabajo 
		1. se puede traer desde el open folder o
		2. conectar el repositorio con la carpeta con el comando en la terminal $code ./ -r$ que indica con code ./ que abra desde la ubicación actual y el -r que reutilice si la pantalla del editor si ya esta abierto.
		3. Se puede incluir carpetas en el git ignore llendo al documento .gitignore y en la parte final añadirlas con la ubicación de esa carpeta o archivo. Es buena práctica incluir un comentario sobre de que trata ese archivo o carpeta antes de incluirlo en el gitignore



La extensión de Visual Studio Code para darle colorsitoss diferentes a cada proyecto donde trabajamos se llama [Peacock](https://www.peacockcode.dev/guide/#overview) (de John Papa).

Además, aquí puedes ver los atajos de teclado para VSCode:

-   Windows: [https://code.visualstudio.com/shortcuts/keyboard-shortcuts-windows.pdf](https://code.visualstudio.com/shortcuts/keyboard-shortcuts-windows.pdf)
-   macOS: [https://code.visualstudio.com/shortcuts/keyboard-shortcuts-macos.pdf](https://code.visualstudio.com/shortcuts/keyboard-shortcuts-macos.pdf)
-   Linux: [https://code.visualstudio.com/shortcuts/keyboard-shortcuts-linux.pdf](https://code.visualstudio.com/shortcuts/keyboard-shortcuts-linux.pdf)