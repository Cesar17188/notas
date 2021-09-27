# Regresión y evaluación de hipótesis

[[regresión lineal]]

## Métricas de evaluación y regresión

**por qué usamos un Decision Tree Regressor (o en general una regresion) para un problema que es de CLASIFICACION**.

Entiendo que las regresiones son para problemas donde queremos calcular valores continuos. Por otra parte, los Clasificadores se usan sobre valores discretos.

Ahora bien, si el objetivo con el dataset Iris era predecir la clase de cada especie (setosa, virginica, versicolor), este output es de tipo discreto (cualitativo), por tanto, se debería haber usado un algoritmo de tipo Clasificacion (no de regresion, según entiendo).

Por ende, como en la clase usamos una regresion para “clasificar”, lo cual pienso que no es adecuado, pues esto conduce a resultados muy sospechosos o erroneos, tal como obtuvimos en la matriz de confusion (linea 28) donde todos los valores dan 1.0 (muy sospechoso…).

En el libro “Python Machine Learning” abordan el problema de clasificacion de iris mediante una regresion logistica (OJO: aunque su nombre dice regresion, éste es en realidad un algoritmo de clasificación).

Generalmente tiene diferentes pasos para crear tu modelo. Primero el set de entrenamiento y el de pruebas (70,30). El de pruebas son las predicciones que hace tu modelo, es decir dado los x datos tu modelo predice la categoría a o el valor. Para pruebas, con datos reales. La idea es tener una pequeña muestra de lo que tu modelo va a hacer, por ello tenemos los ingenieros de datos y o devops o ML engineers son las personas que garantizan que tu modelo corra en toda la BD, en tiempo real, que pueda leer y procesar todos los datos. Y tu como DS, debes establecer cuales seria el caso en el que se re-entrene. O puedes hacer otro modelo para calcular ese tiempo. Siempre ten en mente que tu trabajos es crear mejores algoritmos y siempre los tendrán que mejorar y cuando saques uno, debes pensar en como hacer la v.2


https://colab.research.google.com/drive/1A086N9BTfHXJwxvKuBsMugVzfL6hSqqu?usp=sharing