# Regresión lineal simple con Scikit-Learn: división de los datos

**Procedimiento de Regresión Linear Simple con Scikit-Learn:**

-   Importar las librerías y modelos necesarios:
    -   pandas: `import pandas as pd` → para manejo de datos
    -   matplotlib: `import matplotlib.pyplot as plt` → permite insertar gráficos estadísticos
    -   train_test_split: `from sklearn import train_test_split` → este módulo permite separar nuestros dato en datos de entrenamiento y prueba
    -   LinearRegression: `from sklearn import LinearRegression` → El modelo en sí
-   Importar los datos (en este caso desde un archivo csv):

```
dataset = pd.read_csv(<nombre_archivo>)
```

-   Asignar los datos a sus respectivas variables:

```python
x = dataset.iloc[<slice>]
y = dataset.iloc[<slice>] #iloc sólo admite slice notation para la selección de parte de los datos
```

-   Separar los datos en datos de prueba y datos de test:

```python
X_train, X_test, Y_train, Y_test = train_test_split(x,y,test_size=0.2, random_state=0)
# test_size → porcentaje de los datos de prueba a tomar
# random_state = 0 → tipo de selección de datos (a un mismo valor devuelve la misma selección)
```

The **train_test_split** function takes several arguments which are explained below:

1.  **X, y**: These are the feature matrix and response vector which need to be splitted.
2.  **test_size**: It is the ratio of test data to the given data. For example, setting test_size = 0.4 for 150 rows of X produces test data of 150 x 0.4 = 60 rows.
3.  **random_state**: If you use random_state = some_number, then you can guarantee that your split will be always the same. This is useful if you want reproducible results, for example in testing for consistency in the documentation (so that everybody can see the same numbers).