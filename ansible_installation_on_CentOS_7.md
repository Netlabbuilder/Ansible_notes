The following steps are to install the latest version of Ansible (ansible 2.8.5, as of 26.09.2019), and get it up and running on CentOS 7 (CentOS Linux release 7.6.1810) with Python3 (Python 3.6.8):

**1. Check CentOS 7 version:**
```
[root@netlabbuilder ~]# cat /etc/centos-release
CentOS Linux release 7.6.1810 (Core)

[root@netlabbuilder ~]# hostnamectl 
Static hostname: netlabbuilder  
Icon name: computer-vm  
Chassis: vm  
Machine ID: 0130132fcc9240d2b4c716df1dec6d7c  
Boot ID: 008c22643d7b4acb9535495785ed8efc  
Virtualization: vmware  
Operating System: CentOS Linux 7 (Core)  
CPE OS Name: cpe:/o:centos:centos:7  
Kernel: Linux 3.10.0-957.27.2.el7.x86_64  
Architecture: x86-64  
``` 
**2. Check Python (Python 2 and Python 3) version:**
```
[root@netlabbuilder ~]# python --version
Python 2.7.5
[root@netlabbuilder ~]# python3.6 --version
Python 3.6.8
```
**3. Install the latest version of Ansible and get it running with Python3**
```
[root@netlabbuilder ~]# pip3 install ansible
```
**4. Verify the ansible and its Python3 interpreter**
```
[root@netlabbuilder ~]# ansible --version
ansible 2.8.5
config file = /etc/ansible/ansible.cfg  
configured module search path = ['/root/.ansible/plugins/modules', '/usr/share/ansible/plugins/modules']  
ansible python module location = /usr/lib/python3.6/site-packages/ansible  
executable location = /usr/bin/ansible  
python version = 3.6.8 (default, May  2 2019, 20:40:44) [GCC 4.8.5 20150623 (Red Hat 4.8.5-36)]  
```
**5. Ansible working directory (folder) is found under /etc/ansible**
```
[root@netlabbuilder ~]# cd /etc/ansible/  
[root@netlabbuilder ansible]# tree  
├── ansible.cfg
├── hosts
├── playbooks
│   ├── config_name_server.yml
│   └── show_name_server.yml
└── roles

2 directories, 4 files
[root@netlabbuilder ansible]#
```
