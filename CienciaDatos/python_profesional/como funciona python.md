# ¿Cómo funciona Python?

Tambien podemos verlo de esta forma:

1.  Los lenguajes compilados convierten el código a binario que es el que lee la computadora.
2.  Los interpretados requieren de un programa que lee las instrucciones en tiempo real y las ejecuta, por lo que el programa interpreta el código escrito y lo traduce en lenguaje de máquina en tiempo real. Esto también explicaría porque en los notebook escritos en collab o jupyter podemos ejecutar nuestro código de python por partes.

![[Pasted image 20210811162253.png]]

![[Pasted image 20210811162302.png]]

-   Tanto **compiladores** como **interpretadores** son programas que convierten el código que escribes a lenguaje de máquina.  
    **Compilado:** Aquel lenguaje que tiene que ser traducido al código de máquina para producir un programa ejecutable  
    .
    
-   **Interpretado:** es un lenguaje de programación para el que la mayoría de sus implementaciones ejecuta las instrucciones directamente, sin una previa compilación del programa a instrucciones en lenguaje máquina.  
    .
    
-   **Garbage collector:** Es una sección especial de python que se encarga de tomar los objetos y las variables que no están en uso y eliminarlas.  
    .
    
-   **¿Qué es la carpeta **pycache**?** Dentro de la carpeta tenemos el bytecode que es el código intermedio que crea python al ser un lenguaje interpretado para que pueda ser leido por la máquina virtual, la ventaja es que funiona como una especie de recuperacion del código que ya hemos trabajado, para que la proxima vez que ejecutes el programa se ejecutará más rápido porque no tiene que convertirse a bytecode de nuevo.

El recolector de basura (Garbage Collector) sirve como administrador de memoria automático. El recolector de basura administra la asignación y liberación de memoria para una aplicación.
![[Pasted image 20210811162215.png]]