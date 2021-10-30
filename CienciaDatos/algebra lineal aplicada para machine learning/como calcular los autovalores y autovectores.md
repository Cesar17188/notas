# Cómo calcular los autovalores y autovectores

-   Lo que estamos viendo, es que efectivamente los tres son el mismo vector. Conservan la misma dirección, lo único que está cambiando es su amplitud, y en algún caso también el sentido.  
    
    ![](https://platzi.com/clases/1728-algebra-ml/23896-como-calcular-los-autovalores-y-autovectores/url)
-   Entonces, lo que se está teniendo, es que lo que cambia es el **_Autovalor asociado_**.  
    
    ![](https://platzi.com/clases/1728-algebra-ml/23896-como-calcular-los-autovalores-y-autovectores/url)
-   Se puede ver que el Autovector encontrado por numpy, es un múltiplo del Autovector que propusimos.

![C.PNG](https://static.platzi.com/media/user_upload/C-d1bd0e14-30c4-436d-8b97-1fc4f30637dd.jpg)  

![C1.PNG](https://static.platzi.com/media/user_upload/C1-02434739-54b1-4153-8f20-a1575fddcd3e.jpg)  

![C2.PNG](https://static.platzi.com/media/user_upload/C2-adaf03e0-9574-4fcd-ab34-d71b0cb183b2.jpg)


Lo que sucede en la combinación lineal de una matriz con un vector es que se transforma el espacio, de ahí su nombre “transformación lineal”. Entonces, los ejes que conocemos como “x” e “y” se modifican y van a cambiar dependiendo de la matriz que esté describiendo ese espacio, en este caso, la matriz “x”. Lo que sucede con los autovectores es que son vectores que, durante la transformación del espacio, se mantienen en el subespacio generado por el vector “original” en el espacio “original”. No necesariamente todos los autovectores del nuevo espacio estan dentro del mismo subespacio generado, por eso, este otro vecto ortgonal es también un autovector que se mantiene en el subesapcio generado de otro vector “original”.

Si nosotros quisiéramos averiguar cual es ese vector “original” tendríamos que tratar el problema como un sistema de ecuaciones lineales donde “x” e “y” son las incógnitas de ese vector. Les dejo acá la captura de como se podría solucionar en python.

Lo que pasa con el vector [[0.14142136] , [0.14142136]] es que al transformarse el espacio, se mantiene dentro de su subespacio generado escalándose en 5 (que es su autovalor o el lambda, como arroja la función de Eigenvalues de numpy).

![Captura de pantalla (760).png](https://static.platzi.com/media/user_upload/Captura%20de%20pantalla%20%28760%29-30976320-5e81-4ffa-9a69-8b751757b8e0.jpg)

```python
# Importamos las bibliotecas

%matplotlib inline

import numpy as np
import matplotlib.pyplot as plt

# Creamos una matriz
X = np.array([[3, 2], [4, 1]])
print(X)

# Vemos la biblioteca para calcular los autovectores y autovalores de Numpy
print(np.linalg.eig(X))

# Pedimos que muestre los autovalores
autovalores, autovectores = np.linalg.eig(X)
print(autovalores)

# Pedimos cual es el autovalor asociado a cada autovector 
print(autovectores[:, 0]) 

# Mostramos el autovector numero 1
print(autovectores[:, 1])

# Importamos nuestra función para graficar. 
%run ".\\Funciones auxiliares\graficarVectores.ipynb"

# Definamos un array 
v = np.array([[-1], [2]])
# Calculamos la tranformacion con el calculo del producto interno 
Xv = X.dot(v)
# Y lo comparamos con el autovector anterior 
v_np = autovectores[:, 1]
print(Xv)
print(v_np)

# Graficamos al que calculamos con el producto interno, el vector original y el que nos devolvió el método de Numpy
graficarVectores([Xv.flatten(), v.flatten(), v_np], cols = ['green','orange','blue'])

plt.ylim(-4,2)
plt.xlim(-7,3)
```

## Conclusión:

Entonces, podemos ver que el autovector encontrado por Numpy es un múltiplo del autovector que nosotros propusimos. Eso quiere decir que los autovectores son lo mismo, solo que pueden variar en amplitud o en sentido, pero la dirección se mantiene. Si tenemos un autovector, menos ese autovector también es autovector.