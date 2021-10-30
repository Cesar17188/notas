# Manejo de rutas del sistema: PyFilesystem2

```
#
import fs
#
CURRENT_DIR =fs.open_fs(".")
print(CURRENT_DIR.exists("."))
CURRENT_DIR.exists("..")
#
DATA_DIR = fs.open_fs("../")
print(DATA_DIR.exists(""))
DATA_DIR.listdir(".")

for path in DATA_DIR.walk.files():
    print(path)

    with DATA_DIR.open(path) as data_file:
        print(data_file.read())

for path in DATA_DIR.walk.dirs():
    print(path)
#
DATA_DIR.makedir("external_fs",recreate=True)
#
sub_data_dir = DATA_DIR.makedirs("external_fs/fs/nested", recreate=True)
sub_data_dir.makedir("test")
```