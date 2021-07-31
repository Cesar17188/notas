# Ordenando datos geográficos

Estos son tipos de datos que se pueden presentar en diferentes formas (latitud, longitud, códigos de países, ciudades, etc), lo acostumbrado es pintar los datos en el dashboard e integrarle color de manera visual (tipo mapas covid-19)

```sql
SELECT ciudades.ciudad_id,
        ciudades.ciudad,
        COUNT (*) AS rentas_por_ciudad
FROM ciudades
    INNER JOIN direcciones ON ciudades.ciudad_id = direcciones.ciudad_id
    INNER JOIN tiendas ON direcciones.direccion_id = tiendas.direccion_id
    INNER JOIN inventarios ON tiendas.tienda_id = inventarios.tienda_id
    INNER JOIN rentas ON inventarios.inventario_id = rentas.inventario_id
GROUP BY ciudades.ciudad_id;
```

