# Promesas

Para crear las promesas [[promesas]] [[promesas node]] usamos la clase Promise. El constructor de Promise recibe un sólo argumento, un callback con dos parámetros, **resolve** y **reject**. resolve es la función a ejecutar cuando se resuelve y reject cuando se rechaza.

El async/await es sólo syntax sugar de una promesa, por debajo es exactamente lo mismo.

La clase Promise tiene algunos métodos estáticos bastante útiles:

-   **Promise.all**. Da error si una de las promesas es rechazada.
-   **Promise.race**. Regresa sólo la promesa que se resuelva primero.

Aquí tienes el código inicial para hacer este ejercicio (el del repo es el código final, lo cual complica todo).

Copia, pega & disfruta de la clase.

```
<html>
  <head>
    <title>Promesas</title>
  </head>

  <body>
    <a href="/ejercicios/">Go back</a>

    <ul>
      <li><button id="sequence">Get Top Movies in Sequence</button></li>
      <li><button id="parallel">Get Top Movies in Parallel</button></li>
      <li><button id="fastest">Get Fastest Top Movie</button></li>
    </ul>

    <ul id="movies"></ul>

    <script>
      // Ejemplo: renderMovies([{ title: "Spider-Man", release_date: "2019-06-30", poster_path: "/rjbNpRMoVvqHmhmksbokcyCr7wn.jpg" }])
      // Traducir las funciones de usar thens a usar async/await
      // Crear función para que no nos gastemos la cantidad de requests demasiado rapido
      // Crear función donde hacemos requests secuenciales
      // Crear función donde hacemos requests en paralelo
      // Crear función donde obtenemos el primer request que llegue

      // The Movie Database API: https://developers.themoviedb.org/3/getting-started/introduction
      const apiKey = 'b89fc45c2067cbd33560270639722eae';

      function getMovie(id) {
      const url = `https://api.themoviedb.org/3/movie/${id}?api_key=${apiKey}`;
      return fetch(url).then(response => response.json());
      }

      function getPopularMovies() {
        const url = `https://api.themoviedb.org/3/discover/movie?sort_by=popularity.desc&api_key=${apiKey}`;
        return fetch(url)
          .then(response => response.json())
          .then(data => data.results);
      }

      function getTopMoviesIds(n = 3) {
        return getPopularMovies().then(popularMovies =>
           popularMovies.slice(0, n).map(movie => movie.id)
         );
      }

      function renderMovies(movies) {
        const movieList = document.getElementById('movies');
        movieList.innerHTML = '';

        movies.forEach(movie => {
          const listItem = document.createElement('li');
          listItem.innerHTML = `
            <img src="https://image.tmdb.org/t/p/w342${movie.poster_path}" />
            <h5>${movie.title}</h5>
            <p>Released on <em>${movie.release_date}</em></p>
            `;

          movieList.appendChild(listItem);
        });
      }

      function getTopMoviesInSequence() {
        
        return [];
      }

      function getTopMoviesInParallel() {
        return [];
      }

      async function getFastestTopMovie() {
        return {};
      }

      document.getElementById('sequence').onclick = async function() {
        const movies = await getTopMoviesInSequence();
        renderMovies(movies);
      };

      document.getElementById('parallel').onclick = async function() {
        const movies = await getTopMoviesInParallel();
        renderMovies(movies);
      };

      document.getElementById('fastest').onclick = async function() {
        const movie = await getFastestTopMovie();
        renderMovies([movie]);
      };
    </script>
  </body>
</html>

```


## Funciones asíncronas

‌

Cuando queremos tener una función que se ejecute eventualmente podemos usar las promesas, también se usan para esperar datos que van a tardar en llegar. Para esperar una información hay que usar el _keyword_ `await`, pero para usarlo hay que colocar `async` antes de la función.

```
function resolveAfter2Seconds() {
  return new Promise(resolve => {
    setTimeout(() => {
      resolve('resolved');
    }, 2000);
  });
}

async function asyncCall() {
  console.log('calling');
  var result = await resolveAfter2Seconds();
  console.log(result);
  // expected output: 'resolved'
}

asyncCall();
```

‌

Para esperar información de alguna API necesitamos usar este tipo de funciones para esperar la información en un tiempo indeterminado.

‌

## Promesas

‌

El objeto **`Promise`** (Promesa) es usado para computaciones asíncronas. Una promesa representa un valor que puede estar disponible ahora, en el futuro, o nunca.

```
new Promise( /* ejecutor */ function(resolver, rechazar) { ... } );
```

‌

Una **Promesa** es un proxy para un valor no necesariamente conocido en el momento que es creada la promesa. Permite asociar manejadores que actuarán asincrónicamente sobre un eventual valor en caso de éxito, o la razón de falla en caso de una falla. Esto permite que métodos asíncronos devuelvan valores como si fueran síncronos: en vez de inmediatamente retornar el valor final, el método asíncrono devuelve una _promesa_ de suministrar el valor en algún momento en el futuro.

‌

Una `Promesa` se encuentra en uno de los siguientes estados:

‌

-   _pendiente (pending)_: estado inicial, no cumplida o rechazada.
    
-   _cumplida (fulfilled)_: significa que la operación se completó satisfactoriamente.
    
-   _rechazada (rejected)_: significa que la operación falló.
    

‌

[`Promise.all(iterable)`](https://developer.mozilla.org/es/docs/Web/JavaScript/Referencia/Objetos_globales/Promise/all)

‌

Devuelve una de dos promesas: una que se cumple cuando todas las promesas en el argumento iterable han sido cumplidas, o una que se rechaza tan pronto como una de las promesas del argumento iterable es rechazada. Si la promesa retornada es cumplida, lo hace con un arreglo de los valores de las promesas cumplidas en el mismo orden definido en el iterable. Si la promesa retornada es rechazada, es rechazada con la razón de la primera promesa rechazada en el iterable. Este método puede ser útil para agregar resultados de múltiples promesas

‌

[`Promise.race(iterable)`](https://developer.mozilla.org/es/docs/Web/JavaScript/Referencia/Objetos_globales/Promise/race)

‌

Devuelve una promesa que se cumple o rechaza tan pronto como una de las promesas del iterable se cumple o rechaza, con el valor o razón de esa promesa.

![[Pasted image 20211001180007.png]]