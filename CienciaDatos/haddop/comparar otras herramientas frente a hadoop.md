# Comparar otras herramientas frente a hadoop

Consola 1

```
git checkout 2_Comparar_otras_herramientas_frente_a_Hadoop
docker network create -d bridge hadoopNet
docker run -p 9200:9200 -p 9300:9300 --net=hadoopNet --name elasticsearch -e "discovery.type=single-node" docker.elastic.co/elasticsearch/elasticsearch:7.6.2
```

Consola 2

```
cd curso-hadoop-platzi/2_comparar_otras_herramientas_frente_a_Hadoop
docker run -it --rm --net=hadoopNet --name logstash -v "$PWD/pipeline":/app --entrypoint bash docker.elastic.co/logstash:7.6.2
logstash -f /app/logstash.conf
platzi comparando herramientas de hadoop con elasticstack
```

Consola 3

```
cd curso-hadoop-platzi/2_comparar_otras_herramientas_frente_a_Hadoop
docker run -rm --name kibana --net=hadoopNet -p 5601:5601 kibana:7.6.2
```

Consola 4

```
cd curso-hadoop-platzi/2_comparar_otras_herramientas_frente_a_Hadoop
docker ps
docker inspect hadoopNet
clear
curl http://localhost:9200/_search\?pretty\&size\=1000
```