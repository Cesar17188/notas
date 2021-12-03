# Algoritmos de aprendizaje no supervisado

## K-means

![[Pasted image 20211109182222.png]]

"K" se refiere al número de grupos que piensas existen en los datos
"means" se refiere al centro que es un el centro de cada grupo obtenido por la media de todos los elementos que conforman el grupo

## Función de coste
> J(C$^1$, ... , C$^k$) = sum {j=1 - k} (sum {x tal que S $_j$} (||x$_i$$^j$ - C $^j$||$^2$))

k = suma sobre todos los clusters
sum {x tal que S $_j$} = Suma todos los puntos de datos en un cluster j
x$_i$$^j$  = posición de un i$^t$$^h$ punto de datos en el cluster j
C $^j$ = Posición del centroide para el cluster j
x$_i$$^j$ - C $^j$ = Función de distancia (Euclideana)

1. Asigna cada punto de datos en un cluster
2. Calcula los centroides como el promedio de los puntos de datos.

## Regla de actualización
Colocar (aleatoriamente) k centroides -> **(Calcular la distancia distinta de cada punto de datos a cada centroido -> Asigna cada punto de datos a un cluster basado en la distancia más corta -> Computa nuevos centroides como promedios de los miembros del cluster.)**

## Rendimiento
Para 1 solo modelo

Inertia: quñe tan cerca están los puntos de datos al centroide. Este número se necesita pequeño

Silhouette score: qué tan lejanos son los clusters, de [-1, 1]. Este número debe ser cercano a 1.

Idealmente prueba K-Means para diferente número de k.

## Repaso: ingredientes de K-means
 Proceso de decisión:
 * Calcular la distancia de cada punto de datos a cada centroide
 * Asignar cada punto de datos al centroide más cercano
 * Calcular los nuevos centroides promediando los puntos de datos asignados al cluster

Función de coste/error
Minimizar la distancia de los puntos de datos a los clusters
> J(C$^1$, ... , C$^k$) = sum {j=1 - k} (sum {x tal que S $_j$} (||x$_i$$^j$ - C $^j$||$^2$))

Regla de actualización
Repite el proceso de decisión hasta que los puntos de datos asignados a cada cluster sean los mismos.

## K-Means performance

We can use _elbow for optimal K_ method.  

![](https://media2.giphy.com/media/12vVAGkaqHUqCQ/giphy.gif)