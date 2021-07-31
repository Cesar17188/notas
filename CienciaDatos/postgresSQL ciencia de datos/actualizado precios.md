# Actualizando precios

Otra de las tareas comunes que te encontraras en la ciencia de datos es actualizar datos o guardalos de una forma ligeramente diferente en otro lugar, en este caso vamos a hacer una actualizacion de precios de usd a mxn.

Para esta tarea vamos a usar la tabla "tipos de cambio" y "precio_peliculas_tipo_cambio.

Primero creamos el query que nos permita obtener el costo de la renta de las peliculas convertido de $USD a $MXN

![[Pasted image 20210728103240.png]]

```sql
SELECT peliculas.pelicula_id,
       tipos_cambio.tipo_cambio_id,
       tipos_cambio.cambio_usd * peliculas.precio_renta AS precio_mxn
FROM peliculas,
    tipos_cambio
WHERE tipos_cambio.codigo = 'MXN';
```

Ahora creamos un Trigger usando PGAdmin para actualizar los datos en la tabla **precio_peliculas_tipo_cambio**

![[Pasted image 20210728103302.png]]

![[Pasted image 20210728103309.png]]

```sql
BEGIN
    INSERT INTO precio_peliculas_tipo_cambio(
        pelicula_id,
        tipo_cambio_id,
        precio_tipo_cambio,
        ultima_actualizacion
    )
    SELECT NEW.pelicula_id,
    tipos_cambio.tipo_cambio_id,
    tipos_cambio.cambio_usd * NEW.precio_renta AS precio_tipo_cambio,
    CURRENT_TIMESTAMP
    FROM tipos_cambio
    WHERE tipos_cambio.codigo = 'MXN';
    RETURN NEW;
END
```

El script creado por el sistema

```sql
CREATE FUNCTION public.precio_peliculas_tipo_cambio()
    RETURNS trigger
    LANGUAGE 'plpgsql'
     NOT LEAKPROOF
AS $BODY$
BEGIN
    INSERT INTO precio_peliculas_tipo_cambio(
        pelicula_id,
        tipo_cambio_id,
        precio_tipo_cambio,
        ultima_actualizacion
    )
    SELECT NEW.pelicula_id,
    tipos_cambio.tipo_cambio_id,
    tipos_cambio.cambio_usd * NEW.precio_renta AS precio_tipo_cambio,
    CURRENT_TIMESTAMP
    FROM tipos_cambio
    WHERE tipos_cambio.codigo = 'MXN';
    RETURN NEW;
END
$BODY$;
```

Creamos el Trigger para hacer un insert o un update cada que la tabla peliculas sufra un cambio

![[Pasted image 20210728103340.png]]

```sql
CREATE TRIGGER trigger_update_tipos_cambio
    AFTER INSERT OR UPDATE
    ON public.peliculas
    FOR EACH ROW
    EXECUTE PROCEDURE public.precio_peliculas_tipo_cambio();
```

Revisamos que nuestra tabla objetivo este vacía, o en su defecto hacemos un TRUNCATE para limpiarla.

![[Pasted image 20210728103359.png]]

Ahora vamos a cambiar el precio de renta de un registro de 4.99 a 5.99 usando PGadmin.

![[Pasted image 20210728103407.png]]

![[Pasted image 20210728103411.png]]

Como observas se crea un registro de forma automática en una tabla que nos permite obtener el precio en moneda local y conservar la consistencia de los datos cada que algo cambie.