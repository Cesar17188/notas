# Conocer Flume

[Más información de Apache Flume](https://www.guru99.com/create-your-first-flume-program.html)  
Se puede comparar con Apache Kafka, por si les suena más conocido.

**Code**

```
git checkout 5_Conocer_Flume

cd 5_Conocer_Flume

cat -Dockerfile

docker build -t myflume .

docker run -it --rm  -p 9090:9090 myflume

hola mundo desde flume

curl -X POST -H 'Content-Type: application/json; charset=UTF-8' -d '[{"headers": {"header.key":"header.value"}, "body":"ha ingresado un nuevo estudiante"}]' localhost:9090
```