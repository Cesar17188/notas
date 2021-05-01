## Bloque o stack de vectores

Nos será útil definir vectores *concatenando* otros vectores. Por ejemplo, sean $a,b,c,d$ cuatro vectores con:
a =
$$
\begin{bmatrix}a\\b\\d\end{bmatrix} $$

Si $b$ es un $m$-vector, $c$ un $n$-vector y $d$ un $p$-vector entonces a queda definido como el (m+n+p)-vector 

$$

a=(b_{0}, b_{1},..., b_{m-1}, c_{0}, c_{1},..., c_{n-1}, d_{0}, d_{1},..., d_{p-1})

$$ 

Por ejemplo, si $B=(1,2)$ y $C$ =(1.2, -4.7, 0.1) entonces tenemos que:

$$

A=\left(B,C\right)=\left(1,2,1.2,-4.7,0.1\right)

$$