# Aplicación de las matrices D y V y U y su efecto en la transformación

Al descomponer la matriz en una multiplicación de matrices, el orden en el que se operan las transformaciones del espacio se da de derecha a izquierda: cuando tenemos A = U * D * V quiere decir que la primera transformación es V, la segunda es D y la tercera es U. Esto sucede con todas las composiciones que son, en definitiva, multiplicaciones matriciales.

**Efecto de la descomposición de una matriz en vectores singulares:**  
V → rota el espacio  
D → Escala el espacio (agranda o encoje los vectores, también puede cambiar su sentido)  
U → rota nuevamente los vectores

**Nota:**  
La descomposición por valores singulares tiene efectos similares:

-   autovectores → rota el espacio
-   diag(autovalores) → escala el espacio
-   inv(autovectores) → rota el espacio

-   La matriz V rota el espacio
-   La matriz D escala el espacio.
-   La matriz U rota de nuevo el espacio.
-   La transformación del espacio de una matriz A es igual a la transformación de las matrices SVD (Valores singulares)