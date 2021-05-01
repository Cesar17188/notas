# Listas y Diccionarios anidados

# Listas
Una lista es una estructura de datos y un tipo de dato en python con características especiales. Lo especial de las listas en Python es que nos permiten almacenar cualquier tipo de valor como enteros, cadenas y hasta otras funciones; por ejemplo:
```python
lista = [1, 2.5, 'DevCode', [5,6] ,4]
```

# Diccionarios

Un Diccionario es una estructura de datos y un tipo de dato en Python con características especiales que nos permite almacenar cualquier tipo de valor como enteros, cadenas, listas e incluso otras funciones. Estos diccionarios nos permiten además identificar cada elemento por una clave (Key).
1. Para definir un diccionario, se encierra el listado de valores entre llaves. Las parejas de clave y valor se separan con comas, y la clave y el valor se separan con dos puntos.
```python
diccionario = {'nombre' : 'Carlos', 'edad' : 22, 'cursos': ['Python','Django','JavaScript'] }
```
2. Podemos acceder al elemento de un Diccionario mediante la clave de este elemento, como veremos a continuación:
```python
print diccionario['nombre'] #Carlos
print diccionario['edad']#22
print diccionario['cursos'] #['Python','Django','JavaScript']
```
3. También es posible insertar una lista dentro de un diccionario. Para acceder a cada uno de los cursos usamos los índices:
```python
print diccionario['cursos'][0]#Python
print diccionario['cursos'][1]#Django
print diccionario['cursos'][2]#JavaScript
```
4. Para recorrer todo el Diccionario, podemos hacer uso de la estructura for:  
```python
for key in diccionario:
  print key, ":", diccionario[key]
```

# Lista de diccionarios
Es posible crear una lista que contenga diccionarios como por ejemplo:
```python
super_list = [
 {'first_name': 'Cesar', 'last_name': 'Armendariz'},
 {'first_name': 'Miguel', 'last_name': 'Torres'},
 {'first_name': 'Pepe', 'last_name': 'Rodelo'},
 {'first_name': 'Susana', 'last_name': 'Martinez'},
 {'first_name': 'Jose', 'last_name': 'García'}
]
```                                                                

# Diccionario de listas
Cabe ver que las caracteristicas de diccionarios y listas se manejan de la misma manera
De igual manera es posible crear diccionarios de listas por ejemplo:
```python
super_dict = {
 'natural_nums': [1, 2, 3, 4, 5],
 'integer_nums': [-1, -2, 0, 1, 2],
 'floating_nums': [1.1, 4.5, 6.43]
 }```        	 
  