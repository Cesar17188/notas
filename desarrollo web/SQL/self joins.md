# Self Joins

hacer un join con la propia tabla

vamos a buscar el nombre de los alumnos cuyos tutores son otros alumnos y pondremos el nombre del alumno junto a su respectivo tutor.

```sql
SELECT CONCAT(a.nombre, ' ', a.apellido) AS alumno,
	   CONCAT(t.nombre,' ',t.apellido) AS tutor
FROM platzi.alumnos AS a
	INNER JOIN platzi.alumnos AS t ON a.tutor_id = t.id
```

Obtener los 10 tutores que sean alumnos cuyas tutorias sean con el conteo más alto.

```sql
SELECT CONCAT(t.nombre,' ',t.apellido) AS tutor,
	   COUNT(*) AS alumnos_por_tutor
FROM platzi.alumnos AS a
	INNER JOIN platzi.alumnos AS t ON a.tutor_id = t.id
GROUP BY tutor
ORDER BY alumnos_por_tutor DESC
LIMIT 10;
```

```sql
--reto promedio de los alumnos por tutor agrupado por tutor
SELECT AVG(alumnos_por_tutor) AS promedio_alumnos, tutor
FROM(
SELECT CONCAT(t.nombre,' ',t.apellido) AS tutor,
	   COUNT(*) AS alumnos_por_tutor
FROM platzi.alumnos AS a
	INNER JOIN platzi.alumnos AS t ON a.tutor_id = t.id
GROUP BY tutor
ORDER BY alumnos_por_tutor DESC) AS promedio
GROUP BY tutor
```