# Trabajando con Vue Components

```
<template>
  <form v-for="(movie, i) in movies" :key="i">
    <h3>{{ movie.name }}</h3>
    <button
      type="button"
      v-on:click="movie.quantity--"
      v-bind:disabled="movie.quantity <= 0"
    >
      -
    </button>
    {{ movie.quantity }}
    <button
      type="button"
      v-on:click="movie.quantity++"
      v-bind:disabled="!(movie.quantity < movie.available)"
    >
      +
    </button>
  </form>
</template>

<script>
export default {
  name: "Form",
  data() {
    return {
      movies: [
        { name: "Avengers", available: 5, quantity: 0 },
        { name: "Wonder Woman", available: 15, quantity: 0 },
      ],
    };
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
```

Solo como dato, pueden notar que el editor marca un error en la etiqueta de apertura de `<form>`, como tal, no es un error grave, pero para Vue es importante. Este error se debe a que Vue espera a que tú le digas cuál va a ser el identificador de cada elemento que se está iterando, de esta forma puedes evitar problemas de reactividad en el futuro.

La forma de solucionarlo es añadiendo un atributo `:key` a la etiqueta:

```
<form v-for="movie in movies" :key="movie.name">
```

En este caso estoy usando el atributo `name` de cada película como identificador, lo ideal sería que si tu array ya trae un ID lo uses.

Otra forma mucho más práctica para solucionar esto es decirle a Vue que genere un ID con autoincremento, de esta forma:

```
<form v-for="(movie, i) in movies" :key="i">
```

De esta forma, en la variable `i` Vue puede ir guardando un contador que puede actuar como id, simplemente se lo pasamos al `:key` 😄

PD. Puedes abreviar cualquier usando el `@`, por ejemplo, en lugar de poner `v-on:click`, pueden usar `@click` 👀