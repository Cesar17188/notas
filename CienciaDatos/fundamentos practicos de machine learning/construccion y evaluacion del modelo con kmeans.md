# Construcción y evaluación del modelo con K-Means

Les comparto un código para hacer el calculo del numero de cluster usando el método del codo mencionado en la clase anterior

```
from sklearn.cluster import KMeans

wcss = []
for i in range(1, 11):
    kmeans = KMeans(n_clusters=i, max_iter=1000, random_state=0)
    kmeans.fit(x)
    wcss.append(kmeans.inertia_)
plt.plot(range(1, 11), wcss)
plt.title('Elbow Method')
plt.xlabel('Number of clusters')
plt.ylabel('WCSS')
plt.show()
```

lo que me dio como resultado  

![](https://i.imgur.com/DMXslDR.png)

Ahí se ve que según la técnica del codo el numero k = 3 es el numero de clusters ideal.

**Evaluación del modelo**  
Podríamos decir que nuestra evaluación será semi-supervisada puesto que usamos los datos del target del data set, simplemente comparamos nuestros resultados con los datos del target (accuracy). El número de grupos (k) óptimo será el que mejor accuracy tenga.