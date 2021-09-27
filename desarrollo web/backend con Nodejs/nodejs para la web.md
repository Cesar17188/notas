# Node.js para la web

En esta ocación tenemos que leer codígo e interpratar lo que se esta haciendo:

```js
const http = require('http');
const server = http.createServer();

// El servidor funciona con eventos
server.on('request', (request, response) => {
  // request: lo que llegá del request
  // response: lo que le vamos a responder al cliente
  response.statusCode = '200';
  response.setHeader('Content-Type', 'text-plain');

  response.end('hellow world\n')
});

server.listen(9000);
console.log('Servidor en la url http://localhost:9000');
```
Segundo Servidor que usa el evento **POST** para recibir datos e imprimirlos tal cúal:
```js
const http = require('http');
const server = http.createServer();

// El servidor funciona con eventos
// request: lo que llegá del request
// response: lo que le vamos a responder al cliente
// El Objeto request es un RewriteString
// Los strings heredan de los event Evimetter -> es decir también tiene eventos
server.on('request', (request, response) => {
  if (request.method === 'POST' && request.url == '/echo') {
    let body = [];
    request.on('data', chunk => {
      body.push(chunk);
    })  // Caundo recibe nuestros datos, hay un evento end 
      .on('end', () => {
      // Acá ya termino de recibir nuestros datos
      response.writeHead(200, { "Content-Type": "text-plain"});
      // En lugar de quemar la respuesta, responderemos con el cuerpo
        /* El string chunk tiene los datos de tipo buffer y lo que hay que hacer para que sea un string
          para que sea una cadena de texto en un string podemos usar la utilidad Buffer
        */
        body = Buffer.concat(body).toString();
      response.end(body)
    })
  } else {
    response.statusCode = 404;
    response.end();
  }

});

server.listen(9001);
console.log('Servidor en la url http://localhost:9001'); 
```
**Servidor que recibe tu fecha de cunpleaños y devuelve el dia de la semana que nacieron**:
```js
const http = require('http');
const server = http.createServer();
// My firts server by Jasan Hernández :)
const Days = ['Domingo', 'Lunes', 'Martes', 'Miercoles', 'Viernes', 'Sabado', 'Domingo'];
const Months = [
  'Enero', 'Febrero', 'Marzo', 'Abril', 'Mayo', 'Junio', 'Julio',
  'Agosto', 'Septiembre', 'Octubre', 'Noviembre', 'Diciembre'
];
// El servidor funciona con eventos
server.on('request', (req, res) => {
  if (req.method === 'POST' && req.url == "/send") {
    // Arreglo que guardara los chunks que le enviemos
    let body = [];
    req.on('data', chunk => {
      body.push(chunk);
      // Cuando terminamos de guardar nuestros datos hay un evento end
    })
      .on('end', () => {
      // Acá ya termino de recibir los chuks
        res.writeHead(200, { "Content-Type": "text-plain" });
        // En lugar de quemar la respuesta, responderemos con el cuerpo
        // Tenemos que parcear los datos que vienen de tipo Buffer
        body = Buffer.concat(body).toString();
        let result = body.split('/');
        let date = new Date(result[2], result[1] - 1, result[0]);
        let dateFormatt = `Naciste el día ${Days[date.getDay()]} 
        ${date.getDate()} de ${Months[date.getMonth()]} del año ${date.getFullYear()}`;

        res.end(dateFormatt);
    })
  } else {
    res.statusCode = 404;
    res.end('No Found');
  }
})

server.listen(8000);
console.log('Servidor en la url http://localhost:8000'); 
```