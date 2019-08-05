# Amazon S3

---
# CentOS
rsync= checks all the info in two directories and update if there is any change 
sync a folder or a file with another directory; a= exactly all the file, v= verbose
```
rsync -avz /home/ /mnt
```

```/etc/fstab```

```
xfs noexec,defaults 0 0
```


shows the logs in ```var/log/secure```


s= source; g= file path
```
sed -i 's/SELINUX=enforcing/SELINUX=disabled/g' /etc/selinux/config
```
Set timezone to Asia-Kolkata
```
timedatectl set-timezone Asia/Kolkata
```

Bind Mariadb Server with loopback IP or localhost or lo or 127.0.0.1 ```vi /etc/my.cnf.d/server.cnf``` or ```vi /etc/my.cnf```

edit it
```
bind-address=127.0.0.1
```

# REDHAT

Changes in ```cat /etc/sysconfig/network-scripts/ifcfg-ens3``` [ens3=ETHERNET] for making dhcp address to static address
```
BOOTPROTO
ONBOOT YES
IPADDR
```


---

# **Topics for RHCSA EXAM/ Redhat Exam:-**

* Shell
* IO Redirection
* Archieve(TAR) and Compression
* NTP Client
* Partition
* LVM
* User Management and Group Management
* Permissions
* Stratis
* VDO(Virtual Disk Optimiser)
* Tuning
* Yum and RPM
* Password Break
* IP Static
* Crontab