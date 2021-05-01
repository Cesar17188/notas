# Derivada

La derivada es uno de los conceptos más importante en matemáticas. La derivada es el resultado de un [[límite]] y representa la pendiente de la recta tangente a la gráfica de la función en un punto. Pero vayamos por partes.

La definición de derivada es la siguiente:

![](http://recursostic.educacion.es/descartes/web/materiales_didacticos/Derivada_de_una_funcion/Deriva1.gif)

Se dice que una [[función]] $f(x)$ es derivable en un punto, por lo que cual se denomina que la [[función]] es continua. Si la derivada de la [[función]] en un punto tal no existe, eso nos indica que la [[función]] es discontinua, una de las funciones discontinuas más importantes son las denominadas a trozos que son funciones que tomas diferentes valores en distintos puntos.

![Captura.PNG](https://static.platzi.com/media/user_upload/Captura-e40ffe82-91b8-4ff4-8ec8-771103a71cd2.jpg)

# Tipos de derivadas
[[derivada parcial]]

# Notación de la derivada

Existen diferentes formas de expresar la derivada si de notaciones hablamos. Cada una de ellas fue propuesta por un científico diferente al momento de desarrollar los principios del [[cálculo]].

Si sabemos que la [[variable]] **x** es la [[variable]] independiente y **y** la [[variable]] dependiente a través de la relación **y=f(x)**. Algunas notaciones para la derivada son las siguientes:

![](https://imgur.com/G1I94R2.jpg)

## Notación de Leibniz

La notación de Leibniz surge del símbolo **dy/dx** que representa un operador de diferenciación y no debemos confundirlo como una división. Si quisiéramos expresar una segunda derivada usando la notación de Leibniz se puede mostrar como:

![](https://imgur.com/BIWWToW.jpg)

Y para mostrar la n-ésima derivada se expresa de la forma:

![](https://imgur.com/iN2KeSc.jpg)

Esta notación nos sirve para entender como la derivada puede ser expresada como los incrementos tanto de **x** como de **y** cuando el incremento de **x** tiende a cero.

![](https://imgur.com/DwA8heo.jpg)

## Notación de Lagrange

La notación más sencilla de todas es la de Lagrange. Esta notación expresa que la [[función]] es una derivada usando una comilla simple antes del argumento, llamada _prima_.

![](https://imgur.com/shUJtc0.jpg)

Esta expresión se lee como “efe prima de equis”. La cual representa la primera derivada de una [[función]]. Si deseamos expresar la segunda derivada sería:

![](https://imgur.com/Z1Vboyd.jpg)

Y para mostrar la n-ésima derivada se expresa de la forma:

![](https://imgur.com/udihVSe.jpg)

## Notación de Newton

Por último tenemos la notación de Newton. Esta notación es muy usada en campos como la física y la ingeniería debido a su simplicidad para expresar la primera y segunda derivada. Se usa sobre todo en funciones relacionadas al tiempo en campos como la mecánica. Por ejemplo, como una función que representa el movimiento de una partícula.

Su representación de la primera y segunda derivada es la siguiente:

**ẋ ẍ**

Para ver el código de derivación google colab ir a [[Google colab derivación]]

# Importancia de la derivada

## La derivada para encontrar la tangente de una curva

Como ya sabes, la derivada nace del problema de encontrar la pendiente de la recta tangente a un punto, pero también es muy similar a encontrar la velocidad de un objeto, ambos problemas involucran el mismo límite.

Por ejemplo, si tenemos una curva, llamémosle C, y esta curva tiene una ecuación y=f(x). Entonces, si queremos encontrar la recta tangente en un punto P(a, f(a)) necesitamos otro punto, llamémosle Q(x,f(x)). Lo siguiente que queda es calcular la pendiente, que si recuerdas bien es:

![](https://imgur.com/oiOKHZC.jpg)

Para que te quede mucho más claro te dejo su diagrama:

![](https://imgur.com/D1CuriM.jpg)

Pero está pendiente no funciona como una tangente en el punto P. Lo que hace es crear una recta entre el punto P y Q. ¿Qué tendríamos que hacer para que esta recta entre dos puntos se vuelva una tangente? Así es, debemos hacer que Q se acerque lo más posible a P, una distancia muy pequeña.

Para este comportamiento solo debemos aplicar el [[límite]] como lo vimos en la clase anterior y por la magia de las matemáticas tendremos nuestra recta tangente. En el siguiente diagrama lo puedes visualizar de una manera más sencilla para que te quede más claro.

![](https://imgur.com/2EIQzQd.jpg)

Este es un brevísimo repaso de la clase anterior si lo notaste, pero la pregunta aquí es ¿y esto cómo se parece a la velocidad?

## La derivada para encontrar la velocidad

Imagina que tenemos una [[función]] s=d(t), que representa la distancia recorrida de Freddy cuando corre por las mañanas. Esta [[función]] tiene como variable independiente el tiempo y como dependiente la distancia.

Si quisiéramos saber a qué velocidad promedio está corriendo, digamos en un intervalo de tiempo entre t=a y t=h. No te preocupes por los valores de a y h, son solo dos constantes positivas. ¿Qué ecuación crees que describa este fenómeno? Así es, aplicamos la vieja confiable, la fórmula de velocidad de toda la vida. Por si se te olvido es esta:

![](https://imgur.com/TPSoAiI.jpg)

Aplicando la fórmula para este ejemplo, tenemos que:

![](https://imgur.com/6kyYpyU.jpg)

Realizando la resta del denominador, queda como:

![](https://imgur.com/FJpDJiB.jpg)

Esto es mucho más claro en el siguiente gráfico:

![](https://imgur.com/Yb2rCe8.jpg)

Me imagino que ya sabes por dónde va esto. La velocidad promedio es una recta entre dos instantes de tiempo. Estos instantes los podemos ver en el punto P y Q. Pero si queremos saber la velocidad instantánea, por ejemplo, en el punto P que es cuando el tiempo t=a. Lo que tendremos que hacer es aplicar el mismo tipo de[[límite]], obteniendo que la velocidad instantánea en el tiempo t=a es:

![](https://imgur.com/9Ci9LcD.jpg)

Tanto encontrar la recta tangente a una curva como la velocidad son algunas aplicaciones de la derivada. Pero ahora me gustaría invitarte a que te hagas la siguiente pregunta, **¿cómo podemos interpretar la derivada de una manera general?**

## La razón de cambio

Las funciones son dos cantidades que dependen una de otra como ya sabes. Por ejemplo, la cocción de un alimento depende del tiempo en que lo dejemos en el fuego, el precio de un producto depende de su demanda en el mercado, el conocimiento que obtengas depende de cuánto tiempo estudies, etc. Como ves, casi todo en nuestro mundo son un conjunto de relaciones y es aquí donde la derivada puede hacer su magia.

Si estudiamos las funciones como pequeños cambios tenemos que estudiar sus incrementos. ¿Y cómo hacemos esto? ¡Pues ya lo hemos estado haciendo! Si tenemos la [[función]] y=f(x), entonces su incremento en x cuando pasamos de x1 a x2 es:

![](https://imgur.com/sLqSAFm.jpg)

Recuerda que el símbolo delta en mayúscula nos sirve para indicar el cambio entre dos cantidades.

Para el cambio en y sería con:

![](https://imgur.com/UcEl3gp.jpg)

A la división de estos dos incrementos la llamamos **razón de cambio promedio de y con respecto a x.**

![](https://imgur.com/z117ffz.jpg)

Las razones de cambio nos dicen qué tanto cambia una cantidad y con respecto a x. Específicamente la razón de cambio promedio nos dice que tanto cambia y en un intervalo entre x1 y x2. Por lo que si queremos saber qué tanto cambia una [[función]] en un instante determinado debemos aplicar la **razón de cambio instantánea que es la definición de la derivada.**

![](https://imgur.com/yuhEZrR.jpg)

Si nuestra derivada es muy grande significa que y crece muy rápido con respecto a x, pero si la derivada es muy pequeña o casi cero entonces el crecimiento de y respecto a x es mínimo.

Entonces, si lo ves bien, casi cualquier proceso que involucre la relación de dos variables en una [[función]] podemos analizar su crecimiento o decrecimiento gracias a la derivada. Esto nos brinda un mundo de posibilidades para estudiar el comportamiento de nuestros datos y la “velocidad” con la que estos cambian.