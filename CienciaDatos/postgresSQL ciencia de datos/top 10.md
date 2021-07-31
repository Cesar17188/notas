# Top 10

Los dashboards generalmente se miden como data points, generalmente tienen diferentes secciones, algunas tabulares, otras con formas de gráfica y en este caso vamos a realizar un top 10 de rentas de peliculas (aunque ya lo hice antes en el reto y el tutorial Hi Five).

![[Pasted image 20210728101917.png]]

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

**ROW_NUMBER()** es una **window function** que asigna un numero entero secuencial a cada row (fila) de un query resultante, una window function siempre contiene una clausula **OVER()** directamente seguida por el nombre de la window function y las argumentos de la misma.

A window function call always contains an OVER clause directly following the window function's name and argument(s).

```sql
ROW_NUMBER() OVER (
    [PARTITION BY expr1, expr2,...]
    ORDER BY expr1 [ASC | DESC], expr2,...
)
```

-   _PARTITION BY_ divide el set resultante retornado por la clausula FORM en particiones, esta clausula es opcional, si la omites el set resultante es tratado como una sola partición de datos.
    
-   **ORDER BY** es una clausula requerida, esta ordena las filas en cada partición, ya que ROW_NUMBER es una funcion de orden sensitiva o sensible al orden.
    

Finalmente a cada fila de la partición le es asignado un numero secuencial en la columna row_number

Otro ejemplo

```sql
-- TOP TEN MEJORES CLIENTES
SELECT
    ROW_NUMBER() OVER (
        ORDER BY sum(pagos.cantidad) DESC
    ) AS top_clientes,
    clientes.cliente_id,
    clientes.nombre,
    clientes.apellido,
    SUM(cantidad) AS total_pagos_cliente
    FROM pagos
    JOIN clientes ON pagos.cliente_id = clientes.cliente_id
    GROUP BY clientes.cliente_id
;
```

Usando **PARTITION BY** para segmentar los mejores clientes por tienda, usando tambien CTE's

```sql
-- TOP MEJORES CLIENTES
WITH ventas_peliculas_por_tienda AS (
    SELECT
    clientes.tienda_id AS sucursal,
    clientes.cliente_id,
    clientes.nombre,
    clientes.apellido,
    SUM(cantidad) AS total_pagos_cliente
    FROM pagos
    JOIN clientes ON pagos.cliente_id = clientes.cliente_id
    GROUP BY clientes.cliente_id, sucursal
    )
    SELECT 
        ROW_NUMBER() OVER (
        PARTITION BY sucursal
        ORDER BY total_pagos_cliente DESC
    ) AS top_clientes,
    sucursal,
    cliente_id,
    nombre,
    apellido,
    total_pagos_cliente
    FROM ventas_peliculas_por_tienda
    WHERE total_pagos_cliente > 150
    ;

```
