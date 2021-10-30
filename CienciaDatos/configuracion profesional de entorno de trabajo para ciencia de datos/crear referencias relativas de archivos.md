# Crear referencias relativas de archivos

```
#
import pyprojroot
pyprojroot.here().joinpath("data", "raw")
#
import pyhere
pyhere.here("data", "raw")
pyhere.here().resolve().joinpath("raw")

#
def make_dir_function(dir_name):
    def dir_function(*args):

        if isinstance(dir_name, str):
            return pyprojroot.here().joinpath(dir_name, *args)
        else:
            return pyprojroot.here().joinpath(*dir_name, *args)

    return dir_function

# Nested lambda.
make_dir_function_lambda = lambda dir_name: lambda *args: pyprojroot.here().joinpath(dir_name, *args)

#
data_dir = make_dir_function("data")
data_dir("external", "os", "do")
#figures_dir = make_dir_function_lambda("figures")
figures_dir("amazing", "plots", "here")

```