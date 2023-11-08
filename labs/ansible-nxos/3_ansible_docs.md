# Ansible Documentation

## Readthedocs

Simple as that: https://docs.ansible.com/ansible/latest/

Network device management modules are out of core ansible - in ansible [galaxy](https://galaxy.ansible.com/): 
- NX-OS: https://galaxy.ansible.com/cisco/nxos
- IOS(-XE): https://galaxy.ansible.com/cisco/ios
- Everything "Cisco": [Search in galaxy](https://galaxy.ansible.com/search?deprecated=false&tags=networking&keywords=cisco)

Deeper into NX-OS galaxy page You'll see alist of modules starting with [cisco.nxos.nxos_aaa_server](https://github.com/ansible-collections/cisco.nxos/blob/main/docs/cisco.nxos.nxos_aaa_server_module.rst).

We'll review some module examples in later chapter, but for ducomentation understanding purposes take a look at module [cisco.nxos.nxos_vlans](https://github.com/ansible-collections/cisco.nxos/blob/main/docs/cisco.nxos.nxos_vlans_module.rst):
- Review *Parameters* table.
- Try to compare it to *Examples*.

## ansible-doc

Ansible docs provide the same information in a terminal window readable mode.

Run `ansible-doc cisco.nxos.vlans` and compare the output to what You see in online documentation.
