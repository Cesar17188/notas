# Introducción a Numpy

Numpy (Numerical Python)Biblioteca de Python sencilla de usar y muy rápida, adecuada para el manejo de arreglos (álgebra lineal).

-   Es necesario tenerla instalada para usarla (en caso de usar Colab este paso ya está hecho)
-   Hay que importar la librería en nuestro código:

```
import numpy as np
```

-   La biblioteca trabaja principalmente con arreglos (vectores, matrices y tensores). Para declarar un arreglo escribimos:

```
np.array(<arreglo>)
```

-   Podemos asignar una cabecera a nuestros valores de la siguiente manera:

```
cabecera = [('nobre_datos',tipo_datos)]
datos = [(data)]
arreglo = np.array(datos,dtype=cabecera)

#ejemplo:
headers = [('Nombre', 'S10'),('edad',int),('país','S15')]  #'S10' significa string de tamaño 10
data = [('Manuel',12,'Bolivia'),('Jose',10,'Paraguay'),('Daniel',5,'Venezuela'),('Ivon',30,'Chile'),('Lupe',28,'Mexico')]
people = np.array(data,dtype=headers)
```

-   Para tomar parte de un arreglo usamos slice notation (de manera similar a las listas):

```
mi_arreglo = np.array([1,2,3],[4,5,6],[7,8,9])
mi_arreglo[1][1] #devuelve 5
mi_arreglo[1:] #devuelve la segunda y tercera fila
```

-   Comandos utiles.
    -   np.zeros(<dimension>) → crea un arreglo de dimensión indicada con todos los valores iguales a 0
    -   np.ones(<dimension>) → crea un arreglo de dimensión indicada con todos los valores iguales a 1
    -   np.linspace(<inicio>,<fin>,<n_datos>) → crea un arreglo de n datos igualmente espaciados con un inicio y fin indicados
    -   <arreglo>.ndim → devuelve la dimensión del arreglo
    -   np.sort(arreglo) → devuelve el arreglo ordenado (en caso de tener encabezado se puede usar el atributo order=’<nombre_dato>’)
    -   np.arrange(<inicio>,<fin>,<pasos>) → crea un arreglo con inicio y fin dado aumentando el paso
    -   np.full(<dimension>,<valores>) → crea un arreglo de la dimensión data cuyos componentes son llenados con los valores
    -   np.diag(<diagonal>,<k>) → crea una matriz diagonal con los valores dados (k es opcional y determina el número de columnas (signo negativo) o filas(signo positivo) a aumentar en caso de que la matriz no sea cuadrada)