# Readable y Writeable Streams

Los Readable y Writeable streams tienen los siguientes eventos y funciones respectivamente:

## Readable

### Eventos

-   **data**. Se dispara cuando recibe datos.
-   **end**. Se dispara cuando termina de recibir datos.
-   **error**. Se dispara cuando hay un error.

### Funciones

-   pipe
-   unpipe
-   read
-   push

## Writeable

### Eventos

-   **drain**. Se dispara cuando emite datos.
-   **finish**. Se dispara cuando termina de emitir.
-   **error**. Se dispara cuando hay un error.

### Funciones

-   write
-   end

Recuerda que tienen estos eventos porque los heredan de la clase **EventEmitter**.

**writable-stream.js**

```js
//importamos Writable del módulo de streams
const { Writable } = require('stream')

/**
 * Creamos un nuevo Writable y lo asignamos
 * a la constante writableStream
 */
const writableStream = new Writable({
  defaultEncoding: 'utf8',
  /**
   *
   * @param {*} chunk el buffer de entrada
   * @param {*} encoding la codificación
   * del buffer, si el chunk es un string
   * el enconding es la codificación en
   * caracteres de esa cadena, si la
   * codificación es un buffer esta se puede
   * ignorar
   * @param {*} callback esta función es
   * llamada cuando se complete el
   * procesamiento para el chunk
   * proporcionado.
   */
  write(chunk, encoding, callback) {
    console.log(chunk.toString())
    callback()
  }
})
process.stdin.pipe(writableStream)
```

**readable-stream.js**

```js
//requerimos el módulo de Readable stream
const { Readable } = require('stream')
//instanciamos un nuevo Readable stream
const readableStream = new Readable()
/**
 * Cuando se ejecuta el método push()
 * los datos son almacenados en el buffer
 * si no se consumen los datos en el buffer 
 * estos se almacenan en la cola interna 
 * hasta que son consumidos
 */
readableStream.push(`${0 / 0}`.repeat(10).concat(' Batman, Batman!'))
/**
 * El stream de lectura se da por terminado
 * cuándo el buffer recibe un null en este caso
 * con el método push(null)
 */
readableStream.push(null)

/**
 * "pipe(writable)" Este método nos permite 
 * encadenar diferentes streams para su 
 * manipulación por medio de cómputos. Lo que
 * hace es recibir un stream
 * de entrada, realiza una operación sobre 
 * dicho stream y devuelve un nuevo stream con
 * dicha transformación.
 * 
 * "stdout" es un writable stream que toma el 
 * buffer y lo muestra en pantalla
 */
readableStream.pipe(process.stdout)
```

**readable-stream-on-demand.js**

```js
//importamos el modulo readable
const { Readable } = require('stream')

//instanciamos un nuevo readable stream
const readableStream = new Readable({
  /**
   * constructor
   * @param {*} size tamaño del buffer
   * de lectura este se representa en bytes
   * y el valor por defecto es 16kb para un
   * readable stream y para fs es de 64kb
   * parámetro opcional
   */
  read(size) {
    setTimeout(() => {
      //la letra es mayor que z
      if (this.chartCode > 90) {
        //finalizamos la lectura
        this.push(null)
        return;
      }
      /**
       * agregamos la letra al buffer y después
       * se le suma 1 
       */
      this.push(String.fromCharCode(this.chartCode++))
    }, 100)
  }
})

/**
 * inicializamos el atributo chartCode
 * y le asignamos el valor  ASCII de la letra A
 */
readableStream.chartCode = 65
/**
 * manejamos el stream de lectura y le asignamos
 * un stream de salida por pantalla
 */
readableStream.pipe(process.stdout)
```

el **`process.stdout`**, cuando corremos un programa en consola tenemos 3 outputs posibles

-   standard input (stdin)
-   standard output (stdout)
-   standard error (stderr)  
    .  
    El output es lo que mostramos en consola  
    el input es el argumento que le damos al programa, todo lo que sigue al `programa.js`  
    El error es un número que regresamos dependiendo del error que queramos mostrar (Puede no ser un número)

Por lo mismo, hice el siguiente programa usando lo que vimos en Readable y Writable, pero el output del Readable se tomará como argumento del Writable. Así:

```js
const  {Writable, Readable} = require( 'stream' );

const  readableStream = new Readable();
readableStream.push(`${0/0} `.repeat(10).concat('Batman! Batman\n'))
readableStream.push(null);
readableStream.pipe(process.stdin);

const  writableStream = new Writable({
    write(chunk, encoding, callback){
        console.log(chunk.toString());
        callback()
    }

});

process.stdin.pipe(writableStream);
```

char code
![[Pasted image 20210823193457.png]]