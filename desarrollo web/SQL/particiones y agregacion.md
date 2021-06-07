# Particiones y agregación

**- ROW_NUMBER()**: nos da el numero de la tupla que estamos utilizando en ese momento.  
**- OVER([PARTITION BY column] [ORDER BY column DIR])**: nos deja Particionar y Ordenar la window function.  
**- PARTITION BY(column/s)**: es un group by para la window function, se coloca dentro de OVER.  
**- FIRST_VALUE(column)**: devuelve el primer valor de una serie de datos.  
**- LAST_VALUE(column)**: Devuelve el ultimo valor de una serie de datos.  
**- NTH_VALUE(column, row\number)**: Recibe la columna y el numero de row que queremos devolver de una serie de datos  
**- RANK()**: nos dice el lugar que ocupa de acuerdo a el orden de cada tupla, deja gaps entre los valores.  
**- DENSE_RANK()**: Es un rango mas denso que trata de eliminar los gaps que nos deja RANK.  
**- PERCENT_RANK()**: Categoriza de acuerdo a lugar que ocupa igual que los anteriores pero por porcentajes.

```sql
-- Particiones y agregación

SELECT ROW_NUMBER() OVER() as row_id, *
FROM platzi.alumnos;

-- Partición

SELECT ROW_NUMBER() OVER(ORDER BY fecha_incorporacion) as row_id, *
FROM platzi.alumnos;

SELECT FIRST_VALUE(colegiatura) OVER(PARTITION BY carrera_id) as primera_colegiatura, *
FROM platzi.alumnos;

SELECT LAST_VALUE(colegiatura) OVER(PARTITION BY carrera_id) as ultima_colegiatura, *
FROM platzi.alumnos;

SELECT NTH_VALUE(colegiatura, 3) OVER(PARTITION BY carrera_id) as n_colegiatura, *
FROM platzi.alumnos;

-- Rango

SELECT *,
	DENSE_RANK() OVER(PARTITION BY carrera_id ORDER BY colegiatura DESC) AS colegiatura_rank
FROM platzi.alumnos
ORDER BY carrera_id, colegiatura_rank;

-- PERCENT RANK
-- (rank - 1)/ (total rows)

SELECT *,
	PERCENT_RANK() OVER(PARTITION BY carrera_id ORDER BY colegiatura DESC) AS colegiatura_rank
FROM platzi.alumnos
ORDER BY carrera_id, colegiatura_rank;
```