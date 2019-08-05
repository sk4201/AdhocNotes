# Linux
cat hello.txt
```
hello world this is file writer
hello world
my name is khan
```
tac hello.txt
```
my name is khan
hello world
hello world this is file writer
```
rev hello.txt

* reverse every letter in a word

qrencode => Make QRCodes
```
qrencode -s 16X16 -o adhoc.png https://www.adhocnw.org
```

## Docker
* It is a technology which provide us platform to do multiple type of things in a single platform in a system.
* Docker is a platform provider.
* We can use Docker to provide enviornment for website, Apps, Console application etc.
* Docker can be used to build hadoop platform.
* It is a platform which can run on any platform.
* Docker uses your base OS kernel to build new operating system, it means if you have windows as your base system on which docker is installed, then Windows NT kernel will be used to build new OS.

## Installation of Docker
import .repo of kubernetes from index of summer19 of adhoc for installation of Docker

```
rpm -q docker
systemctl status docker
systemctl enable docker
```

docker version
```
Client:
 Version:         1.13.1
 API version:     1.26
 Package version: docker-1.13.1-68.gitdded712.el7.centos.x86_64
 Go version:      go1.9.4
 Git commit:      dded712/1.13.1
 Built:           Tue Jul 17 18:34:48 2018
 OS/Arch:         linux/amd64

Server:
 Version:         1.13.1
 API version:     1.26 (minimum version 1.12)
 Package version: docker-1.13.1-68.gitdded712.el7.centos.x86_64
 Go version:      go1.9.4
 Git commit:      dded712/1.13.1
 Built:           Tue Jul 17 18:34:48 2018
 OS/Arch:         linux/amd64
 Experimental:    false
```

* Docker Image is needed for Docker.
```
hub.docker.com
```
For searching images in hub.docker.com
```
docker search java
```
For Pulling images
```
docker pull hello-world
docker pull python
docker pull fedora
```
```
docker images
```

* Docker container is created by the docker image.
* Redhat has a backend of Fedora
<!-- ### Docker & Container -->
 i= interactive, t= terminal
To build a OS from docker we have a command ```docker run```
```
docker run -it fedora
```
shows shutdown and running containers; a= all
```
docker ps -a
```
* Container is a running machine

shows only running containers
```
docker ps
```
To go to running container; admiring_euclid= Container name
```
docker attach admiring_euclid
```
For making user input container name; fedora= OS Name
```
docker run -it --name c1 fedora bash
```
For shifting container to background
```Ctrl+p q```
For starting a container from another container; c1= container name
```
docker start c1
```
exec= execute; c1= container name; difference is run command makes container and this only exceute it and shifting to another container with exiting present container
```
docker exec -it c1 bash
```
Revision:-
* pull
* image
* ps
* search
* run
* exec
* start
* stop

Remove all the images of containers
```
docker rmi DOCKER_IMAGE_
```
shows all the image id of containers
```
docker ps -qa
```
for removing all the containers at one time 
```
docker rm $(docker ps -qa)
```
made a Centos OS Container and then do ping
```
docker run -it centos:7 ping 8.8.8.8
```
shows the config info of container; elated_yonath= container name
```
docker inspect elated_yonath
```
searches ipadd word line and prints it
```
docker inspect elated_yonath | grep -i ipadd
```



