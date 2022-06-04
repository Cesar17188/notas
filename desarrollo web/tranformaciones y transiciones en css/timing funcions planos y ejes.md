# Timing functions, planos y ejes
Seguramente has visto esta imagen en muchos lugares cuando se habla de 3D. Esta es básicamente una forma más abstracta de representar una figura en 3D, básicamente el eje Y es la altura, el eje X es la anchura y el eje Z es la profundidad, es decir, eso que sale hacia ti.

![Ejes.png](https://static.platzi.com/media/user_upload/Ejes-54fb8c32-0ea5-42f0-912e-53b0c601a334.jpg)

Alo largo del eje Z podemos tener varios ejes X y Y, es decir, podemos tener varias capas, una debajo de otra, y básicamente eso es el contexto de apilamiento, vas apilando cada capita una debajo de la otra 😄 👇

![](https://media.giphy.com/media/1IvbqeWg7gLlRi2TAC/giphy.gif)

**Timinig function  
**La función de tiempo de animación especifica la curva de velocidad de una animación. La curva de velocidad define el TIEMPO que usa una animación para cambiar de un conjunto de estilos CSS a otro.  
animation-timing-function: linear|ease|ease-in|ease-out|ease-in-out|step-start|step-end|steps(int,start|end)|cubic-bezier(n,n,n,n).

Opciones  
• linear La animación tiene la misma velocidad de principio a fin.  
• ease Valor por defecto. La animación tiene un comienzo lento, luego rápido, antes de que termine lentamente.  
• ease-in La animación tiene un comienzo lento.  
• ease-out La animación tiene un final lento.  
• ease-in-out La animación tiene un comienzo lento y un final lento.  
• step-start Equivalente a pasos (1, inicio)  
• step-end Equivalente a pasos (1, fin)  
• steps(int,start|end) Especifica una función paso a paso, con dos parámetros. El primer parámetro especifica el número de intervalos en la función. Debe ser un número entero positivo (mayor que 0). El segundo parámetro, que es opcional, es el valor “inicio” o “final”, y especifica el punto en el que se produce el cambio de valores dentro del intervalo. Si se omite el segundo parámetro, se le asigna el valor “fin”  
• cubic-bezier(n,n,n,n) Defina sus propios valores en la función cubic-bezier. Los valores posibles son valores numéricos de 0 a 1.


https://easings.net/