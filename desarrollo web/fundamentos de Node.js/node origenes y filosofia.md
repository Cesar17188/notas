# Node: orígenes y filosofía

Node.js es una de las formas más rápidas de desarrollar, ejecutar y correr código en servidor de forma muy escalable.

## ¿Qué es Node.js?
Es un entorno de ejecución de JavaScript fuera del navegador. Se crea en 2009 orientado a servidores. Por lo que no se necesita de un buscador como (googlechrome, firefox, opera) para ejecutar javascript. Puedes ejecutarlo en servidores, para construir herramientas, IOT o en cualquier consola o dispositivo que se tenga. Lo que permite correr servidores de forma asíncrona

## Características
* Concurrencia 
	* Monohilo, con entradas y salidas asíncronas. [[asicronismo js]]
	* Un proceso por cada núcleo del procesador.
* Motor V8 [[V8, el JS engine de chrome]]
	* Entorno de ejecución de JS creado por Google, y libre desde 2008.
	* Escrito en C++
	* Convierte Js en código máquina en lugar de interpretarlo en tiempo real
* Módulos
	* Todo lo que no sea sintaxis de programación, son módulos [[acerca de npm, paquetes y modulos]]
	* Muchos módulos vienen por defecto en el paquete de Node
	* Puedes crear tus propios módulos
* Orientado a eventos
	* Hay un bucle de eventos que se ejecuta constantemente
	* Puedes orientar tu código de forma reactiva