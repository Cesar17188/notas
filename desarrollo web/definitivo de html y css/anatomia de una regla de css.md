# Anatomía de una regla de CSS

**La estructura CSS se basa en reglas que tienen el siguiente formato:**

![](https://lenguajecss.com/css/introduccion/estructura-de-css/sintaxis-simple.png)

**Selector**: El selector es el elemento HTML que vamos a seleccionar del documento para aplicarle un estilo concreto.

**Propiedad**: La propiedad es una de las diferentes características que brinda el lenguaje CSS para dar estilos.

**Valor**: Cada propiedad CSS tiene una serie de valores concretos, con los que tendrá uno u otro comportamiento.

**Cada una de estas reglas se terminará con el carácter punto y coma (😉.**

## 

![](https://lenguajecss.com/css/introduccion/estructura-de-css/sintaxis-multiples-valores.png)

_Con todo esto le iremos indicando al navegador que, para cada etiqueta (selector especificado) debe aplicar las reglas (propiedad y valor) indicadas._

![[Pasted image 20211126154639.png]]
![[Pasted image 20211126154648.png]]

Vale aclarar que el selector puede ser tanto un elemento conocido como p, h1, li, etc; como una clase, pseudo-clase, pseudo-elemento o id.

La diferencia es que a los elementos conocidos se les _llama_ (se les inserta en CSS) mediante su propio nombre. Por ejemplo:  

![HTML.png](https://static.platzi.com/media/user_upload/HTML-54cf45db-6874-428d-8e2f-b5870922ce4d.jpg)

A las clases, pseudo-clases y pseudo-elemetos se les _llama _mediante un punto.  

![HTML (1).png](https://static.platzi.com/media/user_upload/HTML%20%281%29-bde2b689-ecdf-4fda-8dbe-500ecaf69972.jpg)

A los id se les _llama _mediante un numeral.  

![HTML (2).png](https://static.platzi.com/media/user_upload/HTML%20%282%29-f05848b4-967c-4a7e-bcec-79b8b5e14e97.jpg)