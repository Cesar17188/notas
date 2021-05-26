# Seleccionar de un set de opciones

## Seleccionar desde un set opciones
### Seleccionar valores especificos por el row

```sql
SELECT * 
FROM ( 
	SELECT ROW_NUMBER() OVER() AS row_id, *
	FROM platzi.alumnos
) AS alumnos_with_row_num
WHERE row_id IN (1,5,10,12,15,20);
```

### Traer todos los alumnos que tengan al profesor con id 30 
```sql
SELECT *
FROM platzi.alumnos
WHERE id IN (
	SELECT id 
	FROM platzi.alumnos
	WHERE tutor_id = 30
);
```