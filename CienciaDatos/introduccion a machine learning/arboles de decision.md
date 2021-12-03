
# Árboles de decisión

## Bases

![[Pasted image 20211109172400.png]]

Los conjuntos nos permiten "votar" por la respuesta correcta.

6 árboles predicen 1;
3 árboles preciden 0;

Respuesta final: 1

## Parámetros
Número de árboles: más árboles menor la variación, pero más cómputo

Max features: El número de features usados para partir (split)

Max depth: El número de niveles del árbol de decisición

N$_s$$_p$$_l$$_i$$_t$ = Min samples split: Número de data points que un nodo debe tener antes de dividirse.

n$_m$$_i$$_n$ = Min samples leaf: El mínimo número de muestras requeridas para estar en una hoja (leaf).

## Función de coste y regla de actualización

Función de coste: Para un feature seleccionado encuentra el mejor split-point (punto de separación) y separa los datos en dos nodos más pequeños.

Regla de actualización: Si el nodo hoja tiene más de n$_m$$_i$$_n$ puntos de datos, repite la función de coste, sino para.

## Rendimiento
 Se pueden usar métricas de clasificación o regresión para evaluar qué tan bueno es el modelo.
 
 Para clasificación se puede usa la matriz de confunción de [[regresion logistica]]  mientras que para regresión (predicción) se puede usar MSE / R$^2$
 
 ## Repaso: ingredientes de árbol de decisión
 - Proceso de decisión: De un subset de features aleatorios de tus datos elige un feature. Divide tus datos.
 - Función de error/coste: Usando Gini o criterio de entropía para encontrar el mejor umbral para dividir tus datos.
 - Regla de actualización:  Si los nodos hoja no tienen n$_m$$_i$$_n$ puntos de datos, repite el proceso.

📚Further reading [here](https://www.section.io/engineering-education/introduction-to-random-forest-in-machine-learning/#:~:text=A%20random%20forest%20is%20a%20machine%20learning%20technique%20that's%20used,consists%20of%20many%20decision%20trees.).