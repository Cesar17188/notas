# Cómo funciona realmente un sitio web

1.- Los protocolos se encargan de manejar todas las peticiones que hacen la páginas de internet desde tu navegador hacia los servidores DNS, éstos transforman la dirección de la página web en una dirección IP y tu navegador se conecta a esa IP.

2.- Una vez se tiene la dirección IP el navegador envía un HTTP request en donde envía información con las características del cliente y los requerimientos del mismo, es decir, Host requerido, página del sitio que necesita, tipo de navegador, versión del navegador, etc.

3.- El servidor envía los resultados por medio del mismo protocolo HTTP en forma de un HTTP Response en donde manda todo el HTML del sitio web así como otros datos que el navegador necesita.

4.- Por último se cargan los assets de nuestro sitio web y es aquí donde se descargan imágenes, sonidos, etc.


1.  El navegador le hace una petición al sistema operativo para ver si tiene una versión en caché.
2.  GET le pide al servidor los datos y se los envía a la IP del servidor.
3.  El servidor responde con un número, como 200 (OK), 404 (No encontrado), 500 (error del servidor).
4.  Assets request.

La cookies son datos guardados en variables y van en el request y en el response del servidor. Las cookies pesan, entonces es importante limitarlas para no afectar la velocidad de las peticiones.