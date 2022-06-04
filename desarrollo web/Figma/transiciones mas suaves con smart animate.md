# Transiciones más suaves con Smart Animate

## ¿Cómo se mueve un elemento en la vida real?
* Se desplaza desde un punto A hasta un punto B, tomando velocidad al principio y desacelerando al final.

## ¿Qué necesitamos para hacer un smart animate?

* Dos frames con la misma cantidad de frames y sus nombres correspondientes
	* Uno será el punto A
	* El otro será el punto B
* Definir una interacción que cause el trigger de la animación

## Parámetros del trigger
* none
* On Tap / Drag
* While Hovering / Pressing
* Key / Gamepad
* Mouse Enter / Leave
* Touch Down / Up


## La clave está en el ritmo

## Cómo quitamos elementos de una interfaz
* Un elemento desaparece cuando su opacidad se mueve desde 100% a 0%
* También puede desaparecer con movimiento, sacándolo del frame.
	* Combinando ambos

## Recomendaciones
* Nombra muy bien tus capas
	* Esto te ayudará a identificar fácilmente los diferentes objetos que se están moviendo a lo largo de los frames
* El tiempo máximo de respuesta a una acción / trigger debe ser de 400 ms.
	* "Doherty Threshold"


recopilación de blogs, canales de youtube, y màs sobre diseño UI y UX. Espero que les sea útil:[Recopilación sobre UX - UI](https://gist.github.com/jfelipebc/672d119c13d283d6952afe65b6f63c7c)

