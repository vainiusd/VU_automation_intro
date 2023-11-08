# NX-OS modules

## Generic

Generic modules are for Yout to use as You please. As in command line configuration it is separated into "show" and "config" modes.

### [cisco.nxos.nxos_command](https://github.com/ansible-collections/cisco.nxos/blob/main/docs/cisco.nxos.nxos_command_module.rst)

This module allows running aarbitrary exec mode commands.
```
cat <<'EOF' >> playbook.yml

  - name: "Run 'show version | json' command"
    cisco.nxos.nxos_command:
      commands:
        - command: show version
          output: json
    register: version_json

  - name: Output last command result to terminal
    ansible.builtin.debug:
      var: version_json.stdout[0]

  - name: Set fact from json output
    ansible.builtin.set_fact:
      custom_hostname: "{{ version_json.stdout[0]['host_name'] }}"
 
  - name: Output just created fact to terminal
    ansible.builtin.debug:
      var: custom_hostname

  - name: "Run 'show version' command"
    cisco.nxos.nxos_command:
      commands:
        - command: show version
    register: version

  - name: Output last command result to terminal
    ansible.builtin.debug:
      var: version.stdout[0]
EOF
```
Run the extended playbook:
`ansible-playbook playbook.yml`

### [cisco.nxos.nxos_config](https://github.com/ansible-collections/cisco.nxos/blob/main/docs/cisco.nxos.nxos_config_module.rst)

This module allows executing config mode commands.
```
cat <<'EOF' >> playbook.yml

  - name: "Send configuration commands for interface Eth1/5"
    cisco.nxos.nxos_config:
      lines:
      - description Ansible set text
      - spanning-tree port type edge
      parents: interface Ethernet1/5
EOF
```

First run: `ansible-playbook playbook.yml`. You should see a change (`changed: [N9K-1]`).
Then again: `ansible-playbook playbook.yml`. No change is needed (`ok: [N9K-1]`)

## Feature oriented

### [cisco.nxos.nxos_vrf](https://github.com/ansible-collections/cisco.nxos/blob/main/docs/cisco.nxos.nxos_vrf_module.rst)

Instead of explicitly telling what commands to enter, run a module that already has the feature's configuration programmed in itself.

```
cat <<'EOF' >> playbook.yml

  - name: Enable BGP for VRFs
    cisco.nxos.nxos_feature:
      feature: bgp
      state: enabled

  - name: Create new VRF
    cisco.nxos.nxos_vrf:
      name: test_vrf
      rd: "2023:9"
      description: Ansible created VRF
      state: present
EOF
```

## Fact collection

### [cisco.nxos.nxos_facts](https://github.com/ansible-collections/cisco.nxos/blob/main/docs/cisco.nxos.nxos_facts_module.rst)

```
cat <<'EOF' >> playbook.yml

  - name: Gather legacy and resource facts
    cisco.nxos.nxos_facts:
      gather_subset: all
      gather_network_resources: all
      available_network_resources: true

  - name: Output collected facts to terminal
    ansible.builtin.debug:
      var: ansible_facts
EOF
```