# HTTP

Node nos ofrece el modulo HTTP el cual nos permite principalmente crear un servidor en nuestro computador.  
En este modulo encontraremos todo lo necesario que necesitamos para crear un sistema de rutas, que responderá cada ruta, los header que podrá mandar, etc.  
Uno de los métodos principales de este modulo es createServer, el cual nos permitirá abrir un puerto para crear el servidor.

Para agregar utf-8 a las páginas yo usé el siguiente código:

```js
    w.writeHead(201, { 'content-type': 'text/html; charset=utf-8'})
```

w es el response (Solo que traigo la costumbre de Go de usar w para el response y r para el request)

utf-8 sirve para usar carácteres como las tildes, las ñ, las ¿ y otras cosas.

Dejo por aca este artículo donde explican un poco más a fondo como crear un sistema de enrutamiento básico en node.js. A mi me sirvió como complemento a esta clase. El link: [https://medium.com/@officialrahulmandal/adding-routes-and-logic-to-a-pure-node-js-server-9f995298d984](https://medium.com/@officialrahulmandal/adding-routes-and-logic-to-a-pure-node-js-server-9f995298d984)

Complementario: Cuando un servidor HTTP le da una respuesta a un cliente le envia un status con información de su petición. Este status le indica al cliente que pasó con su petición. Por ejemplo en el orden de los 200 significa que todo salió bien y en el orden de los 400 significa que el cliente cometio un error al enviar la petición (una ruta incorrecta, un permiso incorrecto). Esa es la razón de que se envie un 201.

![[Pasted image 20210811155426.png]]