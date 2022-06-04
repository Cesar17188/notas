# Transition timing function y delay

-   **_transitionend :_**  
    Este evento sucede cuanto una transición ha terminado. Hay que tener en cuenta que si una transición se elimina antes de completarse, este evento no se genera.  
    Otro caso importante, es que tampoco se va activar si no tenemos **_transition-delay_** o **_transition-duration_** o cuando sus valores son de 0s (cero segundos).
    
-   **_transitionstart:_**  
    Este evento sucede cuando la transición ha comenzado después del tiempo que se determino en **_transition-delay._**
    
-   **_transitionrun:_**  
    Este evento sucede cuando se crea por primera vez una transición y antes de que comience cualquier **_transition-delay_**
    

**1. NOTA:**  
La diferencia entre **_transitionrun_** y **_transitionstart_** es que la primera ocurre antes del tiempo determinado en _transition-delay_ y la segunda ocurre cuando la animación ha comenzado, o sea, después del _transition-delay_

-   **_transitioncancel:_**  
    Y este evento sucede cuando se cancela una transición. esto puede suceder cuando no dejamos que ocurra _transition-delay_ y _transition-duration_

**2. NOTA:**  
**_transition-delay_** es el tiempo en que demora en comenzar nuestro transición.