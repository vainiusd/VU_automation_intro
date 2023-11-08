# Ansible NX-OS connection methods

## network-cli

Set necessary connectivity variables:
```
cat <<'EOF' > group_vars/all.yml
ansible_user: admin
ansible_password: Cisco12345
ansible_network_os: nxos
ansible_connection: ansible.netcommon.network_cli
EOF
```
Set actual device IP address (the name is not resovable):
```
cat <<'EOF' >> host_vars/N9K-1.yml 
ansible_host: 192.168.227.91
```
Create the playbook:
```
cat <<'EOF' > playbook.yml
---
- name: First playbook
  hosts: N9K-1
  gather_facts: false

  tasks:

  - name: Ping self
    cisco.nxos.nxos_ping:
      dest: 192.168.227.91
      vrf: management
EOF
```
And run this playbook with verbose output:
`ansible-playbook playbook.yml -vvvv`

## httpapi
Switch to HTTP API:
```
cat <<'EOF' >> group_vars/all.yml
ansible_connection: ansible.netcommon.httpapi
EOF
```
And run this playbook with verbose output:
`ansible-playbook playbook.yml -vvvv`

Do You see any difference?
The same command is sent to the device. The only difference actually is the transport and message format (which is hidden).
[Here is the source code](https://github.com/ansible-collections/cisco.nxos/blob/6d1d1976b1e6595beb219fabffa8017bbd111ec7/plugins/httpapi/nxos.py#L97) that shows the actual request destination.

## netconf
Implements pass through NETCONF client (raw xml messages). Source [link](https://github.com/ansible-collections/cisco.nxos/blob/6d1d1976b1e6595beb219fabffa8017bbd111ec7/plugins/netconf/nxos.py#L45C1-L46C9)

## Links

NXOS Platform Options: https://docs.ansible.com/ansible/latest/network/user_guide/platform_nxos.html