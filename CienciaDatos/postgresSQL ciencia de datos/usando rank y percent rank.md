# Usando rank y percent rank

Ya vimos como hacer un top ten utilizando window functions, como lo vimos estas nos ayudan a traer la relación entre un registro y el resto del dataset para saber que lugar ocupa o que rango ocupa.

Partimos del mismo query de la clase de top ten, en esta clase vamos a explorar rank, dense_rank y percentile_rank

```sql
SELECT
    peliculas.pelicula_id as id,
    peliculas.titulo,
    COUNT (*) AS numero_rentas,
    --WINDOW FUNCTION
    ROW_NUMBER() OVER (
       ORDER BY COUNT (*) DESC
    ) AS lugar
FROM rentas
    INNER JOIN inventarios ON rentas.inventario_id = inventarios.inventario_id
    INNER JOIN peliculas ON inventarios.pelicula_id = peliculas.pelicula_id
GROUP BY peliculas.pelicula_id
ORDER BY numero_rentas DESC
LIMIT 10;
```

Percentile Rank

![[Pasted image 20210728104900.png]]

Observamos que la unidad corresponde a la pelicula mas rentada o con una probabilidad de 1.

```sql
SELECT
    peliculas.pelicula_id as id,
    peliculas.titulo,
    COUNT (*) AS numero_rentas,
    --WINDOW FUNCTION
    PERCENT_RANK() OVER (
       ORDER BY COUNT (*) ASC
    ) AS lugar
FROM rentas
    INNER JOIN inventarios ON rentas.inventario_id = inventarios.inventario_id
    INNER JOIN peliculas ON inventarios.pelicula_id = peliculas.pelicula_id
GROUP BY peliculas.pelicula_id
ORDER BY numero_rentas DESC
;
```

Dense Rank

![[Pasted image 20210728104934.png]]

```sql
SELECT
    peliculas.pelicula_id as id,
    peliculas.titulo,
    COUNT (*) AS numero_rentas,
    --WINDOW FUNCTION
    DENSE_RANK() OVER (
       ORDER BY COUNT (*) DESC
    ) AS lugar
FROM rentas
    INNER JOIN inventarios ON rentas.inventario_id = inventarios.inventario_id
    INNER JOIN peliculas ON inventarios.pelicula_id = peliculas.pelicula_id
GROUP BY peliculas.pelicula_id
ORDER BY numero_rentas DESC
;
```

Observamos como las peliculas con 32 rentas todas comparten la posición 3 en el rango, pues no seria justo desplazarlas a números inferiores solo por su orden de aparición de id

Estas window functions nos ahorraron muchísimos cálculos matemáticos que hubiéramos tenido que hacer con sub-queries o con tablas temporales with
