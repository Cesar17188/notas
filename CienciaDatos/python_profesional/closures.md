# Closures

## Nested functions (funciones anidadas)
-   Son funciones dentro de otra función.

```python
def main():
		a = 1

		def nested():
				print(a)

		nested()
main()

// 1
```

```python
def main():
		a = 1

		def nested():
				print(a)

		return nested

my_func =  main()
my_func()

// 1
```

## Closures

Es una forma de acceder a variables de otros scopes a través de una nested function. Se retorna la nested function y esta recuerda el valor que imprime, aunque a la hora de ejecutarla no este dentro de su alcance.

Reglas practicas para identificar un **closure**:

1.  Debemos tener una _nested function_.
2.  La _nested function_ debe referenciar un valor de un _scope_ superior.
3.  La función que envuelve la _nested_ debe retornarla también.

Con este tipo de estructuras podemos crear funciones personalizadas. Se les suele usar o encontrar cuando tenemos, por ejemplo, clases cortas con un solo método (para hacerla mas elegante) o cuando trabajamos con decoradores.

Ejemplo:

```python
def main():
	
	a = 1

	def nested():
		print(a)
	return nested

myfunc = main()
myfunc() #1
```

En el ejemplo anterior incluso se puede borrar la función **main** ( `del(main)` ) y la variable **myfunc** aún recordará la variable a que se encuentra en la función **main**, esto porque es una variable de un _scope_ superior.  
En el siguiente ejemplo podemos hacer una función _personalizada_:

```python
def make_multiplier(x):

    def multiplier(n):
        return x * n
    return multiplier

times10 = make_multiplier(10)
times4 = make_multiplier(4)

print(times10(3))         #30
print(times4(5))          #20
print(times10(times4(2))) #80
```