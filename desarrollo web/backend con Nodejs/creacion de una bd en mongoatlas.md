# Creación de una BD en MongoAtlas

En este modulo aprenderemos como podemos conectarnos a servicios externos en Express.js gracias a la arquitectura que implementamos donde tenemos nuestras rutas, nuestros servicios y librerías, podemos conectarnos a cualquier servicio o cualquier base de datos externa de una manera muy sencilla.

En está ocación vamos a usar Mongo Atlas para conectarnos a una instancia de MongoDB, **mongodb es un sistema de base de datos no relacional**, los llamados **NO-SQL _not only sql_**.

Para esta ocación vamos a hacer uso de nuestras variables de entorno, de está manera **por cada enviroment**, **vamos a usar diferentes configuraciones**, es decir en desarrollo vamos a conectarnos a una instancia o podríamos fácilmente conectarnos a una instancia local, en staging el enviroment de pruebas, o en producción deberíamos usar diferentes bases de datos.

La uri de **mongodb** tiene está estructura.
![[Pasted image 20210901171711.png]]

Donde necesita el

-   **usuario de base de datos**
-   **el host**
-   **el nombre de la base de datos**

Todo esto lo vamos a representar en variables de entorno para que a la hora de cambiar de ambiente, sea muy fácil de remplazarlo, te voy a mostrar como podemos conectarnos en el código.

1.  Crear una cuenta en [Mongo Atlas](https://www.mongodb.com/cloud/atlas)
2.  Podemos hacer click en **start free** o **try free**, ambos nos llevan al mismo formulario para crear nuestra instancia gratuita.
3.  Vamos a llenar el formulario con: email, nombre y apellido, para el password recomendamos un administrador de contraseñas y recomendamos [lastpast](https://www.lastpass.com/)
4.  Nos pide aceptar terminos y condiciones
5.  Podemos elegir cualquier provedor entre: **Amazon web services, google cloud o Azure**
6.  En este caso eligiremos **Amazon**
7.  Despues nos inidica cuales de las regiones tienen la disponibilidad de crear una instancia gratuita, vamos a dejar la que tiene por defecto.
8.  Despues nos muestra una configuración que tiene por defecto y podemos simplemente darle en create cluster.

Mientras que mongodb crea el cluster podemos revisar ciertas configuraciones como por ejemplo: el Network Access, Mongo Atlas limita el acceso a las bases de datos. Lo que se debe hacer cuando estemos en producción es determinar cual es la ip de la máquina que esta en producción para que solo esa IP tenga acceso a nuestra bases de datos, como en está ocación estamos hablando de desarrollo, nosotros vamos a permitir que cualquier IP se conecte a nuestra base de datos.

Permitir que se conecte cualquier IP no es tan grave porque de todas maneras necesitamos el usuario y contraseña, pero es muy buena práctica restringir las conexiones por IP.

Vamos a configurar el **Network Access** y vamos a indicarle que nos deje acceder desde cualquier parte, confirmamos y el crea el registro.

Otra cosa que debemos hacer si nuestra base de datos ya está lista, es crear un usuario en Database Access, en está ocación vamos a elegir a un usuario que solo puede leer y escribir en nuestra base de datos

Ejemplo de user:

`db_user_platzivideos`

`6Poyn0l6TnOw`

Finalmente vamos a revizar si el cluster se está creando, normalmente toma un tiempo porque lo interesante de mongodb atlas a diferencia de otros servicios, es que el crea unas replicas, un cluster se compone de 3 instancias de mongodb, estó hace qu tengamos alta disponibilidad a diferencia de otros servicios, entonces vamos a esperar un momento a que termine de crear nuestra instancia de mongo.

Una vez creada debemos tomar los datos de conexión, para esto le damos en **connect** en cualquiera de las opciones nos proporciona la uri que debemos usar, que es muy similar a la imagen que mostramos con aterioridad. Lo único que nos falta para complementar nuestra uri es la base de datos.

Para esto nos vamos a **collecctions**, en el nos dice las bases de datos que tenemos en esté caso son 0, y lo que le vamos a decir es **Add my own data**, en el podemos dar un nombre a la base de datos, en esté caso la vamos a llamar _platzivideos_db_ y el nombre de la colleccion va a ser _Movies_, la creamos y estamos listos para poder ingresar nuestra uri en el código.