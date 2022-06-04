# Auto-Layout: un amigo para la vida
![[Pasted image 20220111130021.png]]

## ¿Cómo creamos esa consistencia?
* Agregando:
	* Paddings
	* Márgenes
	* Comportamientos

## Propiedades del Auto Layout
* Son frames, no grupos
* Los frames tienen una alineación vertical u horizontal
	* Elementos dentro de un frame vertical: left, right, center o stretch
	* Elementos dentro de un frame horizontal: top, bottom, center o stretch
* Mantienen patrones de distancia simétricos entre sus elementos hijo.

## Creando Auto Layout
* Seleccionar elementos
* Shift + A
* Definir alineación frame
	* Default depende de los elementos existentes
* Definir alineación elementos
* Justificar los paddings
	* Padding se automatiza con puntos medios
* Justificar distancia entre elementos

## Editando Auto-Layout
* Ocultar / Mostrar elementos
	* Esto los "elimina" de la alineación
* Re-organización con:
	* Drag
	* Flechas
	* Íconos

Hay que tener en cuenta la diferencia entre pading y margin.  
Padding: es la distancia que existe del borde del elemento hacia adentro.  
Margin: es la distancia que existe del borde del elemento hacia afuera.  
Visualmente pueden tener el mismo resultado si no se tienen bordes, pero es importante conocer estas diferencias.