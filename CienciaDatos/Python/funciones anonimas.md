# Funciones anónimas

## Funciones
Es una manera de reutilizar código que utilizaremos en diferentes secciones del código, es una manera de programar una vez y utilizar ese código multiples veces en diferentes secciones del código.

```python
def Nombre(datos):
	pass
``` 

## Funciones anonimas (lambda funtion)

Son funciones que no tienen un nombre que se describe desde la sigueinte manera, solo se puede tener una linea de código y se necesita una varaible que tomara el nombre de la función

 ```python
 lambda argumentos: expresión
 ```
 
 Un ejemplo es una funcion lambda que muestre un palindromo
 
 ```python
 palindrome = lambda string: string == string[::-1]
 
 print(palindrome('ana'))
 
 ```
 
 el resultado impreso es TRUE

en código con una función normal sería

```python

def palindrome(string):
	return string == string[::-1]
	
print(palindrome('ana'))
	
```

Esto se puede aplicar con las [[funciones de orden superior]]