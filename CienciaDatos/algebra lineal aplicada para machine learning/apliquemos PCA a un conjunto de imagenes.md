# Apliquemos PCA a un conjunto de imágenes

-   Únicamente con 44 componentes podemos recuperar el 80% de la información.

Resumen de pasos fundamentales en la aplicación de PCA a un conjunto de imágenes:

1.  Definir el porcentaje de información a obtener y aplicar el método.

```
caras_pca = PCA(n_components = 0.5)  # 50% de información
caras_pca.fit(caras) # ejecutar PCA
```

1.  Mostrar el número de elementos necesarios

```
print(caras_pca.n_components_)
```

1.  Mostrar el resultado del procesamiento y evaluar

```
componentes = caras_pca.transform(caras)
proyeccion = caras_pca.inverse_transform(componentes)

fig, axes = plt.subplots(5, 10, figsize=(15, 8),
                       subplot_kw = {'xticks' : [], 'yticks':[]},
                        gridspec_kw = dict(hspace = 0.01, wspace = 0.01))

for i, ax in enumerate(axes.flat):
    ax.imshow(proyeccion[i].reshape(112,92), cmap = "gray")

```

PCA es un algoritmo para reducir las dimensiones. Basicamente lo que vimos en los modulos anteriores (autovectores, autovalores y despomposicion de la matriz por valores singulares SVD) es lo que usa el algoritmo PCA . Si recuerdas con el ejercicio de la “Cebra” usabamos los vectores y escalaes obtenidos de SVD para dibujarl la imagen sin necesidad de usar todos los valores de la matriz. Quiere decir que con un numero reducido de columnas en la matriz puedes obtener la mayor candiad de informacion. **SVD regresa los valores ordenados por la magnitud de su varianza** mayor varianza = mayor informacion.

Tambien recuerda que lo que hacen los algoritmos es reducir las dimensiones o el numero de componentes necesaria. En uno de los ejercicios se redujeron los datos de dos dimensiones X,Y a una sola “X” , es decir, todos los valores son proyectados sobre el eje X y se puede ver aun asi su dispersion.