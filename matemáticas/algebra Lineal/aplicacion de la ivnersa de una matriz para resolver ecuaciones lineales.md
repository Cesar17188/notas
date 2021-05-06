# Aplicación de la inversa de una matriz para resolver un sistema de ecuaciones lineales

tomando por ejemplo

$3x + y = 1$
$2x + y = 1$

esto se traduce en: 

$\begin{bmatrix}{3} & {1}\\{2} & {1}\\ \end{bmatrix}$ * $\begin{bmatrix}{x}\\{y}\\ \end{bmatrix}$ = $\begin{bmatrix}{1}\\{1}\\ \end{bmatrix}$

Siendo que :
A = $\begin{bmatrix}{3} & {1}\\{2} & {1}\\ \end{bmatrix}$
x = $\begin{bmatrix}{x}\\{y}\\ \end{bmatrix}$
b = $\begin{bmatrix}{1}\\{1}\\ \end{bmatrix}$

entonces por despeje

$x = b * A^-1$