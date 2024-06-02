# MacOS Development Environment Configuration Management

## Use Case
Purpose of this playbook is to install packages, programs and configurations needed for my development workflow via Pip, homebrew and shell. Sudo elevation is only required for adding to /usr/local/bin whereas brew and pip should remain on the user level.

## Prepares the following:
- Ansible
- Python Packages
- Fonts
- VS Code and custom config
- TMUX Configuration 
- Bash configuration

## Usage
```yaml
---
- name: Config Manage Fedora
  become: true
  hosts: all
  roles:
    - jacobvhs.unix_conf_management.macos_dev_env
```