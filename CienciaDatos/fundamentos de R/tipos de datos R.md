# Tipos de datos

Además de trabajar con el dataset de Orange Economy vamos a necesitar el dataset de **mtcars**.

Dentro de la consola de R Studio, la función _install.packages_ nos va a ayudar a instalar paquetes, como su nombre lo indica, en este caso intentaremos instalar mtcars.

En caso de no estar disponible para tu versión de R, puedes ir al [Github de la profesora](https://github.com/sap0408/mtcars) y descargarlo.

La función **str** nos va a mostrar la estructura que tiene el dataset que le pasemos.  
Dentro de la consola podemos obtener más información sobre nuestro dataset anteponiendo el signo _?_ quedando `?mtcars`

En el dataset mtcars podemos ver que hay datos de tipo int y num, la diferencia es que num son números con decimal mientras que int son enteros.

Podemos ver que las variables _vs_ y _am_ dentro de mtcars aunque están marcadas con int su función es de tipo boolean, para convertir estos datos utilizaremos la función `as.logical`

**Reto**: Explora la estructura del dataset orangeec. Escribe en los comentarios el número de observaciones y variables que encuentres.

17 obs. y 13 variables. Hay que tener cuidado a la hora de importar el Dataset porque viene con la opción Header por defecto en No, y esto hace que los títulos los tome como una observación más, lo cual no es correcto. Hay que poner el Header en Yes para que tome los títulos de las variables correctamente