# Periféricos y sistemas de entrada de información

![[Pasted image 20220122165844.png]]

Los sistemas operativos normalmente tienen un núcleo llamado kernel, que es el principal elemento que los representa y es la primera parte del sistema operativo que se carga en la memoria RAM. El kernel del sistema operativo tiene acceso a **todo** en nuestra computadora: nuestros archivos, a nuestros periféricos, a los datos de las aplicaciones.

El kernel, inmediatamente después de ser cargado en RAM, se encarga de cargar los drivers: pequeñas piezas de software que permiten interpretar las señales eléctricas del hardware, para que el sistema operativo pueda comunicarse con ellos.

Luego tenemos otro set de drivers que pueden ser los controladores de arranque llamados drivers de aplicación. Cuanto más nos alejamos del kernel, menos privilegios tenemos. Los drivers de aplicación deben pedirle permisos a los drivers anteriores para poder acceder al hardware.

La última capa la representan las aplicaciones. Esta es la capa que menos permisos tiene, ya que las aplicaciones no deberían poder acceder al hardware directamente.

Sistema operativo como anillos:

-   **Primer anillo - Kernel**: El Kernel lo podemos entender como la capa mas profunda de nuestro S.O. por lo tanto tiene acceso completo a archivos, drivers, programas, etc…Igual que cualquier otro proceso, se carga en la RAM como la cualidad de que es lo primero en cargar.  
    En esta capa también viven programas capaces de encriptar y desencriptar información, de tal forma que ninguna otra capa del S.O. tenga acceso a ellos.
-   **Segundo anillo - Drivers**: Como se ha dicho antes los drivers son código que se encargan de interpretar las señales de el hardware y establecer una comunicación con el software del PC. Estos primeros drivers pertenecen a piezas de hardware bastante importantes como la pantalla, el teclado, el mouse, etc…
    -   Es importante indicar que entre el primer y el segundo anillo hay un indice de permisos donde estan almacenados qué permisos tiene cada app
-   **Tercer anillo - Mas Drivers**: Otra capa de drivers carga en un tercer “puesto” en la RAM. Dado que están más alejados del Kernel, tienen menos permisos y privilegios que los drivers del segundo anillo. Dado que mediante los drivers de este anillo, se comunican en su mayoría las Apps, es necesario que primero los drivers del tercer anillo pidan permisos a los del segundo anillo para luego así comunicarse con el hardware.
-   **Cuarto anillo - Apps**: Finalmente en la última capa del modelo de anillos del S.O. nos encontramos con las apps, que se cargan en la RAM para ejecutar procesos. Sin embargo a diferencia de los otros anillos no tienen ningún tipo de acceso directo al hardware del PC. Es importante tener en cuenta que así debería ser, pues de lo contrario cualquier Software escrito por terceros tendría la capacidad de acceder casi por completo al PC y a sus piezas de Hardware.