# PLPGSQL: Stored procedures

PLPGSQL es el lenguaje que Postgres creo para hacer programacion estructurada que tiene el componente fuerte para hacer Triggers y Stored Procedures.

Un **procedure** (procedimiento), es algo muy similar a una funcion pero que no retorna ningun valor esto quiere decir que **ejecutara todos los pasos del procedimiento pero al final no retorna o extrae ningun valor** (a diferencia de las funciones que si retornan valores).

PL/pgSQL es un superset, puedes hacer todo lo SQL pero también Stored Procedures, Functions y Triggers.

Veremos en el código el primer ejemplo de Procedure.

![[Pasted image 20210715125207.png]]

Con este ejercicio puedes observar que cualquier cosa que tengas que realizar una y otra vez lo puedes encapsular en un procedimiento y llamarlo como una funcion cada vez que lo necesites.

La primer parte crea un procedure y lo guarda ebn el arbol de la base de datos.
```sql
-- CREAMOS EL PROCEDURE
CREATE OR REPLACE PROCEDURE test_drop_create_procedure()
LANGUAGE SQL
AS $$
--AQUÍ VA LA CARNITA DE LA FUNCION/PROCEDURE
    DROP TABLE IF EXISTS aaa;
    CREATE TABLE aaa(bbb char(5) CONSTRAINT firstkey PRIMARY KEY);
$$
```

La segunda parte ejecuta ese procedure, cada que lo necesitemos basta con llamarlo con el keyword CALL en cualquier script/consulta de la base de datos, como observamos arriba son solo una serie de instrucciones que no retornan ningun valor.

```sql
-- LLAMAMOS AL PROCEDURE
CALL test_drop_create_procedure();
```

Ahora haremos algo diferente utilizando el lenguaje de PostgreSQL, en este ejercicio crearemos una funcion, esto es propio de postgres y usa los keywords **BEGIN** y **END**

![[Pasted image 20210715125340.png]]

Al igual que el ejercicio anterior la primer parte hace referencia a la funcion que vamos a guardar, la cual retorna un valor vacio (void en ingles) y hace uso del lenguaje plpgsql, la sentencia de la funcion ahora se encuentra entre los keywords BEGIN y END.

```sql
-- CREAMOS LA FUNCION 
CREATE OR REPLACE FUNCTION test_drop_create_function()
RETURNS VOID
LANGUAGE plpgsql
AS $$
BEGIN --INICIA FUNCION
    DROP TABLE IF EXISTS aaa;
    CREATE TABLE aaa(bbb char(5) CONSTRAINT firstkey PRIMARY KEY, ccc char(5));
    DROP TABLE IF EXISTS aaab;
    CREATE TABLE aaab (bbba char(5) CONSTRAINT secondkey PRIMARY KEY, ccca char(5));

END --TERMINA FUNCION
$$
```

Observamos como al ejecutar la funcion se ha guardado en el arbol al igual que lo hizo el procedure, ahora llamamos a la funcion con **SELECT**.

```sql
-- LLAMAMOS A LA FUNCION
SELECT test_drop_create_function();
```