# Pivot tables y cross-tabulations

con un data set se puede ver como a partir de un dato, se comporta los datos o como se agrupan

## Group by

con el comando groupby 
```python
Chicago_df.groupby(['LIGHTING_CONDITION','REPORT_TYPE','CRASH_HOUR']).agg({'BEAT_OF_OCCURRENCE':'sum'})
```

se puede agrupar los datos dependiendo de una variable por ejemplo agrupar los accidentes de transito por las condiciones de luz que existian en el momento del accidente.

Se pueden agrupar los datos con multiples variables como agrupar por condiciones de luz y tipo de reporte y la hora del accidente para que muestre el total de accidentes ocurridos con esas variables

## Pivot table

con pandas, el comando pivot_table, nos permite agrupar toda la tabla del dataset, dejandonos ver la acumulación de datos y agruparlos en variables que expresemos en un 
indice

```python
pd.pivot_table(Chicago_df,index=['LIGHTING_CONDITION','REPORT_TYPE'])
```

## filtro

Cuando tomamos el dataframe y aplicamos el comando filter, nos muestra solo las columnas que ingresemos filtradas y separadas.

```python
Chicago_df.filter(['LIGHTING_CONDITION','REPORT_TYPE'])
```

## crosstab

El comando de pandas $crosstab$ nos permite hacer una tabulación de la tabla entre varias variables, lo cual nos indica en el ejemplo el número de accidentes dependiendo de las condiciones de luz y la hora específica del accidente

```python
pd.crosstab(Chicago_df['LIGHTING_CONDITION'],Chicago_df['CRASH_HOUR'])
```

Tomar muy en cuenta que se debe ingresar datos que si se pueda contabilizar, no se puede trabajar con dos datos dentro de un mismo índice

https://colab.research.google.com/drive/1JHd3R3kqbP7CeImT_NAP_2ilBQYuSuVp#scrollTo=9Wsj9TEoY739