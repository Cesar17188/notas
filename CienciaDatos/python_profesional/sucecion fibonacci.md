# La sucesión de Fibonacci

https://es.wikipedia.org/wiki/Sucesi%C3%B3n_de_Fibonacci

```python
import time

  

# clase iteradora

class FiboIter():

 # asignación de un número máximo

 def __init__(self, max=None) -> None:

 self.max = max 

  

 # inicio de las variables a iterar

 def __iter__(self):

 self.n1 = 0

 self.n2 = 1

 self.counter = 0

 return self

  

 # cálculo del siguiente elemento y su ingreso en la seríe

 def next_add(self):

 self.aux = self.n1 + self.n2

 self.n1, self.n2 = self.n2, self.aux

 self.counter += 1

 return self.aux

  

 # paso siguiente en el iterador

 def __next__(self):

 if self.counter == 0:

 self.counter += 1

 return self.n1

 elif self.counter == 1:

 self.counter += 1

 return self.n2

 else:

 if self.max:

 if self.counter <= self.max:

 self.fibonacci = self.next_add()

 else:

 raise StopIteration

 else:

 self.fibonacci = self.next_add()

 return self.fibonacci

  
  

# Decorador de la seríe

def cal_fibonacci(func):

 def wrapper(*args, **kwargs):

 print('La secuencia es: ')

 func(*args, **kwargs)

 print('Gracias por usar Secuencia Fibonacci')

 return wrapper

  

# llamada a la iteración fibonnacci

@cal_fibonacci

def iter_elem_fibonacci(max):

 fibonacci = FiboIter(max)

 for i, element in enumerate(fibonacci):

 print(f'{i} --> {element}')

 time.sleep(1)

  
  

if __name__ == '__main__':

 max = int(input('Ingrese la cantidad de número de la seríe Fibonacci que desea: '))

 iter_elem_fibonacci(max)

  

# 0 1 1 2
```