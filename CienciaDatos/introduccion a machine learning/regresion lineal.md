# Regresión lineal

Escribí un tutorial sobre el modelo de **regresión lineal**. Puedes encontrar el artículo acá: [https://platzi.com/tutoriales/1766-regresion-python/11159-de-donde-viene-el-algoritmo-de-regresion-lineal/](https://platzi.com/tutoriales/1766-regresion-python/11159-de-donde-viene-el-algoritmo-de-regresion-lineal/)

## bases
* Lineal - positiva: Mientras $x$ crece, $y$ crece
* Lineal - negativa: Mientras $x$ crece, $y$ disminuye
* No lineal: curva exponencial o curva logaritmica

## Regresión lineal: Parámetros
Diferentes parámetros cambia lo que pensamos de la relación entre input features (x) y el output target (y$_p$$_r$$_e$$_d$)
> y{pred}=w$_1$x+w$_0$
W$_1$ = un cambio en "x" resulta un cambio en "y"
W$_0$ = El valor de "y" si "x" es 0

## Regresión lineal: función de coste
Mean-square Error (MSE) Loss:
El costo (E) es la diferencia entre el valor del target (y$_j$) y el valor predecido de nuestra linea (y$_p$$_r$$_e$$_d$)

> J(W$_1$W$_0$) = 1/N sum{1-N} (y$_i$-y$_i$$_p$$_r$$_e$$_d$)$^2$

## Regla de actualización
Queremos minimizar la distancia y$_i$$_p$$_r$$_e$$_d$ sobre cada punto de datos en entrenamiento
Cambiamos W$_0$ y W$_1$ hasta encontrar una suma de distancia menor

> Update Rule = min J(W$_0$, W$_1$)

## Rendimiento
MSE and R$^2$ ayudan a indentificar la fortaleza de la relación entre features de entrada y de salida

## Repaso: ingredientes de la regresión lineal

Proceso de decisión: Una función para predecir el target de salida basada en features de entrada. 
y$_i$$_p$$_r$$_e$$_d$ = W$_0$+ W$_1$ X$_1$ + W$_2$ X$_2$ + ... + W$_N$ X$_N$

### Función de error/coste
El promedio de qué tan bien se predice el target
> J(W$_1$W$_0$) = 1/N sum{1-N} (y$_i$-y$_i$$_p$$_r$$_e$$_d$)$^2$

### Regla de actualización
Encuentra valores W, W$_0$ que mejoren las predicciones

min J(W$_0$, W$_1$, ... , W$_N$)

### Linear Regression : parameters

different parameters change what we think of a relation between input features _(X)_ and the output target _(y_pred)_.

> y{pred}=w_1x+w_0_

**w_1**= a change in “x” means a change in "y"  
**w_0**= the value of “y” if “x” is 0

---

#### Linear Regression : cost function

#### Mean-square Error

#### (MSE) Loss :

The cost (E) is the difference between the target value _(y_i)_ and our line predicted value _(y_pred)_

> jleft(w,:w_0right)=frac{1}{N}sum _{i=1}^N:left(y_i-y_{i:pred}right)^2

---

#### Linear Regression : actualization rule

We want to minimize the distance _(y_i pred)_ above each point on training data  
We change w_0 and w_1 'til find a smaller distance sum is found

> _update rule = min J(w_0, w_1) _

---

pd: i want to add the screenshot, but i don’t know why doesn’t let me, it pop up an error:  

![Request failed with status code 400](https://platzi.com/clases/2459-machine-learning/40693-regresion-lineal/)