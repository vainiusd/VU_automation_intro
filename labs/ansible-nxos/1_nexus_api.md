

# Cisco Nexus API

## All programability interfaces

- CLI (via SSH)
- NX-API (CLI) [link](https://www.cisco.com/c/en/us/td/docs/switches/datacenter/nexus9000/sw/93x/progammability/guide/b-cisco-nexus-9000-series-nx-os-programmability-guide-93x/b-cisco-nexus-9000-series-nx-os-programmability-guide-93x_chapter_010011.html)
- NX-API (REST) [link](https://www.cisco.com/c/en/us/td/docs/switches/datacenter/nexus9000/sw/93x/progammability/guide/b-cisco-nexus-9000-series-nx-os-programmability-guide-93x/b-cisco-nexus-9000-series-nx-os-programmability-guide-93x_chapter_0101110.html) 
- RESTCONF/NETCONF [link](https://www.cisco.com/c/en/us/td/docs/switches/datacenter/nexus9000/sw/93x/progammability/guide/b-cisco-nexus-9000-series-nx-os-programmability-guide-93x/b-cisco-nexus-9000-series-nx-os-programmability-guide-93x_chapter_010111.html)
- gNMI [link](https://www.cisco.com/c/en/us/td/docs/switches/datacenter/nexus9000/sw/93x/progammability/guide/b-cisco-nexus-9000-series-nx-os-programmability-guide-93x/b-cisco-nexus-9000-series-nx-os-programmability-guide-93x_chapter_0110001.html)


## NX-API
### NXAPI-CLI

Message format options demo in Postman:
- JSON
  - CLI SHOW
  - CLI SHOW ASCII
  - CLI CONF
- XML
  - CLI SHOW
  - CLI SHOW ASCII
  - CLI CONF


### NXAPI-REST (DME)

Input format types:
- CLI
- Model

### RESTCONF/NETCONF

Message format options demo in Postman:
- JSON
- XML (omitted)
- Ansible NETCONF usage [example p55](https://www.ciscolive.com/c/dam/r/ciscolive/emea/docs/2019/pdf/LTRDCN-2987.pdf).

NX-OS supported modules:
  - Cisco NXOS device model [link](https://github.com/YangModels/yang/blob/main/vendor/cisco/nx/10.3-2/Cisco-NX-OS-device.yang)
  - Openconfig (Beginning with Cisco NX-OS Release 9.2(1), support is added across a broad range of functional areas. Those include BGP, OSPF, Interface L2 and L3, VRFs, VLANs, and TACACs)

Analysis of raw YANG modules is quite complex:
- All modules per device version [github](https://github.com/YangModels/yang/tree/main/vendor/cisco/nx)
- YANG module catalog for more graphic views: [YANG catalog](https://yangcatalog.org/yang-search)

### gNMI

Section for future development.

## Ansible usage of Nexus API

Supported connections

The Cisco NX-OS collection supports network_cli and httpapi connections.
https://galaxy.ansible.com/cisco/nxos

Ansible NXOS collections:
https://docs.ansible.com/ansible/latest/collections/cisco/nxos/



Useful links:
  - Nick Russo's [postman collections](https://www.postman.com/njrusmc/workspace/public-collections/collection/14123647-d20ecb06-f5b5-4402-9f1e-1206c184be38)
  - NTC blog [comparing IOS-XE and NX-OS YANG models](https://blog.networktocode.com/post/Exploring-IOS-XE-and-NX-OS-based-RESTCONF-Implementations-with-YANG-and-Openconfig/)