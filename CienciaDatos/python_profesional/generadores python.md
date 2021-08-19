# Generadores

Sugar syntax de los iteradores. Los generadores son funciones que guardan un estado. Es un iterador escrito de forma más simple.

```python
def my_gen():

  """un ejemplo de generadores"""

  print('Hello world!')
  n = 0
  yield n # es exactamente lo mismo que return pero detiene la función, cuando se vuelva a llamar a la función, seguirá desde donde se quedó

  print('Hello heaven!')
  n = 1
  yield n

  print('Hello hell!')
  n = 2
  yield n


a = my_gen()
print(next(a)) # Hello world!
print(next(a)) # Hello heaven!
print(next(a)) # Hello hell!
print(next(a)) StopIteration
```

Ahora veremos un **generator expression** (es como list comprehension pero mucho mejor, porque podemos manejar mucha cantidad  
de información sin tener problemas de rendimiento):

```python
#Generator expression

my_list = [0,1,4,7,9,10]

my_second_list = [x*2 for x in my_list] #List comprehension
my_second_gen = ()x*2 for x in my_list]) #Generator expression
```