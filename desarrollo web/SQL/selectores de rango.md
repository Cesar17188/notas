# Selectores de rango

Los tipos de rango que vienen en PostgreSQL son:

-   int4range: Que trae un rango de enteros.
-   int8range: Es un rango de enteros grandes.
-   numrange: Es un rango numérico.
-   tsrange: Es un rango del tipo timestamp pero sin la zona horaria.
-   tstzrange: Es un rango del tipo timestamp con la zona horaria
-   daterange: Es un rango del tipo fecha.  
  
    Esos son los que podemos usar como selectores de rango dentro de PostgreSQL si les interesa conocer más [Acá](https://www.postgresql.org/docs/9.2/rangetypes.html)
	 
```sql
	 SELECT *
FROM platzi.alumnos
WHERE tutor_id IN (1,2,3,4)

SELECT *
FROM platzi.alumnos
WHERE tutor_id >= 1
AND tutor_id <= 10;

SELECT *
FROM platzi.alumnos
WHERE tutor_id BETWEEN 1 AND 10;

SELECT int4range(1, 20) @>3

SELECT numrange(11.1, 19.9) && numrange(20.0, 30.0);

SELECT UPPER(int8range(15, 25));

SELECT LOWER(int8range(15, 25));

SELECT int4range(10,20) * int4range(15,25);

SELECT ISEMPTY (numrange(1,5));


SELECT *
FROM platzi.alumnos
WHERE int4range(10,20) @> tutor_id;

-- reto

SELECT int4range(MIN(tutor_id), MAX(tutor_id)) 

SELECT numrange(
	(SELECT MIN(tutor_id) FROM platzi.alumnos),
	(SELECT MAX(tutor_id) FROM platzi.alumnos)
) * numrange(
	(SELECT MIN(carrera_id) FROM platzi.alumnos),
	(SELECT MAX(carrera_id) FROM platzi.alumnos)
);

	 ```
	 
	 