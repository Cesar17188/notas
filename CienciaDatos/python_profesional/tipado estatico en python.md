# Tipado estático en Python

Para hacer que Python sea de tipado estático es necesario agregar algo de sintaxis adicional a lo aprendido, además, esta característica solo se puede aplicar a partir de la versión 3.6.

```python
# De esta manera se declara una variable, se colocan los dos puntos (:), el tipo de dato y para finalizar se usa el signo igual para asignar el valor a la variable.

<variable> : <tipo_de_dato> = <valor_asignado>

a: int = 5
print(a)

b: str = "Hola"
print(b)

c: bool = True
print(c)
```

Del mismo modo se puede usar esta metodología de tipado en Python a funciones adicionando el signo menos a continuación del signo mayor que para determinar el tipo de dato. Ejemplo:

```python
def <nombre_func> ( <parametro1> : <tipo_de_dato>, <parametro2> : <tipo_de_dato> ) ->  <tipo_de_dato> :
	pass

def suma(a: int, b: int) -> int :
	return a + b

print(suma(1,2))

# 3
```

Existe una librería de fabrica que viene preinstalada con Python que se llama **typing,** que es de gran utilidad para trabajar con tipado con estructuras de datos entre la versión **3.6** y **3.9**, entonces:  
.

```python
from typing import Dict, List

positives: List [int] = [1,2,3,4,5]

users: Dict [str, int] = {
	"argentina": 1.
	"mexico": 34,
	"colombia": 45,
}

countries: List[Dict[str, str]] = [
	{
		"name" : "Argentina",
		"people" : "45000",
	},
	{
		"name" : "México",
		"people" : "9000000",
	},
	{
		"name" : "Colombia",
		"people" : "99999999999",
	}
]
```

```python
from typing import Tuple, Dict, List

CoordinatesType = List[Dict[str, Tuple[int, int]]]

coordinates: CoordinatesType = [
	{
		"coord1": (1,2),
		"coord2": (3,5)
	},
	{
		"coord1": (0,1),
		"coord2": (2,5)
	}
]
```

#### Modulo `mypy`

.  
El modulo mypy se complementa con el modulo typing ya que permitirá mostrar los errores de tipado debil en Python.