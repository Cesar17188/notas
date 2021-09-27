# Creación de tests para nuestros servicios

En está sección aprenderas a crear los test para nuestra capa de servicios, al igual que con la capa de rutas, aquí lo que nos interesa, es que los servicios sean testeados en lo que va a devolver y no las librería que llamá, por lo que debemos mockear la librería de mongo, te mostraré como puedes hacerlo en el código.

_Lo que vamos a hacer es que vamos a ir a nuestra carpeta de utilis - mocks y vamos a crear un nuevo mock que sería para librería de mongo_

Vamos a requerir **sinon**. Lo que **nos permite crear struct o mocks**, **sinon** cada vez que creamos un nuevo `struct`, les `inyecta unas propiedades` si estos fueron llamados o no. Entonces es super útil para que en nuestros servicos puedamos probar cuando el servicio fue ejecutado, si llamó los métodos de las respectivas librerías.

También vamos a traer de los **mocks**. Los mocks que creamos con anterioridad de las peliculas y de la funcionalidad `filteredMoviesMock`, esto es con el fin de cuando se haga un test con los tags podamos simular que se filtro. Luego vamos a hacer la creación de nuestros `structs`.

El primero sería `getAll` de mongo, uno de los métodos que tienen los `structs` es por ejemplo decidir que cuando se llamé con ciertos argumentos resuelva con cierta respuesta, en esté caso vamos a decir que cuando lo llamé con movies que sería la collection que le va a pasar el servicio a la librería de mongo, pues resuelva con nuestros mocks de las peliculas.

Ahora lo que debemos hacer es crear un nuevo archivo para los test de nuestros servicios, el cual vamos a llamar