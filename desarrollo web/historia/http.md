# HTTP (Protocolo de transderencia de hipertexto)

El **Protocolo de transferencia de hipertexto**( Hypertext Transfer Protocol- HTTP) es el protocolo de comunicación que permite las transferencias de información en la World Wide Web.  
■HTTP fue desarrollado por el World Wide Web Consortium y la Internet Engineering Task Force, ■HTTP es un protocolo sin estado, es decir, no guarda ninguna información sobre conexiones anteriores.  
El desarrollo de aplicaciones web necesita frecuentemente mantener estado. Para esto se usan las **cookies**, que es información que un servidor puede almacenar en el sistema cliente.  
Esto le permite a las aplicaciones web instituir la noción de sesión, y también permite rastrear usuarios ya que las cookies pueden guardarse en el cliente por tiempo indeterminado.

![CC_2732678_20601ec6d3a247d59f8f0cc343ad2f47_otros_que_no_quiero_tus_p_cookies.jpg](https://static.platzi.com/media/user_upload/CC_2732678_20601ec6d3a247d59f8f0cc343ad2f47_otros_que_no_quiero_tus_p_cookies-78194659-568b-4b7c-bf6a-568af3dd607a.jpg)

Para este protocolo existen HTTP Request y HTTP Response, los cuales se encarga del procesamiento de las solicitudes.  
⠀  
Existen métodos dentro de HTTP Request:

-   GET: Solicita datos
-   POST: Envía datos.
-   PUT: Crea o reemplaza datos.
-   DELETE: Borra datos específicos.  
    ⠀  
    **HTTPS (_Hypertext Transfer Protocol Secure_)**.- Es la parte de seguridad en la conexión, las peticiones van encriptadas.
	 
	Los códigos de estado de respuesta HTTP indican si se ha completado satisfactoriamente una solicitud HTTP específica. Las respuestas se agrupan en cinco clases:

1.  Respuestas informativas (`100`–`199`),
2.  Respuestas satisfactorias (`200`–`299`),
3.  Redirecciones (`300`–`399`),
4.  Errores de los clientes (`400`–`499`),
5.  y errores de los servidores (`500`–`599`).