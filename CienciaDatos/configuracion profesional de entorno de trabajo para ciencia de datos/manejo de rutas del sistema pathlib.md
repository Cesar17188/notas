# Manejo de rutas del sistema: Pathlib
```
#
import pathlib
#
CURRENT_DIR = pathlib.Path(".").resolve()
print(type(CURRENT_DIR))

DATA_DIR = CURRENT_DIR.parent.joinpath("data") # CURRENT_DIR.parent / "data"
print(DATA_DIR)
print(DATA_DIR.exists())
print(DATA_DIR.is_dir())
#
DATA_DIR.joinpath("external_pathlib", "pathlib", "nested").mkdir(parents=True, exist_ok=True)
#
list(DATA_DIR.glob("*"))
```