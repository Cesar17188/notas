# ¿Qué es Node.js?
[[node origenes y filosofia]]
Node.js es un entorno de ejecución para JavaScript construido con el motor JavaScript V8 [[V8, el JS engine de chrome]] de Chrome. JavaScript [[javascript]] es un lenguaje interpretado pero en Node.js tenemos algo llamado el JIT Compiler que es una especie de monitor que optimiza fragmentos de código que son ejecutados frecuentemente.

La definición formal de **nodejs es:** _un entorno de ejecución para javascript construido con el motor v8._

**El entorno de ejecucíon:** es la capa que corre por el sistema operativo que ejecuta software, básicamente se encarga de como se consume memoria, como acceder a las variables y como corre el [garbage collector](https://es.wikipedia.org/wiki/Recolector_de_basura).

[Chrome V8](https://es.wikipedia.org/wiki/Chrome_V8) Es un engine de Javascript por de **chromiund-project** para chrome y chromium. Además de chrome existen **2 proyectos** que son **chromium** que es la versión open source y luego **chrome canary**, chrome canary se llamá así por una analogía donde antiguamente los mineros iban a la mina y para detectar si habia gases o algún peligro, ponían a un canario en una pequeña jaula, si había un gas y pasaba algo, el canario lasimosamente moría y es la manera en como se daban cuenta si había algún error, lo mismo pasa con chrome canary, es la manera como detectan errores y si todo sale bien, lo pasan a chrome.

[Chrome V8](https://es.wikipedia.org/wiki/Chrome_V8) lo que hace es compilar javascript a código máquina. Recordemos que los lenguajes interpretados se ejecutan muy rápido, pero cuando hay un loop de código muy seguido se demoran, porque cada vez que pasan por esa linea de código tienen que volverla a interpretar a diferencia de los lenguajes compilados que se demoran mucho en cargar, porque tienen que pasar precisamente por ese proceso de compilación, luego se ejecutan muy rápido porque compilan esa linea, por eso cada vez que vuelven a pasar por ese loop, ya esta perfectamente compilado.

**Javascript solía ser interpretado** y **ahora es compilado** con una tecnologia llamada **Just in time compiler** ó [compilación en tiempo de ejecución](https://es.wikipedia.org/wiki/Compilaci%C3%B3n_en_tiempo_de_ejecuci%C3%B3n), está tecnología lo que tiene es un monitor que se encarga de revizar cada cuanto se ejecuta nuestro código, si el código se ejecuta mucho pone un estado warm y lo que hace es que ese código lo compila, si ese código compilado se **ejecuta muchas veces**, lo coloca en un estado **HOT** y es básicamente es hacerle una **optimización** a ese compilado, para que cuando se llame, ya llame a la versión optimizada.

Nodejs fue tomar el engine de JS chrome V8 para crear un entorno de ejecución y poder usar javascript del lado del servidor, recordemos que tenemos otros engine de JS como: [spiderMonkey](https://es.wikipedia.org/wiki/SpiderMonkey), [JavascriptCore](https://es.wikipedia.org/wiki/JavaScriptCore) y [Chakra](https://es.wikipedia.org/wiki/Chakra_(int%C3%A9rprete_de_JScript)). Pero como recientemente van a renovar la versión de Each van a empezar a implementar el motor V8 como Js engine.

## Fechas importantes de NodeJS

-   En **2009** por primera vez [Ryan Dahl](https://en.wikipedia.org/wiki/Ryan_Dahl) mostró al mundo nodejs.
    
-   En **2011** por primera vez Linkenlin usa nodejs en producción.
    
-   En **2013** se saca Gust que es una Plataforma de plugin.
    
-   A la vez Paypal saca un framework de nodejs llamado [Krakenjs](https://github.com/krakenjs/kraken-js).
    
-   En **2015** sale la competencia de nodejs llamada IOJS, pero afortunadamente se reconcilian y crean lo que hoy es [La Nodejs foundation](https://foundation.nodejs.org/).
    
-   En **2017** Nodejs Se vuelve Messtring con un 8.8 millones de instancias funcionando.

https://nodejs.org/es/

https://hacks.mozilla.org/2017/02/a-crash-course-in-just-in-time-jit-compilers/

https://en.wikipedia.org/wiki/JavaScript_engine

https://blog.risingstack.com/history-of-node-js/