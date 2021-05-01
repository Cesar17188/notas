# Manejo de exceptiones

existen 4 palabras clave para el manejo de excepciones

* raise
* try
* except
* finally

## try, except

un ejemplo de como python nos muestra en pantalla un error de excepcion en un programa el del palindromo

```python
def palindrome(string):
	return string == string[::-1]

print (palindrome(1))
```

El error se muestra así

```python
Traceback (most recent call last):
	File "main.py", line 4, in <module>
		print(palindrome(1))
	File "main.py", line 2, in palindrome
		return string == string[::-1]
TypeError: 'int' object is not subscriptable
```

Ahora para poder evitar este tipo de errores podemos utilizar las palabras clave try y except en el código de la siguiente manera

```python
def palindrome(string):
	return string == string[::-1]

try:
	print(palindrome(1))
except TypeError:
	print("Solo se pueden ingresar strings")
```

El resultado sería 

```python
Solo se pueden ingresar strings
```

## raise

Es posible en ocaciones que cometamos errores y [[Python]] no lo reconesca como un error, en ese caso utilizamos la palabra clave raise

```python
def palindrome(string):
	return string == string[::-1]

try:
	print(palindrome(""))
except TypeError:
	print("Solo se pueden ingresar strings")
```

El resultado sería

```python
True
```

Si nosotros ingresamos una cadena vacia en la función palindrome nos devuelve True pero es un error ya que la cadena vacia no deberia reconocerse como una opción de verificación del palindromo

por lo tanto ingresamos

```python
def palindrome(string):
	try:
		if leng(string) == 0:
			raise ValueError("No se puede ingresar una cadena vacía")
		return string == string[::-1]
	except ValueError as ve:
		print(ve)
		return False

try:
	print(palindrome(""))
except TypeError:
	print("Solo se pueden ingresar strings")
```

el resultado sería

```python
No se puede ingresar una cadena vacía 
False
```

## finally

Finalmente se utiliza la palabra clave finally para poder ejecutar acciones puntuales dentro de la función try, except en python como por ejemplo: 

* cerrar un archivo
* cerrar una conexión a base de datos
* generar acciones

```python
try:
	f = open("archivo.txt")
	# hacer cualquier cosa con nuestro archivo
finally:
	f.close()
```