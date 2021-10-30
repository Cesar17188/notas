# Utilizar proyecto como un módulo de Python

### Top Countries function

```
def top_countries(df, countries, n):
    top_countries_df = (
    df
    .select_columns(["country_region", "value"])
    .groupby(["country_region"])
    .aggregate("sum")
    .sort_values("value", ascending=False)
    .reset_index()
    .head(20)
    .transform_column(
        column_name="country_region",
        function=lambda x: "red" if x in countries else "lightblue",
        dest_column_name="color"
        )
    )
    return top_countries_df.head(n)
```

Permite obtener la tabla de paises con su valor y color de acuerdo con el dataframe ingresado _**countries**_ y el número de elementos _**n**_ que se quiere visualizar:  

![Selection_999(192).png](https://static.platzi.com/media/user_upload/Selection_999%28192%29-a803a31a-c1be-41fb-8061-0799f1a7d5a1.jpg)