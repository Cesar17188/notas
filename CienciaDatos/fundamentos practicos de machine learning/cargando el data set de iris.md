# Cargando el data set de Iris

Aqui estan el codigo para el que guste lo pueda usar a su voluntad.

```
from sklearn.cluster import KMeans
from sklearn import datasets
import pandas as pd

import matplotlib.pyplot as plt

iris = datasets.load_iris()

X_iris = iris.data
Y_iris = iris.target

x = pd.DataFrame(iris.data, columns = ['Sepal Lenght', 'Sepal Width', 'Petal Length', 'Petal Width'])
y = pd.DataFrame(iris.target, columns = ['Target'])
x.head(5)

	Sepal Lenght 	Sepal Width 	Petal Length 	Petal Width
0 	5.1 	3.5 	1.4 	0.2
1 	4.9 	3.0 	1.4 	0.2
2 	4.7 	3.2 	1.3 	0.2
3 	4.6 	3.1 	1.5 	0.2
4 	5.0 	3.6 	1.4 	0.2

plt.scatter(x['Petal Length'], x['Petal Width'], c = 'blue')
plt.xlabel('Petal Length', fontsize = 10)
plt.ylabel('Petal Width', fontsize = 10)

Text(0, 0.5, 'Petal Width')
```

Acá dejo los dos grupos: Pétalos y Sépalos

```
plt.scatter(x['Petal Length'], x['Petal Width'], c='blue')
plt.scatter(x['Sepal Length'], x['Sepal Width'], c='red')
plt.xlabel('Petal - Sepal Length', fontsize=10)
plt.ylabel('Petal - Sepal Width', fontsize=10)
plt.show()
```

![iris.png](https://static.platzi.com/media/user_upload/iris-47d7b5d2-02ff-421d-a17a-bc52186ea1b0.jpg)

**Ejemplo de aplicación:**

-   Dataset iris: Presenta los datos de flores: virginica, versicolor y setosa (50 muestras de cada especie), estos datos son: largo y ancho del petalo y del sépalo.
    
-   Para ello importamos el módulo **KMeans** desde sklearn.cluster (`from sklearn.cluster import KMeans`)
    
-   Para cargar los datos de iris importamos el módulo datasets (`from sklearn import datasets`), luego cargamos el dataset a una variable (`<var>=datasets.load_iris()`)