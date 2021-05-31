# Máximos en una tabla
Sacar la última fecha de incorporación de los alumnos
```sql
SELECT fecha_incorporacion
FROM platzi.alumnos
ORDER BY fecha_incorporacion DESC
LIMIT 1;
```
Sacar la última fecha de incorporación de los alumnos por carrera
```sql
SELECT carrera_id, MAX(fecha_incorporacion)
FROM platzi.alumnos
GROUP BY carrera_id
ORDER BY carrera_id;
```

Sacar el nombre inicial alfabéticamente inferior

```sql
SELECT MIN(nombre)
FROM platzi.alumnos
```

Sacar el nombre alfabñeticamente inferior por tutor
```sql
SELECT MIN(nombre), tutor_id
FROM platzi.alumnos
GROUP BY tutor_id
ORDER BY tutor_id
``` 

