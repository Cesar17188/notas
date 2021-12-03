# Introducción y manipulación de datos con Pandas

Biblioteca de código abierto que proporciona estructuras de adtos y herramientas de análisis de datos de alto rendimiento y fáciles de usar.

**Pandas (Panel Data)**

-   Es una librería derivada de numpy pensada para el manejo de datos en forma de panel.
-   Trabaja con series, data frames y panels, generan indices a los arreglos (a manera de panel o tabla de excel), en una (Series), dos (DataFrames) o tres dimensiones (Panels)
-   Al igual que numpy hay que importar primero la librería:

```
import pandas as pd
```

-   Creación de series y dataframes:

```
serie = pd.Series(<datos>)
dataframe = pd.DataFrame(<datos>)
```

El código anterior genera una serie o dataFrame a partir de los datos ingresados, pueden ser listas, tuplas o , en el caso de un DataFrame, arreglos o diccionarios (en el caso de los diccionarios los indices de las columnas toman el valor de las llaves)

-   Algunos comandos útiles
    -   df[<nombre_columna>] → selecciona la columna invocada
    -   pd.read_csv(<nombre_archivo>) → permite importar datos a partir de un csv
    -   type(<objeto>) → permite saber el tipo de objeto
    -   df.shape → Devuelve el tamaño del df
    -   df.colums → Devuelve las columnas del df
    -   df[<nombre_columna>] .describe() → devuelve un análisis estadístico de la columna
    -   df.sort_index() → ordena de acuerdo al índice (axis=0 → filas; axis=1 → columnas)
    -   df.sort_values(by=<campo_a_ordenar>) → ordena de acuerdo a los valores