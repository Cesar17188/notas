# Common table expressions

Como parte de los casos practicos y de las herramientas que nos brinda postgreSQL existen los **Common table expressions**, esto tiene que ver con que se utilizan als expresiones de las tablas en una forma en que pueden ahorrar memoria, hemos visto cuestiones con sub-queries o anidaciones que pueden consumir demasiados recursos, y es la razón por la que se crearon estas herramientas que nos ayudan a quitar carga a estos procesos y hacer algunos procesos iterativos que SQL normal no nos permite utilizar estructuras de control e iterativas, las **Common table expressions** nos permite hacer este tipo de acciones

![[Pasted image 20210726200641.png]]

```sql
WITH RECURSIVE tabla_recursiva(n) AS (
    VALUES (1)
    UNION ALL
    SELECT n+1 FROM tabla_recursiva WHERE n < 100
) SELECT SUM(n) FROM tabla_recursiva; 

```

Otro caso de uso seria extraer los datos de una tabla y metiéndonos a otra pero iterando sobre ellos.

Lee mi tutorial en platzi

[https://platzi.com/tutoriales/1780-postgresql-datos/7204-common-table-expressions/](https://platzi.com/tutoriales/1780-postgresql-datos/7204-common-table-expressions/)

Aquí un ejemplo del uso

```sql
-- tabla temporal 1
WITH peliculas_rentadas AS (
    SELECT pelicula_id, COUNT(fecha_renta) AS rentas_acumuladas
    FROM inventarios
    JOIN  rentas
        ON inventarios.inventario_id = rentas.inventario_id
    GROUP BY inventarios.pelicula_id
    ORDER BY rentas_acumuladas DESC
),

-- tabla temporal 2
peliculas_categoria_horror AS (
    SELECT pelicula_id, nombre
    FROM peliculas_categorias
    JOIN categorias
        ON peliculas_categorias.categoria_id = categorias.categoria_id
    WHERE
        categorias.nombre = 'Horror'
)

SELECT
    peliculas.titulo,
    peliculas.clasificacion,
    peliculas_categoria_horror.nombre AS genero,
    peliculas_rentadas.rentas_acumuladas AS rentas_acumuladas,
    precio_renta * (peliculas_rentadas.rentas_acumuladas) AS monto_rentas_acumulado

FROM peliculas
    JOIN peliculas_categoria_horror
        ON peliculas.pelicula_id = peliculas_categoria_horror.pelicula_id
    JOIN peliculas_rentadas
        ON peliculas.pelicula_id = peliculas_rentadas.pelicula_id

WHERE
    peliculas.duracion > 100 and peliculas.precio_renta < 1 ;
```

