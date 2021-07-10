# Importación de los datos para el proyecto

Es un proceso simple, sin embargo, para iniciar es necesario que cumplas con dos dependencias:

-   La primera es haber instalado PostgreSQL y su set de herramientas en tu Sistema Operativo.
    
-   La segunda es haber instalado PgAdmin 4 para que puedas interactuar de manera gráfica con la base de datos.
    
-   Asegúrate de que el usuario postgresql se encuentra configurado y con todos los permisos.
    

Para conocer los detalles de la instalación de las anteriores dependencias, por favor visita el Curso de PostgreSQL donde es abordado a detalle. En este tutorial de importación asumimos que se encuentra correctamente configurado.

## Paso 1: ingresa a PgAdmin

![](https://lh3.googleusercontent.com/KVxuBdqMwgf1KHXjrAlLRdBchL65GjlvIe8OhDZMkVu5LNtuZxIMURKCtLRdhSo_CWpvKa_T-aB08RBlWBvTFAygXmAolXXPB9VukpZrvaMngw4u4rxJzKq_aEFBLbJT0oIPgMkK)

## Paso 2: Crea la base de datos

Selecciona el elemento Databases del menú izquierdo, da click derecho y selecciona la opción Create > Database.

![](https://lh6.googleusercontent.com/QEkoVtyI95jWYpGPjdFWEP9cXCJQE4w9-gL2C_w385akD8h24RV1FRHozDnF4kAi7zjZpZCbBmVhGs3bnJ4m7aOXlbsIzI7LZs-4-pF6gkmoycabpduDGymt_M7NbK_hVkJ3pW2F)

En el campo Database escribe el nombre “platzimovies” y en el campo owner selecciona el usuario que será dueño de la base de datos.

![](https://lh3.googleusercontent.com/aeZPQ_s7r9kccSDmbKJBno7lhZmgp4dzOoiEBB6-dKPAj1InG7ZWwZq--9b5DByE0H8koq_bkQlPYdsyhu1KXmmwnLIeMEg9lBIGuZlrgs7O_IVdejYlmH0kYJRJDnbt3-EDlvaU)

Da click en el botón Save. Y posteriormente selecciona la base de datos recién creada en el menú derecho.

![](https://lh3.googleusercontent.com/XE_AhN2ce9I9ojycWYoonzxgWYyysxqJkT3NrrvWKicZee7_BrIyAY0r6XbSBPrqWxN-rmlBy0Ha9qC9cUlRQMkl08U4RrSGSLKQPVjUZofUwrIJ_qoRkN2BKC68VxBrreD7yZ8d)

Paso 3: Configura la restauración

Dirígete al menú Tools (Herramientas) y da click en la opción Restore (Restaurar).

![](https://lh4.googleusercontent.com/ZOnGI928dRqdpdbRvluuJQXdY5Sq1g6wLWMb7o_zaNETMkBwCU6sTMZzbx8d8McHEnbrIZ3JmeaqtXt-y28y_PiF3FqBuQg1ikL7kF-ZxRShwz3o0RYjKABa0StGQDKJjXZMea9u)

![](https://lh3.googleusercontent.com/a1eSRruEt-DFoqk4lIye4DIlIvBk70QQ4jkrtJYFB-WOwMtlpqYkmbRCuS6ax8b1JHWadeFY8pxcvgGl-_DB5XYIoXxpjL9UEaetUi89ct6g6wA73iYdPr-DgQumx2ByzTsKrTpn)

## Paso 3: Importa desde archivo

Selecciona la opción Custom or tar en el campo Format. En Role name elige el usuario con permisos root, normalmente es el usuario postgres o el nombre de usuario de tu computadora.

Finalmente, en el campo Filename selecciona el botón de 3 puntos y selecciona el archivo que deberás descargar haciendo click [aquí](https://drive.google.com/open?id=1oE7A4z_D2o-udn_yflwZ03uN3cA0gVpr)

Da click en el botón Restore.

![](https://lh5.googleusercontent.com/6TBLwWen71YXTyd4w3rxzoJdLym2mF7tR_kRgtH1Usd38cNvpmf0h6_LzsNRCK2mJHYNdRDcpBdfQ13GUfZEJdyU1oU3TZy5OmP6qBeAC4vddgX_NRhh6wfFsJGDa_IHvQG28f2d)

Al ejecutar la restauración encontrarás un mensaje similar al siguiente:

![](https://lh6.googleusercontent.com/jd6iTRhNtOt1XMU9gDiuBUbOd3siZnyMYmiIioKHx-Fnh6nQwY-wt6-MVkpJhQHzYD5zBmdmVndvPHxZ3fBHGQ1KbLQwzv40TiIrG_VVELFBPlF0bubRCl6OuAb8_OQouW06HsU8)

## Paso 4: Verifica que las tablas fueron creadas

Yendo al menú izquierdo, dirígete a Servers > Local > Databases > platzimovies > Schemas > public > Tables.

Verifica que ahí aparecen todas las tablas que necesitamos para el ejercicio.

![](https://lh3.googleusercontent.com/6XdRHkZDp6gQ_fJXKHT6bMfn5pX8_ms8gt3DzaXjMK-QVvL1jfqxBnFIahs79QbPQwwzPQWnfc52B8dpsp-uZ-xBLo9WkXHUXfI6cJq5tGep5i24a0uFptSTClyYOGvx1T0LybHM)

Si lo lograste, ¡felicidades! Estás listo para usar nuestra base de datos de ejemplo.