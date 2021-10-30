# null y undefined

-   Null : Son subtipos de Any. Son tipo de variable y se usan también como valor dentro de TS
-   Undefined : Tanto Undefined como Null son valores y tipos dentro de Ts, pero más que nada son subtipos de Any. Significa que se puede asignar `null` y `undefined` a una variable tipo string o number

De las maneras más practicas de solucionar problemas de valores null y undefined es con la opción de configuración --strictNullChecks y ayuda a evitar errores comunes en programación en el ámbito de Javascript

-   En TypeScript, ambos “valores” tienen sus respectivos tipos:
    -   null
    -   undefined
-   Null y Undefined se pueden asumir como subtipos de los otros tipos de datos.
-   Significa que se pueden asignar null y undefied a una variable de tipo string, por ejemplo.

<h5>Opción --strictNullChecks</h5>

-   Solo permite asignar null y undefined a una variable de tipo any o a sus respectivos
-   Ayua a evitar errores comunes en programación de apps en el ámbito JavaScript

Generará un reporte de los errores que encuentre, hacemos `tsc nombreDelArchivo.ts --strictNullChecks`

-   Null
    
    -   Null es la no existencia de la variable
    
    Null es un subtipo de Any, por lo que puedo asignarlo a cualquier tipo de variable
    
    **Sintaxis**
    
    ```tsx
    // Explicito
    let nullVariable: null = null;
    
    // Inferido
    let otherVariable = null;   // --> any
    otherVariable = 'test';
    ```
    
    **Tipo: Null y Undefined La Opcion —strictNullChecks**
    
    -   Solo permite asignar null y undefined a una variable de tipo any o sus tipos respectivos
    -   Ayuda a evitar errores comunes en programación de apps en el ambito Javascript
-   Undefined
    
    Undefined es una variable sin ningun valor
    
    Undefined es un subtipo de Any, por lo que puedo asignarlo a cualquier tipo de variable
    
    **Sintaxis:**
    
    ```tsx
    // Explicito
    let undefinedVariable: undefined = undefined;
    
    // Inferido
    let otherUndefined = undefined;  // --> any
    otherUndefined = 1;
    ```