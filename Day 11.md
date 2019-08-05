### **Today's Topic:-**

* How to create a docker image

By using ```DockerFile ``` we can create a Docker Image.

Apache Web Server  -> Docker Image


* Container does not support ```systemctl```
* Container read everything from Kernel of base OS except 
```systemctl``` (In Linux = ```systemd```)

**Process Tree** in which every running process is listed in tree structure and first process is ```systemd```
```
pstree 
```

Steps to Create your own image :-

* first of all make a file which you want to insert in image

**Dockerfile**
```
FROM fedora                          
#  Sequence wise 
#  this is base image where  we want some changes   
#  FROM check images in local system if not present then pull it from docker hub                                     
MAINTAINER namanjain300@gmail.com                   
# [optional] Info about image creater               
RUN  yum install httpd -y                           
# RUN -> launch a container and do the changes      
COPY index.html /var/www/html                       
# this path is for hosting; source base os -> container
EXPOSE 80                                              
#  EXPOSE is used for telling port no.
#  we want to use HTTP=80(Port no.) Protocol inside container    
ENTRYPOINT httpd -DFOREGROUND                                    
#  by default process of container                               
#  altenative way of starting httpd service instead of systemctl  
```                       
**Creating Image**; t= image name
```
docker build -t "adhocweb" /myweb
```
```ENTRYPOINT``` cannot be replaced by anything else but ```CMD``` can be replaced
```
CMD httpd -DFOREGROUND
```
For replacing the Starting point to anything else just like bash in this example so replace ```ENTRYPOINT``` with ```CMD``` 
```
docker run -it fedora bash
```
for running container in background without logging in; d= detach; cc= container name
```
docker run -itd --name cc fedora bash
```
for stoping a container; c1 = container name
```
docker stop c1
```
for removing all the containers at once
```
docker rm $(docker ps -qa)
```
* SSH is combination of IP with 22 PORT NO.
---
## **Port Forwarding:-**

1234=> a blank port 
```
docker run -itd --name web1 -p 1234:80 adhocweb
```
---
For creating 50 containers at one time by python:-

```py
#!usr/bin/python3
import os
for i in range(50):
    os.system('docker run -itd fedora bash')
```
---
## **Industry 4.0**
* DevOps
* Blockchain
* AI/Data Science

### **DevOps**
* It is not a technology, it is a culture
* Combination of Developer(Technical) and Operations(Non Technical)
* Programming language back propagation

Main topics:
* Automation
* CI | CD
* Container (Docker)
* Microservices

#### **Automation:-**

* IAC (Infrastructure as a Code)
* ```Terraform``` is famous for automating work of clouds wheather it is AWS, Azure, Google cloud
* ```Ansible``` is used to automate Desktop Operations specially Linux

---
## Python 2

* Socket(UDP Protocol) - IP and PORT no.