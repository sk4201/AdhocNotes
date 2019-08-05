# Day 13
# **Ansible**

**Ansible Adhoc Commands:-** for doing a work individually, each module has different command
-a= argument, -m= module, -k= key, a= group name, -u= user
```
ansible a -u ec2-user -k -m command -a "date"

ansible a -u ec2-user -k -m command -a "cal | wc -l"
```
for giving command to ansible in " "
```
ansible localhost -m shell -a " "
```
```
ansible localhost -m shell -a "cal | wc -l" 
```
```
ansible localhost -m shell -a "yum install httpd -y"

O/P:-

[WARNING]: Consider using the yum module rather than running yum.  If you need to use command because yum is insufficient you can add warn=False to
this command task or set command_warnings=False in ansible.cfg to get rid of this message.
                                                                                                                                                     
localhost | CHANGED | rc=0 >>
Loaded plugins: amazon-id, rhui-lb, search-disabled-repos
Package httpd-2.4.6-89.el7_6.x86_64 already installed and latest version
Nothing to doRepository 'python3' is missing name in configuration, using id
Repository 'docker' is missing name in configuration, using id
Repository 'ansible' is missing name in configuration, using id
Repository 'rhel' is missing name in configuration, using id
```
### **Ansible Impotent:-**

For correcting the error we put command:-
```
ansible localhost -m yum -a "name=httpd state=present"

O/P:
localhost | SUCCESS => {
    "ansible_facts": {
        "pkg_mgr": "yum"
    }, 
    "changed": false, 
    "msg": "", 
    "rc": 0, 
    "results": [
        "httpd-2.4.6-89.el7_6.x86_64 providing httpd is already installed"
    ]
}
```
Hosting HTML file in ec2 from Apache Server:-

Service Started:-
```
ansible localhost -m service -a "name=httpd state=started"
```
Now make a html file and then put this command and write the path of your html file in src:-

```
ansible localhost -m copy -a "src=index.html dest=/var/www/html"

O/P:
localhost | CHANGED => {
    "changed": true, 
    "checksum": "3b89e8fa144c88d69d4b7afce02760c871f587f7", 
    "dest": "/var/www/html/index.html", 
    "gid": 0, 
    "group": "root", 
    "md5sum": "e4d4152bc2a02453f13803252eae4c47", 
    "mode": "0644", 
    "owner": "root", 
    "secontext": "system_u:object_r:httpd_sys_content_t:s0", 
    "size": 25, 
    "src": "/root/.ansible/tmp/ansible-tmp-1560575863.48-129723564444637/source", 
    "state": "file", 
    "uid": 0
}
```
**PlayBook** :- includes all the modules of Ansible Adhoc Commands and this is written in ```YAML```(YAML Ain't Markup Language) language
no mandatory for putting playbook in specific location.
But in here we are putting it in /etc/ansible/playbooks/

### **PlayBook**
Playbook has 3 sections:-
* Target (grep)
* Variable (Optional)
* Tasks (Module) :- Write those Modules which we have to execute

Create a file by first.yml

Starting of .yml is always by 
```
---
```
```first.yml```
```
 - hosts: localhost             # this is target section
   tasks:
    - command: whoami 
```
Syntax checking:-
```
ansible-playbook first.yml --syntax-check

O/P:
playbook: first.yml
```
```
ansible-playbook first.yml

O/P:
PLAY [localhost] ************************************************************************************************************************************

TASK [Gathering Facts] ******************************************************************************************************************************
ok: [localhost]

TASK [command] **************************************************************************************************************************************
changed: [localhost]

PLAY RECAP ******************************************************************************************************************************************
localhost                  : ok=2    changed=1    unreachable=0    failed=0 
```
```two.yml```
```
---
 - hosts: localhost             # this is target section
   tasks:
    - command: whoami
    - shell: cal
    - yum: name=httpd state=present
```

```
---
 - hosts: a                     # this is target section            remote_user: ec2-user
   tasks:
    - command: whoami
    - shell: cal
    - yum: name=httpd state=present 
```

```proway.yml```
name is like a comment which tells what work is we doing
```
---
 - hosts: a                     # this is target section
   remote_user: ec2-user
   tasks:]
    - command: whoami
    - shell: cal
    - yum: name=httpd state=present 
```

```
ansible-playbook proway.yml --syntax-check
playbook: proway.yml 
```
```proway.yml```
```
---
 - hosts: localhost             # this is target section
   tasks:
    - name: running whoami command
      command: whoami
    - name: install httpd software
      yum: name=httpd state=installed
```

To check which keywords has what modules:- yum is a keyword in this:-
```
ansible-doc yum
```
```finalpro.yml```
```
---
 - hosts: localhost             # this is target section
   tasks:
    - name: installing httpd software
      yum:
       name: httpd
       state: present
```
```finalpro.yml``` another module
```
---
 - hosts: localhost             # this is target section
   tasks:
    - name: installing httpd software
      yum:
       name: httpd
       state: present

    - name: printing message
      debug:
       msg="Hello world this is Ansible "
```
For lists of all the modules:
```
ansible-doc -l
```
for searching all the modules of aws:-
```
ansible-doc -l | grep -i aws 
```