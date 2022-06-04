# Cómo funcionan las computadoras y los teléfonos móviles
![[Pasted image 20211226154611.png]]


Cuando los datos viajan por la red para identificar el proceso existe lo que es llamado el modelo OSI que consta de 7 capas:  
1.-Fisica  
2.-Enlace de Datos  
3.-Red  
4.-Transporte  
5.-Sesión  
6.-Presentación  
7.-Aplicación

Al realizar la comunicación los datos van subiendo o bajando las capas que los van encapsulando en el protocolo según sea el caso.  
La Capa 4 de Transporte utiliza los protocolos TCP y UDP en el que la diferencia es que TCP va orientado a la conexión confiable y la integridad de los datos.

Cuando mandas un correo o una imagen viaja por TCP porque tienen que llegar los bits completos, si algo se pierde en el camino, se vuelve a reenviar el datagrama.  
Cuando realizas una videollamada o ves un video en Youtube los datos viajan por UDP ya que si se pierden datos en el camino son casi imperceptibles y estar reenviando los datos por cada error seria mas notable al verse lento un video.

![[Pasted image 20211226154736.png]]


Idea básica al escribir y enviar un mail:

1.  Escribimos el mail XD
2.  Apretamos enter para enviar el mail.  
    2.1. Al apretar enter estamos enviando una señal eléctrica desde el teclado  
    2.2. Esta señal es enviada a la motherboard, la motherboard la envia al CPU  
    2.3. La CPU recibe la señal del teclado y la envia al sistema operativo  
    2.4. El sistema operativo (a través de drivers, que son softwares que interpretan las señales eléctricas de los periféricos) interpreta la señal eléctrica y la envía al navegador (pues sabe que nosotros queriamos enviarla ahí por donde apretamos el enter (mientras estabamos en el navegador)  
    2.5. Nosotros cuando estamos en una pestaña de chrome en realidad estamos en un html, un html posee uno o varios script, y ahí un script que esta preparado para hacer algo al momento de pulsar la tecla enter (al momento que ocurra el evento “Pulsar tecla enter”), el cual va a hacer pues hemos apretado a tecla enter.  
    2.6. Javascript entiende que al ocurrir el evento enter tiene que hacer algo con el mail que hemos escrito.  
    2.6.1. AJAX permite enviar datos al servidor (el mail en este caso) y que la pagina no se recargue. AJAX es un API (interfaz de programación), que, entre sus multiples funciones, encapsula los datos que deseamos enviar de una manera que luego el servidor comprendera. La forma de encapsular los datos se denomina formato. AJAX encapsula el mail en un formato llamado JSON  
    2.6.2. AJAX envía el mail en formato JSON a través del protocolo REST (es un conjunto de reglas de como se envían los datos a un servidor) a través de HTTP (esta incluido en REST).  
    2.6.3. HTTP y HTTPS son protocolos de transferencia de texto. HTTPS es más seguro porque permite que solo al servidor al cual estamos enviando los datos pueda interpretar la información, solo el receptor final podrá ver los datos que enviamos. De esta manera se evita que alguien se pueda meter en el medio de al transferencia y ver los datos. Los datos se envían a una dominio DNS, que es la dirección de un servidor  
    2.7. El servidor recibe los datos en forma de señales eléctricas, el sistema operativo del servidor (en general linux(muerte al capitalismo 😛 )) a través de ethernet, transforma los datos que están encapsulados según el protocolo TCP/IP. Este protocolo luego crea los datos hacia el protocolo HTTP, HTTP es recibido por un servidor de HTTP de linux.  
    2.8. El servidor HTTP ahora permite que los programas en el backend procesen la información recibida según corresponda. Los datos procesados son guardados en una base de datos para luego poder acceder a estos datos.  
    2.9. El mail ahora si es enviado al dominio que sigue al @.  
    2.10. El mail ahora va al servidor de mail del dominio que se envía, este lo envía a la base de datos del mail que corresponde (el que esta previo al @), es decir va a la bandeja del receptor.  
    2.11. La bandeja del receptor recibe una notificación  
    2.12. La bandeja envía una notificación a un servidor de notificaciones, el servidor de notificación avisa a nuestro celular que se ha recibido un mail.
3.  El mail fue envía y el receptor fue notificado a su celular.

Más claro échale agua 😛

NOTA: Los DNS es una base de datos que relaciona un nombre con un IP

Glosario:
**AJAX**: Asynchronous Javascript And XML  
**JSON**: Javascript Object Notation  
**REST**: Representational State Transfer  
**HTTP**: Hypertext Transfer Protocol  
**FTP**: File Transfer Protocol  
**SSH**: Secure Shell  
**DNS**: Domain Name System  
**TCP**: Transmission Control Protocol  
**IP**: Internet Protocol  
**SMTP**: Simple Mail Transfer Protocol  
**POP3**: Post Office Protocol  
**UDP**: User Datagram Protocol  
**SoC**: System on a Chip  
**ASCII**: American Standard Code for Information Interchange

```
la nube no existe.

1. dar enter para enviar el email.
2. al presionar el botón, se envía una señal eléctrica a la tarjeta madre.
3. la señal es intervenida por el CPU.
4. una vez la CPU recibe la señal la envía a una capa más arriba de electricidad donde opera el Sistema  Operativo.
5. el Sistema operativo tiene software especializado para entender las señales eléctricas enviadas. (Drivers)
6.  El sistema analiza el "Estado" y sube otra capa más de software hasta el navegador.
7. El navegador entiende otra capa de software aún más arriba, donde se corre Internet.
8. El Internet (nivel usuario) usa tecnologías de FrontEnd que son JavaScript, HTML  y CSS.
9. Ocurre un "evento" que es lo que dispara o provoca que algo ocurra.
10. JavaScript va a encapsular todo lo que escribimos para enviarlo a la "Nube".
11. JavaScript usa un API (Application Program Interface).un API  es una "cosa" que usan los programadores para comunicarse entre sí sin hablar entre ellos, algo así como el dinero en la sociedad.
12. Los Navegadores usan un API llamado AJAX (Asynchronous Java And XML).
13. Con AJAX se puede enviar a través de un navegador cualquier cosa a un servidor sin necesidad de Recargar la página.  
14. Se puede encapsular de muchas maneras con los "Formatos de Archivo".
15. Un formato de Encapsulamiento popular es JSON(JavaScript Object Notation).
16. Para poder enviarse a un servidor  es necesario usar un protocolo preestablecido de envío de Datos que por lo general es el API REST.
17. El "camino" por donde se envía, o más específicamente el Protocolo en este caso es HTTP (Hypertext Transfer Protocol).
18. Aquí llegamos a la capa de Internet.

PARTES DE UNA DIRECCIÓN.

https://gmail.com/enviar_email


HTTP: es el Protocolo.
HTTPS: es un protocolo Seguro que está Encriptado.
gmail.com: Es el dominio (Nombre con el que encontramos en la Web a ese servidor). Se llega a través de DNS(Domain Name Server).
/enviar_email: son instrucciones dentro del servidor. 

Los nombres de dominio o DNS se transforman en IP's.
Existen servidores comunes en los cuales todos los países colaboran y se conforman de:

Un IP: Dirección única en Internet que equivale a un nombre.

172.214.1.110	google.com
 
una vez encontrada la IP se hace una petición al servidor que está programado en algún lenguaje de programación. Gmail, por ejemplo está escrito en JAVA.

Para llegar a JAVA, se debe parar por varias capas. 

El sistema Operativo que corre el servidor: Linux.
Linux tiene drivers que le permiten conectarse con la electricidad del cable de red.

Los cables de red, a través de Routers Switch envían la electricidad al servidor, cutos drivers deben reinterpretar la electricidad en una Capa de Red que se conoce coloquialmente como Ethernet.  

Ethernet envía la señal al servidor (Linux), el servidor transforma la señal en datos que se encapsulan en  un súper protocolo llamado TCP/IP (Se transmite con este protocolo todo sobre internet).

TCP/IP crea los datos hacía el protocolo HTTP  que es recibido por un servidor de HTTP dentro de Linux (Los servidores pueden ser NGINX o APACHE).  

A nivel de Software los servidores son aplicaciones que corren dentro del sistema Operativo (Linux), que agarran las señales y las procesan mediante el Lenguaje de programación programado previamente (En el caso de Gmail es JAVA).

Lo primero que hace el Lenguaje de Programación es enviar el archivo a una Base de Datos (My SQL, Oracle, postgres).

Luego se envía el email, que trabajan con su propio protocolo y se envían con sus propios servidores.

Para enviarlo es necesario usar un servidor de Correo que viene en la petición, por ejemplo si queremos enviar un correo a:
cursos@platzi.com

Platzi.com: es el nombre del dominio.
Cursos es la casilla de correo de dicho dominio.

Los emails tienen dos protocolos SMTP y POP3.
```

Estos protocolos se conectan a un servidor Final (que puede ser Linux, MacOS etc.).Y pasa lo mismo que cuando llega a Gmail.

Los servidores de Email también tienen nombre, uno de los más populares es PostFix, el servidor interpreta el email y a quien se lo envió, así se le asigna a la base de Datos llamado Bandeja y posteriormente crear la “Notificación de Email”.