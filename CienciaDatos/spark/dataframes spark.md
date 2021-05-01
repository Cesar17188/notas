# DataFrame Spark

Estos componentes fueron agregados en la versión 1.3 de [[Spark]] y pueden ser invocados con el contexto espacial de Spark SQL. Como indica su nombre, es un módulo especialmente desarrollado para ser ejecutado con instrucciones parecidas al [[SQL]] estándar.

De la misma forma, como los [[RDD]], estos pueden ser creados a partir de archivos, tablas tipo Hive, bases de datos externas y [[RDD]] o [[DataFrames]] existentes.

El primer detalle que salta cuando creamos un DataFrame es que poseen columnas nombradas, lo que a nivel conceptual es como trabajar con un DataFrame de [[Pandas]]. Con la excepción que a nivel interno [[Spark]] trabaja con [[Scala]], lo cual le asigna a cada columna el tipo de dato Row, un tipo especial de objeto sin tipo definido.

Pero no es todo, los DataFrames implementan un sistema llamado **[[Catalyst]]**, el cual es un motor de optimización de planes de ejecución, parecido al que usan las bases de datos, pero diseñado para la cantidad de datos propia de [[Spark]], aunado a eso, se tiene implementado un optimizador de memoria y consumo de CPU llamado **[[Tungsten]]**, el cual determina cómo se convertirán los planes lógicos creados por Catalyst a un plan físico.

![spark-dataframe.png](https://static.platzi.com/media/user_upload/spark-dataframe-2833682e-af45-4ca3-8233-696f09a8f75c.jpg)

Es una capa superior que existe sobre los [[RDD]] en [[Spark]]. La principal diferencia es:

* Formato
	* A diferencia de un RDD poseen columnas, lo cual les otorga tipos de datos
* Optimización
	* Poseen una mejor implementación, lo cual los hace preferibles.
* Facilidad de creación
	* Se pueden crear desde una [[base de datos]] externa, archivo o [[RDD]] existente.

## ¿Cuándo usar [[RDD]]?

* Cuando te interese controlar el flujo de [[Spark]]
* Si eres usuario de [[Python]], convertir a [[RDD]] un conjunto de datos permite controlar los datos de mejor manera.
* Estás conectándote a versiones antiguas de [[Spark]]

## ¿Cúando usar DataFrames?

* Si ponemos semántica de datos complicadas.
* Vamos a realizar tareas de alto nivel como filtros, mapeos, agregaciones, promedios o sumas.
* Si vamos a usar sentencias SQL-like.