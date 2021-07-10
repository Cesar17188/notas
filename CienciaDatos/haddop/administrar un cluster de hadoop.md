# Administrar un clúster de Hadoop

Cloudera es un ecosistema que se basa en Hadoop y te permite instalar/administrar muchas herramientas de Hadoop.  
Es decir, tú puedes instalar Hadoop como en las primeras clases, instalar Hive, Impala, etc, de forma individual y tendrías que configurar la conexión/interacción entre componentes de forma manual y en cada nodo del clúster. Cloudera te permite instalar todas estas herramientas, interactuar entre las mismas de una forma sencilla y administrarlas de forma muy sencilla, incluso realizar configuraciones y se aplican a todos los nodos que conforman tu clúster.  
Puedes realizar gran cantidad de tareas con un ecosistema hadoop; el ejemplo de estas clases es analizar texto, por ejemplo un conteo de palabras, pero lo más común es crear pipelines y/o ETL’s, es decir, procesos complejos en donde lees y procesas información.  
Ejemplo muy sencillo de pipeline en ecosistema Hadoop con Cloudera:

1.  Importas un histórico de información de tu compañía de una BD Oracle con Sqoop a tu HDFS en formato parquet
2.  Obtienes ciertas métricas anuales procesando dicha información con Spark y las guardas en parquets de salida
3.  Visualizas los resultados en Impala a partir de los parquets generados en el paso anterior.

**Code**

```
git checkout 4_Desarrollar_un_cluster_de_hadoop

cd 4_Desarrollar_un_cluster_de_hadoop

docker run --hostname=quickstart.cloudera --privileged=true -it -v $PWD:/src --publish-all=true -p 8888:8888 -p 8080:80 -p 7180:7180 -p 3106:3106 cloudera/quickstart /usr/bin/docker-quickstart

service hive-metastore start

sudo service hive-server2 restart
```

localhost:7180