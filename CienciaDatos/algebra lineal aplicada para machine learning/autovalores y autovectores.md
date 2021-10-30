# Autovalores y Autovectores

**Autovectores:**  
Son vectores cuya dirección no se modifica al aplicarle la trasformación de una matriz, el sentido y el tamaño sí puede variar. El valor que transforma el vector inicial en el vector final se llama autovalor.  
**Notas:**

-   Sólo las matrices cuadradas tienen autovectores.
-   Hay tantos autovectores como la dimención de la matriz

Las transformaciones lineales ejercen trasformaciones sobre nuestros vectores. Un auto vector es cuando a un vector le aplicamos la transformación no sufre ninguna transformación.

```python
# Importamos las bibliotecas

%matplotlib inline

import numpy as np
import matplotlib.pyplot as plt

# Importamos nuestra función para graficar. 
%run ".\\Funciones auxiliares\graficarVectores.ipynb"

# Vamos a definir 2 colores
orange_light = '#FF9A13'
blue_light = '#1190FF'

# Definimos una matriz
X = np.array([[3, 2], [4, 1]])
print(X)

# Definimos un vector 
v = np.array([[1], [1]])
print(v)

'''Recordemos que lo que estamos queriendo ver es un vector que cuando lo apliquemos la matriz siga siendo el mismo
vector, incluso cuando este sea un multiplo del vector original '''

# A nuestro vector transformado lo llamaremos u 
# Para transformarlo le vamos a aplicar el producto interno al vector original 
u = X.dot(v)
print(u)

# Graficamos los vectores

graficarVectores([u.flatten(), v.flatten()], cols=[orange_light, blue_light])

plt.xlim(-1, 6)
plt.ylim(-1, 6)

# Lo que obtuvimos es nuestro vector original que se llama v con color azul que fue expandido al 
# aplicarle nuestra transformación x de color naranja 

# Lo que esta ocurriendo es que nuestro auto valor es 5 y si lo multiplicamos. Entonces, un auto vector 
# Es aquel que cuando de aplico una matriz me devuelve el mismo vector con la misma dirección, pero con una 
# Amplitud distinta. Ósea, puede estar multiplicado por el autovalor.

lambda_1 = 5
lambda_1 * v

# Este valor no es único, aquí vamos a definir otro y tendrá la misma propiedad.  

s = np.array([[-1], [2]])
print(s)

# Para transformarlo le vamos a aplicar el producto interno al vector original 
t = X.dot(s)
print(t)

graficarVectores([t.flatten(), s.flatten()], cols=[orange_light, blue_light])

plt.xlim(-3,3)
plt.ylim(-3,3)

# Veamos que la dirección se mantiene, aunque haya un cambio de sentido 
```

**Conclusión:** Una matriz de 2x2 tiene 2 auto vectores y 2 autovalores asociados.