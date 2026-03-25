#### These steps are performed on Debian 13 (trixie)
```
$ cat /etc/os-release
PRETTY_NAME="Debian GNU/Linux 13 (trixie)"
NAME="Debian GNU/Linux"
VERSION_ID="13"
VERSION="13 (trixie)"
VERSION_CODENAME=trixie
DEBIAN_VERSION_FULL=13.0
ID=debian
HOME_URL="https://www.debian.org/"
SUPPORT_URL="https://www.debian.org/support"
BUG_REPORT_URL="https://bugs.debian.org/"
```
```
(ansible_jobs) debian@debian:~/ansible_jobs$ ansible --version
ansible [core 2.20.4]
  config file = None
  configured module search path = ['/home/debian/.ansible/plugins/modules', '/usr/share/ansible/plugins/modules']
  ansible python module location = /home/debian/ansible_jobs/lib/python3.13/site-packages/ansible
  ansible collection location = /home/debian/.ansible/collections:/usr/share/ansible/collections
  executable location = /home/debian/ansible_jobs/bin/ansible
  python version = 3.13.5 (main, Jun 25 2025, 18:55:22) [GCC 14.2.0] (/home/tph3394/ansible_jobs/bin/python3)
  jinja version = 3.1.6
  pyyaml version = 6.0.3 (with libyaml v0.2.5)
(ansible_jobs) debian@debian:~/ansible_jobs$
```
```
(ansible_jobs) debian@debian:~/ansible_jobs$ pip3 show ansible-pylibssh
Name: ansible-pylibssh
Version: 1.4.0
Summary: Python bindings for libssh client specific to Ansible use case
Home-page: https://github.com/ansible/pylibssh
Author: Ansible, Inc.
Author-email: info+github/ansible/pylibssh@ansible.com
License: LGPLv2+
Location: /home/debian/ansible_jobs/lib/python3.13/site-packages
Requires:
Required-by:
(ansible_jobs) debian@debian::~/ansible_jobs$
```
