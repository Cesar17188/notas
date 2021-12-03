# Comprendiendo nuestro data set para la creación de un árbol de decisión

**Ejemplo de Entrenamiento de un árbol de decisión**  
Trabajaremos con el dataset Titanic.

-   importamos nuestras librerías:

```
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
import numpy as np
from seaborn import tree

% matplotlib inline
sns.set()
```

-   Leemos nuestro dataset (en este caso está dividido en datos de entrenamiento y prueba)

```
test_df = pd.read_csv(<nombre_archivo>)
train_df = pd.read_csv(<nombre_archivo>)
```

-   Para saber a que tipo de datos pertenece cada columna y la cantidad de datos nulos en cada una usamos el método info:

```
train_df.info()
```

**Nota**  
Podemos generar visualizaciones rápidas de los datos con el método plot:

```
train_df.Survived.value_counts().plot(kind='bar',color=('b','r'))
plt.show()
```