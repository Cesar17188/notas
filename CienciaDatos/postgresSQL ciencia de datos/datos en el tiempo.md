# Datos en el tiempo

Una linea de tiempo es importante para encontrar Picos de eventos, tendencias las cuales pueden ser positivas o negativas.

Vamos a hacer un query relacionado con una linea de tiempo utilizando la funcion **date_part**.

![[Pasted image 20210728110554.png]]

```sql
SELECT 
    date_part('year', rentas.fecha_renta) as anio,
    date_part('month', rentas.fecha_renta) as mes,
    peliculas.titulo,
    COUNT (*) AS numero_rentas
FROM rentas
    INNER JOIN inventarios ON rentas.inventario_id = inventarios.inventario_id
    INNER JOIN peliculas ON inventarios.pelicula_id = peliculas.pelicula_id
GROUP BY anio, mes, peliculas.titulo
ORDER BY anio, mes;
```

Otra vista de ejemplo

![[Pasted image 20210728110612.png]]

```sql
SELECT
    date_part('year', rentas.fecha_renta) as anio,
    date_part('month', rentas.fecha_renta) as mes,
    COUNT (*) AS numero_rentas
FROM rentas
GROUP BY anio, mes
ORDER BY anio, mes;
```
