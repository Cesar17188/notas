# Mejorando nuestra sucesión de Fibonacci

```py
import time

  

def fibo_gen(max: int):

 n1 = 0

 n2 = 1

 counter = 0

 while True:

 if counter == 0:

 counter += 1

 yield n1

 elif counter == 1:

 counter += 1

 yield n2

 else:

 if counter < max:

 aux = n1 + n2

 n1, n2 = n2, aux

 counter += 1

 yield aux

 else:

 break

  

def call_fibo(func):

 def wrapper(*args, **kwargs):

 print('La seríe Fibonnaci es: ')

 func(*args, **kwargs)

 print('Gracias por usar secuencia Fibonacci, Hasta pronto!!')

 return wrapper

  

@call_fibo

def iter_element(max):

 fibonacci = fibo_gen(max)

 for i, element in enumerate(fibonacci):

 print(f'element {i+1} --> {element}')

 time.sleep(1)

  

if __name__ == '__main__':

 max = int(input('Ingrese la cantidad de número de la seríe Fibonacci que desea: '))

 iter_element(max)
 ```