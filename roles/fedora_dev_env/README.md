# Fedora Development Environment Configuration Management

## Use Case
Purpose of this playbook is to install packages, programs and configurations needed for my development workflow via Pip, Fedora repo and shell. Sudo elevation is required and pip will apply to all users.

### Prepares the following:
- Ansible
- Python Packages
- Fonts
- VS Code and custom config
- TMUX Configuration 
- Bash configuration

```yaml
---
- name: Config Manage Fedora
  become: true
  hosts: all
  roles:
    - jacobvhs.unix_conf_management.fedora_dev_env
```
