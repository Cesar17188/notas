# Conocer Sqoop e integrar Hbase

**Code**

```
docker run --hostname=quickstart.cloudera --privileged=true -it -v $PWD:/src --publish-all-true -p 8888:8888 -p 8080:80 -p 7180:7180 -p 3306:3306 cloudera/quickstart /usr/bin/docker-quickstart

hbase shell

create 'newtbl', 'knowledge'

list

describe 'newtbl'

status 'summary'

put 'newtbl', 'r1','knowledge:book','Alicia en el pais de las maravillas'

put 'newtbl', 'r2', 'knowledge:book','Odisea' 

scan 'newtbl'
```

localhost:8080