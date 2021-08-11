# Crear un paquete para NPM

Como crear un paquete de npm, publicarlos y asi otros desarrolladores puedas incluirlo en sus proyectos

Para el ejemplo usaremos un proyecto de random de mensajes, que se puede instalar de forma global y al ejecutar un comando van a poder recibir en la consola un mensjae aleatorio.

pasos

1. Abrimos la terminal y nos ubicamos en la carpeta donde se va a crear el  proyecto. Con el comando $pwd$ podemos verificar en que ruta nos encontramos. 
2. con el comando $mkdir random-messages$ creamos la carpeta donde vamos a trabajar
3. entramos en la carpeta random-messages con el comando $cd random-messages$
4. inicializamos el proyecto con el comando $git init$
5. Con el comando $npm init$ establecemos la configuracion del proyecto 

a partir de este punto seguir los pasos dados en [[iniciar un proyecto con npm]]

Una vez creado el proyecto 
6. entramos al editor de código con el comando $code .$
7. y creamos la carpeta src
8. entramos a la carpeta src
9. creamos un archivo index.js (aqui va a vivir el proyecto, como se va a crear este proyecto del ramdon, como voy la configuración dentro del package y como lo voy a publicar)

Incluir dentro del archivo index.js

```js
const messages = [

 "Cesar",

 "Ana",

 "Oscar",

 "Jessica",

 "Richard",

 "Andres"

];

  

const randomMsg = () => {

 const message = messages[Math.floor(Math.random() * messages.length)];

 console.log(message);

};

  

module.exports = { randomMsg };
```

10. Crear una nueva carpeta dentro del proyecto llamada bin donde estara la configuración de nuestro paquete que se instala de forma global
11. dentro de bin creamos un nuevo archivo llamado global.js
12. dentro de global.js ira el siguiente código

```js
#!/usr/bin/env node

let random = required("../src/index.js");

  

random.randomMsg();
```

esto permitira recibir la lógica de proyecto y setearlo como una variable global

11. ir al package.json 
12. en la parte inferior, bajo "license" creamos un apartado con el nombre $"bin": { "random-msg": "./bin/global.js" }, "preferGlobal": true$

de la siguiente forma