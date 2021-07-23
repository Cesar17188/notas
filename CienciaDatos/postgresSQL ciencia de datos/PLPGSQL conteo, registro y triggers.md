# PLPGSQL: conteo, registro y triggers

Esta clase continua con las funciones y después las meteremos en un trigger (este procedimiento deberás aprenderlo, taladrarlo en tu cabeza y dominarlo).

Creamos la primer funcion del ejemplo

![[Pasted image 20210715131715.png]]

```sql
-- CREAMOS LA FUNCION
CREATE OR REPLACE FUNCTION count_total_movies()
RETURNS int
LANGUAGE plpgsql
AS $$
BEGIN
 RETURN COUNT (*) FROM peliculas;
END
$$;

-- EJECUTAMOS LA FUNCION
SELECT count_total_movies();
```

A continuación creamos una funcion encaminada a ser un Trigger, recuerda que los disparadores se ejecutan cuando algo sucede. La idea en general de la siguiente funcion es tomar un registro de una tabla y duplicarlo en otra.

Observa que al crear la funcion se agrega esta el el arbol en la parte de triggers, pero el trigger entra en acción o se activa hasta que lo creamos en la segunda sentencia.

![[Pasted image 20210715131739.png]]

```sql
-- CREAMOS LA FUNCION QUE EJECUTARA EL TRIGGER
CREATE OR REPLACE FUNCTION duplicate_records()
RETURNS trigger
LANGUAGE plpgsql
AS $$
BEGIN
    INSERT INTO aaab(bbba, ccca)
    VALUES (NEW.bbb, NEW.ccc);
    RETURN NEW;
END
$$;

-- CREAMOS EL TRIGGER
CREATE TRIGGER aaa_changes
    BEFORE INSERT
    ON aaa
    FOR EACH ROW
    EXECUTE PROCEDURE duplicate_records();

-- INSERTAMOS DATOS
INSERT INTO aaa(bbb,ccc)
VALUES('abcde', 'efghi');
```