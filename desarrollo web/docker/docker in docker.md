# Docker-in-Docker
![[Pasted image 20210627010233.png]]

Comandos:  
$ docker run -it --rm -v /var/run/docker.sock:/var/run/docker.sock docker:19.03.12  
$ docker run --rm -it -v /var/run/docker.sock:/var/run/docker.sock -v $(wich docker):/bin/docker wagoodman/dive:latest prodapp