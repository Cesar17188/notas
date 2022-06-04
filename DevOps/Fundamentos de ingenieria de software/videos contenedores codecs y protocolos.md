# Videos, contenedores, codecs y protocolos

![[Pasted image 20220210173805.png]]

En un vídeo hay muchos factores para comprimir, un vídeo es si es una serie de fotos vistas muy rápido. por ejemplo si un vídeo tiene 100 frames a 24 frames/segundo y si cada frame pesara 1.9MB el vídeo pesaría más de 100MB por 4 segundos de vídeo.

Por esto en los vídeos se utilizan varias formas de compresión

**Contenedores:** es el formato es que se guarda el vídeo como .avi, .mp4, .flv, .mpg, .webm  
**Codecs:** es un algoritmo que comprime un vídeo y lo descomprime como divx, h.264, ogg, vp9  
**Protocolos:** es la forma de transmitir los vídeos como RTMP  
**Keyframes:** cada cierta cantidad de frame existe un frame que vuelve a definir todo el área

términos de audio y sonido.

Estrictamente cuando hablamos de **audio** nos referimos a señales eléctricas, cuando hablamos de **sonido** nos referimos a ondas mecánicas.  
Por ejemplo cuando hacemos un aplauso en el mundo “real”, se generan ondas mecánicas (sonido) que llegarían a un micrófono, dicho micrófono se conoce como transductor ya que convierte de un tipo de energía a otra. En éste caso se convierte de energía mecánica a eléctrica y solo después del micrófono es que se le puede llamar audio.

En el caso de la compresión de mp3 no es que el oido humano no escuche esas ondas, de hecho las grabaciones en general de alta fidelidad se hacen a 16bits con un muestreo de 44100 Hz. Esto se basa en el teorema de Nyquist y asegura que grabaremos solo lo que el humano es capaz de escuchar (20Hz-20KHz). Si revisamos un archivo wav podemos ver que se encuentra esa información.

![Wav File](https://s3-us-west-1.amazonaws.com/publicssets/Screen+Shot+2017-03-25+at+9.12.40+AM.png)

Ahora bien, con un mp3 lo que hace es quitar información que no es muy perceptible o relevante con respecto al demás contenido, pero a fin de cuentas el oido si lo puede escuchar. Es como si en un texto se eliminaran algunas letras, el cerebro es capaz e entender el mensaje. **Lo msmo psa con l mp3.**

Para que se queden con una idea más clara de cuanta información de pierde al escuchar un mp3 les dejo ésta imagen comparativa de diversos formatos así como dos links a videos.  

![Table](https://s3-us-west-1.amazonaws.com/publicssets/Screenshot_2016-11-19-15-27-21.png)

El primero es una especie de documental sobre el panorama en la industria de la música desde la perspectiva de la compresión.  
[Distortion of sound](https://www.youtube.com/watch?v=mDZcz-V29_M)

El otro es una charla de Andrew Scheps en google del 2013, igual sobre el tema de compresión.  
[Lost in Translation](https://www.youtube.com/watch?v=SXbH-yzGNfg&t=1s)