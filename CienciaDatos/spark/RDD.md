# RDD (Resilient Distributed Dataset)

Son el componente mínimo con el cual podemos comunicarnos con [[Spark]], son el lenguaje ensanblados que posee [[Spark]].

[[Spark]] posee desde la verisón 1.0 los RDD, los acuales son tolerantes a fallos y pueden ser distribuidos a lo largo de los nodos del [[clúster]].

Los RDD pueden ser creados al cargar datos de manera distribuida, como es desde un HDFS, Cassandra, Hbase o cualquier sistema de datos soportado por Hadoop, pero también por colecciones de datos de [[Scala]] o [[Python]], además de poder ser leídos desde archivos en el sistema local.

En visión general, un RDD puede ser visto como un set de datos los cuales soportan solo dos tipos de operaciones: **transformaciones y acciones**.

Las transformaciones permiten crear un nuevo RDD a partir de uno previamente existente, mientras que las acciones retornan un valor al _driver_ de la aplicación. El núcleo de operación del paradigma de Spark es la ejecución perezosa (_Lazy_), es decir que las transformaciones solo serán calculadas posterior a una llamada de acción.

Además, los RDD poseen una familiaridad con el paradigma orientado a objetos, lo cual permite que podamos realizar operaciones de bajo nivel a modo. _Map_, _filter_ y _reduce_ son tres de las operaciones más comunes.

Una de las grandes ventajas que ofrecen los RDD es la compilación segura; por su particularidad de ejecución perezosa, se calcula si se generará un error o no antes de ejecutarse, lo cual permite identificar problemas antes de lanzar la aplicación. El pero que podemos encontrar con los RDD es que no son correctamente tratados por el _Garbage collector_ y cuando las lógicas de operación se hacen complejas, su uso puede resultar poco práctico, aquí entran los [[dataframes spark]].

## Caraterísticas de los RDD

* Principal abstracción de datos
	*	Es la unidad básica, existen desde su inicio (2009) hasta su versión 3.0
* Distribución
	* Los RDD se distribuyen y particionan a lo largo del [[clúster]]
* Creación simple
	* Al no poseer estructura formal, adoptan la más intuitiva, son un conjunto de datos([[dataset]]).
* Inmutabilidad
	* Posterior a su creación no se pueden modificar. Como por ejemplo las tuplas de datos
* Ejecución perezosa
	* A menos que se realice una acción, todo lo que esta en el código no corre. 

## Transformaciones y acciones
```markdown
| Transformaciones| Acciones  | 
|-----------------|-----------|
|    orderBy()    |  show()   |
|    groupBy()    |  take()   |
|    filter()     |  count()  |
|    select()     |  collect()|
|    join()       |  save()   | 
```

mientras la sintaxis este correcta Spark interpretara las acciones que realicemos, por lo que hasta que realicemos una tranformacion o una acción, es posible que no aparescan errores en el código. 