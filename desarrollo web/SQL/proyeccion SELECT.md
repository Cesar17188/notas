# ¿Qué es una proyección (SELECT)

**Proyección** significa elegir _QUE_ columnas (o expresiones) la consulta debe retornar.  
**Selección** significa _CUALES SON_ las columnas retornadas.

```sql
Supongamos la siguiente consulta:  

select Columna1, Columna2, Columna3 from table_1 where n=3;
```

La **proyección** sería: _Columna1, Columna2 y Columna3_ y la parte de **Selección** es **n**\*=3,\* debido a esto es que denominamos a la clausula **SELECT** como la **proyección** y los filtros aplicados en la clausula **WHERE** como **Selección**.

La Consulta más Básica sería

```sql
SELECT * FROM Tabla1;
```

El astrisco (\*) es un comodín que indica que queremos traer una proyección completa (Todos los campos o columnas existentes en la tabla)

## Alias

Un alias (.**.AS…**), es otra forma de llamar a una tabla o a una columna, y se utiliza para simplificar las sentencias [[sql]] cuando los nombres de tablas o columnas son largos o complicados.

**SELECT** Columna1 **AS** Alias1 **FROM** Tabla1; (Para referirnos a la _Columna1_, podremos denominarla como _Alias1_)

…  
.

## **Funciones de agregación**

Las funciones de agregación en SQL nos permiten efectuar operaciones sobre un conjunto de resultados, pero devolviendo un único valor agregado para todos ellos.  
Es decir, nos permiten obtener medias, máximos, etc… sobre un conjunto de valores.

Las funciones de agregación básicas que soportan todos los gestores de datos son las siguientes:

-   **COUNT**: devuelve el número total de filas seleccionadas por la consulta, como particularidad se puede usar _COUNT(_)\* donde contará todos los registros de la tabla incluyendo nulos.
-   **MIN**: devuelve el valor mínimo del campo que especifiquemos.
-   **MAX**: devuelve el valor máximo del campo que especifiquemos.
-   **SUM**: suma los valores del campo que especifiquemos. Sólo se puede utilizar en columnas numéricas.
-   **AVG**: devuelve el valor promedio del campo que especifiquemos. Sólo se puede utilizar en columnas numéricas.  
    .

## Función IF()

Función que **evalúa una sola expresión** y retorna lo que se le especifica en el caso que sea Verdadera o Falsa

```sql
IF (expresion, resultado_true, resultado_else)
```

## Función CASE()

Sirve para evaluar **una lista de condiciones** y retornar uno o múltiples posibles resultados.

Comienza con la sentencia **CASE**, luego evalua expresiones comenzando con **WHEN** y en caso que sea verdadera, devolverá el resultado especificado para esa condición luego del **THEN**…  
.  
La sentencia **ELSE** es _opcional_ y devolverá este valor en caso que todas las condiciones **WHEN** anteriores sean Falsas.

Si todas las condiciones son falsas, y no existe la clausula ELSE, se devolverá _NULL_.

```sql
CASE 
   WHEN eval_1 THEN resultado_1
   WHEN eval_2 THEN resultado_2
      ...
   WHEN value_n THEN resultado_n
   ELSE resultado
END AS ValorResultado;
```