# Cómo funcionan las redes neuronales

## Objetivos
* Entender arquitectura básica de una red neuronal
* Entender cómo funciona el entrenamiento de redes neuronales
* Explotar cómo mejorar las redes neuronales

## Arquitectura básica de una red neuronal

![[Pasted image 20211110181219.png]]

Una red neuronal es un modelo que usa neuronas y conexiones entre ellos para hacer predicciones.
Son usadas usualmente para aprendizaje supervisado.

Ejemplo
![[Pasted image 20211110181601.png]]

Los pesos gobiernan la fuerza de una conexión entre nodos. Pesos altos == conexión fuerte.

La unidad escondida (nodo) acepta una combinación lineal de nodos adjuntos previamente a él

> g$_1$ = W$_0$$_,$$_1$ + W$_1$$_,$$_1$ X$_1$+W$_2$$_,$$_1$ X$_2$ 

Cada unidad oculta recibe una combinación lineal de todas las entradas.

Para la misma entrada existen diferentes pesos dependiendo de cuál unidad oculta esté adjunta. Estos pesos pueden ser distintos.

Ejemplo:

W$_2$$_,$$_3$ ---- El peso de la segunda entrada a la tercera unidad

### Unidades ocultas perform a function

La unidad oculta ejecuta una función en la combinación lineal (g$_1$(x)). Esta función es una función de activación

> g$_1$(x) -> h$_1$ -> h$_1$(x) 
>  h$_1$(x) = f$_1$(g$_1$(x) ) 

f$_1$ =  función de activación
g$_1$(x) = Combinación lineal de nodos de la capa anterior

### Tipos de función de activación de capas ocultas

![[tipos de funcion de activacion de capas ocultas.jpg]]

![[activacion de capas ocultas.jpg]]

## La predicción: la capa de salida

![[capa de salida 1.jpg]]

- **Algunas** funciones de activación tienen un **rango limitado** (ex: softmax/sigmoide), mientras que otras se **extienden indefinidamente** (ReLUs, lineal)

![[clasificacion regresion.jpg]]

## Aprendizaje profundo. Deep learning: Añadiendo más capas

![[añadiendo mas capas.jpg]]