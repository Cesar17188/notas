# Generando archivos tipo Parquet

Un par de temas muy comunes en Big Data.  
[Impala vs Hive](https://www.dezyre.com/article/impala-vs-hive-difference-between-sql-on-hadoop-components/180)  
[Tablas externas e internas en Hive](https://data-flair.training/blogs/hive-internal-tables-vs-external-tables/)

**Code**

```
CREATE TABLE mysql_master.users STORED AS PARQUET
LOCATION '/USER/cloudera/user data.tsv.gz'
TBLPROPERTIES ('PARQUER.COMPRESS'='SNAPPY')
AS SELECT * FROM mysql_raw.users_tsv;
```