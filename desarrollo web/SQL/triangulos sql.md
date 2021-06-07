# Triangulos sql

```sql
-- lpad left padding
-- rellenar el espacio designado con una cadena sql
-- y con un símbolo
SELECT lpad('sql', 15, '*');

SELECT lpad('*', id, '*'), carrera_id
FROM platzi.alumnos
WHERE id < 10
ORDER BY carrera_id;

SELECT lpad('*', CAST(row_id AS int), '*')
FROM (
	SELECT ROW_NUMBER() OVER(ORDER BY carrera_id) AS row_id, *
	FROM platzi.alumnos
) AS alumnos_with_row_id
WHERE row_id <=5
ORDER BY carrera_id;
```

Para finalizar el rpad lo agrega como un sufijo a la oración o texto que le hayamos dado y el lpad lo agrega como un prefijo.  
Si quieren leer un poco más acá les dejo este [link](https://www.w3schools.com/sql/func_mysql_rpad.asp)