# ansible-role-macOS

## Installation
```shell
ansible-galaxy role install JacobVHS.macos_conf
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
    - JacobVHS.macos_conf
```
```shell
ansible-playbook playbook.yaml
```

## Author
Jacob Schreuder