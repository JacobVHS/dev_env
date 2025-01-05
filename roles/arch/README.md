# Arch
This ansible role configures Arch Linux to run my desktop environment configuration and other shell configs.

A couple of assumptions are made for this role:
- The OS has had basic arch installed
- Your user has passwordless sudo

## Installation
```shell
ansible-galaxy role install JacobVHS.arch_conf
```

## Usage Example
```yaml
---
- name: Config Manage arch for Jacob
  hosts: localhost
  become: true
  vars:
    username: "jacob"
  roles:
    - JacobVHS.unix_conf_management.arch
```
```shell
ansible-playbook playbook.yaml
```

## Author
Jacob Schreuder