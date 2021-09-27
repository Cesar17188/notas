# Considerando las mejores prácticas para el despliegue

En esté punto ya tu aplicación está lista para el despliegue, pero lo que debemos considerar unas muy buenas prácticas para el lanzamiento a producción.

**Buenas prácticas**:

-   Remover constraseñas quemadas
-   Encapsular código spaghetti
-   Revisar la estructura del proyecto
-   Configurar los scripts de build
-   Agregar soporte de cache
-   Añadir HTTPS y CORS
-   Revisar otras prácticas de seguridad.

El termino **quemado significa**: tener las contraseñas directamente en el código y no en variables o variables de entorno, lo que sucede es que si estas contraseñas se suben al repositorio, podría malisiosamente leerse el archivo .git y sacar eso del historial, incluso si ya lo haz hecho y removido en otro commit, es muy importante que lo elimines del historial.

Aquí hay un lectura para remover los datos confidenciales del historial si te ha pasado: [https://help.github.com/es/articles/removing-sensitive-data-from-a-repository](https://help.github.com/es/articles/removing-sensitive-data-from-a-repository)

El **código spaghetti** es ese código que es muy dificil de leer o creece mucho, lo más recomendable es mover porciones de código a diferentes funciones que tengan mucho significado en esa porcion de código en especifico.

Scripts de **build**: si tu proyecto tienen algún paso de build, como de pronto minificar o transpilar código también es necesario que esté para que se vayan en código optimo para producción.

Soporte de cache: muchas veces cuando requerimos las peliculas, ellas no cambian porque no todo el tiempo se están agregando peliculas nuevas, entonces es importante tener una capa de cache tipo: _en 15 minutos siempre enviame el mismo resultado_, de está manera no tenemos que ir hasta base de datos a traer las peliculas, sino que las traemos del cache del navegador.

**Https**: la conexiónes por https son encriptadas y seguras, si por alguna vez un usuario y contraseña por una conexión que no es https, fácilmente podría agarrar tu usuario y contraseña porque están en texto plano.

**Cors**: sirve para que no todos los clientes se conecten a nuestro backend y no nos hagan cosas maliciosas, lo otro que es importante es que esté revisando las buenas prácticas de seguridad, que explores librerías como `helmet` o que revises open web `application security project` (owasp).