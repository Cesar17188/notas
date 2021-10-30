# ¿Cómo interpretar los valores singulares?

en las clases pasadas se habia dicho que D escala (amplia o reduce) la transformación. En este sentido queremos ver como cambia D a U. ¿Y como vemos este efecto? Pues con un simple producto interno, que es lo que se hizo en clase. (En la imagen se demuestra que esos vectores u1 y v1 no son mas que las filas del producto interno de D·U)

![](

![ud.png](https://static.platzi.com/media/user_upload/ud-53e4932c-8888-4191-81a1-f00e7f98dace.jpg)


-   D es una un vector de dos numeros, (aunque realmente es una matriz diagonal) para los calculos python lo simplifica en un vector de dos numeros eje: [a,b]
-   U es una matriz de 2x2
-   cuando multiplico matriz por vector entonces se genera esa multiplicacion u1 = [D[0]*U[0,0], D[0]*U[0,1]
-   U1 es la aplicacion de la multiplicacion UxD a la primera fila de la matriz

Otra manera:

```
D = np.diag(D)
z = np.zeros((2,1))
D = np.concatenate((D,z), axis=1)
```

```
U_D = U.dot(D).T
```

```
u1 = U_D[0]
v1 = U_D[1]
```