# Window functions

Otra de las caracteristicas muy importantes que tienes Postgres son las **window functions** [[window functions]] que nos ayudan a **relacionar un row o un registro en particular con el resto de registros de la tabla y cual es su relación** con ellos, por ejemplo como se posiciona dentro de un ordenamiento o cual es el rango que ocupa.

Con los **window functions podemos hacer un rank** saber en que lugar se ocupa cierto campo, cual tiene mayor cantidad, cual es el 1er, el 2do o el 3ero, todo eso sin hacer sub-queries nos permitirá obtener relaciones entre los datos de forma sencilla.

Otras cosas que puedes hacer es obtener un rango, percent_rank, dense_rank (diferenciar valores repetidos)

Aquí el enlace a la documentación [https://www.postgresql.org/docs/12/functions-window.html](https://www.postgresql.org/docs/12/functions-window.html)