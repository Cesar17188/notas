# Visualización del árbol de decisión

**Visualización del árbol**

-   Importamos los módulos necesarios

```
from io import StringIO #nos permite trabaja con archivos externos
from IPython,display import Image, display #permite interactuar y crear imágenes
import pydotplus #permite usar el lenguaje graphviz para crear imágenes
```

-   Exportamos los datos a graphviz y luego los representamos en un archivo png:

```
out = StringIO()
tree.export_graphviz(tree_one, out_file=out) # exportamos los datos del árbol en lenguaje graphviz a StringIO
graph = pydotplus.graph_from_dot_data(out.getvalue()) #generamos el gráfico a través de pydotplus
graph.write_png('titanic.png') #guardamos el archivo en formato png
```