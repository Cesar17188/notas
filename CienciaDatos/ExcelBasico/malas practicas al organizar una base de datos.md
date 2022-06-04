# Malas prácticas al organizar una base de datos

**Malas prácticas al organizar una base de datos.**  
**Títulos innecesarios.-** Una mala práctica es crear diferentes títulos para enlistar fechas en lugar de tener una sola fila de referencia.

-   Ejemplo: Títulos de celdas “18/Oct 19/Oct 20/Oct” en lugar de tener una celda de referencia como ser “Fecha de Orden” donde se almacenaría todas esas fechas. La segunda celda es muy útil para manejar base de datos, la primera no.

**Formato de Celda.-** Otro error común tener una celda en un formato diferente que no nos permita realizar una acción.

-   Ejemplo: Tener una celda en formato texto y que esto nos impida realizar operaciones en ella.

**El enemigo invisible.-** Otro error común se encuentra en los nombres dentro de una casilla, esta puede contener espacios que son invisibles a simple vista pero que nos causan problemas al tener una base de datos.

-   Solución.- Usa la formula =espacios(texto) en texto pones la casilla donde quieres quitar los espacios y listo. En otras versiones de Excel =ESPACIOS esta con el nombre de =RECORTAR.

**Ceros delante de números.-** Al momento de crear base de datos Excel elimina los ceros que estén delante de números automáticamente.

-   Solución.- Pon un apostrofe (’) delante del numero, esto no te permitirá hacer operaciones con ese dato, pero si realizar búsquedas para las base de datos.

![[Pasted image 20211221161109.png]]

Para quienes tengan su Excel o su computador en un idioma diferente al español, esta página es maravillosa para poder saber cuál es la fórmula en cada uno de los diferentes idiomas: [https://es.excel-translator.de/](https://es.excel-translator.de/) En el buscador escriben la fórmula en español y ahí les da las fórmulas en otros idiomas. E incluso, deja ver el nombre en versiones previas de Excel en español. Por ejemplo, así se ve con ‘ESPACIOS’: 

![Capture.PNG](https://static.platzi.com/media/user_upload/Capture-778ed559-6261-4f74-aa4c-295dd1c17778.jpg)