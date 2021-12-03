# Preparando el conjunto de imágenes para aplicar PCA

-   PCA es una técnica muy útil para reducir la cantidad de dimensiones con las que estamos trabajando.
-   Muchas veces nuestro conjunto de datos es muy grande y es necesario reducirlo al menos en un 20%, dejando el 80% de datos mas significativo.

### ¿Por qué estandarizar los datos?

“El proceso de PCA **identifica aquellas direcciones en las que la varianza es mayor**. Como la varianza de una variable se mide en su misma escala elevada al cuadrado, si antes de calcular las componentes no se estandarizan todas las variables para que tengan media 0 y desviación estándar 1, **aquellas variables cuya escala sea mayor dominarán al resto**. De ahí que sea recomendable estandarizar siempre los datos”.

[Fuente](https://www.cienciadedatos.net/documentos/35_principal_component_analysis)

https://github.com/platzi/algebra-aplicada/tree/master/03%20-%20Algebra%20Lineal%20Aplicada%20-%20Analisis%20de%20Componentes%20Principales%20(PCA)/imagenes

la mejor manera de conseguir el data set es:

```
import sklearn.datasets
 data= sklearn.datasets.fetch_olivetti_faces()
```

automaticamente se descarga el dataset.

Para los que no saben usar el dataset, no hay necesidad de usar imageio para cargar las imagenes, porque ya al hacer:

```
import sklearn.datasets
data= sklearn.datasets.fetch_olivetti_faces()
```

Alli se descarga automaticamente como dice johanR todo el dataset en la variable `data`

tampoco es necesario normalizar los valores porque ya en el dataset estan normalizados, lo unico que se necesitaria es consumirlos.

la variable `data` contiene el dataset, pero los valores estarian dentro de `data.data`.

Ademas, `data.data` es un array almacena individualmente cada imagen en cada posicion del mismo.

La imagen esta almacenada como una tira de valores (todos los valores en una sola dimension), como necesitamos es una matriz, le aplicaremos un reshape.

Las imagenes tienen 4096 valores en una dimension, el cual es un tamaño de 64 x 64 en dos dimensiones, entonces por ejemplo hariamos algo asi:

```
imagen_1 = data.data[0].reshape(64, 64)
imagen_2 = data.data[1].reshape(64, 64)
```

De esa forma estarian manipulando la misma matriz normalizada del profesor, por ejemplo para mostrar la imagen numero 6 del dataset seria asi:

```
plt.imshow(data.data[5].reshape(64,64), cmap='gray')
```