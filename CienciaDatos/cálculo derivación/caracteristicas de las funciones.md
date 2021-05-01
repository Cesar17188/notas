# Características de las funciones

## Función par

Una función es par si cumple la siguiente relación a lo largo de su [[dominio]]:

$f(-x) = f(x)$

Si lo notaste, esta relación nos dice que una [[función]] es par si es simétrica al eje vertical (eje Y). Por ejemplo, una parábola es una función es par.

## Función impar

Una función es impar si cumple la siguiente relación a lo largo de su [[dominio]]:

$f(-x) = - f(x)$

Esta relación nos indica que una [[función]] es impar si es simétrica al eje horizontal (eje X). Por ejemplo, una función cúbica es impar.

Las dos características o propiedades anteriores están muy relacionadas con la simetría. Puedes comprobarlas tú mismo con diferentes funciones e incluso hacer una pequeña rutina en Python que compruebe si una función es par o impar.

## Función acotada

Una [[función]] es acotada si su codominio (también conocido como [[rango]] o imagen) se encuentra entre dos valores, es decir, está acotado. Esta definición se define como que hay un número m que para todo valor del [[dominio]] de la [[función]] se cumple que:

$-m <= f(x) <= m$

Por ejemplo, la[[ función]] seno o coseno están acotadas en el intervalo \[-1, 1\] dentro de su co-dominio.

## Funciones monótonas

Estas funciones son útiles de reconocer o analizar debido a que nos permiten saber si una [[función]] crece o decrece en alguno de sus intervalos. Que algo sea monótono significa que no tiene variaciones. Entonces las funciones monótonas son aquellas que dentro de un intervalo **I**, perteneciente a los números reales, cumple alguna de estas propiedades:

### **1\. La función es monótona y estrictamente creciente:**

![](https://imgur.com/Ep0YEJX.jpg)

No te preocupes si es un poco difícil de leer esta definición que para eso estoy aquí para explicarte. La forma correcta de leer esto es _“si para todo x1 y x2 que pertenecen al intervalo I, tal que x1 sea menor a x2, si y solo si f(x1) sea menor a f(x2)”_. En palabras mucho más sencillas, lo que nos dice esta definición es que **x1** siempre tiene que ser menor que **x2** en nuestro intervalo **I**, y que al evaluar **x2** en la función el resultado de esto siempre será mayor que si evaluamos la función en **x1**. Para las siguientes tres definiciones restantes no cambia mucho la forma en la que se interpretan.

### **2\. La función es monótona y estrictamente decreciente:**

![](https://imgur.com/np7YV32.jpg)

### **3\. La función es monótona y creciente:**

![](https://imgur.com/f33JMzf.jpg)

### **4\. La función es monótona y decreciente:**

![](https://imgur.com/Epn9XIe.jpg)

## Funciones periódicas

Las funciones periódicas son aquellas que se repiten cada cierto periodo, este periodo se denomina con la letra **T**. La relación que debe cumplir la función para ser periódica es la siguiente.

![](https://imgur.com/TIyQmfL.jpg)

Por ejemplo, la función seno y coseno son funciones periódicas con un periodo T = 2π. Es decir que si nosotros calculamos f(x) y calculamos f(x + 2π) en la función seno el valor que nos den ambas expresiones es el mismo.

## Funciones cóncavas y convexas

La forma de demostrar la concavidad de una función se puede hacer a través del análisis de derivadas consecutivas, pero aún no llegamos a eso, así que no te preocupes. A continuación, te dejo una forma súper intuitiva de ver si una función es cóncava o convexa.

Se dice que una función dentro de un intervalo **es cóncava** si la función “abre hacia arriba”. Es decir si se ve la siguiente manera:

![](https://imgur.com/R3kEHEM.jpg)

Ahora, ¿qué sería una función convexa? Pues así es, lo contrario de una cóncava. Se dice que una función dentro de un intervalo **es convexa** si la función “abre hacia abajo”. Es decir si se ve la siguiente manera:

![](https://imgur.com/rgsDvDb.jpg)

Como ves, identificar si una función es cóncava o convexa a través de su gráfica es muy sencillo. Pero si quieres enfrentar un reto, te dejo que cuando sepas que es una derivada regreses a esta clase y busques la forma de comprobar si una función es cóncava o convexa de forma analítica. Como pista, se hace a través del análisis de la segunda derivada.