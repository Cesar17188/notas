# Manejo del estado en React


Así quedaría con el reto:

```
import React from 'react';

export default function Form(props) {
  const [quantity, setquantity] = React.useState(0);
  const { movie } = props;
  return (
    <form>
      <h3>{movie.name}</h3>
      <button type='button' onClick={() => setquantity(quantity - 1)} disabled={quantity === 0}>
        -
      </button>
      {quantity}
      <button
        type='button'
        onClick={() => setquantity(quantity + 1)}
        disabled={movie.available === quantity}
      >
        +
      </button>
    </form>
  );
}
```