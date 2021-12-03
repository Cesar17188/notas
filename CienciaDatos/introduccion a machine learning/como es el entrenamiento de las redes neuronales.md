# Cómo es el entrenamiento de las redes neuronales

## Objetivos
* Escoge tu arquitectura
* La "receta" de entrenamiento
* Ajustar tu tasa de entrenamiento

## Escoge tu arquitectura

![[escoge tu arquitectura.jpg]]

## Deep Feed-Forward (DNNs)
- Funciones de activación
- Usada en muchos problemas complejos

## Convolucional (CNNs)
- Operador convolucional/poll y kernels
- Usada en imágenes y genómicos

## Recurrente (RNNs)
- Celdas de memoria/puerta
- Representa secuencias
- Usada en lenguaje

## La receta para redes neuronales

![[la receta para redes neuronales.jpg]]

## Avance hacia adelante

![[avance hacia adelante.jpg]]


## Funcion de perdida (error/coste) 
### Error cuadrático medio (MSE)

![[error cuadratico medio.jpg]]

### Binary Cross-Entropy (BCE)

![[binary cross-entropy.jpg]]

### Categorical Cross-Entropy (CCE)

![[CCE.jpg]]

## Backpropagation
![[backpropagation.jpg]]

## Analogía de la tasa de aprendizaje
![[analogia de tasa de aprendizaje.jpg]]

Actualizamos cada peso en la red tomando la derivada (parcial) de ello con respecto a cada nodo, empezando dese la salida hacia atrás hasta las entradas.

## Resumen

- Las redes neuronales tienen 3 capas generales: entrada, ocultas, salida.
- Funciones de activación para capas ocultas y de salida
- Entrenar involucra avanzar en la red, calcular la pérdida y backpropagation
- Tasa de aprendizaje y dropout son importantes para el entrenamiento
- Revisar la pérdida y el rendimiento en el set de validación.


El siguiente artículo brinda información para construir una red neuronal utilizando Python  
[https://towardsdatascience.com/how-to-build-your-own-neural-network-from-scratch-in-python-68998a08e4f6?gi=c278a6a3944](https://platzi.com/clases/2459-machine-learning/40699-como-es-el-entrenamiento-de-las-redes-neuronales/url)