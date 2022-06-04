# ¿Cuándo utilizar Network en DevTools?

El panel Network es utilizado para asegurarse de que los recursos se descarguen o carguen como se esperaba.

Los casos de uso más comunes para el panel Network son:

-   Asegurarse de que los recursos se estén cargando o descargando.
-   Inspeccionar las propiedades de un recurso individual, como sus encabezados HTTP, contenido, tamaño, etc.  
    
    ![log.png](https://static.platzi.com/media/user_upload/log-df5a3df0-2d41-498a-b022-48842945685a.jpg)  
    **By: [https://cutt.ly/1tDPeQc](https://cutt.ly/1tDPeQc)**

El panel de network, nos **permite evaluar si los archivos fueron descargados o no** una vez que se carga una página web, estos pueden ser: HTML, imágenes, CSS, JS, entre otros. Cada uno demora cierto tiempo dependiendo de su peso y la velocidad de conexion de internet.

**Secciones de Network**:

1.  **Name**: Nombre del archivo
2.  **Status**: Estatus del http. En este caso 200 significa OK (Todo bien)
3.  **Type**: Tipo de archivo. Por ejemplo: document (html), stylesheet(css), js, png, etc…
4.  **Inialitator**: Cuál archivo solicitó a otro archivo. En este caso, el documento html solicitó a todos los demás archivos.
5.  **Size**: Tamaño del archivo. Se muestra el tamaño no optimizado y optimizado por el navegador.
6.  **Time**: Tiempo total que tarda en descargarse el archivo.
7.  **Waterfall**: Tiempo (sección por sección) que le tomó al archivo descargarse.