# Regresión logística

## bases
[[regresión lineal]]: Predice una salida numérica
![[Pasted image 20211109170751.png]]

Regresión logística: Predice una clase/etiqueta
![[Pasted image 20211109170809.png]]

Queremos saber si un estudiante pasará un examen conciendo cuántas horas estudió.

La salida es la probabilidad para cada entrada(estudiante) Para etiquetar decimos que cualquiera "arriba" de 0.5 pasará; y por debajo, no lo hará.

>p(Pass) = exp(W$_0$ + W$_1$X$_1$) / 1 + exp(W$_0$ + W$_1$X$_1$)

## función de coste y regla de actualización
Sumatoria(sum) sobre todos los puntos de datos (todos los N estudiantes)
Y$_i$ log(P$_p$$_a$$_s$$_s$) = si el estudiante ha **pasado** el examen, este término no es 0.
( 1 - Y$_i$) log(1 - P$_p$$_a$$_s$$_s$) = Si el estudiante **no ha pasado** es "no pasado". Este término no es 0.

> J(W, W$_0$) = -1/N sum{i=1 - N} Y$_i$ log(P$_p$$_a$$_s$$_s$) + ( 1 - Y$_i$) log(1 - P$_p$$_a$$_s$$_s$)

Encuentra los valores W y W$_0$ que mejor preciden la probabilidad 

> Update Rule = min J(W$_0$, W$_1$)


![[Pasted image 20211109170449.png]]

## Confusion Matrix

![[Pasted image 20211109170507.png]]

Accuracy = # of correctly labeled / # of data points

## Repaso: Ingredientes de la regresión logística

Proceso de desición: Probabilidad de que un estudiante pase (Y = 1 )
>p(Pass) = exp(W$_0$ + W$_1$X$_1$) / 1 + exp(W$_0$ + W$_1$X$_1$)

Función de error/coste: el promedio de qué tan bien se predice que un estudiante pasa.
> J(W, W$_0$) = -1/N sum{i=1 - N} Y$_i$ log(P$_p$$_a$$_s$$_s$) + ( 1 - Y$_i$) log(1 - P$_p$$_a$$_s$$_s$)

Regla de actualización: Encuentra valores W y W$_0$ que mejor predicen esta probabilidad
> min J(W$_0$, W$_1$)