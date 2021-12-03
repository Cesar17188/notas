# Regresión logística con Scikit-Learn: definición y división de datos

Si nuestro dato de salida tiene un valor cualitativo utilizamos y aplicamos la regresión logística


Modelo de regresión que está más enfocado en la clasificación de datos cualitativos, entregándonos como resultado un 0 o 1 (sí o no)

**Implementación del código**

-   Importar las librerías necesarias

```
import pandas as pd
from sklearn.model_selection import train_test_split #permite dividir nuestros datos
from sklearn import metrics #nos permite evaluar nuestro modelo
from sklearn.linear_model import LogisticRegression() #modelo que vamos a aplicar
import matplotlib.pyplot as plt
import seaborn as sns #nos permite mejorar la presentación de los gráficos
%matplotlib inline #nos permite insetar gráficos en el notebook
```

-   Importamos nuestros datos y generamos nuestras variables

```
diabetes = pd.read_csv(<nombre_archivo>)
feature_cols = ['Pregnancies','Glucose','BloodPressure','SkinThickness','Insulin','BMI','DiabetesPedigreeFunction','Age'] #columnas presentes en el dataset
x= diabetes[feature_cols]
y= diabetes[['Outcome']]
X_train, X_test, Y_train, Y_test = train_test_split(x,y,test_size=0.25, random_state=0)
```

-   Entrenamos el modelo

```
logreg = LogisticRegression()
logreg.fit(X_train,Y_train)
y_pred = logreg.predict(X_test) #Recogemos las predicciones que entrega nuestro modelo para los datos de prueba
```