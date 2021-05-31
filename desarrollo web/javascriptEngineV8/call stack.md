# Call Stack

-   Como se mandan a llamar las variables y las funciones
-   Las tareas en el callstack se apilan de abajo hacia arriba.
-   Se llaman de la última que mandamos a llamar hacia abajo
-   En la base de la pila reposa el Global Object
-   Si una función llama a otra, la pone encima de la pila.
-   Se ejecuta una tarea a la vez (sincronía)
-   Una vez que se van ejecutando las tareas se van retirando de la pila
-   Al ejecutar todas las tareas se retira el Global object.