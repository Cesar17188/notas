# Conexión con Robot3T y MongoDB Compass a una BD

**Robo 3T** y **MongoDB Compass** son dos clientes con interfaz gráfica que nos permiten conectarnos a nuestras instancias de Mongo DB y manipularlas de una manera más fácil. Con ambos clientes nos podemos conectar a una instancia de cualquier servidor, inclusive a una instancia de MongoDB Atlas.

Para descargarlos se pueden usar los siguientes enlaces respectivamente:

-   [https://robomongo.org/download](https://robomongo.org/download)
-   [https://www.mongodb.com/download-center/compass](https://www.mongodb.com/download-center/compass)

## Conexión usando MongoDB Compass

Si nosotros copiamos el Mongo URI desde Mongo Atlas podemos conectarnos fácilmente con MongoDB Compass:

1.  Iniciamos sesión en MongoDB Atlas [https://www.mongodb.com/cloud/atlas](https://www.mongodb.com/cloud/atlas)
2.  Nos vamos a la sección de **Clusters** en el menú lateral izquierdo.
3.  Seleccionamos **connect** en nuestro cluster sandbox.
4.  Seleccionamos la opción **Connect with MongoDB Compass**.
5.  Si no tenemos MongoDB Compass instalado, podemos descargarlo desde allí. Si ya lo tienes instalado continua con el paso 6.
6.  Le damos clic en el botón **copy** para copiar el Mongo URI.
7.  Abrimos **MongoDB Compass** e inmediatamente va a reconocer nuestra URI que tenemos en el portapapeles.
8.  Hacemos clic en **yes** para que nos cree una nueva conexión, pero es necesario introducir el **password** del usuario de la base de datos.
9.  Podemos ponerle un nombre favorito y darle en **Create favorite** y luego en **Connect**.

![mongodb-compass.png](https://static.platzi.com/media/user_upload/mongodb-compass-17619c01-4409-4039-984b-d46e05e7ff47.jpg)

## Conexión usando Robo 3T

Para poder conectarnos a MongoDB Atlas haciendo uso de Robo 3T, necesitamos copiar el Mongo URI:

1.  Iniciamos sesión en MongoDB Atlas [https://www.mongodb.com/cloud/atlas](https://www.mongodb.com/cloud/atlas)
2.  Nos vamos a la sección de **Clusters** en el menu lateral izquierdo.
3.  Seleccionamos **connect** en nuestro cluster sandbox.
4.  Seleccionamos la opción **Connect with MongoDB Compass**.
5.  Si no tenemos MongoDB Compass instalado, podemos descargarlo desde alli. Si ya lo tienes instalado continua con el paso 6.
6.  Le damos clic en el botón **copy** para copiar el Mongo URI.
7.  Abrimos **Robo 3T** y hacemos clic arriba en la parte izquierda en el link de **create**.
8.  En la parte de abajo hay un input donde pegaremos el Mongo URI y hacemos clic en **From SRV**
9.  Le cambiamos el nombre a nuestra conexión en **Name** por el que consideres más conveniente.
10.  Nos vamos a la pestaña de **Authentication** y actualizamos el **password** por el password correcto del usuario.
11.  Hacemos clic en **test** en la parte inferior izquierda para probar que todo esta OK, y luego podemos hacer clic en **save** y **connect**.

![robo-3t.png](https://static.platzi.com/media/user_upload/robo-3t-6e1979a3-698b-4a9c-95fb-b30de530b4c3.jpg)