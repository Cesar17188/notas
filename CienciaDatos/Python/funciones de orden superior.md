# Funciones de orden superior (High order functions)

Es una función que recibe como parámetro otra función por ejemplo

```python
def saludo(func):
	func()

def hola():
	print('Hola!!')
	
def adios():
	print('Adios!!')
	
saludo(hola)
saludo (adios)
```

resultado
Hola!!
Adios!!

Existen 3 funciones de orden superior muy utilizadas filter, map y reduce

## Filter

si tenemos una lista de tipo numérico [1, 4, 5, 6, 9, 13, 19, 21] y queremos obtener una lista de solos los números impares [1, 5, 9, 13, 19, 21]

para obtenerla podemos usar list comprehensions

```python
my_list = [1, 4, 5, 6, 9, 13, 19, 21]

odd = [i for i in my_list if i % 2 != 0]

print(odd)
```

resultado 

[1, 5, 9, 13, 19, 21]

usando filter

```python
my_list = [1, 4, 5, 6, 9, 13, 19, 21]

odd = list(filter(lambda x: x % 2 != 0, my_list))

print(odd)
```

resultado 

[1, 5, 9, 13, 19, 21]

## map
si tenemos una lista de tipo numérico [1, 2, 3, 4, 5] y queremos obtener una lista con con los números elevados al cuadrado.

para obtenerla podemos usar list comprehensions

```python
my_list = [1, 2, 3, 4, 5]

squares = [i**2 for i in my_list]

print(squares)
```

resultado
[1, 4, 9, 16, 25]

usando map

```python
my_list = [1, 2, 3, 4, 5]

odd = list(map(lambda x: x**2, my_list))

print(odd)
```

resultado
[1, 4, 9, 16, 25]

## reduce
si tenemos una lista de tipo numérico [2, 2, 2, 2, 2] y queremos obtener la multiplicación de todos los elementos en uno


para obtener el resultado se puede usar la función for

```python
my_list = [2, 2, 2, 2, 2]

all_multiplied = 1

for i in my_list:
	all_multiplied = all_multiplied * i

print(all_multiplied)
```

resultado
32

usando reduce

```python
from functools import reduce

my_list = [2, 2, 2, 2, 2]

all_multiplied = reduce(lamda a, b: a * b, my_list)

print(all_multiplied)
```

resultado
32