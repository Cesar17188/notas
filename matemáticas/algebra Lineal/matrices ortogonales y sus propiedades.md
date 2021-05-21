# Matrices Ortogonales y sus propiedades

-   Una matriz ortogonal debe cumplir: que todas sus filas sean ortogonales mutuamente, igual que sus columnas y ademas que sean ortonormales(Que sus normas sean igual a 1)
-   Se tiene una **matriz ortogonal** cuando dicha matriz multiplicada por su transpuesta da como resultado la matriz identidad. Si la inversa de una matriz es igual a la transpuesta entonces la matriz original es ortogonal.

Las  matrices ortogonales tienen como característica que el número de filas es igual al número de columnas. Además, los vectores fila son vectores ortogonales unitarios y los vectores fila de la transpuesta también lo son.

![](https://www.lifeder.com/wp-content/uploads/2019/12/ortogonal-0.jpg)

Cuando una matriz ortogonal se multiplica por los vectores de un espacio vectorial produce una _transformación isométrica_, es decir, una transformación que no cambia las distancias y preserva los ángulos.

Un representante típico de las matrices ortogonales son las _matrices de rotación_. Las transformaciones de las matrices ortogonales sobre un espacio vectorial se denominan _transformaciones ortogonales_.

Las transformaciones geométricas de rotación y reflexión de puntos representados por sus vectores cartesianos, se efectúa mediante la aplicación de matrices ortogonales sobre los vectores originales para obtener las coordenadas de los vectores transformados. Es por esta razón que las matrices ortogonales son ampliamente usadas en el procesamiento gráfico computacional.

## **Propiedades**

Una matriz **_M_** es ortogonal si multiplicada por su transpuesta **_M_****_T_** da como resultado la matriz identidad **_I_**. De igual forma, el producto de la transpuesta de una matriz ortogonal por la matriz original de como resultado la matriz identidad:

**_M MT_** **_= MT_** **_M =  I_**

Como consecuencia de la afirmación anterior, se tiene que la transpuesta de una matriz ortogonal es igual a su matriz inversa:

**_MT \= M\-1_****_._**

El conjunto de las matrices ortogonales de dimensión _n x n_ forman el grupo de ortogonal _O(n)_. Y el subconjunto de _O(n)_ de matrices ortogonales con determinante +1 forman el _Grupo de Matrices Especiales Unitarias SU(n)_. Las matrices del grupo _SU(n)_ son matrices que producen transformaciones lineales de rotación, también conocidas como el _grupo de rotaciones_.

ejemplo en python con google colab en 

[[Google colab matrices ortogonales y propiedades]]