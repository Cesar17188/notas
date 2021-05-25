# Agregación y limitantes (GROUP BY y LIMIT)

`GROUP BY` es una sentencia que agrupa filas que tienen el mismo valor en columnas con el sumatorio. Como decirle ‘encuentra el número de clientes en cada país’.

Suele usarse frecuentemente con las funciones `COUNT` `MAX` `MIN` `MAX` `SUM` `AVG` a un grupo de una o más columnas.

```sql
SELECT *
FROM tabla_diaria
GROUP BY marca;

SELECT *
FROM tabla_diaria;
GROUP BY marca, modelo;

SELECT COUNT(CustomerID), Country
FROM Customers
GROUP BY Country
ORDER BY COUNT(CustomerID) DESC;
```

`SELECT TOP` es usada para especificar el número de registros que se van a retornar.

`SELECT TOP` es útil para tablas con miles de registros, pues un gran número de registros puede afectar el rendimiento.

```sql
SELECT TOP number
FROM table1
WHERE condition;

SELECT TOP 1500
FROM tabla_diaria;
```