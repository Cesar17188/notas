# Operaciones con sets

#### Unión

Resultado de juntar todos los elementos que tienen ambos, combinar ambos sets

```python
set_1 = {1, 2, 3}
set_2 = {3, 4, 5}
set_3 = set_1 | set_2 #  -> {1, 2, 3, 4, 5}

# O de forma mas explicita
set_1.union(set_2) #  -> {1, 2, 3, 4, 5}
```

#### Intersección

Los que se repiten en ambos sets

```python
set_1 = {1, 2, 3}
set_2 = {3, 4, 5}
set_3 = set_1 & set_2 #  -> {3}

# O de forma mas explicita
set_1.intersection(set_2) #  -> {3}
```

#### Diferencia

Tomar dos sets y de uno quitarle todos los elementos que tiene el otro

```python
set_1 = {1, 2, 3}
set_2 = {3, 4, 5}
set_3 = set_1 - set_2 #  -> {1, 2}

# O de forma mas explicita
set_1.difference(set_2) #  -> {1, 2}
```

#### Diferencia Simétrica

Tomar todos los elementos exceptos los que se repiten

```python
set_1 = {1, 2, 3}
set_2 = {3, 4, 5}
set_3 = set_1 ^ set_2 #  -> {1, 2, 4, 5}

# O de forma mas explicita
set_1.symmetric_difference(set_2) #  -> {1, 2, 4, 5}
```

En caso de que quieran hacer operaciones con sets y hacerlo de forma más explícita pueden usar los métodos:  
`set1.union(set2)`  
`set1.symmetric_difference(set2)`  
`set1.difference(set2)`  
`set1.intersection(set2)`  
Y pueden encontrar más métodos que pueden serles útiles [aquí](https://python-reference.readthedocs.io/en/latest/docs/sets/)