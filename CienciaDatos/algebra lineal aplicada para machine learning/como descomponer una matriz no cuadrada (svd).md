# ¿Cómo descompongo una matriz no cuadrada (SVD)?

**Descomposición de una matriz en valores singulares**  
La descomposición por autovectores sólo es aplicable a matrices cuadradas. El presente método permite descomponer cualquier matriz en tres matrices:

-   U → vectores izquierdos singulares
-   D → matriz diagonal de valores singulares
-   V → vectores derechos singulares

Estos valores se obtienen en python mediante el método:

```
U,D,V = np.linalg.svd(matriz)
```

**Nota:**  
Podemos ve a una matriz rectangular como una subtransformación del espacio, es decir podemos condensar información de tres a dos dimensiones.

Al final de la clase el profesor hace mencion de una operacion entre matrices que hace que volvamos a tener la matriz original. En este caso multiplica U D V en ese orden.  
Sin embargo no lo hace en codigo y a simple vista puede salirnos un error de compatibilidad de dimensiones, pues U es 2x2, D (como lo hizo el profesor) es 2x2 y V es 3x3. Y no se puede multiplicar una matriz 2x2 con una 3x3. Lo que hice y dio resultado fue aumentar una columna extra de 0’s al vector D para que ahora sea de 2x3 y realice la multiplicacion y el metodo SVD queda comprobado aqui les dejo el codigo.

```
import numpy as np

A = np.array([[1,2,3],[3,4,5]])
print(A)

U, D, V = np.linalg.svd(A)

magicMatrix = np.array([[D[0],0,0],[0,D[1],0]])
A_calc = U.dot(magicMatrix).dot(V)
```

magicMatrix tendra ese cambio que mencione arriba y A_calc puede comprobarse que es igual a la matriz A original