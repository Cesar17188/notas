# Usando la pseudo inversa para resolver un sistema sobredeterminando

-   Se quiere hallar la solucion del sistema de ecuaciones Ax = b, tal que x hace que ||Ax-b||_2 sea minima.
-   En principio el sistema de ecuaciones es sobredeterminado, lo que implica que las tres rectas no van a cruzarse en un mismo punto.
-   La solucion dada a través de la pseudo inversa es tal que obedece a los pesos de las ecuaciones. Cada ecuacion como tal ejerce un efecto de gravedad que mueve el punto hacia ella.

-   El método de pseudo inversa para encontrar una solución que se acerque para un sistema sobredeterminado da un punto que según el peso de la ecuación.

![pseudoinversa-punto-mas-cercano-solucion-sistema-sobredeterminado.png](https://static.platzi.com/media/user_upload/pseudoinversa-punto-mas-cercano-solucion-sistema-sobredeterminado-59cc40e7-ba3a-46d2-a0c9-e235688dc0ae.jpg)

**_USANDO LA PSEUDO INVERSA PARA RESOLVER UN SISTEMA SOBREDETERMINADO_**  

![](https://platzi.com/clases/1728-algebra-ml/23906-usando-la-pseudo-inversa-para-resolver-un-sistema-/url)

-   Un Sistema de Ecuaciones **_Ax = b_**, puede tener cero soluciones, una solución o infinitas soluciones.  
    
    ![](https://platzi.com/clases/1728-algebra-ml/23906-usando-la-pseudo-inversa-para-resolver-un-sistema-/url)
    
-   Existe una solución cuando tenemos inversa y ya sabemos calcularlo. Estamos con una matriz cuadrada y todos sus vectores son linealmente independientes.  
    
    ![](https://platzi.com/clases/1728-algebra-ml/23906-usando-la-pseudo-inversa-para-resolver-un-sistema-/url)
    
-   Cuando tenemos dos variables “X y Y” y tres ecuaciones, estamos hablando de un **sistema sobre-determinado**.
    

![M.PNG](https://static.platzi.com/media/user_upload/M-edd934ba-4663-4886-8eff-661f98c141d0.jpg)![M1.PNG](https://static.platzi.com/media/user_upload/M1-3bcd01be-2046-4399-8423-b377208354d2.jpg)![M2.PNG](https://static.platzi.com/media/user_upload/M2-5b803e07-63ae-4ffc-b71b-1d0c897d8f41.jpg)![M3.PNG](https://static.platzi.com/media/user_upload/M3-fe0d33da-f702-4441-b869-928bfb3a9ae7.jpg)

-   El punto que está devolviendo la gráfica, no está en el centro del triángulo. Esto se puede entender porque las ecuaciones tienen distinto peso, cada una está tirando el punto más cerca de ella, está como ejerciendo un centro de gravedad, moviendolo.