# Particionado de datos

Como se ha descrito en clases pasadas, los [[RDD]] son la capa de abstracción primaria para poder interactuar con los datos que viven en nuestro ambiente de [[Spark]]. Aunque estos puedan ser enmascarados con un esquema dotándolos de las facultades propias de los [[DataFrames]], la información de fondo sigue operando como [[RDD]].

Por lo tanto, la información, como indica el nombre de los [[RDD]], se maneja de forma distribuida a lo largo del [[clúster]], facilitando las operaciones que se van a ejecutar, ya que segmentos de información pueden encontrarse en diferentes ejecutores reduciendo el tiempo necesario para acceder a la información y poder así realizar los cálculos necesarios.

Cuando un [[RDD]] o [[Dataframe]] es creado, según las especificaciones que se indiquen a la aplicación de [[Spark]], creará un **esquema de particionado básico**, el cual distribuirá los datos a lo largo del [[clúster]]. Siendo así que al momento de ejecutar una acción, esta se ejecutará entre los diversos fragmentos de información que existan para poder así realizar de la forma más rápida las operaciones. Es por eso que un correcto esquema de particionado es clave para poder tener aplicaciones rápidas y precisas que además consuman pocos recursos de red.

Otra de las tareas fundamentales es la **replicación de componentes y sus fragmentos**, ya que al aumentar la disponibilidad de estos podremos asegurar una tolerancia a fallos, mientras más se replique un valor es más probable que no se pierda si existe un fallo de red o energía, además de permitir una disponibilidad casi inmediata del archivo buscado.

La partición y replicación son elementos que deben ser analizados según el tipo de negocio o requerimientos que se tengan en el desarrollo que se encuentre en progreso, por lo cual la cantidad de datos replicados o granularidad de datos existentes en los fragmentos dependerá en función de las reglas de negocio.

