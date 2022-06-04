# Revisando detalles con Network

Esto de vaciar el caché es lo máximo, cuando pruebas proyectos grandes con un framework o librería donde a veces no se cargan bien los css o js cuando editas y usas un servidor en apache por ejemplo, entonces vaciando el caché todo se soluciona!

Existe un shortcut para recargar la página recargando caché:  
.  
En Windows: `ctrl + f5`  
.  
En macOS: `cmd + shift + R`

con network se puede obtener el tiempo que se requirio para hacer las peticiones y verificar el estado de las mismas. Así podemos saber cual es el error en petición y arreglar el proyecto