# Netmiko introduction

In this lab we will install netmiko and run use this python library to connect and configure devices.

## Netmiko installation

1. Activate working environment
2. Install netmiko package
3. Test

### Activate working environment
Commands:
```
cd ~
cd auto_lab/
source env/bin/activate
```
Example output:
```
[stud1@netauto ~]$ cd ~
[stud1@netauto ~]$ cd auto_lab/
[stud1@netauto auto_lab]$ source env/bin/activate
(env) [stud1@netauto auto_lab]$
```

### Install netmiko package
Commands:
```
python3 -m pip install netmiko
```

Example output:
```
(env) [stud1@netauto auto_lab]$ python3 -m pip install netmiko
Collecting netmiko
  Downloading https://files.pythonhosted.org/packages/9b/5a/8db044231644359b1542a7d6e423aed7c925e62021c19d3f23256c3567cb/netmiko-3.3.2-py2.py3-none-any.whl (165kB)

  ... Omitting output ...

Installing collected packages: tenacity, pyserial, scp, future, textfsm, ntc-templates, zipp, importlib-resources, netmiko
  Running setup.py install for future ... done
Successfully installed future-0.18.2 importlib-resources-3.3.0 netmiko-3.3.2 ntc-templates-1.6.0 pyserial-3.5 scp-0.13.3 tenacity-6.3.1 textfsm-1.1.0 zipp-3.4.0
```

### Test

Commands:
```
python3
import netmiko
dir(netmiko)
```

Example output:
```
python3
Python 3.6.8 (default, Dec  3 2020, 18:11:24) 
[GCC 8.4.1 20200928 (Red Hat 8.4.1-1)] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> import netmiko
>>> dir (netmiko)
['BaseConnection', 'CNTL_SHIFT_6', 'ConnectHandler', 'FileTransfer', 'InLineTransfer', 'NetMikoAuthenticationException', 'NetMikoTimeoutException', 'Netmiko', 'NetmikoAuthenticationException', 'NetmikoTimeoutException', 'SCPConn', 'SSHDetect', '__all__', '__builtins__', '__cached__', '__doc__', '__file__', '__loader__', '__name__', '__package__', '__path__', '__spec__', '__version__', '_textfsm', 'a10', 'accedian', 'adtran', 'alcatel', 'apresia', 'arista', 'aruba', 'base_connection', 'broadcom', 'calix', 'centec', 'checkpoint', 'ciena', 'cisco', 'cisco_base_connection', 'citrix', 'cloudgenix', 'coriant', 'dell', 'dlink', 'eltex', 'endace', 'enterasys', 'extreme', 'f5', 'file_transfer', 'flexvnf', 'fortinet', 'hp', 'huawei', 'ipinfusion', 'juniper', 'keymile', 'linux', 'log', 'logging', 'mellanox', 'mikrotik', 'mrv', 'netapp', 'netgear', 'netmiko_globals', 'nokia', 'oneaccess', 'ovs', 'paloalto', 'platforms', 'pluribus', 'progress_bar', 'quanta', 'rad', 'raisecom', 'redispatch', 'ruckus', 'ruijie', 'scp_functions', 'scp_handler', 'sixwind', 'sophos', 'ssh_autodetect', 'ssh_dispatcher', 'ssh_exception', 'terminal_server', 'tplink', 'ubiquiti', 'utilities', 'vyos', 'watchguard', 'yamaha', 'zte']
```

## Managing a device

1. Connect
2. Send operational commands
3. Configure

### Connect
```
import netmiko
n9k_1 = { 
    'device_type': 'cisco_nxos', 
    'host': '192.168.227.91', 
    'username': 'admin', 
    'password': 'Cisco12345', 
}
conn = netmiko.ConnectHandler(**n9k_1)
conn.find_prompt()

```

### Send operational commands
```
output = conn.send_command("show interface status")
print (output)
```

### Configure

```
commands = ['vlan 15', 'name netmiko_vlan']
output = conn.send_config_set(commands)
print(output)

output = conn.send_command("show vlan id 15")
print(output)
```

### Cleanup
```
conn.disconnect()
```
