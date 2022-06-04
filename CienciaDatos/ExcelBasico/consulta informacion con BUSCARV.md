# Consulta información con BUSCARV
En Excel 2010 (sin el Service Pack) esta formula se reemplazó por CONSULTAV fue toda una polémica, pero luego retomaron a BUSCARV a pedido de los usuarios. Por cierto en ingles es VLOOKUP.

![[Pasted image 20211215135421.png]]

Cuando se utiliza la formula buscarv en dos libros diferentes Excel inmoviliza el rango de la matriz_tabla automáticamente, pero cuando se utiliza la formula buscarv dentro del mismo libro, hay que inmovilizar los rangos de la matriz_tabla manualmente, esto se logra oprimiendo F4, después de seleccionar el rango mientras se escribe la fórmula, va a notar que aparecen los símbolos $ en el rango de la matriz_tabla.

Esto sirve para que al arrastrar la formula (hacia abajo) por las filas del Excel, el rango de la matriz_tabla no se desplace hacia abajo a medida que usted arrastra la formula, si esto pasa la matriz_tabla dejaría por fuera los primeros datos de la tabla y obtendria un error #N/A.