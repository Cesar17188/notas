# Window Functions

¿Qué son?

Realizan cálculos en algunas tuplas que se encuentran relacionadas con la tupla actual.

¿Para que sirven?

Evitan el uso de self joins y reduce la complejidad alrededor de la analítica, agregaciones y uso de cursores.

Una función de ventana es una variación de una función de agregación. Cuando una función de agregación, como sum()y mean(), toma n entradas y devuelve un solo valor, una función de ventana devuelve n valores. La salida de una función de ventana depende de todos sus valores de entrada, por lo que las funciones de ventana no incluyen funciones que funcionan por elementos, como round(). Las funciones de ventana incluyen variaciones en funciones agregadas, como cumsum()y cummean(), funciones para clasificar y ordenar, como rank(), y funciones para tomar compensaciones, como lead()y lag().

```sql
-- Window function

SELECT *,
		AVG(colegiatura) OVER ()
FROM platzi.alumnos;


SELECT *,
		SUM(colegiatura) OVER (PARTITION BY carrera_id ORDER BY colegiatura)
FROM platzi.alumnos;

SELECT *,
		RANK() OVER (PARTITION BY carrera_id ORDER BY colegiatura DESC)
FROM platzi.alumnos;

SELECT *,
		RANK() OVER (PARTITION BY carrera_id ORDER BY colegiatura DESC) AS brand_rank
FROM platzi.alumnos
ORDER BY carrera_id, brand_rank;

SELECT *
FROM (
	SELECT *,
	RANK() OVER (PARTITION BY carrera_id ORDER BY colegiatura DESC) AS brand_rank
	FROM platzi.alumnos
) AS ranked_colegiaturas_por_carrera
WHERE brand_rank < 3
ORDER BY brand_rank;
```