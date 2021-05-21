**Producto interno en función de la norma**

-   El producto interno de dos vectores es numéricamente igual a la multiplicación de las normas (de orden 2) de estos vectores por el coseno que forman:  
    v\_1.dot(v\_2) = norm\_2(v\_1)\*norm\_2(v\_2)\*cos(α)

**Notas:**

-   Hallar cosenos en python: np.cos() #solo admite radianes
-   Convertir grados sexagesimales a radianes: np.deg2rad()
-   En ML usamos esta igualdad para hallar la similitud coseno, mientras más pequeño el ángulo entre dos vectores más similares son