# Apache Spark
## ¿Qué es Spark?
* [[framework]] de desarrollo de procesos de Big Data
* [[framework]] preocupado por la velocidad del proceso

Spark se preocupa más por la velocidad de procesamiento, es decir que los procesos en ejecución sea en la práctica en tiempo real. Mientras que [[Hadoop]] (su [[framework]] riva) se preocupa más por el almacenamiento masivo de datos.

![](https://phoenixnap.com/kb/wp-content/uploads/2020/05/hadoop-spark-data-processing.png)

[[big data]] es una filosofía sobre el manejo de datos masivos que necesita de [[framework]]s como spark o [[Hadoop]] para su desarrollo.

Spark se preocupa por mantener la información en memoria RAM, por lo que se ve mejoras significativas en la velocidad de procesos

Todas las aplicaciones en Spark poseen un manejador central de programa (Driver) y varios ejecutores que se crean a lo largo del clúster, estas son las computadoras que realizarán las tareas en paralelo y finalmente devolverán los valores al driver, la aplicación central.


## ¿Qué lenguajes se puede usar esta tecnología?

* [[Java]]
* [[Scala]]
* [[Python]] 
* [[R]]

**Spark** nativamente utiliza el lenguaje **[[Scala]]** y **[[Scala]]** a su vez, utiliza la máquina virtual de [[Java]]. Pero el desarrollo con [[Java]] es algo complicado, por lo que Spark permite su desarrollo con facilidad en lenguajes como [[Python]].

## Componentes de Spark
Las dos principales estructuras que soporta Spark son:

* [[RDD]]
* [[dataframes spark]]

La diferencia reside en la estrutura que poseen

## Limitaciones de Spark

* Spark no es una base de datos, Spark no esta diseñado para realizar operaciones de tecnología [[OLAP]] (es decir de una base de datos tradicional), por lo que si se pone a ingresar, editar, eliminar datos, Spark funcionara de manera muy deficiente. 


 ![](https://carlospesquera.com/wp-content/uploads/2020/02/OLTP-vs-OLAP.png)

## Historia de Spark
* Nace en 2009 en la universidad de Berkeley
* Heredera de [[Hadoop]] como la siguiente versión de [[Hadoop]]
* Versión 3 liberada el 10 de Junio del 2020. Presentando mejoras de optimización en el procesamiento de información.

## Spark vs Hadoop

* Spark se enfoca en el procesamiento de datos desde la memoria RAM
* Spark posee naturalmente un módulo para ML([[machine learning]]), [[streaming]] de datos y [[grafos]]
* No depende de un sistema de archivos, por lo que se puede consumir archivos o datos directamente desde cualquier lugar

![](https://phoenixnap.com/kb/wp-content/uploads/2020/05/hadoop-spark-data-processing.png)

![](https://www.researchgate.net/profile/Sherif_Sakr/publication/304454449/figure/fig3/AS:614225084956672@1523454080036/Spark-Framework-vs-Hadoop-Framework.png)

