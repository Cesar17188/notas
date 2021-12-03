# Organización de archivos en el frontend

Hay herramientas para el manejo del estado que nos ayudan a evitar a tener codigo espaguetti. Esto se le llama Deuda tecnica, por que en el futuro tendremos problemas en el futuro. Nos demoraremos un poco mas pero siempre es bueno tener una buena organizacion.

Se divide entre logico vs interfaz. Es bueno tener una capa de UI y otra una capa de Datos. En react es bueno dividir todo entre componentes contenedores y presentacional.

File Type First

Tipo de organizacion donde cada tipo de archivo.Una de componentes, una de contenedores, otra para rutas.

Feature First

donde cada componente de nuestra aplicacion es dividir una carpeta para cada elemento que tengamos. Una carpeta de Menu, una carpeta de Form, una carpeta de Button. Esta forma es buena ya que cada carpeta sera independiente y no sera tan difiicil de entender.

Apps For Apps

Una carpeta para cada aplicacion

Para Vue, el [Curso Avanzado de Vue.js](https://platzi.com/clases/avanzado-vue/) te da una base sólida de cómo puedes organizar tus carpetas. Para este curso, el profesor crea una web que usa el API de DIABLO III de Blizzard para armar un profile finder, y aquí el profesor organiza todo en diferentes tipos de carpetas, una carpeta para utils, otra para manejar el estado de Vue y otra carpeta de Vistas, y en la carpeta de Vistas, el profesor divide todo por componentes, por ejemplo, si tienes un componente de tipo “arma”, el profesor crea una carpeta para ese componente, y en el `Index.vue` se maneja el componente principal, y dentro de la misma carpeta crea los sub-componentes para ese componente jaja

A mí me gustó mucho esa forma de organizar los componentes para Vue ❤️