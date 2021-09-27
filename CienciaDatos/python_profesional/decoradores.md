# Decoradores

Función que recibe como parametro otra función, le añade nuevas funcionalidades y retorna una función diferente.

Una función que le añade super poderes a otra función.

Ejemplo:

```python
def decorador(func):
	def envoltura():
		print("Esto se añade a mi función original")
		func()
	return envoltura

def saludo():
	print("Hola")

saludo() # output: Hola

saludo = decorador(saludo)
saludo = 
# output: 
# Esto se añade a mi función original
# Hola
```

De forma más estetica:

```python
def decorador(func):
	def envoltura():
		print("Esto se añade a mi función original")
		func()
	return envoltura

@decorador
def saludo()
	print("Hola")

saludo()
# output: 
# Esto se añade a mi función original
# Hola
```

Para entender un poco este tema me remití al curso de Python del canal Píldoras informáticas en YouTube. Clic [aquí](https://www.youtube.com/watch?v=DQXm6bIZgvk&t=2s) para ver el vídeo.  
.  
La sintaxis sería la siguiente:

```
def <funcion_decorador> (<funcion>):

    def <funcion_interna> ():

        <código de la funcion_interna>

    return <funcion_interna>
```

No obstante, dejó el código de ejemplo que usó para explicar este tema por si a alguien le interesa:

```
def funcion_decoradora(funcion_parametro):

    def funcion_interior():

        #Acciones adicionales que decoran

        print("Vamos a realizar un cálculo: ")

        funcion_parametro()

        #Acciones adicionales que decoran

        print("Hemos terminado el cálculo")

    return funcion_interior


# Para llamar la función decoradora se usa el carácter "@" y a continuación el nombre de esta.
# Python entiende que la función adyacente hacia abajo es la función a decorar y la toma como parametro.

@funcion_decoradora
def suma():
    print(15+20)

suma()
```

El resultado en consola sería el siguiente:

```
>>> Vamos a realizar un cálculo: 
>>> 35
>>> Hemos terminado el cálculo
```