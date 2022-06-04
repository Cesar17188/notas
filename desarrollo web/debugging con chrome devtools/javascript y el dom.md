# JavaScript y el DOM


para optener un elemento del DOM lo seleccionamos desde la DevTool de navegador y despues vamos a consola y copiamos $0  
esto nos traera ese elemento

para empezarlos a traer los elementos para agregarle javascript podemos usar estas dos formas:

1.  getElementById() = para llamar a un id.
    
2.  vamos al elemento, damos click derecho, nos saldra un menu vamos a donde dice (copy) y despues donde dice ( copy JS-PATH )
    
    querySelector(“Body > header”)
    

![Captura de pantalla (56).png](https://static.platzi.com/media/user_upload/Captura%20de%20pantalla%20%2856%29-60297e13-8b70-4090-b5d9-f0518461ff09.jpg)

ya despues con el elemento que obtengamos le pondremos el javascript



```js
getElementById() = para llamar a un id.
querySelector() = sirve para llamar a un elemento tanto #id , como .clases .
querySelectorAll() = sirve para llamar a todas las clases que existan.
getElementsByTagName() = sirve para llamar solo elementos HTML.
getElementsByclassName() = sirve para llamar a las clases del documento entero.
```


Escribí un post en la sección de tutoriales de algunas funcionalidades adicionales de devtools.

[https://platzi.com/tutoriales/1867-devtools/5283-funcionalidades-utiles-de-chrome-devtools-no-cubiertas-en-el-curso/](https://platzi.com/tutoriales/1867-devtools/5283-funcionalidades-utiles-de-chrome-devtools-no-cubiertas-en-el-curso/)