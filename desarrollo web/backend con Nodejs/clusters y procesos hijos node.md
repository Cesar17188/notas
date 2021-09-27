# Clusters y procesos hijos

**¿Que es un Cluster en NodeJS?**  
-Segun la documentacion:  
El módulo de clúster proporciona una forma de crear procesos secundarios que se ejecutan simultáneamente y comparten el mismo puerto del servidor.

Node.js ejecuta programación de un solo hilo, que es muy eficiente en la memoria, pero para aprovechar los sistemas de múltiples núcleos de las computadoras, el módulo Cluster le permite crear fácilmente procesos secundarios que cada uno ejecuta en su propio hilo único, para manejar la carga.

**-Segun mi analisis:** El Cluster de NodeJS no es mas que tomar el hilo principal que ejecuta Node y usando los cores del procesador, crear mas hilos de ejecucion, pero que dependen del hilo principal, aun asi Node siguira ejecutandose en un solo hilo, solo que con los Clusters tendra sub-hilos podriamos decir que puedan ejecutar mas procesos, de esta manera manejar la carga al hilo principal.

Una sola instancia de Node.js corre un solo hilo de ejecución. Para tomar ventaja de los sistemas con multiples core, necesitamos lanzar un cluster de procesos de Node.js para manejar la carga.

El módulo [cluster](https://nodejs.org/dist/latest-v8.x/docs/api/cluster.html#cluster_class_worker)  nos permite la creación fácil de procesos hijos que comparten el mismo puerto del servidor. Veamos un ejemplo en código:

```js
const cluster = require("cluster");
const http = require("http");


// Requerimos la cantidad de CPUs que tiene la maquina actual
const numCPUs = require("os").cpus().length;


if (cluster.isMaster) {
  console.log(`Master ${process.pid} is running`);


  // Si el cluster es maestro, creamos tantos procesos como numero de CPUS
  for (let i = 0; i < numCPUs; i++) {
    cluster.fork();
  }


  // Si por alguna razón el cluster se finaliza hacemos un log
  cluster.on("exit", (worker, code, signal) => {
    console.log(`worker ${worker.process.pid} died`);
  });
} else {
  // Los diferentes workers pueden compartir la conexión TCP
  // En este caso es una servidor HTTP
  http
    .createServer((req, res) => {
      res.writeHead(200);
      res.end("hello world\n");
    })
    .listen(8000);


  console.log(`Worker ${process.pid} started`);
}
```

Si corremos nuestro archivo de Node.js ahora compartirá el puerto 8000 con los diferentes workers:

```js
$ node server.js
Master 3596 is running
Worker 4324 started
Worker 4520 started
Worker 6056 started
Worker 5644 started
```

En Windows, todavía no es posible establecer un nombre de proceso server en un worker.

Documentación Oficial de [NodeJs Cluster](https://nodejs.org/api/cluster.html)

