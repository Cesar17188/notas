# Matriz de confusión

Los modelos de clasificación son capaces de predecir cuál es la etiqueta correspondiente a cada ejemplo o instancia basado en aquello que ha aprendido del conjunto de datos de entrenamiento. Estos modelos necesitan ser evaluados de alguna manera y posteriormente comparar los resultados obtenidos con aquellos que fueron entrenados.

Una manera de hacerlo es mediante la matriz de confusión la cual nos permite evaluar el desempeño de un algoritmo de clasificación a partir del conteo de los aciertos y errores en cada una de las clases del algoritmo.

Como su nombre lo dice tenemos una matriz que nos ayuda a evaluar la predicción mediante positivos y negativos como se muestra en la figura.

![Predicción.png](https://static.platzi.com/media/user_upload/Prediccio%CC%81n-e3df59fc-ba05-4fa3-a8a7-f75289d3cd31.jpg)

Los **verdaderos positivos (VP)** son aquellos que fueron clasificados correctamente como positivos como el modelo.  
Los **verdaderos negativos (VN)** corresponden a la cantidad de negativos que fueron clasificados correctamente como negativos por el modelo.  
Los **falsos negativos (FN)** es la cantidad de positivos que fueron clasificados incorrectamente como negativos.  
Los **falsos positivos (FP)** indican la cantidad de negativos que fueron clasificados incorrectamente como positivos.

Para que lo anterior quede más claro consideremos el siguiente ejemplo.

Un médico tiene cuatro pacientes y a cada uno se les solicitó un examen de sangre y por error el laboratorio realizó también un estudio de embarazo, cuando los pacientes llegan el médico les da los resultado.

A la primera paciente le da la noticia que está embarazada y ella ya lo sabía dado que tiene 3 meses de embarazo, es decir, un verdadero positivo.

El siguiente paciente llega y le dice que no está embarazada y es una clasificación evidente dado que es hombre (Verdadero negativo).

El tercer paciente llega y los resultados le indican que no está embarazada sin embargo tiene cuatro meses de embarazo, es decir, que la ha clasificado como falso negativo.

Y por último el cuarto paciente sus resultados han indicado que está embarazado sin embargo es hombre por lo cual es imposible, dando como resultado un falso positivo.

Lo anterior es un proceso que se realiza por cada instancia a clasificar y nos permite calcular la exactitud y su tasa de error con las siguientes fórmulas.

![Exactitud.png](https://static.platzi.com/media/user_upload/Exactitud-eae19c8b-1b7a-43e9-8c30-e3038ba8e515.jpg)

![Tasa de error.png](https://static.platzi.com/media/user_upload/Tasa%20de%20error-af5b74e8-c155-4fc1-9102-491556bdcce9.jpg)

Por lo tanto a mayor exactitud nuestro modelo ha aprendido mejor.