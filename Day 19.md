## HDFS Cluster Setup

Hadoop PORT NO. - ```50070``` [TCP]

Data Node PORT NO. - ```50010``` [TCP]

Block Size :- Chunks where data is divided
By Default Hadoop v2 have 128MB and Hadoop v1 have 64MB and it is changeable

for checking what files are there in ```/```
```
hdfs dfs -ls /
```
```
hdfs dfs -mkdir /google
hdfs dfs -ls /
```

```
yes "hello world this is me" > data.txt
```
for uploading
```
hdfs dfs -put data.txt /google
```

# Ashu Sir Notes

```
Note:  all operation must be  performed by  user  ec2-user 
step1  :  launch  3  ec2-instances 
           1 instace - 2GB  --NN --Elastic  IP --static/fix IP --rhel7.5
           2  instance  -- 1 GB   --DN

---------------------

step 2 : install   jdk in  all the nodes and  set  java path
##########
 3  sudo   yum  install  wget  -y
    4  ls
    5  wget  http://monalisa.cern.ch/MONALISA/download/java/jdk-8-linux-x64.rpm
    6  ls
    7  sudo  rpm  -ivh   jdk-8-linux-x64.rpm 
    8  rpm  -ql  jdk
    9  vi   .bashrc 
########################

step 3 :   download and install hadoop2.7  in all the node  
=================
15  wget  http://13.234.66.67/summer19/bigdata/hadoop-2.7.3.tar.gz
   16  history 
   17  ls
   18  tar  -xvzf  hadoop-2.7.3.tar.gz 
   19  ls
   20  mv  hadoop-2.7.3  hadoop2
   21  ls
   22  vi  .bashrc 
   23  source  .bashrc  
===  cat  /home/ec2-user/.bashrc ========
JAVA_HOME=/usr/java/jdk1.8.0
HADOOP_HOME=/home/ec2-user/hadoop2
PATH=$JAVA_HOME/bin:$HADOOP_HOME/bin:$HADOOP_HOME/sbin:$PATH
export PATH

###################

step  4 :   setup  Namenode  first  
 28  sudo  hostnamectl  set-hostname   ec2-3-90-19-144.compute-1.amazonaws.com
   29  ifconfig 
   30  sudo  vi  /etc/hosts
   31  hostname
   32  ls
   33  cd   hadoop2 /
   34  ls
   35  cd  etc/
   36  ls
   37  cd  hadoop/
   38  ls
   39  echo  $JAVA_HOME
   40  vi hadoop-env.sh 
   41  vi  hdfs-site.xml   
   42  vi   core-site.xml 
   43  hostname
   44  vi   core-site.xml 
   45  history 
   46  ls
   47  cd  /home/ec-user
   48  cd  /home/ec2-user
   49  ls
   50  hdfs  namenode -format   
   51  hadoop-daemon.sh  start  namenode
   52  jps

##############   cat   /etc/hosts ############
172.31.39.188   ec2-3-90-19-144.compute-1.amazonaws.com

Step 5:   setup   all datanode   : 
##################################################
  15  cd  hadoop2/etc/hadoop/
   16  ls
   17  echo   $JAVA_HOME
   18  vi  hadoop-env.sh 
   19  vi hdfs-site.xml 
   20  vi  core-site.xml 
   21  cd
   22  sudo  hostnamectl   set-hostname   ec2-3-86-15-93.compute-1.amazonaws.com
   23  ifconfig 
   24  jps
   25  hadoop-daemon.sh  start  datanode
#####################################################

NOte:  allow   firewall  TCP port  50070 &  9000  in  namenode  
       allow  firewall TCP port  50010  in  all datanode 

```
---

# **RedHat**

For showing the UUID of any disk as this shows the UUID of ```/dev/sda1```
```
lsblk --output=uuid /dev/sda1
```
