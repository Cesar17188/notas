# Ciclo de vida de componentes

Ciclo :

-   Constructor: cuando se corre una instancia
-   ngOnChanges : corre antes y durante en el render, siemrpe que detecte cambios en el Input, está para eso, para detectar los cambios.
-   ngOnInit: corre antes pero tiene la condicione que solo correo una vez. Ahi se corren eventos asincronos.
-   ngAfcterViewInit: corre cuando los hijos de ese componentes se han renderizado.
-   NgOnDestroy: Corre cuando se elimina el componente.


![[Pasted image 20220308142855.png]]

Detectar cambios en el ciclo de vida de un componente:

1.  Constructor:  
    Angular lo ejecuta cada vez que se crea una instancia de un componente.  
    No hacer llamadas asíncronas. Lo que ejecute, se debe completar de inmediato
    
2.  ngOnChange:  
    El evento corre antes del render y durante, si detecta cambios en los inputs. Corre múltiples veces.
    
3.  ngOnInit:  
    Corre antes del render, pero solo una vez, cuando el componente está inicializado. Acá se hacen las llamadas asíncronas, como fetch, llamadas a API, promesas.
    
4.  ngAfterViewInit:  
    Corre cuando los hijos de un componente ya se han inicializado, después del render. Acá se agrega el código que modifica los componentes hijos de manera programática, por fuera del template.
    
5.  ngOnDestroy:  
    Corre cuando un componente se elimina. Por ejemplo a causa de un if.
    

Se debe importar las interfaz del evento e implementarla en la clase del componente.