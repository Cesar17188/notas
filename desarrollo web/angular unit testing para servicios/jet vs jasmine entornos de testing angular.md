# Jest vs. Jasmine: entornos de testing para Angular

Jasmine: es un framework de pruebas
Karma: es un test runner (corre las pruebas)

Karme corre por detras por lo que solo debemos pooner atención en Jasmine donde escribiremos las pruebas.

El framework más famoso de pruebas actualmente es Jest

¿Porqué no se hacen las pruebas en Jest?
Angular viene preconfigurado para hacer las pruebas en Jasmine por lo que no se deben preocupar por nada.

Angular maneja muchos patrones por si mismo, por ejemplo con un comando puedes instalar una PWA (progressive web app) o puedes confirgurar un service side rendering.

En framework de testing manejan la misma estructura por lo que no hay que procuparse del framework a utilizar. En especial cuando hablamos de código JS

Para poder inciar seguiremos los siguientes pasos
1. Crear un proyecto desde el cmd
	1. Verifica si tienes instalado el CLI de Angular
```
	ng --version
```

 2. Crear el nuevo proyecto
```
ng new ng-testing-services

//respuesta a las preguntas
yes
scss
```

2. Ingresamos al proyecto y lo abrimos en visual studio code

```
cd ng-testing-services

code .
```

3. Nos vamos a fijar en archivos que no nos habiamos fijado previamente

1. karma.config.js: Es la configuración del test running, por eso tiene un paquete para jasmine y uno para chrome, debido a que las pruebas se realizan contra un navegador, por lo que karma lanza las pruebas contra un navegador. Cabe reslatar que se puede cambiar de navegador 
2. Karma automaticamente va a leer todos los archvios .spec.ts por que son especificaciones de como ese servicio o componente debería funcionar. Aqui se puede encontrar varias pruebas que ya corren


Como correr pruebas

Vamos a la terminal y corremos el siguiente comando
```
ng test
```

posteriormente observamos las pruebas corridas en karma

Si estamos en wsl dentro de windows es necesario instalar la versión estable más reciente de google chrome y hacer unos cambios en el archivo karme.conf.js

1. dentro del terminar de wsl con el usuario root corremos los siguientes códigos uno por uno

```
sudo apt update && sudo apt -y upgrade && sudo apt -y autoremove

wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb
sudo apt -y install ./google-chrome-stable_current_amd64.deb

google-chrome --version
```

2. cambiamos el código de karma.conf.js
```js
    browsers: ['ChromeHeadless'],
```

3. corremos las pruebas y visualizamos si funciona