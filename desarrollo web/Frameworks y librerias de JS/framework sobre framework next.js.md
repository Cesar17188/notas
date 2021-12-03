# Frameworks sobre frameworks: Next.js

## Next Vs Nuxt

**Next.js** es un framework que usa React.js para las vistas.  
**Nuxt.js** es un framework que usa Vue.js para las vistas.

![[Pasted image 20211114143127.png]]

Form.js

```
import React from "react";
import Link from "next/link";

export default function Form(props) {
  const [quantity, setQuantity] = React.useState(0);
  const { movie } = props;

  return (
    <form>
      <h3>{movie.name}</h3>
      <button
        type="button"
        onClick={() => setQuantity(quantity - 1)}
        disabled={quantity <= 0}
      >
        -
      </button>
      {quantity}
      <button
        type="button"
        onClick={() => setQuantity(quantity + 1)}
        disabled={quantity >= movie.available}
      >
        +
      </button>
      <Link href={{ pathname: "pay", query: { name: movie.name, quantity } }}>
        <a>Pagar</a>
      </Link>
    </form>
  );
}

```

movies.js

```
import Form from "./../components/Form";
import Link from "next/link";

const movies = [
  { name: "Avengers", available: 5, quaantity: 0 },
  { name: "Wonder Woman", available: 15, quaantity: 0 }
];

export default function MoviePage() {
  return (
    <div>
      <Link href="/">
        <a>Home</a>
      </Link>
      <h2>Peliculas</h2>
      {movies.map((movie) => (
        <Form key={movie.name} movie={movie} />
      ))}
    </div>
  );
}

```

index.js

```
import Link from "next/link";

export default function IndexPage() {
  return (
    <div>
      <p>Este es un sitio para comprar boletos de tus peliculas favoritas</p>
      Hello World.{" "}
      <Link href="/movies">
        <a>Ir a comprar pelis</a>
      </Link>
    </div>
  );
}

```