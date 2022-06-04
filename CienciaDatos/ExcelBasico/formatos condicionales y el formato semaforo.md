# Formatos condicionales y el formato de semáforo

![[Pasted image 20211226124953.png]]

La función SI es muy útil, pero no hay que sobre abusar de ella para casos donde no es lo mejor. Les pongo un caso que me ocurrió con un compañero de la U, pero usando como ejemplo los datos del curso.  
.  
Imaginen que al lado de la columna donde está la marca del vendedor tienen que agregar una columna con el pais de origen de esa marca. Uno podría pensar, ahhhhh si, ocupo un SI para cada marca y pum, listo problema listo.(usé solo 3 por resumir el ejemplo).  
=SI(Celda=“apple”,“USA”,SI(Celda=“microsoft”,“USA”,SI(Celda=“sony”,“Japon”)))  
Quedaría así tan solo teniendo 3 marcas, imaginen fueran más o si simplemente van llegando nuevas marca, quedaría una fórmula enooooooorme.  
.  
Este es un típico caso donde es mejor usar BUSCARV haciendo una matriz.  

![excel.png](https://static.platzi.com/media/user_upload/excel-2667e7bc-7d7b-4e61-9a04-fb03a97fe250.jpg)  
De esta forma si hay muchas marcas o si aparecen nuevas marcas se van agregando rápido y es mucho más entendible.  
.  
El SI es un gran poder y por ende, una gran responsabilidad

**Notas:**  
* Señalar columna en donde aplicaremos el condicional  
* Formato condicional: Escala de color  
* Más reglas  
* Parte superior definir regla  
* Escala de colores  
**Semáforo**  
* Señalar columna en donde lo aplicaremos  
* Formato condicional: Nueva regla  
* Estilo de formatos: Conjunto de iconos  
* Ajustar el tipo: numérico  
**Consejos:** Quitarles las comillas a los números que están dentro de la fórmula para que se pueda visualizar los iconos (=SI(I4>800;3;SI(I4=800;2;1)))  

![Clase 21.png](https://static.platzi.com/media/user_upload/Clase%2021-af3df65a-d9c1-409b-8336-9e7954b5bf16.jpg)  
.  
**Resumen o Idea Principal:** Como realizar el análisis de manera más visual en la base de datos