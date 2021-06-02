# Diferencias sql

Resolviendo el reto con left join:

```sql
SELECT a.nombre, a.apellido, a.carrera_id,
	   c.id, c.carrera
FROM platzi.alumnos AS a
	LEFT JOIN platzi.carreras AS c
	ON a.carrera_id = c.id;
```

y con Full Outer Join (atentos acá con los null de cursos borrados):

```sql
SELECT a.nombre,a.apellido,a.carrera_id,
       c.id,c.carrera
FROM platzi.alumnos AS a
    FULL OUTER JOIN platzi.carreras as c ON c.id = a.carrera_id
WHERE a.nombre IS NOT NULL
ORDER BY a.carrera_id;
```

```sql
-- diferencias, son los elementos que se encuentran en una tabla
-- que no se encuentran en una tabla distinta

SELECT carrera_id, COUNT(*) AS cuenta
FROM platzi.alumnos
GROUP BY carrera_id
ORDER BY cuenta DESC;

-- DELETE FROM platzi.carreras
-- WHERE id BETWEEN 30 AND 40;

SELECT a.nombre, a.apellido, a.carrera_id,
	   c.id, c.carrera
FROM platzi.alumnos AS a
	LEFT JOIN platzi.carreras AS c
	ON a.carrera_id = c.id
WHERE c.id IS NULL
ORDER BY a.carrera_id;

--reto

SELECT a.nombre, a.apellido, a.carrera_id,
	   c.id, c.carrera
FROM platzi.alumnos AS a
	FULL OUTER JOIN platzi.carreras AS c
	ON a.carrera_id = c.id
ORDER BY a.carrera_id;
```