# Podemos y debemos pensar a las matrices como transformaciones lineales

## Introducción:

---

A las matrices las podemos pensar como transformaciones lineales que cuando las aplicamos a un espacio o a un vector generan una transformación. La transformación en el caso de un vector podría ser cuando se estira, se achica o incluso cuando generamos una rotación.

**Matrices**

-   Podemos ver a las matrices como transformaciones lineales del espacio sobre el que se aplican, es decir deforman los puntos del espacio sobre el que se aplican, trasladándolos, alargándolos o rotándolos.

**Nota:**  
.flatten() → convierte el vector o matriz en un vector fila

**Explicación para los que se inclinan más por el fundamento matemático:**  
Sea AxB=C  
El producto interno entre Anxm y Boxp dónde n,o son las filas y m,p son las columnas, para que AxB pueda existir cómo producto, se debe cumplir que n=o, y las dimensiones de la matriz resultante © será siempre nxp, entonces, si vas probando a lápiz y papel con dimensiones que a ti se te ocurran (pares dimensionales que cumplan con la condicion de producto interno) te vas a dar cuenta que todas las operaciones tranforman, o bien a la primera matriz o a la segunda, la única excepción a esta regla, es que ambas matrices sean cuadradas, lo cuál nos deja la siguiente conclusión  
**Las matrices son intrínsecamente transformaciones lineales en dónde el espacio es transformado con ciertas excepciones**

Para los que están trabajando con Google Colab, el método que uso para trabajar con archivos en carpetas internas es el siguiente:

Importar drive en el espacio de trabajo y vincular con su cuenta de google:

```
from google.colab import drive
drive.mount('/content/drive')
```

Aquí para vincular les pedirá un código de acceso que obtendrán del link que se les mostrará al momento de ejecutar el código. Con esto ya están listos para importar el archivo:

```
%run 'ubicacion archivo drive'
```

En mi caso para la función graficarVectores, lo encuentro así:

```
%run '/content/drive/My Drive/Mau/cursos/Álgebra Lineal Aplicada para Machine Learning/funciones_auxiliares/graficarVectores.ipynb'
```

Y listo, ya pueden trabajar con su función.