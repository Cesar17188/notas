# Sharding

Es un tipo de partición horizontal para nuestras bases de datos. Divide las tuplas de nuestras tablas en diferentes ubicaciones de acuerdo a ciertos criterios de modo que para hacer consultas, las tendremos que dirigir al _shard_ o parte que corresponda.

## Cuándo usar

Cuando tenemos grandes volúmenes de información estática que representa un problema para obtener solo unas cuantas tuplas en consultas frecuentes.

## Inconvenientes

-   Cuando debamos hacer joins frecuentemente entre shards
-   Baja elasticidad. Los shards crecen de forma irregular unos más que otros y vuelve a ser necesario usar _sharding (subsharding)_
-   La llave primaria pierde utilidad