# Cómo usar React.js

Crea tu cuenta de CodeSandbox aquí: [https://codesandbox.io/](https://codesandbox.io/).

**¿Cómo evitar que todos los componentes vayan envueltos en etiquetas `<div>` y por ende el DOM se llene de divs innecesarios?**  
En vez de envolver todo el componente entre etiquetas `<div>` se puede usar la etiqueta de JSX `<React.Fragment>` (o su “shorthand”… `<>`):

```jsx
<React.Fragment>
	<h2>Titulo</h2>
	<form>...</form>
</React.Fragment>
```

Lo cual sería equivalente a:

```jsx
<>
	<h2>Titulo</h2>
	<form>...</form>
</>
```

  
**¿Cómo hacer que la página no se recargue?**  
Se puede asociar una función que se ejecute `onclick` en cada botón, o como submit del form, cuya primera línea sea `event.preventDefault()`.


Como dato curioso acerca de porqué se recarga la página cuando haces click en esos botones, es porque al estar dentro de un <form>, los elementos button que no tienen el type (button o submit) por default se le asigna el submit, y al darle click se ejecuta se ejecuta el submit del form lo cual genera la recarga de la página.