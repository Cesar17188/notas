# Manejo de rutasdel sistema: OS

### Manejo de Excepciones

La documentación nos resalta y recuerda lo importante que es el manejo de excepciones, por ejemplo si tenemos un proceso iterativo y queremos que finalice por todos los elementos así sea que durante su ejecución tenga errores.

> Note All functions in this module raise OSError (or subclasses thereof) in the case of invalid or inaccessible file names and paths, or other arguments that have the correct type, but are not accepted by the operating system.

[os — Miscellaneous operating system interfaces¶](https://docs.python.org/3/library/os.html)

```
import os
#
CURRENT_DIR = os.getcwd() # Retrieve current directory

print(type(CURRENT_DIR))

print(os.path.abspath(os.path.join(CURRENT_DIR, os.pardir))) # parent directory...
DATA_DIR = os.path.join(CURRENT_DIR, os.pardir, "data/") # os.pardir: ..

print(DATA_DIR)
print(os.path.exists(DATA_DIR))
print(os.path.isdir(DATA_DIR))
#

[os.path.join(DATA_DIR, item) for item in os.listdir(DATA_DIR)]

#
os.mkdir(os.path.join(DATA_DIR, "external_os"))

# 
os.makedirs(os.path.join(DATA_DIR, "external_os", "os", "nested"))
```