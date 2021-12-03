# Pseudo clases y pseudo elementos

Es nombrar clases siguiendo el siguiente patrón: BLOQUE__ELEMENTO–MODIFICADOR

Por ejemplo:

```
<!-- BLOQUE -->
<main class="Padre">
	<!-- BLOQUE__ELEMENTO --> 
	<section class="Padre__Hijo">
		<!-- BLOQUE__ELEMENTO--MODIFICADOR -->
		<article class="Padre__Hijo--Mayor"></article>
	</section>
	<section class="Padre__Hijo"></section>
	<section class="Padre__Hijo"></section>
	<section class="Padre__Hijo"></section>
 </main>
```

youtube- [BEM: Simplifica tu CSS](https://youtu.be/wDUwGo98JTA)

youtube- [Que rayos es la Metodología BEM](https://youtu.be/bvnzyXGkNY4)

Documentacion- [sobre BEM](http://getbem.com/introduction/)

Documentación- [Las Pseudo-classes hacen uso de un ‘:’](https://developer.mozilla.org/es/docs/Web/CSS/Pseudo-classes)

Documentacion- [Los Pseudoelementos hacen uso de dos ‘::’](https://developer.mozilla.org/es/docs/Web/CSS/Pseudoelementos)

```
/*Algunos Pseudo-classes:*/
:root{}
//representa elemento HTML, con la especificidad de clase //usado para anidar variables CSS
:active
//se activa al hacer clic down
:visited
//cambio visual cuando se visita un enlace
:hover
//permite cambiar el estado de un elemento cuando elmause se sobrepone sobre él
:first-child // para afectar solo al primer hijo // se coloca en el padre (ul) para afectar a su primer hijo (li)
:last-child // para afectar solo al ultimo hijo
:not  //negar una codiciones (ignorar una condicion) //ejemplo .clase:not(last-child)
//afecto a todos menos el ultimo
:empty 
//ayuda a detectar cuando un elemento esta vacio. //ejemplo .class:empty{background:yellow;} //resaltar
:nth-child() 
// tag:nth-child(2){} //afectara al segundo elemento
```

[

FAQ / Methodology / BEM

https://en.bem.info/methodology/faq/#why-bem





](https://en.bem.info/methodology/faq/#why-bem)