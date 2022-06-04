# GPUs, tarjetas de video y sonido

![[Pasted image 20220122165100.png]]

Sabemos cómo los archivos se cargan en memoria pero ¿Cómo veo en pantalla que el archivo se ha abierto?

Esto se logra gracias a la Graphic Processing Unit o GPU.

La CPU puede ejecutar cualquier proceso, incluido el dibujado en pantalla de ciertos datos. Pero no es ella quien se encarga, sino la GPU: **tarjetas especialmente fabricadas para realizar estas tareas**.

La comunicación entre la CPU y la GPU se realiza actualmente a través de un socket llamado PCI-Express.

Estas placas de vídeo tienen sus propias unidades o núcleos de procesamiento y su propia memoria RAM.

Lo que sucede es que la GPU divide la pantalla en una matriz y cada núcleo se encarga de dibujar una parte de esa matriz, para lograr una mejor performance.

Esto es mucho más rápido de lo que podría lograr la CPU sola ya que debería dibujar pixel por pixel ella sola.

En este corto video los cazadores de mitos hicieron un versus entre el poder de una CPU y una GPU para hacer multiples tareas, es divertido de ver 😃 [https://www.youtube.com/watch?v=-P28LKWTzrI](https://www.youtube.com/watch?v=-P28LKWTzrI)

La GPU (Graphic processing unit) está conectada a la CPU para que represente datos, especialmente relacionados a imágenes y video ya que en estas tareas es muy eficiente. Se conecta de dos maneras

1.  De manera integrada, cuando está en la computadora (integrada) y tendrá un chip pequeño para procesar video
2.  De manera aparte, se concretará mediante un bridge o un puerto llamado PCI express que es el socket entre la CPU y GPU.  
    Tiene varios factores  
    • Giga Hertz (velocidad) Que es menor al que tiene la CPU  
    • Cores (núcleos) Tiene muchos más Cores que la CPU  
    • VRAM (RAM de video)  
    La GPU convierte la pantalla (imagen, video, etc.) en una matriz de múltiples opciones y la divide en segmentos que la asignará a los diversos núcleos y habla con el software de la memoria RAM (concetada por bridges) para preguntar cómo quiere representar los datos. Algunas veces viene con operaciones 3D, códecs, etc. para hacer más veloz el procesamiento gráfico.  
    La CPU iría pixel por pixel