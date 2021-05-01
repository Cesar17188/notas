# Producto por un escalar o multiplicación escalar-vector.

Otra operación es el *producto por un escalar* o *multiplicación escalar-vector* en la cual un vector es multiplicado por un escalar. La operación se hace elemento a elemento. Sea $\vec{v}$ un vector de $\mathbb{R}^{n}$ y $\alpha\in\mathbb{R}$. Si $\vec{x}=\alpha \vec{v}$ entonces:

$$
\vec{x}=\alpha\vec{v}=\alpha\begin{bmatrix}v_{0}\\v_{1}\\ \vdots\\v_{n-1}\end{bmatrix}=\begin{bmatrix}\alpha\cdot v_{0}\\ \alpha\cdot v_{1}\\\vdots\\\alpha\cdot v_{n-1}\end{bmatrix}
$$

Por ejemplo, si $\vec{v}=(0,1,-2.3)$ y $\alpha=-1.1$ entonces $\alpha\vec{v}=(0,-1.1,2.53)$

## 3.1 Propiedades del producto por un escalar-vector

Sean $\vec{x},\vec{y}$ dos vectores y $\alpha,\beta$ dos escalares cualquiera. Las propiedades que cumple el producto escalar-vector son las siguientes:

* Conmutatividad: $\alpha \vec{x}=\vec{x} \alpha$

  

* Asociatividad: $(\beta\alpha)\vec{x}=\beta(\alpha\vec{x})$

  

* Distribución sobre suma escalar: $(\alpha+\beta)\vec{x} = \alpha\vec{x}+\beta \vec{x} = \beta \vec{x} + \alpha\vec{x} = \vec{x}(\alpha+\beta)$

* Distribución sobre suma de vectores: $\alpha(\vec{x}+\vec{y})=\alpha\vec{x}+\alpha\vec{y}$

## 3.2 Algunas consideraciones

**Combinaciones lineales**. Sean $\vec{a}_{0},\vec{a}_{1},\dots,\vec{a}_{m-1}$ $n$-vectores y $\beta_{0},\beta_{1},\dots,\beta_{m-1}$ escalares entonces podemos definir el siguiente $n$-vector:

$$ \beta_{0}\vec{a}_{0}+\beta_{1}\vec{a}_{1}+\cdots+\beta_{m-1}\vec{a}_{m-1}$$

  

Es llamado una *combinación lineal* de los vectores $\vec{a}_{0},\vec{a}_{1},\dots,\vec{a}_{m-1}$. Los escalares $\beta_{0},\beta_{1},\dots,\beta_{m-1}$ son llamados los *coeficientes* de la combinación lineal.

**Combinaciones lineales de vectores unitarios**. Es posible escribir cualquier $\vec{b}$ $n$-vector como combinación lineal de los vectores unitarios estándar:

$$
\vec{b}=b_{0}\hat{e}_{0}+b_{1}\hat{e}_{1}+\cdots+b_{n-1}\hat{e}_{n-1}
$$

Con $b_{i}$ escalares y $\hat{e}_{i}$ el i-ésimo vector unitario. Un ejemplo específico sería:
$$
\begin{bmatrix}1\\-1\\0\end{bmatrix}=(1)\begin{bmatrix}1\\0\\0\end{bmatrix} +(-1)\begin{bmatrix}0\\1\\0\end{bmatrix} +(0)\begin{bmatrix}0\\0\\1\end{bmatrix}$$

Como nota final aquí, notemos que si el espacio vectorial es de dimensión $n$ entonces tiene $n$ vectores unitarios $\hat{e}_{i}$

**Combinaciones lineales especiales**. Algunas combinaciones de $n$-vectores $\vec{a}_{0},\vec{a}_{1},\dots,\vec{a}_{m-1}$ tienen nombres especiales.  Por ejemplo, si los coeficientes de la combinación lineal son tales que $\beta_{0}=\beta_{1}=\cdots=\beta_{m-1} =1$ entonces simplemente es una suma de vectores. Si en cambio $\beta_{0}=\beta_{1}=\cdots=\beta_{m-1} =1/m$ entonces la combinación lineal se llama el *promedio de vectores*. 

Cuando $\beta_{0}+\beta_{1}+\cdots+\beta_{m-1}=1$ entonces la combinación lineal se llama *combinación afín*, cuando los coeficientes $\beta_{i}$ son no-negativos entonces la combinación lineal es llamada una *mezcla*, *combinación convexa* o un *promedio pesado*.

## 3.3 Producto por un escalar-vector en Python

Desde la clase pasada introducimos Numpy para manejo de vectores. Una de las fortunas de usar numpy sobre listas es la simpleta de este tipo de operaciones. Realizar esta operación será tan sencillo como usar el operador $*$.

Partamos del vector $\vec{x}=(1,-1,1)$ y del escalar $a=3.1$ entonces, realicemos las operaciones $a\vec{x}$ y $\vec{x}a$

Ejemplo desde 

[[Google colab Colores RGB]]