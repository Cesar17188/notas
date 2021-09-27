# Desarrollo y evaluación de modelos

Imagina que ya estás en un proyecto de Data Science y tu quieres comprobar algo. Por ejemplo: ¿En que momento va a renunciar un empleado de la empresa?

1.  Debes plantear una hipótesis inicial, a esta le llamaremos “Hipótesis Nula” y algo que lo contratidga le llamaremos “Hipótesis alternativa”. Y a tu Hipótesis Nula la pondremos a prueba con una “Prueba de Hipótesis”, la cual debes elegir sabiamente.

La prueba de hipótesis la debemos elegir es en base a la forma en la que están distribuidos nuestros datos, tipos de medición , tipos de datos o características. Las pruebas pueden ser:

-   Anova
-   Z-test
-   T-test
-   Chi-squared test

1.  Cuando ya hallas elegido tu prueba de hipótesis, tendrás un P-Value que te dirá si tu hipótesis se acepta o se rechaza, en base a su ubicación en la campana.

**PRUEBA DE MODELOS**

1.  Si quieres comprobar si un modelo funciona de la manera correcta, entrénalo con un conjunto de datos de entrenamiento (se recomienda que contenga un 80% de los datos totales) y evalúa el rendimiento de tu modelo con el 20% de datos restantes.
    
2.  Una vez hallas evaluado tu modelo con el los conjuntos de datos de entrenamiento y de testing (80 y 20) puedes usar una **matriz de confusión**, esto te dirá todos los aciertos de tu modelo.
    
3.  Una vez termines de ver tu Matriz de confusión, podrás ver que tan preciso o exacto es tu modelo.