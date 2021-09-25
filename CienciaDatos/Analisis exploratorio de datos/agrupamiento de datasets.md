# Agrupamiento de datasets

El agrupamiento de datasets es de gran utilidad a la hora de obtener más información sobre ciertas caracteristicas de la data como: la suma de datos de una columna, multiplicación de de datos entre columnas o incluso operaciones estadísticas.

```python
#Llamamos el set de datos público

import pandas as pd

import altair as alt

Chicago_data = 'https://raw.githubusercontent.com/terranigmark/curso-analisis-exploratorio-datos-platzi/main/Traffic_Crashes1.csv'

Chicago_df=pd.read_csv(Chicago_data)

Chicago_df['CRASH_DATE'] = Chicago_df['CRASH_DATE'].apply(lambda x: pd.to_datetime(x,errors='coerce', utc=True))

```

```python
Chicago_df.head()
```

```python
report_1 = report_1.reset_index()

report_1
```

```python
alt.Chart(report_1).mark_bar().encode(

 x='LIGHTING_CONDITION',

 y='NUM_UNITS',

 color='REPORT_TYPE'

).properties(width=220)
```
![[Pasted image 20210910114410.png]]
```python
report_1 = Chicago_df.groupby(['LIGHTING_CONDITION', 'REPORT_TYPE', 'CRASH_HOUR']).agg({'NUM_UNITS':['sum','min','max']})
```

https://colab.research.google.com/drive/1kyn9ZvF539uPtmDzwD3vmB1Lc51r7qOV#scrollTo=BPvQUr9Si9HK