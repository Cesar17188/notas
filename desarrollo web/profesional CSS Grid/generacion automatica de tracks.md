
# Generación automática de tracks + Quíz

<h4>**Ideas/conceptos claves**</h4>

**Track** ⇒ Union de dos o más celdas dentro de una grid

<h4>**Apuntes**</h4>

-   No todas las grillas tendrán items exactamente contados
    -   No contaras con filas y columnas exactas por que los datos pueden ser dinámicos
-   Para ello está la **grid implícita**
    -   Te crea filas o columnas si las necesitas con anchos sin tamaño
-   Para que se valla ordenando según lleguen nuevos elementos se debe usar esta propiedad
    -   Don especificaremos el tamaño donde agregarlo

```css
.container {
	grid-auto-columns: 60px;
}
```

-   También podemos cambiar el orden visual de los elementos hijos

```css
.container {
		grid-auto-flow: row | column | row dense | column dense;
}
```

**RESUMEN:** Debido a que existen casos que nunca sabremos cuantos elementos exactamente tendrá nuestra grilla entonces podemos generarla automáticamente con grillas implícitas.
