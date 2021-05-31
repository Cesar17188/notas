# Queries con tipo de dato DATE

### Traer solo el año de la tabla
```sql
SELECT EXTRACT(YEAR FROM fecha_incorporacion) AS anio_incorporacion
FROM platzi.alumnos;
```

```sql
SELECT DATE_PART('YEAR', fecha_incorporacion) AS anio_incorporacion
FROM platzi.alumnos
```

Traer fecha completa

```sql
SELECT DATE_PART('YEAR', fecha_incorporacion) AS anio_incorporacion,
		DATE_PART('MONTH', fecha_incorporacion) AS mes_incorporacion,
		DATE_PART('DAY', fecha_incorporacion) AS dia_incorporacion
FROM platzi.alumnos
```

```sql
SELECT DATE_PART('YEAR', fecha_incorporacion) AS anio_incorporacion,
		DATE_PART('MONTH', fecha_incorporacion) AS mes_incorporacion,
		DATE_PART('DAY', fecha_incorporacion) AS dia_incorporacion,
		DATE_PART('HOUR', fecha_incorporacion) AS hora_incorporacion,
		DATE_PART('MINUTE', fecha_incorporacion) AS minuto_incorporacion,
		DATE_PART('SECOND', fecha_incorporacion) AS segundo_incorporacion
FROM platzi.alumnos
```

### Seleccionar por año
```sql
-- Tres distintas maneras de lograr filtrar por año
SELECT *
FROM platzi.alumnos
WHERE (
	EXTRACT (YEAR from fecha_incorporacion)
) = 2018;

SELECT *
FROM platzi.alumnos
WHERE (
	DATE_PART('YEAR', fecha_incorporacion)
) = 2019;

SELECT *
FROM (
	SELECT *,
		DATE_PART('YEAR', fecha_incorporacion) as anio_incorporacion
	FROM platzi.alumnos
) AS alumnos_con_anio
WHERE anio_incorporacion = 2020;
```

selección con doble filtro
```sql
-- reto
SELECT *
FROM (
	SELECT *,
		DATE_PART('YEAR', fecha_incorporacion) as anio_incorporacion,
		DATE_PART('MONTH', fecha_incorporacion) as mes_incorporacion
	FROM platzi.alumnos
) AS alumnos_con_anio_mes
WHERE anio_incorporacion = 2020 AND mes_incorporacion = 5;
```

### Duplicados

ver duplicados

```sql

-- Distintas formas de ver duplicados
SELECT *
FROM platzi.alumnos AS ou
WHERE (
	SELECT COUNT(*)
	FROM platzi.alumnos AS inr
	WHERE ou.id = inr.id
) > 1;


SELECT (platzi.alumnos.*)::text, COUNT(*)
FROM platzi.alumnos
GROUP BY platzi.alumnos.*
HAVING COUNT(*) > 1;


SELECT (
	platzi.alumnos.nombre,
	platzi.alumnos.apellido,
	platzi.alumnos.email,
	platzi.alumnos.colegiatura,
	platzi.alumnos.fecha_incorporacion,
	platzi.alumnos.carrera_id,
	platzi.alumnos.tutor_id
	)::text, COUNT(*)
FROM platzi.alumnos
GROUP BY platzi.alumnos.nombre,
	platzi.alumnos.apellido,
	platzi.alumnos.email,
	platzi.alumnos.colegiatura,
	platzi.alumnos.fecha_incorporacion,
	platzi.alumnos.carrera_id,
	platzi.alumnos.tutor_id
HAVING COUNT(*) > 1;


SELECT * 
FROM (
	SELECT id,
	ROW_NUMBER() OVER(
		PARTITION BY 
			nombre,
			apellido,
			colegiatura,
			fecha_incorporacion,
			carrera_id,
			tutor_id
		ORDER BY id ASC
	) AS row,
	*
	FROM platzi.alumnos
) AS duplicados
WHERE duplicados.row > 1;
```

Eliminar Duplicados

```sql
-- reto eliminar duplicados de los registros
DELETE FROM platzi.alumnos
WHERE id IN (
	SELECT id 
	FROM (
		SELECT id,
		ROW_NUMBER() OVER(
			PARTITION BY 
				nombre,
				apellido,
				colegiatura,
				fecha_incorporacion,
				carrera_id,
				tutor_id
			ORDER BY id ASC
		) AS row
		FROM platzi.alumnos
	) AS duplicados
	WHERE duplicados.row > 1
);
```

