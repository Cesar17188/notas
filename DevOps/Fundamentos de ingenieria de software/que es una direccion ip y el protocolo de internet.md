# Qué es una dirección IP y el protocolo de Internet
IP es la sigla de Internet Protocol y una dirección IP es un número único con el cual una computadora o un dispositivo se identifica cuando está conectada a una red con el protocolo IP.

Cada dirección IP está compuesta por 4 números separados por puntos y son una forma de comprender números más grandes y complejos. Las direcciones IP tienen una estructura que las convierten en privadas o públicas y que además hacen parte de la máscara de red y el getaway.

Las direcciones IP permiten que cada computador o dispositivo pueda conectarse al exterior, es decir a Internet, esto a través de tecnologías como NAT o Network Address Translation.
![[Pasted image 20220203111716.png]]

la manera mas facil de ver si una ip es clase A, B o C es utilizando la mascara de red estandar y estas son:  
255.0.0.0 - clase A  
255.255.0.0 - clase B  
255.255.255.0 - clase C  
Pero, tambien existe el metodo de mascara de subred variable, la cual es muy util para segmentar una red ip con mascara de red estandar

todo seccion representada por un 0 en la mascara de red va a ser destinada a host o clientes y las que estan representadas por 255 son la destinada a la red