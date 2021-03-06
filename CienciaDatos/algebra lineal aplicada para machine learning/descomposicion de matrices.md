# Descomposición de matrices

Consiste en reescribir una matriz cuadrada X como un producto de A x B x C, es decir X = AxBxC, donde:

-   A: es la matriz formada por los autovectores
-   B: matriz diagonal formada por los autovalores
-   C: matriz inversa de A.

**Nota**: En matrices reales y simétricas, C = A.T (matriz traspuesta de los autovectores). Esta propiedad tiene menor costo computacional.

Recordatorio: Una matriz cuadrada es aquella que tiene igual número de filas y columnas, y cuyos vectores que la componen son linealmente independientes.


-   Quiere decir encontrar dos o más matrices que me ayuden a escribir la matriz original y que tengan ciertas propiedades.  
    Una matriz A la podemos escribir como: sus autovectores producto punto una matriz diagonal, donde la matriz diagonal tiene todos los autovalores encontrados, producto punto la matriz inversa de sus autovectores.
-   A_calc = autovectores.dot(np.diag(autovalores)).dot(np.linalg.inv(autovectores))
-   **Descomposición 2:** Restricciones:Nuestra Matriz A sea real y simétrica (A = A-transpuesta). Decimos que A = la matriz de autovectores producto punto la matriz diagonal con los autovalores, producto punto la transpuesta de la matriz de autovectores. NOTA: Calcular la transpuesta de una matriz es mucho más económico en cómputo que calcular la inversa de una matriz. Y hay que recordar que el cómputo cuesta dinero.
-   A_calc = autovectores.dot(np.diag(autovalores)).dot(autovectores.T)

```
# Importamos Numpy

import numpy as np

# Creamos una matriz

A = np.array([[3, 2], [4, 1]])
print(A)

# Calculamos los autovalores y los autovectores

autovalores , autovectores = np.linalg.eig(A)

# Mostramos los autovectores y los autovalores 

print(autovalores)
print(autovectores)

A_calc = autovectores.dot(np.diag(autovalores)).dot(np.linalg.inv(autovectores))

# Imprimimos la A_calc

print(A_calc)

# Creamos y mostramos la matriz

A = np.array([[3,2], [2,3]])
print(A)

# Demostramos que esta matriz es simétrica, ya que coincide con su traspuesta

print(A == A.T)

# Calculamos de nuevo los autovalores y los autovectores

autovalores , autovectores = np.linalg.eig(A)
print(autovalores)
print(autovectores)

# Lo que estamos obteniendo es que los autovalores son el 5 y el 1 y nuestra matriz es la que tiene esos valores 

# Podemos reescribirla usando 
# Una matriz simétrica es igual a su traspuesta, pero ademas si esto ocurre podremos escribir la descomposición como nuestra 
# matriz a es igual a los autovectores por la diagonal de las lambdas por la traspuesta de los autovectores

A_calc = autovectores.dot(np.diag(autovalores)).dot(autovectores.T)
print(A_calc)

# Entonces, calcular una traspuesta es muchismo más economico que calcular una inversa, entonces nuestro casi ideal es que 
# en vez de tener una matriz cualquiera estuvimos una matriz real simétrica, sin tener que realizar la inversa 
```

---

**Conclusión:** Podemos escribir a nuestra matriz cuando es cuadrada en función de los autovalores y autovectores, y en el caso de que sea simétrica podemos usar la traspuesta en lugar de la inversa.

Ver más

Responder