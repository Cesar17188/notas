# Instalando Visual Studio Code

Pues que comience la aventura y digo aventura porque te darás cuenta de lo emocionante que será poder trabajar 4 lenguajes de programación en un solo entorno de desarrollo y sí, precisamente eso es lo que nos resuelve Visual Studio Code el cual será nuestro campeón en este curso.

Visual Studio Code lo puedes encontrar en las tres versiones básicas de Sistema Operativo (Windows, Mac y Linux) y lo puedes descargar directo en este enlace: [https://code.visualstudio.com/download](https://code.visualstudio.com/download). Es muy ligero y basta con un Siguiente, siguiente, siguiente para instalar.

![1.png](https://static.platzi.com/media/user_upload/1-837d8602-6e03-4ca8-8dd4-645186ad5625.jpg)

Cuando la instalación haya finalizado verás algo como esto:

![2.png](https://static.platzi.com/media/user_upload/2-075cef8f-63d8-482b-b999-b8edc2d7413c.jpg)

¡Súper! Todo salió bien. Ahora pasemos a configurarlo para cada lenguaje.

Primero ubica la sección de **Extensiones** o en inglés **Extensions**, además de la barra de Search porque estaremos buscando la extensión para cada lenguaje.

![3.png](https://static.platzi.com/media/user_upload/3-212e4876-a8e1-4935-a68a-ca39b650c87f.jpg)

## Java

En la barra de Search Extensions escribe: **Java Extension Pack** y da clic en el botón verde **Install**.

![4.png](https://static.platzi.com/media/user_upload/4-005f7353-de0b-41d3-9c71-3a232ebc9d88.jpg)

Ahora, para tener una mejor experiencia en Debugging, instala el Debugger for Java, el cual encuentras siguiendo el procedimiento anterior.

![5.png](https://static.platzi.com/media/user_upload/5-ef8920b2-6561-4ad0-aa35-7b8d95864e77.jpg)

Listo, terminamos con Java. Aprende más en este enlace: [https://code.visualstudio.com/docs/languages/java](https://code.visualstudio.com/docs/languages/java)

Ahora vamos por Python.

## Python

Comencemos instalando Python en nuestra computadora. Dirígete al sitio [python.org](https://www.python.org/) y dale clic en el botón de Descargar.

![6.png](https://static.platzi.com/media/user_upload/6-3b59a5d1-1066-4568-8932-07d4e396ebd7.jpg)

Ve de la mano con el asistente hasta finalizar la instalación:

![7.png](https://static.platzi.com/media/user_upload/7-7735af7a-c904-4ba5-89eb-2dac0034b050.jpg)

Terminaremos la configuración de Python en Visual Studio Code más adelante. Aprende más [aquí](https://code.visualstudio.com/docs/python/python-tutorial).

Mientras tanto sigamos con PHP.

## PHP

Primero necesitamos instalar el intérprete de PHP, la forma más fácil es descargando XAMPP:

[Descarga XAMPP](https://www.apachefriends.org/es/index.html)

Puedes descargarlo tanto para Linux, Windows o macOS.

![XAMPP.png](https://static.platzi.com/media/user_upload/XAMPP-37f0c5f9-3db1-4bc2-9a4a-67477307f5fb.jpg)

Una vez descargado simplemente debes abrirlo e instalarlo dando click al botón de “Next” como cualquier programa normal. Si te sale una ventana de permisos de Firewall simplemente permite ambas opciones:

![Captura de pantalla de 2021-09-10 10-33-21.png](https://static.platzi.com/media/user_upload/Captura%20de%20pantalla%20de%202021-09-10%2010-33-21-b52d96fc-a6e5-4274-88cf-143ea59a24d2.jpg)

Con el intérprete instalado, para configurar PHP buscaremos la extensión **PHP Server** y pulsamos “Instalar”

![8.png](https://static.platzi.com/media/user_upload/8-d8333727-9468-422e-9861-3f123f4ceef9.jpg)

Ahora debemos asegurarnos de que PHP y la extensión estén conectados. Para ello, en Visual Studio Code nos vamos a settings:

![settings.png](https://static.platzi.com/media/user_upload/settings-9dd9c8e7-1d75-4bf8-ba48-933a3cdd6fdc.jpg)

Y aquí buscamos “PHP Server”, nos debería aparecer algo como esto:

![php path.png](https://static.platzi.com/media/user_upload/php%20path-03ea9b58-9ee7-4d60-ba22-158b5336f264.jpg)

-   En el apartado `Phpserver: PHP Config Path` debe decir: `C:\xampp\php\php.ini`.
-   En el apartado `Phpserver: PHP Path` debe decir: `C:\xampp\php\php.exe`.

❗ _Estas rutas pueden variar si durante la instalación de XAMPP cambiaste el directorio de instalación, o si tu Windows está instalado en otro disco que no sea el disco `C:`._

¡Con esto ya tienes PHP instalado!. Puedes aprender más en la ruta de [Desarrollo Web Backend con PHP](https://platzi.com/desarrollo-php/)

## JavaScript

En este caso no necesitamos instalar absolutamente nada, utilizaremos el editor con su configuración por defecto.

## Comencemos nuestro proyecto

Ya está todo listo, ahora dejemos creado el proyecto.

Para esto seleccionaremos la opción **Add workspace folder**

![9.png](https://static.platzi.com/media/user_upload/9-a86b7cd9-2d62-4184-a470-03b90521e916.jpg)

A continuación creamos una carpeta llamada **CursoPOOUber** y damos clic en Add para finalizar. Ahora generemos esta estructura de carpetas para manejar los documentos correspondientes al lenguaje de programación:

![10.png](https://static.platzi.com/media/user_upload/10-a040f297-dbba-4d4d-87e3-0282cd627ed3.jpg)

Ahora que tenemos listo nuestro sistema de archivos terminemos la configuración de Python en VSC, vamos al menú View -> Command Palette y escribimos python “Seleccionar intérprete”, tal como se muestra en la figura.

![11.png](https://static.platzi.com/media/user_upload/11-0e211cee-45b0-445e-9e3b-a7b4f04a0d8b.jpg)