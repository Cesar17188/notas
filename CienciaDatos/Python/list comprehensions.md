# List Comprenhensions

Son listas que se puede crear con una forma explicita en el formato por ejemplo

``` python
squares = [i**2 for i in range(1, 101) if i % 3 != 0\]
``` 

donde obtenemos una lista de números elevados al cuadrado en un rango que va del 1 al 100 siempre y cuando el número no sea divisible para 3

Utiliza esta estructura

[element for element in iterable if condition]

element: Representa a cada uno de los elementos a poner en la nueva lista

for element in iterable: Ciclo a partir del cual se extraerán elementos de otra lista o cualquier iterable

condition: Condición opcional para filtrar los elementos del ciclo