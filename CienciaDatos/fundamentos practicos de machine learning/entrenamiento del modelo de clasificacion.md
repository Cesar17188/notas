# Entrenamiento del modelo de clasificación

1.- Lo ya mencionado en otros comentarios: Entiendo que **fue un error haber entrenado y luego evaluado el estimador (en este caso el árbol de decisión) con los mismos datos** y haber hecho caso omiso de los _splits_ hechos con `train_test_split`. Esto explica el valor tan alto de exactitud (accuracy) que dio el modelo al final; seguramente hubo un **overfitting** (encima porque no se usó ningún parámetro de regularización como `max_depth` ([más al respecto](https://scikit-learn.org/stable/modules/generated/sklearn.tree.DecisionTreeClassifier.html#sklearn.tree.DecisionTreeClassifier))) y **el modelo terminó memorizando los datos**. Sin un `X_test` para evaluar es difícil saber si el modelo será bueno para predecir nuevas observaciones. De hecho, [tal como el mismo sitio de sklearn lo menciona](https://scikit-learn.org/stable/modules/tree.html) , los árboles de no suelen generalizar bien y tienden a sobreajustarse a los datos de entrenamiento.

2.- De los cursos de ML de platzi que he visto **no he podido ver una clase que aborde las diferentes métricas que hay para evaluar el desempeño del modelo**, y es algo muy importante. Para clasificadores sólo he visto que muestren _accuracy_, siendo que **NO siempre es la mejor métrica para evaluar un modelo**.

1.  Lo anterior lo menciono porque en el minuto 4:40, la profesora da a entender que el _accuracy_ está relacionado con la probabilidad de que el estimador acierte correctamente una predicción, pero sería bueno aclarar que **esto no es del todo cierto**, sobre todo con datasets con _class imbalance_ (donde el número de observaciones de cada clase no es uniforme). Una métrica más acertada sería el `roc_auc_score` (el área bajo la curva ROC). ([Más info:](https://stats.stackexchange.com/questions/312780/why-is-accuracy-not-the-best-measure-for-assessing-classification-models) )

Aquí esta la forma cómo creo que se debió probar. De esta forma el accuracy obtenito es de aproximadamente 0.74

```
x_train , x_test, y_train , y_test =  train_test_split(x_features_one, y_target, test_size= .25, random_state=1)
tree_one = tree.DecisionTreeClassifier()
tree_one = tree_one.fit(x_train,y_train)
tree_one_accuracy = round(tree_one.score(x_test,y_test), 4)
tree_one_accuracy
```