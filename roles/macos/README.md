# macos

## Installation
```shell
ansible-galaxy role install JacobVHS.macos
```

## Usage Example
```yaml
---
- name: Config Manage MacOS for Jacob
  hosts: localhost
  vars:
    username: "jacobschreuder"
    homebrew_formulaes:
      - tmux
    homebrew_casks:
      - kitty
  roles:
    - JacobVHS.unix_conf_management.macos
```
```shell
ansible-playbook playbook.yaml
```

## Author
Jacob Schreuder