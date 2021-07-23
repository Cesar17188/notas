# Agregación de datos

Agregación de datos es el encontrar formas en que podemos juntar los datos y sacar totales (datos sumarizados) y poder entregar reportes o en inteligencia para el negocio.

**Ejemplo 1:** sentencia MAX (obtener el máximo de una columna), en el ejemplo obtenemos el precio maximo por renta de película.

![[Pasted image 20210721203752.png]]

```sql
SELECT titulo, MAX(precio_renta)
FROM peliculas
GROUP BY titulo;
```
Haciendo el ejemplo un poco mas ordenado y enriquecido
```sql
SELECT titulo, MAX(precio_renta) AS precio_maximo_renta
FROM peliculas
GROUP BY titulo
ORDER BY precio_maximo_renta DESC;
```
Obteniendo el mínimo
```sql
SELECT titulo, MIN(precio_renta)
FROM peliculas
GROUP BY titulo;
```
**Ejemplo 2:** sentencia **SUM** (sumatoria), veremos el costo de rentar todas las peliculas del catalogo, esto nos podría servir para sacar distintos tipos de reportes como obtener las ganancias del periodo de interés (dia, mes, trimestre) y sentencia **COUNT** para realizar conteos.
![[Pasted image 20210721203837.png]]

```sql
SELECT clasificacion, COUNT(*)
FROM peliculas
GROUP BY clasificacion;
```
**Ejemplo 3:** sentencia **AVG** (promedio)

![[Pasted image 20210721203857.png]]

Utilizando lo aprendido vemos ahora los siguientes ejemplos.

**Precio promedio por clasificacion de película**.

![[Pasted image 20210721203907.png]]

```sql
SELECT clasificacion, AVG(precio_renta) as precio_promedio
FROM peliculas
GROUP BY clasificacion
ORDER BY precio_promedio DESC;
```

**Duracion promedio por clasificacion de película**.

![[Pasted image 20210721203927.png]]

```sql
SELECT clasificacion, AVG(duracion_renta) as duracion_renta_promedio
FROM peliculas
GROUP BY clasificacion
ORDER BY duracion_renta_promedio DESC;
```

**Duracion renta promedio por clasificacion de película**.

![[Pasted image 20210721203946.png]]

```sql
SELECT clasificacion, AVG(duracion_renta) as duracion_renta_promedio
FROM peliculas
GROUP BY clasificacion
ORDER BY duracion_renta_promedio DESC;
```
**Reto:** Encontrar otro query de interés para el negocio.
```sql
-- PELICULAS MAS RENTADAS
SELECT peliculas.pelicula_id, peliculas.titulo, string_agg(DISTINCT CONCAT(actores.nombre, ' ', actores.apellido), ',') as nombes_actores  , count(*) AS rentas_acumuladas
FROM rentas
-- RELACIONA RENTAS CON INVENTARIOS
JOIN inventarios
    ON rentas.inventario_id = inventarios.inventario_id
-- RELACION PELICULAS CON NO. INVENTARIO (RENTAS NO TIENE EL ID PELICULA)
JOIN peliculas
    on inventarios.pelicula_id = peliculas.pelicula_id
-- RELACIONA PELICULAS CON ACTORES_PELICULAS
JOIN peliculas_actores
    ON peliculas.pelicula_id = peliculas_actores.pelicula_id
-- RELACIONA ACTORES_PELICULAS CON ACTORES
JOIN actores 
    ON actores.actor_id = peliculas_actores.actor_id

GROUP BY   peliculas.pelicula_id
ORDER BY rentas_acumuladas DESC;
```