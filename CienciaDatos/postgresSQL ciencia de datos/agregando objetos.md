# Agregando objetos

Exploraremos las propiedades de los objetos Json para realizar sumarizaciones, una habilidad que como Data Scientist requieres.
![[Pasted image 20210723193022.png]]

```sql
SELECT
    MIN (
        CAST ( -- CAST TRANSFORMA UN TIPO DE DATO EN OTRO
            info -> 'items' ->> 'cantidad' AS INTEGER
        )
    ),
    MAX (
        CAST ( -- CAST TRANSFORMA UN TIPO DE DATO EN OTRO
            info -> 'items' ->> 'cantidad' AS INTEGER
        )
    ),
    SUM (
        CAST ( -- CAST TRANSFORMA UN TIPO DE DATO EN OTRO
            info -> 'items' ->> 'cantidad' AS INTEGER
        )
    ),
    AVG (
        CAST ( -- CAST TRANSFORMA UN TIPO DE DATO EN OTRO
            info -> 'items' ->> 'cantidad' AS INTEGER
        )
    )
FROM Ordenes;
```

Ten en cuenta que el realizar este tipo de computo es costoso para el motor de base de datos una alternativa es usar la opción de JsonB que es un tanto mas eficiente, aunque también permite hacerle frente a bases NO SQL como MongoDB