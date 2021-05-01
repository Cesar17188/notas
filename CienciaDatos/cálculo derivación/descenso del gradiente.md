# Descenso del gradiente

El descenso del gradiente es un [[algoritmo]] de [[optimización]] que se utiliza mucho en el análisis de [[datos]], consiste en ubicar aleatoriamente un punto en nuestra [[función]](plano) y de ahí calcular el gradiente que nos da un [[vector]] donde la [[función]] crece y toma el camino hacia el punto más bajo. Haciendo este proceso iterativamente hasta que se halla un mínimo de la [[función]], donde ya no se puede descender más. $\alpha$ es el ratio de aprendizaje y representa un hiperparámetro que define cuanto afecta el gradiente en cada iteración, una manera de verlo es que si $\alpha$ es muy pequeño necesitara muchas mas iteraciones en llegar a un determinado punto y en algunos casos no se moverá del punto donde se encuentra, ya que el gradiente es tan pequeño que no representara cambio alguno.

El descenso del gradiente se puede aplicar en una [[función]] con n variables

![descenso.jpg](https://static.platzi.com/media/user_upload/descenso-2f88c4f0-bbf1-4ce2-9218-a49bbb41a439.jpg)
ejemplo 

$$f(x,y) = x^2 + y ^2$$

vamos a tomar un punto de la superficie "w" y va a empezar a bajar, se le va a implementar una constante **$\alpha$** (learning rate) dependiendo de su tamaño va a disminuir un tamaño hasta llegar a una convergencia con el punto mínimo dependiendo de la curva donde este el punto inicial.

w:  w - $\alpha$ * $\nabla f$ 

![minimios.jpg](https://static.platzi.com/media/user_upload/minimios-c71443f3-9300-4293-b719-81761ee878b3.jpg)

El descenso del gradiente solo se puede hacer con una curva si se hace con mas de un descenso solo se podra ver de un descenso seleccionado.

Para mirar el código de descenso del gradiente ir a 
[[Google colab descenso del gradiente]]