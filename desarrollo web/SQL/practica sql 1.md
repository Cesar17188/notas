# Queries implementados en PostgreSQL con las tablas de platzi

## El primero
### query 1
```sql
SELECT *
FROM platzi.alumnos
LIMIT 1;
```

### window functions
```sql
SELECT *
FROM (
	SELECT ROW_NUMBER() OVER() AS row_id, *
	FROM platzi.alumnos
) AS alumnos_with_row_num;
```

### window functions con WHERE
```sql
SELECT *
FROM (
	SELECT ROW_NUMBER() OVER() AS row_id, *
	FROM platzi.alumnos
) AS alumnos_with_row_num
WHERE row_id = 1;
```

### Los 10 primeros registros con WHERE (se puede usar LIMIT 10 en lugar de WHERE)
```sql
SELECT *
FROM (
	SELECT ROW_NUMBER() OVER() AS row_id, *
	FROM platzi.alumnos
) AS alumnos_with_row_num
WHERE row_id <= 10
;
```

## El segundo

### Traer la segunda colegiatura más cara con sub querie
```sql
SELECT DISTINCT colegiatura
FROM platzi.alumnos AS a1
WHERE 2 = (
	SELECT COUNT (DISTINCT colegiatura)
	FROM platzi.alumnos AS a2
	WHERE a1.colegiatura <= a2.colegiatura
);
```

### Traer la segunda colegiatura más cara del tutor 20
```sql
SELECT DISTINCT colegiatura, tutor_id
FROM platzi.alumnos
WHERE tutor_id = 20
ORDER BY colegiatura DESC
LIMIT 1 OFFSET 1; 
``` 

### Traer todos los registros de alumnos cuya colegiatura sea la segunda más cara y sea impartida por el tutor 20

```sql
SELECT *
FROM platzi.alumnos AS datos_alumnos
INNER JOIN (
	SELECT DISTINCT colegiatura
	FROM platzi.alumnos
	WHERE tutor_id = 20
	ORDER BY colegiatura DESC
	LIMIT 1 OFFSET 1
) AS segunda_mayor_colegiatura
ON datos_alumnos.colegiatura = segunda_mayor_colegiatura.colegiatura
```

```sql
SELECT *
FROM platzi.alumnos AS datos_alumnos
WHERE colegiatura = (
	SELECT DISTINCT colegiatura
	FROM platzi.alumnos
	WHERE tutor_id = 20
	ORDER BY colegiatura DESC
	LIMIT 1 OFFSET 1
);
```

### Traer la segunda mitad de los registros de la tabla de alumnos de platzi
```sql
SELECT *
FROM platzi.alumnos AS datos_alumnos
WHERE datos_alumnos.id > (
	SELECT COUNT(platzi.alumnos.id)/2
	FROM platzi.alumnos
);
```