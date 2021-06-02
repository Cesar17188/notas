# Mapa de joins

```sql
-- todos los JOINS
-- LEFT JOIN 
-- trae todos los alumnos sin importar si tienen o no
-- carreras
SELECT a.nombre, a.apellido, a.carrera_id,
	   c.id, c.carrera
FROM platzi.alumnos AS a
	LEFT JOIN platzi.carreras AS c
	ON a.carrera_id = c.id
ORDER BY c.id DESC;

-- RIGTH JOIN
-- trae todas las carreras aun si no tienen alumnos 
SELECT a.nombre, a.apellido, a.carrera_id,
	   c.id, c.carrera
FROM platzi.alumnos AS a
	RIGHT JOIN platzi.carreras AS c
	ON a.carrera_id = c.id
-- WHERE a.id IS NULL
ORDER BY c.id DESC;

-- INNER JOIN
-- trae todas los elementos que pertenecen a ambas tablas 
SELECT a.nombre, a.apellido, a.carrera_id,
	   c.id, c.carrera
FROM platzi.alumnos AS a
	INNER JOIN platzi.carreras AS c
	ON a.carrera_id = c.id
-- WHERE a.id IS NULL
ORDER BY c.id DESC;

-- FULL OUTHER JOIN - 
-- trae todas los elementos que no tienen corresponden a la unión de ambas tablas
SELECT a.nombre, a.apellido, a.carrera_id,
	   c.id, c.carrera
FROM platzi.alumnos AS a
	FULL OUTER JOIN platzi.carreras AS c
	ON a.carrera_id = c.id
WHERE a.id IS NULL OR c.id IS NULL
ORDER BY a.carrera_id DESC, c.id DESC;
```