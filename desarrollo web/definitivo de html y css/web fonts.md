# Web fonts

Son grupos familiares de fuentes, los navegadores web poseen fuentes predeterminadas y dependiendo del mismo cada uno de ellos posee estilos diferentes.

**Algunas Generic Families**

1.  serif: Son un tipo de fuente de estilo formal o clásico como Times New Roman.
2.  sans-serif: No tienen acabado en las puntas, como: Verdana.
3.  cursive: Son las que tienen estilo cursivo.
4.  monospace: Son tipos de fuentes con espaciado entre las letras, como: Roboto mono.

**¿Como puedo saber que tipo de fuente tengo instaladas en mi navegador?**

Menú>Configuración>Diseño>Personalizar Fuentes>Fuente Serif/Fuente Sans-serif

**¿Como puedo importar tipos de fuentes a mi proyecto?**

-   Ir a Google Fonts.
-   Seleccionar la fuente.
-   Seleccionar Estilo de fuente.
-   Agregar al proyecto, se considera buena práctica agregar las fuentes utilizando la etiqueta <link>, ya que la fuente cambia la fuente una vez que se haya cargado la página.

**Buenas Prácticas**  
Cargar una sola fuente.  
Importarlas siempre en la etiqueta del head.

Según conceptos de diseño hay varias recomendaciones para elegir la fuente / tipografía:

-   Para textos en digital (Como páginas web) usamos fuente sans-serif sin esas terminaciones (setifas).
-   Las fuentes con Serifa se recomiendan para impresas o en digital para titulos.

Para calcular el interlineado usamos la siguiente regla:

“2 puntos más que la fuente (Fuente de 8px pues interlineado de 10px)”

otra forma de tener varias fuentes para nuestro proyecto sin tener que importarlas desde un link externo es descargado la fuente directamente de google fonts, crear una carpeta fonts en el proyecto almacenar alli los archivos .ttf y luego en el archivo de css importarlas desde alli. el atributo font-family le pondremos el nombre de la fuente y en el src: la ruta donde esta almacenado el archivo .ttf

@font-face{  
font-family: ‘ChakraPetch-Regular’;  
src: url(…/fonts/ChakraPetch-Regular.ttf);  
}

Varios puntos interesantes a sumar:

1.  La “puntitas al final” en la tipografias serif se llaman **_serifas_**.
    
2.  En realidad al grosor no se le dice muy gorditas 😁, se le dice **_peso de la tipografía_**.
    
3.  Tal como indicó Diego en la clase, no es bueno cargar muchas tipografías, normalmente se usan un máximo de 2 tipografías. Pero también es bueno no cargar muchos pesos distintos de una tipografía porque eso compromete el rendimiento, solo agrega a la importación los pesos que necesites.
    
4.  Para que el renderizado de la tipografía sea mas eficiente es buen practica colocarlo en el head antes de cargar el CSS, de modo que cuando el CSS cargue ya tiene disponible las tipografías.
    

**NOTA:** He estado haciendo algunas pruebas y a pesar de no tener una información oficial creo que Google esta haciendo algunas pruebas con sus tipografías en Google Chrome. He creado proyectos donde no importo la tipografía, pero si llamo a la fuente en el CSS y se renderizan correctamente, claro, solo en Google Chrome…