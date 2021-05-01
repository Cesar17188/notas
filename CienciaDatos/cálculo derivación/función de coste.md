# Función de coste

Es el error cuadrático medio --> E.C.M

La [[función]] de coste trata de determinar el error entre el valor estimado y el valor real, con el fin de optimizar los parámetros de la [[red neuronal]].

para ver el código del error cuadrático medio en Google colab ir a
[[Google colab función de coste]]

## Estimadores de error de la función de coste

### Raíz cuadrada media – RMSE

La raíz cuadrada media, es una medida de precisión calculada como la **raíz cuadrada media de los residuos**. Se entiende como residuos la diferencia entre el valor previsto (correcto) y el valor real obtenido.

[![Raíz cuadrada media](https://www.diegocalvo.es/wp-content/uploads/2018/12/Ra%C3%ADz-cuadrada-media.png)](https://www.diegocalvo.es/wp-content/uploads/2018/12/Ra%C3%ADz-cuadrada-media.png)

Raíz cuadrada media

Características del RMSE:

-   Penaliza los valores que son muy grandes.
-   No es fácilmente interpretable.
-   Funciona muy bien para optimizar regresiones en general.

### Error absoluto medio – MAE

El error absoluto medio, es una medida de precisión y se calcula como la **suma media de los valores absolutos** de los errores.

[![Error absoluto medio ](https://www.diegocalvo.es/wp-content/uploads/2018/12/Error-absoluto-medio-MAE.png)](https://www.diegocalvo.es/wp-content/uploads/2018/12/Error-absoluto-medio-MAE.png)

Error absoluto medio

Características del MAE:

-   Más difícil diferenciación y convergencia.
-   Penaliza menos los valores grandes
-   Es más fácil de interpretar

### Error absoluto medio escalado – MASE

El error absoluto medio escalado, es una medida de precisión **similar al MAE** pero escalado.

[![Error absoluto medio escalado](https://www.diegocalvo.es/wp-content/uploads/2018/12/Error-absoluto-medio-escalado.png)](https://www.diegocalvo.es/wp-content/uploads/2018/12/Error-absoluto-medio-escalado.png)

Error absoluto medio escalado

Características del MASE:

-   Más difícil diferenciación y convergencia.
-   Escala univariante.
-   Simétrica.
-   Es más fácil de interpretar.

### Entropía cruzada categórica – Categorical Cross-Entropy

La entropía cruzada categórica, es una medida de precisión para **variables categóricas**.

[![Entropía cruzada categórica](https://www.diegocalvo.es/wp-content/uploads/2018/12/Entrop%C3%ADa-cruzada-categ%C3%B3rica.png)](https://www.diegocalvo.es/wp-content/uploads/2018/12/Entrop%C3%ADa-cruzada-categ%C3%B3rica.png)

Entropía cruzada categórica

Características del Entropía cruzada categórica:

-   Más difícil diferenciación y convergencia.
-   Escala univariante.
-   Simétrica.
-   Es más fácil de interpretar.

### Entropía cruzada binaria – Binary Cross-Entropy

La entropía cruzada binaria, es una medida de precisión para **variables binarias**.

[![Entropía cruzada binaria](https://www.diegocalvo.es/wp-content/uploads/2018/12/Entrop%C3%ADa-cruzada-binaria.png)](https://www.diegocalvo.es/wp-content/uploads/2018/12/Entrop%C3%ADa-cruzada-binaria.png)

Entropía cruzada binaria

Características del Entropía cruzada binaria:

-   Más difícil diferenciación y convergencia.
-   Escala univariante.
-   Simétrica.
-   Es más fácil de interpretar.

## Tipos de optimizadores de la función de coste.

### Descenso estocástico del gradiente – SGD (Stochastic Gradient Descent)

El descenso estocástico o gradiente de descenso incremental, es una aproximación estocástica del gradiente descendiente usado para minimizar una [[función]] objetivo que se escribe como una suma de funciones diferenciables. Este optimizador trata de encontrar mínimos o máximos por iteración.

Al igual que en la [[función]] del gradiente descendente, el gradiente indica la dirección en la que la [[función]] tiene el ratio de aumento más pronunciada aunque no indica hasta donde se debe avanzar en esa dirección.

Como este optimizador no nos fija cuanto avanzar, existe el ratio de aprendizaje que no determina la distancia que recorrerá en cada iteración en la dirección que del gradiente.

### Adam

El optimizador Adam trata de solventar el problema con la fijación de el ratio de aprendizaje del SGD, para ello adapta el ratio de aprendizaje en [[función]] de cómo estén distribuidos los parámetros. Si los parámetros están muy dispersos (sparse) el ratio de aprendizaje aumentará.

Adam es una actualización del Optimizador RMSProp (Root Mean Square Propagation) que se basa en un ratio de aprendizaje adaptativa.

### Adagrad

El optimizador Adagrad es un algoritmo basado en gradiente que adapta el ratio de aprendizaje a los parámetros.

Realiza grandes actualizaciones cuando los parámetros son poco frecuentes y pequeñas actualizaciones cuando son muy frecuentes.

### Adadelta

El optimizador Adadelta es una extensión del algoritmo Adagrad.