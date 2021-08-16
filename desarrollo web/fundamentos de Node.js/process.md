# Process

Podremos entender y ver qué pasa con el Process, podremos escuchar señales, escuchar lo que necesitemos y después hacer cosas con ellos.

Podemos hacer _require_ para obtener **process**

```jsx
const process = require('process')
```

Pero lo anterior no es necesario, ya que **process** es una variable global.

-   **beforeExit** → Es para enviar algo antes que pare un proceso.
-   **exit** → Es para matar un proceso.
-   **uncaughtException** → Permite capturar cualquier error que no fue caputurado previamente.
-   **uncaughtRejection** → Permite capturar cualquier error de promesas que se han rechazado.

```jsx
process.on('uncaughtException', (err, origen) => {
    console.error('Se nos ha olvidado capturar un error')
    console.error(err)
})

funNoExiste()
```

El objecto process es una instancia de `EventEmitter`; podemos suscribirnos a el para escuchar eventos de node.

-   **UncaughtException**: Permite capturar cualquier error que no fue caputurado previamente. Esto evita que Node cierre todos los hijos al encontrar un error no manejado.
    
    ```js
    process.on('uncaughtException', (error, origen) => { console.log(error, origen); });
    ```
    
-   **exit**: Se ejecuta cuando node detiene el `eventloop` y cierra su proceso principal.
    
    ```js
    process.on('exit', () => console.log('Adios'));
    ```
	 
	 Una librería que te permite manejar de forma robusta los argumentos pasados desde la terminal de comandos es **yargs**. Frameworks como Angular o React utilizan internamente estos mismos paquetes junto con cosas como el paquete **colors**, que permite trabajar con colores en consola. Puedes encontrarlos instalados dentro de la carpeta /node_modules.

En mi experiencia personal, yargs es muy potente, y he hecho aplicaciones para CLI robustas con interfaces complejas solamente con este paquete.