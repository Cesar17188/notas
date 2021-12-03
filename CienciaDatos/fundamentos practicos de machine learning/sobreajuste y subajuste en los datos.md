# Sobreajuste y subajuste en los datos

**Sobreajunte (overfiting)**: Es cuando intentamos obligar a nuestro algoritmo a que se ajuste demasiado a todos los datos posibles. Es muy importante proveer con información abundante a nuestro modelo pero también esta debe ser lo suficientemente variada para que nuestro algoritmo pueda generalizar lo aprendido.

**Subajuste (underfiting)**: Es cuando le suministramo a nuestro modelo un conjunto de datos es muy pequeño, en este caso nuestro modelo no sera capas de aprender lo suficiente ya que tiene muy poca infomación. La recomendación cuando se tienen muy pocos datos es usar el 70% de los datos para que el algoritmo aprenda y usar el resto para entrenamiento.

**_Generalización en Machine Learning_**

---

La capacidad de generalización nos indica qué tan bien los conceptos aprendidos por un modelo de aprendizaje automático se aplican a ejemplos específicos que el modelo no vio cuando estaba aprendiendo. El objetivo de un buen modelo de aprendizaje automático es generalizar bien los datos de entrenamiento. Esto nos permite hacer predicciones en el futuro sobre los datos que el modelo nunca ha visto. Sobreajuste y subajuste son terminologías empleados en el aprendizaje automático para hacer referencia a qué tan bien un modelo generaliza nuevos datos ya que el ajuste excesivo y el ajuste insuficiente son las dos causas principales del rendimiento deficiente de los algoritmos de aprendizaje automático.

![](https://platzi.com/clases/1708-fundamentos-ml/23050-sobreajuste-y-subajuste-en-los-datos/url)

_**Sobreajuste**_

---

El sobreajuste hace referencia a un modelo que se sobre-entrena considerando cada mínimo detalle de los datos de entrenamiento. Esto significa que el ruido o las fluctuaciones aleatorias en los datos de entrenamiento son recogidos y aprendidos como conceptos por el modelo. El problema es que estos conceptos no se aplican a nuevos datos y tienen un impacto negativo en la capacidad de los modelos para generalizar.  

![](https://platzi.com/clases/1708-fundamentos-ml/23050-sobreajuste-y-subajuste-en-los-datos/url)  
Este sobre-entrenamiento suele darse con mayor probabilidad en modelos no lineales, por ello muchos de estos algoritmos de aprendizaje automático también incluyen parámetros o técnicas para limitar y restringir la cantidad de detalles que aprende. Algunos ejemplos de algoritmos no lineales son los siguientes:  

![](https://platzi.com/clases/1708-fundamentos-ml/23050-sobreajuste-y-subajuste-en-los-datos/url)

-   Decision Trees
    
-   Naive Bayes
    
-   Support Vector Machines
    
-   Neural Networks  
    
    ![](https://3.bp.blogspot.com/-JI37TU8564I/XHYwCjJCaLI/AAAAAAAAAmE/onVmF8NSgv8GC-s1WLI7pCIH_RTbododACLcBGAs/s1600/33177235518_7d368a2033_h.jpg)  
    
    ![](https://platzi.com/clases/1708-fundamentos-ml/23050-sobreajuste-y-subajuste-en-los-datos/url)  
    **_Subajuste_**
    

---

El subajuste hace referencia a un modelo que no puede modelar los datos de entrenamiento ni generalizar a nuevos datos. Un modelo de aprendizaje automático insuficiente no es un modelo adecuado. Las estrategias para mitigar un ajuste insuficiente son variadas y dependen del contexto.  

![](https://platzi.com/clases/1708-fundamentos-ml/23050-sobreajuste-y-subajuste-en-los-datos/url)  
Como puede deducirse, el subajuste suele darse con mayor probabilidad en modelos lineales, como por ejemplo:  

![](https://platzi.com/clases/1708-fundamentos-ml/23050-sobreajuste-y-subajuste-en-los-datos/url)

-   Logistic Regression
    
-   Linear Discriminant Analysis
    
-   Perceptron  
    
    ![](https://4.bp.blogspot.com/-ETh5qzh4Ri4/XHYyNVGRQpI/AAAAAAAAAmc/nyuM6w0ROyoJsoNTrZscorga-zywK_aLQCLcBGAs/s1600/underfitting-overfitting.png)