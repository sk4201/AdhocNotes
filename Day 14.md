Today's Topic:-
* nfs (Network File System):- It works on Linux Permissions

For showing the name of any file or folder by pressing tab as happens in Linux:-
```
 yum install bash-completion 
```
**Creating nfs Server for downloading and uploading files from another system:-**
```
yum install nfs-utils -y
```

```
systemctl status nfs-server

systemctl start nfs-server

systemctl enable nfs-server.service
```
For checking whether nfs-utils is installed in system or not; rpm= Redhat Packet Manager; q= query; nfs-utils= Package name; c= config files
```
rpm -q nfs-utils
rpm -qc nfs-utils
```

```vi /etc/exports``` ro= read only; /nfs= Shared folder name; rw= read write;

 no_root_squash : By default, any file request made by user root on the client machine is treated as by user nobody on the server. (Exactly which UID the request is mapped to depends on the UID of user “nobody” on the server, not the client.) If no_root_squash is selected, then root on the client machine will have the same level of access to the files on the system as root on the server.
```
/nfs    *(ro)
```
OR
```
/nfs *(rw,no_root_squash)
```
For exporting shared folder; updating the exports file/ Reload exports file
```
exportfs -r
```
### Client Instance Work:-
Tells what server is sharing; 13.232.229.182= Public IP

Shows the shared mounted folders
```
showmount -e
```
```
showmount -e 13.232.229.182

O/P:
Export list for 13.232.229.182:
/nfs *
```

```
mount 13.232.229.182:/nfs 
```
## References
* https://foxutech.com/how-to-install-and-configure-nfs

# **Python**


```getcode.py```
```
#!/usr/bin/python3
import requests # behave like a browser
# now connecting to a website

webdata=requests.get("https://www.google.com")
print(webdata)

O/P:
<Response [200]>
```

Already defined DNS in this path```/etc/resolv.conf``` in Linux
```
127.31.0.2
```

8.8.8.8 => WorldWide Available IP created by Google

HTTP Response Code => Gives code in response of request
* 404 => Website do not exist
* 505 => Server not available
* 302 => Redirect the URL to another URL
* 200 => Successfully Transfer of data

view-source:https://www.google.com => Shows the front end of Every webpage, in this google's front end

Module:
* os
* time
* sys
* subprocess
* webbrowser
* pyqrcode
* requests
* socket
* pyttsx3

```pyttsx3``` => Connect to the speakers/ sound driver of the system
```
import pyttsx3
>>> dir(pyttsx3)

['Engine', '__builtins__', '__cached__', '__doc__', '__file__', '__loader__', '__name__', '__package__', '__path__', '__spec__', '_activeEngines', 'd
river', 'engine', 'init', 'weakref']  
```

```
sudo yum install espeak
```

## **Databases**

Server:-
* MySQL
* Oracle
* MS
* Postgre
* DB2
* Aurora

Engine:-
* InwodB
* MyISAM
* CYS
* Blackhole

```
yum install mariadb-server
rpm -q mariadb-server
```
```
systemctl start mariadb
```
for starting the service with startup of the system
```
systemctl enable mariadb
```
```3306``` is PORT No. of MySQL Server / MariaDB

```/etc/services``` is the path where all the port no. are given and it is also available in windows at different path

For entering in the database:-
```
mysql
```
For printing:-
```
select "hello world";
```
```
select 45+5;
```
hash format of "hello world"
```
select password"hello world"

O/P:
+-------------------------------------------+
| password("hello world")                   |
+-------------------------------------------+
| *67BECF85308ACF0261750DA1075681EE5C412F05 |
+-------------------------------------------+
1 row in set (0.00 sec)
```
but it cannot be reversed

For seeing databases:-
```
show databases;

O/P:
+--------------------+
| Database           |
+--------------------+
| information_schema |
| mysql              |
| performance_schema |
| test               |
+--------------------+
4 rows in set (0.00 sec) 
```

for creating databases:-
```
create database adhoc;
```

```/var/lib/mysql``` is the path of all the databses in mysql
* var means vary which includes 

for entering into a databases( works like ```cd``` command in Linux or Windows):-
```
use adhoc;

O/P:
Database changed
MariaDB [adhoc]>
```
for seeing the tables or data in the databases( an excel file alike include rows and columns):-
```
show tables;
```

for seeing everything what's in the table:-
```
select * from user;
```

for exiting the mysql database:-
```
exit;
```

How to secure mysql (It takes new password for accessing mysql):-
```
mysql_secure_installation
```

```
mysql -u root -p
```
For access without password, there is a little hack we can do:-
```
mysqld_safe --skip-grant-tables &
```

