# Dentro del Engine

![js-engine-complete@2x.png](https://static.platzi.com/media/user_upload/js-engine-complete%402x-285ce1e4-709b-4842-b4e4-90ec6d940f9f.jpg)

-   Una vez el motor recibe un archivo JS genera un Global enviroment
-   En el Global enviroment se genera un Global object que es igual a window
-   También se genera una variable this
-   this depende del contexto, en el entorno global this es igual al objeto global
-   Ya despues de generado el entorno global, comienza a correr nuestro código en el contexto de ejecucion, a través de un stack de tareas apiladas
-   Una vez que el motor comienza a interactuar con el navegador, genera un parseo del documento completo, para encontrar las keywords y las pasa al AST (abstract syntax tree)

[AST Explorer](https://astexplorer.net/)

-   Una vez se tiene el AST, el motor lo pasa al interpreter para retornar bytecode puede ser entendido por la máquina
-   Si en la interpretación del AST ve mucho código que se repite y que se puede optimizar entra el profiler o monitor, y optimiza el codigo y lo regresa compilado como bytecode para que la máquina lo pueda comprender. Es justo en este paso donde aparece el hoisting, donde el motor en su función de optimizacion reinterpreta el código de una mejor forma y se pueden presentar errores de programacón.
-   El hoisting solo sucede con variables y funciones que se mandan a llamar.