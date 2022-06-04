# Alineamiento en el elemento contenedor + Quiz

-   **Alineamiento ⇒** en donde quiero que estén los elementos de mi grid
-   Podemos alinear todos los contenedores a una dirección
-   Tenemos dos Grupos para ordenar por parte del contenedor
    -   **Items**
        -   `justify-items`
        -   `align-items`
        -   `place-items`
    -   **Content**
        -   `justify-content`
        -   `align-content`
        -   `place-content`
-   Propiedades en común:
    -   **Justify** ⇒ Alineación por dentro de la grid
        -   Inline axis (row axis)
        -   De izquierda a derecha
            -   start
            -   end
    -   **Align ⇒ Alinear la Grid en su contenedor**
        -   block axis (column axis)
        -   De arriba hacia abajo
            -   start
            -   end

<h4>`justify-items`</h4>

```css
.container{
		justify-items: start | end | center | stretch;
}
```

<h4>`align-items`</h4>

```css
.container{
	align-items: start | end | center | stretch;
}
```

<h4>`place-items`</h4>

-   Es el shorthand para los dos anteriores

```css
.container{
	align-items: <alig-items> / <justify-items>;
}
```

<h4>`justify-content`</h4>

```css
.container{
		/* Parte 1 */
		justify-content: start | end | center | stretch;
		/* Parte 2 */
		justify-content: space-around | space-between | space-evenly;
}
```

<h4>`Align-content`</h4>

```css
.container{
		/* Parte 1 */
		align-content: start | end | center | stretch;
		/* Parte 2 */
		align-content: space-around | space-between | space-evenly;
}
```