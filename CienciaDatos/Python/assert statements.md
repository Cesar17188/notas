# Assert Statements (Afirmaciones en Python)

Son expresiones combinando variables con operadores, el flujo seria
* El codigo
* el assert se ingresa y pregunta
* si la condición se cumple el código corre, si la condición no se cumple aparece un error

El código de un assert se ve de la siguiente manera

```python
assert condición, mensaje de error
```

se lee así
afirmo que esta condición es verdadera sino aparece el mensaje de error
 
 ejemplo
 
 ```python
 def palindrome (string):
 	return string == string[::-1]

 print(palindrome(""))
```

respuesta 

True

con assert

```python
def palindrome(string):
	assert len(string) > 0, 'No se puede ingresar una cadena vacia'
	return string == string[::-1]
	
print(palindrome(""))
```

la respuesta

```python
AssertionError: No se puede ingresar una cadena vacia
```


		
