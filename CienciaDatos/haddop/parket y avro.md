# Conocer Parquet y Avro

Agregar OCR, y más detalle de cada formato; esto es indispensable en el mundo de Big Data:  
[Más información](https://oswinrh.medium.com/parquet-avro-or-orc-47b4802b4bcb)

Code

consola 1

```git

cd 5_Conocer_Parquet_y_Avro

cd dbs_hadoop

rm -f user_data.tsv.gz

docker-compose up
```

consola 2

```cd

docker run hostname=quickstart.cloudera --privileged=true -it -v $PWD:/src --publish-all=true -p -8888:8888 -p 8080:80 -p 7180:7180 cloudera/quickstart /usr/bin/docker-quickstart

ls src

cd src

gzip user_sta.tsv

hdfs dfs -put *.gz /user/cloudera/raw_data/

hdfs dfs -ls *.gz /user/cloudera/raw_data/
```

Consola 3

```
cd curso-hadoop-platzi/5_Conocer_Parquet_y_Avro

docker ps

docker inspect mysql_db

mysql --host=172.20.0.2 --user=root --password=rootpwd -e "select * from db_name.user_details" -B > user_data.tsv

ls -al
```