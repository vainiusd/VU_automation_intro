# Quick reference


## Documentation
```
ansible-doc --list
ansible-doc full.module.name
```
## Inventory
```
ansible-inventory --list
ansible-inventory --host HOST
```
### Configuration
```
ansible-config view
ansible-config list
ansible-config init
ansible-config dump
```
### Vault
```
ansible-vault create filename.yml
```
### Playbook
```
ansible-playbook playbook.yml 

# Limit to a group or host:
ansible-playbook playbook.yml --limit N9K-1

# Varbose output:
ANSIBLE_VERBOSITY=[0|1|2|3|4] ansible-playbook playbook.yml
ansible-playbook playbook.yml -v[vvv]

# Dry-run check (do not implement changes):
ansible-playbook playbook.yml --check

# Understand the scope and task list of playbook
ansible-playbook playbook.yml --list-hosts
ansible-playbook playbook.yml --list-tasks

# Control playbook run:
ansible-playbook playbook.yml --step
ansible-playbook playbook.yml --start-at-task TASK
ansible-playbook playbook.yml --tags TAGS
ansible-playbook playbook.yml --skip-tags TAGS
```
