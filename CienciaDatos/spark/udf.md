# ¿Qué es un UDF?
Las **funciones definidas por el usuario** o **UDF**, por sus siglas en inglés, son una funcionalidad agregada en [[Spark]] para definir funciones basadas en columnas las cuales permiten extender las capacidades de [[Spark]] al momento de transformar el set de datos.

Este tipo de implementaciones son convenientes cuando tenemos un desarrollo extenso donde hemos identificado la periodicidad de tareas repetitivas como suele ser en pasos de limpieza de datos, transformación o renombrado dinámico de columnas.

Por lo anterior es común encontrar en un proyecto de Spark una librería independiente donde existen todas estas funciones agregadas para que los desarrolladores involucrados en el proyecto puedan usarlas a conveniencia.

El uso de UDF no implica que las funciones que podemos crear nativamente con Python, Scala, R o Java no sean útiles. Una UDF tiene el objetivo de ofrecer un estándar interno en el proyecto que nos encontremos realizando. Además, en caso de ser necesario, una UDF puede ser modificada con ayuda de decoradores para que sea más extensible en diversos escenarios a los cuales nos podemos enfrentar.

Otro motivo para usar UDF es que en el módulo de [[Spark]] MLlib, la librería nativa de Spark para operaciones de Machine Learning, las UDF juegan un papel vital al momento de hacer transformaciones. Por lo cual tener un uso familiar de estas ampliará considerablemente la curva de aprendizaje de Spark MLlib.