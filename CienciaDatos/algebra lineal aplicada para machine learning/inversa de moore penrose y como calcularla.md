# ¿Qué es una pseudo inversa de Moore Penrose y cómo calcularla?

-   La pseudo inversa de Moore Penrose es utilizada cuando en un sistema de ecuaciones lineales representado por Ax = B, x no tiene inversa.
-   La pseudo inversa de MP es única y existe si se verifican 4 condiciones.
-   Para calcularla se siguen los siguientes pasos:

1.  Calcular las matrices U, D, y V (matrices SVD) de A.
2.  Construir D_pse: una matriz de ceros que tiene igual dimension de A, y que luego se transpone.
3.  Reemplazar la submatriz D_pse[: D.shape[0], : D.shape[0]] por np.linalg.inv(np.diag(D))
4.  Reconstruir pseudoinversa: A_pse = V.T.dot(D_pse).dot(U.T)

**Notas**

-   Para calcularla automaticamente por Python: np.linalg.pinv(A)
-   Lo que obtenemos con A_pse es una matriz muy cercana a la inversa. Cercano en el sentido de que minimiza la norma dos de estas distancias. O sea, de estos errores que estamos cometiendo.
-   A_pse no es conmutativa, es decir, A_pse·A ≠ A·A_pse


-   La forma en que python obtiene la pseudo inversa es con el método SVD.
-   SVD es mas certera, y computacionalmente más efectiva.