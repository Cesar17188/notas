# Vectores
Diremos que un *vector* es una lista finita de números. Lo podemos encontrar en dos presentaciones:

* Vector columna:

$$
\begin{Bmatrix}1\\2\\3\end{Bmatrix} $$

o

$$
\begin{bmatrix}1\\2\\3\end{bmatrix} $$

o

$$
\begin{pmatrix}1\\2\\3\end{pmatrix} $$

* Vector renglón

( 1 , 2 , 3 )		 			o    					$[1,2,3]$

Los *elementos* (o *entradas, coeficientes, componentes*) son los valores en el arreglo (los de dentro de los corchetes). El *tamaño* (que también podremos llamar *dimensión* o *longitud*) es el número de elementos que contiene. Por ejemplo, todos los vectores de mostrados anteriormente son de dimension 3 o bien *$3$-vectores*.

En el caso de tener un $1$-vector, e.g. (1.5), no haremos distinción entre el 1-vector y el *escalar* (o número, *parámetro*) $1.5$.

Ahora, si tenemos un $n$-vector $a$ su $i$-ésima entrada se denotara por $a\_{i}$. 

  

Por ejemplo, si $a$ = (1,2,3) entonces $a_{0}$ es igual a $1$, $a_{1}$ es 2 y $a_{2}$ es 3.


Otro ejemplo sería $b$=(3.5,-2.4,0) entonces $b_{0}$ es 3.5, $b_{1}$ es -2.4 y $b_{2}$ es 0

Sean $a$,$b$ dos vectores. Diremos que $a=b$ si y solo si $a_{i}=b_{i}$ con i de $0$ a $n-1$. 

En símbolos: 

* Sean $a$,$b$ dos vectores,   
$a = b$  ⇔ $a_i = b_i$ con 0 ≤ i ≤ n−1

En el futuro nos vamos a referir a dos estrucuras: **espacios vectoriales** y **campos**. De manera simplificada podríamos pensar que los *números* viven en los campos mientras que los vectores viven en los espacios vectoriales.

Como ejemplo, supongamos que tenemos los números $a=1$,$b=2$ y $c=-3$. En este caso decimos que $a ∈ Z$, $b ∈ Z$ y $c ∈ Z$ con $Z$ el **conjuto de los números enteros**. Para fines prácticos $Z$ es también un campo.

Otro ejemplo sería considerar $a = 1$,$b = 2.2$ y $c = -3.99$- En este caso decimos que $a ∈ R$, $b ∈ R$ y $c ∈ R$ con $R$ el **conjunto de los números reales**. Para fines prácticos $R$ es también un campo.

Como último ejemplo, sean $a=(0.2,-2)$ y $b=(-1.2,-3.4)$ dos vectores. En este caso decimos que $a  ∈ {R}^{2}$ y $b ∈ {R}^{2}$, y en general para cualquier $v$ n-vector de entradas reales decimos que $v ∈ {R}^{n}$.

Así pues si el objeto del que estamos hablando es elemento de un espacio vectorial entonces nos referiremos a el como vector, en cambio si el objeto del que hablamos es elemento de un campo entonces nos referimos al mismo como *escalar*.

## 1.1 Algunas consideraciones

###**[[bloque o stack de vectores]]**
###**[[subvector]]**
###**[[convención en notación]]**
###**[[indexación]]**
###**[[cero vectores]]**
###**[[uno vectores]]**
###**[[vectores unitarios]]**

## 1.2 Un ejemplo: Colores RGB

###**[[Google colab Colores RGB]]**

#  2. [[adición entre vectores]].
# 3. [[producto escalar]].
# 4. [[producto interno]]