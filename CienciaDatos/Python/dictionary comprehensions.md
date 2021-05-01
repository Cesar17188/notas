# Dictionary comprehensions


Son diccionarios que se puede crear con una forma explicita en el formato por ejemplo

```python 
my_dict = {i: i**3 for i in range(1, 101) if i % 3 != 0}
``` 

donde obtenemos un diccionario de números que tiene como llave el número base y de valor el número elevado al cubo en un rango que va del 1 al 100 siempre y cuando el número no sea divisible para 3

Utiliza esta estructura

{key: value for element in iterable if condition}

element: Representa a cada una de las llaves y valores a poner en el nuevo diccionario

for element in iterable: Ciclo a partir del cual se extraerán elementos de otra lista o cualquier iterable

condition: Condición opcional para filtrar los elementos del ciclo