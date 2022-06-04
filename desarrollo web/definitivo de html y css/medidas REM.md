# Medidas REM

![[Pasted image 20211218140512.png]]

REM : funciona igual que el em, con la diferencia que es relativo al valor de la fuente del elemento html, y no tiene en cuenta el valor heredado o del elemento que lo contiene.

Por defecto el html viene con un tamaño de fuente de 16px asi que siempre  
.  
1 REM = 16PX  
.  
Si queremos aplicar rem de una forma mas sencilla para no tener que hacer tantos calculos asemos lo siguiente  
.  
vamos a reescribir en css nuestro html

```
html {
      font-size: 62.5%; 
     }

```

esto lo que hara es darle a el html un valor de 10px ya que 16px - 62.5% = 10px

ahora si por ejemplo a una etiqueta le asignamos 2rem este hara referencia a 20px, o si por ejemplo le damos un valor de 1.5rem su valor sera de 15px