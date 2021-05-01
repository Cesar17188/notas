# Subvector

Consideremos el ejemplo anterior donde $a$ es un $(m+n+p)$-vector. Vamos a considerar a $b,c,d$ subvectores de $a$ de tamaños $m,n$ y $p$ respectivamente. Para referirnos a cualquier subvector de $a$ usaremos la notación de dos puntos. Si consideramos $a$ nuestro vector entonces $a_{r:s}$ es un vector de tamaño $s-r+1$

$$

a_{r:s}=(a_{r},a_{r+1},\dots,a_{s})

$$

El subíndice $r:s$ es llamado el *índice de rango*. Y así entonces, siguiente el ejemplo de anterior etenemos que:

$$

b=a_{0:(m-1)}, c=a_{m:(m+n-1)}, d=a_{(m+n):(m+n+p-1)}
$$