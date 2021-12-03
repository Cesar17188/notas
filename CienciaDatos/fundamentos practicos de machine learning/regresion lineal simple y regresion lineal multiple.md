# Regresión lineal simple y regresión lineal múltiple

**Regresión Lineal Simple**

-   Es un algoritmo de aprendizaje supervisado que nos indica la tendencia de un conjunto de datos cuyas variables estén relacionadas.

**Regresión Lineal Múltiple**

-   Permite hallar la tendencia entre más de dos variables

**Nota**

-   Este algoritmo se usa solamente para datos cuantitativos


## Regresión lineal y múltiple

El algoritmo de regresión lineal nos ayuda a conseguir tendencia en los datos, este es un algoritmo de tipo supervisado ya que debemos de usar datos previamente etiquetados.

En la regresión lineal generamos, a partir de los datos, una recta y es a partir de esta que podremos encontrar la tendencia o predicción.

Generalmente es importante tener en cuenta varias dimensiones o variables al considerar los datos que estamos suministrando al modelo, recordando siempre cuidar este set de sobreajuste o subajuste.

Cuando nuestro modelo considera más de dos variables el algoritmo de regresión que usamos se conoce como _Regresión Lineal Múltiple_ y este trabaja sobre un sistema de referencia conocido como hiperplano.

Los algoritmos de regresión, tanto lineal como múltiple trabajan únicamente con datos de tipo cuantitativos.


algo que vale la pena mencionar es que cuando tienes muchas variables X1, X2, …Xn puede suceder que la información mas trascendente se encuentre contenida en tan solo 3 , 5 o unas pocas variables asi que se intenta realizar una “reducción de la dimensión” de manera que solo trabajemos con aquellas variables que representan mayor importancia. métodos para esto pueden ver el más conocido como PCA (principal component analysis).
Agregar también que existen más métodos de **‘Feature selection’ **(o selección de variables) junto con la implementación del PCA, sklearn tiene una sección bastante útil sobre esto: [Feature Selection](https://scikit-learn.org/stable/modules/feature_selection.html)

No obstante, recordar también que los eigenvectores del PCA (los componentes principales) **corresponden a una combinación lineal de TODAS variables** en la que cada una aporta con un cierto ‘peso’ (loadings), las variables más importantes (que más varianza aportan al componente principal en cuestión) son aquellas con loadings más grandes. Así que, en general, uno busca conservar las variables con _loading_ más altos en los Componentes Principales (CP) que aportan más a la varianza total de los datos (explained variance).