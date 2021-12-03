# Framework de ciencia de datos: herramientas para machine learning

 ## Terminología para ciencia de datos
 - Data/Datos: unidades de información o "hechos" de observaciones
 - Features: tipos de información acerca de tus observaciones
 - Filas: Observaciones individuales o muestras
 - Columnas: features que describen tus observaciones
 - Outlier: punto(s) de datos o data point(s) que se comporta de forma extraña
 - Pre-processing: preparar datos para su uso en un modelo de machine learning
 - ETL pipeline: framework de data science para entrae, transformar y cargar.

## Tipos de datos
- Numéricos: Su feature es un número de tipo entero o flotante.
- Categórica: Sus features representan una clase o tipo; usualmente se representan como un mapeo de números o un "one-hot" vector.
- Image: Su feature representa una imagen
- Texto: Su feature es en la forma de texto, sea corto(como Twitter) o largo (como en noticias)
- Nan: Su feature es desconocido o perdido

## Trabajando con Pandas para cargar y entender tus datos 
Pandas es una libreria utilizada principalmente por [[Python]] para poder leer y tratar datasets.
 COMANDOS:
 1. leer un archivo csv con el siguiente comando
 ```py
# leer un archivo CSV
data = pd.read_csv("diabtes.csv")
 ```
2. Mostrar las primeras 5 filas de los datos
 ```py
# Muestra las primeras 5 filas
df.head() 
 ```
 3. Mirar los tipos de datos que trae el dataset
 ```py
 # Muestra el tipo de representación de los datos (float, int, object)
 data.dtypes
 ```
 
## Visualizando tus datos
### Visualización de datos - histogramas
- Te dice qué tan "frecuentes" son ciertos valores en tus datos
- Require de ti para "agrupar" los datos

Con el número de monedas en lso bolsillos de un grupo de personas. Obtengo los siguientes datos, x:
$x = [0, 1, 1, 2, 2, 3, 3, 4, 5, 6, 10, 10]$

Creamos algunos contenedores o grupos. Son:

N = 1 Tienes 0 monedas $[0, 1)$
N = 2 Tiene 1 monedas $[1, 2)$
N = 3 Tiene 2 monedas $[2, 3)$
N = 4 Tiene 3 monedas $[3, 4)$
N = 5 Tiene 4 monedas $[4, 11]$

### Visualización de datos - Gráficas de dispersión
-  Muestra la relación entre 2 features graficándolos como pares ordenados.
-  En cada eje, un feature
-  Te puede ayudar a detectar anomalías.


## Resumen
- Pandas ayuda a cargar y analizar datos
- Histogramas ayudan a ver la distribución de un feature
- Gráficas de dispersión permiten ver la relación entre dos features.


## The data science process

![](https://www.beginnerspython.com/media/uploads/2020/08/17/datascience_wheel.png)
### About feature engineering

Feature engineering is extracting relevant information from data regarding to the field it belongs.

I recommend you reading this book: [https://www.repath.in/gallery/feature_engineering_for_machine_learning.pdf](https://www.repath.in/gallery/feature_engineering_for_machine_learning.pdf)