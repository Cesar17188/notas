# Object

-   Object
    
    Es un tipo de dato no primitivo.
    
    **Declarar a una variable con el tipo object no es lo mismo que crear un Object nativo de JS**
    
    Si tenemos un objeto declarado con el object de TS no podremos acceder a sus atributos mientras que si lo hacemos regularmente como en vanilla JS si podremos hacerlo.
    
    Por lo tanto declarar una variable como object de TS nos puede llegar a servir para una situacion en la que no querramos que el objeto pueda mutar.
    
    **Sintaxis:**
    
    ```tsx
    //Explicito
    let user: object = { id: 234, name: "Federico"}
    
    //Implicito
    //Este objeto sera creado como un objeto nativo de JS
    let user = { id: 234, name: "Federico"}
    ```
	 
	 -   Object: instancia de la clase Object en JavaScript
-   object: tipo para valores no primitivos

Con este tipo no se puede acceder a las propiedades del objecto

Esto es lo que dice la documentacion de typescript: Generally, you won’t need to use this. En pocas palabras, ignoren el tipo object.

Tengo entendido que `{}`, es decir, Object, es mejor que `object`.

Diferencias entre object y Object.  
Object: instancia de la clase Object de Javascript  
object: tipo para valores no primitivos. Con este tipo no se puede acceder a las propiedades del objeto.

[https://2ality.com/2020/01/typing-objects-typescript.html#object-vs.-object-in-typescript](https://2ality.com/2020/01/typing-objects-typescript.html#object-vs.-object-in-typescript)