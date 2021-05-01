# Persistencia

## Problemas al usar un [[RDD]] o [[DataFrame]] varias veces:

-> [[Spark]] recomputa el componente y sus dependencias cada vez que se ejecuta una acción
-> Es costoso (especialmente en problemas iterativos)

## Solución

-> Conservar el componente en memoria y/o disco.
-> Métodos cache() o persist() nos ayudan.
-> En PySpark los datos son almacenados de forma serializada

![](https://iamluminousmen-media.s3.amazonaws.com/media/spark-partitions/spark-partitions-2.jpg)

![](https://miro.medium.com/max/3200/0*XvFAoU7nb3fv-1J3.jpg)