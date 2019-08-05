# **Ansible**
* For Ansible, Linux machine is required

Inventory:- 
* Static
* Dynamic


Localhost user is used through ansible and ping command is used; -m= module include which is ```ping``` here
```
 ansible localhost -m ping

 O/P:-
 localhost | SUCCESS => {
    "changed": false,
    "ping": "pong"
}
```
```
ansible all -m ping -u ec2-user
```
File module; -a= for argument pass
```
ansible localhost -m file -a "path=/root/naman state=directory mode=755"
```
shell module = For running the shell commands through ansible; -vvv= shows the working of backend in terminal
```
ansible localhost -m shell -a "date" -vvv
```





