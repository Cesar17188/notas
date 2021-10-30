# Las tres transformaciones

una matriz es una transformación lineal. Esta transformación para ser aplicada se usa el producto punto. Si analizan lo que escribió el profesor en #circulo unitario transformado, es el producto punto. Hice la misma función pero aplicando el producto punto directamente, si es que le sirve a alguien.  
Un abrazo

```
def graficarMatriz(matriz, vectorCol=['red', 'blue']):
    
    #círculo unitario
    x = np.linspace(-1, 1, 100000)
    y = np.sqrt(1 - (x**2))
    
    #Transformamos x e y en una matriz de vectores x, y
    vector_x_y = np.array([x, y])
    
    # círculo unitario transformado
    prod_punto = matriz.dot(vector_x_y)
    
    #vectores
    u1 = [matriz[0, 0], matriz[1, 0]]
    v1 = [matriz[0, 1], matriz[1, 1]]
    
    graficarVectores([u1, v1], cols=[vectorCol[0], vectorCol[1]])
    
    plt.plot(prod_punto[0], prod_punto[1], 'orange', alpha = 0.7)
    plt.plot(-prod_punto[0], -prod_punto[1], 'green', alpha = 0.7)
```

matematicamente un circulo es x^2+y^2=r  
donde r es el radio, como es el circulo unitario r=1, x^2+y^2=1.  
al despejar y queda la expresion: sqrt(1-x^2)  
x va de -1 a 1 ya qiue es el dominio de la funcion, sabemos que la raiz cuadrada sqrt(x) esta definida en lo reales para los valores de x>=0 si fuera un negativo da un numero complejo.  
Entonces tenemos que hacer 1-x^2>=0  
x^2>=1  
-1<x< 1  
al modificar x e y ya sea diviendolos o restando a sus valor el circulo se puede transformar en parabola, elipse, hiperbola u otra


Aqui un interesante articulo para profundizar sobre el circulo unitario  
[https://www.lifeder.com/circulo-unitario/](https://www.lifeder.com/circulo-unitario/)

Adjunto el código para graficar matriz

```
def graficarMatriz(matriz, vectorCol=['red','blue']):
  #circulo unitario
  x=np.linspace(-1,1,1000000)
  y=np.sqrt(1-x**2)

  #circulo unitario transformado
  x1 = matriz[0,0]*x + matriz[0,1]*y
  y1 = matriz[1,0]*x + matriz[1,1]*y
  x1_neg = matriz[0,0]*x - matriz[0,1]*y
  y1_neg = matriz[1,0]*x - matriz[1,1]*y

  #vectores
  u1 = [matriz[0,0], matriz[1,0]]
  v1 = [matriz[0,1], matriz[1,1]]

  graficarVectores([u1,v1], cols=[vectorCol[0],vectorCol[0]])

  plt.plot(x1,y1, 'green', alpha =0.7)
  plt.plot(x1_neg,y1_neg, 'green', alpha =0.7)
```