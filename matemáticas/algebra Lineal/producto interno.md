# 4. Producto Interno

El *producto interno* (estándar) o simplemente *producto punto* de dos $n$-vectores $\vec{a},\vec{b}$ se define como el escalar:

$$<\vec{a},\vec{b}>=\vec{a}\cdot\vec{b}=a_{0} b_{0}+a_{1} b_{1}+\cdots+a_{n-1} b_{n-1}=\displaystyle\sum_{i=0}^{n-1}a_{i}b_{i}$$

Que es simplemente la suma del producto de sus entradas.

Por ejemplo, si $\vec{a}=(1,2,3)$ y $\vec{b}=(4,5,6)$ entonces el producto punto será:

$$
\vec{a}\cdot\vec{b} = (1,2,3)\cdot(4,5,6)=1\cdot4+2\cdot5+3\cdot6=4+10+18=32
$$

Hasta ahora trabajamos de forma indiferente con *vectores columna* y *vectores renglón*, a partir de este momento **el estándar serán los vectores columna** entonces simpre que hablemos de un vector, dígamos $\vec{a}$ entonces estaremos hablando del vector columna:

$$
\vec{a}=\begin{bmatrix}a_{0}\\a_{1}\\\vdots\\a_{n-1}\end{bmatrix}
$$

Esto también nos permite introducir una nueva operación: **la transposición**. Retomemos el vector $\vec{a}$, denotaremos como $\vec{a}^{T}$ al vector transpuesto de $\vec{a}$:

$$
\vec{a}^{T}=\begin{bmatrix}a_{0}\\a_{1}\\\vdots\\a_{n-1}\end{bmatrix}^{T}=[a_{0}\;a_{1}\;\cdots\;a_{n-1}]
$$

La operación de transposición nos permite cambiar de vectores columna a vectores renglón sin modificar al vector que se transponga. Notemos que es posible poder transponer un vector transpuesto\_

$$
\left(\vec{a}^{T}\right)^{T}=\left(\begin{bmatrix}a_{0}\\a_{1}\\\vdots\\a_{n-1}\end{bmatrix}^{T}\right)^{T}=[a_{0}\;a_{1}\;\cdots\;a_{n-1}]^{T}=\begin{bmatrix}a_{0}\\a_{1}\\\vdots\\a_{n-1}\end{bmatrix}=\vec{a}
$$

Así pues, consideremos el ejemplo anterior de los vectores $\vec{a}$ y $\vec{b}$. Definimos la operación $\vec{a}^{T}\vec{b}$ como:

$$
\vec{a}^{T}\;\vec{b}=[a_{0}\;a_{1}\;\cdots\;a_{n-1}]\begin{bmatrix}b_{0}\\b_{1}\\\vdots\\b_{n-1}\end{bmatrix}=a_{0}b_{0}+a_{1}b_{1}+\cdots+a_{n-1}b_{n-1}=\displaystyle\sum_{i=0}^{n-1}a_{i}b_{i}
$$

Lo cual coincide con la definición del producto interno. Así pues $<\vec{a},\vec{b}>=\vec{a}\cdot\vec{b}=\vec{a}^{T}\;\vec{b}=\displaystyle\sum_{i=0}^{n-1}a_{i}b_{i}$

## 4.1 Propiedades del producto interno

Sean $\vec{a},\vec{b}$ dos $n$-vectores y $\alpha$ un escalar. El producto interno entre $\vec{a}$ y $\vec{b}$ cumple las siguientes propiedades:

* Conmutatividad: $\vec{a}^{T}\vec{b} =\displaystyle\sum_{i=0}^{n-1}a_{i}b_{i}=\displaystyle\sum_{i=0}^{n-1}b_{i}a_{i}=\vec{b}^{T}\vec{a}$
* Asociatividad con multiplicación escalar: $\left(\alpha\vec{a}\right)^{T}\vec{b}=\alpha\left(\vec{a}^{T}\vec{b}\right)$

* Distribución en la adición de vectores: $\left(\vec{a}+\vec{b}\right)^{T}\vec{c}=\vec{a}^{T}\vec{c}+\vec{b}^{T}\\vec{c}$

## 4.2 Consideraciones adicionales
**Proyección**. Si $vec{a}$ es un $n$-vector entonces $hat{e}_{i}^{T}vec{a}=a_{i}$
**Suma de elementos de un vector.** $\mathbf{1}^{T}a=a_{0}+a_{1}+\cdots+a_{n-1}$
**Promedio de entradas de un vector.** $(\mathbf{1}/n)^{T}\vec{a}=(a_{0}+a_{1}+\cdots+a_{n-1})/n$
**Suma de cuadrados de un vector.** $\vec{a}^{T}\;\vec{a}=a_{0}^{2}+a_{1}^{2}+\cdots+a_{n-1}^{2}$

**Producto interno de bloques de vectores**. Sean $\vec{a},\vec{b}$ $k$-vectores formados por concatenar los $n$-vectores $a_{i},b_{i}$:

$$
\vec{a}=\begin{bmatrix}a_{0}\\a_{1}\\\vdots\\a_{k-1}\end{bmatrix},\qquad\vec{b}=\begin{bmatrix}b_{0}\\b_{1}\\\vdots\\b_{k-1}\end{bmatrix}
$$

Entonces el producto punto entre estos vectores va como:
$$
\vec{a}^{T}\vec{b}=[a_{0}\;a_{1}\;cdots\;a_{k-1}]\begin{bmatrix}b_{0}\\b_{1}\\\vdots\\b_{k-1}\end{bmatrix}=a_{0}^{T}b_{0}+a_{1}^{T}b_{1}+ \cdots+a_{k-1}^{T}b_{k-1}
$$

## 4.3 Producto interno en Python.

verlo en [[google colab producto interno vectores]]