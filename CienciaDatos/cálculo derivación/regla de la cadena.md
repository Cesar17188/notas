# Regla de la cadena
## Utilidad en cálculo multivariable

La regla de la cadena nos permite calcular la razón de cambio, por ejemplo, de una [[variable]] **y** respecto a **t** siguiendo un proceso intermedio. Este proceso intermedio es la función de **g(t)** que a su vez se relaciona con **y=f(g(t))**. Si no te acuerdas bien y te confundiste un poco en el proceso recuerda cómo se ve la composición de funciones.

![](https://imgur.com/NA6cIaF.jpg)

Nota como en la razón de cambio de **dy/dt** para su cálculo surge un **encadenamiento** de sus [[derivada]]s a través de los bloques que representan las funciones.

## La regla de la cadena en el cálculo multivariable

Bien, la regla de la cadena para una sola [[variable]] es sencilla relativamente pues su proceso es lineal, encadenando las funciones. Lo puedes observar desde cómo pasa la [[variable]] **t** de izquierda a derecha hasta llegar a **y** por todas las funciones. Pero, ¿esto pasa igual cuando tenemos más de una [[variable]]? La respuesta corta es… no.

En el cálculo multivariable, al tener más de una [[función]], surgen divisiones en la forma en la que la variable inicial llega a la variable final. Por ejemplo si tenemos una función **w=f(x,y)** que depende de dos variables **x** y **y**, pero a su vez estas dependen de una variable **t**. La [[función]] que describimos anteriormente se escribe como:

![](https://imgur.com/LsA97Kk.jpg)

Y sé que esto puede ser un poco complicado de entender, pero no desesperes que juntos lo resolveremos. 😉

La pregunta aquí es ¿Cómo podemos calcular la razón de cambio (o derivada total) de **w** respecto a **t**? La respuesta es: usando la regla de la cadena. Pero antes de empezar a desarrollar este proceso quiero que notes algo importante. La [[función]] **w=f(x,y)** depende de dos variables, por lo que el [[cálculo]] de alguna [[derivada]] de esta función concretamente debe ser parcial. Pero tanto las variables **x** y **y** solo son respecto a una variable, la variable **t**, por lo que el [[cálculo]] de cualquier clase de derivada debe ser total.

Si desarrollamos un diagrama de cómo se relacionan estas variables desde **t** hasta **w** tenemos de resultado la siguiente figura:

![](https://imgur.com/OgEfDgI.jpg)

Aquí podemos ver cómo **t** es la [[variable]] inicial y **w** termina siendo la [[variable]] final de salida. Si pusiéramos las derivadas en cada una de estas relaciones nos quedaría un diagrama como el siguiente:

![](https://imgur.com/YYbrIvH.jpg)

Observa como las derivadas de las funciones **x** y **y** son totales porque solo dependen de una única variable **t**. Sin embargo, las derivadas con respecto a **w** son parciales porque tiene más de dos variables, que en este caso son funciones de **t**. Ahora, ¿cómo podemos aplicar la regla de la cadena? Pues observa el diagrama y la relación entre variables en algunos puntos es lineal (se conectan consecutivamente) y en otros puntos las relaciones para llegar a **w** siguen más de un camino (se ven en paralelo).

Así que aquellas relaciones que sean lineales, como en la regla de la cadena de una sola variable, se multiplicarán como ya lo sabíamos hacer. Pero esto solo nos da una porción de todas las relaciones. Por lo que para obtener el conjunto de todas estas relaciones y porciones que llegan hasta **w** debemos agruparlas, y esto se hace con una suma. Quedan la razón de cambio total (o derivada total) de **w** respecto a **t** como:

![](https://imgur.com/w8CEmQx.jpg)

La constitución de la regla de la cadena en multivariable cambia dependiendo del número de variables intermedias que pueda haber en el proceso de llegar al valor final. Pero ahora cuentas con la intuición para poder construir estos diagramas.

La regla de la cadena tiene una gran importancia pues nos permite relacionar diferentes funciones que otorgan un valor final de salida contra su variable de entrada. Esto es muy útil cuando estudiamos el comportamiento, como puede ser el precio de un producto, que está determinado por diferentes factores.