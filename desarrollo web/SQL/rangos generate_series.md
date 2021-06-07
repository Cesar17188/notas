# Rangos generate_series

```sql
-- Generar rangos
-- Generar series con un número inicial, un número final
-- y paso de la seríe

SELECT * 
FROM generate_series(1.1,4,1.3);

SELECT current_date + s.a AS dates
FROM generate_series(0,14,7) AS s(a)


SELECT *
FROM generate_series('2020-09-01 00:08:00'::timestamp,
					'2020-09-04 12:00:00', '10 hours');
					

SELECT a.id, a.nombre, a.apellido, a.carrera_id,
		s.a
FROM platzi.alumnos AS a
	INNER JOIN generate_series(0,10) AS s(a)
	ON s.a = a.carrera_id
ORDER BY a.carrera_id;
```