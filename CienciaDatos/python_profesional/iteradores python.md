# Iteradores

Antes de entender qué son los iteradores, primero debemos entender a los iterables.

Son todos aquellos objetos que podemos recorrer en un ciclo. Son aquellas estructuras de datos divisibles en elementos únicos que yo puedo recorrer en un ciclo.

ejemplos:
- listas
- strings

Pero en Python las cosas no son así. Los iterables se convierten en iteradores.

Ejemplo:

```python
# Creando un iterador

my_list = [1,2,3,4,5]
my_iter = iter(my_list)

# Iterando un iterador

print(next(my_iter))

# Cuando no quedan datos, la excepción StopIteration es elevada
```

---

```python
# Creando un iterador

my_list = [1,2,3,4,5]
my_iter = iter(my_list)

# Iterando un iterador

while True: #ciclo infinito
  try:
    element = next(my_iter)
    print(element)
  except StopIteration:
    break
```

**Momento impactante:** El ciclo “for” dentro de Python, no existe. Es un while con StopIteration. 🤯🤯🤯

```python
my_list = [1,2,3,4,5]

for element in my_list:
  print(element)
```

---

`evenNumbers.py`:

```python
class EvenNumbers:
  """Clase que implementa un iterador de todos los números pares,
  o los números pares hasta un máximo
  """

  #* Constructor de la clase
  def __init__(self, max = None): #self hace referencia al objeto futuro que voy a crear con esta clase
    self.max = max


  # Método para tener elementos o atributos que voy a necesitar para que el iterador funcione
  def __iter__(self):
    self.num = 0 #Primer número par
    #* Convertir un iterable en un iterador
    return self

  # Método para tener la función "next" de Python
  def __next__(self):
    if not self.max or self.num <= self.max:
      result = self.num
      self.num += 2
      return result
    else:
      raise StopIteration
```

Ventajas de usar iteradores:

1.  Nos ahorra recursos.
2.  Ocupan poca memoria.


Para un ejemplo de iteradores y su uso [[sucecion fibonacci]]