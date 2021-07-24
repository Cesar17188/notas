# Trabajando con objetos

Una de las funcionalidades mas interesantes de Postgres es que nos permite trabajar con objetos JSON.

Postgres tiene dos implementaciones para esto, Json normal y JSONb (de binary) donde ellos guardan internamente el objeto en binario.

Trabajar con JSON dará mucha flexibilidad al desarrollo, y guardar estados, Postgres permite trabajar directamente con Json sin necesidad de usar parsers de python u otro lenguaje de programación.

Ejemplo

Creamos la tabla e insertamos datos de ejemplo

![[Pasted image 20210723191801.png]]

```sql
CREATE TABLE ordenes (
    ID serial NOT NULL PRIMARY KEY,
    info json NOT NULL
);

INSERT INTO ordenes (info)
VALUES
(
    '{"cliente": "David Sanchez", "items": {"producto":"Biberon", "cantidad": "24"}}'
),
(
    '{"cliente": "Edna Cardenas", "items": {"producto":"Carro Juguete", "cantidad": "1"}}'
),
(
    '{"cliente": "Israel Vazquez", "items": {"producto":"Tren Juguete", "cantidad": "2"}}'
);
```
Puedes obtener la respuesta como un select normal que contiene la data en json

![[Pasted image 20210723191819.png]]

```sql
SELECT
    info -> 'cliente' AS cliente
FROM ordenes;
```
Podemos obtenerla como texto

![[Pasted image 20210723191838.png]]

```sql
SELECT
    info ->> 'cliente' AS cliente
FROM ordenes;
```

Obtener todos los datos del json

![[Pasted image 20210723191905.png]]

```sql
SELECT
    info ->> 'cliente' as cliente,
    info -> 'items' ->> 'producto' as producto,
    info -> 'items' ->> 'cantidad' as cantidad
FROM ordenes;
```

Aplicando in **WHERE** para obtener determinada data

![[Pasted image 20210723191924.png]]

```sql
SELECT
    info ->> 'cliente' as cliente
FROM ordenes
WHERE info -> 'items' ->> 'producto' = 'Biberon';
```