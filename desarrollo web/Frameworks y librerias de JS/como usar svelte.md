# Cómo usar Svelte

Rollup

---

Es un paquete de módulos para JavaScript que compila pequeños fragmentos de código en algo más grande y complejo, como una biblioteca o aplicación. Utiliza el nuevo formato estandarizado para módulos de código incluidos en la revisión ES6 de JavaScript, en lugar de soluciones idiosincrásicas anteriores como CommonJS y AMD. Los módulos ES le permiten combinar libremente y sin problemas las funciones individuales más útiles de sus bibliotecas favoritas. Esto eventualmente será posible de forma nativa en todas partes, pero Rollup te permite hacerlo hoy.

---

---

Para mas información puedes ver [acá](https://rollupjs.org/guide/en/)

```
<script>
  const movies = [
    { name: "Avengers", available: 5, quantity: 0 },
    { name: "Wonder Woman", available: 15, quantity: 0 }
  ];
</script>

{#each movies as movie}
<form>
	<h3>{movie.name}</h3>
	<button type="button" on:click={() => movie.quantity--} disabled={movie.quantity <= 0}>-</button>
	{movie.quantity}
	<button type="button" on:click={() => movie.quantity++} disabled={!(movie.quantity < movie.available)}>+</button>
</form>
{/each}
```