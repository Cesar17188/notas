# Medidas EM

EM = es un acronimo de elemento y lo que hace es tomar el tamaño de fuente que tenga el padre directo ejemplo:

```
.container {
   font-size: 20px
   }

.container div {
    font-size: 2em
   }
```

aqui los el tamaño del div que esta dentro de la clase container tenda un tamaño de 40px, ya que  
.  
1em = 20px  
.  
y como estamos asignandole 2 em seria como 20px + 20px  
.  
y si por ejemplo tenemos el siguiente caso :

```
.container {
   font-size: 20px
   }

.container div {
    font-size: 2em
   }

.container div p {
   font-size: 1.5em
   }

```

a continuacion veremos que la etiqueta p tendra un tamaño de fuente de 60px  
ya que toma como referencia el tamaño de su padre ( 40px ) y haria la siguiente operacion 40*1.5 que es igual a 60, es por eso que la etiqueta p tomo el valor de 60px

**Unidades absolutas**  
Generalmente se usa el pixel “px”.

```
h1{
	width: 500px;
}
```

El problema de usar medidas absolutas es que pueden ser desproporcionadas para distintos tipos de dispositivos.  
**Unidades Relativas**  
*  
**Porcentaje**

```
/*Ocupará todo el ancho de la pantalla sin importar el tamaño*/
h1{
	width: 100%;
}
```

**em**  
Depende exclusivamente del cuerpo tipográfico. Es decir del font-size de la etiqueta de su elemento padre.

```
body{
	font-size: 20px;
}
h1{
	font-size: 2em; /*  2 x 20 = 40px */		
}
```

Lo bueno de esta unidad es que si en un futuro modificamos el valor del _font-size_, entonces sus otros valores se ajustarán como podría pasar en el siguiente ejemplo de código.

```
p {
	font-size: 24px;
	margin-top: 1em; /* 1 x 24 = 24px */
	margin-bottom: 1em; /* 1 x 24 = 24 px*/ 
}
```

Lo malo, es que si lo usamos como el profesor planteó como un problema al usar em, podríamos perder la cuenta de cómo calcular el em si es que tenemos muchos elementos anidados (un elemento dentro de otro) ya que depende de su padre directo.

Si te gustó mi resumen dale me gusta y comenta, así me motivo a hacer más resúmenes ✍

Sigamos aprendiendo juntos 💪