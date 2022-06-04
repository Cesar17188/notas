# Qué es la memoria RAM y cómo funcionan los discos duros
![[Pasted image 20220110121105.png]]

Un **disco duro** (del inglés hard drive) es una pieza de hardware que almacena datos en un disco. El usuario puede acceder a estos datos para leer y escribir archivos.

## Cómo funciona un disco duro

En generaciones anteriores, un disco duro contenía un brazo mecánico, que se utilizaba para leer y escribir los datos en un disco de metal mientras este se encuentra girando, algo similar a los antiguos discos de vinilo. Cuando el brazo lee o escribe información, necesita moverse para acceder a las diferentes partes del disco.

Actualmente, existe una serie de nuevos discos, llamados de estado sólido (Solid State Drive) que ya no utilizan ningún tipo de brazo o disco giratorio y cuyo funcionamiento se asimila más al de la memoria RAM, sin que la información se pierda al apagar el equipo. Esto permite que la velocidad de lectura y escritura sea extremadamente rápida y el tiempo de vida útil del disco se extienda por no tener piezas móviles que puedan dañarse.

## Discos duros y memoria RAM

Los discos duros tradicionales son relativamente lentos porque deben posicionarse donde está el archivo almacenado y esto puede implicar que el brazo mecánico que mueve el cabezal se tome mucho tiempo en encontrar todos los _pedazos_ del archivo.

La memoria RAM es más rápida, ya que puede acceder a los datos almacenados de manera instantánea. La diferencia está en que los discos duros no son volátiles: guardan la información de manera persistente aunque se les quite el suministro de energía. La información de la memoria RAM, en cambio, se elimina en el momento en el que el computador se apaga.

Además, almacenan los archivos de manera secuencial: para almacenar un archivo, este se parte en varios pedacitos y se guarda la posición de cada uno de ellos, además de su ubicación, en el disco para poder leerlos secuencialmente.

## Sistemas de archivos de un disco

Para poder almacenar los archivos de forma adecuada, un disco duro necesita un sistema de archivos. Los sistemas de archivos son convenciones internas de los sistemas operativos para poder acceder a los archivos almacenados.

-   En Linux existe ext3 o ext4.
-   En Windows existía FAT16 o FAT32 (File Allocation Table), que fue reemplazado por NTFS (New Technology File System).
-   En Mac OSX el sistema de archivos se llamaba HFS (Hierarchical File System) pero ahora se llama AFS (Apple File System) en macOS Sierra.

Cuando abrimos un archivo, la CPU (Unidad Central de Procesamiento) se lo pide al disco duro y luego lo lleva a la memoria RAM para leerlo.

## Cómo funciona la memoria RAM

En la RAM están almacenados, de manera temporal, todos los programas y archivos que están en ejecución al momento de usar el computador. Si abrimos un archivo con el Bloc de Notas, por ejemplo, ambos deben estar cargados en la RAM. El CPU puede acceder a la memoria RAM a través de un índice compartido, es decir, un índice que indica en qué posiciones de memoria se encuentran qué partes de un archivo o proceso.

Los datos viajan a través de un conjunto de cables paralelos llamado bus de datos, que comunica la CPU con el disco duro y la RAM para permitir la transferencia de datos.


**Discos duros:**

-   Forma en que organizan datos:
    
    -   Persistente
    -   Secuencial
    -   Estructurada (Depende del sistema de archivos, que a su vez depende del S.O. que esté en el disco duro):
        -   Windows: FAT16 - FAT32, NTFS
        -   Linux: Ext3 - Ext4
        -   Mac OS: HFS, APFS
-   Forma de localizar y leer archivos:  
    En la parte superior de los Discos Duros existe una cabecera, la cual guarda el indice de todos los archivos, esto permite que en el momento de lectura desde la cabecera, se conozca en dónde está ubicado el archivo en cuestión.
    
-   Borrado de archivos:  
    Por tal motivo, cuando se “borra” un archivo, lo que realmente se esta haciendo es eliminando el indice en la cabecera que está relacionado con el archivo. Determinados tipos de software permiten la recuperación de estos archivos, leyendo detalladamente toodo el disco duro. Sin embargo algunas practicas de borrado (Sheredder) permiten borrar el archivo por completo, incluso ejecutando el borrado determinado número de repeticiones, lo que imposibilita el trabajo de forenses para la recuperación de datos o archivos.
    

**Memoria RAM (Random access memory)**

-   Procesos:  
    La memoria RAM, siendo tan rápida, tiene la capacidad de ejecutar varios procesos paralelamente. El SO es uno de esos procesos ejecutados por la RAM. Sin embargo la opciones que nos ofrece el SO son muchas y no siempre se utilizan todas, por lo tanto la RAM solo carga aquellas tareas que realmente necesitamos y estamos usando frecuentemente.
    
-   Localización de procesos:  
    A diferencia de los discos duros, la memoria RAM hace uso de un indice compartido con la CPU que es ultra veloz. Esto facilita y permite una localización de los procesos por parte de la CPU de una manera increíblemente rápida.
    

**CPU (Central process unit):**

-   Dentro de este asombroso chip, no encontramos con un espacio que recibe por nombre Memoria Caché. En ella se guardan y almacenan cierto tipo de datos de uso frecuente, para que sea más fácil y rápido el acceso a ellos. Por ejemplo una parte del SO siempre estará almacenada en la Memoria Caché para que sea rápido acceder a él.
    
-   Comunicación:
    
    -   Ram:  
        Para lograr la efectiva comunicación entre la CPU y la RAM existe lo que se conoce como un bus de datos o bridge (puente). Un bus de datos en algunas ocaciones es un cable delgado y ancho. En otros casos esta conexión está establecida como circuito en la placa madre (mother board).
    -   Disco Duro:  
        Para la conexión entre en disco duro y la CPU, el bus de datos recibió inicialmente el nombre ATA, que en una versión posterior se llamó SATA. Hay otro tipo de bus de datos para el disco duro mejor que SATA, que se llamó IDG.