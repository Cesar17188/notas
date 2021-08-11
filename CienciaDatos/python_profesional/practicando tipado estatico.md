# Practicando el tipado estático

#### Modulo `mypy`

El modulo **mypy** se complementa con el modulo **typing** ya que permitirá mostrar los errores de tipado débil en Python.

Para revisar si algún archivo contiene errores de tipado ejecutamos en la línea de comandos lo siguiente:

```
mypy archivo.py --check-untyped-defs
```

Como resultado nos mostrará si existe algún error de compatibilidad de tipos.