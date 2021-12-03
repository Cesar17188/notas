# Modelo de caja

Hay una forma de hacer que CSS calcule el tamaño de un elemento (**width o height, por ejemplo**), restándole cierta cantidad.

Por ejemplo:  
Imagina que quieres colocar **2 cajas dentro de una caja padre** y quieres que cada una tome el **50% de ancho**, pero que cada una tenga un **margen a la izquierda de 10px**. Si colocas width de 50% a cada caja y además le colocas margen, esto hará que las cajas queden una arriba de la otra, porque al agregarle 20px de espacio en márgenes, vas a hacer que ya no ajuste el 50% a cada caja.

Para hacer que ambas cajas sigan tomando el 50% contando los márgenes, puedes hacer lo siguiente:

```
.caja-hijo
{
	width: calc(50% - 20px);
}
```

Esto hará que el ancho se calcule, tomando en cuenta el 50% y los 20px que mantegan de margen.

Para usar padding/margin les recomiendo el siguiente truco:  
Piensen en el sentido de las manecillas del reloj empezando desde las 12 y en ese orden va a ir tomando los valores para asignarlos al elemento  

![2020-11-16 13_17_55-Window.png](https://static.platzi.com/media/user_upload/2020-11-16%2013_17_55-Window-c9dc551f-fe2a-4c7e-8fec-51bf674c90df.jpg)

![[Pasted image 20211129143112.png]]

![[Pasted image 20211129143122.png]]