## Ansible introduction

In this lab we will install ansible, prepare required files for running and run introductionary ansible playbooks against Nexus switches.

### Create python environment

Commands:
```
pwd
mkdir auto_lab
cd auto_lab/
mkdir env
python3 -m venv env
source env/bin/activate
```
Example output:
```
[stud1@netauto ~]$ pwd
/home/stud1
[stud1@netauto ~]$ mkdir auto_lab
[stud1@netauto ~]$ cd auto_lab/
[stud1@netauto ~]$ mkdir env
[stud1@netauto auto_lab]$ python3 -m venv .
[stud1@netauto auto_lab]$ source env/bin/activate
(env) [stud1@netauto auto_lab]$
```

Verify that Your environment is active:
1. bash prompt starts with environment name "(env)"
2. Python binary is located in environment's bin directory

```
(env) [stud1@netauto auto_lab]$ which python3
~/auto_lab/env/bin/python3
(env) [stud1@netauto auto_lab]$ deactivate 
[stud1@netauto auto_lab]$ which python3
/usr/bin/python3
```

### Install and prepare ansible

Commands:
```
python3 -m pip install ansible
ansible --version
ansible-galaxy collection install cisco.nxos
ansible-doc cisco.nxos.nxos_vlans
```

Example output:
```
(env) [stud1@netauto auto_lab]$ python3 -m pip install ansible
Collecting ansible
  Using cached https://files.pythonhosted.org/packages/01/ff/0bdc7b0698f7d4e02e7da6e96d7d856a42667419c5c48bbfc3f8dda9a80e/ansible-2.10.4.tar.gz

  ... Omitting output ...

Installing collected packages: MarkupSafe, jinja2, PyYAML, six, pycparser, cffi, cryptography, pyparsing, packaging, ansible-base, ansible
  Running setup.py install for PyYAML ... done
  Running setup.py install for ansible-base ... done
  Running setup.py install for ansible ... done
Successfully installed MarkupSafe-1.1.1 PyYAML-5.3.1 ansible-2.10.4 ansible-base-2.10.4 cffi-1.14.4 cryptography-3.3.1 jinja2-2.11.2 packaging-20.8 pycparser-2.20 pyparsing-2.4.7 six-1.15.0

(env) [stud1@netauto auto_lab]$ ansible --version
ansible 2.10.4
  config file = None
  configured module search path = ['/home/stud1/.ansible/plugins/modules', '/usr/share/ansible/plugins/modules']
  ansible python module location = /home/stud1/auto_lab/env/lib64/python3.6/site-packages/ansible
  executable location = /home/stud1/auto_lab/env/bin/ansible
  python version = 3.6.8 (default, Dec  3 2020, 18:11:24) [GCC 8.4.1 20200928 (Red Hat 8.4.1-1)]

(env) [stud1@netauto auto_lab]$ ansible-galaxy collection install cisco.nxos
Starting galaxy collection install process
Process install dependency map
Starting collection install process
Installing 'cisco.nxos:1.3.1' to '/home/stud1/.ansible/collections/ansible_collections/cisco/nxos'
Downloading https://galaxy.ansible.com/download/cisco-nxos-1.3.1.tar.gz to /home/stud1/.ansible/tmp/ansible-local-355636fr4i5w3/tmpzo52z5em
cisco.nxos (1.3.1) was installed successfully
Installing 'ansible.netcommon:1.4.1' to '/home/stud1/.ansible/collections/ansible_collections/ansible/netcommon'
Downloading https://galaxy.ansible.com/download/ansible-netcommon-1.4.1.tar.gz to /home/stud1/.ansible/tmp/ansible-local-355636fr4i5w3/tmpzo52z5em
ansible.netcommon (1.4.1) was installed successfully

(env) [stud1@netauto auto_lab]$ ansible-doc cisco.nxos.nxos_vlans
> CISCO.NXOS.NXOS_VLANS    (/home/stud1/.ansible/collections/ansible_collections/cisco/nxos/plugins/modules/nxos_vlans.py)

        This module creates and manages VLAN configurations on Cisco NX-OS.

  * note: This module has a corresponding action plugin.

  ... Omitting output ...
```

### Configure ansible

1. Configuration file
2. Inventory
3. Credentials
4. Test

### My first networking playbook



